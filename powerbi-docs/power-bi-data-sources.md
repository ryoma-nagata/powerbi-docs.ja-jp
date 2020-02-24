---
title: Power BI データ ソース
description: この記事では、Power BI でサポートされているデータ ソースをリストアップします。DirectQuery やオンプレミス データ ゲートウェイに関する情報などです。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: kfollis
ms.openlocfilehash: 261d800dac9b65747e648bc76944a0b8a5077b73
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427095"
---
# <a name="power-bi-data-sources"></a>Power BI データ ソース

この表には、DirectQuery やオンプレミス データ ゲートウェイに関する情報など、データセットに対して Power BI でサポートされているデータ ソースがまとめられています。 データフローの詳細については、「[Power BI データフロー用のデータ リソースに接続する](service-dataflows-data-sources.md)」を参照してください。

> [!NOTE]
> Power BI Desktop 用のデータ コネクタの多くには、認証に Internet Explorer 10 (またはそれ以降) が必要です。 


| データ ソースの | デスクトップから接続する | サービスから接続し、更新する | DirectQuery / ライブ接続 | ゲートウェイ (サポートあり) | ゲートウェイ (必須) |
|---|---|---|---|---|---|---|---|
| Access データベース | はい | はい | いいえ | はい <sup>1</sup> | はい |
| Active Directory | はい | はい | いいえ | はい | はい |
| Adobe Analytics | はい | はい | いいえ | いいえ | いいえ |
| Amazon Redshift | はい | はい | はい | はい | いいえ |
| appFigures | はい | はい | いいえ | いいえ | いいえ |
| AtScale キューブ | はい | はい | はい | はい | いいえ |
| Azure Analysis Services | はい | はい | はい | はい <sup>2</sup> | いいえ |
| Azure Blob Storage | はい | はい | いいえ | はい | いいえ |
| Azure Cosmos DB | はい | はい | いいえ | いいえ | いいえ |
| Azure Cost Management | はい | はい | いいえ | いいえ | いいえ |
| Azure Data Explorer (Kusto) | はい | はい | はい | いいえ | いいえ |
| Azure Data Lake Storage Gen1 | はい | はい | いいえ | いいえ | いいえ |
| Azure Data Lake Storage Gen2 | はい | はい | いいえ | はい | いいえ |
| Azure DevOps | はい | はい | いいえ | いいえ | いいえ |
| Azure DevOps Server | はい | はい | いいえ | はい | はい |
| Azure HDInsight (HDFS) | はい | はい | いいえ | いいえ | いいえ |
| Azure HDInsight Spark | はい | はい | はい | いいえ | いいえ |
| Azure SQL Database | はい | はい | はい | はい <sup>2</sup> | いいえ |
| Azure SQL Data Warehouse | はい | はい | はい | いいえ | いいえ |
| Azure Table Storage | はい | はい | いいえ | はい | いいえ |
| BI コネクタ | はい | はい | はい | はい | はい |
| BI360 - Budgeting & Financial Reporting | はい | はい | いいえ | いいえ | いいえ |
| Common Data Service | はい | はい | いいえ | いいえ | いいえ |
| Data.World - データセットの取得 | はい | はい | いいえ | いいえ | いいえ |
| Denodo | はい | はい | はい | はい | はい |
| Dremio | はい | はい | はい | はい | はい |
| Dynamics 365 (オンライン) | はい | はい | いいえ | いいえ | いいえ |
| Dynamics 365 Business Central | はい | はい | いいえ | いいえ | いいえ |
| Dynamics 365 Business Central (オンプレミス) | はい | はい | いいえ | いいえ | いいえ |
| Dynamics 365 Customer Insights | はい | はい | いいえ | いいえ | いいえ |
| Dynamics NAV | はい | はい | いいえ | いいえ | いいえ |
| Emigo Data Source | はい | はい | いいえ | いいえ | いいえ |
| Entersoft Business Suite | はい | はい | いいえ | いいえ | いいえ |
| Essbase | はい | はい | はい | はい | はい |
| Exasol | はい | はい | はい | はい | はい |
| Excel | はい <sup>3</sup> | はい <sup>3</sup> | いいえ | はい <sup>3</sup> | いいえ <sup>4</sup> |
| Facebook | はい | はい | いいえ | いいえ | いいえ |
| ファイル | はい | はい | いいえ | はい | はい |
| フォルダー | はい | はい | いいえ | はい | はい |
| GitHub | はい | はい | いいえ | いいえ | いいえ |
| Google Analytics | はい | はい | いいえ | いいえ | いいえ |
| Google BigQuery | はい | はい | いいえ | いいえ | いいえ |
| Hadoop ファイル (HDFS) | はい | いいえ | いいえ | いいえ | いいえ |
| HDInsight 対話型クエリ | はい | はい | はい | いいえ | いいえ |
| IBM DB2 | はい | はい | はい | はい | いいえ |
| IBM Informix データベース | はい | はい | いいえ | はい | いいえ |
| IBM Netezza | はい | はい | はい | はい | はい |
| Impala | はい | はい | はい | はい | はい |
| Indexima | はい | はい | はい | はい | はい |
| Industrial App Store | はい | はい | いいえ | いいえ | いいえ |
| Information Grid | はい | はい | いいえ | いいえ | いいえ |
| Intersystems IRIS | はい | はい | はい | はい | はい |
| Intune データ ウェアハウス | はい | はい | いいえ | いいえ | いいえ |
| Jethro ODBC | はい | はい | はい | はい | はい |
| JSON | はい | はい | いいえ | はい** | いいえ <sup>4</sup> |
| Kyligence Enterprise | はい | はい | はい | はい | はい |
| MailChimp | はい | はい | いいえ | いいえ | いいえ |
| Marketo | はい | はい | いいえ | いいえ | いいえ |
| MarkLogic ODBC | はい | はい | はい | はい | はい |
| Microsoft Azure Consumption Insights | はい | はい | いいえ | いいえ | いいえ |
| Microsoft Exchange | はい | はい | いいえ | はい | いいえ |
| Microsoft Exchange Online | はい | はい | いいえ | いいえ | いいえ |
| Microsoft Graph Security | はい | はい | いいえ | はい | いいえ |
| Mixpanel | はい | はい | いいえ | いいえ | いいえ |
| MySQL | はい | はい | いいえ | はい | はい |
| OData | はい | はい | いいえ | はい | いいえ |
| ODBC | はい | はい | いいえ | はい | はい |
| OleDb | はい | はい | いいえ | はい | はい |
| Oracle | はい | はい | はい | はい | はい |
| Paxata | はい | はい | いいえ | はい | いいえ |
| PDF | はい | はい | いいえ | はい | いいえ <sup>4</sup> |
| Planview Enterprise One - CTM | はい | はい | いいえ | いいえ | いいえ |
| Planview Enterprise One - PRM | はい | はい | いいえ | いいえ | いいえ |
| Planview Projectplace | はい | はい | いいえ | いいえ | いいえ |
| PostgreSQL | はい | はい | はい | はい | いいえ |
| Power BI データフロー | はい | はい | いいえ | いいえ | いいえ |
| Power BI データセット | はい | はい | はい | いいえ | いいえ |
| Power Platform データフロー | はい | はい | いいえ | いいえ | いいえ |
| Python スクリプト | はい | はい <sup>5</sup> | いいえ | はい <sup>5</sup> | はい |
| QubolePresto | はい | はい | はい | はい | はい |
| Quick Base | はい | はい | いいえ | はい | はい |
| QuickBooks Online | はい | はい | いいえ | いいえ | いいえ |
| R スクリプト | はい | はい <sup>5</sup> | いいえ | はい <sup>5</sup> | いいえ |
| Roamler | はい | はい | いいえ | はい | いいえ |
| Salesforce オブジェクト | はい | はい | いいえ | いいえ | いいえ |
| Salesforce レポート | はい | はい | いいえ | いいえ | いいえ |
| SAP Business Warehouse メッセージ サーバー | はい | はい | はい | はい | はい |
| SAP Business Warehouse サーバー | はい | はい | はい | はい | はい |
| SAP HANA | はい | はい | はい | はい | はい |
| SharePoint フォルダー | はい | はい | いいえ | はい | いいえ <sup>4</sup> |
| SharePoint リスト | はい | はい | いいえ | はい | いいえ <sup>4</sup> |
| SharePoint Online リスト | はい | はい | いいえ | はい <sup>2</sup> | いいえ |
| Smartsheet | はい | はい | いいえ | いいえ | いいえ |
| Snowflake | はい | はい | はい | はい | いいえ |
| Spark | はい | はい | はい | はい | いいえ |
| SparkPost | はい | はい | いいえ | いいえ | いいえ |
| SQL Server | はい | はい | はい | はい | はい |
| SQL Server Analysis Services | はい | はい | はい | はい | はい |
| Stripe | はい | はい | いいえ | いいえ | いいえ |
| SurveyMonkey | はい | はい | いいえ | はい | いいえ |
| SweetIQ | はい | はい | いいえ | いいえ | いいえ |
| Sybase | はい | はい | いいえ | はい | はい |
| TeamDesk | はい | はい | いいえ | はい | いいえ |
| Tenforce | はい | はい | いいえ | いいえ | いいえ |
| Teradata | はい | はい | はい | はい | はい |
| テキスト/CSV | はい | はい | いいえ | はい | いいえ <sup>4</sup> |
| Twilio | はい | はい | いいえ | いいえ | いいえ |
| tyGraph | はい | はい | いいえ | いいえ | いいえ |
| Vertica | はい | はい | はい | はい | はい |
| Web | はい | はい | いいえ | はい | はい |
| Webtrends | はい | はい | いいえ | いいえ | いいえ |
| Workforce Dimensions | はい | はい | いいえ | はい | いいえ |
| XML | はい | はい | いいえ | はい | いいえ <sup>4</sup> |
| Zendesk | はい | はい | いいえ | いいえ | いいえ |
| | | | | | | | |

