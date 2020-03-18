---
title: Power BI ビジュアルへの外部ライブラリの追加
description: この記事では Power BI ビジュアルで外部ライブラリを使用する方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 02/24/2020
ms.openlocfilehash: 13d5f2ed62ddefb8ac99fe2c91c72fc599a15936
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/07/2020
ms.locfileid: "78922507"
---
# <a name="adding-external-libraries"></a>外部ライブラリを追加する

この記事では Power BI ビジュアルで外部ライブラリを使用する方法について説明します。 これには、Power BI ビジュアルのコードから外部ライブラリをインストール、インポート、および呼び出す方法が含まれます。

## <a name="javascript-libraries"></a>JavaScript ライブラリ

1. *npm* や *yarn* などのパッケージ マネージャーを使用して、外部の JavaScript ライブラリをインストールします。
2. 外部ライブラリを使用して、必要なモジュールをソース ファイルにインポートします。

>[!NOTE]
>ご利用の JavaScript ライブラリに型指定を追加して、Intellisense とコンパイル時の安全性を確保するには、必ず適切なパッケージをインストールしてください。

### <a name="installing-the-d3-library"></a>d3 ライブラリのインストール

以下は、[npm](https://www.npmjs.com/) を使用して、[d3 ライブラリ](https://www.npmjs.com/package/d3)と [@types/d3](https://www.npmjs.com/package/@types/d3) パッケージをインストールする例です。

完全な例については、[Power BI 視覚化](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29)に関するコードを参照してください。

1. *d3* パッケージと *d3 types* パッケージをインストールします。

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. `visual.ts` など、*d3* ライブラリを使用するファイルにそれをインポートします。

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS フレームワーク

1. *npm* や *yarn* などのパッケージ マネージャーを使用して、外部の CSS フレームワークをインストールします。
2. ビジュアルの `.less` ファイルに、`import` ステートメントを含めます。

### <a name="installing-bootstrap"></a>ブートストラップのインストール

[npm](https://www.npmjs.com/) を使用して[ブートストラップ](https://www.npmjs.com/package/bootstrap)をインストールする例を次に示します。

完全な例については、[Power BI 視覚化](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32)に関するコードを参照してください。

1. "*ブートストラップ*" パッケージをインストールします。

    ```powershell
    npm install bootstrap --save
    ```

2. `visual.less` に `import` ステートメントを含めます。

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
