---
title: Power BI ビジュアル API の変更ログ
description: この記事では、Power BI ビジュアル API のさまざまなバージョンにおける主な変更点について説明します
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: fa8759d7edb519240140263bcd01bfdddd9c7d86
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83141068"
---
# <a name="power-bi-visuals-api-changelog"></a>Power BI ビジュアル API の変更ログ
このページには、API バージョンの簡単な概要が含まれています。 ここに記載されているバージョンは安定バージョンと見なされ、変更されません。

## <a name="api-v26"></a>API v2.6
  * 更新オプションに **isInFocus** を追加。ビジュアル ホストに **switchFocusModeState** メソッドを追加
  * **subtotals** のカスタマイズをサポート

## <a name="api-v25"></a>API v2.5
  * **[分析ペイン](./analytics-pane.md)** をサポート
  * `SelectionIdBuilder` の **withMatrixNode** および **withTable** メソッドをサポート
  * `DataRepetitionSelector` インターフェイスのサポートが終了し、`data.CustomVisualOpaqueIdentity` インターフェイスに置き換え

## <a name="api-v23"></a>API v2.3
  * **[ランディング ページ API](./landing-page.md)**
  * **[ローカル ストレージ API](./local-storage.md)**
  * **[タプル フィルター API (複数列フィルター)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[レンダリング イベント API](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v22"></a>API v2.2
  * **[DataView からの JSON フィルターの復元](./filter-api.md#restore-the-json-filter-from-the-data-view)** をサポート
  * **[ContextMenu API](./context-menu.md)**

## <a name="api-v21"></a>API v2.1
  * パフォーマンスの向上:
    * 読み込み時間の短縮
    * より小さなメモリ占有領域
    * 最適化されたデータおよびイベント トランザクション  

**リリース ノート**
* リファクタリングされたフィルター処理 API シリーズは API 2.2 で利用可能になり、API 2.1 ではサポートされません。
* ビジュアルは、その機能で宣言された dataView 型のみを受け取ります。 複数の dataView 型を使用しているビジュアルは、この更新の結果として中断されます。
* `DataViewScopeIdentity` インターフェイスのサポートが終了し、`data.DataRepetitionSelector` インターフェイスに置き換えられました。 `DataViewScopeIdentity` インターフェイスのキー プロパティを使用していた場合は、`JSON.stringify(identity)` に置き換えることができます
* `undefined` は dataView 内で `null` に置き換えられます。 `var item in myArray` を使用して配列を反復処理する場合、`undefined` はスキップされますが、`null` はスキップされません。 このパターンを使用するビジュアルは、この更新によって破損する可能性があります。 配列内の `null` を確認してください。
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* `proto` プロパティでは、dataView 内に非表示のメタデータまたはデータが格納されなくなりました。 `proto` を介してプロパティにアクセスするビジュアルは、この更新によって破損する可能性があります。

## <a name="api-v113"></a>API v1.13
* **[同期スライサー](./enable-sync-slicers.md)** をサポート。これは、PBI の現在のコード状態により、単一フィールド スライサーでのみ動作することに注意してください。[詳細](/power-bi/desktop-slicers)。
* アクセシビリティ:[ハイコントラストのサポート](./high-contrast-support.md) 
* アクセシビリティ:"キーボード フォーカスを許可する" フラグ

## <a name="api-v112"></a>API v1.12
* テーマをサポート
* **[fetchMoreData](./fetch-more-data.md)** をサポート。 **"より多くのデータをフェッチ" API** が 30K のデータ ポイントのハード制限を克服していることに注意してください
* **[キャンバス ツールヒント API](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v111"></a>API v1.11
* **[FilterManager API](./filter-api.md)**
* **[ブックマーク](./bookmarks-support.md)** をサポート 

## <a name="api-v110"></a>API v1.10
* `ILocalizationManager` を追加
* **認証 API**

## <a name="api-v19"></a>API v1.9
* **[launchUrl API](./launch-url.md)**

## <a name="api-v18"></a>API v1.8
* 機能スキーマで新しい型 **fillRule** (勾配) をサポート
* オブジェクト プロパティの機能スキーマで **rule** プロパティをサポート

## <a name="api-v17"></a>API v1.7
* **[RESJSON](./localization.md#resource-file)** をサポート

## <a name="api-v162"></a>API v1.6.2
* ビジュアルをビジュアル編集モードに移行する **[編集モード](./advanced-edit-mode.md)** をサポート
* html に基づく **[インタラクティブ (html) R Power BI ビジュアル](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** をサポート

## <a name="api-v150"></a>API v1.5.0
* ビジュアル対話のための " **[ビジュアル対話を許可](./visuals-interactions.md)** " をサポート

## <a name="api-v140"></a>API v1.4.0
* **[ローカライズ](./localization.md)** をサポート

## <a name="api-v130"></a>API v1.3.0
* **[ツールヒント](./add-tooltips.md)** をサポート

## <a name="api-v120"></a>API v1.2.0
* **colorPalette** を追加して、ビジュアルで使用する色を管理します。
* **複数選択**をサポート。selectionManager は `SelectionId` の配列を受け入れることができます。
* R スクリプトを使用した **[R ビジュアル](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** をサポート

## <a name="api-v110"></a>API v1.1.0
* iFrame 内のデバッグ ビジュアルをサポート
* iFrame の初期化を高速にする軽量のサンドボックスを追加
* [Capabilities.objects で "テキスト" 型がサポートされない](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12)問題を修正
* ビジュアル API の型定義とスキーマを更新するための `pbiviz update` をサポート
* 特定の API バージョンでビジュアルを作成するための、`pbiviz new` の `--api-version` フラグをサポート
* API v1.2.0 のアルファ リリースをサポート

**ビジュアル ホスト**
* データ選択に使用される一意の識別子を作成するための **createSelectionIdBuilder** を追加
* ビジュアルの選択状態を管理し、ビジュアル ホストに変更を通知するための **createSelectionManager** を追加
* ビジュアルで使用する既定の **colors** の配列を追加

## <a name="api-v100"></a>API v1.0.0
* 最初の API リリース
