---
title: データ ビューのマッピング
description: データをビジュアルに渡す前に Power BI がそれを変換する方法
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ff70b2f12921694617a736164484df1326471eea
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425185"
---
# <a name="data-view-mappings-in-power-bi-visuals"></a>Power BI ビジュアルでのデータ ビューのマッピング

`dataViewMappings` では、データ ロールが相互にどのように関連しているかを記述し、それらの条件付き要件を指定することができます。
`dataMappings` ごとに 1 つのセクションがあります。

有効な各マッピングでは `DataView` が生成されますが、現時点では、ビジュアルごとに 1 つのクエリのみを実行するようにサポートしているため、ほとんどの状況で 1 つの `DataView` のみ生成されます。 ただし、次のようなさまざまな条件を使用して複数のデータ マッピングを提供できます。

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "single": { ... },
        "table": { ... },
        "matrix": { ... }
    }
]
```

> [!NOTE]
> 重要な点として、有効なマッピングが `dataViewMappings` で指定されている場合のみ、Power BI で DataView へのマッピングが作成されるということに注意してください。

つまり、次の例のように、`categorical` が `dataViewMappings` で定義されていて、`table` や `single` などの他のマッピングが定義されていないとします。
```json
"dataViewMappings": [
    {
        "categorical": { ... }
    }
]
```

Power BI では、1 つの `categorical` のマッピングを持つ `DataView` が生成されます (`table` およびその他のマッピングは `undefined` になります)。
```javascript
{
    "categorical": {
        "categories": [ ... ],
        "values": [ ... ]
    },
    "metadata": { ... }
}
```

## <a name="conditions"></a>条件

特定のデータ マッピングに対する条件を記述します。 複数の条件セットを指定できます。記述されている条件セットのいずれかにデータが一致する場合、ビジュアルによってデータが有効なものとして受け入れられます。

現時点では、フィールドごとに最小値と最大値を指定できます。 これは、そのデータ ロールにバインドできるフィールドの数を表します。 

> [!NOTE]
> 条件でデータ ロールが省略されている場合は、任意の数のフィールドを持つことができます。

### <a name="example-1"></a>例 1

各データ ロールに複数のフィールドをドラッグできます。 この例では、category を 1 つのデータ フィールドに制限し、measure を 2 つのデータ フィールドに制限しています。

```json
"conditions": [
    { "category": { "max": 1 }, "y": { "max": 2 } },
]
```

### <a name="example-2"></a>例 2

この例では、2 つの条件のいずれか 1 つが必要です。 データ フィールドを厳密に category を 1 つ、measure を 2 つとするか、または厳密に category を 2 つ、measure を 1 つとします。

```json
"conditions": [
    { "category": { "min": 1, "max": 1 }, "measure": { "min": 2, "max": 2 } },
    { "category": { "min": 2, "max": 2 }, "measure": { "min": 1, "max": 1 } }
]
```

## <a name="single-data-mapping"></a>単一のデータ マッピング

単一のデータ マッピングは、最も単純な形式のデータ マッピングです。 1 つの measure フィールドを受け取り、合計を返します。 フィールドが数値の場合、合計を返します。 それ以外の場合、一意の値の数を返します。

単一のデータ マッピングを使用するには、マップするデータ ロールの名前を定義する必要があります。 このマッピングは、1 つの measure フィールドに対してのみ機能します。 2 番目のフィールドが割り当てられている場合、データ ビューは生成されません。 したがって、データを 1 つのフィールドに制限する条件を含めることもお勧めします。

> [!NOTE]
> このデータ マッピングは、他のデータ マッピングと組み合わせて使用することはできません。 データを 1 つの数値に減らすことを目的としています。

### <a name="example-3"></a>例 3

```json
"dataViewMappings": {
    "conditions": [
        { "Y": { "max": 1 } }
    ],
    "single": {
        "role": "Y"
    }
}  
```

結果のデータ ビューには他の種類 (テーブル、カテゴリ別など) も含まれますが、各マッピングに含まれるのは 1 つの値のみです。 single の値のみにアクセスすることをお勧めします。

```JSON
{
    "dataView": [
        {
            "metadata": null,
            "categorical": null,
            "matrix": null,
            "table": null,
            "tree": null,
            "single": {
                "value": 94163140.3560001
            }
        }
    ]
}
```

## <a name="categorical-data-mapping"></a>カテゴリ別のデータ マッピング

カテゴリ別のデータ マッピングは、1 つまたは 2 つの独立したデータ グループを取得するために使用されます。

### <a name="example-4"></a>例 4

DataRoles の前の例の定義を次に示します。

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    }
]
```

