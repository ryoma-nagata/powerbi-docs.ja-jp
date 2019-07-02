---
title: データセットにデータをプッシュする
description: Power BI データセットにデータをプッシュする
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 9eb81610044f795b6f9dc5c58aeefad13de06542
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222151"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Power BI データセットにデータをプッシュする

Power BI API を使用するデータを Power BI のデータセットをプッシュします。 この記事で紹介する既存のデータセットに Product テーブルを含む Sales Marketing データセットをプッシュする方法。

始める前に、Azure Active Directory (Azure AD) 必要があります、 [Power BI アカウント](create-an-azure-active-directory-tenant.md)します。

## <a name="steps-to-push-data-into-a-dataset"></a>データセットにデータをプッシュする手順

* 手順 1:[アプリを Azure AD に登録する](walkthrough-push-data-register-app-with-azure-ad.md)
* 手順 2:[認証アクセス トークンを取得する](walkthrough-push-data-get-token.md)
* 手順 3:[Power BI でデータセットを作成する](walkthrough-push-data-create-dataset.md)
* 手順 4:[Power BI テーブルに行を追加するためにデータセットを取得する](walkthrough-push-data-get-datasets.md)
* 手順 5:[Power BI テーブルに行を追加する](walkthrough-push-data-add-rows.md)

次のセクションでは、データをプッシュする Power BI API 操作の概要を説明します。

## <a name="power-bi-api-operations-to-push-data"></a>データをプッシュする Power BI API の操作

Power BI REST API を使うと、Power BI にデータ ソースをプッシュできます。 アプリは、データセットに行を追加するときに、新しいデータで自動的に更新プログラム ダッシュ ボードのタイルします。 データをプッシュするを使用して、 [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)と[PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)操作。 データセットを検索するには使用、[データセットの取得](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)操作。 これらの操作のいずれかのグループを使用するグループの ID を渡すことができます。 グループ ID の一覧を取得する、[グループの取得](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)操作。

データセットにデータをプッシュするための操作を次に示します。

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [データセットの取得](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [行の POST](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [グループの取得](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

Power BI でデータセットを作成するには、Power BI サービスに JavaScript Object Notation (JSON) 文字列を渡します。 JSON について詳しくは、「[JSON の紹介](http://json.org/)」をご覧ください。

データセットの JSON 文字列は、次のような形式です。

**Power BI のデータセット JSON オブジェクト**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

この Sales Marketing データセットの例では、次に示すように、JSON 文字列を渡します。 この例で**SalesMarketing**データセットの名前と**製品**テーブル名です。 テーブルを定義した後は、テーブル スキーマを定義します。 **SalesMarketing** データセットの場合、テーブル スキーマには次の列が含まれています:ProductID、Manufacturer、Category、Segment、Product、IsCompete。

**データセット オブジェクト JSON の例**

    {
        "name": "SalesMarketing",
        "tables": [
            {
                "name": "Product",
                "columns": [
                {
                    "name": "ProductID",
                    "dataType": "int"
                },
                {
                    "name": "Manufacturer",
                    "dataType": "string"
                },
                {
                    "name": "Category",
                    "dataType": "string"
                },
                {
                    "name": "Segment",
                    "dataType": "string"
                },
                {
                    "name": "Product",
                    "dataType": "string"
                },
                {
                    "name": "IsCompete",
                    "dataType": "bool"
                }
                ]
            }
        ]
    }

Power BI のテーブル スキーマでは、次のデータ型を使うことができます。

## <a name="power-bi-table-data-types"></a>Power BI テーブルのデータ型

| **データ型** | **制限事項** |
| --- | --- |
| Int64 |Int64.MaxValue と Int64.MinValue が許可されまていせん。 |
| Double |Double.MaxValue と Double.MinValue 値が許可されていません。 NaN はサポートされていません。 + 無限大と負の無限大 (たとえば、Min、Max) の一部の関数でサポートされていません。 |
| Boolean |なし |
| DateTime |データの読み込み中には、値 1/300 秒 (3.33 ミリ秒) の整数倍日時分数の量子化します。 |
| String |現在、最大 128 文字でもできます。 |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Power BI へのデータのプッシュに関する詳細

データセットへのデータのプッシュを始める方法については、「[手順 1:アプリを Azure AD に登録する](walkthrough-push-data-register-app-with-azure-ad.md)」 (左側のナビゲーション ウィンドウ) をご覧ください。

[次の手順 >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>次の手順

[Power BI にサインアップする](create-an-azure-active-directory-tenant.md)  
[JSON の紹介](http://json.org/)  
[Power BI REST API の概要](overview-of-power-bi-rest-api.md)  
他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。