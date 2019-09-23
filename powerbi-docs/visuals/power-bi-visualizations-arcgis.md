---
title: 他のユーザーから共有された ArcGIS マップとの対話
description: Power BI のレポート コンシューマーとして読み取りビューで ArcGis マップを使用します
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/10/2019
ms.author: mihart
ms.openlocfilehash: 49eb11698d05ee8877f78b6b3d4cbbc6ef403e75
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61137090"
---
# <a name="interacting-with-arcgis-maps-in-power-bi"></a>Power BI での ArcGIS マップとの対話
このトピックは、Power BI サービス、Desktop、またはモバイルで ArcGIS マップを "*使用する*" ユーザーを対象として書かれています。 作成者から ArcGIS マップを共有された場合、さまざまな方法でそのマップと対話できます。  ArcGIS マップの作成の詳細については、[Esri の ArcGIS マップのチュートリアル](../visuals/power-bi-visualization-arcgis.md)をご覧ください。

ArcGIS マップと Power BI を組み合わせると、マッピングをマップ上のポイントの表現を越える、まったく新しいレベルに引き上げることができます。 基本マップ、場所の種類、テーマ、記号のスタイル、および参照レイヤーで使用可能なオプションを選択して、すばらしい有益なマップの視覚エフェクトを作成します。 空間分析を使用してマップ上で権限のあるデータのレイヤー (国勢調査データなど) を組み合わせることで、より深く理解できる視覚化されたデータを伝達します。

> [!TIP]
> GIS は Geographic Information System (地理情報システム) の略です。
> 

使用している例では、都市別の前年の売上を調べ、ストリート ベースマップとバブル シンボルを使って、サイズと平均世帯年収の参照レイヤーを表します。 マップには、3 つのピンと 1 つのドライブ時間半径 (紫) が含まれています。

![](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri-new.png)

> [!TIP]
> 多くの例やユーザーの声を参照するには、[Esri のページを Power BI で](https://www.esri.com/powerbi)アクセスしてください。 その後、Esri が提供する [Power BI の ArcGIS マップの概要ページ](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm)を参照してください。
> 
> 

<br/>

## <a name="user-consent"></a>ユーザーの同意
仕事仲間から初めて ArcGIS マップを共有されると、Power BI にプロンプトが表示されます。 ArcGIS Maps for Power BI は Esri (www.esri.com) によって提供されており、ArcGIS Maps for Power BI を利用するときは、Esri の使用条件およびプライバシー ポリシーが適用されます。 ArcGIS Maps for Power BI 視覚エフェクトの使用を希望する Power BI ユーザーは、同意ダイアログを受け入れる必要があります。

## <a name="selection-tools"></a>選択ツール
Power BI の ArcGIS マップでは 3 つの選択モードを使用できます。 一度に最大 250 のデータ ポイントを選ぶことができます。

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) 個々のデータ ポイントを選択します。

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) マップに四角形を描画し、含まれるデータ ポイントを選択します。 複数の四角形の領域を選ぶには、Ctrl キーを使います。

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) 参照レイヤー内で境界または多角形を使用して、含まれるデータ ポイントを選択することができます。

<br/>

## <a name="interacting-with-an-arcgis-map"></a>ArcGIS マップとの対話
使うことができる機能は、ユーザーが "*作成者*" (マップを作成したユーザー) か "*使用者*" (誰かから ArcGIS マップを共有されたユーザー) かによって異なります。 コンシューマー ([読み取りビュー](../consumer/end-user-reading-view.md)とも呼ばれる) として ArcGIS マップと対話する場合、以下の操作を使用できます。

* "*ビュー*" アクセス許可を持つ Premium コンシューマーである場合、[視覚化の作成に使用されるデータの確認](../consumer/end-user-show-data.md)、[サブスクライブ](../consumer/end-user-subscribe.md)、[フォーカス モードおよび全画面表示モード](../consumer/end-user-focus.md)でのマップの表示、[関連コンテンツの表示](../consumer/end-user-related.md)、"*レポート作成者*" によって設定された[フィルターとの対話](../consumer/end-user-report-filter.md)、[レポートの共有](../service-share-reports.md)などを行うことができます。

* その他の視覚化の種類と同様に、Power BI **Pro** コンシューマーでは、Premium のコンシューマーが実行できるすべてのことに加えて、[基になるデータのエクスポート](../visuals/power-bi-visualization-export-data.md)、[使用状況メトリックの取得](../service-usage-metrics.md)、コピーの保存と [Web への公開](../service-publish-to-web.md)などを実行できます。

    
* **[フィルター]** ウィンドウを展開し、フィルターを使ってマップを調べることができます。   
    ![](media/power-bi-visualizations-arcgis/power-bi-filter-newer.png)  
* マップに参照レイヤーがある場合は、場所を選んでヒントに詳細を表示できます。 次の図では、Adams 郡を選択し、作成者がマップに追加した平均世帯年収参照レイヤーのデータを表示しています。
  
    ![](media/power-bi-visualizations-arcgis/power-bi-reference-layer.png)  
  
    この場合、グラフも表示されます。 グラフのバーを選ぶと、詳しいデータが表示されます。 Adams 郡の 79 世帯が年収 200,000 ドル以上であることがわかります。
  
    ![](media/power-bi-visualizations-arcgis/power-bi-tooltip-chart.png)
  
    矢印を選んで任意の追加グラフを表示できます。
* ベースマップの場所記号をポイントすると、ヒントに詳細が表示されます。     
  ![](media/power-bi-visualizations-arcgis/power-bi-arcgis-hover.png)
  
  > [!TIP]
  > 特定の場所を選ぶには、ズーム インが必要な場合があります。  または、重複している場所がある場合は、Power BI により一度に複数のヒントが表示されることがあります。 ヒント間を移動するには、矢印を選びます。
  > 
  > ![](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)
  > 
  > 
