---
title: Power BI で Snowflake に接続する
description: Power BI 用の SSO を使用した Snowflake
author: cpopell
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e5519e30be30d6367791d1b6822196b407a21b1
ms.sourcegitcommit: 4d98274aa0b9aa09db99add2dda91a3ba8fed40b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576854"
---
#  <a name="connecting-to-snowflake-in-power-bi-service"></a>Power BI サービスでの Snowflake への接続

## <a name="introduction"></a>概要

Power BI サービスでの Snowflake への接続は、1 つの点でのみ他のコネクタと異なります。それは、AAD に対して追加の機能が (SSO のオプションと共に) 提供されることです。 統合のさまざまな部分で、Snowflake、Power BI、Azure の異なる管理者ロールが必要です。 また、SSO を使用せずに AAD 認証を有効にすることもできます。 基本認証は、サービス内の他のコネクタと同様に機能します。

AAD 統合を構成すること、また、オプションで SSO を有効にすることに関心がある場合:
* Snowflake 管理者の方は、Snowflake のドキュメントで「[Snowflake への Power BI SSO - はじめに](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html)」の記事を参照してください。
* (SSO) Power BI 管理者の方は、「Power BI サービス構成 - 管理ポータル」セクションを参照してください。
* (SSO) Power BI データセット作成者の方は、「Power BI サービス構成 - データセットの有効化」セクションを参照してください。

## <a name="power-bi-service-configuration"></a>Power BI サービス構成

### <a name="admin-portal"></a>管理ポータル

SSO を有効にする場合は、テナント管理者が管理ポータルにアクセスし、Power BI AAD の資格情報を Snowflake に送信することを承認する必要があります。

![テナント管理者による Snowflake SSO の設定](media/service-connect-snowflake/snowflakessotenant.png)

[管理ポータル] に移動し、サイド バー項目の [テナントの設定] を選択します。[統合の設定] まで下にスクロールすると、[Snowflake SSO] のオプションが表示されます。

警告が表示されたら、自身の AAD トークンを Snowflake サーバーに送信することに同意するために、この設定を手動で有効にする必要があります。 有効にするには、[無効] をクリックして切り替え、[適用] をクリックして、設定の変更が有効になるまで待ちます。 構成がサービスに反映されるのに 1 時間ほどかかる場合があります。

この処理が完了すると、SSO でレポートを使用できるようになります。

### <a name="configuring-a-dataset-with-aad"></a>AAD を使用したデータセットの構成

Snowflake コネクタに基づくレポートが Web に発行されたら、データセットの作成者は Power BI Web サービスで適切なワークスペースに移動し、[データセット] を選択して、[設定] を (該当するデータセットの横にある、その他の操作のための [...] メニューで) 選択する必要があります。

Power BI の動作上の理由により、SSO は、オンプレミス データ ゲートウェイを介して実行されているデータソースがない場合にのみ機能します。

* ご自身のデータ モデルで Snowflake ソースのみを使用している場合は、オンプレミス データ ゲートウェイを使用しないように選択すると、SSO を使用できます。
* Snowflake ソースを別のソースと共に使用している場合は、どのソースでも、オンプレミス データ ゲートウェイを使用していなければ SSO を使用できます。
* オンプレミス データ ゲートウェイを介して Snowflake ソースを使用している場合、AAD 資格情報は現在サポートされていません。 Power BI の IP 範囲全体ではなく、ゲートウェイがインストールされている単一の IP から VNet にアクセスしようとしている場合は、これが関係している可能性があります。
* ゲートウェイを必要とする別のソースと共に Snowflake ソースを使用している場合は、オンプレミス データ ゲートウェイでも Snowflake を使用する必要があり、SSO を使用することはできません。

オンプレミス データ ゲートウェイの使用方法の詳細については、「[オンプレミス データ ゲートウェイとは](https://docs.microsoft.com/power-bi/service-gateway-onprem)」の記事を参照してください。

ゲートウェイを使用していない場合は、準備ができています。 オンプレミス データ ゲートウェイに構成されている Snowflake 資格情報があるものの、そのデータ ソースをご自身のモデルのみで使用している場合は、[データセットの設定] ページの切り替えをクリックして、そのデータ モデルに対してゲートウェイを無効にすることができます。

![ゲートウェイをオフに切り替えるデータセットの設定](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

データセットの作成者は、[データ ソースの資格情報] を選択してサインインする必要があります。 データセットからは、基本資格情報または OAuth2 (AAD) 資格情報で Snowflake にサインインできます。 AAD の使用を選択した場合は、データセットを有効にして SSO を使用できます。 この最初のユーザーがデータセットを取得するために Snowflake にサインインするとき、他のユーザーがデータを取得するために Oauth2 資格情報が使用されるようにするオプションを選択する必要があります。 これにより、AAD SSO が有効になります。 最初のユーザーが基本認証または OAuth2 (AAD) を使用してサインインしているかどうかにかかわらず、SSO 用に送信されるのは AAD の資格情報です。 

![Snowflake SSO のデータセット設定](media/service-connect-snowflake/snowflakessocredui.png)

これが完了すると、その他のユーザーは自動的に AAD 認証を使用して、その Snowflake データセットのデータに接続するようになります。

SSO を有効にしないことを選択した場合、レポートを更新するユーザーは、他のほとんどの Power BI レポートと同様に、サインインしたユーザーの資格情報を使用することになります。

### <a name="troubleshooting"></a>トラブルシューティング

統合に関する問題が発生した場合は、Snowflake の[トラブルシューティング ガイド](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting)を参照してください。

