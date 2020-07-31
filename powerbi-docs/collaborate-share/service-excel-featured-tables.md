---
title: Excel で Power BI のおすすめのテーブルにアクセスする (プレビュー)
description: Excel のデータ型ギャラリーで、Power BI データセットのおすすめテーブルのデータを検索できます。
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/24/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 00fba391a6ad92f1e3edaf0e2af9691452724f6e
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251646"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Excel で Power BI のおすすめのテーブルにアクセスする (プレビュー)

Excel のデータ型ギャラリーでは、Power BI データセットの "*おすすめのテーブル*" からのデータを検索することができます。 おすすめのテーブルを使用すると、Excel シートにエンタープライズ データを簡単に追加できます。 以下は、Power BI データを Excel シートに取り込む手順です。

- Power BI データ モデラーによって、[Power BI のデータセットが昇格または認定](../connect-data/service-datasets-promote.md)されます。
- データ モデラーによって、データセット内の[おすすめのテーブルが識別](service-create-excel-featured-tables.md)され、そのデータセットが Power BI サービスに保存されます。
- 組織の残りの部分は、関連する更新可能なデータのために、Excel でこれらのおすすめのテーブルに接続できます。 Excel では、これらのテーブルは "*データ型*" と呼ばれ、データ型ギャラリーに一覧表示されます。

> [!NOTE]
> Excel では、Power BI でアクセスできるデータセットからデータを取得することもできます。 **[データ]** リボンで、 **[データの取得]**  >  **[From Power BI (Microsoft)]\(Power BI から (Microsoft)\)** の順に選択します。
> :::image type="content" source="media/service-excel-featured-tables/excel-get-data-power-bi.png" alt-text="[データ] リボンの Power BI からの [データの取得] オプションのスクリーンショット。":::

## <a name="the-excel-data-types-gallery"></a>Excel のデータ型ギャラリー
Power BI データセットのおすすめのテーブルは、Excel の**データ型**ギャラリーでは、 **[データ]** リボンに "*データ型*" として表示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Excel の [データ] リボンのデータ型ギャラリーのスクリーンショット。":::

ギャラリーを展開すると、 **[株式]** や **[地理]** などの一般的なデータ型に加え、Power BI データセットのおすすめのテーブルである、使用可能な上位 10 個の **[組織]** データ型が表示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Excel のデータ型ギャラリーのスクリーンショット。":::

## <a name="format-a-range-of-cells-as-a-table-optional"></a>セルの範囲をテーブルとして書式設定する (オプション)

 開始する前に、データを Excel テーブルとして書式設定することをお勧めします。 これにより、1 つの行に加えた変更が、テーブル内の他の行に適用されます。 

1. 列ヘッダーを追加します。 
2. その後、データ内のセルを選択し、Ctrl + T キーを押します。 
3. **[先頭行をテーブルの見出しとして使用する]** チェック ボックス  >  **[OK]** の順にクリックします。

    :::image type="content" source="media/service-excel-featured-tables/excel-format-table.png" alt-text="テーブルへの範囲の変換を示すスクリーンショット。":::

## <a name="search-for-power-bi-data-in-the-excel-data-types-gallery"></a>Excel データ型ギャラリーで Power BI データを検索する

Power BI のおすすめのテーブルのデータを検索するには、おすすめのテーブルの値と一致する値を含む、Excel シート内のセルまたは範囲を選択します。 **[組織]** を選択します。 アクセスできるすべてのおすすめのテーブルが Excel によって検索され、一致するものが探されます。

:::image type="content" source="media/service-excel-featured-tables/excel-table-organization.png" alt-text="セルまたはセル範囲の選択のスクリーンショット。":::
 
お探しのおすすめのテーブルがわかっている場合は、ギャラリーから **[From your organization (preview)]\(組織から (プレビュー)\)** を選択して、それを選びます。

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data-table.png" alt-text="Excel の組織データ、サプライヤー データ型テーブルのスクリーンショット。":::
 
検索を行い、Excel によって高い信頼度で一致する行が検出された場合、そのセルは直ちにそれらの行にリンクされます。 リンクされた項目のアイコンにより、セルが Power BI の行にリンクされていることが示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="リンクされた項目のアイコンのスクリーンショット。":::

一致する可能性のある行がセルに複数ある場合、そのセルに疑問符アイコンが表示され、 **[データ選択ウィザード]** ウィンドウが開きます。 次の例では、ユーザーは B2:B10 から範囲を選択し、Power BI のおすすめのテーブルを検索しました。 セル B5 の "Ma Maison" を除き、すべての行に一致がありました。 **[データ選択ウィザード]** には、2 つの一致候補が表示されています。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Excel の [データ選択ウィザード] ウィンドウのスクリーンショット。":::
 
