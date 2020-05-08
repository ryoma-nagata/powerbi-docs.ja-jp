---
title: Microsoft Teams にレポートを埋め込む
description: Microsoft Teams の [Power BI] タブを使用すると、対話形式のレポートをチャンネルまたはチャットに簡単に埋め込むことができます。
author: LukaszPawlowski-MS
ms.author: lukaszp
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 04/27/2020
ms.openlocfilehash: b3fd881a552e3594cbf2172d7b88bbbf9a13f1b9
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82585084"
---
# <a name="embed-reports-in-microsoft-teams-with-the-power-bi-tab"></a>Microsoft Teams の [Power BI] タブを使用してレポートを埋め込む

Microsoft Teams の更新済みの [Power BI] タブを使用すると、対話形式のレポートを Microsoft Teams のチャンネルまたはチャットに簡単に埋め込むことができます。 Microsoft Teams の [Power BI] タブを使用すると、チームが使用するデータを検索したり、チームのチャネル内のデータについて話し合うことができます。  お客様のレポート、ダッシュボード、およびアプリへのリンクを Microsoft Teams のメッセージ ボックスに貼り付けると、それらの情報がリンクのプレビューに表示されます。 お客様のユーザーは、リンクがどの項目につながっているかをより簡単に理解できます。

## <a name="requirements"></a>要件

**Microsoft Teams の [Power BI] タブ**を機能させるには、次のことを確認してください。

- お客様のユーザーが Power BI Pro ライセンスを所有している。または、Power BI ライセンスのある [Power BI Premium 容量 (EM または P SKU)](service-premium-what-is.md) にレポートが含まれている。
- Microsoft Teams に [Power BI] タブがある。
- ユーザーが Power BI サービスにサインインし、レポートを使用できるように自分の Power BI ライセンスをアクティブ化している。
- ユーザーにはデータを表示するためのアクセス許可を持つ必要がある。

また、**リンク プレビュー**を機能させるには、次のことを確認してください。
- Microsoft Teams の [Power BI] タブを使用するための要件をユーザーが満たしている。
- ユーザーが Power BI Bot サービスにサインイン済みである。 


## <a name="embed-your-report"></a>レポートを埋め込む

Microsoft Teams チャンネルまたはチャットにご利用のレポートを埋め込むには、以下の手順に従ってください。

