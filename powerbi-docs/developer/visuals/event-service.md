---
title: Power BI ビジュアルでイベントをレンダリングする
description: Power BI ビジュアルでは、PowerPoint または PDF にエクスポートする準備ができたことを Power BI に通知できます。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 873968a89a230171d8fecba81a7d528767ee7077
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819148"
---
# <a name="render-events-in-power-bi-visuals"></a>Power BI ビジュアルでイベントをレンダリングする

新しい API は、レンダリング中に呼び出す必要がある 3 つのメソッド (`started`、`finished`、`failed`) で構成されます。

レンダリングが開始されたら、Power BI ビジュアルのコードで `renderingStarted` メソッドを呼び出して、レンダリング プロセスが開始されたことを示します。

レンダリングが正常に完了した場合は、Power BI ビジュアルのコードで即座に `renderingFinished` メソッドを呼び出して、ビジュアルのイメージをエクスポートする準備ができたことを、リスナーに通知します (主に "*PDF へのエクスポート*" と "*PowerPoint へのエクスポート*")。

プロセスの間に問題が発生した場合、Power BI ビジュアルは正常にレンダリングされません。 レンダリング プロセスが完了していないことをリスナーに通知するには、Power BI ビジュアルのコードで `renderingFailed` メソッドを呼び出す必要があります。 また、このメソッドでは、障害の理由を示すオプションの文字列も提供します。

## <a name="usage"></a>使用

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>サンプル: ビジュアルにアニメーションが表示されない

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>サンプル: ビジュアルにアニメーションが表示される

ビジュアルにレンダリングするアニメーションまたは非同期関数がある場合は、アニメーションの後または非同期関数の内部で、`renderingFinished` メソッドを呼び出す必要があります。

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>ビジュアル認定のためのレンダリング イベント

ビジュアル認定の要件の 1 つは、ビジュアルによるレンダリング イベントのサポートです。 詳細については、「[認定要件](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)」をご覧ください。
