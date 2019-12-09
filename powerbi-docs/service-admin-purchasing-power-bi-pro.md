---
title: Power BI Pro のライセンスを購入して割り当てる
description: Power BI Pro のユーザー ライセンスを購入して割り当て、ユーザーが Power BI サービスのコンテンツにアクセスして同僚と共同作業を行えるようにする方法を説明します。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: ebaf32bbf84dcbb8efd8516fd0a1ab01011f2d63
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698488"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Power BI Pro のユーザー ライセンスを購入して割り当てる

Power BI Pro は個人ユーザー ライセンスです。ユーザーは、Power BI サービスに対して他のユーザーが発行したレポートやダッシュボードを閲覧して対話的に操作したり、他の Power BI Pro ユーザーとコンテンツを共有して共同作業を行ったりすることができます。 コンテンツが Power BI Premium 容量でホストされている場合を除き、コンテンツを発行したり他のユーザーと共有したり、他のユーザーが作成したコンテンツを利用したりできるのは、Power BI Pro ユーザー ライセンスを持ったユーザーだけです。 詳細については、「[Power BI features by license type](service-features-license-type.md)」 (Power BI のライセンスの種類別機能) を参照してください。

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Power BI Pro のユーザー ライセンスを購入して割り当てる

この記事では、Microsoft 365 管理センターで Power BI Pro ユーザー ライセンスを購入する方法について説明します。その後、それらのライセンスを個々のユーザーに割り当てる 2 つの方法についても説明します。Microsoft 365 管理センターと Azure portal のどちらかの方法を管理者は選択することになります。

### <a name="prerequisites"></a>前提条件

Microsoft 365 管理センターでライセンスを購入して割り当てるには、Microsoft 365 の **[グローバル管理者または課金管理者](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** のどちらかのロールのメンバーであることが必要です。

Azure portal でライセンスの割り当てを行うユーザーは、Power BI が Azure Active Directory 参照で使用する Azure サブスクリプションの所有者である必要があります。

### <a name="purchase-licenses-in-microsoft-365"></a>Microsoft 365 でライセンスを購入する

Microsoft 365 管理センターで Power BI Pro ライセンスを購入するには、次の手順に従います。

1. [Microsoft 365 管理センター](https://portal.office.com/adminportal/home#/homepage)を開きます。

2. ナビ ペインで、 **[課金]**  >  **[サブスクリプション]** の順に選択します。

    ![ナビ ペイン](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. **[サブスクリプション]** ページの右上隅にある **[サブスクリプションの追加]** を選択します。

    ![サブスクリプション](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. 次のようにして、目的のサブスクリプション オファーを見つけます。

    **[Enterprise Suite]** で、 **[Office 365 Enterprise E5]** を選択します。

    ![Office E5 サブスクリプション](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    **[その他のプラン]** で、 **[Power BI Pro]** を選択します。

    ![Power BI Pro のサブスクリプション](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. 目的のサブスクリプションの省略記号 ( **. . .** ) をポイントし、 **[今すぐ購入]** を選択します。

    ![今すぐ購入する](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. ご自分の状況に応じて、**毎月支払う**か、**1 年分支払う**かを選択します。

7. **[ユーザーはいくつ必要ですか?]** に必要なライセンスの数を入力してから、 **[今すぐ支払う]** を選択してトランザクションを完了します。

8. **[サブスクリプション]** ページに取得したサブスクリプションがリストされていることを確認します。

   ![影響を受けるサブスクリプション](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. 最初の購入後に、さらにライセンスを追加するには、 **[サブスクリプション]** ページで **[Power BI Pro]** を選択した後、 **[ライセンスの追加/削除]** を選択します。

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Microsoft 365 管理センターでライセンスを割り当てる

次の手順に従って、個々のユーザー アカウントに Power BI Pro ライセンスを割り当てます。

1. [Microsoft 365 管理センター](https://portal.office.com/adminportal/home#/homepage)を開きます。

2. ナビ ペインで **[ユーザー]** を展開し、 **[アクティブ ユーザー]** を選択します。

    ![アクティブ ユーザー](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. ユーザーを選択し、 **[製品ライセンス]** で **[編集]** を選択します。

    ![製品ライセンスの編集](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. **[Power BI Pro]** で、設定を **[オン]** に切り替え、 **[保存]** を選択します。

    ![製品ライセンスをオンにする](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. 選択したアカウントの **[状態]** で、Power BI Pro ライセンスが正常に割り当てられていることを確認します。

    ![ライセンスの状態の確認](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Azure portal でライセンスを割り当てる

次の手順に従って、個々のユーザー アカウントに Power BI Pro ライセンスを割り当てます。

1. [Azure Portal](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0) を開きます。

2. ナビ ペインで **[Azure Active Directory]** を選択します。

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. **[Azure Active Directory]** で、 **[ライセンス]** を選択します。

    ![ライセンス](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. **[ライセンス]** で、 **[すべての製品]** を選択します。次に **[Power BI Pro]** を選択して、ライセンス ユーザーの一覧を表示します。

    ![ライセンス - すべての製品](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. **[割り当て]** を選択して、Power BI Pro ライセンスをユーザー アカウントに追加します。

    ![ライセンスの割り当て](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>次の手順

ライセンスの割り当てが終わりました。Power BI Pro の詳細を確認してください。

[組織での Power BI のライセンス](service-admin-licensing-organization.md)

[サインインした Power BI ユーザーを見つける](service-admin-access-usage.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
