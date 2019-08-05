---
title: オブジェクトとプロパティ
description: Power BI ビジュアルのカスタマイズ可能なプロパティ
author: MrMeison
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: c22a1cfb281c9902d490e2320b85c2f6bbb63468
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424610"
---
# <a name="object-and-properties"></a>オブジェクトとプロパティ

オブジェクトは、ビジュアルに関連付けられているカスタマイズ可能なプロパティを記述します。
各オブジェクトは複数のプロパティを持つことができ、各プロパティには型が関連付けられます。
型は、プロパティの内容を示します。 型の詳細については、以下を参照してください。

`myCustomObject` は、`dataView` および `enumerateObjectInstances` 内のオブジェクトを参照するために使用される内部名です

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>表示名

`displayName` は、プロパティ ウィンドウに表示される名前です。

## <a name="properties"></a>プロパティ

`properties` は、開発者によって定義されるプロパティのマップです。

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` は、スイッチを使用してオブジェクトを切り替えることができる特殊なプロパティです。

例:

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>プロパティの型

プロパティの型には、`ValueTypeDescriptor` と `StructuralTypeDescriptor` の 2 種類があります。

#### <a name="value-type-descriptor"></a>値型記述子

`ValueTypeDescriptor` は、通常はプリミティブ型で、通常は静的オブジェクトとして使用されます。
一般的な `ValueTypeDescriptor` をいくつか次に示します。

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>構造型記述子

`StructuralTypeDescriptor` は、主に、データ バインドされたオブジェクトに使用されます。
fill は、最も一般的な `StructuralTypeDescriptor` です

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>グラデーション プロパティ

グラデーション プロパティは、標準プロパティとして設定できないプロパティです。 代わりに、カラー ピッカー プロパティ (塗りつぶし型) の置換に関する規則を設定する必要があります。
次の例を参照してください。

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

`"fill"` プロパティと `"fillRule"` プロパティに注意してください。 1 つ目は、カラー ピッカーです。2 つ目は、グラデーションの置換規則で、規則条件が満たされるときに "fill" プロパティ `visually` を置き換えます。

fill プロパティと置換規則との間のこのリンクは、`"fillRule"` プロパティの `"rule"`->`"output"` セクションに設定されています。

`"Rule"`->`"InputRole"` は、規則 (条件) をトリガーするデータ ロールを設定します。 この例では、データ ロール `"Gradient"` にデータが含まれている場合、`"fill"` プロパティに規則が適用されます。

次に示すのは、fill 規則 (`the last item`) をトリガーするデータ ロールの例です。

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="enumerateobjectinstances-method"></a>`enumerateObjectInstances` メソッド

オブジェクトを効果的に使用するには、カスタム ビジュアルに `enumerateObjectInstances` という関数が必要です。 この関数は、プロパティ ウィンドウにオブジェクトを追加し、dataView 内でのオブジェクトのバインド先を決定します。  

一般的なセットアップは次のようになります。

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>プロパティ

`enumerateObjectInstances` のプロパティは、機能内に定義されたプロパティを反映します。 ページの下部の例を参照してください。

### <a name="objects-selector"></a>オブジェクト セレクター

`enumerateObjectInstances` のセレクターは、dataView 内でのオブジェクトのバインド先を決定します。 4 つの異なるオプションがあります。

#### <a name="static"></a>静的

このオブジェクトは、メタデータ `dataviews[index].metadata.objects` にバインドされます

```typescript
selector: null
```

#### <a name="columns"></a>列

このオブジェクトは、一致する `QueryName` を持つ列にバインドされます。

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>セレクター

このオブジェクトは、`selectionID` を作成した要素にバインドされます。 この例では、いくつかの dataPoint に対して `selectionID` が作成されていると仮定し、それらに対してループ処理を行います。

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>スコープ ID

このオブジェクトは、グループの共通部分の特定の値にバインドされます。 たとえば、カテゴリ `["Jan", "Feb", "March", ...]` と系列 `["Small", "Medium", "Large"]` がある場合に、`Feb` と `Large` に一致する値の共通部分にあるオブジェクトを見つけたいとします。 これを実現するには、両方の列の `DataViewScopeIdentity` を取得し、それらを変数 `identities` にプッシュして、セレクターで次の構文を使用することができます。

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>例

この例では、1 つのプロパティ `fill` を持つ customColor オブジェクトを含む 1 つの objectEnumeration を示します。 ここでは、このオブジェクトを `dataViews[index].metadata.objects` に静的にバインドしています

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
