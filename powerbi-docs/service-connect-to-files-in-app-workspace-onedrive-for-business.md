---
title: Power BI ワークスペースの OneDrive のファイルに接続する
description: Power BI ワークスペースの OneDrive への Excel、CSV、Power BI Desktop などのファイルの保存とファイルへの接続について説明します。
author: maggiesMSFT
ms.reviewer: lukasz
ms.service: powerbi
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 180fd8d451be794070d8b0f4d37c40965671d23d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "73854877"
---
# <a name="connect-to-files-stored-in-onedrive-for-your-power-bi-workspace"></a>Power BI ワークスペースの OneDrive に保存されているファイルに接続する
[Power BI にワークスペースを作成](service-create-distribute-apps.md)した後、Excel、CSV、Power BI Desktop などのファイルを Power BI ワークスペースの OneDrive for Business に保存できるようになりました。 OneDrive に保存したファイルは引き続き更新できます。 これらの更新プログラムは、ファイルに基づいて Power BI レポートとダッシュボードに自動的に反映されます。 

> [!NOTE]
> 新しいワークスペース エクスペリエンスでは、Power BI ワークスペースと Office 365 グループ間の関係が変わります。 新しいワークスペースの 1 つを作成するたびに Office 365 グループは自動的に作成されません。 新しいワークスペースの作成については、[こちら](service-create-the-new-workspaces.md)を参照してください

ワークスペースへのファイルの追加は、次の 2 つの手順で行います。 

1. まず、ワークスペースの [OneDrive for Business にファイルをアップロード](service-connect-to-files-in-app-workspace-onedrive-for-business.md#1-upload-files-to-the-onedrive-for-business-for-your-workspace)します。
2. 次に、[アップロードしたファイルに Power BI から接続](service-connect-to-files-in-app-workspace-onedrive-for-business.md#2-import-excel-files-as-datasets-or-as-excel-online-workbooks)します。

> [!NOTE]
> ワークスペースは、[Power BI Pro](service-features-license-type.md) でのみ利用できます。
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-workspace"></a>1 ワークスペースの OneDrive for Business にファイルをアップロードする
1. Power BI サービスで、[ワークスペース] の横にある矢印を選択し、目的のワークスペース名の隣にある省略記号 ( **…** ) を選択します。 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. **[ファイル]** を選択し、Office 365 のワークスペースの OneDrive for Business を開きます。
   
   > [!NOTE]
   > ワークスペース メニューに **[ファイル]** が表示されない場合は、 **[メンバー]** を選択してワークスペースの OneDrive for Business を開きます。 そこで、 **[ファイル]** を選びます。 Office 365 で、アプリのグループ ワークスペース ファイルの OneDrive ストレージの場所が作成されます。 このプロセスにはしばらく時間がかかることがあります。 
   > 
   > 
3. ここで、ワークスペースの OneDrive for Business にファイルをアップロードすることができます。 **[アップロード]** を選び、ファイルに移動します。
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 Excel ファイルをデータセットまたは Excel Online のブックとしてインポートする
ファイルがワークスペースの OneDrive for Business に保存されたので、選択肢ができました。 次のことが行えます。 

* [Excel ブックからデータセットとしてデータをインポートします](service-get-data-from-files.md)。 次に、そのデータを使用して Web ブラウザーやモバイル デバイスで表示できるレポートとダッシュボードを作成します。
* または、[Power BI で Excel ブック全体に接続](service-excel-workbook-files.md)し、Excel Online で表示されるのと同じようにブックを表示します。

### <a name="import-or-connect-to-the-files-in-your-workspace"></a>ワークスペースへのインポートまたはファイルへの接続
1. Power BI で、ワークスペースに切り替えると、ワークスペース名が左上に表示されます。 
2. ナビ ペインの下部にある **[データの取得]** を選択します。 
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. **[ファイル]** ボックスで、 **[取得]** を選択します。
   
   ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. **[OneDrive]**  -  *[<ワークスペース名>]* を選択します。
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. 必要なファイルを選び、**接続**します。
   
    この時点で、[Excel ブックからデータをインポートする](service-get-data-from-files.md)か、[Excel ブック全体に接続する](service-excel-workbook-files.md)かどうかを決定します。
6. **[インポート]** または **[接続]** を選びます。
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. **[インポート]** を選択した場合、 **[データセット]** タブにブックが表示されます。 
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    **[接続]** を選択した場合、 **[ブック]** タブにブックが表示されます。
   
    ![](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>次のステップ
* [Power BI でアプリとワークスペースを作成する](service-create-distribute-apps.md)
* [Excel ブックからデータをインポートする](service-get-data-from-files.md)
* [Excel ブック全体に接続する](service-excel-workbook-files.md)
* 他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
* フィードバックがある場合は、 「[Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi)」 (Power BI に関するヒント) を参照してください。

