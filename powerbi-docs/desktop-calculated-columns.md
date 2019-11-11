---
title: Power BI Desktop で計算列を使用する
description: Power BI Desktop の計算列
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 10c6f9f512c1b8c837842247d9dc928e8e065451
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876629"
---
# <a name="using-calculated-columns-in-power-bi-desktop"></a>Power BI Desktop で計算列を使用する
計算列を使うと、既にモデル内に存在するテーブルに新しいデータを追加できます。 しかし、値のクエリを実行してデータ ソースから新しい列に読み込む代わりに、列の値を定義する Data Analysis Expressions (DAX) 数式を作成します。 Power BI Desktop では、レポート ビューの [新しい列] 機能を使用して計算列を作成します

クエリ エディターの [カスタム列の追加] を使用してクエリの一部として作成するカスタム列とは異なり、レポート ビューまたはデータ ビューで作成する計算列は、モデルに既に読み込まれているデータに基づいて作成されます。 たとえば、2 つの異なる (しかし関連する) テーブルの 2 つの異なる列の値を連結して、加算を実行したり、サブ文字列を抽出したりすることができます。

作成した計算列は、他のフィールドと同じように [フィールド] の一覧に表示されますが、その値が数式の結果であることを示す特別なアイコンが表示されます。 列に好きな名前を付けたり、列を他のフィールドと同じようにレポートのビジュアルに追加したりできます。

![](media/desktop-calculated-columns/calccolinpbid_fields.png)

計算列は、結果の計算に [Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx) (DAX) を使用します。これは、Power BI Desktop で取り扱っているようなリレーショナル データを操作することを意図した数式言語です。 DAX は 200 以上の関数、演算子、およびコンストラクトを含むライブラリを提供しているため、数式を作成する際の柔軟性が非常に高く、データ分析に必要なほとんどすべての計算結果を得ることができます。 DAX の詳細については、この記事の最後にある「詳細情報」を参照してください。

DAX の数式は Excel の数式と似ています。 実際には、DAX は Excel と同じ機能が多数あります。 ただし、DAX の関数は、Power BI Desktop などのレポートで、データを対話式にスライスしたりフィルターを掛けたりする操作を意図して設計されています。 Excel ではテーブル内の各行に対して異なる数式を使用できますが、それとは異なり、新しい列に対して DAX 数式を作成すると、テーブル内のすべての行について結果が計算されます。 列の値は必要に応じて再計算されます。たとえば、基になるデータが更新され、値が変更されたときなどです。

## <a name="lets-look-at-an-example"></a>例を見てみましょう
Jeff は Contoso の配送マネージャーであり、さまざまな市区町村への配送の数を表示するレポートを作成したいと考えています。 Jeff は、市区町村と都道府県ごとに異なるフィールドがある Geography テーブルを持っています。 しかし、Jeff はレポートで同じ行の単一の値として市区町村、都道府県を表示したいと考えています。 現時点では、Jeff の Geography テーブルには必要なフィールドがありません。

![](media/desktop-calculated-columns/calccolinpbid_cityandstatefields.png)

しかし、計算列を使用することで、Jeff は [市区町村] 列の市区町村を、[都道府県] 列の都道府県にまとめる、または連結することができます。

Jeff は、Geography テーブルを右クリックした後、[新しい列] をクリックします。 その後、Jeff は次の DAX 式を数式バーに入力します。

![](media/desktop-calculated-columns/calccolinpbid_formula.png)

この数式は単に、CityState という新しい列を作成し、Geography テーブルの各行で [市区町村] 列の値を取り、コンマとスペースを追加し、[都道府県] 列の値を連結します。

これで、Jeff は必要なフィールドを取得しました。

![](media/desktop-calculated-columns/calccolinpbid_citystatefield.png)

Jeff はここで、配送数と共にレポート キャンバスにそれを追加することができます。 これで、Jeff は、すばやく最小限の作業で、ほぼすべての種類の視覚化に追加できる [市区町村, 都道府県] フィールドを取得しました。 Jeff は、マップの視覚エフェクトが作成されたときに、Power BI Desktop で新しい列の [市区町村, 都道府県] の値を読み取る方法が既に把握されていることを理解しています。

![](media/desktop-calculated-columns/calccolinpbid_citystatemap.png)

## <a name="learn-more"></a>詳細情報
ここでは、計算列に関する概要のみを示しました。 この後は、「[チュートリアル:Power BI Desktop で計算列を作成する](desktop-tutorial-create-calculated-columns.md)」を読むことをお勧めします。サンプル ファイルをダウンロードし、さまざまな列を作成する方法についてステップ バイ ステップで学ぶことができます。 

DAX の詳細については、「[Power BI Desktop での DAX の基本事項](desktop-quickstart-learn-dax-basics.md)」をご覧ください。

クエリの一部として作成する列の詳細については、「[Power BI Desktop での一般的なクエリ タスク](desktop-common-query-tasks.md)」の「カスタム列の作成」セクションをご覧ください。  

