# SBOM sg  

## SPDX history and v3.0 details  

### やること  

1. SPDX v1.0は全てのTagの内容と意図などを調査、記載する。  
   それ以降のバージョンは、前のバージョンから何が追加削除変更されたかの履歴、それぞれのTagの内容と意図を調査、記載する。  
2. SPDX v3.0については、仕様が日々大きく変わっているため、調査した日付もしくは対象としたspdx-3-model repositoryのcommit idを記載しておく。  
3. SPDX v3.0 については、各プロファイル毎に分けますが数多くのクラスが分かりにくくなっているので、
   まずは1名で担当、調査が難しいことが分かった場合には、複数回に分ける or 何名かで調査していくなどの報告をする。  

-> Tagの歴史を追うだけにする?
-> 最初はSPDXのoverviewの粒度で変化を見ていくのはどうか?
   1. 大きくは何が追加削除されたか、構造が変わった部分。
      -> v1.0 -> v2.3まではこれを調べて資料化する。★ → 3か月くらいで纏めたい  
         小泉さん、小保田  
         
   2. 細かくはタグや値の変化

### 担当  

以下、それぞれリリースページの該当Tagから調査  
参照: https://github.com/spdx/spdx-spec/tags  

1. v1.0  
2. v1.1  
3. v1.2  
4. v2.0  
5. v2.1  
6. v2.1.1  
7. v2.2  
8. v2.2.1-ISO-final + v2.2.1-ISO-submittal  
   ※ 差分があるか無いか分からないので纏めました。大きく差分があった場合は分けて調査しましょう。  
9. v2.2.1  
10. v2.2.2  
11. v2.3  
    
12. v2.3 - CycloneDX v1.4との比較 ★ → ~~すぐ纏まるんじゃないかと思ってる  ~~
    忍頂寺(〆切は相談)  

--- 並行して
13. v3.0では非常に大きく変更されたので、どのように変わったかをまずは纏める ★ → 遅くとも4月末までにまとめたい  
    -> 難易度が高い、表現の仕方、資料の作り方にセンスが必要  
       SPDX Liteのメンテ(プロファイル作成)ともリンクする  
       - 福地(Lite部分)、伊藤、當麻  

14. v3.0 Core  
15. v3.0 Software  
16. v3.0 Licensing  
17. v3.0 Security  
18. v3.0 Build  
19. v3.0 AI  

- 追加議論  
  CycloneDXもバージョンごとに調査する?  

### Usage Profile

https://github.com/yoshi-i/spdx-3-model にて議論。  
Google docsで提案前最終版  
https://docs.google.com/document/d/1gvcU3Qgs5IH_SbVoeYLt1PSwuTgEX3RTr6CEcUQ6hXc/edit#heading=h.x8df7ykvzy8o

→ 3/7の週にドラフト json or class図っぽいものを kobota が作るので、Slack上で議論させてください。  
