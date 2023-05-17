SPDX-License-Identifier: Community-Spec-1.0

# Lite

## Summary

Lite is a sbom that contains the mininum elements.

## Description

Lite is a sbom that contains the mininum elements.


## Metadata

- name: Lite
- SubclassOf: 
- Instantiability: Concrete

## Properties

- packageVersion
  - type: xsd:string
  - minCount: 0
  - maxCount: 1
- downloadLocation
  - type: xsd:anyURI
  - minCount: 0
  - maxCount: 1
- packageUrl
  - type: xsd:anyURI
  - minCount: 0
  - maxCount: 1
- homePage
  - type: xsd:anyURI
  - minCount: 0
  - maxCount: 1
- sourceInfo
  - type: xsd:string
  - minCount: 0
  - maxCount: 1
- concludedLicense
  - type: /Licensing/LicenseField
  - minCount: 0
  - maxCount: 1
- declaredLicense
  - type: /Licensing/LicenseField
  - minCount: 0
  - maxCount: 1
- copyrightText
  - type: xsd:string
  - minCount: 0
  - maxCount: 1
- licenseComment
  - type: xsd:string
  - minCount: 0
  - maxCount: 1
- licenseId
  - type: xsd:string
  - minCount: 1
  - maxCount: 1
- licenseName
  - type: xsd:string
  - minCount: 1
  - maxCount: 1
- licenseText
  - type: xsd:string
  - minCount: 1
  - maxCount: 1



## External properties restrictions

- /Core/Element/name
  - minCount: 1

