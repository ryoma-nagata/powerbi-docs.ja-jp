---
title: Power BI Embedded 容量のスケーリング | Microsoft Docs
description: この記事では、Microsoft Azure で Power BI Embedded の容量をスケーリングする方法について説明します。
services: power-bi-embedded
author: rkarlin
ms.author: rkarlin
manager: kfile
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 01/31/2019
ms.openlocfilehash: b9a632fa39d320d14d1282cee5e59022a8ab0303
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61388511"
---
# <a name="scale-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Azure Portal で Power BI Embedded 容量をスケーリングする

この記事では、Microsoft Azure で Power BI Embedded の容量をスケーリングする方法について説明します。 スケーリングによって容量のサイズを増やしたり、減らしたりできます。

Power BI Embedded 容量を作成していることが前提となります。 作成していない場合、「[Azure Portal での Power BI Embedded 容量の作成](azure-pbie-create-capacity.md)」を参照して作成してください。

> [!NOTE]
> スケーリング操作は約 1 分かかります。 この間は容量を使用できません。 埋め込みコンテンツは読み込みできないことがあります。

## <a name="scale-a-capacity"></a>容量をスケーリングする

1. [Azure Portal ](https://portal.azure.com/)にサインインします。

2. **[すべてのサービス]**  >  **[Power BI Embedded]** の順に選択すると、容量が表示されます。

    ![Azure Portal 内のすべてのサービス](media/azure-pbie-scale-capacity/azure-portal-more-services.png)

3. スケーリングする容量を選択します。

    ![Azure Portal 内の Power BI Embedded 容量リスト](media/azure-pbie-scale-capacity/azure-portal-capacity-list.png)

4. 容量内で **[スケール]** の下にある **[価格レベル]** を選択します。

    ![[スケール] の下にある [価格レベル] オプション](media/azure-pbie-scale-capacity/azure-portal-scale-pricing-tier.png)

    現在ご利用の価格レベルには青で縁取られます。

    ![青で縁取られた現在の価格レベル](media/azure-pbie-scale-capacity/azure-portal-current-tier.png)

5. サイズをスケーリングするには、移動先とする新しいレベルを選択します。 選択した新しいレベルが青の点線で囲まれます。 **[選択]** を選択すると、新しいレベルに移動します。

    ![新しいレベルの選択](media/azure-pbie-scale-capacity/azure-portal-select-new-tier.png)

    容量のスケーリングには 1、2 分かかります。

6. [概要] タブでレベルを確認します。現在の価格レベルが表示されています。

    ![現在のレベルを確認する](media/azure-pbie-scale-capacity/azure-portal-confirm-tier.png)

## <a name="next-steps"></a>次の手順

容量の一時停止と開始については、「[Pause and start your Power BI Embedded capacity in the Azure portal](azure-pbie-pause-start.md)」 (Azure Portal で Power BI Embedded を一時停止し、開始する) を参照してください。

自分のアプリケーションに Power BI コンテンツを埋め込む方法については、[Power BI ダッシュボード、レポート、タイルを埋め込む方法](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/)に関するページを参照してください。

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](http://community.powerbi.com/)。
