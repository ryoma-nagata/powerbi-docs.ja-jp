---
title: Power BI Desktop の行レベルのセキュリティを使用してデータ アクセスを制限する
description: Power BI Desktop 内にインポートしたデータセットと DirectQuery の行レベルのセキュリティを構成する方法。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 01/31/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 89c33de2ef7319c6dcbeace0df79786128e16cd9
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83334317"
---
# <a name="restrict-data-access-with-row-level-security-rls-for-power-bi-desktop"></a>Power BI Desktop の行レベルのセキュリティを使用してデータ アクセスを制限する

Power BI Desktop で行レベル セキュリティ (RLS) を使用すると、特定のユーザーのデータ アクセスを制限できます。 フィルターは、行レベルでデータを制限します。 役割内でフィルターを定義できます。

Power BI Desktop で Power BI にインポートされたデータ モデルの RLS を構成できます。 SQL Server などの [DirectQuery](../connect-data/desktop-use-directquery.md) を使用しているデータセットに RLS を構成することもできます。 これまで、RLS を実装できるのは、Power BI の外部にあるオンプレミスの Analysis Services モデル内だけでした。 Analysis Services のライブ接続では、オンプレミスのモデルに行レベルのセキュリティを構成します。 このセキュリティ オプションは、ライブ接続データセットには表示されません。

> [!IMPORTANT]
> Power BI サービス内で役割とルールを定義した場合は、Power BI Desktop でこれらの役割を再作成し、サービスにレポートを公開する必要があります。 Power BI サービス内の RLS のオプションについては、[こちら](../admin/service-admin-rls.md)を参照してください。

[!INCLUDE [include-short-name](../includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](../includes/rls-limitations.md)]

[!INCLUDE [include-short-name](../includes/rls-faq.md)]

## <a name="next-steps"></a>次のステップ

[Power BI サービスでの行レベルのセキュリティ (RLS)](../admin/service-admin-rls.md)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。