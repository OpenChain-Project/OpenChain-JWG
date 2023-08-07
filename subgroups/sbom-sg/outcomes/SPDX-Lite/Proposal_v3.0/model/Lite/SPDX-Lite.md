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

## Issues  

Not sure how to describe the following four points. We'd like to discuss with SPDX community.  

1. Which class and element should be used to represent a license with or without an SPDX short ID?  
**It seems to reconfigure Licensing classes in [issue#399](https://github.com/spdx/spdx-3-model/pull/399).**  

2. Do we need to list external properties restriction at profile-level.md that already have minCount:1 specified?

3. How should we write ```CustomLicense``` information if we want it to be required if it exists and not required if it does not exist?  

4. How should we handle the packageFileName in SPDX2.3 when we receive an archived file of an OSS package?  
For example, if we receive ```nginx``` ```v1.25.1``` in the file ```nginx-1.25.1.tar.gz```, ```Package/name == nginx``` and ```Package/packageVersion === 1.25.1```. We have to to use Relationship with ```File``` to represent packageFileName.  
**This topic appears to be discussed in [issue#83](https://github.com/spdx/spdx-3-model/issues/83).**  

## EOF  
