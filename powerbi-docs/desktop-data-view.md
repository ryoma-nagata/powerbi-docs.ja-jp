---
title: Power BI Desktop のデータ ビュー
description: Power BI Desktop のデータ ビュー
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 87a72ba5ac69334c04e65871c81a9006e183d88d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876369"
---
# <a name="data-view-in-power-bi-desktop"></a>Power BI Desktop のデータ ビュー
**データ ビュー**は、**Power BI Desktop** モデル内のデータを検査、調査、理解するのに役立ちます。 これは、**クエリ エディター**内のテーブル、列、データの表示方法とは異なります。 データ ビューには、モデルに読み込まれた *後* のデータが表示されます。

データをモデル化しているときに、レポート キャンバスにビジュアルを作成することなく、実際のテーブルまたは列の内容を行レベルまで確認したい場合があります。 これは、メジャーと計算列を作成している場合や、データ型またはデータのカテゴリを識別する必要に特に便利です。

それでは、**データ ビュー**の要素のいくつかを詳しく見てみましょう。

![Power BI Desktop のデータ ビュー](media/desktop-data-view/dataview_fullscreen.png)

1. **[データ ビュー] アイコン** – このアイコンを選択すると、データ ビューに入ります。

2. **[データ グリッド]** – 選んだテーブルとその中のすべての列と行を表示します。 **レポート ビュー**に表示されない列はグレー表示されます。列を右クリックしてオプションを表示できます。

3. **[モデリング] リボン** – ここでは、リレーションシップの管理、計算の作成、列のデータ型、書式設定、データ カテゴリの変更を行うことができます。

4. **[数式] バー** – メジャーと計算列の DAX 数式を入力します。

5. **[検索]** – モデル内のテーブルまたは列を検索します。

6. **[フィールド] 一覧** – データ グリッドに表示するテーブルまたは列を選びます。

## <a name="filtering-in-data-view"></a>データ ビューでフィルター処理

**データ ビュー**では、データにフィルターを適用したり、並べ替えたりすることもできます。 各列には、並べ替え方向を示すアイコンが表示されます (適用された場合)。

![Power BI Desktop のデータ ビューの並べ替えとフィルター処理](media/desktop-data-view/dataview_sort-and-filter.png)

個々の値にフィルターを適用したり、列のデータに基づいて高度なフィルター処理を適用したりできます。 

> [!NOTE]
> 現在のユーザー インターフェイスとは異なるカルチャで Power BI モデルが作成されている場合 (たとえば、モデルがアメリカ英語で作成されているとき、それをスペイン語で表示している)、テキスト フィールド以外のあらゆるものに関して、データ ビュー ユーザー インターフェイスには検索ボックスが表示されません。
