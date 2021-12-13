# ML管理者用メモ


## 1. 管理者画面へのログイン

パスワードを入手したら、Webブラウザから管理者画面にログインしてください。

### 1.1 管理者の操作が必要な保留案件がない場合

Openchain-japan-wg-xxx Administrative Database

という画面が表示されます。この画面の、

Openchain-japan-wg-xxx administrative interface (requires authorization)

のリンクをクリックすることにより、管理者用画面に遷移します。

### 1.2 管理者の操作が必要な保留案件がある場合

その案件の内容と、操作のためのインタフェース (ボタン等) が表示されます。
その内容は多くの場合、管理者の承認が必要なため保留されている、新規の加入申請やメッセージなどです。

## 2. 初期設定

### 2.1 Language options

管理者用画面の Language options のリンクから、加入者が選択できる言語を設定できます。
初期状態ではEnglish (USA)のみが有効になっているので、Japaneseにチェックを入れてから、
画面下の "Submit Your Changes" ボタンを押します。(必要があれば他の言語もどうぞ)

### 2.2 Digest options

管理者用画面の Digest options のリンクをクリックして Digest options 画面に入ります。
"Can list members choose to receive list traffic bunched in digests?" において、"No" の
ラジオボタンを選択して、画面下の "Submit Your Changes" ボタンを押します。

これは、Digest メッセージにおいて日本語が文字化けする問題があり、文字化けの解決策が
わからなかったため、加入者がDigestの配信を選択できないようにするための処置です。

### 2.3 メッセージサイズの最大値

管理者用画面の General Options の画面において、
"Maximum length in kilobytes (KB) of a message body. Use 0 for no limit." の値を調整します。
ここで設定した値を超えたサイズのメッセージは、管理者が承認しなければMLに転送されません。
初期値は小さな値が設定されていて、頻繁に管理者による対応が必要になるので、10000とか、
適当に大きな値を設定します。0を設定すると、無制限にできます。

### 2.4 メッセージのsubjectに付加されるprefix

General Options画面 画面で、"Prefix for subject line of list postings." を設定できます。
運用開始後に変更するとややこしいので、短くしたいなら最初に変更しておいたほうが良いでしょう。

