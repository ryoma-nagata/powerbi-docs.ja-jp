---
title: 組織での Power BI のライセンス
description: Power BI で使用できるさまざまなライセンスの種類の概要と、管理者が組織のライセンスを購入して管理する方法。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/08/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 1bd3af61bb7c1fe525a4e5822724ccb07c57eace
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83344298"
---
# <a name="power-bi-licensing-in-your-organization"></a>組織での Power BI のライセンス

Power BI サービスでユーザーが実行できる内容は、所有するユーザーごとのライセンスの種類と、操作するコンテンツが、Power BI Premium 容量に割り当てられているワークスペース内にあるかどうかによって異なります。 Power BI サービスのすべてのユーザーにライセンスが必要です。

ユーザーがライセンスを取得する方法は 2 つあります。 ユーザーは、セルフサービス サインアップ機能と職場または学校アカウントを使用して、無料または Pro ライセンスを取得できます。 あるいは、管理者が Power BI サブスクリプションを取得し、ユーザーにライセンスを割り当てることができます。

この記事では、管理者の観点からのサービスの購入と、ユーザーごとのライセンスについて重点的に説明します。 ユーザーがライセンスを取得する方法の詳細については、「[個人として Power BI にサインアップする](../fundamentals/service-self-service-signup-for-power-bi.md)」を参照してください。

## <a name="who-can-purchase-and-assign-licenses"></a>ライセンスを購入して割り当てることができるユーザー

組織のライセンスを購入または割り当てるには、管理者ロールが割り当てられている必要があります。 管理者ロールは、Azure Active Directory 管理センターまたは Microsoft 365 管理センターを使用して割り当てられます。 次の表に、購入とライセンスに関連するタスクを実行するために必要なロールを示します。 Azure Active Directory での管理者ロールの詳細については、「[Azure Active Directory で管理者ロールを表示して割り当てる](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-manage-roles-portal)」を参照してください。 ベスト プラクティスなど、Microsoft 365 での管理者ロールの詳細については、「[管理者ロールについて」](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide)を参照してください。

| サービスとライセンスを購入できるユーザー | ユーザー ライセンスを管理できるユーザー |
| --------------- | --------------- |
| 課金管理者 | ライセンス管理者 |
| 全体管理者 | ユーザー管理者 |
|  | 全体管理者 |

これらのロールでは組織を管理します。 Power BI サービス管理者のロールについては、「[Power BI サービス管理者ロールについて](service-admin-role.md)」を参照してください。

## <a name="get-power-bi-for-your-organization"></a>組織の Power BI を取得する

グローバル管理者または課金管理者は、Power BI サービスにサインアップし、組織内のユーザーのライセンスを購入できます。 購入する準備がまだできていない場合は、Power BI Pro 試用版を選択してください。 25 個のライセンスを取得して、1 か月間ご利用いただけます。 サインアップの詳しい手順ついては、「[組織の Power BI サブスクリプションを取得する](service-admin-org-subscription.md)」を参照してください。

## <a name="about-self-service-sign-up"></a>セルフサービス サインアップについて

個々のユーザーは、職場または学校のアカウントでサインアップすることで、自分の Power BI ライセンスを取得できます。 無料ライセンスでは、ユーザーはマイ ワークスペースを使用して、Power BI の個人データの分析と視覚化を試すことができますが、他のユーザーとの共同作業を開始することはできません。 コンテンツを共有するには、Power BI Pro ライセンスが必要です。 ユーザーは、ライセンスの種類を Pro にアップグレードすることができます。また、組織で商用クラウドを使用している場合は、直接 Pro にサインアップすることができます。 政府向けまたはソブリン クラウド インスタンスにデプロイされた組織や教育機関では、Pro を直接購入したり、Pro にアップグレードすることはできません。

組織内のユーザーがセルフサービス サインアップできないようにする場合は、「[セルフサービス サインアップを有効または無効にする](service-admin-disable-self-service.md)」を参照し、オフにする方法を確認してください。

組織内のどのユーザーが既にライセンスを所有している可能性があるかを確認する場合は、「[ユーザー ライセンスを表示および管理する](service-admin-manage-licenses.md)」を参照し、その方法を確認してください。

## <a name="license-types-and-capabilities"></a>ライセンスの種類と機能

