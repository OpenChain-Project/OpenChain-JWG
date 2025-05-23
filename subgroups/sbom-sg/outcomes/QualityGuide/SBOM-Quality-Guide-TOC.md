# SBOM品質向上ガイド

## 目次

0. [はじめに](#0-はじめに)  
1. [目的と適用範囲](#1-目的と適用範囲)  
2. [用語と定義](#2-用語と定義)  
3. [基本要求事項](#3-基本要求事項)  
4. [適合通知](#4-適合通知)  
5. [SBOM品質評価と改善策](#5-SBOM品質評価と改善策)  
 5.1 [情報記述の正確性および一貫性の確保](#51-情報記述の正確性および一貫性の確保)  
 5.2 [コンポーネント粒度の標準化と正規化](#52-コンポーネント粒度の標準化と正規化)  
 5.3 [ソース情報の補完と透明性向上](#53-ソース情報の補完と透明性向上)  
 5.4 [脆弱性連携及びリスクマネジメントの強化](#54-脆弱性連携及びリスクマネジメントの強化)  
 5.5 [上流・下流間の情報統合と連携強化](#55-上流下流間の情報統合と連携強化)  
 5.6 [改ざん検知と変更管理体制の構築](#56-改ざん検知と変更管理体制の構築)  
 5.7 [記述範囲の明確化と責任所在の定義](#57-記述範囲の明確化と責任所在の定義)  
 5.8 [部品間関係性の統一的表現](#58-部品間関係性の統一的表現)  
6. [自動化戦略と運用プロセス](#6-自動化戦略と運用プロセス)  
 6.1 [自動検証ツールの導入](#61-自動検証ツールの導入)  
 6.2 [変換プロセスと正規化](#62-変換プロセスと正規化)  
 6.3 [運用負荷軽減と人的レビューの統合](#63-運用負荷軽減と人的レビューの統合)  
7. [ガイドの運用と管理](#7-ガイドの運用と管理)  
 7.1 [ガイド更新プロセス](#71-ガイド更新プロセス)  
 7.2 [改訂履歴の管理と文書化](#72-改訂履歴の管理と文書化)  
8. [参考文献・関連資料](#8-参考文献関連資料)

#### Appendix-1. [SBOM サンプル](#appendix-1-sbom-サンプル)
#### Appendix-2. [5章の項目記載用テンプレート](#appendix-2-5章の項目記載用テンプレート)

---

### 0. はじめに  
本章では、SBOMの品質向上が求められる背景及び本ガイドの作成意義を説明します。OpenChain-Telco-SBOM-Guideの基本枠組みを踏襲しながら、最新の業界議論で挙げられた課題を統合し、透明性や整合性を持ったSBOM作成のための指針を示す狙いについて述べる。

## 各章概要

### 1. 目的と適用範囲  
[OpenChain Telco SBOM Guide Version 1.1の 1.スコープ](https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_JP.md#1-%E3%82%B9%E3%82%B3%E3%83%BC%E3%83%97) を継承する。必要に応じてフォーマットおよび産業非依存の形に追加・削除・変更する。このガイドを詳細にブレークダウンしたものが各産業界、各フォーマットで利用できるように記述する。(以降、同様)  

- **目的**：SBOMの標準化、正確性、透明性、及び自動化可能性を高めるための改善策を示し、関係者間での共通理解を形成する。  
- **適用範囲**：ソフトウェアパッケージ、コンテナ、SaaS、組込みソフトウェアなど、あらゆるSBOM生成及び運用における対象プロセス。

> 文言を適切に選んで記載する必要があり、少し悩むかも知れないので短いですが1名アサインさせてください。  

> おそらく内容が全部でそろってから改変が必要、とりあえずのドラフトです。

担当: [田中の]

本文書 "SBOM Quality Guide" は、サプライチェーンの中での関係者の共通理解を形成するためのドキュメントです。SBOMの標準化、正確性、透明性、及び自動化の可能性を高めるための改善策を提示します。

サプライチェーンの関係者がソフトウェア部品表（SBOM：Software Bill of Materials）を作成・提供・利用する場合に共通課題となる点について改善策を提案することにより、SBOM流通時の障壁を取り除くための助けとなります。

本ガイドは、本ガイドに適合するエンティティに対して、OpenChain （OpenChain Specificationのどのバージョンでも）を採用することを要求するものではありませんが、OpenChainを採用することが大いに推奨されることに留意ください。(Comment:この文必要?)

このガイドは、ソフトウェアパッケージ、コンテナ、SaaS、組込みソフトウェアなど、あらゆるSBOM生成及び運用における対象プロセスに適応することを前提に記述されています。本ガイドが参照するのは個々のSBOMであり、SBOMを提供するエンティティではありません。
本ガイドに沿ったSBOMを「SBOM Quality Guide Compatible」と呼ぶことができます。

本ガイドの要件に一致するSBOMをリリースすることは、同じソフトウェアのSBOMを別の方法または形式で配信することを妨げるものではありません。

本ガイドは Creative Commons Attribution License 4.0 (CC-BY-4.0)の下にライセンスされています。(Comment:＞ライセンスはこれでいい?)

### 2. 用語と定義  
[OpenChain Telco SBOM Guide Version 1.1の 2.用語と定義](https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_JP.md#2-%E7%94%A8%E8%AA%9E%E3%81%A8%E5%AE%9A%E7%BE%A9) を継承する。  

本章では、SBOM、SPDX、CycloneDX、purl、依存関係など、本ガイドで使用する専門用語の定義を統一し、混乱や誤解が生じないよう基盤知識を整理する。

> 主にCDXの説明追加。他にも必要な単語やフレーズがあれば適宜追加ください。1名。  

担当: [富田]  

### 3. 基本要求事項  
[OpenChain Telco SBOM Guide Version 1.1の 3.要求要件](https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_JP.md#3-%E8%A6%81%E6%B1%82%E8%A6%81%E4%BB%B6) を継承する。

> 3.1 データフォーマット / 3.2 SPDX要素  
> (3.3) CDX要素 について という項目を追加して記載。1名  

担当: []  

> 3.3 (3.4に変更) 機械が読み取り可能なデータフォーマット / 3.4 (3.5に変更) 人間が読み取り可能なデータフォーマット 
> CDXはJSONだけなので、Tag:Valueの扱いをどうしたら良いか、またSPDXとして記載してある部分をどのように修正したら良いかを考え、案として記載して下さい。 1名  

担当: []  

> 3.5 (3.6に変更) SBOM ビルド情報  
> 4章の課題と解決に含まれる部分があるかもしれませんが、一旦、CreaterのValueとして email などを含める必要がある点(課題議論で出ていましたが、このフィールドは責任組織を表すとともに、連絡を取りたいときに使うのが目的となるため) があるのでそれらを考え案として記載してください。 1名  

担当: []  

> 3.6 (3.7に変更) 納入のタイミング / 3.7 (3.8に変更) 納入方法 / 3.8 (3.9に変更) SBOMの範囲 / 3.9 (3.10に変更) SaaSで提供されるSBOM / 3.10 (3.11に変更) コンテナ用SBOM 
> 3.11 (3.12に変更) SBOMの検証 / 3.12 (3.13に変更) SBOM の merge / 3.13 (3.14に変更) SBOM の守秘義務  
> 議論が必要になりますが、SPDXという単語が利用されている部分以外は 特に変更しないでよさそう。 量が多いので3.6からと3.11からの2名  

担当: [], []  

### 4. 適合通知  
[OpenChain Telco SBOM Guide Version 1.1の 4. 適合通知](https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_JP.md#4-%E9%81%A9%E5%90%88%E9%80%9A%E7%9F%A5) を継承。  

> ```OpenChain SBOM Quality Guide v1.0``` とドキュメント名を修正して記載
> 分量も少ないので他を担当している方でも重複して担当可能  

担当: [富田]

### 5. SBOM品質評価と改善策  
本章では、OpenChain SBOM SG 内の議論で提起された課題に基づいて、SBOMの質を評価および改善する具体的なチェック項目と解決策を体系的に整理し、ベストプラクティスとして記載する。  
[5章の項目記載用テンプレート](#appendix-2-5章の項目記載用テンプレート) を用いて追加する。  

> **以下は、SBOM sg 内で議論されたものの例**  
> これら議論の内容から重複するものをマージしてピックアップした  
> [2025/02/03](https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/meetings/20250203.md)  
> [2025/02/17](https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/meetings/20250217.md)  
> [2025/02/25](https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/meetings/20250225.md)  
> [2025/03/05](https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/meetings/20250305.md)  
> [2025/03/24](https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/meetings/20250324.md)

#### 5.1 情報記述の正確性および一貫性の確保  

##### 5.1.1. 課題の概要  
パッケージ名、バージョン、サプライヤー名などの記述について、各部署やツールごとに表記方法が異なるため、情報の正確性と一貫性が欠如しています。統一された基準がない場合、SBOMの自動解析や脆弱性マッチング等において、正確な判定が困難になる。

##### 5.1.2. 課題の詳細  
例えば、様々な仕様やガイドラインにおいて SBOM では パッケージ名の記載が必須となっているが、その記述内容については明確な規程が無い。その為、サプライヤーによっては、パッケージ名称にバージョン情報を含めたり、パッケージ名称にディストリビューション名が含まれている等、各部署やツールごとに表記方法が異なる。この場合、全く同じパッケージであっても、受領側で同一パッケージであることを特定することが困難になる。

##### 5.1.3. 改善策  
- 業界標準や社内ルールに基づいた統一表記ルールを策定し、具体例（正規表現などのフォーマット例）を広く共有。  
- 自動検証ツールを提供、各パッケージ名・バージョン・サプライヤー名の記載がルールに準拠しているかをチェックする仕組みを構築。  
- 定期的なレビューおよびフィードバックプロセスを整備し、記載基準の変更や改善策の継続的なアップデートを実施。

##### 5.1.4. 評価方法  
- 自動検証ツールによるルール違反件数の定量的なモニタリングを実施し、改善前後の誤記や不整合件数の減少率を評価。  
- 定期的に、各記述項目が統一ルールに沿って記載されているかをランダムにチェックし、合格率を評価。  
- フィードバックプロセス内で、ツールやルールの更新による運用効果を各社各部門間などで共有し、改善効果の定性的評価を合わせて実施。

##### 5.1.5. リスクと留意事項  
- 自動検証ツールのルール設定が不十分な場合、例外ケースや特殊な記述に対する対応が不完全になる可能性がある。  
- ルールの改定や正規表現の例示が現場実態と乖離している場合、過度な自動チェックによって正当な情報が誤検知されるリスクがある。  
- ツールやプロセスは完全自動化が難しく、最終的な精査や例外事項の対応は人的レビューが必要となる点を留意する必要がある.

#### 5.2 コンポーネント粒度の標準化と正規化  
担当: 田中さん  
- ファイル単位またはパッケージ単位といった情報記述の粒度を明確にし、複数のSBOM間で情報統合を図るための変換ツールの利用方法を整理。

##### 5.2.1. 課題の概要

SBOMに含まれるコンポーネントの単位には、ファイルとパッケージの2種類が想定される。
サプライチェーンの中でこのコンポーネントの粒度が統一できれば問題はないが、サプライチェーンが複雑になると、サプライチェーンの中でコンポーネントの粒度が異なるSBOMをやり取りする可能性が高くなる。
SBOMを1つのファイルにマージして提供するか、複数のファイルで提供するかに関係なく、サプライチェーンの中で粒度が異なるSBOMが存在する場合に、矛盾なく依存関係を記述することができるのかという課題がある。

##### 5.2.2. 課題の説明

この課題について、以下のように、Vendor、Maker、Userの3者のみの単純化した条件で説明する。
- 前提条件
  1. VendorがアプリAをバイナリとSBOMでMakerに提供する
  1. MakerがアプリAとOSSを含む商品XとSBOMをUserに提供する
  1. アプリAはMakerが商品Xで使用しているOSSに依存している

上記の条件で、アプリAのSBOMのコンポーネントの粒度がバイナリファイルまたはバイナリパッケージの場合と、Makerが最終商品のコンポーネントの粒度をバイナリファイルまたはバイナリパッケージでSBOMを生成する場合の組み合わせを表にした。

|||MakerがUserに提供するSBOM|MakerがUserに提供するSBOM|
|-|-|-|-|
||コンポーネントの単位|ファイル|パッケージ|
|Vendorが提供するアプリAのSBOM|ファイル|ファイル単位|アプリAが依存するOSSのファイル情報をパッケージ情報に変換してアプリAのみファイル単位にする|
|Vendorが提供するアプリAのSBOM|パッケージ|アプリAのパッケージからファイルを分解してファイル単位にする|パッケージ単位|

上記の表からわかる通り、どのケースでも対応は可能だが、組み合わせによってMakerの作業の手間に違いが出ることが分かった。
各SBOMのコンポーネントの粒度の違いにより異なる対応が必要になるということから、コンポーネントの粒度ががわからないと対応ができないということになる。
この例のように単純なサプライチェーンの場合は、SBOMに粒度の情報がなくても別の手段で確認することはできそうであるが、さらにサプライチェーンが複雑になるとSBOM自身に粒度の情報が必要となる。

##### 5.2.3. 改善策

コンポーネントの粒度がわかるようになっていて、粒度に合わせた対応ができること。
現実的には、SBOMの交換フォーマットの仕様によりパッケージとファイルの違いはわかるようになっているので問題ないと思われるが、フォーマットに関係なく上位レベルでコンポーネントの粒度の違がわかるようになっているという条件があることが必要だと考える。

##### 5.2.4. 評価方法

最終商品のSBOMを作成するために外部から受け取ったり、内部で作成したりした複数のSBOMについてこの粒度の違いがあるのかを判別できること。

##### 5.2.5. リスクと留意事項

コンポーネントの粒度の違いをSBOMの表記上では解決できたとしても、実際に脆弱性情報と紐づけるときに問題が起きるのではないか。
例えば、コンポーネントの粒度がファイル単位の情報が混ざっている場合に、脆弱性情報とのマッピングが手間なくできるのかという懸念がある。


#### 5.3 ソース情報の補完と透明性向上  
担当: 武山さん
- バイナリ提供時にもソースファイル一覧、ハッシュ値、ライセンス情報など補完すべき情報を必須項目化するなど、自動抽出プロセスを導入する方針を示す。

#### 5.4 脆弱性連携及びリスクマネジメントの強化  
担当: 細見さん  

##### 5.4.1. 課題の概要
- 各コンポーネント情報と脆弱性情報（CVE等）の連携方法、及びリスク評価を自動的にマッピングする仕組みの導入方法を規定する。  
- 脆弱性情報をどのようにSBOMの各エントリに反映させ、何を結論として確定するかが明確に定義されていない  
- 法規制や社内ルールとの整合をとるためには、最終的に人手による確認やメタデータの調整が必要となる  
- CPEで仕様として定められた形式に準拠することが推奨されているが、実際には各社が提供する情報によっては、必要な項目が欠落していたり、オプションの部分に独自の解釈が加えられることがある<br>

※ セキュリティ（脆弱性管理）に関する内容をSBOMの品質向上ガイドとしてどこまで書くかは後で調整することとして、とりあえず一通り書いていきます。

##### 5.4.2. 課題の詳細
<!-- 対象課題の現状と理想状態を簡潔に説明, 図示しても良い -->

ソフトウェアの脆弱性を早く網羅的に検出することは、SBOMを作成し管理する主要な目的の１つである。そのためには、SBOMにソフトウェアを構成するコンポーネントの識別情報が網羅的に記述されており、その識別情報と公的機関や民間企業などが提供している脆弱性情報のソフトウェア識別情報とを正確に照合できる必要がある。しかしながら、これらの実現を阻害する複数の要因がある。<br>
また、SBOMと脆弱性情報との照合によってそのSBOMが表すソフトウェアに脆弱性が検出された場合、そのソフトウェアは脆弱性を悪用したサイバー攻撃を受ける可能性がある。検出された脆弱性がどの程度悪用されやすいか、悪用された場合にどのような影響があるかによってリスクの程度が異なる。適切なリスク管理には、前述した網羅的な脆弱性の検出に加え、SBOMにおけるコンポーネント間の正確で網羅的な依存関係の記述も課題となる。<br>
（なお、脆弱性検出や影響推定の精度もリスク要因だが、ここでいうリスク管理の対象には含まない。）  

##### 5.4.3. 改善策
<!-- 問題解決のための具体的な対策（例：自動チェックツール導入、記述ルールの統一）-->
<!-- 改善策の実施手順の概要 -->

前述した課題に対する主な対策を列挙する。

- SBOMへのコンポーネント識別情報の網羅的記述
  1. コンポーネントの洗い出しと標準フォーマットに沿ったSBOMへの記述<br>
    - 十分にテストされコンポーネント検出の精度や制約が既知のSBOM生成ツールを用いる。
    - SBOMの作成には、可能ならばソフトウェアのビルド時にSBOMを生成するツールを用いる。ビルド時のSBOM生成が難しい場合はソースコードやバイナリコードからSBOMを生成する。<br>
      脆弱性管理の対象となるソフトウェアのコンポーネントは、ソフトウェア開発においてビルドされ運用環境で実行されるコンポーネント群になるため、ビルド前のソースコードにはあるがビルド後のバイナリには含まれないコンポーネントを除外し、逆にビルド時に外部から取り込まれるコンポーネントは含まれるようにしておくことが望ましい。
  2. コンポーネントの名前とバージョンを識別情報とする場合の記述<br>
    - NVDやJVNといった網羅性の高い脆弱性データベースでは脆弱性のあるソフトウェアの識別にCPE（Common Platform Enumaration）が用いられているため、SBOMの各コンポーネントにもCPEの記法に合わせて名前とバージョンを記述しておくのが良い。特に名前の中に空白がある場合はその空白をアンダースコア（_）に置き換え、バージョンはSemantic Versioningの記法で出来る限りマイナーバージョンやパッチバージョンまで記述する。
    - なお、CPEはNVD等の脆弱性データベースでソフトウェアパッケージの識別子に利用されているが、OSVなどの脆弱性データベースではCPEが用いられていない。利用する脆弱性データベースで使われているソフトウェア識別子の種類によって、名前などの表記方法が異なる可能性に留意する必要がある。
  3. コンポーネントのCPE名を識別情報とする場合の記述<br>
    - 最新のCPE Dictionaryに登録されている各コンポーネントのCPE名をソフトウェア識別子として記述する。<br>
      CPE名は同一のソフトウェアパッケージに対して複数登録されている場合があるため、その全てをSBOMに記述しておくのが良い。<br>
[CPE Dictionary] https://nvd.nist.gov/products/cpe 
    - CycloneDXにはコンポーネントの識別子としてCPEや後述のPURLをそれぞれ直接記述するための属性があり、SPDXではこれらを外部参照（SPDX v2.x）または外部識別子（SPDX v3.0）の値として記述する。
  4. コンポーネントのPURLを識別情報とする場合の記述<br>
    - ソフトウェア開発時に各コンポーネントのPURL（Package URL）またはSWIDを作成してSBOMに付与する。今後、SWIDがNVD等の主要な脆弱性データベースで採用される可能性は低いと見られており、PURLを優先的に検討すべきである。PURLからCPEへの変換に取り組むpurl2cpeプロジェクトもある。<br>
    [purl2cpe] https://github.com/scanoss/purl2cpe 
    - 脆弱性が発見された時に初めて作成されるCPE名に対して、PURLはソフトウェアが開発された時に作成できるため、脆弱性の発見を待つ必要がなく、現在一般的なパッケージマネージャを使ったソフトウェア開発においてPURLの自動生成が可能。逆に、パッケージマネージャを使っていない、または開発後のバイナリしかないソフトウェアについては、PURLの記述に必須のタイプ情報（パッケージマネージャ名）を書けない場合がある。<br>

- SBOMと脆弱性情報との正確な照合
  1. SBOM側の課題と改善策<br>
    - SBOMと脆弱性情報とを正確に照合するためにSBOM側で行なうべきことは、ほぼ上述したような識別情報の記述方法に集約される。
  2. 脆弱性情報側の課題と改善策
    - 脆弱性情報の側にも、SBOMに含まれるコンポーネントと正確に照合し、最新の脆弱性を漏れなく検出できるようにするためには、幾つかの課題がある。
    - CPE名の揺れ:<br>
    CPE名は、製品の種別、ベンダ名、製品名、バージョン、アップデート、エディション、言語で構成されるが、これらの要素の多くに表記揺れやCPE Dictionaryへの登録後に変更される可能性がある。変更されるケースとしては、誤りの修正のほかに製品やベンダのM&Aによってベンダ名が更新されることがある。なお、CPE名の更新は、登録済みのCPE名を変更ではなく新たCPE名として追加登録されるため、同じ製品に対してCPE名が複数存在することの一因となっている。<br>
    こうしたCPE名の変化・増加は将来に渡って行われる可能性があるため、登録済みのCPE名をSBOMに記述するだけでなく、SBOMと脆弱性情報のCPE名との照合時には曖昧照合のテクニックを用いてある程度の違いを吸収することも考慮すべきである。<br>
    また、こうした課題を持つCPE名の替わり、または補完のために、PURLとCPE名との対応づけを行なった上でSBOMにPURLがあれば利用することも考えられる。
    - CVEやCPEの登録の遅れ<br> : 企業やコミュニティからの早期情報収集

- SBOMへの依存関係の記述によるリスク管理強化
  1. 最上位コンポーネントの特定<br>
  SPDXではDESCRIBES関係の記述, CycloneDXではcomponent階層の最上位で表現する。
  2. コンポーネント間の包含関係の記述<br>
  SPDXではCONTAINS関係の記述, CycloneDXではcomponent階層で表現する。
  3. その他の依存関係の記述<br>
  SPDXでは上記のほかにも、関係は明確でないが依存していることが分かっている場合に「依存関係」（"depends on"）の記述が可能。あるコンポーネントの脆弱性や動作の不具合が、他のコンポーネントに影響することが判明している場合などに利用できる。<br>

  NTIAのSBOM最小要素およびOpenChain Telco SBOM Guideでは、コンポーネントの依存関係について上記のうち1.と2.が要件に含まれている。<br>
  多くのSBOM生成ツールではコンポーネント間の依存関係を出力するが、その正確さや網羅性はツールとソフトウェアによって様々である。NTIAのSBOM最小要素の要件を満たすことを求めているガイドラインやガイダンスに適合するためには、少なくとも上記1.と2.のタイプの依存関係が含まれていることを確認しておく必要がある。リスク管理の一環として、依存関係を用いて脆弱性の影響範囲を判断する場合は、あらかじめ依存関係が既知のソフトウェアで、利用するSBOM生成ツールの依存関係抽出精度を評価しておく。

##### 5.4.4. 評価方法
<!-- 改善効果を示す指標（例：チェックリストの項目とその達成率）-->
<!-- 定量・定性評価の実施方法と評価サイクル -->
（まだ書きかけ）<br>
- まずはSBOMのチェックツールでコンポーネント識別情報の記述方法に問題がないか確認。<br>
　（記述形式上の問題があると、脆弱性情報との照合ツールがSBOMを正しく読めない場合もある）
- 改善策を施したSBOMと脆弱性情報との照合を、なるべく出自の異なる多くのSBOMドキュメントと脆弱性情報で試行し、精度を確認しておく。これが、実際の運用においてSBOMを用いた脆弱性管理の有効性に対する期待値となる。

##### 5.4.5. リスクと留意事項
<!-- 改善策実施に伴うリスク、例外対応、補足事項 -->
（まだ書きかけ）<br>
- ソフトウェアの識別しにCPE名を用いる場合、前述したようにCPE Dictionary上ではその内容の誤りや最新状況に合わない部分があっても修正はされず、新たなCPE名の登録によって対処される。そのため・・・
- ソフトウェアの識別子にPURLを用いる場合、PURLではバージョンがオプションとなっているが、これがないと脆弱性情報との一意な対応付けができないため、PURLが自動生成される場合もSBOMの全てのコンポーネントのPURLに（SBOM自体のバージョン属性やCPEにも）バージョンが記載されていることを確認する。それでも、バージョン記述の揺れによる照合ミスのリスクは残ることに留意すべき。

#### 5.5 上流・下流間の情報統合と連携強化  
担当: 余保さん  
- ベンダーが提供するSBOMと組立メーカー内部のSBOMの整合性を確保するため、共通リポジトリの運用、定期的なクロスチェック、及び自動差分比較ツールの活用を推奨。

#### 5.6 改ざん検知と変更管理体制の構築  
担当: 平能さん  

##### 5.6.1. 課題の概要
- SBOM生成直後のデジタル署名やハッシュ値の付与、変更履歴管理、自動監視システムによる改ざん検知の仕組みを具体策として提示する。

##### 5.6.2. 課題の概要
SBOMは本来、ソフトウェアの構成要素や依存関係、既知の脆弱性などを正確に記述した重要ものである。しかし、以下のような理由でSBOMの真正性・完全性が損なわれるリスクがある。

- 手動での修正・補完に起因する入力ミスや意図しない変更。
- 複数ツールによる出力の差異やフォーマットの不整合。
- 改変によって重要な脆弱性情報が欠落し、セキュリティ評価が不十分となる。
- 改変履歴の管理がされていないことで信頼性の検証が困難になる。

##### 5.6.3. 改善策
SBOMの信頼性と改ざん耐性を確保するために、以下の改善策を導入する。

- デジタル署名の付与：SBOM生成直後に、デジタル署名またはハッシュ値を付与し、後の改変検知を可能にする。
- 改変履歴の管理：バージョン管理システムでSBOMファイルの変更履歴を記録・追跡する。
- 自動検証ツールの運用：署名やハッシュ値の整合性を自動でチェックするツールを導入。
- 自動監視システム：改ざん検知用プロセス整備を行い、定期的に署名検証を行い異常時にアラートを発出する。
- 更新・再配布ルールの整備：定期的なSBOMの更新と、その際の署名再付与と自動再配布の仕組みを明文化。
- 監査・チェック体制：定期的なレビュー、ログ監査、人による最終確認を補完的に実施。

##### 5.6.4. 評価方法

- 真正性の検証結果：デジタル署名やハッシュ値の整合性検証がパスしているか。
- 改変履歴の可視化：バージョン管理ツール上での差分履歴が明確に把握できるか。
- 監査ログの有無と内容の適切性：署名検証ログ、改ざんアラート履歴などが整備されているか。
- 自動監視の運用状況：定期的な自動検証ジョブの稼働状況および異常時の対応履歴の確認。

##### 5.6.5. リスクと留意事項

- 署名鍵の管理リスク：署名鍵や証明書の漏洩や期限切れに注意。適切な鍵管理と失効手順が必要。
- 運用負荷の増加：新たなプロセス導入に伴い、開発環境の変更やチーム内教育コストが発生。
- ツール間互換性の課題：異なるSBOMツールのフォーマット差異により、ハッシュ値や署名の一貫性が損なわれる可能性。
- 人手介入の余地の最小化：なるべく自動化することでヒューマンエラーを排除し、必要最小限の人手による検証に留める。

#### 5.7 記述範囲の明確化と責任所在の定義  
担当: 小保田  
- ソースコード、バイナリ、ファームウェア、ハードウェア情報など、SBOMに含める情報範囲を明確にするとともに、作成者（Creator）やパッケージ提供者（packageSupplier）など各責任所在を明示する。

#### 5.8 部品間関係性の統一的表現  
担当: 大和田さん  
- コンポーネント間の依存関係や関連性（例：dependsOn、contains、generates等）の統一的記述ルールを定義し、テンプレートおよび自動検証ツールによる整合性チェックの方法を明示する。  

#### 5.9 依存関係把握とパッケージ取得手法の問題
担当: 伊藤さん  

（まだ書きかけ）<br>

##### 5.9.1. 課題の概要

- ソースコードとパッケージ両方から依存関係を取得することで、重複や冗長な情報が混在し、全体の依存関係把握が難しくなる  
- ロックファイルやパッケージマネージャーのログだけで解析した場合、最新の依存関係や推移的な依存関係が完全に反映されない場合がある  
- 解析手法に統一性や自動化が不足しており、正確な依存関係抽出と整合性の維持に手動の補完が必要となっている

##### 5.9.2. 課題の詳細

- パッケージ間の依存関係は、一般に、パッケージをBuild/生成する際の、ソースコード、コンパイル情報から導き出される
- しかしながら、ソースコード、およびソースコードが参照するライブラリ群には、最終的に生成されるアプリケーションにおいては利用されない領域が存在し、それら利用されない領域への依存関係・利用されない領域から参照される依存関係、などを擬陽性として排除し、依存関係を軽量化することが一般に行われる
- 他方、パッケージマネジメントシステムが保有する依存関係は、当該のパッケージに含まれるソフトウェア全てが利用される前提で依存関係を管理することが期待されている
- 結果として、完璧な依存関係管理を実施した場合でも、最終アプリケーションを構成するソフトウェア情報・Build/生成情報を用いて生成する依存関係と、パッケージマネジメントシステムが保有する依存関係情報を統合することで得られる依存関係には、差異・過剰な記述、などが生じる余地が存在する

##### 5.9.3. 改善策
<!-- 問題解決のための具体的な対策（例：自動チェックツール導入、記述ルールの統一）-->
<!-- 改善策の実施手順の概要 -->
##### 5.9.4. 評価方法
<!-- 改善効果を示す指標（例：チェックリストの項目とその達成率）-->
<!-- 定量・定性評価の実施方法と評価サイクル -->
##### 5.9.5. リスクと留意事項
<!-- 改善策実施に伴うリスク、例外対応、補足事項 -->

#### 5.10 ツール間の連携性と柔軟性の不足  
担当: 濵さん  
- ORT（OSS Review Toolkit）などのツールは、デフォルト(ORT だと ScanCode)以外のスキャンツール（例：FOSSologyなど）も利用可能だが、切り替え方法など実際に試した例はほとんどなく、各ツールに互換性があるのかどうかが良く知られていない  
- ツール間での連携を強化するためのドキュメントやルールが不十分であり、ユーザー側で各ツールの特性を理解し調整する必要がある  

案：
SBOM解析エコシステムでは解析エンジンやフォーマットごとに仕様や出力形式が異なり、相互運用性が確立されていない。その結果、自動化パイプライン上での切り替えや結果統合時に手作業によるフォーマット変換やスキーマ調整を余儀なくされ、メンテナンスコストおよびヒューマンエラーリスクが増大している。
解決策としては、中間表現を介した標準化レイヤーを導入し、パイプライン全体で一貫したデータフローを確保する手法が有効である。さらに、切り替え手順を抽象化したフロー図やサンプル設定を揃え、自動検証ステップを組み込んだワークフローを採用することで、導入コストを低減しつつ柔軟性を向上させることが可能となる。


#### 5.11 ツールの保守・更新状況とコミュニティの連携
担当: 濵さん  
- 利用される一部ツールのメンテナやコントリビュータが足りておらず、メンテナンス状況が不十分  
- 商用ツールとの互換性や統一出力形式を実現するための標準ガイドラインや連携策が不足

案：
SBOM生成・解析ツールはプロジェクトごとに開発・メンテナンス状況が大きく異なり、リリース頻度やバグ修正対応にばらつきが見られる。そのため、利用者はバージョンアップ時の互換性確認やフォークメンテナンスに追われ、長期的安定運用が困難となる場合がある。
持続可能なエコシステムの構築には、リリースサイクルや貢献状況の可視化、多言語対応を含む貢献ガイドライン整備を進めることが不可欠である。また、利用者と開発者が定期的に意見交換できるフォーラムを設置し、相互のニーズを反映した標準化活動を推進することで、ツール全体の安定性と発展を担保できる。


#### 5.x ...

> **TBD: 6章を記載するかどうかについては、5章をまとめた後に議論する**  

> ### 6. 自動化戦略と運用プロセス  
> 本章では、SBOMの品質向上に寄与する自動化可能なプロセスと、さらに必要な人的レビューとの統合運用について述べる。
> 
> #### 6.1 自動検証ツールの導入  
> - 命名規則、バージョン形式、必須項目有無の自動チェックを実現するツールの選定と運用方針を策定。  
> 
> #### 6.2 変換プロセスと正規化  
> - 異なるフォーマットの一貫性を確保するための変換ツール及びデータ正規化プロセスの設計と運用手法を定義。
> 
> #### 6.3 運用負荷軽減と人的レビューの統合  
> - 初期の自動チェックに続き、例外ケースやあいまいな情報に対して人的レビューを組み合わせるハイブリッド運用フローの設計と導入方法を示す。

### 7. ガイドの運用と管理  
本章は、本ガイド自体の管理に焦点を当て、定期的な見直し、更新、および改訂履歴の管理プロセスについて記述。ここでは、SBOMそのものの運用ではなく、あくまで本SBOM品質向上ガイドの保守管理手法を記す。

#### 7.1 ガイド更新プロセス  
- 業界標準や自動化ツールの進展、及びユーザーフィードバックに基づき、本ガイドの定期レビューと改訂プロセスを策定。  
- 更新時の関係者間の調整手続きや承認プロセスも明確化。

#### 7.2 改訂履歴の管理と文書化  
- 各バージョンごとの変更内容、更新日、影響範囲を詳細に記録するための履歴管理方法と文書化のルールを定義します。  
- ガイド自身の真正性と透明性を維持するための管理策を含めます。

### 8. 参考文献・関連資料  
- [OpenChain-Telco-SBOM-Guide](https://github.com/OpenChain-Project/Telco-WG) に加え、SPDX、NTIA SBOM Minimum Elementsなどの国際規格および関連文献の参照先を掲載。

---

### Appendix-1. SBOM サンプル  

ここには、仕様上正しく、また実際に企業などで利用されている、値の内容まで含めた、JSON Formatで記述されたSBOMのサンプルファイルを記載する。  
SPDX 及び CycloneDX の仕様に詳しい人々にレビューをしてもらう必要がある。  

### Appendix-2. 5章の項目記載用テンプレート

ここに記載のあるテンプレートを用いて、5章の各項目を追加していく。  
ガイドにそれら項目を追加するべきかどうか、また記載内容そのものについて、GitHub Discussion もしくは Issues を起こし議論する。(TBD: 議論プロセス)  

#### 5.x [対象項目名]（例：5.1 情報記述の正確性および一貫性の確保）

##### 5.x.1. 課題の概要
- 対象課題の概要を簡潔に記述する  

##### 5.x.2. 課題の詳細
- 対象課題の詳細説明  
- 課題の背景や影響範囲の概要も記載する  
- 図などを埋め込んで説明しても良い

##### 5.x.3. 改善策
- 課題解決のための具体的な対策（例：自動チェックツール導入、記述ルールの統一、プロセスの定義など）  
- 改善策の実施手順

##### 5.x.4. 評価方法
- 改善効果を示す指標（例：自動チェックツールにより何をチェックするのか、またチェックリストの項目とその達成率を指標とする、など）  
- 定量・定性評価の実施方法と評価サイクル

##### 5.x.5. リスクと留意事項
- 改善策実施に伴うリスク、例外対応、補足事項
