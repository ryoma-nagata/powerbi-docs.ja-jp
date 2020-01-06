---
title: Power BI Desktop の DirectQuery
description: Power BI Desktop の DirectQuery (ライブ接続とも呼ばれます) を使用します
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/19/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 08b739c5be01efed5abf8258540b5ab66b3b390b
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "73876061"
---
# <a name="use-directquery-in-power-bi-desktop"></a>Power BI Desktop の DirectQuery
**Power BI Desktop** を利用すれば、データ ソースに接続するとき、常にデータのコピーを **Power BI Desktop** にインポートできます。 データ ソースによっては、代替手法を利用できます。**DirectQuery** でデータ ソースに直接接続する方法です。

## <a name="supported-data-sources"></a>サポートされているデータ ソース
**DirectQuery** をサポートしているデータ ソースの詳細については、「[DirectQuery でサポートされるデータ ソース](desktop-directquery-data-sources.md)」を参照してください。

## <a name="how-to-connect-using-directquery"></a>DirectQuery を使用して接続する方法
**[データの取得]** を使用し、**DirectQuery** でサポートされているデータ ソースに接続すると、接続ウィンドウが開きます。このウィンドウで、接続方法を選択できます。  

![](media/desktop-use-directquery/directquery_2a.png)

**Import** と **DirectQuery** の選択の違いは次のようになります。

**インポート** – 選択したテーブルと列は **Power BI Desktop** にインポートされます。 視覚エフェクトを作成するか、操作するとき、**Power BI Desktop** はインポートされたデータを使用します。 初回インポートまたは最近の更新以降、変更された基礎データを確認するには、データを更新し、完全データ セットをもう一度インポートする必要があります。

**DirectQuery** – **Power BI Desktop** にデータがインポートまたはコピーされることはありません。 リレーショナル ソースの場合、選択したテーブルと列は **[フィールド]** リストに表示されます。 SAP Business Warehouse のように多次元ソースの場合、選択したキューブのディメンションとメジャーは **[フィールド]** リストに表示されます。 視覚エフェクトを作成するか、操作するとき、**Power BI Desktop** は基礎データ ソースに問い合わせるので、現在のデータが常に表示されることになります。

いくつかの制約がありますが、**DirectQuery** を利用するとき、さまざまなデータ モデリングとデータ変換を利用できます。 視覚エフェクトを作成するか、操作するとき、基礎ソースに問い合わせる必要があります。視覚エフェクトの更新に必要な時間は基礎データ ソースのパフォーマンスに依存します。 要求の処理を必要となるデータが最近要求されているとき、Power BI Desktop は最近のデータを利用し、視覚エフェクトの表示に必要な時間を短縮します。 **[ホーム]** リボンの **[更新]** を選択すると、すべての視覚エフェクトが現在のデータで更新されます。

**DirectQuery** の詳細については、「[Power BI と DirectQuery](desktop-directquery-about.md)」の記事を参照してください。 また、**DirectQuery** 使用の利点、制限、重要な考慮事項については、次のセクションを参照してください。

## <a name="benefits-of-using-directquery"></a>DirectQuery を使用する利点
**DirectQuery** を使用する場合の利点は次のとおりです。

* **DirectQuery** なら、他の方法では全データをインポートすること自体が不可能なほど大きなデータセットでも事前集計を使用して視覚化を作成できます。
* 元になるデータが変更されるとデータの更新が必要になる場合があり、レポートによっては、現在のデータを表示しなければならない場合に大きなデータの転送が必要になって、データの再インポートが不可能になることがあります。 対照的に、 **DirectQuery** レポートは常に現在のデータを使用します。
* データセットの 1 GB 制限は、**DirectQuery** には適用され*ません*。

## <a name="limitations-of-directquery"></a>DirectQuery の制限
現在、 **DirectQuery**の使用には、いくつかの制限があります。

* [複合モデル](desktop-composite-models.md)を使用しない限り、すべてのテーブルを必ず 1 つのデータベースから取得する必要があります。

* **クエリ エディター**のクエリが複雑すぎるとエラーが発生します。 エラーを解決するには、問題となるステップを**クエリ エディター**で削除するか、**DirectQuery** を使用する代わりにデータを*インポート*する必要があります。 SAP Business Warehouse のように多次元ソースの場合、**クエリ エディター**はありません。

* タイム インテリジェンス機能は **DirectQuery** では利用できません。 たとえば、データ列 (年度、四半期、月、日など) の特殊な処理は **DirectQuery** モードではサポートされていません。

* 基になるデータ ソースに送信されるクエリが許容範囲のパフォーマンスを確実に発揮できるよう、メジャー内で許可される DAX 式には制約があります。

* **DirectQuery** を使用した場合の返されるデータには 100 万行の制限があります。 この制限は **DirectQuery** を使用して返されるデータセットの作成に使用される集計や計算には影響せず、返される行のみに影響します。 たとえば、データ ソースに対して実行すクエリで 1,000 万行を集計し、その集計の結果のデータが 100 万行未満であれば、**DirectQuery** を使用して、Power BI に正確に返すことができます。 **DirectQuery** から 100 万行を超える行が返された場合、Power BI はエラーを返します。

