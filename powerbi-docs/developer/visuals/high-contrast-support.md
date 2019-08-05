---
title: ハイコントラスト モードのサポート
description: ハイコントラスト モードのサポートを Power BI ビジュアルに追加する方法
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cb77ea012fdfdbd5be62c58c6f9b94a0355db1a9
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424932"
---
# <a name="high-contrast-mode-support"></a>ハイコントラスト モードのサポート

Windows "*ハイコントラスト*" 設定では、よりはっきりした色を使用して、テキストとアプリを見やすくします。
[Power BI でのハイコントラスト サポート](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast)に関する記事をご覧ください。

ハイコントラスト サポートをビジュアルに追加するには、次のものが必要です。

1. 初期化時:Power BI がハイコントラスト モードであるかどうかを検出し、そうである場合は、現在のハイコントラストの色を取得します。
2. 毎回の更新時:見やすくするためにビジュアルを表示する方法を変更します。

PowerBI-visuals-sampleBarChart ビジュアルには、ハイコントラスト サポートが実装されています。

詳細は、「[PowerBI-visuals-sampleBarChart ビジュアル リポジトリ](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6)」を参照してください

## <a name="on-init"></a>初期化時

`options.host` の colorPalette メンバーには、ハイコントラスト モード用のいくつかのプロパティがあります。 これらのプロパティを使用して、ハイコントラスト モードがアクティブかどうかを判断し、そうである場合は使用する色を指定します。

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>Power BI がハイコントラスト モードであることを検出する

`host.colorPalette.isHighContrast` が `true` の場合は、ハイコントラスト モードがアクティブであり、ビジュアルはそれに応じて描画されます。

### <a name="get-high-contrast-colors"></a>ハイコントラストの色を取得する

ハイコントラスト モードでは、ビジュアルは次の色に限定されます。

* **前景**色は、線、アイコン、テキスト、輪郭、または図形の塗りつぶしを描画するために使用されます。
* **背景**色は、背景および線で囲まれた図形の塗りつぶしの色として使用されます。
* **前景に選択された**色は、選択された要素またはアクティブな要素を示すために使用されます。
* **ハイパーリンク**の色は、ハイパーリンク テキストに対してのみ使用されます。

> [!NOTE]
> 2 番目の色が必要な場合は、ある程度の不透明度で前景色を使用できます (Power BI のネイティブ ビジュアルでは 40% の不透明度が使用されます)。 ビジュアルの詳細を見やすくするために、これは控えめに使用してください。

これらの値は、初期化中に格納できます。

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

または、初期化中に `host` オブジェクトを格納し、更新中に関連する `colorPalette` プロパティにアクセスすることもできます。

## <a name="on-update"></a>更新時

ハイコントラスト サポートの具体的な実装はビジュアルに応じて異なり、グラフィック デザインの詳細に依存します。 通常、ハイコントラスト モードでは、重要な詳細情報を限られた色で区別しやすくするために、既定とは若干異なるデザインが必要になります。

Power BI ネイティブ ビジュアルが従うガイドラインの一部を以下に示します。

* すべてのデータ ポイントで同じ色 (前景) が使用されます。
* すべてのテキスト、軸、矢印、直線などでは 前景色が使用されます。
* 厚みのある図形は、太いストローク (少なくとも 2 ピクセル) と背景色の塗りつぶしを使用して、枠線として描画されます。
* 関連性がある場合、データ ポイントは別々のマーカー図形によって区別され、データ行は異なるダッシュ線によって区別されます。
* あるデータ要素が強調表示されると、他のすべての要素の不透明度が 40% に変わります。
* スライサーの場合、アクティブなフィルター要素では前景に選択された色が使用されます。

たとえばサンプルの棒グラフでは、すべてのバーが太さ 2 ピクセルの前景の枠線および背景の塗りつぶしで描画されています。 既定の色と、2 つのハイコントラスト テーマを使用した場合の外観を比較してください。

![標準色を使用したサンプルの棒グラフ](./media/hc-samplebarchart-standard.png)
![*黒 #2* の色テーマを使用したサンプルの棒グラフ](./media/hc-samplebarchart-dark2.png)
![*白* の色テーマを使用したサンプルの棒グラフ](./media/hc-samplebarchart-white.png)

次の場所は、ハイコントラストをサポートするように変更された `visualTransform` 関数の 1 つの場所で、これは `update` 中にレンダリングの一部として呼び出されます。

### <a name="before"></a>より前

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>後

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
