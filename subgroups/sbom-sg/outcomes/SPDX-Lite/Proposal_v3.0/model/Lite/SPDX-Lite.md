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

NG
- /Core/Element  
  - /Core/ElementCollection  
    - /Core/Bundle  
      - /Core/Bom  
        - /Software/SBOM/creationInfo  
        * minCount: 1 (Originally minCount: 1 in Element class)  
OK
 - /Software/SBOM  
   - /Core/creationInfo  
     * minCount: 1 (Originally minCount: 1 in Element class)  

- /Software/SBOM/creationInfo <- /Core/Bom <- /Core/Bundle <- /Core/ElementCollection <- /Core/Element  
  * minCount: 1 (Originally minCount: 1 in Element class)  
- /Software/Package/spdxId  <- /Software/SoftwareArtifact <- /Core/Artifact <- /Core/Element  
  * minCount: 1 (Originally minCount: 1 in Element class)  
- /Software/Package/name <- /Software/SoftwareArtifact <- /Core/Artifact <- /Core/Element  
  * minCount: 1 (External properties restricted in Package class)  
- /Software/Package/comment <- /Software/SoftwareArtifact <- /Core/Artifact <- /Core/Element  
  * minCount: 1 (**if exists**)  
- /Software/Package/creationInfo <- /Software/SoftwareArtifact <- /Core/Artifact <- /Core/Element  
  * minCount: 1 (Originally minCount: 1 in Element class)  
- /Software/Package/suppliedBy <- /Software/SoftwareArtifact <- /Core/Artifact  
  * minCount: 1  
- /Software/Package/packageVersion  
  * minCount: 1  
- /Software/Package/downloadLocation  
  * minCount: 1  
- /Software/Package/homePage  
  * minCount: 1 (**if exists**)  
- /Software/Package/copyrightText <- /Software/SoftwareArtifact  
  * minCount: 1  

The following elements are used to represent relationships between software packages and to link between packages and licenses.

- /Core/Relationship/relationshipType
  * minCount: 1 (Originally minCount: 1 in Relationship class)  
- /Core/Relationship/from  
  * minCount: 1 (Originally minCount: 1 in Relationship class)  

The following elements are used to describe package licenses.  

- /SimpleLicensing/LicenseExpression/licenseExpression  
  * minCount: 1 (Originally minCount: 1 in LicensingExpression class)  
- /SimpleLicensing/SimpleLicensingText/liecnseText  
  * minCount: 1 (Originally minCount: 1 in SimpleLicensingText class)  

## EOF  
