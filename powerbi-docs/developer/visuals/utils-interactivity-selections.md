---
title: Power BI ビジュアルのインタラクティビティ ユーティリティ
description: この記事では、インタラクティビティ ユーティリティを使用して Power BI ビジュアルに選択項目を追加する方法について説明します
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 8a9218085b0da655d1ce4b3ece0b2666c4826c86
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061870"
---
# <a name="microsoft-power-bi-visuals-interactivity-utils"></a>Microsoft Power BI ビジュアルのインタラクティビティ ユーティリティ

InteractivityUtils は、Power BI のカスタム ビジュアルのクロス選択とクロスフィルタリングの実装を簡略化するための一連の関数およびクラスです。

## <a name="installation"></a>インストール

> [!NOTE]
> 引き続き以前のバージョンの powerbi-visuals-tools (バージョン番号が 3.x.x 未満) を使用する場合は、新しいバージョンのツール (3.x.x) をインストールします。

> [!IMPORTANT]
> インタラクティビティ ユーティリティの新しい更新プログラムでは、最新バージョンのツールのみがサポートされます。 [詳細については、最新のツールで使用できるようにビジュアル コードを更新する方法に関する記事を参照してください](migrate-to-new-tools.md)

パッケージをインストールするには、現在のカスタム ビジュアルを使用して、ディレクトリ内で次のコマンドを実行する必要があります。

```bash
npm install powerbi-visuals-utils-interactivityutils --save
```

バージョン 3.0 以降では、依存関係を解決するために ```powerbi-models``` もインストールする必要があります。

```bash
npm install powerbi-models --save
```

インタラクティビティ ユーティリティを使用するには、ビジュアルのソース コードに必要なコンポーネントをインポートする必要があります。

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
```

### <a name="including-css-artifacts-to-the-custom-visual"></a>カスタム ビジュアルに CSS 成果物を含める

カスタム ビジュアルにパッケージを使用するには、次の CSS ファイルを `your.less` ファイルにインポートする必要があります。

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

その結果、次のようなファイル構造になります。

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

> [!NOTE]
> Power BI Visuals Tools によって外部 CSS ルールはラップされるため、.css ファイルを .less ファイルとしてインポートする必要があります。

## <a name="usage"></a>Usage

### <a name="define-interface-for-data-points"></a>データ ポイントのインターフェイスを定義する

通常、データ ポイントには選択項目と値が含まれます。 このインターフェイスによって `SelectableDataPoint` インターフェイスが拡張されます。 `SelectableDataPoint` には既に次のプロパティが含まれています。

```typescript
  /** Flag for identifying that data point was selected */
  selected: boolean;
  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;
  /**
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points should select based
   * only on series even if they exist as category/series intersections.
   */
  specificIdentity?: powerbi.extensibility.ISelectionId;
```

インタラクティビティ ユーティリティを使用する最初の手順では、インタラクティビティ ユーティリティのインスタンスを作成し、ビジュアルのプロパティとしてオブジェクトを保存します

```typescript
export class Visual implements IVisual {
  // ...
  private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
  // ...
  constructor(options: VisualConstructorOptions) {
      // ...
      this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
      // ...
  }
}
```

```typescript
import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}
```

2 番目の手順では、基本動作クラスを拡張します。

> [!NOTE]
> [5.6.x バージョンのインタラクティビティ ユーティリティ](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0)で導入された BaseBehavior。 以前のバージョンを使用する場合は、以下のサンプルから動作クラスを作成します (`BaseBehavior` クラスは同じです)。

動作クラスのオプションのインターフェイスを定義します。

```typescript
import { SelectableDataPoint } from "./interactivitySelectionService";

import {
    IBehaviorOptions,
    BaseDataPoint
} from "./interactivityBaseService";

