---
title: Power BI での複合グラフ
description: 複合グラフに関するこのチュートリアルでは、複合グラフを使用するケースと、Power BI サービスおよび Power BI Desktop で複合グラフを作成する方法について説明します。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: lnv66cTZ5ho
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/23/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: e4b7b4b336b376f6ccec0bc0fe56de107ab8bd09
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/13/2019
ms.locfileid: "67124304"
---
# <a name="combo-chart-in-power-bi"></a>Power BI での複合グラフ

Power BI の複合グラフは、折れ線グラフと縦棒グラフを組み合わせた 1 つの視覚化です。 2 つのグラフを 1 つに組み合わせると、データの比較をよりすばやく行うことができます。

複合グラフには、1 つまたは 2 つの Y 軸を保持できます。

## <a name="when-to-use-a-combo-chart"></a>複合グラフを使用するケース

複合グラフは、次のような場合に最適な選択肢になります。

* 同じ X 軸を持つ折れ線グラフと縦棒グラフがある場合。

* 値の範囲が異なる複数のメジャーを比較する場合。

* 2 つのメジャーの間の相関関係を 1 つの視覚化で示す場合。

* あるメジャーが別のメジャーで定義されているターゲットを満たすかどうかを調べる場合。

* キャンバスのスペースを節約する場合。

## <a name="prerequisites"></a>前提条件

複合グラフは、Power BI サービスでも Power BI Desktop でも利用できます。 このチュートリアルでは、Power BI サービスを使用して複合グラフを作成します。 Power BI にサインインするためのユーザーの資格情報があることを確認してください。

このビデオでは、売上およびマーケティングのサンプルを使って複合グラフを作成する様子をご覧いただけます。

<iframe width="560" height="315" src="https://www.youtube.com/embed/lnv66cTZ5ho?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>  

## <a name="create-a-basic-single-axis-combo-chart"></a>基本的な 1 つの軸の複合グラフを作成する

作業を進めるために、Power BI サービスを開き、 **[小売りの分析 のサンプル]** に接続します。 独自の複合グラフを作成するには、Power BI サービスにサインインして、 **[データの取得]**  >  **[サンプル]**  >  **[小売りの分析のサンプル]**  >  **[接続]** を選択します。 **[小売りの分析のサンプル]** ダッシュボードが表示されます。

1. [小売りの分析のサンプル] ダッシュボードで、 **[Total Stores]** タイルを選択し、 **[Store Sales Overview]** レポートを開きます。

1. **[レポートの編集]** を選んで、編集ビューでレポートを開きます。

1. ページの下部で **+** を選択して、新しいレポート ページを追加します。

1. 今年の売上と粗利益を月単位で表示する縦棒グラフを作成します。

    1. [フィールド] ウィンドウで、 **\[Sales] \(売上)** \> **\[This Year Sales] \(今年の売上)**  >  **[値]** を選択します。

    1. **[Sales]** \> **[Gross Margin This Year]** を **[値]** にドラッグします。

    1. **[Time]** \> **[Fiscal Month]** の順に選択して、 **[軸]** に追加します。

        ![新しく作成した縦棒グラフのスクリーンショット。](media/power-bi-visualization-combo-chart/combotutorial1new.png)

1. 視覚化の右上隅にある省略記号を選択し、 **[並べ替え] > [FiscalMonth]** を選択します。 並べ替え順序を変更するには、省略記号をもう一度選び、 **[昇順で並べ替え]** または **[降順で並べ替え]** を選択します。

1. 縦棒グラフを複合グラフに変換します。 次の 2 つの複合グラフを使用できます: **[折れ線グラフおよび積み上げ縦棒グラフ]** と **[折れ線グラフおよび集合縦棒グラフ]** 。 縦棒グラフを選んだ状態で **[視覚化]** ウィンドウから **[折れ線グラフおよび集合縦棒グラフ]** を選びます。

    ![[折れ線グラフおよび集合縦棒グラフ] オプションが強調された [視覚化] ウィンドウのスクリーンショット。](media/power-bi-visualization-combo-chart/converttocombo_new2.png)

1. **[フィールド]** ウィンドウで、 **[Sales]**  >  **[Last Year Sales]** を **[線の値]** ウェルにドラッグします。

    ![[Last Year Sales] がドラッグで入力された [線の値] ウェルのスクリーンショット。](media/power-bi-visualization-combo-chart/linevaluebucket.png)

    複合グラフは次のようになります。

    ![[Last Year Sales] の線の値が追加された縦棒グラフのスクリーンショット。](media/power-bi-visualization-combo-chart/combochartdone-new.png)

