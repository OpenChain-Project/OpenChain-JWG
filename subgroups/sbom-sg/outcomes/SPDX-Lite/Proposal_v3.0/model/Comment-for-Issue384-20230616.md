# Lite Profile requirements

## Our usage  

We want to define as a profile a collection of mandatory elements that meet the following requirements:  

1. Able to use for open source license clearance  
2. NTIA minimum elements for a SBOM compliant  

## Nessesary Classes  

Classes we think is necessary based on the results of our research  

- Package (<- SoftwareArtifact <- Artifact <- Element)  
- License (<- ExtendableLicense(?) <- Element(?) )  
- LicenseAddition (<- Element)  
- CustomLicense (<- License <- ExtendableLicense(?) <- Element(?) ) 
- CustomLicenseAddition (<- LicenseAddition <- Element)  
- Relationship (<- Element)  

## Required elements  

The following elements are what we want to use to identify OSS packages and their licenses and copyright notices.  

- /Software/Package/spdxId <- /Core/Element/spdxId  
  * minCount:1 at Element class  
- /Software/Package/name <- /Core/Element/name  
  * minCount:1 used external restriction at Package class  
- /Software/Package/comment <- /Core/Element/comment  
  * XXX  
- /Software/Package/creationInfo <- /Core/Element/creationinfo  
  * minCount:1 at Element class  
- /Software/Package/suppliedBy <- /Core/Artifact  
  * XXX  
- /Software/Package/packageVersion  
  * XXX
- /Software/Package/packageUrl  
  * XXX
- /Software/Package/concludedLicense <- /Software/SoftwareArtifact/concludedLicense  
  * XXX  
- /Software/Package/declaredLicense <- /Software/SoftwareArtifact/declaredLicense  
  * XXX  
- /Software/Package/copyrightText <- /Software/SoftwareArtifact/copyrightText  
  * XXX  

The following elements are what we want to use to describe licenses that does not have SPDX short identifier.  

- /Licensing/CustomLicense/spdxId <- /Core/Element/spdxId  
  * minCount:1 at Element class  
- /Licensing/CustomLicense/name  <- /Core/Element/name  
  * XXX  
- /Licensing/CustomLicense/licenseText <- /Licensing/License/licenseText  
  * minCount:1 at License class
- /Licensing/CustomLicenseAddition/spdxId  <- /Core/Element/spdxId  
  * minCount:1 at Element class  
- /Licensing/CustomLicenseAddition/name <- /Core/Element/name  
  * XXX  
- /Licensing/CustomLicenseAddition/additionText <- /Licensing/LicenseAddition/additionText  
  * minCount:1 at LicenseAddition class  
  
The following elements are what we want to satisfy the NTIA minimum elements.  
To avoid complex operations, we want to limit vocabularies.  

- /Core/Relationship  
  - Vocabularies  
    - contains  
    - describes  

# EOF  
