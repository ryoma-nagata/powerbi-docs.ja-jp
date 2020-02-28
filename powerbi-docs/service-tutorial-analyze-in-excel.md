---
title: チュートリアル:Excel から開始して Power BI の [Excel で分析] を使用する
description: このチュートリアルでは、Excel から開始して [Power BI データセット] ページに接続し、Excel にデータセットをインポートします。
author: tejaskulkarni
ms.reviewer: davidiseminger
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 02/13/2020
ms.author: tekulkar
LocalizationGroup: Connect to services
ms.openlocfilehash: d3795c34e477c593af4afefbe5cc01040026bfa4
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/18/2020
ms.locfileid: "77426543"
---
# <a name="tutorial-use-power-bi-analyze-in-excel-starting-in-excel"></a>チュートリアル:Excel から開始して Power BI の [Excel で分析] を使用する

あなたの組織では、Power BI を利用してデータへのアクセスを共有しています。 Excel から Power BI の [Excel で分析] 機能を開始して、Excel でピボットテーブルとピボットグラフを作成します。 これにより、自分の分析にコンテキストが追加されたり、関連するデータセットを見つけてインポートする時間を短縮したりすることができます。

Power BI データセットの使用を開始するには、Excel 内で [Excel で分析] を選択します。 データを使用するピボットテーブルを作成する方法について説明します。  

組織によって共有されている追加のデータセットを見つけるには、[データセット] ページに戻ります。

いずれかの時点で問題が発生した場合は、以下のフローの適切な手順で **[いいえ]** を選択し、リンクされたフォームでフィードバックを提供してください。  

このチュートリアルで学習する内容は次のとおりです。

> [!div class="checklist"]
> * [Power BI データセット] ページから ODC ファイルをダウンロードします。
> * Excel からデータセットへのアクセスを有効にします。
> * データセットを使用してピボットテーブル、グラフ、およびワークシートを作成します

## <a name="prerequisites"></a>前提条件

このチュートリアルを完了するには、次のものが必要です。

* Power BI アカウント。 Power BI にサインアップしていない場合は、[無料の試用版にサインアップ](https://app.powerbi.com/signupredirect?pbi_source=web)してください。

* 「[Power BI サービスの概要](https://docs.microsoft.com/power-bi/service-get-started)」チュートリアルに記載されているすべての手順を理解しておきます。

* Power BI Premium データセットと Power BI Pro ライセンスが必要です。詳細については、「[Power BI Premium とは](https://docs.microsoft.com/power-bi/service-premium-what-is)」を参照してください。

* 前提条件の完全な一覧については、包括的な「[Excel で分析](https://docs.microsoft.com/power-bi/service-analyze-in-excel#requirements)」のドキュメントを参照してください。

* アクティブな [Microsoft Office E5 サブスクリプション](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab)

## <a name="get-started"></a>作業の開始

Excel で、Power BI 共有データを使用してピボットテーブルを作成するオプションを選択し、[Power BI データセット] ページに移動します。

![[データセット] ページ](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-01.png)

"Excel で分析" ワークフローを使用しているときに、進行する各手順を完了したかどうかを示すいくつかのプロンプトが表示されます。 いずれかの手順で問題が発生した場合は、 **[いいえ]** を選択して、対応するフォームに関するフィードバックを提供します。

![ワークフローの手順](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-02.png)

## <a name="download-and-open-the-odc-file"></a>ODC ファイルをダウンロードして開く

対応する一覧と関連するワークスペースからデータセットを選択し、[Excel で分析] をクリックします。 Power BI によって ODC ファイルが作成され、ブラウザーからコンピューターにダウンロードされます。

![データセットの選択](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-03.png)

Excel でファイルを開くと、Power BI データセットの表、フィールド、メジャーとともに、空のピボットテーブルとフィールドの一覧が表示されます。 Excel でローカルのデータセットに対して作業する場合と同じように、ピボットテーブルやグラフを作成したり、データセットを分析したりできます。

## <a name="enable-data-connections"></a>データ接続を有効にする

Excel で Power BI データを分析するために、接続を信頼するように求めるメッセージが表示される場合があります。 管理者は、Power BI 管理ポータルから、Analysis Services データベースのオンプレミス データセット上での [Excel で分析] の使用を無効にすることができます。

![接続を有効にする](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-04.png)

## <a name="install-updates-and-authenticate"></a>更新プログラムをインストールして認証する

新しい ODC ファイルを初めて開くときに、Power BI アカウントでの認証が必要になることもあります。  問題が発生した場合は、包括的な [Excel で分析](https://docs.microsoft.com/power-bi/service-analyze-in-excel#sign-in-to-power-bi )のドキュメントで詳細を確認するか、ワークフロー中に [いいえ] をクリックします。

![接続を有効にする](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-05.png)

## <a name="analyze-away"></a>分析

他のローカル ブックと同様に、[Excel で分析] を使うと、ピボット テーブルとグラフの作成、データの追加、データへのビューが設定されたさまざまなワークシートの作成を行うことができます。 [Excel で分析] を使うと、すべての詳細レベルのデータが、データセットへのアクセス許可を持つすべてのユーザーに公開されます。 このブックは保存できますが、これを Power BI に発行することやインポートして戻すこと、または組織内の他のユーザーと共有することはできません。 詳細およびその他のユース ケースについては、「[Excel で分析](https://docs.microsoft.com/power-bi/service-analyze-in-excel#analyze-away)」を参照してください。

## <a name="clean-up-resources"></a>リソースをクリーンアップする

Power BI サービスおよび [データセット] ページとの対話は、ODC ファイルのダウンロードとワークフローのクリックに限定するようにします。 これらのいずれかの手順で問題が発生した場合は、適切な手順で **[いいえ]** を指定し、リンクされているフォームでフィードバックを提供してください。 フォームには、問題に関する詳細情報のリンクが含まれています。 [データセット] ページに戻って、プロセスを再試行するか、別のデータセットを選択します。

## <a name="next-steps"></a>次の手順

次の記事にも興味をもたれるかもしれません。

* [Power BI Desktop でレポート間のドリルスルーを使用する](https://docs.microsoft.com/power-bi/desktop-cross-report-drill-through)

* [Power BI Desktop でスライサーを使用する](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-slicers)
