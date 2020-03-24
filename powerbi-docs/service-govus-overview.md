---
title: 米国政府顧客向け Power BI - 概要
description: 米国政府機関のお客様は、Power BI Pro サブスクリプションを Office 365 Government プランに追加できます。 このサービスの説明では、サインアップして利用可能な機能を確認する方法について説明します。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/13/2020
ms.author: kfollis
LocalizationGroup: Get started
ms.openlocfilehash: b36bc6d23b56b4118f848ad9fa4e8f39dbc65d2d
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376726"
---
# <a name="power-bi-for-us-government-customers"></a>米国政府顧客向け Power BI
この記事は、Office 365 Government プランの一部として Power BI をデプロイする米国政府機関のお客様を対象としています。 Government プランは、米国のコンプライアンスとセキュリティ標準を満たする必要がある組織の固有のニーズに合うように設計されています。 米国政府機関のお客様向けに設計された Power BI サービスは、Power BI サービスの商用バージョンとは異なります。 これらの機能の相違点と能力について、以下のセクションで説明します。

## <a name="add-power-bi-to-your-office-365-government-plan"></a>Office 365 Government プランに Power BI を追加する

Power BI US Government サブスクリプションを取得してユーザーにライセンスを割り当てる前に、Office 365 Government プランに登録する必要があります。 組織に既に Office 365 Government プランがある場合は、「[Power BI Pro Government サブスクリプションを購入する](#purchase-a-power-bi-pro-government-subscription)」に進んでください。

### <a name="enroll-in-office-365-government-plan"></a>Office 365 Government プランに登録する

新規のお客様は、Government プランにサインアップする前に、組織の資格を検証する必要があります。  [Office 365 for Government 適格性検証フォーム](https://www.microsoft.com/microsoft-365/government/eligibility-validation)を完成させることから始めます。 組織に適したプランを確実に選択するには、[Office 365 US Government サービスの説明](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government)を参照してください。

> [!NOTE]
> Power BI を既に商用環境にデプロイ済みで、US Government クラウドに移行したい場合は、新しい Power BI Pro サブスクリプションを Office 365 Government プランに追加する必要があります。 次に、米国政府向けの Power BI サービスに商用データをレプリケートし、商用ライセンスの割り当てをユーザー アカウントから削除してから、Power BI Pro Government ライセンスをユーザー アカウントに割り当てます。
>
>

### <a name="government-cloud-instances"></a>Government クラウドのインスタンス
Office 365 には、政府機関のさまざまなコンプライアンス要件を満たすための複数の環境が用意されています。 各環境で提供される内容の詳細については、リンク先のサービスの説明を参照してください。

* [Office 365 Government Community Cloud (GCC)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc) は、連邦政府、州政府、および地方自治体向けに設計されています。

* [Office 365 Government Community Cloud High (GCC-High)](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod) は、連邦政府機関、軍需産業、航空宇宙産業、および機密扱いではないが統制している情報を保持しているその他の組織向けに設計されています。 この環境は、国際武器取引規則 (ITAR) のデータまたは国防省調達規則 (DFARS) に関する要件がある、国家安全保障に関わる組織と企業に適しています。

* [Office 365 DoD 環境](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/gcc-high-and-dod)は、米国国防総省専用に設計されています。 

### <a name="purchase-a-power-bi-pro-government-subscription"></a>Power BI Pro Government サブスクリプションを購入する

Office 365 のデプロイ後に、Power BI サブスクリプションを追加できます。 [米国政府組織の登録](service-govus-signup.md#existing-office-government-cloud-customers)に関するページの詳細なガイダンスに従って、Power BI Pro Government サービスを購入します。 Power BI を使用する必要があるすべてのユーザーに割り当てできる数のライセンスを購入した後、それらのライセンスを個々のユーザー アカウントに割り当てます。

> [!IMPORTANT]
> Power BI US Government は、無料ライセンスとして利用することはできません。 Government Community Cloud にアクセスするには、各ユーザーに Pro ライセンスが割り当てられている必要があります。 無料ライセンスが割り当てられているユーザー アカウントには、商用クラウドへのアクセスのみが許可され、認証とアクセスの問題が発生します。 Power BI Premium を購入している場合は、ユーザー アクセスを有効にするために Pro ライセンスを割り当てる必要はありません。  レポートが Premium 容量に発行されている限り、組織内のすべてのユーザーが共有されているレポートにアクセスできます。 ライセンスの種類の違いを確認するには、「[Power BI サービスのライセンスの種類別機能](service-features-license-type.md)」を参照してください。
>
>

## <a name="connect-to-power-bi-for-us-government"></a>米国政府向け Power BI に接続する

米国政府向け Power BI に接続するには、商用ユーザー向けとは別の URL を使用します。 Power BI にサインインするには、次の URL を使用します。

| 商用バージョンの URL | US Government バージョンの URL | GCC High 用の米国政府向け URL |
| --- | --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) | [https://app.high.powerbigov.us](https://app.high.powerbigov.us) |

お使いのアカウントを複数のクラウドにプロビジョニングできます。 その場合は、Power BI Desktop を使用するときのサインイン時に、接続先のクラウドを選択できます。

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>行政機関向け Azure Cloud Services とグローバルな Azure Cloud Services 間の接続

Azure は複数のクラウドに分散されています。 既定では、クラウド固有のインスタンスへの接続を開くファイアウォール規則を有効にすることができますが、クラウド間ネットワークはこれとは異なります。  パブリック クラウド内のサービスと Government Community Cloud 内のサービスの間で通信を行うには、固有のファイアウォール規則を構成する必要があります。 たとえば、Power BI の政府機関向けクラウドのデプロイから SQL のパブリック クラウド インスタンスにアクセスする場合は、SQL のファイアウォール規則が必要です。 次のデータセンターの Azure Government クラウドへの接続を許可するには、SQL の固有のファイアウォール規則を構成します。

* USGov アイオワ州
* USGov バージニア州
* USGov テキサス
* USGov アリゾナ

パブリック クラウドでは、IP 範囲を使用できます。 US Government クラウドの IP 範囲を取得するには、[Azure IP Ranges and Service Tags – US Government Cloud ](https://www.microsoft.com/download/details.aspx?id=57063) (Azure IP 範囲とサービス タグ ｰ US Government クラウド) ファイルをダウンロードしてください。 

SQL でファイアウォールを設定するには、「[IP ファイアウォール規則の作成および管理](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure#create-and-manage-ip-firewall-rules)」の手順に従ってください。

## <a name="power-bi-feature-availability"></a>Power BI の機能の利用可能性

Government クラウドのお客様の要件に対応するため、Government プランと商用プランにはいくつかの違いがあります。 次の表で、各 Government 環境で使用できる機能を確認してください。

|特徴 |   |GCC |GCC-High |DoD|
|------|------|------|------|------|
|管理|無料ライセンス|利用不可|利用不可|利用不可|
|  |データ ストレージの制限の設定|利用可能|利用可能|利用可能|
|  |共有とアクセス制御のための Active Directory グループの使用|利用可能|利用可能|利用可能|
|  |Office 365 セキュリティ/コンプライアンス管理センターを使用した監査|利用可能|利用可能|利用可能|
|  |外部ユーザーの共有|利用可能|利用可能|利用可能|
|  |レポートとダッシュボードの使用状況メトリック|利用不可|利用不可|利用不可|
|  |GCC と商用クラウド間の Azure B2B|利用不可|利用不可|利用不可|
|レポートの作成|ダッシュボードとレポートの作成と表示|利用可能|利用可能|利用可能|
|  |スケジュールされたデータ更新|利用可能|利用可能|利用可能|
|  |更新可能なチーム ダッシュボード|利用可能|利用可能|利用可能|
|  |ページ分割されたレポート|利用可能|利用可能|ロードマップ上で|
|  |テンプレート アプリ|利用不可|利用不可|利用不可|
|データに接続する|Excel からのデータとレポートのインポート|利用可能|利用可能|利用可能|
|  |CSV ファイルからのデータのインポート|利用可能|利用可能|利用可能|
|  |Power BI Desktop ファイルからのデータのインポート|利用可能|利用可能|利用可能|
|  |CDS への接続|利用可能|利用不可|利用不可|
|  |Azure Data Lake Storage Gen2 コネクタ|利用不可|利用不可|利用不可|
|データ管理|データ管理ゲートウェイ|利用可能|利用可能|利用可能|
|  |Azure SQL でのデータの暗号化|利用可能|利用可能|利用可能|
|  |Power BI 用 Blob Storage でのデータの暗号化|利用可能|利用可能|利用可能|
|製品間の統合|Power BI Web パーツを使用した SharePoint Online への埋め込み|利用不可|利用不可|利用不可|
|  |埋め込み Web パーツを使用した SharePoint Online への埋め込み|利用可能|利用可能|利用可能|
|  |データフロー関数と AI 関数|利用不可|利用不可|利用不可|
|  |データドリブン アラートのための Power Automate との接続|利用不可|利用不可|利用不可|
|  |チームでの [Power BI] タブ|利用可能|利用不可|利用不可|
|  |自動化された機械学習|利用不可|利用不可|利用不可|
|  |Cognitive Services|利用不可|利用不可|利用不可|
|  |Azure ML|利用不可|利用不可|利用不可|

## <a name="next-steps"></a>次の手順

* [米国政府向け Power BI へのサインアップ](service-govus-signup.md)
* [Microsoft Power Apps US Government](https://docs.microsoft.com/power-platform/admin/powerapps-us-government)
* [Power Automate US Government](https://docs.microsoft.com/power-automate/us-govt)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">米国政府向け Power BI のデモ</a>
