---
title: コンシューマー向け Power BI サービスのダッシュボードのタイル
description: コンシューマー向け Power BI のダッシュボードのタイルの概要。 これには、SQL Server Reporting Services (SSRS) から作成されるタイルが含まれます。
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 0481a09aaeac4f6c76c49d3a816ac880cdb9d60b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "79114057"
---
# <a name="dashboard-tiles-in-power-bi"></a>Power BI のダッシュボードのタイル

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

タイルは、*デザイナー*によってダッシュボードにピン留めされた、データのスナップショットです。 "*デザイナー*" は、レポート、データセット、ダッシュボード、Q&A 質問ボックス、Excel、SQL Server Reporting Services (SSRS) などから、タイルを作成できます。  次のスクリーンショットは、ダッシュボードにピン留めされているさまざまなタイルを示しています。

![Power BI ダッシュボード](./media/end-user-tiles/power-bi-dash.png)


レポートからピン留めされたタイルに加え、*デザイナー*は **[タイルの追加]** を利用し、ダッシュボードに直接、スタンドアロンのタイルを追加できます。 スタンドアロン タイルには、テキスト ボックス、画像、ビデオ、ストリーミング データ、Web コンテンツが含まれます。

Power BI を構成する要素を理解するうえで助けが必要ですか?  「[Power BI - 基本的な概念](end-user-basic-concepts.md)」を参照してください。


## <a name="interacting-with-tiles-on-a-dashboard"></a>ダッシュボードのタイルと対話する

1. タイルにマウス カーソルを置き、省略記号を表示します。
   
    ![タイルの省略記号](./media/end-user-tiles/ellipses_new.png)
2. 省略記号を選んで、タイルの操作メニューを開きます。 利用できるオプションは、視覚化タイプやタイルの作成方法によって異なります。 たとえば、次のような項目が表示されます。

    - Q&A を利用して作成されたタイル
   
        ![省略記号アイコン](./media/end-user-tiles/power-bi-options-1.png)

    - ブックから作成されたタイル
   
        ![省略記号アイコン](./media/end-user-tiles/power-bi-options-2.png)

    - レポートから作成されたタイル
   
        ![省略記号アイコン](./media/end-user-tiles/power-bi-options-3.png)
   
    ここでは、次の操作を実行できます。
   
   * [このタイルの作成に使われたレポートを開く ](end-user-reports.md) ![レポート アイコン](./media/end-user-tiles/chart-icon.jpg)  
   
   * [タイルの作成に使用した Q&A 質問を開く ](end-user-reports.md) ![Q&A アイコン](./media/end-user-tiles/qna-icon.png)  
   

   * [このタイルの作成に使われたブックを開く ](end-user-reports.md) ![ワークシート アイコン](./media/end-user-tiles/power-bi-open-worksheet.png)  
   * [フォーカス モードでタイルを表示する ](end-user-focus.md) ![フォーカス アイコン](./media/end-user-tiles/fullscreen-icon.jpg)  
   * [分析情報を表示する ](end-user-insights.md) ![分析情報アイコン](./media/end-user-tiles/power-bi-insights.png)
   * [コメントを追加し、ディスカッションを開始する ](end-user-comment.md) ![コメント アイコン](./media/end-user-tiles/comment-icons.png)
   * [ダッシュボードのタイルで設定されたアラートを管理する ](end-user-alerts.md) ![アラート アイコン](./media/end-user-tiles/power-bi-alert-icon.png)
   * [Excel でデータを開く ](end-user-export.md) ![エクスポート アイコン](./media/end-user-tiles/power-bi-export-icon.png)


3. 操作メニューを閉じるには、キャンバスの空白領域を選びます。

### <a name="select-click-a-tile"></a>タイルの選択 (クリック)
タイルを選択したときに次に生じる動作は、タイルの作成方法、および[カスタム リンク](../service-dashboard-edit-tile.md)があるかどうかによって異なります。 カスタム リンクがある場合、タイルを選択するとそのリンクに移動します。 それ以外の場合、タイルを選択すると、そのタイルを作成するために使われたレポート、Excel Online ブック、オンプレミスの SSRS レポート、Q&A の質問に移動します。

> [!NOTE]
> 例外は、 **[タイルを追加]** を使ってダッシュボードに直接作成したビデオ タイルの場合です。 (この方法で作成された) ビデオ タイルを選択すると、ダッシュボード上で直接ビデオが再生されます。   
> 
> 

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
* 視覚エフェクトの作成に使われたレポートが保存されなかった場合は、タイルを選択してもアクションは発生しません。
* Excel Online のブックから作成されたタイルの場合、そのブックに対して少なくとも読み取りのアクセス許可がないと、タイルを選択したときにブックが Excel Online で開かれません。
* **[タイルの追加]** を使ってダッシュボード上に直接作成されたタイルについては、カスタム ハイパーリンクが設定されている場合は、タイトル、サブタイトル、またはタイルを選択したときにその URL が開かれます。  それ以外の場合、既定では、イメージ、Web コード、またはテキスト ボックスのためにダッシュボード上に直接作成されたこれらのタイルのいずれかを選択しても、アクションは実行されません。
* SSRS 内のレポートに対する権限がない場合、SSRS から作成されたタイルを選択すると、アクセス権がないことを示すページが生成されます (rsAccessDenied)。
* SSRS サーバーが置かれたネットワークへのアクセス権がない場合、SSRS から作成されたタイルを選択すると、サーバーが見つからないことを示すページが生成されます (HTTP 404)。 レポートを表示するには、デバイスにレポート サーバーへのネットワーク アクセスが必要です。
* タイルの作成に使った元の視覚エフェクトが変更された場合、タイルは変更されません。  たとえば、*デザイナー*がレポートからの折れ線グラフをピン留めし、折れ線グラフを横棒グラフに変更した場合でも、ダッシュボード タイルは引き続き折れ線グラフを表示します。 データは更新されますが、視覚化の種類は変更されません。

## <a name="next-steps"></a>次のステップ
[データ更新](../refresh-data.md)

[Power BI - 基本的な概念](end-user-basic-concepts.md)
