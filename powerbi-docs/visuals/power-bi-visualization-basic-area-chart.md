---
title: 基本的な面グラフ
description: 基本的な面グラフです。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: fe1d2a6f086831a4ae6bd78d8669dce9459bffad
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839867"
---
# <a name="basic-area-chart"></a>基本的な面グラフ
基本的な面グラフ (層グラフとも呼ばれます) は、折れ線グラフに基づいています。 軸と折れ線の間の領域は、量を示すために色で塗りつぶされます。 

面グラフは、時間の経過に伴う変化の大きさを強調し、トレンドの合計値に注目させるために使用できます。 たとえば、時間の経過に伴う利益を表すデータを面グラフにプロットして、総利益を強調することができます。

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>基本的な面グラフを使用すべきケース
基本的な面グラフを選ぶとよい状況を挙げます。

* 時系列全体にわたって量のトレンドを確認および比較する場合 
* 個々の系列が物理的に数えられる集合を表す場合

### <a name="prerequisites"></a>前提条件
 - Power BI サービス
 - 小売りの分析のサンプル

先に進むには、Power BI にサインインして、 **[データの取得] \> [サンプル] \> [小売りの分析のサンプル]** を選んでから、 **[ダッシュボードに移動]** を選びます。 

## <a name="create-a-basic-area-chart"></a>基本的な面グラフの作成
 

1. [小売りの分析のサンプル] ダッシュボードで、 **\[Total Stores] \(総店舗数)** タイルを選び、[小売りの分析のサンプル] レポートを開きます。
2. **[編集]** を選択し、編集ビューでレポートを開きます。
3. レポートの下部にある黄色の正符号 [+] アイコンを選んで、新しいページを追加します。
4. 今年の売上と去年の売上を月ごとに表示する面グラフを作成します。
   
   a. [フィールド] ウィンドウで、 **[Sales] \> [Last Year Sales]** を選択し、 **[This Year Sales] > [Value]** を選択します。

   ![](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  [視覚化] ウィンドウの [面グラフ] アイコンを選んで、グラフを基本的な面グラフに変換します。

   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  **\[Time] \(時間) \> \[Month] \(月)** を選び、[Month] を **[軸]** に追加します。   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  月別にグラフを表示するには、(ビジュアルの右上隅にある) 省略記号を選択し、 **[Sort by month]** (月別に並べ替え) を選択します。 並べ替え順序を変更するには、省略記号をもう一度選び、 **[昇順で並べ替え]** または **[降順で並べ替え]** を選択します。

## <a name="highlighting-and-cross-filtering"></a>強調表示とクロス フィルター処理
[フィルター] ウィンドウの使用方法については、「[Power BI でのレポートへのフィルターの追加](../power-bi-report-add-filter.md)」をご覧ください。

グラフ内の 1 つの特定の領域を強調表示するには、その領域または上部の境界を選びます。  他の視覚エフェクトの種類とは異なり、同じページに他の視覚エフェクトがある場合、基本的な面グラフを強調表示しても、レポート ページの他の視覚エフェクトはクロス フィルター処理されません。 ただし、面グラフは、レポート ページ上の他の視覚化によってトリガーされたクロス フィルター処理のターゲットになります。 

1. 面グラフを選択し、それを別のレポート ページにコピーして、試してください (CTRL + C および CTRL + V)。
2. 影付きの領域を 1 つ選択し、次いでもう 1 つ影付きの領域を選択します。 ページのその他の視覚化には、何も影響がないことがわかります。

    ![面グラフ上で選択されている今年の売上](media/power-bi-visualization-basic-area-chart/power-bi-select-area.png)

3. ここで、ページ上の縦棒グラフの 1 本のバーまたは折れ線グラフの 1 月など、その他の視覚化の要素を 1 つ選択します。 面グラフの変化を確認してください。フィルタリングされます。  

    ![選択されている Ft Oglethorpe バー](media/power-bi-visualization-basic-area-chart/power-bi-filter.png) 

詳しくは、「[Power BI レポートでの視覚化の相互作用](../service-reports-visual-interactions.md)」をご覧ください。


## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング   
* [障碍を持つユーザーのためにレポートをより使いやすくする](../desktop-accessibility.md)
* 基本的な面グラフは、複数層の面の重なりによって値がわかりにくくなるため、値の比較には有効ではありません。 Power BI では、面の重なりを示すために透過が使用されます。 ただし、透過は 2 つか 3 つの異なる面についてのみうまく機能します。 4 つ以上のメジャーとトレンドを比較する必要がある場合は、折れ線グラフを使用してみてください。 4 つ以上のメジャーと量を比較する必要がある場合は、ツリーマップを使用してみてください。

## <a name="next-step"></a>次の手順
[Power BI のレポート](power-bi-visualization-card.md)  

