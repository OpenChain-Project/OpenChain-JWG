# SBOM Document Quality Guide  

THIS IS A DRAFT DOCUMENT. IT IS CURRENTLY BEING USED TO BRAINSTORM IDEAS. PLEASE FOLLOW THE SBOM STUDY GROUP TO LEARN MORE AND PARTICIPATE.  

Mailing list: https://lists.openchainproject.org/g/sbom

---
## Table of Contents  

0. [Preface](#0-preface)
1. [Scope](#1-scope)
2. [Terms and Definitions](#2-terms-and-definitions)
3. [Requirements](#3-requirements)
4. [Conformant notice](#4-conformant-notice)
5. [SBOM Quality Assessment and Improvement Measures](#5-sbom-quality-assessment-and-improvement-measures)  
5.1. [Ensuring Accurate and Consistent Information Descriptions](#51-ensuring-accurate-and-consistent-information-descriptions)  
5.2. [Standardization and Normalization of Component Granularity](#52-standardization-and-normalization-of-component-granularity)  
5.3. [Complementing Source Information and Enhancing Transparency](#53-complementing-source-information-and-enhancing-transparency)  
5.4. [Strengthening Vulnerability Integration and Risk Management](#54-strengthening-vulnerability-integration-and-risk-management)  
5.5 [Enhanced Information Integration and Collaboration Between Upstream and Downstream](#55-enhanced-information-integration-and-collaboration-between-upstream-and-downstream)  
5.6. [Establishing a Tamper Detection and Change Management System](#56-establishing-a-tamper-detection-and-change-management-system)  
5.7. [Clarifying the Scope of Descriptions and Defining Accountability](#57-clarifying-the-scope-of-descriptions-and-defining-accountability)  
5.8. [Unified Expression of Inter-Component Relationships](#58-unified-expression-of-inter-component-relationships)  
5.9. [Capturing Dependencies and Issues in Package Retrieval Methods](#59-capturing-dependencies-and-issues-in-package-retrieval-methods)  
5.10. [Insufficient Interoperability and Flexibility Among Tools](#510-insufficient-interoperability-and-flexibility-among-tools)  
5.11. [Tool Maintenance and Community Collaboration](#511-tool-maintenance-and-community-collaboration)
6. [Guide Administration and Management](#6-guide-administration-and-management)
7. [References and Related Documents](#7-references-and-related-documents)  

Appendix-1. [SBOM Sample](#appendix-1-sbom-sample)  
Appendix-2. [Template for Documenting Each Best Practice at Chapter 5](#appendix-2-template-for-quality-evaluation-items-chapter-5)  

---
## 0. Preface

This document, "OpenChain SBOM Document Quality Guide", is based on [the original OpenChain Telco SBOM Guide](https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_EN.md). While the original text has been preserved as much as possible, modifications have been made based on [the discussions within the SBOM study group](https://github.com/OpenChain-Project/SBOM-sg/blob/main/meetings/20250423.md). You can refer to [all previous discussions](https://github.com/OpenChain-Project/SBOM-sg/tree/main/meetings) for additional background information.  

Key differences between the two documents include:
- Both specifications are compatible. An SBOM that conforms to the Telco SBOM Guide is also compliant with this document.  
- Although the Telco SBOM Guide is designed for cross-industry use, the wording has been refined to clearly reflect its applicability across various sectors.  
- The document is written in a manner that is independent of any specific SBOM format.  
- A new chapter has been added to explain what constitutes a high-quality SBOM document, why this is important, and how such documents can be utilized.  
- Best practices addressing various challenges in creating, managing SBOMs have been incorporated.  
- As part of these best practices, actual SBOM document samples are provided in JSON format along with their corresponding schema.  

## 1. Scope

This document “OpenChain SBOM Document Quality Guide”is intended to form a common understanding among stakeholders in the supply chain. It presents improvements to improve the standardization, accuracy, transparency, and automation potential of SBOM.

It helps to remove barriers in the distribution of software bills of materials (SBOM) by proposing improvements to common issues when the parties involved in the supply chain create, provide and use them.

*Please Note* that this guide does not require a conforming entity to adopt OpenChain (in any version) but doing so is greatly encouraged.

This guide is intended for all SBOM generation and operation target processes, including software packages, containers, SaaS, and embedded software. This guide refers to individual SBOMs, not the entities that provide them.
An SBOM using this guide can be called “OpenChain SBOM Document Quality Guide Compatible.”

Releasing SBOMs that match the requirements outlined in this guide does not preclude an entity from also delivering SBOMs for the same software in alternate ways or formats.

This guide is licensed under [Creative Commons Attribution License 4.0 (CC-BY-4.0)](https://creativecommons.org/licenses/by/4.0/).

---

> *(The following sections are still having its wording refined and will be reviewed in the future.)*

## 2. Terms and Definitions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 ([RFC2119](https://www.ietf.org/rfc/rfc2119.txt)) and ([RFC8174](https://www.ietf.org/rfc/rfc8174.txt)) when they appear in all capitals.

### Data Format  
Data Format means the data format of the information in the SBOM. Possible Data Formats include SPDX, Cyclone DX, SWID, or other proprietary formats.

### Entity  
Entity shall mean the legal entity (for profit, non profit, or natural person) that distributes software to third parties (e.g., other organizations or individuals). Entity does not include other group companies, or companies under common control of the Entity.

### SBOM  
A Software Bill of Materials (SBOM) is a formal record containing the details and supply chain relationships of various components used in building software.

### SBOM Type  
An SBOM can be of one of the following types:

- Design,
- Source,
- Build,
- Analyzed,
- Deployed,
- Runtime.

The definitions of these types can be found in the [CISA document](https://www.cisa.gov/sites/default/files/2023-04/sbom-types-document-508c.pdf).

### SPDX
SPDX (Software Package Data Exchange) is the [ISO standard](https://www.iso.org/standard/81870.html) (ISO/IEC 5962:2021) for exchanging SBOM for a given software package, including associated license and copyright information. The standard was created by the [Linux Foundation's SPDX project](https://spdx.dev/).

### OpenChain ```Specification?```  
OpenChain means [OpenChain ISO/IEC 5230:2020](https://www.iso.org/standard/81039.html), the international standard that specifies the key requirements of a quality open source license compliance program in order to provide a benchmark that builds trust between organizations exchanging software solutions that incorporate open source software. The OpenChain standard is produced by the [OpenChain project](https://www.openchainproject.org) of the Linux Foundation.

**TBD** ```ISO/IEC 18974:2023?```

### Transitive dependencies
Transitive dependencies are all components that are necessary for the software to run. They include any dependency of the package that is not a direct dependency.

### Package URL (PURL)
Package URL (PURL) is a _de facto_ standard to uniquely identify software packages.

### CycloneDX  
**TODO**

### SBOM Document  
**TBD**

### SWHID? (SWID?)
**TODO**

---

## 3. Requirements

### 3.1 Data Format
An OpenChain Telco SBOM Guide compatible document SHALL adhere to the version 2.2 of the SPDX Data Format as standardized in ISO/IEC 5962:2021, or to the version 2.3 of the standard, and as further described below with respect to the included elements.

#### 3.1.1 Verification and reference material
* ISO/IEC 5962:2021 Information technology — SPDX® Specification V2.2.1
* [SPDX Specification V2.3](https://spdx.github.io/spdx-spec/v2.3/)

#### 3.1.2 Rationale
To ensure simplified handling and streamlining of tooling and competences in the telecommunications supply chain, both for suppliers and consumers of software, OpenChain Telco SBOM Guide Compatible documents shall adhere to the SPDX Data Format as standardized in ISO/IEC 5962:2021. By harmonizing on the use of this standard SBOM Data Format in an organization's external interfaces, the complexities for organizations supplying and consuming software are simplified, as only one set of unified requirements will be applicable.

As clarification, an entity is free to use alternative Data Formats for internal use, or deliver SBOMs in alternative Data Formats to organizations that so request or on its own initiative. The OpenChain Telco SBOM Guide is a SBOM-level specification to adhere to, and not an organizational specification to adhere to. There are no conforming entities, only conforming SBOMs, delivered by entities that have implemented the OpenChain Telco SBOM Guide.

### 3.2 SPDX Elements to be included in an OpenChain Telco SBOM Guide Compatible document

The following elements are REQUIRED.

Document creation information
* SPDXVersion: mandatory in SPDX
* DataLicense: mandatory in SPDX
* SPDXID: mandatory in SPDX
* DocumentName: mandatory in SPDX
* DocumentNamespace: mandatory in SPDX
* Creator: mandatory in SPDX
* Created: mandatory in SPDX
* CreatorComment: to be able to put “SBOM Build information”

Package information
* PackageName: mandatory in SPDX
* SPDXID: mandatory in SPDX
* PackageVersion: needed by “NTIA SBOM Minimum elements”
* PackageSupplier: needed by “NTIA SBOM Minimum elements”
* PackageDownloadLocation: mandatory in SPDX
* PackageLicenseConcluded: mandatory in SPDX 2.2
* PackageLicenseDeclared: mandatory in SPDX 2.2
* PackageCopyrightText: mandatory in SPDX 2.2

One of the two attributes PackageChecksum or PackageVerificationCode is RECOMMENDED:
recommended by “NTIA SBOM Minimum elements”

A package SHOULD be identified by a Package URL (PURL).

If the PURL is present, it SHOULD be put in ExternalRef field, e.g.
```
ExternalRef: PACKAGE-MANAGER purl pkg:pypi/django@1.11.1
```

Relationships between SPDX elements
* Relationship: at least DESCRIBES and CONTAINS, needed by “NTIA SBOM Minimum elements”

#### 3.2.1 Verification and reference material
NTIA minimum elements

#### 3.2.2 Rationale
Recognizing the Telco industry need for harmonization and special requirements, the “OpenChain Telco SBOM Guide” is proposed to ensure predictability to the industry as to the elements of an SBOM that is expected.

“Component Hash” is recommended, but not required by the “NTIA SBOM Minimum elements”.

In SPDX, it maps to PackageChecksum or PackageVerificationCode.
Most SCA tools have the capability to produce hashes.

The CISA document "Framing Software Component Transparency: Establishing a Common Software Bill of Materials (SBOM), Third Edition"
https://www.cisa.gov/resources-tools/resources/framing-software-component-transparency-2024
allows both, see table in section 2.5.

Package URL (PURL) is a _de facto_ standard to uniquely identify software packages.

### 3.3 Machine Readable Data Format
An OpenChain Telco SBOM Compatible document SHALL include, at a minimum, SPDX in one of the following machine readable formats: Tag:Value or JSON.

#### 3.3.1 Verification and reference material
Tag:Value and JSON formats are described here:
* in SPDX 2.2 https://spdx.github.io/spdx-spec/v2.2.2/conformance/#44-standard-data-format-requirements
* in SPDX 2.3 https://spdx.github.io/spdx-spec/v2.3/conformance/#44-standard-data-format-requirements

#### 3.3.2 Rationale
There are 3 majors formats for SBOMs: SPDX, CycloneDX, and SWID.
These 3 formats are the ones recommended by NTIA document "The Minimum Elements For a Software Bill of Materials (SBOM)" (see References section).

The reasons for selecting SPDX as data format of the OpenChain Telco SBOM Guide include the following:
* SPDX is an ISO standard,
* SPDX has more features than CycloneDX for license compliance,
* SPDX has a human-readable format (CycloneDX has only JSON and XML),
* SWID is more a software identifier than a fully fledged SBOM format.

To facilitate a simplified toolchain, a machine readable version of the SBOM needs to be included. To ensure repeatability and harmonization a conformant SBOM must be in Tag:Value or JSON format. An entity can release additional machine readable formats but they are not required to conform to the Guide.

Tag:Value is the most human-readable format, and there are converters between the various SPDX formats
(e.g. https://tools.spdx.org/app/convert/). JSON is a format produced by several tools.

### 3.4 Human Readable Data Format
An OpenChain Telco SBOM Compatible document SHALL include, at a minimum, the SPDX in one of the following human readable formats: Tag:Value or JSON.

#### 3.4.1 Verification and reference material
Tag:Value and JSON formats are described here:
* in SPDX 2.2 https://spdx.github.io/spdx-spec/v2.2.2/conformance/#44-standard-data-format-requirements
* in SPDX 2.3 https://spdx.github.io/spdx-spec/v2.3/conformance/#44-standard-data-format-requirements

#### 3.4.2 Rationale
As the Tag:Value format is also human readable it has been chosen so that both the requirements for a standardized machine readable and human readable version can be met using one file. An entity can release additional human readable formats but they are not required to conform to the OpenChain Telco SBOM Guide.

### 3.5 SBOM Build information
SBOMs conforming to the OpenChain Telco SBOM Guide MUST contain information as when they were created (using the SPDX `Created` field) and to which version of the software they were created (using the SPDX `CreatorComment` field).

The `Creator` field MUST:
* contain a line with the `Organization` keyword;
* contain a line with the `Tool` keyword; in this line we MUST have after the `Tool` keyword the tool name and the tool version.

The tool name and the tool version SHOULD be separated by hyphen ("-"), no other hyphen SHOULD appear on the line.

SBOMs conforming to the OpenChain Telco SBOM Guide MUST provide their SBOM Types as
[defined by CISA](https://www.cisa.gov/sites/default/files/2023-04/sbom-types-document-508c.pdf)
in the `CreatorComment` field.

The SBOM Type RECOMMENDED syntax is “SBOM Type: xxx” where “xxx” is one of the 6 keywords “Design”, “Source”, “Build”, “Analyzed”, “Deployed” and “Runtime”.

#### 3.5.1 Verification and reference material
SPDX standard

#### 3.5.2 Rationale
It is important to know which tool and which version of the tool have created the SBOM.

The SPDX standard gives "toolidentifier-version" as an example, but it is not mandatory to have this syntax.

For example, there is a tool that outputs:
```
Creator: Tool: sigs.k8s.io/bom/pkg/spdx
```
We have also:
```
Creator: Tool: scancode-toolkit 32.3.0
```
and
```
Creator: Tool: SCANOSS-PY: 1.18.1
```
where the name contains an hyphen, and the tool name and tool version are not separated by an hyphen.

So we cannot require a precise syntax.

The CreatorComment is a free text field. We use it to store the CISA SBOM Types, as there is no
specific field for that in SPDX 2.2 and 2.3, but any other information can of course be put in it also.

We do not require a specific format. We only require that at least one of the words
“Design”, “Source”, “Build”, “Analyzed”, “Deployed”, “Runtime” is present, regardless of the case.

So, the following possibilities are all valid, and the first one is the recommended one:
```
CreatorComment: SBOM Type: Deployed
```
```
CreatorComment: Analyzed
```
```
CreatorComment: This SBOM was created during build phase.
```

### 3.6 Timing of SBOM delivery
The SBOM SHALL be delivered no later than at the time of the delivery of the software (in either binary or source form). 

#### 3.6.1 Verification and reference material
“NTIA SBOM Minimum elements”, section “Distribution and Delivery”

#### 3.6.2 Rationale
To ensure that the receiving entity can ingest the software and its SBOM, it shall be delivered no later than at the delivery of the software. An SBOM may be delivered before the software if an adopting entity so elects, but the software delivery must nevertheless be accompanied by the corresponding SBOM to ensure compliance with the Guide.

### 3.7 Method of SBOM delivery
The SBOM SHALL be embedded into the software “package” where technically feasible. If it is not technically feasible to embed the SBOM into the software “package” being delivered, such as in the case of space-constrained embedded systems, the supplying party will supply a web hosted version of the SBOM that is available for at least 18 months and SHALL NOT in any way restrict recipients’ ability to copy and store these locally for their own use. Such restrictions MAY NOT be placed on the recipient in additional confidentiality agreements. 

#### 3.7.1 Verification and reference material
“NTIA SBOM Minimum elements”, section “Distribution and Delivery”

#### 3.7.2 Rationale
Other options of SBOM delivery such as webhosting are less stable and access is not guaranteed over time; however “embedding” may not be technically feasible. Thus, in scenarios where it is not possible on technical grounds to include the SBOM in the software delivery, publishing the SBOM online is permitted provided that the SBOM is accessible for the recipients of the software for 18 months. This duration is in line with the OpenChain specification requirements on recertification.

### 3.8 SBOM Scope
The SBOM SHALL contain all open source software that is delivered with the product including all of the transitive dependencies. The SBOM SHOULD contain all commercial components.

If some components are not included, they MUST be reported as “known unknowns.”

#### 3.8.1 Verification and reference material
“NTIA SBOM Minimum elements”, section “Known Unknowns”

#### 3.8.2 Rationale
It might not be possible, advisable or feasible to have the commercial component information in the SBOM. However, it is advisable that the SBOM should be as complete as possible.

### 3.9 SBOM in a SaaS deployment
As the OpenChain Telco SBOM Guide is only applied on the SBOM level, there is no requirement on an entity that has elected to supply an OpenChain Telco SBOM Compatible document for some or even all of its software deliveries to also provide this for its SaaS offerings. However, an entity may elect to apply the OpenChain Telco SBOM Guide also to its SaaS offerings and thus also deliver the open source software used in the SaaS offerings with their transitive dependencies as an SBOM.

#### 3.9.1 Verification and reference material

#### 3.9.2 Rationale
There is currently no consensus in the industry on what an SaaS SBOM should contain.

### 3.10 SBOMs for containers
SBOMs for containers SHOULD include all open source components delivered in the container. This includes the packages installed into the container, components copied or downloaded to the container and dependencies used to build the compiled components in the container.

#### 3.10.1 Verification and reference material

#### 3.10.2 Rationale
Every open source component delivered should be part of the SBOMs.

### 3.11 SBOM Verification
It is RECOMMENDED to provide a digital signature of the SBOM in order to guarantee the
integrity of the SBOM.

#### 3.11.1 Verification and reference material
Sigstore https://www.sigstore.dev/ is an example of such capability.

#### 3.11.2 Rationale
While the verification of SBOMs is an important topic, OpenChain Telco defers this work to other initiatives for the moment and intends to revisit this topic in future iterations of this document.

### 3.12 SBOM Merger
SBOMs following this Guide can be built from several SBOM files with a well-defined relationship to each other using the relationship definition features in SPDX.

#### 3.12.1 Verification and reference material
There exist tools to merge several SBOMs into one, e.g. https://github.com/interlynk-io/sbomasm

#### 3.12.2 Rationale
It is often easier when dealing with a large software product to provide individual SBOMs of its parts than a single SBOM.

### 3.13 SBOM Confidentiality
SBOMs MAY be subject to confidentiality agreements. A conformant SBOM MUST NOT, however, be subject to any confidentiality agreements that would prevent a recipient from redistributing the parts of the SBOM applicable to software that such recipient has a right to redistribute.

#### 3.13.1 Verification and reference material
“NTIA SBOM Minimum elements”, section “Access Control”

#### 3.13.2 Rationale
Some open source software licenses enable any recipient to redistribute the software. In these situations, the recipients should also be able to redistribute the relevant parts of the SBOMs.

## 4. Conformant notice
To indicate that the software has a conformant SBOM available, you MAY use the following statement: “This software is supplied with an SBOM conformant to the OpenChain Telco SBOM Guide v1.1, the Guide is available at [https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_EN.md](https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_EN.md)”

You MAY at your choosing use the following statement in your Telco Guide conformant SBOM “This SBOM conforms to the OpenChain Telco SBOM Guide v1.1 [https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_EN.md](https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_EN.md), it is provided to the recipient free of charge, and the recipient is free to redistribute this SBOM to any third party that they distribute the corresponding software to, provided that they have all the necessary rights to distribute the software to such third party”

The following statement MAY be used as statement in the RFP document, order document, or contract document when requesting an RFP, purchasing orders, or outsourced development orders from a software vendor or telco system suppliers.
“When releasing software, it is REQUIRED to provide an SBOM compliant with the OpenChain Telco SBOM Guide v1.1 for all software released.  This Guide is available at [https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_EN.md](https://github.com/OpenChain-Project/Telco-WG/blob/main/OpenChain-Telco-SBOM-Guide_EN.md)”

---
## 5. SBOM Quality Assessment and Improvement Measures

This section highlights the challenges often encountered when generating and managing SBOMs, and introduces best practices for addressing them. These measures are designed to enhance the accuracy, consistency, and transparency of SBOM documents, as well as to improve the overall processes involved in handling them.

### 5.1 Ensuring Accurate and Consistent Information Descriptions

#### 5.1.1 Issue Overview  
Challenges exist in the inconsistent representation of information such as package names, versions, and supplier names across different companies and tools. Without unified standards, automatic analysis of SBOMs or vulnerability matching becomes challenging, leading to inaccuracies.

#### 5.1.2 Detailed Description  
In many SBOM guides, the keys defining what should be included are explicitly specified, along with the corresponding values that should be written. However, since a precise format for these values is often not defined, issues can arise during practical implementation.  

For example, the two SBOMs below use different package names - one as 'hello' and the other as 'hello 0.0.1'. This discrepancy is due to differences in the output formats of the tools used. 
- [example7-bin.spdx.json](https://github.com/spdx/spdx-examples/blob/master/software/example7/spdx2.2/example7-bin.spdx.json#L44)  
  ```"name": "hello",```  
- [hello-dist.spdx.json](https://github.com/spdx/spdx-examples/blob/master/software/example12/spdx2.2/hello-dist.spdx.json#L56)  
  ```"name": "hello 0.0.1",```  

Although verifying that these represent the same package is possible by comparing, for instance, their PURLs, the fact that different tools may write different values for the same key frequently leads to confusion and poses challenges to the smooth operation of SBOM management.  

#### 5.1.3 Improvement Measures  
- Organizations involved in the software supply chain shall agree to document values - such as purl - that uniquely identify a package.  
- A standardized notation rule based on industry standards or internal guidelines shall be formulated, and concrete examples (e.g., format examples using regular expressions) shall be widely shared among the organizations involved in the software supply chain.  
- Verification tools shall be shared among the organizations in the software supply chain, and a mechanism shall be established to check whether the following items - crucial for package identification and prone to inconsistent notation—comply with the established rules:  
  - Package name  
  - Package version  
  - Package supplier name  
  - Package source  
  - Presence of purl  

#### 5.1.4 Evaluation Methods  
- Randomly check whether each documented item adheres to the standardized notation rules, and evaluate the compliance rate.  

#### 5.1.5 Risks and Considerations  
- If the documentation rules are inadequately defined or overly complex, there is a risk of misclassification due to incomplete handling of exceptional cases or unique notations.
- If the rules deviate from actual operational practices, there is a risk of misclassification resulting from either insufficient or excessively stringent checks.
- It should be noted that complete automation of tools and processes is challenging; therefore, final checks and exception handling will require manual review.  

### 5.2 Standardization and Normalization of Component Granularity

#### 5.2.1 Issue Overview  
SBOMs are expected to include components at two levels: file and package.  
While it presents no issue if the granularity of these components is consistent throughout the supply chain, as complexity increases, there is a higher likelihood that SBOMs exchanged within the supply chain will vary in their component granularity. Regardless of whether an SBOM is provided as a single merged file or as multiple files, the challenge is to describe dependencies consistently when SBOMs with different granularities coexist in the supply chain.  

#### 5.2.2 Detailed Description  
A simplified scenario involving three parties: ```Vendor```, ```Maker```, and ```User```.  

- Preconditions
  1. ```Vendor``` provides ```App A``` to ```Maker``` as both a binary and an SBOM.
  2. ```Maker``` provides ```Product X```, which includes ```App A``` and the other OSS, along with an SBOM, to ```User```.
  3. ```App A``` depends on the other OSS used in ```Product X``` provided by ```Maker```.

Under these conditions, the combinations of granularity for the components in ```App A```’s SBOM - whether at the binary file level or binary package level - and the granularity at which ```Maker``` generates the final ```Product X```’s SBOM (as binary file or binary package) are summarized in the table below.

|   |   | ```Maker```'s SBOM Provided to ```User```<br> (File Level) | ```Maker```'s SBOM Provided to ```User```<br> (Package Level) |  
| :-- | :-- | :-- | :-- |  
| ```Vendor```'s SBOM for ```App A``` (File Level) | **Component Granularity: File** | File level | Convert the File Level information regarding other OSS dependencies of ```App A``` into Package level. And convert the Package level information for ```App A``` into File level. |  
| ```Vendor```'s SBOM for ```App A``` (Package level) | **Component Granularity: Package** | Decompose ```App A``` package into files (File level) | Package level |

As shown in the table, while each case is feasible, the workload for ```Maker``` varies depending on the combination. Because different approaches are necessary to handle the discrepancies in component granularity between SBOMs, addressing the issue becomes challenging without explicit granularity information. 
Although alternative methods might be employed in a simple supply chain scenario like this example even if the SBOM lacks granularity details, as the supply chain becomes more complex, including granularity information within the SBOM becomes essential.

#### 5.2.3 Improvement Measures  
- Ensure that the granularity of the components is clearly indicated, thereby enabling appropriate handling based on that granularity.  
- In practice, the specifications of the SBOM document format clearly distinguish between packages and files, so there is no issue. However, the granularity of components should be identifiable even before reaching the top-level component.

#### 5.2.4 Evaluation Methods  
- Validate via automated or manual reviews that the granularity metadata is consistently present and properly formatted across SBOMs.  

#### 5.2.5 Risks and Considerations  
- There is a potential for issues when linking with vulnerability information. For example, if component granularity is mixed, it may not be possible to automatically identify the corresponding vulnerability information, leading to concerns over increased manual effort and time.  

### 5.3 Complementing Source Information and Enhancing Transparency

#### 5.3.1 Issue Overview  
When only binaries and an SBOM are distributed, the lack of detailed source information (e.g., source file lists, hash values, and license data) reduces transparency and complicates vulnerability assessments.

#### 5.3.2 Detailed Description

#### 5.3.3 Improvement Measures  

#### 5.3.4 Evaluation Methods  

#### 5.3.5 Risks and Considerations  

### 5.4 Strengthening Vulnerability Integration and Risk Management

#### 5.4.1 Issue Overview  
Accurate identification and mapping of vulnerabilities is critical; however, inconsistent or incomplete component details and dependency relationships in SBOMs can lead to ineffective vulnerability management.

#### 5.4.2 Detailed Description  

#### 5.4.3 Improvement Measures  

#### 5.4.4 Evaluation Methods  

#### 5.4.5 Risks and Considerations  

### 5.5 Enhanced Information Integration and Collaboration Between Upstream and Downstream

#### 5.5.1 Issue Overview  
Discrepancies between SBOMs provided by upstream vendors and those generated internally by integrators can lead to misalignment and integration challenges.

#### 5.5.2 Detailed Description  

#### 5.5.3 Improvement Measures  

#### 5.5.4 Evaluation Methods  

#### 5.5.5 Risks and Considerations  

### 5.6 Establishing a Tamper Detection and Change Management System

#### 5.6.1 Issue Overview  
Unauthenticated changes or tampering with SBOM data can compromise its integrity, undermining risk assessments and quality assurance efforts.

#### 5.6.2 Detailed Description  

#### 5.6.3 Improvement Measures  

#### 5.6.4 Evaluation Methods  

#### 5.6.5 Risks and Considerations  

### 5.7 Clarifying the Scope of Descriptions and Defining Accountability

#### 5.7.1 Issue Overview  
Ambiguities in what information should be included (e.g., source code, binaries, firmware, hardware details) and lack of clear assignment of responsibility for data entries can lead to gaps in SBOM quality.

#### 5.7.2 Detailed Description  

#### 5.7.3 Improvement Measures  

#### 5.7.4 Evaluation Methods  

#### 5.7.5 Risks and Considerations  

### 5.8 Unified Expression of Inter-Component Relationships

#### 5.8.1 Issue Overview  
Inconsistent depiction of relationships between components (e.g., dependency, containment, derivation) may hinder accurate automated analysis and risk assessment.

#### 5.8.2 Detailed Description  

#### 5.8.3 Improvement Measures  

#### 5.8.4 Evaluation Methods  

#### 5.8.5 Risks and Considerations  

### 5.9 Capturing Dependencies and Issues in Package Retrieval Methods  

#### 5.9.1 Issue Overview  
Disparities between dependencies extracted directly from source code versus those derived from package management systems can lead to redundant or erroneous information.

#### 5.9.2 Detailed Description  

#### 5.9.3 Improvement Measures  

#### 5.9.4 Evaluation Methods  

#### 5.9.5 Risks and Considerations  

### 5.10 Insufficient Interoperability and Flexibility Among Tools  

#### 5.10.1 Issue Overview  
Different SBOM generation and analysis tools, such as ORT (OSS Review Toolkit), FOSSology, or ScanCode, may produce outputs with variations that complicate integration in a unified processing workflow.

#### 5.10.2 Detailed Description  

#### 5.10.3 Improvement Measures  

#### 5.10.4 Evaluation Methods  

#### 5.10.5 Risks and Considerations  

### 5.11 Tool Maintenance and Community Collaboration

#### 5.11.1 Issue Overview  
Inconsistent maintenance, updates, and community support for SBOM generation and analysis tools can undermine long-term reliability and compatibility.

#### 5.11.2 Detailed Description  

#### 5.11.3 Improvement Measures  

#### 5.11.4 Evaluation Methods  

#### 5.11.5 Risks and Considerations  

---
## 6. Guide Administration and Management

This section describes the processes for maintaining and updating the Quality Guide itself, ensuring that it remains relevant as industry standards and technologies evolve.

### 6.1 Guide Update Process

- Define a cyclical review schedule to update the guide based on technological advances, industry feedback, and regulatory changes.  
- Establish a review committee responsible for collecting feedback, evaluating proposed changes, and coordinating updates.

### 6.2 Revision History

- Maintain detailed revision logs that document the changes made in each update, including dates, affected sections, and impact on SBOM quality requirements.  
- Publish revision history alongside the guide to ensure transparency and traceability.

## 7. References and Related Documents

- ISO/IEC 5962:2021 – SPDX® Specification  
- [SPDX Specification V2.3](https://spdx.github.io/spdx-spec/v2.3/)  
- [CycloneDX Documentation](https://cyclonedx.org/)  
- NTIA SBOM Minimum Elements  
- CISA SBOM Types Document – [CISA Document](https://www.cisa.gov/sites/default/files/2023-04/sbom-types-document-508c.pdf)  
- Relevant publications on SBOM quality improvement and vulnerability management

---
## Appendix

### Appendix-1: SBOM Sample  
A sample SBOM file in JSON format demonstrating compliance with this guide.  
*Note: The sample should include complete component data, matching identifiers, and verified relationships as per SPDX or CycloneDX standards.*

### Appendix-2: Template for Quality Evaluation Items (Chapter 5)  
The template below can be used to document items related to quality evaluation:

```
#### [Section Number] [Item Name]

##### [Section Number].1 Issue Overview
- Briefly describe the overall issue.

##### [Section Number].2 Detailed Description
- Provide background, impact, and clarification on the issue.

##### [Section Number].3 Improvement Measures
- List specific countermeasures (e.g., tool introduction, standardization of templates, process definition).

##### [Section Number].4 Evaluation Methods
- Define both quantitative and qualitative evaluation criteria.

##### [Section Number].5 Risks and Considerations
- Enumerate risks, exceptions handling, and any supplementary remarks.
```
