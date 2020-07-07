---
title: 階層スライサーに複数のフィールドを追加する
description: 階層内に複数のフィールドを含む階層スライサーを作成する方法について説明します。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/11/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 2b9c4a8f4695f8d701eba535180194d29dd8bdec
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238177"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>階層スライサーに複数のフィールドを追加する

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

単一のスライサー内の複数の関連フィールドに対してフィルター処理を行う場合は、"*階層*" スライサーと呼ばれるものを作成することで、それを行います。 Power BI Desktop または Power BI サービスでこれらのスライサーを作成できます。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Power BI の階層スライサー":::

スライサーに複数のフィールドを追加すると、既定では、展開して次のレベルの項目を表示できる項目の横に矢印または "*シェブロン*" が表示されます。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Power BI の階層スライサーのドロップダウン":::
 
 
項目の 1 つ以上の子を選択すると、最上位レベルの項目に半選択された円が表示されます。
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Power BI での単一選択の階層スライサー":::

## <a name="format-the-slicer"></a>スライサーの書式設定

スライサーの動作は変更されていません。 スライサーのスタイルを指定することもできます。 たとえば、単一選択モードに設定できます。 または、リストとドロップダウンを入れ替えることができます。 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="ドロップダウン スライサーとして書式設定された階層スライサー":::

### <a name="change-the-expandcollapse-icon"></a>展開/折りたたみアイコンを変更する

階層スライサーには、他の書式設定オプションがいくつかあります。 展開/折りたたみアイコンを、既定の矢印からプラス/マイナス記号またはキャレットに変更できます。

1. スライサーを選択してから、 **[書式]** を選択します。
1. **[項目]** を展開し、 **[展開/折りたたみアイコン]** を選択します。
1. **[シェブロン]** 、 **[プラス/マイナス]** 、または **[キャレット]** から選択します。
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="階層スライサー用の展開/折りたたみアイコンを選択する":::
 
### <a name="change-the-indentation"></a>インデントを変更する

レポートの領域が狭い場合は、子項目をインデントする量を減らすことができます。 既定では、インデントは 15 ピクセルですが、それを増減できます。 

1. スライサーを選択してから、 **[書式]** を選択します。
1. **[項目]** を展開してから、 **[階段状レイアウトのインデント]** をドラッグして、値を小さくするか大きくします。 ボックスに数値を入力することもできます。

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="階層スライサーのインデントを設定する":::

## <a name="next-steps"></a>次の手順

- [Power BI のスライサー](../visuals/power-bi-visualization-slicers.md)
- 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。