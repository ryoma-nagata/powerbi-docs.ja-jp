---
title: Oracle データベースへの接続
description: Oracle を Power BI Desktop に接続するために必要な手順とダウンロード
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/29/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 7c91095cf321fed56a0cb1c3c6bd1113f380a524
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878503"
---
# <a name="connect-to-an-oracle-database"></a>Oracle データベースへの接続
**Power BI Desktop** を使用して Oracle データベースに接続するには、Power BI Desktop を実行しているコンピューター上に適切な Oracle クライアント ソフトウェアをインストールする必要があります。 使用する Oracle クライアント ソフトウェアは、インストールした Power BI Desktop のバージョン ( **32 ビット**バージョンか **64 ビット**バージョン) によって異なります。

**サポートされるバージョン**:Oracle 9 以降、Oracle クライアント ソフトウェア 8.1.7 以降。

## <a name="determining-which-version-of-power-bi-desktop-is-installed"></a>インストールされている Power BI Desktop バージョンの特定
どのバージョンの Power BI Desktop がインストールされているかを特定するには、 **[ファイル] > [ヘルプ] > [バージョン情報]** の順に選択し、次に **[バージョン]** 行を確認します。 次の図の場合、Power BI Desktop の 64 ビット バージョンがインストールされています。

![](media/desktop-connect-oracle-database/connect-oracle-database_1.png)

## <a name="installing-the-oracle-client"></a>Oracle クライアントのインストール
Power BI Desktop の **32 ビット** バージョンの場合、次のリンクをクリックして **32 ビット** Oracle クライアントをダウンロードし、インストールします。

* [32-bit Oracle Data Access Components (ODAC) with Oracle Developer Tools for Visual Studio (12.1.0.2.4)](https://www.oracle.com/technetwork/topics/dotnet/utilsoft-086879.html)

Power BI Desktop の **64 ビット** バージョンの場合、次のリンクをクリックして **64 ビット** Oracle クライアントをダウンロードし、インストールします。

* [64-bit ODAC 12c Release 4 (12.1.0.2.4) for Windows x64](https://www.oracle.com/technetwork/database/windows/downloads/index-090165.html)

## <a name="connect-to-an-oracle-database"></a>Oracle データベースへの接続
一致する Oracle クライアント ドライバーがインストールされると、Oracle データベースに接続できます。 接続するには、次の手順を実行します。

1. [データの取得] ウィンドウから、 **[データベース] > [Oracle データベース]** を選択します。
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_2.png)
2. 表示される **[Oracle データベース]** ダイアログでサーバーの名前を指定し、 **[接続]** を選択します。 SID が必要な場合、次の形式を使用して指定できます:"*サーバー名/SID*"。SID はデータベースの一意名です。 "*サーバー名/SID*" の形式でうまくいかない場合は、"*サーバー名/サービス名*" を試してください。サービス名は接続時に使用した別名です。


   ![](media/desktop-connect-oracle-database/connect-oracle-database_3.png)

   > [!TIP]
   > この手順で接続に問題がある場合は、[サーバー名] フィールドで次の形式を使ってみてください。(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=host_name)(PORT=port_num))(CONNECT_DATA=(SERVICE_NAME=service_name)))
   
3. ネイティブ データベース クエリを使用してデータをインポートする場合、 **[Oracle データベース]** ダイアログで **[詳細オプション]** セクションを展開して **[SQL ステートメント]** ボックスを開き、クエリを入力します。
   
   ![](media/desktop-connect-oracle-database/connect-oracle-database_4.png)
4. [Oracle データベース] ダイアログに Oracle データベース情報 (SID やネイティブ データベース クエリといったオプションの情報を含む) を入力したら、 **[OK]** を選択して接続します。
5. Oracle データベースがデータベース ユーザー資格情報を必要とする場合、ダイアログで指示が表示されたら資格情報を入力します。


## <a name="troubleshooting"></a>トラブルシューティング

Microsoft Store から Power BI Desktop をダウンロードした場合、Oracle ドライバーの問題により Oracle データベースに接続できない可能性があります。 この問題が発生した場合は、"オブジェクト参照が設定されていません" というエラー メッセージが返されます。 この問題に対処するには、次のいずれかの操作を行ってください。

* 代わりに https://powerbi.microsoft.com/desktop から Power BI Desktop をダウンロードします。

* Microsoft Store から取得したバージョンを使用する場合は、ご利用のローカル コンピューター上で、_12.X.X\client_X_ から _12.X.X\client_X\bin_ に oraons.dll をコピーします。 X はバージョンおよびディレクトリの番号を表します。

Oracle データベースへの接続時に Power BI Gateway に **オブジェクト参照が設定されていません** というエラー メッセージが表示される場合は、「[データ ソースの管理 - Oracle](service-gateway-onprem-manage-oracle.md)」に記載されている手順に従うことで問題を解決できる場合があります。
