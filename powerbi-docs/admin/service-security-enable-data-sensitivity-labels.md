---
title: Power BI で秘密度ラベルを有効にする
description: Power BI 内で秘密度ラベルを有効にする方法を説明します
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 07/06/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: 0fe1b7b1b8175511838005b7b63ca7543bbf939a
ms.sourcegitcommit: 181679a50c9d7f7faebcca3a3fc55461f594d9e7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2020
ms.locfileid: "86034338"
---
# <a name="enable-sensitivity-labels-in-power-bi"></a>Power BI で秘密度ラベルを有効にする

[Microsoft Information Protection 秘密度ラベル](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)を Power BI で使用するには、テナント上で有効にする必要があります。 この記事では、Power BI テナント管理者がそれを行う方法について説明します。 Power BI の秘密度ラベルの概要については、「[Power BI における秘密度ラベル](service-security-sensitivity-label-overview.md)」を参照してください。 Power BI で秘密度ラベルを適用する方法の詳細については、「[秘密度ラベルを適用する](./service-security-apply-data-sensitivity-labels.md)」を参照してください。 

秘密度ラベルが有効になっているとき:

* 組織内で指定されたユーザーおよびセキュリティ グループは、Power BI のレポート、ダッシュボード、データセット、データフローを分類して[秘密度ラベルを適用](./service-security-apply-data-sensitivity-labels.md)することができます。
* 組織のすべてのメンバーは、それらのラベルを表示できます。

秘密度ラベルを有効にするには、Azure Information Protection ライセンスが必要です。 詳細については、「[ライセンス](service-security-sensitivity-label-overview.md#licensing)」を参照してください。

## <a name="enable-sensitivity-labels"></a>秘密度ラベルを有効にする

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

* Azure Information Protection [ライセンス](service-security-sensitivity-label-overview.md#licensing)を持っていない。
* 秘密度ラベルが Power BI でサポートされている Microsoft Information Protection バージョンに移行されていない。 [秘密度ラベルの移行](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)の詳細を確認してください。
* 組織内で Microsoft Information Protection 秘密度ラベルが定義されていない。 使用できるようにするには、ラベルが公開済みのポリシーに含まれている必要があることにご留意ください。 [秘密度ラベルの詳細を確認する](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels)か、[Microsoft セキュリティとコンプライアンス センター](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels)にアクセスして、組織でラベルを定義してポリシーを公開する方法をご覧ください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

Power BI における秘密度ラベルの制限一覧については、「[Power BI における秘密度ラベル](service-security-sensitivity-label-overview.md#limitations)」を参照してください。

## <a name="next-steps"></a>次の手順

この記事では、Power BI 内で秘密度ラベルを有効にする方法を説明しました。 次の記事では、Power BI におけるデータ保護の詳細について説明しています。 

* [Power BI の秘密度ラベルの概要](service-security-sensitivity-label-overview.md)
* [Power BI で秘密度ラベルを適用する方法](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Power BI 内で Microsoft Cloud App Security の制御を使用する](service-security-using-microsoft-cloud-app-security-controls.md)
* [保護メトリック レポート](service-security-data-protection-metrics-report.md)