[組織] データ オプションを使用すれば、複数のおすすめのテーブルから行を返すことができます。 Excel では、一致する可能性のある行が、その元のデータ型によってグループ化されます。 Excel により、一致する可能性が最も高い行に基づいてデータ型が並べ替えられます。 シェブロンの矢印を使用して、一致する行のデータ型を折りたたんだり展開したりできます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="可能性のあるものが複数示されている Excel の [データ選択ウィザード] ウィンドウのスクリーンショット。":::
 
各行について、行の名前を選択すると行の詳細が表示され、適切な行を選択するのに役立ちます。 それが見つかったら、 **[選択]** を押して、その行を Excel のセルにリンクします。 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="[データ選択ウィザード] の詳細のスクリーンショット。":::
 
セルの **[カード]** アイコンを選択すると、おすすめのテーブル内のすべてのフィールドと計算フィールドのデータを含むカードが表示されます。 カードのタイトルには、おすすめのテーブルの [行ラベル] フィールドの値が表示されます。
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="リンクされた項目の詳細のスクリーンショット。":::

**[データの挿入]** アイコンを選択してから、フィールドの一覧からフィールド名を選んで、その値をグリッドに追加します。  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="フィールド名の選択のスクリーンショット。":::

フィールド値は、隣接するセルに配置されます。 セルの数式ではリンクされたセルとフィールド名が参照されるので、Excel 関数内でそのデータを使用できます。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel のセルの数式のスクリーンショット。":::

## <a name="cell-formulas"></a>セルの数式

Excel テーブルを使用する場合は、`.` (ピリオド) 参照を使用して、リンク テーブルの列を参照し、データ フィールドを追加することができます。

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Excel のピリオド参照のスクリーンショット。":::

同様に、セルを使用する場合は、セルを参照し、`.` (ピリオド) 参照を使用してフィールドを取得することができます。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="セルのピリオド参照のスクリーンショット。":::
 
## <a name="data-caching-and-refresh"></a>データのキャッシュと更新

Excel によってセルが Power BI のおすすめのテーブルの行にリンクされると、すべてのフィールド値が取得されて Excel ファイルに保存されます。 自分がファイルを共有したすべてのユーザーは、Power BI からデータを要求することなく、任意のフィールドを参照できます。  

リンク セルのデータを更新するには、 **[データ]** リボンの **[すべて最新の情報に更新]** ボタンを使用します。 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="[すべて最新の情報に更新] のスクリーンショット。":::
 
また、個々のセルを更新することもできます。 セルを右クリックし、 **[データ型]**  >  **[最新の情報に更新]** を選択してください。

## <a name="show-a-card-change-or-convert-to-text"></a>カードを表示、変更、またはテキストに変換

リンク セルには、右クリック メニュー オプションが追加されています。 セルを右クリックします。 通常のオプションと共に、以下も表示されます。

- **Show Data Type Card (データ型のカードの表示)** 。
- **更新する**。
- **変更**。
- **テキストに変換**。

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="右クリックして表示された [テキストに変換] のスクリーンショット。":::
 
**[テキストに変換]** を使用すると、Power BI のおすすめのテーブルの行へのリンクが削除されます。 重要な点として、セル内のテキストはリンク セルの行ラベルの値になります。 意図していなかった行にセルをリンクした場合は、Excel の **[元に戻す]** を選択して、セルの初期値を復元します。

## <a name="licensing"></a>ライセンス

Excel のデータ型ギャラリーと Power BI のおすすめのテーブルに接続されたエクスペリエンスをご利用いただけるのは、Excel E5 および G5 のお客様のみです。 

## <a name="security"></a>セキュリティ

Power BI でアクセス許可を持っているデータセットのおすすめのテーブルのみが表示されます。 データを更新するときは、Power BI のデータセットにアクセスして行を取得するためのアクセス許可が必要です。 これには、データセットに対するビルドまたは書き込みのアクセス許可が必要です。 Excel では、行全体の返されるデータがキャッシュされます。 自分が Excel ファイルを共有するすべてのユーザーが、すべてのリンク セルのすべてのフィールドのデータを表示できます。

Power BI データセットに行レベルのセキュリティまたは Microsoft Information Protection の秘密度ラベルが適用されている場合、そのデータセットのおすすめのテーブルは Excel のデータ型ギャラリーに含まれません。 これは、初期プレビューの制限事項です。

## <a name="administrative-control"></a>管理制御

