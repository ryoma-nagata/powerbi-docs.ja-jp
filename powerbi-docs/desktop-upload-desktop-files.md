---
title: Power BI Desktop からの発行
description: Power BI Desktop からの発行
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 3a67c36b2594696e1c576693cc5808eb0227c1c7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "76709610"
---
# <a name="publish-datasets-and-reports-from-power-bi-desktop"></a>Power BI Desktop からデータセットとレポートを発行する
Power BI Desktop ファイルを Power BI サービスに発行すると、モデル内のデータが Power BI ワークスペースに発行されます。 **レポート** ビューで作成したレポートの場合も同様です。 ワークスペース ナビゲーターに、同じ名前の新しいデータセットおよびレポートが表示されます。

Power BI Desktop から発行すると、Power BI で **[データの取得]** を使用して接続し、Power BI Desktop ファイルをアップロードした場合と同じ効果を得られます。

> [!NOTE]
> Power BI でどのような変更をレポートに加えても、元の Power BI Desktop ファイルには保存されません。 これには、レポートで視覚化を追加、削除、または変更した場合が含まれます。
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Power BI Desktop データセットおよびレポートを発行するには
1. Power BI Desktop で、 **[ファイル]** \> **[発行]** \> **[Power BI へ発行]** を選択するか、リボンの **[発行]** を選択します。  

   ![[発行] ボタン](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Power BI にサインインします。
3. 発行先を選択します。

   ![発行先を選択する](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

発行が完了すると、レポートのリンクを受け取ります。 リンクを選択し、Power BI サイトでレポートを開きます。

![発行の完了を伝えるダイアログ](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="republish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Power BI Desktop から発行されたデータセットの再発行または置換
Power BI Desktop ファイルを発行すると、Power BI Desktop で作成したデータセットとすべてのレポートが Power BI サイトにアップロードされます。 Power BI Desktop ファイルを再発行すると、Power BI サイト内のデータセットが、Power BI Desktop ファイルから取得された更新済みデータセットと置き換えられます。

このプロセスは簡単ですが、いくつかの点について理解しておく必要があります。

* Power BI Desktop ファイルと同じ名前のデータセットが Power BI 内に複数あると、発行が失敗する可能性があります。 同じ名前のデータセットが Power BI に 1 つだけ存在するようにしてください。 ファイルの名前を変更して発行することもでき、その場合はファイルと同じ名前の新しいデータセットが作成されます。
* 列またはメジャーの名前を変更するか、これらを削除すると、Power BI でそのフィールドを使用している既存の視覚化が壊れる可能性があります。 
* Power BI は、既存列の形式変更の一部を無視します。 たとえば、列の形式を 0.25% から 25% に変更した場合などです。
* Power BI の既存のデータセット用に構成された更新スケジュールがあるとします。 ファイルに新しいデータ ソースを追加してから再発行する場合は、次にスケジュールされている更新の前に、それらにサインインしておく必要があります。
* Power BI Desktop から発行されたデータセットを再発行し、定義された更新スケジュールがある場合、再発行後すぐにデータセットの更新が開始されます。 

