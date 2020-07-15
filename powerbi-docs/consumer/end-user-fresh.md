---
title: Power BI でコンテンツが最新の状態に維持されるしくみ
description: Power BI では、常に最新のデータ、レポート、ダッシュボード、アプリが使用されるようになっています。そのしくみについて説明します。
author: mihart
ms.service: powerbi
ms.reviewer: mihart
ms.custom: ''
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Get started
ms.openlocfilehash: 73affb07b137ee60fe00f7d344759ec2de1bcb85
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2020
ms.locfileid: "86215920"
---
# <a name="your-content-is-up-to-date"></a>コンテンツが最新の状態に維持される

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

*コンシューマー*は、*デザイナー*が作成し、コンシューマーと共有したコンテンツを使用します。 そのコンテンツが最新の状態になっているか気になることがあるでしょう。あるいは、コンテンツの最終更新日が知りたくなることもあります。 最新のコンテンツを使用していることがわかれば、自信を持って作業できます。  
 
![Power BI ダッシュボード](media/end-user-fresh/power-bi-dashboards.png)


必ず最新のデータを使用することは、多くの場合、正しい意思決定をする上で重要です。 最新のコンテンツを確実に使用するには何ができるでしょうか。 ほとんどの場合、何もする必要はありません。 共有アプリはアプリ デザイナーが設定したスケジュールに基づいて自動的に更新されます。 共有ダッシュボードや共有レポートの場合も同じです。デザイナーが手作業か、自動更新スケジュールを利用し、コンテンツが最新の状態に維持されるように取り計らいます。  

データの新しさについて疑問があれば、デザイナーにお問い合わせください。

## <a name="how-to-locate-the-name-of-the-designer-or-owner"></a>デザイナーまたは所有者の名前を見つける方法

### <a name="dashboard-or-report"></a>ダッシュボードまたはレポート

所有者の名前は、ダッシュボードとレポートのタイトル バーでわかります。 レポートまたはダッシュボードの名前を選択すると、**所有者**を含む追加の詳細が表示されます。

![Power BI ダッシュボードの所有者](media/end-user-fresh/power-bi-owner.png)


### <a name="apps"></a>アプリ

アプリ画面には、デザイナーの名前とアプリの最終更新日時が表示されます。  

1. ナビ ペインから **[アプリ]** を選択します。

    ![ナビゲーション ウィンドウ](media/end-user-fresh/power-bi-nav-app.png)



2. アプリをポイントすると、タイトル、更新日、デザイナーの名前が表示されます。 

    ![2 つのアプリの内、1 つが選択されています](media/end-user-fresh/power-bi-app.png)


### <a name="shared-with-me"></a>共有アイテム
**[共有アイテム]** 画面には、コンテンツ所有者の名前とコンテンツが最後に共有された日付が表示されます。

![共有アイテム画面に変更日付と所有者が表示されています](media/end-user-fresh/power-bi-share.png) 


## <a name="how-to-look-up-the-last-refresh-date"></a>最終更新日を調べる方法
最終更新日に興味があれば、ほとんどのコンテンツでそれを調べることができます。 

### <a name="dashboard-tiles"></a>ダッシュボード タイル
ダッシュボード タイルの場合、タイルをフォーカス モードで表示すると、最終更新日のタイムスタンプが表示されます。

1. ダッシュボード タイルで**その他のオプション** (...) を選択し、 **[フォーカス モードで開く]** を選択します。

    ![省略記号を選択すると表示されるメニュー](media/end-user-fresh/power-bi-focus-mode.png)

2. 右上隅に最終更新日が表示されます。 表示されない場合、ブラウザーの幅を大きくしてください。 

    ![幅を広くしたブラウザーに最終更新日が表示されています](media/end-user-fresh/power-bi-last-refresh2.png)

### <a name="dashboards-and-reports"></a>ダッシュボードとレポート
最終更新日を調べるもう 1 つの方法に **[関連の表示]** を使用する方法があります。  **[関連の表示]** は、Power BI の上部メニュー バーから**その他のオプション** (...) を選択して利用できます。

![メニューから [関連の表示] を選択する](media/end-user-fresh/power-bi-view-related-dropdown.png)

**[関連コンテンツ]** ウィンドウに、ダッシュボードまたはレポートの基になるデータセットの最終更新情報が表示されます。

![Power BI ダッシュボード](media/end-user-fresh/power-bi-refresh.png)

## <a name="what-happens-if-an-app-is-deleted-by-the-designer"></a>デザイナーがアプリを削除するとどうなるか

デザイナーがアプリを削除すると、そのアプリに関連付けられているダッシュボードやレポートも Power BI ワークスペースから自動的に削除されます。 今後は利用できなくなり、アプリは [アプリ] コンテナーまたはナビ ペインの他の場所に表示されなくなります。


## <a name="subscribe-to-see-changes"></a>サブスクライブして変更を確認する
最新の状態に維持する別の方法として、レポートやダッシュボードにサブスクライブするという方法があります。 ログインしてレポートやダッシュボードを開く代わりに、設定したスケジュールに基づいてスナップショットを送信するように Power BI に指示します。  詳細については、[ダッシュボードとレポートにサブスクライブする](end-user-subscribe.md)方法に関するページを参照してください。

## <a name="set-data-alerts"></a>データ アラートの設定
設定した上限を超えてデータが変化した場合、通知を受けますか。 [データ アラートを作成します](end-user-alerts.md)。  データ アラートを使用すれば、最新の状態を維持することが簡単になります。 データ アラートを使用して、レポート内の値が特定のしきい値を超えた場合、電子メールを送信するように Power BI に指示します。  たとえば、在庫が 25 ユニットを下回った場合や売上が目標を超えた場合にメールを受信します。  

## <a name="next-steps"></a>次のステップ
[データ アラートを作成する](end-user-alerts.md)    
[ダッシュボードとレポートにサブスクライブする](end-user-subscribe.md)    
[関連するコンテンツを表示する](end-user-related.md)    
