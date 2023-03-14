# Usage Profile  

- Purpose  
  - JP
    サプライチェーンで受けわたる「パッケージ」「ディストリビューション」「Deriverables」それぞれについて、どのような条件でリリースされたのかを記載するための仕様。  
  - EN  
    TODO  

- Information we need to know  
  Ref: https://github.com/OpenChain-Project/OpenChain-JWG/blob/master/subgroups/sbom-sg/meetings/spdx-asia-telco/UsageProf-Usecase-20230110.pptx  
       page. 2  
  ```Product Maker must know ... ```  
  1. License Conditions  
     Declared or Concluded licenses  
  2. Intended Usage  
     Other outer reference documents.  
     ex. how to use this package.  
         DONT Distribute and debug only etc.  
  3. Build Conditions
     build config => refer build profile with ExternalRef  
  4. Test conditions  
     test profile? => refer xxx profile with ExternalRef  
  5. Valid until date, event  
     Indicates how long this material will be valid.
  6. CreationInformation (added in the discussion)  
     Who created this Usage Profile document?

- spdx-3-model
  クラス図だと思われます。  
  draw.io の UML templateを使わない理由がよくわかりませんが、一般的な図形を使って書いているので分かりにくい点があります。  
  また、まだ作業中のため間違っている点も多く、この図から最終的なドキュメントを把握しようとするのは至難の業。  
  → あまりとらわれず、あるべき姿を記述しましょう。  

// EOF  
