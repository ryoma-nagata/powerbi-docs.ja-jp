---
title: レポート フィルター ウィンドウの概要
description: コンシューマー向け Power BI サービス内のレポートにフィルターを追加する方法
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ef7e4f556832f1323043a80cf219678a16511c9e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532809"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>レポート フィルター ウィンドウの使用方法

この記事では、Power BI サービスのレポートの **[フィルター]** ウィンドウについて説明します。 このフィルターを使用すると、お使いのデータの新しい分析情報を得ることができます。

Power BI でデータをフィルター処理方法は多数あります。 フィルターの詳細については、[Power BI レポートでのフィルターと強調表示](../power-bi-reports-filters-and-highlighting.md)に関するページをご覧ください。

![矢印が [フィルター] オプションを指しているブラウザー上のレポートのスクリーンショット。](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>レポート フィルター ウィンドウの操作

同僚とレポートを共有する場合は、必ず **[フィルター]** ウィンドウを探してください。 レポートの右端に沿って折りたたまれている場合があります。 それを選択して展開します。

![[フィルター] ウィンドウが展開されているレポートのスクリーン ショット。](media/end-user-report-filter/power-bi-filter-pane.png)

**[フィルター]** ウィンドウには、レポート *デザイナー*によってレポートに追加されたフィルターが含まれています。 お客様のような*コンシューマー*は、既存のフィルターを操作して、その変更内容を保存できますが、新しいフィルターをレポートに追加することはできません。 たとえば、上のスクリーンショットでは、デザイナーによって 2 つのページ レベル フィルターが追加されています:**セグメント**と**年**です。 これらのフィルターを操作して変更することはできますが、3 番目のページ レベル フィルターを追加することはできません。

Power BI サービスでは、 **[フィルター]** ウィンドウで加えたすべての変更はレポートに保持されます。 それらの変更は、サービスによってレポートのモバイル バージョンに回されます。

**[フィルター]** ウィンドウを設計者の既定値にリセットするには、![[既定値にリセット] オプションのスクリーンショット](media/end-user-report-filter/power-bi-reset.png) を 上部のメニュー バーから選択します。

## <a name="view-all-the-filters-for-a-report-page"></a>レポート ページのすべてのフィルターを表示する

**[フィルター]** ウィンドウには、デザイナーによってレポートに追加されたすべてのフィルターが表示されます。 **[フィルター]** ウィンドウは、フィルターに関する情報を表示し、それらを操作できる領域でもあります。 加えた変更を保存したり、 **[既定値にリセット]** を使用したりすると、フィルターを元の設定に戻すことができます。

保存したい変更がある場合は、個人用ブックマークを作成することもできます。  詳細については、[ブックマーク](end-user-bookmarks.md)に関するページをご覧ください。

**[フィルター]** ウィンドウでは、いくつかの種類のレポート フィルターが表示および管理されます。 これらは、ビジュアル、レポート ページ、およびレポート全体に適用できます。

この例では、2 個のフィルターがあるビジュアルが選択されています。 レポート ページにも、 **[このページでフィルター]** という見出しの下にフィルターがあります。 また、レポート全体にも **[日付]** フィルターがあります。

![ビジュアルとそれに関連するフィルターが呼び出されたレポートのスクリーンショット。](media/end-user-report-filter/power-bi-all-filters2.png)

一部のフィルターの横には **(すべて)** があります。 **(すべて)** とは、フィルターにすべての値が含まれていることを意味します。 上のスクリーンショットの **[Segment(All)]** \(セグメント (すべて)\) は、このレポート ページにすべての製品セグメントに関するデータが含まれることを示します。 **[Region is West]** \(リージョンは西\) ページ レベル フィルターを選択した場合、レポート ページには西リージョンのデータのみが含まれます。

このレポートを表示するユーザーは、だれでもこれらのフィルターを操作できます。

### <a name="view-only-those-filters-applied-to-a-visual"></a>ビジュアルに適用されたフィルターのみを表示する

特定のビジュアルに適用されたフィルターの詳細を知るには、ビジュアルの上にマウスを置き、フィルター アイコン ![フィルター アイコンのスクリーン ショット](media/end-user-report-filter/power-bi-filter-icon.png) を表示します。 そのフィルター アイコンを選択し、そのビジュアルに影響するすべてのフィルターやスライサーなどが含まれるポップアップを表示します。 ポップアップ上のフィルターは、 **[フィルター]** ウィンドウに表示されるものと同じです。

![それらのフィルターが [フィルター] ウィンドウのどこを指すかを矢印が示す、フィルター一覧のスクリーンショット。](media/end-user-report-filter/power-bi-hover-visual-filter.png)

このビューで表示できるフィルターの種類は次のとおりです。

- 基本フィルター

- スライサー

- クロス強調表示

- クロス フィルター処理

- 高度なフィルター

- 上位 N のフィルター

- 相対日付フィルター

- 同期スライサー

- 含める/除外するフィルター

- URL を使って渡されるフィルター

次の例では、以下がわかります。

1. 縦棒グラフがクロス フィルター処理されています。

1. **含む**は**セグメント**用のクロス フィルター処理であり、3 つが含まれています。

1. **四半期**にスライサーが適用されています。

1. このレポート ページには**リージョン** フィルターが適用されており、

1. このビジュアルには **isVanArsdel** と**年**のフィルターが適用されています。

![上の番号付きのリストと一致するように、フィルターの一覧が番号付けされたレポートとそのフィルターのスクリーンショット。](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>フィルターで検索する

フィルターには、値が多数あることがあります。 検索ボックスを使用すると、目的の値を検索して選択できます。

![フィルターで検索する方法を示すスクリーンショット。](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>フィルターの詳細を表示

フィルターについて理解するには、利用可能な値とその数を確認します。  フィルターの詳細を表示するには、フィルター名の横にある矢印の上にカーソルを置いて選択します。
  
![西リージョンが選択されたフィルターのスクリーンショット。](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>フィルター選択の変更

データの分析情報を検索する方法の 1 つには、フィルターの操作があります。 選択されているフィルターを変更するには、フィールド名の横のドロップダウン矢印を使用します。  フィルターおよび Power BI がフィルター処理するデータの種類に応じて、オプションは一覧からの単純な選択から、日付または数値の範囲の識別におよびます。 下記の詳細フィルターでは、ツリーマップの **[Total Units YTD]** \(個数合計 YTD\) フィルターを 2,000 と 3,000 に変更しました。 この変更により、ツリーマップから Prirum が削除されたことに着目してください。
  
![Fashions Direct が選択されたレポートとそのフィルターのスクリーンショット。](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> 一度に 1 つ以上のフィルター値を選択するには、CTRL キーを押しながら保持します。 ほとんどのフィルターでは、複数の選択がサポートされています。

### <a name="reset-filter-to-default"></a>フィルターを既定にリセットする

フィルターに加えたすべての変更を取り消すには、上部のメニュー バーから **[既定値にリセット]** を選択します。  この選択により、フィルターはレポート デザイナーで設定された元の状態に戻ります。

![[既定値にリセット] オプションのスクリーンショット。](media/end-user-report-filter/power-bi-reset.png)

### <a name="clear-a-filter"></a>フィルターのクリア

**(すべて)** に設定するフィルターが 1 つのみの場合、フィルター名の横の消しゴム アイコン ![消しゴム アイコンのスクリーン ショット](media/end-user-report-filter/power-bi-eraser-icon.png) を 選択してそれを消去します。
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>次の手順

[レポート ページでビジュアル相互間でクロスフィルター処理とクロス強調表示を行う](end-user-interactions.md)方法と理由について