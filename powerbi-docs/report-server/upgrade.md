---
title: Power BI Report Server のアップグレード
description: Power BI Report Server のアップグレード方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.custom: ''
ms.date: 09/05/2017
ms.openlocfilehash: cb2a5ede49acb218450174bbf77388be5c504617
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861730"
---
# <a name="upgrade-power-bi-report-server"></a>Power BI Report Server のアップグレード

Power BI Report Server のアップグレード方法について説明します。

 **ダウンロード** ![ダウンロード](media/upgrade/download.png "download")

Power BI Report Server および Power BI Report Server 向けに最適化された Power BI Desktop をダウンロードするには、「[Power BI Report Server によるオンプレミスでのレポート作成](https://powerbi.microsoft.com/report-server/)」を参照してください。

## <a name="before-you-begin"></a>開始する前に

レポート サーバーをアップグレードする前に、レポート サーバーをバックアップする次の手順を実行することをお勧めします。

### <a name="backing-up-the-encryption-keys"></a>暗号化キーのバックアップ

暗号化キーは、レポート サーバーのインストールの初回構成時に、バックアップする必要があります。 また、サービス アカウントの ID を変更したり、コンピューター名を変更したりするたびに、キーはバックアップする必要があります。 詳細については、「 [Back Up and Restore Reporting Services Encryption Keys](/sql/reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys)」を参照してください。

### <a name="backing-up-the-report-server-databases"></a>レポート サーバー データベースのバックアップ

レポート サーバーはステートレス サーバーであるため、すべてのアプリケーション データは、SQL Server データベース エンジンのインスタンスで実行される **reportserver** と **reportservertempdb** データベースに格納されます。 **reportserver** と **reportservertempdb** データベースは、SQL Server データベースをバックアップするサポート対象のいずれかの方法を使用して、バックアップすることができます。 レポート サーバー データベースについては、次のような推奨事項があります。

* **reportserver** データベースをバックアップするには、完全復旧モデルを使用します。
* **reportservertempdb** データベースをバックアップするには、単純復旧モデルを使用します。
* 各データベースに対して異なるバックアップ スケジュールを設定できます。 **reportservertempdb** をバックアップする唯一の理由は、ハードウェア障害が発生した場合にこのデータベースの再作成を回避することです。 ハードウェア障害が発生した場合、 **reportservertempdb**のデータを復旧する必要はありませんが、テーブル構造については復旧が必要になります。 **reportservertempdb**が失われた場合、レポート サーバー データベースの再作成以外にこのデータベースを復元する方法はありません。 **reportservertempdb**を再作成する場合、プライマリ レポート サーバー データベースと同じ名前を使用することが重要です。

SQL Server リレーショナル データベースのバックアップと復旧の詳細については、「[SQL Server データベースのバックアップと復元](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)」を参照してください。

### <a name="backing-up-the-configuration-files"></a>構成ファイルのバックアップ

Power BI Report Server は、アプリケーション設定の格納に構成ファイルを使用します。 初めてサーバーを構成するときおよびカスタム拡張機能を配置した後は常に、ファイルをバックアップする必要があります。 バックアップするのは次のファイルです。

* config.json
* RSHostingService.exe.config
* RSReportServer.config
* Rssvrpolicy.config
* Reportingservicesservice.exe.config
* レポート サーバーの ASP.NET アプリケーション用の Web.config
* ASP.NET 用の Machine.config

## <a name="upgrade-the-report-server"></a>レポート サーバーのアップグレード

Power BI Report Server のアップグレードは簡単です。 わずかな手順でファイルをインストールできます。

1. PowerBIReportServer.exe の場所を検索し、インストーラーを起動します。

2. **[Power BI Report Server をアップグレードする]** を選択します。

    ![Power BI Report Server のアップグレード](media/upgrade/reportserver-upgrade1.png "Power BI Report Server のアップグレード")

3. ライセンス条件を読んで同意し、**[アップグレード]** を選択します。

    ![使用許諾契約書](media/upgrade/reportserver-upgrade-eula.png "使用許諾契約書")

4. 正常にアップグレードした後で、**[レポート サーバーの構成]** を選択し、Reporting Services 構成マネージャーを起動するか、**[閉じる]** を選択してインストーラーを終了します。

    ![アップグレードの構成](media/upgrade/reportserver-upgrade-configure.png)

## <a name="upgrade-power-bi-desktop"></a>Power BI Desktop のアップグレード

レポート サーバーをアップグレードしたら、そのサーバーに一致する、Power BI Power BI Report Server に最適化された Power BI Desktop のバージョンに、すべての Power BI のレポート作成者がアップグレードしたかどうかを確認する必要があります。

## <a name="next-steps"></a>次の手順

* [管理者の概要](admin-handbook-overview.md)  
* [Power BI レポート サーバー向けに最適化された Power BI Desktop のインストール](install-powerbi-desktop.md)  
* [レポート サービスのインストールを確認する](/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
* [レポート サーバー サービス アカウントを構成する](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
* [レポート サーバーの URL を構成する](/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
* [レポート サーバー データベース接続を構成する](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
* [レポート サーバーを初期化する](/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
* [レポート サーバーで SSL 接続を構成する](/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
* [Windows サービス アカウントとアクセス許可を構成する](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
* [Power BI レポート サーバーのブラウザーのサポート](browser-support.md)

その他の質問 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。