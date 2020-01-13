---
title: Power BI Pro のライセンスを購入して割り当てる
description: Power BI Pro のユーザー ライセンスを購入して割り当て、ユーザーが Power BI サービスのコンテンツにアクセスして同僚と共同作業を行えるようにする方法を説明します。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 12/18/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 01eb30857b0b76f96e7e18115d92fb1d68dbef0c
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223821"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Power BI Pro のユーザー ライセンスを購入して割り当てる

Power BI Pro は個人ユーザー ライセンスです。ユーザーは、Power BI サービスに対して他のユーザーが発行したレポートやダッシュボードを閲覧して対話的に操作したり、他の Power BI Pro ユーザーとコンテンツを共有して共同作業を行ったりすることができます。 コンテンツが Power BI Premium 容量でホストされている場合を除き、コンテンツを発行したり他のユーザーと共有したり、他のユーザーが作成したコンテンツを利用したりできるのは、Power BI Pro ユーザー ライセンスを持ったユーザーだけです。 詳細については、「[Power BI の価格](https://powerbi.microsoft.com/pricing/)」の「_Power BI 機能の比較_」セクションを参照してください。

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Power BI Pro のユーザー ライセンスを購入して割り当てる

この記事では、Microsoft 365 管理センターで Power BI Pro ユーザー ライセンスを購入する方法について説明します。その後、それらのライセンスを個々のユーザーに割り当てる 2 つの方法についても説明します。Microsoft 365 管理センターと Azure portal のどちらかの方法を管理者は選択することになります。

### <a name="prerequisites"></a>前提条件

Microsoft 365 管理センターでライセンスを購入して割り当てるには、Microsoft 365 の **[グローバル管理者または課金管理者](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** のどちらかのロールのメンバーであることが必要です。

Azure portal でライセンスの割り当てを行うユーザーは、Power BI が Azure Active Directory 参照で使用する Azure サブスクリプションの所有者である必要があります。

### <a name="purchase-licenses-in-microsoft-365"></a>Microsoft 365 でライセンスを購入する

Microsoft 365 管理センターで Power BI Pro ライセンスを購入するには、次の手順に従います。

1. [Microsoft 365 管理センター](https://portal.office.com/adminportal/home#/homepage)を開きます。

2. ナビ ペインで、 **[課金]** を選択し、次に **[サブスクリプション]** を選択します。

3. **[サブスクリプション]** ページの右上隅にある **[サブスクリプションの追加]** を選択します。

4. 次のようにして、目的のサブスクリプション オファーを見つけます。

    - **[Enterprise Suite]** で、 **[Office 365 Enterprise E5]** を選択します。

    - **[その他のプラン]** で、 **[Power BI Pro]** を選択します。

5. 目的のサブスクリプションの省略記号 ( **. . .** ) をポイントし、 **[今すぐ購入]** を選択します。

6. ご自分の状況に応じて、**毎月支払う**か、**1 年分支払う**かを選択します。

7. **[ユーザーはいくつ必要ですか?]** に必要なライセンスの数を入力してから、 **[今すぐ支払う]** を選択してトランザクションを完了します。

8. **[サブスクリプション]** ページに取得したサブスクリプションがリストされていることを確認します。

9. 最初の購入後に、さらにライセンスを追加するには、 **[サブスクリプション]** ページで **[Power BI Pro]** を選択した後、 **[ライセンス数の変更]** を選択します。

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理センターでライセンスを割り当てる

Microsoft 365 管理センターでライセンスを割り当てる方法については、「[ユーザーにライセンスを割り当てる](/office365/admin/manage/assign-licenses-to-users)」を参照してください。

ゲスト ユーザーについては、「[[ライセンス] ページでユーザーにライセンスを割り当てる](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page)」を参照してください。 ゲスト ユーザーに Pro ライセンスを割り当てる前に、Microsoft アカウントの担当者に連絡して、Microsoft との契約条件に準拠していることを確認してください。

### <a name="assign-licenses-in-the-azure-portal"></a>Azure portal でライセンスを割り当てる

次の手順に従って、個々のユーザー アカウントに Power BI Pro ライセンスを割り当てます。

1. [Azure Portal](https://portal.azure.com/) を開きます。

2. **Azure Active Directory** を検索して選択します。

3. **[Azure Active Directory]** で、 **[ライセンス]** を選択します。

4. **[ライセンス]** で、 **[すべての製品]** を選択します。次に **[Power BI Pro]** を選択して、ライセンス ユーザーの一覧を表示します。

5. **[割り当て]** を選択して、Power BI Pro ライセンスをユーザー アカウントに追加します。

## <a name="next-steps"></a>次の手順

ライセンスの割り当てが終わりました。Power BI Pro の詳細を確認してください。

[組織での Power BI のライセンス](service-admin-licensing-organization.md)

[サインインした Power BI ユーザーを見つける](service-admin-access-usage.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
