---
title: Power BI Desktop のモデル ビュー
description: Power BI Desktop のモデル ビュー
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ea568c061142e66e79351de8a6c0f0603a46f775
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "76753229"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Power BI Desktop でモデル ビューを操作する

"*モデル ビュー*" には、モデル内のすべてのテーブル、列、リレーションシップが表示されます。 このビューは、モデルに多数のテーブル間の複雑な関係がある場合に特に役立ちます。

ウィンドウの横にある **[モデル]** アイコンを選択すると、既存のモデルのビューが表示されます。 リレーションシップ行の上にカーソルを置くと、使用されている列が表示されます。

![モデル ビュー、Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

この図では、"*Stores*" テーブルに "*StoreKey*" 列があり、これは "*Sales*" テーブル (同様に "*StoreKey*" 列がある) に関連付けられています。 2 つのテーブルには "*多対一*" (\*:1) のリレーションシップがあります。 線の中央の矢印は、フィルター コンテキスト フローの方向を示しています。 二重矢印は、クロス フィルターの方向が "*両方*" に設定されていることを意味します。

リレーションシップをダブルクリックすると、 **[リレーションシップの編集]** ダイアログ ボックスで開くことができます。 リレーションシップについて詳しくは、「[Power BI Desktop でのリレーションシップの作成と管理](desktop-create-and-manage-relationships.md)」をご覧ください。
