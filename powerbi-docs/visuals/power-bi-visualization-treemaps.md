---
title: Power BI のツリーマップ
description: Power BI のツリーマップ
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4c28071917dbe5669e6e35bd416236ef7047eb24
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408680"
---
# <a name="treemaps-in-power-bi"></a>Power BI のツリーマップ

ツリーマップでは、入れ子になった一連の四角形で階層データが表示されます。 階層の各レベルは、色付きの四角形 (ブランチ) で表され、ブランチには四角形 (リーフ) が含まれます。 Power BI では、各四角形内のスペースのサイズは測定値に基づいています。 各四角形は大きさの順に左上 (最大) から右下 (最小) に向かって配置されます。

![カテゴリ別の製品の数と製造元ツリーマップのスクリーンショット。](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

たとえば、売上を分析する場合、衣料カテゴリに対して次の最上位レベル ブランチが存在することがあります: **Urban** (都市部向け)、**Rural** (地方向け)、**Youth** (若者向け)、**Mix** (組み合わせ)。 Power BI により、カテゴリ内の衣料メーカー用の製造メーカーについては、カテゴリ四角形をリーフに分割されます。 これらは売上数に基づいてサイズが決まり、網掛け表示されます。

上の **Urban** ブランチでは、**VanArsdel** の衣料の売上が多く、 **Natura** と **Fama** の売上はそれよりも少なく、 **Leo** の売上はわずかです。 そのため、このツリーマップの **Urban** ブランチは次のようになります。

* 左上隅にある **VanArsdel** の四角形が最も大きい。

* **Natura** と **Fama** の四角形はそれよりもやや小さい。

* 他のすべての衣料売上に関する多くの四角形がある。

* **Leo** の四角形は非常に小さい。

各リーフ ノードのサイズと網掛けの比較によって、その他の衣料カテゴリ全体の売上品目数を比較することができます。つまり、四角形が大きく網掛けが濃いほど、値は大きいことになります。

ツリーマップの作成例を見たい方は、 このビデオの 2:10 にスキップし、Amanda がツリーマップを作成するところをご覧ください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-treemap"></a>ツリーマップを使用すべきケース

ツリーマップは、次のような場合に最適な選択肢です。

* 大量の階層データを表示する。

* 横棒グラフで多数の値を効果的に処理できない。

* 各部分と全体の間の割合を示す。

* 階層内のカテゴリの各レベルにわたってメジャーの分布のパターンを示す。

* サイズと色分けを使用して属性を示す。

* パターン、外れ値、最も重要な要因、および例外を見分ける。

## <a name="prerequisites"></a>前提条件

* Power BI サービスまたは Power BI Desktop

* 小売りの分析のサンプル レポート

## <a name="get-the-retail-analysis-sample-report"></a>小売りの分析のサンプル レポートを取得する

次の手順では、「Retail Analysis Sample」を使用します。 視覚エフェクトを作成するには、データセットとレポートへの編集アクセス許可が必要です。 Power BI のサンプルはすべて編集できます。 他のユーザーからのレポートの共有を受ける場合、レポートでは視覚化を作成できません。 作業を進めるには、[小売りの分析のサンプル レポート](../sample-datasets.md)を取得します。

**小売りの分析のサンプル** データセットを取得したら、作業を開始できます。

## <a name="create-a-basic-treemap"></a>基本的なツリーマップの作成

レポートを作成し、基本的なツリーマップを追加します。

1. **[マイ ワークスペース]** から **[データセット]**  >  **[レポートの作成]** を選択します。

    ![[データセット] > [レポートの作成] のスクリーンショット。](media/power-bi-visualization-treemaps/power-bi-create-a-report.png)

1. **[フィールド]** ウィンドウで、 **[Sales]\(売上\)**  >  **[Last Year Sales]\(前年度の売上\)** を選択します。

   ![選択されている [Sales]\(売上\) > [Last Tear Sales]\(前年度の売上\) と、結果のビジュアルのスクリーンショット。](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)

1. ツリーマップ アイコン ![ツリーマップ アイコンのスクリーンショット](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) を選択して、グラフをツリーマップに変換します。

   ![構成されていないツリーマップのスクリーンショット。](media/power-bi-visualization-treemaps/treemapconvertto_new.png)

1. **[アイテム]**  >  **[カテゴリ]** を **[グループ]** にドラッグします。

    四角形のサイズが総売上高に基づき、色でカテゴリが表されるツリーマップが Power BI によって作成されます。 つまり、カテゴリ別の総売上高の相対的な大きさを視覚的に説明する階層が作成されます。 **[Mens]\(男性向け\)** カテゴリの売上高が最高で、 **[Hosiery]\(靴下・下着類\)** カテゴリの売上高が最低です。

    ![構成されたツリーマップのスクリーンショット。](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. **[ストア]**  >  **\[Chain] \(チェーン)** を **"Details"** にドラッグしてツリーマップを完成させます。 これで、前年の売上高をカテゴリおよびチェーン別に比較できます。

   ![[ストア] > [チェーン] が詳細に追加されたツリーマップのスクリーンショット。](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > [色の彩度] と [詳細] を同時に使用することはできません。

1. **[Chain]** (チェーン) エリアにポインターを合わせると、 **[カテゴリ]** のその部分のヒントが表示されます。

    たとえば、 **[090-Home]** の四角形内の **[Fashions Direct]** にポインターを合わせると、Home カテゴリの Fashion Direct の部分のツールヒントが表示されます。

   ![ヒントが表示されている Home のスクリーンショット。](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)

1. ツリーマップを[ダッシュボード タイルとして追加 (ビジュアルをピン留め)](../service-dashboard-tiles.md) します。

1. [レポート](../service-report-save.md)を保存します。

## <a name="highlighting-and-cross-filtering"></a>強調表示とクロス フィルター処理

**[フィルター]** ウィンドウの使い方については、[レポートへのフィルターの追加](../power-bi-report-add-filter.md)に関するページをご覧ください。

ツリーマップ内の **[カテゴリ]** または **[詳細]** を強調表示すると、レポート ページ上の他の視覚エフェクトがクロス強調表示またはクロスフィルター処理されます。逆の場合も同様です。 先に進むには、このレポート ページにいくつかのビジュアルを追加するか、このレポートの他のページのいずれかにツリーマップをコピーします。

1. ツリーマップ上で、 **[カテゴリ]** 、または **[カテゴリ]** 内の **[チェーン]** のいずれかを選択します。 これにより、ページ上の他の視覚化がクロス強調表示されます。 たとえば、 **[050-Shoes]** を選択すると、前年の靴の売上高が **3,640,471 ドル**で、そのうち**ファッション ディレクター** アカウントの売上高が **2,174,185 ドル**であったことが表示されます。

   ![クロス強調表示されている店舗売上の概要レポートのスクリーンショット。](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. **[Last Year Sales by Chain]\(チェーン別の前年売上高\)** 円グラフで、 **[Fashions Direct]** スライスを選択し、ツリーマップをクロス フィルター処理します。
   ![クロス フィルター処理機能を示す GIF。](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. グラフ相互間のクロスフィルター処理とクロス強調表示を管理するには、「[Power BI レポート内でのビジュアルの相互作用を変更する](../service-reports-visual-interactions.md)」を参照してください。

## <a name="next-steps"></a>次の手順

* [Power BI のウォーターフォール図](power-bi-visualization-waterfall-charts.md)

* [Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)
