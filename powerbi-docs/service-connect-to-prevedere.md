---
title: Power BI で Prevedere に接続する
description: Power BI 用 Prevedere
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 8abf93b30b976aea1d0164238d173abe1be260e8
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185364"
---
# <a name="connect-to-prevedere-with-power-bi"></a>Power BI で Prevedere に接続する
独占的で重要な財務情報にアクセスし、ビジネスを確実かつ積極的に推進します。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Power BI 用 [Prevedere コンテンツ パック](https://app.powerbi.com/getdata/services/prevedere)に接続します。

>[!NOTE]
>まだ Prevedere ユーザーでない場合は、[サンプル キー](https://prevederepowerbiconnector.azurewebsites.net/static/learnmore.html)を使って試してください。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
   ![](media/service-connect-to-prevedere/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
   ![](media/service-connect-to-prevedere/services.png)
3. **[Prevedere]** を選択し、 **[取得]** を選択します。
   
   ![](media/service-connect-to-prevedere/connect.png)
4. **[認証方法]** として **[キー]** を選択し、Prevedere API キーを入力します。
   
    ![](media/service-connect-to-prevedere/creds.png)
5. **[サインイン]** を選択して、インポート プロセスを開始します。 完了すると、ナビゲーション ウィンドウに、新しいダッシュ ボード、レポート、モデルが表示されます。 インポートされたデータを表示するダッシュボードを選択します。
   
     ![](media/service-connect-to-prevedere/dashboard.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="whats-included"></a>含まれるもの
コンテンツ パックは、小売予測、予測モデル、主要指標などの情報を取得します。

## <a name="system-requirements"></a>システム要件
このコンテンツ パックは、Prevedere API キーまたはサンプル キー (下記参照) へのアクセスが必要です。

## <a name="finding-parameters"></a>パラメーターの見つけ方
<a name="FindingParams"></a>

既存の顧客は、API キーを使用してデータにアクセスできます。 まだ顧客になっていない場合は、[サンプル キー](https://prevederepowerbiconnector.azurewebsites.net/static/learnmore.html)を使ってサンプル データを表示、分析できます。

## <a name="troubleshooting"></a>トラブルシューティング
インスタンスのサイズによっては、データの読み込みに時間がかかる場合があります。

## <a name="next-steps"></a>次の手順
[Power BI の概要](service-get-started.md)

[Power BI でデータを取得する](service-get-data.md)

