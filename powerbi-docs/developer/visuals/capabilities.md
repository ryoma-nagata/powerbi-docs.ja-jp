---
title: capabilities
description: Power BI ビジュアルの capabilities とプロパティ
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: f6bb4293a44f98f2f8098fb197c7b406b618d211
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425461"
---
# <a name="power-bi-visual-capabilities"></a>Power BI ビジュアルの capabilities

capabilities では、ビジュアルに関する情報がホストに提供されます。 Capabilities モデルのすべてのプロパティは、省略可能です`optional`

ビジュアルの capabilities のルート オブジェクトは、`dataRoles` や `dataViewMappings` などです。

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-your-visual-expects---dataroles"></a>ビジュアルに必要なデータ フィールドを定義する - `dataRoles`

データにバインドできるフィールドを定義するには、`DataViewRole` オブジェクトの配列を受け取る `dataRoles` 使用します。これにより、必要なすべてのプロパティが定義されます。

### <a name="properties"></a>プロパティ

* **name** - このデータ フィールドの内部名 (一意である必要があります)
* **kind** - フィールドの種類:
    * `Grouping` - メジャー フィールドのグループ化に使用される離散値
    * `Measure` - 数値データ値
    * `GroupingOrMeasure` - グループ化またはメジャーとして使用できます
* **displayName** - プロパティ ウィンドウでユーザーに表示される名前
* **description** - フィールドの簡単な説明 (省略可能)
* **requiredtypes** - このデータ ロールに必要なデータの種類。 一致しない値はすべて null に設定されます (省略可能)
* **preferredTypes** - このデータ ロールで優先されるデータの型 (省略可能)

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>"requiredTypes" と "preferredTypes" で有効なデータ型

* **bool** - ブール値
* **integer** - 整数値
* **numeric** - 数値
* **text** - テキスト値
* **geography** - 地理データ

### <a name="example"></a>例

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

上記のデータ ロールでは、次のフィールドが作成されます

![データ ロールの表示](./media/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped---dataviewmappings"></a>データのマップ方法を定義する - `dataViewMappings`

DataViewMapping では、データ ロールが相互にどのように関連しているかを説明し、それらの条件付き要件を指定することができます。

ほとんどのビジュアルでは 1 つのマッピングが提供されますが、複数の dataViewMapping を指定することができます。 有効な各マッピングで DataView が生成されます。 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

[DataViewMappings の詳細についてはこちらを参照してください](dataview-mappings.md)

## <a name="define-property-pane-options---objects"></a>プロパティ ウィンドウのオプションを定義する - `objects`

オブジェクトでは、ビジュアルに関連付けられているカスタマイズ可能なプロパティについて説明します。
各オブジェクトに複数のプロパティを含めることができ、各プロパティには型が関連付けられています。
型は、プロパティがどのようになるかを示します。 型の詳細については、以下を参照してください。

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

[オブジェクトの詳細についてはこちらを参照してください](objects-properties.md)

## <a name="handle-partial-highlighting---supportshighlight"></a>部分的な強調表示を処理する - `supportsHighlight`

既定では、この値は false に設定されています。これは、ページ上の何かが選択されると "値" が自動的にフィルター処理されることを意味します。これにより、選択された値のみを表示するようにビジュアルが更新されます。 完全なデータを表示するが、選択された項目のみを強調表示したい場合は、capabilities.json で `supportsHighlight` を true に設定する必要があります。

[強調表示の詳細についてはこちらを参照してください](highlight.md)

## <a name="handle-advanced-edit-mode---advancededitmodesupport"></a>高度な編集モードを処理する - `advancedEditModeSupport`

ビジュアルでは、高度な編集モードのサポートを宣言できます。
capabilities json で特に指定されていない限り、既定では、ビジュアルで高度な編集モードはサポートされません。

[advancedEditModeSupport の詳細についてはこちらを参照してください](advanced-edit-mode.md)

## <a name="data-sorting-options-for-visual---sorting"></a>ビジュアルのデータ並べ替えオプション - `sorting`

ビジュアルでは、その capabilities を使用して並べ替え動作を定義できます。
capabilities.json に特に明記されていない限り、既定では、ビジュアルで並べ替え順序の変更はサポートされません。

[並べ替えの詳細についてはこちらを参照してください](sort-options.md)
