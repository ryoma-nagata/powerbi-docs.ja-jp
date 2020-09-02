---
title: Power BI で DirectQuery とデータフローを使用する (プレビュー)
description: Power BI でデータフローに DirectQuery を使用する方法について説明します
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 3e7bb33eae8be4a0eaa7eb4d92ca165c74b14ed5
ms.sourcegitcommit: 13c4bec679313f2951f1833033316cb8176da8a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/26/2020
ms.locfileid: "88937380"
---
# <a name="use-directquery-with-dataflows-in-power-bi-preview"></a>Power BI で DirectQuery とデータフローを使用する (プレビュー)

DirectQuery を使用してデータフローに直接接続し、それによってデータをインポートせずにデータフローに直接接続することができます。 

データフローに DirectQuery を使用すると、Power BI とデータフローのプロセスに対して次の改善が可能になります。

* **個別の更新スケジュールを回避する** - DirectQuery では、データフローに直接接続するため、インポートされたデータセットを作成する必要がなくなります。 そのため、データフローに DirectQuery を使用すると、データフローとデータセット用の個別の更新スケジュールが不要になり、データの同期が保証されます。

* **データのフィルター処理** - DirectQuery は、データフロー内のデータのフィルター処理されたビューを操作する場合に便利です。 データをフィルター処理することでデータフロー内のデータの小さなサブセットを処理したい場合は、DirectQuery (およびコンピューティング エンジン) を使用してデータフローのデータをフィルター処理し、目的のフィルター処理されたサブセットを操作できます。


## <a name="using-directquery-for-dataflows"></a>データフローに対して DirectQuery を使用する

データフローに対する DirectQuery の使用は、Power BI Desktop の 2020 年 5 月バージョンから使用できるようになったプレビュー機能です。 

データフローに DirectQuery を使用するための前提条件もあります。

* データフローが Power BI Premium が有効なワークスペース内に存在する必要があります
* **コンピューティング エンジン**を有効にする必要があります。 コンピューティング エンジンの詳細については、「[拡張コンピューティング エンジン](service-dataflows-enhanced-compute-engine.md)」をご覧ください。

## <a name="enable-directquery-for-dataflows"></a>データフローに対して DirectQuery を有効にする

データフローを DirectQuery からアクセスできるようにするには、拡張コンピューティング エンジンが最適化された状態になっている必要があります。 データフローに対して DirectQuery を有効にするには、新しい **[コンピューティング エンジンの拡張設定]** オプションを **[オン]** に設定します。 次の画像は、適切に選択された設定を示しています。

![データフローに対して強化されたコンピューティング エンジンを有効にする](media/service-dataflows-directquery/dataflows-directquery-01.png)

この設定を適用したら、最適化を有効にするためにデータフローを更新してください。 


## <a name="considerations-and-limitations"></a>考慮事項と制限事項

DirectQuery とデータフローには、いくつかの既知の制限事項があります。これらについて、次の一覧で説明します。

* この機能のプレビュー期間中は、データフローに DirectQuery を使用すると一部のお客様にタイムアウトやパフォーマンス上の問題が発生する場合があります。 このような問題は、このプレビュー期間中にアクティブに対処されています。

* インポートおよび DirectQuery データ ソースがある複合または混合モデルは、現在、サポートされていません。

* 大規模なデータフローでは、視覚エフェクトを表示するときに、タイムアウトの問題が発生する可能性があります。 この機能の一般提供の一環として、この制限は削除される予定です。 一方、タイムアウトの問題が発生する大規模なデータフローでは、Import モードを使用する必要があります。

* DirectQuery を使用している場合は、データ ソースの設定で、データフロー コネクタに無効な資格情報が表示されます。 これが動作に影響することはなく、データセットは正常に機能します。 この問題は、一般提供が近づくにつれ解消されます。



## <a name="next-steps"></a>次の手順

データフローを使用する場合の詳細およびシナリオについては、以下の記事が役に立ちます。

* [データフローを使用したセルフサービスのデータ作成](service-dataflows-overview.md)
* [Power BI Premium での計算されたエンティティの使用](service-dataflows-computed-entities-premium.md)
* [オンプレミス データ ソースでのデータフローの使用](service-dataflows-on-premises-gateways.md)
* [Power BI データフロー用の開発者向けリソース](service-dataflows-developer-resources.md)
* [データフローと Azure Data Lake の統合 (プレビュー)](service-dataflows-azure-data-lake-integration.md)

Common Data Model について詳しくは、次の概要記事をご覧ください。
* [Common Data Model の概要](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Common Data Model のスキーマとエンティティの詳細について GitHub で学習する](https://github.com/Microsoft/CDM)

Power BI Desktop の関連記事:

* [Power BI Desktop から Power BI サービスのデータセットに接続する](../connect-data/desktop-report-lifecycle-datasets.md)
* [Power BI Desktop でのクエリの概要](desktop-query-overview.md)

Power BI サービスの関連記事:
* [スケジュールされた更新の構成](../connect-data/refresh-scheduled-refresh.md)
