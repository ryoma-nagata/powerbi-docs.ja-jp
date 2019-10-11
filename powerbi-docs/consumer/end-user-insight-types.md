---
title: Power BI でサポートされているインサイトの種類
description: Power BI でのクイック インサイトと詳細情報の表示。
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/2/2019
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 507d49ba6cdb894667bf66f8f35c5c325b9ff25e
ms.sourcegitcommit: b7a9862b6da940ddebe61bc945a353f91cd0e4bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2019
ms.locfileid: "71943919"
---
# <a name="types-of-insights-supported-by-power-bi"></a>Power BI でサポートされているインサイトの種類

Power BI サービスでは、ダッシュボードまたはレポートのインサイトを自動的に検索できます。

## <a name="how-does-insights-work"></a>インサイトのしくみ
Power BI はデータセットのさまざまなサブセットをすばやく検索します。 Power BI は検索する際、興味がある可能性のあるインサイトを検出するために一連の洗練されたアルゴリズムを適用します。 Power BI は、割り当てられた時間で、可能な限り多くのデータセットをスキャンします。

データセットまたはダッシュボードのタイルに対して、インサイトを実行できます。   

## <a name="what-types-of-insights-can-we-find"></a>見つけることができる情報の種類
使用されているアルゴリズムの一部を以下に示します。

## <a name="category-outliers-topbottom"></a>カテゴリ外れ値 (上/下)
モデル内のメジャーとして、ディメンションの 1 つまたは 2 つのメンバーが、ディメンションの他のメンバーよりも値がはるかに大きいケースを強調表示します。  

![カテゴリの外れ値の例](./media/end-user-insight-types/pbi_auto_insight_types_category_outliers.png)

## <a name="change-points-in-a-time-series"></a>時系列の変更点
データの時系列の傾向で、大きな変化があったときに強調表示します。

![時系列の変更点の例](./media/end-user-insight-types/pbi_auto_insight_types_changepoint.png)

## <a name="correlation"></a>相関関係
データセット内のディメンションに対してプロットした場合に、複数のメジャーで相互の相関関係が示されるケースを検出します。

![相関関係の例](./media/end-user-insight-types/pbi_auto_insight_types_correlation.png)

## <a name="low-variance"></a>低差異
データ ポイントが平均から離れていないケースを検出します。

![低差異の例](./media/end-user-insight-types/power-bi-low-variance.png)

## <a name="majority-major-factors"></a>マジョリティ (主要因子)
別のディメンションによって分類した場合に、合計値の大部分が単一の因子に帰する可能性があるケースを検索します。  

![主な要因の例](./media/end-user-insight-types/pbi_auto_insight_types_majority.png)

## <a name="overall-trends-in-time-series"></a>時系列の全体的な傾向
時系列データの上昇または下降の傾向を検出します。

![時系列の全体的な傾向の例](./media/end-user-insight-types/pbi_auto_insight_types_trend.png)

## <a name="seasonality-in-time-series"></a>時系列の周期性
週単位、月単位、または年単位の周期性などの時系列データの定期的なパターンを見つけます。

![周期性の例](./media/end-user-insight-types/pbi_auto_insight_types_seasonality_new.png)

## <a name="steady-share"></a>安定した共有
連続した変数にわたる親の全体の値に関連して、子の値のシェア間に親子の相関関係があるケースを強調表示します。

![安定した共有の例](./media/end-user-insight-types/pbi_auto_insight_types_steadyshare.png)

## <a name="time-series-outliers"></a>時系列外れ値
時系列全体にわたるデータに対して、その他の日付/時刻値と大きく異なる値を持つ特定の日付や時刻がある場合を検出します。

![時系列外れ値の例](./media/end-user-insight-types/pbi_auto_insight_types_time_series_outliers.png)

## <a name="next-steps"></a>次の手順
[Power BI のインサイト](end-user-insights.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