* 作成者が ArcGIS マップにインフォグラフィックス レイヤーを追加している場合、マップの右上隅に追加データが表示されます。  たとえば、次の例ではマップ作成者が "Children under 14" を追加しています。
  
    ![](media/power-bi-visualizations-arcgis/power-bi-demographics.png)

## <a name="considerations-and-limitations"></a>考慮事項と制限事項
ArcGIS Maps for Power BI は、次のサービスとアプリケーションで使うことができます。

<table>
<tr><th>サービス/アプリ</th><th>使用できるかどうか</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>はい</td>
</tr>
<tr>
<td>Power BI サービス (app.powerbi.com)</td>
<td>はい</td>
</tr>
<tr>
<td>Power BI モバイル アプリケーション</td>
<td>はい</td>
</tr>
<tr>
<td>Power BI Publish to Web</td>
<td>いいえ</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>いいえ</td>
</tr>
<tr>
<td>Power BI サービスの埋め込み (PowerBI.com)</td>
<td>いいえ</td>
</tr>
</table>

**ArcGIS Maps for Power BI が連携するしくみ**
Power BI の ArcGIS マップは Esri (www.esri.com) によって提供されます。 Power BI の ArcGIS マップのご利用の際には、Esri の[使用条件](https://go.microsoft.com/fwlink/?LinkID=8263222)および[プライバシー ポリシー](https://go.microsoft.com/fwlink/?LinkID=826323)が適用されます。 Power BI の ArcGIS マップ ビジュアルの使用を希望される Power BI ユーザーは、同意ダイアログを受け入れる必要があります (詳細については「ユーザーの同意」をご覧ください)。  Esri の ArcGIS Maps for Power BI の使用には Esri の使用条件とプライバシー ポリシーが適用され、同意ダイアログからもリンクされています。 各ユーザーは、ArcGIS Maps for Power BI を初めて使う前に同意する必要があります。 ユーザーが同意すると、ビジュアルにバインドされたデータは少なくともジオコーディングのために Esri のサービスに送信され、マップで表すことができる緯度と経度の情報に場所情報が変換されます。 データの視覚エフェクトにバインドされているすべてのデータが Esri のサービスに送信されるものと想定する必要があります。 Esri は、基本マップ、空間分析、ジオコーディングなどのサービスを提供します。ArcGIS Maps for Power BI のビジュアルは、Esri によって提供および保持されている証明書によって保護された SSL 接続を使って、これらのサービスと対話します。 ArcGIS Maps for Power BI に関する追加情報は、Esri の [ArcGIS Maps for Power BI 製品ページ](https://www.esri.com/powerbi)から入手できます。

**Power BI Plus**    
![Plus アイコンを選択して、サインアップまたはサインインします](media/power-bi-visualizations-arcgis/power-bi-plus.png)

ユーザーが ArcGIS Maps for Power BI を通して Esri によって提供されている Plus サブスクリプションにサインアップすると、ユーザーは Esri と直接的な関係に入ります。 Power BI は、Esri にユーザーの個人情報を送信しません。 ユーザーは、自分の AAD ID を使って、Esri 提供の AAD アプリケーションにサインインして信頼します。 これにより、ユーザーは Esri と直接個人情報を共有します。 ユーザーが Plus コンテンツを ArcGIS Maps for Power BI のビジュアルに追加した場合、他の Power BI ユーザーもその内容を表示または編集するために Esri の Plus サブスクリプションが必要です。 

Esri の ArcGIS Maps for Power BI の仕組みの技術的な詳細については、サポート サイトから Esri に問い合わせてください。

**ArcGIS マップが表示されません。**     
ArcGIS Maps for Power BI を使うことができないサービスまたはアプリケーションでは、視覚エフェクトが Power BI のロゴを含む空のビジュアルとして表示されます。

**すべての情報がマップに表示されません**    
マップ上に緯度/経度をジオコーディングする際、最大 30,000 のデータ ポイントが表示されます。 便番号や住所などのデータ ポイントをジオコーディングする場合、ジオコード化されるのは最初の 15,000 データ ポイントのみです。 場所の名前または国のジオコード化は、1500 個の住所制限の対象には含まれません。

**Power BI の ArcGIS マップを使用する場合、料金はかかりますか。**

すべての Power BI ユーザーは追加コストなしで ArcGIS Map for Power BI を使うことができます。 これは **Esri** によって提供されるコンポーネントであり、ご利用の際には、この記事の前述のとおり、**Esri** が示す使用条件およびプライバシー ポリシーが適用されます。 ArcGIS **Plus** にサブスクライブすると、料金が発生します。

**キャッシュに空きがないというエラー メッセージが表示されます**

これは対処中のバグです。  それまでの間は、エラー メッセージに表示されるリンクを選んで、Power BI キャッシュをクリアする手順を参照してください。

**オフラインで自分の ArcGIS マップを表示できますか。**

いいえ、Power BI でマップを表示するには、ネットワーク接続が必要です。

## <a name="next-steps"></a>次の手順
ヘルプの表示:**Esri** は、**Power BI の ArcGIS マップ**の機能セットに関する[包括的なドキュメント](https://go.microsoft.com/fwlink/?LinkID=828772)を提供します。

[**Power BI の ArcGIS マップ**](https://go.microsoft.com/fwlink/?LinkID=828771)に関する Power BI コミュニティ スレッドで、質問、最新情報の検索、問題の報告、および回答の検索を行うことができます。


[Power BI の ArcGIS マップ製品ページ](https://www.esri.com/powerbi)
