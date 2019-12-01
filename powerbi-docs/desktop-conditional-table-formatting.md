---
title: Power BI Desktop での条件付きテーブルの書式設定
description: テーブルへのカスタマイズされた書式の適用
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: d28028c7b75bedae958df77c743c52b44c4437d9
ms.sourcegitcommit: 7f27b9eb0e001034e672050735ab659b834c54a3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74311738"
---
# <a name="conditional-formatting-in-tables"></a>テーブルでの条件付き書式設定 
テーブルで条件付き書式を使用するときに、グラデーションを使用するなど、セルの値または他の値やフィールドに基づいてカスタマイズされたセルの色を指定できます。 セルの値と共にデータ バーも表示できます。 

条件付き書式にアクセスするには、Power BI Desktop の **[視覚化]** ウィンドウの **[フィールド]** ウェルで、書式設定する **[値]** ウェルの値の横にある下向きの矢印を選択します (または、フィールドを右クリックします)。 条件付き書式を管理できるのは、 **[フィールド]** ウェルの **[値]** 領域のフィールドだけです。

![[条件付き書式設定] メニュー](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

次のセクションでは、それぞれの条件付き書式設定オプションについて説明します。 1 つまたは複数のオプションを 1 つのテーブル列で結合できます。

> [!NOTE]
> テーブルに適用すると、条件付きで書式設定されたセルに適用されているすべてのカスタム テーブル スタイルが、条件付き書式でオーバーライドされます。

視覚化から条件付き書式を削除するには、再度フィールドを右クリックし、 **[条件付き書式の削除]** を選択し、削除する書式の種類を選択します。

![[条件付き書式の削除] メニュー](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

## <a name="background-color-scales"></a>バックグラウンドのカラー スケール

**[条件付き書式]** を選択し、 **[バックグラウンドのカラー スケール]** を選択すると、次のダイアログが表示されます。

![[バックグラウンドのカラー スケール] ダイアログ](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

フィールドに **[色の基準]** を設定することで、データ モデルから色の基準とするフィールドを選択できます。 さらに、 **[集計]** 値を利用し、選択したフィールドの集計の種類を指定できます。 色が付けられるフィールドは **[色の適用対象]** フィールドに指定されるので、追跡することができます。書式設定の基礎として数値を選択する限り、テキスト フィールドや日付フィールドに条件付き書式設定を適用できます。

![[色の基準] フィールド](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

所定の値範囲に個別の色値を使用するには、 **[ルールに基づく色]** を選択します。 色スペクトルを使用するには、 **[ルールに基づく色]** のチェックを外します。 

![[バックグラウンドのカラー スケール] ダイアログ](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

### <a name="color-by-rules"></a>ルールに基づく色

**[ルールに基づく色]** を選択するとき、1 つまたは複数の色範囲を入力し、そのそれぞれに決まった色を指定できます。  値範囲はそれぞれ、 *[値が次の場合]* 条件で始まり、 *[かつ]* 条件、色と続きます。

![[ルールに基づく色] 値範囲](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

各範囲の値入りテーブル セルには指定の色が付きます。 次の画像には 3 つのルールがあります。

![[ルールに基づく色] の例](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules.png)

サンプル テーブルは次のように表示されます。

![[ルールに基づく色] が適用されたサンプル テーブル](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)


### <a name="color-minimum-to-maximum"></a>最小から最大の色分け

*[最小]* 値と *[最大]* 値とその色を構成できます。 **[左右逆方向]** ボックスをオンにした場合は、オプションの*中央*値も構成できます。

![[左右逆方向] ボタン](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

サンプル テーブルは次のように表示されます。

![色を左右逆方向にしたサンプル テーブル](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

## <a name="font-color-scales"></a>フォントのカラー スケール

**[条件付き書式]** を選択し、 **[フォントのカラー スケール]** を選択すると、次のダイアログが表示されます。 このダイアログは **[バックグラウンドのカラー スケール]** ダイアログに似ていますが、セルの背景色ではなくフォントの色を変更します。

![[フォントのカラー スケール] ダイアログ](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

サンプル テーブルは次のように表示されます。

![フォントのカラー スケールを適用したサンプル テーブル](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="data-bars"></a>データ バー

**[条件付き書式]** を選択し、 **[データ バー]** を選択すると、次のダイアログが表示されます。 

![[データ バー] ダイアログ](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

既定では、 **[バーのみを表示]** オプションは選択されていません。テーブル セルには、バーと実際の値の両方が表示されます。

![データ バーと値を含むサンプル テーブル](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

**[バーのみを表示]** オプションが選択されていると、テーブル セルにはバーのみが表示されます。

![データ バーのみを含むサンプル テーブル](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)

## <a name="color-formatting-by-field-value"></a>フィールド値に基づく色の書式設定

色を指定するメジャーまたは列を使用し、テキスト値または 16 進コードのいずれかを使用して、テーブルにおけるフォントの色の背景やマトリックス ビジュアルにその色を適用することができます。 また、特定のフィールドに対してカスタム ロジックを作成し、そのロジックで目的の色をフォントや背景に適用することができます。

たとえば、次の表には、各製品モデルに関連付けられた色があります。 

![ProductName フィールドと色の名前](media/desktop-conditional-table-formatting/conditional-table-formatting_01.png)

フィールド値に基づいてセルを書式設定するには、そのビジュアルの *Color* 列を右クリックして **[条件付き書式]** を選択し、この場合はメニューから **[背景色]** を選択します。 

![メニューから背景色を選択する](media/desktop-conditional-table-formatting/conditional-table-formatting_02.png)

表示されたダイアログで、次の図のように、 **[書式設定基準]** のドロップダウンの領域で **[フィールド値]** を選択します。

![フィールド値に基づく書式設定](media/desktop-conditional-table-formatting/conditional-table-formatting_03.png)

フォントの色に対してこのプロセスを繰り返すことができます。次の画面のように、ビジュアルの結果は **Color** 列で単色になります。

![フィールド値に基づく書式設定](media/desktop-conditional-table-formatting/conditional-table-formatting_04.png)

また、希望する条件に基づいてさまざまな 16 進コードを出力するビジネス ロジックに基づいて、DAX 計算を作成することもできます。 通常、これは条件付き書式に複数のルールを作成するより簡単です。 次のサンプル イメージの *ColorKPI* フィールドを検討してください。

![DAX 計算](media/desktop-conditional-table-formatting/conditional-table-formatting_05.png)

次に、以下の方法で **[背景色]** にフィールド値を設定できます。

![KPI に基づいてフィールドの色を設定する](media/desktop-conditional-table-formatting/conditional-table-formatting_06.png)

次のマトリックスのような結果を取得することができます。

![色に基づく KPI 値を使用したマトリックス ビジュアル](media/desktop-conditional-table-formatting/conditional-table-formatting_07.png)

想像力と DAX を少し使うだけで、より多くのバリエーションを作成できます。

[https://www.w3.org/TR/css-color-3/](https://www.w3.org/TR/css-color-3/) にある CSS カラー仕様に一覧されている次の値のいずれかを使用して、ビジュアルの色を設定できます。
* 3、6、または 8 桁の 16 進コード (例: #3E4AFF)。 コードの先頭に # 記号が含まれていることを確認します。 "3E4AFF" は受け入れられません。 
* RGB 値または RGBA 値 (例: RGBA(234, 234, 234, 0.5))
* HSL 値または HSLA 値 (例: HSLA (123, 75%, 75%, 0.5))
* 色の名前 (例: Green、SkyBlue、PeachPuff) 

## <a name="considerations-and-limitations"></a>考慮事項と制限事項
条件付きテーブルの書式設定を使用する場合は、留意すべき考慮事項がいくつかあります。

* 条件付き書式は、**マトリックス** ビジュアルの値にのみ適用され、小計や総計には適用されません。 
* 条件付き書式は **[合計]** 行には適用されません。
* グループがないテーブルは、条件付き書式をサポートしていない単一行として表示されます。
* 自動最大値/最小値を使用したグラデーション書式、または割合のルールを使用したルールベースの書式を使用する場合、データに NaN 値が含まれていると、条件付き書式を適用することはできません。 NaN は 'Not a number' (数値ではない) を意味します。これは、通常、ゼロ除算エラーによって発生します。 このようなエラーを回避するには、[DIVIDE() DAX 関数](https://docs.microsoft.com/dax/divide-function-dax)を使用できます。


## <a name="next-steps"></a>次の手順
詳しくは、次の資料を参照してください。  

* [Power BI における色の書式設定に関するヒントとコツ](visuals/service-tips-and-tricks-for-color-formatting.md)  

