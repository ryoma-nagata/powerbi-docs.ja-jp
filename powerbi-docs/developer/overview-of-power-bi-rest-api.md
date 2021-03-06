---
title: Power BI API の機能
description: Power BI API の機能
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 03/25/2019
ms.openlocfilehash: bbca4e5bf52ee0d4674cfcdc28edd53e90033a98
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2020
ms.locfileid: "74265221"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>Power BI API の開発者向け機能

Power BI REST API を使用すると、Power BI レポート、ダッシュボード、およびタイルと統合されるアプリを作成できます。

Power BI REST API を使用すると、レポート、データセット、ワークスペースなどの Power BI オブジェクトで管理タスクを実行できます。

Power BI API を使って行うことのできる例は以下のとおりです。

| **参照する内容** | **参照先の記事** |
|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| Power BI ユーザーと Power BI 以外のユーザーのためにレポート、ダッシュボード、タイルを埋め込む | [Power BI ダッシュボード、レポート、およびタイルを埋め込む方法](embedding-content.md) |
| Power BI オブジェクトで管理タスクを実行する | [Power BI REST API リファレンス](https://docs.microsoft.com/rest/api/power-bi/) |
| 既存のビジネス ワークフローを拡張して、主要なデータを Power BI ダッシュボードにプッシュします。 | [ダッシュボードにデータをプッシュする](walkthrough-push-data.md) |
| Power BI に対して認証を行う | [Power BI に対して認証を行う](get-azuread-access-token.md) |

> [!NOTE]
> Power BI API では引き続き、ワークスペースをグループと呼びます。 したがって、グループと記述されている場合はすべて、ワークスペースを使用していることを意味します。

## <a name="api-developer-tools"></a>API 開発者ツール

| ツール | 説明 |  |  |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
| [プレイグラウンド ツール](https://microsoft.github.io/PowerBI-JavaScript/demo) | Power BI JavaScript API を使用した完全なサンプルを体験できます。 このツールを使うと、さまざまな種類の Power BI Embedded のサンプルを簡単に再生することもできます。 |  |  |
| [Power BI JavaScript Wiki](https://github.com/Microsoft/powerbi-javascript/wiki) | Power BI JavaScript API の詳細情報が得られます。 |  |  |
| [Postman](https://www.getpostman.com/) | 要求の実行、テスト、デバッグ、監視、自動テストの実行などを行います。 |

## <a name="push-data-into-power-bi"></a>Power BI にデータをプッシュする

Power BI API を使って、[データセットにデータをプッシュ](walkthrough-push-data.md)できます。 この機能により、データセット内のテーブルに行を追加できます。 ダッシュボードのタイルやレポートのビジュアルに新しいデータが反映されます。

![サンプル データ をプッシュする](media/what-can-you-do/powerbi-push-data.png)

## <a name="github-repositories"></a>GitHub リポジトリ

* [Power BI の開発者向けサンプル](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)

## <a name="next-steps"></a>次のステップ

* [データセットにデータをプッシュする](walkthrough-push-data.md)
* [Power BI カスタム ビジュアルの開発](visuals/custom-visual-develop-tutorial.md)
* [Power BI REST API リファレンス](rest-api-reference.md)
* [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
