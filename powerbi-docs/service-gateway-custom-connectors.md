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
ms.openlocfilehash: 074a8dd876e0612f87c220f9fb077b60b2b85c88
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271808"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>オンプレミス データ ゲートウェイでカスタム データ コネクタを使用する

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Power BI 用データ コネクタを使用すると、アプリケーション、サービス、またはデータ ソースからデータに接続してアクセスすることができます。 カスタム データ コネクタを開発して、Power BI Desktop で使用することができます。

Power BI 用にカスタム データ コネクタを開発する方法の詳細については、[Data Connector SDK GitHub のページ](http://aka.ms/dataconnectors)を参照してください。 このサイトには、Power BI と Power Query の概要情報とサンプルが含まれています。

Power BI Desktop でカスタム データ コネクタを使用するレポートを作成すると、オンプレミス データ ゲートウェイを使用して Power BI サービスからこれらのレポートを更新することができます。

## <a name="how-to-enable-and-use-this-capability"></a>この機能を有効にして使用する方法

オンプレミス データ ゲートウェイの 2018 年 7 月以降のバージョンをインストールすると、オンプレミス データ ゲートウェイ アプリに **[コネクタ]** タブが表示されます。ここでは、カスタム コネクタの読み込み元のフォルダーを選択するオプションが表示されます。 必ずゲートウェイ サービスを実行しているユーザーがアクセスできるフォルダーを選択してください (既定では *NT SERVICE\PBIEgwService*)。 そのフォルダー内のカスタム コネクタ ファイルがゲートウェイによって自動的に読み込まれ、それらのファイルがデータ コネクタの一覧に表示されます。

![カスタム コネクタ 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

オンプレミス データ ゲートウェイ (個人用モード) を使用している場合は、この時点で、ご利用の Power BI レポートを Power BI サービスにアップロードして、ゲートウェイを使用してそれを更新できるはずです。

オンプレミス データ ゲートウェイの場合でも、カスタム コネクタのデータ ソースを作成する必要があります。 ゲートウェイ クラスターにこのクラスターでのカスタム コネクタの使用を許可することを選択すると、Power BI サービスの [ゲートウェイ設定] ページに、新しいオプションが表示されます。 このオプションを使用可能にするため、クラスター内のすべてのゲートウェイに 2018 年 7 月以降の更新プログラムのリリースがあることを確認します。 ここで、そのオプションを選択して、このクラスターでのカスタム コネクタの使用を有効にします。

![カスタム コネクタ 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

このオプションを有効にすると、このゲートウェイ クラスターの下に作成できる使用可能なデータ ソースとして、カスタム コネクタが表示されます。 新しいカスタム コネクタを使用してデータ ソースを作成したら、Power BI サービスでそのカスタム コネクタを使用して、Power BI レポートを更新できるようになります。

![カスタム コネクタ 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

* 作成するフォルダーに、バック グラウンドのゲートウェイ サービスがアクセスできることを確認します。 通常、ユーザーの Windows フォルダー下のフォルダーやシステム フォルダーにはアクセスできません。 フォルダーにアクセスできない場合、オンプレミス データ ゲートウェイ アプリでメッセージが表示されます (これは、個人用バージョンのゲートウェイには適用されません)
* オンプレミス データ ゲートウェイで使用するカスタム コネクタには、カスタム コネクタのコードで "TestConnection" セクションを実装する必要があります。 これは Power BI Desktop でカスタム コネクタを使用する場合には必要ありません。 Desktop で機能するカスタム コネクタを持つことはできますが、この理由からゲートウェイでは機能しません。 TestConnection セクションの実装方法については、[このドキュメント](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support)を参照してください。

## <a name="next-steps"></a>次の手順

* [データ ソースの管理 - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [データ ソースの管理 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [データ ソースの管理 - SQL Server](service-gateway-enterprise-manage-sql.md)  
* [データ ソースの管理 - Oracle](service-gateway-onprem-manage-oracle.md)  
* [データ ソースの管理 - インポート/スケジュールされた更新](service-gateway-enterprise-manage-scheduled-refresh.md)  

* [オンプレミス データ ゲートウェイのプロキシ設定を構成する](/data-integration/gateway/service-gateway-proxy)  
* [Power BI からオンプレミス データ ソースへの SSO (シングル サインオン) に Kerberos を使用する](service-gateway-sso-kerberos.md)  

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。