Power BI 管理者は、Excel のデータ型ギャラリーでおすすめのテーブルを使用できる組織内のユーザーを制御できます。 詳細については、管理ポータルの記事の「[おすすめのテーブルの設定](../admin/service-admin-portal.md#featured-tables-settings)」をご覧ください。 
 
### <a name="auditing"></a>監査

管理の監査ログには、おすすめのテーブルに関する次のイベントが表示されます。

- **AnalyzedByExternalApplication**:どのユーザーがどのおすすめのテーブルにアクセスしているかを管理者が把握できます。
- **UpdateFeaturedTables**:どのユーザーがおすすめのテーブルを発行および更新しているかを管理者が把握できます。

監査ログのイベントの完全な一覧については、「[Power BI でユーザー アクティビティを追跡する](../admin/service-admin-auditing.md)」をご覧ください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

初期プレビューの制限事項を次に示します。

- 統合は、Excel の Insider ビルドで使用できます。
- Excel のデータ型ギャラリーには、Power BI Desktop および Power BI サービスで適切なライセンスを持つユーザー向けのおすすめのテーブルが含まれます。 プレビューの開始時には Power BI サービスのサポートを利用できない可能性がありますが、今後追加される予定です。
- 次の機能を使用する Power BI データセットのおすすめのテーブルは、Excel に表示されません。 

    - 行レベル セキュリティのデータセット。
    - Microsoft Information Protection が有効なデータセット。
    - DirectQuery データセット。
    - ライブ接続を使用するデータセット。

- Excel には、おすすめのテーブルの列および計算列のデータのみが表示されます。 次のものは初期プレビューでは提供されません。

    - おすすめのテーブルで定義されるメジャー。
    - 関連テーブルで定義されるメジャー、およびリレーションシップから計算される暗黙のメジャー。

- Excel には、新しい Power BI ワークスペースに格納されているおすすめのテーブル ("*データ型*") のみが表示されます。 クラシック ワークスペース、または個人用ワークスペースに格納されているおすすめのテーブルは、Excel ではデータ型として表示されません。 Power BI で[クラシック ワークスペースを新しいワークスペースにアップグレードする](service-upgrade-workspaces.md)ことができます。

Excel でのデータ型のエクスペリエンスは、lookup 関数に似ています。 Excel シートから提供されるセル値を受け取り、Power BI のおすすめのテーブルで一致する行が検索されます。 検索エクスペリエンスには、次のような動作があります。

- **[組織データ]** ボタンを使用して検索する場合、Excel では認定済みデータセット内のおすすめのテーブルだけが検索されます。
- 行の一致は、おすすめのテーブルに含まれるテキスト列に基づいています。 これには Power BI Q&A 機能と同じインデックスが使用されます。これは英語での検索用に最適化されています。 その他の言語で検索すると、正確な一致が得られない場合があります。 数値列は一致とは見なされません。
- 一致は、個々の検索語句の完全一致とプレフィックス一致に基づいています。 セルの値は、スペース、またはタブのようなその他の空白文字に基づいて分割されます。 その後、各単語が検索語句と見なされます。 行のテキスト フィールドの値が、完全一致とプレフィックス一致で各検索語句と比較されます。 行のテキスト フィールドがその検索語句で始まる場合は、プレフィックス一致が返されます。 たとえば、セルに "Orange County" が含まれていた場合、"Orange" と "County" が個別の検索語句になります。 

    - 値が "Orange" または "County" と完全に一致するテキスト列を含む行が返されます。 
    - 値が "Orange" または "County" で始まるテキスト列を含む行が返されます。 
    - 重要なこととして、"Orange" または "County" を含んでいても、それらの語句で始まらない行は返されません。

- Power BI では、各セルに対して最大 100 行の候補が返されます。
- XMLA エンドポイントでのおすすめのテーブルの設定または更新はサポートされていません
- データ モデルを含む Excel ファイルを使用して、おすすめのテーブルを発行することができます。 そのデータを Power BI Desktop に読み込み、おすすめのテーブルを発行します。
- おすすめのテーブルのテーブル名、行ラベル、またはキー列を変更すると、そのテーブルの行にリンクされたセルを使用する Excel ユーザーに影響を及ぼす可能性があります。 
- Excel では、データが Power BI データセットから取得された日時が表示されます。 これは、Power BI でデータが更新された時間、またはデータセット内の最新のデータ ポイントの時間であるとは限りません。 たとえば、Power BI のデータセットが 1 週間前に更新されましたが、基になるソース データは更新が行われた時点で 1 週間経過していたとします。 実際のデータは 2 週間前のものになりますが、Excel では、データが Excel に取り込まれた日付/時刻として、取得されたデータが表示されます。

## <a name="next-steps"></a>次の手順

- [Power BI Desktop でおすすめのテーブルを設定する](service-create-excel-featured-tables.md)
- [Power BI からの Excel のデータ型の使用](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)について、Excel のドキュメントを参照します。
- わからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

