---
title: スケジュールされた更新の構成
description: ここでは、ゲートウェイを選択して、スケジュールされた更新を構成する手順を説明します。
author: mgblythe
ms.reviewer: kayu''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/06/2019
ms.author: mblythe
LocalizationGroup: Data refresh
ms.openlocfilehash: 89f8b3d609b9433cc85d8af709eec828f924ad8e
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73860694"
---
# <a name="configure-scheduled-refresh"></a>スケジュールされた更新の構成

>[!NOTE]
>2 か月間操作が行われなかった場合、データセットに対するスケジュールされた更新は一時停止されます。 詳しくは、この記事で後述する「[*スケジュールされた更新*](#scheduled-refresh)」をご覧ください。
>
>

**[今すぐ更新]** と **[更新のスケジュール設定]** を使用したスケジュールされた更新をデータセットがサポートしている場合、更新を正常に行うために重要な要件と設定がいくつかあります。 **ゲートウェイの接続**、**データ ソースの資格情報**、**更新のスケジュール設定**です。 それぞれを詳しく見てみましょう。

ここでは、[オンプレミス データ ゲートウェイ (個人用モード)](service-gateway-personal-mode.md) と[オンプレミス データ ゲートウェイ](service-gateway-onprem.md)の両方で使用可能なオプションを説明します。

次の操作を行うと、 **[スケジュールされている更新]** 画面に移動できます。

1. **[データセット]** の下で一覧表示されたデータセットの横にある**その他のオプション** (...) を選択します。
2. **[更新のスケジュール設定]** を選択します。

    ![更新のスケジュール設定](media/refresh-scheduled-refresh/dataset-menu.png)

## <a name="gateway-connection"></a>ゲートウェイ接続
パーソナル ゲートウェイまたはエンタープライズ ゲートウェイのどちらをオンラインにして使用できるようにしているかによって、ここに表示されるオプションが変わります。

使用できるゲートウェイがない場合は、 **[ゲートウェイ接続]** が無効になっています。 パーソナル ゲートウェイをインストールする方法を示すメッセージも表示されます。

![ゲートウェイが構成されていません](media/refresh-scheduled-refresh/gateway-not-configured.png)

パーソナル ゲートウェイを構成している場合は、オンラインになっていると、パーソナル ゲートウェイを選択できます。 使用できない場合は、パーソナル ゲートウェイはオフラインとして表示されます。

![ゲートウェイ接続](media/refresh-scheduled-refresh/gateway-connection.png)

エンタープライズ ゲートウェイが使用できる場合は、エンタープライズ ゲートウェイも選択できます。 任意のゲートウェイ用に構成されたデータ ソースの **[ユーザー]** タブにアカウントが表示されている場合は、使用可能なエンタープライズ ゲートウェイのみ表示されます。

## <a name="data-source-credentials"></a>データ ソース資格情報
### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
パーソナル ゲートウェイを使用してデータを更新している場合は、バックエンド データ ソースに接続するために資格情報を指定する必要があります。 オンライン サービスからコンテンツ パックに接続した場合は、接続用に入力した資格情報は、スケジュールされた更新に引き継がれます。

![データ ソース資格情報](media/refresh-scheduled-refresh/data-source-credentials-pgw.png)

必要なのは、このデータセットで更新を初めて使用するときにデータ ソースにサインインすることだけです。 入力した後は、資格情報はデータセットに保持されます。

> [!NOTE]
> 一部の認証方法では、データ ソースへのサインインに使用するパスワードの有効期限が切れた場合、またはパスワードが変更された場合は、 **[データ ソースの資格情報]** でもデータ ソースのパスワードを変更する必要があります。
>
>

問題が生じた場合、問題は Windows にサインインしてサービスを開始できなかったためにゲートウェイがオフラインであること、または Power BI が更新されたデータに対してクエリを実行するためにデータ ソースにサインインできなかったことのいずれかに関係しています。 更新に失敗した場合は、データセットの設定を確認します。 ゲートウェイ サービスがオフラインの場合、 **[状態]** にエラーが表示されています。 Power BI がデータ ソースにサインインできない場合、データ ソースの資格情報でエラーが表示されます。

### <a name="on-premises-data-gateway"></a>オンプレミス データ ゲートウェイ
オンプレミス データ ゲートウェイを使用してデータを更新している場合は、資格情報を指定する必要はありません。ゲートウェイの管理者によってデータ ソースに定義されているためです。

![[更新のスケジュール設定] コマンド](media/refresh-scheduled-refresh/data-source-credentials-egw.png)

> [!NOTE]
> データ更新のためにオンプレミスの SharePoint に接続するとき、Power BI は "*匿名*"、"*基本*"、および "*Windows (NTLM/Kerberos)* " の認証メカニズムのみをサポートします。 オンプレミスの SharePoint データ ソースのデータ更新では、Power BI は "*ADFS*" または "*フォーム ベース認証*" のメカニズムをサポートしません。
>
>

## <a name="scheduled-refresh"></a>スケジュールされている更新
**[スケジュールされている更新]** セクションでは、データセットを更新する頻度と時間帯を定義します。 一部のデータ ソースでは、更新を構成できるようにするためにゲートウェイは不要です。その他のデータ ソースでは、ゲートウェイが必要となります。

**[データを最新の状態に保つ]** スライダーを **[オン]** に設定して、設定を構成します。

> [!NOTE]
> Power BI サービスでは、スケジュールされた更新時間の **15 分**以内にデータの更新を開始することを目標にしています。
>
>

![[スケジュールされている更新] ダイアログ ボックス](media/refresh-scheduled-refresh/scheduled-refresh.png)

> [!NOTE]
> 2 か月間操作が行われなかった場合、データセットに対するスケジュールされた更新は一時停止されます。 データセットに基づいて作成されたダッシュボードまたはレポートにアクセスするユーザーがいない場合、そのデータセットは非アクティブと見なされます。 その時点で、スケジュールされた更新が一時停止されており、データセットの更新スケジュールが**無効**と表示されることを示すメールが、データセットの所有者に送られます。 データセットに基づいて作成されたダッシュボードまたはレポートに再度アクセスするだけで、スケジュールされた更新は再開されます。"
>
>

## <a name="whats-supported"></a>サポートされている機能
スケジュールされた更新のために、さまざまなゲートウェイに応じて一定のデータセットがサポートされています。 ここでは、使用できるデータセットを理解するうえで参考になる情報を紹介します。

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
**Power BI Desktop**

* Power BI Desktop の **[データの取得]** および [クエリ エディター] に表示されるすべてのオンライン データ ソース。
* Hadoop ファイル (HDFS) と Microsoft Exchange を除く、Power BI Desktop の **[データの取得]** および [クエリ エディター] に表示されるすべてのオンプレミスのデータ ソース。

**Excel**

> [!NOTE]
> Excel 2016 以降では、Power Query はリボンの **[データ]** セクションで、 **[データの取得と変換]** の下に表示されます。
>
>

* Power Query に表示されるすべてのオンライン データ ソース
* Hadoop ファイル (HDFS) と Microsoft Exchange を除く、Power Query に表示されるすべてのオンプレミスのデータ ソース
* Power Pivot に表示されるすべてのオンライン データ ソース
* Hadoop ファイル (HDFS) と Microsoft Exchange を除く、Power Pivot に表示されるすべてのオンプレミスのデータ ソース

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

## <a name="troubleshooting"></a>トラブルシューティング
期待どおりにデータが更新されないことがあります。 通常、これはゲートウェイに関係する問題です。 ツールと既知の問題については、ゲートウェイに関するトラブルシューティングの記事を参照してください。

- [オンプレミス データ ゲートウェイのトラブルシューティング](service-gateway-onprem-tshoot.md)
- [Power BI Gateway - Personal のトラブルシューティング](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>次の手順
- [Power BI でのデータの更新](refresh-data.md)  
- [Power BI Gateway - Personal](service-gateway-personal-mode.md)  
- [オンプレミス データ ゲートウェイ (個人用モード)](service-gateway-onprem.md)  
- [オンプレミス データ ゲートウェイのトラブルシューティング](service-gateway-onprem-tshoot.md)  
- [Power BI Gateway - Personal のトラブルシューティング](service-admin-troubleshooting-power-bi-personal-gateway.md)  

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。

