---
title: 分析を実行し、ダッシュボード タイルの分析情報を表示する
description: Power BI のエンド ユーザーとして、ダッシュボード タイルに関する分析情報を取得する方法を説明します。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: et_MLSL2sA8
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: fcfb16de53b4e6c67b7c46fec87ab614d07cb9b1
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2019
ms.locfileid: "61049235"
---
# <a name="view-data-insights-on-dashboard-tiles-with-power-bi"></a>Power BI を使用してダッシュボード タイルに関するデータの分析情報を表示する
ダッシュボード上の各視覚化タイルはデータ実行の入り口です。 タイルを選択すると、レポートが開き、レポートの背後ではデータセットをフィルター処理し、並べ替えて掘り下げることができます。 また、インサイトを実行すると、Power BI でデータの探索が自動的に実行されます。

クイック インサイトを実行して、データに基づいて、興味のある対話型の視覚化を生成します。 特定のダッシュボード タイルでクイック インサイトを実行することができます。インサイトに対してインサイトを実行することもできます。

インサイトの基となっているのは、Microsoft Research と共同開発して拡大を続けている[高度な分析アルゴリズムのセット](end-user-insight-types.md)です。引き続きこれを使って、より多くの人が新しい直感的な方法でデータから詳細情報を見つけられるようにしていきます。

## <a name="run-insights-on-a-dashboard-tile"></a>ダッシュボード タイルへのインサイトの実行
ダッシュボード タイルでインサイトを実行すると、Power BI ではその 1 つのダッシュボード タイルを作成するために使用されたデータのみが検索されます。 

1. [ダッシュボードを開きます](end-user-dashboards.md)。
2. タイルの上にマウスを置きます。 省略記号 [...] を選択し、 **[詳細情報の表示]** を選択します。 

    ![省略記号メニュー モード](./media/end-user-insights/power-bi-hover.png)


3. タイルが[フォーカス モード](end-user-focus.md)で開き、インサイト カードが右側に表示されます。    
   
    ![フォーカス モード](./media/end-user-insights/pbi-insights-tile.png)    
4. 興味をそそる情報がありましたか? 詳細に確認するには、その分析情報カードを選択します。 選択した分析情報が左側に表示され、右側には、その単一の分析情報に含まれるデータのみに基づく新しい分析情報カードが表示されます。    

 ## <a name="interact-with-the-insight-cards"></a>インサイト カードとの対話
分析情報を開いたら、引き続き探索してください。

   * キャンバス上のビジュアルをフィルター処理します。  フィルターを表示するには、右上の矢印を選択し、[フィルター] ウィンドウを展開します。

     ![[フィルター] メニューが展開された分析情報](./media/end-user-insights/power-bi-insights-on-insights.png)
   
   * インサイト カード自体に対してインサイトを実行します。 これは**関連する分析情報**と呼ばれることがよくあります。 右上にある電球アイコン ![[分析情報の取得] アイコン](./media/end-user-insights/power-bi-bulb-icon.png) または **[分析情報の取得]** を選択します。
     
     ![[詳細情報の取得] アイコンが表示されたメニュー バー](./media/end-user-insights/power-bi-autoinsights-tile.png)
     
     インサイトが左側に表示され、右側には、その単一の情報に含まれるデータのみに基づく新しいカードが表示されます。
     
     ![詳細情報についての詳細情報](./media/end-user-insights/power-bi-insights-on-insights-new.png)

元のインサイト キャンバスに戻るには、左上にある **[フォーカス モードの終了]** を選択します。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
- **[分析情報の表示]** は、DirectQuery では機能しません。Power BI にアップロードされたデータに限り機能します。
- **[分析情報の表示]** を使用できない種類のダッシュボード タイルもあります。 たとえば、カスタム ビジュアルでは使用できません。<!--[custom visuals](end-user-custom-visuals.md)-->


## <a name="next-steps"></a>次の手順
使用できるクイック分析情報の種類については[こちら](end-user-insight-types.md)を参照してください。

