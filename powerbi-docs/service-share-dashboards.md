---
title: 同僚や他のユーザーと Power BI ダッシュボードやレポートを共有する
description: 組織内の同僚や組織外の他のユーザーと Power BI ダッシュボードやレポートを共有する方法と、共有について知っておく必要があること。
author: maggiesMSFT
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/19/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 05a134f50f9a09ae5b51578a5e4e5f0a01a95740
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871505"
---
# <a name="share-power-bi-dashboards-and-reports-with-coworkers-and-others"></a>同僚や他のユーザーと Power BI ダッシュボードやレポートを共有する
"*共有*" は、自分のダッシュボードおよびレポートに他のユーザーがアクセスできるようにするのによい方法です。 Power BI では、[複数の異なる方法でダッシュボードでの共同作業を行ったり、ダッシュボードやレポートを配布](service-how-to-collaborate-distribute-dashboards-reports.md)したりできます。

![ダッシュボードの一覧での共有アイコン](media/service-share-dashboards/power-bi-share-new-look.png)

共有を行うには、コンテンツの共有先が組織内でも組織外でも、共有元に [Power BI Pro ライセンス](service-features-license-type.md)が必要です。 コンテンツが [Premium 容量](service-premium-what-is.md)にない限り、受信者には Power BI Pro ライセンスも必要です。 

Power BI サービスのほとんどの場所からダッシュボードとレポートを共有できます:[お気に入り]、[最近使った項目]、[自分と共有] (所有者が許可している場合)、[マイ ワークスペース]、またはその他のワークスペース。 ダッシュボードやレポートを共有する場合、共有した相手はそれを表示して操作することはできますが、編集することはできません。 [行レベル セキュリティ (RLS)](service-admin-rls.md) を適用しない限り、自分のダッシュボードやレポートに表示されるものと同じデータが同僚にも表示されます。 共有元のユーザーが許可した場合、共有先のユーザーも同僚と共有できます。 組織外のユーザーも、ダッシュボードやレポートを表示して操作することはできますが、それを共有することはできません。 

Power BI Desktop からダッシュボードを共有することはできません。 しかし、[任意の Power BI モバイル アプリからダッシュボードを共有](consumer/mobile/mobile-share-dashboard-from-the-mobile-apps.md)できます。  

## <a name="video-share-a-dashboard"></a>ビデオ:ダッシュボードの共有
Amanda が社内および社外の同僚とダッシュボードを共有する様子をご覧ください。 その後、ビデオで説明されている手順に従って、ご自分でやってみてください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/0tUwn8DHo3s?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="share-a-dashboard-or-report"></a>ダッシュボードまたはレポートを共有する

1. ダッシュボードかレポートの一覧、または開いているダッシュボードかレポート内で、 **[共有]** ![共有アイコン](media/service-share-dashboards/power-bi-share-icon.png)を選択します。

2. 上部のボックスに、個々のユーザーの完全なメール アドレス、配布グループ、またはセキュリティ グループを入力します。 動的配布リストと共有することはできません。 
   
   アドレスが組織外のユーザーとも共有できますが、警告が表示されます。
   
   ![外部共有に関する警告](media/service-share-dashboards/power-bi-share-dialog-warning.png) 
 
   >[!NOTE]
   >入力ボックスでは、最大 100 のユーザーまたはグループがサポートされます。 多数のユーザーと共有する必要がある場合は、ワークスペースでダッシュボードを作成し、[アプリとしてそれを配布する](service-create-distribute-apps.md)ことを検討してください。
   > 
   > 


