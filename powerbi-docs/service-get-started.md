---
title: Power BI サービスの概要
description: Power BI オンライン サービスの概要 (app.powerbi.com)
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: B2vd4MQrz4M
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 007819ead82f558efa8179a49dfba9454558dfbb
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68995202"
---
# <a name="tutorial-get-started-with-the-power-bi-service-apppowerbicom"></a>チュートリアル:Power BI サービスの概要 (app.powerbi.com)
このチュートリアルは、初めて *Power BI サービス*を使うときに役立ちます。 Power BI サービスと他の Power BI 製品の関係を理解するため、最初に「[Power BI とは?](power-bi-overview.md)」を読むことをお勧めします。

![Power BI Desktop、サービス、モバイルの間のリレーションシップ](media/service-get-started/power-bi-components.png)

このチュートリアルでは、以下の手順を実行します。

> [!div class="checklist"]
> * Power BI サービスの入門コンテンツを探します。
> * Power BI オンライン アカウントにサインインするか、まだ行っていない場合はサインアップします。
> * Power BI サービスを開きます。
> * データをいくつか取得し、それをレポート ビューで開きます。
> * そのデータを使用して視覚化を作成し、レポートとして保存します。
> * レポートからタイルをピン留めし、ダッシュボードを作成します。
> * Q&A 自然言語ツールを利用し、別の視覚化をダッシュボードに追加します。
> * データセット、レポート、ダッシュボードを削除してリソースをクリーンアップします。

## <a name="sign-up-for-the-power-bi-service"></a>Power BI サービスにサインアップする
Power BI アカウントがない場合は、始める前に[無料の Power BI Pro 試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)してください。

アカウントを作成した後、ブラウザーに「*app.powerbi.com*」と入力して Power BI サービスを開きます。 

Power BI Desktop のヘルプを探している場合は、「[Power BI Desktop の概要](desktop-getting-started.md)」をご覧ください。 Power BI モバイルについては、「[モバイル デバイス用の Power BI アプリ](consumer/mobile/mobile-apps-for-mobile-devices.md)」をご覧ください。

