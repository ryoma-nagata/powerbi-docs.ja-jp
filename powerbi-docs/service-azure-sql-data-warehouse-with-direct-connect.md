---
title: Azure SQL Data Warehouse と DirectQuery
description: Azure SQL Data Warehouse と DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.date: 04/28/2020
LocalizationGroup: Data from databases
ms.openlocfilehash: 472eacea2a84d1f4a71d6869406e17f2ffd03e6b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82255887"
---
# <a name="azure-sql-data-warehouse-with-directquery"></a>Azure SQL Data Warehouse と DirectQuery

Azure SQL Data Warehouse と DirectQuery を使用すると、Azure SQL Data Warehouse に既に含まれているデータとメトリックに基づいて動的なレポートを作成できます。 DirectQuery を使用すると、データを探索するときにクエリが Azure SQL Data Warehouse に送り返されます。 リアルタイム クエリを SQL Data Warehouse のスケールと組み合わせることで、ユーザーはテラバイトのデータに対し、分単位で動的なレポートを作成することができます。 さらに、 **[Power BI で開く]** ボタンを使用すると、ユーザーは手動で情報を指定しなくても、Power BI を SQL Data Warehouse に直接接続することができます。

SQL Data Warehouse コネクタを使用する場合:

* 接続するときに、完全修飾のサーバー名を指定します (詳細については後述します)。
* サーバーのファイアウォール ルールが「Azure サービスに対するアクセスを許可」するように構成されていることを確認してください。
* 列の選択、フィルターの追加など、どの操作によってもクエリが直接データ ウェアハウスに対して行われます。
* タイルは、約 15 分ごとに更新するように設定されているため、更新をスケジュール設定する必要はありません。  更新は、接続するときに [詳細] 設定で調整できます。
* DirectQuery データセットの Q&A は使用できません。
* スキーマ変更は自動選択されません。

これらの制限および注意事項については、エクスペリエンスの向上に伴い変更される可能性があります。 接続するための手順の詳細を以下に示します。

## <a name="using-the-open-in-power-bi-button"></a>[Power BI で開く] ボタンの使用

> [!Important]
> Azure SQL Data Warehouse への接続性を改善しました。  Azure SQL Data Warehouse データ ソースに接続するための操作性を向上させるには、Power BI Desktop を使用します。  モデルとレポートをビルドしたら、Power BI サービスに発行できます。  Power BI サービス内の Azure SQL Data Warehouse への直接接続は、非推奨になりました。

SQL Data Warehouse と Power BI の間で移動する最も簡単な方法は、Azure portal の **[Power BI で開く]** ボタンを使用することです。 このボタンを使用すると、Power BI で新しいダッシュボードの作成をシームレスに開始できるようになります。

1. 開始するには、Azure portal の SQL Data Warehouse のインスタンスに移動します。 この時点では、SQL Data Warehouse は Azure portal にのみ表示されることに注意してください。

2. **[Power BI で開く]** ボタンをクリックする

    ![Power BI で開く](media/service-azure-sql-data-warehouse-with-direct-connect/openinpowerbi.png)

3. 自動的にサインインできない場合、または Power BI アカウントがない場合は、サインインする必要があります。

4. SQL Data Warehouse からの情報があらかじめ入力されている、SQL Data Warehouse 接続ページに移動します。 資格情報を入力し、接続をクリックして接続を作成します。

## <a name="connecting-through-power-bi"></a>Power BI 経由で接続する

SQL Data Warehouse は、Power BI の [データの取得] ページにも表示されます。 

1. ナビ ペインの下部にある **[データの取得]** を選択します。  

    ![[データの取得] ボタン](media/service-azure-sql-data-warehouse-with-direct-connect/getdatabutton.png)

2. **[データベース]** で **[取得]** を選択します。

    ![データベース](media/service-azure-sql-data-warehouse-with-direct-connect/databases.png)

3. **[SQL Data Warehouse]** \> **[接続]** の順に選択します。

    ![Azure SQL DW との直接接続](media/service-azure-sql-data-warehouse-with-direct-connect/azuresqldatawarehouseconnect.png)

4. 接続するために必要な情報を入力します。 以下の **[検索パラメーター]** セクションは、このデータが Azure portal のどこに配置されているかを示します。

    ![サーバー名](media/service-azure-sql-data-warehouse-with-direct-connect/servername.png)

    ![詳細なサーバー名](media/service-azure-sql-data-warehouse-with-direct-connect/servernamewithadvanced.png)

    ![ユーザー名](media/service-azure-sql-data-warehouse-with-direct-connect/username.png)

   > [!NOTE]
   > ユーザー名は Azure SQL Data Warehouse インスタンスで定義されているユーザーになります。

5. アスタリスクで示される、新しいタイルまたは新しく作成されたデータセットを選択すると、データセットの詳細を表示します。 このデータセットは、データベースと同じ名前になります。

    ![データセット 2](media/service-azure-sql-data-warehouse-with-direct-connect/dataset2.png)

6. すべてのテーブルと列を調べることができます。 列を選択すると、クエリがソースに送り返されて、ビジュアルが動的に作成されます。 フィルターもクエリに変換され、データ ウェアハウスに戻されます。 これらのビジュアルは、新しいレポートに保存したり、ダッシュボードに戻してピン留めしたりできます。

    ![探索 3](media/service-azure-sql-data-warehouse-with-direct-connect/explore3.png)

## <a name="finding-parameter-values"></a>パラメーターの値の見つけ方

完全修飾サーバー名とデータベース名は、Azure portal に表示されています。 この時点では、SQL Data Warehouse は Azure portal にのみ表示されることに注意してください。

![Azure Portal](media/service-azure-sql-data-warehouse-with-direct-connect/azureportal.png)

> [!NOTE]
> Power BI テナントが Azure SQL Data Warehouse と同じリージョン内にある場合、送信料は発生しません。 Power BI テナントが置かれている場所を確認するには、[こちらの手順](https://docs.microsoft.com/power-bi/service-admin-where-is-my-tenant-located)を使用してください。

[!INCLUDE [direct-query-sso](includes/direct-query-sso.md)]

## <a name="next-steps"></a>次の手順

* [Power BI とは?](fundamentals/power-bi-overview.md)  
* [Power BI のデータの取得](service-get-data.md)  
* [Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-overview-what-is/)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
