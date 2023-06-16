# Lite Profile requirements

## Our usage  

We want to define as a profile a collection of minimum elements that meet the following requirements:  

1. Use for open source license clearance  
2. NTIA minimum elements for a SBOM compliant  
3. Enable linking (or adding relationships) to elements used in security (defect) profiles  

## Nessesary Classes  

Classes we think is necessary based on the results of our research  

- Package (<- SoftwareArtifact <- Artifact <- Element)  
- License (<- ExtendableLicense(?) ) 
- Relationship (<- Element)

## mandatory elements  

The following elements are what we want to use to identify OSS packages and their licenses and copyright notices.  

- /Core/Element/spdxId  
- /Core/Element/name  
- /Core/Element/comment  
- /Core/Element/creationinfo  
- /Software/Package/packageVersion  
- /Software/Package/packageUrl  
- /Software/SoftwareArtifact/concludedLicense  
- /Software/SoftwareArtifact/declaredLicense  
- /Software/SoftwareArtifact/copyrightText  

The following elements are what we want to use to describe licenses that does not have SPDX short identifier.  

- /Licensing/License/licenseComment
  We intended [7.16 Comments on license](https://spdx.github.io/spdx-spec/v2.3/package-information/#7.16) at SPDX v2.3  
- /Licensing/License/licenseId  
- /Licensing/License/licenseName  
- /Licensing/License/licenseText  

The following elements are what we want to satisfy the NTIA minimum elements.  

- /Core/Relationship  
  - Vocabularies  
    - contains  
    - describes  

# EOF  
