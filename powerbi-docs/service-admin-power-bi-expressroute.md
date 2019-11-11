---
title: Power BI と ExpressRoute
description: Power BI と ExpressRoute
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 59ddddcf1b02f07b850294fa314b7508f7f9fcdc
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73856950"
---
# <a name="power-bi-and-expressroute"></a>Power BI と ExpressRoute

**ExpressRoute** は、(Power BI が存在する) Azure データセンターとオンプレミスのインフラストラクチャとの間または Azure データセンターとコロケーション環境との間にプライベート接続を作成することを可能にする Azure サービスです。

**Power BI** と **ExpressRoute** を使用すると、組織から Power BI へのプライベート ネットワーク接続を作成して (または ISP の共用施設を使用して) インターネットを迂回することにより、機密性の高い Power BI データおよび接続のセキュリティを高めることができます。

詳細については、「[ExpressRoute の概要](/azure/expressroute/expressroute-introduction)」をご覧ください。 Power BI は ExpressRoute に準拠していますが、Power BI との間で送受信されるデータがパブリック インターネットを経由する例外がいくつかあります。 Power BI によって使用される URL の一覧については、「[Power BI の URL](power-bi-whitelist-urls.md)」をご覧ください。

![ExpressRoute のダイアグラム](media/service-admin-power-bi-expressroute/pbi_expressroute_1.png)