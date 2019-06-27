---
title: Power BI Desktop での式に基づくタイトル
description: Power BI Desktop で変更をプログラムでの式に基づくプログラムによる条件付き書式を使用して動的なタイトルを作成します。
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769744"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Power BI Desktop での式に基づくタイトル

動的に作成することができます、Power BI ビジュアルのタイトルをカスタマイズします。 Data Analysis Expressions (DAX) フィールド、変数、またはその他のプログラム要素に基づいて作成すると、ビジュアルのタイトルは必要に応じて自動的に調整できます。 これらの変更は、フィルター、選択、またはその他のユーザーの操作や構成に基づきます。

![Power BI Desktop のスクリーン ショットの条件付き書式設定オプション](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

動的のタイトルの作成とも呼ばれる*タイトルの式に基づく*は簡単です。 

## <a name="create-a-field-for-your-title"></a>タイトルのフィールドを作成します。

式ベースのタイトルを作成する最初の手順では、タイトルに使用するモデルのフィールドを作成します。 

あらゆる種類の創造的な方法が必要だ、または express する内容の反映、ビジュアルのタイトルがあります。 2 つの例を見ていきましょう。

製品のブランド名のビジュアルを受信するフィルター コンテキストに基づいて変更する式を作成することができます。 次の図は、このようなフィールドに DAX 数式を示します。

![スクリーン ショットの DAX の数式](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

別の例では、変更がユーザーの言語またはカルチャに基づく動的なタイトルを使用しています。 メジャーの DAX 言語に固有のタイトルを作成するにを使用して、`USERCULTURE()`関数。 この関数は、オペレーティング システムやブラウザーの設定に基づき、ユーザーのカルチャ コードを返します。 次の DAX switch ステートメントを使用すると、適切な翻訳された値を選択します。 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

または、すべての翻訳を格納する参照テーブルから文字列を取得することができます。 モデルには、そのテーブルを配置します。 

これらは、Power BI Desktop でビジュアルのタイトルを動的な式に基づくを作成する際の例の 2 だけです。 タイトルで行うことができますが、想像力と、モデルによってのみ制限されます。


## <a name="select-your-field-for-your-title"></a>タイトルのフィールドを選択します。

モデルを作成するフィールドの DAX 式を作成した後、ビジュアルのタイトルに適用する必要があります。

フィールドを選択し、適用するには、**視覚化**ウィンドウ。 **形式**領域で、**タイトル**ビジュアルのタイトルのオプションを表示します。 

右クリックすると**タイトルのテキスト**、選択できるように、コンテキスト メニューが表示されます ***fx* 条件付き書式**します。 そのメニュー項目を選択すると、**タイトルのテキスト** ダイアログ ボックスが表示されます。 

![スクリーン ショットのタイトル テキスト ダイアログ ボックス](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

そのウィンドウのタイトルに使用するために作成するフィールドを選択できます。

## <a name="limitations-and-considerations"></a>制限事項と考慮事項

ビジュアルのタイトルを式に基づくの現在の実装にいくつかの制限があります。

* ビジュアルの Python、R ビジュアルまたは主要な影響元のビジュアルで現在、式ベースの書式設定機能はサポートされていません。
* タイトルを作成するフィールドは、文字列データ型である必要があります。 数値または日付/時刻 (またはその他の任意のデータ型) を返すメジャーは現在サポートされていません。

## <a name="next-steps"></a>次の手順

この記事では、ユーザーがレポートと対話するときに変更可能な動的フィールドに、ビジュアルのタイトルを有効にする DAX 式を作成する方法について説明します。 次の記事に役に立つもします。

* [Power BI Desktop でクロス レポートのドリルスルーを使用します。](desktop-cross-report-drill-through.md)
* [Power BI Desktop でドリルスルーを使用する](desktop-drillthrough.md)