## <a name="important-considerations-when-using-directquery"></a>DirectQuery を使用する場合の重要な考慮事項
**DirectQuery** の使用時には次の 3 点を考慮してください。

* **パフォーマンスと負荷** - **DirectQuery** 要求はすべて、ソース データベースに送信されます。そのため、ビジュアルの更新に必要な時間は、そのバックエンド ソースがクエリの結果を返す時間に依存します。 ビジュアルの場合、**DirectQuery** 使用の推奨応答時間 (要求したデータが返される時間) は 5 秒以内です。最大推奨応答時間は 30 秒です。 それ以上長くなると、レポート使用のユーザー エクスペリエンスが許容範囲外になります。 また、レポートを Power BI サービスに公開すると、数分かかるクエリはタイムアウトとなり、エラーがユーザーに送信されます。
  
  ソース データベースの負荷も、公開されたレポートを使用する Power BI ユーザーの数に基づき考慮してください。 *行レベルのセキュリティ* (RLS) を使用した場合も大きな影響があります。RLS 以外のダッシュボード タイルを複数のユーザーが共有した場合、1 件のクエリがデータベースに実行されますが、ダッシュボード タイルで RLS を使用することは、通常、タイルの更新には、*ユーザー*あたり 1 クエリ必要になることを意味します。そのため、ソースデータベースに大きな負荷がかかり、パフォーマンスに影響を与える可能性があります。
  
  Power BI では、可能な限り効率的なクエリが作成されます。 ただし、特定の状況では、生成されたクエリは十分に効率的ではなく、更新が失敗することがあります。 たとえば、生成されたクエリがバックエンド データ ソースから過度に大量の行を取得することがあります。その場合、次のエラーが発生します。
  
      The resultset of a query to external data source has exceeded
  
  このような状況は、カーディナリティが非常に高い列を含む簡単なグラフで集計オプションが *[Don’t Summarize]* (集計しない) に設定されている場合に発生します。 ビジュアルの場合、列のカーディナリティは 100 万未満にする必要があります。あるいは、適切なフィルターを適用する必要があります。
* **セキュリティ** - 既定では、公開されたレポートを利用するユーザーは全員、Power BI サービスに公開した後に入力された資格情報を利用し、バックエンド データ ソースに接続します。 これはインポートされたデータと同じ状況になります。バックエンド ソースに定義されているセキュリティ ルールに関係なく、すべてのユーザーに同じデータが表示されます。 DirectQuery ソースで実装されたユーザーごとのセキュリティが必要なお客様は、RLS を使用するか、ソースに対する Kerberos 制約付き認証を構成する必要があります。 Kerberos はすべてのソースで使用できるわけではありません。 [RLS についての詳細情報](service-admin-rls.md)。 [DirectQuery についての詳細情報](https://docs.microsoft.com/power-bi/service-gateway-sso-kerberos)。 
* **サポートされている機能** - **Power BI Desktop** の一部の機能は **DirectQuery** モードでサポートされていないか、制限があります。 また、Power BI サービスには、**DirectQuery** 使用時のデータセットで利用できない機能もあります (*クイック分析情報*など)。 そのため、**DirectQuery** を利用するかどうかを判断するとき、以上のような **DirectQuery** 利用時の機能制約を考慮する必要があります。   

## <a name="publish-to-the-power-bi-service"></a>Power BI サービスに公開する
**DirectQuery** を使用して作成したレポートを Power BI サービスに発行できます。

使用されるデータ ソースが**オンプレミス データ ゲートウェイ**を必要としていない場合 (**Azure SQL Database**、**Azure SQL Data Warehouse**、または **Redshift**)、公開したレポートを Power BI サービスに表示する前に資格情報を入力する必要があります。

資格情報を入力するには、Power BI の **[設定]** 歯車アイコンを選択し、 **[設定]** を選択します。

![](media/desktop-use-directquery/directquery_3.png)

Power BI に **[設定]** ウィンドウが表示されます。 そこから、 **[データセット]** タブを選択し、 **DirectQuery**を使用するデータセットを選択し、 **[資格情報を編集]** を選択します。

![](media/desktop-use-directquery/directquery_4.png)

資格情報を入力せずに、公開したレポートを開いたり、**DirectQuery** 接続で作成されたデータセットを調べたりすると、このようなデータ ソースでエラーが発生します。

DirectQuery を使用する **Azure SQL Database**、**Azure SQL Data Warehouse**、および **Redshift** 以外のデータ ソースについては、**オンプレミス データ ゲートウェイ**をインストールし、データ ソースを登録してデータ接続を確立する必要があります。 オンプレミス データ ゲートウェイの詳細については[こちら](https://go.microsoft.com/fwlink/p/?LinkID=627094)を参照してください。

## <a name="next-steps"></a>次の手順
**DirectQuery** について詳しくは、次のリソースをご覧ください。

* [Power BI の DirectQuery](desktop-directquery-about.md)
* [DirectQuery でサポートされるデータ ソース](desktop-directquery-data-sources.md)
* [DirectQuery と SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
* [オンプレミス データ ゲートウェイ](service-gateway-onprem.md)

