---
title: Power BI 内でデータの秘密度ラベルを有効にする
description: Power BI 内でデータの秘密度ラベルを有効にする方法を説明します
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/23/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: ba1cacfa930bcc0ed51234dea13639420ac8fab7
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315651"
---
# <a name="enable-data-sensitivity-labels-in-power-bi"></a>Power BI 内でデータの秘密度ラベルを有効にする

[Microsoft Information Protection データ秘密度ラベル](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)を Power BI で使用するには、テナント上で有効にする必要があります。 この記事では、Power BI テナント管理者がそれを行う方法について説明します。 Power BI のデータ秘密度ラベルの概要については、「[Power BI におけるデータ保護](service-security-data-protection-overview.md)」を参照してください。 Power BI で秘密度ラベルを適用する方法の詳細については、「[秘密度ラベルを適用する](../collaborate-share/service-security-apply-data-sensitivity-labels.md)」を参照してください。 

秘密度ラベルが有効になっているとき:

* 組織内で指定されたユーザーおよびセキュリティ グループは、Power BI のレポート、ダッシュボード、データセット、データフローを分類して[秘密度ラベルを適用](../collaborate-share/service-security-apply-data-sensitivity-labels.md)することができます。
* 組織のすべてのメンバーは、それらのラベルを表示できます。

