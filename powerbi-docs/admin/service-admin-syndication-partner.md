---
title: Power BI を O365 パートナーに追加できない
description: Power BI を Microsoft 365 シンジケート パートナーに追加できません。 シンジケート モデルは Microsoft 365 で使用される購入モデルです。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 2c590875b4dee81f7ca54434d6e5895be885be97
ms.sourcegitcommit: 2cb249fc855e369eed1518924fbf026d5ee07eb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2020
ms.locfileid: "83812337"
---
# <a name="unable-to-add-power-bi-to-office-365-partner-subscription"></a>Power BI を Office 365 パートナー サブスクリプションに追加できない

Microsoft 365 では、企業が独自のソリューションとバンドルおよび統合した Microsoft 365 を再販することが可能です。購入、請求、サポートを一本化したサービスをエンド カスタマーに提供できます。

Office 365 サブスクリプションに加えて Power BI のご利用に関心をお持ちの場合は、お客様のパートナーにお問い合わせください。 現在パートナーで Power BI が提供されていない場合は、他のオプションを利用できます。

## <a name="work-with-your-partner-to-purchase-power-bi"></a>パートナーから Power BI を購入する

Power BI Pro または Power BI Premium へのサブスクリプションを購入する場合、パートナーに問い合わせて選択できるオプションについて検討します。

* Power BI をポートフォリオに追加することをパートナーが承諾したなら、パートナーから購入できるようになります。

* パートナーは、Power BI を Microsoft から直接、または Power BI を提供している別のパートナーから購入できるモデルにお客様を移行することができます。

## <a name="purchase-from-microsoft-or-another-channel"></a>Microsoft または別のチャネルから購入する

パートナーとの関係によっては、Microsoft または別のパートナーから Power BI を直接購入できる場合があります。 Microsoft 365 管理センターで、Power BI サブスクリプションを追加できるかどうかを確認できます (グローバル管理者または課金管理者ロールのメンバーシップが必要)。

1. [Microsoft 365 管理センター](https://admin.microsoft.com/AdminPortal/Home#/homepage)に移動します。

1. 左側のメニューで **[課金]** を開きます。

    * **[サブスクリプション]** が表示される場合、Microsoft からサービスを直接取得することや、Power BI を提供する別のパートナーに問い合わせることができます。

        ![[課金] の [サブスクリプション]](media/service-admin-syndication-partner/billingsub.png)

    * **[サブスクリプション]** が表示されない場合は、直接 Microsoft から、または別のパートナーから購入することはできません。

パートナーが Power BI を提供しておらず、直接 Microsoft から、または別のパートナーから購入できない場合は、無料試用版へのサインアップを検討してください。

## <a name="sign-up-for-a-free-trial"></a>無料試用版にサインアップする

Power BI の無料試用版にサインアップできます。 試用期間の最後に Power BI Pro を購入しない場合でも、Power BI の機能の多くが提供される無料ライセンスがあります。 詳細については、「[個人として Power BI にサインアップする](../fundamentals/service-self-service-signup-for-power-bi.md)」を参照してください。

### <a name="enable-ad-hoc-subscriptions"></a>アドホック サブスクリプションを有効にする

既定では、個別のサインアップ (アドホック サブスクリプションとも呼ばれます) は無効になっています。 この場合、サインアップしようとすると次のメッセージが表示されます。*Your IT department has turned off signup for Microsoft Power BI. (あなたの所属する組織の IT 部門により、Microsoft Power BI のサインアップが無効にされています。)*

![サインアップ不可画像](media/service-admin-syndication-partner/sorry.png)

アドホック サブスクリプションを有効にするには、パートナーに連絡して、有効にするよう依頼することができます。 テナント管理者の場合、Azure Active Directory PowerShell コマンドを使用する方法がわかっていれば、自分でアドホック サブスクリプションを有効にできます。 [Graph 用 Azure Active Directory PowerShell](/powershell/azure/active-directory/install-adv2/)

1. Microsoft 365 の資格情報を使用して Azure Active Directory にサインインします。 次のスクリプトの 1 行目では、ユーザーに資格証明が要求されます。 2 行目で、Azure Active Directory に接続します。

    ```powershell
    $msolcred = get-credential
    connect-msolservice -credential $msolcred
    ```

    ![資格情報を入力する](media/service-admin-syndication-partner/aad-signin.png)

1. サインインした後、次のコマンドを実行して、`AllowAdHocSubscriptions` の現在の設定を確認します。

    ```powershell
    Get-MsolCompanyInformation
    ```

1. 次のコマンドを実行して、無料サインアップを有効にします。

    ```powershell
    Set-MsolCompanySettings -AllowAdHocSubscriptions $true
    ```

## <a name="next-steps"></a>次の手順

[組織での Power BI のライセンス](service-admin-licensing-organization.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。