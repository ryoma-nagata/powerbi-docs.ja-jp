---
title: Power BI で Application Insights に接続する
description: Power BI 用 Application Insights
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 3a41b237ccc4e249d85385b54860f60460efbb31
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70186133"
---
# <a name="connect-to-application-insights-with-power-bi"></a>Power BI で Application Insights に接続する
Power BI を使用して、[Application Insights](/azure/application-insights/app-insights-overview/) テレメトリから強力なカスタム ダッシュボードを作成できます。 新しい方法でアプリのテレメトリを視覚化します。 複数のアプリまたはコンポーネント サービスからのメトリックを単一のダッシュボードに統合します。 この Application Insights 用 Power BI コンテンツ パックの最初のリリースには、アクティブなユーザー、ページ ビュー、セッション、ブラウザーと OS のバージョン、マップ内でのユーザーの地理的分布など、一般的な使用関連メトリックのためのウィジェットが含まれています。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Power BI 用 Application Insights コンテンツ パック](https://app.powerbi.com/getdata/services/application-insights)に接続します。

>[!NOTE]
>この統合方法は現在、**非推奨**です。 Application Insights から Power BI への推奨される接続方法の詳細については、[Analytic クエリのエクスポート機能](https://docs.microsoft.com/azure/application-insights/app-insights-export-power-bi#export-analytics-queries)に関するページを参照してください。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
    ![[データの取得] ボタン](media/service-connect-to-application-insights/pbi_getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
    ![[サービスの取得] ボタン](media/service-connect-to-application-insights/pbi_getservices.png)
3. **[Application Insights]**  >  **[取得]** の順に選択します。
   
    ![Application Insights コンテンツ パック](media/service-connect-to-application-insights/appinsights.png)
4. **[Application Insights リソース名]** 、 **[リソース グループ]** 、 **[サブスクリプション ID]** など、接続するアプリケーションの詳細を入力します。 詳細については、後の「[Application Insights のパラメーター](#FindingAppInsightsParams)」を参照してください。
   
    ![Application Insights 接続ダイアログ ボックス](media/service-connect-to-application-insights/pbi_contpkappinsitconnectndialog.png)    
5. **[サイン イン]** を選択し、画面の指示に従って接続します。
   
    ![Application Insights 接続サインイン](media/service-connect-to-application-insights/pbi_contpkappinsitconnectn2.png)
6. インポート処理が自動的に開始します。 完了すると、通知が表示され、ナビゲーション ウィンドウにアスタリスク付きで新しいダッシュボード、レポート、データセットが表示されます。  インポートされたデータを表示するダッシュボードを選択します。
   
    ![Application Insights ダッシュボード](media/service-connect-to-application-insights/pbi_contpkappinsitdash.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="whats-included"></a>含まれるもの
Application Insights コンテンツ パックには、次のテーブルとメトリックが含まれています。  

    ´´´
    - ApplicationDetails  
    - UniqueUsersLast7Days   
    - UniqueUsersLast30Days   
    - UniqueUsersDailyLast30Days  
    - UniqueUsersByCountryLast7Days  
    - UniqueUsersByCountryLast30Days   
    - PageViewsDailyLast30Days   
    - SessionsLast7Days   
    - SessionsLast30Days  
    - PageViewsByBrowserVersionDailyLast30Days   
    - UniqueUsersByOperatingSystemLast7Days   
    - UniqueUsersByOperatingSystemLast30Days    
    - SessionsDailyLast30Days   
    - SessionsByCountryLast7Days   
    - SessionsByCountryLast30Days   
    - PageViewsByCountryDailyLast30Days  
    ´´´ 

<a name="FindingAppInsightsParams"></a>

## <a name="finding-parameters"></a>パラメーターの見つけ方
リソース名、リソース グループ、サブスクリプション ID はすべて Azure Portal でわかります。 名前を選択すると、詳細ビューが開き、[要点] ドロップダウンを使用して必要なすべての値を知ることができます。

![Application Insights パラメーター](media/service-connect-to-application-insights/pbi_contpkappinsitparams.png)

これらの値をコピーして、Power BI に対するフィールドに貼り付けます。

![Application Insights パラメーター](media/service-connect-to-application-insights/pbi_contpkappinsitparam2.png)

## <a name="next-steps"></a>次の手順
[Power BI の概要](service-get-started.md)

[Power BI でデータを取得する](service-get-data.md)

