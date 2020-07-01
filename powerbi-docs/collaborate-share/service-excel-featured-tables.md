---
title: Excel で Power BI のおすすめのテーブルにアクセスする (プレビュー)
description: Excel のデータ型ギャラリーで、Power BI データセットのおすすめテーブルのデータを検索できます。
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/20/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a872c0ada80a7168ebc6bb545de1ad474c4561b7
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85226357"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>Excel で Power BI のおすすめのテーブルにアクセスする (プレビュー)

Excel のデータ型ギャラリーで、Power BI データセットのおすすめテーブルのデータを検索できます。 おすすめのテーブルを使用すると、Excel シートにエンタープライズ データを簡単に追加できます。 組織は、Power BI の認定および昇格されたデータセット機能を使用することで、関連する更新可能なデータをより多くのユーザーが検索および使用して、より適切な意思決定を行えるようにすることができます。 [Power BI からの Excel のデータ型](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)を使用する方法に関する Excel のドキュメントを参照してください。

データ型ギャラリーには、モデル作成者が Power BI データセットにキュレーションしたおすすめのテーブルのみが表示されます。 また、Power BI でアクセスできる Excel のデータセットを参照することもできます。 Excel で、 **[データ]** リボンの **[データの取得]** の下にある **[Power BI データセット]** オプションを選択します。

## <a name="access-power-bi-data-through-the-excel-data-types-gallery"></a>Excel のデータ型ギャラリーを使用して Power BI データにアクセスする
Power BI データセットのおすすめのテーブルは、[データ] リボンの Excel のデータ型ギャラリーに表示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Excel の [データ] リボン":::

ギャラリーを展開すると、使用可能な上位のデータ型が表示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Excel のデータ型ギャラリー":::
 
Power BI のおすすめのテーブルのデータを検索するには、Excel シート内のセルまたは範囲を選択します。

:::image type="content" source="media/service-excel-featured-tables/excel-select-cell.png" alt-text="セルの選択":::
 
ギャラリーから **[組織データ]** オプションを選択して、アクセス権のある認定済みデータセット内のおすすめのテーブルでデータを検索します。

:::image type="content" source="media/service-excel-featured-tables/excel-organizational-data.png" alt-text="Excel の組織データ":::
 
検索するデータの種類がわかっている場合、または [組織データ] オプションを使用しても一致する行が見つからない場合は、特定のデータ型を選択します。

:::image type="content" source="media/service-excel-featured-tables/excel-select-data-type.png" alt-text="データ型の選択":::
 
検索を行い、高い信頼度で一致する行が見つかった場合、そのセルは直ちにその行とリンクされます。 リンクされた項目のアイコンにより、セルが Power BI の行にリンクされていることが示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="リンクされた項目のアイコン":::

セルに一致する可能性のある行が複数ある場合は、データ セレクター ペインが表示されます。 そのセルには疑問符アイコンが表示され、それを使用するとその行のデータ セレクター ペインが開きます。 ユーザーが A2:A7 の範囲を選択し、Power BI のおすすめのテーブルを検索した後の例を次に示します。

:::image type="content" source="media/service-excel-featured-tables/excel-multiple-matches.png" alt-text="一致する可能性のある複数の行":::

**[Data Selector]\(データ セレクター\)** ペインには、一致する可能性のある行が表示されます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-pane.png" alt-text="Excel の [Data Selector]\(データ セレクター\) ペイン":::
 
[組織データ] オプションでは、複数のデータ型から行を返すことができます。 Excel では、一致する可能性のある行が、その元のデータ型によってグループ化されます。 Excel により、一致する可能性が最も高い行に基づいてデータ型が並べ替えられます。 シェブロンの矢印を使用して、一致する行のデータ型を折りたたんだり展開したりできます。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="Excel の [Data Selector]\(データ セレクター\) ペイン":::
 
各行について、行の名前を選択すると行の詳細が表示され、適切な行を選択するのに役立ちます。 行が見つかったら、 **[選択]** をクリックして、その行を Excel のセルにリンクします。 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-select.png" alt-text="[Data Selector]\(データ セレクター\) の詳細":::
 
行が選択されると、セルはその行にリンクされ、その値では Power BI のおすすめのテーブルの **[行ラベル]** フィールドの値が使用されます。 

:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-icon.png" alt-text="Excel のリンクされた項目":::
 
**[リンク セル]** のアイコンを選択すると、おすすめのテーブルに含まれるすべてのフィールドと計算フィールドのデータが記載されたカードが表示されます。 カードのタイトルには、おすすめのテーブルの [行ラベル] フィールドの値が表示されます。
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="リンクされた項目の詳細":::

**[データの挿入]** アイコンを選択して、フィールド値をグリッドに追加します。

:::image type="content" source="media/service-excel-featured-tables/excel-insert-data.png" alt-text="データの挿入"::: 

フィールドの一覧からフィールド名を選択して、その値をグリッドに追加します。  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="フィールド名の選択":::

フィールド値は、隣接するセルに配置されます。 セルの数式ではリンクされたセルとフィールド名が参照されるので、Excel 関数内でそのデータを使用できます。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel のセルの数式":::
 
データを Excel テーブルとして書式設定すると、フィールドの追加によってテーブルが拡張され、フィールド名と一致するように列のヘッダーが設定されます。 同じデータ型にリンクされた行にも、それぞれの値が入力されます。

