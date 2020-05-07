---
title: 追加の診断情報をキャプチャする
description: 次の手順では、Power BI Web クライアントから追加の診断情報を手動で収集するために可能性のある 2 つのオプションを提供します。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/17/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 670373afb5cb890c87a24a129cd43fde7bd5d892
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "74698902"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Power BI 用に追加の診断情報をキャプチャする

この記事では、Power BI Web クライアントから追加の診断情報を手動で収集する手順について説明します。

1. Microsoft Edge または Internet Explorer で [Power BI](https://app.powerbi.com) を閲覧します。

1. **F12** キーを押して、Microsoft Edge 開発者ツールを開きます。

   ![Microsoft Edge 開発者ツールの [要素] タブのスクリーンショット。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. **[ネットワーク]** タブを選びます。既ににキャプチャされたトラフィックが一覧表示されます。

   ![Microsoft Edge 開発者ツールの [ネットワーク] タブのスクリーンショット。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    次の操作を実行できます。

    * ウィンドウ内を閲覧して、発生する可能性のある問題を再現します。

    * セッション中にいつでも F12 キーを押して、開発者ツール ウィンドウの表示/非表示を切り替えます。

1. セッションのプロファイリングを停止するには、開発者ツール領域の **[ネットワーク]** タブで赤い四角形を選択します。

   ![Microsoft Edge 開発者ツールの [停止] ボタンが強調表示された [ネットワーク] タブのスクリーンショット。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. フロッピー ディスク アイコンを選択して、HTTP アーカイブ (HAR) ファイル形式でデータをエクスポートします。

   ![Microsoft Edge 開発者ツールのフロッピー ディスク アイコンが強調表示された [ネットワーク] タブのスクリーンショット。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. ファイル名を指定し、HAR ファイルを保存します。

    HAR ファイルには、次のようにブラウザー ウィンドウと Power BI の間のネットワーク要求に関するすべての情報が含まれます。

    * 各要求のアクティビティ ID。

    * 各要求の正確なタイムスタンプ。

    * クライアントに返されるエラー情報。

    このトレースには、画面に表示されるビジュアルを設定するのに使われるデータも含まれます。

1. サポートのレビュー用にも HAR ファイルを提供できます。

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
