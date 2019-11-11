---
title: Power BI レポート サーバーの新機能
description: Power BI レポート サーバーの新機能について説明します。 これは主要な機能領域を網羅しており、新しいアイテムがリリースされるたびに更新されます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: 526a971817c50599bf77ae085f3d5ff07294b25b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858757"
---
# <a name="whats-new-in-power-bi-report-server"></a>Power BI レポート サーバーの新機能

Power BI Report Server と Power BI Report Server 向けに最適化された Power BI Desktop の新機能について説明します。 この記事は主要な機能領域を網羅しており、新しいリリースのたびに更新されます。

関連するPower BI の最新情報については、以下を参照してください。

* [Power BI サービスの新機能](../service-whats-new.md)
* [Power BI Desktop の新機能](../desktop-latest-update.md)
* [Power BI 用モバイル アプリの新機能](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="september-2019"></a>2019 年 9 月

すべての新機能の詳細については、「[Power BI Report Server September 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/)」というブログ記事を参照してください。

Power BI Report Server の 2019 年 9 月の更新には、多くの Power BI レポート機能が含まれています。 特に重要な機能には次のものがあります。

- **スライサー用のビジュアルレベル フィルター** スライサーにビジュアルレベル フィルターを追加できます。 他のビジュアルレベル フィルターと同じように動作します。スライサー自体をフィルタリングし、他のビジュアルはフィルタリングされません。 このフィルターは、空白を除外するためや、メジャー フィルターを使用する場合に便利です。
- **テーブルとマトリックスのためのアイコン セット** KPI アイコンを利用することで、Excel のアイコン セットと同じように、テーブルとマトリックスにさまざまなアイコン セットを表示するためのルールを設定できます。
- **ビジュアルのグループ化** PowerPoint のように、ビジュアル、図形、テキスト ボックス、画像、ボタンをグループにし、1 つのレポート ページにまとめることができるようになりました。 オブジェクトをグループにまとめると、まとめて移動させたり、サイズを変更したりできます。 グループ化すると、ページごとにたくさんのオブジェクトからなる層が形成され、レポートでの作業が簡単になります。
- **新しい既定のテーマ** Microsoft では、新しいテーマの JSON オプションに合うように、レポートに利用できるテーマを更新し、新しいレポートの既定のテーマを変更しています。 新しい既定のテーマは Microsoft のデザイン言語との相性が良く、ビジュアルのための最良のデザイン手法に従います。 
- **新しくなったウィンドウ デザイン** インターフェイスの大部分を新しくしました。 すべてのウィンドウ、フッター、ビュー スイッチャーを明るい色に変更し、余白設定を変更し、新しいアイコンを導入しました。 この新しいデザインは、インターフェイス全体を新しくするための最初の一歩です。

機能の完全な一覧は次のようになります。 

### <a name="reporting"></a>レポート

- 新しくなったウィンドウ デザイン
- スライサー用のビジュアル レベル フィルター
- パフォーマンス アナライザー ウィンドウの並べ替え
- ビジュアル ヘッダー ツールヒント
- テーブルとマトリックスの合計ラベルのカスタマイズ
- 階層スライサーのスライサー同期のサポート
- ビジュアル間で一貫性のあるフォント サイズ
- テーブルとマトリックスのアイコン セット
- ルールによる条件付き書式設定のパーセントのサポート
- 新しいフィルター ウィンドウが一般公開されました
- 散布図上で再生軸を使用する場合のデータ色のサポート
- 相対日付とドロップダウン スライサーを使用した場合のパフォーマンスの向上
- ビジュアルのグループ化
- テーマでの色とテキストのクラス
- 新しい既定のテーマ

### <a name="analytics"></a>分析

- カスタム書式設定文字列
- 書式設定オプションの条件付き書式の更新

    - ビジュアルの背景とタイトルの色
    - カードの色
    - ゲージの塗りつぶしと色
    - 代替テキスト
    - 罫線の色

- 条件付き書式の警告
- ドリルスルー探索機能の向上
- 新しい DAX 式:REMOVEFILTERS と CONVERT
- 新しい == DAX 比較演算子

### <a name="data-preparation"></a>データ準備

- M Intellisense の改善
- 新しい変換:位置による列の分割
- データ プロファイルからクリップボードへのコピー


## <a name="may-2019-power-bi-desktop-for-power-bi-report-server"></a>2019 年 5 月:Power BI Report Server 向け Power BI Desktop

すべての新機能の詳細については、「[Power BI Report Server May 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/)」というブログ記事を参照してください。

このリリースの特に重要な機能には次のものがあります。

### <a name="performance-analyzer"></a>パフォーマンス アナライザー 

レポートの実行速度が予想よりも遅い場合、Power BI Desktop でパフォーマンス アナライザーをお試しください。 これを開始すると、レポート内で行うあらゆるアクションに関する情報が含まれるログ ファイルが作成されます。 パフォーマンス アナライザーの詳細は[こちら](../desktop-performance-analyzer.md)で参照してください。

### <a name="new-modeling-view"></a>新しいモデリング ビュー

Power BI Desktop の新しいモデルリング ビューでは、多くのテーブルを含む複雑なデータセットを表示し、操作できます。 特に重要な機能には、複数の図からなるレイアウトと列、メジャー、テーブルの一括編集があります。 モデリング ビューの詳細は[こちら](../desktop-modeling-view.md)で参照してください。

### <a name="accessible-visual-interaction"></a>アクセス可能なビジュアルの相互作用

キーボード ナビゲーションを使用し、さまざまな組み込みビジュアル上のデータ ポイントにアクセスできるようになりました。 Power BI レポートのアクセシビリティの詳細は[こちら](../desktop-accessibility.md)で参照してください。

### <a name="conditional-formatting-titles-and-web-url-actions"></a>条件付き書式設定タイトルと Web URL アクション

Power BI レポートは対話式です。 レポートの現在の状態が反映されるよう、レポートのタイトルが動的に変化すれば理にかないます。 同じ式バインドの書式設定を利用し、ボタン、図形、画像の URL を動的に変化させることができます。 式ベースのタイトルの詳細は[こちら](../desktop-conditional-format-visual-titles.md)で参照してください。

### <a name="cross-highlight-by-axis-labels"></a>軸ラベルによるクロス強調表示

ビジュアル内で軸カテゴリ ラベルを選択すると、ビジュアル内でデータ ポイントを選択する場合と同じように、ページ上の他の要素が強調表示されます。 クロス強調表示の詳細は[こちら](../power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting)で参照してください。

### <a name="all-the-new-features"></a>すべての新機能

新機能の全一覧は次のようになります。

### <a name="reporting"></a>レポート

- 折れ線グラフの一点でクロス強調表示 
- タイトルを右端で折り返す 
- クロスフィルターの既定の視覚的相互作用を更新
- ビジュアルの境界線の角を丸くする 
- 単一選択スライサー  
- Bing 地図のヒートマップ サポート  
- 軸ラベルによるクロス強調表示  
- 既定のヒントの書式設定  
- ボタン、図形、イメージに対する静的 Web URL サポート  
- ページの配置オプション   
- 選択ウィンドウの改善  
- アクセス可能なビジュアルの相互作用  
- ビジュアルのタイトルの条件付き書式  
- ボタン、図形、イメージ用の Web URL アクションの条件付き書式
- パフォーマンス アナライザー ウィンドウ
- テーブルとマトリックスのキーボード ナビゲーション
- 行のデータ ラベルの位置コントロール
- KPI ビジュアル インジケーターのテキスト サイズ コントロール

### <a name="analytics"></a>分析

- 日付の階層表示の一般提供が開始  

### <a name="modeling"></a>モデリング

- 新しいモデリング ビューの一般提供が開始
- 新しい DAX 関数
- ALLSELECTED DAX 関数に対する更新
- 新しいレポート用の自動日付テーブルの無効化

## <a name="may-2019-power-bi-report-server"></a>2019 年 5 月:Power BI Report Server

### <a name="support-for-trusted-visuals"></a>信頼されたビジュアルのサポート

信頼されたビジュアルのサポートが Power BI Report Server に追加されました。 現在のところ、Mapbox と PowerOn のビジュアルがサポートされています。 ESRI、Visio、PowerApps は今回のリリースではサポートされていません。

### <a name="improved-security-features"></a>改善されたセキュリティ機能

**RestrictedResourceMimeTypeForUpload**。管理者はこれを利用し、text/html のように、禁止する MIME の種類をコンマ区切りの一覧で指定できます。

## <a name="january-2019"></a>2019 年 1 月

Power BI レポートでは、次の機能がサポートされています。

[**行レベルのセキュリティ**](row-level-security-report-server.md) Power BI Report Server を使用して行レベルのセキュリティ (RLS) を設定すると、特定のユーザーについてデータ アクセス権を制限することができます。 フィルターでは行レベルでデータ アクセスが制限され、ロール内でフィルターを定義することができます。

[**マトリックス行ヘッダーでの展開と折りたたみ**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse) 個々の行ヘッダーの展開/折りたたみ機能を追加しました。これは最も要望の多かったビジュアル機能の 1 つです。

[ **.pbix ファイル間でのコピーと貼り付け**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste) .pbix ファイル間で、ビジュアルをコピーして (ビジュアルのコンテキスト メニューまたは標準的な Ctrl + C キーボード ショートカットを使用)、それを別のレポートに貼り付ける (Ctrl + V キーを使用) ことができます。

[**スマート配置ガイド**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides) レポートのページ上でオブジェクトを移動するときにスマート配置ガイドが表示され (PowerPoint で表示されるように)、ページ上で行うあらゆる配置が楽に行えます。 ご利用のページ上で何かをドラッグまたはサイズ変更する場合は常にスマート ガイドが表示されます。 オブジェクトを別のオブジェクトの近くに移動する場合、移動するオブジェクトは他方のオブジェクトと揃えられた位置に配置されます。

**アクセシビリティ機能**一覧されるアクセシビリティ機能が多すぎます: たとえば、[フィールド一覧ペインのアクセシビリティ サポート](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList)。 フィールド一覧ペインには、完全にアクセスできます。 キーボードとスクリーン リーダーを使用するだけで、ウィンドウ内を移動することができ、さらにコンテキスト メニューを使用することで、ご利用のレポート ページにフィールドを追加できます。

#### <a name="custom-visuals"></a>カスタム ビジュアル

- このリリースに付属する API バージョンは 2.3 です。

### <a name="administrator-settings"></a>管理者の設定

管理者は、サーバー ファームの SSMS 詳細プロパティで、次のプロパティを設定できます。

**AllowedResourceExtensionsForUpload** レポート サーバーにアップロードできるリソースの拡張子を設定します。 &ast;.rdl や &ast;.pbix などの組み込みのファイル形式に対する拡張子を含める必要はありません。 既定値は、“&ast;、&ast;.xml、&ast;.xsd、&ast;.xsl、&ast;.png、&ast;.gif、&ast;.jpg、&ast;.tif、&ast;.jpeg、&ast;.tiff、&ast;.bmp、&ast;.pdf、&ast;.svg、&ast;.rtf、&ast;.txt、&ast;.doc、&ast;.docx、&ast;.pps、&ast;.ppt、&ast;.pptx” です。 

**SupportedHyperlinkSchemes** レンダリングが許可されるハイパーリンク アクション上で定義することが許可される URI スキームのコンマ区切り一覧を設定するか、すべてのハイパーリンク スキームを有効にする “&ast;” を設定します。 たとえば、"http,https" を設定した場合、"https://www. contoso.com” へのハイパーリンクは許可されますが、“mailto:bill@contoso.com” または “javascript:window.open(‘www.contoso.com’, ‘_blank’)” へのハイパーリンクは削除されます。 既定値は “&ast;” です。

## <a name="august-2018"></a>2018 年 8 月

2018 年 8 月に、Power BI Report Server 向けに最適化された Power BI Desktop のバージョンに多くの新しい機能が追加されます。 それらは次の領域に分類されます。

- [レポート](#reporting)
- [分析](#analytics)
- [モデリング](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>2018 年 8 月リリースの重要なポイント

ここでは、数多くのすべての新機能から特に興味深い機能を紹介します。 詳細については、こちらの[ブログ記事](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/)を参照してください。

#### <a name="report-theming"></a>レポートのテーマ

2018 年 8 月リリースの Power BI Report Server にレポートのテーマが追加されました。これにより、テーマや会社のブランドに合わせてレポート全体をすばやく色付けすることができます。 テーマをインポートすると、テーマの色を使用するためにすべてのグラフが自動的に更新され、カラー パレットからテーマの色にアクセスすることができます。 **[テーマの切り替え]** ボタンの下にある **[テーマのインポート]** オプションを使用して、テーマ ファイルをアップロードすることができます。

テーマ ファイルは JSON ファイルであり、ビジュアルに適用する既定の書式設定と共に、レポートで使用するすべての色が含まれます。
ここでは、レポートの既定の色を更新するだけのシンプルな JSON テーマのサンプルを示します。

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>異なるフィールドによる条件付き書式設定

モデルでの異なるフィールドによる列の書式設定機能は、条件付き書式設定について大幅に改善されたものの 1 つです。

#### <a name="conditional-formatting-by-values"></a>値による条件付き書式設定

条件付き書式設定の新しい種類として、**フィールド値に基づく書式設定**というものもあります。 フィールド値に基づく書式設定では、16 進コードまたは名前で色を指定し、その色を背景またはフォントの色に適用するメジャーまたは列を使用することができます。

#### <a name="report-page-tooltips"></a>レポート ページのヒント

レポート ページのヒント機能は、Power BI Report Server の 2018 年 8 月の更新プログラムに含まれています。 この機能を利用して、レポートで他のビジュアル用のカスタム ヒントとして使用するレポート ページをデザインできます。

#### <a name="log-axis-improvements"></a>ログ軸の改善

デカルト グラフ内のログ軸が大幅に改善されました。 完全に正または完全に負のデータがある場合、複合グラフを含むデカルト グラフの数値軸に対して、ログ スケールを選択できるようになりました。

#### <a name="sap-hana-sso-direct-query"></a>SAP HANA SSO 直接クエリ

Kerberos での SAP HANA SSO 直接クエリのサポートが Power BI レポートで利用できるようになりました。

>[!Note]
>Power BI Desktop で作成されたレポートでリレーショナル データ ソースとして SAP HANA が扱われる場合にのみ、このシナリオがサポートされます。  Power BI Desktop でこれを有効にするには、[オプション] の下にある DirectQuery メニューで、[SAP HANA をリレーショナル ソースとして扱う] チェック ボックスをオンにして [OK] をクリックします。

#### <a name="custom-visuals"></a>カスタム ビジュアル

- このリリースに付属する API バージョンは 1.13.0 です。

- 現在、カスタム ビジュアルは、サーバー API の現在のバージョン (利用可能な場合) と互換性のある以前のバージョンにフォールバックできます。

### <a name="reporting"></a>レポート 

- [レポートのテーマ](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [アクションをトリガーするボタン](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [複合グラフの線のスタイル](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [ビジュアルの既定の並べ替えの改善](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [数値のスライサー](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [高度なスライサー同期](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [ログ軸の改善](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [じょうごグラフのデータ ラベル オプション](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [ストロークの幅をゼロに設定する](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [レポートに対するハイ コントラストのサポート](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [ドーナツの半径のコントロール](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [円とドーナツの詳細ラベルの位置コントロール](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [複合グラフのメジャーごとの各データ ラベルの書式設定](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [柔軟性と書式設定が改善された新しいビジュアル ヘッダー](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [壁紙の書式設定](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [テーブルとマトリックスに関するヒント](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [ビジュアルのツールヒントをオフにする](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [スライサーのアクセシビリティ](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [書式設定ウィンドウの改善](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [折れ線グラフと複合グラフの階段状折れ線のサポート](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [並べ替え機能の改善](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [[PDF にエクスポート] でのレポートの印刷 (Power BI Desktop)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [ブックマーク グループの作成](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [スライサーの修正](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [レポート ページのヒント](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>分析

- [新しい DAX 関数:COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [ドリルスルーの測定](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [異なるフィールドによる条件付き書式設定](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [値による条件付き書式設定](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>モデリング

- [データ ビューでのフィルター処理と並べ替え](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [改善されたロケールの書式設定](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [メジャー用のデータ カテゴリ](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [統計の DAX 関数](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>2018 年 5 月

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>レポート サーバー向け Power BI iOS モバイル アプリをリモート構成する

IT 管理者は、組織の MDM ツールを使用し、レポート サーバーへの Power BI iOS モバイル アプリのアクセスをリモートで構成できるようになりました。 詳細については、「[Configure Power BI iOS mobile app access to a report server remotely](configure-powerbi-mobile-apps-remote.md)」 (リモートでレポート サーバーへの Power BI iOS モバイル アプリのアクセスを構成する) を参照してください。

## <a name="march-2018"></a>2018 年 3 月

2018 年 3 月に、Power BI Report Server 向けに最適化された Power BI Desktop のバージョンに数多くの新しい機能が追加されます。 それらは次の領域に分類されます。

- [ビジュアル](#visuals-updates)
- [レポート](#reporting)
- [分析](#analytics)
- [パフォーマンス](#performance)
- [レポート サーバー](#report-server)
- [その他](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>2018 年 3 月リリースの重要なポイント

ここでは、数多くのすべての新機能から特に興味深い機能を紹介します。

#### <a name="rule-based-conditional-formatting-for-table-and-matrixhttpspowerbimicrosoftcomblogpower-bi-desktop-november-2017-feature-summaryconditionalformatting"></a>[テーブルとマトリックス用のルール ベースの条件付き書式](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

テーブルまたはマトリックスの特定のビジネス ロジックに基づいて、列の背景またはフォントの色を条件付きで色付けするルールを作成します。

#### <a name="show-and-hide-pageshttpspowerbimicrosoftcomblogpower-bi-desktop-january-2018-feature-summaryhidepages"></a>[ページの表示と非表示](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

閲覧者がレポートにアクセスできるようにしたいが、一部のページが完全に完成していない場合があります。 そのページの準備ができるまで非表示にできるようになりました。 通常のナビゲーションからページを非表示にすることもできます。その場合、閲覧者はブックマークやドリルスルーを使用してページにアクセスできます。

#### <a name="bookmarkinghttpspowerbimicrosoftcomblogpower-bi-desktop-march-2018-feature-summarybookmarking"></a>[ブックマーク](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

ブックマークと言えば、レポートのデータでストーリーを伝えるブックマークを作成します。

- [ブックマークのクロス強調表示](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting):ブックマークには、ブックマークを作成した時点のレポート ページのクロス強調表示状態が維持され、表示されます。
- [ブックマークの柔軟性の向上](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility):ブックマークはレポートで設定したプロパティを反映し、選択したビジュアルのみに影響します。

#### <a name="multi-select-data-points-across-multiple-chartshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarycrosshighlight"></a>[複数のグラフにまたがってデータ ポイントを複数選択する](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

複数のグラフの複数のデータ ポイントを選択し、クロスフィルター処理をページ全体に適用します。

#### <a name="sync-slicers-across-multiple-pages-of-your-reporthttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summarysyncslicers"></a>[レポートの複数のページにまたがってスライサーを同期する](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

スライサーは、レポート内の 1 ページ、2 ページ、またはそれ以上のページに適用できます。

#### <a name="quick-measureshttpspowerbimicrosoftcomblogpower-bi-desktop-february-2018-feature-summaryquickmeasures"></a>[クイック メジャー](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

テーブル内の既存のメジャーと数値列に基づいて新しいメジャーを作成します。

#### <a name="drilling-down-filters-other-visualshttpspowerbimicrosoftcomblogpower-bi-desktop-december-feature-summarydrillfiltersothervisuals"></a>[他のビジュアルに詳細なフィルターを適用する](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

1 つのビジュアルの特定のカテゴリをドリルダウンする場合、同じカテゴリでページのすべてのビジュアルをフィルター処理することができます。

### <a name="visuals-updates"></a>ビジュアルの更新

- [テーブルとマトリックスのセルの配置](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [テーブルとマトリックスの列の表示単位と精度のコントロール](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [横棒グラフと縦棒グラフのオーバーフロー データ ラベル](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [デカルトのデータ ラベルの背景色を制御し、ビジュアルをマッピングする](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [棒/列の余白を調整する](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [グラフの軸ラベルに使用される領域を増やす](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [X 軸と Y 軸のグループ化からの散布ビジュアル](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [緯度と経度に基づくマップの高密度サンプリング](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [レスポンシブ スライサー](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [相対日付スライサーのアンカー日付を追加する](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>レポート

- [レポートの読み取りモードでビジュアル ヘッダーをオフにする](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [低速なデータ ソース向けのレポート オプション](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [強化された既定のビジュアル配置](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [選択ウィンドウで視覚順を制御する](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [レポートでオブジェクトをロックする](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [書式設定および分析ウィンドウで検索する](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [フィールドのプロパティ ウィンドウとフィールドの説明](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>分析

- [UTCNOW() と UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [カスタム日付テーブルのマーキング](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [他のビジュアルの詳細フィルター](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [複数の行カードに対する多次元 AS モデルのセル レベルの書式設定](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>パフォーマンス

- [フィルター処理のパフォーマンスの向上](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [DirectQuery のパフォーマンスの向上](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [開く動作と保存のパフォーマンス向上](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [[データのない項目を表示する] の改善](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>レポート サーバー

#### <a name="export-to-accessible-pdf"></a>アクセス可能な PDF へのエクスポート

ページ分割された (RDL) レポートを PDF にエクスポートする際に、アクセス可能な/タグ付けされた PDF ファイルを取得できるようになりました。 サイズは大きくなりますが、スクリーン リーダーやその他の支援技術による読み取りや移動が容易になります。 アクセス可能な PDF を有効にするには、**AccessiblePDF** デバイス情報の設定を **True** に指定します。 「[PDF デバイス情報の設定](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings)」と「[デバイス情報設定の変更](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings)」を参照してください。

### <a name="other-improvements"></a>その他の改良

- [[例から列を追加する] の改善](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [[コンサルティング サービス] クイック リンク](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [エラー レポートの改善](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [以前に発生したエラーの表示](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>2017 年 10 月

### <a name="power-bi-report-data-sources"></a>Power BI レポート データ ソース

Power BI Report Server の Power BI レポートは、さまざまなデータ ソースに接続できます。 データをインポートしてデータ更新スケジュールを設定したり、DirectQuery または SQL Server Analysis Services へのライブ接続を使って直接クエリを実行したりできます。 スケジュールされた更新および DirectQuery をサポートするデータ ソースの一覧については、「Power BI Report Server での Power BI レポート データ ソース」をご覧ください。

### <a name="scheduled-data-refresh-for-imported-data"></a>インポートしたデータのスケジュールされたデータ更新

Power BI Report Server では、スケジュールされたデータ更新をセットアップして、ライブ接続や DirectQuery ではなく埋め込みモデルで、Power BI レポートのデータを最新の状態に保つことができます。 埋め込みモデルではデータをインポートするので、元のデータ ソースからは切断されています。 データを最新の状態に保つにはデータを更新する必要があり、スケジュールされた更新はそのための方法です。 Power BI Report Server での Power BI レポートのスケジュールされた更新に関する記事をご覧ください。

### <a name="editing-power-bi-reports-from-the-server"></a>サーバーからの Power BI レポートの編集

サーバーから Power BI レポート (.pbix) ファイルを開いて編集できますが、取得されるのはアップロードした元のファイルです。  つまり、**サーバーによってデータが更新された場合、ファイルを初めて開いたときには、データは更新されません**。 変更を反映するには、手動でローカルにファイルを更新する必要があります。

### <a name="large-file-uploaddownload"></a>大きいファイルのアップロード/ダウンロード

アップロードできるファイルの最大サイズは 2 GB ですが、SQL Server Management Studio (SSMS) のレポート サーバーの設定では、既定で 1 GB に制限されています。  これらのファイルは SharePoint 用の場合と同様にデータベースに格納され、SQL Server カタログ用の特別な構成は必要ありません。  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>OData フィードとしての共有データセットへのアクセス

OData フィードを使って Power BI Desktop から共有データセットにアクセスできます。 詳細については、「[Power BI Report Server で OData フィードとして共有データセットにアクセスする](access-dataset-odata.md)」をご覧ください。

### <a name="scale-out"></a>スケールアウト

このリリースでは、スケールアウトがサポートされています。ロード バランサーを使って、最良のエクスペリエンスになるようにサーバーのアフィニティを設定します。 シナリオはまだスケールアウト対応に最適化されていないため、モデルが複数のノードにレプリケートされる可能性があることに注意してください。 シナリオは、ネットワーク ロード バランサーと固定セッションがなくても機能します。 ただし、モデルが N 回読み込まれるのでノード間でメモリの過剰使用が発生するだけでなく、要求の間に新しいノードに達するとモデルがストリーミングされるため、接続の間でパフォーマンスが低下します。  

### <a name="administrator-settings"></a>管理者の設定

管理者は、サーバー ファームの SSMS 詳細プロパティで、次のプロパティを設定できます。

* EnableCustomVisuals:True/False
* EnablePowerBIReportEmbeddedModels:True/False
* EnablePowerBIReportExportData:True/False
* MaxFileSizeMb:既定値が 1000 になりました
* ModelCleanupCycleMinutes:メモリからのモデルの削除をチェックする頻度
* ModelExpirationMinutes:最終使用時刻に基づく、モデルの有効期限が切れて削除されるまでの時間
* ScheduleRefreshTimeoutMinutes:モデルのデータ更新にかけられる時間。 既定では 2 時間です。  ハード上限はありません。

**構成ファイル rsreportserver.config**

```xml
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>開発者 API

SSRS 2017 に導入された開発者 API (REST API) が、Power BI Report Server で Excel ファイルと .pbix ファイルの両方を使うことができるように拡張されました。 プログラムでサーバーからファイルをダウンロードし、更新してから再発行するといったユース ケースが考えられます。 たとえば、これは PowerPivot モデルを含む Excel ブックを更新する唯一の方法です。

大きいファイル用に別の新しい API があることに注意してください。これは、Swagger の Power BI Report Server バージョンで更新されます。 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) と Power BI Report Server のメモリ使用量

Power BI Report Server は、SQL Server Analysis Services (SSAS) を内部的にホストするようになりました。 これは、スケジュールされた更新に限ったことではありません。 SSAS をホストすることで、レポート サーバーのメモリ使用量を大幅に拡張できます。 サーバー ノードでは AS.ini 構成ファイルを使うことができるので、SSAS に慣れている場合は、最大メモリ制限やディスク キャッシュなどの設定を更新できます。詳細については、「[Server properties in Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services)」(Analysis Services でのサーバー プロパティ) をご覧ください。

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Excel ブックの表示と操作

Excel と Power BI には、業界で他に類を見ないツール ポートフォリオが含まれています。 併用することで、企業のアナリストはデータをより簡単に収集し、整理し、分析し、視覚的に調査できます。 Web ポータルで Power BI レポートを表示することに加え、Power BI Report Server では、ビジネス ユーザーは Excel ブックで同じことができるようになりました。セルフサービスの Microsoft BI コンテンツを 1 か所で公開し、表示します。

[Power BI Report Server のプレビュー環境に Office Online Server (OOS) を追加する方法を紹介したチュートリアル](excel-oos.md)を公開しています。 ボリューム ライセンス アカウントのお客様は Volume License Servicing Center から閲覧専用機能を持つ OOS を無料でダウンロードできます。 構成後、次のような Excel ブックを表示し、操作できます。

* 外部データ ソースとの依存関係がない
* 外部 SQL Server Analysis Services データ ソースにライブ接続している
* PowerPivot データ モデルがある

### <a name="support-for-new-table-and-matrix-visuals"></a>新しいテーブルとマトリックス ビジュアルのサポート

Power BI Report Server は、Power BI の新しいテーブル ビジュアルとマトリックス ビジュアルをサポートするようになりました。 これらのビジュアルでレポートを作成するには、2017 年 10 月リリース向けに更新された Power BI Desktop リリースが必要です。 Power BI Desktop (2017 年 6 月) リリースと並列インストールすることはできません。 Power BI Desktop の最新バージョンについては、[Power BI Report Server のダウンロード ページ](https://powerbi.microsoft.com/report-server/)で、 **[ダウンロードの詳細オプション]** を選んでください。

## <a name="june-2017"></a>2017 年 6 月

* Power BI Report Server が一般公開 (GA) されました。

## <a name="may-2017"></a>2017 年 5 月

* Power BI レポート サーバー プレビューが利用可能
* Power BI レポートをオンプレミスで公開する機能
  * カスタム ビジュアルのサポート
  * サポートされるのは **Analysis Services のライブ接続**のみです。今後、さらに多くのデータ ソースがサポートされる予定です。
  * Power BI レポート サーバーでホストされている Power BI レポートを表示するように Power BI モバイル アプリを更新
* レポートにコメントを含めてコラボレーションを強化

## <a name="next-steps"></a>次の手順

次のソースをチェックして、Power BI Report Server の新機能に関する最新情報を常に把握してください。

* [Microsoft Power BI ブログ](https://powerbi.microsoft.com/blog/)
* [SQL Server Reporting Services チームのブログ](https://blogs.msdn.microsoft.com/sqlrsteamblog/)
* [Guy in a Cube の YouTube チャネル](https://aka.ms/guyinacube)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
