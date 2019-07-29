---
title: Power BI のデータ ゲートウェイを展開するためのガイダンス
description: Power BI のゲートウェイの展開に関するベスト プラクティスと考慮事項について説明します。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271719"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Power BI のデータ ゲートウェイを展開するためのガイダンス

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

この記事では、ネットワーク環境に Power BI 用にデータ ゲートウェイを展開するためのガイダンスと考慮事項について説明します。

オンプレミス データ ゲートウェイをダウンロード、インストール、構成、および管理する方法の詳細については、「[オンプレミス データ ゲートウェイとは](/data-integration/gateway/service-gateway-onprem)」を参照してください。 また、オンプレミス データ ゲートウェイと Power BI の詳細については、[Microsoft Power ブログ](https://powerbi.microsoft.com/blog/)と [Microsoft Power BI コミュニティ サイト](https://community.powerbi.com/)を参照してください。

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>オンプレミス データ ゲートウェイのインストールに関する注意点

Power BI クラウド サービスのオンプレミス データ ゲートウェイをインストールする前に、注意すべきいくつかの考慮事項があります。 以下のセクションでは、これらの考慮事項について説明します。

### <a name="number-of-users"></a>ユーザー数

ゲートウェイを使用しているレポートを使用するユーザーの数は、ゲートウェイをインストールする場所を決定するときに重要なメトリックです。 考慮すべきいくつかの質問を次に示します。

* これらのレポートを使用しているユーザーの数は、1 日のうちの時間帯によって異なりますか。
* そのような種類の接続 (DirectQuery またはインポート) を使用していますか。
* すべてのユーザーが同じレポートを使用しますか。

すべてのユーザーが毎日同じ時刻に特定のレポートにアクセスする場合、それらのすべての要求を処理できるマシンにゲートウェイをインストールする必要があります (これを決定するために役立つパフォーマンス カウンターと最小要件については次のセクションを参照してください)。

**Power BI** には*レポート*あたり *1 つ*のゲートウェイのみが許可されるという制約があり、そのためレポートが複数のデータソースを基にしている場合でも、そのすべてのデータソースが 1 つのゲートウェイを通過する必要があります。 ただし、ダッシュ ボードが*複数*のレポートを基にしている場合、関係しているレポートごとに専用のゲートウェイを使用して、それによってその単一のダッシュ ボードに関係している複数のレポート間でゲートウェイの負荷を分散することができます。

### <a name="connection-type"></a>接続の種類

**Power BI** では、次の 2 種類の接続が提供されます:**DirectQuery** と**インポート**。 すべてのデータソースが両方の接続の種類をサポートするわけではありません。セキュリティ条件、パフォーマンス、データの制限、データ モデルのサイズといった多くの理由でどちらかの種類が選択されます。 接続の種類とサポートされているデータ ソースの詳細については、[使用可能なデータソースの種類の一覧](service-gateway-data-sources.md#list-of-available-data-source-types)を参照してください。

使用する接続の種類によっては、ゲートウェイの使用量が異なる場合があります。 たとえば、可能な場合は常に、**DirectQuery** データ ソースを**スケジュールされた更新**データ ソースから分離する必要があります (それらが異なるレポートにあり、分離可能であると仮定します)。 このようにすることで、朝にスケジュールされている会社のメイン ダッシュボードで使用される大きなサイズのデータ モデルの更新と同時に、ゲートウェイで数千の DirectQuery 要求がキューに入れられるのを防ぎます。 それぞれの考慮事項を次に示します。

* **スケジュールされた更新**: クエリのサイズと、1 日あたりに発生する更新の数に応じて、推奨される最小ハードウェア要件の間で維持するか、より高いパフォーマンスのマシンにアップグレードするかを選択できます。 特定のクエリが折りたたまれない場合、変換がゲートウェイ マシンで発生し、その場合、ゲートウェイ マシンで使用可能な RAM を増やすとメリットがあります。

* **DirectQuery** の場合: いずれかのユーザーがレポートを開くかデータを参照するたびにクエリが送信されます。 したがって 1,000 を超えるユーザーが同時にデータにアクセスすることを予測している場合、コンピューターが堅牢性と対応可能なハードウェア コンポーネントを確認する必要があります。 CPU コアを増やすと、**DirectQuery** 接続のスループットが向上します。

インストールするマシンの要件については、オンプレミス データ ゲートウェイの[インストール要件](/data-integration/gateway/service-gateway-install#requirements)の記事を参照してください。

### <a name="location"></a>場所

ゲートウェイのインストールの場所は、クエリのパフォーマンスに大きな影響を与えるため、ネットワークの待機時間を最小限に抑えるために、ゲートウェイ、データ ソースの場所、および Power BI テナントが、互いにできるだけ近い場所にあることを確認します。 Power BI テナントの場所を確認するには、Power BI サービスで、右上にある **[?]** アイコンをクリックし、 **[Power BI について]** を選択します。

![Power BI テナントの場所を決定する](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

また、Azure Analysis Services と共に Power BI ゲートウェイを使用する場合は、両方のデータ領域が一致していることを確認してください。 複数のサービスのデータ領域を設定する方法の詳細については、[こちらのビデオ](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/)をご覧ください。

## <a name="next-steps"></a>次の手順

* [プロキシ設定の構成](/data-integration/gateway/service-gateway-proxy)  
* [ゲートウェイのトラブルシューティング - Power BI](service-gateway-onprem-tshoot.md)  
* [オンプレミス データ ゲートウェイに関するよく寄せられる質問 (FAQ) - Power BI](service-gateway-power-bi-faq.md)  

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

