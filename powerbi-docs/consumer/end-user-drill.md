---
title: ビジュアルのドリルダウンとドリルアップ
description: この記事では、Microsoft Power BI サービスでビジュアルをドリルダウンする方法について説明します。
author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 02/18/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 7c0c08e8056232fa7c60b20faf48b0137a19bc5f
ms.sourcegitcommit: f9909731ff5b6b69cdc58e9abf2025b7dee0e536
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77496411"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Power BI でのビジュアルのドリル モード

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

この記事では、Microsoft Power BI サービスでビジュアルをドリルダウンする方法について説明します。 データ ポイントでドリルダウンとドリルアップを使用すると、データに関する詳細を深く掘り下げて調べることができます。 

## <a name="drill-requires-a-hierarchy"></a>ドリルには階層が必要

ビジュアルに階層がある場合は、ドリルダウンしてさらに詳細な情報を表示できます。 たとえば、分野、競技、種目で構成された階層でオリンピック メダル数を表示するビジュアルがあるとします。 既定では、ビジュアルには分野 (体操、スキー、水泳など) 別にメダル数が表示されます。 しかし、このビジュアルは階層構造になっているので、いずれかのビジュアル要素 (棒、線、バブルなど) を選ぶと、さらに詳細な図が表示されます。 **水泳**要素を選ぶと、競泳、飛び込み、水球のデータが表示されます。  **飛び込み**要素を選ぶと、飛び板飛び込み、高飛び込み、シンクロナイズド ダイビングの各種目に関する詳細が表示されます。

日付は、他とは違う種類の階層です。  多くの場合、レポート デザイナーは日付階層をビジュアルに追加します。 一般的な日付階層には、年、四半期、月、および日が含まれます。 

## <a name="figure-out-which-visuals-can-be-drilled"></a>ドリルできるビジュアルを確認する
どの Power BI ビジュアルに階層が含まれるかわからない場合は、 ビジュアルをポイントします。 これらのドリル コントロールの組み合わせが上部に表示される場合、ビジュアルには階層があります。

![ドリル アイコンのスクリーンショット。](./media/end-user-drill/power-bi-drill-icons.png)  


## <a name="learn-how-to-drill-down-and-up"></a>ドリルダウンおよびドリルアップの方法

この例では、販売区域、都市、郵便番号、店舗名で構成される階層構造を持つツリーマップを使用します。 ツリーマップをドリルする前に、今年販売された合計ユニット数を販売区域別に調べます。 

![ツリーマップとそのフィルターのスクリーンショット。](./media/end-user-drill/power-bi-treemaps.png)  


### <a name="two-ways-to-access-the-drill-features"></a>ドリル機能を使用する 2 つの方法

階層を持つビジュアルのドリルダウン、ドリルアップ、展開の機能にアクセスするには 2 つの方法があります。 両方を試して、最も気に入ったものを選んでください。

- 最初の方法: ビジュアルをポイントし、アイコンを表示して使用します。  

    ![ポイントの例のスクリーンショット。](./media/end-user-drill/power-bi-hover.png)

- 2 番目の方法: ビジュアルを右クリックし、メニューを表示して使用します。

    ![右クリックの例のスクリーンショット。](./media/end-user-drill/power-bi-drill-menu.png)



## <a name="drill-pathways"></a>ドリルの経路

### <a name="drill-down-all-fields-at-once"></a>すべてのフィールドを一度にドリルダウンする
![ドリルダウン アイコン](./media/end-user-drill/power-bi-drill-icon3.png)

ビジュアルをドリルするには複数の方法があります。 ドリルダウン アイコンを選択すると、階層内の次のレベルに移動します。 ケンタッキー州とテネシー州の**販売区域**レベルを調べている場合、両方の州の都市レベルをドリルダウンした後、両方の州の郵便番号レベルをドリルダウンし、最後に両方の州の店舗名レベルをドリルダウンできます。 パスの各ステップでは、新しい情報が表示されます。

![ドリルの経路を示す図](./media/end-user-drill/power-bi-drill-path.png)

[販売区域別の今年の合計ユニット数] に戻るまで ![ドリルアップ アイコン](./media/end-user-drill/power-bi-drill-icon5.png) ドリルアップ アイコンを選択します。

### <a name="expand-all-fields-at-once"></a>すべてのフィールドを一度に展開する
![展開アイコン](./media/end-user-drill/power-bi-drill-icon6.png)

"**展開**" は、現在のビューに新しい階層レベルを追加します。 したがって、**Territory** レベルを表示している場合は、展開して都市、郵便番号、名前の詳細をツリーマップに追加できます。 パスの各ステップでは、前のレベルと同じ情報に、次のレベルの新しい情報が追加されます。

![展開の経路を示す図](./media/end-user-drill/power-bi-expand-path.png)

一度に 1 つのフィールドをドリルダウンまたは展開することを選択することもできます。


### <a name="drill-down-one-field-at-a-time"></a>一度に 1 つのフィールドをドリルダウンする


