SPDX-License-Identifier: Community-Spec-1.0

# SoftwareArtifact

## Summary

A distinct article or unit related to Software.

## Description

A software artifact is a distinct article or unit related to software
such as a package, a file, or a snippet.

## Metadata

- name: SoftwareArtifact
- SubclassOf: /Core/Artifact
- Instantiability: Abstract

## Properties

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

