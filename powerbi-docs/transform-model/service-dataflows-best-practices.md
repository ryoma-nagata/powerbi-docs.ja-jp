---
title: Power BI データフローのベスト プラクティス
description: Power BI データフローのベスト プラクティス
author: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: d4b23039d8516375e98233254c92b2f7bbeb648d
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "90861615"
---
# <a name="dataflows-best-practice"></a>データフローのベスト プラクティス

この記事では、Power BI でのデータフローの設計に関するベスト プラクティスについて説明します。 このガイダンスを使用して、データフローを作成し、独自のデータフローにこれらのプラクティスを適用する方法を学習できます。

> [!NOTE]
> この記事に記載されている推奨事項はガイドラインです。 この記事の各ベスト プラクティスについて、このガイダンスから外れることに対する正当な理由が存在する可能性があります。 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>強化されたコンピューティング エンジンを使用するにはインジェストと変換を分割する

データフローを作成するとき、1 つのデータフローを作成して、すべてのエンティティ、変換、結合、拡張機能を 1 つの場所にまとめたくなることがあります。 データセットが小さければ、1 つのデータフローでも効果的な場合があります。 しかし、扱うデータの量が多くなると、結合や特定の変換を実行で、スロットルやメモリの制限が発生することがあります。 これらの問題に対処するため、より大きなデータ ボリュームにスケーリングする Power BI Premium ユーザー向けに強化されたエンジンがリリースされています。 強化されたコンピューティング エンジンは、リンクされたエンティティまたは計算されたエンティティに対してのみ機能するため、インジェスト用に個別のデータフローを作成し、すべての複雑なマージと変換を実行するためにリンクされたデータフローを作成すると、強化されたエンジンを活用できます。

データフローの分割は、更新に関する問題の診断とデバッグにも役立ちます。特に、スロットリング制限があるソースを操作する場合に有効です。

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>強化されたコンピューティング エンジンを使用できるアクションを実行する

他の種類の変換を実行する前に、計算されたエンティティで結合とフィルター変換を最初に実行することで、強化されたコンピューティング エンジンを利用します。

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>SharePoint に接続するときにデータフローを分割する

SharePoint を使用して複数のファイルに接続するときに、散発的な障害が発生することがあります。 SharePoint では、信頼性と応答性が維持されるように要求が調整されます。 その結果、SharePoint から Excel ファイルに接続するときに、1 つのデータフローですべてのファイルをダウンロードすることになる場合があります。 20 個を超える多数のファイルをダウンロードする場合は、2 つ以上のデータフローを作成して、更新の負荷を分割し、SharePoint の調整を克服します。

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>同じワークスペース内でリンクされたエンティティの更新がスケジュールされないようにする

リンクされたエンティティが含まれるデータフローから定期的にロックアウトされる場合は、同じワークスペース内の対応する依存データフローがデータフローの更新中にロックされることの結果である可能性があります。 そのようなロックではトランザクションの精度が提供され、両方のデータフローが正常に更新されることが保証されますが、編集がブロックすることもあります。 

リンクされたデータフローに対して個別のスケジュールを設定した場合、データフローが不必要に更新され、データフローの編集がブロックされる可能性があります。 この問題を回避するには、次の 2 つの推奨事項があります。 

* ソース データフローと同じワークスペース内のリンクされたデータフローに対して、更新スケジュールを設定しないようにします
* 更新スケジュールを個別に構成し、ロック動作を回避したい場合は、データフローを別のワークスペースに分割します。

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>インジェスト用と変換用に別のワークスペースを作成する

基になるソース システムの生データへのアクセスを許可することなく、多くのユーザーが基になるデータフロー データにアクセスできるようにするには、共有する必要があるすべてのデータが含まれるワークスペースを別に作成して、アクセス許可を割り当てます。 個々のデータフローのアクセス許可は、現在サポートされていません。

### <a name="ensure-capacity-is-in-the-same-region"></a>容量が同じリージョンに含まれるようにする

現在、データフローでは、複数の geo リージョンはサポートされていません。 Premium 容量は、Power BI テナントと同じリージョンに存在する必要があります。

### <a name="separate-on-premises-sources-from-cloud-sources"></a>クラウド ソースからオンプレミス ソースを分離する

前述のベスト プラクティスに加えて、オンプレミス、クラウド、SQL Server、Spark、Dynamics などのソースの種類ごとに、個別のデータフローを作成することができます。 データ ソースの種類ごとにデータフローを分けることを強くお勧めします。 そのようにソースの種類ごとに分離すると、トラブルシューティングが容易になり、データフローを更新するときの内部制限が回避されます。

### <a name="separate-dataflows-into-a-separate-capacity"></a>データフローを個別の容量に分割する

容量でのメモリ制限のため、スロットリング制限や、データフロー障害がたびたび発生する場合は、データフローを分離するか、Premium 容量をスケールアップしてメモリを増設することを検討してください。

## <a name="next-steps"></a>次の手順

この記事では、データフローに関するベスト プラクティスについて説明しました。 データフローの詳細については、以下の記事も役に立ちます。

* [データフローを使用したセルフサービスのデータ作成](service-dataflows-overview.md)
* [Power BI でのデータフローの作成と使用](service-dataflows-create-use.md)
* [Power BI Premium での計算されたエンティティの使用](service-dataflows-computed-entities-premium.md)
* [オンプレミス データ ソースでのデータフローの使用](service-dataflows-on-premises-gateways.md)

CDM による開発とチュートリアル リソースについて詳しくは、次をご覧ください。
* [Common Data Model の概要](/powerapps/common-data-model/overview)
* [CDM フォルダー](/common-data-model/data-lake)
* [CDM モデル ファイル定義](/common-data-model/model-json)


Power Query とスケジュールされた更新について詳しくは、次の記事をご覧ください。
* [Power BI Desktop でのクエリの概要](desktop-query-overview.md)
* [スケジュールされた更新の構成](../connect-data/refresh-scheduled-refresh.md)