3. 必要な場合はメッセージを追加します。 これはオプションです。
4. 同僚が他のユーザーとコンテンツを共有できるようにするには、 **[受信者がダッシュボードを共有できるようにする] または [受信者がレポートを共有できるようにする]** をオンにします。
   
   他のユーザーに共有を許可することを "*再共有*" と呼びます。 共有を許可すると、そのユーザーは Power BI サービスやモバイル アプリから再共有したり、組織内の他のユーザーにメール招待状を転送したりできます。 招待状は 1 か月後に期限が切れます。 組織外のユーザーは、再共有を行えません。 コンテンツの所有者として、再共有を無効にしたり、再共有を個別に取り消したりできます。 「[共有または他のユーザーによる再共有を停止する](#stop-sharing-or-stop-others-from-sharing)」を参照してください。

5. **[基になるデータセットからの新しいコンテンツのビルドをユーザーに許可します]** を選択すると、このダッシュボードのデータセットに基づいて、他のワークスペースに独自のレポートを作成できます。

1. **[共有]** を選択します。
   
   ![[共有] ボタンを選ぶ](media/service-share-dashboards/power-bi-share-dialog-share.png)  
   
   Power BI によって、共有コンテンツへのリンクを含むメール招待状が、グループではなく個人に送信されます。 **[成功]** 通知が表示されます。 
   
   組織内の受信者がリンクをクリックすると、Power BI はダッシュボードまたはレポートをそのユーザーの **[自分と共有]** リスト ページに追加します。 ユーザーが自分の名前を選択すると、そのユーザーと自分とで共有されているすべてのコンテンツが表示されます。 
   
   ![[自分と共有] リスト ページ](media/service-share-dashboards/power-bi-shared-with-me-new-look.png)
   
   組織外の受信者がリンクをクリックすると、ダッシュボードまたはレポートが表示されますが、通常の Power BI ポータルではありません。 詳細については、「[組織外のユーザーとダッシュボードまたはレポートを共有する](#share-a-dashboard-or-report-outside-your-organization)」を参照してください。

## <a name="see-who-has-access-to-a-dashboard-or-report"></a>ダッシュボードまたはレポートへのアクセス権があるユーザーを確認する
場合によっては、自分が共有している相手や、その相手が共有しているユーザーを確認する必要があります。

1. ダッシュボードかレポートの一覧、またはダッシュボードかレポート自体で、 **[共有]** ![共有アイコン](media/service-share-dashboards/power-bi-share-icon.png) を選びます。 
2. **[ダッシュボードの共有]** または **[レポートの共有]** ダイアログ ボックスで、 **[アクセス]** を選びます。
   
    ![[ダッシュボードの共有] ダイアログ ボックスの [アクセス] タブ](media/service-share-dashboards/power-bi-share-dialog-access.png)

    組織外のユーザーは、 **[ゲスト]** として一覧に含められます。

## <a name="stop-sharing-or-stop-others-from-sharing"></a>共有または他のユーザーによる再共有を停止する
再共有をオンおよびオフにできるのは、ダッシュボードまたはレポートの所有者のみです。

### <a name="if-you-havent-sent-the-sharing-invitation-yet"></a>共有の招待をまだ送信していない場合
* 招待を送信する前に、招待の下部にある **[受信者がダッシュボードを共有できるようにする] または [受信者がレポートを共有できるようにする]** チェック ボックスをオフにします。

### <a name="if-youve-already-shared-the-dashboard-or-report"></a>ダッシュボードまたはレポートを既に共有している場合
1. ダッシュボードかレポートの一覧、またはダッシュボードかレポート自体で、 **[共有]** ![共有アイコン](media/service-share-dashboards/power-bi-share-icon.png) を選びます。 
2. **[ダッシュボードの共有]** または **[レポートの共有]** ダイアログ ボックスで、 **[アクセス]** を選びます。
   
    ![[ダッシュボードの共有] ダイアログ ボックスの [アクセス] タブ](media/service-share-dashboards/power-bi-share-dialog-access.png)
3. **[読み取りと共有し直し]** の横にある省略記号 **[...]** をクリックして、以下を選択します。
   
   ![[読み取りと共有し直し] の省略記号](media/service-share-dashboards/power-bi-change-access.png)
   
   * そのユーザーが他のユーザーと共有できないようにするには、 **[読み取り]** を選びます。
   * そのユーザーが共有されたコンテンツをまったく表示できないようにするには、 **[アクセスの削除]** を選びます。

4. **[アクセス許可の削除]** ダイアログ ボックスで、レポートやデータセットなど、関連するコンテンツへのアクセスも削除するかどうかを決定します。 警告アイコン ![Power BI の警告アイコン](media/service-share-dashboards/power-bi-warning-icon.png) が付いた項目を削除する場合、関連するコンテンツは正しく表示されなくなるため、それも削除することをお勧めします。

    ![Power BI の共有に関する警告ダイアログ ボックス](media/service-share-dashboards/power-bi-sharing-warning-dialog.png)

## <a name="share-a-dashboard-or-report-outside-your-organization"></a>組織外でダッシュボードまたはレポートを共有する
組織外のユーザーと共有すると、共有相手は共有されたダッシュボードまたはレポートへのリンクを含むメールを受け取ります。共有相手は、それを表示するために Power BI にサインインする必要があります。 Power BI Pro ライセンスがない共有相手は、リンクをクリックした後でライセンスにサインアップできます。

サインイン後に、共有されたダッシュボードまたはレポートが、通常の Power BI ポータルではなく、独自のブラウザー ウィンドウに表示されます。 後でこのダッシュボードまたはレポートにアクセスするには、リンクをブックマークする必要があります。

共有相手は、このダッシュボードまたはレポートのコンテンツを編集できません。 グラフを操作し、フィルターやスライサーを変更することはできますが、その変更を保存することはできません。 

共有されたダッシュボードまたはレポートを表示できるのは、直接の共有相手だけです。 たとえば、Vicki@contoso.com にメールを送信した場合、ダッシュボードを見ることができるのは Vicki だけです。 リンクがある場合でも、誰もダッシュボードを表示することはできません。 Vicki は、同じメール アドレスを使用してそれにアクセスする必要があります。誰かが他のメール アドレスでサインアップした場合、ダッシュボードにアクセスすることはできません。

オンプレミスの Analysis Services の表形式モデルでロール レベルまたは行レベルのセキュリティが実装されている場合、組織外のユーザーはデータを何も表示できません。

Power BI モバイル アプリから組織外のユーザーにリンクを送信した場合、そのリンクをクリックすると、ダッシュボードは Power BI モバイル アプリではなくブラウザーで開きます。

[外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可](service-admin-portal.md#export-and-sharing-settings)した場合、既定の使用のみのエクスペリエンスは適用されません。 [詳細情報](service-admin-azure-ad-b2b.md)

## <a name="limitations-and-considerations"></a>制限事項と考慮事項
ダッシュボードとレポートの共有について留意すべき事項:

* 一般に、自分と同僚はダッシュボードまたはレポート内の同じデータを表示することになります。 そのため、自分の方がより多くのデータを表示できるアクセス許可を持っている場合、相手はこちらのダッシュボードまたはレポートのすべてのデータを表示できることになります。 ただし、ダッシュボードまたはレポートの基になるデータセットに[行レベル セキュリティ (RLS)](service-admin-rls.md) が適用されている場合は、各ユーザーの資格情報を使用して各々がアクセスできるデータが決定されます。
* ダッシュボードのすべての共有相手は、[読み取りビュー](consumer/end-user-reading-view.md#reading-view)で表示し、関連するレポートを操作できます。 同僚はレポートを作成したり、既存のレポートへの変更を保存したりすることはできません。
* データセットを表示またはダウンロードすることはできませんが、Excel で分析機能を使ってデータセットに直接アクセスすることはできます。 管理者は、グループ内の全員に対して、Excel で分析を使う機能を制限できます。 ただし、これはそのグループ内の全員に対して、そのグループが属しているすべてのワークスペースに対して制限されます。
* [データの更新](refresh-data.md)はだれでも手動で行えます。
* 電子メールに Office 365 を使用している場合は、配布グループに関連付けられた電子メール アドレスを入力することにより、配布グループのメンバーと共有できます。
* メール ドメインを共有している同僚と、ドメインが異なっていても同じテナント内に登録されている同僚は、他のユーザーとダッシュボードを共有できます。 たとえば、ドメイン contoso.com と contoso2.com が同じテナントに登録されていて、メール アドレスが konrads@contoso.com である場合、ravali@contoso.com と gustav@contoso2.com に共有のアクセス許可が付与されていれば、両方で共有できます。
* 同僚が既に特定のダッシュボードまたはレポートにアクセスできる場合は、ダッシュボードまたはレポートを使用しているときに URL をコピーすることで、直接リンクを送信できます。 例: `https://powerbi.com/dashboards/g12466b5-a452-4e55-8634-xxxxxxxxxxxx`
* 同様に、同僚が特定のダッシュボードに既にアクセスできる場合は、[基になるレポートへの直接リンクを送信する](service-share-reports.md)ことができます。 
* 1 回の共有アクションで、最大 100 のユーザーまたはグループと共有できます。 ただし、項目へのアクセス権は、500 を超えるユーザーに付与できます。 これを行う場合は、ユーザーを個々に指定して複数回共有するか、すべてのユーザーを含むユーザー グループと共有します。

## <a name="troubleshoot-sharing"></a>共有のトラブルシューティング

### <a name="my-dashboard-recipients-see-a-lock-icon-in-a-tile-or-a-permission-required-message"></a>ダッシュボードの受信者に、タイルまたは「アクセス許可が必要」のメッセージにロック アイコンが表示される

共有相手がレポートを表示しようとしたときに、ダッシュボードにロックされたタイルが表示されたり、"アクセス許可が必要です" というメッセージが表示されたりすることがあります。

![Power BI のロックされたタイル](media/service-share-dashboards/power-bi-locked_tile_small.png)

その場合は、基になるデータセットへのアクセス許可を付与する必要があります。

1. コンテンツ リストの **[データセット]** タブに移動します。

1. データセットの横にある省略記号 ( **...** ) を選択してから、 **[アクセス許可の管理]** を選びます。

    ![アクセス許可の管理](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. **[ユーザーの追加]** を選びます。

    ![[ユーザーの追加] を選択](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. 個々のユーザーの完全なメール アドレス、配布グループ、またはセキュリティ グループを入力します。 動的配布リストと共有することはできません。

    ![メール アドレスの追加](media/service-share-dashboards/power-bi-add-user-dataset.png)


1. **[追加]** を選択します。

### <a name="i-cant-share-a-dashboard-or-report"></a>ダッシュボードまたはレポートを共有できない

ダッシュボードまたはレポートを共有するには、基になるコンテンツ (つまり、関連するすべてのレポートやデータセット) を再共有するためのアクセス許可が必要です。 共有できないというメッセージが表示された場合は、レポートの作成者に、それらのレポートおよびデータセットを再共有するアクセス許可を依頼してください。

!["共有できません" メッセージ](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)


## <a name="next-steps"></a>次の手順
* ご意見およびご提案がある場合は、 [Power BI コミュニティ サイト](https://community.powerbi.com/)をご利用ください。
* [ダッシュボードとレポートを共有する方法](service-how-to-collaborate-distribute-dashboards-reports.md)
* [フィルター処理された Power BI レポートを共有する](service-share-reports.md)。
* わからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

