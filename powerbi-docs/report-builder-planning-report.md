---
title: Power BI レポート ビルダーでのレポートの計画
description: Power BI の改ページ調整されたレポート ビルダーを使用して、さまざまな種類のページ分割されたレポートを作成できます。 便利でわかりやすいレポートを作成するには、まず計画を立てると役立ちます。
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: fd4a318d7a61f6f2298de6b9d5d23ad2ae063d28
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840512"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>Power BI レポート ビルダーでのレポートの計画
  Power BI の改ページ調整されたレポート ビルダーを使用して、さまざまな種類のページ分割されたレポートを作成できます。 たとえば、売上データの概要または詳細、マーケティングと売上の傾向、運用レポート、ダッシュボードを表示するレポートを作成できます。 表現力豊かな書式付きテキストを活用したレポート (販売注文、製品カタログ、定型書簡など) を作成することもできます。 レポート ビルダーで同じ基本的な構成要素をさまざまに組み合わせて使用することで、これらすべてのレポートが作成されます。 便利でわかりやすいレポートを作成するには、まず計画を立てると役立ちます。 開始する前に考慮できるいくつかの事柄を次に示します。  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>レポートをどのような形式で表示するか
  
レポートは、Power BI ポータルなどのブラウザーにオンラインでレンダリングしたり、Excel、Word、PDF などの他の形式にエクスポートしたりできます。 すべてのエクスポート形式ですべての機能を利用できるわけではないため、レポートの最終的な形式は重要な考慮事項です。 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>データをどのような構造で表示するか
  
テーブル、マトリックス (クロス集計レポートやピボット テーブル レポートに似ています)、グラフ、自由形式構造、またはこれらを組み合わせてデータを表示できます。 詳細については、[Power BI レポート ビルダーでのテーブル、マトリックス、およびリスト](report-builder-tables-matrices-lists.md)に関する記事を参照してください。  
  
## <a name="how-do-you-want-your-report-to-look"></a>どのような外観のレポートにするか
  
レポート ビルダーには、レポートを読みやすくしたり、重要な情報を強調表示したり、対象ユーザーがレポートを移動しやすくしたりするためにレポートに追加できるレポート アイテムが多数用意されています。 レポートの外観をどのようにするかを知っておくことで、テキストボックス、四角形、画像、直線などのレポート アイテムが必要かどうかを判断できます。 アイテムの表示/非表示、ドキュメント マップの追加、詳細レポートまたはサブレポートの包含、または他のレポートへのリンクも実行できます。   
  
## <a name="should-the-data-be-filtered"></a>データのフィルター処理が必要か
  
レポートのスコープを特定のユーザー、場所、または期間に絞り込むことができます。 レポート データをフィルター処理するには、パラメーターを使用して必要なデータのみを取得して表示します。 詳細については、[Power BI レポート ビルダーでのレポート パラメーター](paginated-reports-parameters.md)に関する記事を参照してください。  
  
## <a name="do-you-need-to-create-calculations"></a>計算を作成する必要があるか 
  
     Sometimes, your data source and datasets do not contain the exact fields that you need for your report. In that situation, you might have to create your own calculated fields. For example, you might want to multiply the price per unit times the quantity to get a line item sales amount. Expressions are also used to provide conditional formatting and other advanced features. For more information, see [Expressions in Power BI Report Builder](report-builder-expressions.md).  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>最初はレポート アイテムを非表示にするか
  
レポートの初回の実行時に、データ領域、グループ、および列などのレポート アイテムを非表示にするかどうかを検討します。 たとえば、概要テーブルを最初に表示し、その後で詳細なデータにドリルダウンできます。 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>レポートをどのように配信するか  
  
     You can save your report to your local computer and continue to work on it, or run it locally for your own information. However, to share your report with others, you need to save the report to Power BI. Saving it to Power BI lets others run it whenever they want to. Alternatively, you can set up a subscription and e-mail delivery of the report to other individuals. You can have the report delivered in a specific export format if you prefer. 
  
## <a name="next-steps"></a>次の手順

- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
