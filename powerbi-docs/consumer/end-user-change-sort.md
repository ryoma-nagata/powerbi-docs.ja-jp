---
title: レポートでのグラフの並べ替え方法の変更
description: Power BI レポートでのグラフの並べ替え方法の変更
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/28/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: e325d13dd8001e8da41dc5602bf3f7dbba2f371f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73852386"
---
# <a name="change-how-a-chart-is-sorted-in-a-power-bi-report"></a>Power BI レポートでのグラフの並べ替え方法の変更

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Power BI サービスでは、さまざまなデータ フィールドを並べ替えることで視覚効果を変更できます。 並べ替えで視覚化を変更することで、伝えたい情報を強調でき、その傾向 (あるいは強調したい点) を視覚化に反映させることができます。

数値データ (売り上げ高など) を使用している場合でも、テキスト データ (州名など) を使用している場合でも、必要に合わせて視覚エフェクトを並べ替え、目的に応じたスタイルで表示できます。 Power BI は柔軟な並べ替え機能とクイック メニューを備えています。 視覚効果画面で**その他の操作** (...) を選択し、並べ替えるフィールドを選択します。

![X 軸がアルファベット順で並べ替えられた横棒グラフ](media/end-user-change-sort/power-bi-more-actions.png)

ダッシュボード上のビジュアルを並べ替えることはできませんが、Power BI レポートのほとんどの視覚エフェクトは、グラフ内のカテゴリ名のアルファベット順や、各カテゴリの数値順に、並べ替えることができます。 たとえば、このグラフは**店舗名**のカテゴリを基準としてアルファベット順に並べ替えられています。

![X 軸がアルファベット順で並べ替えられた横棒グラフ](media/end-user-change-sort/pbi-chartsortcategory.png)

カテゴリ (店舗名) から値 (平方フィートごとの売上) に、並べ替えの基準を簡単に変更できます。

1. **その他の操作** (...) を選び、 **[並べ替え] > [Sales Per Sq Ft]\(平方フィートごとの売上\)** を選びます。
2. 必要に応じて、もう一度**その他の操作** (...) を選び、 **[降順で並べ替え]** を選びます。 並べ替えに使用されているフィールドは太字で表示され、黄色のバーが表示されます。

   ![[並べ替え]、[昇順で並べ替え]、[降順で並べ替え] の順に選択しているビデオ](media/end-user-change-sort/sort.gif)

> [!NOTE]
> すべてのビジュアルが並べ替え可能なわけではありません。 たとえば、次のビジュアルは並べ替えできません: ツリーマップ、マップ、塗り分け地図、散布図、ゲージ、カード、ウォーターフォール。

## <a name="saving-changes-you-make-to-sort-order"></a>並べ替え順序の変更を保存する
Power BI レポートでは、フィルター、スライサー、並べ替え、その他のデータ ビューに行った変更が保存されます。 そのため、レポートを終了し後で戻ったときに、変更が保存されています。  レポートのデザイナーの設定に戻す場合、上のメニュー バーから **[既定値にリセット]** を選択します。 

![永続的な並べ替え](media/end-user-change-sort/power-bi-reset.png)

ただし、 **[既定値にリセット]** ボタンが淡色表示になっている場合、変更を保存する (永続化する) 機能をレポートのデザイナーが無効にしています。

<a name="other"></a>
## <a name="sorting-using-other-criteria"></a>その他の条件を使用した並べ替え
別のフィールド (ビジュアルには含まれません) またはその他の条件を使用して、ビジュアルを並べ替えたい場合があります。  たとえば、月のアルファベット順ではなく数字順に並べ替えることや、数値を桁ごとにではなく数値全体で比較して (たとえば、0、1、20、9 ではなく、0、1、9、20 の順序で) 並べ替えることができます。  レポートのデザイナーは、この種の並べ替えを実行できるようにデータセットを更新することができます。 デザイナーの連絡先情報は、ヘッダー バーからレポート名を選択することで確認できます。

![連絡先情報を示すドロップダウン](media/end-user-change-sort/power-bi-contact.png)

## <a name="next-steps"></a>次の手順
「[Power BI での視覚化](end-user-visualizations.md)」をご覧ください。

[Power BI - 基本的な概念](end-user-basic-concepts.md)