1. ドリルダウン アイコンを選択して、オンにします ![ドリルダウンの "オン/オフ" をオンにしたアイコンのスクリーンショット。](./media/end-user-drill/power-bi-drill-icon2.png).

    ビジュアル要素を選択することで**一度に 1 つのフィールド**をドリルダウンするオプションを使用できるようになりました。 ビジュアル要素 (横棒、バブル、リーフ) の例。

    ![ドリルダウンの "オン/オフ" をオンにしたアイコンを指し示す矢印付きのビジュアルのスクリーンショット。](media/end-user-drill/power-bi-drill-icon-selected.png)

    ドリルダウンをオンにしないと、ビジュアル要素 (横棒、バブル、リーフなど) を選択してもドリル ダウンされません。 代わりに、それによって、レポート ページ上の他のグラフがクロス フィルター処理されます。

1. **TN** のリーフを選択します。 以上で、ツリーマップに、店舗があるテネシー州のすべての都市と販売区域が表示されます。

    ![TN のみのデータを表示しているツリーマップのスクリーンショット。](media/end-user-drill/power-bi-drill-down-one.png)

1. この時点で、次のようなことができます。

    1. テネシー州のドリルダウンを続行する。

    1. テネシー州の特定の都市をドリル ダウンする。

    1. 代わりに展開する。

    一度に 1 つのフィールドのドリルダウンを続けます。  **Knoxville, TN** を選びます。 ツリーマップに Knoxville の店舗の郵便番号が表示されます。

    ![郵便番号 37919 を表示しているツリーマップのスクリーンショット。](media/end-user-drill/power-bi-drill-two.png)

    階層を上下に移動するとタイトルが変わることに注意してください。

### <a name="expand-all-and-expand-one-field-at-a-time"></a>一度に全フィールドおよび 1 フィールドを展開する

郵便番号のみが表示されるツリーマップでは役に立ちません。  そこで、階層内の 1 つ下のレベルを*展開*します。  

1. ツリーマップをアクティブにして、"*下方向に展開*" アイコン ![下方向に展開アイコンのスクリーンショット。](./media/end-user-drill/power-bi-drill-icon6.png) を選択します。 ツリーマップに、階層の 2 つのレベル (郵便番号と店舗名) が表示されます。

    ![郵便番号と店舗名を表示しているツリーマップのスクリーンショット](./media/end-user-drill/power-bi-expand-one.png)

1. テネシー州の 4 つの階層レベルすべてのデータを表示するには、ツリーマップの第 2 レベル **Territory および City による Total Units This Year** に達するまでドリルアップ矢印を選択します。

    ![TN のすべてのデータを表示しているツリーマップのスクリーンショット。](media/end-user-drill/power-bi-expand-two.png)

1. ドリルダウンがオンのままである ![ドリルダウンの "オン/オフ" をオンにしたアイコンのスクリーンショット。](./media/end-user-drill/power-bi-drill-icon2.png) ことを確認し、 "*下方向に展開*" アイコン ![下方向に展開アイコンのスクリーンショット。](./media/end-user-drill/power-bi-drill-icon6.png) を選択します。 以上で、ツリーマップに、同数のリーフ (ボックス) が表示されますが、各リーフには追加の詳細が含まれます。 都市と州だけでなく、郵便番号も表示されるようになります。

    ![都市、州、郵便番号を表示しているビジュアルのスクリーンショット。](./media/end-user-drill/power-bi-expand-three.png)

1. "*下方向に展開*" アイコンをもう一度選択し、ツリーマップのテネシー州に対する 4 つの階層レベルすべての詳細を表示します。 リーフをポイントするとさらに多くの詳細が表示されます。

    ![リーフに固有のデータを含むヒントを表示しているツリーマップのスクリーンショット。](./media/end-user-drill/power-bi-expand-all.png)

## <a name="show-the-data-as-you-drill"></a>データをドリルしながら表示する
**[データの表示]** を使用してバックグラウンドの処理を確認します。 ドリルまたは展開するたびに、 **[データの表示]** によって、ビジュアルの構築に使用されるデータが表示されます。 これは、階層、ドリル、展開が連携してビジュアルを構築するしくみを理解するのに役立ちます。 

右上隅で**その他のオプション** (...) を選択し、 **[データの表示]** を選択します。 

![省略記号メニューのスクリーンショット。](./media/end-user-drill/power-bi-ellipses.png)

次の表は、販売区域から店舗名まで一度にすべてのフィールドをドリルダウンした結果を示しています。  


![4 つのレベルすべてのドリルダウンのデータを示すスクリーンショット。](./media/end-user-drill/power-bi-show-data.png)

**都市**、**郵便番号**、**名前**の合計が同じであることに注意してください。 常にそうであるとは限りません。  しかし、このデータの場合は、各郵便番号および各都市の店舗は 1 つのみです。  



## <a name="considerations-and-limitations"></a>考慮事項と制限事項
- 既定では、ドリルによってレポートの他のビジュアルはフィルター処理されません。 ただし、レポート デザイナーは、この既定の動作を変更できます。 ドリルしながら、ページの他のビジュアルがクロスフィルター処理またはクロス強調表示されるかどうかを確認します。

- 共有してもらったレポートを表示するには、Power BI Pro または Premium ライセンスが必要です。 [お使いのライセンスの種類について](end-user-license.md)


## <a name="next-steps"></a>次の手順

[Power BI レポートのビジュアル](../visuals/power-bi-report-visualizations.md)

[Power BI レポート](end-user-reports.md)

[Power BI - 基本的な概念](end-user-basic-concepts.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
