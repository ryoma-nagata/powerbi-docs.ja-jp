---
title: Microsoft Teams と Power BI で共同作業する
description: Microsoft Teams のチャネルとチャットで、対話型の Power BI コンテンツを簡単に共有し、共同作業を行うことができます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 07/22/2020
ms.openlocfilehash: 17a0879dac416a98d214ed11861947cb2c311487
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254210"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>Microsoft Teams と Power BI で共同作業する

Microsoft Teams のチャネルとチャットで、対話型の Power BI コンテンツを共有および共同作業を行うためのオプションがいくつかあります。 

- Microsoft Teams の **[Power BI]** タブを使用すると、[対話形式のレポートを Microsoft Teams のチャネルおよびチャットに埋め込む](service-embed-report-microsoft-teams.md)ことができます。 **[Power BI]** タブを使用すると、仕事仲間があなたのチームのデータを検索し、あなたのチームのチャネル内のデータについて話し合うことができます。 
- ご自分のレポート、ダッシュボード、およびアプリへのリンクを [Microsoft Teams] メッセージ ボックスに貼り付けるときに、[リンク プレビュー](service-teams-link-preview.md)を作成します。 リンク プレビューには、リンクに関する情報が表示されます。 
- Power BI サービスでレポートやダッシュボードを表示しているときに Teams で会話をすばやく開始するには、[[Teams で共有]](service-share-report-teams.md) を使用します。
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="Teams チャネルに埋め込まれた Power BI レポートのスクリーンショット。":::

## <a name="requirements"></a>要件

一般に、Microsoft Teams で Power BI を機能させるには、次の要素を確認します。

- お客様のユーザーが Power BI Pro ライセンスを所有している。または、Power BI ライセンスのある [Power BI Premium 容量 (EM または P SKU)](../admin/service-premium-what-is.md) にレポートが含まれている。
- ユーザーが Power BI サービスにサインインし、自分の Power BI ライセンスをアクティブ化している。
- Microsoft Teams の **[Power BI]** タブを使用するための要件をユーザーが満たしている。

Microsoft Teams の **[Power BI]** タブを使用するには、次の要素を確認します。

- Microsoft Teams に **[Power BI]** タブがある。
- Microsoft Teams で **[Power BI]** タブを使用してレポートを追加するには、レポートがホストされているワークスペースで、少なくともビューアー ロールを持っている。 さまざまなロールの詳細については、「[新しいワークスペースのロール](service-new-workspaces.md#roles-in-the-new-workspaces)」をご覧ください。
- Microsoft Teams の **[Power BI]** タブでレポートを表示するには、ユーザーがそのレポートを表示するためのアクセス許可を持っている必要があります。
- ユーザーは、チャネルとチャットにアクセスできる Microsoft Teams ユーザーである必要があります。

Power BI で **[Teams で共有]** 機能を使用するには、次の設定を確認します。

- Power BI 管理者が、Power BI 管理ポータルで **[Teams で共有]** テナント設定を無効にしていない。 この設定により、組織は **[Teams で共有]** ボタンに非表示にすることができます。 詳細については、[Power BI 管理ポータル](../admin/service-admin-portal.md#share-to-teams-tenant-setting)に関する記事を参照してください。

## <a name="grant-access-to-reports"></a>レポートへのアクセスを許可する

Microsoft Teams にレポートを埋め込んだり、項目へのリンクを送信しても、レポートを表示するためのアクセス許可が自動的にユーザーに与えられることはありません。 [Power BI でユーザーにレポートの表示を許可する](service-share-dashboards.md)必要があります。 チーム用に Microsoft 365 グループを使用すると、作業を容易にすることができます。

> [!IMPORTANT]
> Power BI サービスでレポートを表示できるユーザーを確認し、一覧に含まれないユーザーにアクセスを許可します。

チーム内のすべてのユーザーがレポートに確実にアクセスできるようにする方法の 1 つは、1 つのワークスペースにレポートを配置し、チームの Microsoft 365 グループにアクセス権を付与することです。

## <a name="known-issues-and-limitations"></a>既知の問題と制限事項

- Power BI では、Microsoft Teams と同じローカライズされた言語はサポートされていません。 そのため、埋め込みのレポートが適切にローカライズされていない可能性があります。
- Power BI ダッシュボードを Microsoft Teams の **[Power BI]** タブに埋め込むことはできません。
- Power BI のライセンスまたはレポートへのアクセス許可を持たないユーザーには、"コンテンツは利用できません" というメッセージが表示されます。
- Internet Explorer 10 を使用している場合、問題が発生する可能性があります。 <!--You can look at the [browsers support for Power BI](../consumer/end-user-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL フィルター](service-url-filters.md)は、Microsoft Teams の **[Power BI]** タブではサポートされていません。
- 国内のクラウドでは、この新しい **[Power BI]** タブは使用できません。 Power BI アプリの新しいワークスペース エクスペリエンスやレポートがサポートされていない古いバージョンを使用できる可能性があります。
- タブを保存したら、タブの設定からタブ名を変更することはできません。 変更するには、 **[名前変更]** オプションを使用します。
- リンク プレビュー サービスでは、シングル サインオンはサポートされていません。
- リンク プレビューは、チャットまたはプライベート チャネルでは機能しません。

## <a name="next-steps"></a>次のステップ

- [Microsoft Teams に Power BI コンテンツを埋め込む](service-embed-report-microsoft-teams.md)
- [Microsoft Teams で Power BI リンク プレビューを入手する](service-teams-link-preview.md)
- [Power BI サービスから Teams に直接共有する](service-share-report-teams.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
