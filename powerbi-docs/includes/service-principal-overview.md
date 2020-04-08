---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621608"
---
サービス プリンシパルとは、Azure AD アプリケーションが Power BI サービスのコンテンツと API にアクセスできるようにするための認証方法です。

Azure Active Directory (Azure AD) アプリを作成すると、[サービス プリンシパル オブジェクト](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)が作成されます。 サービス プリンシパル オブジェクト (単に "*サービス プリンシパル*" とも呼ばれる) を使用することで、Azure AD はご利用のアプリの認証を行うことができます。 認証が完了すると、アプリは Azure AD テナント リソースにアクセスできるようになります。

認証を行うために、サービス プリンシパルでは、Azure AD アプリの "*アプリケーション ID*" と次のいずれかが使用されます。
* アプリケーション シークレット
* 証明書