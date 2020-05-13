---
title: Power BI Report Server と Power BI サービスの比較
description: この記事では、Power BI Report Server と Power BI サービスの機能を比較します。
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 03/04/2020
ms.openlocfilehash: 18ca1b58d37fedb2c8246b91dc765168002e163e
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275940"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>Power BI Report Server と Power BI サービスの比較

Power BI Report Server と Power BI サービスには、多くの類似点といくつかの重要な相違点があります。 次の表で、これらについて説明します。

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Power BI Report Server と Power BI サービスの機能

| 機能 | Power BI レポート | Power BI サービス | メモ |
|---------|---------|---------|---------|
| デプロイ | オンプレミスまたはクラウドでホスト | クラウド | Power BI Premium またはソフトウェア アシュアランスによる SQL Server Enterprise を通じてライセンス供与された場合は、Power BI Report Server を Azure VM にデプロイできます (クラウドでホストされます)|
| ソース データ | クラウドとオンプレミスの両方またはいずれか | クラウドとオンプレミスの両方またはいずれか |  |
| ライセンス | Power BI Premium またはソフトウェア アシュアランス (SA) 付きの SQL Server EE | Power BI Pro と Power BI Premium の両方またはいずれか | |  
| ライフサイクル | 最新のライフサイクル ポリシー | フル マネージドのサービス |  |
| リリース サイクル | 年に 3 回 (1 月、5 月、9 月) | 月に 1 回 | 最新の機能と修正プログラムは、Power BI サービスに先に提供されます。 サービスに対する Power BI Desktop リリースからの機能のロールアップは、各リリースで Power BI Report Server に提供されます。他のほとんどの機能は、Power BI サービスのみを対象としています。 |
| Power BI Desktop での Power BI レポートの作成 | はい | はい |  |
| ブラウザーでの Power BI レポートの作成 | いいえ | はい |  |
| Power BI 共有データセットをホストして接続する | いいえ | はい | [ワークスペース全体のデータセットの概要](../connect-data/service-datasets-across-workspaces.md) |
| ゲートウェイが必要 | いいえ | オンプレミス データ ソースでは必要 |  |
| リアルタイム ストリーミング | いいえ | はい | [Power BI のリアルタイム ストリーミング](../connect-data/service-real-time-streaming.md) |
| Dashboards | いいえ | はい | [Power BI サービスのダッシュボード](../consumer/end-user-dashboards.md) |
| アプリを使用した一群のレポートの配布 | いいえ | はい | [Power BI でダッシュボードとレポートを含むアプリを作成して発行する](../collaborate-share/service-create-distribute-apps.md) |
| コンテンツ パック | いいえ | はい | [組織のコンテンツ パック: 概要](../collaborate-share/service-organizational-content-pack-introduction.md) |
| Salesforce などのサービスへの接続 | はい | はい | Power BI サービスのコンテンツ パックで[使用するサービスに接続する](../connect-data/service-connect-to-services.md)。 Power BI Report Server で、認定されたコネクタを使用してサービスに接続します。 詳細については、「[Power BI Report Server での Power BI レポート データ ソース](data-sources.md)」を参照。 |
| 質疑応答 | いいえ | はい | [Power BI サービスと Power BI Desktop の Q&A](../create-reports/power-bi-tutorial-q-and-a.md) 
| クイック分析情報 | いいえ | はい | [Power BI を使用してデータ インサイトを自動的に生成する](../consumer/end-user-insights.md) |
| [Excel で分析] | いいえ | はい | [Excel で分析](../collaborate-share/service-analyze-in-excel.md) 
| ページ分割されたレポート | はい | はい | [Premium 容量の Power BI サービスでページ分割されたレポートが利用可能](../paginated-reports/paginated-reports-report-builder-power-bi.md) (プレビュー) |
| Power BI モバイル アプリ | はい | はい | [Power BI モバイル アプリの概要](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ArcGIS マップ | いいえ | はい | [Esri が提供する Power BI サービスおよび Power BI Desktop の ArcGIS マップ](../visuals/power-bi-visualization-arcgis.md) |
| Power BI レポートの電子メールのサブスクリプション | いいえ | はい | Power BI サービスのレポートまたはダッシュボードを[自分または他のユーザーがサブスクライブします](../collaborate-share/service-report-subscribe.md) |
| ページ分割されたレポートの電子メールのサブスクリプション | はい | はい | [Power BI サービスのページ分割されたレポートを自分および他のユーザーがサブスクライブする](../consumer/paginated-reports-subscriptions.md)<br><br>[Reporting Services での電子メール配信](https://docs.microsoft.com/sql/reporting-services/working-with-subscriptions-web-portal)  |
| データ警告 | いいえ | はい | Power BI サービスで[データ アラート](../create-reports/service-set-data-alerts.md)を設定する
| 行レベルのセキュリティ (RLS) | はい | はい | DirectQuery (データ ソース) とインポート モードの両方で利用可能 <br><br>[Power BI サービス](../admin/service-admin-rls.md)での行レベル セキュリティ <br><br>[Power BI Report Server](row-level-security-report-server.md) での行レベル セキュリティ |
| 全画面表示モード | いいえ | はい | Power BI サービスでの[全画面表示モード](../consumer/end-user-focus.md) |
| Office 365 の高度な共同作業 | いいえ | はい | Office 365 を使用した[ワークスペースでの共同作業](../collaborate-share/service-collaborate-power-bi-workspace.md) |
| R ビジュアル | いいえ | はい | Power BI Desktop で [R ビジュアルを作成](../create-reports/desktop-r-visuals.md)し、それらを Power BI サービスに発行する。 R ビジュアルがある Power BI レポートは、Power BI Report Server に保存できる。  |
| プレビュー機能 | いいえ | はい | [Power BI サービスのプレビュー機能のオプトイン](../consumer/end-user-preview-features.md) |
| Power BI ビジュアル | はい | はい | [Power BI ビジュアル](../developer/visuals/power-bi-custom-visuals.md) |
| 複合モデル | いいえ | はい |
| Power BI Desktop | Report Server 用に最適化されたバージョン。Report Server と一緒にダウンロード可能 | Power BI サービス用に最適化されたバージョン。Windows ストアから入手可能 | [Report Server 用の Power BI Desktop](https://powerbi.microsoft.com/report-server/) <br><br> [Power BI サービス用の Power BI Desktop](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>次のステップ

[Power BI レポート サーバーのインストール](install-report-server.md)






