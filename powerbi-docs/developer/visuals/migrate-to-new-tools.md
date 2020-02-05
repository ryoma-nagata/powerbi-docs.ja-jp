---
title: powerbi-visuals-tools バージョン 3.x への移行
description: 新しいバージョンの powerbi-visuals-tools の概要
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d9af0ab870732990201ab3478d71fdafa9e13439
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76818826"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>新しい powerbi-visuals-tools バージョン 3.*x* への移行

バージョン 3 以降の Power BI Visuals Tools (powerbi-visuals-tools または `pbiviz`) では、webpack を使用してカスタム ビジュアルが構築されます。
新しいバージョンでは、開発者がビジュアルを作成するため、次のような多くの機能強化が提供されています。

- TypeScript バージョン 3.*x* が既定で使用されます。 TypeScript 1.5 以降では、分類が変更されています。 TypeScript の詳細については、[こちら](https://www.typescriptlang.org/docs/handbook/modules.html)を参照してください。

- ECMAScript 6 (ES6) モジュールがサポートされます。 [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries) の代わりに、ES6 インポートが使用されるようになりました。

- 新しいバージョンの Data-Driven Documents ([D3v5](https://d3js.org/)) とその他の ES6 モジュール ベースのライブラリがサポートされます。

- パッケージ サイズが小さくなりました。 [ツリー シェイキング](https://webpack.js.org/guides/tree-shaking/)は、未使用のコードを削除するために webpack によって使用されます。 これにより、JavaScript コードが減り、ビジュアルの読み込みのパフォーマンスが向上します。

- API パフォーマンスの向上。

- Globalize.js ライブラリは、FormattingUtils に[統合されています](migrate-to-new-tools.md#remove-the- globalizejs-library)。

- Power BI Visuals Tools では、[webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) を使用して、ビジュアルのコード ベースが表示されます。

この記事では、新しいバージョンの Power BI Visuals Tools のすべての移行手順について説明します。

## <a name="backward-compatibility"></a>下位互換性

この新しいツールでは、古いビジュアルのコード ベースとの下位互換性情報が保存されますが、外部ライブラリを読み込むには追加の変更が必要になることがあります。

モジュール システムをサポートするライブラリが、webpack モジュールとしてインポートされます。 ビジュアルのその他すべてのライブラリとソース コードは、1 つのモジュールにラップされます。

以前の Power BI Visuals Tools で使用されていた JQuery や Lodash などのグローバル変数は、現在は非推奨になっています。 ご使用のビジュアルの古いコードがグローバル変数に依存している場合、そのビジュアルは新しいツールで動作しない可能性があります。

前のバージョンの Power BI Visuals Tools では、`powerbi.extensibility.visual` モジュールにビジュアル クラスを定義する必要がありました。 新しいバージョンのツールでは、代わりにメインの TypeScript (.ts) ファイルでビジュアル クラスを定義する必要があります。 通常、そのファイルは `src/visual.ts` です。

## <a name="install-powerbi-visuals-tools"></a>powerbi-visuals-tools をインストールする

次のコマンドを実行して、新しいツールをインストールします。

```cmd
npm install -g powerbi-visuals-tools
```

次のコードは、[sampleBarChart ビジュアル リポジトリ](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15)の `package.json` ファイルからのもので、ビジュアル プロジェクトが新しいツールで動作するように更新された後のものです。

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>Power BI Custom Visuals API のインストール

新しいバージョンの powerbi-visual tools には、すべての API バージョンが含まれていません。 代わりに、特定のバージョンの [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api) パッケージをインストールする必要があります。 ご使用の Power BI カスタム ビジュアルの API バージョンと一致するパッケージのバージョンを選択します。 このパッケージにより、Power BI Custom Visuals API のすべての型定義が提供されます。

次のコマンドを実行して、プロジェクトのプロジェクト依存関係に `powerbi-visuals-api` を追加します。

```cmd
npm install --save-dev powerbi-visuals-api
```

また、webpack には `powerbi-visuals-api` の型が自動的に含まれるため、古い API 型定義へのリンクをすべて削除します。 対応する変更は [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) と [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14) にあります。

## <a name="update-tsconfigjson"></a>tsconfig.json を更新する

外部モジュールを使用するには、`out` オプションを `outDir` に変更します。 たとえば、`"out": "./.tmp/build/visual.js",` の代わりに `"outDir": "./.tmp/build/",` を使用します。

この変更が必要なのは、TypeScript ファイルが個別に JavaScript ファイルにコンパイルされるからです。 そのため、visual.js ファイルを出力として指定する必要はもうありません。

最新の JavaScript を出力として使用する場合は、`target` オプションを `ES6` に変更することもできます。 この変更は、[省略可能](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7)です。

## <a name="update-custom-visuals-utilities"></a>カスタム ビジュアル ユーティリティを更新する

いずれかの [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils) パッケージを使用する場合は、それらも最新バージョンに更新する必要があります。 これを行うには、次のコマンドを実行します。

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

たとえば、TypeScript の外部モジュールを使用して新しいバージョンを取得するには、次を実行します。 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

すべての `powerbi-visuals-utils` パッケージを使用するビジュアルの例については、[MekkoChart リポジトリ](https://github.com/Microsoft/powerbi-visuals-mekkochart)を参照してください。

## <a name="remove-the-globalizejs-library"></a>Globalize.js ライブラリを削除する

新しいバージョンの [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) には、Globalize.js が含まれています。 そのため、このライブラリをプロジェクトに手動で含める必要はありません。 必要なすべてのローカライズが、最終パッケージに自動的に追加されます。

## <a name="configure-loading-of-external-libraries"></a>外部ライブラリの読み込みを構成する

`pbiviz.json` の `externalJS` 配列のライブラリの後に新しい JavaScript ファイルを含めます。 例:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

ソース コードでライブラリをインポートします。 たとえば、`lodash-es` の場合は、次のステートメントを使用します。

```JS
import * as _ from "lodash-es";
```

前の例では、`_` は `lodash` ライブラリのグローバル変数です。

## <a name="make-changes-in-the-sources-of-your-visuals"></a>ビジュアルのソースを変更する

行う必要がある主な変更は、内部モジュールを外部モジュールに変換することです。 内部モジュール内で外部モジュールを使用することはできません。

ここでは、行う変更について詳しく説明します。 横棒グラフのカスタム ビジュアル コード サンプルを使って、これらの変更を説明します。

1. [ソース コード](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3)の各ファイルからすべてのモジュール定義を削除します。

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Power BI Custom Visuals API の定義をインポートします](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4)。

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. `powerbi` 内部モジュールから[必要なインターフェイスまたはクラスをインポート](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35)します。

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

4. [D3.js ライブラリをインポートします](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2)。

    ```typescript
    import * as d3 from "d3";
    ```

    または、必要な D3 ライブラリ モジュールのみをインポートします。

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [ビジュアル プロジェクトに定義されているユーティリティ、クラス、インターフェイスを、メイン ソース ファイルにインポートします](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41)。

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

新しいバージョンのツールを使用すると、`CSS`、`Less` スタイルを TypeScript コードに直接インポートできます。 以前に使用されていた [styles セクション](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21)は、コンパイラによって無視されるようになりました。

スタイルシートを使用するには、メインの TypeScript (.ts) ファイルを開き、次の行を追加します。  

```typescript
import "./../style/visual.less";
```  

`CSS`、`Less` スタイルは、自動的にコンパイルされます。

### <a name="externaljs-section-in-pbivizjson"></a>pbiviz.json の externalJS セクション

webpack にはインポートされたすべてのライブラリが含まれているため、このツールでは、ビジュアル バンドルに読み込む[ `externalJS` ライブラリの一覧を必要としません](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20)。

> [!NOTE]
> `pbiviz.json` では、`externalJS` セクションは空のままにします。

一般的なコマンド `npm run package` を使用して、ビジュアル パッケージを作成するか、`npm run start` で開発サーバーを起動します。

## <a name="update-the-d3js-library-to-version-5"></a>D3.js ライブラリをバージョン 5 に更新する

新しいビジュアル ツールを使用すると、D3.js ライブラリの新しいバージョンの使用を開始できます。 次のコマンドを実行して、ビジュアル プロジェクト内で D3 を更新します。

- `npm install --save d3@5` (新しい D3.js をインストールする場合)

- `npm install --save-dev @types/d3@5` (D3.js 用の新しい型定義をインストールする場合)

> [!IMPORTANT]
> D3 バージョン 5 では、いくつかの重大な変更が導入されています。

新しい D3.js で動作するようにコードを変更します。

- インターフェイス `d3.Selection<T>` は、`Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>` に[変更されました](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157)。

- `attr` メソッドの 1 回の呼び出しを使用して複数の属性を適用することはできません。 代わりに、[各属性を個別の呼び出しで `attr` に渡す](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278)必要があります。 また、[`style` メソッドも個別に呼び出します](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247)。

- D3.js バージョン 4 では、新しい `merge` メソッドが導入されました。 このメソッドは、data-join 演算の後で `enter` セクションと `update` セクションをマージするためによく使用されます。 D3 を適切に使用するには、[`merge` メソッドを呼び出します](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272)。

D3.js ライブラリの変更の詳細については、[こちら](https://github.com/d3/d3/blob/master/CHANGES.md)を参照してください。

## <a name="install-babel-and-core-js"></a>Babel と core-js をインストールする

バージョン 3.1 以降のビジュアル ツールでは、幅広いブラウザーをサポートするために、Babel を使用して最新の JavaScript コードが古い ECMAScript 5 (ES5) にコンパイルされます。

Babel オプションは既定で有効になっていますが、[`core-js`](https://www.npmjs.com/package/core-js) パッケージを手動でインポートする必要があります。 次のコマンドを実行して、パッケージをインストールします。

```cmd
npm install --save core-js
```

次に、ビジュアル コードの開始点でパッケージをインポートします。 通常、これは 'src/visual.ts' ファイルです。

```JS
import "core-js/stable";
```

Babel の[ドキュメント](https://babeljs.io/docs/en/)で詳細を参照してください。
