---
title: ビジュアルの動的な参照線を作成する
description: Power BI サービスでビジュアルの動的な参照線を作成します
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/14/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ce99539e1804746970eae20dc9396f0f0536afea
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61184108"
---
# <a name="create-dynamic-reference-lines-for-visuals-in-the-power-bi-service"></a>Power BI サービスでビジュアルの動的な参照線を作成します

**Power BI サービス**の **[分析]** ウィンドウによって、動的な*参照線*を視覚化に追加して、重要な傾向や情報に注目させることができます。

![](media/service-analytics-pane/power-bi-analytics-pane.png)

> [!NOTE]
> **[分析]** ウィンドウは、レポート キャンバスでビジュアルを選択した場合にのみ表示されます。
> 
> 

## <a name="use-the-analytics-pane"></a>[分析] ウィンドウを使用する
**[分析]** ウィンドウでは、次の種類の動的参照線を作成できます (ビジュアルの種類によっては使用できないものがあります)。

* X 軸の定数線
* Y 軸の定数線
* 最小値線
* 最大値線
* 平均線
* 中央値線
* 百分位線


ビジュアルで使用可能な動的参照線を表示するには、次のようにします。

1. ビジュアルを選択または作成した後、 **[視覚化]** ウィンドウの **[分析]** アイコン ![](media/service-analytics-pane/power-bi-analytics-icon.png) を選びます。

2. 作成する線の種類の下矢印を選択して、オプションを展開します。 この例では、 **[平均線]** を選択します。
   
   ![平均線を追加する](media/service-analytics-pane/power-bi-add.png)

3. 新しい線を作成するには、 **[+ 追加]** を選び、線の作成に使うメジャーを決定します。  **[メジャー]** ドロップダウンに、選んだ視覚エフェクトで使用可能なデータが自動的に設定されます。 ここでは、 **[Open store count]** を使ってみます。

5. 色、透明度、スタイル、位置 (ビジュアルのデータ要素を基準にして) など、線についてのあらゆる種類のオプションがあります。 線にラベルを付ける場合は、タイトルを設定して、 **[データ ラベル]** スライダーを **[オン]** にします。  この例では、線のタイトルを "*Avg # Open Stores*" にして、他のいくつかのオプションを次のようにカスタマイズします。
   
   ![平均線分析をカスタマイズする](media/service-analytics-pane/power-bi-average-line2.png)

1. **[分析]** ウィンドウの **[平均線]** 項目の横に数字が表示されます。 この数字は、ビジュアルで現在有効になっている動的な線の数とその種類を示します。 店舗数目標の 9 として **[定数線]** を追加した場合、 **[定数線]** 参照線もこのビジュアルに適用されたことが **[分析]** ウィンドウに示されます。
   
   ![](media/service-analytics-pane/power-bi-reference-lines.png)
   

**[分析]** ウィンドウで動的参照線を作成することにより、あらゆる種類の興味深い情報に焦点を当てることができます。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング

選択したビジュアルに動的参照線を適用できない場合は (この例では **[マップ]** ビジュアル)、 **[分析]** ウィンドウを選択すると次のように表示されます。
   
![分析は使用できない](media/service-analytics-pane/power-bi-no-lines.png)

動的参照線を使用できるかどうかは、使用されているビジュアルの種類によって決まります。 次の一覧では、現在各動的線を使用できるビジュアルを示します。

次のビジュアルではすべての動的線を使用できます。

* 面グラフ
* 折れ線グラフ
* 散布図
* 集合縦棒グラフ
* 集合横棒グラフ

次のビジュアルでは、 **[分析]** ウィンドウの *定数線* のみを使用できます。

* 積み上げ面グラフ
* 積み上げ横棒グラフ
* 積み上げ縦棒グラフ
* 100% 積み上げ横棒グラフ
* 100% 積み上げ縦棒グラフ

次のビジュアルでは、現在は *傾向線* のみを使用できます。

* 非積み上げ折れ線グラフ
* 集合縦棒グラフ

最後に、次のような非デカルト ビジュアルには、現在は **[分析]** ウィンドウの動的線を適用できません。

* マトリックス
* 円グラフ
* ドーナツ
* テーブル

## <a name="next-steps"></a>次の手順
[Power BI Desktop の [分析] ウィンドウ](desktop-analytics-pane.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

