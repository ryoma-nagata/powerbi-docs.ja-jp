---
title: オンプレミス データ ソースでのデータフローの使用
description: データフローでオンプレミスのデータを使用する方法を学びます
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/08/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: efd110ad73b1bd72813d418a1f641613c88dc0d5
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "75762579"
---
# <a name="using-dataflows-with-on-premises-data-sources"></a>オンプレミス データ ソースでのデータフローの使用

**データフロー**を使用すると、さまざまなソースからデータのコレクションを作成し、データをクリーンアップし、データを変換し、Power BI ストレージにデータを読み込むことができます。 データフローを作成するとき、オンプレミスのデータ ソースを使用したい場合があります。 この記事では、データフローの作成に関する要件と、それらの接続を有効にするために必要な**エンタープライズ ゲートウェイ**の構成方法を明らかにします。

![データフローとゲートウェイ](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="configuring-an-enterprise-gateway-for-use-with-dataflows"></a>データフローで使用するためのエンタープライズ ゲートウェイの構成

ゲートウェイを使用してデータフローを作成する場合、そのユーザーはエンタープライズ ゲートウェイの管理者である必要があります。または、ユーザーと使用する予定のデータソースをその管理者が共有している必要があります。 


> [!NOTE]
> データフローは、エンタープライズ ゲートウェイを使用した場合にのみサポートされます。

## <a name="using-an-on-premises-data-source-in-a-dataflow"></a>データフローでのオンプレミス データ ソースの使用

データフローを作成するときに、次の図のように、データ ソースの一覧からオンプレミスのデータ ソースを選択します。

![オンプレミスのデータ ソースを選択する](media/service-dataflows-onpremises-gateways/onpremises-gateways_02a.png)

選択すると、オンプレミスのデータへのアクセスに使用するエンタープライズ ゲートウェイに関する接続の詳細を指定するように求められます。 ゲートウェイ自体を選択し、選択したゲートウェイの資格情報を指定する必要があります。

![接続の詳細を指定する](media/service-dataflows-onpremises-gateways/onpremises-gateways_03.png)

## <a name="monitoring-your-gateway"></a>ゲートウェイの監視

ゲートウェイでデータセットを監視するのと同じ方法で、エンタープライズ ゲートウェイでデータフローを監視できます。

次の図のように、Power BI のデータフロー設定画面では、データフローのゲートウェイの状態を監視し、データフローにゲートウェイを割り当てることができます。

![ゲートウェイの監視](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="changing-a-gateway"></a>ゲートウェイの変更

特定のデータフローに使用されるエンタープライズ ゲートウェイを、2 つの方法で変更することができます。

1. **作成ツールから** – データフロー作成ツールを使用して、すべてのクエリに割り当てられているゲートウェイを変更することができます。

    > [!NOTE]
    > データフローでは、新しいゲートウェイを使用して、必要なデータ ソースの検索または作成が試みられます。 それができない場合、必要なすべてのデータフローを選択したゲートウェイから使用できるようになるまで、ゲートウェイを変更することはできません。

2. **設定画面から** - Power BI サービスのデータフロー設定画面を使用して、割り当てられているゲートウェイを変更することができます。

エンタープライズ ゲートウェイについて詳しくは、「[オンプレミス データ ゲートウェイ](service-gateway-onprem.md)」をご覧ください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

エンタープライズ ゲートウェイとデータフローの使用に関しては、既知の制限がいくつかあります。

* 各データフローでは、1 つのゲートウェイだけを使用できます。 そのため、すべてのクエリを、同じゲートウェイを使用するように構成する必要があります。
* ゲートウェイを変更すると、データフロー全体に影響があります。
* 複数のゲートウェイが必要な場合の最善の方法は、複数のデータフロー (ゲートウェイごとに 1 つ) を作成し、計算機能またはエンティティ参照機能を使用して、データを統合することです。
* データフローは、エンタープライズ ゲートウェイを使用した場合にのみサポートされます。 個人用ゲートウェイは、ドロップダウン リストおよび設定画面で選択できません。


## <a name="next-steps"></a>次の手順

この記事では、データフロー用にオンプレミス データ ソースを使用すること、およびそのようなデータにアクセスするためにゲートウェイを使用および構成する方法について説明しました。 次の記事も役に立ちます

* [データフローを使用したセルフサービスのデータ作成](service-dataflows-overview.md)
* [Power BI でのデータフローの作成と使用](service-dataflows-create-use.md)
* [Power BI Premium での計算されたエンティティの使用](service-dataflows-computed-entities-premium.md)
* [Power BI データフロー用の開発者向けリソース](service-dataflows-developer-resources.md)

Power Query とスケジュールされた更新について詳しくは、次の記事をご覧ください。
* [Power BI Desktop でのクエリの概要](desktop-query-overview.md)
* [スケジュールされた更新の構成](refresh-scheduled-refresh.md)

Common Data Model について詳しくは、次の概要記事をご覧ください。
* [Common Data Model の概要](https://docs.microsoft.com/powerapps/common-data-model/overview)

