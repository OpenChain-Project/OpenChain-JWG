# Lite Profile requirements

## Our usage  

We want to define a profile as a collection of required elements that meet the following requirements:  

1. Able to use for open source license clearance  
2. NTIA minimum elements for a SBOM compliant  

## Nessesary Classes  

Nessesary Classes we think:

- Package (<- SoftwareArtifact <- Artifact <- Element)  
- CustomLicense (<- License <- ExtendableLicense(?) <- Element(?) ) 
- Relationship (<- Element)  

## Required elements  

**We want the place represented by X to be minCount: 1.**

The following elements are what we want to use to identify OSS packages and their licenses and copyright notices.  

- /Software/Package/spdxId <- /Core/Element/spdxId  
  * minCount:1 at Element class  
- /Software/Package/name <- /Core/Element/name  
  * minCount:1 using external restriction at Package class  
- /Software/Package/comment <- /Core/Element/comment  
  * X  
- /Software/Package/creationInfo <- /Core/Element/creationinfo  
  * minCount:1 at Element class  
- /Software/Package/suppliedBy <- /Core/Artifact  
  * X  
- /Software/Package/packageVersion  
  * X
- /Software/Package/downloadLocation  
  * X  
- /Software/Package/homePage  
  * X  
- /Software/Package/concludedLicense <- /Software/SoftwareArtifact/concludedLicense  
  * X  
- /Software/Package/declaredLicense <- /Software/SoftwareArtifact/declaredLicense  
  * X  
- /Software/Package/copyrightText <- /Software/SoftwareArtifact/copyrightText  
  * X  

The following elements are what we want to use to describe licenses that does not have SPDX short identifier.  

- /Licensing/CustomLicense/spdxId <- /Core/Element/spdxId  
  * minCount:1 at Element class  
- /Licensing/CustomLicense/name  <- /Core/Element/name  
  * X  
- /Licensing/CustomLicense/comment  <- /Core/Element/comment  
  * X  
- /Licensing/CustomLicense/licenseText <- /Licensing/License/licenseText  
  * minCount:1 at License class
  
The following elements are what we want to satisfy the NTIA minimum elements.  

- /Core/Relationship  
  - Vocabularies  
    - contains  
    - describes  

# EOF  
