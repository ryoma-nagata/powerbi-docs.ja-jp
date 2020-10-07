---
title: Power BI ビジュアルでスライサーの同期機能を有効にする
description: この記事では、Power BI ビジュアルにスライサーの同期機能を追加する方法を説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 4e9989bb7a34a89cb6244a2378d6660a5079fc82
ms.sourcegitcommit: 6bc66f9c0fac132e004d096cfdcc191a04549683
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/06/2020
ms.locfileid: "91748105"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Power BI ビジュアルでのスライサーの同期

[スライサーの同期](../../visuals/power-bi-visualization-slicers.md)機能をサポートするには、カスタム スライサー視覚化で API バージョン 1.13.0 以降を使用する必要があります。

さらに、次のコードで示すように、*capabilities.json* ファイルでオプションを有効にする必要があります。

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

*capabilities.json* ファイルを更新した後は、カスタム スライサー ビジュアルを選択したときに、 **[スライサーの同期]** オプション ウィンドウを表示できます。

> [!NOTE]
> スライサーの同期機能では、複数のフィールドはサポートされていません。 スライサーに複数のフィールド (**カテゴリ**または**メジャー**) がある場合、機能は無効になります。

![[スライサーの同期] ウィンドウ](media/enable-sync-slicers/sync-slicers-panel.png)

**[スライサーの同期]** ウィンドウでは、スライサーの表示とそのフィルター処理を複数のレポート ページに適用できることがわかります。