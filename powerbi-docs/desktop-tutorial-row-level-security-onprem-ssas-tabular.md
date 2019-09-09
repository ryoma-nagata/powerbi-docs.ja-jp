---
title: Power BI での Analysis サービス表形式モデルを使用した動的な行レベルのセキュリティ
description: Analysis Services 表形式モデルを使用した動的な行レベル セキュリティ
author: selvarms
manager: amitaro
ms.reviewer: davidi
editor: davidi
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 05/28/2019
ms.author: selvar
LocalizationGroup: Connect to data
ms.openlocfilehash: bbd40173bd10abf312ff382a9452f7636234bc95
ms.sourcegitcommit: 9665997274301b228f45aa7250ba557e90164a4d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70751691"
---
# <a name="dynamic-row-level-security-with-analysis-services-tabular-model"></a>Analysis Services 表形式モデルを使用した動的な行レベル セキュリティ

このチュートリアルでは、サンプル データセットを使って以下の手順に従い、**Azure Analysis Services 表形式モデル**で[**行レベルのセキュリティ**](service-admin-rls.md)を実装し、それを Power BI レポートで使用する方法を示します。 

* [**AdventureworksDW2012**](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) データベースに新しいセキュリティ テーブルを作成する
* 必要なファクト テーブルとディメンション テーブルを持つ表形式モデルを作成する
* ユーザー ロールとアクセス許可を定義する
* モデルを **Analysis Services 表形式** インスタンスにデプロイする
* レポートにアクセスするユーザーに合ったデータを表示する Power BI Desktop レポートをビルドする
* レポートを **Power BI サービス**にデプロイする
* レポートに基づいて新しいダッシュボードを作成する
* 同僚とダッシュボードを共有する 

このチュートリアルでは [**AdventureworksDW2012** データベース](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)が必要です。

## <a name="task-1-create-the-user-security-table-and-define-data-relationship"></a>タスク 1:ユーザーのセキュリティ テーブルを作成し、データのリレーションシップを定義する

**SQL Server Analysis Services (SSAS) 表形式**モデルを使用して、行レベルの動的なセキュリティを定義する方法を説明する多くの記事を見つけることができます。 サンプルでは、[行フィルターを使用した動的なセキュリティの実装](https://docs.microsoft.com/analysis-services/tutorial-tabular-1200/supplemental-lesson-implement-dynamic-security-by-using-row-filters)に関するページを使用します。 

ここに示す手順では、**AdventureworksDW2012** リレーショナル データベースを使用する必要があります。

1. **AdventureworksDW2012** では、以下に示すように **DimUserSecurity** テーブルを作成します。 [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) を使用して、テーブルを作成することができます。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable.png)

2. テーブルを作成して保存したら、以下に示すように、**DimUserSecurity** テーブルの **SalesTerritoryID** 列と **DimSalesTerritory** テーブルの **SalesTerritoryKey** 列の間にリレーションシップを確立する必要があります。 

   **SSMS** で、**DimUserSecurity** テーブルを右クリックし、 **[デザイン]** を選択します。 その後、 **[テーブル デザイナー]、[リレーションシップ]** の順に選択します。完了したら、テーブルを保存します。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_keys.png)

3. テーブルにユーザーを追加します。**DimUserSecurity** テーブルを右クリックし、 **[上位 200 行の編集]** を選択します。 ユーザーを追加すると、**DimUserSecurity** テーブルは、独自のユーザーを使用した場合でも、次のように表示されるはずです。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_users.png)
   
   これらのユーザーは以降のタスクで表示されます。

4. 次に、**DimSalesTerritory** テーブルで "*内部結合*" を行います。このテーブルには、ユーザーに関連付けられている地域の詳細が示されます。 ここでは SQL コードで "*内部結合*" を行います。図には、その後、テーブルがどのように表示されるかが示されています。
   
       select b.SalesTerritoryCountry, b.SalesTerritoryRegion, a.EmployeeID, a.FirstName, a.LastName, a.UserName from [dbo].[DimUserSecurity] as a join  [dbo].[DimSalesTerritory] as b on a.[SalesTerritoryID] = b.[SalesTerritoryKey]
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/createusersecuritytable_join_users.png)

   図には、**手順 2** で作成されたリレーションシップのおかげで、販売地域ごとの担当者が示されます。 たとえば、**Jon Doe** は**オーストラリア**の担当であることがわかります。 