<sup>1</sup>[ACE OLEDB プロバイダー](https://www.microsoft.com/download/details.aspx?id=54920)でサポートされ、ゲートウェイと同じコンピューターにインストールされます。

<sup>2</sup> オンプレミス バージョンと同じ M 関数でサポートされます。

<sup>3</sup> Excel 1997-2003 ファイル (.xls) には [ACE OLEDB プロバイダー](https://www.microsoft.com/download/details.aspx?id=54920)が必要です。

<sup>4</sup> オンプレミス バージョンのテクノロジに必須です。

<sup>5</sup>[個人ゲートウェイ](service-gateway-personal-mode.md)でのみサポートされます。

## <a name="single-sign-on-sso-for-directquery-sources"></a>DirectQuery ソースのシングル サインオン (SSO)

SSO オプションが有効になっている場合、データ ソースを基に作成されたレポートにユーザーがアクセスすると、Power BI によって基になるデータ ソースへのクエリで、認証済みの Azure AD 資格情報が送信されます。 これにより、Power BI はデータ ソース レベルで構成されているセキュリティ設定を適用できます。
SSO オプションは、このデータ ソースを使うすべてのデータセットで有効になります。 インポートのシナリオに使われる認証方法には影響しません。 次のデータ ソースでは、DirectQuery 経由の接続で SSO をサポートします。

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- SAP BW Message Server
- Snowflake
- Spark
- SQL Server
- Teradata

> [!Note]
> Azure Multi-Factor Authentication (MFA) はサポートされていません。 DirectQuery で SSO を使用する必要があるユーザーは、MFA から除外する必要があります。

## <a name="next-steps"></a>次の手順

[Power BI Desktop でデータに接続する](desktop-quickstart-connect-to-data.md)  
[Power BI で DirectQuery を使用する](desktop-directquery-about.md)  
[Power BI の SQL Server Analysis Services ライブ データ](sql-server-analysis-services-tabular-data.md)  
[オンプレミス データ ゲートウェイとは](service-gateway-onprem.md)  
