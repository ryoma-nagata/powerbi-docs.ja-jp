---
title: Power BI で IntelliBoard に接続する
description: Power BI 用 IntelliBoard
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e912c47c58c96de8d2875b83a530468135e93ef2
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70185907"
---
# <a name="connect-to-intelliboard-with-power-bi"></a>Power BI で IntelliBoard に接続する
IntelliBoard を使用すると、Reporting Services を介してご利用の Moodle 学習管理システムのデータに簡単にアクセスできます。 Power BI 用 IntelliBoard コンテンツ パックは、コース、登録ユーザー、全体的な成績、および LMS アクティビティに関するメトリックを含む、追加の分析を提供します。

[!INCLUDE [include-short-name](./includes/service-deprecate-content-packs.md)]

Power BI 用 [IntelliBoard コンテンツ パック](https://app.powerbi.com/getdata/services/intelliboard)に接続します。

## <a name="how-to-connect"></a>接続する方法
1. 左側のナビゲーション ウィンドウの下部にある **[データの取得]** を選択します。  
   
    ![](media/service-connect-to-intelliboard/getdata.png)
2. **[サービス]** ボックスで、 **[取得]** を選択します。  
   
    ![](media/service-connect-to-intelliboard/services.png)
3. **[IntelliBoard]** 、 **[取得]** の順に選択します。  
   
    ![](media/service-connect-to-intelliboard/intelliboard.png)
4. **[OAuth 2]** を選択し、 **[サインイン]** をクリックします。 要求されたら、IntelliBoard 資格情報を入力します。
   
    ![](media/service-connect-to-intelliboard/creds.png)
   
    ![](media/service-connect-to-intelliboard/creds2.png)
5. 接続されると、ダッシュボード、レポート、およびデータセットが自動的に読み込まれます。 完了すると、タイルが IntelliBoard アカウントからのデータで更新されます。
   
    ![](media/service-connect-to-intelliboard/dashboard.png)

**実行できる操作**

* ダッシュボード上部にある [Q&A ボックスで質問](consumer/end-user-q-and-a.md)してみてください。
* ダッシュボードで[タイルを変更](service-dashboard-edit-tile.md)できます。
* [タイルを選択](consumer/end-user-tiles.md)して基になるレポートを開くことができます。
* データセットは毎日更新するようにスケジュール設定されますが、更新のスケジュールは変更でき、また **[今すぐ更新]** を使えばいつでも必要なときに更新できます。

## <a name="whats-included"></a>含まれるもの
コンテンツ パックには、次のテーブルのデータが含まれています。  

    - アクティビティ  
    - Agents  
    - Auth  
    - Countries  
    - CoursesProgress  
    - Enrollments
    - Lang  
    - Platform  
    - Totals  
    - UsersProgress    

## <a name="system-requirements"></a>システム要件
このコンテンツ パックをインスタンス化するには、上記のテーブルへのアクセス許可を持つ IntelliBoard アカウントが必要です。

## <a name="next-steps"></a>次の手順
[Power BI とは?](power-bi-overview.md)

[Power BI サービスのデザイナー向けの基本的な概念](service-basic-concepts.md)

