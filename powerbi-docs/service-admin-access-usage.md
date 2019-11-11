---
title: サインインした Power BI ユーザーを見つける
description: テナント管理者が Power BI にサインインしたユーザーを確認するには、Azure Active Directory アクセスと使用状況レポートを使用して、ユーザーを表示します。
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 63257953b89a6c96ce451783193656f9dfacf5bd
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73873741"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>サインインした Power BI ユーザーを見つける

テナント管理者が Power BI にサインインしたユーザーを確認するには、[Azure Active Directory アクセスと使用状況レポート](/azure/active-directory/reports-monitoring/concept-sign-ins)を使用して、ユーザーを表示します。

> [!NOTE]
> **サインイン** レポートでは役に立つ情報が提供されますが、各ユーザーが持つライセンスの種類は示されません。 ライセンスを表示するには、Microsoft 365 管理センターを使用します。

## <a name="requirements"></a>要件

(非管理者を含む) すべてのユーザーが自分のサインインのレポートを表示できますが、すべてのユーザーに関するレポートを表示するには、次の要件を満たす必要があります。

* テナントには Azure Active Directory Premium ライセンスが関連付けられている必要があります。

* 次のいずれかのロールである必要があります:全体管理者、セキュリティ管理者、セキュリティ閲覧者。

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Azure portal を使用してサインインを表示する

サインイン アクティビティを表示するには、次の手順のようにします。

1. **Azure portal** で、 **[Azure Active Directory]** を選択します。

1. **[監視]** で **[サインイン]** を選択します。
   
    ![[Azure Active Directory] オプションと [サインイン] オプションが強調表示されている Azure UI のスクリーンショット。](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. **[Microsoft Power BI]** または **[Power BI Gateway]** のいずれかを選択して、アプリケーションをフィルター処理し、 **[適用]** を選択します。

    **Microsoft Power BI** では、サービス関連のサインイン アクティビティでフィルター処理されます。一方、**Power BI Gateway** では、オンプレミス データ ゲートウェイに固有のサインイン アクティビティでフィルター処理されます。
   
    ![[アプリケーション] フィールドが強調表示されているサインイン フィルターのスクリーンショット。](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>データをエクスポートする

CSV ファイル形式または JSON ファイル形式で[サインイン レポートをダウンロード](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report)できます。

![[ダウンロード] ボタンのスクリーンショット。](media/service-admin-access-usage/download-sign-in-data-csv.png)

**サインイン** レポートの先頭で、 **[ダウンロード]** を選択し、次のオプションのいずれかを選択します。

* **[CSV]** : 現在フィルター処理されているデータの CSV ファイルをダウンロードします。

* **[JSON]** : 現在フィルター処理されているデータの JSON ファイルをダウンロードします。

## <a name="data-retention"></a>データのリテンション期間

サインイン関連のデータは、最大 30 日間使用できます。 詳しくは、「[Azure Active Directory レポートの保持ポリシー](/azure/active-directory/reports-monitoring/reference-reports-data-retention)」を参照してください。

## <a name="next-steps"></a>次の手順

[組織内での監査の使用](service-admin-auditing.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。