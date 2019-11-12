---
title: Power BI レポート ビルダーでの式の例
description: 式は、Power BI ページ分割されたレポート ビルダーのページ分割されたレポートで、内容とレポートの外観を制御するためによく使われます。
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 06847956eae4dfefc7cff75b5a360fbb8b892c39
ms.sourcegitcommit: d173e22f5a3e76717adfaa573ea391bde0338ffe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728562"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Power BI レポート ビルダーでの式の例
式は、Power BI ページ分割されたレポート ビルダーのページ分割されたレポートで、内容とレポートの外観を制御するためによく使われます。 式を記述するには Microsoft Visual Basic を使い、式では組み込み関数、カスタム コード、レポートとグループ変数、およびユーザー定義変数を使うことができます。 式は等号 (=) で始まります。   

このトピックでは、レポートの一般的なタスクに使用できる式の例を示します。  
  
-   [Visual Basic の関数](#VisualBasicFunctions): Visual Basic の日付、文字列、変換、条件関数の例。  
  
-   [レポート関数](#ReportFunctions): 集計およびその他の組み込みレポート関数の例。  
  
-   [レポート データの外観](#AppearanceofReportData): レポートの外観を変更する例。  
  
-   [プロパティ](#Properties): レポート アイテムのプロパティを設定して書式または表示状態を制御する例。  
  
-   [パラメーター](#Parameters): 式の中でパラメーターを使用する例。  
  
-   [カスタム コード](#CustomCode): 埋め込みカスタム コードの例。  
  
単純な式と複雑な式、式を使用できる場所、および式に含めることができる参照の種類について詳しくは、「[Expressions in Power BI Report Builder](report-builder-expressions.md)」(Power BI レポート ビルダーでの式) のトピックをご覧ください。 
  
## <a name="functions"></a>関数  
 レポート内の多くの式には、関数が含まれます。 これらの関数を使って、データの書式設定、ロジックの適用、レポートのメタデータへのアクセスを行うことができます。 Microsoft Visual Basic ランタイム ライブラリの関数や、`xref:System.Convert` および `xref:System.Math` 名前空間の関数を使って、式を記述することができます。 カスタム コード内の関数への参照を追加できます。 また、`xref:System.Text.RegularExpressions` などの Microsoft .NET Framework のクラスを使うこともできます。  
  
##  <a name="VisualBasicFunctions"></a> Visual Basic の関数  
 Visual Basic の関数を使って、テキスト ボックスに表示されるデータや、パラメーター、プロパティ、またはレポートの他の領域に使われるデータを、操作することができます。 このセクションでは、これらの関数の使い方を示す例を提供します。 詳しくは、MSDN の「[Visual Basic ランタイム ライブラリのメンバー](https://go.microsoft.com/fwlink/?LinkId=198941)」をご覧ください。  
  
 .NET Framework では、特定の日付形式など、さまざまなカスタム書式オプションが提供されています。 詳しくは、「[型の書式設定](/dotnet/standard/base-types/formatting-types)」をご覧ください。  
  
### <a name="math-functions"></a>数値演算関数  
  
-   **Round** 関数は、数値を最も近い整数に丸めるのに役立ちます。 次の例では、1.3 が 1 に丸められます。  
  
    ```  
    = Round(1.3)  
    ```  
  
     また、Excel の **MRound** 関数のように、数値を指定した値の倍数に丸める式を記述することもできます。 整数値を作成する係数で値を乗算し、数値を丸めた後、同じ係数で除算します。 たとえば、1.3 を最も近い 0.2 の倍数 (1.4) に丸めるには、次の式を使います。  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="DateFunctions"></a> 日付関数  
  
-   **Today** 関数では、現在の日付が提供されます。 この式をテキスト ボックスで使ってレポートに日付を表示したり、パラメーターで使って現在の日付に基づいてデータをフィルター処理したりすることができます。  
  
    ```  
    =Today()  
    ```  
  
-   日付の特定の部分を抽出するには、**DateInterval** 関数を使います。 **DateInterval** の有効なパラメーターを次にいくつか示します。

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    たとえば、次の式では、今日の日付が今年の何週目かが示されます。
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   **DateAdd** 関数は、1 つのパラメーターに基づいて日付の範囲を提供する場合に役立ちます。 次の式では、*StartDate* という名前のパラメーターの日付より 6 か月後の日付が提供されます。  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   **Year** 関数では、特定の日付の年が示されます。 これを使って、日付をグループ化したり、一連の日付に対するラベルとして年を表示したりすることができます。 次の式では、販売注文日の特定のグループに対する年が提供されます。 **Month** 関数および他の関数を使って、日付を操作することもできます。 詳しくは、Visual Basic のドキュメントをご覧ください。  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   式で関数を組み合わせて、形式をカスタマイズすることができます。 次の式では、日付の形式を月 - 日 - 年から月 - 週 - 週の番号に変更します。 たとえば、12/23/2009 は December Week 3 に変換されます。  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     データセット内の計算フィールドとして使うと、グラフでこの式を使って各月の週ごとに値を集計できます。  
  
-   次の式では、SellStartDate の値が MMM-YY として書式設定されます。 SellStartDate フィールドは、datetime データ型です。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   次の式では、SellStartDate の値が dd/MM/yyyy として書式設定されます。 SellStartDate フィールドは、datetime データ型です。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   **CDate** 関数では、値が日付に変換されます。 **Now** 関数では、システムに従った現在日時を含む日付値が返されます。 **DateDiff** では、2 つの Date 値の間に含まれる時間間隔数を示す Long 値が返されます。  
  
     次の例では、現在の年の開始日が表示されます  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   次の例では、現在の月に基づいて、前の月の開始日が表示されます。  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   次の式では、SellStartDate と LastReceiptDate の間隔の年数が生成されます。 これらのフィールドは、2 つの異なるデータセット DataSet1 と DataSet2 に含まれます。  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   **DatePart** 関数では、特定の Date 値の指定したコンポーネントに含まれる Integer 値が返されます。次の式では、DataSet1 に含まれる SellStartDate の最初の値の年が返されます。 レポートには複数のデータセットがあるため、データセットのスコープを指定します。  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   **DateSerial** 関数では、指定した年、月、日と午前 0 時に設定された時刻情報を表す Date 値が返されます。 次の例では、現在の月に基づいて、前の月の終了日が表示されます。  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   次の式では、ユーザーが選択した日付のパラメーター値に基づいて、さまざまな日付が表示されます。  
  
|例の説明|例|  
|-------------------------|-------------|  
|昨日|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|2 日前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|1 か月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|2 か月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|1 年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|2 年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="StringFunctions"></a> 文字列関数  
  
-   連結演算子と Visual Basic の定数を使って、複数のフィールドを結合します。 次の式では、2 つのフィールドが返され、同じテキスト ボックスの異なる行に表示されます。  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   文字列内の日付と数値を、**Format** 関数で書式設定します。 次の式では、*StartDate* および *EndDate* パラメーターの値が、長い日付形式で表示されます。  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     テキスト ボックスに日付または数値のみが含まれる場合は、テキスト ボックス内で **Format** 関数を使う代わりに、テキスト ボックスの Format プロパティを使って書式設定を適用する必要があります。  
  
-   **Right**、**Len**、および **InStr** 関数は、部分文字列を返す場合に便利です。たとえば、*DOMAIN*\\*username* をトリミングしてユーザー名だけにします。 次の式では、*User* という名前のパラメーターからバックスラッシュ (\\) 文字の右側にある文字列の部分が返されます。  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     次の式の結果は前の式と同じ値ですが、Visual Basic の関数ではなく、.NET Framework の `xref:System.String` クラスのメンバーを使っています。  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   複数値パラメーターから選択した値を表示します。 次の例では、**Join** 関数を使って、*MySelection* パラメーターの選択した値を 1 つの文字列に連結しています。これを、レポート アイテム内のテキスト ボックスの値に対する式として設定できます。  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     次の例では、上の例と同じことを行うだけでなく、選択した値の一覧の前にテキスト文字列を表示しています。  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   .NET Framework の `xref:System.Text.RegularExpressions` の **Regex** 関数は、既存の文字列の形式を変更するのに便利です (たとえば、電話番号の書式設定)。 次の式では、**Replace** 関数を使って、フィールド内の 10 桁の電話番号の形式を、"*nnn*-*nnn*-*nnnn*" から "(*nnn*) *nnn*-*nnnn*" に変更しています。  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Fields!Phone.Value の値に余分なスペースがないこと、および `xref:System.String` 型であることを確認します。  
  
### <a name="lookup"></a>Lookup  
  
-   キー フィールドを指定することにより、**Lookup** 関数を使ってデータセットから一対一のリレーションシップに対する値を取得できます (たとえば、キー/値ペア)。 次の式では、データセット ("Product") から、指定した製品 ID に一致する製品名が表示されます。  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   キー フィールドを指定することにより、**LookupSet** 関数を使って、データセットから一対多のリレーションシップに対する値のセットを取得できます。 たとえば、1 人の人が複数の電話番号を持つ場合があります。 次の例では、PhoneList データセットの各行には、個人識別子と電話番号が含まれているものとします。 **LookupSet** では、値の配列が返されます。 次の式では、戻り値を 1 つの文字列に結合し、ContactID で指定されたユーザーの電話番号の一覧を表示しています。  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="ConversionFunctions"></a> 変換関数  
 Visual Basic の関数を使って、フィールドをあるデータ型から別のデータ型に変換できます。 変換関数を使うと、フィールドの既定のデータ型を計算に必要なデータ型に変換したり、テキストを結合したりできます。  
  
-   次の式では、定数 500 を、フィルター式の Value フィールドで Transact-SQL の通貨データ型と比較するために Decimal 型に変換しています。  
  
    ```  
    =CDec(500)  
    ```  
  
-   次の式では、複数値パラメーター *MySelection* で選択されている値の数が表示されます。  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="DecisionFunctions"></a> 決定関数  
  
-   **Iif** 関数では、式が true かどうかに応じて、2 つの値のいずれかが返されます。 次の式では、**Iif** 関数を使って、`LineTotal` の値が 100 を超えている場合は、ブール値 **True** を返します。 それ以外の場合は、**False** を返します。  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   `PctComplete` の値に応じて 3 つの値のいずれかを返すには、複数の **IIF** 関数 ("入れ子になった IIF" とも呼ばれます) を使います。 テキスト ボックスの塗りつぶし色に次の式を配置して、テキスト ボックスの値に応じて背景色を変更できます。  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     値が 10 以上の場合は緑の背景、1 から 9 の場合は青の背景、1 未満の場合は赤の背景が表示されます。  
  
-   同じ機能を別の方法で実現するには、**Switch** 関数を使います。 **Switch** 関数は、テストする条件が 3 つ以上ある場合に便利です。 **Switch** 関数では、一連の式の中で true と評価された最初の式に関連付けられている値が返されます。  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     値が 10 以上の場合は緑の背景、1 から 9 の場合は青の背景、1 の場合は黄の背景、0 以下の場合は赤の背景が表示されます。  
  
-   `ImportantDate` フィールドの値を調べて、1 週間より古い場合は "Red" を返し、それ以外の場合は "Blue" を返します。 この式を使って、レポート アイテム内のテキスト ボックスの Color プロパティを制御できます。  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   `PhoneNumber` フィールドの値を調べて、**null** (Visual Basic では **Nothing**) の場合は "No Value" を返し、それ以外の場合は電話番号の値を返します。 この式を使って、レポート アイテム内のテキスト ボックスの値を制御できます。  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   `Department` フィールドの値を調べて、サブレポートの名前または **null** (Visual Basic では **Nothing**) を返します。 この式を、条件付きドリルスルー サブレポートに使用できます。  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   フィールドの値が null かどうかを調べます。 この式を使って、画像レポート アイテム内の **Hidden** プロパティを制御できます。 次の例では、フィールドの値が null ではない場合にのみ、LargePhoto フィールドで指定される画像が表示されます。  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   **MonthName** 関数は、指定した月の名前を含む文字列値が返されます。 次の例では、フィールドの値が 0 の場合、Month フィールドに NA と表示します。  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="ReportFunctions"></a> レポート関数  
 式では、レポート内のデータを操作する他のレポート関数への参照を追加できます。 このセクションでは、これらの関数のうち 2 つについての例を示します。 
  
###  <a name="Sum"></a> Sum  
  
-   **Sum** 関数では、グループ内またはデータ領域内の値の合計を計算できます。 この関数は、グループのヘッダーまたはフッターで役に立ちます。 次の式では、Order グループまたはデータ領域のデータの合計が表示されます。  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   条件付き集計計算に **Sum** 関数を使うこともできます。 たとえば、データセットに State という名前で取り得る値が Not Started、Started、Finished であるフィールドがある場合、次の式をグループ ヘッダーに配置すると、値 Finished の合計だけが計算されます。  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="RowNumber"></a> RowNumber  
  
-   **RowNumber** 関数をデータ領域内のテキスト ボックスで使うと、式が含まれるテキスト ボックスの各インスタンスの行番号が表示されます。 この関数は、テーブルの行に番号を付けるときに便利な場合があります。 また、行数に基づいて改ページするなど、より複雑なタスクにも役に立つことがあります。 詳しくは、このトピックの「[改ページ](#PageBreaks)」をご覧ください。  
  
     **RowNumber** に対して指定するスコープにより、番号の付け直しを始めるタイミングを制御します。 **Nothing** キーワードは、最も外側のデータ領域の最初の行からカウントを始めることを示します。 入れ子になったデータ領域内でカウントを始めるには、データ領域の名前を使います。 グループ内でカウントを始めるには、グループの名前を使います。  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="AppearanceofReportData"></a> レポート データの表示方法  
 式を使って、レポートでのデータの表示方法を操作できます。 たとえば、2 つのフィールドの値を 1 つのテキスト ボックスに表示したり、レポートに関する情報を表示したり、レポートに改ページを挿入する方法を制御したりすることができます。  
  
###  <a name="PageHeadersandFooters"></a> ページのヘッダーとフッター  
 レポートを設計するとき、レポートの名前とページ番号をレポート フッターに表示したい場合があります。 これは、次の式を使って行うことができます。  
  
-   次の式では、レポートの名前とそれが実行された時刻が提供されます。 レポートのフッターまたはレポートの本体のテキスト ボックスに配置できます。 時刻の書式は、.NET Framework の短い日付用の書式文字列で設定されてます。  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   レポートのフッターのテキスト ボックスに配置された次の式では、ページ番号とレポートの総ページ数が提供されます。  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 次の例では、ディレクトリ一覧と同じように、ページの最初の値と最後の値をページ ヘッダーに表示する方法について説明します。 データ領域には `LastName` という名前のテキスト ボックスが含まれるものとします。  
  
-   次の式をページ ヘッダーの左側のテキスト ボックスに配置し、ページの `LastName` テキスト ボックスの最初の値を提供します。  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   次の式をページ ヘッダーの右側のテキスト ボックスに配置し、ページの `LastName` テキスト ボックスの最後の値を提供します。  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 次の例では、ページの合計を表示する方法について説明します。 データ領域には `Cost` という名前のテキスト ボックスが含まれるものとします。  
  
-   次の式をページのヘッダーまたはフッターに配置して、値の合計をページの `Cost` テキスト ボックスに提供します。  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  ページのヘッダーまたはフッターの 1 つの式で参照できるレポート アイテムは 1 つだけです。 また、ページのヘッダーおよびフッターの式では、テキスト ボックスの名前を参照することはできますが、テキスト ボックス内の実際のデータ式は参照できません。  
  
###  <a name="PageBreaks"></a> 改ページ  
 レポートによっては、グループやレポート アイテムの代わりに、またはグループやレポート アイテムに加えて、指定した行数の最後に改ページを配置する場合があります。 これを行うには、目的のグループまたは詳細レコードを含むグループを作成し、グループに改ページを追加して、指定した行数でグループにグループ式を追加します。  
  
-   次の式をグループ式に配置すると、25 行ごとに値が割り当てられます。 グループに対して改ページを定義すると、この式により 25 行ごとに改ページが挿入されます。  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     1 ページの行数をユーザーが設定できるようにするには、次の式で示すように、`RowsPerPage` という名前のパラメーターを作成し、グループ式をそのパラメーターに基づくようにします。  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="Properties"></a> プロパティ  
 式は、テキスト ボックスにデータを表示するためだけに使われるのではありません。 レポート アイテムにプロパティを適用する方法を変更するためにも使用できます。 レポート アイテムのスタイル情報や、その表示状態を変更できます。  
  
###  <a name="Formatting"></a> 書式設定  
  
-   次の式をテキスト ボックスの Color プロパティで使うと、`Profit` フィールドの値に応じてテキストの色が変更されます。  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     Visual Basic のオブジェクト変数 `Me` を使うこともできます。 この変数は、テキスト ボックスの値を参照するもう 1 つの方法です。  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   次の式をデータ領域のレポート アイテムの BackgroundColor プロパティで使うと、各行の背景色が薄緑と白の交互になります。  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     スコープを指定して式を使う場合は、集計関数に対してデータセットを指定することが必要な場合があります。  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  使用できる色は、.NET Framework の KnownColor 列挙型から取得します。  
  
### <a name="chart-colors"></a>グラフの色  
 図形グラフの色を指定するには、データ ポイント値に色がマップされる順序を制御するカスタム コードを使用できます。 これは、同じカテゴリ グループを使う複数のグラフに対して一貫した色を使うのに役立ちます。 
  
###  <a name="Visibility"></a> 表示状態  
 レポート アイテムの表示状態プロパティを使って、レポート内のアイテムを表示または非表示にすることができます。 テーブルなどのデータ領域では、式の値に基づいて詳細行を最初は非表示にしておくことができます。  
  
-   次の式をグループ内の詳細行の初期表示状態に対して使うと、`PctQuota` フィールドが 90% を超えるすべての売上の詳細行が表示されます。  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   次の式をテーブルの Hidden プロパティに設定すると、12 行より多い場合にのみテーブルが表示されます。  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   次の式を列の **Hidden** プロパティに設定すると、データがデータ ソースから取得された後で、レポート データセットにフィールドが存在する場合にのみ、列が表示されます。  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="Hyperlinks"></a> URL  
 レポート データを使って URL をカスタマイズでき、テキスト ボックスに対するアクションとして URL を追加するかどうかを条件付きで制御することもできます。  
  
-   次の式をテキスト ボックスのアクションとして使うと、URL パラメーターとしてデータセット フィールド `EmployeeID` を指定するカスタマイズされた URL が生成されます。  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   次の式では、テキスト ボックスに URL を追加するかどうかが、条件付きで制御されます。 この式は `IncludeURLs` という名前のパラメーターに依存し、レポートにアクティブな URL を含めるかどうかをユーザーが決定できます。 この式は、テキスト ボックスにアクションとして設定されます。 パラメーターを False に設定してからレポートを表示すると、ハイパーリンクなしで Microsoft Excel にレポートをエクスポートできます。  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="ReportData"></a> レポート データ  
 式を使って、レポートで使われるデータを操作できます。 パラメーターおよび他のレポート情報を参照することができます。 レポートのデータを取得するために使われるクエリを変更することもできます。  
  
###  <a name="Parameters"></a> パラメーター  
 パラメーターで式を使って、パラメーターの既定値を変更することができます。 たとえば、レポートの実行に使われたユーザー ID に基づき、パラメーターを使って、特定のユーザー向けにデータをフィルター処理できます。  
  
-   次の式をパラメーターの既定値として使うと、レポートを実行しているユーザーのユーザー ID が収集されます。  
  
    ```  
    =User!UserID  
    ```  
  
-   クエリ パラメーター、フィルター式、テキスト ボックス、またはレポートの他の領域でパラメーターを参照するには、**Parameters** グローバル コレクションを使います。 次の例では、パラメーターの名前が *Department* であるものとします。  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Parameters をレポートで作成しても、非表示に設定することができます。 レポートがレポート サーバーで実行されても、パラメーターはツール バーに表示されず、レポートのユーザーは既定値を変更できません。 既定値に設定された非表示パラメーターを、カスタム定数として使うことができます。 フィールド式などの任意の式で、この値を使うことができます。 次の式では、*ParameterField* という名前のパラメーターに対する既定のパラメーター値によって指定されたフィールドを識別します。  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="CustomCode"></a> カスタム コード  
 レポートに埋め込まれたカスタム コードを使用できます。 
  
### <a name="using-group-variables-for-custom-aggregation"></a>カスタム集計に対するグループ変数の使用  
 特定のグループ スコープのローカルなグループ変数に対する値を初期化した後、その変数への参照を式に含めることができます。 カスタム コードでグループ変数を使用できる方法の 1 つは、カスタム集計を実装することです。 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>実行時に null 値またはゼロ値を表示しない  
 レポートの処理時に、式の一部の値が null または未定義と評価されることがあります。 これにより、評価された式ではなく **#Error** がテキスト ボックスに表示される実行時エラーが発生する可能性があります。 **IIF** 関数は、If-Then-Else ステートメントとは異なり、**true** または **false** をテストするルーチンに渡される前に、**IIF** ステートメントの各部分が評価されるため (関数の呼び出しを含めて)、この動作の影響を特に受けやすくなります。 ステートメント `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` は、`Fields!Sales.Value` が NOTHING の場合、レンダリングされるレポートで **#Error** になります。  
  
 この状況を回避するには、次の方法のいずれかを使います。  
  
-   フィールド B の値が 0 または未定義の場合は、分子を 0 に設定し、分母を 1 に設定します。それ以外の場合は、分子をフィールド A の値に設定し、分母をフィールド B の値に設定します。  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   カスタム コード関数を使って、式の値を返します。 次の例では、現在の値と前の値の差の割合を返します。 これを使って、任意の 2 つの連続する値の差を計算でき、最初の比較 (前の値がない場合) のエッジ ケースと、前の値または現在の値のいずれかが **null** (Visual Basic では **Nothing**) であるケースが処理されます。  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     次の式では、"ColumnGroupByYear" コンテナー (グループまたはデータ領域) に対して、テキスト ボックスからこのカスタム コードを呼び出す方法を示します。  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     これは、実行時の例外を回避するのに役立ちます。 これにより、`=IIF(Me.Value < 0, "red", "black")` のような式をテキスト ボックスの **Color** プロパティで使い、値が 0 より大きいか、または小さいかどうかに基づいて、条件付きでテキストを表示することができます。  
  
## <a name="next-steps"></a>次の手順

- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
  
