---
title: Power BI Desktop で多対多のリレーションシップ
description: Power BI Desktop で多対多カーディナリティのリレーションシップを使用します
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/13/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 578d5f77753884575111b3247f5aa4d3ae79e179
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73866811"
---
# <a name="relationships-with-a-many-many-cardinality-in-power-bi-desktop"></a>Power BI Desktop での多対多カーディナリティのリレーションシップ

Power BI Desktop の "*多対多カーディナリティのリレーションシップ*" 機能を使用すると、"*多対多*" のカーディナリティを使用するテーブルを結合できます。 2 つ以上のデータ ソースを含むデータ モデルを、より簡単かつ直感的に作成できます。 "*多対多カーディナリティのリレーションシップ*" 機能は、Power BI Desktop のより大きな機能である "*複合モデル*" の一部です。

![[リレーションシップの編集] ウィンドウでの多対多のリレーションシップ](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Power BI Desktop の "*多対多カーディナリティのリレーションシップ*" 機能は、関連する 3 つの機能の 1 つです。

* **複合モデル**:DirectQuery 接続やインポートなど、2 つ以上のデータ接続を任意の組み合わせでレポートに含めることができます。 詳細については、「[Power BI Desktop で複合モデルを使用する](desktop-composite-models.md)」を参照してください。

* **多対多カーディナリティのリレーションシップ**:"*複合モデル*" では、テーブル間に "*多対多カーディナリティのリレーションシップ*" を確立することができます。 このアプローチでは、テーブル内の一意の値の要件が除外されます。 また、リレーションシップを作成するためだけに新しいテーブルを導入するなどの以前の回避策も除外されます。 この機能については、この記事で詳しく説明します。

* **ストレージ モード**:どのビジュアルでバックエンド データ ソースへのクエリが必要かを指定できるようになりました。 クエリを必要としないビジュアルは、それらが DirectQuery に基づいている場合でもインポートされます。 この機能はパフォーマンスの向上とバック エンドの負荷の軽減に役立ちます。 以前は、スライサーのような単純なビジュアルでも、バックエンド ソースに送信されるクエリが開始されました。 詳細については、「[Power BI Desktop のストレージ モード (プレビュー)](desktop-storage-mode.md)」をご覧ください。

## <a name="what-relationships-with-a-many-many-cardinality-solves"></a>"*多対多カーディナリティのリレーションシップ*" によって解決されるもの

"*多対多カーディナリティのリレーションシップ*" 機能が利用可能になるまでは、2 つのテーブル間のリレーションシップは Power BI で定義されていました。 リレーションシップに関係する少なくとも 1 つのテーブルの列に、一意の値を含める必要がありました。 しかし多くの場合、一意の値を含む列はありませんでした。 

たとえば、2 つのテーブルに *Country* (国) というラベルの付いた列があり、*Country* (国) の値がどちらのテーブルでも一意ではなかったとします。 このようなテーブルを結合するには、回避策を用意する必要がありました。 このような回避策の 1 つは、必要な一意の値を含む追加のテーブルをモデルに導入することです。 "*多対多カーディナリティのリレーションシップ*" 機能では、**多対多**のカーディナリティを持つリレーションシップを使用して、このようなテーブルを直接結合することができます。  

## <a name="use-relationships-with-a-many-many-cardinality"></a>"*多対多カーディナリティのリレーションシップ*" を使用する

Power BI で 2 つのテーブル間のリレーションシップを定義する場合、リレーションシップのカーディナリティを定義する必要があります。 たとえば、*ProductSales* (製品売上) と *Product* (製品) の間のリレーションシップ&mdash;列 *ProductSales[ProductCode]* と *Product[ProductCode]* を使用します&mdash;を、"*多対一*" として定義します。 リレーションシップをこのように定義する理由は、各製品に対して多くの売上が存在し、*Product* (製品) テーブル内の列 *(ProductCode)* が一意であるためです。 リレーションシップのカーディナリティを "*多対一*"、"*一対多*"、または "*一対一*" として定義すると、Power BI によってそれが検証され、選択したカーディナリティが実際のデータと一致していることが確認されます。

たとえば、次の図の単純なモデルを見てみましょう。

![リレーションシップ ビュー](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

ここで、*Product* (製品) で次の 2 つの行のみが表示されているとします。

![2 つの行を含む Product (製品) テーブルのビジュアル](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

また、*Sales* (売上) テーブルには、製品 C の行を含めて 4 行しか含まれていないとします。参照整合性エラーのため、製品 C の行は *Product* (製品) テーブルには存在しません。

![4 つの行を含む Sales (売上) テーブルのビジュアル](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

*ProductName* (製品名) と *Price* (価格) (*Product* (製品) テーブル)、および各製品の合計 *Qty* (数量) (*ProductSales* (製品売上) テーブル) が、次のように表示されます。 

![製品名、価格、および数量を表示するビジュアル](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

前の画像からわかるように、製品 C の売上に関連付けられている空白の *ProductName* 行が存在しています。この空白行は次のことを示しています。

* *Product* (製品) テーブルに対応する行が存在しない、*ProductSales* (製品売上) テーブルの任意の行がある。 この例の製品 *C* の場合のように、参照整合性の問題が存在する。

* 外部キー列が null である *ProductSales* (製品売上) テーブルの行がある。 

これらの理由により、どちらの場合の空白行も、*ProductName* (製品名) と *Price* (価格) が不明な売上を示しています。

テーブルが 2 つの列で結合される場合に、どちらの列も一意ではないことがあります。 たとえば、次の 2 つのテーブルを考えてみましょう。

* *Sales* (売上) テーブルでは、*State* (州) 別の売上データが表示されており、各行にはその州の売上の種類が含まれています。 州はカリフォルニア州、ワシントン州、テキサス州などです。 

    ![州別の売上を表示する Sales (売上) テーブル](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* *CityData* (市区町村データ) テーブルでは、人口や州 (カリフォルニア州、ワシントン州、ニューヨーク州など) など、市区町村に関するデータが表示されています。

    ![市区町村、州、および人口を表示する Sales (売上) テーブル](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

両方のテーブルに *State* (州) の列があり、州別の売上と、各州の合計人口についてレポートを表示したいところですが、どちらのテーブルでも *State* (州) 列が一意ではないという問題があります。 

## <a name="the-previous-workaround"></a>以前の回避策

2018 年 7 月リリースよりも以前のバージョンの Power BI Desktop では、ユーザーがこれらのテーブル間に直接のリレーションシップを作成することはできませんでした。 一般的な回避策は、以下の手順を実行することでした。

* 一意の *State* ID のみを含む第 3 のテーブルを作成します。 テーブルには、次のいずれか、またはすべてが当てはまります。
  * 計算テーブル (Data Analysis Expressions [DAX] を使用して定義されたもの)。
  * クエリ エディターで定義されたクエリに基づくテーブル。テーブルのいずれかから抽出された一意の ID を表示する場合があります。
  * 結合された完全なセット。

* 一般的な "*多対一*" のリレーションシップを使用して、2 つの元のテーブルをその新しいテーブルに関連付けます。

回避策のテーブルは、表示されたままにしておくことも、**フィールド**一覧に表示されないように非表示にすることもできます。 テーブルを非表示にする場合、"*多対一*" リレーションシップが一般的に両方向にフィルター処理に設定され、いずれのテーブルからでも *State* (州) フィールドを使用できます。 後続のクロス フィルタ リングは、もう 1 つのテーブルにも反映されます。 このアプローチを次の図に示します。

![リレーションシップ ビュー](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

*State* (州) (*CityData* (市区町村データ) テーブル) と共に合計の *Population* (人口) と合計の *Sales* (売上) を表示するビジュアルは、次のようになります。

![テーブルのビジュアル](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> この回避策で *CityData* (市区町村データ) テーブルの州が使用されると、そのテーブルに含まれる State (州) のみが一覧表示され、したがってテキサス州は除外されます。 また、"*多対一*" リレーションシップとは異なり、合計行にはすべての *Sales* (売上) (テキサス州のデータを含む) が含まれますが、このような不一致の行を対象とする空白行は含まれません。 同様に、*State* (州) が null 値の *Sales* (売上) を対象とする空白行はありません。

また、そのビジュアルに *City* (市区町村) も追加する場合、*City* (市区町村) ごとの人口はわかりますが、*City* (市区町村) に対して表示される *Sales* (売上) では、対応する *State* (州) の *Sales* (売上) が単純に繰り返されます。 これは通常、次の図に示すように、列でのグループ化が一部の集計メジャーに関連付けられていない場合に発生します。

![テーブルのビジュアル](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

この回避策のすべての *States* の組み合わせとして新しい *Sales* (売上) テーブルを定義し、これを**フィールド** リストで表示させた場合、次の図に示すように、同じビジュアルによって (新しいテーブル上の) *State* (州) と、*Population* (人口) の合計と *Sales* (売上) の合計が表示されます。

![テーブルのビジュアル](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

このように、*TX* (テキサス州)&mdash;*Sales* (売上) データを含むが *Population* (人口) は不明&mdash;と *New York* (ニューヨーク州)&mdash;*Population* (人口) データを含むが *Sales* データは不明&mdash;が含まれます。 この回避策は最適ではなく、多くの問題を含んでいます。 多対多カーディナリティのリレーションシップを作成すると、次のセクションで説明するように、発生する問題に対処することができます。

## <a name="use-relationships-with-a-many-many-cardinality-instead-of-the-workaround"></a>回避策の代わりに "*多対多カーディナリティのリレーションシップ*" を使用する

2018 年 7 月バージョンの Power BI Desktop 以降、以前に説明したもののようなテーブルを直接関連付けることができます。似たような回避策を利用する必要はありません。 リレーションシップのカーディナリティを "*多対多*" に設定することが可能になりました。 この設定は、どちらのテーブルにも一意の値が含まれていないことを示しています。 このようなリレーションシップでも、どちらのテーブルがもう一方のテーブルをフィルター処理するかを制御できます。または、両方のテーブルが相互にフィルター処理する双方向のフィルター処理を適用できます。  

Power BI Desktop では、いずれのテーブルにもリレーションシップの列に一意の値が含まれていないと判断された場合、カーディナリティの既定値は "*多対多*" になります。 このような場合、リレーションシップの設定が意図した動作であり、データの問題による意図しない結果ではないことを確認する警告が表示されます。 

たとえば、*CityData* (市区町村データ) と *Sales* (売上) 間に直接リレーションシップを作成する場合&mdash;ここではフィルターのフローが *CityData* (市区町村データ) から *Sales* (売上) になるようにする必要があります&mdash;Power BI Desktop で次の図に示すような **[リレーションシップの編集]** ウィンドウが表示されます。

![[リレーションシップの編集] ウィンドウ](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

その結果、 **[リレーションシップ]** ビューには、2 つのテーブル間に直接かつ多対多のリレーションシップが表示されるようになります。 **フィールド** リストにおけるテーブルの外観、およびビジュアルが作成されるときの後続の動作は、回避策を適用した場合と似ています。 回避策では、個別の *State* (州) データを表示する追加のテーブルは表示されません。 たとえば、前のセクションで説明したように、*State* (州)、*Population* (人口)、*Sales* (売上) のデータを表すビジュアルは、次のように表示されます。

![テーブルのビジュアル](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

"*多対多カーディナリティのリレーションシップ*" と、より一般的な "*多対一*" のリレーションシップの主な違いは、次のとおりです。

* 表示される値に、もう一方のテーブルの一致しない行を示す空白行が含まれません。 また、もう一方のテーブルのリレーションシップで使用される列が null である行を示す値も含まれません。
* 複数の行が関連する可能性があるため、`RELATED()` 関数を使用することはできません。
* テーブルに `ALL()` 関数を使用しても、多対多のリレーションシップによって関連付けられているもう一方のテーブルに適用されているフィルターは削除されません。 前の例では、次のスクリプトのように定義されたメジャーでは関連する *CityData* (市区町村データ) テーブルの列に対するフィルターは削除されません。

    ![スクリプトの例](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    *State* (州)、*Sales* (売上)、および *Sales total* (売上合計) のデータを表示するビジュアルは、次のようになります。

    ![テーブルのビジュアル](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

前述した相違点に注意しながら、`ALL(\<Table>)` を使用する計算 ("*合計に対する割合*" など) が意図した結果を返すことを確認します。 


## <a name="limitations-and-considerations"></a>制限事項と考慮事項

このリリースの "*多対多カーディナリティのリレーションシップ*" と複合モデルには、いくつかの制限事項があります。

次の Live Connect (多次元) ソースは、複合モデルでは使用できません。

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI データセット
* Azure Analysis Services

DirectQuery を使用してこれらの多次元ソースに接続すると、別の DirectQuery ソースに接続することも、これをインポートしたデータと結合することもできません。

DirectQuery を使用する際の既存の制限は、"*多対多カーディナリティのリレーションシップ*" を使用する場合にも適用されます。 これらの制限事項の多くは、テーブルのストレージ モードに応じてテーブルごとに適用されるようになりました。 たとえば、インポートしたテーブルの計算列からは他のテーブルを参照できますが、DirectQuery テーブルの計算列からは引き続き同じテーブルの列しか参照できません。 モデル内のテーブルのいずれかが DirectQuery である場合、モデル全体に他の制限事項が適用されます。 たとえば、モデル内のいずれかのテーブルにストレージ モードの DirectQuery がある場合、そのモデルでは QuickInsights 機能と Q&A 機能を使用できません。 

## <a name="next-steps"></a>次の手順

複合モデルと DirectQuery について詳しくは、次の記事をご覧ください。
* [Power BI Desktop の複合モデル](desktop-composite-models.md)
* [Power BI Desktop のストレージ モード (プレビュー)](desktop-storage-mode.md)
* [Power BI Desktop で DirectQuery を使用する](desktop-directquery-about.md)
* [Power BI Desktop の DirectQuery でサポートされるデータ ソース](desktop-directquery-data-sources.md)
