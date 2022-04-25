# N Usage Profile section

## Usage Scope field <a name="N.1"></a>

### Description

While required license conditions or any requirements for software packages are changed dynamically, such as in each development phase transition or in the final product shipment to the public, software package supplyer need to tell its consumers detail conditions to be obey.
Especially in the large scale development which operated via multi layer software supply chain through upstream to downstream, community to industorial company, license conditions must be carried through upstream side to downstream side along with the software package through such multi layer supply chain.

On the other hand, each software package are used as in consumer's own will and purpose under the license condition. Even though the software package supplyer able to notice detail usage and condition just their own prerequisite assumption.

With this field, software package supplyer able to describe detail license conditions or any requirements to use software package along with its prerequisite assumptions of the detail descriptions. And also it's able to focus those information in the SPDX for specific usage of specific downstream consumer with mention the prerequisite product and the expiration date. 


Table NN — Metadata for the usage scope field

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..* |
| Format | ["DocumentRef-"[idstring]":"]SPDXID \<Single line of text\>. <br>where "DocumentRef-"`[idstring]`":" is an optional reference to a Package SPDX ididentifier as described in [7.2](package-information.md#7.2).<br> |

<br>

### Intent

To describe detail license conditions or any requirements to use software package along with its prerequisite assumptions of the detail descriptions from the package supplyer.

### Examples

EXAMPLE 1 Tag: `UsageScope:`

```text
UsageScope: SPDXRef-a_specific_binary_verNNN: shipped for consumer product/ medical system / automotive system
```

```text
UsageScopeComment: A_specific_binary_verNNN is compiled and velified as production level quality
```

EXAMPLE 2 RDF: Property `spdx:usagescope` in any `spdx:SpdxDocument`, `spdx:Package` or `spdx:File`

```text
```

## Usage Scope Comment field <a name="N.1"></a>

### Description

Table NN — Metadata for the usage scope comment field

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | Free form text that may span multiple lines, refers only to the immediately preceding usagescope.  |


### Intent

To describe prerequisite assumptions of usage scope by the package supplyer.

### Examples

EXAMPLE 1 Tag: `UsageScopeComment:`

```text
UsageScopeComment: A_specific_binary_verNNN is compiled and velified as production level quality
```

EXAMPLE 2 RDF: Property `rdfs:comment` in class `spdx:UsageScope`

```text
```

## Package Release Date field 

### Description

This field provides a place for recording package release date

Table NN — Metadata for the package release date

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | `YYYY-MM-DDThh:mm:ssZ`<br>where:<br><ul><li>`YYYY` is year</li><li>`MM` is month with leading zero</li><li>`DD` is day with leading zero</li><li>`T` is delimiter for time</li><li>`hh` is hours with leading zero in 24 hour time</li><li>`mm` is minutes with leading zero</li><li>`ss` is seconds with leading zero</li><li>`Z` is universal time indicator</li></ul> |


### Intent

Description of the package release date for strict identification of the prerequisite assumptions of usage scope by the package supplyer.

### Examples

EXAMPLE 1 Tag: `PackageReleaseDate:`

```text
PackageReleaseDate: 2010-01-29T18:30:22Z
```

EXAMPLE 2 RDF: Property `spdx:packageReleseDate` in class `spdx:UsageScope`

```text
```


## Package Build Date field

### Description

This field provides a place for recording build date of the package 

Table NN — Metadata for the package build date

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | `YYYY-MM-DDThh:mm:ssZ`<br>where:<br><ul><li>`YYYY` is year</li><li>`MM` is month with leading zero</li><li>`DD` is day with leading zero</li><li>`T` is delimiter for time</li><li>`hh` is hours with leading zero in 24 hour time</li><li>`mm` is minutes with leading zero</li><li>`ss` is seconds with leading zero</li><li>`Z` is universal time indicator</li></ul> |


### Intent

Description of the build date of the package for strict identification of the prerequisite assumptions of usage scope by the package supplyer.
It's recoreded from build system tools or date field of the package file.

### Examples

EXAMPLE 1 Tag: `PackageBuildDate:`

```text
PackageBuildDate: 2010-01-29T18:30:22Z
```

EXAMPLE 2 RDF: Property `spdx:packageBuildDate` in class `spdx:UsageScope`

```text
```

## Valid Until field

### Description

Identify expiration condition of the usage profile desciriptions which declared by supplyer of the package.
For example, to specify "usage scope" descriptions under specific period and/or specific conditions such as "This SPDX descriptions are valid until next delivery of newer SPDX descriptions". 

Table NN — Metadata for the valid until field

| Attribute | Value |
| --------- | ----- |
| Required | No |
| Cardinality | 0..1 |
| Format | Free form text that may span multiple lines, refers only to the immediately preceding usagescope.  |


### Intent

To the place for descibing period / conditions / events which affects to validity of usage scope descriptions.

### Examples

EXAMPLE 1 Tag: `ValidUntil:`

```text
ValidUntil: 2030-01-29T18:30:22Z
```
```text
ValidUntil: Updated descriptions are delivered
```


EXAMPLE 2 RDF: Property `rdfs:comment` in class `spdx:UsageScope`

```text
```
