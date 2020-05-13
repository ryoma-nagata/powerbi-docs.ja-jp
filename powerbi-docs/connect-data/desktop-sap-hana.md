---
title: Power BI Desktop で SAP HANA を使用する
description: Power BI Desktop で SAP HANA を使用する
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 9b205a0ae9b58acf054a9afe43196e77ee404c84
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83289122"
---
# <a name="connect-to-sap-hana-databases-in-power-bi-desktop"></a>Power BI Desktop で SAP HANA データベースに接続する

Power BI Desktop を利用し、 *SAP HANA* データベースにアクセスできるようになりました。 SAP HANA を使用するには、Power BI Desktop の SAP HANA データ接続が正常に機能するように、SAP HANA ODBC ドライバーをローカルのクライアント コンピューターにインストールする必要があります。 SAP HANA Client ツールは、[SAP Development Tools](https://tools.hana.ondemand.com/#hanatools) からダウンロードできます。このツールには、必要な ODBC ドライバーが含まれています。 または、[SAP Software Download Center](https://support.sap.com/en/my-support/software-downloads.html) から入手することもできます。 Software ポータルで、Windows コンピューター向けの *SAP HANA CLIENT* を検索してください。 SAP Software Download Center は構成が頻繁に変更されるので、サイトのナビゲーションに関する具体的なガイダンスはありません。

SAP HANA データベースに接続するには、 **[データの取得]** 、 **[データベース]** 、 **[SAP HANA データベース]** 、 **[接続]** の順に選択します。

![SAP HANA データベース、[データの取得] ダイアログ ボックス、Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

SAP HANA データベースに接続する場合、サーバー名を指定します。 次に、ドロップダウンと入力ボックスで、ポートを指定します。

このリリースでは、Power BI Desktop および Power BI サービスで [DirectQuery](desktop-directquery-sap-hana.md) モードの SAP HANA がサポートされます。 DirectQuery モードで SAP HANA を使用するレポートを Power BI サービスに公開およびアップロードすることができます。 DirectQuery モードで SAP HANA を使用しないときも、Power BI サービスにレポートを公開およびアップロードすることができます。

## <a name="supported-features-for-sap-hana"></a>SAP HANA でサポートされる機能

このリリースでは、次の一覧に示すように SAP HANA 向けに多くの機能が用意されています。

* SAP HANA 向け Power BI コネクタでは、SAP ODBC ドライバーを使用して最適なユーザー エクスペリエンスを提供します。

* SAP HANA は、DirectQuery およびインポート オプションの両方をサポートします。

* Power BI は、HANA 情報モデル (分析ビューや計算ビューなど) をサポートし、ナビゲーションを最適化します。

* SAP HANA では、ダイレクト SQL 機能を使用して行と列のテーブルに接続することもできます。

* Power BI には、HANA モデル向けに最適化されたナビゲーションが含まれています。

* Power BI は、SAP HANA の変数と入力パラメーターをサポートします。

* Power BI は、HDI コンテナー ベースの計算ビューをサポートします。

  * Power BI Desktop の 2019 年 8 月のリリースでは、HDI コンテナー ベースの計算ビューのサポートは、パブリック プレビュー段階にあります。 Power BI で HDI コンテナー ベースの計算ビューにアクセスするには、Power BI で使用する HANA データベース ユーザーが、アクセスするビューを格納する HDI ランタイム コンテナーにアクセスするためのアクセス許可を持っていることを確認します。 このアクセス権を付与するには、HDI コンテナーへのアクセスを許可するロールを作成します。 次に、Power BI で使用する HANA データベース ユーザーにそのロールを割り当てます  (このユーザーには、通常どおり、\_SYS\_BI スキーマでシステム テーブルから読み取るためのアクセス許可も必要です)。データベース ロールを作成して割り当てる方法の詳細な手順については、SAP の公式ドキュメントを参照してください。 [この SAP のブログ記事](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/)から始めることも可能です。

  * 現在、HDI ベースの計算ビューに関連付けられている HANA 変数には、いくつかの制限があります。 これらの制限は、HANA 側のエラーによるものです。
  
    第 1 に、HDI コンテナー ベースの計算ビューの共有列に HANA 変数を適用することはできません。 この制限を解消するには、HANA 2 バージョン 37.02 以降または HANA 2 バージョン 42 以降にアップグレードします。 第 2 に、現在、変数およびパラメーターに対する複数エントリの既定値は、Power BI UI に表示されません。 この制限は SAP HANA のエラーによるものですが、SAP はまだ修正を発表していません。

## <a name="limitations-of-sap-hana"></a>SAP HANA の制限

SAP HANA を使用する場合、次に示すいくつかの制限があります。

* NVARCHAR 文字列は最大 4,000 文字の Unicode 文字に切り捨てられます。
* SMALLDECIMAL はサポートされていません。
* VARBINARY はサポートされていません。
* 有効な日付は 1899/12/30 から 9999/12/31 まで

## <a name="next-steps"></a>次の手順

DirectQuery と SAP HANA の詳細については、次のリソースを参照してください。

* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
* [Power BI で DirectQuery を使用する](desktop-directquery-about.md)
* [Power BI データ ソース](power-bi-data-sources.md)
* [SAP HANA の暗号化を有効にする](desktop-sap-hana-encryption.md)
