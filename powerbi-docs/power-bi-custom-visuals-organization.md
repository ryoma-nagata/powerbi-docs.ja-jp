---
title: Power BI の組織のビジュアル
description: Power BI で組織のビジュアルを使用、管理、作成する
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/11/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 9775b7cd1eb936019051ae952bc270924061daaa
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68415340"
---
# <a name="organizational-visuals-in-power-bi"></a>Power BI の組織のビジュアル

Power BI でカスタム ビジュアルを使い、ご自身の目的に合った独自のビジュアルを作成することができます。 カスタム ビジュアルは開発者が作成します。これは多くの場合、Power BI に付属している多くのビジュアルが各自の要件を満たしていないときに作成されます。

カスタム ビジュアルが重要視される組織もあります。その組織に特有のデータやインサイトを伝えるために必要だからです。その組織だけのビジネス手法を反映し、データに特別な要件が求められることもあります。 そのような組織はカスタム ビジュアルを開発し、組織全体で共有し、適切に保守管理する必要があります。 Power BI カスタム ビジュアルではその機能を利用できます。

次の図は、Power BI における組織のカスタム ビジュアルのフロー プロセスを示したものです。管理者から始まり、開発と保守管理を経由し、最終的にデータ アナリストの元に届けられます。

![カスタム ビジュアルの図](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

組織のビジュアルは、Power BI 管理者が管理ポータルから展開および管理します。 組織のリポジトリに展開されると、組織のユーザーは簡単に見つけて、Power BI Desktop から直接、自分のレポートに組織のカスタム ビジュアルをインポートできます。

作成したレポートで組織のカスタム ビジュアルを使用する方法については、[組織のカスタム ビジュアルをレポートにインポートする方法](power-bi-custom-visuals.md)に関する記事をご覧ください。

## <a name="administer-organizational-custom-visuals"></a>組織のカスタム ビジュアルを管理する

組織のカスタム ビジュアルを管理し、展開する方法については、[組織のカスタム ビジュアルの展開と管理](https://go.microsoft.com/fwlink/?linkid=866790)に関する記事をご覧ください。

> [!WARNING]
> カスタム ビジュアルには、セキュリティやプライバシーのリスクがあるコードが含まれる場合があります。 組織のリポジトリに展開する前に、カスタム ビジュアルの作成者とソースを信頼できることを確認してください。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

注意する必要がある考慮事項と制限事項がいくつかあります。

管理者:

* レガシ カスタム ビジュアル (新しいバージョンの API に基づいて作成されていないカスタム ビジュアルなど) はサポートされていません

* カスタム ビジュアルがリポジトリから削除されると、削除されたそのビジュアルを利用している既存のレポートでレンダリングが停止します。 リポジトリからの削除は元に戻せません。 カスタム ビジュアルを一時的に無効にするには、[無効にする] 機能を使用します。

エンド ユーザー:

* 組織のカスタム ビジュアルは、組織のリポジトリからインポートされるプライベートなビジュアルです。 他のプライベートなビジュアルと同じように、これらを [PowerPoint にエクスポート](https://docs.microsoft.com/power-bi/consumer/end-user-powerpoint)したり、ユーザーが[レポート ページをサブスクライブする](https://docs.microsoft.com/power-bi/consumer/end-user-subscribe)ときに受信する電子メールに表示したりすることはできません。 これらの機能をサポートしているのは、マーケットプレースから直接インポートされる[認定済みカスタム ビジュアル](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified)のみです。

* AppSource マーケットプレースの Visio ビジュアル、PowerApps ビジュアル、Map box ビジュアル、GlobeMap ビジュアルは、組織のリポジトリから展開された場合、レンダリングされません。

## <a name="troubleshoot"></a>トラブルシューティング

トラブルシューティングについては、[Power BI カスタム ビジュアルのトラブルシューティング](power-bi-custom-visuals-troubleshoot.md)に関する記事を参照してください。

## <a name="faq"></a>よく寄せられる質問

詳細情報と質問の回答については、[Power BI カスタム ビジュアルについてよく寄せられる質問](power-bi-custom-visuals-faq.md#organizational-custom-visuals)に関するページをご覧ください。

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。
