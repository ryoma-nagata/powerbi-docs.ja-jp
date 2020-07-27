---
title: デプロイ パイプラインの概要
description: Power BI のデプロイ パイプラインについて説明します
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: 5522d84cab235270a2eb368be02cfa0fb4e5eaa9
ms.sourcegitcommit: 10c5b6cd5e7070f96de8a9f1d9b95f3d242ac7f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86557143"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>デプロイ パイプラインの概要 (プレビュー)

現代の組織にとって、分析は意思決定を行う上で必要不可欠な要素です。 Power BI を分析ツールとして使用することが増えたことで、より多くのデータを使用し、より魅力的に、そしてよりわかりやすいようにする必要性が出てきました。 ただし、これだけでなく、Power BI は常に利用可能で信頼性の高いものである必要があります。 これらの要件を満たすため、BI 作成者は効率的に共同作業を行う必要があります。

デプロイ パイプラインは、Premium 容量を持つ企業の BI 作成者が組織のコンテンツのライフサイクルを管理できるようにする、効率的で再利用可能なツールです。 これにより、レポート、ダッシュボード、データセットなどの Power BI コンテンツをエンド ユーザーが使用する前に、開発してテストできます。

このツールは、次の 3 つのステージからなるパイプラインとして設計されています。

* **<a name="development"></a>開発**
    
    このステージは、他の作成者と共に新しいコンテンツを設計、構築、アップロードするために使用されます。 これは、デプロイ パイプラインの最初のステージです。

* **<a name="test"></a>テスト**

    コンテンツがアップロードされ、すべての変更が開発ステージで行われた後、テストのためにコンテンツをこのステージに移動できます。 テスト環境で実行できることの 3 つの例を次に示します。

    * テスト担当者およびレビュー担当者とコンテンツを共有する

    * 大量のデータがあるテストを読み込んで実行する

    * アプリをテストして、エンド ユーザー向けにどのように表示されるかを確認する

* **<a name="production"></a>運用**

    コンテンツのテスト後、運用ステージを使用して、コンテンツの最終バージョンを組織内のビジネス ユーザーと共有します。

![開発、テスト、運用という 3 つのステージすべてが設定された、動作中のデプロイ パイプラインのスクリーンショット。](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>次の手順

>[!div class="nextstepaction"]
>[デプロイ パイプラインの使用を開始する](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[デプロイ パイプライン プロセスを理解する](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[デプロイ パイプラインのトラブルシューティング](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[デプロイ パイプラインのベスト プラクティス](deployment-pipelines-best-practices.md)