---
title: Power BI Desktop で Adobe Analytics に接続する
description: Power BI Desktop で Adobe Analytics に簡単に接続して使用します
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: bc6b40754e12531c57dfcab2923fdf999aee5481
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85224818"
---
# <a name="connect-to-adobe-analytics-in-power-bi-desktop"></a>Power BI Desktop で Adobe Analytics に接続する 
**Power BI Desktop** では、**Adobe Analytics** に接続し、Power BI Desktop の他のデータ ソースと同じように基になっているデータを使用できます。 

![Adobe Analytics からデータを取得する](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

## <a name="connect-to-adobe-analytics-data"></a>Adobe Analytics データに接続する
**Adobe Analytics** データに接続するには、Power BI Desktop の **[ホーム]** リボンで **[データの取得]** を選択します。 左側のカテゴリで **[オンライン サービス]** を選択すると、 **[Adobe Analytics コネクタ]** が表示されます。

![Adobe Analytics からデータを取得する](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

表示される **[Adobe Analytics]** ウィンドウで、 **[サインイン]** ボタンをクリックし、Adobe Analytics アカウントへのサインイン資格情報を指定します。 次の図のように、Adobe のサインイン ウィンドウが表示されます。

![Adobe Analytics にサインインする](media/desktop-connect-adobe-analytics/connect-adobe-analytics_03.png)

プロンプトが表示されたら、ユーザー名とパスワードを入力します。 接続が確立されたら、Power BI の **[ナビゲーター]** ダイアログで複数のディメンションとメジャーをプレビューして選択し、1 つの表形式の出力を作成できます。 選択した項目に必要な入力パラメーターを指定することもできます。 

![ナビゲーターを使用してデータを選択する](media/desktop-connect-adobe-analytics/connect-adobe-analytics_04.png)

選択したテーブルを**読み込んで**、テーブル全体を **Power BI Desktop** に取り込むことができます。またはクエリを**編集**して**クエリ エディター**を開き、使用するデータのセットをフィルターし、絞り込んでから、その絞り込んだデータのセットを **Power BI Desktop** に取り込むこともできます。

![ナビゲーターでデータを読み込んで編集する](media/desktop-connect-adobe-analytics/connect-adobe-analytics_05.png)


## <a name="next-steps"></a>次のステップ
Power BI Desktop を使用して接続できるデータの種類は他にもあります。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop のデータ ソース](desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop で Excel ブックに接続する](desktop-connect-excel.md)   
* [Power BI Desktop にデータを直接入力する](desktop-enter-data-directly-into-desktop.md)   
