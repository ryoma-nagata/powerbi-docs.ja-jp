---
title: Power BI ビジュアルのサンプル
description: この記事では、スライサー、20 種類を超えるグラフ、WebGL、および R のビジュアルとスクリプトを含むサンプルの Power BI ビジュアルを紹介します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/17/2019
ms.openlocfilehash: 5e2ad0fa43a186be76a58f1ab3bb4bf054a677a5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83132421"
---
# <a name="samples-of-power-bi-visuals"></a>Power BI ビジュアルのサンプル

これらの Power BI ビジュアルは、GitHub からダウンロードして、使用および変更することができます。 これらのサンプルは、Power BI を使用して開発するときによくある状況を処理する方法を示しています。

## <a name="slicers"></a>スライサー

スライサーを使用すると、レポートの他の視覚化に表示されるデータの一部を絞り込むことができます。 スライサーは、Power BI に複数用意されているデータのフィルター処理方法の 1 つです。

| <img src="media/samples/chiclet-slicer.png" width="200">  | <img src="media/samples/timeline-slicer.png" width="200"> | <img src="media/samples/sample-slicer.png" width="200">|
| ------------- | ------------- | -------------|
| [Chiclet Slicer (Chiclet スライサー)](https://github.com/Microsoft/powerbi-visuals-chicletslicer/)  </br>その他のビジュアルでキャンバス内フィルターとして動作する画像またはテキストのボタンを表示します | [タイムライン スライサー](https://github.com/Microsoft/powerbi-visuals-timeline/) </br>日付でフィルター処理するグラフィカル日付範囲セレクター | [スライサーのサンプル](https://github.com/Microsoft/powerbi-visuals-sampleslicer/) </br>高度なフィルター処理 API の使用方法を示します

## <a name="charts"></a>グラフ

横棒グラフ、円グラフ、ワード クラウドなどのギャラリーを参考にしてください。

| <img src="media/samples/aster-plot.png" width="200">  | <img src="media/samples/bullet-chart.png" width="200"> | <img src="media/samples/Chord.png" width="200">|
| ------------- | ------------- | -------------|
| [アスター プロット](https://github.com/Microsoft/powerbi-visuals-asterplot/)  </br>2 番目の値を使用して掃引角を決める、標準ドーナツ グラフ上のツイスト | [箇条書きグラフ](https://github.com/Microsoft/powerbi-visuals-bulletchart/) </br>目標の追跡に役立つコンテキストを提供する、追加の視覚要素を持つ横棒グラフ | [弦](https://github.com/Microsoft/powerbi-visuals-chord/) </br>マトリックスのデータ間の関係を表示するグラフィカル メソッド
| <img src="media/samples/dot-plot.png" width="200"> | <img src="media/samples/dual-kpi.png" width="200">| <img src="media/samples/enhanced-scatter.png" width="200"> 
| [ドット プロット](https://github.com/Microsoft/powerbi-visuals-dotplot/) </br>頻度の分布を見栄えよく表現します | [デュアル KPI](https://github.com/Microsoft/powerbi-visuals-dualkpi/) </br>2 つのメジャーを時系列で効率的に視覚化します。共同タイムライン上にそれらの傾向が表示されます | [強化された散布図](https://github.com/Microsoft/powerbi-visuals-enhancedscatter/) </br>既存の散布図に対する改善
| <img src="media/samples/forcegraph.png" width="200">| <img src="media/samples/gantt.png" width="200">| <img src="media/samples/table-heatmap.png" width="200">
| [フォース グラフ](https://github.com/Microsoft/powerbi-visuals-forcegraph/) </br>エンティティ間の接続を示すのに便利な、曲線軌道を使用したフォース レイアウト ダイアグラム | [ガント](https://github.com/Microsoft/powerbi-visuals-gantt/) </br>プロジェクトのタイムラインまたはスケジュールをリソースと共に示す横棒グラフ | [テーブル ヒートマップ](https://github.com/Microsoft/powerbi-visuals-heatmap/) </br>テーブルで色を使用してデータを簡単かつ直感的に比較します
| <img src="media/samples/histogram-chart.png" width="200"> | <img src="media/samples/linedot-chart.png" width="200"> | <img src="media/samples/mekko-chart.png" width="200"> 
| [ヒストグラム グラフ](https://github.com/Microsoft/powerbi-visuals-histogram/) </br>連続した間隔または特定の期間についてデータの分布を視覚化します | [LineDot グラフ](https://github.com/Microsoft/powerbi-visuals-linedotchart/) </br>対象ユーザーにデータに対する関心を起こさせる、アニメーション ドットで描かれたアニメーション折れ線グラフ | [Mekko chart](https://github.com/Microsoft/powerbi-visuals-mekkochart/) </br>100% 積み上げ縦棒グラフと 100% 積み上げ横棒グラフが同時に 1 つのビューに結合されました
| <img src="media/samples/multikpi.png" width="200"> | <img src="media/samples/powerkpi.png" width="200"> | <img src="media/samples/powerkpi-matrix.png" width="200"> 
| [Multi KPI](https://github.com/microsoft/PowerBI-visuals-MultiKPI/) </br> 主要な KPI と、サポート データの複数のスパークラインを備えた、強力なマルチ KPI 視覚化 | [Power KPI](https://github.com/microsoft/PowerBI-visuals-PowerKPI/) </br>複数折れ線グラフとラベルを使用し、現在の日付、値、差異を示す強力な KPI インジケーター | [累乗 KPI マトリックス](https://github.com/microsoft/PowerBI-visuals-PowerKPIMatrix/) </br>コンパクトで読みやすいリストで、バランスのとれたスコアカードと無制限の数のメトリックと KPI を監視します
| <img src="media/samples/pulse-chart.png" width="200">| <img src="media/samples/radar-chart.png" width="200"> | <img src="media/samples/sankey-chart.png" width="200"> 
| [パルス グラフ](https://github.com/Microsoft/powerbi-visuals-pulsechart/) </br>重要なイベントの注釈が付けられたこの折れ線グラフは、データでストーリーを伝えるのに最適です| [Radar chart (レーダー チャート)](https://github.com/Microsoft/powerbi-visuals-radarchart/) </br>カテゴリ軸にプロットされた複数のメジャーを表示します。これは、属性を比較するのに便利です | [Sankey グラフ](https://github.com/Microsoft/powerbi-visuals-sankey/) </br>系列の幅がフローの量に比例しているフロー ダイアグラム
| <img src="media/samples/stream-graph.png" width="200"> | <img src="media/samples/sunburst.png" width="200">| <img src="media/samples/tornado.png" width="200">
| [ストリーム グラフ](https://github.com/Microsoft/powerbi-visuals-streamgraph/) </br>平滑補間法を使用した積み上げ面グラフ。時間の経過と共に値を表示するためによく使用されます | [サンバースト グラフ](https://github.com/Microsoft/powerbi-visuals-sunburst/) </br>階層データを視覚化するための複数レベルのドーナツ グラフ| [トルネード チャート](https://github.com/Microsoft/powerbi-visuals-tornado/) </br>2 つのグループ間の変数の相対的重要度を比較します
 | <img src="media/samples/word-cloud.png" width="200">
 | [ワード クラウド](https://github.com/Microsoft/powerbi-visuals-wordcloud/) </br>データ内に頻出するテキストからおもしろいビジュアルを作成します

## <a name="webgl"></a>WebGL

WebGL では、Web コンテンツで OpenGL ES 2.0 に基づく API を使用して、HTML キャンバス内で 2D および 3D レンダリングを実行できます。

| <img src="media/samples/globe-map.png" width="250">|
| ------------- |
| [Globe Map](https://github.com/Microsoft/powerbi-visuals-globemap/) </br>インタラクティブな 3D マップ上の場所をプロットします。

## <a name="r-visuals"></a>R ビジュアル

これらのサンプルは、R ビジュアルと R スクリプトの分析とビジュアルの機能を活用する方法を示します。

| <img src="media/samples/association-rules.png" width="200">| <img src="media/samples/clustering.png" width="200">| <img src="media/samples/clustering-with-outliers.png" width="200">|
|------------- |------------- |------------- |------------- |
| [関連付けルール](https://github.com/Microsoft/powerbi-visuals-assorules/) </br>if-then ステートメントを使用することで、一見関連がないデータ間のリレーションシップを発見します | [クラスタリング](https://github.com/Microsoft/powerbi-visuals-clustering-kmeans/) </br>k 平均法アルゴリズムを使用してデータ内の類似グループを見つけます | [外れ値によるクラスタリング](https://github.com/microsoft/PowerBI-visuals-dbscan/) </br>データの類似グループと外れ値を見つけます
| <img src="media/samples/correlation-plot.png" width="200"> | <img src="media/samples/decision-tree-chart.png" width="200"> | <img src="media/samples/forecasting-tbats.png" width="200"> 
| [相関プロット](https://github.com/Microsoft/powerbi-visuals-corrplot/) </br>データ テーブル内で最も相関のある変数を強調表示します | [デシジョン ツリー グラフ](https://github.com/Microsoft/powerbi-visuals-decision-tree/) </br>再帰的パーティション分割を使用して統計的確率を判断するためのツリー形式の概略図 | [予測 TBATS](https://github.com/Microsoft/powerbi-visuals-forcasting-tbats/) </br>TBATS モデルを使用した、複数の季節性がある系列の時系列予測
| <img src="media/samples/forecasting-with-ARIMA.png" width="200"> | <img src="media/samples/funnel-plot.png" width="200"> | <img src="media/samples/outliers-detection.png" width="200"> 
| [Forecasting with ARIMA (ARIMA による予測)](https://github.com/Microsoft/powerbi-visuals-forcastingarima/) </br>自己回帰和分移動平均 (ARIMA) を使用して、履歴データに基づいて将来の値を予測します | [じょうごプロット](https://github.com/Microsoft/powerbi-visuals-funnel/) </br>じょうごプロットを使用して、データ内の外れ値を見つけます | [外れ値の検出](https://github.com/Microsoft/powerbi-visuals-outliers-det/) </br>最適な方法とプロットを使用してデータ内の外れ値を見つけます
| <img src="media/samples/spline-chart.png" width="200"> | <img src="media/samples/time-series-decomposition-chart.png" width="200"> | <img src="media/samples/time-series-forecasting-chart.png" width="200">
| [スプライン グラフ](https://github.com/Microsoft/powerbi-visuals-spline/) </br>ノイズの多いデータを視覚化して把握します | [時系列分解グラフ](https://github.com/Microsoft/powerbi-visuals-timeseriesdecomposition/) </br>"Loess に基づく STL (Seasonal and Trend) 分解" を使用して時系列の要素を把握します | [時系列予測グラフ](https://github.com/Microsoft/powerbi-visuals-forcasting-exp/) </br>指数平滑法を使用して、以前の予測値に基づいて将来の値を予測します

## <a name="next-steps"></a>次の手順

Power BI ビジュアルの作成を試すには、「[チュートリアル: Power BI のビジュアルを開発する](custom-visual-develop-tutorial.md)」。
