---
title: ビジュアル フィルター API
description: Power BI ビジュアルで他のビジュアルをフィルター処理する方法
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 50e9601faf497675ebc3f24609a856a600e3bcb1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425047"
---
# <a name="power-bi-visual-filters-api"></a>Power BI ビジュアル フィルター API

ビジュアルのフィルター処理で、データをフィルター処理できます。 選択との主な違いは、別のビジュアルで強調表示がサポートされていても、他のビジュアルが任意の方法でフィルター処理されることです。

ビジュアルのフィルター処理を有効にするには、capabilities.json コンテンツの `general` セクションに `filter` オブジェクトが含まれている必要があります。

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

フィルター API インターフェイスは [`powerbi-models`](https://www.npmjs.com/package/powerbi-models) パッケージで使用できます。 このパッケージには、フィルター インスタンスを作成するためのクラスも含まれています。

```cmd
npm install powerbi-models --save
```

古いバージョンのツール (バージョン 3.x.x より前のバージョン) を使用する場合、`powerbi-models` をビジュアル パッケージに含める必要があります。 [パッケージを含める方法の簡単なガイド](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md)

すべてのフィルターは `IFilter` インターフェイスを拡張します。

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```

`target` - データソースのテーブル列です。

## <a name="basic-filter-api"></a>基本フィルター API

基本フィルター インターフェイスは次のようになります。

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

`operator` - 値が "In"、"NotIn"、"All" の列挙型

`values` - 条件の値

基本フィルターの例:

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

このフィルターは、"`col1` が値 1、2、3 のいずれかに等しいすべての行を表示する" という意味です。

対応する SQL は次のとおりです。

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

フィルターを作成するには、`powerbi-models` の BasicFilter クラスを使用します。

以前のバージョンのツールを使用する場合は、`window['powerbi-models']` によって window オブジェクト内のモデルのインスタンスを取得する必要があります。

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

ビジュアルは、コンストラクター内のビジュアルに提供されたホスト インターフェイス IVisualHost の applyJsonFilter() メソッドを使用してフィルターを呼び出します。

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="advanced-filter-api"></a>高度なフィルター API

[高度なフィルター API](https://github.com/Microsoft/powerbi-models) を使用すると、複数の条件 ("LessThan"、"Contains"、"Is"、"IsBlank" など) に基づく複雑なクロスビジュアルのデータ ポイント選択/フィルター処理クエリが可能になります。

このフィルターは、ビジュアル API 1.7.0 で導入されました。

高度なフィルター API には、`table` および `column` の名前を指定した `target` も必要です。 ただし、高度なフィルター API の演算子は `"And" | "Or"` です。 

さらに、フィルターでは、interface で値の代わりに条件を使用します。

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

`operator` パラメーターの条件演算子は、`"None" | "LessThan" | "LessThanOrEqual" | "GreaterThan" | "GreaterThanOrEqual" | "Contains" | "DoesNotContain" | "StartsWith" | "DoesNotStartWith" | "Is" | "IsNot" | "IsBlank" | "IsNotBlank"` です

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

対応する SQL は次のとおりです。

```sql
SELECT * FROM table WHERE col1 < 0;
```

高度なフィルター API を使用した完全なサンプルコードは、[`Sampleslicer visual` リポジトリ](https://github.com/Microsoft/powerbi-visuals-sampleslicer)にあります。

## <a name="tuple-filter-api-multi-column-filter"></a>タプル フィルター API (複数列フィルター)

タプル フィルター API は、ビジュアル API 2.3.0 で導入されました。

タプル フィルター API は基本フィルターに似ていますが、複数の列およびテーブルに対して条件を定義することができます。

また、フィルターにはインターフェイスがあります。 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

`target` は、テーブル名を持つ列の配列です。

```typescript
declare type ITupleFilterTarget = IFilterTarget[];
```

  フィルターは、さまざまなテーブルの列に対応できます。

`$schema` は "http://powerbi.com/product/schema#tuple" です

`filterType` は `FilterType.Tuple` です

`operator` では `"In"` 演算子の使用のみが許可されます

`values` はタプル値の配列です。各タプルは、ターゲット列の値の許可された 1 つの組み合わせを表します。 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

完全な例:

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the 1st column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for `Team` column of `DataTable` table
        },
        {
            value: 5 // the value for `Value` column of `DataTable` table
        }
    ],
    [
        // the 2nd column combination value (aka column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "http://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

**条件の列名と値の順序は区別されます。**

対応する SQL は次のとおりです。

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restoring-json-filter-from-dataview"></a>DataView からの JSON フィルターの復元

API 2.2 以降では、**JSON フィルター**は **VisualUpdateOptions** から復元できます。

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

ユーザーがブックマークを切り替え、ビジュアルが対応する `filter` オブジェクトを取得するとき、Power BI はビジュアルの `update` メソッドを呼び出します。
[ブックマーク サポートの詳細についてはこちらをご覧ください](bookmarks-support.md)

### <a name="sample-json-filter"></a>JSON フィルターのサンプル

![JSON フィルターのスクリーンショット](./media/json-filter.png)

### <a name="clear-json-filter"></a>JSON フィルターのクリア

フィルター API は、リセットまたはクリアとしてフィルターの `null` 値を受け入れます。

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
