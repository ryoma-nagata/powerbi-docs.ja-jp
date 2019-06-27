---
title: Power BI サービスのページ分割されたレポートをサブスクライブする
description: この記事では、Power BI サービスのページ分割されたレポートをサブスクライブする際の留意点について説明します。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839564"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Power BI サービスのページ分割されたレポートを自分および他のユーザーがサブスクライブする 

Power BI サービスのページ分割されたレポートに対して自分および他のユーザー用の電子メール サブスクリプションを設定できるようになりました。 一般に、[Power BI サービスのレポートおよびダッシュボードをサブスクライブ](service-report-subscribe.md)する場合とプロセスは同じです。 この記事では、違いと考慮事項について詳しく説明します。 

サブスクリプションの設定時には、メールの受信頻度を次の中から選択します: 毎日、毎週、1 時間ごと。 毎日または毎週を選択した場合は、サブスクリプションを実行する時刻を選択できます。 いずれの場合も、すべてのレポートに、1 日あたり最大 24 個の異なるサブスクリプションを設定できます。 

## <a name="considerations-for-paginated-report-subscriptions"></a>ページ分割されたレポート サブスクリプションに関する考慮事項 

- ダッシュボードまたは Power BI レポート用のサブスクリプションとは異なり、ご利用のサブスクリプションには、レポート出力全体の添付ファイルが含まれています。  次の添付ファイルの種類がサポートされています: PDF、PowerPoint プレゼンテーション (PPTX)、Excel ブック (XLSX)、Word 文書 (DOCX)、CSV ファイル、および XML。

- 電子メールの本文にレポートのプレビュー イメージはありません。  オプション項目としてレポートの最初のページのイメージを用意する予定です。 

- レポート添付ファイルのサイズの最大値は、25 MB です。 

- Azure Analysis Services や Power BI のデータセットなど、現在サポートされているデータ ソースに接続する、他のユーザーのページ分割されたレポートをサブスクライブすることができます。 SQL Server Reporting Services で現在の方法と同様に、レポート添付ファイルでもご利用のアクセス許可に基づいてデータが反映されることに留意してください。 

- レポート ページのサブスクリプションは、レポートの名前に関連付けられています。  

- メール サブスクリプションは、レポートの既定のパラメーター値と一緒に送信されます。 

- ページ分割されたレポートには、頻度を設定する **[データ更新後]** オプションはありません。 基になるデータ ソースから常に最新の値を取得します。 

## <a name="next-steps"></a>次の手順

[Power BI サービスのレポートとダッシュボードを自分および他のユーザーがサブスクライブする](service-report-subscribe.md)

[Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
