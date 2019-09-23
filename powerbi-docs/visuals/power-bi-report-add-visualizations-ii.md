---
title: パート 2、Power BI レポートへの視覚化の追加
description: パート 2、Power BI レポートへの視覚化の追加
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c42d96fea37a6309908dd357425c3d0504e18397
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61410192"
---
# <a name="part-2-add-visualizations-to-a-power-bi-report"></a>パート 2、Power BI レポートへの視覚化の追加
[パート 1](power-bi-report-add-visualizations-ii.md) では、フィールド名の横にあるチェックボックスを選んで、基本的な視覚化を作成しました。  パート 2 では、ドラッグ アンド ドロップを使用し、 **[フィールド]** ウィンドウと **[視覚化]** をウィンドウを最大限活用して、視覚化を作成および変更する方法について説明します。

### <a name="prerequisites"></a>前提条件
- [パート 1](power-bi-report-add-visualizations-ii.md)
- Power BI Desktop - 視覚エフェクトは、Power BI サービスまたは Power BI Desktop を使ってレポートに追加できます。 このチュートリアルでは Power BI Desktop を使用します。 
- [小売りの分析のサンプル](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="create-a-new-visualization"></a>視覚化の新規作成
このチュートリアルでは、小売りの分析のデータセットを詳しく調べ、いくつかの主要な視覚化を作成します。

### <a name="open-a-report-and-add-a-new-blank-page"></a>レポートを開き、新しい空白のページを追加します。
1. 小売りの分析のサンプルの .PBIX ファイルを Power BI Desktop で開きます。 
   ![](media/power-bi-report-add-visualizations-ii/power-bi-open-desktop.png)   

2. キャンバスの下部にある黄色のプラス アイコンを選び、新しいページを追加します。

### <a name="add-a-visualization-that-looks-at-this-years-sales-compared-to-last-year"></a>この年と前年の売上比較を示す視覚化を追加します。
1. **[セールス]** テーブルで **[This Year Sales]** (今年の売上) >  **[値]** 、 **[Last Year Sales]** (前年の売上) を選びます。 Power BI によって縦棒グラフが作成されます。  興味深い内容であるため、詳しく分析していきましょう。 月別の売上はどのような状況でしょうか?  
   
   ![](media/power-bi-report-add-visualizations-ii/power-bi-barchart.png)
2. 時間テーブルから、 **[FiscalMonth]** を **[軸]** 領域までドラッグします。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-month.png)
3. [視覚化を面グラフに変更](power-bi-report-change-visualization-type.md)します。  選択できる視覚化には多くの種類があります。どの種類を使ったらよいか調べるには、[それぞれの種類についての説明、ベスト プラクティスのヒント、チュートリアル](power-bi-visualization-types-for-reports-and-q-and-a.md)をご覧ください。 [視覚化] ウィンドウで面グラフ アイコン ![](media/power-bi-report-add-visualizations-ii/power-bi-areachart.png) を選びます。
4. 視覚エフェクトを並べ替えるには、省略記号を選び、 **[Sort by FiscalMonth]\(月別に並べ替え\)** を選びます。
5. [視覚化のサイズを変更](power-bi-visualization-move-and-resize.md)するため、視覚化を選び、輪郭の円の 1 つをグラブしてドラッグします。 幅を広げればスクロール バーが不要になり、小さくすれば別の視覚化を追加する領域を確保できます。
   
   ![](media/power-bi-report-add-visualizations-ii/pbi_part2_7b.png)
6. [レポートを保存](../service-report-save.md)します。

### <a name="add-a-map-visualization-that-looks-at-sales-by-location"></a>場所別の売上を示すマップ視覚化を追加
1. **[Store]\(店舗\)** テーブルで **[Territory]** を選びます。 Power BI は [担当地域] が場所であることを認識するため、マップの視覚化を作成します。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map.png)
2. **[Total Stores]** (総店舗数) を [サイズ] 領域までドラッグします。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-map2.png)
3. 凡例を追加します。  店舗名別にデータを確認するには、 **[Chain]** (チェーン) を [凡例] 領域までドラッグします。  
   ![](media/power-bi-report-add-visualizations-ii/power-bi-legend.png)

## <a name="next-steps"></a>次の手順
* 「[Power BI での視覚化](power-bi-report-visualizations.md)」をご覧ください。  
* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

