---
title: Power BI Embedded の分析の容量と SKU
description: Power BI Embedded 分析の容量と SKU について確認します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/11/2020
ms.openlocfilehash: 1c6c4faa9f5cff46695ddd9d30869103d7bf482b
ms.sourcegitcommit: d6a48e6f6e3449820b5ca03638b11c55f4e9319c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/18/2020
ms.locfileid: "77427209"
---
# <a name="capacity-and-skus-in-power-bi-embedded-analytics"></a>Power BI Embedded の分析の容量と SKU

運用環境に移行する場合、Power BI Embedded 分析には、埋め込み Power BI コンテンツを公開するための専用容量 (*A*、*EM*、または *P* SKU) が必要です。

容量とは、排他的使用のために予約されたリソースの専用セットです。 これにより、ユーザーごとのライセンスを購入しなくても、ユーザーに対してダッシュボード、レポート、データセットを公開できます。 また、コンテンツに対して信頼性の高い、一貫性のあるパフォーマンスも提供されます。

>[!NOTE]
>公開するためには、1 つの Power BI Pro アカウントが必要です。

## <a name="what-is-embedded-analytics"></a>Embedded 分析とは

Power BI Embedded 分析には 2 つのソリューションが含まれています。
* *Power BI Embedded* - Azure のオファリング
* *Power BI Premium* の一部としての Embedding Power BI - Office のオファリング

### <a name="power-bi-embedded"></a>Power BI Embedded

Power BI Embedded は、アプリケーションにビジュアルを埋め込むことを望む ISV と開発者用です。

Power BI Embedded を使用するアプリケーションでは、ユーザーは Power BI Embedded 容量に格納されているコンテンツを使用できます。

### <a name="power-bi-premium"></a>Power BI Premium

[Power BI Premium](../service-premium-what-is.md) は、組織、パートナー、顧客、サプライヤーを 1 つのビューで見ることができる完全 BI ソリューションを望む企業向けです。

Power BI Premium は SaaS 製品であり、ユーザーはモバイル アプリ、社内で開発したアプリを使用して、または Power BI ポータル (Power BI サービス) でコンテンツを利用できます。 これにより、Power BI Premium は、内部および外部の顧客向けアプリケーションの両方に対してソリューションが提供可能となります。

## <a name="capacity-and-skus"></a>容量と SKU

各容量には SKU の選択肢が用意されており、各 SKU ではメモリとコンピューティング能力に対して異なるリソース階層が提供されます。 必要な SKU の種類は、デプロイするソリューションの種類によって異なります。

購入する SKU を決定する前に、このセクションの情報を確認してください。
* 各階層でサポートされているワークロードを確認するには、「[Premium 容量でワークロードを構成する](../service-admin-premium-workloads.md)」の記事を参照してください
* このリンクを使用して、[容量の計画とテストを行います](../service-premium-capacity-optimize.md#testing-approaches)

### <a name="power-bi-embedded-skus"></a>Power BI Embedded の SKU

Power BI Embedded には、*A* SKU が付属しています。
* [Power BI Embedded 容量で処理できることを確認する](https://powerbi.microsoft.com/blog/power-bi-developer-community-june-july-update/#Capacity-Plan)
* [*A* SKU を購入する](../service-admin-premium-purchase.md#purchase-a-skus-for-testing-and-other-scenarios)

### <a name="power-bi-premium-skus"></a>Power BI Premium の SKU

Power BI Premium には、*P* および *EM* の 2 つの SKU が用意されています。
* [*P* および *EM* SKU の違いを理解する](../service-premium-what-is.md#subscriptions-and-licensing)
* [Premium SKU を購入する](../service-admin-premium-purchase.md)

### <a name="which-sku-should-i-use"></a>どの SKU を使用すべきか

次の表に、機能の概要、必要な容量、それぞれに必要な特定の SKU を示します。 

</br>
<table>
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<col width="20%">
<tbody>
<tr>
<td style="text-align: center"; colspan="2"><p><b>機能</b></p></td>
<td style="text-align: center">
<p><b>Power BI Embedded</b></p>
</td>
<td style="text-align: center"; colspan="2">
<p><b>Power BI Premium</b></p>
</td>
</tr>
<tr>
<td><p><em>使用対象</em><p></td>
<td><p><em>使用元</em><p></td>
<td style="text-align: center"><p><em>A SKU</br>(Azure)</em></p></td>
<td style="text-align: center"><p><em>EM SKU</br>(Office)</em></p></td>
<td style="text-align: center"><p><em>P SKU</br>(Office)</em></p></td>
</tr>
<tr>
<td>Power BI ワークスペースからアーティファクトを埋め込む</td>
<td>
</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="2">Power BI レポート</td>
<td>組織向けの埋め込みアプリケーション</br>(ユーザー所有データ)</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>顧客向けの埋め込みアプリケーション</br>(アプリ所有データ)</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td rowspan="3">Power BI コンテンツ<br>(無料の Power BI ライセンスを使用)</td>
<td>Power BI サービス</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>Power BI モバイル</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
</tr>
<tr>
<td>MS Office アプリ</td>
<td style="text-align: center">✖</td>
<td style="text-align: center">✔</td>
<td style="text-align: center">✔</td>
</tr>
</tbody>
</table>

### <a name="capacity-considerations"></a>容量に関する考慮事項

次の表に、容量ごとの支払いと使用に関する考慮事項を示します。

</br>
<table>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><p><strong>Power BI Embedded</strong></p></td>
<td style="text-align: center;" colspan="2"><p><strong>Power BI Premium</strong></p></td>
</tr>
<tr>
<td><p><strong>プラン</strong></p></td>
<td style="text-align: center;"><p>Azure</p></td>
<td style="text-align: center;" colspan="2"><p>Office</p></td>
</tr>
<tr>
<td><p><strong>SKU</strong></p></td>
<td style="text-align: center;"><p>A</p></td>
<td style="text-align: center;"><p>EM</p></td>
<td style="text-align: center;"><p>P</p></td>
</tr>
<tr>
<td><p><strong>Billing</strong></td>
<td style="text-align: center;">1 時間ごと</td>
<td style="text-align: center;">月単位</td>
<td style="text-align: center;">月単位</td>
</tr>
<tr>
<td><p><strong>コミットメント</strong></td>
<td style="text-align: center;">なし</td>
<td style="text-align: center;">年単位</td>
<td style="text-align: center;">月単位または年単位</td>
</tr>
<tr>
<td valign="top"><p><strong>使用方法</strong></td>
<td style="text-align: center;">Azure リソースは以下が可能です:</br>- <a href="azure-pbie-scale-capacity.md">スケールアップまたはダウン</a></br>- <a href="azure-pbie-pause-start.md">一時停止と再開</a>
</td>
<td style="text-align: center;">埋め込み先: アプリ、</br> Microsoft アプリケーション</td>
<td style="text-align: center;">埋め込み先: アプリ、</br> Power BI サービス</td>
</tr>
</tbody>
</table>

### <a name="sku-memory-and-computing-power"></a>SKU のメモリとコンピューティング能力

次の表は、各 SKU のリソースと制限を示しています。

| 容量ノード | 合計 v コア数 | バックエンド v コア数 | RAM (GB) | フロントエンド v コア数 | DirectQuery/ライブ接続 (秒あたり) | モデル更新並列処理 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| P4 | 64 | 32 | 200 | 32 | 240 | 48 |
| P5 | 128 | 64 | 400 | 64 | 480 | 96 |
| | | | | | | |

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
>[顧客向けに埋め込む](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[組織向けの埋め込み](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [アプリからの埋め込み](embed-from-apps.md)