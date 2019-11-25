---
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 09/13/2019
ms.author: mblythe
ms.openlocfilehash: c658e683e86a899d45728220dee3706a0d617f0f
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284128"
---
## <a name="limitations"></a>制限事項

クラウド モデルの行レベル セキュリティにおける現在の制限事項を次に示します。

* Power BI サービスでロールおよびルールを以前に定義している場合、Power BI Desktop 内で再作成する必要があります。

* RLS は、Power BI Desktop を使用して作成されたデータセットにのみ定義できます。 Excel で作成されたデータセットに対して RLS を有効にするには、最初にファイルを Power BI Desktop (PBIX) ファイルに変換する必要があります。 [詳細情報](../desktop-import-excel-workbooks.md)

* ETL と DirectQuery 接続のみサポートされます。 Analysis Services へのライブ接続は、オンプレミス モデルで処理されます。

## <a name="known-issues"></a>既知の問題

Power BI Desktop から既に発行されているレポートを発行しようとすると、エラー メッセージが出るという既知の問題があります。 シナリオは次のようになります。

1. Anna には Power BI サービスに発行されたデータセットが与えられており、RLS を構成しています。

1. Anna は Power BI Desktop でレポートを更新し、再発行します。

1. Anna は、エラーを受け取ります。

**回避策:** この問題が解決されるまで、Power BI サービスから Power BI Desktop ファイルを再発行します。 これを行うには、 **[データの取得]**  >  **[ファイル]** を選択します。
