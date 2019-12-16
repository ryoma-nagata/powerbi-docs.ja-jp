---
title: DAX:BLANK を値に変換しない
description: BLANK を値に変換する方法に関するガイダンス。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 2f70b98ed540a2e5b87e5a949e30b0c1c02069d1
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700388"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX:BLANK を値に変換しない

データ モデラーとして、メジャー式を記述するときに、意味のある値を返すことができない場合があります。 このような場合、代わりにゼロのような値を返したいと考えるかもしれません。 この設計が効率的で実用的であるかどうかを慎重に判断することをお勧めします。

BLANK の結果を明示的にゼロに変換する次のメジャー定義を検討します。

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

また、BLANK の結果をゼロに変換する別のメジャー定義を検討します。

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

[DIVIDE](/dax/divide-function-dax) 関数は、**Profit** メジャーを **Sales** メジャーで除算します。 結果がゼロまたは BLANK である場合、第 3 引数の代替結果 (オプション) が返されます。 この例では、ゼロが代替結果として渡されるため、メジャーは常に値を返すことが保証されます。

これらのメジャー設計は非効率的で、レポート設計品質が低下します。

レポート ビジュアルに追加されると、Power BI は、フィルター コンテキスト内のすべてのグループを取得しようとします。 多くの場合、大規模なクエリの結果を評価したり取得したりすると、レポートの表示が遅くなります。 各例では、疎な計算を効率的な密な計算に変換し、Power BI が必要以上にメモリを使用するようにします。

また、グループ化が多すぎると、レポート ユーザーを閉口させることも多くなります。

**Profit Margin** メジャーをテーブル ビジュアルに追加して、顧客別にグループ化するとどうなるかを見てみましょう。

![テーブル ビジュアルには、次の 3 つの列があります: Customer、Sales、Profit Margin。 テーブルには約 10 行のデータが表示されていますが、垂直スクロール バーから、表示できる行が他にも数多くあることがわかります。 Sales 列には値が表示されていません。 Profit Margin 列にはゼロのみが表示されています。](media/dax-avoid-converting-blank/table-visual-poor.png)

このテーブル ビジュアルには、膨大な数の行が表示されます  (実際にはモデルに 18,484 名の顧客が存在し、テーブルはそのすべてを表示しようとします)。ビュー内の顧客が売上を達成していないことに注目してください。 それにもかかわらず、**Profit Margin** メジャーから常に値が返るため、表示されています。

> [!NOTE]
> ビジュアルに表示するデータ ポイントが多すぎる場合、Power BI ではデータ削減戦略を使用して大きなクエリ結果を削除または集計することがあります。 詳細については、[ビジュアルの種類別のデータ ポイントの制限と戦略](../visuals/power-bi-data-points.md)に関する記事をご覧ください。

**Profit Margin** メジャーの定義が改善されるとどうなるかを見てみましょう。 **Sales** メジャーが BLANK (またはゼロ) でない場合にのみ、値が返されるようになりました。

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

テーブル ビジュアルには、現在のフィルター コンテキスト内で販売を行った顧客のみが表示されるようになりました。 メジャーが改善された結果、レポート ユーザーにとってより効率的で実用的なエクスペリエンスが得られます。

![同じテーブル ビジュアルに 4 行のデータが表示されるようになりました。 各行は、売上の値があり、Profit Margin の値がゼロ以外の顧客の行です。](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> 必要に応じて、[[データのない項目を表示する]](../desktop-show-items-no-data.md) オプションを有効にすることで、フィルター コンテキスト内の (値または BLANK を返す) すべてのグループを表示するようにビジュアルを構成できます。

## <a name="recommendation"></a>推奨事項

意味のある値が返すことができない場合、メジャーにより BLANK が返されるようにすることをお勧めします。

この設計方法は、Power BI でレポートをより速く表示でき、効果的です。 また、集計が BLANK の場合、既定ではレポートのビジュアルでグループ化が削除されるため、BLANK を返す方が望ましいのです。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Data Analysis Expressions (DAX) リファレンス](/dax/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
