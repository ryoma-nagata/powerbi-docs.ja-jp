---
title: オンプレミス データ ゲートウェイに関するよく寄せられる質問 (FAQ) - Power BI
description: これは、Power BI のオンプレミス データ ゲートウェイに関してよく寄せられる質問 (FAQ) です。 Power BI で使用されるゲートウェイに関してよく寄せられる質問を 1 か所にまとめています。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 99a03f88ed5f6585ca8ed6d64f396e70cdd046e5
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68272748"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>オンプレミス データ ゲートウェイに関するよく寄せられる質問 (FAQ) - Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**質問:** パーソナル ゲートウェイをアップグレードする必要はありますか。  
**回答:** いいえ。Power BI のパーソナル ゲートウェイを引き続き使用できます。

**質問:** ゲートウェイをインストールし、それを Power BI サービスで管理するために必要な特別なアクセス許可はありますか。
**回答:** 特別なアクセス許可は必要ありません。

**質問:** オンプレミスのデータ ソースに接続する Power Pivot データ モデルの入った Excel ブックをアップロードできますか。 このシナリオではゲートウェイは必要ですか。  
**回答:** はい、そのようなブックをアップロードできます。 ゲートウェイは必要ありません。 データが Excel データ モデルに存在するため、Excel ブックに基づく Power BI でのレポートはライブではなくなります。 Power BI のレポートを更新するには、更新されたブックを毎回、再アップロードする必要があります。 あるいは、更新をスケジュールし、ゲートウェイを使用します。

**質問:** ユーザーが DirectQuery 接続のあるダッシュボードを共有する場合、同じアクセス許可を持たない他のユーザーでもデータを表示できますか。  
**回答:** Analysis Services に接続されたダッシュボードの場合、ユーザーはアクセス権限を持つデータのみを表示できます。 ユーザーが同じアクセス許可を持たない場合、データを表示できません。 その他のデータ ソースの場合、すべてのユーザーはそのデータ ソースの管理者によって入力された資格情報を共有します。

**質問:** Oracle サーバーに接続できないのはなぜですか。  
**回答:** Oracle サーバーに接続するには、Oracle クライアントをインストールし、tnsnames.ora ファイルに適切なサーバー情報を構成することが必要な場合があります。 このインストールは、ゲートウェイとは別に行います。 詳細については、「[Oracle クライアントのインストール](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client)」をご覧ください。

**質問:** ゲートウェイは ExpressRoute と連携して動作しますか。  
**回答:** はい。 ExpressRoute と Power BI の詳細については、「[Power BI と ExpressRoute](service-admin-power-bi-expressroute.md)」を参照してください。

**質問:** R スクリプトを使用しています。 これには対応していますか。
**回答**:R スクリプトは、個人用モードでのみサポートされています。

## <a name="analysis-services-in-power-bi"></a>Power BI の Analysis Services

**質問:** Analysis Services では、msdmpump.dll を使用してカスタムの有効なユーザー名マッピングを作成できますか。  
**回答:** いいえ。 現時点ではサポートされていません。

**質問:** ゲートウェイを使用し、多次元 (OLAP) インスタンスに接続できますか。  
**回答:** はい。 オンプレミス データ ゲートウェイでは、Analysis Services の表形式と多次元モデルへのライブ接続をサポートしています。

**質問:** Windows 認証を使用するオンプレミス サーバーとは異なるドメイン内のコンピューターにゲートウェイをインストールした場合、どうなりますか。  
**回答:** 結果は保証されません。 うまく機能するかどうかはすべて、2 つのドメイン間の信頼関係に応じて決まります。 2 つの異なるドメインが信頼されたドメイン モデルに含まれていれば、ゲートウェイは Analysis Services サーバーに接続し、有効なユーザー名を解決できる可能性があります。 含まれていない場合、ログインできないことがあります。

**質問:** オンプレミスの Analysis Services サーバーにどの有効なユーザー名が渡されているかを調べる方法がありますか。  
**回答:** これについては[トラブルシューティング記事](service-gateway-onprem-tshoot.md)で回答します。

## <a name="next-steps"></a>次の手順

* [オンプレミス データ ゲートウェイのトラブルシューティング](/data-integration/gateway/service-gateway-tshoot)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

