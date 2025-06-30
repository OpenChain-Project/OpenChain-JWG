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

本文書 "SBOM Document Quality Guide" は、サプライチェーンの中での関係者の共通理解を形成するためのドキュメントです。SBOMの標準化、正確性、透明性、及び自動化の可能性を高めるための改善策を提示します。

サプライチェーンの関係者がソフトウェア部品表（SBOM：Software Bill of Materials）を作成・提供・利用する場合に共通課題となる点について改善策を提案することにより、SBOM流通時の障壁を取り除くための助けとなります。

本ガイドは、本ガイドに適合するエンティティに対して、OpenChain （OpenChain Specificationのどのバージョンでも）を採用することを要求するものではありませんが、OpenChainを採用することが大いに推奨されることに留意ください。

このガイドは、ソフトウェアパッケージ、コンテナ、SaaS、組込みソフトウェアなど、あらゆるSBOM生成及び運用における対象プロセスに適応することを前提に記述されています。本ガイドが参照するのは個々のSBOMであり、SBOMを提供するエンティティではありません。
本ガイドに沿ったSBOMを「SBOM Document Quality Guide Compatible」と呼ぶことができます。

本ガイドの要件に一致するSBOMをリリースすることは、同じソフトウェアのSBOMを別の方法または形式で配信することを妨げるものではありません。