## <a name="task-2-create-the-tabular-model-with-facts-and-dimension-tables"></a>タスク 2:ファクト テーブルとディメンション テーブルを持つ表形式モデルを作成する

1. リレーショナル データ ウェアハウスが準備できたら、表形式モデルを定義する必要があります。 モデルは [**SQL Server Data Tools (SSDT)** ](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools) を使用して作成できます。 詳細については、「[新しいテーブル モデル プロジェクトの作成](https://msdn.microsoft.com/library/hh231689.aspx)」を参照してください。

2. 次に示すように、モデルに必要なすべてのテーブルをインポートします。
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/ssdt_model.png)

3. 必要なテーブルをインポートしたら、**読み取り**権限を持つ **SalesTerritoryUsers** という役割を定義する必要があります。 SQL Server Data Tools で **[モデル]** メニューを選択してから、 **[ロール]** を選びます。 **[ロール マネージャー]** ダイアログ ボックスで、 **[新規]** を選択します。

4. **[ロール マネージャー]** の **[メンバー]** タブで、**タスク 1 の手順 3** で **DimUserSecurity** テーブルに定義したユーザーを追加します。
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager.png)

5. 次に、 **[行フィルター]** タブの下に示されている **DimSalesTerritory** と **DimUserSecurity** の両方のテーブルに適切な関数を追加します。
   
    ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/rolemanager_complete.png)

6. この手順では、**LOOKUPVALUE** 関数を使用して、Windows ユーザー名が **USERNAME** 関数によって返されるものと一致する列の値を返すようにします。 その後、**LOOKUPVALUE** で返された値が、同じテーブルまたは関連テーブルのものと一致する場所にクエリを制限することができます。 **[DAX フィルター]** 列に、次の数式を入力します。
   
       =DimSalesTerritory[SalesTerritoryKey]=LOOKUPVALUE(DimUserSecurity[SalesTerritoryID], DimUserSecurity[UserName], USERNAME(), DimUserSecurity[SalesTerritoryID], DimSalesTerritory[SalesTerritoryKey])

    この数式では、**LOOKUPVALUE** 関数は、**DimUserSecurity[UserName]** が現在ログオンしている Windows ユーザー名と同じで、**DimUserSecurity[SalesTerritoryID]** が **DimSalesTerritory[SalesTerritoryKey]** と同じである場合に、**DimUserSecurity[SalesTerritoryID]** 列のすべての値を返します。
   
    > [!IMPORTANT]
    > 行レベルのセキュリティを使用している場合、DAX 関数の [USERELATIONSHIP](https://msdn.microsoft.com/query-bi/dax/userelationship-function-dax) はサポートされません。

   その後、**LOOKUPVALUE** によって返される Sales セットの SalesTerritoryKey を使用して、**DimSalesTerritory** に示される行が制限されます。 **SalesTerritoryKey** 値が **LOOKUPVALUE** 関数によって返される ID 内にある行のみが表示されます。

7. **DimUserSecurity** テーブルについては、 **[DAX フィルター]** 列に、次の数式を追加します。
   
       =FALSE()

    この数式では、すべての列が `false` に解決されるように指定します。これは、**DimUserSecurity** テーブル列に対してクエリを実行できないことを意味します。

8. この時点で、モデルを処理してデプロイする必要があります。 詳細については、[デプロイに関する記事](https://msdn.microsoft.com/library/hh231693.aspx)を参照してください。

## <a name="task-3-add-data-sources-within-your-on-premises-data-gateway"></a>タスク 3:オンプレミス データ ゲートウェイ内のデータ ソースを追加する

表形式モデルがデプロイされ、使用できるようになったら、Analysis Services 表形式サーバーへのデータ ソース接続を追加する必要があります。

1. **Power BI サービス**からオンプレミスの分析サービスにアクセスできるようにするには、使用している環境に **[オンプレミス データ ゲートウェイ](service-gateway-onprem.md)** がインストールされ、構成されている必要があります。

2. ゲートウェイを正しく構成したら、**Analysis Services** 表形式インスタンス用のデータ ソース接続を作成する必要があります。 詳細については、「[データ ソースの管理 - Analysis Services](service-gateway-enterprise-manage-ssas.md)」を参照してください。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_gateway.png)

  前の手順が完了していれば、ゲートウェイは構成されており、オンプレミスの **Analysis Services** データ ソースと対話できるようになっています。

## <a name="task-4-create-report-based-on-analysis-services-tabular-model-using-power-bi-desktop"></a>タスク 4:Power BI Desktop を使用して Analysis Services 表形式モデルに基づくレポートを作成する

1. **Power BI Desktop** を起動して、 **[データの取得]、[データベース]** の順に選択します。

2. データ ソース リストから、 **[SQL Server Analysis Services データベース]** を選択して、 **[接続]** を選びます。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata.png)

