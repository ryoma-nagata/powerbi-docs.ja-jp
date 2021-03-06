---
title: Power BI デザイナーのダッシュボードの概要
description: ダッシュボードは、Power BI サービスの主要な機能です。 これでは、ストーリーをしばしばキャンバスと呼ばれる 1 つのページで視覚化します。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: eb2c513e8ee8ad1c8ad93866f688e40f6c5af56d
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160790"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Power BI デザイナーのダッシュボードの概要

Power BI の*ダッシュボード*は、ストーリーをしばしばキャンバスと呼ばれる 1 つのページで視覚化します。 これは 1 ページに限られているため、適切に設計されたダッシュボードには、そのストーリーの最も重要な要素のみが含まれます。 リーダーは、その詳細を関連レポートで表示できます。

![ダッシュボード](media/service-dashboards/power-bi-dashboard2.png)

ダッシュボードは、Power BI サービス専用の機能です。 これは Power BI Desktop では利用できません。 ダッシュボードはモバイル デバイスで作成することはできませんが、そこで[参照および共有する](mobile-apps-view-dashboard.md)ことができます。

## <a name="dashboard-basics"></a>ダッシュボードの基礎 

ダッシュボードに表示される視覚化は、*タイル*と呼ばれます。 タイルはレポートからダッシュボードに*ピン留め*します。 Power BI を初めて使うときは、「[Power BI サービスのデザイナー向けの基本的な概念](service-basic-concepts.md)」を読むと基礎がよくわかります。

ダッシュボード上の視覚エフェクトはレポートから生成され、各レポートは 1 つのデータセットが基になっています。 ダッシュボードは基になっているレポートとデータセットへの入り口と考えることもできます。 視覚化を選ぶと、その作成に使われたレポート (およびデータセット) に行き着きます。

![ダッシュボード、レポート、データセット間の関係を示す図](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>ダッシュボードの利点
ダッシュボードは、ビジネスを注視し、最も重要なすべてのメトリックをひとめで見るための、素晴らしい手段です。 ダッシュボード上の視覚エフェクトは、1 つまたは複数の基になっているデータセットから、および 1 つまたは複数の基になっているレポートから生成できます。 ダッシュボードは、オンプレミスのデータとクラウド データを結合し、存在する場所に関係なくデータを統合して表示します。

ダッシュボードは単なるきれいな絵ではありません。 高度な対話機能を備え、基になっているデータが変化するとタイルが更新されます。

## <a name="who-can-create-a-dashboard"></a>ダッシュボードを作成できるユーザー
ダッシュボードを作成する機能は "*作成者*" の機能であり、レポートに対する編集のアクセス許可が必要です。 編集のアクセス許可はレポート作成者と、作成者からアクセス許可を付与された同僚が使用できます。 たとえば、David がワークスペース ABC でレポートを作成し、そのワークスペースのメンバーとしてあなたを追加した場合、あなたと David の両方に編集のアクセス許可があります。 これに対して、直接または [Power BI アプリ](service-create-distribute-apps.md)の一部としてレポートが共有されている場合、あなたはレポートを "*使用*" することになります。 ダッシュボードにタイルをピン留めすることができない場合があります。 

> [!IMPORTANT]
> ワークスペースでダッシュボードを作成するには、[Power BI Pro](service-free-vs-pro.md) のライセンスが必要です。 Power BI Pro ライセンスを使用せずに、自分のマイ ワークスペースにダッシュボードを作成できます。


## <a name="dashboards-versus-reports"></a>ダッシュボードとレポート
[レポート](service-reports.md)とダッシュボードは、両方とも視覚エフェクトがたくさんあるキャンバスであるため似ているように思えます。 しかし、次の表に示すように、大きな違いがあります。

| **機能** | **ダッシュボード** | **レポート** |
| --- | --- | --- |
| ページ |1 ページ |1 ページ以上 |
| データ ソース |ダッシュボードごとに、1 つ以上のレポートおよび 1 つ以上のデータセット |レポートごとに 1 つのデータセット |
| Power BI Desktop での使用可能性 |いいえ | はい。 Power BI Desktop でレポートを作成および表示することができます |
| 購読 |はい。 ダッシュボードをサブスクライブできます |はい。 レポート ページにサブスクライブできます |
| フィルター処理 |いいえ。 フィルター処理またはスライスはできません |はい。 さまざまな方法でフィルター処理、強調表示、スライスできます |
| おすすめ |はい。 1 つのダッシュボードを "*おすすめの*" ダッシュボードとして設定できます |いいえ |
| お気に入り | はい。 複数のダッシュボードを "*お気に入り*" として設定できます | はい。 複数のレポートを "*お気に入り*" として設定できます
| 通知の設定 |はい。 特定の状況でダッシュボードのタイルを使用できます |いいえ |
| 自然言語クエリ (Q&A) |はい | はい (ただし、レポートと基になるデータセットに対して編集のためのアクセス許可を持っている場合) |
| 基になっているデータセットのテーブルとフィールドの表示 |いいえ。 データのエクスポートはできますが、ダッシュボード自体にテーブルとフィールドを表示することはできません |はい |


## <a name="next-steps"></a>次の手順
* [サンプル ダッシュボード](sample-tutorial-connect-to-the-samples.md)のツアーを利用してダッシュボードに慣れます。
* [ダッシュボードのタイル](service-dashboard-tiles.md)について学習します。
* ダッシュボードの個々のタイルを追跡し、特定のしきい値に達したときにメールを受け取りたい場合は、 [タイルにアラートを作成](service-set-data-alerts.md)します。
* [Power BI Q&A](power-bi-tutorial-q-and-a.md) を使ってデータについて質問し、視覚化の形式で回答を受け取る方法を学習します。