> [!TIP]
> 自分のペースで進められる無料のトレーニング コースを代わりに選択しますか? [EdX の Analyzing and Visualizing Data (データの分析と視覚化) コースに登録](http://aka.ms/edxpbi)してください。

[YouTube の再生リスト](https://www.youtube.com/playlist?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP)を参照してください。 使い始める場合は、次のビデオ「*Power BI サービスの概要*」が役に立ちます。
> 
> <iframe width="560" height="315" src="https://www.youtube.com/embed/B2vd4MQrz4M" frameborder="0" allowfullscreen></iframe>
> 

## <a name="what-is-the-power-bi-service"></a>Power BI サービスとは何ですか?
Microsoft Power BI サービスは、Power BI オンラインまたは app.powerbi.com とも呼ばれています。 Power BI を利用すると、自分にとって重要な事柄について常に最新情報を得ることができます。 Power BI サービスの*ダッシュボード*を使うと、ビジネスの実情を正確に把握することができます。 ダッシュボードに "*タイル*" が表示されます。それを選択すると、"*レポート*" を開いてさらに調査できます。 複数の*データ セット*に接続し、関連するすべてのデータを 1 か所にまとめます。 Power BI を構成する要素を理解するうえで助けが必要ですか? 「[Power BI サービスのデザイナー向けの基本的な概念](service-basic-concepts.md)」を参照してください。

Excel ファイルまたは CSV ファイルに重要なデータがある場合、Power BI ダッシュボードを作成し、どこにいても通知が受けられるようにし、他のユーザーと洞察を共有できるようにすることができます。  Salesforce などの SaaS アプリケーションへのサブスクリプションを使用していますか。  Salesforce に接続してそのデータから自動的にダッシュボードを作成するか、接続可能な[その他のすべての SaaS アプリケーションをチェックアウト](service-get-data.md)すると、一歩進んだスタートが切れます。 組織に属している場合は、[アプリ](service-create-distribute-apps.md)が自分に公開されているかどうかを確認します。

その他のすべての方法については、「[Power BI のデータの取得](service-get-data.md)」を参照してください。

## <a name="step-1-get-data"></a>手順 1:データの取得
CSV ファイルからデータを取得する例を次に示します。 このチュートリアルに従って作業しますか? [財務サンプル CSV ファイルのダウンロード](http://go.microsoft.com/fwlink/?LinkID=521962)

1. [Power BI にサインイン](http://www.powerbi.com/)します。 アカウントをお持ちではありませんか。 心配はご無用です。無料の試用版にご登録いただけます。
2. Power BI がブラウザーで開きます。 左ナビゲーション バーの下部にある **[データの取得]** を選択します。

    **[データの取得]** ページが開きます。   

3. **[新しいコンテンツの作成]** セクションで、 **[ファイル]** を選択します。 
   
   ![ファイルの取得](media/service-get-started/gs1.png)
4.  **[ローカル ファイル]** を選択します。
   
     ![[データの取得] > [ファイル] 画面](media/service-get-started/gs2.png)

5. コンピューター上のファイルに移動し、 **[開く]** を選びます。

5. このチュートリアルでは、 **[インポート]** を選択し、レポートおよびダッシュボードの作成に使用できるデータセットとして、Excel ファイルを追加します。 **[アップロード]** を選択した場合は、Excel ブック全体が Power BI にアップロードされるので、それを Excel Online で開いて編集できます。
   
   ![[インポート] を選択する](media/service-get-started/power-bi-import.png)
6. データセットの準備ができたら、 **[データセットの表示]** を選んでレポート エディターで開きます。 

    ![ダイアログでデータセットの準備ができる](media/service-get-started/power-bi-gs.png)

    視覚化をまだ作成していないため、レポート キャンバスは空白になっています。

    ![空のレポート キャンバス](media/service-get-started/power-bi-report-editor.png)

7. 上部のナビゲーション バーに **[読み取りビュー]** のオプションがあることに注意してください。 このオプションがあるということは、現在編集ビューになっていることを意味します。 

    ![[読み取りビュー] オプション](media/service-get-started/power-bi-editing-view.png)

    編集ビューが表示されるユーザーはレポートの "*所有者*" なのでレポートを編集できます。 つまり、ユーザーは "*作成者*" です。 同僚とレポートを共有している場合、同僚は読み取りビューでレポートを操作することだけができます。同僚は "*コンシューマー*" です。 詳しくは、[読み取りビューと編集ビュー](consumer/end-user-reading-view.md)に関するトピックをご覧ください。
    
    レポート エディターについて詳しく理解するには、[用意されているツアー](service-the-report-editor-take-a-tour.md)をご覧ください。
 

## <a name="step-2-start-exploring-your-dataset"></a>手順 2:データセットを探索する
データに接続したので、探索を開始します。  何か興味深いものを発見したときは、ダッシュボードを作成し、時間経過によってどのように変化するかを監視できます。 そのしくみを見てみましょう。
    
1. レポート エディターで、ページの右側にある **[フィールド]** ウィンドウを使って視覚エフェクトを作成します。 **Gross Sales** と **Date** のチェック ボックスをオンにします。
   
   ![フィールド一覧](media/service-get-started/fields.png)

    Power BI は、データを分析して視覚エフェクトを作成します。 最初に **Date** を選択した場合は、テーブルが表示されます。 最初に **Gross Sales** を選択した場合は、グラフが表示されます。 

2. 別のデータ表示方法に切り替えます。 このデータを折れ線グラフにしてみます。 **[視覚化]** ウィンドウで折れ線グラフ アイコンを選択します。
   
   ![折れ線グラフが選択されたレポート エディター](media/service-get-started/gettingstart5new.png)

3. 役に立ちそうなので、グラフをダッシュボードに "*ピン留め*" します。 視覚エフェクトをポイントし、ピン留めアイコンを選択します。 この視覚エフェクトをピン留めすると、最新の値がひとめでわかるようにダッシュボードに保存されて最新の様態に維持されます。
   
   ![ピン留めアイコン](media/service-get-started/pinnew.png)

4. これは新しいレポートであるため、視覚エフェクトをダッシュボードにピン留めする前に、レポートを保存するよう要求されます。 レポートに名前を付け (たとえば、"*一定期間内の売上*" など)、 **[保存してから続ける]** を選択します。 
   
   ![レポートの保存ダイアログ](media/service-get-started/pbi_getstartsaveb4pinnew.png)
   
5. 新しいダッシュボードに折れ線グラフをピン留めし、"*チュートリアルの財務サンプル*" という名前を付けます。 
   
   ![レポート名の設定](media/service-get-started/power-bi-pin.png)
   
6. **[Pin]** (ピン留め) を選択します。
   
    右上隅の近くに成功メッセージが表示されたら、視覚エフェクトがダッシュボードにタイルとして追加されたことがわかります。
   
    ![ダッシュボードにピン留めダイアログ](media/service-get-started/power-bi-pin-success.png)

7. **[ダッシュボードに移動]** を選択し、新しいダッシュボードにタイルとしてピン留めされた折れ線グラフを確認します。 視覚エフェクトのタイルをさらに追加し、[タイルの名前変更やサイズ変更、リンク、位置変更](service-dashboard-edit-tile.md)を行って、ダッシュボードの見栄えをよくします。
   
   ![視覚エフェクトがピン留めされたダッシュボード](media/service-get-started/power-bi-new-dashboard.png)
   
8. ダッシュボード上の新しいタイルを選択すると、レポートに戻ることができます。 Power BI の表示が読み取りビューのレポート エディターに戻ります。 編集ビューに戻すには、上部のナビゲーションー バーから **[レポートの編集]** を選択します。 編集ビューにした後、タイルの探索とピン留めを続けることができます。 

## <a name="step-3--continue-the-exploration-with-qa-natural-language-querying"></a>手順 3:Q&A で探索を続行する (自然言語によるクエリ)
1. データのクイック探索については、Q&A ボックスで質問してください。 Q&A の質問ボックスは、ダッシュボードの上部 ( **[データについて質問する]** ) と、レポートの上部ナビゲーション バー ( **[質問する]** ) にあります。 たとえば、「*what segment had the most revenue*」(最も収益が高いセグメントはどれですか) と Q&A ボックスに入力します。
   
   ![Q&A キャンバス](media/service-get-started/powerbi-qna.png)

2. Q&A によって回答が検索され、視覚エフェクトの形式で表示されます。 ピン留めアイコン ![ピン留めアイコン](media/service-get-started/pbi_pinicon.png) を選択して、ダッシュボードの視覚エフェクトを表示できます。
3. **チュートリアルの財務サンプル** ダッシュボードに視覚エフェクトをピン留めします。
   
    ![ダッシュボードにピン留めダイアログ](media/service-get-started/power-bi-pin2.png)

4. ダッシュボードに戻ると、新しいタイルが表示されます。

   ![グラフがピン留めされたダッシュボード](media/service-get-started/power-bi-final-dashboard.png)

## <a name="clean-up-resources"></a>リソースをクリーンアップする
チュートリアルはこれで完了です。データセット、レポート、ダッシュボードは削除してかまいません。 

1. 左側のナビゲーション バーで **[マイ ワークスペース]** を選択します。
2. **[データセット]** タブを選択し、このチュートリアルのためにインポートしたデータセットを検索します。  
3. 省略記号 [...]、 **[削除]** の順に選択します。

    ![データセットを削除する](media/service-get-started/power-bi-delete.jpg)

    データセットを削除すると、Power BI のレポートとダッシュボードも削除されます。 


## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [Power BI で使用するオンライン サービスに接続する](service-connect-to-services.md)

