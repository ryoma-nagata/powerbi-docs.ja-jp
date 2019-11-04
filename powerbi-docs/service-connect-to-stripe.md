---
title: Power BI で Stripe に接続する
description: Power BI 用 Stripe
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: b0e8739e93d24ba10b0ffc72042b847cce1d5fe9
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060767"
---
# <a name="connect-to-stripe-with-power-bi"></a>Power BI で Stripe に接続する
Power BI コンテンツ パックを使用して、Power BI 内の Stripe データを視覚化および探索します。 Power BI の Stripe コンテンツ パックでは、顧客、料金、イベント、請求書に関するデータを取得します。 データには、過去 30 日間での最新の 1 万件のイベントと 5000 件の料金が含まれています。 コンテンツは、ユーザーの管理するスケジュールに従って 1 日に 1 回、自動的に更新されます。 

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Power BI 用 Stripe コンテンツ パック](https://app.powerbi.com/getdata/services/stripe)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある [データの取得] を選択します。  
   
    ![](media/service-connect-to-stripe/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。  
   
    ![](media/service-connect-to-stripe/services.png)  
3. **[Stripe]** &gt; **[取得]** を選びます。  
   
    ![](media/service-connect-to-stripe/stripe.png)  
4. お使いの Stripe [API キー](https://dashboard.stripe.com/account/apikeys)を指定して接続します。  
   
    ![](media/service-connect-to-stripe/creds.png)
5. インポート処理が自動的に開始されます。 完了すると、アスタリスクの付いたナビゲーション ウィンドウに、新しいダッシュボード、レポート、モデルが表示されます。 インポートされたデータを表示するダッシュボードを選択します。
   
    ![](media/service-connect-to-stripe/dashboard.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="next-steps"></a>次の手順
[Power BI とは?](fundamentals/power-bi-overview.md)

[Power BI のデータの取得](service-get-data.md)

