---
title: Power BI Desktop で集計を使用する
description: Power BI Desktop でビッグ データに対して対話型の分析を実行する
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 37cbea42d530f05df1d9f1003554680b80c5b5c3
ms.sourcegitcommit: 212fb4a46af3e434a230331f18456c6a49a408fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907951"
---
# <a name="aggregations-in-power-bi-desktop"></a>Power BI Desktop での集計

Power BI で**集計** を使用すると、以前は不可能だった方法でビッグ データを対話的に分析することが可能になります。 **集計**によって、意思決定のために大規模なデータセットをロック解除するコストを大幅に削減できます。

![Microsoft Power BI Desktop での集計](media/desktop-aggregations/aggregations_07.jpg)

**集計**を使用することの利点を次に示します。

* **ビッグ データに対するクエリのパフォーマンス**: ユーザーが Power BI レポートのビジュアルを操作するときに、DAX クエリがデータセットに送信されます。 詳細レベルで必要なリソースの一部を使用して、集計レベルでデータをキャッシュすることでクエリ速度が向上します。 それ以外の方法では不可能な方法でビッグ データのロックを解除します。
* **データ更新の最適化**: 集計レベルでデータをキャッシュすることで、キャッシュ サイズを削減し、更新時間を短縮します。 データがユーザーに使用可能になるまでの時間を短縮します。
* **分散アーキテクチャを実現**: Power BI のメモリ内キャッシュで集計クエリの処理を可能にすることで、効果的に処理します。 DirectQuery モードでデータ ソースに送信されるクエリを制限して、同時実行の制限内に収まるようにします。 到着するクエリは、データ ウェアハウスとビッグ データ システムが通常に処理できる、フィルター処理された、トランザクション レベルのクエリになります。

### <a name="table-level-storage"></a>テーブルレベルのストレージ
テーブルレベルのストレージは通常、集計機能で使用されます。 詳細については、[Power BI Desktop のストレージ モード](desktop-storage-mode.md)に関する記事をご覧ください。

### <a name="data-source-types"></a>データ ソースの種類
集計は、データ ウェアハウスやデータ マート、Hadoop ベースのビッグ データ ソースなど、ディメンション モデルを表すデータ ソースと共に使用されます。 この記事では、Power BI での一般的なモデリングの相違点を、データ ソースの種類ごとに説明します。

Power BI のインポート (非多次元) と DirectQuery のすべてのソースが集計で機能します。

## <a name="aggregations-based-on-relationships"></a>リレーションシップに基づく集計

リレーションシップに基づく**集計**は通常、ディメンション モデルで使用されます。 データ ウェアハウスおよびデータ マートをソースとする Power BI データセットは、ディメンション テーブルとファクト テーブル間のリレーションシップを持つスター/スノーフレーク スキーマと似ています。

1 つのデータ ソースからの次のモデルを検討してください。 すべてのテーブルが最初に DirectQuery を使用しているとします。 **Sales** ファクト テーブルには、数十億の行が含まれています。 **Sales** のストレージ モードをキャッシュの **[インポート]** に設定すると、かなりの量のメモリを消費し、多額の管理オーバーヘッドがかかる可能性があります。

![モデル内のテーブル](media/desktop-aggregations/aggregations_02.jpg)

代わりに、集計テーブルとして **Sales Agg** テーブルを作成します。 これは **Sales** よりも粒度が高いため、含まれる行は大幅に少なくなります。 行数は、**CustomerKey**、**DateKey**、および **ProductSubcategoryKey** でグループ化された **SalesAmount** の合計と等しくなるはずです。 数十億行ではなく、数百万行になり、はるかに管理しやすくなります。

次のディメンション テーブルは、高いビジネス価値を持つクエリに最もよく使用されるとします。 これらのテーブルは、*一対多* (または*多対一*) リレーションシップを使用して、**Sales Agg** をフィルター処理できます。

* Geography
* 顧客
* Date
* Product Subcategory
* Product Category (製品カテゴリ)

次の図に、このモデルを示します。

![モデル内の集計テーブル](media/desktop-aggregations/aggregations_03.jpg)

