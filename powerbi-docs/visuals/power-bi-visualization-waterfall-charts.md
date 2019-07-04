---
title: Power BI のウォーターフォール図
description: Power BI のウォーターフォール図
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c9ad87d851f52db6cd2720c9e3bd5d4bb7b189a7
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408917"
---
# <a name="waterfall-charts-in-power-bi"></a>Power BI のウォーターフォール図

ウォーターフォール図は、Power BI で値が加算または減算されるときの累計を示します。 一連の加算と減算の変化によって、初期値 (純利益など) が、どのように影響を受けるかを理解するために役立ちます。

各縦棒が色分けされるため、ひと目で増減を識別できます。 最初と最後の値の縦棒は、通常[横軸を起点](https://support.office.com/article/Create-a-waterfall-chart-in-Office-2016-for-Windows-8de1ece4-ff21-4d37-acd7-546f5527f185#BKMK_Float "横軸を起点")としますが、中間値の縦棒は浮動縦棒です。 この形式から、ウォーターフォール図はブリッジ図と呼ばれることもあります。

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="when-to-use-a-waterfall-chart"></a>ウォーターフォール図を使用すべきケース

ウォーターフォール図は、次のような場合に最適な選択肢です。

* 時間、系列、またはさまざまなカテゴリにわたりメジャーに変化がある場合。

* 合計値に影響を与える大きな変化を監査する場合。

* 収益のさまざまな要因を示すことによって、会社の年間利益をプロットして、総利益 (または損) に到達するよう表示する場合。

* 会社のある年の年始と年末の社員数をグラフに示す場合。

* 毎月の収入と支出、および口座の現在の残高を視覚化する場合。

## <a name="prerequisites"></a>前提条件

* Power BI サービスまたは Power BI Desktop

* 小売りの分析のサンプル レポート

## <a name="get-the-retail-analysis-sample-report"></a>小売りの分析のサンプル レポートを取得する

次の手順では、「Retail Analysis Sample」を使用します。 視覚エフェクトを作成するには、データセットとレポートへの編集アクセス許可が必要です。 Power BI のサンプルはすべて編集できます。 他のユーザーからのレポートの共有を受ける場合、レポートでは視覚化を作成できません。 作業を進めるには、[小売りの分析のサンプル レポート](../sample-datasets.md)を取得します。

**小売りの分析のサンプル** データセットを取得したら、作業を開始できます。

## <a name="create-a-waterfall-chart"></a>ウォーターフォール図の作成

ここでは、月別の売上差異 (予想売上高と実際の売上高の差異) を示すウォーターフォール図を作成します。

1. **[マイ ワークスペース]** から **[データセット]**  >  **[レポートの作成]** を選択します。

    ![[データセット] > [レポートの作成] のスクリーンショット。](media/power-bi-visualization-waterfall-charts/power-bi-create-a-report.png)

1. **[フィールド]** ウィンドウで、 **[Sales]**  >  **[Total Sales Variance]** を選択します。

   ![[Sales] > [Total Sales Variance] が選択された状態および結果のビジュアルのスクリーンショット。](media/power-bi-visualization-waterfall-charts/power-bi-first-value.png)

1. ウォーターフォール アイコン ![ウォーターフォール アイコンのスクリーンショット](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-icon.png) を選択して、グラフをツリーマップに変換します。

    **[Total Sales Variance]** が **[Y 軸]** 領域内にない場合、そこにドラッグします。

    ![視覚エフェクトのテンプレート](media/power-bi-visualization-waterfall-charts/convertwaterfall.png)

1. **[Time]**  >  **[FiscalMonth]** を選択して、 **[カテゴリ]** に追加します。

    ![ウォーターフォール](media/power-bi-visualization-waterfall-charts/power-bi-waterfall.png)

1. Power BI でウォーターフォール図が時系列で並べ替えられたことを確認します。 グラフの右上隅から、省略記号 (...) を選択します。

    **[昇順で並べ替え]** オプションと **[FiscalMonth]** オプションの左横に黄色のインジケーターがあることを確認します

    ![[並べ替え] > [FiscalMonth] の選択](media/power-bi-visualization-waterfall-charts/power-bi-sort-by.png)

    X 軸の値を見て、**Jan** から **Aug** の順になっていることを確認します。

    さらに調べると、月別の変化の要因がわかります。

1. **[Store]**  >  **[Territory]** を **[詳細]** バケットにドラッグします。

    ![[詳細] バケットでのストアの表示](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown.png)

    Power BI の既定では、月別の増減に寄与した上位 5 個の要素が追加されます。

    ![[詳細] バケットでのストアの表示](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-initial.png)

    ここでは上位 2 個の要素にのみ関心があります。

1. **[書式]** ウィンドウで **[詳細]** を選択し、 **[最大ブレークダウン]** を **2** に設定します。

    ![[書式] > [詳細]](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-breakdown-maximum.png)

    ウォーターフォール図をざっと見ると、オハイオ州とペンシルバニア州の地域が売上の増加と減少の両方に最も大きく貢献していることがわかります。

    ![ウォーターフォール グラフ](media/power-bi-visualization-waterfall-charts/power-bi-waterfall-axis.png)

    これは興味深い発見です。 オハイオ州とペンシルバニア州の売上が他の地域よりもはるかに高いため、この 2 つの州がこのように重大な影響を及ぼしているのでしょうか。 このようなことも確認するには、

1. 今年の売上値と昨年の売上値を地域別に表示するマップを作成します。

    ![PA とオハイオがクローズアップされたマップ](media/power-bi-visualization-waterfall-charts/power-bi-map.png)

    このマップはこの理論をサポートしています。 これら 2 つの地域は、昨年 (バブルのサイズ) と今年 (バブルの網掛け) の売上値が最高だったことが示されています。

## <a name="highlighting-and-cross-filtering"></a>強調表示とクロス フィルター処理

**[フィルター]** ウィンドウの使い方については、[編集ビューでのレポートへのフィルターの追加](../power-bi-report-add-filter.md)に関するページをご覧ください。

ウォーターフォール図内の縦棒を強調表示すると、レポートのページ上の他の視覚化がクロス フィルター処理されます。逆の場合も同様です。 ただし、 **[合計]** の縦棒では強調表示がトリガーされることも、クロス フィルター処理に反応することもありません。

## <a name="next-steps"></a>次の手順

* [Power BI レポート内でのビジュアルの相互作用を変更する](../service-reports-visual-interactions.md)

* [Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)
