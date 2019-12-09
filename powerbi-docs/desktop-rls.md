---
title: Power BI Desktop での行レベルのセキュリティ (RLS) を理解する
description: Power BI Desktop 内にインポートしたデータセットと DirectQuery の行レベルのセキュリティを構成する方法。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.custom: ''
ms.date: 12/05/2019
LocalizationGroup: Create reports
ms.openlocfilehash: abbd8f34f42bdcfdca6e65df58c78bf394f00d91
ms.sourcegitcommit: 9a265d8117cc202f5f700286b5ff42a631aacdb4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2019
ms.locfileid: "74882813"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>Power BI Desktop での行レベルのセキュリティ (RLS)

Power BI Desktop で行レベル セキュリティ (RLS) を使用すると、特定のユーザーのデータ アクセスを制限できます。 フィルターは、行レベルでデータを制限します。 役割内でフィルターを定義できます。

Power BI Desktop で Power BI にインポートされたデータ モデルの RLS を構成できます。 SQL Server などの [DirectQuery](desktop-use-directquery.md) を使用しているデータセットに RLS を構成することもできます。 これまで、RLS を実装できるのは、Power BI の外部にあるオンプレミスの Analysis Services モデル内だけでした。 Analysis Services のライブ接続では、オンプレミスのモデルに行レベルのセキュリティを構成します。 このセキュリティ オプションは、ライブ接続データセットには表示されません。

> [!IMPORTANT]
> Power BI サービス内で役割とルールを定義した場合は、Power BI Desktop でこれらの役割を再作成し、サービスにレポートを公開する必要があります。

Power BI サービス内の RLS のオプションについては、[こちら](service-admin-rls.md)を参照してください。

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>次の手順

[Power BI サービスでの行レベルのセキュリティ (RLS)](service-admin-rls.md)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。