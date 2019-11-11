---
title: Power BI の DirectQuery でサポートされるデータ ソース
description: DirectQuery を使用できるデータ ソースの一覧を取得します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/16/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 4c2e2904790d69e5df388d34b5a737f1890d7e12
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878278"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Power BI の DirectQuery でサポートされるデータ ソース

**Power BI Desktop** と **Power BI サービス**には、接続してデータへのアクセスを可能にする多数のデータ ソースがあります。 この記事では、Power BI のどのデータ ソースが **DirectQuery** と呼ばれる接続方法をサポートしているかを説明します。 DirectQuery の詳細については、「[**Power BI での DirectQuery**](desktop-directquery-about.md)」を参照してください。

次のデータ ソースは、Power BI で DirectQuery をサポートしています。

* Amazon Redshift
* AtScale (ベータ)
* Azure Data Explorer
* Azure HDInsight Spark
* [Azure SQL Database](service-azure-sql-database-with-direct-connect.md)
* [Azure SQL Data Warehouse](service-azure-sql-data-warehouse-with-direct-connect.md)
* Denodo
* Google BigQuery
* HDInsight 対話型クエリ
* IBM DB2 (Microsoft プロバイダー)
* IBM Netezza
* Impala (バージョン 2.x)
* MarkLogic
* Oracle データベース (バージョン 12 以降)
* Oracle Essbase
* PostgreSQL
* SAP Business Warehouse Application サーバー
* SAP Business Warehouse メッセージ サーバー
* SAP HANA
* Snowflake
* Spark (バージョン 0.9 以降)
* SQL Server
* Teradata
* Vertica

名前の後に **(ベータ)** または **(プレビュー)** と書かれているデータ ソースは、変更される可能性があり、運用環境での使用はサポートされていません。 **Power BI サービス**にレポートを発行した後はサポートされない可能性もあるので、発行されたレポートを開いたり、データセットを探したりした場合にエラーが発生することがあります。

**(ベータ)** と **(プレビュー)** のデータ ソースの唯一の違いは、使用可能になる前に、 **(プレビュー)** のソースはプレビュー機能として有効にする必要があるという点です。 **(プレビュー)** データ コネクタを有効にするには、**Power BI Desktop** で **[ファイル]、[オプションと設定]、** の順に進み、 **[プレビュー機能]** を選択します。

> [!NOTE]
> SQL Server への DirectQuery クエリでは、アクセスを確立するために、現在の Windows 認証資格情報またはデータベース資格情報を使って認証を行うが必要があります。 代替資格情報はサポートされていません。
>

## <a name="on-premises-gateway-requirements"></a>オンプレミス ゲートウェイの要件
次の表では、**Power BI サービス**にレポートを発行した後に、指定したデータ ソースに接続するために、**オンプレミス データ ゲートウェイ**が必要かを示します。

| Source | ゲートウェイが必要 |
| --- | --- |
| Amazon Redshift |いいえ |
| Azure HDInsight Spark (Beta) |いいえ |
| Azure SQL Database |いいえ |
| Azure SQL Data Warehouse |いいえ |
| Google BigQuery |いいえ |
| IBM Netezza |はい |
| IBM DB2 (IBM プロバイダー) |はい |
| IBM DB2 (Microsoft プロバイダー) |いいえ |
| IBM Informix データベース |いいえ |
| Impala (バージョン 2.x) |はい |
| MySQL |はい |
| ODBC |はい |
| Oracle データベース |はい |
| PostgreSQL |はい |
| SAP Business Warehouse Application サーバー |はい |
| SAP Business Warehouse メッセージ サーバー |はい |
| SAP HANA |はい |
| Snowflake |はい |
| Spark (ベータ) バージョン 0.9 以降 |はい |
| SQL Server |はい |
| Sybase |はい |
| Teradata |はい |
| Vertica |はい |


## <a name="single-sign-on-sso-for-directquery-sources"></a>DirectQuery ソースのシングル サインオン (SSO)

SSO オプションが有効になっている場合、データ ソースを基に作成されたレポートにユーザーがアクセスすると、Power BI によって基になるデータ ソースへのクエリで、認証済みの Azure AD 資格情報が送信されます。 これにより、Power BI はデータ ソース レベルで構成されているセキュリティ設定を適用できます。

SSO オプションは、このデータ ソースを使うすべてのデータセットで有効になります。 インポートのシナリオに使われる認証方法には影響しません。 次のデータ ソースでは、DirectQuery 経由の接続で SSO をサポートします。

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- SAP BW Message Server (プレビュー)
- Spark
- SQL Server
- Teradata

> [!Note]
> Azure Multi-Factor Authentication (MFA) はサポートされていません。 DirectQuery で SSO を使用する必要があるユーザーは、MFA から除外する必要があります。

## <a name="next-steps"></a>次の手順
DirectQuery の詳細については、次のリソースを参照してください。

* [Power BI の DirectQuery](desktop-directquery-about.md)
* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery と SAP BW](desktop-directquery-sap-bw.md)
* [オンプレミス データ ゲートウェイ](service-gateway-onprem.md)

