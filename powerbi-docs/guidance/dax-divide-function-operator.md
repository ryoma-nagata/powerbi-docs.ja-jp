---
title: DAX:DIVIDE 関数と除算演算子 (/)
description: DAX DIVIDE 関数を使用する場合のガイダンスです。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: v-pemyer
ms.openlocfilehash: c20a366ef657e851ef77a9649dbcc8b66b67dac0
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74695199"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX:DIVIDE 関数と除算演算子 (/)

データ モデラーとして、分子を分母で除算する DAX 式を記述する場合に、[DIVIDE](/dax/divide-function-dax) 関数または除算演算子 (/ - スラッシュ) を使用することを選択できます。

DIVIDE 関数を使用する場合は、分子と分母の式で渡す必要があります。 必要に応じて、_別の結果_を表す値を渡すこともできます。

```dax
DIVIDE(<numerator>, <denominator> [,<alternateresult>])
```

DIVIDE 関数は、ゼロ除算を自動的に処理するように設計されています。 代替結果が渡されず、分母がゼロまたは空白の場合、関数は空白を返します。 代替結果が渡された場合は、BLANK の代わりにそれが返されます。

DIVIDE 関数では、最初に分母の値をテストする必要がないため、便利です。 この関数は、分母の値のテストにおいて、[IF](/dax/if-function-dax) 関数よりも最適化されています。 0 での除算のチェックは高コストであるため、パフォーマンスが大きく向上します。 さらに DIVIDE を使用することで、より簡潔で洗練された式になります。

## <a name="example"></a>例

次のメジャー式は安全な除算を行いますが、4 つの DAX 関数を使用します。

```dax
Profit Margin =
IF(
    OR(
        ISBLANK([Sales]),
        [Sales] == 0
    ),
    BLANK(),
    [Profit] / [Sales]
)
```

このメジャー式では、同じ結果が得られますが、より効率性が高く洗練されています。

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

## <a name="recommendations"></a>推奨事項

分母がゼロまたは空白を返す_可能性がある_式である場合は常に、DIVIDE 関数を使用することをお勧めします。

分母が定数値の場合は、除算演算子を使用することをお勧めします。 この場合、除算は成功することが保証され、不要なテストを回避するため、式のパフォーマンスが向上します。

DIVIDE 関数で代替値を返す必要があるかどうかを慎重に検討してください。 メジャーの場合、通常、意味のある結果を評価できない場合は BLANK を返す方が優れた設計です。 詳細については、「[BLANK を値に変換しない](dax-avoid-converting-blank.md)」を参照してください。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
