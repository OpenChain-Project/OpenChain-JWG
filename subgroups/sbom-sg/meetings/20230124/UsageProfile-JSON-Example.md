# JSON example for usage profile  

## minimum  

- Ref: https://github.com/spdx/spdx-examples/blob/master/example9/spdx/appbomination.spdx.json  

```
{
    ...,
    "packages": [ {
        "PackageName": "foo",
        "SPDXID": "SPDX-Ref-foo-1.2.3",
        "PackageVersion": "1.2.3",
        ...,
        "ReleaseDate": "2022-12-01T00:00:00Z",
        "BuiltDate": "2022-12-01T00:00:00Z",
        "ValidUntilDate": "2023-02-28T00:00:00Z"
    }, {
        "PackageName": "bar",
        "SPDXID": "SPDX-Ref-bar-1.0.0",
        "PackageVersion": "1.0.0",
        ...,
        "ReleaseDate": "2022-12-01T00:00:00Z",
        "BuiltDate": "2022-12-01T00:00:00Z",
        "ValidUntilDate": "2023-03-31T00:00:00Z"
    } ],
    "files": [{
        ...,
    }],
    "relationships": [ { // コンポーネント間の関係を記述するために存在しているのでは？ つまり、Usageとの関係を記述しちゃダメなのでは？ MLに質問を投げてみる。=> 忍頂寺さん
        "spdxElementId" : "SPDX-Ref-foo-1.2.3",
        "relatedSpdxElement" : "SPDX-Ref-Usage-01",
        "relationshipType" : "DESCRIBED_BY"
    }, {
        "spdxElementId" : "SPDX-Ref-bar-1.0.0",
        "relatedSpdxElement" : "SPDX-Ref-Usage-01",
        "relationshipType" : "DESCRIBED_BY" // ここの定義も精査が必要
    }, { // UsageProfile間の関係性をRelationshipで記述できるか？ **※UsageProfile間の関係性をどう記述するか**  
        "spdxElementId": "SPDX-Ref-Usage-01",
        "relatedSpdxElement" : "SPDX-Ref-Usage-02",
        "relationshipType" : "CONTAINS" // こういう書き方する？
    }, { // AND/OR/WITHなどはRelationには存在しないので他の表現方法を考える必要がある。 **※UsageProfile間の関係性のAND/OR条件などをどう記述するか**
        "spdxElementId": "SPDX-Ref-Usage-02",
        "relatedSpdxElement" : "SPDX-Ref-Usage-03",
        "relationshipType" : "AND/OR/WITH(例外)" // それぞれの個別要件間の関係性を記述したい。その場合、ValidUntilDate, Eventなどをどう考えるか。
    } ], // ExternalRef -> 契約書を参照させて、それをUsageProfileとRelation持たせる。 契約書はA-B間だけのものであって、A-B-CとChainがつながると、A-C間で情報が欠落する。**※UsageProfileのもととなる契約条件をどう記述、参照させるか**
    "usages": [ { // 誰がいつ、このUsage条件を規定しているのかがわかるような情報が必要なのではないか。
        "SPDXID": "SPDX-Ref-Usage-01",
        "UsageScope": "契約条件1", // ここは DESCRIBED_BY などと同様の定義が必要
        "UsageScopeComment": "全体要件",
        "PackageBuildCondition": "-O -gDEBUG ...", // Build Profileとの関連は？
        "ValidUntilDate": "2023-01-31T00:00:00Z" // これがPackageのValidUntilを上書きしてほしい
        ...
    }, { 
        "SPDXID": "SPDX-Ref-Usage-02",
        "UsageScope": "契約条件2",
        "UsageScopeComment": "個別要件",
        "PackageBuildCondition": "-O -gDEBUG ...", 
        "ValidUntilDate": "2023-01-15T00:00:00Z"
        ...
    }, { 
        "SPDXID": "SPDX-Ref-Usage-03",
        "UsageScope": "契約条件3",
        "UsageScopeComment": "個別要件",
        "PackageBuildCondition": "-O -gDEBUG ...",
        "ValidUntilDate": "2023-01-15T00:00:00Z"
        ...
}]
}
```
