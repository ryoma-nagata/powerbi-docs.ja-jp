---
title: Power BI で SendGrid に接続する
description: Power BI 用 SendGrid
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: a05d78cfb0c1e34f0ec263f5455982cd4064905b
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185816"
---
# <a name="connect-to-sendgrid-with-power-bi"></a>Power BI で SendGrid に接続する
SendGrid 用 Power BI コンテンツ パックを使用すると、SendGrid アカウントから考察や統計情報を得ることができます。 SendGrid コンテンツ パックを使用して、SendGrid の統計情報をダッシュボードに視覚化することができます。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Power BI 用 [SendGrid コンテンツ パック](https://app.powerbi.com/getdata/services/sendgrid)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
   ![](media/service-connect-to-sendgrid/pbi_getdata.png) 
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
   ![](media/service-connect-to-sendgrid/pbi_getservices.png) 
3. **SendGrid** コンテンツ パックを選び、 **[取得]** をクリックします。
   
   ![](media/service-connect-to-sendgrid/sendgrid.png) 
4. ダイアログが表示されたら、SendGrid のユーザー名とパスワードを入力します。 **[サインイン]** をクリックします。
   
   ![](media/service-connect-to-sendgrid/pbi_sendgridsignin.png)
5. Power BI にデータがインポートされると、新しいダッシュボード、レポート、データセットが左側のナビゲーション ウィンドウに表示され、そこに過去 90 日間の電子メール統計情報が取り込まれています。 新しい項目には黄色のアスタリスク \* でマークが付けられます。
   
   ![](media/service-connect-to-sendgrid/pbi_sendgriddash.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="whats-included"></a>含まれるもの
SendGrid のダッシュ ボードで次のメトリックを使用できます。

* 全体的なメール統計情報 - 要求、配信済み、バウンス済み、スパム ブロック、スパム レポートなど。
* カテゴリ別のメール統計情報
* 地理別のメール統計情報
* ISP 別のメール統計情報
* デバイス、クライアント、ブラウザー別のメール統計情報

## <a name="next-steps"></a>次の手順
[Power BI とは?](power-bi-overview.md)

[データの取得](service-get-data.md)

