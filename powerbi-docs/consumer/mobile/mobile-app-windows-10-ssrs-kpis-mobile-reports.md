---
title: Windows 10 モバイル アプリで SSRS のモバイル レポートと KPI を表示する - Power BI
description: Windows 10 用 Power BI モバイル アプリにより、タッチ対応のモバイルからオンプレミスの重要なビジネス情報に簡単にアクセスできるようになります。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/28/2018
ms.author: mshenhav
ms.openlocfilehash: 98c76fd5903a44c8cc1ef5b175f235f1ec4382e9
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2019
ms.locfileid: "61340845"
---
# <a name="view-reporting-services-ssrs-mobile-reports-and-kpis-in-the-windows-10-power-bi-mobile-app"></a>Windows 10 の Power BI モバイル アプリで Reporting Services (SSRS) のモバイル レポートと KPI を表示する
Windows 10 用 Power BI モバイル アプリを使って、タッチ対応のモバイルから、SQL Server 2016 Reporting Services のオンプレミスの重要なビジネス情報に簡単にアクセスできます。 

![Reporting Services のモバイル レポート](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="first-things-first"></a>最初に行うこと
SQL Server 2016 Enterprise Edition Mobile Report Publisher で [Reporting Services のモバイル レポートを作成](https://msdn.microsoft.com/library/mt652547.aspx)し、[Reporting Services の Web ポータル](https://msdn.microsoft.com/library/mt637133.aspx)にそのレポートを公開します。 KPI は Web ポータルで作成します。 作成したレポートと KPI を簡単に探せるように、フォルダーで整理したりお気に入りに追加したりします。 

Windows 10 用 Power BI モバイル アプリで、フォルダーやお気に入りに追加したモバイル レポートや KPI を表示します。 

> [!NOTE]
> デバイスで Windows 10 を実行している必要があります。 このアプリは、最低 1 GB RAM と 8 GB の内部記憶域を持つデバイスに適しています。
> 
> 

## <a name="explore-samples-without-a-sql-server-2016-reporting-services-server"></a>SQL Server 2016 Reporting Services サーバーを使用せずにサンプルを参照する
Reporting Services の Web ポータルへのアクセス権がない場合でも、Reporting Services のモバイル レポートの機能を参照できます。

1. Windows 10 デバイスで Power BI アプリを開きます。
2. 左上隅にあるグローバル ナビゲーション ボタン ![グローバル ナビゲーション ボタン](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) をタップします。
3. **[設定]** アイコン ![[設定] アイコン](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png) をタップし、 **[サーバーに接続]** を右クリックするかタップして長押しした後、 **[サンプルを表示]** をタップします。
   
   ![SSRS のサンプルを表示](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-connect-ssrs-samples.png)
4. Retail Reports または Sales Reports フォルダーを開き、その KPI やモバイル レポートを調べます。
   
   ![KPI とモバイル レポートのサンプル](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-win10-ssrs-sample-kpis.png)

サンプルを参照して KPI とモバイル レポートを操作します。

## <a name="connect-to-a-reporting-services-report-server"></a>Reporting Services レポート サーバーに接続する
1. 左側のナビゲーション バーの下部にある **[設定]** ![[設定] アイコン](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png) をタップします。
2. **[サーバーに接続]** をタップします。
3. サーバーのアドレス、ユーザー名、パスワードを入力します。 サーバーのアドレスには次の形式を使用します。
   
     `http://<servername>/reports` または `https://<servername>/reports`
   
   > [!NOTE]
   > 接続文字列の先頭に、**http** または **https** を含めてください。
   > 
   > 
   
    必要に応じて、 **[詳細オプション]** をタップしてサーバーの名前を指定します。
4. チェック マークをタップして接続します。 
   
   左側のナビゲーション バーに、サーバーが表示されます。
   
   ![左側のナビゲーション バー内のサーバー](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-server.png)
   
   >[!TIP]
   >[グローバル ナビゲーション] ボタン ![[グローバル ナビゲーション] ボタン](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/powerbi_windows10_options_icon.png) をタップすると、Power BI サービスでいつでも Reporting Services のモバイル レポートとダッシュボードの間を行き来できます。 
   > 

## <a name="view-reporting-services-kpis-and-mobile-reports-in-the-power-bi-app"></a>Power BI アプリで Reporting Services の KPI とモバイル レポートを表示する
Reporting Services の KPI とモバイル レポートは、Reporting Services の Web ポータルと同じフォルダーに表示されます。

![レポート フォルダー](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-folders.png)

* [KPI] をタップすると、フォーカス モードで表示されます。
  
    ![フォーカス モードの KPI](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-kpis.png)
* モバイル レポートをタップして開き、Power BI アプリで操作します。
  
    ![Reporting Services のモバイル レポート](././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report.png)

## <a name="view-your-favorite-kpis-and-reports"></a>お気に入りの KPI とレポートを表示する
Reporting Services Web ポータルで KPI とモバイル レポートをお気に入りに設定し、Power BI のお気に入りのダッシュボードやレポートと共に、Windows 10 デバイスの便利なフォルダーで表示できます。

* **[お気に入り]** をタップします。
  
   ![[お気に入り] アイコン](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-ssrs-mobile-report-favorite-menu.png)
  
   Web ポータルでお気に入りに追加したアイテムは、すべてこのページに表示されます。
  
   ![[お気に入り] ページ](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-favorites.png)

[Power BI モバイル アプリでのお気に入り](mobile-apps-favorites.md)の詳細については、こちらをご覧ください。

## <a name="remove-a-connection-to-a-report-server"></a>レポート サーバーへの接続を削除する
Power BI モバイル アプリから一度に接続できるのは、1 つのレポート サーバーだけです。 別のサーバーに接続する場合は、現在のサーバーを切断する必要があります。

1. 左側のナビゲーション バーの下部にある **[設定]** ![[設定] アイコン](./././media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-settings-icon.png) をタップします。
2. 接続を望まないサーバー名をタップしてそのまま押さえます。
3. **[サーバーの削除]** をタップします。
   
    ![サーバーの削除](./media/mobile-app-windows-10-ssrs-kpis-mobile-reports/power-bi-windows-10-ssrs-remove-server-menu.png)

## <a name="create-reporting-services-mobile-reports-and-kpis"></a>Reporting Services のモバイル レポートと KPI を作成する
Power BI モバイル アプリでは、Reporting Services KPI とモバイル レポートを作成できません。 作成するには、SQL Server Mobile Report Publisher と SQL Server 2016 Reporting Services Web ポータルを使用します。

* [Reporting Services のモバイル レポートを作成](https://msdn.microsoft.com/library/mt652547.aspx)し、Reporting Services の Web ポータルに公開します。
* [Reporting Services の Web ポータルで KPI を作成](https://msdn.microsoft.com/library/mt683632.aspx)します

## <a name="next-steps"></a>次の手順
* [Windows 10 用の Power BI モバイル アプリの概要](mobile-windows-10-phone-app-get-started.md)  
* [Power BI とは?](../../power-bi-overview.md)  
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](http://community.powerbi.com/)。

