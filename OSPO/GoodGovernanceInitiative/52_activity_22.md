## ソフトウェアの脆弱性を管理する

GitLabの問題へのリンク: <https://gitlab.ow2.org/ggi/ggi-castalia/-/issues/22>。

### 説明

コードは最も安全性の低い部分と同じくらい安全です。最近の事例(例: heartbleed[^heartbleed]、 equifax[^equifax])では、企業が直接開発したものではないコード部分の脆弱性をチェックすることの重要性が示されている。データ漏えい (評判に大きな影響を与える) からランサムウェア攻撃、ビジネスを脅かすサービスの利用不能まで、さまざまなリスクにさらされている。

オープンソースソフトウェアは、プロプライエタリなソフトウェアよりも脆弱性管理に優れていることが知られているが、その主な理由は以下のとおりである。
* オープンなコードやプロセスの問題を見つけて修正しようとする目が増えています。
* オープンソースプロジェクトは、脆弱性を修正し、パッチや新バージョンをはるかに迅速にリリースする。

例えば、プロプライエタリなソフトウェアに関する[WhiteSourceによる調査](https://resources.whitesourcesoftware.com/blog-whitesource/3-reasons-why-open-source-is-safer-than-commercial-software)では、オープンソースコンポーネントに見つかった脆弱性の95%が、分析の時点ですでに修正プログラムをリリースしていたことが示されているという。したがって、問題は、コードベースとその依存関係の両方の脆弱性を、閉じているかオープンソースであるかに関係なく、より適切に管理することです。

これらのリスクを軽減するには、ソフトウェア資産の評価プログラムを設定し、脆弱性チェックプロセスを定期的に実行する必要があります。影響を受けるチームに警告し、既知の脆弱性を管理し、ソフトウェア依存関係による脅威を防止するツールを実装します。

### オポチュニティの評価

ソフトウェアを使用する企業は、以下の点で脆弱性を監視する必要があります。
* インフラ(クラウドインフラストラクチャ、ネットワークインフラストラクチャ、データストアなど)
* そのビジネス・アプリケーション(人事、CRMツール、社内および顧客関連のデータ管理)
* 社内コード (会社のWebサイト、社内開発プロジェクトなど)
* すべての直接的および間接的なソフトウェアとサービスの依存関係。

何か悪いことが起こるまで、脆弱性のROIはほとんどわからない。脆弱性の本当のコストを見積もるには、大規模なデータ侵害やサービスの利用不能の影響を考慮する必要があります。

同様に、企業内のセキュリティ関連の問題のために秘密を守り、隠れるという文化も、何としてでも避けなければならない。そうではなく、脆弱性の状態に関する情報を共有し、開発者からCレベルの幹部まで、適切な人々から最善の答えを見つけるために議論する必要がある。

ソフトウェアの脆弱性を慎重に管理することで、サイバー攻撃を防ぐ利点は数多くあります。
* 風評リスクを回避し、
* 搾取の損失を避ける(DDoS、ランサムウェア、攻撃後の代替ITシステムの再構築時間)。
* データ保護規制を遵守します。

OSSソフトウェアの脆弱性を管理することは、組織内のシステムとサービスのセキュリティにグローバルに取り組む、より大きなサイバーセキュリティプロセスの一部にすぎません。

### 進捗評価

脆弱性と開発者が信頼できる使いやすいプロセスを監視する専任の人員またはチームが必要です。脆弱性評価は、継続的インテグレーションプロセスの標準的な部分であり、専用のダッシュボードでリスクの現在の状態を監視できます。

次の**検証ポイント**は、このアクティビティの進捗状況を示しています。
- [ ] 社内のすべてのソフトウェアとサービスが評価され、既知の脆弱性がないか監視されている場合は、アクティビティが対象になります。
- [ ] 日常の開発ルーチンに問題が発生しないように、専用のツールとプロセスがソフトウェア生産チェーンに実装されている場合は、アクティビティがカバーされます。
- [ ] 個人またはチームは、暴露に対するCVE/脆弱性リスクを評価する責任がある。
- [ ] 個人またはチームは、関係者(SysOps、DevOps、開発者など。)にCVE/脆弱性を配布する責任があります。

### ツール

* GitHubツール
  - GitHubは、プラットフォームでホストされているコードをセキュリティで保護するためのガイドラインとツールを提供します。詳細については、[GitHub docs](https://docs.github.com/en/github/administering-a-repository/about-securing-your-repository)を参照してください。
  - GitHubは、依存関係の脆弱性を自動的に特定する[Dependabot](https://docs.github.com/en/github/managing-security-vulnerabilities/about-alerts-for-vulnerable-dependencies)を提供している。
* [Eclipse Steady](https://eclipse.github.io/steady/)は無料のオープンソースツールで、JavaやPythonのプロジェクトの脆弱性を分析し、開発者が脆弱性を緩和できるように支援する。
* [OWASP dependency-check](https://owasp.org/www-project-dependency-check/): オープンソースの脆弱性スキャナー。
* [OSS Review Toolkit](https://github.com/oss-review-toolkit/ort): は、オープンソースのオーケストレータであり、設定された脆弱性データサービスから、使用されている依存関係に関するセキュリティアドバイザリを収集することができる。

### リソース

* CVEの[MITRE's vulnerability database (MITREの脆弱性データベース)](https://cve.mitre.org/) 。NVDの[NISTのセキュリティデータベース](https://nvd.nist.gov/)、および[CVEの詳細](https://www.cvedetails.com/)などの衛星リソースも参照してください。
* Googleの新しいイニシアチブ、[open source Vulnerabilities](https://osv.dev/)もチェックしてみてください。
* OWASPワーキンググループは、商用とオープンソースの両方の世界から、脆弱性スキャナーのリストを[彼らのウェブサイト](https://owasp.org/www-community/Vulnerability_Scanning_Tools)に公開しています。
* J. WilliamsとA.Dabirsiaghi。2012年の安全でない図書館の不幸な現実。
* [オープンソース依存関係における脆弱性の検出、評価、緩和](https://link.springer.com/article/10.1007/s10664-020-09830-x)、Serena Elisa Ponta、Henrik Plate&Antonino Sabetta、Empirical Software Engineering volume 25、ページ3175-3215 (2020) 。
* [オープンソース・ソフトウェアの脆弱性に対する修正の手動キュレーションデータセット](https://arxiv.org/abs/1902.02595)、Serena E.Ponta、Henrik Plate、Antonino Sabetta、Michele Bezzi、Cedric Dangremont。また、[前述のデータセットを実装するための、開発中のツールキット](https://sap.github.io/project-kb/)もあります。

[^heartbleed]: https://fr.wikipedia.org/wiki/Heartbleed
[^equifax]: https://arstechnica.com/information-technology/2017/09/massive-equifax-breach-caused-by-failure-to-patch-two-month-old-bug/
