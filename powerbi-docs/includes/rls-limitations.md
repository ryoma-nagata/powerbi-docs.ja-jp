---
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 01/31/2020
ms.author: davidi
ms.openlocfilehash: b67025de5e2a70876a31fd42e22c9572403288fa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "77464429"
---
## <a name="limitations"></a>制限事項

クラウド モデルの行レベル セキュリティにおける現在の制限事項は次のようになります。

* Power BI サービスでロールおよびルールを以前に定義している場合、Power BI Desktop 内で再作成する必要があります。

* RLS は、Power BI Desktop を使用して作成されたデータセットにのみ定義できます。 Excel で作成されたデータセットに対して RLS を有効にするには、最初にファイルを Power BI Desktop (PBIX) ファイルに変換する必要があります。 [詳細については、こちらをご覧ください](../desktop-import-excel-workbooks.md)。

* Import と DirectQuery 接続のみサポートされます。 Analysis Services へのライブ接続は、オンプレミス モデルで処理されます。

## <a name="known-issues"></a>既知の問題

Power BI Desktop から既に発行されているレポートを発行しようとすると、エラー メッセージが出るという既知の問題があります。 シナリオは次のようになります。

1. Anna には Power BI サービスに発行されたデータセットが与えられており、RLS を構成しています。

1. Anna は Power BI Desktop でレポートを更新し、再発行します。

1. Anna は、エラーを受け取ります。

**回避策:** この問題が解決されるまで、Power BI サービスから Power BI Desktop ファイルを再発行します。 これを行うには、 **[データの取得]**  >  **[ファイル]** を選択します。
