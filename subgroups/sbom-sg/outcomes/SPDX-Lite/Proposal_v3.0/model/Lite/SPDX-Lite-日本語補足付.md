SPDX-License-Identifier: Community-Spec-1.0

# SPDX-Lite

## Summary

Everything having to do with SPDX-Lite.

## Description

The SPDX-Lite namespace defines concepts related to SPDX-Lite.

## Metadata

- id: https://rdf.spdx.org/v3/SPDX-Lite
- name: SPDX-Lite

## External properties restrictions  

**相談 1:** 
継承関係を含めて記載する。どれをminCount: 1とすべきか?  
スコープとして定義するけど、必須にはしない、という定義が必要。  

- /SBOM/creationInfo  
  * minCount: 1  
- /Software/File/name  
  * minCount: 1  
- /Software/Package/spdxId <- /Core/Element/spdxId  
  * minCount: 1  
    Element classで指定されている  
- /Software/Package/name <- /Core/Element/name  
  * minCount: 1  
    Package classで external properties restriction されている
- /Software/Package/comment <- /Core/Element/comment  
  * minCount: 1  
- /Software/Package/creationInfo <- /Core/Element/creationinfo  
  * minCount: 1  
    Element classで指定されている  
- /Software/Package/suppliedBy <- /Core/Artifact  
  * minCount: 1  
- /Software/Package/packageVersion  
  * minCount: 1  
- /Software/Package/downloadLocation  
  * minCount: 1  
- /Software/Package/homePage  
  * minCount: 1  
- /Software/Package/concludedLicense <- /Software/SoftwareArtifact/concludedLicense  
  * minCount: 1  
- /Software/Package/declaredLicense <- /Software/SoftwareArtifact/declaredLicense  
  * minCount: 1  
- /Software/Package/copyrightText <- /Software/SoftwareArtifact/copyrightText  
  * minCount: 1  

The following elements are what we want to use to describe licenses that does not have SPDX short identifier.  

- /Licensing/CustomLicense/spdxId <- /Core/Element/spdxId  
  * minCount: 1  
    Element classで指定されている  
- /Licensing/CustomLicense/name  <- /Core/Element/name  
  * minCount: 1  
- /Licensing/CustomLicense/comment  <- /Core/Element/comment  
  * minCount: 1  
- /Licensing/CustomLicense/licenseText <- /Licensing/License/licenseText  
  * minCount: 1  
    License classで指定されている  
  
The following elements are what we want to satisfy the NTIA minimum elements.  

- /Core/Relationship  
**相談 2:** 
  Vocablariesを制限したいが、それは別のprofileとしてPRする必要があるとの見解。その為、SPDX-Liteとしての提案としては Relationshipの
  ```  
  relationshipType
  type: RelationshipType
  minCount: 1
  maxCount: 1  
  ```  
  と、from/toを必須とするだけに留めるというPRにしてはどうか？
  <s>
  - Vocabularies  
    - contains  
    - describes  
  </s>