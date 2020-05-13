---
title: Power BI サービスで Excel ブックから魅力的なレポートを作成する
description: この記事では、Excel ブックから魅力的なレポートをすばやく作成する方法について説明します。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Data from files
ms.openlocfilehash: 9758f706b90f74c7c7f9d1feff2b00516e6c324c
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347495"
---
# <a name="from-excel-workbook-to-stunning-report-in-the-power-bi-service"></a>Power BI サービスで Excel ブックから魅力的なレポートを作成する
最新の売上データを直前のキャンペーンの感触と組み合わせて、上司にレポートを今日中に提出しなければなりません。 しかし、最新のデータはさまざまなサードパーティ システムと、自分のノート PC 内のファイルに散在しています。 以前なら、ビジュアルとレポート書式を作成するのに何時間もかかって、次第に不安になったことでしょう。

ご心配なく。 Power BI では、すぐに魅力的なレポートを作成できます。

この例では、ローカル システムから Excel ファイルをアップロードし、レポートを新規に作成して同僚と共有します。このすべてを Power BI 内から実行できます。

## <a name="prepare-your-data"></a>データの準備
例として、単純な Excel ファイルを見てみましょう。 

1. Power BI に Excel ファイルを読み込む前に、データをフラット テーブルに整理する必要があります。 フラット テーブルでは、各列に同じデータ型 (テキスト、日付、数値、通貨など) が含まれます。 テーブルにはヘッダー行が必要ですが、合計を表示する列や行は必要ありません。

   ![Excel で整理されたデータ](media/service-from-excel-to-stunning-report/pbi_excel_file.png)

2. 次に、データをテーブルとして書式設定します。 Excel で **[ホーム]** タブの **[スタイル]** グループから **[テーブルとして書式設定]** を選択します。 

3. ワークシートに適用するテーブルのスタイルを選んでください。 

   これで、Excel ワークシートを Power BI に読み込む準備ができました。

   ![テーブルとして書式設定されたデータ](media/service-from-excel-to-stunning-report/pbi_excel_table.png)

## <a name="upload-your-excel-file-to-the-power-bi-service"></a>Excel ファイルを Power BI サービスにアップロードする
Power BI サービスは、多くのデータ ソースに接続できます。自分のコンピューターで使用中の Excel ファイルもそれに含まれます。 

 > [!NOTE] 
 > このチュートリアルの残りの部分の作業を進めるには、[財務サンプル ブック](../create-reports/sample-financial-download.md)を使用します。

