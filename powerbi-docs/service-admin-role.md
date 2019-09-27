---
title: Power BI 管理者の役割について
description: Power BI サービス内にインポートしたデータセットと DirectQuery の行レベルのセキュリティを構成する方法。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2185d7a9c91ed014cf0bed29d6393be0e40556a8
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71074504"
---
# <a name="understanding-the-power-bi-service-administrator-role"></a>Power BI サービス管理者ロールについて

組織で Power BI サービス管理者ロールを使用する方法について説明します。 このロールのユーザーは、Power BI テナントとその管理機能を完全に制御できます (ライセンス以外)。

<iframe width="640" height="360" src="https://www.youtube.com/embed/PQRbdJgEm3k?showinfo=0" frameborder="0" allowfullscreen></iframe>

Office 365 の完全な管理アクセス権を付与することなく、Power BI 管理ポータルにアクセスできるようにする必要があるユーザーには、Power BI サービス監理者ロールを割り当てることができます。

Office 365 ユーザー管理管理者が、Microsoft 365 管理センターまたは PowerShell スクリプトを使用して、ユーザーを Power BI サービス管理者ロールに割り当てます。 割り当てられたユーザーは、[Power BI 管理ポータル](service-admin-portal.md)にアクセスできます。 そこで、テナント全体の利用状況の指標にアクセスでき、Power BI 機能のテナント全体の利用状況を制御できます。

## <a name="limitations-and-considerations"></a>制限事項と考慮事項

Power BI サービス管理者ロールでは、次の機能を使用できません。

* Microsoft 365 管理センター内のユーザーとライセンスを変更する機能

* 監査ログへのアクセス 詳しくは、「[組織内での監査の使用](service-admin-auditing.md)」をご覧ください。

## <a name="assign-users-to-the-admin-role-in-office-365"></a>Office 365 で管理者ロールにユーザーを割り当てる

Microsoft 365 管理センターでユーザーを Power BI 管理者ロールに割り当てるには、以下の手順を行います。

1. [Microsoft 365 管理センター](https://portal.office.com/adminportal/home#/homepage)で、**[ユーザー]** > **[アクティブなユーザー]** の順に選択します。

    ![Microsoft 365 管理センター](media/service-admin-role/powerbi-admin-users.png)

1. 役割を割り当てるユーザーを選択します。

1. **[役割]** で **[編集]** を選択します。

    ![ロールを編集する](media/service-admin-role/powerbi-admin-edit-roles.png)

1. **[カスタム管理者]** > **[Power BI サービス管理者]** の順に選択します。

    ![Power BI サービス管理者](media/service-admin-role/powerbi-admin-role.png)

1. **[保存]** を選択し、**[閉じる]** を選択します。

そのユーザー名の役割に対する **[Power BI service administrator]** \(Power BI サービス管理者) がリストされます。

![表示](media/service-admin-role/powerbi-admin-role-set.png)

## <a name="assign-users-to-the-admin-role-with-powershell"></a>PowerShell で管理者ロールにユーザーを割り当てる

PowerShell を使用してロールにユーザーを割り当てることもできます。 ユーザーは、Azure Active Directory (Azure AD) で管理されます。 Azure AD PowerShell モジュールがまだない場合は、[最新バージョンをダウンロードしてインストール](https://www.powershellgallery.com/packages/AzureAD/)します。

1. 最初に、Azure AD に接続します。
   ```
   PS C:\Windows\system32> Connect-AzureAD
   ```

1. 次に、**Power BI サービス管理者**ロールに対する **ObjectId** を取得します。 [Get-AzureADDirectoryRole](/powershell/module/azuread/get-azureaddirectoryrole) を実行することで、**ObjectId** を取得できます。

    ```
    PS C:\Windows\system32> Get-AzureADDirectoryRole

    ObjectId                             DisplayName                        Description
    --------                             -----------                        -----------
    00f79122-c45d-436d-8d4a-2c0c6ca246bf Power BI Service Administrator     Full access in the Power BI Service.
    250d1222-4bc0-4b4b-8466-5d5765d14af9 Helpdesk Administrator             Helpdesk Administrator has access to perform..
    3ddec257-efdc-423d-9d24-b7cf29e0c86b Directory Synchronization Accounts Directory Synchronization Accounts
    50daa576-896c-4bf3-a84e-1d9d1875c7a7 Company Administrator              Company Administrator role has full access t..
    6a452384-6eb9-4793-8782-f4e7313b4dfd Device Administrators              Device Administrators
    9900b7db-35d9-4e56-a8e3-c5026cac3a11 AdHoc License Administrator        Allows access manage AdHoc license.
    a3631cce-16ce-47a3-bbe1-79b9774a0570 Directory Readers                  Allows access to various read only tasks in ..
    f727e2f3-0829-41a7-8c5c-5af83c37f57b Email Verified User Creator        Allows creation of new email verified users.
    ```

    この例では、ロールの **ObjectId** は 00f79122-c45d-436d-8d4a-2c0c6ca246bf となります。

1. 次に、ユーザーの **ObjectId** を取得します。 [Get-AzureADUser](/powershell/module/azuread/get-azureaduser) を実行して見つけることができます。

    ```
    PS C:\Windows\system32> Get-AzureADUser -ObjectId 'tim@contoso.com'

    ObjectId                             DisplayName UserPrincipalName      UserType
    --------                             ----------- -----------------      --------
    6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c Tim         tim@contoso.com        Member
    ```

1. 役割にメンバーを追加するには、[Add-AzureADDirectoryRoleMember](/powershell/module/azuread/add-azureaddirectoryrolemember) を実行します。

    | パラメーター | 説明 |
    | --- | --- |
    | ObjectId |ロールの ObjectId。 |
    | RefObjectId |メンバーの ObjectId。 |

    ```powershell
    Add-AzureADDirectoryRoleMember -ObjectId 00f79122-c45d-436d-8d4a-2c0c6ca246bf -RefObjectId 6a2bfca2-98ba-413a-be61-6e4bbb8b8a4c
    ```

## <a name="next-steps"></a>次の手順

[組織内の Power BI を管理する](service-admin-administering-power-bi-in-your-organization.md)  
[Power BI 管理ポータル](service-admin-portal.md)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](http://community.powerbi.com/)。