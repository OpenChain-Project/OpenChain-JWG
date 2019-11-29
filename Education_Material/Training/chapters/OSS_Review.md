---
---
# 第5章
# 企業におけるOSS利用
# OSSレビュー


---
---
# OSSレビュー                                    

## プログラムマネージャー、プロダクトマネージャーおよびエンジニアに提案されたOSSコンポーネントの有益性や品質面のレビューを実施しその後、選択されたコンポーネントの使用に付随する権利や義務についてのレビューが開始される

## OSSコンプライアンス プログラムにとって鍵となる要素が「OSS レビュー」のプロセスであり、これにより企業は使用するOSSを分析し、権利と義務を理解することができる

## OSSレビューのプロセスには以下のステップがある：
  * 関連情報の収集
  * ライセンスの義務の分析と理解
  * 企業のポリシーや事業目標に合わせた指導の提供

---
#### OSSレビューはOSSコンプライアンス プログラムの基本的構成要素です。 

#### OSSレビューはエンジニアリング チーム、ビジネス チーム、および法務チームが集まる場となりえます。より大規模に首尾よく行うために、計画や組織化を必要とする場合があります。
#### 関連情報収集においてエンジニアリング チームもしくは開発チームが参加することもあります。
#### 法務チームはライセンスの義務について分析、決定を下し、指導を行います。
#### ビジネスおよびエンジニアリング チームは指導を受けて、実装します。

#### The OSS Review is a basic building block of a OSS Compliance Program. 

#### A OSS Review can be the meeting point for engineering, business and legal teams, and can require planning and organization to successfully conduct on a large scale.
#### Engineering or developer teams may participate in gathering relevant information
#### Legal teams analyze and determine license obligations and provide guidance
#### Business and engineering teams may receive and implement guidance


---
---
# どのような情報を集める必要があるか？

## OSSの使用分析にあたり、OSSコンポーネントの属性、起源、使用方法などの情報を集める。たとえば以下のようなものがある。

  * パッケージ名
  * パッケージを取り巻くコミュニティの状況（活動状況、メンバーの多様性、反応の早さ）
  * 版名（バージョン）
  * ダウンロード元もしくはソースコードのURL
  * 著作権保有者
  * ライセンスおよびライセンスのURL
  * 帰属表示やその他の告知/通知/表示、それらのURL
  * 意図して行われた改変に関する記述
  * 依存関係のリスト
  * 製品で意図している使用方法
  * そのパッケージを内包する製品のファースト リリース（最初の公開・販売）
  * ソースコードがメンテナンスされているロケーション
  * 過去に別経緯でそのパッケージに対して下された承認の可能性
  * 外部ベンダーからの提供物の場合： 
  * 開発チームのコンタクト ポイント
  * 著作権表示、帰属表示、およびライセンスの義務履行に必要なベンダー改変ソースコード

---
#### 注目すべきは、この情報のリストが 非常に多く見えることです。しかし、必要とされる情報量はOSSコードを取り扱おうとする企業の規模、および、OSSをどのように取り扱うかに依存します。大規模な組織体は小規模なものよりも多くの情報を必要とする傾向があります。
#### 外部ベンダーを利用した場合は、いくつか付加的な論点があります。まず、将来的にOSSに関する問題が生じた場合、そのベンダーを追跡調査する必要があるかもしれません。その際に信頼できるコンタクト先が重要となります。またベンダーから引き渡されたOSSに対しライセンスの義務を果たす必要があるかもしれません。そういった義務を果たすべく必要性に応じて告知／表示やソースコードがあることを確かめましょう。

---
#### It should be noted that this list of information looks quite large. However, the amount of information required depends on the size of your company and what you intend to do with the OSS code. Large entities tend to require more information than small entities.

---
---
# ソースコード スキャン ツール

## ソースコードスキャンを自動化するツールは数多く、さまざまなものが存在

## それらのすべては特定のニーズに向けたソリューションであるため、あらゆる課題を解決するものではない

## 企業はそれらの中で自分たちの特定の市場領域や製品に合うものを選定する

## 多くの企業は自動化ツールと人手によるレビューを併用している

## 無償で、自由に利用できるソースコード スキャン ツールの1つのよい例としてThe Linux Foundation でホストしたプロジェクトである、OSSologyがある：https://www.OSSology.org 

---
#### 本スライドではオープンソースコードスキャンツールがどんなもので、それがどういった働きをし、経験の浅いユーザがこのトピックについてどのように知識を集めることができるのか、といった点について全体像で説明しています。

#### This slide explains the big picture of what Open Source code scanning tools are, how they work, and where a new user can start to gather knowledge about the subject.


---
---
