---
title: Power BI Q&A 内で質問と用語を理解できるように Q&A を学習させる
description: Power BI Q&A を使用し、実際のデータを探索する方法
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
LocalizationGroup: Ask questions of your datadefintion
ms.openlocfilehash: e5b870201943b93bfdaec2881005785c2f3c470b
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82865810"
---
# <a name="teach-qa-to-understand-questions-and-terms-in-power-bi-qa"></a>Power BI Q&A 内で質問と用語を理解できるように Q&A を学習させる

[Q&A の設定] の **[Q&A の学習]** セクションでは、Q&A が認識しなかった自然言語の質問と用語を理解できるようトレーニングします。 まず、Q&A が認識しなかった単語を含む質問を送信します。 そうすると、Q&A により、その用語の定義を求められます。 その単語が表すものに対応するフィルターまたはフィールド名を入力します。 そうすると、Q&A が元の質問を解釈し直します。 結果に満足したら、保存します。

> [!NOTE]
> [Q&A の学習] 機能では、インポート モードのみがサポートされています。 また、オンプレミスおよび Azure Analysis Services のデータ ソースへの接続はまだサポートされていません。 この制限は、Power BI の今後のリリースでは削除される予定です。

## <a name="start-to-teach-qa"></a>Q&A の学習を開始する

1. Power BI Desktop の **[モデリング]** リボンで、 **[Q&A の設定]**  >  **[Q&A の学習]** の順に選択します。

    ![[Q&A の学習]、シノニム、赤](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-synonym-red.png)

2. Q&A が認識しない用語を含む文を入力し、 **[送信]** を選択します。

3. 赤色の下線で示された単語を選択します。 

    Q&A により、候補が提示され、用語の正しい定義を指定するように求められます。 
    
3. **[Q&A で認識されない用語を定義します]** の下に、定義を指定します。

    ![[Q&A の学習]、シノニム、プレビュー](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-fixpreview.png)

4. **[保存]** を選択します。更新されたビジュアルのプレビューが表示されます。

5. 次の質問を入力するか、 **[X]** を選択して閉じます。

レポートをサービスに再度公開するまで、レポートのコンシューマーには、この変更は表示されません。

## <a name="define-nouns-and-adjectives"></a>名詞と形容詞を定義する

Q&A には、次の 2 種類の語句を学習させることができます。

- 名詞
- 形容詞

### <a name="define-a-noun-synonym"></a>名詞のシノニムを定義する

データを操作する際に、別の名前で呼ぶことがあるフィールド名が使用されている場合がよくあります。 例として、"Sales" があります。 sales を意味する単語や語句は、"revenue" など、たくさんあります。 列の名前が "Sales" の場合に、レポートのコンシューマーが「revenue」と入力すると、Q&A は正しい列を選択して、質問に適切に回答することができない可能性があります。 その場合は、"Sales" と "Revenue" が同じものを指していることを Q&A に教える必要があります。

Q&A は、Microsoft Office のナレッジを使用して、認識できない単語が名詞である場合を自動的に検出します。 Q&A が名詞を検出すると、次のようなプロンプトが表示されます。

- <your term> **refers to** (&lt;your term&gt; は次を指す) 

実際のデータに含まれている用語をボックスに入力します。

![[Q&A の学習]、シノニム、プロンプト](media/q-and-a-tooling-teach-q-and-a/qna-tooling-synonym-prompt.png)

データ モデルのフィールド以外のものを指定すると、望ましくない結果が生じる可能性があります。

### <a name="define-an-adjective-filter-condition"></a>形容詞フィルター条件を定義する

基になるデータの条件として機能する用語を定義することが必要になる場合があります。 例として、"Awesome Publishers" があります。 "Awesome" は、X 個の製品を公開している公開元のみを選択する条件となります。 Q&A は形容詞を検出しようとして、別のプロンプトを表示します。

- <field name> **that have** (次を含む &lt;field name&gt;)  

条件をボックスに入力します。

![[Q&A の学習]、シノニム、プロンプト](media/q-and-a-tooling-teach-q-and-a/qna-tooling-adjectives.png)

定義できる条件の例を次に示します。

- Country which is USA
- Country which is not USA
- Products > 100
- Products greater than 100
- Products = 100
- Products is 100
- Products < 100
- Products smaller than 100

これらの例では、"Products" は列名またはメジャーのいずれかになります。 

Q&A 式自体に集計を指定することもできます。 たとえば ‘popular products’ が 100 単位以上販売された製品である場合は、‘sum of units sold > 100’ の製品を人気製品として定義できます。  

:::image type="content" source="media/q-and-a-tooling-teach-q-and-a/power-bi-qna-popular-products.png" alt-text="'popular products' を定義する":::

ツール内で定義できる条件は1つだけです。 より複雑な条件を定義するには、DAX を使用して計算列またはメジャーを作成した後、ツール セクションを使用して、その列またはメジャーに対して 1 つの条件を作成します。

## <a name="manage-terms"></a>用語の管理

定義を指定した後、戻って、加えた修正をすべて確認し、それを編集または削除することができます。 

1. **[Q&A の設定]** で、 **[用語の管理]** セクションに移動します。

2. 不要になった用語をすべて削除します。 現在、用語を編集することはできません。 用語を再定義するには、用語を削除してから定義します。

    ![Q&A の [用語の管理]](media/q-and-a-tooling-teach-q-and-a/qna-manage-terms.png)

## <a name="next-steps"></a>次の手順

自然言語エンジンを強化するためのベスト プラクティスがいくつかあります。 詳細については、「[Q&A ベスト プラクティス](q-and-a-best-practices.md)」を参照してください。
