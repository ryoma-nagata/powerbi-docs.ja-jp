---
title: 動的バインド
description: 動的バインドを使用してレポートを埋め込む方法について説明します。
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8110023de4df28f65129bd53203cec9752acc1af
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73864459"
---
# <a name="dynamic-binding"></a>動的バインド

動的バインドを使用すると、レポートを埋め込む際にデータセットを動的に選択できます。 レポートとデータセットは、必ずしも同じワークスペースに存在している必要はありません。 エンド ユーザーには、選択したデータセットに応じて異なる結果が表示されます。

両方のワークスペース (レポートが含まれるワークスペースとデータセットが含まれるワークスペース) が容量に割り当てられている必要があります。

動的バインドを使用したレポートの埋め込みには、次の 2 つの段階があります。
1. トークンを生成する
2. 構成オブジェクトを調整する

## <a name="generating-a-token"></a>トークンを生成する
トークンを生成するには、[複数の項目の埋め込みトークンを生成するための API](embed-sample-for-customers.md#multiEmbedToken) を使用します。

動的バインドは、「*組織向けの埋め込み*」と「*顧客向けの埋め込み*」の両方の埋め込みシナリオでサポートされます。

| ソリューション                   | トークン                               | 要件                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *組織向けの埋め込み* | Power BI ユーザーのアクセス トークン     | 使用する Azure AD トークンを所有するユーザーには、すべての成果物に対する適切なアクセス許可があることが必要です。                                                                    |
| *顧客向けの埋め込み*    | Power BI ユーザーではないユーザーのアクセス トークン | レポートと動的にバインドされたデータセットの両方に対するアクセス許可を含んでいることが必要です。 新しい API を使用して、複数のアーティファクトをサポートする埋め込みトークンを生成します。 |

## <a name="adjusting-the-config-object"></a>構成オブジェクトを調整する
構成オブジェクトに `datasetBinding` を追加します。 ページ末尾の例を参考にしてください。

Power BI での埋め込みに馴染みのない方は、Power BI のコンテンツを埋め込む方法を次のチュートリアルでご覧いただけます。
* [顧客向けのアプリケーションに Power BI コンテンツを埋め込む](embed-sample-for-customers.md)
* [チュートリアル:組織向けのアプリケーションに Power BI コンテンツを埋め込む](embed-sample-for-your-organization.md)

 ### <a name="example"></a>例
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```