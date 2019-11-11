---
title: クライアント アプリケーションとツールで Power BI Premium データセットに接続する (プレビュー)
description: クライアント アプリケーションとツールから Power BI Premium のデータセットに接続する方法について説明します。
author: minewiskan
ms.author: owend
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 07/24/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 0364fae1648e6155cc5e5a92850861c3bedbabdc
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871901"
---
# <a name="connect-to-datasets-with-client-applications-and-tools-preview"></a>クライアント アプリケーションとツールでデータセットに接続する (プレビュー)

Power BI Premium ワークスペースとデータセットでは、Microsoft およびサード パーティのクライアント アプリケーションとツールからの*読み取り専用*接続をサポートします。 既定では、接続は有効になっています

> [!NOTE]
> この記事は、Power BI Premium のワークスペースとデータセットに読み取り専用接続を導入することのみを対象にしています。 プログラミング、特定のツールとアプリケーション、アーキテクチャ、ワークスペースとデータセットの管理に関する詳細な情報を提供することを想定して*いません*。 ここで説明されているサブジェクトには、Analysis Services 表形式モデルのデータベース アーキテクチャと管理をしっかりと理解しておく必要があります。

## <a name="protocol"></a>プロトコル

Power BI Premium では、クライアント アプリケーションとご利用のワークスペースとデータセットを管理するエンジン間の通信に、[XML for Analysis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference) (XMLA) プロトコルを使用します。 これらの接続は、一般的に XMLA エンドポイントとして参照されるものを介しています。 XMLA は、内部にある Microsoft Analysis Services エンジンによって使用されるのと同じ通信プロトコルであり、Power BI のセマンティック モデル、ガバナンス、ライフサイクル、データ管理を実行します。 

ほとんどのクライアント アプリケーションとツールでは、XMLA エンドポイントを使用することによって、エンジンと明示的に通信することはありません。 代わりに、XMLA を使用して排他的に通信する、クライアント アプリケーションとエンジン間の仲介者として、MSOLAP、ADOMD、AMO などのクライアント ライブラリを使用します。


## <a name="supported-tools"></a>サポートされているツール

次のツールでは、Power BI Premium ワークスペースとデータセットへの読み取り専用アクセスをサポートします。

**SQL Server Management Studio (SSMS)** - DAX、MDX、XMLA、TraceEvent クエリをサポートします。 バージョン 18.0 が必要です。 [こちら](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)からダウンロードしてください。 

**SQL Server Profiler** - SSMS 18.0 (プレビュー) に含まれます。このツールではサーバー イベントのトレースとデバッグを提供します。 後で分析するファイルまたはテーブルに対する各イベントのデータをキャプチャして保存できます。 SQL Server では公式に非推奨になりましたが、Profiler は引き続き SSMS に含まれており、Analysis Services と Power BI Premium で引き続きサポートされます。 詳細については、「[SQL Server Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler)」を参照してください。

