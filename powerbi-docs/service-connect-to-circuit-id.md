---
title: Power BI で Circuit ID に接続する
description: Power BI 用 Circuit ID
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 3c8ef3e522c9f20ff9602d29670ccaf28cd92048
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185939"
---
# <a name="connect-to-circuit-id-with-power-bi"></a>Power BI で Circuit ID に接続する
Circuit ID からの通信データの分析は、Power BI を使えば簡単に行えます。 Power BI は、データを取得し、そのデータに基づいて既定のダッシュボードと関連レポートを作成します。 接続すると、データの探索や、必要に応じたダッシュボードのカスタマイズを行えます。 データは毎日自動的に更新されます。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Power BI 用 [Circuit ID コンテンツ パック](https://app.powerbi.com/getdata/services/circuitid)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
    ![](media/service-connect-to-circuit-id/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
    ![](media/service-connect-to-circuit-id/services.png)
3. **[Circuit ID]** \> **[接続]** の順に選択します。
   
    ![](media/service-connect-to-circuit-id/circuitid.png)
4. [認証方式] で、[Basic] を選択し、ユーザー名とパスワードを入力します。 続いて、[サインイン] をクリックします。
   
    ![](media/service-connect-to-circuit-id/circuitid_login.png)
5. Power BI によるデータのインポート後、新しいダッシュ ボード、レポート、データセットが左側のナビゲーション ウィンドウに表示されます。 新しい項目には黄色のアスタリスクでマークが付けられます。
   
    ![](media/service-connect-to-circuit-id/circuitid_dashboard_chrome.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="next-steps"></a>次の手順
[Power BI とは?](power-bi-overview.md)

[Power BI のデータの取得](service-get-data.md)