3. **Analysis Services** 表形式インスタンスの詳細を入力して、 **[ライブ接続]** を選択します。 **[OK]** を選択します。 **Power BI** では、動的セキュリティは**ライブ接続**でのみ機能します。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

4. **Analysis Services** インスタンスにデプロイされたモデルがあることがわかります。 該当するモデルを選択してから、 **[OK]** を選びます。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/getdata_connectlive.png)

   これで、**Power BI Desktop** では、 **[フィールド]** ウィンドウのキャンバスの右側に使用可能なフィールドがすべて表示されます。

5. 右側の **[フィールド]** ウィンドウで、**FactInternetSales** テーブルからは **SalesAmount** メジャーを、**SalesTerritory** テーブルからは **SalesTerritoryRegion** ディメンションを選択します。

6. このレポートをシンプルなものにしておくために、この時点では列を追加しません。 データをよりわかりやすくするために、視覚化を**ドーナツ グラフ**に変更します。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart.png)

7. レポートの準備ができたら、Power BI ポータルに直接発行できます。 **Power BI Desktop** の **[ホーム]** リボンで、 **[発行]** を選択します。

## <a name="task-5-create-and-share-a-dashboard"></a>タスク 5:ダッシュボードを作成して共有する

1. レポートを作成し、それを **Power BI** サービスに発行しました。 これで、前の手順で作成された例を使用して、モデル セキュリティ シナリオを示すことができます。
   
   ロールが**販売マネージャー**である Sumit は、あらゆる販売地域からのデータを表示することができます。 Sumit はこのレポート (前のタスクの手順で作成されたレポート) を作成し、Power BI サービスに発行します。
   
   Sumit がレポートを発行したら、次の手順では、そのレポートに基づいて、**TabularDynamicSec** というダッシュボードを Power BI サービスで作成します。 次の図で、Sumit がすべての販売地域に対応するデータを表示できることがわかります。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/donut_chart_1.png)

2. ここで、Sumit は、オーストラリア地域の販売担当である Jon Doe という同僚とダッシュボードを共有します。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/user_jon_doe.png)
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/pbi_dashboard.png)

3. Jon Doe が **Power BI** サービスにログインし、Sumit が作成した共有ダッシュボードを表示した場合、自分の地域の売り上げ**のみ**が表示されるはずです。 
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/dashboard_jon_doe.png)

    お疲れ様でした。 **Power BI サービス**には、オンプレミスの **Analysis Services** 表形式モデルで定義された動的な行レベルのセキュリティが表示されます。 Power BI では **EffectiveUserName** プロパティを使用し、現在の Power BI ユーザーの資格情報をオンプレミス データ ソースに送信してクエリを実行します。

## <a name="task-6-understand-what-happens-behind-the-scenes"></a>タスク 6:バックグラウンドでの動作を理解する

このタスクでは [SQL Profiler](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler) に慣れていることを前提とします。これは、オンプレミスの SSAS 表形式インスタンスで SQL Server プロファイラー トレースをキャプチャする必要があるためです。

