---
title: Power BI ユーザー ライセンスの表示と管理
description: 管理者が組織内の Power BI ユーザー ライセンスを表示および管理する方法について説明します。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 16cd210955ff358bd6bf64346b4e3169648bab8d
ms.sourcegitcommit: 3f864ec22f99ca9e25cda3a5abda8a5f69ccfa8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2020
ms.locfileid: "84160021"
---
# <a name="view-and-manage-power-bi-user-licenses"></a>Power BI ユーザー ライセンスの表示と管理

この記事では、管理者が Microsoft 365 管理センターまたは Azure portal を使用して、Power BI サービスのユーザー ライセンスを表示および管理する方法について説明しています。

> [!NOTE]
>
>ユーザーには、Power BI Free と Power BI Pro ライセンスの両方を割り当てることができます。 これは、ユーザーが無料ライセンスにサインアップした後で Power BI Pro ライセンスが割り当てられた場合に起こる場合があります。 ここでは、最上位のライセンス レベルを有効にします。
>

## <a name="view-your-subscriptions"></a>サブスクリプションを表示する

組織が持っている Power BI サブスクリプションを確認するには、次の手順に従います。

1. [Microsoft 365 管理センター](https://admin.microsoft.com)にサインインします。
2. ナビゲーション メニューで、 **[課金]**  >  **[製品とサービス]** を選択します。

アクティブな Power BI サブスクリプションが、ご利用中のその他のサブスクリプションと共に一覧表示されます。 次に示すように、想定されていない Power BI Free のサブスクリプションが表示される場合があります。

  ![ユーザーがアクティブ化した Power BI (無料) サブスクリプション](media/service-admin-manage-licenses/power-bi-free-user-activated.png)

この種類のサブスクリプションは、ユーザーがセルフサービス サインアップを利用するときに自動的に作成されます。 詳細については、「[組織内の Power BI](https://docs.microsoft.com/microsoft-365/admin/misc/power-bi-in-your-organization?view=o365-worldwide)」を参照してください。

## <a name="manage-user-licenses-in-microsoft-365"></a>Microsoft 365 でライセンスを管理する

Microsoft 365 管理センターを使用してユーザー ライセンスを管理するには、「[ビジネス サブスクリプションと課金ドキュメント](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide)」を参照してください。

## <a name="manage-user-licenses-in-azure-portal"></a>Azure portal でライセンスを管理する

次の手順に従い、Azure portal を使用して、Power BI ライセンスの表示と割り当てを行います。

1. [Azure portal](https://portal.azure.com) にサインインします。

2. **Azure Active Directory** を検索して選択します。

3. Azure Active Directory リソース メニューの **[管理]** の下にある **[ライセンス]** を選択します。

4. リソース メニューから **[すべての製品]** を選択します。次に、Power BI ライセンスの種類を選択して、ライセンス ユーザーの一覧を表示します。

5. ライセンスを割り当てるには、コマンド バーで、 **[+ 割り当て]** を選択します。 **[ライセンスの割り当て]** ページでユーザーを選択します。次に、 **[割り当てオプション]** を選択して、選択したユーザー アカウントの Power BI ライセンスを有効にします。

6. ライセンスを削除するには、ユーザー名の横のチェックボックスを選択した後、 **[ライセンスを削除する]** を選択します。

## <a name="next-steps"></a>次の手順

- [Power BI Pro を購入する](service-admin-purchasing-power-bi-pro.md)
- [組織向けのライセンス](service-admin-licensing-organization.md)
