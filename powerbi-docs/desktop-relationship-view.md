---
title: Power BI Desktop のリレーションシップ ビュー
description: Power BI Desktop のリレーションシップ ビュー
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: a947b5c0b957336f02d3ec2e27d2bfd36b36c639
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514351"
---
# <a name="relationship-view-in-power-bi-desktop"></a>Power BI Desktop のリレーションシップ ビュー
**リレーションシップ ビュー**には、モデル内のすべてのテーブル、列、リレーションシップが表示されます。 これは、モデルに多数のテーブル間の複雑な関係が含まれる場合に特に役立ちます。

では、見てみましょう。

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  [リレーションシップ ビュー] アイコン - クリックすると、リレーションシップ ビューにモデルが表示されます。

**B.** リレーションシップ – リレーションシップの上にカーソルを置くと、使用されている列が表示されます。 リレーションシップをダブルクリックすると、 **[リレーションシップの編集]** ダイアログ ボックスが開き、リレーションシップが表示されます。 

上の図では、*Stores* テーブルに*StoreKey* 列があり、この列は *Sales* テーブル (同様に *StoreKey* 列を持つ) に関連があることがわかります。 これは*多対一* (\*: 1) 関係であることがわかり、線の中央のアイコンは、クロス フィルターの方向が *両方* に設定されていることを示します。 アイコン上の矢印は、フィルター コンテキストのフローの方向を示しています。

リレーションシップについて詳しくは、「[Power BI Desktop でのリレーションシップの作成と管理](desktop-create-and-manage-relationships.md)」をご覧ください。

