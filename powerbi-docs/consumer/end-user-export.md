---
title: Power BI ビジュアルからデータをエクスポートする
description: レポートのビジュアルとダッシュボードのビジュアルからデータをエクスポートし、Excel でそれを表示します。
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: mihart
LocalizationGroup: Consumers
ms.openlocfilehash: 3ab3b7a96fb629b303263b1ccf5c2f31603300b4
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71073145"
---
# <a name="export-data-from-a-visual"></a>ビジュアルからデータをエクスポートする
ビジュアルの作成に使用されているデータを確認したい場合は、[Power BI でそのデータを表示する](end-user-show-data.md)か、またはそのデータを Excel にエクスポートすることができます。 データをエクスポートするオプションを使用するには、特定の種類のライセンスと、コンテンツの編集アクセス許可が必要です。 エクスポートできない場合は、Power BI 管理者に問い合わせてください。 

## <a name="from-a-visual-on-a-power-bi-dashboard"></a>Power BI ダッシュボード上のビジュアルから

1. Power BI ダッシュボードから始めます。 ここでは、"***マーケティングと売上サンプル***" アプリのダッシュボードを使用しています。 [このアプリは AppSource.com からダウンロード](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample-preview?flightCodes=e2b06c7a-a438-4d99-9eb6-4324ce87f282)できます。

    ![アプリのダッシュボード](media/end-user-export/power-bi-dashboards.png)

2. ビジュアルをポイントすると省略記号 [...] が表示され、クリックするとアクション メニューが表示されます。

    ![省略記号を選択したときに表示されるメニュー](media/end-user-export/power-bi-action-menu.png)

3. **[Excel にエクスポート]** を選択します。

4. 次に行われることは、使用しているブラウザーによって異なります。 ファイルを保存するように求められるか、またはブラウザーの下部にエクスポートされたファイルへのリンクが表示される場合があります。 

    ![エクスポートされたファイルへのリンクが示されている Chrome ブラウザー](media/end-user-export/power-bi-dashboard-exports.png)

5. Excel でファイルを開きます。  

    ![Excel での Total Units YTD](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>レポート内のビジュアルから
レポート内のビジュアルから、.csv または .xlsx (Excel) 形式として、データをエクスポートできます。 

1. ダッシュボードでタイルを選択して、基になっているレポートを開きます。  この例では、上と同じビジュアル *Total Units YTD Var %* を選択しています。 

    ![強調表示されたダッシュボードのタイル](media/end-user-export/power-bi-export-reports.png)

    このタイルは "*売上とマーケティング サンプル*" のレポートから作成されたものであるため、そのレポートが開きます。 また、選択したタイル ビジュアルが含まれるページが開きます。 

2. レポートでタイルを選択します。 右側の **[フィルター]** ウィンドウに注意してください。 このビジュアルにはフィルターが適用されています。 フィルターの詳細については、[レポートでのフィルターの使用](end-user-report-filter.md)に関する記事を参照してください。

    ![選択された [フィルター] ウィンドウ](media/end-user-export/power-bi-export-filter.png)


3. ビジュアルの右上隅にある省略記号を選択します。 **[データのエクスポート]** を選択します。

    ![ドロップダウンから選択したデータをエクスポートする](media/end-user-export/power-bi-export-report.png)

4. 概要データまたは基になるデータをエクスポートするオプションが表示されます。 "*売上およびマーケティング サンプル*" アプリを使用している場合、 **[基になるデータ]** は無効になります。 ただし、両方のオプションが有効になるレポートもあります。 ここでは、その違いについて説明します。

    **[概要データ]** : ビジュアルで表示されている内容のデータをエクスポートする場合、このオプションを選択します。  この種類のエクスポートでは、ビジュアルの作成に使用されたデータのみが表示されます。 ビジュアルにフィルターが適用されている場合は、エクスポートしたデータもフィルター処理されています。 たとえば、このビジュアルの場合、エクスポートには 2014 年と中央地域のみのデータ、そして次の 4 つの製造元のデータのみが含まれます: VanArsdel、Natura、Aliqui、Pirum。
  

    **[基になるデータ]** : ビジュアルに表示されているデータに**加えて**、基になるデータセットからの追加データをエクスポートする場合は、このオプションを選択します。  これには、データセットには含まれているものの、ビジュアルでは使用されていないデータが、含まれる場合があります。 

    ![基になるデータまたは概要データを選択するメニュー](media/end-user-export/power-bi-export-option.png)

5. 次に行われることは、使用しているブラウザーによって異なります。 ファイルを保存するように求められるか、またはブラウザーの下部にエクスポートされたファイルへのリンクが表示される場合があります。 

    ![Microsoft Edge ブラウザーで表示されているエクスポートされたファイル](media/end-user-export/power-bi-export-edge-browser.png)


6. Excel でファイルを開きます。 エクスポートされたデータの量を、ダッシュボードの同じビジュアルからエクスポートしたデータと比べてください。 違うのは、このエクスポートには**基になるデータ**が含まれているためです。 

    ![Excel のサンプル](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>次の手順

[視覚化の作成に使用されたデータを表示する](end-user-show-data.md)