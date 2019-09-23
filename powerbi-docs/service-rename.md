---
title: ダッシュボード、レポート、ワークスペース、レポートのページ、データセットの名前を変更する
description: Power BI サービスのほとんどすべてのものの名前を変更します。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/01/2018
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 905ef263084cf531e6b38fb4640286e4d78697ce
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273769"
---
# <a name="rename-almost-anything-in-power-bi-service"></a>Power BI サービスのほとんどすべてのものの名前を変更する
この記事では、Power BI サービスのダッシュボード、レポート、レポートのページ、ブック、データセット、アプリ、ワークスペースの名前を変更する方法について説明します。

**名前を変更できるもの**

| コンテンツの種類 | 作成者 | 自分と共有 |
| --- | --- | --- |
| ワークスペースのダッシュボード |はい |いいえ |
| ワークスペースのレポート |はい |いいえ |
| ワークスペースのブック |はい |いいえ |
| ワークスペースのデータセット |はい |いいえ |
| アプリ ワークスペース |はい (所有者の場合、または管理者アクセス許可を持っている場合) |いいえ |
| 発行されたアプリ |[アプリ] 画面からはできませんが、管理者アクセス許可がある場合はアプリ ワークスペースでアプリの名前を変更して新しい名前で再発行できます |いいえ |
| アプリのコンテンツ (ダッシュボード、レポート、ブック、データセット) |[アプリ] 画面からはできませんが、管理者アクセス許可がある場合はアプリ ワークスペースでアプリのコンテンツの名前を変更して新しい名前で再発行できます |いいえ |
| **[自分と共有]** のコンテンツ |いいえ |いいえ |

## <a name="rename-a-dashboard-report-or-workbook"></a>ダッシュボード、レポート、ブックの名前を変更する
1. ワークスペースで **[ダッシュボード]** 、 **[レポート]** 、または **[ブック]** タブを選びます。名前を変更するアイテムをポイントし、歯車アイコン ![歯車アイコン](media/service-rename/powerbi-cog-icon.png) を選びます。 歯車アイコンが表示されない場合は、名前を変更するアクセス許可がありません。
   
   ![Power BI サービス ワークスペース](media/service-rename/power-bi-workspace-dashboards.png)
2. [設定] ページで、新しい名前を入力して **[保存]** を選びます。
   
   ![データセットの [設定] ウィンドウ](media/service-rename/power-bi-rename-dashboard2.png)

## <a name="rename-a-dataset"></a>データセットの名前を変更する
1. ワークスペースで **[データセット]** タブを選びます。
   
   ![ワークスペースの [データセット] タブ](media/service-rename/power-bi-ellipses.png)
2. 名前を変更するアイテムをポイントし、省略記号 [...] を選んで、 **[名前の変更]** を選びます。  
   
      ![[名前の変更] の選択](media/service-rename/power-bi-rename-datasets.png)
   
   > [!NOTE]
   > ドロップダウンのオプションは変化します。
   > 
   > 
3. [設定] ページで、新しい名前を入力して **[保存]** を選びます。
   
     ![[名前変更] ウィンドウ](media/service-rename/power-bi-rename.png)

## <a name="rename-an-app-workspace"></a>アプリ ワークスペースの名前を変更する
管理者アクセス許可を持つユーザーはアプリ ワークスペースの名前を変更できます。

1. 名前を変更するワークスペースに移動します。
2. 右上隅の省略記号 [...] を選び、 **[ワークスペースの編集]** を選びます。 このオプションが表示されない場合は、このワークスペースの名前を変更するアクセス許可がありません。 
   
    ![[ワークスペースの編集] の選択](media/service-rename/power-bi-edit-workspace.png)
3. 新しいワークスペース名を入力し、 **[保存]** を選びます。
   
   ![[ワークスペースの編集] ウィンドウ](media/service-rename/power-bi-workspace-rename.png)

## <a name="rename-a-page-in-a-report"></a>レポートのページの名前を変更する
Power BI レポートのページの名前を変更するには、  1 回クリックするだけです。 ページの名前は[レポート編集ビュー](service-interact-with-a-report-in-editing-view.md)で変更できます。

1. レポートを[編集ビュー](consumer/end-user-reading-view.md)で開きます。
2. Power BI ウィンドウの下部にあるレポート ページのタブを探します。
   
    ![タブが強調表示されたレポート](media/service-rename/report-page-tabs-new.png)
3. タブを選び、名前を変更するレポート ページを開きます。
4. タブ上の名前をダブルクリックして、強調表示にします。  
   
    ![タブ名の強調表示](media/service-rename/hilite-tab.png)
5. レポート ページの新しい名前を入力して、Enter キーを押します。
   
    ![新しいページ名の入力](media/service-rename/new-name.png)

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
* 名前を変更しようとするアイテムが自分と共有されている場合、またはコンテンツ パックの一部である場合は、歯車アイコンは表示されず、[設定] にはアクセスできません。
* **[データセット]** タブに省略記号 [...] が表示されていない場合は、ブラウザーのウィンドウを広げます。

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

