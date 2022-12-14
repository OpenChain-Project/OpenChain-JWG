# LicenseInfo sg 2022/12/13

## Agenda  

- SBOM GuideBook  
- SBOM sg  
- Usage Profile  

## SBOM GuideBook  

 → 目次ドラフト共有済  
 - ガイドに追加・削除したほうが良いものは?  
   1. SBOMを何に使うのか、という章が欲しい。 - 伊藤  
   2. SPDX Liteなど、Prospectiveの説明を少し手厚くしたい。  
   3. SPDXとCycloneDXのコンパチビリティ、共通となるデータ項目なども含めるか?  
      → 現状、しっかり決まっていたり、わかっているものにフォーカスしたい。  
        こうしたい、こうあるべきという項目は含めない。  
   → その他、目次を見ていただき、Slack上で継続議論。  

## SBOM sg  

 - SBOM sgへの改名要望  
   背景: OSSJやOCSでセキュリティ観点からのSBOMが想定以上に進み始めている。  
        ライセンス観点だけからSPDXなどを議論しているだけではその進みに遅れる。  
        OpenSSFなど、他団体とのコラボレーションなどを含めて、SBOM議論を進める必要があるのでは?  
        また、LicenseInfoという名前だと、他団体とのコラボレーションが上手くいかない可能性があり、
        その為にも分かりやすい名前が必要なのではないか。
   → 方向性としては賛成。運営のやり方は考えたほうが良い。  
      伊藤さんだけでは、手が回らなくなると思われる。動ける人を当てる必要がある。他団体とのコミュニケーションも必要。  
      SBOM SG: Chair - co-Chair体制など。  
      範囲が広がること、他団体との連携が強くなることで、運営上の負荷分散を図りたいので、Co-Chairというタイトルなどのアサインをしたらどうか？  
      Discussion:  
      - Chairの交代まで考える?  
      - SBOM - Automationの合併まで考える?  
        3人 Chair 体制というのも考えられる。  
      Discussion 結果: 2022/12/13 決定 (反対意見の猶予 (期間決定せず) 有。Slack上にコメント下さい)  
      → SBOM sg に改名する  
      → AutomationとSBOMは分離したままとする。  
      → Chair: 小保田   
        co Chair: 伊藤、忍頂寺  

## Usage Profile  

 - SPDX mini summit での発表内容と議論  
   Build ProfileとUsage Profile間で議論が必要。  
   AI BOMは特に議論なく、説明だけされた。  
 - Build ProfileとUsage Profileについて、使い方が違うことは認識されたが、Tagなどが被っているので相互に議論が必要。  
 - Usage Profileの特定のTagの値として、one line stringという定義ではなくより厳しい形で実装出来ないのか?  
   Build Profile: Google Brian  
                  双方のProfileの理解と、Usage Profileをもう少し深く議論  
                  それらを経て、Build Profileと将来的に議論する  

EOF  
