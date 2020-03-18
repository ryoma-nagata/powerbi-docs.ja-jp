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
ms.openlocfilehash: 88e7e4b83f303f2b366f276b5020194f55f21f25
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380723"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Power BI ビジュアルでのスライサーの同期

[スライサーの同期](https://docs.microsoft.com/power-bi/desktop-slicers)機能をサポートするには、カスタム スライサー ビジュアルで API バージョン 1.13 以降を使用する必要があります。

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
