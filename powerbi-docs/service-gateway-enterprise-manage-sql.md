---
title: データ ソースの管理 - SQL
description: オンプレミス データ ゲートウェイとそのゲートウェイに属しているデータ ソースを管理する方法。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2c21792f97445b336709038f7ec2ec39d041312b
ms.sourcegitcommit: 73228d0a9038b8369369c059ad06168d2c5ff062
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2019
ms.locfileid: "68730050"
---
# <a name="manage-your-data-source---sql-server"></a>データ ソースの管理 - SQL Server

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

[オンプレミス データ ゲートウェイをインストール](/data-integration/gateway/service-gateway-install)したら、ゲートウェイで使用できる[データ ソースを追加する](service-gateway-data-sources.md#add-a-data-source)ことができます。 この記事では、スケジュールされた更新または DirectQuery に使用されるゲートウェイと SQL Server データ ソースの操作方法について説明します。

## <a name="add-a-data-source"></a>データ ソースの追加

データ ソースを追加する方法の詳細については、「[Add a data source](service-gateway-data-sources.md#add-a-data-source)」(データソースの追加) を参照してください。

![SQL Server データ ソースの選択](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> DirectQuery を使用する場合、ゲートウェイは **SQL Server 2012 SP1** と後続のバージョンのみに対応しています。

次に、 **[サーバー]** や **[データベース]** など、データ ソースの情報を入力する必要があります。  

また、 **[認証方法]** も選択する必要があります。 **[Windows]** または **[基本]** を選択できます。 Windows 認証ではなく SQL 認証を使用する場合は、 **[基本]** を選択してください。 次に、このデータ ソースで使用される資格情報を入力します。

> [!NOTE]
> データ ソースへのすべてのクエリは、Kerberos シングル サインオン (SSO) が構成され、データ ソースに対して有効な場合を除き、これらの資格情報を使用して実行されます。 SSO を使用すると、インポート データセットは保存された資格情報を使用しますが、DirectQuery データセットは現在の Power BI ユーザーを使用し、SSO を使用してクエリを実行します。 資格情報の格納方法の詳細については、「[暗号化された資格情報をクラウドに保存する](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud)」、または、[Power BI からオンプレミスのデータ ソースへの SSO (シングル サインオン) に Kerberos を使用する](service-gateway-sso-kerberos.md)方法を説明する記事を参照してください。

![データ ソース設定の入力](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

すべての情報を入力したら、 **[追加]** を選択します。 このデータ ソースは、オンプレミスの SQL Server サーバーに対するスケジュールされた更新または DirectQuery に使用できるようになりました。 成功すると、"*接続成功*" というメッセージが表示されます。

![接続の状態の表示](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>詳細設定

必要に応じて、データ ソースのプライバシー レベルを構成できます。 これにより、データを結合できる方法を制御します。 これは、スケジュールされた更新にのみ使用します。 DirectQuery には適用されません。 データ ソースのプライバシー レベルの詳細については、「[プライバシーレベル (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)」を参照してください。

![プライバシー レベルの設定](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="using-the-data-source"></a>データ ソースの使用

データ ソースを作成した後、DirectQuery 接続かスケジュールされた更新のいずれかによって使用できるようになります。

> [!NOTE]
> Power BI Desktop とオンプレミス データ ゲートウェイ内のデータ ソースとの間で、サーバーとデータベース名が一致している必要があります。

データセットとゲートウェイ内のデータ ソース間のリンクは、サーバー名とデータベース名に基づいています。 このため、これらは一致している必要があります。 たとえば、**Power BI Desktop** 内でサーバー名の IP アドレスを指定する場合は、ゲートウェイ構成内のデータ ソースでもその IP アドレスを使用する必要があります。 Power BI Desktop で *SERVER\INSTANCE* を使用する場合は、ゲートウェイ用に構成されているデータ ソース内でも同じものを使用する必要があります。

これは、DirectQuery とスケジュールされた更新のどちらにも該当します。

### <a name="using-the-data-source-with-directquery-connections"></a>DirectQuery 接続でデータ ソースを使用する

**Power BI Desktop** とゲートウェイ用に構成されているデータ ソースとの間では、サーバーとデータベース名が一致している必要があります。 また、DirectQuery のデータセットを公開するには、自分のアカウントがデータ ソースの **[ユーザー]** タブの一覧に表示されている必要があります。 DirectQuery の選択は、最初にデータをインポートする Power BI Desktop 内で発生します。 Directquery の使用方法の詳細については、「[Use DirectQuery in Power BI Desktop](desktop-use-directquery.md)」(Power BI Desktop で DirectQuery を使用する) を参照してください。

公開した後は、Power BI Desktop か **[データの取得]** のいずれかから、レポート機能が利用可能になります。 ゲートウェイ内にデータ ソースを作成してから、接続が使用できるようになるまでには、数分ほどかかることがあります。

### <a name="using-the-data-source-with-scheduled-refresh"></a>スケジュールされた更新でデータ ソースを使用する

ゲートウェイ内に構成されているデータ ソースの **[ユーザー]** タブの一覧に自分のアカウントが表示されていて、さらにサーバーとデータベース名が一致している場合は、スケジュールされた更新で使用するオプションとして、ゲートウェイが表示されます。

![ユーザーの表示](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>次の手順

* [SQL Server でオンプレミス データに接続する](service-gateway-sql-tutorial.md)
* [オンプレミス データ ゲートウェイのトラブルシューティング](/data-integration/gateway/service-gateway-tshoot)
* [ゲートウェイのトラブルシューティング - Power BI](service-gateway-onprem-tshoot.md)
* [Power BI からオンプレミス データ ソースへの SSO (シングル サインオン) に Kerberos を使用する](service-gateway-sso-kerberos.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

