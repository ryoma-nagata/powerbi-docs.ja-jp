---
title: X 軸と Y 軸のプロパティのカスタマイズ
description: X 軸と Y 軸のプロパティのカスタマイズ
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: 9DeAKM4SNJM
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 3bfe84acdf73fcb5ace791c9a84943262d0f73ab
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67390245"
---
# <a name="customize-x-axis-and-y-axis-properties"></a>X 軸と Y 軸のプロパティのカスタマイズ

このチュートリアルでは、視覚化に含まれる X 軸と Y 軸をカスタマイズする、さまざまな方法について説明します。 すべての視覚化に軸があるわけではありません。 たとえば、円グラフには軸はありません。 また、カスタマイズのオプションは視覚化によって異なります。 オプションの数が多すぎて 1 つの記事では扱いきれないため、よく使われる軸のカスタマイズをいくつか見ていくほか、Power BI レポート キャンバスで使用する視覚的な **[書式]** ウィンドウについて説明します。  

> [!NOTE]
> このページは、Power BI サービスと Power BI Desktop の両方に適用されます。 これらのカスタマイズは **[書式]** (ペイント ローラー ![ペイント ローラー アイコンのスクリーンショット](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) アイコンが選択されているときに利用でき、Power BI Desktop でも利用できます。

Amanda が X 軸と Y 軸をカスタマイズするのをご覧ください。 ドリルダウンとドリルアップを使用するときにさまざまな方法で連結を制御する手順を示します。

<iframe width="560" height="315" src="https://www.youtube.com/embed/9DeAKM4SNJM" frameborder="0" allowfullscreen></iframe>

## <a name="prerequisites"></a>前提条件

- Power BI サービス

- 小売りの分析のサンプル レポート

## <a name="customize-visualization-x--and-y-axes-in-reports"></a>レポート内の X 軸と Y 軸の視覚化をカスタマイズする

まず、[Power BI サービス](https://app.powerbi.com) にサインインし、[小売りの分析のサンプル](../sample-datasets.md) レポートを[レポート編集](../service-interact-with-a-report-in-editing-view.md)ビューで開きます。

### <a name="create-a-stacked-column-chart-visualization"></a>積み上げ縦棒グラフの視覚化を作成する

視覚化をカスタマイズする前に、それを構築する必要があります。

1. Power BI サービスで **[マイ ワークスペース]** を展開します。

1. 下にスクロールして、 **[データセット]** の一覧から **[Retail Analysis Sample]** を選択します。

1. **[視覚化]** ウィンドウから、積み上げ縦棒グラフ アイコンを選択します。

    ![[視覚化] ウィンドウと空の積み上げ縦棒グラフのスクリーンショット](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-stacked-column-chart.png)

1. X 軸の値を設定するには、 **[フィールド]** ウィンドウから **[Time]**  >  **[FiscalMonth]** を選択します。

1. Y 軸の値を設定するには、 **[フィールド]** ウィンドウから、 **[Sales]**  >  **[Last Year Sales]** および **[Sales]**  >  **[This Year Sales]**  >  **[Value]** を選択します。

    ![値が取り込まれた積み上げ縦棒グラフのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-create-chart.png)

### <a name="customize-the-x-axis"></a>X 軸をカスタマイズする

これで X 軸をカスタマイズできます。

1. **[視覚化]** ウィンドウで、 **[書式]** (ペイント ローラー アイコン ![ペイント ローラー アイコンのスクリーンショット](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-paintroller.png)) を選択して、カスタマイズのオプションを表示します。

1. X 軸のオプションを展開します。

   ![X 軸のオプションのスクリーン ショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-x-axis.png)

1. **[X 軸]** スライダーを **[オン]** に移動します。

    ![[オン] のスライダーのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    X 軸をオフにする理由の 1 つとして考えられるのは、データのための領域を増やすことです。

1. テキストの色、サイズ、フォントを設定します。

    - **色**:黒を選択します

    - **文字のサイズ**:「*14*」と入力します

    - **フォント ファミリ**: **[Arial Black]** を選択します

1. **[タイトル]** オプションを **[オン]** にスライドして、X 軸の名前を表示します。 この例では、**FiscalMonth** です。

1. タイトルのテキストの色、サイズ、フォントを設定します。

    - **タイトルの色**:オレンジ色を選択します

    - **軸のタイトル**:「*Fiscal Month*」と入力します

    - **タイトル テキストのサイズ**:「*21*」と入力します

カスタマイズが完了すると、積み上げ縦棒グラフは次のようになります。

![カスタマイズした積み上げ縦棒グラフのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-customize-axis.png)

行った変更を保存して、次のセクションに移動します。

すべての変更を既定値に戻す必要がある場合は、 **[X 軸]** カスタマイズ ウィンドウの下部にある **[既定値に戻す]** を選択します。

### <a name="customize-the-y-axis"></a>Y 軸をカスタマイズする

次に、Y 軸をカスタマイズします。

1. Y 軸のオプションを展開します。

   ![Y 軸のオプションのスクリーン ショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis.png)

1. **[Y 軸]** スライダーを **[オン]** に移動します。  

    ![[オン] のスライダーのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/onoffslider.png)

    Y 軸をオフにする理由の 1 つとして考えられるのは、データのための領域を増やすことです。

1. Y 軸の **[位置]** を **[右]** に設定します。

1. テキストの色、サイズ、フォントを設定します。

    - **色**:黒を選択します

    - **文字のサイズ**:「*14*」と入力します

    - **フォント ファミリ**: **[Arial Black]** を選択します

1. **[表示単位]** を **[百万]** に設定し、 **[小数点以下桁数の値]** を *[0]* に設定します。

1. この視覚化の場合、Y 軸にタイトルを表示してもビジュアルがわかりやすくなることはないので、 **[タイトル]** は **[オフ]** のままにします。  

1. 色とストロークを変更して、グリッド線が目立つようにします。

    - **色**:ダーク グレーを選択します

    - **ストローク**:「*2*」と入力します

これらのカスタマイズをすべて完了すると、棒グラフは次のように表示されるはずです。

![Y 軸をカスタマイズしたグラフのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-y-axis-complete.png)

## <a name="customizing-visualizations-with-dual-y-axes"></a>2 つの Y 軸を持つ視覚化をカスタマイズする

最初に、店舗数が売上高に与える影響を調べる複合グラフを作成します。 これは、[複合グラフのチュートリアル](power-bi-visualization-combo-chart.md)で作成したグラフと同じものです。 その後、2 つの Y 軸の書式を設定します。

### <a name="create-a-chart-with-two-y-axes"></a>2 つの Y 軸を持つグラフを作成する

1. **[Time] > [FiscalMonth]** で **[Sales] > [Gross Margin last year %]** を追跡する新しい折れ線グラフを作成します。

    ![新しい折れ線グラフのスクリーン ショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-line-chart.png)

    > [!NOTE]
    > 月別に並べ替えるためのヘルプについては、「[その他の条件を使用した並べ替え](../consumer/end-user-change-sort.md#other)」をご覧ください。

    1 月の粗利率は 35% で、4 月には最高値の 45% になり、7 月に下がって 8 月に再びピークに達しました。 前年と本年は同じ売上パターンになるでしょうか?

1. **[This Year Sales] > [Value]** と **[Last Year Sales]** を折れ線グラフに追加します。

    ![新しいデータが追加された折れ線グラフのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/flatline_new.png)

    **[Gross Margin Last Year %]** (**0M%** のグリッド線に沿った青い線) の目盛が **[Sales]** の目盛よりかなり小さいため、比較が困難です。 また、Y 軸のラベルのパーセンテージがおかしくなっています。

1. ビジュアルを読みやすく分かりやすくするため、折れ線グラフを「折れ線グラフおよび積み上げ縦棒グラフ」に変換します。

   ![折れ線グラフおよび積み上げ縦棒グラフのアイコンが強調された [視覚化] ウィンドウのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/converttocombo_new.png)

1. **[Gross Margin% Last Year]** (前年の粗利 (%)) を **[各棒の値]** から **[線の値]** にドラッグします。

    ![3 つの値が明確に表された折れ線グラフおよび積み上げ縦棒グラフのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes.png)

    これで、最初のセクションで作成した積み上げ縦棒グラフの上に、折れ線グラフが重なった状態になりました。 上で学んだことを使って、必要に応じて、軸のフォントの色とサイズを設定してください。

   ![カスタマイズした折れ線グラフおよび積み上げ縦棒グラフのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-dual-axes-new.png)

   Power BI によって 2 つの軸が作成されるため、各データセットを異なる縮尺でプロットできます。 左側の測定単位はドルで、右側の測定単位は割合です。

### <a name="format-the-secondary-y-axis"></a>2 番目の Y 軸の書式を設定する

1. **[視覚化]** ウィンドウで、ペイント ローラーのアイコンを選択して、書式設定のオプションを表示します。

1. Y 軸のオプションを展開します。

1. **[セカンダリを表示]** オプションが見つかるまで、下にスクロールします。 **[オン]** になっていることを確認します。

   ![[セカンダリを表示] オプションのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/combo3.png)

1. (省略可能) 2 つの軸をカスタマイズします。 棒の軸または線の軸の**位置**を切り替えた場合、2 つの軸の左右が切り替わります。

### <a name="add-titles-to-both-axes"></a>両方の軸にタイトルを追加する

非常に複雑な視覚化には、軸のタイトルの追加が有用です。  タイトルにより、同僚は視覚化の内容を理解しやすくなります。

1. **「Y 軸 (棒)」** と **「Y 軸 (折れ線)」** の **[タイトル]** を **[オン]** に切り替えます。

1. 両方とも、 **[スタイル]** を **[タイトルの表示のみ]** に設定します。

   ![[タイトル] オプションと [スタイル] オプションのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/yaxissettings.png)

1. これで、複合グラフに 2 つの軸がともにタイトル付きで表示されます。

   ![カスタマイズした 2 つの Y 軸を持つグラフのスクリーンショット。](media/power-bi-visualization-customize-x-axis-and-y-axis/power-bi-combo-chart.png)

詳細については、「[Power BI における色の書式設定に関するヒントとコツ](service-tips-and-tricks-for-color-formatting.md)」を参照してください。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

X 軸が日付型としてレポートの所有者別に分類されている場合、 **[種類]** オプションが表示され、連続またはカテゴリ別から選択できます。

## <a name="next-steps"></a>次の手順

- [Power BI レポートでの視覚化](power-bi-report-visualizations.md)

- [視覚化のタイトル、凡例、および背景をカスタマイズする](power-bi-visualization-customize-title-background-and-legend.md)

- [色の書式設定と軸のプロパティの概要](service-getting-started-with-color-formatting-and-axis-properties.md)

- [Power BI サービス コンシューマーの基本的な概念](../consumer/end-user-basic-concepts.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。
