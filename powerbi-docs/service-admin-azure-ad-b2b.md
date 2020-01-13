---
title: Azure AD B2B で外部ゲスト ユーザーにコンテンツを配布する
description: Power BI と Azure Active Directory Business-to-Business(Azure AD B2B) との統合により、組織外のゲスト ユーザーに Power BI コンテンツを安全に配布できるようになりました。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 22328ddd6be697f658301516d05971cdcee0d260
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223889"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Azure AD B2B で外部ゲスト ユーザーに Power BI コンテンツを配布する

Power BI と Azure Active Directory Business-to-Business(Azure AD B2B) との統合により、内部データに対する制御を引き続き維持しながら、組織外のゲスト ユーザーに Power BI コンテンツを安全に配布できるようになりました。 さらに、組織内のコンテンツの編集と管理を組織外のゲスト ユーザーに許可できます。

この記事では、Power BI での B2B Azure AD の基本的な概要を示します。 詳細については、「[Azure Active Directory B2B を使用して外部ゲスト ユーザーに Power BI コンテンツを配布する](whitepaper-azure-b2b-power-bi.md)」を参照してください。

## <a name="enable-access"></a>アクセスを有効にする

ゲスト ユーザーを招待する前に、Power BI 管理ポータル内で [[外部ユーザーとコンテンツを共有する]](service-admin-portal.md#export-and-sharing-settings) 機能を有効にします。

[[外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する]](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) 機能を使用することもできます。 これにより、組織の Power BI の参照など、ワークスペース内のコンテンツを参照および作成できるゲスト ユーザーを選択できます。

## <a name="who-can-you-invite"></a>招待できるユーザー

メール アドレスを使用しているゲスト ユーザーを招待できます。gmail.com、outlook.com、hotmail.com などの個人アカウントも含めて、ほとんどのメール アドレスに対応しています。 Azure AD B2B では、これらのアドレスは "*ソーシャル ID*" と呼ばれます。

[米国政府向け Power BI](service-govus-overview.md) など、政府機関向けクラウドに関連付けられているユーザーを招待することはできません。

## <a name="invite-guest-users"></a>ゲスト ユーザーを招待する

ゲスト ユーザーの招待が必要なのは、初めて自分の組織に招待するときだけです。 ユーザーを招待する方法には、計画的な招待とアドホック招待の 2 種類があります。

### <a name="planned-invites"></a>計画的な招待

招待するユーザーがわかっている場合は、計画的な招待を使用します。 Azure portal または PowerShell を使用して、招待を送信することができます。 ユーザーを招待するには、テナント管理者である必要があります。

Azure portal で招待を送信するには、次の手順のようにします。

1. [Azure portal](https://portal.azure.com) で、 **[Azure Active Directory]** を選択します。

1. **[管理]** で、 **[ユーザー]**  >  **[すべてのユーザー]**  >  **[新しいゲスト ユーザー]** を選択します。

    ![[新しいゲスト ユーザー] オプションが強調された Azure portal のスクリーン ショット。](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. **メール アドレス**と**個人的なメッセージ**を入力します。

    ![Azure AD Portal の [新しいゲスト ユーザー] ダイアログのスクリーン ショット。](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. **[招待]** を選びます。

複数のゲスト ユーザーを招待するには、PowerShell を使用します。 詳しくは、「[Azure Active Directory B2B コラボレーション コードと PowerShell サンプル](/azure/active-directory/b2b/code-samples/)」をご覧ください。

ゲスト ユーザーは、受信した招待メール内で **[開始]** を選択する必要があります。 その操作により、ゲスト ユーザーはテナントに追加されます。

![ゲスト ユーザー宛ての招待メールのスクリーンショット。](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>アドホック招待

任意の時点で外部ユーザーを招待するには、共有 UI を使ってダッシュボードやレポートに、またはアクセス ページを使ってアプリに、それらの外部ユーザーを追加します。 アプリを使うよう外部ユーザーを招待するときに行うことの例を次に示します。

![Power BI 内のアプリのアクセス リストに追加される外部ユーザーのスクリーンショット。](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

ゲスト ユーザーには、アプリをそのゲスト ユーザーと共有したことを示す電子メールが届きます。

![ゲスト ユーザーと共有されたアプリに関する電子メールのスクリーンショット](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

ゲスト ユーザーは、自分の所属する組織の電子メール アドレスでサインインする必要があります。 サインイン後、招待を受け入れるよう求められます。 サインイン後、アプリがゲスト ユーザーに対して開かれます。 アプリに戻るには、リンクをブックマークするか、メールを保存します。

## <a name="licensing"></a>ライセンス

ゲスト ユーザーは、共有されているコンテンツを表示するために、適切なライセンスが必要になります。 ユーザーが適切なライセンスを持っていることを確認するには、Power BI Premium の使用、Power BI Pro ライセンスの割り当て、ゲストの Power BI Pro ライセンスの使用の、3 つの方法があります。

[[外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する]](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) 機能を使用する場合、ワークスペースにコンテンツを投稿したり他のユーザーとコンテンツを共有したりするゲスト ユーザーには、Power BI Pro ライセンスが必要になります。

### <a name="use-power-bi-premium"></a>Power BI Premium を使用する

[Power BI Premium 容量](service-premium-what-is.md)にワークスペースを割り当てると、ゲスト ユーザーは Power BI Pro ライセンスなしでアプリを使用できるようになります。 Power BI Premium では、高いリフレッシュ レート、専用の容量、大規模なモデル サイズなどの他の機能をアプリで活用することもできます。

![Power BI Premium でのゲスト ユーザー エクスペリエンスのダイアグラム。](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>ゲスト ユーザーに Power BI Pro ライセンスを割り当てる

テナント内で Power BI Pro ライセンスをゲスト ユーザーに割り当てると、そのゲスト ユーザーはテナント内のコンテンツを表示できるようになります。 ライセンスの割り当ての詳細については、「[[ライセンス] ページでユーザーにライセンスを割り当てる](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page)」を参照してください。 ゲスト ユーザーに Pro ライセンスを割り当てる前に、Microsoft アカウントの担当者に連絡して、Microsoft との契約条件に準拠していることを確認してください。

![テナントから Pro ライセンスを割り当てるゲスト ユーザー エクスペリエンスのダイアグラム。](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>ゲスト ユーザーが独自の Power BI Pro ライセンスを使用する

ゲスト ユーザーは、そのテナント内で Power BI Pro ライセンスに既に割り当てられています。

![独自のライセンスを持ち込む場合のゲスト ユーザー エクスペリエンスのダイアグラム。](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>コンテンツを編集および管理できるゲスト ユーザー

[[外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する]](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) を使用すると、指定したゲスト ユーザーが組織の Power BI にアクセスできるようになります。 アクセス許可がある任意のコンテンツを表示できます。 これらのユーザーは、ホームにアクセスしたり、ワークスペースを参照したり、アプリをインストールしたり、自分がアクセス リストのどこに載っているかを確認したり、ワークスペースにコンテンツを投稿することができます。 新しいワークスペース エクスペリエンスを使用するワークスペースを作成したり、その管理者になったりすることができます。 いくつかの制限が適用されます。 「考慮事項と制限事項」のセクションでは、これらの制限事項が一覧表示されています。
 
これらのユーザーが Power BI にサインインできるよう、テナントの URL を提供します。 テナントの URL を見つけるには、次の手順に従います。

1. Power BI サービスの上部のメニューで、ヘルプ **[?]** を選択して、 **[Power BI について]** を選択します。

2. **[テナントの URL]** の横にある値を見つけます。 この値は、ゲスト ユーザーと共有できるテナントの URL です。

    ![ゲスト ユーザーのテナントの URL が強調された [Power BI について] ダイアログのスクリーンショット。](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

* 既定では、外部の Azure AD B2B によってゲストはコンテンツの使用のみに制限されます。 外部の Azure AD B2B ゲストは、アプリ、ダッシュボード、レポートの表示、データのエクスポート、ダッシュボードとレポートの電子メール サブスクリプションの作成ができます。 ワークスペースにアクセスしたり、独自のコンテンツを公開することはできません。 ただし、[[外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する]](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) 機能を通じてアクセス権を獲得するゲスト ユーザーに対しては、これらの制限は適用されません。

* ゲスト ユーザーを招待するためには、Power BI Pro のライセンスが必要です。 Pro 試用版のユーザーが Power BI にゲスト ユーザーを招待することはできません。

* [[外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する]](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) 機能を通じて有効にされたゲスト ユーザーには、一部のエクスペリエンスが使用可能になりません。 これらのユーザーがレポートを更新または発行するには、[データの取得] などの Power BI サービスの Web UI を使用して、Power BI Desktop ファイルをアップロードする必要があります。  次のエクスペリエンスはサポートされていません。
    * Power BI Desktop から Power BI サービスに直接発行することはできません。
    * ゲスト ユーザーは、Power BI Desktop を使用して Power BI サービス内のサービス データセットに接続することができません
    * Office 365 グループに関連付けられた従来のワークスペース:
        * ゲスト ユーザーは、これらのワークスペースを作成したり、その管理者になったりすることはできません
        * ゲスト ユーザーはメンバーであってもかまいません
    * ワークスペース アクセス リストに対して、アドホック招待の送信はサポートされていません
    * ゲスト ユーザーに対して、Power BI Publisher for Excel はサポートされていません
    * ゲスト ユーザーは、Power BI Gateway をインストールして組織に接続することができません
    * ゲスト ユーザーは、組織全体に発行されるアプリをインストールできません
    * ゲスト ユーザーは組織のコンテンツ パックを使用、作成、更新、またはインストールできません
    * ゲスト ユーザーは [Excel で分析] を使用できません
    * ゲスト ユーザーはコメント時に @mentioned の対象になりません
    * ゲスト ユーザーはサブスクリプションを使用できません
    * この機能を使用するゲスト ユーザーには、職場または学校のアカウントが必要です。 
    
* 個人用アカウントを使用するゲスト ユーザーの場合は、サインインの制限により、さらに多くの制限事項が発生します。
    * Web ブラウザーを通じて Power BI サービスの利用を体験することができます。
    * Power BI Mobile アプリを使用することはできません。
    * 職場または学校アカウントが要求される資格情報を指定するためのサインインができません。

* 現在、この機能は Power BI SharePoint Online レポート Web パーツでは使用できません。

* Active Directory には、全体的な組織内で外部ゲスト ユーザーが実行できる内容を制限できる設定が存在します。 これは Power BI 環境にも適用されます。 これらの設定については、次のドキュメントで説明されています。
    * [外部コラボレーションの設定を管理する](/azure/active-directory/b2b/delegate-invitations#configure-b2b-external-collaboration-settings)
    * [特定の組織からの B2B ユーザーへの招待を許可またはブロックする](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>次の手順

行レベル セキュリティのしくみなど、詳細については、ホワイトペーパー「[Distribute Power BI content to external guest users using Azure AD B2B (Azure AD B2B を使用して外部ゲスト ユーザーに Power BI のコンテンツを配布する)](https://aka.ms/powerbi-b2b-whitepaper)」をご覧ください。

Azure AD B2B について詳しくは、「[Azure Active Directory B2B コラボレーションとは](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/)」をご覧ください。
