---
title: Power BI で Azure Mobile Engagement に接続する
description: Power BI 用 Azure Mobile Engagement
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 5563bec1bc68d8e0dd5749a124c405c4383003db
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70186011"
---
# <a name="connect-to-azure-mobile-engagement-with-power-bi"></a>Power BI で Azure Mobile Engagement に接続する
Power BI Azure Mobile Engagement コンテンツ パックを使用すると、短時間でアプリ データの情報を得られます。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Power BI 用 [Azure Mobile Engagement コンテンツ パック](https://app.powerbi.com/groups/me/getdata/services/azme)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
    ![](media/service-connect-to-azure-mobile/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
    ![](media/service-connect-to-azure-mobile/services.png)
3. **[Azure Mobile Engagement]** \> **[取得]** を選択します。
   
    ![](media/service-connect-to-azure-mobile/azme.png) 
4. アプリのコレクションとアプリ名を指定します。 この情報は、Azure Mobile Engagement アカウントにあります。
   
    ![](media/service-connect-to-azure-mobile/parameters.png) 
5. [認証方式] で、キーを入力し、[サインイン] をクリックします。
   
    ![](media/service-connect-to-azure-mobile/creds.png)
6. Power BI によるデータのインポート後、新しいダッシュ ボード、レポート、データセットが左側のナビゲーション ウィンドウに表示されます。 新しい項目は、黄色のアスタリスク (\*) でマークされます。このアスタリスクは、選択すると非表示になります。
   
    ![](media/service-connect-to-azure-mobile/dashboard.png)

## <a name="what-now"></a>実行できる操作

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="next-steps"></a>次の手順
[Power BI の概要](service-get-started.md)

[Power BI でデータを取得する](service-get-data.md)

