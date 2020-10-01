---
title: Power BI Desktop での拡張データセット メタデータの使用
description: この記事では、Power BI で拡張データセット メタデータを使用する方法について説明します。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/22/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 67141f67be85f5c292118d4e88cfe3c5a949ce4f
ms.sourcegitcommit: ff981839e805f523748b7e71474acccf7bdcb04f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "91019862"
---
# <a name="using-enhanced-dataset-metadata"></a>拡張データセット メタデータの使用

Power BI Desktop によってレポートが作成されると、対応する PBIX ファイルと PBIT ファイルにデータセット メタデータも作成されます。 以前は、メタデータは Power BI Desktop に固有の形式で格納されていました。 Base-64 でエンコードされた M 式とデータ ソースが使用され、そのメタデータの格納方法に関する制限事項が適用されていました。

**拡張データセット メタデータ**機能のリリースにより、これらの制限事項の多くはなくなります。 PBIX ファイルは、ファイルを開いたときに自動的に拡張メタデータにアップグレードされます。 **拡張データセット メタデータ**を使用すると、Power BI Desktop によって作成されたメタデータでは、[表形式オブジェクト モデル](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)に基づいて、Analysis Services 表形式モデルに使用されるものと同様の形式が使用されます。


**拡張データセット メタデータ**機能は、将来の Power BI 機能がそのメタデータに基づいて構築されるため、戦略的かつ基本的な機能です。 拡張データセット メタデータを活用するための追加機能としては、Power BI データセットを管理するための [XMLA 読み取り/書き込み](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)や、次世代機能を活用するための Power BI への Analysis Services ワークロードの移行などがあります。


## <a name="next-steps"></a>次の手順

Power BI Desktop では、あらゆる種類の操作を実行できます。 そのような機能について詳しくは、次のリソースをご覧ください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop の新機能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop でのクエリの概要](../transform-model/desktop-query-overview.md)
* [Power BI Desktop でのデータ型](desktop-data-types.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop での一般的なクエリ タスク](../transform-model/desktop-common-query-tasks.md)