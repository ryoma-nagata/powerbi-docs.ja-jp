---
title: チュートリアル:Power BI で機械学習モデルを構築する (プレビュー)
description: このチュートリアルでは、Power BI で Machine Learning モデルを構築します。
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61407202"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>チュートリアル:Power BI で機械学習モデルを構築する (プレビュー)

このチュートリアルの記事では、**自動機械学習**を使用して、Power BI でバイナリの予測モデルを作成して適用します。 このチュートリアルには、Power BI データフローを作成し、データフローで定義されているエンティティを使用して機械学習モデルを Power BI で直接トレーニングおよび検証するためのガイダンスが含まれています。 また、そのモデルを使用して、予測を生成します。

まず、バイナリの予測機械学習モデルを作成して、オンライン セッション属性のセットに基づいてオンラインの買い物客の購入意図を予測します。 この演習には、ベンチマーク機械学習データセットが使用されます。 モデルのトレーニングが完了すると、モデルの結果を説明する検証レポートが Power BI によって自動的に生成されます。 この検証レポートを確認し、スコア付けのためにモデルをデータに適用できます。

このチュートリアルは、次の手順で構成されています。

> [!div class="checklist"]
> * 入力データを使用してデータフローを作成する
> * 機械学習モデルの作成とトレーニング
> * モデル検証レポートを確認する
> * データフロー エンティティにモデルを適用する
> * モデルのスコア付けされた出力を Power BI レポートで使用する

## <a name="create-a-dataflow-with-the-input-data"></a>入力データを使用してデータフローを作成する

このチュートリアルの最初の部分では、入力データを使用してデータフローを作成します。 このプロセスでは、以下のセクションで示すように、データの取得を始め、いくつかの手順を実行します。

### <a name="get-data"></a>データを取得

データフローを作成する最初の手順として、データ ソースを準備します。 このケースでは、一連のオンライン セッションの機械学習データセットを使用しており、その一部は購入に至っています。 データセットにはこれらのセッションに関する一連の属性が含まれ、それをモデルのトレーニングに使用します。

データセットは、UC Irvine Web サイトからダウンロードできます。  また、このチュートリアルのために、[online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv) のリンクからこれを入手することもできます。

### <a name="create-the-entities"></a>エンティティを作成する

データフローにエンティティを作成するには、Power BI サービスにサインインし、AI プレビューが有効になっている専用容量内のワークスペースに移動します。

ワークスペースがまだない場合は、Power BI サービスの左側のナビゲーション メニューで **[ワークスペース]** を選択して作成し、表示されるパネルの下部にある **[アプリのワークスペースの作成]** を選択します。 これで、ワークスペースの詳細を入力するパネルが右側に開きます。 ワークスペース名を入力し、 **[詳細]** を選択します。 ラジオ ボタンを使用してワークスペースに [専用の容量] が使用されていること、AI プレビューが有効になっている専用の容量インスタンスに割り当てられていることを確認します。 その後、 **[保存]** を選びます。

