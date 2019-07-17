---
title: Power BI 管理ポータル
description: 管理ポータルを使用して、組織内の Power BI のテナントを管理できます。 利用状況の指標、Microsoft 365 管理センターへのアクセス、設定などの項目があります。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/27/2019
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: a871a7475dd8282f9ce63646c371182548504357
ms.sourcegitcommit: b439ded53bfbbb58be27ecedf93d618f5158df33
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2019
ms.locfileid: "67568142"
---
# <a name="administering-power-bi-in-the-admin-portal"></a>管理ポータルでの Power BI の管理

管理ポータルを使用すると、組織の Power BI "*テナント*" を管理できます。 ポータルには、利用状況の指標、Microsoft 365 管理センターへのアクセス、設定などの項目が含まれています。

完全な管理ポータルには、Office 365 のグローバル管理者であるか、Power BI サービス管理者の役割が割り当てられているすべてのユーザーがアクセスできます。 これらの役割のいずれも割り当てられていない場合、表示できるのはポータルの **[容量の設定]** のみです。 Power BI サービス管理者の役割の詳細については、「[Power BI 管理者の役割について](service-admin-role.md)」を参照してください。

## <a name="how-to-get-to-the-admin-portal"></a>管理ポータルにアクセスする方法

Power BI の管理ポータルにアクセスするには、アカウントが Office 365 または Azure Active Directory 内で **[グローバル管理者]** とマークされているか、Power BI サービス管理者の役割が割り当てられている必要があります。 Power BI サービス管理者の役割の詳細については、「[Power BI 管理者の役割について](service-admin-role.md)」を参照してください。 Power BI 管理ポータルにアクセスするには、次のように操作します。

1. Power BI サービスの右上にある設定アイコン (歯車) を選択します。

1. **[管理ポータル]** を選択します。

    ![管理ポータルの設定](media/service-admin-portal/powerbi-admin-settings.png)

ポータルには 9 つのタブがあります。 この記事の残りの部分では、これらの各タブについて説明します。

![管理ポータルのナビゲーション](media/service-admin-portal/powerbi-admin-landing-page.png)

