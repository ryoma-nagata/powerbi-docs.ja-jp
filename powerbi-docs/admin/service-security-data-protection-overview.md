---
title: Power BI におけるデータ保護
description: Power BI においてデータ保護がどのように機能するかを説明します
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: fa969f8f738cf09e9e01e284de8f60e2fd8ce9ab
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315674"
---
# <a name="data-protection-in-power-bi"></a>Power BI におけるデータ保護

革新的な企業には、機密データを処理および保護する方法に関してビジネス上の厳格な規制と要件があります。 そのようなデータに対する管理機能と可視性を提供するために、Power BI は Microsoft Information Protection および Microsoft Cloud App Security と統合されています。 これを使用すると、次のことができます。
* Microsoft Information Protection の[秘密度ラベル](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide)を使用して Power BI サービス内のコンテンツ (ダッシュボード、レポート、データセット、データフロー) の分類およびラベル付けを行う。Office 365 内でファイルの分類と保護に使用する分類と同じものを使用します。
* Excel、PowerPoint、または PDF ファイルにデータをエクスポートするときに、データに対して Microsoft Information Protection の秘密度ラベルと保護を適用する。
* Microsoft Cloud App Security を使用して、Power BI 内のアクティビティの監視、セキュリティの問題の調査、Microsoft Cloud App Security のアプリの条件付きアクセス制御を利用した Power BI 内のコンテンツの保護を行う。

