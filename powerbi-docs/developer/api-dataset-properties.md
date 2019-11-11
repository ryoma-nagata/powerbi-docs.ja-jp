---
title: Power BI データセット プロパティ
description: Power BI データセット API のプロパティについて説明します
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: b0fabcb5915a4f642abc1af03979a4597e2aa2f7
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73864959"
---
# <a name="dataset-properties"></a>データセットのプロパティ

データセット API の現行のバージョン 1 では、名前とテーブルのコレクションを使用したデータセットの作成にのみ対応しています。 各テーブルには名前を付け、列のコレクションを含めることができます。 各列には、名前とデータ型があります。 特にメジャーおよびテーブル間のリレーションシップをサポートすることで、これらのプロパティを大幅に拡張します。 このリリースでサポートするプロパティの完全な一覧を次に示します。

> [!IMPORTANT]
> [データセット操作グループ](https://docs.microsoft.com/rest/api/power-bi/datasets)に関するページからアクセスできます。

## <a name="dataset"></a>データセット

名前  |タイプ  |説明  |読み取り専用  |必須
---------|---------|---------|---------|---------
ID     |  Guid       | システム全体で一意である、データセットの識別子です。        | True        | False        
名前     | 文字列        | データセットのユーザー定義名です。        | False        | True        
tables     | テーブル[]        | テーブルのコレクションです。        |  False       | False        
relationships     | リレーションシップ[]        | テーブル間のリレーションシップのコレクションです。        | False        |  False  
defaultMode     | 文字列        | "Push" と "Streaming" の値で、データセットがプッシュされるか、ストリーミングされるか、またはその両方かを決定します。         | False        |  False

## <a name="table"></a>テーブル

名前  |タイプ  |説明  |読み取り専用  |必須
---------|---------|---------|---------|---------
名前     | 文字列        |  テーブルのユーザー定義名前です。 これは、テーブルの識別子としても使用されます。       | False        |  True       
列     |  列[]       |  列のコレクション。       | False        |  True       
メジャー     | メジャー[]        |  メジャーのコレクション。       | False        |  False       
isHidden     | ブール値        | true の場合、クライアント ツールにテーブルは表示されません。        | False        | False        

## <a name="column"></a>列

名前  |タイプ  |説明  |読み取り専用  |必須
---------|---------|---------|---------|---------
名前     |  文字列        | 列のユーザー定義名です。        |  False       | True       
dataType     |  文字列       |  サポートされている [EDM データ型](https://msdn.microsoft.com/library/ee382832.aspx) と制限事項です。 [データ型の制限事項](#DataTypeRestrictions) を参照してください。      |  False       | True        
formatString     | 文字列        | 値が表示されるときの値の書式設定を示す文字列です。 文字列の書式設定の詳細については、[「FORMAT_STRING Contents」](https://msdn.microsoft.com/library/ms146084.aspx) (FORMAT_STRING の内容) を参照してください。      | False        | False        
sortByColumn    | 文字列        |   同一テーブル内の列の文字列名であり、現在の列を並べ替えるために使用されます。     | False        | False       
dataCategory     | 文字列        |  この列のデータを説明するデータのカテゴリで使用される文字列です。 一般的に使用される値:Address、City、Continent、Country、Image、ImageUrl、Latitude、Longitude、Organization、Place、PostalCode、StateOrProvince、WebUrl       |  False       | False        
isHidden    |  ブール値       |  列がビューで非表示になっているかどうかを示すプロパティです。 既定値は false です。       | False        | False        
summarizeBy     | 文字列        |  列の既定の集計方法です。 含まれる値: default、none、sum、min、max、count、average、distinctCount     |  False       | False

## <a name="measure"></a>メジャー

名前  |タイプ  |説明  |読み取り専用  |必須
---------|---------|---------|---------|---------
名前     | 文字列        |  メジャーのユーザー定義名です。       |  False       | True        
expression     | 文字列        | 有効な DAX 式です。        | False        |  True       
formatString     | 文字列        |  値が表示されるときの値の書式設定を示す文字列です。 文字列の書式設定の詳細については、[「FORMAT_STRING Contents」](https://msdn.microsoft.com/library/ms146084.aspx) (FORMAT_STRING の内容) を参照してください。       | False        | False        
isHidden     | 文字列        |  true の場合、クライアント ツールにテーブルは表示されません。       |  False       | False       

## <a name="relationship"></a>リレーションシップ

名前  |タイプ  |説明  |読み取り専用  |必須 
---------|---------|---------|---------|---------
名前     | 文字列        | リレーションシップのユーザー定義名です。 リレーションシップの識別子としても使用されます。        | False       | True        
crossFilteringBehavior     | 文字列        |    リレーションシップのフィルターの方向:OneDirection (既定値)、BothDirections、Automatic       | False        | False        
fromTable     | 文字列        | 外部キー テーブルの名前です。        | False        | True         
fromColumn    | 文字列        | 外部キー列の名前です。        | False        | True         
toTable    | 文字列        | 主キー テーブルの名前です。        | False        | True         
toColumn     | 文字列        | 主キー列の名前です。        | False        | True        

<a name="DataTypeRestrictions"/>

## <a name="data-type-restrictions-applies-to-datatype-property"></a>データ型の制限 (dataType プロパティに適用される)

データ型  |制限事項  
---------|---------
Int64     |   Int64.MaxValue と Int64.MinValue が許可されまていせん。      
Double     |  Double.MaxValue と Double.MinValue 値が許可されていません。 NaN はサポートされていません。一部の関数では正の無限大と負の無限大がサポートされていません (例: Min、Max)。       
ブール値     |   True または False。
DateTime    |   データの読み込み中に、日時分数の値を 1/300 秒 (3.33ms) の整数倍に量子化します。      
文字列     |  現在のところ、文字列値あたり、最大 4,000 文字が許可されます。
小数|精度=28、スケール=4

## <a name="example"></a>例
次のコード サンプルには、上記のプロパティが複数含まれています。

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```