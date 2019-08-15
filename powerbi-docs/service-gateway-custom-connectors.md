---
title: オンプレミス データ ゲートウェイでカスタム データ コネクタを使用する
description: オンプレミス データ ゲートウェイでカスタム データ コネクタを使用できます。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 3c0ef172115dba05deb02d724b663742a2e71c13
ms.sourcegitcommit: 9665bdabce3bfc31f68dd8256b135bfd56f60589
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68832527"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>オンプレミス データ ゲートウェイでカスタム データ コネクタを使用する

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Power BI 用のデータ コネクタを使用すると、アプリケーション、サービス、またはデータ ソースからデータに接続してアクセスすることができます。 カスタム データ コネクタを開発して、Power BI Desktop で使用することができます。

Power BI 用にカスタム データ コネクタを開発する方法の詳細については、[データ コネクタ SDK に関する GitHub ページ](http://aka.ms/dataconnectors)を参照してください。 このサイトには、Power BI と Power Query の開始方法とサンプルについての情報が含まれています。

Power BI Desktop でカスタム データ コネクタを使用するレポートを作成すると、オンプレミス データ ゲートウェイを使用して Power BI サービスからこれらのレポートを更新することができます。

## <a name="enable-and-use-this-capability"></a>この機能を有効にして使用する

2018 年 7 月以降のバージョンのオンプレミス データ ゲートウェイをインストールすると、オンプレミス データ ゲートウェイ アプリに **[コネクタ]** タブが表示されます。 **[フォルダーからカスタム データ コネクタを読み込みます]** ボックスで、ゲートウェイ サービスを実行しているユーザーがアクセスできるフォルダーを選択します。 既定のユーザーは、*NT SERVICE\PBIEgwService* です。 ゲートウェイでは、そのフォルダーにあるカスタム コネクタ ファイルが自動的に読み込まれます。 これらは、データ コネクタの一覧に表示されます。

![カスタム データ コネクタ](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

オンプレミス データ ゲートウェイ (個人用モード) を使用している場合は、Power BI レポートを Power BI サービスにアップロードし、ゲートウェイを使用してそれを更新することができます。

オンプレミス データ ゲートウェイの場合は、カスタム コネクタのデータ ソースを作成する必要があります。 ゲートウェイ クラスターにこのクラスターでのカスタム コネクタの使用を許可することを選択すると、Power BI サービスのゲートウェイ設定ページにオプションが表示されるはずです。 このオプションを使用可能にするため、クラスター内のすべてのゲートウェイに 2018 年 7 月以降の更新プログラムのリリースがあることを確認します。 そのオプションを選択して、このクラスターでのカスタム コネクタの使用を有効にします。

![[ゲートウェイ クラスターの設定] ページ](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

このオプションを有効にすると、このゲートウェイ クラスターの下に作成できる使用可能なデータ ソースとしてカスタム コネクタが表示されます。 新しいカスタム コネクタを使用するデータ ソースを作成した後、Power BI サービスでそのカスタム コネクタを使用して、Power BI レポートを更新できます。

![[データ ソース設定] ページ](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

* 作成するフォルダーに、バック グラウンドのゲートウェイ サービスがアクセスできることを確認します。 通常、ユーザーの Windows フォルダー下のフォルダーやシステム フォルダーにはアクセスできません。 フォルダーにアクセスできない場合、オンプレミス データ ゲートウェイ アプリにメッセージが表示されます。 この手順は、オンプレミス データ ゲートウェイ (個人用モード) には適用されません。
* オンプレミス データ ゲートウェイで使用するカスタム コネクタには、カスタム コネクタのコードで "TestConnection" セクションを実装する必要があります。 Power BI Desktop でカスタム コネクタを使用する場合、このセクションは必要ありません。 このため、Power BI Desktop で動作するコネクタを使用できますが、ゲートウェイでは使用できません。 TestConnection セクションの実装方法の詳細については、[こちらのドキュメント](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support)を参照してください。

## <a name="next-steps"></a>次の手順

* [データ ソースの管理 - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [データ ソースの管理 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [データ ソースの管理 - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [データ ソースの管理 - Oracle](service-gateway-onprem-manage-oracle.md)  
* [データ ソースの管理 - インポート/スケジュールされた更新](service-gateway-enterprise-manage-scheduled-refresh.md)
* [オンプレミス データ ゲートウェイのプロキシ設定を構成する](/data-integration/gateway/service-gateway-proxy)
* [Power BI からオンプレミス データ ソースへのシングル サインオン (SSO) に Kerberos を使用する](service-gateway-sso-kerberos.md)  

他にわからないことがある場合は、 [Power BI コミュニティ](http://community.powerbi.com/)で質問してみてください。
