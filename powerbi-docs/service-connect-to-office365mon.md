---
title: Power BI で Office365Mon に接続する
description: Power BI 用 Office365Mon
author: paulinbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 11/26/2019
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 8e9563d10d80290a48e20cd2d6a889831d34924b
ms.sourcegitcommit: fe9253a6021b9e198afa28aa9c670c3bacf59674
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74548588"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Power BI で Office365Mon に接続する
Office 365 の障害および正常性のパフォーマンス データの分析は、Power BI や Office365Mon テンプレート アプリを使用すると簡単です。 Power BI は、障害および正常性 プローブを含むデータを取得してから、そのデータに基づいてすぐに使えるダッシュボードおよびレポートを作成します。

Power BI 用 [Office365Mon テンプレート アプリ](https://msit.powerbi.com/groups/me/getapps/services/office365mon.office365mon_powerbi_v3)に接続します。

>[!NOTE]
>Power BI テンプレート アプリに接続して読み込むには、Office365Mon の管理者アカウントが必要です。

## <a name="how-to-connect"></a>接続する方法
1. ナビ ペインの下部にある **[データの取得]** を選択します。
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. **[Office365Mon]** \> **[接続]** を選択します。
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. [認証方法] として **[oAuth2]** を選択し、 **[サイン イン]** をクリックします。
   
   プロンプトが表示されたら、Office365Mon の管理者資格情報を入力し、認証プロセスに従います。
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. Power BI によるデータのインポート後、新しいダッシュ ボード、レポート、データセットがナビ ペインに表示されます。 新しい項目は、黄色のアスタリスク (\*) でマークされます。Office365Mon エントリを選択します。
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="troubleshooting"></a>トラブルシューティング
Office365Mon サブスクリプション資格情報を使用してログインした後に **"ログインに失敗しました"** エラーが表示された場合、使用しているアカウントには、アカウントから Office365Mon データを取得するためのアクセス許可がありません。 管理者アカウントであることを確認してからやり直してください。

## <a name="next-steps"></a>次の手順
[Power BI とは?](fundamentals/power-bi-overview.md)

[Power BI のデータの取得](service-get-data.md)

