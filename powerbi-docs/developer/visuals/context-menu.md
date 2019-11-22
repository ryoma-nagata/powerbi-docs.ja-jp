---
title: Power BI ビジュアルの機能とプロパティ
description: この記事では、Power BI ビジュアルの機能とプロパティについて説明します。
author: asander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 206f1aec7c76b00b6f725d8469eb3e483a01c653
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061778"
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
