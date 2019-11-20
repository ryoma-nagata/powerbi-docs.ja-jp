---
title: Excel 2016 から Power BI へ発行する
description: Excel ブックを Power BI サイトに発行する方法について説明します。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 81bc53bae43cb16af92a9ecaf20c26c594a24368
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73881134"
---
# <a name="publish-to-power-bi-from-excel-2016"></a>Excel 2016 から Power BI へ発行する
Excel 2016 では、Excel ブックのデータに基づいて対話性の高いレポートやダッシュボードを作成できる [Power BI](https://powerbi.microsoft.com) サイトに Excel ブックを直接発行できます。 これにより、分析情報を組織内のユーザーと共有できます。

詳しい説明の前に、次の点に注意してください。

* Power BI に発行する前に、ブックを OneDrive for Business に保存する必要があります。
* Office、OneDrive for Business、Power BI へのサインインに使用するアカウントは同じアカウントである必要があります。
* 空白のブックや、Power BI でサポートされているコンテンツが含まれていないブックを発行することはできません。
* 暗号化されたブック、パスワードで保護されたブック、または Information Protection Management が使用されているブックは発行できません。
* Power BI に発行するには、先進認証が有効 (既定値) になっている必要があります。 無効になっている場合、[ファイル] メニューの [発行] オプションは使用できません。

## <a name="to-publish-your-excel-workbook"></a>Excel ブックを公開するには
Excel で、 **[ファイル]**  >  **[発行]** の順に選択します。

### <a name="local-file-publishing"></a>ローカル ファイルの発行
2017 年 2 月の更新以降、Excel 2016 で Excel のローカル ファイルを発行できるようになりました。 OneDrive for Business や SharePoint Online に保存する必要はありません。

> [!IMPORTANT]
> ローカル ファイルは、Office 365 サブスクリプションがある Excel 2016 のみで発行できます。 Excel 2016 スタンドアロン インストールでは引き続き、Excel ブックを OneDrive for Business または SharePoint Online に保存する必要がある "発行" のみの動作となります。
> 
> 

**[発行]** を選択する際に、発行先のワークスペースを選択できます。 アクセス可能な個人またはグループのワークスペースを指定できます。

![](media/service-publish-from-excel/pbi_choose_workspace.png)

Power BI でブックを取得する方法に関する 2 つのオプションが表示されます。

![](media/service-publish-from-excel/pbi_uploadexport3.png)

発行後、ローカル ファイルとは別に、Power BI にコピーとして保存されます。 Power BI でファイルを更新する場合は、更新バージョンを再び発行する必要があります。 Power BI のブックまたはデータセットでデータを更新したり、更新スケジュールを設定したりできます。

### <a name="publishing-from-excel-standalone"></a>Excel スタンドアロンからの発行
ブックがまだ OneDrive に保存されていない場合は、最初に OneDrive に保存する必要があります。 [クラウドに保存] を選択し、OneDrive for Business の場所を選択します。

![](media/service-publish-from-excel/pbi_savetoonedrive2.png)

OneDrive にブックが保存されている状態で **[発行]** を選択すると、Power BI でブックを取得する方法に関する 2 つのオプションが表示されます。

![](media/service-publish-from-excel/pbi_uploadexport2.png)

#### <a name="upload-your-workbook-to-power-bi"></a>Upload your workbook to Power BI (ブックを Power BI にアップロードする)
このオプションを選択すると、ブックは、Excel Online を使用しているときと同じように Power BI に表示されます。 ただし、Excel Online とは異なり、ワークシートの要素をダッシュボードにピン留めするのに役立ついくつかの優れた機能を利用できます。

Power BI で開いているブックを編集することはできません。ただし、変更を加える必要がある場合は、 **[編集]** を選択して、Excel Online でブックを編集するか、自分のコンピューターの Excel で開くかを選択できます。 ブックに加えたすべての変更は、OneDrive 上のブックに保存されます。

ブックをアップロードするとき、Power BI にデータセットは作成されません。 ブックは、ワークスペース ナビ ペインの [レポート] に表示されます。 Power BI にアップロードされたブックは、アップロード済みの Excel ブックであることを示す特殊な Excel アイコンで表示されます。

このオプションは、データがワークシートにのみ存在する場合や、Power BI で表示したいピボットテーブルやグラフがある場合に選択します。
Excel の [Power BI へ発行] から [アップロード] を使用することは、ブラウザーの Power BI から [データの取得]、[ファイル]、[OneDrive for Business]、[Power BI で Excel に接続し、管理し、表示する] の順に選択することと同じです。

#### <a name="export-workbook-data-to-power-bi"></a>Export workbook data to Power BI (ブックのデータを Power BI にエクスポートする)
このオプションを選択すると、テーブルやデータ モデル内のサポートされているデータがすべて、Power BI の新しいデータセットにエクスポートされます。 Power View シートがある場合、これらは Power BI でレポートとして再作成されます。

ブックは引き続き編集できます。 変更を保存すると、通常約 1 時間以内に Power BI のデータセットと同期されます。 直ちに同期する必要がある場合は、もう一度 [発行] を選択します。これだけで、その場ですぐに変更をエクスポートできます。 レポートとダッシュボードに視覚エフェクトがあれば、それらも更新されます。

このオプションは、データの取得と変換機能または Power Pivot を使用してデータをデータ モデルに読み込んでいる場合や、Power BI で表示したい視覚エフェクトが含まれる Power View シートがブックにある場合に選択します。

Excel の [Power BI へ発行] から [エクスポート] を使用することは、ブラウザーの Power BI から [データの取得]、[ファイル]、[OneDrive for Business]、[Export Excel data into Power BI]\(Excel データを Power BI にエクスポートする) の順に選択することと同じです。

## <a name="publishing"></a>発行
いずれかのオプションを選択すると、Excel は、現在のアカウントで Power BI にサインインし、Power BI サイトにブックを発行します。 Excel のステータス バーに注意してください。 処理が実行されていることが示されます。

![](media/service-publish-from-excel/pbi_publishingstatus.png)

完了すると、Excel から Power BI を直接開くことができます。

![](media/service-publish-from-excel/pbi_gotopbi.png)

## <a name="next-steps"></a>次の手順
[Power BI の Excel データ](service-excel-workbook-files.md)  
他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

