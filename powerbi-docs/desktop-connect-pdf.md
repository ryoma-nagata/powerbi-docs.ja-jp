---
title: Power BI Desktop で PDF ファイルに接続する
description: Power BI Desktop で PDF ファイルからデータに簡単に接続して使用します
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 77a036cd1852c237c827dca07363492c94d8a272
ms.sourcegitcommit: c0f4d00d483121556a1646b413bab75b9f309ae9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160274"
---
# <a name="connect-to-a-pdf-file-in-power-bi-desktop"></a>Power BI Desktop で PDF ファイルに接続する
Power BI Desktop では、Power BI Desktop の他のデータ ソースと同様に、**PDF ファイル**に接続してこのファイルに含まれるデータを使用できます。

![PDF ファイルのデータへの接続](media/desktop-connect-pdf/connect-pdf-04.png)

次のセクションでは、**PDF ファイル**に接続し、データを選択して、そのデータを **Power BI Desktop** に取り込む方法について説明します。

常に、**Power BI Desktop** の最新リリースにアップグレードすることをお勧めします。これは、「[Power BI Desktop の取得](desktop-get-the-desktop.md)」内のリンクから取得できます。 

## <a name="connect-to-a-pdf-file"></a>PDF ファイルへの接続
**PDF** ファイルに接続するには、Power BI Desktop の **[ホーム]** リボンで **[データの取得]** を選択します。 左側のカテゴリから **[ファイル]** を選択すると、 **[PDF]** が表示されます。

![[データの取得] で PDF を選択する](media/desktop-connect-pdf/connect-pdf-01.png)

使用する PDF ファイルの場所を指定するよう求められます。 フィルの場所を指定し、PDF フィルが読み込まれたら、 **[ナビゲーター]** ウィンドウが開き、ファイルから使用可能なデータが表示されます。その中から 1 つまたは複数の要素を選択し、**Power BI Desktop** にインポートして使用することができます。

![PDF ファイルのデータへの接続](media/desktop-connect-pdf/connect-pdf-04.png)

PDF ファイル内の検出された要素の横にあるチェック ボックスをオンにすると、これらの要素が右側のウィンドウに表示されます。 インポートする準備ができたら、 **[読み込み]** ボタンを選択して、そのデータを **Power BI Desktop** に取り込みます。

2018 年 11 月リリース以降の **Power BI Desktop** では、PDF 接続用の省略可能なパラメーターとして、 **[開始ページ]** と **[最終ページ]** を選択できます。 また、以下の形式を使用して、M 式言語内でこれらのパラメーターを指定することもできます。

`Pdf.Tables(File.Contents("c:\sample.pdf"), [StartPage=10, EndPage=11])`


## <a name="next-steps"></a>次の手順
Power BI Desktop を使用して接続できるデータの種類は他にもあります。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](desktop-what-is-desktop.md)
* [Power BI Desktop のデータ ソース](desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop で Excel ブックに接続する](desktop-connect-excel.md)   
* [Power BI Desktop にデータを直接入力する](desktop-enter-data-directly-into-desktop.md)   

