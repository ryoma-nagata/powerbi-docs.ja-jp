---
title: スライサーに複数のフィールドを追加する
description: 階層内の複数のフィールドを含むスライサーを作成する方法について説明します。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: c41fa1e0c8510f64f9c6e53c83fe9ee8a2e75e67
ms.sourcegitcommit: 915cb7d8088deb0d9d86f3b15dfb4f6f5b1b869c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2020
ms.locfileid: "81006895"
---
# <a name="add-multiple-fields-to-a-slicer-preview"></a>スライサーに複数のフィールドを追加する (プレビュー)

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

1 つのスライサー内の複数の関連フィールドに対してフィルター処理を行う場合は、"*階層*" スライサーと呼ばれるものを作成します。 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Power BI の階層スライサー":::

このプレビュー機能を有効にするには、 **[ファイル]** メニュー > **[オプションと設定]**  >  **[オプション]** を選択します。 **[グローバル]** で、 **[プレビュー機能]** セクションにアクセスし、 **[Hierarchy slicer]\(階層スライサー\)** がオンになっていることを確認します。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-preview.png" alt-text="階層スライサー プレビュー機能を選択する":::

スライサーに複数のフィールドを追加すると、アイテムの横に矢印または "*シェブロン*" が表示されます。それを展開して次のレベルの項目を表示できます。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Power BI の階層スライサーのドロップダウン":::
 
スライサーの動作は変更されていません。 リストとドロップダウンを入れ替えることはできます。スライサーのスタイルを希望に合わせて指定することもできます。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="ドロップダウン スライサーとして書式設定された階層スライサー":::
 
単一選択モードに設定できます。 一部の子が選択されている項目に対して、半選択された円が表示されます。
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Power BI での単一選択の階層スライサー":::

## <a name="next-steps"></a>次の手順

- [Power BI のスライサー](../visuals/power-bi-visualization-slicers.md)
- 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。