SPDX-License-Identifier: Community-Spec-1.0

# License

## Summary

Abstract class for the portion of an AnyLicenseInfo representing a license.

## Description

A License represents a license text, whether listed on the SPDX License List
(ListedLicense) or defined by an SPDX data creator (CustomLicense).

## Metadata

- name: License
- SubclassOf: AnyLicenseInfo
- Instantiability: Abstract

## Properties

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
