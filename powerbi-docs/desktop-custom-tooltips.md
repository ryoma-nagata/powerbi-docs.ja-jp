---
title: Power BI Desktop でのヒントのカスタマイズ
description: ドラッグ アンド ドロップでビジュアル用カスタム ヒントを作成
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: d5259ba22287a8a2ade3107e4320c39713dcb45e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239750"
---
# <a name="customizing-tooltips-in-power-bi-desktop"></a>Power BI Desktop でのヒントのカスタマイズ
ヒントにより、ビジュアル上のデータ ポイントのコンテキスト情報と詳細を、洗練された方法で提供できます。 次の図は、Power BI Desktop のグラフに適用されたヒントを示しています。

![既定のヒント](media/desktop-custom-tooltips/custom-tooltips-1.png)

視覚エフェクトが作成されると、既定のヒントに、データ ポイントの値とカテゴリが表示されます。 ツール ヒント情報をカスタマイズすると便利な場合が多く、ビジュアルを表示しているユーザーに追加のコンテキストと情報を提供できます。 カスタム ヒントを使用すると、ヒントの一部として表示する追加のデータ ポイントを指定できます。

## <a name="how-to-customize-tooltips"></a>ヒントをカスタマイズする方法
カスタマイズされたヒントを作成するには、次の図に示すように、**[視覚化]** ウィンドウの **[フィールド]** ウェルで、フィールドを **[ヒント]** バケットにドラッグします。 次の図では、2 つのフィールドが **[ヒント]** バケットに配置されています。

![ヒント フィールドの追加](media/desktop-custom-tooltips/custom-tooltips-2.png)

ヒントがフィールド ウェルに追加されると、視覚エフェクトのデータ ポイントにポインターを合わせたときに、そのフィールドの値がヒントに表示されます。

![カスタム ヒント](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-calcs"></a>集計または簡単な計算でのヒントのカスタマイズ
ヒントをさらにカスタマイズするには、**[ヒント]** バケットのフィールドの横にある矢印を使用して集計関数または *[簡単な計算]* を選択し、使用可能なオプションを選択します。

![簡単な計算でのヒント](media/desktop-custom-tooltips/custom-tooltips-4.png)

データセットで使用できるフィールドを使って**ツール ヒント**をカスタマイズし、ダッシュボードやレポートを閲覧しているユーザーに情報と洞察をすばやく伝える方法は多数あります。

