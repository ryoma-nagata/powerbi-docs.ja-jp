---
title: 'クイック スタート: データに接続する'
description: Power BI Desktop でデータ ソースに接続する
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: 1366a5281a36293a484f08c12ab9f8891e29123d
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "73876205"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>クイック スタート: Power BI Desktop におけるデータへの接続

このクイック スタートでは、**Power BI Desktop** を使用してデータに接続します。これは、データ モデルの作成とレポートの作成における最初の手順です。

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Power BI にサインアップしていない場合は、[無料の試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)してください。

## <a name="prerequisites"></a>前提条件

この記事の手順を完了するには、以下が必要です。
* **Power BI Desktop** をダウンロードしてインストールします。このアプリケーションは無料であり、ローカル コンピューター上で動作します。 [**Power BI Desktop**](https://powerbi.microsoft.com/desktop) を直接ダウンロードするか、[**Microsoft ストア**](https://aka.ms/pbidesktopstore)から入手することができます。
* [このサンプル Excel ブックをダウンロード](https://go.microsoft.com/fwlink/?LinkID=521962)し、この Excel ファイルを保存できる *C:\PBID-qs* という名前のフォルダーを作成します。 このクイックスタートの以降の手順では、それがダウンロード済みの Excel ブックのファイルの場所であることを前提とします。

## <a name="launch-power-bi-desktop"></a>Power BI Desktop を起動する

**Power BI Desktop** をインストールしたら、アプリケーションを起動してローカル コンピューターで実行されるようにします。 Power BI チュートリアルが表示されます。 チュートリアルに従うか、クリックしてスキップし、空白のキャンバスから始めます。ここで接続先のデータからビジュアルとレポートを作成します。 

![Power BI Desktop - 空白のキャンバス](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>データに接続する

**Power BI Desktop** では、多数の異なる種類のデータに接続できます。 Microsoft Excel ファイルなどの基本的なデータ ソースに接続でき、あらゆる種類のデータが含まれている Salesforce、Microsoft Dynamics、Azure Blob Storage などのオンライン サービスにも接続できます。

データに接続するには、 **[ホーム]** リボンの **[データの取得]** を選択します。

![データを取得](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

**[データの取得]** ウィンドウが表示され、**Power BI Desktop** が接続できる多数の異なるデータ ソースから選択できます。 このクイックスタートでは、この記事の始めの「*前提条件*」セクションで説明したダウンロード済みの Excel ブックを使用します。

![データを取得](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

これは Excel ファイルであるため、 **[データの取得]** ウィンドウで **[Excel]** を選択し、 **[接続]** ボタンを選択します。

接続する Excel ファイルの場所を指定することを求められます。 ダウンロード済みのファイルは "*Financial Sample*" という名前であるため、そのファイルを選択し、 **[開く]** を選択します。

![データを取得](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

**Power BI Desktop** によってブックが読み込まれ、その内容が読み取られ、ファイル内の使用可能なデータが **[ナビゲーター]** ウィンドウに表示されます。このウィンドウで、Power BI Desktop に読み込むデータを選択できます。 各テーブルの横にあるチェックボックスをオンにすることで、インポートするテーブルを選択します。 ここでは、使用可能なテーブルを両方インポートします。

![データを取得](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

選択を行ったら、 **[読み込み]** を選択して Power BI Desktop にデータをインポートします。

## <a name="view-data-in-the-fields-pane"></a>[フィールド] ウィンドウにデータを表示する

テーブルが読み込まれると、 **[フィールド]** ウィンドウにデータが表示されます。 テーブル名の横にある三角形を選択することで、各テーブルを展開できます。 次の図では、*financials* テーブルが展開され、各フィールドが表示されています。 

![データを取得](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

これで完了です。 **Power BI Desktop** でデータに接続し、そのデータを読み込んで、それらのテーブル内のすべての利用可能なフィールドを表示しました。

## <a name="next-steps"></a>次の手順

データに接続したら、ビジュアルとレポートの作成などのさまざまな操作を **Power BI Desktop** で行うことができます。 操作を開始するには、次のリソースを参照してください。

* [Power BI Desktop のファースト ステップ ガイド](desktop-getting-started.md)
