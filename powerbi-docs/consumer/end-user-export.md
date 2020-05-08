---
title: Power BI ビジュアルからデータをエクスポートする
description: レポートのビジュアルとダッシュボードのビジュアルからデータをエクスポートし、Excel でそれを表示します。
author: mihart
ms.reviewer: cmfinlan
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/20/2020
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 811eaa9769a099122597d7132de80cbc2d22a51b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "79040151"
---
# <a name="export-data-from-a-visual"></a>ビジュアルからデータをエクスポートする

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

ビジュアルの作成に使用されているデータを確認したい場合は、[Power BI でそのデータを表示する](end-user-show-data.md)か、またはそのデータを Excel にエクスポートすることができます。 データをエクスポートするオプションを使用するには、特定の種類のライセンスと、コンテンツの編集アクセス許可が必要です。 エクスポートできない場合は、Power BI 管理者に問い合わせてください。 データをエクスポートするには、ユーザー単位の Pro ライセンス、または Premium 容量ライセンスを持つ組織内のユーザー単位の Pro ライセンスのいずれかの Power BI Pro ライセンスが必要です。 通常、この種類のライセンスは、"*コンシューマー*" ではなく、レポート "*デザイナー*" が使用します。 詳細については、「[Power BI ライセンスの種類](end-user-license.md)」を参照してください。


## <a name="from-a-visual-on-a-power-bi-dashboard"></a>Power BI ダッシュボード上のビジュアルから

1. Power BI ダッシュボードから始めます。 ここでは、"***マーケティングと売上サンプル***" アプリのダッシュボードを使用しています。 [このアプリは AppSource.com からダウンロード](https://appsource.microsoft.com/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282)できます。

    ![アプリのダッシュボード](media/end-user-export/power-bi-dashboards.png)

2. ビジュアルをポイントすると、**その他のオプション** (...) が表示され、クリックするとアクション メニューが表示されます。

    ![省略記号を選択したときに表示されるメニュー](media/end-user-export/power-bi-options-menu.png)

3. **[.csv にエクスポート]** を選択します。

4. 次に行われることは、使用しているブラウザーによって異なります。 ファイルを保存するように求められるか、またはブラウザーの下部にエクスポートされたファイルへのリンクが表示される場合があります。 

    ![エクスポートされたファイルへのリンクが示されている Chrome ブラウザー](media/end-user-export/power-bi-dashboard-exports.png)

5. Excel でファイルを開きます。 

    > [!NOTE]
    > データへのアクセス許可を持っていない場合は、エクスポートすることも Excel で開くこともできません。  

    ![Excel での Total Units YTD](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>レポート内のビジュアルから
レポート内のビジュアルから、.csv または .xlsx (Excel) 形式として、データをエクスポートできます。 

1. ダッシュボードでタイルを選択して、基になっているレポートを開きます。  この例では、上と同じビジュアル *Total Units YTD Var %* を選択しています。 

    ![強調表示されたダッシュボードのタイル](media/end-user-export/power-bi-export-reports.png)

    このタイルは "*売上とマーケティング サンプル*" のレポートから作成されたものであるため、そのレポートが開きます。 また、選択したタイル ビジュアルが含まれるページが開きます。 

2. レポートで、ビジュアルを選択します。 右側の **[フィルター]** ウィンドウに注意してください。 このビジュアルにはフィルターが適用されています。 フィルターの詳細については、[レポートでのフィルターの使用](end-user-report-filter.md)に関する記事を参照してください。

    ![選択された [フィルター] ウィンドウ](media/end-user-export/power-bi-export-filter.png)


3. 視覚エフェクトの右上隅にある **[その他のオプション] (...)** を選択します。 **[データのエクスポート]** を選択します。

    ![ドロップダウンから選択したデータをエクスポートする](media/end-user-export/power-bi-export-report.png)

4. 概要データまたは基になるデータをエクスポートするオプションが表示されます。 "*売上およびマーケティング サンプル*" アプリを使用している場合、 **[基になるデータ]** は無効になります。 ただし、両方のオプションが有効になるレポートもあります。 ここでは、その違いについて説明します。

    **[概要データ]** : 現在ビジュアルで表示されている内容のデータをエクスポートする場合、このオプションを選択します。  この種類のエクスポートでは、ビジュアルの現在の状態を作成するのに使用されたデータのみが表示されます。 ビジュアルにフィルターが適用されている場合は、エクスポートしたデータもフィルター処理されています。 たとえば、このビジュアルの場合、エクスポートには 2014 年と中央地域のみのデータ、そして次の 4 つの製造元のデータのみが含まれます: VanArsdel、Natura、Aliqui、Pirum。 ご利用のビジュアルに集計 (合計、平均など) がある場合は、エクスポートも集計されます。 
  

    **[基になるデータ]** : ビジュアルに表示されているデータに**加えて**、基になるデータセットからの追加データをエクスポートする場合は、このオプションを選択します。  これには、データセットには含まれているものの、ビジュアルでは使用されていないデータが、含まれる場合があります。 ビジュアルにフィルターが適用されている場合は、エクスポートしたデータもフィルター処理されています。  ご利用のビジュアルに集計 (合計、平均など) がある場合、エクスポートでは集計が削除されます。基本的にデータは平坦化されます。 

    ![基になるデータまたは概要データを選択するメニュー](media/end-user-export/power-bi-export-underlying.png)

5. 次に行われることは、使用しているブラウザーによって異なります。 ファイルを保存するように求められるか、またはブラウザーの下部にエクスポートされたファイルへのリンクが表示される場合があります。 

    ![Microsoft Edge ブラウザーで表示されているエクスポートされたファイル](media/end-user-export/power-bi-export-edge-browser.png)

    > [!NOTE]
    > データへのアクセス許可を持っていない場合は、エクスポートすることも Excel で開くこともできません。  


6. Excel でファイルを開きます。 エクスポートされたデータの量を、ダッシュボードの同じビジュアルからエクスポートしたデータと比べてください。 違うのは、このエクスポートには**基になるデータ**が含まれているためです。 

    ![Excel のサンプル](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>次の手順

[視覚化の作成に使用されたデータを表示する](end-user-show-data.md)