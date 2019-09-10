---
title: Power BI ビジュアルでスライサーの同期機能を有効にする
description: この記事では、Power BI ビジュアルにスライサーの同期機能を追加する方法を説明します。
author: EugeneElkin
ms.author: v-evelk
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 4d7b73a5d06f34fd197464d4444d0e19d6c1c026
ms.sourcegitcommit: b602cdffa80653bc24123726d1d7f1afbd93d77c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70237215"
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

![[スライサーの同期] ウィンドウ](./media/sync-slicers-panel.png)

**[スライサーの同期]** ウィンドウでは、スライサーの表示とそのフィルター処理を複数のレポート ページに適用できることがわかります。
