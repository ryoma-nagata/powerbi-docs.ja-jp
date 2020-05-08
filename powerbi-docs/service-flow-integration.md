---
title: Power BI と Power Automate との統合
description: Power BI データ アラートによってトリガーされる Power Automate フローを作成する方法について説明します。
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: YhmNstC39Mw
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/25/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: aafba825c5bd4ece3c8b97256d5943f91b456cd7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "77609700"
---
# <a name="power-automate-and-power-bi"></a>Power Automate と Power BI

[Power Automate](https://docs.microsoft.com/power-automate/getting-started) は、ビジネス ユーザーが依存するアプリケーションや SaaS サービスが増える中で、全体のワークフローを自動化する機能を提供する SaaS です。 Power Automate を使用すると、お気に入りのアプリとサービス (Power BI を含む) を統合することで、通知の受信、ファイルの同期、データの収集などのタスクを自動化できます。 ワークフローを自動化すると、反復的なタスクが容易になります。

[Power Automate の使用を今すぐ開始しましょう。](https://docs.microsoft.com/power-automate/getting-started)

Power BI のアラートがトリガーされたときに詳細なメールを同僚に送信する Power Automate フローを Sirui が作成するところをご覧ください。 その後、ビデオで説明されている手順に従って、ご自分でやってみてください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/YhmNstC39Mw" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-flow-that-is-triggered-by-a-power-bi-data-alert"></a>Power BI データ アラートでトリガーされるフローを作成する

### <a name="prerequisites"></a>前提条件
このチュートリアルでは、フローをテンプレートから作成する方法とゼロから作成する方法について説明します。 この手順を行うには、[Power BI でデータ アラートを作成](service-set-data-alerts.md)し、[無料の Slack アカウントを作成](https://flow.microsoft.com/#home-signup)してから Power Automate にサインアップしてください (サインアップは無料です)。

## <a name="create-a-flow-that-uses-power-bi---from-a-template"></a>Power BI を使用するフローをテンプレートから作成する
このタスクでは、テンプレートを使用して、Power BI データ アラート (通知) によってトリガーされるシンプルなフローを作成します。

1. Power Automate にサインインします (flow.microsoft.com)。
2. **[自分のフロー]** を選択します。
   
   ![Power Automate のメニュー バー](media/service-flow-integration/power-bi-my-flows.png)
3. **[テンプレートから作成]** を選択します。
   
    ![マイ フローのメニュー バー](media/service-flow-integration/power-bi-template.png)
4. [検索] ボックスを使用して Power BI テンプレートを検索し、 **[Power BI データ アラートがトリガーされたときに対象ユーザーにメールを送信する] > [続行]** の順に選択します。
   
    ![検索結果](media/service-flow-integration/power-bi-flow-alert.png)


### <a name="build-the-flow"></a>フローを構築する
このテンプレートには、1 つのトリガー (アイルランドが新しいオリンピック メダルを獲得するとトリガーされる Power BI データ アラート) と、1 つのアクション (メールを送信する) が含まれています。 Power Automate でフィールドを選択すると、含めることができる動的なコンテンツが表示されます。  この例では、メッセージの本文にタイル値とタイル URL を含めます。

![フロー テンプレート](media/service-flow-integration/power-bi-template1.png)

1. トリガーのドロップダウンから Power BI データ アラートを選択します。 **[アイルランドが新しいメダルを獲得]** を選びます。 アラートの作成方法については、「[Data alerts in Power BI](service-set-data-alerts.md)」(Power BI のデータ アラート) を参照してください。
   
   ![アラート ドロップダウン](media/service-flow-integration/power-bi-trigger-flow.png)
2. 1 つまたは複数の有効なメール アドレスを入力し、 **[編集]** (下図参照) または **[動的なコンテンツの追加]** を選択します。 
   
   ![電子メール送信画面](media/service-flow-integration/power-bi-flow-email.png)

3. Power Automate では、保持や変更が可能なタイトルとメッセージが自動的に作成されます。 Power BI でアラートを作成するときに設定したすべての値を使用できます。やり方は、グレーの強調表示されている領域にカーソルを合わせ、選択するだけです。 

   ![電子メール送信画面](media/service-flow-integration/power-bi-flow-email-default.png)

1.  たとえば、Power BI で**さらにメダルを獲得**というタイトルのアラートを作成した場合、 **[アラートのタイトル]** を選択すると、そのテキストをメールの件名フィールドに追加できます。

    ![メール テキストの作成](media/service-flow-integration/power-bi-flow-message.png)

    また、既定のメールの本文をそのまま使うことも、独自に作成することもできます。 上記の例には、メッセージにいくつかの変更が含まれています。

1. 終わったら、 **[フローの作成]** または **[フローの保存]** を選びます。  フローが作成され、評価されます。  Power Automate でエラーが検出されると、通知が表示されます。
2. エラーが検出された場合、 **[フローの編集]** を選択して修正するか、 **[完了]** を選択して新しいフローを実行します。
   
   ![成功メッセージ](media/service-flow-integration/power-bi-flow-running.png)
5. データ アラートがトリガーされると、指定したアドレスにメールが送信されます。  
   
   ![アラート メール](media/service-flow-integration/power-bi-flow-email2.png)

## <a name="create-a-power-automate-that-uses-power-bi---from-scratch-blank"></a>Power BI を使用する Power Automate フローを最初 (ゼロ) から作成する
このタスクでは、Power BI データ アラート (通知) によってトリガーされるシンプルなフローをゼロから作成します。

1. Power Automate にサインインします。
2. **[マイ フロー]**  >  **[一から作成]** の順に選びます。
   
   ![Power Automate の上部メニュー バー](media/service-flow-integration/power-bi-my-flows.png)
3. [検索] ボックスを使用して Power BI トリガーを検索し、 **[Power BI - When a data driven alert is triggered]\(Power BI - データ ドリブン アラートがトリガーされた場合\)** を選択します。

### <a name="build-your-flow"></a>フローを構築する
1. ドロップダウンからアラート名を選択します。  アラートの作成方法については、「[Data alerts in Power BI](service-set-data-alerts.md)」(Power BI のデータ アラート) を参照してください。
   
    ![アラートの名前の選択](media/service-flow-integration/power-bi-totalstores2.png)
2. **[新しいステップ]**  >  **[アクションの追加]** を選択します。
   
   ![新しいステップの追加](media/service-flow-integration/power-bi-new-step.png)
3. 「**Outlook**」を検索し、 **[Create event]** (イベントの作成) を選択します。
   
   ![フローの構築](media/service-flow-integration/power-bi-create-event.png)
4. イベント フィールドに入力します。 Power Automate でフィールドを選択すると、含めることができる動的なコンテンツが表示されます。
   
   ![フローの作成の続行](media/service-flow-integration/power-bi-flow-event.png)
5. 完了したら、 **[フローの作成]** を選択します。  Power Automate によってフローが保存され、評価されます。 エラーがない場合、 **[完了]** を選択してこのフローを実行します。  新しいフローが **[自分のフロー]** ページに追加されます。
   
   ![フローの完了](media/service-flow-integration/power-bi-flow-running.png)
6. Power BI データ アラートでフローがトリガーされると、次のような Outlook イベント通知を受け取ります。
   
    ![Power Automate による Outlook 通知のトリガー](media/service-flow-integration/power-bi-flow-notice.png)

## <a name="next-steps"></a>次のステップ
* [Power Automate の概要](https://docs.microsoft.com/power-automate/getting-started/)
* [Power BI サービスでのデータ アラートの設定](service-set-data-alerts.md)
* [iPhone でデータ アラートを設定する](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* [Windows 10 用の Power BI モバイル アプリでデータ アラートを設定する](consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)
* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

