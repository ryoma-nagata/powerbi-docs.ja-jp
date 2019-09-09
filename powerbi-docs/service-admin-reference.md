---
title: 管理者のための PowerShell コマンドレット、REST API、.NET SDK
description: スクリプトとプログラミング API を使って Power BI を管理する方法について説明します。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: da19eaffff7abfd8edd745cdb58c008ea40eee8a
ms.sourcegitcommit: 9665997274301b228f45aa7250ba557e90164a4d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70751499"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>Power BI 管理のための PowerShell コマンドレット、REST API、.NET SDK
Power BI では、管理者が PowerShell コマンドレットを使用して一般的なタスクのスクリプトを作成できます。 REST API も公開され、管理ソリューションを開発するための .NET SDK が提供されます。 このトピックでは、コマンドレットの一覧と、それに対応する SDK メソッドおよび REST API エンドポイントを示します。 詳細については、次のトピックを参照してください。

- PowerShell の[ダウンロード](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/)と[ドキュメント](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps)
- REST API の[ドキュメント](https://docs.microsoft.com/rest/api/power-bi/admin)
- .NET SDK の[ダウンロード](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)

> 以下のコマンドレットを管理用のテナントに対して動作させるには、`-Scope Organization` と共に呼び出す必要があります。

| **コマンドレット名** | **エイリアス** | **SDK メソッド** | **REST API エンドポイント** | **説明** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | 該当なし | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | 指定されたデータセットのデータ ソースを取得します。 |
| `Get-PowerBIDataset` | 該当なし | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | Power BI テナント内の、データセットの完全な一覧を取得します。 |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | Power BI テナント内の、ワークスペースの完全な一覧を取得します。 |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | 指定されたワークスペースのメンバーとしてユーザーを追加します。 |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | 指定されたワークスペースのメンバーシップ一覧からユーザーを削除します。 |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | 削除されたワークスペースを復元します。 |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | 指定されたワークスペースのプロパティを更新します。 |
| `Get-PowerBIDataset -WorkspaceId` | 該当なし | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | 指定されたワークスペース内のデータセットを取得します。 |
| `Get-PowerBIReport` | 該当なし | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | Power BI テナント内の、レポートの完全な一覧を取得します。 |
| `Get-PowerBIDashboard` | 該当なし | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | Power BI テナント内の、ダッシュボードの完全な一覧を取得します。 |
| `Get-PowerBIDashboard -WorkspaceId` | 該当なし | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | 指定されたワークスペース内のダッシュボードを取得します。 |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | 指定したダッシュボードのタイルを取得します。 |
| `Get-PowerBIReport` | 該当なし | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | 指定されたワークスペース内のレポートを取得します。 |
| `Get-PowerBIImport` | 該当なし | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | Power BI テナント内の、インポートの完全な一覧を取得します。 |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | 該当なし | 該当なし | Power BI にログインし、セッションを開始します。 |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | 該当なし | 該当なし | Power BI からログアウトし、既存のセッションを終了します。 |
| `Invoke-PowerBIRestMethod`| 該当なし | 該当なし | 該当なし | Power BI に任意の REST API 呼び出しを送信します。 |
| `Get-PowerBIAccessToken`| 該当なし | 該当なし | 該当なし | セッションの Power BI のアクセス トークンを取得します。 |
| `Resolve-PowerBIError`| 該当なし | 該当なし | 該当なし | 失敗したコマンドレットの呼び出しの詳細なエラー情報を取得します。 |