:::image type="content" source="media/service-excel-featured-tables/excel-field-column-name.png" alt-text="フィールドは列名です"::: 

## <a name="cell-formulas"></a>セルの数式

Excel テーブルを使用する場合は、`.` (ピリオド) 参照を使用して、リンク テーブルの列を参照し、データ フィールドを追加することができます。

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Excel のピリオド参照":::

同様に、セルを使用する場合は、セルを参照し、`.` (ピリオド) 参照を使用してフィールドを取得することができます。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="セルのピリオド参照":::
 
## <a name="data-caching-and-refresh"></a>データのキャッシュと更新

Excel によってセルが Power BI のおすすめのテーブルの行にリンクされると、すべてのフィールド値が取得されて Excel ファイルに保存されます。 自分がファイルを共有したすべてのユーザーは、Power BI からデータを要求することなく、任意のフィールドを参照できます。  

リンク セルのデータを更新するには、 **[データ]** リボンの **[すべて最新の情報に更新]** ボタンを使用します。 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="すべて最新の情報に更新":::
 
また、個々のセルを更新することもできます。 セルを右クリックし、 **[データ型]**  >  **[最新の情報に更新]** を選択してください。

## <a name="show-a-card-change-or-convert-to-text"></a>カードを表示、変更、またはテキストに変換

リンク セルには、右クリック メニュー オプションが追加されています。 セルを右クリックし、次の順に選択します: **[データ型]**  >  

- **カードを表示**
- **Refresh\(更新\)**
- **変更点** 
- **テキストに変換**。

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="右クリック、テキストに変換":::
 
**[テキストに変換]** を使用すると、Power BI のおすすめのテーブルの行へのリンクが削除されます。 重要な点として、セル内のテキストはリンク セルの行ラベルの値になります。 意図していなかった行にセルをリンクした場合は、Excel の **[元に戻す]** を選択して、セルの初期値を復元します。

## <a name="licensing"></a>ライセンス
Excel のデータ型ギャラリーと Power BI のおすすめのテーブルに接続されたエクスペリエンスをご利用いただけるのは、Excel E5 および G5 のお客様のみです。 

## <a name="security"></a>セキュリティ

Power BI でアクセス許可を持っているデータセットのおすすめのテーブルのみが表示されます。 データを更新するときは、Power BI のデータセットにアクセスして行を取得するためのアクセス許可が必要です。 これには、データセットに対するビルドまたは書き込みのアクセス許可が必要です。 Excel では、行全体の返されるデータがキャッシュされます。 自分が Excel ファイルを共有するすべてのユーザーが、すべてのリンク セルのすべてのフィールドのデータを表示できます。

Power BI データセットに行レベルのセキュリティまたは Microsoft Information Protection の秘密度ラベルが適用されている場合、そのデータセットのおすすめのテーブルは Excel のデータ型ギャラリーに含まれません。 これは、初期プレビューの制限事項です。

## <a name="curate-a-featured-table-in-power-bi-desktop"></a>Power BI Desktop でおすすめのテーブルをキュレーションする
Excel のデータ型ギャラリーには、Power BI サービスにアップロードされたデータセット内のおすすめのテーブルが表示されます。 Power BI Desktop を使用して、データ モデルでおすすめのテーブルをキュレーションし、Power BI サービスにアップロードします。

### <a name="turn-on-the-featured-table-preview"></a>おすすめのテーブルのプレビューを有効にする

1. Power BI Desktop で、 **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]**  >  **[プレビュー機能]** の順に選択します。
2. **[Featured tables]\(おすすめのテーブル\)** チェック ボックスをオンにします。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="おすすめのテーブル オプションをプレビューする":::

### <a name="select-a-table"></a>テーブルを選択する

1. Power BI Desktop でモデル ビューに移動します。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="モデル ビュー":::
 
2. テーブルを選択し、 **[Is featured table]\(おすすめのテーブル\)** を **[はい]** に設定します。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="[Is featured table]\(おすすめのテーブル\) を [はい] に設定する":::

4. **[Set up this featured table]\(このおすすめのテーブルの設定\)** で、必須フィールドを指定します。

    - **[説明]** 。
    - **[行ラベル]** フィールド値は、ユーザーが行を簡単に識別できるようにするために Excel で使用されます。 これは、リンク セルのセル値として、また **[Data Selector]\(データ セレクター\)** ペインおよび **[情報]** カード内に表示されます。 
    - **[キー列]** フィールド値により、行の一意の ID が指定されます。 この値により、Excel でセルをテーブル内の特定の行にリンクすることが可能になります。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="おすすめのテーブルの設定":::

Power BI サービスに対してデータセットを発行またはインポートすると、Excel のデータ型ギャラリーにおすすめのテーブルが表示されます。

- Excel ではデータ型の一覧がキャッシュされるため、新しく発行されたおすすめのテーブルを表示するには、Excel を再起動する必要があります。
- 一部のデータセットはプレビュー段階ではサポートされておらず、これらのデータセット内で定義されているおすすめのテーブルは Excel に表示されません。 詳細については、「考慮事項と制限事項」をご覧ください。

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

- Excel には、新しい Power BI ワークスペースに格納されているおすすめのテーブルのみが表示されます。 クラシック ワークスペース、または個人用ワークスペースに格納されているおすすめのテーブルは、Excel ではデータ型として表示されません。 Power BI で[クラシック ワークスペースを新しいワークスペースにアップグレードする](service-upgrade-workspaces.md)ことができます。

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

- わからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