## <a name="create-a-combo-chart-with-two-axes"></a>2 つの軸を持つ複合グラフを作成する

このタスクでは、粗利と売上を比較します。

1. **前年の粗利 (%)** を**月ごと**に追跡する新しい折れ線グラフを作成します。 省略記号を選択して、**月ごと**に**昇順**で並べ替えます。

    ![新しい線グラフのスクリーンショット。](media/power-bi-visualization-combo-chart/combo1_new.png)

     1 月の粗利 (%) は 35% で、4 月には最高値の 45% になり、7 月に下がって 8 月に再びピークに達しました。 前年と本年は同じ売上パターンになるでしょうか?

1. **[This Year Sales]**  >  **[Value]** と **[Last Year Sales]** を折れ線グラフに追加します。 **[Gross Margin Last Year %]** の目盛は、 **[Sales]** の目盛よりはるかに小さくなります。 比較は困難です。

    ![[Value] と [Last Year Sales] を追加した折れ線グラフのスクリーンショット。](media/power-bi-visualization-combo-chart/flatline_new.png)

1. ビジュアルの読みやすく分かりやすくするため、折れ線グラフを「折れ線グラフおよび積み上げ縦棒グラフ」に変換します。

    ![[折れ線グラフおよび積み上げ縦棒グラフ] オプションが強調された [視覚化] ウィンドウのスクリーンショット。](media/power-bi-visualization-combo-chart/converttocombo_new.png)

1. **[Gross Margin% Last Year]** (前年の粗利 (%)) を **[各棒の値]** から **[線の値]** にドラッグします。 

    ![折れ線グラフおよび積み上げ縦棒グラフのスクリーンショット](media/power-bi-visualization-combo-chart/power-bi-combochart.png)

    Power BI は 2 つの軸を作成し、 サービスがデータセットを異なる縮尺でプロットできるようにします。 左側の測定単位はドル売上高で、右側の測定単位は割合です。 それで、質問の答えがわかります。はい、同じパターンが見られます。

## <a name="add-titles-to-the-axes"></a>タイトルを各軸に追加する

1. ペイント ローラー アイコン ![ペイント ローラー アイコンのスクリーンショット。](media/power-bi-visualization-combo-chart/power-bi-paintroller.png) を選択して、[書式設定] ウィンドウを開きます。

1. 下矢印を選んで、 **Y 軸** のオプションを展開します。

1. **[Y 軸 (棒)]** に対して、次のオプションを選択します。

    | 設定 | 値 |
    | ------- | ----- |
    | 位置 | **[左]** を選択します。 |
    | 表示単位 | **[百万]** を選択します。 |
    | タイトル | スライダーを **[オン]** に移動します。 |
    | スタイル | **[タイトルのみを表示]** を選択します。 |
    | セカンダリの表示 | スライダーを **[オン]** に移動します。  これにより、複合グラフの折れ線グラフの部分の書式を設定するためのオプションが表示されます。 |

1. **[Y 軸 (折れ線)]** に対して、次のオプションを選択します。

    | 設定 | 値 |
    | ------- | ----- |
    | 位置 | **[右]** を選択します。 |
    | タイトル | スライダーを **[オン]** に移動します。 |
    | スタイル | **[タイトルのみを表示]** を選択します。 |

    これで、複合グラフに 2 つの軸がともにタイトル付きで表示されます。

    ![各タイトルが表示された折れ線グラフおよび積み上げ縦棒グラフのスクリーンショット。](media/power-bi-visualization-combo-chart/power-bi-titles-on.png)

1. 必要に応じて、グラフの表示および読みやすさが向上するように、テキストのフォント、サイズ、色を変更し、その他の書式設定オプションも設定します。

ここからは次のことができます。

* [複合グラフをダッシュボード タイルとして追加](../service-dashboard-tiles.md)します。

* [レポートを保存](../service-report-save.md)します。

* [障碍を持つユーザーのためにレポートをより使いやすくします](../desktop-accessibility.md)。

## <a name="cross-highlighting-and-cross-filtering"></a>クロスハイライトとクロス フィルター処理

複合グラフ内の縦棒または折れ線を強調表示すると、レポートのページ上の他の視覚化がクロスハイライトおよびクロス フィルター処理されます。 [[ビジュアル対話]](../service-reports-visual-interactions.md) を使用すれば、この既定の動作を変更できます。

## <a name="next-steps"></a>次の手順

[Power BI のドーナツ グラフ](power-bi-visualization-doughnut-charts.md)

[Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)