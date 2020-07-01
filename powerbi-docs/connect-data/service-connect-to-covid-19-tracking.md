---
title: COVID-19 US トラッキング レポートに接続する
description: COVID-19 US ケース テンプレート アプリを取得してインストールする方法、およびデータに接続する方法。
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/05/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 5487d9f0eb5d8b172cc3e29ea24e88704267cd85
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85230251"
---
# <a name="connect-to-the-covid-19-us-tracking-report"></a>COVID-19 US トラッキング レポートに接続する
この記事では、COVID-19 トラッキング レポート用のテンプレート アプリをインストールする方法と、データ ソースに接続する方法について説明します。

![COVID-19 US トラッキング レポート](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-title-screen.png)

データに関する免責事項や情報など、レポート自体の詳細については、「[米国の州政府および地方自治体向けの COVID-19 の追跡サンプル](../create-reports/sample-covid-19-us.md)」を参照してください。

テンプレート アプリをインストールし、データ ソースに接続した後、必要に応じてレポートをカスタマイズできます。 その後、組織内の同僚にアプリとして配布することができます。

## <a name="install-the-app"></a>アプリをインストールする

1. アプリにアクセスするには、次のリンクをクリックします: [COVID-19 US トラッキング レポート テンプレート アプリ](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.covid19ms)

1. アプリの [AppSource] ページが表示されたら、[ **[今すぐ入手する]** ](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.covid19ms) をクリックします。

    [![AppSource の Covid-19 US トラッキング レポート](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-appsource-icon.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.covid19ms)

1. メッセージが表示されたら、 **[インストール]** をクリックします。 アプリがインストールされると、[アプリ] ページに表示されます。

   ![[アプリ] ページの COVID-19 US トラッキング レポート](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>データ ソースに接続する

1. [アプリ] ページのアイコンをクリックして、アプリを開きます。

1. 表示されたスプラッシュ スクリーンで、 **[接続]** を選択します。

   ![テンプレート アプリのスプラッシュ スクリーン](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-splash-screen.png)

1. 2 つのサインイン ダイアログが順に表示されます。 両方で、プライバシー レベルを [パブリック] に設定します。

   ![Covid-19 US トラッキング レポートのサインイン ダイアログ](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-signin-dialog.png)

   レポートはデータ ソースに接続され、最新のデータが設定されます。 この間は、利用状況モニターが作動します。

   ![COVID-19 US トラッキング レポートの進行中の更新](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>レポート更新のスケジュールを設定する

データ更新が完了すると、アプリに関連付けられているワークスペースが表示されます。 レポート データを最新の状態に保つために、[更新スケジュールを設定](../connect-data/refresh-scheduled-refresh.md)します。

## <a name="customize-and-share"></a>カスタマイズと共有

詳細については、「[アプリをカスタマイズして共有する](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app)」を参照してください。 アプリを公開または配布する前に、必ず、[レポートの免責事項](../create-reports/sample-covid-19-us.md#disclaimers)を確認してください。

## <a name="next-steps"></a>次の手順
* [米国の州政府および地方自治体向けの COVID-19 の追跡サンプル](../create-reports/sample-covid-19-us.md)
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
* [Power BI テンプレート アプリとは](../connect-data/service-template-apps-overview.md)
* [組織でテンプレート アプリをインストールして配布する](../connect-data/service-template-apps-install-distribute.md)
