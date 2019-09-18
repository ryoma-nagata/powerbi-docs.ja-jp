---
title: レポートでのグラフの並べ替え方法の変更
description: Power BI レポートでのグラフの並べ替え方法の変更
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 08/21/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 98a91b0651e7a357f0ba0462f6ba8734c64ab162
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2019
ms.locfileid: "70302744"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Power BI レポートでのグラフの並べ替え方法の変更
Power BI レポートのほとんどの視覚エフェクトは、グラフ内のカテゴリ名のアルファベット順や、各カテゴリの数値順に、並べ替えることができます。 たとえば、このグラフは**店舗名**のカテゴリを基準に並べ替えられています。

![X 軸がアルファベット順で並べ替えられた横棒グラフ](media/end-user-change-sort/pbi_chartsortcategory.png)

カテゴリ (店舗名) から値 (平方フィートごとの売上) に、並べ替えの基準を簡単に変更できます。

1. 省略記号 ([...]) を選び、 **[並べ替え] > [Sales Per Sq Ft]\(平方フィートごとの売上\)** を選びます。
2. 必要に応じて、もう一度省略記号を選び、 **[降順で並べ替え]** を選びます。

   ![[並べ替え]、[昇順で並べ替え]、[降順で並べ替え] の順に選択しているビデオ](media/end-user-change-sort/sort.gif)

> [!NOTE]
> すべてのビジュアルが並べ替え可能なわけではありません。 たとえば、次のビジュアルは並べ替えできません: ツリーマップ、マップ、塗り分け地図、散布図、ゲージ、カード、ウォーターフォール。

## <a name="saving-changes-you-make-to-sort-order"></a>並べ替え順序の変更を保存する
Power BI レポートでは、フィルター、スライサー、並べ替え、その他のデータ ビューに行った変更が保存されます。 そのため、レポートを終了し後で戻ったときに、変更が保存されています。  レポートのデザイナーの設定に戻す場合、上のメニュー バーから **[既定値にリセット]** を選択します。 

![永続的な並べ替え](media/end-user-change-sort/power-bi-reset.png)

ただし、 **[既定値にリセット]** ボタンが淡色表示になっている場合、変更を保存する (永続化する) 機能をレポートのデザイナーが無効にしています。

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>その他の条件を使用した並べ替え
別のフィールドまたはその他の条件を使用して、ビジュアルを並べ替えたい場合があります。  たとえば、月のアルファベット順ではなく数字順に並べ替えることや、数値を桁ごとにではなく数値全体で比較して (たとえば、0、1、20、9 ではなく、0、1、9、20 の順序で) 並べ替えることができます。  

場合によっては、自由にビジュアルを並べ替えることができます (月別など)。  並べ替えられない場合は、レポートの基になっているデータセットの調整が必要な可能性があります。 レポートのデザイナーにデータセットを更新するよう依頼してください。

## <a name="next-steps"></a>次の手順
「[Power BI での視覚化](end-user-visualizations.md)」をご覧ください。

[Power BI - 基本的な概念](end-user-basic-concepts.md)
