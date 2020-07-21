---
title: Power BI Desktop から Web ページに接続する
description: Power BI Desktop で Web ページのデータに簡単に接続して使用する
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 618e2acb415d72870fd599142775720955e8ba88
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214724"
---
# <a name="connect-to-webpages-from-power-bi-desktop"></a>Power BI Desktop から Web ページに接続する

Web ページに接続し、そのデータを Power BI Desktop にインポートして、ご自分のビジュアルやご自分のデータ モデルで使用できます。

Power BI Desktop で、 **[ホーム]** リボンから **[データの取得]、[Web]** の順に選択します。

![[Web] の選択を示す、Power BI Desktop のスクリーンショット。](media/desktop-connect-to-web/connect-to-web_1.png)

ダイアログが表示され、データをインポートする Web ページの URL の指定を要求されます。

![[URL] フィールドを示す、[Web] ダイアログのスクリーンショット。](media/desktop-connect-to-web/connect-to-web_2.png)

URL を入力するか貼り付けて、 **[OK]** をクリックします。 Power BI Desktop はそのページに接続し、ページで利用可能なデータを **[ナビゲーター]** ウィンドウに表示します。 ページ全体のテーブルなど、利用可能なデータ要素の 1 つを選択すると、 **[ナビゲーター]** ウィンドウの右側にデータのプレビューが表示されます。

![選択されたテーブルのデータのプレビューを示す、[ナビゲーター] ダイアログのスクリーンショット。](media/desktop-connect-to-web/connect-to-web_3.png)

Power BI Desktop にデータをインポートする前に、 **[編集]** ボタンを選択して **[クエリ エディター]** を起動し、その Web ページのデータを調整および変換できます。 または、 **[読み込み]** ボタンを選択して、左側のウィンドウで選択したすべてのデータ要素をインポートできます。

**[読み込み]** を選択すると、選択した項目がインポートされて、Power BI Desktop の [レポート] ビューの右側の **[フィールド]** ウィンドウで使用できるようになります。

![選択されたテーブルの一覧を示す、[フィールド] ペインのスクリーンショット。](media/desktop-connect-to-web/connect-to-web_4.png)

Web ページへの接続と Power BI Desktop へのデータの取り込みは以上です。

この後は、これらのフィールドをレポート キャンバスにドラッグして、必要なすべての表示を作成できます。 他のデータと同じように Web ページのデータを使用することもできます。データを調整したり、データとモデルの他のデータ ソースとの間にリレーションシップを作成したり、必要な Power BI レポートを作成するための処理を行ったりできます。

Web ページへの接続の詳細については、「[Power BI Desktop 概要ガイド](../fundamentals/desktop-getting-started.md)」を参照してください。

## <a name="next-steps"></a>次の手順
Power BI Desktop を使用して接続できるデータの種類は他にもあります。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop のデータ ソース](desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop で Excel ブックに接続する](desktop-connect-excel.md)   
* [Power BI Desktop で CSV ファイルに接続する](desktop-connect-csv.md)   
* [Power BI Desktop にデータを直接入力する](desktop-enter-data-directly-into-desktop.md)   