**DAX Studio** - Analysis Services に対して DAX クエリを実行して分析するためのオープンソースのコミュニティ ツール。 バージョン 2.8.2 以降が必要です。 詳細については、[daxstudio.org](https://daxstudio.org/) を参照してください。

**Excel PivotTables** - Office 16.0.11326.10000 以上のクイック実行のバージョンが必要です。

**サード パーティ** - Power BI Premium のデータセットに接続、クエリを行い、使用できるクライアント データの視覚化アプリケーションとツールが含まれます。 ほとんどのツールで最新バージョンの MSOLAP クライアント ライブラリが必要ですが、一部のツールでは ADOMD が使用される可能性があります。

## <a name="client-libraries"></a>クライアント ライブラリ

クライアント ライブラリは、クライアント アプリケーションとツールで Power BI Premium ワークスペースに接続するために必要です。 Analysis Services への接続に使用されるのと同じクライアント ライブラリは、Power BI Premium でもサポートされます。 Microsoft クライアント アプリケーション (Excel、SQL Server Management Studio (SSMS)、SQL Server Data Tools (SSDT) など) では、3 つすべてのクライアント ライブラリがインストールされ、通常のアプリケーションの更新とともに更新されます。 場合によって、特にサード パーティのアプリケーションとツールでは、より新しいバージョンのクライアント ライブラリをインストールする必要がある可能性があります。 クライアント ライブラリは、毎月更新されます。 詳細については、「[Azure Analysis Services に接続するためのクライアント ライブラリ](https://docs.microsoft.com/azure/analysis-services/analysis-services-data-providers)」を参照してください。

## <a name="connecting-to-a-premium-workspace"></a>Premium ワークスペースに接続する

Premium 専用容量に割り当てられたワークスペースに接続することはできません。 専用容量に割り当てられたワークスペースには、URL 形式の接続文字列はありません。 

ワークスペースの接続文字列を取得するには、Power BI で、 **[ワークスペースの設定]** の **[Premium]** タブにある **[ワークスペース接続]** で **[コピー]** をクリックします。

![ワークスペースの接続文字列](media/service-premium-connect-tools/connect-tools-workspace-connection.png)

ワークスペースの接続には、次の URL 形式を使用して、Analysis Services サーバー名と同じようにワークスペースを指定します:   
`powerbi://api.powerbi.com/v1.0/[tenant name]/[workspace name]` 

例: `powerbi://api.powerbi.com/v1.0/contoso.com/Sales Workspace`

### <a name="to-connect-in-ssms"></a>SSMS で接続するには

**[サーバーに接続]**  >  **[サーバーの種類]** で、 **[Analysis Services]** を選択します。 **[サーバー名]** に URL を入力します。 **[認証]** で **[Active Directory - MFA サポートで汎用]** を選択して、 **[ユーザー名]** に組織のユーザー ID を入力します。 

接続されると、ワークスペースは Analysis Services サーバーとして表示され、ワークスペースのデータセットはデータベースとして表示されます。  

![SSMS](media/service-premium-connect-tools/connect-tools-ssms.png)

### <a name="initial-catalog"></a>初期カタログ

SQL Server Profiler などの一部のツールでは、*初期カタログ*の指定が必要な場合があります。 自分のワークスペースでデータセット (データベース) を指定します。 **[サーバーに接続]** で **[オプション]** をクリックします。 **[サーバーに接続]** ダイアログの **[接続プロパティ]** タブで、 **[データベースに接続]** にデータセット名を入力します。

### <a name="duplicate-workspace-name"></a>重複するワークスペース名

別のワークスペースと同じ名前でワークスペースに接続している場合、次のエラーが表示されることがあります: **powerbi://api.powerbi.com/v1.0/[テナント名]/[ワークスペース名] に接続できません。**

このエラーを回避するには、ワークスペース名に加えて、ObjectIDGuid を指定します。これは URL のワークスペースの objectID からコピーできます。 objectID を接続 URL に追加します。 例: 'powerbi://api.powerbi.com/v1.0/myorg/Contoso Sales - 9d83d204-82a9-4b36-98f2-a40099093830'

### <a name="duplicate-dataset-name"></a>重複するデータセット名

同じワークスペース内の別のデータセットと同じ名前でデータセットに接続している場合、データセット GUID をデータセット名に追加します。 SSMS のワークスペースに接続されている場合、データセット名*および* GUID の両方を取得できます。 

### <a name="delay-in-datasets-shown"></a>データセットの表示の遅延

ワークスペースに接続している場合、新しいデータセット、削除されたデータセット、名前を変更したデータセットからの変更は、表示されるまで最大 5 分かかることがあります。 

### <a name="unsupported-datasets"></a>サポートされていないデータセット

次のデータセットは、XMLA エンドポイントを使用してアクセスすることはできません。 次のデータセットは、SSMS のワークスペースやその他のツールには表示*されません*。 

- Analysis Services モデルに対するライブ接続でのデータセット 
- REST API を使用したプッシュ データでのデータセット
- Excel ブックのデータセット 

次のデータセットは、Power BI サービスではサポートされていません。   

- Power BI データセットに対するライブ接続でのデータセット

### <a name="roles-and-role-memberships"></a>ロールとロールのメンバーシップ

現時点では、モデルのロールとロールのメンバーシップは、XMLA エンドポイントを使用して検出も表示もされません。

## <a name="disable-connectivity"></a>接続を無効にする

既定では、XMLA エンドポイント接続はデータセット ワークロードに対して有効になっています。 [ワークロードの設定](service-admin-premium-workloads.md#workload-settings)で接続を無効にすることができます。

## <a name="audit-logs"></a>監査ログ 

クライアント アプリケーションとツールでワークスペースに接続する場合、XMLA エンドポイントからのアクセスは **GetWorkspaces** 操作で Power BI 監査ログに記録されます。 詳細については、[Power BI の監査](service-admin-auditing.md)に関するページを参照してください。

## <a name="see-also"></a>参照

[Analysis Services リファレンス](https://docs.microsoft.com/bi-reference/#pivot=home&panel=home-all)   
[SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)   
[SQL Server Analysis Services 表形式のプロトコル](https://docs.microsoft.com/openspecs/sql_server_protocols/ms-ssas-t/b98ed40e-c27a-4988-ab2d-c9c904fe13cf)   
[動的管理ビュー (DMV)](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)   


他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
