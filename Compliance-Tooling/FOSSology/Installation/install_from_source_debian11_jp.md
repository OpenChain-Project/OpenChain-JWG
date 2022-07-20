# FOSSology をソースコードからインストールする手順 (Debian11)

This document explains how to install FOSSology from source code. Please refer to https://github.com/fossology/fossology/wiki/Install-from-Source for the original information in English from FOSSology project.

FOSSology (https://www.fossology.org/) には、  
  
- Dockerを使う
- VagrantとVirtualBoxを使う
- ソースコードからインストールする
  
の3つの主なインストール方法がある。この文書は、これらのうちソースコードからインストールする方法について、その手順を示すことを目的とする。

## 目次

1. テスト環境
1. ソースコードの取得
1. 前提ソフトウェアのインストール
1. FOSSologyのビルドとインストール
1.  インストール後の設定
1. Post-installスクリプトの実行
1. システムの起動時に自動的に起動させる設定
1. エラーへの対処

## 1. テスト環境

### 1.1 テスト環境
この文書に記載の内容は、以下の条件で動作テストした。


|Item|Description|
|---|---|
|OS |Debian GNU/Linux 11 (bullseye)|
|FOSSology |Version 4.1.0.16|
|CPU |Intel(R) Core(TM) i3-3220T CPU @ 2.80GHz|
|RAM |8GB|

### 1.2 ディスクスペース

FOSSologyは、アップロードされたデータをファイルシステム上のリポジトリに格納する。リポジトリへのデフォルトのパスは /srv/fossology/repository である。これは /usr/local/etc/fossology/fossology.conf により変更可能である。このリポジトリは、ソフトウェアパッケージをアップロードするにつれて次第に大きくなっていく。個人プロジェクト用途の小規模なシステムでは数Gバイト、大規模なシステムでは数百G〜数Tバイトにもなり得る。このリポジトリは独立したマウントポイントとすることが推奨されている。
https://github.com/fossology/fossology/wiki/Configuration-and-Tuning

また、PostgreSQL が使用する /var/lib/postgresql/ 以下も、大きなスペースを必要とする。

下の表は、新規インストールした FOSSology に linux-4.19.6.tar.gz をアップロードした際のディスクスペース使用量を du コマンドで調査した結果である。参考のために、ここに掲載する。

|Item |Disk space usage|
|---|---|
|Uploaded file (linux-4.19.6.tar.gz)|155 MBytes|
|/srv/fossology/|2.3 GBytes|
|/var/lib/postgresql/|513 MBytes|


## 2. ソースコードの取得

gitをまだインストールしていない場合は、インストールする。
```
$ sudo apt install git
```
適当なディレクトリに移動して、ソースコードをGitHubからクローンする。
```
$ git clone https://github.com/fossology/fossology.git
```

## 3. 前提ソフトウェアのインストール

この項目では lsb_release コマンドを使用するのでインストールする。既に最新版がインストールされている場合は、"lsb-release is already the newest version" というメッセージが出力される。
```
$ sudo apt install lsb-release
```
次に、ソースコードをクローンしたディレクトリの下の utils ディレクトリに移動する。ここでは仮に "~/install/fossology/utils" とする。
```
$ cd ~/install/fossology/utils
```
FOSSologyの古いバージョンをインストールしている場合は、それを削除する。スクリプトが用意されているので、それを実行する。
```
$ sudo ./fo-cleanold
```
次に、前提ソフトウェアをインストールする。これも、用意されたスクリプトを実行するだけで、必要なソフトウェアが自動でインストールされる。
```
$ sudo ./fo-installdeps
```

## 4. FOSSologyのビルドとインストール
"~/install/fossology" に移動して、make を実行する。
```
$ cd ..
$ make
$ sudo make install
```

## 5.  インストール後の設定

この項目に記載の内容は、以下を参考にしている。  
https://github.com/fossology/fossology/wiki/Configuration-and-Tuning  
ただし、上記サイトの "Adjusting the Kernel" の項目については、PostgreSQL 9.3 およびそれ以降のバージョンでは設定不要なので、本文書では取り扱わない。  
https://wiki.postgresql.org/wiki/What%27s_new_in_PostgreSQL_9.3

### 5.1 PostgreSQLのチューニング

/etc/postgresql/<VERSION>/main/postgresql.conf を編集する。今回のテスト環境では以下の各行を次のように変更した。インストールするシステムのRAM容量に応じて適宜調整するとよい。
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
```
$ sudo systemctl restart postgresql
```

### 5.2 PHPの設定

今回のテスト環境では、/etc/php/<VERSION>/apache2/php.ini の以下の各行を次のように変更した。

```
max_execution_time = 300
memory_limit = 702M
post_max_size = 701M
upload_max_filesize = 700M
```

### 5.3 Apache の設定

/etc/apache2/sites-available にある 000-default.conf を、FOSSologyのものに置き換える。必要になったら元に戻せるよう、元のファイルは適宜保存するとよい。

```
$ cd /etc/apache2/sites-available
$ sudo ln -s /usr/local/etc/fossology/conf/src-install-apache-example.conf 000-default.conf
```
次に、
```
$ sudo apache2ctl configtest
```
を実行して、"Syntax OK" が出力されることを確認する。ここで、AH00558やAH00671のエラーが出る場合の対処については後述する。
```
$ sudo apache2ctl graceful
```
を実行して Apache を再起動する。

## 6. Post-installスクリプトの実行

インストール後の設定を自動で行うスクリプトが用意されているので、それを実行する。データベースの作成などが行われる。
```
$ cd /usr/local/lib/fossology
$ sudo ./fo-postinstall
```
以下のコマンドを実行して、FOSSologyが正しくインストールされたことを確認する。(メッセージは何も出力されない)

```
$ cd /usr/local/etc/fossology/mods-enabled/scheduler/agent
$ sudo ./fo_scheduler -t
```

Webブラウザから http://<IP_ADDRESS>/repo/ にアクセスしてユーザ名 fossy / パスワード fossy でログインし、以下を実施する。

- 自分用のユーザアカウントを、管理者権限ありで作成する。  
- ユーザ fossy のパスワードを変更しておく。  

## 7. システムの起動時に自動的に起動させる設定

システムの起動時にFOSSologyが自動的に起動するよう、次のコマンドを実行する。
```
$ sudo systemctl enable fossology
```
最後にシステム全体を再起動して、FOSSologyが立ち上がることを確認する。

## 8. エラーへの対処

### 8.1 apache2ctl configtest の AH00558

$ sudo apache2ctl configtest を実行した際に、
```
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
```
が出力される場合には、/etc/apache2/conf-available に fqdn.conf を作成して、以下の内容を記述する。(hogehoge のところには、そのサーバのホスト名を記述する)

```
ServerName hogehoge
```

次に、以下のコマンドを実行する。
```
$ sudo a2enconf fqdn
$ sudo service apache2 restart
```

### 8.2 apache2ctl configtest の AH00671

```
AH00671: The Alias directive in /etc/apache2/sites-enabled/fossology.conf at line 3 will probably never match because it overlaps an earlier Alias.
```
この warning が出る理由は、000-default.conf と fossology.conf の両方に同じ記述
```
Alias /repo /usr/local/share/fossology/www/ui
```
があるためであると思われるが、そのどちらか一方を削除すると、この warning は出なくなる一方、FOSSologyが起動しなくなる。この warning は無視してよさそうである。

---
OpenChain Japan WG - This document is licensed under Creative Commons CC0 1.0 Universal.

