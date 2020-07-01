---
title: Power BI Desktop でのヒントのカスタマイズ
description: ドラッグ アンド ドロップでビジュアル用カスタム ヒントを作成
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: a21bccb78df5ba84d3e9a7dc07d9d392c74c0153
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231959"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>Power BI Desktop でヒントをカスタマイズする

ヒントにより、ビジュアル上のデータ ポイントのコンテキスト情報と詳細を、洗練された方法で提供できます。 次の図は、Power BI Desktop のグラフに適用されたヒントを示しています。

![既定のヒント](media/desktop-custom-tooltips/custom-tooltips-1.png)

視覚エフェクトが作成されると、既定のヒントに、データ ポイントの値とカテゴリが表示されます。 ヒント情報のカスタマイズが有用である多くの状況があります。 ヒントのカスタマイズによって、ビジュアルを表示するユーザーに対して、追加のコンテキストと情報が提供されます。 カスタム ヒントを使用すると、ヒントの一部として表示する追加のデータ ポイントを指定できます。

## <a name="how-to-customize-tooltips"></a>ヒントをカスタマイズする方法

カスタマイズされたヒントを作成するには、次の図に示すように、 **[視覚化]** ペインの **[フィールド]** ウェルで、フィールドを **[ヒント]** バケットにドラッグします。 次の図では、3 つのフィールドが **[ヒント]** バケットに配置されています。

![ヒント フィールドの追加](media/desktop-custom-tooltips/custom-tooltips-2.png)

**[ヒント]** にヒントが追加されると、視覚化上のデータ ポイントにポインターを合わせたときに、それらのフィールドの値が表示されます。

![カスタム ヒント](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-measures"></a>集計またはクイック メジャーでのヒントのカスタマイズ

集計関数または*クイック メジャー*を選択することで、ヒントをさらにカスタマイズできます。 **[ヒント]** バケット内のフィールドの横にある矢印を選択します。 次に、使用可能なオプションから選択します。

![クイック メジャーでのヒント](media/desktop-custom-tooltips/custom-tooltips-4.png)

ダッシュボードやレポートを閲覧するユーザーに情報と分析情報をすばやく伝えるために、データセットで使用できるフィールドを使用して、ヒントをカスタマイズする方法は多数あります。