1. ユーザー (Jon Doe) が Power BI サービスのダッシュボードにアクセスすると、すぐにセッションが初期化されます。 **salesterritoryusers** 役割は、 **<EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>** などの有効なユーザー名ですぐに有効になることがわかります。
   
       <PropertyList><Catalog>DefinedSalesTabular</Catalog><Timeout>600</Timeout><Content>SchemaData</Content><Format>Tabular</Format><AxisFormat>TupleFormat</AxisFormat><BeginRange>-1</BeginRange><EndRange>-1</EndRange><ShowHiddenCubes>false</ShowHiddenCubes><VisualMode>0</VisualMode><DbpropMsmdFlattened2>true</DbpropMsmdFlattened2><SspropInitAppName>PowerBI</SspropInitAppName><SecuredCellValue>0</SecuredCellValue><ImpactAnalysis>false</ImpactAnalysis><SQLQueryMode>Calculated</SQLQueryMode><ClientProcessID>6408</ClientProcessID><Cube>Model</Cube><ReturnCellProperties>true</ReturnCellProperties><CommitTimeout>0</CommitTimeout><ForceCommitTimeout>0</ForceCommitTimeout><ExecutionMode>Execute</ExecutionMode><RealTimeOlap>false</RealTimeOlap><MdxMissingMemberMode>Default</MdxMissingMemberMode><DisablePrefetchFacts>false</DisablePrefetchFacts><UpdateIsolationLevel>2</UpdateIsolationLevel><DbpropMsmdOptimizeResponse>0</DbpropMsmdOptimizeResponse><ResponseEncoding>Default</ResponseEncoding><DirectQueryMode>Default</DirectQueryMode><DbpropMsmdActivityID>4ea2a372-dd2f-4edd-a8ca-1b909b4165b5</DbpropMsmdActivityID><DbpropMsmdRequestID>2313cf77-b881-015d-e6da-eda9846d42db</DbpropMsmdRequestID><LocaleIdentifier>1033</LocaleIdentifier><EffectiveUserName>jondoe@moonneo.com</EffectiveUserName></PropertyList>

2. 有効なユーザー名要求に基づいて、Analysis Services では、ローカルの Active Directory のクエリの実行後に実際の moonneo\jondoe 資格情報に要求を変換します。 **Analysis Services** で資格情報が取得されると、**Analysis Services** によって、ユーザーに表示およびアクセス権限のあるデータが返されます。

3. ダッシュボードでさらにアクティビティが発生した場合、たとえば、Jon Doe が SQL Profiler を使用してダッシュボードから基になるレポートに移動した場合、特定のクエリが DAX クエリとして Analysis Services 表形式モデルに返されることがわかります。
   
   ![](media/desktop-tutorial-row-level-security-onprem-ssas-tabular/profiler1.png)

4. また、レポートのデータを取り込むために以下のような DAX クエリが実行されることがわかります。
   
   ```
   EVALUATE
     ROW(
       "SumEmployeeKey", CALCULATE(SUM(Employee[EmployeeKey]))
     )
   
   <PropertyList xmlns="urn:schemas-microsoft-com:xml-analysis">``
             <Catalog>DefinedSalesTabular</Catalog>
             <Cube>Model</Cube>
             <SspropInitAppName>PowerBI</SspropInitAppName>
             <EffectiveUserName>jondoe@moonneo.com</EffectiveUserName>
             <LocaleIdentifier>1033</LocaleIdentifier>
             <ClientProcessID>6408</ClientProcessID>
             <Format>Tabular</Format>
             <Content>SchemaData</Content>
             <Timeout>600</Timeout>
             <DbpropMsmdRequestID>8510d758-f07b-a025-8fb3-a0540189ff79</DbpropMsmdRequestID>
             <DbPropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbPropMsmdActivityID>
             <ReturnCellProperties>true</ReturnCellProperties>
             <DbpropMsmdFlattened2>true</DbpropMsmdFlattened2>
             <DbpropMsmdActivityID>f2dbe8a3-ef51-4d70-a879-5f02a502b2c3</DbpropMsmdActivityID>
           </PropertyList>
   ```

## <a name="considerations"></a>考慮事項

* Power BI でオンプレミスの行レベル セキュリティを使用できるのは、ライブ接続の場合のみです。

* モデル処理後のデータでの変更は、Power BI サービスからの**ライブ接続**に関するレポートにアクセスするユーザーに対してすぐに使用可能となります。

