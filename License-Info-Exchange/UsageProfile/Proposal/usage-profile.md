# N Usage Profile section

## N.1 Usage Scope field <a name="N.1"></a>

### N.1.1 Description

While required license conditions or any requirements for software packages are changed dynamically, such as in each development phase transition or in the final product shipment to the public, software package supplyer need to tell its consumers detail conditions to be obey.
Especially in the large scale development which operated via multi layer software supply chain through upstream to downstream, community to industorial company, license conditions must be carried through upstream side to downstream side along with the software package through such multi layer supply chain.

On the other hand, each software package are used as in consumer's own will and purpose under the license condition. Even though the software package supplyer able to notice detail usage and condition just their own prerequisite assumption.

With this field, software package supplyer able to describe detail license conditions or any requirements to use software package along with its prerequisite assumptions of the detail descriptions. And also it's able to focus those information in the SPDX for specific usage of specific downstream consumer with mention the prerequisite product and the expiration date. 


Table NN — Metadata for the usage scope field

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..* |
| Format | ["DocumentRef-"[idstring]":"]SPDXID \<Single line of text\>. <br>where "DocumentRef-"`[idstring]`":" is an optional reference to a Package / File SPDX identifier as described in [7.2](package-information.md#7.2) and [8.2](file-information.md#8.2).<br> |

<br>

### N.1.2 Intent

To describe detail license conditions or any requirements to use software package along with its prerequisite assumptions of the detail descriptions from the package supplyer.

### N.1.3 Examples

EXAMPLE 1 Tag: `UsageScope:`

```text
UsageScope: SPDXRef-a_specific_binary_verNNN: shipped for consumer product/ medical system / automotive system
```

```text
UsageScopeComment: A_specific_binary_verNNN is compiled and velified as production level quality
```

EXAMPLE 2 RDF: Property `spdx:UsageScope` in any `spdx:SpdxDocument`, `spdx:Package` or `spdx:File`

```text
    <UsageScope>
      <UsageScopeElement>
        <File rdf:about="http://spdx.org/spdxdocs/spdx-tools-v1.2-3F2504E0-4F89-41D3-9A0C-0305E82..."
      </UsageScopeElement>
      <Usage>SPDXRef-a_specific_binary_verNNN: shipped for consumer product/ medical system / automotive system
      </Usage>
    </UsageScope>
  ...

```

## N.2 Usage Scope Comment field <a name="N.2"></a>

### N.2.1 Description

Table NN — Metadata for the usage scope comment field

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | Free form text that may span multiple lines, refers only to the immediately preceding usagescope.  |


### N.2.2 Intent

To describe prerequisite assumptions of usage scope by the package supplyer.

### N.2.3 Examples

EXAMPLE 1 Tag: `UsageScopeComment:`

```text
UsageScopeComment: A_specific_binary_verNNN is compiled and velified as production level quality
```

EXAMPLE 2 RDF: Property `rdfs:comment` in class `spdx:UsageScope`

```text
<UsageScope>
         <rdfs:comment> A_specific_binary_verNNN is compiled and velified as production level quality</rdfs:comment>
</UsageScope>
```
```

## N.3 UsageScope SPDX identifier field <a name="N.3"></a>

### N.3.1 Description

Uniquely identify any element in an SPDX document which may be referenced by other elements. These may be referenced internally and externally with the addition of the SPDX document identifier. The metadata for the SPDX identifier field is shown in Table NN.

**Table NN — Metadata for the SPDX identifier field**

| Attribute | Value |
| --------- | ----- |
| Required | Yes |
| Cardinality | 1..1 |
| Format | "SPDXRef-"`[idstring]` <br> where `[idstring]` is a unique string containing letters, numbers, `.`, and/or `-`. |

### N.3.2 Intent

There may be several usecase of the same package within an SPDX document. Each element needs to be able to be referred to uniquely so that relationships between elements can be clearly articulated.

### N.3.3 Examples

EXAMPLE 1 Tag: `SPDXID:`

```text
SPDXID: SPDXRef-1
```

EXAMPLE 2 RDF: The URI for the element will follow the form:

```text
[SPDX document namespace]#[SPDX identifier]
```

See [6.5](document-creation-information.md#6.5) for the definition of the SPDX document namespace and [6.3](document-creation-information.md#6.3) for the definition of the SPDX identifier

Using `xml:base`:

```text
<rdf:RDF xml:base="http://acme.com/spdxdocs/acmeproj/v1.2/1BE2A4FF-5F1A-48D3-8483-28A9B0349A1B">
    ...
    <Package rdf:about="#SPDXRef-1">
    ...
    </Package>
</rdf:RDF>
```

Using document URI:

```text
<UsageScope rdf:about="http://acme.com/spdxdocs/acmeproj/v1.2/1BE2A4FF-5F1A-48D3-8483-28A9B0349A1B#SPDXRef-1">
    ...
</UsageScope>
```

## N.4 Package Release Date field 

### M.4.1 Description

This field provides a place for recording package release date

Table NN — Metadata for the package release date

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | `YYYY-MM-DDThh:mm:ssZ`<br>where:<br><ul><li>`YYYY` is year</li><li>`MM` is month with leading zero</li><li>`DD` is day with leading zero</li><li>`T` is delimiter for time</li><li>`hh` is hours with leading zero in 24 hour time</li><li>`mm` is minutes with leading zero</li><li>`ss` is seconds with leading zero</li><li>`Z` is universal time indicator</li></ul> |


### N.4.2 Intent

Description of the package release date for strict identification of the prerequisite assumptions of usage scope by the package supplyer.

### N.4.3 Examples

EXAMPLE 1 Tag: `PackageReleaseDate:`

```text
PackageReleaseDate: 2010-01-29T18:30:22Z
```

EXAMPLE 2 RDF: Property `spdx:packageReleseDate` in class `spdx:UsageScope`

```text
<UsageScope rdf:about="...">
    <packageReleaseDate> 2010-01-29T18:30:22Z </packageReleaseDate>
</UsageScope>
```


## N.5 Package Build Date field

### N.5.1 Description

This field provides a place for recording build date of the package 

Table NN — Metadata for the package build date

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | `YYYY-MM-DDThh:mm:ssZ`<br>where:<br><ul><li>`YYYY` is year</li><li>`MM` is month with leading zero</li><li>`DD` is day with leading zero</li><li>`T` is delimiter for time</li><li>`hh` is hours with leading zero in 24 hour time</li><li>`mm` is minutes with leading zero</li><li>`ss` is seconds with leading zero</li><li>`Z` is universal time indicator</li></ul> |


### N.5.2 Intent

Description of the build date of the package for strict identification of the prerequisite assumptions of usage scope by the package supplyer.
It's recoreded from build system tools or date field of the package file.

### N.5.3 Examples

EXAMPLE 1 Tag: `PackageBuildDate:`

```text
PackageBuildDate: 2010-01-29T18:30:22Z
```

EXAMPLE 2 RDF: Property `spdx:packageBuildDate` in class `spdx:UsageScope`

```text
<UsageScope rdf:about="...">
    <packageBuildDate> 2010-01-29T18:30:22Z </packageBuildDate>
</UsageScope>
```

## N.6 Valid Until field

### N.6.1 Description

Identify expiration condition of the usage profile desciriptions which declared by supplyer of the package.
For example, to specify "usage scope" descriptions under specific period and/or specific conditions such as "This SPDX descriptions are valid until next delivery of newer SPDX descriptions". 

Table NN — Metadata for the valid until field

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | Free form text that may span multiple lines, refers only to the immediately preceding usagescope.  |


### N.6.2 Intent

To the place for descibing period / conditions / events which affects to validity of usage scope descriptions.

### N.6.3 Examples

EXAMPLE 1 Tag: `ValidUntil:`

```text
ValidUntil: 2030-01-29T18:30:22Z
```
```text
ValidUntil: Updated descriptions are delivered
```


EXAMPLE 2 RDF: Property `rdfs:comment` in class `spdx:ValidUntil` of `spdx:UsageScope`

```text
<UsageScope rdf:about="...">
    <ValidUntil>
         <rdfs:comment> Earlyer date of 2030-01-29T18:30:22Z or Updated descriptions are delivered</rdfs:comment>
    </ValidUntil>
</UsageScope>
```
