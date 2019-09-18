---
title: 'チュートリアル: Power BI サービス ダッシュボードでデータ アラートを設定する'
description: このチュートリアルでは、Microsoft Power BI サービスで設定した制限を超えてダッシュボード内のデータが変更された場合に通知されるように、アラートを設定する方法について説明します。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: removed
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: tutorial
ms.date: 08/26/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 16639f6e9bf005d04c64fc3ae6a331338efdd5d4
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2019
ms.locfileid: "70064545"
---
# <a name="tutorial-set-dashboard-alerts-on-power-bi-dashboards"></a>チュートリアル:Power BI ダッシュボードでアラートを設定する
ダッシュボード内のデータが設定した制限を上回って、または下回って変更された場合に通知されるように、アラートを設定します。 アラートは、ゲージ、KPI、カードに対して動作します。 この機能は進化し続けているため、[次の「ヒントとトラブルシューティング」セクション](#tips-and-troubleshooting)を参照してください。

![タイル、カード、KPI](media/end-user-alerts/card-gauge-kpi.png)

ダッシュボードを共有している場合であっても、見ることができるのは自分で設定したアラートだけです。 データ アラートはプラットフォーム間で完全に同期されます。[Power BI モバイル アプリ](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)および Power BI サービスで、データ アラートを設定して表示できます。 

> [!WARNING]
> これらのアラートは、データに関する情報を提供します。 モバイル デバイスで Power BI データを参照していて、そのデバイスが盗まれた場合、Power BI サービスを使用してすべてのアラートをオフにすることをお勧めします。
> 

このチュートリアルでは、以下について説明します。
> [!div class="checklist"]
> * 通知を設定できるユーザー
> * アラートをサポートするビジュアル
> * アラートが表示される対象のユーザー
> * Power BI Desktop およびモバイルでアラートを操作する
> * アラートの作成方法
> * アラートを受信する場所

Power BI にサインアップしていない場合は、[無料の試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)してください。

この例では、営業とマーケティングのサンプル アプリのダッシュボード カード タイルを使用しています。 このアプリは、[Microsoft AppSource](https://appsource.microsoft.com) から入手できます。 アプリの入手方法については、[Power BI でのアプリのインストールと使用](end-user-app-view.md)に関する説明を参照してください。

1. ダッシュボードのゲージ、KPI、またはカード タイルで、省略記号を選びます。
   
   ![カード タイル](media/end-user-alerts/power-bi-cards.png)
2. ベルのアイコン ![アラート アイコン](media/end-user-alerts/power-bi-bell-icon.png)、または **[アラートの管理]** を選択して、 **[総店舗数]** に 1 つまたは複数のアラートを追加します。

   ![省略記号が選択されているカード タイル](media/end-user-alerts/power-bi-ellipses.png)

   
1. **[アラートの管理]** ウィンドウで、 **[+ アラート ルールの追加]** を選択します。  スライダーが **[オン]** に設定されていることを確認し、アラートのタイトルを指定します。 タイトルは、アラートの内容を簡単に理解するために役立ちます。
   
   ![アラート管理ウィンドウ](media/end-user-alerts/power-bi-manage-alert.png)
4. 下にスクロールして、アラートの詳細を入力します。  この例では、市場シェアが 35 以上になった場合に 1 日に 1 回通知するアラートを作成します。 アラートは通知センターに表示されます。 電子メールの送信も設定します。
   
   ![アラート管理ウィンドウ、しきい値の設定](media/end-user-alerts/power-bi-manage-alert-details.png)
5. **[保存して閉じる]** を選びます。
 
   > [!NOTE]
   > アラートは更新されたデータでのみ動作します。 データが更新されると、Power BI はそのデータにアラートが設定されているかどうかを確認します。 データがアラートのしきい値に達した場合、アラートがトリガーされます。 
   > 

## <a name="receiving-alerts"></a>アラートの受信
追跡対象データがユーザー設定のしきい値のいずれかに達した場合は、いくつかの処理が行われます。 最初に、最後のアラートが送信されてから 1 時間以上または 24 時間以上 (選択したオプションによって異なる) 経過しているかどうかが確認されます。 データがしきい値を超えている場合に限り、アラートを受け取ります。

次に、Power BI によりアラートが通知センターに送信され、さらにオプションで電子メールでもアラートが送信されます。 各アラートにはデータへの直接リンクが含まれています。 リンクを選択して、関連するタイルを表示します。  

1. 電子メールを送信するようにアラートを設定した場合は、次のようなメールを受信します。 これは別のダッシュボードで設定したアラートです。このダッシュボードは、ユーザビリティ チームが完了したタスクを追跡します。
   
   ![アラート メール](media/end-user-alerts/power-bi-alert-email.png)
2. Power BI は、メッセージを**通知センター**に追加し、新しいアラート アイコンを該当するタイルに追加します。
   
   ![Power BI サービスの通知アイコン](media/end-user-alerts/power-bi-task-alert.png)
3. アラートの詳細を見るには通知センターを開きます。
   
    ![アラートを読む](media/end-user-alerts/power-bi-notification.png)
   
  

## <a name="managing-alerts"></a>アラートの管理

アラートを管理するには多くの方法があります。ダッシュボードのタイル自体、Power BI の [設定] メニュー、[iPhone の Power BI モバイル アプリ](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)または [Windows 10 用の Power BI モバイル アプリ](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)の個別のタイルなどで管理できます。

### <a name="from-the-tile-itself"></a>タイル自体から

1. タイルのアラートを変更または削除する必要がある場合は、ベルのアイコン ![アラート アイコン](media/end-user-alerts/power-bi-bell-icon.png) を選択して **[アラートの管理]** ウィンドウを再び開きます。 そのタイルに設定されているすべてのアラートが表示されます。
   
    ![アラート管理ウィンドウ](media/end-user-alerts/power-bi-manage-alerts.png).
2. アラートを変更するには、アラート名の左側にある矢印を選択します。
   
    ![アラート名の横の矢印](media/end-user-alerts/power-bi-modify-alert.png).
3. アラートを削除するには、アラート名の右側にあるごみ箱を選択します。
   
      ![選択されたごみ箱アイコン](media/end-user-alerts/power-bi-alert-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Power BI の [設定] メニューから

1. Power BI のメニュー バーで歯車アイコンを選択します。
   
    ![歯車アイコン](media/end-user-alerts/powerbi-gear-icon.png).
2. **[設定]** の **[アラート]** を選択します。
   
    ![[設定] ウィンドウの [アラート] タブ](media/end-user-alerts/power-bi-alert-settings.png)
3. ここからは、アラートをオンまたはオフにしたり、 **[アラートの管理]** ウィンドウを開いて変更を行ったり、アラートを削除したりできます。

## <a name="tips-and-troubleshooting"></a>ヒントとトラブルシューティング 

* アラートは、ゲージ、KPI、カードに対してのみ設定できます。
* ゲージ、KPI、またはカードに対してアラートを設定できない場合、システム管理者に問い合わせてください。 ダッシュボードまたは特定の種類のダッシュボード タイルでは、アラートがオフになっているか、使用できないことがあります。
* アラートは更新されたデータでのみ動作します。 静的データでは動作しません。 Microsoft が提供する多くのサンプルは、静的なものです。 


## <a name="clean-up-resources"></a>リソースをクリーンアップする
アラートを削除する手順については、上記で説明しています。 手短に言えば、Power BI のメニュー バーで歯車アイコンを選択します。 **[設定]** で **[アラート]** を選択し、アラートを削除します。

> [!div class="nextstepaction"]
> [モバイル デバイスでデータ アラートを設定する](mobile/mobile-set-data-alerts-in-the-mobile-apps.md)


