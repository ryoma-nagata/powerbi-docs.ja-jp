---
title: Power BI サービスから Power BI Desktop にレポートをダウンロードする (プレビュー)
description: Power BI サービスから Power BI Desktop ファイルへのレポートのダウンロード
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/12/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 61fc821e63889951aefd0ef815f885ffa8a880cf
ms.sourcegitcommit: d12bc6df16be1f1993232898f52eb80d0c9fb04e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68994818"
---
# <a name="download-a-report-from-the-power-bi-service-to-power-bi-desktop-preview"></a>Power BI サービスから Power BI Desktop にレポートをダウンロードする (プレビュー)
Power BI Desktop では、ローカル コンピューターから Power BI サービスにレポート ( *.pbix* ファイル) を発行できます。 Power BI レポートは反対の方向に発行することもできます。Power BI サービスから Power BI Desktop にレポートをダウンロードできます。 いずれの場合も、Power BI レポートの拡張子は .pbix です。

この記事の後半では、注意する必要のあるいくつかの制限事項と考慮事項について説明します。

![[ファイル] ドロップダウン](media/service-export-to-pbix/power-bi-file-export.png)

## <a name="download-the-report-as-a-pbix-file"></a>レポートを .pbix ファイルとしてダウンロードする

2016 年 11 月 23 日以降に [Power BI Desktop で作成され](guided-learning/publishingandsharing.yml?tutorial-step=2)、その後更新されたレポートのみダウンロードできます。 作成がそれ以前の場合、Power BI サービスの **[レポートのダウンロード]** メニュー オプションは淡色表示されます。

.pbix ファイルをダウンロードするには、次の手順に従います。

1. Power BI サービスで、ダウンロードするレポートを[編集ビュー](https://docs.microsoft.com/power-bi/service-interact-with-a-report-in-editing-view)で開きます。

2. 上部のナビゲーション バーから、 **[ファイル]、[レポートのダウンロード]** の順に選択します。
   
3. レポートがダウンロードされているとき、ステータス バナーに進捗状況が表示されます。 ファイルの用意ができると、.pbix ファイルを保存する場所を問われます。 ファイルの既定の名前はレポートのタイトルと同じです。
   
4. Power BI Desktop をまだインストールしていない場合、[インストール](desktop-get-the-desktop.md)し、.pbix ファイルを Power BI Desktop で開きます。
   
    レポートを Power BI Desktop で開くと、Power BI サービスのレポートで使用できる一部の機能が Power BI Desktop では使用できないという警告メッセージが表示されることがあります。
   
    ![警告ダイアログ](media/service-export-to-pbix/power-bi-export-to-pbix_2.png)

5. Power BI Desktop のレポート エディターと Power BI サービスのレポート エディターは似ています。  
   
    ![Power BI Desktop レポート エディター](media/service-export-to-pbix/power-bi-desktop.png)

## <a name="considerations-and-troubleshooting"></a>考慮事項とトラブルシューティング
Power BI サービスから .pbix ファイルをダウンロードすることに関しては、重要な考慮事項と制限事項がいくつかあります。

* ファイルをダウンロードするには、レポートの編集アクセス権限が必要です。
* レポートが Power BI Desktop を使用して作成され、Power BI サービスに*発行*されているか、.pbix ファイルが Power BI サービスに*アップロード*されている必要があります。
* レポートは、2016 年 11 月 23 日以降に更新または発行されている必要があります。 それ以前に発行されたレポートはダウンロードできません。
* この機能は、Power BI サービスでもともと作成されたレポートやコンテンツ パックには使用できません。
* ダウンロードしたファイルを開くときは常に最新バージョンの Power BI Desktop を使用してください。 最新バージョンではない Power BI Desktop では、ダウンロードした .pbix ファイルを開くことができない場合があります。
* データをダウンロードする機能を管理者が無効にしている場合、この機能は Power BI サービスに表示されません。
* 増分更新を使用しているデータセットは .pbix ファイルにダウンロードできません。

## <a name="next-steps"></a>次の手順
この機能に関しては、**Guy in a Cube** の簡単なビデオをご覧ください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/ymWqU5jiUl0" frameborder="0" allowfullscreen></iframe>

Power BI サービスの使い方を知るのに役立つ記事を以下に示します。

* [Power BI のレポート](consumer/end-user-reports.md)
* [Power BI サービスのデザイナー向けの基本的な概念](service-basic-concepts.md)

Power BI Desktop をインストールした後、次の記事を参照すると短時間で作業を開始するのに役立ちます。

* [Power BI Desktop の概要](desktop-getting-started.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

