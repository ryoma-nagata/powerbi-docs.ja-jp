---
title: Power Query のバックグラウンド更新を無効にする
description: Power Query のバックグラウンド更新を無効にする場合のガイダンス。
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 39eef27e746e636ddb331d28a930c1cd0dca0a5d
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214921"
---
# <a name="disable-power-query-background-refresh"></a>Power Query のバックグラウンド更新を無効にする

この記事は、Power BI Desktop を使用するインポート データのモデラーを対象としています。

既定では、Power Query ではデータをインポートするときに、クエリごとに最大 1,000 行のプレビュー データがキャッシュされます。 プレビュー データは、ソース データと、クエリの各ステップの変換結果のクイック プレビューを表示するのに役立ちます。 これは、Power BI Desktop ファイル内ではなく、ディスク上に個別に格納されます。

ただし、Power BI Desktop ファイルに多数のクエリが含まれている場合、プレビュー データを取得して保存すると、更新の完了にかかる時間が長くなる可能性があります。

## <a name="recommendation"></a>推奨事項

"_バックグラウンドで_" プレビュー キャッシュを更新するように Power BI Desktop ファイルを設定することで、更新を高速化することができます。 Power BI Desktop では、 _[ファイル]、[オプションと設定]、[オプション]_ の順に選択し、 _[データの読み込み]_ ページを選択することでこれを有効にできます。 次に、 **[バックグランドでのデータ プレビューのダウンロードを許可する]** オプションをオンにします。 このオプションは、現在のファイルに対してのみ設定できることに注意してください。

![バックグラウンド データ オプションを示す Power BI Desktop のスクリーンショット。](media/power-query-background-refresh/power-query-options-background-data.png)

バックグラウンド更新を有効にすると、プレビュー データが期限切れになる可能性があります。 これが発生すると、Power Query エディターから次の警告が通知されます。

![古いプレビュー データに関する Power Query エディターの警告を示す Power BI Desktop のスクリーンショット。](media/power-query-background-refresh/power-query-preview-data-old.png)

プレビュー キャッシュはいつでも更新することができます。 1 つのクエリに対して更新することも、 **[プレビューの更新]** コマンドを使用してすべてのクエリに対して更新することもできます。 これは、Power Query エディター ウィンドウの **ホーム** リボンにあります。

![プレビュー データを更新するための Power Query エディター コマンドを示す Power BI Desktop のスクリーンショット。](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>次の手順

この記事に関する詳細については、次のリソースを参照してください。

- [Power Query のドキュメント](/power-query/)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
