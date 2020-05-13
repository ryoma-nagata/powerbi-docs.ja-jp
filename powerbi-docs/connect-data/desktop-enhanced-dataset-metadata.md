---
title: Power BI Desktop での拡張データセット メタデータの使用 (プレビュー)
description: この記事では、Power BI で拡張データセット メタデータを使用する方法について説明します。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 87b4be55b1b811f63dbb7fe271bc3c3fa4af2755
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83347426"
---
# <a name="using-enhanced-dataset-metadata-preview"></a>拡張データセット メタデータの使用 (プレビュー)

Power BI Desktop によってレポートが作成されると、対応する PBIX ファイルと PBIT ファイルにデータセット メタデータも作成されます。 以前は、メタデータは Power BI Desktop に固有の形式で格納されていました。 Base-64 でエンコードされた M 式とデータ ソースが使用され、そのメタデータの格納方法に関する制限事項が適用されていました。

**拡張データセット メタデータ**機能のリリースにより、これらの制限事項の多くはなくなります。 **拡張データセット メタデータ**機能が有効になっていると、Power BI Desktop によって作成されたメタデータでは、[表形式オブジェクト モデル](https://docs.microsoft.com/bi-reference/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)に基づいて、Analysis Services 表形式モデルに使用されるものと同様の形式が使用されます。


**拡張データセット メタデータ**機能は、将来の Power BI 機能がそのメタデータに基づいて構築されるため、戦略的かつ基本的な機能です。 拡張データセット メタデータを活用するための追加機能としては、Power BI データセットを管理するための [XMLA 読み取り/書き込み](https://docs.microsoft.com/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)や、次世代機能を活用するための Power BI への Analysis Services ワークロードの移行などがあります。



## <a name="enable-enhanced-dataset-metadata"></a>拡張データセット メタデータを有効にする

**拡張データセット メタデータ**機能は、現在プレビューの段階です。 拡張データセット メタデータを有効にするには、次の図に示すように、Power BI Desktop で **[ファイル]、[オプションと設定]、[オプション]、[プレビュー機能]** の順に選択し、 **[Store datasets using enhanced metadata format]\(拡張メタデータ形式を使用してデータセットを格納する\)** チェックボックスをオンにします。 

![プレビュー機能を有効にする](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-01.png)

Power BI Desktop を再起動するように求められます。

![再起動のプロンプト](media/desktop-enhanced-dataset-metadata/enhanced-dataset-metadata-02.png)

プレビュー機能を有効にすると、Power BI Desktop によって、以前のメタデータ形式を使用する PBIX ファイルと PBIT ファイルのアップグレードが試行されます。 

> [!IMPORTANT]
> **拡張データセット メタデータ**機能を有効にすると、レポートへのアップグレードを元に戻すことができなくなります。 **拡張データセット メタデータ**を有効にすると、Power BI Desktop で読み込まれた、または作成された Power BI レポートは、拡張データセット メタデータ形式に不可逆的に変換されます。

## <a name="considerations-and-limitations"></a>考慮事項と制限事項

プレビュー バージョンでは、プレビュー機能が有効になっている場合、次の制限事項が適用されます。

### <a name="unsupported-features-and-connectors"></a>サポートされていない機能とコネクタ
アップグレードされていない既存の PBIX ファイルまたは PBIT ファイルを開いたときに、データセットに次の機能またはコネクタが含まれている場合、アップグレードは失敗します。 このような障害が発生した場合、ユーザー エクスペリエンスへの直接的な影響はなく、Power BI Desktop では引き続き以前のメタデータ形式が使用されます。

* Python スクリプト
* カスタム コネクタ
* Azure DevOps Server
* BI コネクタ
* Denodo
* Dremio
* Exasol
* Indexima
* IRIS
* Jethro ODBC
* Kyligence Enterprise
* Mark Logic ODBC
* Qubole Presto
* Team Desk
* 列名に "\\n" などの特定の文字の組み合わせを含む M 式
* **拡張データセット メタデータ**機能が有効になっているデータセットを使用する場合は、Power BI サービスでシングル サイン オン (SSO) データ ソースを設定することはできません

また、**拡張データセット メタデータ**を使用するために既に正常にアップグレードされている PBIX ファイルと PBIT ファイルでは、現在のバージョンで上記の機能またはコネクタを使用することは*できません*。

### <a name="lineage-view"></a>系列ビュー
現在、新しいメタデータ形式を使用するデータセットでは、データフローへのリンクが、Power BI サービスの系列ビューに表示されません。

## <a name="next-steps"></a>次の手順

Power BI Desktop では、あらゆる種類の操作を実行できます。 そのような機能について詳しくは、次のリソースをご覧ください。

* [Power BI Desktop とは何ですか?](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop の新機能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop でのクエリの概要](../transform-model/desktop-query-overview.md)
* [Power BI Desktop でのデータ型](desktop-data-types.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop での一般的なクエリ タスク](../transform-model/desktop-common-query-tasks.md)
