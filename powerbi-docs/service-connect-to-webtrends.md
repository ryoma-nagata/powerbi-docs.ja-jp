---
title: Power BI で Webtrends に接続する
description: Power BI 用 Webtrends
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 25339052c0ddf410dab473a5a4a2fd9bbe445120
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70184617"
---
# <a name="connect-to-webtrends-with-power-bi"></a>Power BI で Webtrends に接続する
Power BI 用 Webtrends コンテンツ パックには、[合計ページ] ビューやトラフィック ソースごとのアクセス数などのすぐに使用できるさまざまなメトリックスが含まれています。 Power BI 内の Webtrends データの視覚化は、Webtrends アカウントに接続することで開始します。 提供されるダッシュボードとレポートをそのまま使用することもできますし、最も関心のある情報を強調表示するためにカスタマイズすることができます。  データは、1 日 1 回自動的に更新されることになります。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

[Power BI 用 Webtrends コンテンツ パック](https://app.powerbi.com/getdata/services/webtrends)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
   ![](media/service-connect-to-webtrends/getdata3.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
   ![](media/service-connect-to-webtrends/services.png)
3. **[Webtrends]** \> **[取得]** の順に選びます。
   
   ![](media/service-connect-to-webtrends/webtrends.png)
4. コンテンツ パックは、特定の Webtrends プロファイル ID に接続します。 [このパラメーターの見つけ方](#FindingParams)について詳しくは、後述します。
   
   ![](media/service-connect-to-webtrends/parameters.png)
5. 接続する Webtrends の資格情報を提供します。 [ユーザー名] フィールドには、アカウントとユーザー名が必要となることに注意してください。 以下で[詳細](#FindingParams)を確認してください。
   
   ![](media/service-connect-to-webtrends/creds.png)
6. 承諾後、インポート処理が自動的に開始されます。 完了すると、ナビゲーション ウィンドウに、新しいダッシュ ボード、レポート、モデルが表示されます。 インポートされたデータを表示するダッシュボードを選択します。
   
   ![](media/service-connect-to-webtrends/dashboard.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="whats-included"></a>含まれるもの
<a name="Included"></a>

Webtrends コンテンツ パックは、次のレポートのデータを取得します。  

| レポート名 | レポート ID |
| --- | --- |
| 主要メトリック | |
| オンサイト検索 |34awBVEP0P6 |
| 終了ページ |7FshY8eP0P6 |
| 次のページ |CTd5rpeP0P6 |
| 前のページ |aSdOeaUgnP6 |
| サイト ページ |oOEWQj3sUo6 |
| オンサイトの広告クリックスルー |41df19b6d9f |
| 市区町村 |aUuHskcP0P6 |
| Countries |JHWXJNcP0P6 |
| 訪問者 |xPcmTDDP0P6 |
| 訪問期間 |U5KAyqdP0P6 |
| 検索語句 |IKYEDxIP0P6 |
| トラフィック ソース |JmttAoIP0P6 |
| 検索エンジン |yGz3gAGP0P6 |
| エントリ ページ |i6LrkNVRUo6 |

>[!NOTE]
>SharePoint プロファイルの場合、メトリック名は Webtrends の UI に表示される名前と多少異なる場合があります。 SharePoint と Web プロファイルとの間の整合性を保つために、次のようなマッピングが行われます。   

    - セッション = アクセス  
    - 新しいユーザー = 新しい訪問者  
    - セッションあたりのビュー = アクセスあたりのページ ビュー  
    - ユーザーの日ごとの平均滞在時間 = 訪問者の平均サイト滞在時間  

## <a name="system-requirements"></a>システム要件
このコンテンツ パックを使用するには、[適切なレポートのセット](#Included)が有効になっている Webtrends プロファイルにアクセスする必要があります。

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>パラメーターの見つけ方
プロファイルを選択すると、URL に Webtrends プロファイルの ID が見つかります。

![](media/service-connect-to-webtrends/webtrendsparameters.png)

資格情報は、Webtrends へのサインイン時に入力したものと同じですが、アカウントとユーザー名は同じ行で、バックスラッシュ (\) で区切ることが期待されます。

![](media/service-connect-to-webtrends/webtrendscreds.png)

## <a name="troubleshooting"></a>トラブルシューティング
資格情報を入力した後、コンテンツ パックの読み込み中に問題が発生することがあります。 読み込み中に「問題発生」メッセージが表示される場合は、次のトラブルシューティング方法を参照してください。 問題が解決しない場合は、 https://support.powerbi.com にサポート チケットを提出してください。

1. 適切なプロファイル ID が使用されている。詳しくは、「[パラメーターの見つけ方](#FindingParams)」をご覧ください。
2. 「[含まれるもの](#Included)」に示されているレポートへのアクセス許可がユーザーに与えられている。

## <a name="next-steps"></a>次の手順
[Power BI とは?](power-bi-overview.md)

[Power BI サービスのデザイナー向けの基本的な概念](service-basic-concepts.md)

