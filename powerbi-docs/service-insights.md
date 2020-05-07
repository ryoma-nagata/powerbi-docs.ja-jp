---
title: Power BI を使用してデータ インサイトを自動的に生成する
description: データセットとダッシュボード タイルに関する詳細情報を取得する方法を説明します。
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 5f571cabcc413947713cd232863b3ecad910436d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "73872246"
---
# <a name="generate-data-insights-automatically-with-power-bi"></a>Power BI を使用してデータ インサイトを自動的に生成する
新しいデータセットがあるが、どこから始めるべきかわからない場合。  ダッシュボードをすばやく構築する必要がある場合。  不足している情報を探したい場合。

クイック インサイトを実行して、データに基づいて、興味のある対話型の視覚化を生成します。 クイック インサイトは、データセット全体に対して実行することも (クイック インサイト)、特定のダッシュボード タイルに対して実行することもできます (範囲指定のインサイト)。 インサイトに対してインサイトを実行することもできます。

> [!NOTE]
> 分析情報は、DirectQuery では機能しません。Power BI にアップロードされたデータに限り機能します。
> 

インサイトの基となっているのは、Microsoft Research と共同開発して拡大を続けている[高度な分析アルゴリズムのセット](service-insight-types.md)です。引き続きこれを使って、より多くの人が新しい直感的な方法でデータから詳細情報を見つけられるようにしていきます。

## <a name="run-quick-insights-on-a-dataset"></a>データセットへのクイック インサイトの実行
Amanda がクイック インサイトをデータセットに対して実行し、フォーカス モードでインサイトを開き、インサイトの 1 つをダッシュボード上にタイルとして固定し、ダッシュボード タイルのインサイトを取得する様子をご覧ください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/et_MLSL2sA8" frameborder="0" allowfullscreen></iframe>


次はあなたの番です。 [サプライヤー クオリティ分析サンプル](sample-supplier-quality.md)を使用して分析情報を試してみます。

1. **[データセット]** タブから**その他のオプション** (...) を選び、 **[クイック分析情報を取得する]** を選びます。
   
    ![[データセット] タブ](media/service-insights/power-bi-ellipses.png)
   
    ![省略記号メニュー](media/service-insights/power-bi-tab.png)
2. Power BI は[さまざまなアルゴリズム](service-insight-types.md)を使用して、データセット内の傾向を検索します。
   
    ![詳細情報の検索ダイアログ](media/service-insights/pbi_autoinsightssearching.png)
3. 数秒で、情報を取得する準備が整います。  **[詳細情報の表示]** を選択して、視覚化を表示します。
   
    ![成功メッセージ](media/service-insights/pbi_autoinsightsuccess.png)
   
    > [!NOTE]
    > データが統計的に有意でないために分析情報を生成できないデータセットもあります。  詳細については、「[Power BI クイック インサイト用のデータの最適化](service-insights-optimize.md)」を参照してください。
    > 
    
4. 視覚化は、最大 32 個の個別のインサイト カードとともに特別な **[クイック分析情報]** キャンバスに表示されます。 各カードには、グラフまたはグラフと簡単な説明が含まれます。
   
    ![クイック分析キャンバス](media/service-insights/power-bi-insights.png)

## <a name="interact-with-the-insight-cards"></a>インサイト カードとの対話

1. ダッシュボードに視覚化を追加するには、カードの上にポインターを移動してピン アイコンを選択します。

2. カードをポイントし、**その他のオプション** (...) を選択し、 **[詳細情報の表示]** を選択します。 

    分析情報画面がフォーカス モードで開きます。
   
    ![分析情報フォーカス モード](media/service-insights/power-bi-insight-focus.png)
3. フォーカス モードでは次のことができます。
   
   * 視覚エフェクトをフィルター処理します。 **[フィルター]** ウィンドウがまだ開いていない場合、ウィンドウの右側にある矢印を選択して展開します。

       ![展開された分析情報フィルター メニュー](media/service-insights/power-bi-insights-filter-new.png)
   * **[ビジュアルをピン留めする]** を選択し、分析情報カードをダッシュボードにピン留めします。
   * カード自体で分析情報を実行します。カードは*範囲付き分析情報*と呼ばれることもあります。 右上隅にある電球アイコン ![[詳細情報の取得] アイコン](media/service-insights/power-bi-bulb-icon.png) または **[詳細情報の取得]** を選択します。
     
       ![分析情報の取得アイコン](media/service-insights/pbi-autoinsights-tile.png)
     
     インサイトが左側に表示され、右側には、その単一の情報に含まれるデータのみに基づく新しいカードが表示されます。
     
       ![詳細情報についての詳細情報](media/service-insights/power-bi-insights-on-insights-new.png)
4. 元のインサイト キャンバスに戻るには、左上隅にある **[フォーカス モードの終了]** を選択します。

## <a name="run-insights-on-a-dashboard-tile"></a>ダッシュボード タイルへのインサイトの実行
データセット全体から情報を検索する代わりに、検索を絞り込み、単一のダッシュボード タイルの作成に使用するデータに範囲付き分析情報を実行します。 

1. ダッシュボードを開きます。
2. タイルの上にマウスを置きます。 **その他のオプション** (...) を選択し、 **[詳細情報の表示]** を選択します。 タイルが[フォーカス モード](service-focus-mode.md)で開き、インサイト カードが右側に表示されます。    
   
    ![フォーカス モード](media/service-insights/pbi-insights-tile.png)    
3. 興味をそそる情報がありましたか? 詳細に確認するには、その分析情報カードを選択します。 選択した分析情報が左側に表示され、右側には、その単一の分析情報に含まれるデータのみに基づく新しい分析情報カードが表示されます。    
4. 引き続きデータを掘り下げ、興味がある情報が見つかったら、右上隅から **[ビジュアルをピン留めする]** を選んで、それをダッシュボードにピン留めします。

## <a name="next-steps"></a>次のステップ
- データセットを所有している場合は、[クイック分析情報用に最適化します](service-insights-optimize.md)。
- 使用できるクイック分析情報の種類については[こちら](service-insight-types.md)を参照してください。

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

