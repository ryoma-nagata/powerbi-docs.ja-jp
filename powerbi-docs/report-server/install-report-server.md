---
title: Power BI レポート サーバーのインストール
description: Power BI レポート サーバーのインストール方法について説明します。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/26/2019
ms.openlocfilehash: 7297e73dc0e412f75412eb48398ef9c85cda8d6e
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "74565773"
---
# <a name="install-power-bi-report-server"></a>Power BI Report Server のインストール

Power BI レポート サーバーのインストール方法について説明します。

## <a name="download-power-bi-report-server"></a>Power BI Report Server のダウンロード

「[Power BI Report Server によるオンプレミスでのレポート作成](https://powerbi.microsoft.com/report-server/)」ページで **[無料試用版をダウンロードする]** を選択します。

PowerBIReportServer.exe ファイルを実行するときは、無料試用版を選択するか、ご自分のプロダクト キーを入力します。 詳細をお読みください。

## <a name="before-you-install"></a>インストールする前に

Power BI Report Server をインストールする前に、「[Power BI レポート サーバーをインストールするためのハードウェアとソフトウェアの要件](system-requirements.md)」を確認することをお勧めします。

 > [!IMPORTANT]
 > Power BI Report Server は、読み取り専用ドメイン コントローラー (RODC) がある環境にインストールできます。ただし、Power BI Report Server が正常に機能するためには、読み取り/書き込みドメイン コントローラーにアクセスできることが必要です。 Power BI Report Server が RODC にしかアクセスできない場合は、サービスを管理しようとしたときにエラーが発生する可能性があります。

### <a name="power-bi-report-server-product-key"></a>Power BI Report Server のプロダクト キー

Power BI Report Server のプロダクト キーは、次の 2 つの異なるソースから取得できます。

- Power BI Premium
- SQL Server Enterprise Software Assurance (SA)

詳細をお読みください。

#### <a name="power-bi-premium"></a>Power BI Premium

Power BI Premium を購入した場合は、Power BI 管理者ポータルの **[Premium 設定]** タブ内で、Power BI Report Server のプロダクト キーにアクセスできます。 管理ポータルを利用できるのは、グローバル管理者、または Power BI サービス管理者ロールが割り当てられているユーザーに限られます。

![Premium の設定](../report-server/media/install-report-server/pbirs-product-key.png "Premium 設定の Power BI Report Server キー")

**[Power BI Report Server キー]** を選択すると、プロダクト キーを含むダイアログが表示されます。 これをコピーして、インストールで使用することができます。

![プロダクト キー](../report-server/media/install-report-server/pbirs-product-key-dialog.png "Power BI Report Server のプロダクト キー")

#### <a name="sql-server-enterprise-software-assurance-sa"></a>SQL Server Enterprise Software Assurance (SA)

SQL Server Enterprise SA 契約がある場合は、[ボリューム ライセンス サービス センター](https://www.microsoft.com/Licensing/servicecenter/)からプロダクト キーを取得できます。

## <a name="install-your-report-server"></a>レポート サーバーのインストール

Power BI Report Server のインストールは簡単です。 ファイルのインストールはわずかな手順だけです。

インストール時に SQL Server データベース エンジン サーバーが使用可能になっている必要はありません。 インストール後に Reporting Services を構成する必要があります。

1. PowerBIReportServer.exe の場所を検索し、インストーラーを起動します。

2. **[Install Power BI Report Server]** \(Power BI レポート サーバーのインストール\) を選択します。

    ![Power BI Report Server のインストール](media/install-report-server/pbireportserver-install.png)
3. インストールするエディションを選択し、 **[次へ]** を選択します。

    ![エディションを選択する](media/install-report-server/pbireportserver-choose-edition.png)

    評価エディションまたは開発者エディションのいずれかを選択できます。

    ![エディション 2](media/install-report-server/pbireportserver-choose-edition2.png)

    それ以外の場合、Power BI サービスまたはボリューム ライセンス サービス センターから取得したプロダクト キーを入力します。 プロダクト キーを取得する方法の詳細については、前述の「[インストールする前に](#before-you-install)」セクションを参照してください。
4. ライセンス条件を読んで同意してから、 **[次へ]** を選択します。

    ![ライセンス条項](media/install-report-server/pbireportserver-eula.png)
5. レポート サーバー データベースを格納するためのデータベース エンジンを使用できる必要があります。 **[次へ]** を選択し、レポート サーバーのみをインストールします。

    ![ファイルのみをインストールする](media/install-report-server/pbireportserver-install-files-only.png)
6. レポート サーバーのインストール場所を指定します。 **[インストール]** を選択して続行します。

    ![インストール先のパスを指定する](media/install-report-server/pbireportserver-install-file-path.png)

    既定のパスは、C:\Program Files\Microsoft Power BI Report Server です。

7. 正常にセットアップした後で、 **[Configure Report Server]** \(レポート サーバーの構成\) を選択し、Reporting Services 構成マネージャーを起動します。

    ![レポート サーバーを構成する](media/install-report-server/pbireportserver-configure.png)

## <a name="configure-your-report-server"></a>自分のレポート サーバーを構成する

セットアップで **[レポート サーバーの構成]** を選択すると、Reporting Services Configuration Manager が表示されます。 詳細については、「[Reporting Services Configuration Manager](https://docs.microsoft.com/sql/reporting-services/install-windows/reporting-services-configuration-manager-native-mode)」(Reporting Services 構成マネージャー) を参照してください。

Reporting Services の初期構成を完了するには、[レポート サーバー データベースを作成](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-report-server-create-a-report-server-database)します。 この手順を完了するには、SQL Server データベース サーバーが必要です。

### <a name="creating-a-database-on-a-different-server"></a>別のサーバーでデータベースを作成する

別のコンピューター上のデータベース サーバーでレポート サーバー データベースを作成する場合は、レポート サーバーのサービス アカウントをデータベース サーバー上で認識される資格情報に変更します。 

既定では、レポート サーバーは、仮想サービス アカウントを使用します。 別のサーバーにデータベースを作成しようとすると、接続の権限の適用手順で次のエラーが発生することがあります。

`System.Data.SqlClient.SqlException (0x80131904): Windows NT user or group '(null)' not found. Check the name again.`

エラーを回避するために、ネットワーク サービスまたはドメイン アカウントのいずれかにサービス アカウントを変更できます。 ネットワーク サービスにサービス アカウントを変更すると、レポート サーバーのコンピューター アカウントのコンテキストで権限が適用されます。

![レポート サーバー サービス アカウントを構成する](media/install-report-server/pbireportserver-configure-account.png)

詳細については、「[Configure the report server service account](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)」 (レポート サーバー サービス アカウントを構成する) を参照してください。

## <a name="windows-service"></a>Windows サービス

Windows サービスは、インストールの一部として作成されます。 **Power BI レポート サーバー**として表示されます。 サービス名は **PowerBIReportServer** です。

![レポート サーバー Windows サービス](media/install-report-server/pbireportserver-windows-service.png)

![レポート サーバー Windows サービスのプロパティ](media/install-report-server/pbireportserver-windows-service2.png)

## <a name="default-url-reservations"></a>既定の URL 予約

URL 予約は、プレフィックス、ホスト名、ポート、および仮想ディレクトリから構成されます。

| パーツ | 説明 |
| --- | --- |
| プレフィックス |既定のプレフィックスは HTTP です。 以前に Secure Sockets Layer (SSL) 証明書をインストールした場合、セットアップは、HTTPS プレフィックスを使用して URL 予約を作成しようとします。 |
| ホスト名 |既定のホスト名は、厳密なワイルドカード (+) です。 レポート サーバーが `https://<computername>/reportserver`、`https://localhost/reportserver`、`https://<IPAddress>/reportserver.` を含むコンピューターに解決されるすべてのホスト名に対して指定されたポート上ですべての HTTP 要求を受け入れることを指定します。 |
| ポート |既定のポートは 80 です。 ポート 80 以外のポートを使用する場合は、ブラウザー ウィンドウで Web ポータルを開くときに、それを URL に明示的に追加する必要があります。 |
| 仮想ディレクトリ |既定では、仮想ディレクトリは、レポート サーバー Web サービス用に ReportServer の形式で、Web ポータル用に Reports の形式で作成されます。 レポート サーバー Web サービスの場合、既定の仮想ディレクトリは **reportserver** です。 Web ポータルの場合、既定の仮想ディレクトリは **reports** です。 |

完全な URL 文字列の例は次のようになることがあります。

* `https://+:80/reportserver`、レポート サーバーへのアクセスを提供します。
* `https://+:80/reports`、Web ポータルへのアクセスを提供します。

## <a name="firewall"></a>ファイアウォール

リモート コンピューターからレポート サーバーにアクセスする場合、ファイアウォールがある場合は、ファイアウォール規則を構成したことを確認します。

Web サービスの URL と Web ポータルの URL 用に構成した TCP ポートを開きます。 既定では、TCP ポート 80 に対して構成されます。

## <a name="additional-configuration"></a>追加の構成

* Power BI サービスとの統合を構成し、Power BI ダッシュボードにレポート アイテムを固定できるようにするには、「[Integrate with the Power BI service](https://docs.microsoft.com/sql/reporting-services/install-windows/power-bi-report-server-integration-configuration-manager) 」(Power BI サービスとの統合) を参照してください。
* サブスクリプションの処理用の電子メールを構成するには、「[E-Mail settings](https://docs.microsoft.com/sql/reporting-services/install-windows/e-mail-settings-reporting-services-native-mode-configuration-manager)」 (電子メール設定) および「[E-Mail Delivery in Reporting Services](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)」 (レポート サービスの電子メールの配信) を参照してください。
* レポート コンピューターで Web ポータルにアクセスしてレポートを表示および管理できるように Web ポータルを構成するには、「[Configure a firewall for report server access](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-firewall-for-report-server-access)」 (レポート サーバーにアクセスするためのファイアウォールを構成する) と「[Configure a Report Server for Remote Administration](https://docs.microsoft.com/sql/reporting-services/report-server/configure-a-report-server-for-remote-administration)」 (リモート管理用にレポート サーバーを構成する) を参照してください。

## <a name="next-steps"></a>次の手順

[管理者の概要](admin-handbook-overview.md)  
[レポート サーバーのプロダクト キーを検索する方法](find-product-key.md)  
[Power BI レポート サーバー向けに最適化された Power BI Desktop のインストール](install-powerbi-desktop.md)  
[レポート サービスのインストールを確認する](https://docs.microsoft.com/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
[レポート サーバー サービス アカウントを構成する](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
[レポート サーバーの URL を構成する](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
[レポート サーバー データベース接続を構成する](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
[レポート サーバーを初期化する](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
[レポート サーバーで SSL 接続を構成する](https://docs.microsoft.com/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
[Windows サービス アカウントとアクセス許可を構成する](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
[Power BI レポート サーバーのブラウザーのサポート](browser-support.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。