export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {
    /** D3 selection object of main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;
    /** D3 selection object of some element on backgroup to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
}
```

`visual behaviour` のクラスを定義します。 `click`、`contextmenu` マウス イベントを処理する担当のクラス。
データ要素のクリックを使用すると、ビジュアルから選択ハンドラーが呼び出され、データ ポイントが選択されます。 または、ユーザーがビジュアルの背景要素をクリックすると、選択がクリアされます。 また、クラスには、`bindClick`、`bindClearCatcher`、`bindContextMenu` という対応するメソッドがあります。

```typescript
export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {
    /** D3 selection object of main elements on the chart */
    protected options: BaseBehaviorOptions<SelectableDataPointType>;
    protected selectionHandler: ISelectionHandler;

    protected bindClick() {
      // ...
    }

    protected bindClearCatcher() {
      // ...
    }

    protected bindContextMenu() {
      // ...
    }

    public bindEvents(
        options: BaseBehaviorOptions<SelectableDataPointType>,
        selectionHandler: ISelectionHandler): void {
      // ...
    }

    public renderSelection(hasSelection: boolean): void {
      // ...
    }
}
```

また、`BaseBehavior` クラスを拡張することもできます。

```typescript
import powerbi from "powerbi-visuals-api";
import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
    value: powerbi.PrimitiveValue;
}

export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
  // ...
}
```

要素のクリックを処理するには、D3 選択オブジェクトの `on` メソッドを呼び出します (elementsSelection と clearCatcherSelection の場合も同様)。

```typescript
protected bindClick() {
  const {
      elementsSelection
  } = this.options;

  elementsSelection.on("click", (datum) => {
      const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
      mouseEvent && this.selectionHandler.handleSelection(
          datum,
          mouseEvent.ctrlKey);
  });
}
```

選択マネージャーの `showContextMenu` メソッドを呼び出すには、`contextmenu` イベント用に同様のハンドラーを追加します。

```typescript
protected bindContextMenu() {
    const {
        elementsSelection
    } = this.options;

    elementsSelection.on("contextmenu", (datum) => {
        const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
        if (event) {
            this.selectionHandler.handleContextMenu(
                datum,
                {
                    x: event.clientX,
                    y: event.clientY
                });
            event.preventDefault();
        }
    });
}
```

インタラクティビティ ユーティリティから `bindEvents` メソッドが呼び出され、関数がハンドラーに割り当てられ、`bindClick`、`bindClearCatcher`、および `bindContextMenu` の呼び出しが `bindEvents` メソッドに追加されます。

```typescript
  public bindEvents(
      options: BaseBehaviorOptions<SelectableDataPointType>,
      selectionHandler: ISelectionHandler): void {

      this.options = options;
      this.selectionHandler = selectionHandler;

      this.bindClick();
      this.bindClearCatcher();
      this.bindContextMenu();
  }
```

グラフ内の要素のビジュアル状態を更新する処理を担当する `renderSelection` メソッド。

実装の `renderSelection` メソッドのサンプルを次に示します。

```typescript
public renderSelection(hasSelection: boolean): void {
    this.options.elementsSelection.style("opacity", (category: any) => {
        if (category.selected) {
            return 0.5;
        } else {
            return 1;
        }
    });
}
```

最後のステップでは、`visual behavior` のインスタンスと、インタラクティビティ ユーティリティ インスタンスの `bind` メソッドの呼び出しを作成しています。

```typescript
this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
    behavior: this.behavior,
    dataPoints: this.categories,
    clearCatcherSelection: select(this.target),
    elementsSelection: selectionMerge
});
```

* `selectionMerge` は D3 選択オブジェクトであり、ビジュアルに対して選択可能なすべての要素を表します。

* `select(this.target)` は D3 選択オブジェクトであり、ビジュアルのメイン DOm 要素を表します。

* 要素を持つ `this.categories` データ ポイント (インターフェイスは `VisualDataPoint` または `categories: VisualDataPoint[];`)

* `this.behavior` は `visual behavior` の新しいインスタンスです。

  次のように、ビジュアルのコンストラクター内に作成されます。

  ```typescript
  export class Visual implements IVisual {
    // ...
    constructor(options: VisualConstructorOptions) {
        // ...
        this.behavior = new Behavior();
    }
    // ...
  }
  ```

これで、ビジュアルで選択項目を処理できるようになりました。

## <a name="next-steps"></a>次の手順

* [ブックマークの切り替えで選択を処理する方法を確認する](bookmarks-support.md#visuals-with-selection)

* [ビジュアルのデータ ポイントのコンテキスト メニューを追加する方法を確認する](context-menu.md)

* [選択マネージャーを使用して Power BI ビジュアルに選択項目を追加する方法を確認する](selection-api.md)
