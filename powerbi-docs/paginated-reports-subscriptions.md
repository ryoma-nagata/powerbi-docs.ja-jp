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
ms.date: 07/15/2019
ms.openlocfilehash: 2d48892450bbf6ab09a4bc88cd2be9a58bbdc863
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307082"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Power BI サービスのページ分割されたレポートを自分および他のユーザーがサブスクライブする 

Power BI サービスのページ分割されたレポートに対して自分および他のユーザー用の電子メール サブスクリプションを設定できるようになりました。 一般に、[Power BI サービスのレポートおよびダッシュボードをサブスクライブ](service-report-subscribe.md)する場合とプロセスは同じです。 この記事では、違いと考慮事項について詳しく説明します。 

サブスクリプションの設定時には、メールの受信頻度を次の中から選択します: 毎日、毎週、1 時間ごと。 毎日または毎週を選択した場合は、サブスクリプションを実行する時刻を選択できます。 いずれの場合も、すべてのレポートに、1 日あたり最大 24 個の異なるサブスクリプションを設定できます。 

## <a name="considerations-for-paginated-report-subscriptions"></a>ページ分割されたレポート サブスクリプションに関する考慮事項 

- ダッシュボードまたは Power BI レポート用のサブスクリプションとは異なり、ご利用のサブスクリプションには、レポート出力全体の添付ファイルが含まれています。  次の添付ファイルの種類がサポートされています: PDF、PowerPoint プレゼンテーション (PPTX)、Excel ブック (XLSX)、Word 文書 (DOCX)、CSV ファイル、および XML。

- レポートのプレビュー画像を電子メールの本文に含めることができます。  これは省略可能であり、選択した添付ファイル形式によっては、添付したレポート ドキュメントの最初のページと多少異なる場合があります。 

- レポート添付ファイルのサイズの最大値は、25 MB です。 

- Azure Analysis Services や Power BI のデータセットなど、現在サポートされているデータ ソースに接続する、他のユーザーのページ分割されたレポートをサブスクライブすることができます。 SQL Server Reporting Services で現在の方法と同様に、レポート添付ファイルでもご利用のアクセス許可に基づいてデータが反映されることに留意してください。 

- 電子メール サブスクリプションは、ご利用のレポートに対して現在選択されているパラメーターまたは既定のパラメーターのいずれかを使用して送信できます。  ご利用のレポート用に作成するサブスクリプションごとに異なるパラメーター値を設定してもかまいません。 

- レポートの作成者が式ベースのパラメーターを設定している場合 (たとえば、既定値が常に今日の日付である場合)、サブスクリプションでは既定値としてそれが使用されます。 他のパラメーター値を変更して、現在の値を使用することを選択できますが、その値も明示的に変更しない限り、サブスクリプションでは式ベースのパラメーターが使用されます。

- ページ分割されたレポートには、頻度を設定する **[データ更新後]** オプションはありません。 基になるデータ ソースから常に最新の値を取得します。 

## <a name="next-steps"></a>次の手順

[Power BI サービスのレポートとダッシュボードを自分および他のユーザーがサブスクライブする](service-report-subscribe.md)

[Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
