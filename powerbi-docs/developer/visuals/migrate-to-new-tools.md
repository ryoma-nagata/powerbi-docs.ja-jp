---
title: powerbi-visuals-tools 3.x への移行
description: 新しいバージョンの powerbi-visuals-tools の概要
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cc554bff1cbd248ccd69a80ee47b60af981cdab1
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061824"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>新しい powerbi-visuals-tools 3.x.x への移行

バージョン 3 以降、Power BI Visuals Tools では、Webpack を使用してカスタム ビジュアルが構築されます。
新しいバージョンでは、開発者がビジュアルを作成するための多くの新しい機会がもたらされます

* TypeScript v3. x. x (既定)。 TypeScript 1.5 以降、用語が変更されています。 TypeScript の詳細については、[こちら](https://www.typescriptlang.org/docs/handbook/modules.html)を参照してください。

* ES6 モジュールがサポートされます。 もう [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries) 使用する必要はありません。代わりに ES6 の import を使用してください。

* 新しいバージョンの [D3v5](https://d3js.org/) とその他の ES6 モジュール ベースのライブラリがサポートされます。

* パッケージ サイズが小さくなりました。 Webpack では、[ツリー シェイキング](https://webpack.js.org/guides/tree-shaking/)を使用して、未使用のコードが削除されます。 これにより、JS のコードが削減されるため、ビジュアル読み込みのパフォーマンスが向上します。

* API パフォーマンスの向上。

* Globalize.js ライブラリは、formatting-utils に[統合されています](migrate-to-new-tools.md#remove-globalizejs-library)。

* ツールでは、[webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) を使用して、ビジュアルのコード ベースが表示されます。

新しいバージョンの Power BI ビジュアル ツールの移行手順について、以下で説明します。

## <a name="backward-compatibility"></a>下位互換性

新しいツールを使用すると、古いビジュアルのコード ベースとの下位互換性が維持されますが、外部ライブラリを読み込むには追加の変更が必要になることがあります。

モジュール システムをサポートするライブラリが、Webpack モジュールとしてインポートされます。 その他のすべてのライブラリとビジュアル ソース コードは、1 つのモジュールにラップされます。

以前の pbiviz ツールで使用されていた JQuery や Lodash などのグローバル変数は、現在は非推奨になっています。 これは、古いビジュアル コードがグローバル変数でリレーされると、ビジュアルが破損する可能性があることを意味します。

前のバージョンの Power BI Visuals Tools では、`powerbi.extensibility.visual` モジュールにビジュアル クラスを定義する必要がありました。

## <a name="how-to-install-powerbi-visuals-tools"></a>powerbi-visuals-tools のインストール方法

次のコマンドを実行して、新しいツールセットをインストールできます。

```cmd
npm install -g powerbi-visuals-tools
```

sampleBarChart ビジュアルのサンプルと、`package.json` 内の対応する[変更](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16):

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>Power BI Custom Visuals API のインストール方法

新しいバージョンの powerbi-visual tools には、すべての API バージョンがその中に含まれていません。 その代わりに、開発者が特定のバージョンの [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api) パッケージをインストールする必要があります。 パッケージのバージョンと Power BI Custom Visuals の API バージョンは一致し、Power BI Custom Visuals API のすべての型定義が提供されます。

コマンド `npm install --save-dev powerbi-visuals-api` を実行して、`powerbi-visuals-api` をプロジェクトの依存関係に追加します。
また、古い API の型定義へのリンクを削除する必要があります。 これは、`powerbi-visuals-api` の型が、Webpack によって自動的に含まれるためです。 対応する変更は、`package.json` の [この](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14)行にあります。

## <a name="update-tsconfigjson"></a>`tsconfig.json` を更新する

外部モジュールを使用するには、`out` オプションを `outDir`.
`"outDir": "./.tmp/build/",` に切り替える必要があります (`"out": "./.tmp/build/visual.js",` から切り替えます)。

これが必要なのは、TypeScript ファイルは、個別に JavaScript ファイルにコンパイルされるためです。 もう出力として visual.js ファイルを指定する必要がないのは、これが理由です。

また、最新の JavaScript を出力として使用する場合は、`target` オプションを `ES6` に変更することもできます。 [これは任意です](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6)。

## <a name="update-custom-visuals-utils"></a>Custom Visuals utils を更新する

いずれかの [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils) を使用する場合は、それらも最新バージョンに更新する必要があります。

コマンド `npm install powerbi-visuals-utils-<UTILNAME> --save` を実行します。 (例: `npm install powerbi-visuals-utils-dataviewutils --save`) を使用して、TypeScript の外部モジュールを含む新しいバージョンを取得します。

MekkoChart [リポジトリ](https://github.com/Microsoft/powerbi-visuals-mekkochart)で例を見つけることができます。
このビジュアルでは、すべての utils が使用されます。

## <a name="remove-globalizejs-library"></a>Globalize.js ライブラリを削除する

新しいバージョンの [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) には、すぐに使用できる globalize.js が含まれています。
このライブラリをプロジェクトに手動で含める必要はありません。
必要なすべてのローカライズが、最終パッケージに自動的に追加されます。

## <a name="fix-loading-external-libraries"></a>外部ライブラリの読み込みを修正する

代わりに、`pbiviz.json` の `externalJS` 配列で lib の後ろに新しい JS ファイルを含めます。 例:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

ソースに libs をインポートします。 `lodash-es` の例:

```JS
import * as _ from "lodash-es";
```

ここで `_` は `lodash` ライブラリのグローバル変数です。

## <a name="changes-in-the-visuals-sources"></a>ビジュアル ソースの変更

主な変更は、内部モジュール内の外部モジュールを使用することはできないため、内部モジュールを外部モジュールに変換することです。

これらの変更は、サンプルの横棒グラフに適用されている変更を示しています。

変更の詳細な説明を以下に示します。

1. [ソース コード](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)の各ファイルからすべてのモジュール定義を削除します。

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Power BI custom visual API の定義をインポートします](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2)。

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. `powerbi` 内部モジュールから必要なインターフェイスまたはクラスを[インポート](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23)します。

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. D3.js ライブラリを[インポート](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1)します。

    ```typescript
    import * as d3 from "d3";
    ```

    または、必要な D3 ライブラリ モジュールのみをインポートします

    ```typescript
    import { max, min } from "d3-array";
    ```

5. Visual プロジェクトに定義されているユーティリティ、クラス、インターフェイスを、メイン ソース ファイルに[インポート](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10)します。

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>CSS スタイルをインポートする

新しいバージョンのツールを使用すると、開発者は、CSS、LESS スタイルを TypeScript コードに直接インポートできます。

そのため、前に使用されていた [styles セクション](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22)はコンパイラによって無視されます。

スタイルシートを使用するには、main ts ファイルを開き、次の行を追加します。  

```typescript
import "./../style/visual.less";
```  

CSS、LESS スタイルは、自動的にコンパイルされます。  

### <a name="externaljs-section-in-pbivizjson"></a>pbiviz.json の externalJS セクション

ツールでは、ビジュアル バンドルに読み込む `externalJS` の一覧は[必要ありません](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20)。 Webpack に、インポートされるすべてのライブラリが含まれているためです。

**pbivi.json の externalJS セクションは空にする必要があります。**

一般的なコマンド `npm run package` を呼び出して、ビジュアル パッケージを作成するか、`npm run start` で開発サーバーを起動します。

## <a name="updating-d3js-library-to-version-5"></a>D3.js ライブラリのバージョン 5 への更新

新しいツールを使用すると、新しいバージョンの D3.js ライブラリの使用を開始できます。

ビジュアル プロジェクト内で D3 を更新するコマンドを呼び出します。

`npm install --save d3@5` (新しい D3.js をインストールする場合)

`npm install --save-dev @types/d3@5` (D3.js 用の新しい型定義をインストールする場合)

互換性を破るさまざまな変更があるため、新しい D3.js を使用するようにコードを変更する必要があります。

1. インターフェイス `d3.Selection<T>` [ が](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) から `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>` に変更されました。

2. `attr` メソッドの 1 回の呼び出しで複数の属性を適用することはできません。 `attr` メソッドの別の呼び出しで各属性を[渡す必要があります](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278)。 `style` メソッドでも[同様](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247)です。

3. D3.js v4 では、新しい merge メソッドが導入されました。 このメソッドは、data-join の後ろで enter セクションと update をマージするためによく使用されます。 D3 を適切に使用するには、[merge メソッドを呼び出します](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272)。

D3.js ライブラリの変更の[詳細を参照](https://github.com/d3/d3/blob/master/CHANGES.md)してください。

## <a name="babel"></a>Babel

バージョン 3.1 以降のツールでは、幅広いブラウザーをサポートするために、Babel を使用して、新しい最新の JS コードが古い ES5 にコンパイルされます。

このオプションは既定で有効になっていますが、[`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill) パッケージを手動でインポートする必要があります。

パッケージをインストールするためのコマンドを実行します。

`npm install --save @babel/polyfill`

次に、ビジュアル コードの開始点にパッケージをインポートします (通常は "src/visual.ts" ファイル)。

`import "@babel/polyfill";`

Babel の[ドキュメント](https://babeljs.io/docs/en/)で詳細を参照してください。

最後に、[webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) を実行して、ビジュアルのコード ベースを表示します。  

![ビジュアル コード統計](./media/webpack-stats.png)
