---
title: インクルード ファイル
description: インクルード ファイル
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: d56988986cfd994bb21c9bc25d024903719472cf
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82255810"
---
## <a name="single-sign-on"></a>シングル サインオン

Azure SQL の DirectQuery データセットをサービスに発行した後は、Azure Active Directory (Azure AD) OAuth2 を使用して、エンドユーザーのシングル サインオン (SSO) を有効にできます。

SSO を有効にするには、データセットの設定に移動し、 **[データ ソース]** タブを開いて、SSO のチェック ボックスをオンにします。

![Azure SQL DQ の構成ダイアログ ボックス](media/direct-query-sso/sso-dialog.png)

SSO オプションが有効になっている場合、データ ソースを基に作成されたレポートにユーザーがアクセスすると、Power BI によって Azure SQL Database または Data Warehouse へのクエリで、認証済みの Azure AD 資格情報が送信されます。 このオプションを使用すると、Power BI で、データ ソース レベルで構成されているセキュリティ設定を適用できます。

SSO オプションは、このデータ ソースを使うすべてのデータセットで有効になります。 インポートのシナリオに使われる認証方法には影響しません。

