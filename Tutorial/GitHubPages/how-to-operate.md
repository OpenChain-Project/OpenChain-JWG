# Github Pages運用について

## Github Pagesとして公開されるWebページについて

https://github.com/OpenChain-Project/Onboarding-JWG/tree/master/docs  
以下に存在するmarkdownファイルを修正し、commit/pushすることによって、Webサイト  
https://openchain-project.github.io/Onboarding-JWG/  
として公開されます。  
なお更新は、push後、最大1分程度待たされる場合があります。  

## branchの運用について

gitflowなど様々な方法論がありますが、慣れてない方も多いと思いますので、**master branchのみ**でいきましょう。慣れている方々は、どのようなbranching modelを採用して作業していただいても構いませんが、リポジトリ内に存在する不要なbranchは定期的に削除しましょう。  
**PRを送る方々は、上記リポジトリのmaster branchに対してsend pr**してください。  
**mergeの方法なども**色々ありますが、commit logの内容含めて**気にしない**こととします。write権以上を持つ方は、ローカルで作業後prしてmergeするもよし、web上で編集するもよしのゆるゆる運用です。  
但し、masterのみでの運用ですので、**cherry pickしてpush -f!とかはやめましょう**。  

## リポジトリ管理者へのお願い

- merge権限を持つ方を、サブグループ毎に1名は登録し管理しましょう。  
※ サブグループページへのmerge requestが来た時に、各サブグループ毎に判断できるように。  
管理方法は、```Settings → Manage access```だけで運用するか、maintenance dir等を作成、管理者listなどを作るか、決めましょう。  
- 【提案】wikiからの移設が一段落したら、リポジトリを整理しましょう  
Japan-WG-GeneralのコンテンツをOnboarding-JWGに移動し、各ディレクトリを整理しましょう。更に可能であれば他国のWGに倣って、Onboarding-JWGをOpenChain-JWGに改名しましょう。  

## 今後のイベント / Upcoming Eventsの更新について

- docs/upcoming-events.md  
- subgroups/{FAQ,education,leaflet,licensing,planning,promotion,tooling}/upcoming-events.md  

上記のファイル内に、何か記載するとトップページの今後のイベントに追加されますので、イベント日時等が決まり次第、更新していってください。なお、**GFM markdownとして正しくないと、正常に表示されない**のでご注意ください。  
例: リスト(箇条書き)は、改行する(最後に2個のスペースを入れる)こと  

## JWG全般の情報更新について  

- 誰がメンテナンスしていく?  
  promotion sg? planning sg?

- 利用ファイル群  
必要に応じて追加していってください。  
   - index.md : Github Pages 日本語トップページ
   - index_en.md : Github Pages 英語トップページ
   - meeting-minutes.md : 全体会合の記録 日本語
   - meeting-minutes_en.md : 全体会合の記録 英語
   - outcomes.md : 成果物一覧 日本語
   - outcomes_en.md : 成果物一覧 英語

## 各サブグループへのお願い

- **merge権限を持つ方を1名以上選出**してください。  
- docs/subgroups/以下のmarkdownファイルが、サブグループサイトです。必要に応じて更新してください。  
- wikiのmediaに存在するサブグループに関係するファイルを、
   > https://wiki.linuxfoundation.org/openchain/openchain-japanese-working-group?do=media&ns=openchain  

   Githubの以下のフォルダ  
  > https://github.com/OpenChain-Project/Onboarding-JWG/tree/master/subgroups  

  に移動してください。  

- サブグループのイベント予定の公開をお願いします。  
  **今後のイベント / Upcoming Eventsの更新について**にも記載しましたが、  
  > https://github.com/OpenChain-Project/Onboarding-JWG/tree/master/subgroups/{サブグループ名}/  
  以下の、upcoming-events.md  

  を定期的に更新、commit/pushしてください。

EOF
