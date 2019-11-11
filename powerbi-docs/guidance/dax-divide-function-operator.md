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
ms.openlocfilehash: c96518bb8de7f323b51a7e1e3f34f9d9bf056c79
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875383"
---
# <a name="dax-divide-function-vs-divide-operator-"></a>DAX:DIVIDE 関数と除算演算子 (/)

この記事は、DAX 式を定義するデータ モデラーを対象としています。

## <a name="background"></a>背景

分子を分母で除算する DAX 式を記述する場合に、[DIVIDE](/dax/divide-function-dax) 関数または除算演算子 (/ - スラッシュ) を使用することを選択できます。

DIVIDE 関数を使用する場合は、分子と分母の式で渡す必要があります。 必要に応じて、別の結果を表す値を渡すこともできます。

```dax

DIVIDE(<numerator>, <denominator> [,<alternateresult>])

```

DIVIDE 関数は、ゼロ除算を自動的に処理するように設計されています。 代替結果が渡されず、分母がゼロまたは空白の場合、関数は空白を返します。 代替結果が渡された場合は、空白の代わりにそれが返されます。

DIVIDE 関数では、最初に分母の値をテストする必要がないため、便利です。 この関数は、分母の値のテストにおいて、[IF](/dax/if-function-dax) 関数よりも最適化されています。 0 での除算のチェックは高コストであるため、パフォーマンスが大きく向上します。 また、DIVIDE を使用することで、より簡潔で洗練された式になります。

## <a name="example"></a>例

次のメジャー式は安全な除算を行いますが、4 つの DAX 関数を使用します。

```dax

=IF(OR(ISBLANK([Sales]), [Sales] == 0), BLANK(), [Profit] / [Sales])

```

このメジャー式では、同じ結果が得られますが、より効率性が高く洗練されています。

```dax

=DIVIDE([Profit], [Sales])

```

## <a name="recommendations"></a>推奨事項

分母がゼロまたは空白を返す_可能性がある_式である場合は常に、DIVIDE 関数を使用することをお勧めします。

分母が定数値の場合は、除算演算子を使用することをお勧めします。 この場合、除算は成功することが保証され、不要なテストを回避するため、式のパフォーマンスが向上します。

DIVIDE 関数で代替値を返す必要があるかどうかを慎重に検討する必要があります。 メジャーの場合、通常、空白を返すより優れたデザインです。 これは、集計が空白の場合、既定ではレポートのビジュアルでグループ化が削除されるためです。 これにより、データが存在するグループにビジュアルを集中させることができます。 必要に応じて、[データのない項目を表示する] オプションを有効にすることで、フィルター コンテキスト内の (値または空白を返す) すべてのグループを表示するようにビジュアルを構成できます。
