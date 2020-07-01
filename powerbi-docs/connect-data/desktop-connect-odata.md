---
title: Power BI Desktop で OData フィードに接続する
description: Power BI Desktop で OData フィードに簡単に接続して使用します
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: edbea68fac44811469e0f6f90d68028eeb35be71
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85224383"
---
# <a name="connect-to-odata-feeds-in-power-bi-desktop"></a>Power BI Desktop で OData フィードに接続する
Power BI Desktop では、**OData フィード**に接続し、Power BI Desktop の他のデータ ソースと同じように基になっているデータを使用できます。

OData フィードに接続するには、Power BI Desktop の **[ホーム]** リボンから **[データの取得]、[OData フィード]** の順に選択します。

![](media/desktop-connect-odata/connect-to-odata_1.png)

**[OData フィード]** ウィンドウが表示されたら、ボックスに OData フィードの URL を入力するか貼り付けて、 **[OK]** を選択します。

![](media/desktop-connect-odata/connect-to-odata_2.png)

Power BI Desktop は OData フィードに接続し、使用可能なテーブルと他のデータ要素を **[ナビゲーター]** ウィンドウに表示します。 要素を選択すると、 **[ナビゲーター]** ウィンドウの右側のペインにデータのプレビューが表示されます。 任意の数のテーブルを選択してインポートできます。 **[ナビゲーター]** ウィンドウに、現在選択されているテーブルのプレビューが表示されます。

![](media/desktop-connect-odata/connect-to-odata_3.png)

Power BI Desktop にデータをインポートする前に、 **[編集]** ボタンを選択して **[クエリ エディター]** を起動し、OData フィードからのデータを調整および変換できます。 または、 **[読み込み]** ボタンを選択して、左側のウィンドウで選択したすべてのデータ要素をインポートできます。

**[読み込み]** を選択すると、選択した項目がインポートされて、 **[読み込み]** ウィンドウにインポートの進行状況が表示されます。

![](media/desktop-connect-odata/connect-to-odata_4.png)

完了すると、Power BI Desktop の **[レポート]** ビューの右側の *[フィールド]* ウィンドウで、選択したテーブルと他のデータ要素が使用できるようになります。

![](media/desktop-connect-odata/connect-to-odata_5.png)

これで完了です。

Power BI Desktop で OData フィードからインポートしたデータを使用して、表示やレポートを作成したり、他の Excel ブック、データベース、他のデータ ソースなどの他のデータに接続してインポートしたりできます。

## <a name="next-steps"></a>次のステップ
Power BI Desktop を使用して接続できるデータの種類は他にもあります。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop のデータ ソース](desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop で Excel ブックに接続する](desktop-connect-excel.md)   
* [Power BI Desktop にデータを直接入力する](desktop-enter-data-directly-into-desktop.md)   