* [利用状況の指標](#usage-metrics)
* [ユーザー](#users)
* [監査ログ](#audit-logs)
* [テナント設定](#tenant-settings)
* [容量の設定](#capacity-settings)
* [埋め込みコード](#embed-codes)
* [組織のビジュアル](#organizational-visuals)
* [データフロー ストレージ (プレビュー)](#dataflowStorage)
* [ワークスペース](#workspaces)

## <a name="usage-metrics"></a>利用状況の指標

**[利用状況の指標]** を使用すると、組織の Power BI の使用状況を監視することができます。 また、組織のどのユーザーやグループが Power BI を最もアクティブに使用しているかを確認することもできます。 

> [!NOTE]
> ダッシュボードに初めてアクセスした場合、またはダッシュボードを長期間表示しなかった後でもう一度アクセスした場合は、ダッシュボードを読み込んでいる間、読み込み中画面が表示される可能性があります。

ダッシュボードが読み込まれると、タイルのセクションが 2 つ表示されます。 最初のセクションには個々のユーザーの利用状況データが、2 番目のセクションには組織内のグループについての同様の情報が含まれます。

各タイルに表示される内容の詳細は次のとおりです。

* ユーザー ワークスペース内のすべてのダッシュ ボード、レポート、およびデータセットの重複しない数。
  
    ![ダッシュボード、レポート、データセットの重複しない数](media/service-admin-portal/powerbi-admin-usage-metrics-number-tiles.png)

* アクセス可能ユーザー数別の最も使用されたダッシュボード。 たとえば、3 人のユーザーと共有しているダッシュ ボードがあるときに、別の 2 人のユーザーに接続されているコンテンツ パックにそのダッシュボードを追加した場合、数値は 6 になります (1 + 3 + 2)。
  
    ![最も使用されたダッシュボード](media/service-admin-portal/powerbi-admin-usage-metrics-top-dashboards.png)

* ユーザーが最も接続しているコンテンツ。 これは、データ取得処理によってユーザーがアクセスできるコンテンツであり、SaaS コンテンツ パック、組織のコンテンツ パック、ファイル、またはデータベースになります。
  
    ![最も使用されたパッケージ](media/service-admin-portal/powerbi-admin-usage-metrics-top-connections.png)

* 所有しているダッシュボードの数 (自分で作成したダッシュボードと共有しているダッシュ ボードの両方) に基づく上位ユーザー ビュー。
  
    ![上位ユーザー - ダッシュボード](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-dashboards.png)

* 所有しているレポートの数に基づく上位ユーザー ビュー。
  
    ![上位ユーザー - レポート](media/service-admin-portal/powerbi-admin-usage-metrics-top-users-reports.png)

2 番目のセクションでは、同じ種類の情報が表示されますが、そのデータは (ユーザーではなく) グループに基づいています。 これにより、組織のどのグループが最もアクティブであり、どのようなコンテンツを使用しているかを確認できます。

これらの情報によって、組織全体のユーザーとグループが Power BI をどのように使用しているかについてリアルな洞察を得ることができ、組織内の非常にアクティブなユーザーとグループを認識できます。

## <a name="control-usage-metrics"></a>利用状況の指標の制御

利用状況の指標レポートは、Power BI または Office 365 の管理者が、オンまたはオフにすることができる機能です。 管理者は、どのユーザーが利用状況の指標にアクセスできるかを細く制御できます。 これらは、組織内のすべてのユーザーに対して既定で**オン**になります。

管理者は、コンテンツ作成者が利用状況の指標内のユーザーごとのデータを参照できるかどうかも決定できます。 

レポート自体の詳細については、「[Power BI のダッシュボードとレポートの利用状況の指標を監視する](service-usage-metrics.md)」を参照してください。

### <a name="usage-metrics-for-content-creators"></a>コンテンツ作成者用の使用状況メトリック

1. 管理ポータルで、 **[テナント設定]**  >  **[コンテンツ作成者用の使用状況メトリック]** を選択します。

    ![管理者ポータルのテナント設定の利用状況の指標](media/service-admin-portal/power-bi-admin-usage-metrics.png)

1. 利用状況の指標を有効 (または無効) にして、 **[適用]** を選択します。

    ![有効になった利用状況指標](media/service-usage-metrics/power-bi-tenant-settings-updated.png)


### <a name="per-user-data-in-usage-metrics"></a>利用状況の指標内のユーザーごとのデータ

既定では、ユーザーごとのデータは利用状況の指標に対して有効であり、コンテンツ コンシューマーのアカウント情報は指標レポートに含まれます。 一部またはすべてのユーザーに対してこの情報を含めない場合は、指定したセキュリティ グループまたは組織全体に対してこの機能を無効にします。 アカウント情報は、 *[名前なし]* としてレポートに表示されます。

![ユーザーごとの利用状況データ](media/service-admin-portal/power-bi-admin-per-user-usage-data.png)

### <a name="delete-all-existing-usage-metrics-content"></a>既存のすべての利用状況の指標コンテンツを削除する

組織全体に対して利用状況の指標を無効にする場合、管理者は次の一方または両方のオプションを選択できます。

- **[既存のすべての使用状況メトリック コンテンツを削除します]** では、利用状況の指標のレポートとデータセットを利用して構築された既存のレポートとダッシュボード タイルがすべて削除されます。 このオプションで、組織の全ユーザーを対象に、既に利用している場合でも、使用状況指標データの全アクセスが削除されます。 
- **[現在の使用状況のメトリック コンテンツ内の既存のユーザーごとのデータすべてを削除します]** 。このオプションでは、組織内の全ユーザーを対象に、既に利用している場合でも、ユーザーごとのデータへのアクセス権がすべて削除されます。 

削除した既存の利用状況の指標コンテンツとユーザーごとの指標コンテンツは元に戻せないので注意が必要です。

## <a name="users"></a>Users

Microsoft 365 管理センターで Power BI のユーザー、グループ、管理者を管理します。 **[ユーザー]** タブには、テナントの管理センターへのリンクが含まれています。

![Microsoft 365 管理センターに移動](media/service-admin-portal/powerbi-admin-manage-users.png)

## <a name="audit-logs"></a>監査ログ

Office 365 セキュリティ/コンプアライアンス センターで Power BI 監査ログを管理します。 **[監査ログ]** タブには、テナントのセキュリティ/コンプアライアンス センターへのリンクが含まれています。 [詳細情報](service-admin-auditing.md)

監査ログを使用するには、設定 [ **[内部アクティビティの監査とコンプライアンスのための監査ログの作成]** ](#create-audit-logs-for-internal-activity-auditing-and-compliance) を有効にします。

## <a name="tenant-settings"></a>テナント設定

**[テナント設定]** タブを使うと、組織で利用できる機能をきめ細かく制御できます。 機密データに関して懸念がある場合、一部の機能がお客様の組織に適していない場合や、特定の機能を特定のグループのみが使用できるようにする必要がある場合があります。

**[テナント設定]** タブの最初の 2 つのセクションを次の図に示します。

![テナント設定](media/service-admin-portal/powerbi-admin-tenant-settings.png)

> [!NOTE]
> テナントのすべてのユーザーに対して設定の変更が有効になるには、最大で 10 分かかることがあります。

次の 3 つの状態を設定できます。

* **組織全体に対して無効にする**:組織内の誰もこの機能を使用できません。

    ![すべて無効にする設定](media/service-admin-portal/powerbi-admin-tenant-settings-disabled.png)

* **組織全体に対して有効にする**:組織内の誰でもこの機能を使用できます。

    ![すべて有効にする設定](media/service-admin-portal/powerbi-admin-tenant-settings-enabled.png)

* **組織のサブセットに対して有効にする**:組織のユーザーまたはグループの特定のサブセットがこの機能を使用できます。

    特定のユーザーのグループを除いて、組織全体に対して機能を有効にすることができます。

    ![サブセットを有効にする設定](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except.png)

    特定のユーザーのグループのみに対して機能を有効にすることも、ユーザーのグループに対して機能を無効にすることもできます。 この方法を使用すると、特定のユーザーが許可されているグループに属している場合でも、その機能へのアクセス権を持たないようにすることができます。

    ![一部を除いて有効にする設定](media/service-admin-portal/powerbi-admin-tenant-settings-enabled-except2.png)

次のいくつかのセクションでは、さまざまな種類のテナント設定の概要を示します。

## <a name="help-and-support-settings"></a>ヘルプとサポートの設定

### <a name="publish-get-help-information"></a>[ヘルプを表示] の情報を公開する

組織内のユーザーは、Power BI のヘルプ メニューから、内部のヘルプおよびサポート リソースにアクセスできます。 具体的には、これらのパラメーターにより、[詳細]、[コミュニティ]、[ヘルプを表示] の各メニュー項目の動作を変更します。

また、ライセンス要求に対して、ユーザーをカスタム ソリューションに誘導する URL を指定することもできます。 このパラメーターにより、[アカウントのアップグレード] ボタンのターゲット URL をカスタマイズします。これは、Power BI Pro のライセンスを持たないユーザーに対して、Power BI Pro への更新ダイアログ ボックスおよび [パーソナル ストレージの管理] ページで表示されます。

## <a name="workspace-settings"></a>ワークスペースの設定

### <a name="create-workspaces"></a>ワークスペースを作成する

管理者は、 **[Create workspaces]\(ワークスペースの作成\)** 設定を使用して、アプリ ワークスペースを作成してダッシュボード、レポート、その他のコンテンツで共同作業を行うことができる組織内のユーザーを指定します。 アプリ ワークスペースの詳細については、[こちら](service-create-the-new-workspaces.md)を参照してください。

管理ポータルには、テナント内のワークスペースに関する設定の別のセクションがあります。 そのセクションでは、ワークスペースの一覧を並べ替えたり、フィルターを適用したり、ワークスペースごとの詳細を表示したりできます。 詳細については、「[ワークスペース](#workspaces)」を参照してください。

また、管理ポータルでは、組織にアプリを配布する権限を持つユーザーを制御することもできます。 詳細については、この記事の「[コンテンツ パックとアプリを組織全体に発行する](#publish-content-packs-and-apps-to-the-entire-organization)」を参照してください。

## <a name="export-and-sharing-settings"></a>エクスポートと共有の設定

### <a name="share-content-with-external-users"></a>外部ユーザーとコンテンツを共有する

組織内のユーザーは組織外のユーザーとダッシュボードを共有できます。 [詳細情報](service-share-dashboards.md#share-a-dashboard-or-report-with-people-outside-your-organization)

![外部ユーザーの設定](media/service-admin-portal/powerbi-admin-sharing-external-02.png)

外部ユーザーと共有すると、次の図のようなメッセージが表示されます。

![外部ユーザーと共有する](media/service-admin-portal/powerbi-admin-sharing-external.png)  

### <a name="publish-to-web"></a>Web に公開

組織内のユーザーは、Web にレポートを公開することができます。 [詳細情報](service-publish-to-web.md)

**[Web に公開]** 設定を有効にした場合のレポートの **[ファイル]** メニューを次の図に示します。

![Web に公開設定](media/service-admin-portal/powerbi-admin-publish-to-web.png)

**[Web に公開]** の設定に基づき、UI にさまざまなオプションが表示されます。

|特性 |組織全体に対して有効にする |組織全体に対して無効にする |特定のセキュリティ グループ   |
|---------|---------|---------|---------|
|**[ファイル]** メニューの下の **[Web に公開]** 。|すべてのユーザーに対して有効|すべてのユーザーに対して非表示|承認されたユーザーまたはグループに対してのみ表示されます。|
|**[設定]** の下の **[埋め込みコードの管理]**|すべてのユーザーに対して有効|すべてのユーザーに対して有効|すべてのユーザーに対して有効<br><br>*  **[削除]** オプションは、承認されたユーザーまたはグループの場合にのみ使用可能です。<br>*  **[コードを取得]** は、すべてのユーザーに対して有効になります。|
|管理ポータル内の **[埋め込みコード]**|状態には次のいずれかが反映されます。<br>* アクティブ<br>* サポートされていません<br>* ブロック|状態は **[無効]** と表示|状態には次のいずれかが反映されます。<br>* アクティブ<br>* サポートされていません<br>* ブロック<br><br>ユーザーがテナント設定に基づいて承認されていない場合、状態は **[侵害]** となります。|
|既存の公開済みレポート|すべて有効|すべて無効|すべてのユーザーに対して、レポートの表示が続行されます。|

### <a name="export-data"></a>データのエクスポート

組織内のユーザーは、タイルや視覚エフェクトからデータをエクスポートできます。 [詳細情報](visuals/power-bi-visualization-export-data.md)

タイルからデータをエクスポートするためのオプションを次の図に示します。

![タイルからデータをエクスポートする](media/service-admin-portal/powerbi-admin-export-data.png)

> [!NOTE]
> また、 **[データのエクスポート]** を無効にして、ユーザーが **[Excel で分析]** 機能と、Power BI サービスのライブ接続を使用できないように設定することもできます。

### <a name="export-reports-as-powerpoint-presentations-or-pdf-documents"></a>PowerPoint プレゼンテーションまたは PDF ドキュメントとしてレポートをエクスポート

組織内のユーザーは、Power BI レポートを PowerPoint ファイルまたは PDF ドキュメントとしてエクスポートできます。 [詳細情報](consumer/end-user-powerpoint.md)

**[PowerPoint プレゼンテーションまたは PDF ドキュメントとしてレポートをエクスポート]** 設定を有効にした場合のレポートの **[ファイル]** メニューを次の図に示します。

![PowerPoint プレゼンテーションとしてレポートをエクスポート](media/service-admin-portal/powerbi-admin-powerpoint.png)

### <a name="print-dashboards-and-reports"></a>ダッシュボードとレポートの印刷

組織内のユーザーは、ダッシュボードとレポートを印刷できます。 [詳細情報](consumer/end-user-print.md)

ダッシュボードを印刷するためのオプションを次の図に示します。

![ダッシュボードの印刷](media/service-admin-portal/powerbi-admin-print-dashboard.png)

設定 **[ダッシュボードとレポートを印刷する]** を有効にした場合のレポートの **[ファイル]** メニューを次の図に示します。

![レポートを印刷する](media/service-admin-portal/powerbi-admin-print-report.png)

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する
Azure B2B ゲスト ユーザーは、組織内のコンテンツの編集および管理できます。 [詳細情報](service-admin-azure-ad-b2b.md)

次の図は、[外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する] オプションを示しています。

![外部のゲスト ユーザーによる組織内のコンテンツの編集および管理を許可する](media/service-admin-portal/powerbi-admin-tenant-settings-b2b-guest-edit-manage.png)

### <a name="email-subscriptions"></a>電子メール サブスクリプション
組織内のユーザーは電子メール サブスクリプションを作成できます。 サブスクリプションの詳細は[こちら](service-report-subscribe.md)をご覧ください。

![電子メール サブスクリプションを有効にする](media/service-admin-portal/power-bi-manage-email-subscriptions.png)

## <a name="content-pack-and-app-settings"></a>コンテンツ パックとアプリの設定

### <a name="publish-content-packs-and-apps-to-the-entire-organization"></a>コンテンツ パックとアプリを組織全体に発行する

管理者はこの設定を使用して、特定のグループだけではなく、組織全体にコンテンツ パックとアプリを発行できるユーザーを決定します。 アプリの発行の詳細は[こちら](service-create-distribute-apps.md)をご覧ください。

コンテンツ パックを作成するときの **[組織全体]** オプションを次の図に示します。

![コンテンツ パックを組織に発行する](media/service-admin-portal/powerbi-admin-publish-entire-org.png)

### <a name="create-template-apps-and-organizational-content-packs"></a>テンプレート アプリと組織のコンテンツ パックを作成する

組織内のユーザーは、Power BI Desktop 内の 1 つのデータ ソース上に構築されたデータセットを使用する、テンプレート アプリと組織のコンテンツ パックを作成できます。 テンプレート アプリの詳細は[こちら](template-content-pack-authoring.md)をご覧ください。

### <a name="push-apps-to-end-users"></a>アプリをエンド ユーザーにプッシュする

レポートの作成者は、[AppSource](https://appsource.microsoft.com) からのインストールを要求することなく、エンド ユーザーとアプリを直接共有できます。 詳細については、「[エンド ユーザーにアプリを自動的にインストールする](service-create-distribute-apps.md#automatically-install-apps-for-end-users)」を参照してください。

## <a name="integration-settings"></a>統合の設定

### <a name="ask-questions-about-data-using-cortana"></a>Cortana を使ってデータに関する質問をする

組織内のユーザーは、データについて Cortana を使って質問することができます。 [詳細情報](service-cortana-enable.md)

> [!NOTE]
> この設定は、組織全体に適用され、特定のグループに限定することはできません。

### <a name="use-analyze-in-excel-with-on-premises-datasets"></a>オンプレミスのデータセットで [Excel で分析] を使用する

組織内のユーザーは、Excel を使用して、オンプレミスの Power BI データセットの表示および操作を行うことができます。 [詳細情報](service-analyze-in-excel.md)

> [!NOTE]
> また、 **[データのエクスポート]** を無効にして、ユーザーが **[Excel で分析]** 機能を使用することを防ぐこともできます。

### <a name="use-arcgis-maps-for-power-bi"></a>ArcGIS Maps for Power BI を使用する

組織内のユーザーは、Esri が提供する ArcGIS Maps for Power BI の視覚エフェクトを使用できます。 [詳細情報](visuals/power-bi-visualization-arcgis.md)

### <a name="use-global-search-for-power-bi-preview"></a>Power BI でグローバル検索を使用する (プレビュー)

組織のユーザーには、Azure Search に依存する外部の検索機能を使用できます。 たとえば、Cortana を使用し、Power BI のダッシュボードとレポートから重要な情報を直接取得できます。 [詳細情報](service-cortana-intro.md)

## <a name="custom-visuals-settings"></a>カスタム ビジュアルの設定

### <a name="add-and-use-custom-visuals"></a>カスタム視覚化の追加と使用

組織内のユーザーは、カスタム ビジュアルを操作して共有することができます。 [詳細情報](power-bi-custom-visuals.md)

> [!NOTE]
> この設定は組織全体に適用するか、特定のグループに限定することができます。


Power BI Desktop (2019 年 3 月リリース以降) では、**グループ ポリシー**を使用して、組織内に配置されているコンピューター間でカスタム ビジュアルの使用を無効にすることができます。

<table>
<tr><th>属性</th><th>値</th>
</tr>
<td>キー</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableCustomVisuals</td>
</tr>
</table>

値が 1 (10 進数) の場合は、Power BI でカスタム ビジュアルの使用が有効になります (既定)。

値が 0 (10 進数) の場合は、Power BI でカスタム ビジュアルの使用が無効になります。

### <a name="allow-only-certified-visuals"></a>認定済みビジュアルのみを許可する

カスタム ビジュアルを追加し、使用する許可が与えられた組織のユーザー ([カスタム視覚化の追加と使用] 設定に示されています) は、[認定済みのカスタム ビジュアル](https://go.microsoft.com/fwlink/?linkid=2002010)のみを使用できます (認定のないビジュアルはブロックされ、使用すると、エラー メッセージが表示されます)。 


Power BI Desktop (2019 年 3 月リリース以降) では、**グループ ポリシー**を使用して、組織内に配置されているコンピューター間で未認定のカスタム ビジュアルの使用を無効にすることができます。

<table>
<tr><th>属性</th><th>値</th>
</tr>
<td>キー</td>
    <td>Software\Policies\Microsoft\Power BI Desktop\</td>
<tr>
<td>valueName</td>
<td>EnableUncertifiedVisuals</td>
</tr>
</table>

値が 1 (10 進数) の場合は、Power BI で未認定のカスタム ビジュアルの使用が有効になります (既定)。

値が 0 (10 進数) の場合は、Power BI で未認定のカスタム ビジュアルの使用が無効になります (このオプションでは、[認定済みのカスタム ビジュアル](https://go.microsoft.com/fwlink/?linkid=2002010)の使用のみが有効になります)。

## <a name="r-visuals-settings"></a>R ビジュアルの設定

### <a name="interact-with-and-share-r-visuals"></a>R ビジュアルとの対話と共有

組織内のユーザーは、R スクリプトで作成したビジュアルと対話して共有することができます。 [詳細情報](visuals/service-r-visuals.md)

> [!NOTE]
> この設定は、組織全体に適用され、特定のグループに限定することはできません。

## <a name="audit-and-usage-settings"></a>監査と使用状況の設定

### <a name="create-audit-logs-for-internal-activity-auditing-and-compliance"></a>内部アクティビティの監査とコンプライアンスのための監査ログの作成

組織内のユーザーは監査を使用して、組織内の他のユーザーによって実行された Power BI のアクションを監視することができます。 [詳細情報](service-admin-auditing.md)

監査ログのエントリを記録するには、この設定を有効にする必要があります。 監査を有効にしてから監査データを表示できるようになるまで、最大で 48 時間の遅延が発生する場合があります。 データがすぐに表示されない場合は、後で、監査ログを確認してください。 監査ログの表示アクセス許可を取得してからログにアクセスできるようになるまでにも、同様の遅延が発生する場合があります。

> [!NOTE]
> この設定は、組織全体に適用され、特定のグループに限定することはできません。

### <a name="usage-metrics-for-content-creators"></a>コンテンツ作成者用の使用状況メトリック

組織内のユーザーは、自分が作成したダッシュボードとレポートの使用状況メトリックを確認できます。 [詳細情報](service-usage-metrics.md)

### <a name="per-user-data-in-usage-metrics-for-content-creators"></a>コンテンツ作成者用の使用状況メトリックにおけるユーザーごとのデータ

コンテンツ作成者用の使用状況メトリックには、コンテンツにアクセスしているユーザーの表示名とメール アドレスが示されます。 [詳細情報](service-usage-metrics.md)

ユーザーごとのデータは利用状況メトリックに対して既定で有効になり、コンテンツ作成者のアカウント情報はメトリック レポートに含まれます。 一部またはすべてのユーザーに対してこの情報を含めない場合は、指定したセキュリティ グループまたは組織全体に対してこの機能を無効にします。 アカウント情報は、 *[名前なし]* としてレポートに表示されます。

## <a name="dashboard-settings"></a>ダッシュボードの設定

### <a name="data-classification-for-dashboards"></a>ダッシュボードのデータ分類

組織内のユーザーは、ダッシュボードのセキュリティ レベルを示す分類を使って、ダッシュボードにタグを付けることができます。 [詳細情報](service-data-classification.md)

> [!NOTE]
> この設定は、組織全体に適用され、特定のグループに限定することはできません。

## <a name="developer-settings"></a>開発者の設定

### <a name="embed-content-in-apps"></a>アプリにコンテンツを埋め込む

組織内のユーザーが、Power BI のダッシュボードとレポートを、サービスとしてのソフトウェア (SaaS) アプリケーションに埋め込むことができます。 この設定を無効にすると、ユーザーが REST API を使用して、Power BI コンテンツをアプリケーションに埋め込むことができなくなります。 [詳細情報](developer/embedding.md)

### <a name="allow-service-principals-to-use-power-bi-apis"></a>Power BI API の使用をサービス プリンシパルに許可

Azure Active Directory (Azure AD) に登録されている Web アプリは、サインインしているユーザーなしで Power BI API にアクセスするために、割り当て済みのサービス プリンシパルを使用します。 アプリによるサービス プリンシパル認証の使用を許可するには、許可されているセキュリティ グループにそのサービス プリンシパルを含める必要があります。 [詳細情報](developer/embed-service-principal.md)

> [!NOTE]
> サービス プリンシパルは、対象セキュリティ グループの Power BI テナントのすべての設定のアクセス許可を継承します。 アクセス許可を制限するには、サービス プリンシパル専用のセキュリティ グループを作成し、関連する有効な Power BI 設定の [特定のセキュリティ グループを除く] リストに追加します。

## <a name="dataflow-settings"></a>データフローの設定

### <a name="create-and-use-dataflows"></a>データフローの作成と使用

組織内のユーザーはデータフローを作成して使用できます。 データフローの概要については、「[Power BI でのセルフサービスのデータ準備](service-dataflows-overview.md)」をご覧ください。 Premium 容量でのデータフローを有効にするには、「[ワークロードを構成する](service-admin-premium-workloads.md)」を参照してください。

> [!NOTE]
> この設定は、組織全体に適用され、特定のグループに限定することはできません。

## <a name="template-apps-settings"></a>テンプレート アプリの設定

3 つの設定により、テンプレート アプリを発行またはインストールするテンプレート アプリの機能を制御します。

![Power BI 管理ポータルのテンプレート アプリ設定](media/service-admin-portal/power-bi-admin-portal-template-apps.png)

### <a name="publish-template-apps"></a>テンプレート アプリを発行する

組織内のユーザーはテンプレート アプリのワークスペースを作成できます。 [AppSource](https://appsource.microsoft.com) またはその他の配布方法を利用して、組織外のクライアントにテンプレート アプリを発行または配布できるユーザーを制御します。

![Power BI 管理ポータル、テンプレート アプリの作成設定](media/service-admin-portal/power-bi-admin-portal-template-app-settings.png)

### <a name="install-template-apps-listed-on-appsource"></a>AppSource にリストされているテンプレート アプリをインストールする

組織内のユーザーは、[AppSource](https://appsource.microsoft.com)から**のみ**、テンプレートをダウンロードしてインストールできます。 AppSource からテンプレート アプリをインストールできる特定のユーザーまたはセキュリティ グループを制御します。

![Power BI 管理ポータル、テンプレート アプリのインストール設定](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-appsource.png)

### <a name="install-template-apps-not-listed-on-appsource"></a>AppSource にリストされていないテンプレート アプリをインストールする

**[AppSource](https://appsource.microsoft.com)にリストされていない**テンプレート アプリをダウンロードしてインストールできる組織内のユーザーを制御します。

![Power BI 管理ポータル、テンプレート アプリのインストール設定](media/service-admin-portal/power-bi-admin-portal-template-app-settings-installer-nonappsource.png)

## <a name="capacity-settings"></a>容量の設定

### <a name="power-bi-premium"></a>Power BI Premium

**[Power BI Premium]** タブでは、組織用に購入されたすべての Power BI Premium 容量 (EM または P SKU) を管理できます。 組織内のすべてのユーザーに **[Power BI Premium]** タブが表示されますが、そのタブにコンテンツが表示されるのは、ユーザーが、"*容量管理者*"、または割り当てのアクセス許可を持つユーザーとして割り当てられている場合のみです。 アクセス許可が何も割り当てられていないユーザーには、次のメッセージが表示されます。

![Premium の設定にアクセスできません](media/service-admin-portal/premium-settings-no-access.png)

### <a name="power-bi-embedded"></a>Power BI Embedded

**[Power BI Embedded]** タブを使用すると、顧客用に購入した Power BI Embedded (A SKU) の容量を表示できます。 Azure からは A SKU の購入のみ可能であるため、**Azure portal** から [Azure の埋め込み容量を管理](developer/azure-pbie-create-capacity.md)します。

Power BI Embedded (A SKU) の設定を管理する方法について詳しくは、「[Azure の Power BI Embedded とは何か](developer/azure-pbie-what-is-power-bi-embedded.md)」をご覧ください。

## <a name="embed-codes"></a>埋め込みコード

管理者は、テナントに対して生成されている埋め込みコードを表示することができます。 コードを取り消したり削除したりすることもできます。 [詳細情報](service-publish-to-web.md)

![Power BI 管理ポータル内の埋め込みコード](media/service-admin-portal/embed-codes.png)

 ## <a name="organizational-visuals">組織のビジュアル</a> 

**[組織のビジュアル]** タブでは、組織内にカスタム ビジュアルを展開して管理できます。 組織のビジュアルを使用すると、組織に独自のビジュアルを簡単に展開でき、レポート作成者はそれを検出して、Power BI Desktop からレポートにインポートできます。 [詳細情報](power-bi-custom-visuals-organization.md)

> [!WARNING]
> カスタム ビジュアルには、セキュリティやプライバシー上のリスクを伴うコードが含まれている可能性があります。組織のリポジトリに展開する前に、カスタム ビジュアルの作成者とソースが信頼できることを確認してください。

次の図では、組織のリポジトリに現在展開されているすべてのカスタム ビジュアルを示します。

![組織の管理のビジュアル](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-01.png)

### <a name="add-a-new-custom-visual"></a>新しいカスタム ビジュアルの追加

一覧に新しいカスタム ビジュアルを追加するには、次の手順のようにします。 

1. 右側のウィンドウで、 **[カスタム ビジュアルの追加]** を選択します。

    ![カスタム ビジュアル フォーム](media/service-admin-portal/power-bi-custom-visuals-organizational-admin-02.png)

1. **[カスタム ビジュアルを追加します]** フォームに入力します。

    * **[.pbiviz ファイルの選択]** (必須): アップロードするカスタム ビジュアル ファイルを選択します。 バージョン管理されている API カスタム ビジュアルのみをサポートしています (詳細はここをお読みください)。

    カスタム ビジュアルをアップロードする前に、そのビジュアルのセキュリティとプライバシーを調べ、組織の基準に適合することを確認してください。

    * **[カスタム ビジュアルに名前を付ける]** (必須): Power BI Desktop ユーザーにとってわかりやすくなるように、ビジュアルに短いタイトルを付けます

    * **アイコン**:Power BI Desktop UI に表示されるアイコン ファイルです。

    * **[説明]** : ユーザーにとってわかりやすくなるようにビジュアルに簡単な説明を与えます

1. **[追加]** を選択して、アップロード要求を開始します。 成功すると、一覧に新しい項目が表示されます。 失敗すると、エラー メッセージが表示されます。

### <a name="delete-a-custom-visual-from-the-list"></a>一覧からカスタム ビジュアルを削除する

ビジュアルを完全削除するには、リポジトリでビジュアルのごみ箱アイコンを選択します。

> [!IMPORTANT]
> 削除は元に戻すことができません。 削除の直後から、既存のレポートでそのビジュアルのレンダリングが停止します。 同じビジュアルをもう一度アップロードしても、削除された前のビジュアルが置き換わることはありません。 ただし、ユーザーは、新しいビジュアルを再度インポートして、レポート内に作成したインスタンスを置き換えることはできます。

### <a name="disable-a-custom-visual-in-the-list"></a>一覧でカスタム ビジュアルを無効にする

組織のストアからビジュアルを無効にするには、歯車アイコンを選択します。 **[アクセス]** セクションで、カスタム ビジュアルを無効にします。

無効にしたビジュアルは既存のレポートに表示されず、次のエラー メッセージが表示されます。

*This custom visual is no longer available.Please contact your administrator for details. (このカスタム ビジュアルは使用できなくなりました。詳細については管理者に問い合わせてください。)*

ただし、ブックマークが設定されたビジュアルは引き続き機能します。

更新または管理者による変更の後、Power BI Desktop ユーザーはアプリケーションを再起動するか、Power BI サービスでブラウザーを最新の情報に更新して、更新の内容を確認する必要があります。

### <a name="update-a-visual"></a>ビジュアルを更新する

組織のストアからビジュアルを更新するには、歯車アイコンを選択します。 新しいバージョンのビジュアルを参照してアップロードします。

ビジュアル ID が変わらないことを確認します。 新しいファイルで、組織全体のすべてのレポートの以前のファイルが置き換えられます。 ただし、ビジュアルの新しいバージョンのためにビジュアルの以前のバージョンを使用できなくなったり、データ構造が破損されたりする可能性がある場合は、以前のバージョンを置き換えないでください。 代わりに、新しいバージョンのビジュアル用に新しく登録することをお勧めします。 たとえば、新しいバージョン番号 (バージョン X.X) を新しく登録されたビジュアルのタイトルに追加します。 こうすると、バージョン番号が更新されているだけで同じビジュアルであることがわかるので、既存のレポートの機能は中断されません。 この場合も、ビジュアル ID が変わらないことを確認します。 次回ユーザーが Power BI Desktop から組織のリポジトリに入ると、新しいバージョンをインポートできます。レポートに入っている現在のバージョンを置換するように求められます。

詳細については、[組織のカスタム ビジュアルに関してよく寄せられる質問](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#organizational-custom-visuals)のページにアクセスしてください。

## <a name="dataflowStorage">データフロー ストレージ (プレビュー)</a>

既定では、Power BI で使用されるデータは、Power BI で利用可能な内部ストレージに保存されます。 データフローと Azure Data Lake Storage Gen2 (ADLS Gen2) を統合すると、組織の Azure Data Lake Storage Gen2 アカウントにデータフローを保存できます。 詳細については、「[データフローと Azure Data Lake の統合 (プレビュー)](service-dataflows-azure-data-lake-integration.md)」を参照してください。

## <a name="workspaces"></a>ワークスペース

管理者は自分のテナントに存在するワークスペースを表示できます。 ワークスペースの一覧を並べ替えたり、フィルターを適用したり、ワークスペースごとの詳細を表示したりできます。 テーブルの列は、ワークスペースの [Power BI 管理者 Rest API](/rest/api/power-bi/admin) によって返されるプロパティに対応しています。 個人ワークスペースの種類は **PersonalGroup**、従来のワークスペースの種類は **Group**、新しいワークスペース エクスペリエンスのワークスペースの種類は **Workspace** です。 詳細については、「[Power BI で新しいワークスペースを作成する](service-create-the-new-workspaces.md)」をご覧ください。

![ワークスペース リスト](media/service-admin-portal/workspaces-list.png)


## <a name="next-steps"></a>次の手順

[組織内の Power BI を管理する](service-admin-administering-power-bi-in-your-organization.md)  
[Power BI 管理者の役割について](service-admin-role.md)  
[組織内の Power BI を監査する](service-admin-auditing.md)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
