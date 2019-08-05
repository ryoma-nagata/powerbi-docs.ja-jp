---
title: ランディング ページ
description: Power BI ビジュアルにランディング ページを追加する方法
author: sranins
ms.author: rasala
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 44cc9314b31803c97d3203d4aab846685d8f88fa
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424886"
---
# <a name="landing-page"></a>ランディング ページ

API 2.3.0 を使用すると、ビジュアルにランディング ページを追加できます。これを行うには、`supportsLandingPage` を機能に追加し、これを true に設定します。これにより、データを追加する前にビジュアルの初期化と更新が行われます (つまり、ウォーターマークが表示されなくなります)。したがって、データがない場合にビジュアルに表示する独自のランディング ページをデザインできます。

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

サンプル

![ランディング ページのスクリーンショット](./media/landing-page.png)
