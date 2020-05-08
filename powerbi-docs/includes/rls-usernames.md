---
ms.openlocfilehash: 3e89344ef1298864b485f465b28c56397a7e1511
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "61194093"
---
## <a name="using-the-username-or-userprincipalname-dax-function"></a>username() または userprincipalname() DAX 関数の使用
データセット内で DAX 関数 *username()* または *userprincipalname()* を利用できます。 Power BI Desktop の式の中で使用することができます。 モデルを発行するときに、Power BI サービス内で使用されます。

Power BI Desktop 内で、*username()* は *DOMAIN\User* の形式でユーザーを返し、*userprincipalname()* は <em>user@contoso.com</em> の形式でユーザーを返します。

Power BI サービス内で、*username()* と *userprincipalname()* は両方とも、ユーザーのユーザー プリンシパル名 (UPN) を返します。 これはメール アドレスに似ています。

