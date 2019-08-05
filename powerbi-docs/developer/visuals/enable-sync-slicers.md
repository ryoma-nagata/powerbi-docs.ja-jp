---
title: スライサーの同期を有効にする
description: Power BI ビジュアルのスライサーの同期機能を追加する方法
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 9966475e8bcaccad2090451b47ef09ef0a9af125
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425024"
---
# <a name="sync-slicers"></a>スライサーの同期

[スライサーの同期](https://docs.microsoft.com/power-bi/desktop-slicers)をサポートするには、カスタム スライサー ビジュアルで API 1.13 以上を使用する必要があります。

2 番目の必要な側面は、`capabilities.json` 内の有効化オプションです (次のサンプルを参照してください)。

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

`capabilities.json` の変更後、カスタム スライサー ビジュアルをクリックすると、[スライサーの同期] オプション パネルが表示されます。

> [!NOTE]
> スライサーの同期では複数のフィールドがサポートされないため、スライサーに複数のフィールド (カテゴリまたはメジャー) があると、この機能は無効になります。

![[スライサーの同期] パネル](./media/sync-slicers-panel.png)

パネルでは、スライサーの可視性とそのフィルターがいくつかのレポート ページに適用される可能性があることを確認できます。
