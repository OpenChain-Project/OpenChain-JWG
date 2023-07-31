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

- /Software/SBOM/creationInfo <- /Core/Element/creationInfo  
  * minCount: 1 (Originally minCount: 1 in Element class)  
- /Software/Package/spdxId  <- /Core/Element/spdxId  
  * minCount: 1 (Originally minCount: 1 in Element class)  
- /Software/Package/name <- /Core/Element/name  
  * minCount: 1 (External properties restricted in Package class)  
- /Software/Package/comment <- /Core/Element/comment  
  * minCount: 1  
- /Software/Package/creationInfo <- /Core/Element/creationinfo  
  * minCount: 1 (Originally minCount: 1 in Element class)  
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

- /Core/Relationship/relationshipType
  * minCount: 1 (Originally minCount: 1 in Relationship class)  
- /Core/Relationship/from  
  * minCount: 1 (Originally minCount: 1 in Relationship class)  

The following elements are what we want to use to describe licenses that does not have SPDX short identifier.  

- /ExpandedLicensing/CustomLicense ?

OR
- /SimpleLicensing/AnyLicenseInfo ?

## Questions  

We are not sure how to describe the following three points, so we'd like to ask SPDX community.  

1. Which class and element should be used to represent a license with or without an SPDX short ID?  
**It seems to reconfigure Licensing classes in [issue#399](https://github.com/spdx/spdx-3-model/pull/399).**  

2. How do we list the elements that need to be listed if they are present in the deliverable but not if they are not?  
For example, if there is a CustomLicense, it should be listed but not if there is none.  

3. When we receive an archived file of an OSS package, how should the file name be represented?  
For example, if we receive ```nginx``` ```v1.25.1``` in the file ```nginx-1.25.1.tar.gz```, ```Package/name == nginx``` and ```Package/packageVersion === 1.25.1```. So what classes and elements should be used in the file names passed in and how should they be associated with the package information?  

## EOF  