データの秘密度ラベルを有効にするには、Azure Information Protection ライセンスが必要です。 詳細については、「[ライセンス](service-security-data-protection-overview.md#licensing)」を参照してください。

## <a name="enable-data-sensitivity-labels"></a>データの秘密度ラベルを有効にする

Power BI **管理ポータル**に移動し、 **[テナント設定]** ウィンドウを開き、 **[情報保護]** セクションを見つけます。

![[Information Protection] セクションを探す](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

**[Information Protection]** セクションで、次の手順を実行します。
1. **[Power BI コンテンツの秘密度ラベルを適用することをユーザーに許可する]** を開きます。
1. トグルを有効にします。
1. Power BI 資産の秘密度ラベルを適用および変更できるユーザーを定義します。 既定では、組織内のすべてのユーザーが秘密度ラベルを適用できます。 ただし、特定のユーザーまたはセキュリティ グループに対してのみ秘密度ラベルの設定を有効にすることができます。 組織全体または特定のセキュリティ グループのどちらかを選択すると、ユーザーまたはセキュリティ グループの特定のサブセットを除外できます。
   
   * 組織全体に対して秘密度ラベルが有効になっている場合、通常、例外はセキュリティ グループです。
   * 特定のユーザーまたはセキュリティ グループに対してのみ秘密度ラベルが有効になっている場合、通常、例外は特定のユーザーです。  
    この方法を使用すると、特定のユーザーが Power BI 内で秘密度ラベルを適用するためのアクセス許可を持つグループに属している場合でも、適用できないようにすることが可能です。

1. **[適用]** を押します。

![秘密度ラベルを有効にする](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> 資産に対する "*作成*" および "*編集*" アクセス許可を持ち、このセクション内で設定した関連するセキュリティ グループに属している Power BI Pro ユーザーのみが秘密度ラベルを設定および編集できるようになります。 このグループに属していないユーザーは、ラベルを設定および編集することはできません。  

## <a name="troubleshooting"></a>トラブルシューティング

Power BI では、Microsoft Information Protection 秘密度ラベルを使用します。 そのため、機密ラベルを有効にしようとしてエラー メッセージが表示された場合は、次のいずれかが原因として考えられます。

* Azure Information Protection [ライセンス](service-security-data-protection-overview.md#licensing)を持っていない。
* 秘密度ラベルが Power BI でサポートされている Microsoft Information Protection バージョンに移行されていない。 [秘密度ラベルの移行](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)の詳細を確認してください。
* 組織内で Microsoft Information Protection 秘密度ラベルが定義されていない。 使用できるようにするには、ラベルが公開済みのポリシーに含まれている必要があることにご留意ください。 [秘密度ラベルの詳細を確認する](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)か、[Microsoft セキュリティとコンプライアンス センター](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels)にアクセスして、組織でラベルを定義してポリシーを公開する方法をご覧ください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

次の一覧に、Power BI における秘密度ラベルの制限事項をいくつか示します。

**[全般]**
* 秘密度ラベルは、ダッシュボード、レポート、データセット、およびデータフローにのみ適用できます。 現在のところ、[ページ分割されたレポート](../paginated-reports/report-builder-power-bi.md)とブックでは使用できません。
* Power BI 資産の秘密度ラベルは、ワークスペースの一覧、系列ビュー、最近使用、アプリ ビューでのみ表示されます。現在のところ、"自分と共有" には表示されません。 ただし、Power BI 資産に適用されているラベルは、表示されない場合でも、Excel、PowerPoint、および PDF ファイルにエクスポートされたデータに常に保持されることに注意してください。
* 秘密度ラベルは、グローバル (パブリック) クラウド内のテナントに対してのみサポートされています。 秘密度ラベルは、他のクラウド内のテナントではサポートされません。
* データの秘密度ラベルは、テンプレート アプリではサポートされていません。 テンプレート アプリの作成者によって設定された秘密度ラベルは、アプリが抽出されてインストールされると削除されます。また、アプリ コンシューマーによってインストールされたテンプレート アプリの成果物に追加された秘密度ラベルは、アプリが更新されると失われます (リセットされて、なくなります)。
* Power BI では、[転送不可](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions)、[ユーザー定義](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions)、[HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions) 保護の種類の秘密度ラベルがサポートされていません。 保護の種類である転送不可とユーザー定義は、[Microsoft 365 セキュリティ センター](https://security.microsoft.com/)または [Microsoft 365 コンプライアンス センター](https://compliance.microsoft.com/)で定義されているラベルを参照します。
* Power BI 内で親ラベルを適用することをユーザーに許可することはお勧めしません。 親ラベルをコンテンツに適用する場合、そのコンテンツからファイル (Excel、PowerPoint、PDF) にデータをエクスポートすると失敗します。 「[サブラベル (ラベルのグループ化)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels)」を参照してください。

**エクスポート**
* ラベルと保護の制御は、データが Excel、PowerPoint、PDF のファイルにエクスポートされるときにのみ適用されます。 ラベルと保護は、データが .csv ファイル、.pbix ファイル、Excel で分析、その他のエクスポート パスにエクスポートされるときは適用されません。
* エクスポート後のファイルに秘密度ラベルと保護を適用するとき、ファイルにコンテンツのマーキングが追加されることはありません。 ただし、コンテンツのマーキングを適用するようにラベルが構成されている場合、ファイルを Office デスクトップ アプリで開いたとき、Azure Information Protection 統合ラベル付けクライアントによって自動的に適用されます。 デスクトップ、モバイル、Web 向けアプリに組み込みのラベル付けを使用するとき、コンテンツのマーキングが自動的に適用されることはありません。 「[Office アプリがコンテンツのマーキングと暗号化を適用するとき](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption)」を参照してください。
* Power BI からファイルをエクスポートしたユーザーには、秘密度ラベルの設定に従って、そのファイルにアクセスして編集するためのアクセス許可が与えられます。 データをエクスポートしたユーザーに、そのファイルに対する所有者のアクセス許可を与えられません。
* データがファイルにエクスポートされるとき、ラベルを適用できない場合、エクスポートに失敗します。 ラベルが適用できず、エクスポートに失敗したかどうかを確認するには、タイトル バーの中央にあるレポートまたはダッシュボードの名前をクリックし、情報ドロップダウンが開いたら、"秘密度ラベルを読み込めません" と表示されているか確認します。 適用後のラベルが公開されていないか、セキュリティ管理者によって削除されたか、システムに一時的な問題が発生した場合にこれが起こります。

## <a name="next-steps"></a>次の手順

この記事では、Power BI 内でデータの秘密度ラベルを有効にする方法を説明しました。 次の記事では、Power BI におけるデータ保護の詳細について説明しています。 

* [Power BI におけるデータ保護の概要](service-security-data-protection-overview.md)
* [Power BI 内でデータの秘密度ラベルを適用する](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Power BI 内で Microsoft Cloud App Security の制御を使用する](service-security-using-microsoft-cloud-app-security-controls.md)
* [データ保護メトリック レポート](service-security-data-protection-metrics-report.md)