**重要な注意事項**
* 秘密度ラベルは、Power BI 内のコンテンツへのアクセスには影響**しません**。Power BI 内のコンテンツへのアクセスは、Power BI のアクセス許可によってのみ管理されます。 ラベルが表示されている間、関連する暗号化設定 ([Microsoft 365 セキュリティ センター](https://security.microsoft.com/)または [Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)で構成します) は適用されません。 これらは、Excel、PowerPoint、および PDF ファイルにエクスポートされたデータにのみ適用されます。
* 秘密度ラベルとファイル暗号化は、Excel、PowerPoint、PDF へのエクスポート以外のエクスポート パスには適用**されません**。 Power BI テナント管理者は、秘密度ラベルとそれに関連付けられているファイル暗号化設定の適用をサポートしていないエクスポート パスのいずれか、またはすべてを無効にすることができます。

## <a name="sensitivity-labels-in-power-bi"></a>Power BI における秘密度ラベル

秘密度ラベルは、[Microsoft 365 セキュリティ センター](https://security.microsoft.com/)または [Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)内で作成および管理します。

これらのセンターのどちらかで秘密度ラベルにアクセスするには、 **[分類] > [秘密度ラベル]** に移動します。 これらの秘密度ラベルは、Azure Information Protection、Office アプリ、Office 365 サービスなど、複数の Microsoft サービスで使用できます。

> [!Important]
> 組織で Azure Information Protection の秘密度ラベルが使用されている場合、Power BI でラベルを使用するには、それらを前述のサービスのいずれかに[移行](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)する必要があります。

> [!NOTE]
> 秘密度ラベルはパブリック クラウド内のテナントでのみサポートされており、ソブリン クラウドなどのクラウド内のテナントではサポートされていません。

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Power BI での秘密度ラベルの動作

Power BI のダッシュボード、レポート、データセット、またはデータフローに秘密度ラベルを適用すると、そのリソースにタグを適用する場合と同じように、次の利点が得られます。
* **カスタマイズ可能** - 個人用、公開、一般、社外秘、極秘など、組織内にあるさまざまなレベルの機密コンテンツのカテゴリを作成できます。
* **クリア テキスト** - ラベルはクリア テキストであるため、ユーザーは秘密度ラベルのガイドラインに従ってコンテンツの取り扱い方を簡単に理解できます。
* **永続的** - 秘密度ラベルがコンテンツに適用されると、そのコンテンツが Excel、PowerPoint、および PDF ファイルにエクスポートされてもラベルが付属し、ポリシーを適用して徹底するための基盤となります。

つまり、秘密度ラベルは、コンテンツが Excel、PowerPoint、および PDF ファイルにエクスポートされてもコンテンツに付いて行き、ポリシーを適用して徹底するための基盤となります。

Power BI テナント管理者は、[Power BI 管理ポータル](service-admin-portal.md)で、[Excel へのエクスポート](service-admin-portal.md#export-to-excel)と [PowerPoint および PDF へのエクスポート](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents)を制御できます。

## <a name="sensitivity-label-example"></a>秘密度ラベルの例

Power BI における秘密度ラベルのしくみは、簡単に説明すると次の例のようになります。
1. Power BI サービスで、 **[極秘]** という秘密度ラベルがレポートに適用されています。

   ![リスト ビューの秘密度ラベル](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. このレポートから Excel ファイルにデータをエクスポートすると、エクスポートした Excel ファイルに秘密度ラベルと保護が適用されます。

   ![コンテンツに付いて行く秘密度ラベル](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

Microsoft Office アプリケーションの場合、秘密度ラベルは、上の画像に示されているように、メールやドキュメントに対するタグとして表示されます。 また、コンテンツには、Power BI 全体で使用されたり共有されたりするときに、そのコンテンツに保持され、付いて回る (ステッカーのような) 分類を割り当てることもできます。 この分類を使用して、使用状況レポートを生成し、実際の機密コンテンツのアクティビティ データを確認できます。 この情報を基に、後からいつでも保護設定を適用できます。

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>Power BI で秘密度ラベルを使用するための要件

Power BI 内で秘密度ラベルを有効にして使用する前に、まず次の前提条件を満たす必要があります。
* 秘密度ラベルが [Microsoft 365 セキュリティ センター](https://security.microsoft.com/)または [Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)内で確実に定義されている。
* Power BI で[秘密度ラベルを有効にする](service-security-enable-data-sensitivity-labels.md)。
* ユーザーが[適切なライセンス](#licensing)を持っていることを確認する。
* Power BI で Microsoft Cloud App Security を使用する場合は、[適切なライセンス](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing)を持っていることを確認してください。

## <a name="protect-content-using-microsoft-cloud-app-security"></a>Microsoft Cloud App Security を使用してコンテンツを保護する

Microsoft Cloud App Security を使用して、Power BI のコンテンツを意図しない漏洩や違反から保護することができます。 Microsoft Cloud App Security を設定して構成すると、セキュリティ管理者は、ユーザーのアクセスとアクティビティの監視、リアルタイムのリスク分析の実行、ラベル固有の制御の設定を行うことができます。

たとえば、組織では Microsoft Cloud App Security を使用して、ユーザーが Power BI から管理されていないデバイスに機密データをダウンロードできないようにするポリシーを構成できます。 このような構成により、Microsoft Cloud App Security を使用して、情報漏洩につながるユーザー アクションをすべてリアルタイムで防止する一方で、ユーザーは生産性を維持し、どこからでも Power BI に接続できます。

**必要条件**

秘密度ラベルで Microsoft Cloud App Security を使用する前に、次の前提条件を満たす必要があります。
* Cloud App Security と Azure Information Protection が[テナントに対して有効になっている](https://docs.microsoft.com/cloud-app-security/azip-integration)。
* アプリが [Microsoft Cloud App Security に接続されている](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps)。

## <a name="licensing"></a>ライセンス

* Power BI 内で Microsoft Information Protection の秘密度ラベルを適用および表示するには、Azure Information Protection Premium P1 または Premium P2 ライセンスが必要です。 Microsoft Azure Information Protection は、スタンドアロンとして、またはいずれかの Microsoft ライセンス スイートを介して購入できます。 詳細については、「[Azure Information Protection の価格](https://azure.microsoft.com/pricing/details/information-protection/)」を参照してください。
* Office アプリ内でラベルを表示および適用するには、[ライセンス要件](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels)があります。
* Power BI コンテンツにラベルを適用するには、ユーザーは前述のいずれかの Azure Information Protection ライセンスに加えて、Power BI Pro ライセンスも持っている必要があります。
* 意図しない漏えいや侵害から Power BI コンテンツを保護するために使用する場合は、[Microsoft Cloud App Security の必要なライセンス](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing)を持っている必要があります。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

次の一覧に、Power BI における秘密度ラベルの制限事項をいくつか示します。

**[全般]**
* 秘密度ラベルは、ダッシュボード、レポート、データセット、およびデータフローにのみ適用できます。 現在のところ、[ページ分割されたレポート](../paginated-reports/report-builder-power-bi.md)とブックでは使用できません。
* Power BI 資産の秘密度ラベルは、ワークスペースの一覧、系列、お気に入り、最近使用、アプリ ビューでのみ表示されます。現在、ラベルは "自分と共有" では表示されません。 ただし、Power BI 資産に適用されているラベルは、表示されない場合でも、Excel、PowerPoint、および PDF ファイルにエクスポートされたデータに常に保持されることに注意してください。
* 秘密度ラベルは、グローバル (パブリック) クラウド内のテナントに対してのみサポートされています。 秘密度ラベルは、他のクラウド内のテナントではサポートされません。
* データの秘密度ラベルは、テンプレート アプリではサポートされていません。 テンプレート アプリの作成者によって設定された秘密度ラベルは、アプリが抽出されてインストールされると削除されます。また、アプリ コンシューマーによってインストールされたテンプレート アプリの成果物に追加された秘密度ラベルは、アプリが更新されると失われます (リセットされて、なくなります)。
* Power BI では、[転送不可](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions)、[ユーザー定義](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions)、[HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions) 保護の種類の秘密度ラベルはサポートされていません。 転送不可とユーザー定義の保護の種類では、[Microsoft 365 セキュリティ センター](https://security.microsoft.com/)または [Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)で定義されているラベルが参照されます。
* Power BI 内で親ラベルを適用することをユーザーに許可することはお勧めしません。 親ラベルをコンテンツに適用する場合、そのコンテンツからファイル (Excel、PowerPoint、PDF) にデータをエクスポートすると失敗します。 「[サブラベル (ラベルのグループ化)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels)」を参照してください。

**エクスポート**
* ラベルと保護の制御は、データが Excel、PowerPoint、および PDF ファイルにエクスポートされるときにのみ適用されます。 ラベルと保護は、データが .csv ファイル、.pbix ファイル、Excel で分析、またはその他のエクスポート パスにエクスポートされるときは適用されません。
* エクスポート後のファイルに秘密度ラベルと保護を適用するとき、ファイルにコンテンツのマーキングが追加されることはありません。 ただし、コンテンツのマーキングを適用するようにラベルが構成されている場合は、ファイルを Office デスクトップ アプリで開いたとき、Azure Information Protection 統合ラベル付けクライアントによって自動的に適用されます。 デスクトップ、モバイル、または Web アプリに対して組み込みのラベル付けを使用する場合、コンテンツのマーキングが自動的に適用されることはありません。 「[Office アプリがコンテンツのマーキングと暗号化を適用するとき](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption)」を参照してください。
* Power BI からファイルをエクスポートしたユーザーには、秘密度ラベルの設定に従って、そのファイルにアクセスして編集するためのアクセス許可が与えられます。 データをエクスポートしたユーザーに、そのファイルに対する所有者のアクセス許可を与えられません。
* データがファイルにエクスポートされるときにラベルを適用できない場合は、エクスポートに失敗します。 ラベルを適用できなかったためにエクスポートに失敗したかどうかを確認するには、タイトル バーの中央にあるレポートまたはダッシュボードの名前をクリックし、情報ドロップダウンが開いたら、"秘密度ラベルを読み込めません" と表示されているかどうかを確認します。 これは、適用されたラベルが公開されていないか、セキュリティ管理者によって削除された場合、または一時的なシステムの問題によって発生する可能性があります。


## <a name="next-steps"></a>次の手順

この記事では、Power BI におけるデータ保護の概要について説明しました。 次の記事では、Power BI におけるデータ保護の詳細について説明しています。 

* [Power BI 内でデータの秘密度ラベルを有効にする](service-security-enable-data-sensitivity-labels.md)
* [Power BI 内でデータの秘密度ラベルを適用する](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Power BI 内で Microsoft Cloud App Security の制御を使用する](service-security-using-microsoft-cloud-app-security-controls.md)
* [データ保護メトリック レポート](service-security-data-protection-metrics-report.md)