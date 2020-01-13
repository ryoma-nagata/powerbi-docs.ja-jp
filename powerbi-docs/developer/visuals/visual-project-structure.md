---
title: Power BI ビジュアル プロジェクトの構造
description: この記事では、ビジュアル プロジェクトの構造について説明します
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542095"
---
# <a name="power-bi-visual-project-structure"></a>Power BI ビジュアル プロジェクトの構造

このツールでは、pbiviz の新しい `<visual project name>` を実行すると、ファイルとフォルダーの基本的な構造が `<visual project name>` フォルダーに作成されます。

## <a name="visual-project-structure"></a>ビジュアル プロジェクトの構造

![ビジュアル プロジェクトの構造](./media/visual-project-structure.png)

* `.vscode` - VS Code のプロジェクトの設定が含まれています。 ワークスペースを構成するには、`.vscode/settings.json` ファイルを編集します。 詳細については、[VS コードの設定に関するドキュメント](https://code.visualstudio.com/docs/getstarted/settings)を参照してください。

* `assets` フォルダーには、`icon.png` ファイルのみが含まれています。 このツールでは、Power BI の [視覚化] ウィンドウでのビジュアルのアイコンとしてこのファイルを使用します。

    ![[視覚化] ウィンドウ](./media/visualization-pane-analytics-tab.png)

* `node_modules` フォルダーには、[ノード パッケージ マネージャーによってインストールされた](https://docs.npmjs.com/files/folders.html)すべてのパッケージが含まれています。

* `src` フォルダーには、ビジュアルのソース コードが含まれています。 既定では、ツールによって次の 2 つのファイルが作成されます。

  * `visual.ts` - ビジュアルのメイン ソース コード。

  * `settings.ts` - ビジュアルの設定のコード。 ファイルのクラスを使用すると、[ビジュアル プロパティの操作](./objects-properties.md#properties)が簡単になります。

* `style` フォルダーには、ビジュアルのスタイルを含む `visual.less` ファイルが含まれています。

* `capabilities.json` ファイルには、ビジュアルのメイン プロパティと設定が含まれています。 これにより、ビジュアルは、サポートされている機能、オブジェクト、プロパティ、データ ビュー マッピングを宣言できます。

    詳細については、[機能に関するドキュメント](./capabilities.md)を参照してください。

* `package-lock.json` は、npm によって `node_modules` ツリーまたは `package.json` のいずれかが変更されるすべての操作に対して、自動的に生成されます。

    詳細については、NPM の公式ドキュメントで [`package-lock.json` に関するページ](https://docs.npmjs.com/files/package-lock.json)を参照してください。

* `package.json` は、プロジェクト パッケージを説明しています。 通常は、プロジェクト、その作成者、説明、プロジェクトの依存関係に関する情報が含まれています。

    詳細については、NPM の公式ドキュメントで [`package.json` に関するページ](https://docs.npmjs.com/files/package.json.html)を参照してください。

* `pbiviz.json` には、ビジュアル メタデータが含まれています。 このファイルで、ビジュアルのメタデータを指定します。

    ファイルの一般的な内容は次のとおりです。

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    パラメーターの説明

  * `name` - ビジュアルの内部名。

  * `displayName` - Power BI の UI インターフェイスでのビジュアルの名前。

  * `guid` - ビジュアルの一意の ID。

  * `visualClassName` - ビジュアルのメイン クラスの名前。 Power BI は、このクラスのインスタンスを作成し、Power BI レポートのビジュアルを使用して起動します。

  * `version` - ビジュアルのバージョン番号。

  * `author` - 作成者の名前と連絡先のメール アドレスが含まれています。

  * `assets` の `icon` - ビジュアル用のアイコン ファイルへのパス。

  * `externalJS` には、ビジュアルで使用される JS ライブラリのパスが含まれています。

    > [!IMPORTANT]
    > 最新バージョンのツール 3.x.x 以降では、`externalJS` は使用されません。

  * `style` は、スタイル ファイルへのパスです。

  * `capabilities` は、`capabilities.json` ファイルへのパスです。

  * `dependencies` は、`dependencies.json` ファイルへのパスです。 `dependencies.json` には、R ベースのビジュアルで使用される R パッケージに関する情報が含まれています。

  * `stringResources` は、ローカライズされたファイルへのパスの配列です。

  詳細については、[ビジュアルでのローカライズに関するドキュメント](./localization.md)を参照してください。

* `tsconfig.json` は、TypeScript の構成ファイルです。

    詳細については、[TypeScript の構成に関する公式ドキュメント](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)を参照してください。

    `files` セクションの `tsconfig.json` には、`pbiviz.json` ファイルの `visualClassName` プロパティで指定され、ビジュアルのメイン クラスが配置されている *.ts ファイルへのパスが含まれている必要があります。

* `tslint.json` ファイルには、TSLint の構成が含まれています。

    詳細については、[TSLint の構成に関する公式ドキュメント](https://palantir.github.io/tslint/usage/configuration/)を参照してください。

## <a name="next-steps"></a>次の手順

* ビジュアル、ユーザー、Power BI の相互作用について理解をさらに深めるには、[ビジュアルの概念](./power-bi-visuals-concept.md)に関する詳細を参照してください。

* [ステップ バイ ステップ ガイド](./custom-visual-develop-tutorial.md)を使って、独自の Power BI ビジュアルをゼロから開発しましょう。
