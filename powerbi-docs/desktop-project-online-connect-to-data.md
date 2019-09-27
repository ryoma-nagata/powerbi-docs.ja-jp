---
title: 'Project Online: Power BI Desktop 経由でデータに接続する'
description: 'Project Online: Power BI Desktop 経由でデータに接続する'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b0dc84d7b2d8da0df8a9e61a43f35898d197c188
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513735"
---
# <a name="project-online-connect-to-data-through-power-bi-desktop"></a>Project Online: Power BI Desktop 経由でデータに接続する
Power BI Desktop を経由して Project Online のデータに接続することができます。

## <a name="step-1-download-power-bi-desktop"></a>手順 1:Power BI Desktop をダウンロードする
1. [Power BI Desktop をダウンロード](http://go.microsoft.com/fwlink/?LinkID=521662)し、インストーラーを実行して **Power BI Desktop** をコンピューターにインストールします。

## <a name="step-2-connect-to-project-online-with-odata"></a>手順 2:OData を使用して Project Online に接続する
1. **Power BI Desktop** を開きます。
2. *[ようこそ]* 画面で、 **[データの取得]** を選択します。
3. **[OData フィード]** を選択し、 **[接続]** を選択します。
4. [URL] ボックスに OData フィードのアドレスを入力して、[OK] をクリックします。
   
   Project Web App サイトのアドレスが *https://\<tenantname\>.sharepoint.com/sites/pwa* である場合、OData フィードに入力するアドレスは *https://\<tenantname\>.sharepoint.com/sites/pwa/\_api/Projectdata* になります。
   
   この例では、 https://contoso.sharepoint.com/sites/pwa/default.aspx を使用します。
5. Power BI Desktop により、Office 365 アカウントを使用して認証するよう求められます。 組織アカウントを選択し、資格情報を入力します。
   
   ![](media/desktop-project-online-connect-to-data/image.png)

OData フィードへの接続に使用するアカウントは、少なくとも Project Web App サイトにアクセスするためのポートフォリオ閲覧者権限を有する必要があります。 

ここから、接続してクエリを作成するテーブルを選択できます。  作業の開始方法について  次のブログの投稿では、Project Online のデータからバーンダウン グラフを作成する方法を示します。  ブログの投稿では、Power Query を使用して Project Online に接続する方法について言及していますが、これは Power BI Desktop にも適用されます。

[Power Pivot と Power Query を使用してプロジェクトのバーンダウン グラフを作成する](http://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