1. 作業を始めるには、まず Power BI サービスにサインインします。 まだサインアップしていない場合は、[無料で登録できます](https://powerbi.com)。

2. ここでは、ダッシュボードを新しく作成することにします。 **[マイ ワークスペース]** を開き、 **[作成]** アイコンを選択します。

   ![[作成] アイコン](media/service-from-excel-to-stunning-report/power-bi-new-dash.png)

3. **[ダッシュボード]** を選択し、名前を入力し、 **[作成]** を選択します。 

   データのない新しいダッシュボードが表示されます。

   ![[作成] ドロップダウン](media/service-from-excel-to-stunning-report/power-bi-create-dash.png)

4. ナビ ペインの下部にある **[データの取得]** を選択します。 

5. **[データの取得]** ページの **[新しいコンテンツの作成]** の **[ファイル]** ボックスで、 **[取得]** を選択します。

   ![ファイルからデータを取得](media/service-from-excel-to-stunning-report/pbi_get_files.png)

6. **[ファイル]** ページで、 **[ローカル ファイル]** を選択します。 ご使用のコンピューターで Excel ブック ファイルに移動し、 **[開く]** を選択して Power BI サービスに読み込みます。 

   ![[データの取得] > [ファイル] ウィンドウ](media/service-from-excel-to-stunning-report/pbi_local_file.png)

7. **[ローカル ファイル]** ページで、 **[インポート]** を選択します。


## <a name="build-your-report"></a>レポートの構築
Power BI サービスに Excel ファイルがインポートされたら、レポートの作成を開始できます。 

1. "**データセットの準備ができました**" というメッセージが表示されたら、 **[データセットの表示]** を選択します。  

   Power BI が編集ビューで開き、レポート キャンバスが表示されます。 右側には、 **[視覚化]** 、 **[フィルター]** 、 **[フィールド]** の各ウィンドウがあります。 **[フィールド]** ウィンドウに Excel ブックのテーブルのデータが表示されていることに注意してください。 テーブルの名前の下には、Power BI によって、列見出しが個別のフィールドとして一覧表示されます。

   ![[フィールド] ウィンドウでの Excel データの表示](media/service-from-excel-to-stunning-report/pbi_report_fields.png)

2. これで、視覚化の作成を開始できるようになりました。 上司が確認したいのは、時間の経過に伴う利益の推移です。 **[フィールド]** ウィンドウから **[Profit]** をレポート キャンバスまでドラッグします。 

   Power BI により、既定の横棒グラフが表示されます。 

3. **[Date]** をレポート キャンバスまでドラッグします。 

   Power BI により、日付ごとに利益を表示する棒グラフに更新されます。

   ![レポート エディターでの縦棒グラフ](media/service-from-excel-to-stunning-report/pbi_report_pin-new.png)

   > [!TIP]
   > グラフが予測したようにならない場合は、集計を確認します。 たとえば、 **[値]** で、追加したフィールドを右クリックし、データの集計方法が希望どおりであることを確認します。 この例では、 **[合計]** を使用しています。
   > 

また、上司は、利益が大きいのはどの国かについて知りたいと考えています。 気に入ってもらうため、マップの視覚エフェクトを使うことにします。 

1. レポート キャンバスの空白領域を選択します。 

2. **[フィールド]** ウィンドウから **[Country]** フィールドと **[Profit]** フィールドをレポート キャンバスにドラッグします。

   Power BI によって、各場所の相対的な利益を表すバブルの表示された地図ビジュアルが作成されます。

   ![レポート エディターでのマップ ビジュアル](media/service-from-excel-to-stunning-report/pbi_report_map-new.png)

製品ごとに市場セグメントごとの売上を示したビジュアルを表示するにはどうしたらよいでしょうか? 簡単です。 

1. **[フィールド]** ウィンドウで、 **[Sales]** 、 **[Product]** 、 **[Segment]** の各フィールドを選択します。 
   
   Power BI によってすぐに棒グラフが作成されます。 

2. **[視覚化]** メニューで、アイコンのいずれかを選択すると、グラフの種類を変更できます。 たとえば、**積み上げ縦棒グラフ**に変更します。 

3. グラフを並べ替えるには、**その他のオプション** (...)、 **[並べ替え]** の順に選択します。

   ![レポート エディターでの積み上げ縦棒グラフ](media/service-from-excel-to-stunning-report/pbi_barchart-new.png)

すべてのビジュアルをダッシュボードにピン留めします。 これで、仕事仲間とダッシュボードを共有する準備ができました。

   ![3 つのビジュアルがピン留めされたダッシュボード](media/service-from-excel-to-stunning-report/pbi_report.png)

## <a name="share-your-dashboard"></a>ダッシュボードを共有する
作成したダッシュボードを上司と共有することにします。 ダッシュボードと基になるレポートは、Power BI アカウントを持つ仕事仲間と共有できます。 仕事仲間はレポートを操作できますが、変更は変更できません。

1. レポートを共有するには、ダッシュボードの上部にある **[共有]** を選択します。

   ![[共有] アイコン](media/service-from-excel-to-stunning-report/power-bi-share.png)

   Power BI に、 **[ダッシュボードの共有]** ページが表示されます。 

2. **[メール アドレスを入力してください]** ボックスに受信者のメール アドレスを入力し、その下のボックスにメッセージを追加します。 

3. 受信者がこのダッシュボードを他のユーザーと共有できるようにするため、 **[受信者がダッシュボードを共有できるようにする]** を選びます。 **[共有]** を選択します。

   ![[ダッシュボードの共有] ウィンドウ](media/service-from-excel-to-stunning-report/power-bi-share-dash-new.png)

## <a name="next-steps"></a>次のステップ

* [Power BI サービスの概要](../fundamentals/service-get-started.md)
* [Power BI Desktop の概要](../fundamentals/desktop-getting-started.md)
* [Power BI サービスのデザイナー向けの基本的な概念](../fundamentals/service-basic-concepts.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
