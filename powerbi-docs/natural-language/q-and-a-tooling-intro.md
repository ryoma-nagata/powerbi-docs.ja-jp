---
title: Power BI Q&A をトレーニングするための Q&A ツールの概要 (プレビュー)
description: Power BI Q&A ツールの概要
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: maggies
ms.openlocfilehash: 6178c9f157578110a09abf3fcbebccba54339f13
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866076"
---
# <a name="intro-to-qa-tooling-to-train-power-bi-qa-preview"></a>Power BI Q&A をトレーニングするための Q&A ツールの概要 (プレビュー)

Power BI Q&A "*ツール*" を使用すると、ユーザーの自然言語エクスペリエンスを向上させることができます。 デザイナーまたは管理者は、自然言語エンジンを操作し、次の 3 つの領域を強化します。 

- ユーザーが寄せた質問を確認する。
- 質問を理解できるように Q&A を学習させる。
- Q&A に学習させた用語を管理する。

これらの専用ツール機能のほかにも、Power BI Desktop の **[モデリング]** タブには、多くのオプションが用意されています。  

- 同意語
- 行ラベル
- Q&A に非表示する
- 言語スキーマを構成する (詳細設定)

## <a name="get-started-with-qa-tooling"></a>Q&A ツールの概要

Q&A ツールは Power BI Desktop 内でのみ使用でき、現在はインポート モードのみをサポートしています。

1. Power BI Desktop を開き、Q&A を使用してビジュアルを作成します。 
2. ビジュアルの隅にある歯車アイコンを選択します。 

    ![Q&A ビジュアルの歯車](media/q-and-a-tooling-intro/qna-visual-gear.png)

    [作業の開始] ページが開きます。  

    ![Q&A の [作業の開始]](media/q-and-a-tooling-intro/qna-tooling-dialog.png)

### <a name="review-questions"></a>質問の確認

**[質問の確認]** を選択すると、自分のテナントの Power BI サービス内で使用されているデータセットの一覧が表示されます。 **[質問の確認]** ページには、データセットの所有者、ワークスペース、および最終更新日も表示されます。 ここでは、データセットを選択したり、ユーザーが寄せた質問を確認したりできます。 データには、認識されなかった単語も表示されます。 ここに表示されるデータはすべて過去 28 日間のものです。

![Q&A の [質問の確認]](media/q-and-a-tooling-intro/qna-tooling-review-questions.png)

### <a name="teach-qa"></a>Q&A トレーニング

**[Q&A の学習]** セクションでは、Q&A をトレーニングして単語を認識させることができます。 まず、Q&A が認識しなかった単語を含む質問を入力します。 Q&A により、その用語の定義を求めるプロンプトが表示されます。 その単語が表すものに対応するフィルターまたはフィールド名を入力します。 そうすると、Q&A が元の質問を解釈し直します。 結果に満足したら、自分の入力を保存します。 詳細については、[Q&A トレーニング](q-and-a-tooling-teach-q-and-a.md)に関するページを参照してください

![[Q&A の学習]、シノニム、プレビュー](media/q-and-a-tooling-intro/qna-tooling-teach-fixpreview.png)

### <a name="manage-terms"></a>用語の管理

ここには、[Q&A の学習] セクションで保存したすべてのものが表示されます。そのため、定義した用語を確認したり削除したりすることができます。 現在、既存の定義を編集することはできません。そのため、用語を再定義するには、その用語を削除してから再作成する必要があります。

![Q&A の [用語の管理]](media/q-and-a-tooling-intro/qna-manage-terms.png)

### <a name="suggest-questions"></a>質問の提案

設定を行わないと、Q&A ビジュアルでは開始するためのいくつかの質問が提案されます。 これらの質問は、データ モデルに基づいて自動的に生成されます。 **[質問の提案]** では、自動的に生成された質問を独自の質問で上書きすることができます。 

開始するには、追加する質問をテキスト ボックスに入力します。 プレビュー セクションには、Q & ビジュアルの結果がどのように示されるかが表示されます。 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-suggest-questions.png" alt-text="Q&A の質問の提案":::
 
