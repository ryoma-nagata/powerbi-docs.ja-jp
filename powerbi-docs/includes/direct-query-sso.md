---
title: インクルード ファイル
description: インクルード ファイル
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: ed87101fe7f5fadd24594d53bbd0ffb6f029faa4
ms.sourcegitcommit: 92b033ee7a6e36808371b247b7b41536cee6c2f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "90012799"
---
## <a name="single-sign-on"></a>シングル サインオン

Azure SQL の DirectQuery データセットをサービスに発行した後は、Azure Active Directory (Azure AD) OAuth2 を使用して、エンドユーザーのシングル サインオン (SSO) を有効にできます。

SSO を有効にするには、データセットの設定に移動し、 **[データ ソース]** タブを開いて、SSO のチェック ボックスをオンにします。

![Azure SQL DQ の構成ダイアログ ボックス](media/direct-query-sso/sso-dialog.png)

SSO オプションが有効になっている場合、データ ソースを基に作成されたレポートにユーザーがアクセスすると、Power BI によって Azure SQL Database または Data Warehouse へのクエリで、認証済みの Azure AD 資格情報が送信されます。 このオプションを使用すると、Power BI で、データ ソース レベルで構成されているセキュリティ設定を適用できます。

SSO オプションは、このデータ ソースを使うすべてのデータセットで有効になります。 インポートのシナリオに使われる認証方法には影響しません。

> [!Note]
> Azure Multi-Factor Authentication (MFA) はサポートされていません。 DirectQuery で SSO を使用する必要があるユーザーは、MFA から除外する必要があります。
