---
title: Power BI のオンプレミス ゲートウェイを管理する
description: Power BI でオンプレミスのデータに接続できるようにゲートウェイを管理する方法を説明します。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 04/18/2018
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Gateways
ms.openlocfilehash: 8acc0e403c983de79657cd01a7aa7f458bfb01ad
ms.sourcegitcommit: 9278540467765043d5cb953bcdd093934c536d6d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559064"
---
# <a name="manage-a-power-bi-on-premises-gateway"></a>Power BI のオンプレミス ゲートウェイを管理する

[Power BI データ ゲートウェイをインストール](service-gateway-install.md)したら、要件に基づいてこれを管理します。 このトピックでは、データ ソースとユーザーを追加および削除する方法、ゲートウェイを再起動する方法、ゲートウェイを移行、復元、引き継ぎ、および削除する方法について説明します。

Power BI サービスの **[ゲートウェイの管理]** 領域を通して、ローカル コンピューター上のゲートウェイ アプリで PowerShell スクリプトを使用してゲートウェイを管理できます。 この記事では、Power BI サービスを中心に説明します。

ゲートウェイをインストールした直後であれば、[データ ソースの追加](#add-a-data-source)と[ユーザーの追加](#add-users-to-a-data-source)を行って、ユーザーがデータ ソースにアクセスできるようにすることをお勧めします。


## <a name="manage-data-sources"></a>データ ソースを管理する

Power BI は、多数のオンプレミス データ ソースをサポートしますが、各データ ソースには独自の要件があります。 ゲートウェイは、単一のデータ ソースにも複数のデータ ソースにも使用できます。 この例では、SQL Server をデータ ソースとして 追加する方法を示しますが、他のデータ ソースも手順は類似しています。

> [!NOTE]
> ゲートウェイの管理者は、それぞれが別の資格情報を持つ、同じソースに接続される複数のデータ ソースを作成し、ユーザーのアクセス レベルに基づいてこれらのデータ ソースを各ユーザーを追加できるようになりました。

### <a name="add-a-data-source"></a>データ ソースの追加

1. Power BI サービスの右上にある歯車アイコン ![[設定] 歯車アイコン](media/service-gateway-manage/icon-gear.png) >  **[ゲートウェイの管理]** の順に選択します。

    ![ゲートウェイの管理](media/service-gateway-manage/manage-gateways.png)

1. ゲートウェイを選択し、 **[データ ソースの追加]** を選択するか、[ゲートウェイ] > **[データ ソースの追加]** に移動します。

    ![データ ソースの追加](media/service-gateway-manage/add-data-source.png)

1. **データ ソースの種類**を選択します。

    ![SQL Server の選択](media/service-gateway-manage/select-sql-server.png)


1. データ ソースの情報を入力します。 この例では、**サーバー**、**データベース**、およびその他の情報です。  

    ![データ ソース設定](media/service-gateway-manage/data-source-settings.png)

1. SQL Server では、 **[認証方法]** で **[Windows]** または **[基本]** (SQL 認証) を選択します。  **[基本]** を選択した場合は、データ ソースの資格情報を入力します。

1. 現在、このデータ ソースを利用できない場合、または低速である場合、 **[テスト接続をスキップする]** を選択します。 そのようにしない場合、データ ソースの作成が失敗する可能性があります。

    > [!NOTE]
    > Analysis Services では、テスト接続のスキップはサポートされていません。

1. **[詳細設定]** で、必要に応じてデータ ソースの[プライバシー レベル](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)を構成します ([DirectQuery](desktop-directquery-about.md) には適用されません)。

    ![詳細設定](media/service-gateway-manage/advanced-settings.png)

1. **[追加]** を選択します。 接続に成功すると、「"*接続成功*"」というメッセージが表示されます。

    ![接続成功](media/service-gateway-manage/connection-successful.png)

これで、このデータ ソースを使用して、Power BI ダッシュボードとレポートに SQL Server のデータを含めることができます。

### <a name="remove-a-data-source"></a>データ ソースの削除

データ ソースを使用しなくなった場合は、それを削除できます。 データ ソースを削除すると、そのデータ ソースに依存するすべてのダッシュボードやレポートが壊れることに注意してください。

データ ソースを削除するには、データ ソースに移動し、 **[削除]** を選択します。

![データ ソースの削除](media/service-gateway-manage/remove-data-source.png)


## <a name="manage-users-and-administrators"></a>ユーザーと管理者を管理する

データ ソースをゲートウェイに追加した後、ユーザーとメールが有効なセキュリティ グループに (ゲートウェイ全体ではなく) 特定のデータ ソースへのアクセス権を与えます。 データ ソースのユーザーの一覧は、データ ソースのデータが含まれるレポートを発行できるユーザーを制御します。 レポートの所有者は、ダッシュボード、コンテンツ パック、およびアプリを作成し、それらを他のユーザーと共有できます。

ゲートウェイへの管理アクセス権をユーザーとセキュリティ グループに与えることもできます。


### <a name="add-users-to-a-data-source"></a>データ ソースへのユーザーの追加

1. Power BI サービスの右上隅で、歯車アイコン ![[設定] 歯車アイコン](media/service-gateway-manage/icon-gear.png) >  **[ゲートウェイの管理]** を選択します。

2. ユーザーを追加するデータ ソースを選択します。

3. **[ユーザー]** を選択し、選択したデータ ソースへのアクセス権を与える組織のユーザーを入力します。 次の画面では、Maggie と Adam が追加されています。

    ![[ユーザー] タブ](media/service-gateway-manage/users-tab.png)

4. **[追加]** を選択します。追加されたメンバーがボックスに表示されます。

    ![ユーザーの追加](media/service-gateway-manage/add-user.png)

これで完了です。 アクセスを与えるデータ ソースごとにユーザーを追加する必要があります。 各データ ソースには、別個のユーザー リストがあります。データ ソースごとにユーザーを追加する必要があります。


### <a name="remove-users-from-a-data-source"></a>データ ソースからのユーザーの削除

データ ソースの **[ユーザー]** タブで、このデータ ソースを使用できるユーザーまたはメールが有効なセキュリティ グループを削除できます。

![ユーザーの削除](media/service-gateway-manage/remove-user.png)


### <a name="add-and-remove-administrators"></a>管理者の追加と削除

ゲートウェイの **[管理者]** タブで、ゲートウェイを管理できるユーザー (またはメールが有効なセキュリティ グループ) の追加と削除を実行できます。

![[管理者] タブ](media/service-gateway-manage/administrators-tab.png)


## <a name="manage-a-gateway-cluster"></a>ゲートウェイ クラスターを管理する

2 つ以上のゲートウェイがあるクラスターを作成した場合は、すべてのゲートウェイ管理オプション (データ ソースの追加やゲートウェイへの管理アクセス許可の付与など) が、クラスターの一部であるすべてのゲートウェイに適用されます。 

管理者が **Power BI サービス**の歯車アイコンの下にある **[ゲートウェイの管理]** メニュー項目を使用するときに、登録済みクラスターまたは個々のゲートウェイのリストが表示されますが、クラスターのメンバーである個々のゲートウェイ インスタンスは表示されません。

新しい**スケジュールされている更新**要求と DirectQuery 操作はすべて、指定されたゲートウェイ クラスターのプライマリ インスタンスに自動的にルーティングされます。 プライマリ ゲートウェイ インスタンスがオンラインでない場合、要求はクラスターの別のゲートウェイ インスタンスにルーティングされます。


## <a name="share-a-gateway"></a>ゲートウェイの共有

ゲートウェイを "*共有*" することは本質的にできませんが、ゲートウェイに管理者を追加したり、ゲートウェイのデータ ソースにユーザーを追加したりできます。 

ゲートウェイをインストールすると、既定ではご自身がゲートウェイの管理者となります。 前述のように、他のユーザーを管理者として追加できます。 これらの管理者は、データ ソースの追加や、ゲートウェイの構成や削除を行えます。

また、各ゲートウェイの下に作成したデータ ソースにユーザーを割り当てることもできます。 ユーザーはそのデータ ソースを使用して、Power BI レポートを更新できます。 ただし、ユーザーはデータ ソースまたはゲートウェイの設定を変更できません。

## <a name="migrate-restore-or-take-over-a-gateway"></a>ゲートウェイの移行、復元、または引き継ぎを行う

ゲートウェイの移行、復元、または引き継ぎを行うコンピューターで、ゲートウェイ インストーラーを実行します。

1. ゲートウェイをダウンロードしてインストールします。

2. Power BI アカウントにサインインした後、ゲートウェイを登録します。 **[Migrate, restore or take over an existing gateway]/(既存のゲートウェイの移行、復元、または引き継ぎ/)**  >  **[次へ]** を選択します。

    ![ゲートウェイの登録](media/service-gateway-manage/register-gateway.png)

3. 利用可能なクラスターとゲートウェイから選択し、選択したゲートウェイのリカバリ キーを入力します。 **[構成]** を選択します。

    ![移行、復元、または引き継ぎ](media/service-gateway-manage/migrate-restore-takeover.png)


## <a name="restart-a-gateway"></a>ゲートウェイを再起動する

ゲートウェイは Windows サービスとして実行されます。 他の Windows サービスと同じように、その開始と停止の方法は複数あります。 コマンド プロンプトを使用する方法を次に示します。

1. ゲートウェイが実行されているコンピューターで、管理者権限でコマンド プロンプトを起動します。

2. サービスを停止するには `net stop PBIEgwService` を入力します。

3. サービスを再起動するには `net start PBIEgwService` を入力します。


## <a name="remove-a-gateway"></a>ゲートウェイの削除

ゲートウェイを使用しなくなった場合は、それを削除できます。 ただし、ゲートウェイを削除すると、追加されたすべてのデータ ソースも削除されることに注意してください。 これにより、それらのデータ ソースに依存しているダッシュボードとレポートが壊れます。

1. Power BI サービスの右上隅で、歯車アイコン ![[設定] 歯車アイコン](media/service-gateway-manage/icon-gear.png) >  **[ゲートウェイの管理]** を選択します。

2. ゲートウェイを選択し、 **[削除]** を選択します。
   
   ![ゲートウェイの削除](media/service-gateway-manage/remove-gateway.png)


## <a name="next-steps"></a>次の手順

[データ ゲートウェイの展開に関するガイダンス](service-gateway-deployment-guidance.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。