1. Microsoft Teams でチャネルまたはチャットを開き、 **[+]** アイコンを選択します。

    ![チャンネルまたはチャットにタブを追加する](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

2. [Power BI] タブを選択します。

    ![[Power BI] が選択された Microsoft Teams のタブ リスト](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

3. 提供されているオプションを使用して、ワークスペース、[自分と共有]、または Power BI アプリからレポートを選択します。

    ![Microsoft Teams の設定の [Power BI] タブ](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

4. タブ名は、レポート名と一致するように自動的に更新されますが、変更することもできます。 

5. **[保存]** をクリックします。

## <a name="supported-reports-for-embedding-the-power-bi-tab"></a>[Power BI] タブを埋め込む場合にサポートされているレポート
[Power BI] タブでは、次の種類のレポートを埋め込むことができます。

- 対話型レポートとページ分割されたレポート。
- 個人用ワークスペース、新しいワークスペース エクスペリエンス、およびクラシック ワークスペースのレポート。
- Power BI アプリのレポート。

## <a name="get-a-link-preview"></a>リンク プレビューを取得する

Power BI サービスのコンテンツのリンク プレビューを取得するには、次の手順に従ってください。

1. Power BI サービス内のレポート、ダッシュボード、またはアプリへのリンクをコピーします。 たとえば、ブラウザーのアドレス バーからリンクをコピーします。

2. そのリンクを [Microsoft Teams] メッセージ ボックスに貼り付けます。 プロンプトが表示されたら、リンク プレビュー サービスにサインインします。 リンク プレビューが読み込まれるまで数秒待つことが必要になる場合があります。

    ![Power BI Bot にサインインする](media/service-embed-report-microsoft-teams/service-teams-link-preview-sign-in-needed.png)

3. サインインに成功すると、基本的なリンクのプレビューが表示されます。

    ![基本的なリンクのプレビュー](media/service-embed-report-microsoft-teams/service-teams-link-preview-basic.png)

4. 展開アイコンを選択して、リッチ プレビュー カードを表示します。

    ![展開アイコン](media/service-embed-report-microsoft-teams/service-teams-link-preview-expand-icon.png)

5. リッチ リンク プレビュー カードに、リンクと、関連するアクション ボタンが表示されます。

    ![リッチ リンク プレビュー カード](media/service-embed-report-microsoft-teams/service-teams-link-preview-nice-card.png)

6. メッセージを送信します。



## <a name="grant-access-to-reports"></a>レポートへのアクセスを許可する

Microsoft Teams にレポートを埋め込んだり、項目へのリンクを送信しても、レポートを表示するためのアクセス許可が自動的にユーザーに与えられることはありません。[Power BI でユーザーにレポートの表示を許可する](service-share-dashboards.md)必要があります。 チームに Office 365 グループを使用すると、作業を容易にすることができます。 

> [!IMPORTANT]
> Power BI サービスでレポートを表示できるユーザーを確認し、一覧に含まれないユーザーにアクセスを許可します。

チーム内のすべてのユーザーがレポートに確実にアクセスできるようにする方法の 1 つとして、Power BI の 1 つのワークスペースにレポートを配置し、チームがそのワークスペースにアクセスできるように Office 365 グループを設定します。

## <a name="link-previews"></a>リンク プレビュー 

リンク プレビューは、Power BI の次の項目に対して提供されます。
- レポート
- ダッシュボード
- Apps

リンク プレビュー サービスでは、ユーザーのサインインが必要です。 サインアウトするには、メッセージ ボックスの下部にある [Power BI] アイコンを選択して、[サインアウト] を選択します。

## <a name="start-a-conversation"></a>会話の開始

Power BI レポート タブを Teams に追加すると、レポートに関するタブの会話が Teams によって自動的に作成されます。 

- 右上隅にある **[[会話] タブを表示します]** を選択します。

    ![[[会話] タブを表示します] アイコン](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-icon.png)

    最初のコメントは、レポートへのリンクです。 その Teams チャネル内のすべてのユーザーが、会話でレポートを表示してディスカッションできます。

    ![タブの会話](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-tab.png)

## <a name="known-issues-and-limitations"></a>既知の問題と制限事項

- Power BI では、Microsoft Teams と同じローカライズされた言語はサポートされていません。 そのため、埋め込みのレポートが適切にローカライズされていない可能性があります。
- Power BI ダッシュボードを Microsoft Teams の Power BI タブに埋め込むことはできません。
- Power BI のライセンスまたはレポートへのアクセス許可を持たないユーザーには、"コンテンツは利用できません" というメッセージが表示されます。
- Internet Explorer 10 を使用する場合、問題が発生する可能性があります。 <!--You can look at the [browsers support for Power BI](consumer/end-user-browsers.md) and for [Office 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- [URL フィルター](service-url-filters.md)は、Microsoft Teams の [Power BI] タブではサポートされていません。
- 国内のクラウドでは、この新しい [Power BI] タブは使用できません。 Power BI アプリの新しいワークスペース エクスペリエンスのワークスペースやレポートをサポートしていない古いバージョンを使用できる可能性があります。 
- タブを保存したら、タブの設定からタブ名を変更することはできません。 変更するには、名前変更オプションを使用します。
- リンク プレビュー サービスでは、シングル サインオンはサポートされていません。
- リンク プレビューは、チャットまたはプライベート チャネルでは機能しません。

## <a name="next-steps"></a>次の手順
- [同僚や他のユーザーとダッシュボードやレポートを共有する](service-share-dashboards.md)  
- [Power BI でのアプリの作成および配布](service-create-distribute-apps.md)  
- [Power BI Premium とは何ですか?](service-premium-what-is.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
