---
title: Power BI で Planview Enterprise に接続する
description: Power BI 用 Planview Enterprise
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 64b8b0cce79e2c859ea4d926e1f0d3dfc0c1b83b
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185845"
---
# <a name="connect-to-planview-enterprise-with-power-bi"></a>Power BI で Planview Enterprise に接続する
Planview Enterprise コンテンツ パックを使用すると、Power BI で直接、リソースと作業管理データをまったく新しい方法で視覚化できます。 Planview Enterprise サインイン資格情報を使用して、ポートフォリオへの投資を対話形式で表示し、予算を上回ったり下回ったりしている部分を認識し、会社の戦略的優先順位とのプロジェクトの整合度合いを把握できます。 また、既定のダッシュボードやレポートを拡張して最も重要な情報を入手することもできます。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Power BI 用 Planview Enterprise コンテンツ パック](https://app.powerbi.com/getdata/services/planview-enterprise)に接続します

>[!NOTE]
>Planview Enterprise データを Power BI にインポートするには、ロールで Reporting Portal Viewer 機能が有効になっている Planview Enterprise ユーザーである必要があります。 下の追加要件を参照してください。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
    ![](media/service-connect-to-planview/get.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
    ![](media/service-connect-to-planview/services.png)
3. Power BI ページで **[Planview Enterprise]** を選択し、 **[取得]** を選択します。  
    ![](media/service-connect-to-planview/planview.png)
4. [Planview Enterprise URL] テキスト ボックスに、使用する Planview Enterprise サーバーの URL を入力します。 [Planview Enterprise データベース] テキスト ボックスに Planview Enterprise データベースの名前を入力して、[次へ] をクリックします。  
    ![](media/service-connect-to-planview/params.png)
5. [認証方法] ボックスの一覧で、 **[基本]** を選択します。 アカウントの **[ユーザー名]** と **[パスワード]** を入力し、 **[サインイン]** を選択します。  
   ![](media/service-connect-to-planview/creds.png)
6. 左側のウィンドウで、ダッシュボードの一覧から Planview Enterprise を選択します。  
     ダッシュボードに Planview Enterprise のデータがインポートされます。 データの読み込みには時間がかかる場合があります。  
    ![](media/service-connect-to-planview/dashboard.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="system-requirements"></a>システム要件
Planview Enterprise データを Power BI にインポートするには、ロールで Reporting Portal Viewer 機能が有効になっている Planview Enterprise ユーザーである必要があります。 下の追加要件を参照してください。

この手順では、Power BI アカウントを使用して Microsoft Power BI のホーム ページに既にサインインしているものとします。 Power BI アカウントがない場合は、[powerbi.com](https://powerbi.microsoft.com/get-started/) にアクセスし、 **[Power BI - クラウド コラボレーションと共有]** の下の **[無料で試す]** を選択します。 その後、 **[データを取得]** をクリックします。

## <a name="next-steps"></a>次の手順:

[Power BI とは?](power-bi-overview.md)

[Power BI のデータの取得](service-get-data.md)