マッピングは次のようになります。

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "select": [
                { "bind": { "to": "measure" } }
            ]
        }
    }
}
```

これは単純な例で、簡単に言えば次のようになります。「`category` DataRole のマップで、`category` にドラッグするすべてのフィールドについて、そのデータが `categorical.categories` にマップされるようにします。 また、`measure` DataRole を `categorical.values` にマップします。」

* **for...in** - このデータ ロール内のすべての項目について、それらをデータ クエリに含めます。
* **bind...to** - for...in と同じ結果が生成されますが、それを 1 つのフィールドに制限する条件を DataRole が持つことが想定されています。

### <a name="example-5"></a>例 5

この例では、前の例の最初の 2 つの DataRoles を使用し、さらに `grouping` と `measure2` を定義します。

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Grouping with",
        "name": "grouping",
        "kind": "Grouping"
    },
    {
        "displayName": "X Axis",
        "name": "measure2",
        "kind": "Grouping"
    }
]
```

マッピングは次のようになります。

```json
"dataViewMappings":{
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "group": {
                "by": "grouping",
                "select":[
                    { "bind": { "to": "measure" } },
                    { "bind": { "to": "measure2" } }
                ]
            }
        }
    }
}
```

ここでの違いは、categorical.values をどのようにマップするかという点です。 ここでは、「`measure` および `measure2` のデータ ロールを、データ ロール `grouping` によってグループ化されるようにマップします」ということを示しています。

### <a name="example-6"></a>例 6

dataRoles を次に示します。

```json
"dataRoles": [
    {
        "displayName": "Categories",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measures",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Series",
        "name": "series",
        "kind": "Measure"
    }
]
```

dataViewMapping を次に示します。

```json
"dataViewMappings": [
    {
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "group": {
                    "by": "series",
                    "select": [{
                            "for": {
                                "in": "measure"
                            }
                        }
                    ]
                }
            }
        }
    }
]
```

カテゴリ別の `dataview` は次のように視覚化できます。

| カテゴリ別 |  |  | | | |
|-----|-----|------|------|------|------|
| | 年 | 2013 | 2014 | 2015 | 2016 |
| 国 | | |
| 米国 | | x | x | 125 | 100 |
| カナダ | | x | 50 | 200 | x |
| メキシコ | | 300 | x | x | x |
| 英国 | | x | x | 75 | x |

Power BI ではそれがカテゴリ別 dataview として生成されます。 これはカテゴリのセットです。

```JSON
{
    "categorical": {
        "categories": [
            {
                "source": {...},
                "values": [
                    "Canada",
                    "Mexico",
                    "UK",
                    "USA"
                ],
                "identity": [...],
                "identityFields": [...],
            }
        ]
    }
}
```

各カテゴリは値のセットにもマップされます。 これらの値はそれぞれ系列 (年) でグループ化されます。

たとえば、2013 年のカナダの売上は null で、2014 年のカナダの売上は 50 です。

```JSON
{
    "values": [
        {
            "source": {...},
            "values": [
                null,
                300,
                null,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                50,
                null,
                150,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                200,
                null,
                null,
                125
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                null,
                null,
                null,
                100
            ],
            "identity": [...],
        }
    ]
}
```

## <a name="table-data-mapping"></a>テーブルのデータ マッピング

