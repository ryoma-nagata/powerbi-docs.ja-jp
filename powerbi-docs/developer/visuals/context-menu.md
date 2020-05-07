---
title: Power BI ビジュアルの機能とプロパティ
description: この記事では、Power BI ビジュアルの機能とプロパティについて説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 7d24ea77fd73ca6a83176d1b8560c88fa98a8d6b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "79380757"
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
