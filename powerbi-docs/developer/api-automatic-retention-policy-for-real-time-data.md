---
title: リアルタイム データに対する自動保持ポリシーを使用する Power BI API
description: Power BI サービスでの自動保持ポリシーについて説明します
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 07726535246f8b115402373c315062151177d27c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61347351"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>リアルタイム データの自動保持ポリシー

Power BI サービスの自動保持ポリシーは、クエリ文字列パラメータです。これは、既定の保持ポリシーを有効にして、ダッシュボードへの新しいデータの一定のフローを維持しながら、古いデータを自動的にクリーンアップします。 最初の保持ポリシーは、"*先入れ先出し (FIFO)* " と呼ばれるものです。 これを有効にすると、データは 200,000 行に達するまでテーブルに集積されます。 データが 200,000 行を超えると、データセットから最も古い行が削除されます。 これにより、200,000 ～ 210,000 行の最新のデータだけが保持されます。  
  
<center>

![保持ポリシー](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

最初にデータセットを作成するときに、保持ポリシーが有効になっています。 必要なのは、"default retention policy" クエリ パラメーターを POST データセットの呼び出しに追加し、*basicFIFO* と等しくなるように設定することだけです。  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}