テーブルのデータ ビューは、単純なデータ マッピングです。 基本的には、これは数値データ ポイントを集計できるデータ ポイントの一覧です。

### <a name="example-7"></a>例 7

特定の機能を指定:

```json
"dataRoles": [
    {
        "displayName": "Values",
        "name": "values",
        "kind": "Measure"
    }
]
```

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                }
            }
        }
    }
]
```

テーブルの `dataview` は次のように視覚化できます。  

| 国| 年 | Sales |
|-----|-----|------|
| 米国 | 2016 | 100 |
| 米国 | 2015 | 50 |
| カナダ | 2015 | 200 |
| カナダ | 2015 | 50 |
| メキシコ | 2013 | 300 |
| 英国 | 2014 | 150 |
| 米国 | 2015 | 75 |

Power BI ではそれがテーブル dataview として生成されます。 順序があるとは考えないでください。

```JSON
{
    "table" : {
        "columns": [...],
        "rows": [
            [
                "Canada",
                2014,
                50
            ],
            [
                "Canada",
                2015,
                200
            ],
            [
                "Mexico",
                2013,
                300
            ],
            [
                "UK",
                2014,
                150
            ],
            [
                "USA",
                2015,
                100
            ],
            [
                "USA",
                2015,
                75
            ],
            [
                "USA",
                2016,
                100
            ]
        ]
    }
}
```

データを集計するには、目的のフィールドを選択して [合計] をクリックします。  

![データの集計](./media/data-aggregation.png)

## <a name="matrix-data-mapping"></a>マトリックスのデータ マッピング

マトリックスのデータ マッピングはテーブルのデータ マッピングに似ていますが、行が階層的に表示されます。 また、`dataRole` 値の 1 つを列ヘッダー値として使用することもできます。

```json
{
    "dataRoles": [
        {
            "name": "Category",
            "displayName": "Category",
            "displayNameKey": "Visual_Category",
            "kind": "Grouping"
        },
        {
            "name": "Column",
            "displayName": "Column",
            "displayNameKey": "Visual_Column",
            "kind": "Grouping"
        },
        {
            "name": "Measure",
            "displayName": "Measure",
            "displayNameKey": "Visual_Values",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "matrix": {
                "rows": {
                    "for": {
                        "in": "Category"
                    }
                },
                "columns": {
                    "for": {
                        "in": "Column"
                    }
                },
                "values": {
                    "select": [
                        {
                            "for": {
                                "in": "Measure"
                            }
                        }
                    ]
                }
            }
        }
    ]
}
```

Power BI によって階層データ構造が作成されます。 ツリーのルートには、`Category` データ ロールの最初の列のデータと、データ ロールの 2 番目の列の子が含まれます。

データセット:

| 親 | 子 | 孫 | 列 | 値 |
|-----|-----|------|-------|-------|
| Parent1 | Child1 | Grand child1 | Col1 | 5 |
| Parent1 | Child1 | Grand child1 | Col2 | 6 |
| Parent1 | Child1 | Grand child2 | Col1 | 7 |
| Parent1 | Child1 | Grand child2 | Col2 | 8 |
| Parent1 | Child2 | Grand child3 | Col1 | 5 |
| Parent1 | Child2 | Grand child3 | Col2 | 3 |
| Parent1 | Child2 | Grand child4 | Col1 | 4 |
| Parent1 | Child2 | Grand child4 | Col2 | 9 |
| Parent1 | Child2 | Grand child5 | Col1 | 3 |
| Parent1 | Child2 | Grand child5 | Col2 | 5 |
| Parent2 | Child3 | Grand child6 | Col1 | 1 |
| Parent2 | Child3 | Grand child6 | Col2 | 2 |
| Parent2 | Child3 | Grand child7 | Col1 | 7 |
| Parent2 | Child3 | Grand child7 | Col2 | 1 |
| Parent2 | Child3 | Grand child8 | Col1 | 10 |
| Parent2 | Child3 | Grand child8 | Col2 | 13 |

Power BI のコア マトリックス ビジュアルでは、それがテーブルのようにレンダリングされます。

![マトリックス ビジュアル](./media/matrix-visual-smaple.png)

ビジュアルはデータ構造を次に示すように取得します (最初の 2 つの行のみが示されます)。

```json
{
    "metadata": {...},
    "matrix": {
        "rows": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Parent1",
                        "identity": {...},
                        "childIdentityFields": [...],
                        "children": [
                            {
                                "level": 1,
                                "levelValues": [...],
                                "value": "Child1",
                                "identity": {...},
                                "childIdentityFields": [...],
                                "children": [
                                    {
                                        "level": 2,
                                        "levelValues": [...],
                                        "value": "Grand child1",
                                        "identity": {...},
                                        "values": {
                                            "0": {
                                                "value": 5 // value for Col1
                                            },
                                            "1": {
                                                "value": 6 // value for Col2
                                            }
                                        }
                                    },
                                    ...
                                ]
                            },
                            ...
                        ]
                    },
                    ...
                ]
            }
        },
        "columns": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col1",
                        "identity": {...}
                    },
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col2",
                        "identity": {...}
                    },
                    ...
                ]
            }
        },
        "valueSources": [...]
    }
}
```

## <a name="data-reduction-algorithm"></a>データの削減アルゴリズム

DataView で受信するデータ量を制御する場合、`DataReductionAlgorithm` を適用できます。

既定では、すべてのカスタム ビジュアルには、"count" が1000 のデータ ポイントに設定された top DataReductionAlgorithm が適用されます。 これは capabilities.json の次のプロパティを設定することと同じです。

```json
"dataReductionAlgorithm": {
    "top": {
        "count": 1000
    }
}
```

"count" 値は 30000 までの任意の整数値に変更できます。 R ベースのカスタム ビジュアルでは最大 150000 行をサポートできます。

## <a name="data-reduction-algorithm-types"></a>データの削減アルゴリズムの種類

`DataReductionAlgorithm` の設定には次の 4 つの種類があります。

* `top` - データセットの先頭から取得した値にデータを制限する場合。 先頭から "count" 個の値がデータセットから取得されます。
* `bottom` - データセットの末尾から取得した値にデータを制限する場合。 末尾から "count" 個の値がデータセットから取得されます。
* `sample` - "count" 個の項目に制限された単純なサンプリング アルゴリズムによってデータセットを減らします。 これは、最初と最後の項目と、それらの間にある等間隔の "count" 個の項目が含まれることを意味します。
たとえば、データ セットが [0, 1, 2,...100] で、`count: 9` の場合、[0, 10, 20 ...100] を受け取ります
* `window` - "count" 個の要素を含む、ある時点のデータ ポイントの 1 つの "ウィンドウ" を読み込みます。 現時点では、`top` と `window` は同等です。 ウィンドウ設定を完全にサポートするための取り組みを進めています。

## <a name="data-reduction-algorithm-usage"></a>データの削減アルゴリズムの使用

`DataReductionAlgorithm` は、カテゴリ別、テーブル、またはマトリックスの `dataview` マッピングで使用できます。

これは、`categories` または `values` のグループ セクション (カテゴリ別のデータ マッピングに対して) に設定できます。

### <a name="example-8"></a>例 8

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" },
            "dataReductionAlgorithm": {
                "window": {
                    "count": 300
                }
            }  
        },
        "values": {
            "group": {
                "by": "series",
                "select": [{
                        "for": {
                            "in": "measure"
                        }
                    }
                ],
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 100
                    }
                }  
            }
        }
    }
}
```

データ削減アルゴリズムは、テーブル `dataview` マッピングの `rows` セクションに適用できます。

### <a name="example-9"></a>例 9

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 2000
                    }
                } 
            }
        }
    }
]
```

データ削減アルゴリズムは、`matrix` `dataview` マッピングの `rows` または `columns` セクション (あるいはその両方) に適用できます。
