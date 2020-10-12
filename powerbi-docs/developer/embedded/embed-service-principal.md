---
title: サービス プリンシパルとアプリケーション シークレットを使用した Power BI コンテンツの埋め込み
description: Azure Active Directory アプリケーション サービス プリンシパルとアプリケーション シークレットを使用して、埋め込み分析を認証する方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 05/12/2020
ms.openlocfilehash: e9faa50cd7e2c4a1a51dfb4a72dda950cf3a396a
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/06/2020
ms.locfileid: "91746794"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>サービス プリンシパルとアプリケーション シークレットを使用した Power BI コンテンツの埋め込み

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

この記事では、"*アプリケーション ID*" と "*アプリケーション シークレット*" を使用したサービス プリンシパル認証について説明します。

>[!NOTE]
>ご利用のバックエンド サービスは、秘密キーではなく、証明書を使用してセキュリティで保護することをお勧めします。
>* [秘密キーまたは証明書を使用して Azure AD からアクセス トークンを取得する方法の詳細を説明します](/azure/architecture/multitenant-identity/client-assertion)。
>* [サービス プリンシパルと証明書を使用した Power BI コンテンツの埋め込み](embed-service-principal-certificate.md)

## <a name="method"></a>メソッド

埋め込み分析でサービス プリンシパルとアプリケーション ID を使用するには、次の手順を行います。

1. [Azure AD アプリ](/azure/active-directory/manage-apps/what-is-application-management)を作成します。

    1. Azure AD アプリのシークレットを作成します。
    
    2. アプリの "*アプリケーション ID*" と "*アプリケーション シークレット*" を取得します。

    >[!NOTE]
    >これらの手順については**手順 1** で説明します。 Azure AD アプリの作成の詳細については、[Azure AD アプリの作成](/azure/active-directory/develop/howto-create-service-principal-portal)に関するページを参照してください。

2. Azure AD セキュリティ グループを作成します。

3. Power BI サービス管理者設定を有効にします。

4. サービス プリンシパルを、ご利用のワークスペースに追加します。

5. 自分のコンテンツを埋め込みます。

> [!IMPORTANT]
> Power BI でサービス プリンシパルを使用できるようにすると、アプリケーションの AD アクセス許可は無効になります。 アプリケーションのアクセス許可はその後、Power BI 管理ポータルを介して管理されます。

## <a name="step-1---create-an-azure-ad-app"></a>手順 1 - Azure AD アプリを作成する

