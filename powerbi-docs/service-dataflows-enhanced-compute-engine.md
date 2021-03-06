---
title: データフローで強化されたコンピューティング エンジンを使用する
description: データフローを使用して、Power BI Premium で拡張コンピューティング エンジンを使用する方法について説明します
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 1d2bd150d33d95f2ec8759f9e876b3920eede3b6
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75840072"
---
# <a name="the-enhanced-compute-engine"></a>拡張コンピューティング エンジン

Power BI の拡張コンピューティング エンジンにより、Power BI Premium サブスクライバーは自身の容量を使用してデータフローの使用を最適化できます。 拡張コンピューティング エンジンを使用すると、次のような利点があります。

* 計算対象エンティティに対する、実行時間の長い ETL ステップ (*joins*、*distinct*、*filters*、*group by* の実行など) に必要な更新時間の大幅な短縮
* エンティティに対して DirectQuery クエリの実行 (2020 年 2 月)

以降のセクションでは、拡張コンピューティング エンジンを有効にする方法について説明し、一般的な質問に回答します。


## <a name="using-the-enhanced-compute-engine"></a>拡張コンピューティング エンジンの使用

拡張コンピューティング エンジンは、Power BI サービスの **[容量の設定]** ページの **[データフロー]** セクションで有効にします。 既定では、拡張コンピューティング エンジンは **[オフ]** になっています。 このオプションをオンにするには、次の図に示すように、トグルを **[オン]** に切り替えて、設定を保存します。 

![拡張コンピューティング エンジンをオンにする](media/service-dataflows-enhanced-compute-engine/enhanced-compute-engine-01.png)

拡張コンピューティング エンジンをオンにしたら、データフローに戻ります。同じ容量の既存のリンクされたエンティティから作成されたデータフローに対して、複雑な演算 (*joins* や *group by* などの演算) を実行する計算対象エンティティのパフォーマンスが向上しているはずです。 

コンピューティング エンジンを最大限に活用するには、次のように ETL ステージを 2 つの異なるデータフローに分割する必要があります。

* **データフロー 1**: このデータフローでは、データ ソースから必要なすべてを取り込み、それをデータフロー 2 に配置するだけです。
* **データフロー 2**: この 2 つ目のデータフローですべての ETL 操作が実行されますが、データフロー 1 が同じ容量にあり、それを参照していることを確認します。 また、コンピューティング エンジンが確実に使用されるように、他の演算を実行する前に、フォールドできる演算 (filter、group by、distinct、join) を確実に実行します。

## <a name="common-questions-and-answers"></a>一般的な質問と回答

**質問:** 拡張コンピューティング エンジンを有効にしましたが、更新に時間がかかります。 なぜでしょうか。

**回答:** 拡張コンピューティング エンジンを有効にすると更新時間が遅くなる原因には、2 つの理由が考えられます。

 - 拡張コンピューティング エンジンを有効にすると、エンジンが適切に機能するためにある程度のメモリが必要になります。 そのため、更新の実行に使用できるメモリが減り、更新がキューに格納される可能性が高くなります。これにより、同時に更新できるデータフローの数が減少します。 これに対処するには、拡張コンピューティングを有効にするときに、データフローに割り当てられているメモリを増やして、同時実行のデータフロー更新に使用できるメモリが変わらないようにします。

 - 更新が遅くなるもう 1 つの理由は、コンピューティング エンジンが既存のエンティティに対してしか機能しないことです。データフローがデータフローではないデータ ソースを参照している場合は、改善が見られません。 一部のビッグ データ シナリオでは、データを拡張コンピューティング エンジンに渡す必要があるため、データ ソースからの最初の読み取りが遅くなり、パフォーマンスが向上しません。  

**質問:** 拡張コンピューティング エンジンのトグルが表示されません。 なぜでしょうか。

**回答:** 拡張コンピューティング エンジンは、世界中のリージョンに段階的にリリースされています。 2020 年末までに、すべてのリージョンがサポートされる予定です。

**質問:** コンピューティング エンジンでサポートされているデータ型は何ですか?

**回答:** 拡張コンピューティング エンジンとデータフローでは、現在、次のデータ型がサポートされています。 データフローで次のデータ型のいずれかが使用されていない場合は、更新時にエラーが発生します。

* 日付/時刻
* 10 進数
* テキスト
* 整数
* 日付/時刻/タイムゾーン
* True/False
* Date
* 時刻

## <a name="next-steps"></a>次の手順

この記事では、データフロー用の拡張コンピューティング エンジンの使用に関する情報を提供しました。 次の記事も役に立ちます。

* [データフローを使用したセルフサービスのデータ作成](service-dataflows-overview.md)
* [Power BI でのデータフローの作成と使用](service-dataflows-create-use.md)
* [Power BI Premium での計算されたエンティティの使用](service-dataflows-computed-entities-premium.md)
* [Power BI データフロー用の開発者向けリソース](service-dataflows-developer-resources.md)

Power Query とスケジュールされた更新について詳しくは、次の記事をご覧ください。
* [Power BI Desktop でのクエリの概要](desktop-query-overview.md)
* [スケジュールされた更新の構成](refresh-scheduled-refresh.md)

Common Data Model について詳しくは、次の概要記事をご覧ください。
* [Common Data Model の概要](https://docs.microsoft.com/powerapps/common-data-model/overview)