Power BI ユーザーごとのライセンスには、無料と Pro の 2 種類があります。 ユーザーに必要なライセンスの種類は、コンテンツの格納場所とそのコンテンツとのやり取り方法によって決まります。 コンテンツを格納できる場所は、組織の[サブスクリプションの種類](#subscription-types)によって決まります。

サブスクリプションの種類の 1 つである、[Power BI Premium](service-admin-premium-purchase.md) では、無料ライセンスを持つユーザーが、Premium 容量に割り当てられているワークスペースのコンテンツを操作できます。 Premium 容量以外では、無料ライセンスを持つユーザーは、Power BI サービスのみを使用してデータに接続し、個人用ワークスペースでレポートとダッシュボードを作成できます。 他のユーザーとコンテンツを共有したり、アプリ ワークスペースにコンテンツを発行したりすることはできません。

標準の Power BI サブスクリプションでは、共有容量が使用されます。 コンテンツが共有容量に格納されている場合、Power BI Pro ライセンスが割り当てられているユーザーは、他の Power BI Pro ユーザーとのみ共同作業できます。 他のユーザーが共有しているコンテンツの利用、アプリ ワークスペースへのコンテンツの発行、ダッシュボードの共有、ダッシュボードとレポートのサブスクライブを行うことができます。  ワークスペースが Premium 容量にある場合、Pro ユーザーは、Power BI Pro ライセンスを持っていないユーザーにコンテンツを配布できます。

以下の表は、各ライセンスの種類の基本的な機能をまとめたものです。 ライセンスの種類ごとの利用可能な機能の詳細については、「[ライセンスの種類別の機能](../fundamentals/service-features-license-type.md)」を参照してください。

| ライセンスの種類 | ワークスペースが共有容量にある場合の機能 | ワークスペースが Premium 容量にある場合のその他の機能 |
| --------- | ----------- | ----------- |
| Power BI (無料) | マイ ワークスペースのコンテンツにアクセスする | 共有されているコンテンツを使用する |
| Power BI Pro | アプリ ワークスペースへのコンテンツの発行、ダッシュボードの共有、ダッシュボードとレポートのサブスクライブ、Pro ライセンスを持つユーザーとの共有を行う | 無料ライセンスを持つユーザーにコンテンツを配布する |

## <a name="subscription-types"></a>サブスクリプションの種類

Microsoft からのすべてのユーザーベースの商用ライセンス サブスクリプションは、Azure Active Directory の ID に基づいています。 これは、商用ライセンスについて Azure Active Directory でサポートされる ID でサインインする必要があることを意味します。 ID サービスに Azure Active Directory を使用する Microsoft サブスクリプションに、Power BI サブスクリプションを追加することができます。 Office 365 E5 など、一部のサブスクリプションには Power BI Pro ライセンスが含まれているため、Power BI に対して個別のサインアップを行う必要はありません。

組織の Power BI サブスクリプションには、Power BI Pro を使用するセルフサービス BI と Power BI Premium を使用する高度な分析の 2 種類があります。

標準のセルフサービス Power BI Pro サブスクリプションでは、管理者がユーザーごとのライセンスを割り当てます。 Power BI Pro ライセンスについては、ユーザーごとの月額料金が発生します。これにより、コラボレーション、発行、共有、およびアドホック分析が可能になります。 コンテンツは、Microsoft によって完全に管理されている共有ストレージ容量に保存されます。

Power BI Premium サブスクリプションでは、組織に専用の容量が割り当てられます。 エンタープライズ BI、ビッグ データ分析、クラウドおよびオンプレミスのレポートに適しており、Premium では高度な管理とデプロイ制御が提供されます。 専用のコンピューティング リソースとストレージ リソースは、組織内の容量管理者によって管理されます。 この専用環境については、月額料金が発生します。 他の Premium の利点に加え、Premium 容量に格納されているコンテンツは、Power BI Pro ライセンスを持っていないユーザーがアクセスでき、それらのユーザーに配布することができます。 Premium を使用するには、少なくとも 1 人のユーザーに Power BI Pro ライセンスが割り当てられている必要があります。また、コンテンツ作成者と開発者には引き続き Power BI Pro ライセンスが必要です。

2 種類のサブスクリプションは相互に排他的ではありません。 Power BI Premium と Power BI Pro の両方を持つことができます。 この構成では、Premium 容量に格納されているコンテンツをすべてのユーザーと共有でき、共有容量も利用できます。 容量の制限については、「[Power BI ワークスペースでデータ ストレージを管理する](service-admin-manage-your-data-storage-in-power-bi.md)」を参照してください。

製品の機能と価格を比較する場合は、「[Power BI の価格](https://powerbi.microsoft.com/pricing)」を参照してください。

## <a name="guest-user-access"></a>ゲスト ユーザー アクセス

組織外のユーザーにコンテンツを配布することができます。 コンテンツをゲストとして表示するために招待することにより、外部ユーザーとコンテンツを共有することができます。 Azure Active Directory Business-to-Business (Azure AD B2B) を使用すると、外部のゲスト ユーザーと共有できます。 外部ユーザーと共有するには、次の前提条件を満たす必要があります。

- 外部ユーザーとコンテンツを共有する機能を有効にする必要があります

- ゲスト ユーザーは、共有コンテンツを表示するために適切なライセンスを取得している必要があります

ゲスト ユーザー アクセスの詳細については、「[Azure AD B2B で外部ゲスト ユーザーに Power BI コンテンツを配布する](service-admin-azure-ad-b2b.md)」を参照してください。

## <a name="purchase-power-bi-pro-licenses"></a>Power BI Pro ライセンスを購入する

管理者として、Microsoft 365 または Microsoft パートナーを通じて Power BI Pro ライセンスを購入します。 ライセンスを購入した後、それを個々のユーザーに割り当てます。 詳細については、「[Power BI Pro のライセンスを購入して割り当てる](service-admin-purchasing-power-bi-pro.md)」を参照してください。

### <a name="power-bi-pro-license-expiration"></a>Power BI Pro ライセンスの有効期限切れ

Power BI Pro ライセンスの有効期限切れ後には猶予期間があります。 ライセンスがボリューム ライセンス契約の一部である場合、猶予期間は 90 日です。 ライセンスを直接購入した場合、猶予期間は 30 日です。

Power BI Pro のサブスクリプション ライフサイクルは Office 365 と同じです。 詳しくは、「[一般法人向け Office 365 のサブスクリプションが終了したとき、データとアクセスはどうなりますか?](https://support.office.com/article/What-happens-to-my-data-and-access-when-my-Office-365-for-business-subscription-ends-4436582f-211a-45ec-b72e-33647f97d8a3)」をご覧ください。


## <a name="next-steps"></a>次の手順

- [Power BI Pro のライセンスを購入して割り当てる](service-admin-purchasing-power-bi-pro.md)
- [Microsoft 365 のビジネス サブスクリプションと課金ドキュメント](https://docs.microsoft.com/microsoft-365/commerce/?view=o365-worldwide)
- [サインインした Power BI ユーザーを見つける](service-admin-access-usage.md)
- 他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
