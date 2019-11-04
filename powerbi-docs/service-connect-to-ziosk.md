---
title: Power BI で Ziosk Survey Analytics に接続する
description: Power BI 用 Ziosk
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 5e16264c3cf5b6d361353c18ba9eb666fd00ce5d
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060461"
---
# <a name="connect-to-ziosk-survey-analytics-with-power-bi"></a>Power BI で Ziosk Survey Analytics に接続する
BI 用 Ziosk Survey Analytics コンテンツ パックは、Ziosk タブレットを使用しているレストランに対し、Ziosk 調査データによって提供される、日、場所、従業員などに基づくセグメント化を含む詳細データへのアクセスを提供します。

Power BI 用 [Ziosk Survey Analytics コンテンツ パック](https://app.powerbi.com/getdata/services/ziosk-survey-analytics)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。  
   
    ![](media/service-connect-to-ziosk/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。  
   
    ![](media/service-connect-to-ziosk/services.png)
3. **[Ziosk Survey Analytics]** 、 **[接続]** の順に選びます。  
   
    ![](media/service-connect-to-ziosk/ziosk.png)
4. **[OAuth 2]** を選択し、 **[サインイン]** をクリックします。 要求されたら、Ziosk 資格情報を入力します。
   
    ![](media/service-connect-to-ziosk/creds.png)
   
    ![](media/service-connect-to-ziosk/creds2.png)
5. 接続されると、ダッシュボード、レポート、およびデータセットが自動的に読み込まれます。 完了すると、タイルが Ziosk アカウントからのデータで更新されます。
   
    ![](media/service-connect-to-ziosk/dashboard.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="whats-included"></a>含まれるもの
コンテンツ パックには、次のテーブルのデータが含まれています。  

    - アルコール カテゴリ  
    - 前菜カテゴリ  
    - コメント キーワード  
    - 日付  
    - 放送時間区分  
    - デザート カテゴリ  
    - フリー フォーム  
    - 子供カテゴリ  
    - メッセージ  
    - プレミアム コンテンツ カテゴリ  
    - 質問  
    - ストア  
    - 調査  
    - 平日  


## <a name="system-requirements"></a>システム要件
このコンテンツ パックをインスタンス化するには、上記のテーブルへのアクセス許可を持つ Ziosk アカウントが必要です。

## <a name="next-steps"></a>次の手順
[Power BI とは?](fundamentals/power-bi-overview.md)

[Power BI サービスのデザイナー向けの基本的な概念](service-basic-concepts.md)

