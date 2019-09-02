---
title: Power BI で VMob に接続する
description: Power BI 用 VMob
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e6c63d93c876377da7a5d36e814431dfda8665c3
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185781"
---
# <a name="connect-to-vmob-with-power-bi"></a>Power BI で VMob に接続する
VMob データの追跡と探索は、Power BI と VMob コンテンツ パックを使って簡単に行うことができます。 Power BI によって取得されるデータは、すべての期間と過去 30 日間のユーザー統計情報、過去 30 日間の販売 KPI、過去 30 日間のキャンペーンの成果です。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Power BI 用 [VMob コンテンツ パック](https://app.powerbi.com/getdata/services/vmob)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
    ![](media/service-connect-to-vmob/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
   ![](media/service-connect-to-vmob/services.png)
3. **[VMob]** \> **[接続]** を選びます。
   
   ![](media/service-connect-to-vmob/vmob.png)
4. プロンプトが表示されたら、VMob URL を入力し、[次へ] をクリックします。 この URL は、VMob によって個別に提供されます。
   
    ![](media/service-connect-to-vmob/params.png)
5. [認証方法] ドロップダウンで **[基本]** オプションを選択し、VMob のユーザー名とパスワードを入力して、 **[サイン イン]** をクリックします。
   
    ![](media/service-connect-to-vmob/creds.png)
6. インポート処理が自動的に開始され、Power BI によって VMob データが取得され、すぐに使えるダッシュボードとレポートが作成されます。
   
   ![](media/service-connect-to-vmob/dashboard2.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="next-steps"></a>次の手順
[Power BI の概要](service-get-started.md)

[Power BI でデータを取得する](service-get-data.md)

