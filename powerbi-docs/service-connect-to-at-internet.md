---
title: Power BI で AT Internet Bridge に接続する
description: Power BI 用 AT Internet Bridge
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: c24a508652b147b6fc684039d2965f9935b624c0
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70186034"
---
# <a name="connect-to-at-internet-bridge-with-power-bi"></a>Power BI で AT Internet Bridge に接続する
AT Internet 社が提供する統合デジタル分析プラットフォーム Analytics Suite を使用すると、データからイミディエイト値を抽出できます。 Power BI 用 AT Internet Bridge コンテンツ パックには、ユーザーのサイトに関する、訪問者、ソース、ローカライズ、およびデバイスのデータが格納されます。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Power BI 用 [AT Internet Bridge コンテンツ パック](https://app.powerbi.com/getdata/services/at-internet-bridge)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。
   
   ![](media/service-connect-to-at-internet/pbi_getdata.png) 
2. **[サービス]** ボックスで、 **[取得]** を選択します。
   
   ![](media/service-connect-to-at-internet/pbi_getservices.png) 
3. **[AT Internet Bridge]** \> **[取得]** の順に選択します。
   
   ![](media/service-connect-to-at-internet/atinternet.png)
4. 接続先の AT Internet Web サイト番号を指定します。
   
   ![](media/service-connect-to-at-internet/params.png)
5. 認証メカニズムとして **[Basic]** を選択し、AT Internet のユーザー名とパスワードを入力して、 **[サインイン]** をクリックします。
   
   ![](media/service-connect-to-at-internet/creds.png)
6. **[接続]** をクリックしてインポート プロセスを開始します。 完了すると、ナビゲーション ウィンドウに、新しいダッシュ ボード、レポート、モデルが表示されます。 インポートされたデータを表示するダッシュボードを選択します。
   
    ![](media/service-connect-to-at-internet/atinternet.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="whats-included"></a>含まれるもの
このコンテンツ パックには、次の表に、過去 45 日間のデータが含まれています。  

    - 変換  
    - デバイス  
    - ローカライズ  
    - ソース  
    - グローバル アクセス  

## <a name="next-steps"></a>次の手順
[Power BI とは?](power-bi-overview.md)

[Power BI サービスのデザイナー向けの基本的な概念](service-basic-concepts.md)

