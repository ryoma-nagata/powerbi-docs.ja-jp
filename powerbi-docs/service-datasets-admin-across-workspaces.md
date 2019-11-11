---
title: ワークスペース全体でデータセットの使用を制御する (プレビュー) - Power BI
description: Power BI テナント内の情報のフローを制限する方法について説明します。
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d1ad29bebc148d9f30e8d22240dd149787251a0a
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872583"
---
# <a name="control-the-use-of-datasets-across-workspaces-preview"></a>ワークスペース全体でデータセットの使用を制御する (プレビュー)

ワークスペース全体でデータセットを使用することは、組織内でデータのカルチャとデータの民主化を推進するための強力な方法です。 それでも、Power BI の管理者であれば、Power BI テナント内の情報のフローを制限することがあります。 テナント設定の **[ワークスペース全体でデータセットを使用する]** を使用すると、セキュリティ グループごとにデータセットの再利用を完全にまたは部分的に制限できます。

![Power BI 管理者ワークスペースの設定](media/service-datasets-admin-across-workspaces/power-bi-admin-workspace-settings.png)

この設定をオフにした場合、レポート作成者には次の影響があります。

- ワークスペース間でレポートをコピーするボタンを使用できません。 
- 共有データセットに基づくレポートでは、 **[レポートの編集]** ボタンを使用できません。
- Power BI サービスの検出エクスペリエンスでは、現在のワークスペースのデータセットのみが表示されます。
- Power BI Desktop の検出エクスペリエンスでは、自分がメンバーになっているワークスペースのデータセットのみが表示されます。
- Power BI Desktop で、ユーザーが自分がメンバーであるワークスペース以外のデータセットに対して、ライブ接続を使用して .pbix ファイルを開くと、別のデータセットに接続するように求めるエラー メッセージが表示されます。

## <a name="provide-a-link-for-the-certification-process"></a>認証プロセスのリンクを提供する

テナント管理者の場合、 **[推奨]** 設定ページに**詳細情報**のリンクの URL を提供することができます。  このリンクで、認定プロセスについてのドキュメントに移動できます。 **詳細情報**のリンクの宛先を指定しない場合は、既定で[データセットの認定](service-datasets-certify.md)に関する記事が示されます。

![データセットの認定の詳細情報](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

## <a name="next-steps"></a>次の手順

- [ワークスペース全体でデータセットを使用する (プレビュー)](service-datasets-across-workspaces.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
