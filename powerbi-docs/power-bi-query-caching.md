---
title: Power BI Premium でのクエリのキャッシュ
description: Power BI Premium でのクエリのキャッシュ
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/16/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: e45773784fbe97f8521ad071c03e86dcbddddbeb
ms.sourcegitcommit: 4689766f08f5285deac50bec595d57c3a398fff5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68329115"
---
# <a name="query-caching-in-power-bi-premium"></a>Power BI Premium でのクエリのキャッシュ

Power BI Premium を使用する組織は、*クエリ キャッシュ*を活用して、データセットに関連付けられたレポートを高速化できます。 クエリ キャッシュにより、Premium 容量はそのローカル キャッシュ サービスを使用してクエリ結果を維持するよう指示され、基になるデータ ソースによってそれらの結果が計算されることが回避されます。

> [!IMPORTANT]
> クエリ キャッシュは Power BI Premium でのみ利用できます。 Azure Analysis Services または SQL Server Analysis Services を利用する LiveConnect データセットに適用することはできません。

キャッシュされたクエリ結果は、ユーザーおよびデータセットのコンテキストに固有であり、常にセキュリティ規則を順守します。 現時点では、このサービスでは、表示した最初のページに対してのみクエリ キャッシュが行われます。 つまり、レポートと対話する際には、クエリはキャッシュされません。 クエリ キャッシュは[個人用ブックマーク](consumer/end-user-bookmarks.md#personal-bookmarks)と[固定フィルター](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/)を尊重します。そのため、個人用レポートによって生成されたクエリはキャッシュされます。 同じクエリを利用する[ダッシュボードのタイル](service-dashboard-tiles.md)も、クエリがキャッシュされることでメリットを得られます。 パフォーマンスは、データセットが頻繁にアクセスされてあまり更新する必要がない場合に、特に大きなメリットを得られます。 クエリ キャッシュにより、全体的なクエリ数を減少させることで、Premium 容量に対する負荷を軽減することもできます。

クエリ キャッシュの動作は、Power BI サービスのデータセット用の **[設定]** ページで制御します。 ここには次の 2 つの設定があります。

- **オフ**: このデータセットにはクエリ キャッシュを使用しません。

- **オン**: このデータセットにはクエリ キャッシュを使用します。

![[クエリ キャッシュ] ダイアログ ボックス](media/power-bi-query-caching/power-bi-query-caching.png)

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

- キャッシュの設定を **[オン]** から **[オフ]** に変更すると、以前に保存されたデータセットのクエリ結果が容量のキャッシュから削除されます。 キャッシュは明示的にオフにするか、または管理者が容量の既定値を **[オフ]** に設定していた場合は規定値に戻すことで、オフにすることができます。 キャッシュをオフにすると、レポートで次回このデータセットに対してクエリを実行する際に、わずかな遅延が生じる可能性があります。 遅延は、保存された結果を活用しないでオンデマンドで実行される、こうしたレポート クエリが原因で発生します。 また、クエリを処理するには、まず必須のデータセットをメモリに読み込まなければならない場合があります。
- クエリ キャッシュを最新の情報に更新したら、Power BI では、基になるデータ モデルに対してクエリを実行し、最新の結果を取得する必要があります。 大量のデータセットでクエリ キャッシュが有効になっているとき、Premium 容量の負荷が高い場合は、キャッシュの更新中にパフォーマンスが低下する可能性があります。 パフォーマンスの低下は、実行されるクエリの量が増えることで発生します。

## <a name="next-steps"></a>次の手順

[Power BI Premium とは何ですか?](service-premium-what-is.md)

