---
title: Power BI ビジュアルにランディング ページを追加する
description: この記事では、Power BI ビジュアルにランディング ページを追加する方法を説明します。
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d15c52134fe3c8638625e50a1374867a4abed3c1
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70236696"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Power BI ビジュアルにランディング ページを追加する

API 2.3.0 では、Power BI のビジュアルにランディング ページを追加できます。 それを行うには、機能に `supportsLandingPage` を追加して、true に設定します。 これにより、データを追加する前にビジュアルが初期化されて更新されます。 ビジュアルにはウォーターマークが表示されなくなるため、ビジュアルにデータがないときにビジュアルに表示される独自のランディング ページをデザインできます。

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

次の図に、ランディング ページの例を示します。

![ランディング ページのスクリーンショット](./media/landing-page.png)
