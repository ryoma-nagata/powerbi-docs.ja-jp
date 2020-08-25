---
title: Power BI でカスタマー マネージド キーを使用する
description: Power BI でカスタマー マネージド キーを使用する方法について学習します。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: 8d13cc7a24486fada7f8d428ba52abeaa49d2518
ms.sourcegitcommit: b60063c49ac39f8b28c448908ecbb44b54326335
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/12/2020
ms.locfileid: "88160934"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>Power BI でカスタマー マネージド キーを使用する

Power BI では、保存データと処理中のデータが暗号化されます。 既定では、Power BI で Microsoft マネージド キーを使用してデータを暗号化します。 組織は、レポート イメージから Premium 容量にインポートされたデータセットまで、Power BI 全体で保存時のユーザー コンテンツの暗号化に独自のキーを使用することを選択できます。 

## <a name="why-use-customer-managed-keys"></a>カスタマー マネージド キーを使用する理由
組織は Power BI カスタマー マネージド キー (CMK) を使用して、クラウド サービス プロバイダー (この場合は Microsoft) と共に保存データの暗号化に関するコンプライアンス要件を満たすことができます。 CMK を使用すると、組織は提供および管理するキーを使用して Power BI ユーザーコンテンツを暗号化できます。 カスタマー マネージド キーを失効させると、1 時間以内に Power BI 内のユーザーのコンテンツを、Microsoft を含む全員が読み取ることができなくなります。 BYOK オファリングと比較して、CMK は、Power BI Premium 容量外のユーザー コンテンツも対象としており、より厳密なキャッシュ ポリシーが適用されます。既定ではすべての容量に対して BYOK が有効になります。 
 
## <a name="how-to-use-customer-managed-keys"></a>カスタマー マネージド キーを使用する方法
Power BI カスタマー マネージド キーをオプトインするには、組織がサイズ要件を満たしている必要があります。 組織のグローバル管理者は、Microsoft にサポート リクエストを送信するか、組織の Microsoft アカウント マネージャーに連絡してプロセスの詳細を確認する必要があります。  


## <a name="next-steps"></a>次のステップ

次のリンクには、カスタマー マネージド キーに役立つ可能性がある情報が用意されています。

* [Power BI で独自の暗号化キーを使用する](service-encryption-byok.md)
* [Power BI Premium の Multi-Geo のサポートを構成する](service-admin-premium-multi-geo.md)
* [容量はどのように機能するのか](service-premium-what-is.md#how-capacities-function)
* [増分更新](service-premium-incremental-refresh.md)。
