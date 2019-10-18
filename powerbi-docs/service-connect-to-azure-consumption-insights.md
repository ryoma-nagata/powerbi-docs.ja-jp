---
title: Power BI で Microsoft Azure Consumption Insights に接続する
description: Power BI 用 Microsoft Azure Consumption Insights
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020435"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Power BI で Microsoft Azure Consumption Insights に接続する
Power BI コンテンツ パックを使用すると Power BI サービスで Microsoft Azure の消費データを調べて監視します。 データは、1 日 1 回自動的に更新されます。

Power BI サービス用 [Microsoft Azure Consumption Insights コンテンツ パック](https://app.powerbi.com/getdata/services/azureconsumption)に接続します。

> [!NOTE]
> よりカスタマイズされた設定については、Power BI Desktop で [Azure Consumption Insights コネクタ](desktop-connect-azure-consumption-insights.md)を使用してみてください。

## <a name="how-to-connect"></a>接続する方法
1. Power BI サービスで、左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
    ![データの取得](media/service-connect-to-azure-consumption-insights/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
   ![サービスの取得](media/service-connect-to-azure-consumption-insights/services.png)
3. **[Microsoft Azure Consumption Insights]** \> **[今すぐ入手]** の順に選択します。 
   
   ![今すぐ入手する](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. インポートするデータの月数と Azure Enterprise 登録番号を指定します。 [これらのパラメーターの見つけ方](#FindingParams)について詳しくは、後述します。
   
    ![Microsoft Azure Consumption Insights への接続](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. 接続するためのアクセス キーを指定します。 登録キーは、Azure EA Portal で見つけることができます。 
   
    ![Microsoft Azure Consumption Insights: キー](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. インポート処理が自動的に開始します。 完了すると、ナビゲーション ウィンドウに、新しいダッシュボード、レポート、モデルが表示されます。 インポートされたデータを表示するダッシュボードを選択します。
   
   ![Microsoft Azure Consumption Insights ダッシュボード](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="whats-included"></a>含まれるもの
Microsoft Azure Consumption Insights コンテンツ パックには、接続時に指定した月の範囲の月単位のレポート データが含まれています。 この範囲の期間は移動するので、データセットが更新されると、含まれる日付も更新されます。

## <a name="system-requirements"></a>システム要件
コンテンツ パックは、Azure portal 内のエンタープライズ機能にアクセスする必要があります。 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>パラメーターの見つけ方
Power BI レポートは、課金情報を閲覧できる EA ダイレクト、パートナー、インダイレクトのユーザーが利用できます。 接続フローで期待される各値の詳細については、以下を参照してください。

**月数**

* インポートするデータの現在からの月数 (1 から 36)。

**登録番号**

* Azure Enterprise の登録番号です。これは [Azure Enterprise Portal](https://ea.azure.com/) のホーム画面の **[加入契約の詳細]** で見つけることができます。
  
    ![登録番号](media/service-connect-to-azure-consumption-insights/params2.png)

**アクセス キー**

* アクセス キーは、Azure Enterprise Portal の **[利用状況のダウンロード]**  >  **[API アクセス キー]** で見つけることができます。
  
    ![アクセス キー](media/service-connect-to-azure-consumption-insights/creds2.png)

**追加のヘルプ**

* Azure Enterprise Power BI パックの設定に関する追加のヘルプについては、Azure Enterprise Portal にサインインし、 **[ヘルプ]** の API ヘルプ ファイルを参照してください。 また、その他の手順については、 **[レポート]**  ->  **[利用状況のダウンロード]**  ->  **[API アクセス キー]** で見つけることができます。
* よりカスタマイズされた設定については、Power BI Desktop で [Azure Consumption Insights コネクタ](desktop-connect-azure-consumption-insights.md)を使用してみてください。

## <a name="next-steps"></a>次の手順

Power BI Desktop の [Azure Consumption Insights コネクタ](desktop-connect-azure-consumption-insights.md)

[Power BI でデータを取得する](service-get-data.md)

