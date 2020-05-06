---
title: ダッシュボード、レポート、ブック、データセット、またはワークスペースを削除する
description: Power BI からほとんどすべてのものを削除する方法について説明します
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/11/2018
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: 0ccc32a18098673034e7f37b92f8edb5636ef21d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "73872536"
---
# <a name="delete-almost-anything-in-power-bi-service"></a>Power BI サービスのほとんどすべてのものを削除する
この記事では、Power BI サービスでダッシュボード、レポート、ブック、データセット、アプリ、視覚化、ワークスペースを削除する方法について説明します。

## <a name="delete-a-dashboard"></a>ダッシュボードの削除
ダッシュボードを、除去することができます。 ダッシュボードを除去しても、基となっているデータセットや、ダッシュボードに関連付けられているレポートは削除されません。

* ダッシュボードの所有者であれば、ダッシュボードを除去できます。 同僚とダッシュボードを共有している場合、自分の Power BI ワークスペースからダッシュボードを除去すると、同僚の Power BI ワークスペースからそのダッシュボードが除去されます。
* 他の人のダッシュボードを共有しているものの、参照する必要がなくなった場合は、除去できます。  ダッシュボードを除去しても、他の人の Power BI ワークスペースからは除去されません。
* ダッシュボードが[組織のコンテンツ パック](service-organizational-content-pack-disconnect.md)の一部である場合、それを除去する唯一の方法は、関連付けられているデータセットを除去することです。

### <a name="to-delete-a-dashboard"></a>ダッシュボードを削除するには
1. ワークスペースで、 **[ダッシュボード]** タブを選択します。
2. 削除するダッシュボードを見つけて、削除アイコン ![削除アイコン](media/service-delete/power-bi-delete-icon.png).

    ![ビデオ](media/service-delete/power-bi-delete-dash.gif)

## <a name="delete-a-report"></a>レポートの削除
レポートを削除しても、レポートの基になっているデータセットは削除されません。  レポートからピン留めしたすべての視覚化も削除されません。視覚化は、個別に削除しない限り、ダッシュボード上に保持されます。

### <a name="to-delete-a-report"></a>レポートを削除するには
1. ワークスペースで、 **[レポート]** タブを選択します。
2. 削除するレポートを見つけて、削除アイコン   ![削除アイコン](media/service-delete/power-bi-delete-icon.png).   

    ![ワークスペースのレポート タブ](media/service-delete/power-bi-delete-reportnew.png)
3. 削除を確認します。

   ![レポートの削除ダイアログ](media/service-delete/power-bi-delete-report.png)

   > [!NOTE]
   > レポートが[コンテンツ パック](service-organizational-content-pack-introduction.md)の一部である場合は、この方法では削除できません。  「[組織のコンテンツ パックに対する接続を削除する](service-organizational-content-pack-disconnect.md)」を参照してください。
   >
   >

## <a name="delete-a-workbook"></a>ブックを削除する
ブックを除去することができます。 ただし、ブックを除去すると、そのブックのデータを含むダッシュボード タイルやレポートもすべて除去されます。

ブックが OneDrive for Business に格納されている場合は、Power BI から削除しても OneDrive からは削除されません。

### <a name="to-delete-a-workbook"></a>ブックを削除するには
1. ワークスペースで、 **[ブック]** タブを選択します。
2. 削除するブックを見つけて、削除 ![削除アイコン](media/service-delete/power-bi-delete-report2.png) アイコンを選択します。

    ![ブック タブ](media/service-delete/power-bi-delete-workbooknew.png)
3. 削除を確認します。

   ![ブックの削除ダイアログ](media/service-delete/power-bi-delete-confirm.png)

## <a name="delete-a-dataset"></a>データセットの削除
データセットは削除することができます。 ただし、データセットを削除すると、そのデータセットのデータを含むダッシュボード タイルとレポートもすべて削除されます。

データセットが 1 つ以上の[組織のコンテンツ パック](service-organizational-content-pack-disconnect.md)の一部である場合、削除する唯一の方法は、データセットが使用されているコンテンツ パックから除去し、処理されるまで待ち、もう一度削除を試みることです。

