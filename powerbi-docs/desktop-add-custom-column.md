---
title: Power BI Desktop でカスタム列を追加する
description: Power BI Desktop で新しいカスタム列をすばやく作成します
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 443053bc973005d3e2a655b1222d049a4251e7d7
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73878875"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Power BI Desktop でカスタム列を追加する

Power BI Desktop でクエリ エディターを使用して、データの新しいカスタム列をモデルに簡単に追加できます。 クエリ エディターでは、カスタム列を定義するために [PowerQuery M 式クエリ](https://docs.microsoft.com/powerquery-m/quick-tour-of-the-power-query-m-formula-language)を作成して、カスタム列を作成したり、名前を変更したりすることができます。 PowerQuery M 式クエリには、[包括的な関数参照コンテンツ セット](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference)があります。 

クエリ エディターでカスタム列を作成すると、Power BI Desktop によって、クエリの **[クエリの設定]** に **[適用したステップ]** として追加されます。 いつでも変更、移動、または修正できます。

![[カスタム列の追加] ページ](media/desktop-add-custom-column/add-custom-column_01.png)

## <a name="use-query-editor-to-add-a-custom-column"></a>クエリ エディターを使用してカスタム列を追加する

カスタム列の作成を開始するには、次の手順を実行します。

1. Power BI Desktop を起動し、いくつかのデータを読み込みます。

2. リボンの **[ホーム]** タブで **[クエリの編集]** を選択し、メニューの **[クエリの編集]** を選択します。

   ![[クエリの編集] を選択する](media/desktop-add-custom-column/add-column-from-example_02.png)

   **[クエリ エディター]** ウィンドウが表示されます。 

2. リボンの **[列の追加]** タブで、 **[カスタム列]** を選択します。

   ![[カスタム列] を選択する](media/desktop-add-custom-column/add-custom-column_02.png)

   **[カスタム列の追加]** ウィンドウが表示されます。

## <a name="the-add-custom-column-window"></a>[カスタム列の追加] ウィンドウ

**[カスタム列の追加]** ウィンドウには、以下の機能があります。 
- 右側の **[利用可能な列]** ボックスに、利用可能な列の一覧が表示されます。

- **[新しい列名]** ボックスに、カスタム列の初期名が表示されます。 この列の名前は、変更できます。

- **[カスタム列の式]** ボックスに、[PowerQuery M 式クエリ](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference)が表示されます。 これらのクエリを作成するには、新しいカスタム列を定義する数式を作成します。 

   ![[カスタム列の追加] ページ](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>カスタムの列の式を作成する

1. 右側の **[利用可能な列]** の一覧で列を選択し、一覧の下の **[挿入]** を選択して、カスタム列の式に追加します。 一覧で列をダブルクリックして追加することもできます。

2. 数式を入力して列を作成するときに、 **[カスタム列の追加]** ウィンドウの下部にあるインジケーターを確認します。 

   エラーがない場合は、緑色のチェック マークと、"*構文エラーが検出されませんでした*" というメッセージが表示されます。

   ![[カスタム列の追加] ページでの成功した構文チェック](media/desktop-add-custom-column/add-custom-column_04.png)

   構文エラーがある場合は、黄色の警告アイコンと、数式内のエラーが発生した場所へのリンクが表示されます。

   ![[カスタム列の追加] ページでのエラー](media/desktop-add-custom-column/add-custom-column_05.png)

3. **[OK]** を選択します。 

   Power BI Desktop によってカスタム列がモデルに追加され、 **[クエリの設定]** にあるクエリの **[適用したステップ]** の一覧に **[追加されたカスタム]** ステップが追加されます。

   ![[クエリの設定] に追加されたカスタム列](media/desktop-add-custom-column/add-custom-column_06.png)

4. カスタム列を変更するには、 **[適用したステップ]** の一覧の **[追加されたカスタム]** ステップをダブルクリックします。 

   **[カスタム列の追加]** ウィンドウが表示され、作成したカスタム列の式が示されます。

## <a name="use-the-advanced-editor-for-custom-columns"></a>カスタム列に対して詳細エディターを使用する

クエリの作成後、**詳細エディター**を使用して、クエリの任意のステップを変更することもできます。 これを行うには、次の手順に従います。

1. **[クエリ エディター]** ウィンドウで、リボンの **[ビュー]** タブを選択します。 

2. **[詳細設定エディター]** を選択します。

   **[詳細エディター]** ページが表示され、クエリを完全に制御できます。 

   ![[詳細エディター] ページ](media/desktop-add-custom-column/add-custom-column_07.png)

   
## <a name="next-steps"></a>次の手順

- カスタム列を作成するには、クエリ エディターに提供する例に基づいて列を作成するなど、他の方法もあります。 詳細については、「[Power BI Desktop で例から列を追加する](desktop-add-column-from-example.md)」を参照してください。

- Power Query M のリファレンス情報については、「[Power Query M 関数リファレンス](/powerquery-m/power-query-m-function-reference)」を参照してください。

