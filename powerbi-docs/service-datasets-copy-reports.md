---
title: 他のワークスペースからレポートをコピーする (プレビュー) - Power BI
description: 組織全体でユーザーとデータセットを共有する方法について説明します。 これで、各自のワークスペースのデータセットに基づいてレポートを作成できます。
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: af0ffa5a879a2249c34ac73895103dfdf63e4d27
ms.sourcegitcommit: 4d5166944fcc6fe4666cab055ae75e7a0a77866d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530620"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>他のワークスペースからレポートをコピーする (プレビュー)

ワークスペースまたはアプリで気に入ったレポートを見つけたら、それをコピーし、別のワークスペースに保存できます。 これで、そのレポートのコピーを変更し、ビジュアルや他の要素を追加または削除することができるようになります。 データ モデルを作成する必要はありません。 既に作成されています。 また、一から始めるより、既存のレポートを変更するほうがずっと簡単です。 ただし、新しいワークスペースからアプリを作成する場合、レポートのコピーをアプリに発行できないことがあります。 詳細については、記事「ワークスペース全体でデータセットを使用する」の「[考慮事項と制限事項](service-datasets-across-workspaces.md#considerations-and-limitations)」を参照してください。

> [!NOTE]
> コピーを作成するには、元のレポートが Premium 容量内のワークスペースにある場合でも、Pro ライセンスが必要です。

## <a name="save-a-copy-of-a-report"></a>レポートのコピーを作成する

1. アプリまたはワークスペースで、[レポート] リスト ビューに移動します。

1. **[アクション]** で、 **[コピーの保存]** を選択します。

    ![レポートのコピーを作成する](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    **[コピーの保存]** アイコンが表示されるのは、レポートが新しいエクスペリエンス ワークスペース内にあり、[ビルド アクセス許可](service-datasets-build-permissions.md#build-permissions-for-shared-datasets)をお持ちの場合のみです。 ワークスペースにアクセスできる場合でも、データセットに対するビルド アクセス許可が必要です。

3. **[このレポートのコピーを保存します]** で、レポートに名前を付けて保存先のワークスペースを選択します。

    ![[コピーの保存] ダイアログ ボックス](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    レポートを現在のワークスペースまたは Power BI サービスの別のワークスペースに保存できます。 自分がメンバーである新しいエクスペリエンス ワークスペースのワークスペースのみが表示されます。
  
4. **[保存]** を選択します。

    レポートのコピーを保存すると、データセットへのライブ接続が作成され、完全なデータセットを使用してレポート作成エクスペリエンスを開くことができます。 データセットのコピーは作成していません。 データセットは、まだ元の場所に存在します。 独自のレポートで、そのデータセットのすべてのテーブルとメジャーを使用することができます。 データセットで行レベル セキュリティ (RLS) の制限が有効になるため、RLS ロールに基づいて表示のアクセス許可があるデータのみが表示されます。

    レポートがワークスペースの外部のデータセットに基づいている場合は、Power BI によってデータセットのリストのエントリが自動的に作成されます。 このデータセットのアイコンは、ワークスペース内のデータセットのアイコンとは異なります。 ![共有データセットのアイコン](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    これで、ワークスペースの外部のデータセットをどのレポートとダッシュボードが使用するかをワークスペースのメンバーが把握できます。 エントリにはデータセットに関する情報と、いくつかの選択アクションが表示されます。

    ![データセットのアクション](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>関連データセットを表示する

ワークスペースにレポートがあるときに、必要に応じてどのデータセットに基づいているかを確認することができます。

1. [レポート] リスト ビューで、 **[関連の表示]** を選択します。

    ![[関連の表示] アイコン](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. **[関連コンテンツ]** ダイアログ ボックスには、すべての関連項目が表示されます。 このリストでは、データセットは他のものと同じように表示されます。 別のワークスペース内にあるかどうかは判別できません。 これは既知の問題です。
 
    ![[関連コンテンツ] ダイアログ ボックス](media/service-datasets-copy-reports/power-bi-dataset-related.png)

## <a name="delete-a-report-and-its-shared-dataset"></a>レポートとその共有データセットを削除する

ワークスペース内のレポートおよびそれに関連付けられている共有データセットが不要になったと判断する場合があります。

1. レポートを削除します。 ワークスペース内のレポートの一覧で、**削除**アイコンを選択します。

    ![レポートの削除アイコン](media/service-datasets-across-workspaces/power-bi-datasets-delete-report.png)

2. データセットの一覧で、共有データセットには**削除**アイコンがないことがわかります。 ページを最新の情報に更新するか、別のページに移動して戻ります。 データセットがなくなります。 そうでない場合は、 **[関連の表示]** を確認してください。 ワークスペース内の別のテーブルに関連している可能性があります。

    ![[関連の表示] アイコン](media/service-datasets-across-workspaces/power-bi-dataset-view-related-icon.png)

    > [!NOTE]
    > このワークスペース内の共有データセットを削除しても、データセットは削除されません。 それに対する参照が削除されるだけです。


## <a name="next-steps"></a>次の手順

- [ワークスペース全体でデータセットを使用する (プレビュー)](service-datasets-across-workspaces.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](http://community.powerbi.com/)。