### <a name="to-delete-a-dataset"></a>データセットを削除するには
1. ワークスペースで、 **[データセット]** タブを選択します。
2. 削除するデータセットを見つけて、**その他のオプション** (...) を選択します。  

    ![データセット タブ](media/service-delete/power-bi-delete-datasetnew.png)
3. ドロップダウン リストで、 **[削除]** を選択します。

   ![省略記号メニュー](media/service-delete/power-bi-delete-datasetnew2.png)
4. 削除を確認します。

   ![ダッシュボードの削除ダイアログ](media/service-delete/power-bi-delete-dataset-confirm.png)

## <a name="delete-a-workspace"></a>ワークスペースの削除
> [!WARNING]
> ワークスペースを作成するときは、Office 365 グループを作成します。 そして、ワークスペースを削除するときは、その Office 365 グループを削除します。 つまり、SharePoint や Microsoft Teams などの他の O365 製品からもグループが削除されます。
>
>

ワークスペースはその作成者が削除できます。 削除すると、すべてのグループ メンバーに関連するアプリも削除され、組織全体にアプリを発行した場合は、AppSource から除去されます。 ワークスペースを削除することは、ワークスペースから脱退することとは異なります。

### <a name="to-delete-a-workspace---if-you-are-an-admin"></a>ワークスペースを削除するには (管理者の場合)
1. ナビ ペインから **[ワークスペース]** を選択します。

2. 削除するワークスペースの右にある**その他のオプション** (...) を選択してから、 **[ワークスペースの編集]** を選択します。

    ![ワークスペース](media/service-delete/power-bi-delete-workspace.png)

3. **[ワークスペースの編集]** ウィンドウで、 **[ワークスペースの削除]**  >  **[削除]** の順に選択します。

    ![ワークスペースの削除](media/service-delete/power-bi-delete-workspace2.png)

### <a name="to-remove-a-workspace-from-your-list"></a>リストからワークスペースを除去するには
ワークスペースのメンバーである必要がなくなった場合は、ワークスペースから***脱退***することができます。そうすると、ワークスペースはリストから除去されます。 ワークスペースから脱退しても、他のすべてのワークスペース メンバーはそのままです。  

> [!IMPORTANT]
> ワークスペースの管理者が 1 人しかいない場合、Power BI ではその管理者の脱退は許可されません。
>
>

1. 除去するワークスペースに移動します。

2. 右上隅にある**その他のオプション** (...) を選択し、 **[ワークスペースからの脱退]**  >  **[脱退する]** の順に選択します。

      ![ワークスペースからの脱退](media/service-delete/power-bi-leave-workspace.png)

   > [!NOTE]
   > ドロップダウン リストに表示されるオプションは、そのワークスペースの管理者であるか、メンバーであるかによって異なります。
   >
   >

## <a name="delete-or-remove-an-app"></a>アプリを削除または除去する
アプリはアプリ リスト ページから簡単に除去できます。 ただし、アプリを完全に削除できるのはアプリ管理者のみです。

### <a name="remove-an-app-from-your-app-list-page"></a>アプリ リスト ページからアプリを除去する
アプリ リスト ページからアプリを削除しても、他のメンバーのアプリは削除されません。

1. ナビ ペインで、 **[アプリ]** を選択してアプリ リスト ページを開きます。
2. 削除するアプリにカーソルを合わせ、削除アイコン ![](media/service-delete/power-bi-delete-report2.png) を選択します。

   ![アプリの選択](media/service-delete/power-bi-delete-app.png)

   アプリを誤って除去した場合、いくつかの方法で戻すことができます。  たとえば、アプリ作成者に再送信を依頼するか、アプリへのリンクが示されている元のメールを見つけます。または、[通知センター](service-notification-center.md)でアプリの通知がまだリストされているかどうかを確認するか、組織の [AppSource](consumer/end-user-apps.md) を確認します。

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
この記事では、Power BI サービスの主な構成要素を削除する方法について説明します。 しかし、Power BI で削除できるものは他にも多数あります。  

* [おすすめのダッシュボードを除去する](service-dashboard-featured.md)
* [ダッシュボードをお気に入りから外す](service-dashboard-favorite.md)
* [レポート ページを削除する](service-delete.md)
* [ダッシュボード タイルを削除する](service-dashboard-edit-tile.md)
* [レポートの視覚化を削除する](service-delete.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
