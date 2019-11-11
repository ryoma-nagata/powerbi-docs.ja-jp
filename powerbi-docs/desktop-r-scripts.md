---
title: Power BI Desktop での R スクリプトの実行
description: Power BI Desktop での R スクリプトの実行
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6b69f701e0a5b9030a1f4469d6b09b189759debc
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876175"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>Power BI Desktop での R スクリプトの実行
**Power BI Desktop** で R スクリプトを直接実行し、生成されたデータセットを Power BI Desktop データ モデルにインポートできます。

## <a name="install-r"></a>R をインストールする
Power BI Desktop で R スクリプトを実行するには、ローカル コンピューターに **R** をインストールする必要があります。 **R** はさまざまな場所から無料でダウンロードし、インストールできます。たとえば、[Revolution Open ダウンロード ページ](https://mran.revolutionanalytics.com/download/)や [CRAN Repository](https://cran.r-project.org/bin/windows/base/) があります。 Power BI Desktop での R スクリプトの現在のリリースでは、インストール パスで Unicode 文字と空白 (空の文字) がサポートされています。

## <a name="run-r-scripts"></a>R スクリプトを実行する
Power BI Desktop で数回の手順を踏むことで、R スクリプトを実行し、データ モデルを作成し、データ モデルからレポートを作成し、Power BI サービスで共有できます。 Power BI Desktop の R スクリプトは、小数点 (.) とコンマ (,) が含まれる数値形式をサポートするようになりました。

### <a name="prepare-an-r-script"></a>R スクリプトを準備する
Power BI Desktop で R スクリプトを実行するには、ローカル R 開発環境でスクリプトを作成し、それが正常に動作することを確認します。

Power BI Desktop でスクリプトを実行するには、新しく、変更されていないワークスペースでスクリプトが正常に動作することを確認します。 つまり、すべてのパッケージと依存関係を明示的に読み込み、実行する必要があります。 *source()* を利用し、依存スクリプトを実行できます。

Power BI Desktop で R スクリプトを準備し、実行するとき、いくつかの制限があります。

* インポートできるのはデータ フレームだけです。Power BI にインポートするデータがデータ フレームで表されていることを確認してください。
* 型が「複合」や「ベクトル」の列はインポートされず、作成されたテーブルではエラー値で置換されます。
* 「該当なし」の値は、Power BI Desktop では NULL 値に変換されます。
* R スクリプトは、30 分以上実行するとタイムアウトになります。
* ユーザー入力の待機中など、R スクリプトの対話的呼び出しでスクリプトの実行が停止します。
* R スクリプト内で作業ディレクトリを設定する場合は、作業ディレクトリへの相対パスではなく、完全パスを定義する *必要* があります。

### <a name="run-your-r-script-and-import-data"></a>R スクリプトを実行し、データをインポートする
1. Power BI Desktop では、R スクリプトのデータ コネクタは **[データの取得]** にあります。 R スクリプトを実行するには、 **[データの取得]&gt;[詳細]** の順に選び、次の図に示すように **[その他]&gt;[R スクリプト]** の順に選びます。
   
   ![](media/desktop-r-scripts/r-scripts-1.png)
2. R がローカル コンピューターにインストールされている場合、最近インストールしたバージョンが R エンジンとして選択されます。 スクリプトをスクリプト ウィンドウにコピーし、 **[OK]** を選択します。
   
   ![](media/desktop-r-scripts/r-scripts-2.png)
3. R がインストールされていないか、識別されない場合、あるいはローカル コンピューターに複数のインストールが存在する場合、 **[R インストール設定]** を展開してインストール オプションを表示するか、R スクリプトを実行するインストールを選択します。
   
   ![](media/desktop-r-scripts/r-scripts-3.png)
   
   R がインストールされているが、識別されない場合、 **[R インストール設定]** を展開するとき、テキスト ボックスにその場所を明示的に指定できます。 上の画像では、パス *C:\Program Files\R\R-3.2.0* がテキスト ボックスに明示的に指定されています。
   
   R インストール設定は、[オプション] ダイアログの [R スクリプト] セクションの中央に配置されています。 R インストール設定を指定するには、 **[ファイル] > [オプションと設定]** を選んでから、 **[オプション] > [R スクリプト]** を選びます。 R の複数のインストールを使用できる場合、ドロップダウン メニューが表示され、使用するインストールを選べます。
   
   ![](media/desktop-r-scripts/r-scripts-4.png)
4. **[OK]** を選択し、R スクリプトを実行します。 スクリプトが正常に実行されたら、生成されたデータ フレームを選択し、Power BI モデルに追加できます。

### <a name="refresh"></a>更新
Power BI Desktop で R スクリプトを更新できます。 R スクリプトを更新するとき、Power BI Desktop は Power BI Desktop 環境で R スクリプトをもう一度実行します。

## <a name="next-steps"></a>次の手順
Power BI での R については、次の追加情報を参照してください。

* [Power BI Desktop で R ビジュアルを作成する](desktop-r-visuals.md)
* [Power BI で外部 R IDE を使用する](desktop-r-ide.md)

