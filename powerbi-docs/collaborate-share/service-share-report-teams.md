---
title: Power BI サービスから Teams に直接共有する
description: Power BI ダッシュボードとレポートを、Power BI サービスから Microsoft Teams に直接共有できます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 07/22/2020
ms.openlocfilehash: 6305a41188c4416b62d5432823bb30946e5e524d
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254078"
---
# <a name="share-directly-to-teams-from-the-power-bi-service"></a>Power BI サービスから Teams に直接共有する

Power BI ダッシュボード、レポート、およびビジュアルを、Power BI サービスから Microsoft Teams に直接共有できます。 Power BI サービスでレポートやダッシュボードを表示しているときに会話をすばやく開始するには、 **[Teams で共有]** 機能を使用します。

Power BI および Teams がどのように連携するかの背景と満たす必要がある要件については、「[Microsoft Teams での Power BI を使用した共同作業](service-collaborate-microsoft-teams.md)」を参照してください。

## <a name="share-power-bi-content-to-teams"></a>Power BI コンテンツを Teams に共有する

次の手順に従って、Power BI サービスでレポート、ダッシュボード、およびビジュアルへのリンクを、Microsoft Teams のチャネルとチャットに共有します。

1. 次のいずれかのオプションを選択します。

   * ダッシュボードまたはレポートのアクション バーの **[Teams で共有]** :

       ![アクション バーの [Teams で共有] ボタンのスクリーンショット。](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * 1 つのビジュアルのコンテキスト メニューの **[Teams で共有]** :
    
      ![視覚化のコンテキスト メニューの [Teams で共有] ボタンのスクリーンショット。](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

1. **[Microsoft Teams で共有]** ダイアログ ボックスで、リンクの送信先のチャネルまたはユーザーを選択します。 必要に応じて、メッセージを入力できます。 先に Microsoft Teams へのサインインを求められる場合があります。

    ![情報とメッセージが表示された [Microsoft Teams で共有] ダイアログ ボックスのスクリーンショット。](media/service-share-report-teams/service-teams-share-to-teams-dialog.png)

1. **[共有]** を選択して、リンクを送信します。
    
1. リンクが既存の会話に追加されるか、新しいチャットが開始されます。

    ![Power BI 項目へのリンクが含まれる Microsoft Teams の会話のスクリーンショット。](media/service-share-report-teams/service-teams-share-to-teams-deep-link.png)

1. リンクを選択し、Power BI サービスで項目を開きます。

1. 特定の視覚化のコンテキスト メニューを使用した場合、レポートが開くとその視覚化が強調表示されます。

    ![特定の視覚化が強調表示されて開かれた Power BI レポートのスクリーンショット。](media/service-share-report-teams/service-teams-share-to-teams-spotlight-visual.png)


## <a name="known-issues-and-limitations"></a>既知の問題と制限事項

- Power BI のライセンスまたはレポートへのアクセス許可を持たないユーザーには、"コンテンツは利用できません" というメッセージが表示されます。
- ブラウザーで厳格なプライバシー設定を使用している場合は、 **[Teams で共有]** ボタンが機能しないことがあります。 **[問題が発生した場合新しいウィンドウで開いてみてください]** オプションを、ダイアログ ボックスが正しく開かない場合は使用してください。
- **[Teams で共有]** には、リンク プレビューは含まれていません。
- リンクプ レビューと **[Teams で共有]** では、項目を表示するためのアクセス許可がユーザーに付与されません。 アクセス許可は個別に管理する必要があります。
- レポートの作成者が視覚化の **[その他]** オプションを **[オフ]** に設定している場合、視覚化のコンテキスト メニューの **[Teams で共有]** ボタンは使用できません。
- その他の問題については、Microsoft Teams での共同作業に関する記事の「[既知の問題と制限事項](service-collaborate-microsoft-teams.md#known-issues-and-limitations)」セクションを参照してください。

## <a name="next-steps"></a>次の手順

- [Microsoft Teams と Power BI で共同作業する](service-collaborate-microsoft-teams.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
