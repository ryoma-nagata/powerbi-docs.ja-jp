---
title: Power BI ビジュアルにコンテキスト メニューを追加する
description: Power BI の視覚化にコンテキスト メニューを追加する方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 9e63a1196ddc7557fcf8b2fceb424415a63d4df9
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748082"
---
# <a name="add-context-menu-to-power-bi-visual"></a>Power BI ビジュアルにコンテキスト メニューを追加する

`selectionManager.showContextMenu()` とパラメーター `selectionId` と (`{x:, y:}` オブジェクトとしての) 位置を使用して、ビジュアル用のコンテキスト メニューを Power BI に表示させることができます。

> [!IMPORTANT]
> この `selectionManager.showContextMenu()` は、Visuals API 2.2.0 で導入されました。

通常は、参照用のサンプル BarChart に追加されている右クリック イベント (タッチ デバイスの場合は長押し) Context-Menu として追加されます。

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