**[追加]** ボタンを選択すると、 **[Your suggested questions]\(提案した質問\)** にこの質問が追加されます。 質問が追加されるごとに、この一覧の末尾に追加されます。 質問は、この一覧に示すのと同じ順序で Q&A ビジュアルに表示されます。 

:::image type="content" source="media/q-and-a-tooling-intro/power-bi-qna-save-suggest-questions.png" alt-text="提案された質問を保存する":::
 
**[保存]** を選択して、提案された質問の一覧が Q&A ビジュアルに表示されるようにします。 


## <a name="other-qa-settings"></a>Q&A のその他の設定

### <a name="bulk-synonyms"></a>シノニムの一括定義

Power BI Desktop の **[モデリング]** タブには、Q&A のエクスペリエンスを向上させるためのさまざまなオプションがあります。 

1. Power BI Desktop 内で、[モデルリング ビュー] を選択します。

2. フィールドまたはテーブルを選択して、 **[プロパティ]** ペインを表示させます。  このペインはキャンバスの右側に表示され、いくつかの Q&A アクションを一覧表示します。 オプションの 1 つのに **[シノニム]** があります。 **[シノニム]** ボックスでは、選択したテーブルまたはフィールドの代替をすばやく定義できます。 また、ツール ダイアログ ボックスの **[Q&A の学習]** セクションでシノニムを定義することもできますが、通常、テーブル内のたくさんのフィールドに対してシノニムを定義する場合は、こちらの方が高速です。

    ![Q&A の [モデリング] ペインの [シノニム]](media/q-and-a-tooling-intro/qna-modelling-pane-synonyms.png)

3. 1 つのフィールドに対して複数のシノニムを定義するには、コンマを使用して次のシノニムを示します。

### <a name="hide-from-qa"></a>Q&A に非表示する

また、フィールドとテーブルは非表示にして、Q&A の結果に表示されないようにすることもできます。 

1. Power BI Desktop 内で、[モデルリング ビュー] を選択します。

2. フィールドまたはテーブルを選択して **[プロパティ]** ペインを表示し、 **[非表示]** を **[オン]** にします。

    Q&A は、その設定を考慮し、そのフィールドが Q&A によって認識されないようにします。 たとえば、ID フィールドと外部キーを非表示にして、同じ名前のフィールドが不必要に重複しないようにすることができます。 フィールドは非表示にしても、Power BI Desktop の Q&A 以外のビジュアル内で使用できます。

### <a name="set-a-row-label"></a>行ラベルを設定する

行ラベルを使用すると、テーブル内の 1 つの行を最も適切に識別する列 (または "*フィールド*") を定義できます。 たとえば、"Customer" という名前のテーブルの場合、行ラベルは通常 "表示名" になります。 この追加のメタデータを指定すると、ユーザーが「Show me sales by customer」と入力した場合に、Q&A が役に立つビジュアルをプロットできるようになります。 "customer" をテーブルとして扱わず、代わりに "表示名" を使用して、各顧客の売上を示す棒グラフを表示することができます。 行ラベルはモデリング ビューでのみ設定できます。 

1. Power BI Desktop 内で、[モデルリング ビュー] を選択します。

2. テーブルを選択して、 **[プロパティ]** ペインを表示させます。

3. **[行ラベル]** ボックスで、フィールドを選択します。

## <a name="configure-the-linguistic-schema-advanced"></a>言語スキーマを構成する (詳細設定)

Power BI では、基になる自然言語の結果のスコアリングや重み付けの変更など、Q&A 内で自然言語エンジンを徹底的にトレーニングして強化できます。 方法については、[Q&A の言語スキーマの編集と言い回しの追加](q-and-a-tooling-advanced.md)に関するページを参照してください。

## <a name="next-steps"></a>次の手順

自然言語エンジンを強化するためのベスト プラクティスがいくつかあります。 詳細については、「[Q&A ベスト プラクティス](q-and-a-best-practices.md)」を参照してください。