次のいずれかの方法を使用して、Azure AD アプリを作成します。
* [Microsoft Azure portal でアプリを作成する](https://portal.azure.com/#allservices)
* [PowerShell](/powershell/azure/create-azure-service-principal-azureps?view=azps-3.6.1) を使用してアプリを作成する

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Microsoft Azure portal での Azure AD アプリの作成

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. **[証明書とシークレット]** タブをクリックします。

     ![スクリーンショットには、Azure portal のアプリに対する [証明書とシークレット] ペインが示されています。](media/embed-service-principal/certificates-and-secrets.png)


8. **[新しいクライアント シークレット]** をクリックします

    ![新しいクライアント シークレット](media/embed-service-principal/new-client-secret.png)

9. *[クライアント シークレットの追加]* ウィンドウで、説明を入力し、クライアント シークレットの有効期限を指定し、 **[追加]** をクリックします。

10. "*クライアント シークレット*" 値をコピーして保存します。

    ![クライアント シークレットの値](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >このウィンドウから離れると、クライアント シークレットの値は非表示となり、再度表示することもコピーすることもできません。

### <a name="creating-an-azure-ad-app-using-powershell"></a>PowerShell を使用した Azure AD アプリの作成

このセクションには、[PowerShell](/powershell/azure/create-azure-service-principal-azureps?view=azps-1.1.0) を使用して新しい Azure AD アプリを作成するためのサンプル スクリプトが含まれています。

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```

## <a name="step-2---create-an-azure-ad-security-group"></a>手順 2 - Azure AD セキュリティ グループを作成する

ご利用のサービス プリンシパルには、Power BI コンテンツおよび API のいずれに対してもアクセス権がありません。 サービス プリンシパルにアクセス権を付与するには、Azure AD でセキュリティ グループを作成し、作成済みのサービス プリンシパルをそのセキュリティ グループに追加します。

Azure AD セキュリティ グループを作成するには、次の 2 つの方法があります。
* 手動 (Azure で)
* PowerShell の使用

### <a name="create-a-security-group-manually"></a>セキュリティ グループを手動で作成する

Azure セキュリティ グループを手動で作成するには、「[Azure Active Directory を使用して基本グループを作成してメンバーを追加する](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)」に記載の手順に従ってください。 

### <a name="create-a-security-group-using-powershell"></a>PowerShell を使用してセキュリティ グループを作成する

新しいセキュリティ グループを作成し、そのセキュリティ グループにアプリを追加するためのサンプル スクリプトを以下に示します。

>[!NOTE]
>組織全体に対してサービス プリンシパル アクセスを有効にする場合、この手順をスキップします。

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>手順 3 - Power BI サービス管理者設定を有効にする

Azure AD アプリから Power BI コンテンツおよび API にアクセスできるようにするには、Power BI 管理者が Power BI 管理ポータルでサービス プリンシパル アクセスを有効にする必要があります。

Azure AD で作成したセキュリティ グループを、 **[開発者向け設定]** の特定のセキュリティ グループのセクションに追加します。

>[!IMPORTANT]
>サービス プリンシパルには、それが有効にされたテナント設定へのアクセス権があります。 これには、ご利用の管理者設定に応じて、特定のセキュリティ グループまたは組織全体が含まれます。
>
>サービス プリンシパル アクセスを特定のテナント設定に限定するには、特定のセキュリティ グループへのアクセスのみを許可します。 あるいは、サービス プリンシパル専用のセキュリティ グループを作成し、それを目的のテナント設定から除外することもできます。

![管理ポータル](media/embed-service-principal/admin-portal.png)

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>手順 4 - サービス プリンシパルを、ご利用のワークスペースに追加します。

Power BI サービス内でレポート、ダッシュボード、データセットなどの Azure AD アプリのアクセス成果物を有効にするには、メンバーまたは管理者としてのサービス プリンシパル エンティティをご利用のワークスペースに追加します。

>[!NOTE]
>このセクションでは、UI の手順について説明します。 また、[グループ - グループ ユーザー API の追加](/rest/api/power-bi/groups/addgroupuser)に関するページを参照して、サービス プリンシパルをワークスペースに追加することもできます。

1. アクセスを有効にするワークスペースまでスクロールし、 **[その他]** メニューで、 **[ワークスペース アクセス]** を選択します。

    ![ワークスペースの設定](media/embed-service-principal/workspace-access.png)

2. **管理者**または**メンバー**としてのサービス プリンシパルをワークスペースに追加します。

    ![ワークスペース管理者](media/embed-service-principal/add-service-principal-in-the-UI.png)

## <a name="step-5---embed-your-content"></a>手順 5 - コンテンツを埋め込む

サンプル アプリケーション内にも、独自のアプリケーション内にも使用するコンテンツを埋め込むことができます。

* [サンプル アプリケーションを使用してコンテンツを埋め込む](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [自分のアプリケーション内にコンテンツを埋め込む](embed-sample-for-customers.md#embed-content-within-your-application)

使用するコンテンツが埋め込まれると、[運用開始](embed-sample-for-customers.md#move-to-production)の準備が整います。

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>次の手順

>[!div class="nextstepaction"]
>[アプリを登録する](register-app.md)

> [!div class="nextstepaction"]
>[顧客向けの Power BI Embedded](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Azure Active Directory でのアプリケーション オブジェクトとサービス プリンシパル オブジェクト](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[サービス プリンシパルを使用するオンプレミス データ ゲートウェイを使用した行レベルのセキュリティ](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[サービス プリンシパルと証明書を使用した Power BI コンテンツの埋め込み](embed-service-principal-certificate.md)