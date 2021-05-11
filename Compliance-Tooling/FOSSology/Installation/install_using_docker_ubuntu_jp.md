# FOSSology をDockerを使ってインストールする手順 (Ubuntu編)

[FOSSology](https://www.fossology.org/ "www.fossology.org") には、  
  
- Dockerを使う
- VagrantとVirtualBoxを使う
- ソースコードからインストールする
  
の3つの主なインストール方法がある。この文書は、これらのうちDockerを使ってインストールする方法について、その手順を示すことを目的とする。Docker を使う方法では、Docker イメージ単体ではスキャンした結果の保存が保証されないため、データベースをコンテナの外部に用意することが[推奨](https://github.com/fossology/fossology/blob/master/README.md#user-content-docker)されている。また、FOSSologyは、アップロードされたデータをファイルシステム上のリポジトリに格納する。このリポジトリは、ソフトウェアパッケージをアップロードするにつれて次第に大きくなっていく。個人プロジェクト用途の小規模なシステムでは数Gバイト、大規模なシステムでは数百G〜数Tバイトにもなり得る。このリポジトリは独立したマウントポイントとすることが[推奨](https://github.com/fossology/fossology/wiki/Configuration-and-Tuning)されている。そこで本文書では、Docker container 上の FOSSology から host OS 上の PostgreSQL データベースおよび上記リポジトリ用ディレクトリにアクセスするようにインストールする手順を紹介する。

## 目次

1. テスト環境
1. Apacheの停止
1. Docker CEのインストール
1. PostgreSQLのインストールと設定
1.  リポジトリ用ディレクトリの作成
1. FOSSologyの実行とシステム起動時に自動的に実行するための設定
1. Docker イメージの更新

## 1. テスト環境

この文書に記載の内容は、以下の環境で動作テストした。


|Item|Description|
|---|---|
|OS |Ubuntu 20.04.1 LTS (Focal Fossa) |
|CPU |Intel(R) Core(TM) i5-3470T CPU @ 2.90GHz|
|RAM |8GB|

## 2. Apacheの停止

システムに Apache HTTP サーバがインストールされている場合は、これを停止する。
```
$ sudo systemctl stop apache2
$ sudo systemctl disable apache2
```

## 3. Docker CE のインストール

Ubuntu に Docker CE をインストールする。本項は[こちら](https://docs.docker.com/engine/install/ubuntu/)を参考にした。

### 3.1 古いバージョンのアンインストール

```
$ sudo apt remove docker docker-engine docker.io containerd runc
```

### 3.2 前提ソフトウェアのインストール

```
$ sudo apt update
$ sudo apt install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

### 3.3 GPG 公開鍵のインストールと確認

公開鍵のインストール

```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

フィンガープリントの確認

```
$ sudo apt-key fingerprint 0EBFCD88

pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]
```

### 3.4 aptリポジトリの設定

```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

### 3.5 Docker CE のインストール

```
$ sudo apt update
$ sudo apt install docker-ce docker-ce-cli containerd.io
```

### 3.6 ユーザ名の docker グループへの追加と動作確認

rootではなく自分のユーザの権限で Docker を起動できるように、ユーザ名を docker グループに追加する。この設定を反映させるには、コマンドの実行後、一旦ログアウトして再ログインが必要である。一般ユーザの権限で Docker を起動しない場合は省略可能。

```
$ sudo gpasswd -a ${USER} docker
$ exit
```
Hello-world イメージを実行してみて、Docker が正しくインストールされたことを確認する。
```
$ docker run hello-world
```

## 4. PostgreSQLのインストールと設定

### 4.1 PostgreSQLのインストール

```
$ sudo apt update
$ sudo apt install postgresql
```

### 4.2 postgres ユーザのパスワードを設定

postgresユーザのパスワードを設定する。パスワードは任意である。

```
$ sudo passwd postgres
```

### 4.3 データベースの作成

前項で設定したパスワードで "postgres" としてログインし、データベース "fossology" を作成する。続けて、データベースのユーザ "fossy" を作成する。パスワードは "fossy" を設定する。

```
$ su - postgres
$ createdb fossology
$ createuser --pwprompt --interactive fossy
Enter password for new role: 						← fossy を入力
Enter it again: 							← fossy を入力
Shall the new role be a superuser? (y/n)				← n を入力
Shall the new role be allowed to create databases? (y/n)		← n を入力
Shall the new role be allowed to create more new roles? (y/n)		← n を入力
```

"postgres" ユーザからログアウトする。

```
$ exit
```

### 4.4 PostgreSQLのチューニング

この項目に記載の内容は、[こちら](https://github.com/fossology/fossology/wiki/Configuration-and-Tuning)を参考にしている。ただし "Adjusting the Kernel" の項目については、PostgreSQL 9.3 およびそれ以降のバージョンでは[設定不要](https://wiki.postgresql.org/wiki/What%27s_new_in_PostgreSQL_9.3)なので、本文書では取り扱わない。  

/etc/postgresql/12/main/postgresql.conf を編集する。今回のテスト環境では以下の各行を次のように変更した。インストールするシステムのRAM容量に応じて適宜調整するとよい。
```
shared_buffers = 2GB                    # システムのRAMが1GB以上の場合はRAMの1/4〜
effective_cache_size = 4GB              # RAMの1/2〜3/4
work_mem = 128MB
maintenance_work_mem = 400MB            # RAM 1GBあたり50MB が目安
fsync = on
full_page_writes = off
standard_conforming_strings = on
autovacuum = on
```
これらの設定を有効にするには、PostgreSQLの再起動が必要である。

## 5. リポジトリ用ディレクトリの作成

```
$ sudo mkdir /srv/fossology
```

## 6. FOSSologyの実行とシステム起動時に自動的に実行するための設定

### 6.1 Docker イメージの取得

```
$ docker pull fossology/fossology
```

### 6.2 FOSSology の実行
```
$ docker run -d --name=FOSSology \
    -v /srv/fossology:/srv/fossology \
    -v /etc/localtime:/etc/localtime:ro \
    --network="host" -e FOSSOLOGY_DB_HOST="127.0.0.1" fossology/fossology
```

Webブラウザから http://HOST_IP_ADDRESS/repo/ にアクセスして、FOSSology が起動していることを確認する。

### 6.3 システム起動時に自動的に実行するための設定

/etc/systemd/system に docker-fossology.service を作成する。

```
$ sudo vi /etc/systemd/system/docker-fossology.service
```

上記ファイルに以下の内容を記述する。

```
[Unit]
Description=FOSSology container
Requires=docker.service
After=docker.service

[Service]
Restart=always
ExecStart=/usr/bin/docker start -a FOSSology
ExecStop=/usr/bin/docker stop -t 2 FOSSology

[Install]
WantedBy=default.target
```

システム起動時に自動的にサービスとして起動するための設定

```
$ sudo systemctl enable docker-fossology.service
```

最後にシステムを再起動して、FOSSology が起動していることを確認する。

## 7. Docker イメージの更新

### 7.1 Docker イメージの取得

```
$ docker pull fossology/fossology
```
取得した Docker イメージの確認。新しい方のイメージの TAG が latest となる。
```
$ docker images
REPOSITORY            TAG                 IMAGE ID            CREATED             SIZE
fossology/fossology   latest              c495f03ae95e        3 days ago          644MB
fossology/fossology   <none>              74467f7793ed        3 weeks ago         644MB
hello-world           latest              bf756fb1ae65        7 months ago        13.3kB
```
### 7.2 起動中のコンテナの削除

起動中のコンテナを強制削除する。このコマンドの "FOSSology" は、6.2 項の docker run コマンドで指定したコンテナ名である。
```
$ docker rm -f FOSSology
FOSSology
```
### 7.3 コンテナの起動
```
$ docker run -d --name=FOSSology \
    -v /srv/fossology:/srv/fossology \
    -v /etc/localtime:/etc/localtime:ro \
    --network="host" -e FOSSOLOGY_DB_HOST="127.0.0.1" fossology/fossology
```
### 7.4 不要なイメージの削除

停止しているコンテナをすべて削除する。
```
$ docker container prune
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
```
不要なイメージを削除する。
```
$ docker rmi $(docker images -f "dangling=true" -q)
```

---
OpenChain Japan WG - This document is licensed under Creative Commons CC0 1.0 Universal.

