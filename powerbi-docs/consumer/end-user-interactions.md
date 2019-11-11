---
title: レポート内のビジュアルの相互作用について理解する
description: レポート ページでビジュアルがどのように相互作用するかについて説明する Power BI エンド ユーザー向けドキュメント。
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 28e6cea55b02fabddd0b2f118631a09c0344b66f
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863092"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Power BI のレポート内でビジュアルがどのように相互作用するか
Power BI の優れた機能の 1 つは、レポート ページ上のすべてのビジュアルが相互接続される方法です。 ビジュアルのいずれかのデータ ポイントを選択すると、そのデータを含むページ上の他のすべてのビジュアルが選択に基づいて変化します。 

![ビジュアルの相互作用のビデオ](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>ビジュアルの相互作用のしくみ

既定では、レポート ページ上の 1 つのビジュアルでデータ ポイントを選択すると、そのページ上の他のビジュアルに対してクロスフィルター処理またはクロス強調表示が行われます。 ページ上のビジュアルがどのように相互作用するかは、レポート *デザイナー*によって設定されます。 *デザイナー*には、視覚的な相互作用のオンとオフを切り替えるオプションと、既定のクロスフィルター処理、クロス強調表示、および[詳細表示](end-user-drill.md)の動作を変更するオプションがあります。 

階層または詳細表示を目にしたことがない場合、[Power BI でのドリル ダウン](end-user-drill.md)に関する記事を読んで詳細を学ぶことができます。 

データに含まれる 1 つの値が他の値にどのように貢献しているかを確認するには、クロスフィルター処理およびクロス強調表示が役立ちます。 たとえば、ドーナツ グラフで [Moderation] セグメントを選択すると、[Total units by Month] グラフにおけるそのセグメントの各列に対する貢献が強調表示されます。また、折れ線グラフがフィルター処理されます。

![ビジュアルの相互作用をとらえた画像](media/end-user-interactions/power-bi-interactions.png)

「[フィルター処理と強調表示について](end-user-report-filter.md)」を参照してください。 


  
> [!NOTE]
> *クロスフィルター処理* と *クロス強調表示* という用語は、ここで説明する動作を、 **[フィルター]** ウィンドウを使ってビジュアルのフィルター処理と強調表示を行う場合の動作と区別するために使用しています。  

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
- [詳細表示](end-user-drill.md)に対応しているビジュアルがレポートに含まれる場合、既定では、あるビジュアルに詳細表示を適用してもレポート ページの他のビジュアルは変更されません。     
- visualA を使用して visualB とやりとりすると、visualA のビジュアルレベル フィルターが visualB にも適用されます。

## <a name="next-steps"></a>次の手順
[レポート フィルターの使用方法](../power-bi-how-to-report-filter.md)
