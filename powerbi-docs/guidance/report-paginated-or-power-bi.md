---
title: どのようなときに Power BI のページ分割されたレポートを使用するか
description: Power BI のページ分割されたレポートを使用するのに適した場合のガイダンスです。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 2e048c3aa2ebc6e51388be652234c2ccf2348663
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886138"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>どのようなときに Power BI のページ分割されたレポートを使用するか

この記事の対象者は、Power BI 用のレポートをデザインするレポート作成者です。 どのような場合に [Power BI のページ分割されたレポート](../paginated-reports-report-builder-power-bi.md)を開発すればよいかを判断するときに役立つ推奨事項を示します。

> [!NOTE]
> Power BI のページ分割されたレポートを発行するには、Power BI Premium サブスクリプションが必要です。 レポートは、[ページ分割されたレポートのワークロードが有効になっている](../service-admin-premium-workloads.md#paginated-reports)専用容量のワークスペースにある場合にのみ表示されます。

Power BI のページ分割されたレポートは、**印刷**または **PDF 生成**に対して最適化されています。 また、高度に書式設定されたピクセル単位で完璧なレイアウトを作成する機能も提供されます。 したがって、ページ分割されたレポートは、販売請求書などの運用レポートに最適です。

それに対し、Power BI レポートは**探索と対話性**に最適化されています。 また、幅広い最新のビジュアルを使用してデータを提示することもできます。 このため、Power BI レポートは、レポート ユーザーがデータを探索し、関係やパターンを発見できるようにする、分析レポートに最適です。

次のような場合は、Power BI のページ分割されたレポートの使用を検討することをお勧めします。

* レポートを印刷するか、PDF ドキュメントとして出力する必要があることがわかっている場合。
* データ グリッド レイアウトが広がり、収まり切らなくなる可能性がある場合。 Power BI レポートのテーブルまたはマトリックスは、すべてのデータを表示するために動的にサイズ変更することができないことを考慮してください。代わりにスクロールバーが表示されます。 しかし、印刷した場合は、スクロールして見えていないデータを表示することはできません。
* 自分が必要とする機能が、Power BI のページ分割されたレポートにある場合。 そのようなレポート シナリオの多くについては、この記事で後ほど説明します。

## <a name="legacy-reports"></a>レガシ レポート

SQL Server Reporting Services (SSRS) の[レポート定義言語 (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) レポートが既にある場合は、それらを [Power BI レポート](../consumer/end-user-reports.md)として開発し直すか、ページ分割されたレポートとして Power BI に移行するかを選択できます。 詳細については、「[SQL Server Reporting Services レポートを Power BI に移行する](migrate-ssrs-reports-to-power-bi.md)」を参照してください。

Power BI ワークスペースに発行すると、ページ分割されたレポートと Power BI レポートを並用できるようになります。 その後、[Power BI アプリ](../service-create-distribute-apps.md)を使用して簡単に配布できます。

移行するのではなく、SSRS レポートの再開発を検討することがあります。 特に、分析エクスペリエンスの提供を目的としたレポートに当てはまります。 このような場合、Power BI レポートの方が優れたレポート ユーザー エクスペリエンスを提供する可能性があります。

## <a name="paginated-report-scenarios"></a>ページ分割されたレポートのシナリオ

Power BI のページ分割されたレポートを開発せざるを得ない多くのシナリオがあります。 多くは、Power BI レポートではサポートされていない機能です。

* **印刷対応**: ページ分割されたレポートは、印刷または PDF の生成に対して最適化されています。 データ領域は、必要に応じて、制御された方法で複数のページに拡張およびオーバーフローできます。 レポート レイアウトでは、余白、ページ ヘッダー、ページ フッターを定義できます。
* **表示形式**: Power BI では、ページ分割されたレポートをさまざまな形式で表示できます。 Microsoft Excel、Microsoft Word、Microsoft PowerPoint、PDF、CSV、XML、MHTML などの形式を使用できます。 (Power BI サービスでは、レポートを表示するために MHTML 形式が使用されます)。レポート ユーザーは、自分に適した形式でエクスポートできます。
* **高精度のレイアウト**: 高度に書式設定されたピクセル単位で完璧なレイアウトを、インチまたはセンチメートルの単位で構成した正確なサイズと位置でデザインできます。
* **動的レイアウト**: 多くのレポート プロパティを設定して VB.NET の式を使用することにより、応答性の高いレイアウトを作成できます。 式では、多くのコア .NET Framework ライブラリにアクセスできます。
* **レンダリング固有のレイアウト**: 式を使用して、レポートのレイアウトを適用されたレンダリング形式に基づいて変更できます。 たとえば、PDF などの非対話形式を使用して表示されたときは、表示の切り替え (ドリルダウンとドリルアップの実現) を無効にするように、レポートをデザインできます。
* **ネイティブ クエリ**: Power BI データセットを最初に開発する必要はありません。 任意の[サポートされているデータ ソース](../paginated-reports-data-sources.md)に対して、ネイティブ クエリを作成 (またはストアド プロシージャを使用) することができます。 クエリにはパラメーター化を含めることができます。
* **グラフィック クエリ デザイナー**: Power BI Report Builder には、データセットのクエリの作成とテストに役立つグラフィック クエリ デザイナーが用意されています。
* **静的データセット**: データセットを定義し、レポート定義にデータを直接入力することができます。 この機能は、デモをサポートしたり、概念実証 (POC) を提供したりする場合に、特に役立ちます。
* **データ統合**: 異なるデータ ソースのデータを組み合わせたり、静的データセットのデータと組み合わせることができます。 これを行うには、VB.NET の式を使用してカスタム フィールドを作成します。
* **パラメーター化**: データドリブン パラメーターやカスケード型パラメーターなど、高度にカスタマイズされたパラメーター化エクスペリエンスを設計できます。 パラメーターの既定値を定義することもできます。 レポート ユーザーが適切なフィルターをすばやく設定できるように、これらのエクスペリエンスを設計できます。 また、パラメーターでは、レポート データをフィルター処理する必要はありません。"what-if" シナリオまたは動的フィルターやスタイル設定をサポートするために使用できます。
* **画像データ**: 画像がデータ ソースにバイナリ形式で格納されている場合は、レポートで画像を表示できます。
* **カスタム コード**: レポートで VB.NET 関数のコード ブロックを作成し、任意のレポート式で使用できます。
* **サブレポート**: Power BI のページ分割されたレポートを、(同じワークスペースにある) 他のレポートに埋め込むことができます。
* **柔軟なデータ グリッド**: Tablix データ領域を使用して、グリッド レイアウトをきめ細かく制御できます。 入れ子になったグループや隣接するグループなど、複雑なレイアウトもサポートされています。 また、複数のページに印刷するときに、見出しを繰り返すように構成できます。 さらに、サブレポートや他の視覚エフェクト (データ バー、スパークライン、インジケーターなど) を埋め込むこともできます。
* **空間データ型**: マップ データ領域では、[SQL Server の空間データ型](/sql/relational-databases/spatial/spatial-data-sql-server)を視覚化できます。 そのため、GEOGRAPHY および GEOMETRY データ型を使用して、点、線、または多角形を視覚化できます。 ESRI 図形ファイルで定義された多角形を視覚化することもできます。
* **最新のゲージ**: 放射状ゲージと線形ゲージを使用して、KPI の値と状態を表示できます。 グリッド データ領域に埋め込んだり、グループ内で繰り返したりすこともできます。
* **HTML 表示**: HTML として格納されていると、さまざまな書式でテキストを表示できます。
* **差し込み印刷**: テキスト ボックスのプレースホルダーを使用して、データ値をテキストに挿入できます。 これにより、差し込み印刷レポートを作成できます。
* **対話機能**: 対話機能には、表示の切り替え (ドリルダウンとドリルアップの実現)、リンク、対話形式での並べ替え、ツールヒントなどがあります。 また、Power BI レポートや他の Power BI ページ分割レポートにドリルスルーするリンクを追加することもできます。 リンクでは、同じレポート内の別の場所に移動することもできます。
* **サブスクリプション**:Power BI では、ページ分割されたレポートを、サポートされる任意の形式のレポート添付ファイルとして、スケジュールに従って電子メールで配信できます。
* **ユーザーごとのレイアウト**: レポートを開く認証されたユーザーに基づいて、応答性の高いレポート レイアウトを作成できます。 異なる方法でデータをフィルター処理したり、データ領域や視覚エフェクトを非表示にしたり、異なる書式を適用したり、ユーザー固有のパラメーターの既定値を設定したりするように、レポートをデザインできます。

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

* [Power BI Premium のページ分割されたレポートとは](../paginated-reports-report-builder-power-bi.md)
* Guy in a Cube 動画:[Power BI でのページ分割されたレポートの概要](https://www.youtube.com/watch?v=wfqn45XNK3M)
* [SQL Server Reporting Services レポートを Power BI に移行する](migrate-ssrs-reports-to-power-bi.md)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
* Power BI チームへのご提案は、 [Power BI を改善するためのアイデアをお寄せください](https://ideas.powerbi.com)
