---
title: DAX:VALUES の代わりに SELECTEDVALUE を使用する
description: SELECTEDVALUE 関数を使用する場合のガイダンスです。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: v-pemyer
ms.openlocfilehash: 6aef2c06cc62668ea7dea9fe404e294d1a5faa93
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "74700480"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX:VALUES の代わりに SELECTEDVALUE を使用する

データ モデル作成者は、列が特定の値によってフィルター処理されるかどうかをテストする DAX 式を記述する必要が生じることがあります。

以前のバージョンの DAX では、3 つの DAX 関数を含むパターンを使用して、この要件を安全に実現できました。 これらの関数は、[IF](/dax/if-function-dax)、[HASONEVALUE](/dax/hasonevalue-function-dax)、および [VALUES](/dax/values-function-dax) です。 次のメジャー定義は、その例を示しています。 この定義では、オーストラリアの顧客に対する売上のみについて、売上税が計算されます。

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

この例では、1 つの値によって **Country-Region** 列がフィルター処理される場合にのみ、HASONEVALUE 関数によって TRUE が返されます。 TRUE の場合、VALUES 関数はリテラル テキスト "Australia" と比較されます。 VALUES 関数によって TRUE が返されると、**Sales** メジャーが 0.10 (10%) で乗算されます。 複数の値によって列がフィルター処理されるために HASONEVALUE 関数によって FALSE が返された場合は、最初の IF 関数によって BLANK が返されます。

HASONEVALUE は、防御的な手法として使用します。 複数の値によって **Country-Region** 列がフィルター処理される可能性があるため、この関数は必須です。 この場合、VALUES 関数によって複数の行から成るテーブルが返されます。 複数行のテーブルがスカラー値と比較されると、エラーになります。

## <a name="recommendation"></a>推奨事項

[SELECTEDVALUE](/dax/selectedvalue-function) 関数を使用することをお勧めします。 これにより、この記事で説明されているパターンと同じ結果を、より効率的かつ円滑に得ることができます。

ここで、SELECTEDVALUE 関数を使用して、メジャー定義の例を書き直します。

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> SELECTEDVALUE 関数に "_代替結果_" 値を渡すことができます。 列にフィルターが適用されないか、または複数のフィルターが適用されると、代替結果値が返されます。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