![ワークスペースの作成](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

ワークスペースが作成されたら、次の図に示すように、ようこそ画面の右下にある **[スキップ]** を選択できます。

![ワークスペースがある場合はスキップする](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

**[データフロー (プレビュー)]** タブを選択します。ワークスペースの右上にある **[作成]** ボタンを選択し、 **[データフロー]** を選択します。

![データフローを作成する](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

**[新しいエンティティを追加]** を選択します。 これにより、ブラウザーで **Power Query** エディターが起動します。

![新しいエンティティを追加](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

次の図に示すように、データ ソースとして **[Text/CSV File]\(テキスト/CSV ファイル\)** を選択します。

![[Text/CSV File]\(テキスト/CSV ファイル\) の選択](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

次に表示される **[データ ソースへの接続]** で、 **[File path or URL]\(ファイル パスまたは URL\)** ボックスに *online_shoppers_intention.csv* への次のリンクを貼り付け、 **[次へ]** を選択します

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![ファイル パス](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

Power Query エディターに、CSV ファイル内のデータのプレビューが表示されます。 コマンド リボンの **[テーブルの変換]** を選択し、表示されるメニューから **[先頭の行を見出しとして使用]** を選択します。 これにより、 _[昇格されたヘッダー数]_ クエリ ステップが画面の右側の **[適用されたステップ]** セクションに追加されます。 右側のウィンドウにある **[名前]** ボックスの値を変更することで、クエリの名前をわかりやすい名前に変更できます。 たとえば、クエリ名を _Online Visitor_ に変更できます。

![フレンドリ名に変更する](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

このデータセットの属性データ型の一部は "_数値型_" または "_ブール型_" ですが、**Power Query** によって文字列と解釈される場合があります。 各列ヘッダーの上部にある属性の種類アイコンを選択して、以下に示す列を次の型に変更します。

* **10 進数:** Administrative_Duration、Informational_Duration、ProductRelated_Duration、BounceRates、ExitRates、PageValues、SpecialDay
* **True/False:** Weekend、Revenue

![データ型を変更する](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

トレーニングする**バイナリの予測**モデルには、過去の観察の結果を特定するラベルとしてブール型のフィールドが必要です。 このデータセットでは、_Revenue_ 属性は購入を示し、この属性は既にブール値として使用できます。 そのため、ラベルの計算列を追加する必要はありません。 他のデータセットでは、既存のラベル属性をブール型の列に変換する処理が必要になる場合があります。

**[完了]** ボタンを選択して Power Query エディターを閉じます。 これにより、追加した _Online Visitors_ データを含むエンティティの一覧が表示されます。 右上隅にある **[保存]** を選択し、データフローの名前を指定し、次の図に示すように、ダイアログの **[保存]** を選択します。

![データフローを保存する](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>データフローを更新する

データフローを保存すると、データフローが保存されたことを示す通知が表示されます。 **[今すぐ更新]** を選択し、ソースからデータフローにデータを取り込みます。

![今すぐ更新](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

右上隅にある **[閉じる]** を選択し、データフローの更新が完了するまで待ちます。

**[アクション]** コマンドを使ってデータフローを更新することもできます。 データフローには、更新が完了したときのタイムスタンプが表示されます。

![更新のタイムスタンプ](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>機械学習モデルの作成とトレーニング

更新が完了したら、データフローを選択します。 機械学習モデルを追加するには、トレーニング データとラベル情報が含まれている基本エンティティの **[アクション]** 一覧で **[ML モデルを適用します]** ボタンを選択し、 **[機械学習モデルの追加]** を選択します。

![機械学習モデルの追加](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

機械学習モデルを作成する最初の手順は、予測するラベル フィールドを含む履歴データを特定することです。 モデルは、このデータから学習することで作成されます。

使用しているデータセットのケースでは、これは **Revenue** フィールドです。 [履歴の結果フィールド] の値として **Revenue** を選択し、 **[次へ]** を選択します。

![履歴データを選択する](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

次に、作成する機械学習モデルの種類を選択する必要があります。 Power BI では、特定した履歴の結果フィールドの値が分析され、そのフィールドを予測するために作成できる機械学習モデルの種類が提案されます。

このケースでは、ユーザーが購入するかどうかの二元の結果を予測しているので、モデルの種類として **[バイナリの予測]** を選択し、[次へ] を選択します。

![[バイナリの予測] の予測](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

次に、Power BI によってデータの事前スキャンが行われ、モデルに使用できる入力が提案されます。 モデルに使用する入力フィールドをカスタマイズすることもできます。 キュレーションされたデータセットで、すべてのフィールドを選択するには、エンティティ名の横にあるチェックボックスをオンにします。 **[次へ]** を選択して入力を受け入れます。

![[次へ] チェックボックスを選択する](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

最後の手順では、モデルの名前と、モデルの検証結果を要約する、自動的に生成されるレポートで使用される結果のわかりやすいラベルを指定する必要があります。 次に、モデルに _Purchase Intent Prediction_ と名前を付け、true と false に _Purchase_ と _No-Purchase_ というラベルを付けます。 その後、 **[保存]** を選びます。

![モデルを保存する](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

これで、機械学習モデルをトレーニングする準備ができました。 **[今すぐ更新]** を選択して、モデルのトレーニングを開始します。

![今すぐ更新](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

トレーニング プロセスは、履歴データをサンプリングして正規化し、データセットを 2 つの新しいエンティティ *Purchase Intent Prediction Training Data* と *Purchase Intent Prediction Testing Data* に分割することから始まります。

データセットのサイズによっては、トレーニング プロセスに数分から数時間かかることがあります。 この時点で、データフローの **[機械学習モデル]** タブでモデルを確認できます。 _[準備完了]_ の状態は、モデルがトレーニングのためにキューに格納されているか、トレーニング中であることを示します。

![トレーニングの準備完了](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

モデルのトレーニング中は、データフローの表示または編集を実行できません。 データフローの状態によって、モデルがトレーニング中および検証中であることを確認できます。 これは、ワークスペースの **[データフロー]** タブで進行中のデータ更新と表示されます。

![処理中](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

モデルのトレーニングが完了すると、データフローに更新された更新時間が表示されます。 データフローの **[機械学習モデル]** タブに移動すると、モデルがトレーニング済みであることを確認できます。 作成したモデルには **[トレーニング済み]** と表示され、 **[最後のトレーニング]** の時刻が更新されます。

![最後のトレーニング時刻](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>モデル検証レポートを確認する

モデル検証レポートを確認するには、 **[機械学習モデル]** で、モデルの **[アクション]** 列の **[パフォーマンス レポートを表示して、モデルを適用します]** ボタンを選択します。 このレポートには、機械学習モデルがどのように実行される可能性があるかが示されます。

レポートの **[モデル パフォーマンス]** ページで、 **[主要なインフルエンサ]** を選択し、モデルの最上位の予測子を表示します。 予測子のいずれかを選択して、その予測子に関連付けられた結果の分布を確認できます。

![モデル パフォーマンス](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

[モデル パフォーマンス] ページの **[Probability Threshold]\(確率しきい値\)** スライサーを使用すると、モデルの精度とリコールに対する影響を確認できます。

![確率しきい値](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

レポートの他のページには、モデルの統計的なパフォーマンス メトリックが記載されます。

このレポートには、実行されたさまざまなイテレーション、入力からの特徴の抽出方法、および最後に使用されたモデルのハイパーパラメーターが記述された [トレーニングの詳細] ページも含まれています。

## <a name="apply-the-model-to-a-dataflow-entity"></a>データフロー エンティティにモデルを適用する

レポートの上部にある **[モデルの適用]** ボタンを選択すると、データフローの更新時にこのモデルが呼び出されます。 **[適用]** ダイアログで、モデルを適用するソース データを含むターゲット エンティティを指定できます。

![モデルを適用します](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

プロンプトが表示されたら、データフローを **[更新]** して、モデルの結果をプレビューする必要があります。

モデルを適用すると、新しいエンティティが作成され、モデルを適用したエンティティに **enriched <model_name>** というサフィックスが追加されます。 このケースでは、**OnlineShoppers** エントリにモデルを適用すると、**OnlineShoppers enriched Purchase Intent Prediction** が作成されます。これにはモデルからの予測された出力が含まれます。

バイナリの予測モデルを適用すると、予測された結果、確率スコア、および予測の上位レコード固有のインフルエンサーという 3 つの列が追加され、各列には指定した列名がプレフィックスとして付けられます。

![結果の 3 列](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

既知の問題があるため、強化されたエンティティのスコア付けされた出力列には、Power BI Desktop からのみアクセスできます。 サービスでこれらをプレビューするには、特殊なプレビュー エンティティを使用する必要があります。

データフローの更新が完了したら、**OnlineShoppers enriched Purchase Intent Prediction Preview** エンティティを選択して結果を確認できます。

![結果を表示する](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>モデルのスコア付けされた出力を Power BI レポートで使用する

機械学習モデルからのスコア付けされた出力を使用するには、データフロー コネクタを使用して、Power BI デスクトップからデータフローに接続できます。 これで、**OnlineShoppers enriched Purchase Intent Prediction** エンティティを使用して、モデルの予測を Power BI のレポートに組み込むことができるようになりました。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の手順に従って Power BI でバイナリの予測モデルを作成して適用しました。

* 入力データを使用してデータフローを作成する
* 機械学習モデルの作成とトレーニング
* モデル検証レポートを確認する
* データフロー エンティティにモデルを適用する
* モデルのスコア付けされた出力を Power BI レポートで使用する

Power BI での機械学習の自動化の詳細については、「[Power BI での自動化 された機械学習 (プレビュー)](service-machine-learning-automated.md)」を参照してください。