本ガイドは Creative Commons Attribution License 4.0 (CC-BY-4.0)の下にライセンスされています。(Comment:ライセンスはこれでいい?)

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
<!--
[OpenChain Telco SBOM Guide Version 1.1の 4. 適合通知](https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_JP.md#4-%E9%81%A9%E5%90%88%E9%80%9A%E7%9F%A5) を継承。  

> ```OpenChain SBOM Document Quality Guide v1.0``` とドキュメント名を修正して記載
> 分量も少ないので他を担当している方でも重複して担当可能  

担当: [富田]
-->

ソフトウェアがSBOMに適合していることを示すために、以下の記述を使用してもよい：

"このソフトウェアは、OpenChain SBOM Document Quality Guide v1.0 に準拠したSBOMとともに提供される。このガイドは、[https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/outcomes/QualityGuide/SBOM-Document-Quality-Guide.en.md](https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/outcomes/QualityGuide/SBOM-Document-Quality-Guide.en.md)で入手できる。"

"このSBOMはOpenChain SBOM Document Quality ガイドv1.0（[https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/outcomes/QualityGuide/SBOM-Document-Quality-Guide-TOC.en.md](https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/outcomes/QualityGuide/SBOM-Document-Quality-Guide.en.md)） に準拠しており、受領者には無償で提供される。受領者は、対応するソフトウェアを頒布するいかなる第三者に対しても、当該第三者にソフトウェアを頒布するために必要なすべての権利を有することを条件に、このSBOMを自由に再頒布することができる。"

また、ソフトウェアベンダーや通信システムサプライヤーにRFP、購買発注、受託開発発注を依頼する場合、RFP文書、発注文書、契約文書の記載事項として、以下の文を使用してもよい：

"ソフトウェアをリリースする場合、リリースされるすべてのソフトウェアについて、OpenChain SBOM Document Quality Guide v1.0 に準拠したSBOMを提供することを要求する。 このガイドは"[https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/outcomes/QualityGuide/SBOM-Document-Quality-Guide.en.md](https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/outcomes/QualityGuide/SBOM-Document-Quality-Guide.en.md)"で入手できる。"

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
異なる企業やツール間において、パッケージ名、バージョン、供給者名などの情報が一貫せず表現されるという課題が存在する。記述内容に関する統一された基準が欠如しているため、SBOMの自動解析や脆弱性との照合が困難となり、結果として正確な処理が妨げられる事態が生じる。  

##### 5.1.2. 課題の詳細  
多くのSBOMガイドラインでは、記載すべき内容を示すキーが明示され、対応する値も定められているものの、これら値の具体的な書式が定義されていないケースが多く、実際の運用において問題が発生する可能性がある。  

例えば、以下の2つのSBOMでは、パッケージ名の記載方法が異なっており、一方は「hello」、もう一方は「hello 0.0.1」となっている。この不一致は、使用されたツールの出力形式の違いに起因するものである。  

- [example7-bin.spdx.json](https://github.com/spdx/spdx-examples/blob/master/software/example7/spdx2.2/example7-bin.spdx.json#L44)  
  "name": "hello"  
- [hello-dist.spdx.json](https://github.com/spdx/spdx-examples/blob/master/software/example12/spdx2.2/hello-dist.spdx.json#L56)  
  "name": "hello 0.0.1"  

これらが同一パッケージであることは、例えば ExternalRef や components の identifier として purl 等を用いて比較すれば確認可能ではあるが、各ツールが同一のキーに対して異なる値を出力するケースが多くみられるため、SBOM管理の円滑な運用に支障を来す恐れがある。  

##### 5.1.3. 改善策  
- purl など一意にパッケージを特定可能な値を記載することをソフトウェアサプライチェーン上関係する組織間で合意する。  
- 業界標準や社内ルールに基づいた統一表記ルールを策定し、具体例（正規表現などのフォーマット例）をソフトウェアサプライチェーン上関係する組織間で広く共有する。  
- 検証ツールをソフトウェアサプライチェーン関係組織間で共有、パッケージの特定に必要かつ表記が揺れがちな以下の項目について、ルールに準拠しているかをチェックする仕組みを構築する。  
  - パッケージ名  
  - パッケージバージョン  
  - パッケージサプライヤー名  
  - パッケージの取得元  
  - purlの記載有無  

##### 5.1.4. 評価方法  
- 各記述項目が統一表記ルールに沿って記載されているかをランダムにチェックし、合格率を評価する。  

##### 5.1.5. リスクと留意事項  
- 記述ルールの設定が不十分であったり複雑な場合、例外ケースや特殊な記述への対応が不完全になり、誤判定するリスクがある。  
- ルールが現場実態と乖離している場合、不足または過度なチェックが発生、誤判定するリスクがある。  
- ツールやプロセスは完全な自動化が難しく、最終的なチェックや例外対応は人的レビューが必要となる点について留意する必要がある。  

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
各SBOMのコンポーネントの粒度の違いにより異なる対応が必要になるということから、コンポーネントの粒度ががわからないと対応が難しくなる。
この例のように単純なサプライチェーンの場合は、SBOMに粒度の情報がなくても別の手段で確認することはできそうであるが、さらにサプライチェーンが複雑になるとSBOM自身に粒度の情報が必要となる。

##### 5.2.3. 改善策

サプライチェーンの中で粒度が統一できるのであれば問題はない。
統一できない場合は、コンポーネントの粒度がわかるようになっていて、粒度に合わせた対応ができないと問題になる可能性がある。
SBOMの交換フォーマットの仕様によりパッケージとファイルの違いはわかるようになっているので現実的に問題になる状況は少ないと思われる。
フォーマットの仕様に依存しない方法でコンポーネントの粒度の違いがわかるようになっていることが望ましいと考える。

##### 5.2.4. 評価方法

最終商品のSBOMを作成するために外部から受け取ったり、内部で作成したりした複数のSBOMについてこの粒度の違いがあるのかを判別できること。

##### 5.2.5. リスクと留意事項

コンポーネントの粒度の違いをSBOMの表記上では解決できたとしても、実際に脆弱性情報と紐づけるときに問題が起きるのではないか。
例えば、コンポーネントの粒度がファイル単位の情報が混ざっている場合に、脆弱性情報とのマッピングが手間なくできるのかという懸念がある。


#### 5.3 ソース情報の補完と透明性向上  
担当: 武山さん
- バイナリ提供時にもソースファイル一覧、ハッシュ値、ライセンス情報など補完すべき情報を必須項目化するなど、自動抽出プロセスを導入する方針を示す。

#### 5.4 脆弱性管理及びセキュリティリスク管理の強化  
担当: 細見さん  
<!-- （細見）セクションのタイトルにあった「脆弱性連携」という言葉があまりポピュラーでないことと内容が限定的に思われたため、「脆弱性管理」に変更しています -->

##### 5.4.1. 課題の概要
SBOMを利用した、ソフトウェア製品のコンポーネント単位での脆弱性管理やセキュリティリスク管理の強化が期待されている。そのためには、SBOMに次のような情報が正確かつ網羅的に記載されていることが重要となるが、いずれも容易とは言い難い。
1. 各コンポーネントの脆弱性の有無を知るために脆弱性情報と照合できる識別情報
2. 見つかった脆弱性の報告や対処を依頼するための該当コンポーネントの提供者情報
3. その脆弱性が他のコンポーネントに及ぼす影響を知るためのコンポーネント間の依存関係
4. その脆弱性がソフトウェア製品に及ぼす影響の有無や状態を記したセキュリティアドバイザリ

##### 5.4.2. 課題の詳細
<!-- 対象課題の現状と理想状態を簡潔に説明, 図示しても良い -->
SBOMの中で脆弱性管理およびセキュリティリスク管理に利用される情報には、それぞれ次のような課題がある。
1. コンポーネントの識別情報にコンポーネントの名前とバージョンを使用する場合、5.1.2節で例示されたような名前の表記揺れが生じ、脆弱性の検出漏れに繋がる。PURLやCPE名などの一意な識別子を記載しても、照合先の脆弱性データベースが対応していない場合がある。
2. 特にツールで生成されるSBOMの提供者情報は、記載されていない、一般に知られていない略称や提供者ではない文字列が記載されている、連絡用アドレスがないなど、問合せに利用できない場合がある。
3. ツールの種類や設定、またはソフトウェア製品の開発言語や開発環境によって、コンポーネント間の依存関係が取得できない場合がある。
4. セキュリティアドバイザリの標準的な記述形式としてCSAFやVEXがあるものの、まだあまり普及しておらず、対応しているツールも少ない。

| |
|---|
|このあたりに、SBOMと脆弱性情報との突合〜リスク管理の大まかなフロー図を入れようかと|
| |

##### 5.4.3. 改善策
<!-- 問題解決のための具体的な対策（例：自動チェックツール導入、記述ルールの統一）-->
<!-- 改善策の実施手順の概要 -->

上述の各課題は、それぞれ次のような対応により改善することができる。

1. OSV[^OSV]やNVD[^NVD]など、利用する脆弱性データベースに登録されているソフトウェアの名前や同様の表記方法を用いてコンポーネントの名前を記述する。または、それぞれの脆弱性データベースに採用されているソフトウェア識別子を記載する（例えばOSVならばPURL、NVDならばCPE名）。
2. コンポーネントの提供者情報には、実在し且つ公開されている組織や個人の名前、および有効なE-mailアドレスやURLなどの問合せ先情報を記載する。
3. パッケージマネージャからコンポーネント間の依存関係を取得できるツールを利用し、依存関係を含んだSBOMを生成する。
4. 見つかった脆弱性が影響するコンポーネントやその影響状態を記したVEXの情報がある場合は、SBOMに外部参照情報として記載する。フォーマットが対応していればSBOMとVEXを同じドキュメントに記載してもよい。[^VEX]

[^OSV]: A distributed vulnerability database for Open Source, https://osv.dev
[^NVD]: National Vulnerability Database, https://nvd.nist.gov
[^VEX]: Vulnerability Exploitability eXchange, CycloneDX v1.4以降やSPDX v3.0以降ではそれぞれのフォーマットでSBOMとVEXの情報を１つのドキュメントとして記述可能

<!--
前述した各課題への基本的な対応方法は次の通り。

1. 脆弱性情報と精度良く照合するためのコンポーネント情報の記述<br>
    次のいずれかをSBOMのコンポーネントごとに記述しておく。
   - コンポーネントの名前とバージョンを適切に記述
     - SBOMの基本的な情報であるコンポーネントの名前とバージョンを適切に記述しておくことによって、様々な脆弱性情報との照合が可能になる。
   - コンポーネントのCPE名を記述
     - CPE（Common Platform Enumeration）記法で書かれた識別子（CPE名）をSBOMのコンポーネント情報の１つとして記述する。CPE名を記述しておくことにより、NVDなどの網羅性の高い脆弱性データベースと直接照合できる。
   - コンポーネントのPURLを記述
     - CPE名と同様に、PURL（Package URL）をSBOMのコンポーネント情報の１つとして記述する。PURLは、
CPE名に比べて表記揺れの可能性が低く、ソフトウェア開発時にSBOMへ網羅的に付与しておくことができる。

2. 脆弱性の影響範囲を調べるために有効なコンポーネント間の依存関係の記述<br>
    NTIAの"SBOMの最小要素"やOpenChain Telco SBOM Guideの要件からも、脆弱性の影響範囲特定に有効な情報として、SBOMに少なくとも次の2種類の依存関係を記述しておく。
   - SBOMを構成する最上位コンポーネントの記述<br>
  SPDXではSBOMドキュメントと最上位パッケージとのDESCRIBES関係で記述し、CycloneDXではcomponent階層の最上位で表現する。
   - コンポーネント間の包含関係の記述<br>
  SPDXではパッケージ間のCONTAINS関係で記述し、CycloneDXではcomponent階層で表現する。

3. 適切なリスク管理<br>
    ソフトウェアに関するサイバーセキュリティの基本的なリスク管理では、下記のような指標を用いた「攻撃を受ける可能性の高さ」と「影響の大きさ」の積でリスクを評価し、これをできるだけ小さい状態に維持する。<br>
   - 攻撃を受ける可能性の高さ：脆弱性の有無と深刻度
   - 影響の大きさ：脆弱性のあるコンポーネント自体やこれに依存している他のコンポーネントが停止または掌握された場合の被害の程度

    コンポーネント毎の脆弱性の有無とコンポーネント間の依存関係は、前述の1.と2.を用いて把握することができる。脆弱性の深刻度には、脆弱性データベースに記録されているCVSS（脆弱性の深刻度スコア）やEPSS（脆弱性が悪用される確率）などが使える。
    被害の程度は、実際の被害額を正確に見積もることが難しいため、３段階ほどのレベルを設定することが多い。<br>
    新たな脆弱性が見つかった場合、評価したリスクが大きい場合は即時対応を優先し、リスクが小さい場合は事業継続性やコストを考慮して優先度を判断する。
-->

<!-- 
リスク管理では脆弱性データベースに登録されている様々な情報を利用してリスク分析を行なうが、セキュリティアドバイザリに関する内容（VEX等）をSBOMとは独立に記述するというポリシーの下ではSBOMに対する要件は限られているため、このガイドでは詳しく述べないこととした。
-->

##### 5.4.4. 評価方法
<!-- 改善効果を示す指標（例：チェックリストの項目とその達成率）-->
<!-- 定量・定性評価の実施方法と評価サイクル -->
上記それぞれの改善策については、次のような評価方法が考えられる。

1. コンポーネントの識別情報と脆弱性情報との照合精度の評価
- SBOMのデータフォーマットに対応した検証ツールでコンポーネントの識別情報の記述形式に問題がないことを確認する。
- SBOMのコンポーネント識別情報と脆弱性情報との照合を、なるべく作成者や作成ツールが異なる多くのSBOMドキュメントと脆弱性情報で試行し、精度を確認する。精度は、適合率（正確さ）のほか、可能であれば再現率（網羅性）も計測し、実用的な期待値となっているかを確認する。

2. コンポーネントの提供者情報
- SBOM生成ツールから出力されたコンポーネントの提供者情報についても、その組織名や個人名、連絡先の情報が存在するかどうかを、Web検索などによって確認する。

3. コンポーネント間の依存関係の精度評価とセキュリティアドバイザリの調査
- 依存関係も、コンポーネントの識別情報と同様に期待値としての精度を評価しておくと良い。SBOM生成ツールにおいて、パッケージマネージャを用いた依存関係抽出では高い精度を期待できるが、コード解析による抽出では誤検出や検出漏れの可能性がある。<br>
- VEXは、まだ限られた一部のソフトウェアベンダーが提供している程度だが、セキュリティリスク管理に有用な情報であるため、ベンダーのセキュリティ情報サイトなどで確認しておく。

##### 5.4.5. リスクと留意事項
<!-- 改善策実施に伴うリスク、例外対応、補足事項 -->
それぞれの改善策には、次のようなリスクがあることに留意しておく。

1. 脆弱性情報と照合するためのコンポーネントの識別情報について
  - 脆弱性情報との照合にコンポーネントの名前とバージョンを用いる場合、脆弱性情報に記載されているソフトウェアの名前の表記方法は、脆弱性情報の種類によって若干異なる場合がある。また、ツールから出力されたコンポーネントの名前にも表記揺れが生じうる（5.1節参照）。
  - 脆弱性情報との照合にコンポーネントのPURLを利用できる脆弱性データベースは、現状では一部に限られている（OSVはPURLに対応、NVDは未対応）。
  - いずれかのコンポーネントの実行時に動的に読み込まれるようなコンポーネントの情報はSBOMに記述されていない場合がある。
<!-- また、PURLではバージョンがオプションとなっているが、これがないと脆弱性情報との一意な対応付けができないため、PURLが自動生成される場合もSBOMの全てのコンポーネントのPURLに（SBOM自体のバージョン属性やCPEにも）バージョンが記載されていることを確認する。それでも、バージョン記述の揺れによる照合ミスのリスクは残ることに留意すべき。-->

2. コンポーネントの提供者情報について
  - コンポーネントの名前と同様に、提供者名も表記揺れによって一貫性が保たれない場合がある（5.1節参照）。
  - コンポーネント（パッケージ）の提供者は、企業の買収や事業停止、個人の都合などによって、開発やサポートが停止していたり他者へ移っている場合がある。SBOMにEOL/EOS情報があるかの確認、アップデートや問い合わせ対応などの状況を見ておくことも、リスク管理の一環となる。

3. コンポーネント間の依存関係とセキュリティアドバイザリについて
  - SBOMに記述されたコンポーネント間の依存関係は、実際に動作しているソフトウェアにおける依存関係とは必ずしも一致しない。その理由としては、依存関係抽出の精度不足のほか、上記のコンポーネント情報と同様に動的に読み込まれるコンポーネントに関する依存関係が記述されていない場合や、逆にソフトウェアの実行時に一部のコンポーネントが利用されない場合などがある。
  - 膨大な数のコンポーネントで構成されたソフトウェアでは同時に大量の脆弱性が検出される場合がある一方、その大半に即時の対応を要するケースは少なく、適切なトリアージが必要である。しかし、まだ大半のコンポーネントについてVEXのような定型で機械可読なセキュリティアドバイザリが提供されていない現状では、脆弱性の影響有無や対処手段を一括で取得し管理することが容易でないため、過去に判断を保留したものを含めて見落としが無いか注意する必要がある。


#### 5.5 上流・下流間の情報統合と連携強化  
担当: 余保さん  
- ベンダーが提供するSBOMと組立メーカー内部のSBOMの整合性を確保するため、共通リポジトリの運用、定期的なクロスチェック、及び自動差分比較ツールの活用を推奨。

#### 5.6 改ざん検知と変更管理体制の構築  
担当: 平能さん  

##### 5.6.1. 課題の概要
SBOMの運用においては、ソフトウェアの更新とは異なるタイミングでSBOMが更新されることがある。また、SBOMの記述内容に誤りが含まれる可能性もある。
しかし現状では、SBOMそのものが改変されたことを検出する仕組みが十分に整っておらず、ソフトウェアとの整合性を保証することが困難である。

##### 5.6.2. 課題の詳細

- 手動修正による情報の不整合：SBOMに対して後から人手で内容を修正・補完する運用がある場合、元のソフトウェア構成と一致しない内容になってしまうことがある。たとえば、不要なコンポーネント情報を加筆してしまうなど、意図しない改変が混入するリスクがある。

- バージョン管理の未導入による改変履歴の不透明化：SBOMの内容が変更されたとしても、それが記録される仕組み（バージョン管理）がない場合、誰が・いつ・なぜ・どのように内容を変更したのかが追跡できず、意図的な改ざんと単なる更新の区別がつかない。また、過去のSBOMに戻すこともできないため、信頼性が著しく低下する。

- フォーマットの不統一と情報の欠落：複数のツールでSBOMが自動生成された場合に、形式や記述内容の違いから、統合や編集時に依存関係など一部の情報が抜け落ちるリスクがある。これにより、SBOMを基に行うセキュリティ評価が不完全となる恐れがある。

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

##### 5.8.1. 課題の概要
- コンポーネント間の依存関係や関連性（例：dependsOn、contains、generates等）の統一的記述ルールを定義し、テンプレートおよび自動検証ツールによる整合性チェックの方法を明示する。  

##### 5.8.2. 課題の詳細
- コンポーネント間の関係性の記述表記は非常に多くあり、どの表記を選択するかが人によって異なる
- 同じ関係性に対して複数の表記がある
- 同じ表記が複数の関係性に使われる
- そのため、SBOMを提供者と受領者で表記が異なり、効果的な利用を妨げてしまう

##### 5.8.3. 改善策
- 一般的な関係性について、標準となる表記を提案し、表記のブレが少なくなることを促す
- 等価な関係性表記を標準的な表記に置き換えるツールや複数の関係性に使われる表記を見つけるツールを用意する
- 標準となる表記の提案 [SPDX / CycloneDX]
  - コンポーネントの現在の状態を記述するもの
    - contains/composition-assemblies：～を含む（構成される）
    - dependsOn/composition-dependencies：～に依存する（を必要とする）
  - コンポーネントの由来を記述するもの
    - generatedFrom*：components-pedigree：～生成された（複製された、改変された、ビルドされた）[* SPDX のVocabulariesには存在しない]
- 【参考１】[SPDX Specification Version 3.0.1 relationshipType](https://spdx.github.io/spdx-spec/v3.0.1/model/Core/Vocabularies/RelationshipType/)分類
  - コンポーネントの現在の状態を記述するもの
    - ～を含む（構成される）
      - contains: The from Element contains each to Element.
      - expandsTo: The from archive expands out as an artifact described by each to Element.
    - ～に依存する（を必要とする）
      - dependsOn: The from Element depends on each to Element, during a LifecycleScopeType period.
      - hasDynamicLink: The from Element dynamically links in each to Element, during a LifecycleScopeType period.
      - hasOptionalDependency: The from Element optionally depends on each to Element, during a LifecycleScopeType period.
      - hasProvidedDependency: The from Element has a dependency on each to Element, dependency is not in the distributed artifact, but assumed to be provided, during a LifecycleScopeType period.
      - hasStaticLink: The from Element statically links in each to Element, during a LifecycleScopeType period.
      - invokedBy: The from Element was invoked by the to Agent, during a LifecycleScopeType period (for example, a Build element that describes a build step).
    - その他の状態
      - hasConcludedLicense: The from SoftwareArtifact is concluded by the SPDX data creator to be governed by each to license.
      - hasDeclaredLicense: The from SoftwareArtifact was discovered to actually contain each to license, for example as detected by use of automated tooling.
      - hasDependencyManifest: The from Element has manifest files that contain dependency information in each to Element.
      - hasDistributionArtifact: The from Element is distributed as an artifact in each to Element (e.g. an RPM or archive file).
      - hasDocumentation: The from Element is documented by each to Element.
      - hasMetadata: Every to Element is metadata about the from Element (from hasMetadata to).
      - hasOptionalComponent: Every to Element is an optional component of the from Element (from         - hasOptionalComponent to).
      - hasPrerequisite: The from Element has a prerequisite on each to Element, during a LifecycleScopeType period.
      - hasRequirement: The from Element has a requirement on each to Element, during a LifecycleScopeType period.
      - hasSpecification: Every to Element is a specification for the from Element (from hasSpecification to), during a LifecycleScopeType period.
  - コンポーネントの由来を記述するもの
    - ～生成された（複製された、改変された、ビルドされた）
      - amendedBy: The from Element is amended by each to Element.
      - availableFrom: The from Element is available from the additional supplier described by each to Element.
      - configures: The from Element is a configuration applied to each to Element, during a LifecycleScopeType period.
      - coordinatedBy: The from Vulnerability is coordinatedBy the to Agent(s) (vendor, researcher, or consumer agent).
      - copiedTo: The from Element has been copied to each to Element.
      - delegatedTo: The from Agent is delegating an action to the Agent of the to Relationship (which must be of type invokedBy), during a LifecycleScopeType (e.g. the to invokedBy Relationship is being done on behalf of from).
      - generates: The from Element generates each to Element.
      - hasInput: The from Build has each to Element as an input, during a LifecycleScopeType period.
      - hasOutput: The from Build element generates each to Element as an output, during a LifecycleScopeType period.
      - hasVariant: Every to Element is a variant the from Element (from hasVariant to).
      - packagedBy: Every to Element is a packaged instance of the from Element (from packagedBy to).
      - patchedBy: Every to Element is a patch for the from Element (from patchedBy to).
    - ～と加工された
      - hasAddedFile: Every to Element is a file added to the from Element (from hasAddedFile to).
      - hasDeletedFile: Every to Element is a file deleted from the from Element (from hasDeletedFile to).
    - 生成・加工の環境
      - hasHost: The from Build was run on the to Element during a LifecycleScopeType period (e.g. the host that the build runs on).
      - hasTest: Every to Element is a test artifact for the from Element (from hasTest to), during a LifecycleScopeType period.
      - hasTestCase: Every to Element is a test case for the from Element (from hasTestCase to).
      - modifiedBy: The from Element is modified by each to Element.
      - testedOn: The from Element has been tested on the to Element(s).
      - trainedOn: The from Element has been trained on the to Element(s).
      - usesTool: The from Element uses each to Element as a tool, during a LifecycleScopeType period.
  - 脆弱性関連
      - affects: The from Vulnerability affects each to Element. The use of the affects type is constrained to VexAffectedVulnAssessmentRelationship classed relationships.
      - doesNotAffect: The from Vulnerability has no impact on each to Element. The use of the doesNotAffect is constrained to VexNotAffectedVulnAssessmentRelationship classed relationships.
      - exploitCreatedBy: The from Vulnerability has had an exploit created against it by each to Agent.
      - fixedBy: Designates a from Vulnerability has been fixed by the to Agent(s).
      - fixedIn: A from Vulnerability has been fixed in each to Element. The use of the fixedIn type is constrained to VexFixedVulnAssessmentRelationship classed relationships.
      - foundBy: Designates a from Vulnerability was originally discovered by the to Agent(s).
      - hasAssessmentFor: Relates a from Vulnerability and each to Element with a security assessment. To be used with VulnAssessmentRelationship types.
      - hasAssociatedVulnerability: Used to associate a from Artifact with each to Vulnerability.
      - publishedBy: Designates a from Vulnerability was made available for public use or reference by each to Agent.
      - reportedBy: Designates a from Vulnerability was first reported to a project, vendor, or tracking database for formal identification by each to Agent.
      - republishedBy: Designates a from Vulnerability's details were tracked, aggregated, and/or enriched to improve context (i.e. NVD) by each to Agent.
      - underInvestigationFor: The from Vulnerability impact is being investigated for each to Element. The use of the underInvestigationFor type is constrained to VexUnderInvestigationVulnAssessmentRelationship classed relationships.
  - 未分類
      - ancestorOf: The from Element is an ancestor of each to Element.
      - descendantOf: The from Element is a descendant of each to Element.
      - describes: The from Element describes each to Element. To denote the root(s) of a tree of elements in a collection, the rootElement property should be used.
      - hasDataFile: The from Element treats each to Element as a data file. A data file is an artifact that stores data required or optional for the from Element's functionality. A data file can be a database file, an index file, a log file, an AI model file, a calibration data file, a temporary file, a backup file, and more. For AI training dataset, test dataset, test artifact, configuration data, build input data, and build output data, please consider using the more specific relationship types: trainedOn, testedOn, hasTest, configures, hasInput, and hasOutput, respectively. This relationship does not imply dependency.
      - hasEvidence: Every to Element is considered as evidence for the from Element (from hasEvidence to).
      - hasExample: Every to Element is an example for the from Element (from hasExample to).
      - other: Every to Element is related to the from Element where the relationship type is not described by any of the SPDX relationship types (this relationship is directionless).
      - serializedInArtifact: The from SpdxDocument can be found in a serialized form in each to Artifact.
- 【参考２】[CycloneDX v1.6 JSON](https://cyclonedx.org/docs/1.6/json/)におけるコンポーネント間関係性の記載方法
  - [componentsの中にcomponents](https://cyclonedx.org/docs/1.6/json/#components_items_components)を階層的に記述することで内部構造を示す
  - [componentsの中のpedigree](https://cyclonedx.org/docs/1.6/json/#components_items_pedigree)によって、created, distributed, modified, redistributed, combined等を記述する
  - components間の依存関係については、[dependencies](https://cyclonedx.org/docs/1.6/json/#dependencies)で記述する
    - [記述例](https://cyclonedx.org/use-cases/compositions-dependencies/)
  - もう一つのcomponents間の関係の記述方法として[composition](https://cyclonedx.org/docs/1.6/json/#compositions)がある
    - compositionの中の[assemblies](https://cyclonedx.org/docs/1.6/json/#compositions_items_assemblies)によって構成要素の列挙や、[dependencies](https://cyclonedx.org/docs/1.6/json/#compositions_items_dependencies)によって依存関係を記述する
    - assembliesやdependenciesの情報の完全性の状態を[aggregate](https://cyclonedx.org/docs/1.6/json/#compositions_items_aggregate)で示す
    - [記述例](https://cyclonedx.org/use-cases/compositions-dependencies/)


##### 5.8.4. 評価方法
- ツールによる修正量や検出量を評価指標とする

##### 5.8.5. リスクと留意事項
- プログラム言語やビルド手法、ソフトウェアの管理手法の進化に伴い、新たな関係性が生まれ、標準と定めた表記では適切な表現ができなくなる可能性がある
- その点を鑑み、厳格な運用ではなく、自由度のある対応を可能とする形とする方が良い 

#### 5.9 依存関係把握とパッケージ取得手法の問題
担当: 伊藤さん  

（まだ書きかけ）<br>

##### 5.9.1. 課題の概要

- コンポーネント間の依存関係は、パッケージ生成時に想定されるすべての利用事例に対応した記述がなされるべきである
  - ライブラリパッケージなどのような事例では、サプライチェーン下流で一部関数が使用されない可能性がある場合でも、パッケージに含まれるすべてのソフトウェアについてコンポーネント間の依存関係や関連性を記述する必要がある
- アプリケーションBuild時など、Build時に用意したパッケージに存在しても、生成されるオブジェクトファイルに含まれないソフトウェアが存在するなど、パッケージ内容の取捨選択が行われた場合、SBOM記述としては生成結果に含まれるコンポーネントに絞り込まれた記述となることが望ましい
  - 脆弱性情報などとの突合せにより、該当・非該当を判断する場合、呼び出されないコード、含まれないデータなどに対して、擬陽性を示すことを抑止するために、SBOM記述と生成されたオブジェクトファイルの内容を合致させる必要がある

##### 5.9.2. 課題の詳細

- パッケージの内容によっては、SBOMに記述される依存関係が、パッケージをサプライチェーン内で授受する場合やパッケージのセットを汎用ディストリビューションとして授受する時点での記述内容と、同パッケージを用いてアプリケーションソフトウェアをBuildする際、アプリケーションソフトウェアとしての実行時、クラウド環境などにおけるサービス提供タイミングなど、それぞれの時点で変化し得ることを前提にしなければならない
  - パッケージの生成段階と利用段階それぞれにおける依存関係
    - 汎用のソフトウェア部品として生成されたパッケージには、パッケージを受け取った側が利用しないソフトウェアが含まれ得る
    - パッケージを受け取った側が、そのパッケージを用いてアプリケーションソフトウェアなどを生成する場合、Buildオプション・リンク情報など追加定義を与えることが一般的であるため、依存関係に変化が生じ得る
    - ダイナミックリンク機構あるいはアプリケーションソフトウェアがPlug Inとして外部バイナリを取り込む機構を持つ場合、さらには複数のアプリケーションが密接に通信処理を実施しながら一体となってサービスを提供する場合、など、実処理段階で依存関係に変化が生じる場合も存在する
  - パッケージ生成ツールのSBOM品質
    - パッケージ生成ツール・パッケージマネジメントシステムが保有する依存関係は、当該のパッケージに含まれるソフトウェア全てが利用される前提で依存関係を管理することが期待されているが、パッケージ内の構成に依っては循環参照などが生じたとしても、そのまま依存関係を記述されることとなり、後段の解析において障害となりうる
    - パッケージ生成ツールは、ソースコードを解析して依存関係を導出するかは、ツールに依存し、場合によってはソースコード以外の開発者が与えたドキュメント情報を引き写しているだけである可能性がある
    - パッケージ・パッケージに付随するSBOMを受け取った側が、ソースコードとパッケージ両方から依存関係を取得することで、重複や冗長な情報が混在し、全体の依存関係把握が難しくなる
  - パッケージ受領者による依存関係の確認
    - 前述のように、脆弱性情報などとの突合せを考慮すると、依存関係についてアプリケーションソフトウェアの構成、動的な依存関係の把握を、パッケージに同梱されている依存関係記述とは別個に取得することが望ましい
    - SBOMを受け取った側が、SBOMに記載された依存関係を検証する際、実際にパッケージを用いているアプリケーションソフトウェアの構成に正確に沿った検証を行うことが望ましく、そのためには、パッケージ生成時だけではなくアプリケーションソフトウェア生成時のBuildオプションなどを反映することが望ましい
    - 解析手法に統一性や自動化が不足しており、正確な依存関係抽出と整合性の維持に手動の補完が必要となっている
    - 複数のパッケージに含まれる各ライブラリと、アプリケーションプログラムを生成するBuildシステム、相互でSBOM情報を取得・再生成できる構成となっていなければ、生成されるオブジェクトファイルに対する正確なコンポーネント情報、コンポーネント間の依存情報が生成できない
    - アプリケーションソフトウェアとして生成されたオブジェクトファイルに対するSBOMと、動的にリンクを行うダイナミックリンクライブラリ、動的にパッケージを読み込むPlug-inなどの各パッケージが提供するSBOM情報を、アプリケーションソフトウェアの実稼働に即して正確に再構成しなければ、情報の欠落が生じ得る

- ロックファイルやパッケージマネージャーのログだけで解析した場合、最新の依存関係や推移的な依存関係が完全に反映されない場合がある  
- パッケージ間の依存関係は、一般に、パッケージをBuild/生成する際の、ソースコード、コンパイル情報から導き出される
- しかしながら、ソースコード、およびソースコードが参照するライブラリ群には、最終的に生成されるアプリケーションにおいては利用されない領域が存在し、それら利用されない領域への依存関係・利用されない領域から参照される依存関係、などを擬陽性として排除し、依存関係を軽量化することが一般に行われる
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

追記案：（作り手　、受け手）分けて書く。

#### SBOM提供者向け

SBOMを生成する際には，使用する解析エンジンやフォーマットを明確に定義し，一貫した出力仕様を維持することが不可欠である。異なる形式が混在すると，受け取り側において中間表現を介する変換が必要になり，自社の自動化パイプラインに組み込む際に手作業によるスキーマ調整が発生する。その結果，メンテナンス工数が増大し，ヒューマンエラーのリスクも高まるため，まずは自社内部で利用する標準フォーマットを一本化し，必要に応じて中間表現への変換モジュールを整備しておくべきである。

さらに，提供するSBOMに関する切り替え手順や設定例を抽象化したドキュメントを用意し，サンプル設定ファイルやフロー図として公開しておくことで，導入事業者の負担を軽減できる。これにより，異なる解析エンジン間での互換性を担保すると同時に，自社製品が他のツールとスムーズに連携しやすい環境を整備し，SBOM提供者としての信頼性を向上させることが可能となる。

#### SBOM受け取り者向け

SBOMを消費する立場では，受領したファイルが複数の形式やスキーマにまたがっている場合，中間表現を介して一元的に解析できる仕組みを構築しておく必要がある。各提供者が独自仕様で出力したSBOMをそのまま取り込むと，自動化パイプラインの中で手動によるフォーマット変換やスキーマ調整が不可避となり，結果として通知遅延や解析漏れの原因となる。そこで，受け取り側でも最初に中間モデルを設計し，各フォーマットからそこへ変換するモジュールを揃えることで，パイプライン全体の一貫性を担保できる。

また，受領したSBOMが想定通りの内容になっているかを自動検証するステップを組み込むことが重要である。抽象化されたフロー図やサンプル設定を参考に，解析エンジン切り替え時のテストケースを事前に準備しておくことで，導入コストを抑えつつ，解析結果の信頼性を向上させられる。こうした仕組みをあらかじめ整備することで，多種多様な提供元からのSBOMを効率的に統合・活用できるようになる。



#### 5.11 ツールの保守・更新状況とコミュニティの連携
担当: 濵さん  
- 利用される一部ツールのメンテナやコントリビュータが足りておらず、メンテナンス状況が不十分  
- 商用ツールとの互換性や統一出力形式を実現するための標準ガイドラインや連携策が不足

案：
SBOM生成・解析ツールはプロジェクトごとに開発・メンテナンス状況が大きく異なり、リリース頻度やバグ修正対応にばらつきが見られる。そのため、利用者はバージョンアップ時の互換性確認やフォークメンテナンスに追われ、長期的安定運用が困難となる場合がある。
持続可能なエコシステムの構築には、リリースサイクルや貢献状況の可視化、多言語対応を含む貢献ガイドライン整備を進めることが不可欠である。また、利用者と開発者が定期的に意見交換できるフォーラムを設置し、相互のニーズを反映した標準化活動を推進することで、ツール全体の安定性と発展を担保できる。

追記案：（作り手　、受け手）分けて書く。

#### SBOM提供者向け

SBOM提供者は、使用する解析ツールの最新安定版やLTS情報、リリースサイクルを明示し、脆弱性対応のタイムラインを文書化することで、受け取り側が更新計画を立てやすくする。また、過去バージョンのサポート期間と終了予定を併記し、リスク評価を助けることが重要である。さらに、SBOMフォーマットやスキーマ変更の影響を示す互換性保証策と簡潔な移行ガイドを提供し、受け取り者がバージョン間の差異を把握できるようにする。加えて、バグ報告や要望を受け付けるチャネル（Issue管理や定例会議）を整備し、メンテナンス状況を継続的に共有することで、エコシステム全体の信頼性向上を図る。

#### SBOM受け取り者向け

生成・解析ツール間のメンテナンス状況にばらつきがあるため、受け取り者は事前に各プロジェクトのリリーススケジュールやIssue対応状況を把握し、バージョン更新時にはテスト環境で互換性検証を行うべきである。加えて、コミュニティ参加を通じて課題や要望をフィードバックし、標準化議論に関与することで、自社に最適な運用ノウハウを獲得し、エコシステム全体の安定性に寄与できる。


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

### Appendix-1. SBOM交換用フォーマット仕様に合わせた解説

ここには、SPDXやCycloneDXの仕様に合わせた場合の解説を記述する。
必要な場合、仕様上正しく、また実際に企業などで利用されている、値の内容まで含めた、JSON Formatで記述されたSBOMのサンプルファイルを記載する。  
SPDX 及び CycloneDX の仕様に詳しい人々にレビューをしてもらう必要がある。  

#### Appendix-1.2. コンポーネント粒度の標準化と正規化

##### Appendix-1.2.1. 粒度の判別方法

「5.2 コンポーネント粒度の標準化と正規化」の評価方法で記述した、コンポーネントの粒度の違いについて実際の交換用フォーマット仕様で判別可能かを確認した。

- SPDX 2.3
  - relationshipsで、relationshipTypeがDEPENDS_ONやDEPENDENCY_OFになっているspdxElementIdとrelatedSpdxElementのSPDXIDからそのコンポーネントがパッケージかファイルかの判別ができる。

- SPDX 3.0.1
  - RelationshipクラスのfromとtoにあるElementのSPDXIDからそのコンポーネントがパッケージかファイルかの判別ができる。

- CycloneDX 1.6
  - dependenciesのrefとdependsOnに記述するbom-refのelment idからコンポーネントがパッケージかファイルかの判別ができる。

##### Appendix-1.2.2. サンプル

> パッケージとファイルの依存関係それぞれのサンプルが必要か?
> とはいっても SPDXIDとbom-refのIDが変わるだけなので代り映えしない
> 各フォーマットの課題があるのであればそこまで踏み込む?

- SPDX 2.3

- SPDX 3.0.1

- CycloneDX 1.6


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