> [!NOTE]
> **Sales Agg** テーブルはよくあるテーブルなので、さまざまな方法で読み込める柔軟性があります。 たとえば、集計は、ソース データベースで ETL/ELT プロセスを使用して実行することも、テーブルの [M 式](/powerquery-m/power-query-m-function-reference)で実行することもできます。 集計では、[Power BI Premium での増分更新](service-premium-incremental-refresh.md)の有無にかかわらず、インポート ストレージ モードを使用できます。または DirectQuery にして[列ストア インデックス](https://docs.microsoft.com/sql/relational-databases/indexes/columnstore-indexes-overview)を使用して高速クエリ用に最適化することもできます。 この柔軟性により、ボトルネックを避けるためにクエリ負荷を分散する分散アーキテクチャが可能になります。

### <a name="storage-mode"></a>ストレージ モード 
使用している例を使って続けましょう。 クエリを高速化するため、**Sales Agg** のストレージ モードを **[インポート]** に設定します。

![ストレージ モードの設定](media/desktop-aggregations/aggregations_04.jpg)

これを行うと、関連するディメンション テーブルを **[デュアル]** ストレージ モードに設定できることを知らせる次のダイアログが表示されます。 

![[ストレージ モード] ダイアログ](media/desktop-aggregations/aggregations_05.jpg)

これらを **[デュアル]** に設定すると、関連するディメンション テーブルを、サブクエリに応じてインポートまたは DirectQuery として機能させることができます。

* **Sales Agg** テーブル (インポート) からメトリックを集計するクエリと、関連するデュアル テーブルからの groupby 属性は、メモリ内キャッシュから返すことができます。
* **Sales** テーブル (DirectQuery) 内でメトリックを集計するクエリと、関連するデュアル テーブルからの groupby 属性は、DirectQuery モードで返すことができます。 グループ化操作を含むクエリ ロジックが、ソース データベースに渡されます。

**デュアル** ストレージ モードに関する詳細については、[ストレージ モード](desktop-storage-mode.md)に関する記事を参照してください。

### <a name="strong-vs-weak-relationships"></a>リレーションシップの強弱
リレーションシップに基づいて集計をヒットさせるには、強いリレーションシップが必要です。

強いリレーションシップには、両方のテーブルが "*単一ソース*" からのものである以下の組み合わせが含まれます。

| *多の側のテーブル | *1* 側のテーブル |
| ------------- |----------------------| 
| デュアル          | デュアル                 | 
| インポート        | インポートまたはデュアル       | 
| DirectQuery   | DirectQuery またはデュアル  | 

"*ソース間*" のリレーションシップが強いと見なされる唯一のケースは、両方のテーブルがインポートである場合です。 多対多リレーションシップは常に弱いと見なされます。

リレーションシップに依存しない "*ソース間*" の集計のヒットについては、グループ化列に基づく集計に関する以下のセクションをご覧ください。

### <a name="aggregation-tables-arent-addressable"></a>集計テーブルにアドレスを指定することはできません
データセットへの読み取り専用アクセス権を持つユーザーは、集計テーブルにクエリを実行できません。 これにより、RLS とともに使用する場合のセキュリティの問題が回避されます。 コンシューマーとクエリは、集計テーブルではなく、詳細テーブルを参照するため、集計テーブルの存在を知る必要はありません。

このため、**Sales Agg** テーブルは非表示にする必要があります。 非表示になっていない場合、[すべて適用] をクリックすると、[集計の管理] ダイアログ ボックスが非表示に設定されます。

### <a name="manage-aggregations-dialog"></a>[集計の管理] ダイアログ
次に、集計を定義します。 **Sales Agg** テーブルを右クリックして、 **[集計の管理]** コンテキスト メニューを選択します。

![[集計の管理] メニューの選択](media/desktop-aggregations/aggregations_06.jpg)

**[集計の管理]** ダイアログが表示されます。 **Sales Agg** テーブル内の各列の 1 行が表示され、ここで集計動作を指定できます。 **Sales** テーブルを参照する Power BI データセットに送信されたクエリは、**Sales Agg** テーブルへ内部的にリダイレクトされます。 データセットのコンシューマーが、**Sales Agg** テーブルの存在を知る必要はありません。

![[集計の管理] ダイアログ](media/desktop-aggregations/aggregations_07.jpg)

次のテーブルは、**Sales Agg** テーブルの集計を示しています。

![集計テーブル](media/desktop-aggregations/aggregations-table_01.jpg)

#### <a name="summarization-function"></a>概要作成関数

[概要作成] のドロップダウンでは、選択肢として次の値が提供されます。
* カウント
* GroupBy
* 最大
* 最小
* 合計
* テーブル行数のカウント

#### <a name="validations"></a>検証

ダイアログによって次の重要な検証が適用されます。

* 選択された詳細列には、カウントとテーブル行数のカウントの概要作成関数を除き、集計列と同じデータ型がある必要があります。 カウントとテーブル行数のカウントには、整数の集計列のみが提供されます。一致するデータ型は必要ありません。
* 3 つ以上のテーブルをカバーするチェーン集計は許可されていません。 たとえば、**テーブル C** を参照する集計を持つ**テーブル B** を参照する**テーブル A** に集計を設定することはできません。
* 2 つのエントリが同じ概要作成関数を使用し、同じ詳細テーブル/列を参照する重複した集計は許可されません。
* 詳細テーブルは、インポートではなく、DirectQuery にする必要があります。

このような検証のほとんどは、次の図のように、ドロップダウンの値を無効にして、ツールヒントの説明テキストを表示することで適用されます。

![ツールヒントで表示される検証](media/desktop-aggregations/aggregations_08.jpg)

### <a name="group-by-columns"></a>グループ化列

この例では、3 つの GroupBy エントリは省略可能です。これらは集計動作には影響しません (この後の画像に示されている、DISTINCTCOUNT サンプル クエリを除く)。 これらは主に読みやすくする目的のために含まれています。 これらの GroupBy エントリがなくても、集計はリレーションシップに基づいてヒットされます。 これは、この記事で後述するビッグ データの例で説明する、リレーションシップなしで集計を使用した場合の動作とは異なります。

### <a name="inactive-relationships"></a>非アクティブなリレーションシップ
非アクティブなリレーションシップによって使用されている外部キー列によるグループ化と、集計ヒットで USERELATIONSHIP 関数に依存することはサポートされていません。

### <a name="detecting-whether-aggregations-are-hit-or-missed-by-queries"></a>集計がクエリでヒットまたはミスされるかどうかを検出する

クエリがメモリ内キャッシュ (ストレージ エンジン)、または SQL Profiler を使用して (データ ソースにプッシュされる) DirectQuery から返されるかどうかを検出する方法については、[ストレージ モード](desktop-storage-mode.md)に関する記事を参照してください。 このプロセスは、集計がヒットされるかどうかを検出するためにも使用することができます。

さらに、SQL Profiler では、次の拡張イベントも提供されます。

    Query Processing\Aggregate Table Rewrite Query

次の JSON スニペットでは、集計が使用されている場合のイベントの出力例を示しています。

* **matchingResult** は、集計がサブクエリに使用されたことを示します。
* **dataRequest** は、サブクエリで使用されたグループ化列と集計列を示します。
* **mapping** は、マップ先の集計テーブル内の列を示します。

![集計が使用されたときのイベントの出力](media/desktop-aggregations/aggregations-code_01.jpg)

### <a name="query-examples"></a>クエリ例
次のクエリでは、*Date* テーブル内の列が集計をヒットできる粒度であるため、集計がヒットされます。 **SalesAmount** には、**Sum** 集計が使用されます。

![クエリの例](media/desktop-aggregations/aggregations-code_02.jpg)

次のクエリでは、集計はヒットしません。 **SalesAmount** の合計を要求しているにもかかわらず、これは **Product** テーブル内の列に対するグループ化操作を実行します。これは集計をヒットできる粒度ではありません。 モデル内のリレーションシップを観察すると、1 つの製品サブカテゴリが複数の **Product** (製品) 行を持っている場合があり、クエリでは、集計する製品が判断できません。 このケースでは、クエリによって DirectQuery に戻され、データ ソースに SQL クエリが送信されます。

![クエリの例](media/desktop-aggregations/aggregations-code_03.jpg)

集計の目的は、わかりやすい合計を求める単純な計算だけではありません。 複雑な計算にも役立ちます。 概念的には、複雑な計算は SUM、MIN、MAX、COUNT のそれぞれのサブクエリに分割され、各サブクエリは集計がヒットするかどうかを判断するために評価されます。 クエリ プランの最適化のため、このロジックはすべてのケースには当てはまりませんが、大抵のものには当てはまります。 次の例では、集計がヒットします。

![クエリの例](media/desktop-aggregations/aggregations-code_04.jpg)

COUNTROWS 関数は集計を利用できます。 **Sales** テーブル用に定義されたテーブル行数の**カウント**の集計があるため、次のクエリでは集計がヒットします。

![クエリの例](media/desktop-aggregations/aggregations-code_05.jpg)

AVERAGE 関数は集計を利用できます。 AVERAGE が COUNT で除算される SUM に内部的に折りたたまれるため、次のクエリでは集計がヒットします。 **UnitPrice** 列には SUM と COUNT の両方に対して定義された集計があるため、集計がヒットします。

![クエリの例](media/desktop-aggregations/aggregations-code_06.jpg)

場合によっては、DISTINCTCOUNT 関数は集計を利用できます。 集計テーブルで **CustomerKey** の差異を維持する **CustomerKey** 用の GroupBy エントリがあるため、次のクエリでは集計がヒットします。 この手法も、約 200 万から 500 万を超える個別値がクエリのパフォーマンスに影響する可能性があるパフォーマンスしきい値の対象となります。 ただしこれは、詳細テーブル内に何十億もの行があり、列内に 200 万から 500 万の個別値があるようなシナリオで役に立ちます。 このケースでは、何十億もの行を含むテーブルをスキャンするよりも、たとえテーブルがメモリ内にキャッシュされている場合でも、個別のカウントの方が速く実行できます。

![クエリの例](media/desktop-aggregations/aggregations-code_07.jpg)

### <a name="rls"></a>RLS
行レベル セキュリティ (RLS) 式を正常に動作させるには、集計テーブルと詳細テーブルの両方をフィルター処理する必要があります。 例を見ると、**Geography** テーブルの RLS 式が機能します。これは、**Sales** テーブルと **Sales Agg** テーブルの両方に対し、Geography はリレーションシップをフィルタリングする側にあるからです。 集計テーブルでヒットするクエリとヒットしないクエリに RLS が正常に適用されます。

![集計管理ロール](media/desktop-aggregations/manage-roles.png)

**Product** テーブルの RLS 式は、**Sales Agg** テーブルをフィルタリングせず、**Sales** テーブルのみをフィルタリングします。 これは推奨されません。 このロールを使用してデータセットにアクセスするユーザーによって送信されたクエリは、集計ヒットの恩恵を受けません。 集計テーブルは詳細テーブルで同じデータを別の方法で表現したものであり、RLS フィルターを適用できないため、集計テーブルからクエリに応答するのは安全ではありません。

**SalesAgg** テーブル自体の RLS 式では、詳細テーブルがフィルタリングされず、集計テーブルだけがフィルタリングされます。 これは許可されていません。

![集計管理ロール](media/desktop-aggregations/filter-agg-error.jpg)

## <a name="aggregations-based-on-group-by-columns"></a>グループ化列に基づく集計 

Hadoop ベースのビッグ データ モデルには、ディメンション モデルとは異なる特性があります。 大規模なテーブル間の結合を避けるため、多くの場合これらはリレーションシップに依存しません。 代わりに、ディメンション属性がファクト テーブルに非正規化されることがよくあります。 このようなビッグ データ モデルは、グループ化列に基づく**集計**を使用して、対話型の分析のためにロックを解除することができます。

次のテーブルには、集計対象の **Movement**  の数値列が含まれています。 その他のすべての列は、グループ化への属性です。 このテーブルには、IoT データと多数の行が含まれています。 ストレージ モードは、DirectQuery です。 データセット全体を集計するデータ ソースに対するクエリは、その膨大な量により低速になります。

![IoT テーブル](media/desktop-aggregations/aggregations_09.jpg)

このデータセットで対話型の分析を有効にするため、経度と緯度などの高いカーディナリティ属性を除くほとんどの属性をグループ化する集計テーブルを追加します。 これにより行数が大幅に削減され、メモリ内キャッシュに余裕で収まるサイズに縮小されます。 **Driver Activity Agg** のストレージ モードはインポートです。

![Driver Activity Agg テーブル](media/desktop-aggregations/aggregations_10.jpg)

次に、 **[集計の管理]** ダイアログで、集計マッピングを定義します。 このダイアログには、**Driver Activity Agg** テーブル内の各列の 1 行が表示され、ここで集計動作を指定できます。

![Driver Activity Agg テーブルの [集計の管理] ダイアログ](media/desktop-aggregations/aggregations_11.jpg)

次のテーブルは、**Driver Activity Agg** テーブルの集計を示しています。

![Driver Activity Agg 集計テーブル](media/desktop-aggregations/aggregations-table_02.jpg)

### <a name="group-by-columns"></a>グループ化列

この例では、**GroupBy** エントリは**省略できません**。これがないと、集計がヒットしません。 これは、この記事で前述したディメンション モデルの例で説明した、リレーションシップに基づいて集計を使用するのとは異なる動作です。

### <a name="query-examples"></a>クエリ例

**Activity Date** 列が集計テーブルの対象に含まれているため、次のクエリでは集計がヒットします。 テーブル行数のカウントの集計は、COUNTROWS 関数によって使用されます。

![クエリの例](media/desktop-aggregations/aggregations-code_08.jpg)

ファクト テーブルにフィルター属性が含まれているモデルには特に、テーブル行数のカウントの集計を使用することをお勧めします。 Power BI では、ユーザーによって明示的に要求されていない場合に、COUNTROWS を使用してデータセットにクエリを送信することができます。 たとえば、[フィルター] ダイアログには、各値の行数が表示されます。

![[フィルター] ダイアログ](media/desktop-aggregations/aggregations_12.jpg)

### <a name="rls"></a>RLS

RLS 式で集計テーブル、詳細テーブル、または両方をフィルタリングできるかどうかに関する、リレーションシップに基づく集計のための上述の同じ RLS ルールは、group by 列に基づく集計にも適用されます。 この例では、集計テーブルのすべての group by 列が詳細テーブルで網羅されているため、**Driver Activity** テーブルに適用されている RLS 式を利用し、**Driver Activity Agg** テーブルをフィルタリングできます。 一方、**Driver Activity Agg** テーブルの RLS フィルターは、**Driver Activity** テーブルに適用できず、許可されません。

## <a name="aggregation-precedence"></a>集計の優先順位

集計の優先順位により、1 つのサブクエリで複数の集計テーブルを対象にすることができます。

次の例を考えてみましょう。 これは、複数の DirectQuery ソースが含まれている[複合モデル](desktop-composite-models.md)です。

* **Driver Activity Agg2** インポート テーブルは、group-by 属性が少なくカーディナリティが低いため、粒度が高くなっています。 行数は、メモリ内キャッシュに余裕で収まるように、数千程度に抑えることができます。 これらの属性は、幹部のダッシュボードで使用されることがあるため、それらを参照するクエリはできるだけ高速にする必要があります。
* **Driver Activity Agg** テーブルは、DirectQuery モードの中間の集計テーブルです。 Azure SQL DW の 10 億を超える行を含み、列ストア インデックスを使用してソースで最適化されます。
* **Driver Activity** テーブルは DirectQuery で、ビッグ データ システムをソースとする IoT データの数兆を超える行が含まれています。 これは、制御されたフィルター コンテキストで IoT の個別の読み取りを表示するドリルスルー クエリを提供します。

> [!NOTE]
> 詳細テーブルと異なるデータ ソースを使用する DirectQuery 集計テーブルは、集計テーブルが SQL Server、Azure SQL または Azure SQL DW ソースからのものである場合にのみサポートされます。

このモデルのメモリ占有領域は比較的小さいものの、大きなデータセットのロックを解除します。 これはクエリの負荷を、それを使用するアーキテクチャのコンポーネントの長所に基づいて分散するため、分散アーキテクチャを表します。

![大きなデータセットをロック解除するメモリ占有領域の小さいモデルのテーブル](media/desktop-aggregations/aggregations_13.jpg)

**Driver Activity Agg2** の **[集計の管理]** ダイアログの *[優先順位]* フィールドには、**Driver Activity Agg** よりも高い 10 が示されています。これは、集計を使用するクエリで最初に考慮されることを意味します。 **Driver Activity Agg2** で対応できる粒度ではないサブクエリでは、代わりに **Driver Activity Agg** が考慮されます。 いずれの集計テーブルでも対応できない詳細クエリは、**Driver Activity** に向けられます。

チェーン集計が許可されていないため (この記事で前述した「[検証](#validations)」を参照)、 **[詳細テーブル]** 列には、**Driver Activity Agg** ではなく **Driver Activity** テーブルが指定されています。

![[集計の管理] ダイアログ](media/desktop-aggregations/aggregations_14.jpg)

次のテーブルは、**Driver Activity Agg2** テーブルの集計を示しています。

![Driver Activity Agg2 集計テーブル](media/desktop-aggregations/aggregations-table_03.jpg)

## <a name="aggregations-based-on-group-by-columns-combined-with-relationships"></a>リレーションシップと結合したグループ化列に基づく集計

この記事で既に説明したように、集計の 2 つの手法を組み合わせることもできます。 リレーションシップに基づく**集計**では、非正規化されたディメンション テーブルを複数のテーブルに分割する必要がある場合があります。 これがコストがかかる場合または特定のディメンション テーブルでは実行が難しい場合は、他に使用されている特定のディメンションとリレーションシップのために集計テーブル内で必要な属性をレプリケートすることができます。

次のモデルでは、**Sales Agg** テーブル内の *Month* (月)、*Quarter* (四半期)、*Semester* (半期)、*Year* (年) をレプリケートします。 **Sales Agg** テーブルと **Date** テーブル間にはリレーションシップはありません。 **Customer** と **Product Subcategory** へのリレーションシップはあります。 **Sales Agg** のストレージ モードはインポートです。

![集計方法を組み合わせる](media/desktop-aggregations/aggregations_15.jpg)

次のテーブルは、**Sales Agg** テーブルの **[集計の管理]** ダイアログ内のエントリ セットを示しています。 **Date** が詳細テーブルの GroupBy エントリは、Date 属性でグループ化するクエリで集計をヒットするために必須です。 前の例と同じく、リレーションシップが存在するため、CustomerKey と ProductSubcategoryKey の GroupBy エントリは集計のヒットには影響しません (これも DISTINCTCOUNT の例外によるものです)。

![Sales Agg 集計テーブル](media/desktop-aggregations/aggregations-table_04.jpg)

### <a name="query-examples"></a>クエリ例

次のクエリでは、CalendarMonth が集計テーブルでカバーされ、CategoryName は一対多のリレーションシップを使用してアクセスできるため、集計がヒットします。 **SalesAmount** には、Sum 集計が使用されています。

![クエリの例](media/desktop-aggregations/aggregations-code_09.jpg)

CalendarDay が集計テーブルの対象に含まれていないため、次のクエリでは集計がヒットしません。

![クエリの例](media/desktop-aggregations/aggregations-code_10.jpg)

次のタイム インテリジェンス クエリでは、集計がヒットしません。これは、DATESYTD 関数によって集計テーブルではカバーされない CalendarDay 値のテーブルが生成されるためです。

![クエリの例](media/desktop-aggregations/aggregations-code_11.jpg)

## <a name="caches-should-be-kept-in-sync"></a>キャッシュの同期状態を保つ

DirectQuery とインポートおよびデュアルのいずれかまたは両方のストレージ モードを組み合わせる**集計**では、メモリ内キャッシュとソース データとの同期が保持されない場合、異なるデータが返される場合があります。 クエリを実行しても、たとえばキャッシュされた値と一致するように DirectQuery の結果をフィルター処理するなどして、データに関する問題に対処することはありません。 これらの機能は、パフォーマンスの最適化で、ビジネス要件に対応する能力を損なわない方法でのみ使用する必要があります。 お客様がご自身のデータ フローを把握し、それに応じて設計してください。 必要に応じて、ソースでそのような問題を処理する手法が確立されています。

## <a name="next-steps"></a>次の手順

以下の記事では、複合モデルと DirectQuery について詳しく説明しています。

* [Power BI Desktop の複合モデル](desktop-composite-models.md)
* [Power BI Desktop での多対多カーディナリティのリレーションシップ](desktop-many-to-many-relationships.md)
* [Power BI Desktop のストレージ モード](desktop-storage-mode.md)

DirectQuery に関する記事:

* [Power BI で DirectQuery を使用する](desktop-directquery-about.md)
* [Power BI の DirectQuery でサポートされるデータ ソース](desktop-directquery-data-sources.md)
