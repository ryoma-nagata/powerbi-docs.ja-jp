---
title: Power BI サービスでデータ アラートを設定する
description: Microsoft Power BI サービスで設定した制限を超えてダッシュボード内のデータが変更された場合に通知されるように、アラートを設定する方法について説明します。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/28/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: a26cd6d654f9378d9fa09ae46b64762213b26089
ms.sourcegitcommit: f05ba39a0e46cb9cb43454772fbc5397089d58b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68522981"
---
# <a name="data-alerts-in-power-bi-service"></a>Power BI サービスでのデータ アラート
アラートを設定すると、ダッシュボード内のデータが設定した制限を超えて変更された場合に通知されます。 

Power BI Pro のライセンスがある場合、または [Premium 容量](service-premium-what-is.md)からダッシュボードを共有されている場合は、タイルにアラートを設定できます。 アラートは、レポートのビジュアルからピン留めされたタイルでのみ、ゲージ、KPI、カードに対してだけ設定できます。 アラートは、レポートからダッシュボードにピン留めしたストリーミング データセットから作成されるビジュアルに設定できますが、 **[タイルの追加]**  >  **[カスタム ストリーミング データ]** でダッシュボードで直接作成したストリーミング タイルには設定できません。 

ダッシュボードを共有している場合であっても、見ることができるのは自分で設定したアラートだけです。 データ アラートはプラットフォーム間で完全に同期されます。[Power BI モバイル アプリ](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)および Power BI サービスで、データ アラートを設定して表示できます。 これらを Power BI Desktop で使用することはできません。 アラートを[自動化し、Microsoft Flow と統合することもできます。](https://flow.microsoft.com) - [お試しください](service-flow-integration.md)。

![タイル](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> データ ドリブン アラート通知は、データに関する情報を提供します。 モバイル デバイスで Power BI データを表示し、そのデバイスが盗まれた場合、Power BI サービスを使用して、すべてのデータ ドリブン アラート ルールをオフにすることをお勧めします。
> 
> 

## <a name="set-data-alerts-in-power-bi-service"></a>Power BI サービスでのデータ アラートの設定
Amanda がダッシュボードのタイルにいくつかのアラートを追加する様子をご覧ください。 その後、ビデオで説明されている手順に従って、ご自分でやってみてください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

この例では、Retail Analysis サンプル ダッシュボードのカード タイルを使用します。

1. ダッシュボードで開始します。 ダッシュボードのゲージ、KPI、またはカード タイルで、省略記号を選びます。
   
   ![[Total Stores] タイル](media/service-set-data-alerts/powerbi-card.png)
2. ベルのアイコン ![アラート アイコン](media/service-set-data-alerts/power-bi-bell-icon.png) を選択して、 **[Total stores]** に 1 つまたは複数のアラートを追加します。
   
1. 最初に、 **[+ アラート ルールの追加]** を選んで、スライダーが **[オン]** に設定されていることを確認し、アラートのタイトルを指定します。 タイトルは、アラートの内容を簡単に理解するために役立ちます。
   
   ![アラート管理ウィンドウ](media/service-set-data-alerts/powerbi-alert-title.png)
4. 下にスクロールして、アラートの詳細を入力します。  この例では、"Total stores" の値が 100 を超えた場合に 1 日に 1 回通知するアラートを作成します。 アラートは通知センターに表示されます。 電子メールの送信も設定します。
   
   ![アラート管理ウィンドウ、しきい値の設定](media/service-set-data-alerts/power-bi-set-alert-details.png)
5. **[保存]** を選択します。

## <a name="receiving-alerts"></a>アラートの受信
追跡対象データがユーザー設定のしきい値のいずれかに達した場合は、いくつかの処理が行われます。 最初に、最後のアラートが送信されてから 1 時間以上または 24 時間以上 (選択したオプションによって異なる) 経過しているかどうかが確認されます。 データがしきい値を超えている場合に限り、アラートを受け取ります。

次に、通知センターにアラートが送信され、さらにオプションで電子メールでもアラートが送信されます。 各アラートにはデータへの直接リンクが含まれています。 リンクを選択して関連するタイルを表示し、調査、共有、詳細の確認を行うことができます。  

1. 電子メールを送信するようにアラートを設定した場合は、次のようなメールを受信します。
   
   ![アラート メール](media/service-set-data-alerts/powerbi-alerts-email.png)
2. Power BI は、メッセージを**通知センター**に追加し、新しいアラート アイコンを該当するタイルに追加します。
   
   ![Power BI サービスの通知アイコン](media/service-set-data-alerts/powerbi-alert-notifications.png)
3. アラートの詳細を見るには通知センターを開きます。
   
    ![アラートを読む](media/service-set-data-alerts/powerbi-alert-notification.png)
   
   > [!NOTE]
   > アラートは更新されたデータでのみ動作します。 データが更新されると、Power BI はそのデータにアラートが設定されているかどうかを確認します。 データがアラートのしきい値に達した場合、アラートがトリガーされます。
   > 
   > 

## <a name="managing-alerts"></a>アラートの管理
アラートを管理するには多くの方法があります。ダッシュボードのタイル自体、Power BI の [設定] メニュー、[iPhone の Power BI モバイル アプリ](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)または [Windows 10 用の Power BI モバイル アプリ](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)の個別のタイルなどで管理できます。

### <a name="from-the-tile-itself"></a>タイル自体から
1. タイルのアラートを変更または削除する必要がある場合は、ベルのアイコン ![アラート アイコン](media/service-set-data-alerts/power-bi-bell-icon.png) を選択して **[アラートの管理]** ウィンドウを再び開きます。 そのタイルに設定されているすべてのアラートが表示されます。
   
    ![アラート管理ウィンドウ](media/service-set-data-alerts/powerbi-see-alerts.png).
2. アラートを変更するには、アラート名の左側にある矢印を選択します。
   
    ![アラート名の横の矢印](media/service-set-data-alerts/powerbi-see-alerts-arrow.png).
3. アラートを削除するには、アラート名の右側にあるごみ箱を選択します。
   
      ![選択されたごみ箱アイコン](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>Power BI の [設定] メニューから
1. Power BI のメニュー バーで歯車アイコンを選択します。
   
    ![歯車アイコン](media/service-set-data-alerts/powerbi-gear-icon.png).
2. **[設定]** の **[アラート]** を選択します。
   
    ![[設定] ウィンドウの [アラート] タブ](media/service-set-data-alerts/powerbi-alert-settings.png)
3. ここからは、アラートをオンまたはオフにしたり、 **[アラートの管理]** ウィンドウを開いて変更を行ったり、アラートを削除したりできます。

## <a name="tips-and-troubleshooting"></a>ヒントとトラブルシューティング
* 現在、Bing タイルまたは日付/時刻メジャーを含むカード タイルについては、アラートはサポートされていません。
* アラートは、数値データ型でのみ機能します。
* アラートは更新されたデータでのみ動作します。 静的データでは動作しません。
* KPI/カード/ゲージ レポート ビジュアルを作成し、そのビジュアルをダッシュボードにピン留めした場合、アラートはストリーミング データセットでのみ動作します。

## <a name="next-steps"></a>次の手順
[データ アラートを含む Microsoft Flow を作成する](service-flow-integration.md)    
[モバイル デバイスでデータ アラートを設定する](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)    
[Power BI とは?](power-bi-overview.md)    
他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](http://community.powerbi.com/)。

