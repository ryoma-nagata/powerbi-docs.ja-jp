---
title: 主要業績評価指標 (KPI) ビジュアル
description: Power BI で主要業績評価指標 (KPI) ビジュアルを作成します
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6EpqaO0
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8fa39c7cc57e24f0c19e1a484c0e925bfeec94f7
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389693"
---
# <a name="key-performance-indicator-kpi-visuals"></a>主要業績評価指標 (KPI) ビジュアル

主要業績評価指標 (KPI) は、測定可能な目標に対する進捗状況を視覚的に伝える方法の 1 つです。 KPI の詳細については、「[PowerPivot の主要業績評価指標 (KPI)](/previous-versions/sql/sql-server-2012/hh272050(v=sql.110))」を参照してください。

Will が単一のメトリック ビジュアル (ゲージ、カード、KPI) を作成するのをご覧ください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-kpi"></a>KPI を使用する場合

KPI は、次のような場合に最適です。

* 進行状況を測定する。 "目標より進んでいるか、または遅れているか" という疑問に答えます。

* 目標までの距離を測定する。 "どの程度進んでいるか、または遅れているか" という疑問に答えます。

## <a name="kpi-requirements"></a>KPI の要件

デザイナーは、特定のメジャーに対する KPI ビジュアルに基づきます。 KPI の目的は、定義済みのターゲットに対する現在の値とメトリックの状態を評価できるようにすることです。 KPI ビジュアルには、値に対して評価される "*基本*" メジャー、"*ターゲット*" となるメジャーまたは値、および "*しきい値*" または "*目標*" が必要です。

KPI データセットには KPI の目標値が含まれている必要があります。 データセットに目標値が含まれていない場合は、目標が含まれる Excel シートをデータ モデルまたは PBIX ファイルに追加することによって作成できます。

## <a name="prerequisites"></a>前提条件

Power BI にサインアップしていない場合は、[無料の試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)してください。

* [Power BI Desktop](https://powerbi.microsoft.com/get-started/) - 無料

* [小売りの分析のサンプル PBIX ファイル](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="how-to-create-a-kpi"></a>KPI を作成する方法

理解するには、「[小売りの分析のサンプルの .PBIX ファイル](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)」を Power BI Desktop で開きます。 売上目標に対する進行状況を測定する KPI を作成します。

1. **小売りの分析のサンプル**をレポート ビュー ![レポート ビュー アイコンのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-report-view.png) で開きます。

1. 選択 ![黄色のタブのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) を選択して、新しいページを追加します。

1. **[フィールド]** ウィンドウで、 **[Sales] > [Total Units This Year]** を選択します。  この値がインジケーターになります。

1. **[時間] > [FiscalMonth]** を追加します。  この値によって傾向が示されます。

1. ビジュアルの右上隅の省略記号を選択して、Power BI が列を **FiscalMonth** を基準として昇順に並べ替えたことを確認します。

    > [!IMPORTANT]
    > ビジュアルを KPI に変換すると、並べ替えオプションは**なくなります**。 ここで正しく並べ替える必要があります。

    ![展開されて [昇順で並べ替え] と [FiscalMonth] が選択された状態の省略記号メニューのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-ascending-by-fiscal-month.png)

    正しく並べ替えると、visual は次のようになります。

    ![正しく並べ替えられたビジュアルのスクリーン ショット。](media/power-bi-visualization-kpi/power-bi-chart.png)

1. **[視覚化]** ウィンドウから **[KPI]** アイコンを選択して、ビジュアルを KPI に変換します。

    ![KPI アイコンが強調された [視覚化] ウィンドウのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-kpi-template.png)

1. 目標を追加するには、 **[Total Units Last Year]** を **[ターゲットにする目標]** フィールドにドラッグします。

    ![完成した KPI ビジュアルと値が示された [フィールド] ウィンドウのスクリーンショット。](media/power-bi-visualization-kpi/power-bi-kpi-done.png)

1. 必要に応じて、ペイント ローラー アイコンを選んで [形式] ウィンドウを開きます。

    * **インジケーター** - インジケーターの表示単位と小数点以下の表示桁数を制御します。

    * **トレンド軸** - **[オン]** に設定すると、ビジュアルにトレンド軸が KPI ビジュアルの背景として表示されます。  

    * **目標** - **[オン]** に設定すると、ビジュアルに目標、および目標からの距離がパーセンテージとして表示されます。

    * **[色の設定] > [方向]** - 一部の KPI では高い値が "*良好な*" 値と見なされ、別の KPI では低い値が "*良好な*" 値と見なされます。 たとえば、前者の例としては収益があり、後者の例としては待機時間があります。 通常、収益では高い値が良好であり、待機時間の高い値は逆の意味です。 **[高いと良好]** を選び、必要に応じて色の設定を変更します。

KPI は Power BI サービスとモバイル デバイスでも使用できます。 これにより、ビジネスの核心部分に常につながっていることができます。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

KPI が上記のようにならない場合、**FiscalMonth** で並べ替えられていない可能性があります。 KPI には並べ替えオプションはありません。 もう一度やり直して、視覚エフェクトを KPI に変換する*前*に、**FiscalMonth** で並べ替える必要があります。

## <a name="next-steps"></a>次の手順

* [Power BI マップの視覚エフェクトに関するヒントとテクニック](power-bi-map-tips-and-tricks.md)

* [Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。
