---
title: Power BI Desktop でのデータ分類
description: Power BI Desktop でのデータ分類
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 8667823567270680415c2fb0ba2db7846dd968ac
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878324"
---
# <a name="data-categorization-in-power-bi-desktop"></a>Power BI Desktop でのデータ分類
**Power BI Desktop** では、ユーザーが列に対してデータ カテゴリを指定すれば、Power BI Desktop が視覚化するときにその列の値をどのように扱うべきかを自動的に見極めます。

Power BI Desktop にデータがインポートされると、データそのものだけでなく、テーブル名と列名、主キーがあるかどうかなどの情報も取得されます。Power BI Desktop はその情報を利用して推測し、視覚化を作成するときの既定のユーザー エクスペリエンスの質を高めます。 

次に例を示します。Power BI Desktop で列に数値が含まれていることが検出されると、ユーザーはおそらくその列を何らかの方法で集計するので、その列は [値] 領域に置かれます。 あるいは、列に日付/時刻値が含まれている場合は、ユーザーはその列を折れ線グラフの時間階層軸として使用するだろうと推測します。

しかし、地理的な場所など、判断がもう少し難しい場合があります。 Excel ワークシートにある次の表について考えてみましょう。

![](media/desktop-data-categorization/datacategorizationtable.png)

Power BI Desktop は GeoCode 列に含まれるコードを、国の省略形として扱うべきでしょうか? それとも米国の州の省略形でしょうか?  このようなコードはどちらの意味も持つので、明確にはわかりません。  たとえば、AL はアラバマ州とアルバニア、AR はアーカンソー州とアルゼンチン、CA はカリフォルニア州とカナダの意味になり得ます。 これは、地図上に GeoCode フィールドを表示しようとするときに違いが出ます。  Power BI Desktop は、世界地図の画像で国を強調表示するべきでしょうか? それとも米国の画像で州を強調表示するべきでしょうか?  このような場合は、データにデータ カテゴリを指定することができます。 データ分類を指定して、Power BI Desktop が使用できる情報をさらに細分化すれば、最適なビジュアルを得ることができます。  

**データ カテゴリを指定するには**

1. レポート ビューまたはデータ ビューの **[フィールド]** リストの一覧で、異なる分類でソートしたいフィールドを選択します。
2. リボンの **[モデリング]** タブで、 **[データ カテゴリ]** ドロップダウン リストをクリックします。  このリストには、列に対して選択可能なデータ カテゴリが表示されます。  列の現在のデータ型には使えない項目は選べなくなっています。  たとえば、列がバイナリ データ型である場合、Power BI Desktop で地理的なデータ カテゴリを選べなくなります。 

![](media/desktop-data-categorization/datacategorization.gif)

これで完了です。  ビジュアルで通常想定されるすべての動作は、自動的に動作するようになります。  

関心がある場合は、[Power BI モバイル アプリの地理的フィルタリング](desktop-mobile-geofiltering.md)についても参照してください。

