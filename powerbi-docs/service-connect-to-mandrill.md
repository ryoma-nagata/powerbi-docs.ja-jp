---
title: Power BI で Mandrill に接続する
description: Power BI 用 Mandrill
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 7440fb6dfcd181b6b1164260626cd0bfa7cda991
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185417"
---
# <a name="connect-to-mandrill-with-power-bi"></a>Power BI で Mandrill に接続する
Power BI コンテンツ パックはお客様の Mandrill アカウントからデータを取得し、ダッシュボード、一連のレポート、およびデータセットを生成してデータを探索できるようにします。 Mandrill の分析を使用すると、ニュースレターや販促活動の情報を素早く取得できます。 データは、毎日更新されるように設定されているため、監視対象のデータが常に最新の状態に保たれています。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Power BI 用 Mandrill コンテンツ パック](http://app.powerbi.com/getdata/services/mandrill)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
    ![](media/service-connect-to-mandrill/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
    ![](media/service-connect-to-mandrill/services.png)
3. **[Mandrill]**  >  **[取得]** の順に選択します。
   
    ![](media/service-connect-to-mandrill/mandrill.png)
4. **[認証方法]** として **[キー]** を選択し、API キーを指定します。 キーは、Mandrill ダッシュボードの **[設定]** タブで確認できます。 **[サインイン]** を選択すると、インポート プロセスが始まります。このプロセスは、お客様のアカウントのデータ量によっては数分かかることがあります。
   
    ![](media/service-connect-to-mandrill/auth.png)
5. Power BI によるデータのインポート後、新しいダッシュ ボード、レポート、データセットが左側のナビゲーション ウィンドウに表示されます。 これは、データを表示するために Power BI によって作成された既定のダッシュボードです。
   
    ![](media/service-connect-to-mandrill/mandrill-dashboard1.jpg)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="next-steps"></a>次の手順
[Power BI とは?](power-bi-overview.md)

[Power BI サービスのデザイナー向けの基本的な概念](service-basic-concepts.md)

