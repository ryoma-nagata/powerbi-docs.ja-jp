---
ms.openlocfilehash: 8dc488a47ac2b5b4e7980b7404b2722b1120b6ab
ms.sourcegitcommit: cde65bb8b1bed1ee8cf512651afeb829ddc155de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "77464408"
---
## <a name="validate-the-roles-within-power-bi-desktop"></a>Power BI Desktop 内でロールを検証する
ロールを作成したら、Power BI Desktop 内でロールの結果をテストします。

1. **[モデリング]** タブから **[ロールとして表示]** を選択します。 

    ![[ロールとして表示] を選択する](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles.png)

    **[ロールとして表示]** ウィンドウが表示されます。このウィンドウには、作成したロールが表示されます。

    ![[ロールとして表示] ウィンドウ](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-view-as-roles-dialog.png)

3. 作成したロールを選択し、 **[OK]** を選択してそのロールを適用します。 

   レポートでは、そのロールに関連するデータがレンダリングされます。

4. **その他のユーザー**を選択し、特定のユーザーを指定することもできます。 

    ![[その他のユーザー] を選択する](./media/rls-desktop-view-as-roles/powerbi-desktop-rls-other-user.png)

   ユーザー プリンシパル名 (UPN) を、Power BI サービスおよび Power BI Report Server で使用されるものとして指定することをお勧めします。

   Power BI Desktop の **[その他のユーザー]** には、DAX 式に基づいた動的セキュリティを使用している場合にのみ、異なる結果が表示されます。 

5. **[OK]** を選択します。 

   そのユーザーに対して表示できる内容に基づいてレポートがレンダリングされます。



