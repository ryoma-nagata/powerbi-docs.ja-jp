---
title: イベントのレンダリング
description: Power BI ビジュアルは、Power Point または PDF にエクスポートする準備ができていることを Power BI に通知できます
author: Yarovinsky
ms.author: alexyar
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 46166b3503a770e033b98474fcf9240235296cc2
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425093"
---
# <a name="event-service"></a>イベント サービス

新しい API は、レンダリング中に呼び出す必要がある 3 つのメソッド (開始、終了、失敗) で構成されます。

レンダリングが開始されると、カスタム ビジュアル コードは、renderingStarted メソッドを呼び出して、レンダリング プロセスが開始されたことを示します。

レンダリングが正常に完了した場合、カスタム ビジュアル コードは、即座に `renderingFinished` メソッドを呼び出して、ビジュアルのイメージの準備ができたことをリスナーに通知します (**主に "PDF へのエクスポート" と "PowerPoint へのエクスポート"** )。

レンダリング処理中に問題が発生してカスタム ビジュアルが正常に完了しなかった場合、 カスタム ビジュアル コードは、`renderingFailed` メソッドを呼び出して、レンダリング プロセスが完了していないことをリスナーに通知する必要があります。 また、このメソッドは、エラーの原因に関するオプションの文字列も提供します。

## <a name="usage"></a>Usage

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering was started. 
     * Usually at the very start of the update method.
     *
     * @param options - the visual update options received as update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Shoudl be called immediately after finishing successfull rendering.
     * 
     * @param options - the visual update options received as update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering failed with optional reason string
     * 
     * @param options - the visual update options received as update parameter
     * @param reason - the option failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="simple-sample-the-visual-hasnt-any-animations-on-rendering"></a>簡易サンプル。 レンダリング時にビジュアルにアニメーションが表示されない

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

### <a name="sample-the-visual-with-animation"></a>サンプル。 アニメーションを使用したビジュアル

ビジュアルにレンダリングするアニメーションまたは非同期関数がある場合は、アニメーションの後または非同期関数の内部で `renderingFinished` メソッドを呼び出す必要があります。

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
            // read more https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>ビジュアル認定のためのレンダリング イベント

ビジュアルによるレンダリング イベントのサポートは、ビジュアル認定の要件の 1 つです。 [認定要件](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)に関する詳細を確認してください
