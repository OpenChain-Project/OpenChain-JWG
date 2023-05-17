SPDX-License-Identifier: Community-Spec-1.0

# LiteLicensingClass

## Summary

LiteLicensingClass contains the minimum part for licensing.

## Description

LiteLicensingClass contains the minimum part for licensing.


## Metadata

- name: LiteLicensingClass
- SubclassOf: 
- Instantiability: Concrete

## Properties

- packageVersion
  - type: xsd:string
  - minCount: 0
  - maxCount: 1
- packageFilename
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
- concludedLicense
  - type: /Licensing/LicenseField
  - minCount: 0
  - maxCount: 1
- declaredLicense
  - type: /Licensing/LicenseField
  - minCount: 0
  - maxCount: 1
- licenseComment
  - type: xsd:string
  - minCount: 0
  - maxCount: 1
- copyrightText
  - type: xsd:string
  - minCount: 0
  - maxCount: 1
- packageComment
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

