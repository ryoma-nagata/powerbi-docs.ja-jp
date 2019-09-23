---
title: Power BI Desktop で Google BigQuery データベースに接続する
description: Power BI Desktop で Google BigQuery に簡単に接続して使用します
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: e47dd26c6a8433777f0c4d3ef15cce41225cf03a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514666"
---
# <a name="connect-to-a-google-bigquery-database-in-power-bi-desktop"></a>Power BI Desktop で Google BigQuery データベースに接続する
Power BI Desktop では、Google **BigQuery** データベースに接続し、Power BI Desktop の他のデータ ソースの場合と同様に基になっているデータを使用できます。

## <a name="connect-to-google-bigquery"></a>Google BigQuery への接続
Google **BigQuery** データベースに接続するには、Power BI Desktop の **[ホーム]** リボンで **[データを取得]** を選択します。 左側のカテゴリから **[データベース]** を選ぶと、 **[Google BigQuery]** が表示されます。

![Google BigQuery の [データを取得] ダイアログ](media/desktop-connect-bigquery/connect_bigquery_01.png)

表示される **Google BigQuery** ウィンドウで、Google BigQuery アカウントにサインインして、 **[接続]** を選択します。

![Google BigQuery へのサインイン](media/desktop-connect-bigquery/connect_bigquery_02.png)

サインインすると、認証されたことを示す次のウィンドウが表示されます。 

![Google へのサインイン](media/desktop-connect-bigquery/connect_bigquery_02b.png)

接続が正常に行われたら、 **[ナビゲーター]** ウィンドウが開き、サーバー上で使用可能なデータが表示されます。その中から 1 つまたは複数の要素を選択し、**Power BI Desktop** にインポートして使用することができます。

![Google BigQuery からのデータ](media/desktop-connect-bigquery/connect_bigquery_03.png)

## <a name="considerations-and-limitations"></a>考慮事項と制限事項
Google **BigQuery** コネクタには、いくつかの制限事項と考慮事項があるので注意してください。

* Google BigQuery コネクタは、Power BI Desktop と Power BI サービスにあります。 Power BI サービスでは、Power BI から Google BigQuery へのクラウド間接続を使用して、コネクタにアクセスできます。

Power BI は、Google BigQuery の**請求書作成プロジェクト**で使用できます。 Power BI は既定で、ユーザに返されたリストの最初のプロジェクトを使用します。 Power BI で使用するときの請求書作成プロジェクトの動作をカスタマイズするには、次の手順に従います。

 * ソースの手順の基になる M で次のオプションを指定します。これは、Power BI Desktop で **Power Query エディター**を使用してカスタマイズできます。

    ```Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here"])```

## <a name="next-steps"></a>次の手順
Power BI Desktop を使用して接続できるデータの種類は他にもあります。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](desktop-what-is-desktop.md)
* [Power BI Desktop のデータ ソース](desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop で Excel ブックに接続する](desktop-connect-excel.md)   
* [Power BI Desktop にデータを直接入力する](desktop-enter-data-directly-into-desktop.md)   

