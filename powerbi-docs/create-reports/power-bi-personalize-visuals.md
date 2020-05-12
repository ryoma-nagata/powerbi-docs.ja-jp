---
title: ユーザーがレポート内のビジュアルをカスタマイズできるようにする
description: レポートの閲覧者は、レポートを編集することなく、独自のビューを作成できます。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/09/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: abc936c6ea4b61e4837e05fbde110e5159296815
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82867118"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>ユーザーがレポート内のビジュアルをカスタマイズできるようにする

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

多くの対象ユーザーとレポートを共有するとき、一部のユーザーが、特定のビジュアルの少し異なるビューを表示することが必要な場合もあります。 場合によっては、軸の内容を入れ替えたり、ビジュアルの種類を変更したり、ツールヒントに何かを追加したりする必要があります。 すべてのユーザーの要件を満たす 1 つのビジュアルを作成するのは困難です。 この新しい機能により、コンシューマーがレポートの読み取りビューで、ビジュアルを探索およびカスタマイズするための権限を与えることができます。 ビジュアルを必要に応じて調整し、戻るためのブックマークとして保存することができます。 レポートの編集アクセス許可を持っている必要はなく、変更のためにレポートの作成者に戻る必要もありません。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="ビジュアルをカスタマイズする":::
 
## <a name="what-report-consumers-can-change"></a>コンシューマーが変更できるレポート

この機能により、コンシューマーは Power BI レポートのビジュアルをアドホック探索することで、さらに洞察を得ることができます。 この機能は、レポート閲覧者の基本的な調査シナリオを有効にする必要があるレポートの作成者にとって理想的です。 レポートの閲覧者が行うことができる変更を次に示します。

- 視覚化の種類の変更
- メジャーまたはディメンションをスワップ アウトする
- 凡例を追加または削除する
- 2 つ以上のメジャーを比較する
- 集計を変更する、など

この機能によって、新しい探索機能が使用できるようになるだけではなく、 コンシューマーが変更をキャプチャして共有する方法も、この機能に含まれています。

- 変更内容をキャプチャする
- 変更内容を共有する
- レポートのすべての変更をリセットする
- ビジュアルのすべての変更をリセットする
- 最近の変更をクリアする

## <a name="turn-on-the-preview-feature"></a>プレビュー機能をオンにする

この機能はプレビュー段階であるため、まず機能スイッチをオンにする必要があります。 **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]** の順に移動します。 **[グローバル]** 設定 > **[プレビュー機能]** で、 **[ビジュアルのカスタマイズ]** が選択されていることを確認します。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-preview-personalize-visual.png" alt-text="[ビジュアルのカスタマイズ] をオンにする":::

現在のファイルの設定で表示するには、Power BI Desktop の再起動が必要な場合もあります。

## <a name="enable-personalization-in-a-report"></a>レポートの個人用設定を有効化する

プレビュー スイッチをオンにした後、コンシューマーがビジュアルをカスタマイズできるようにするレポートに対して、スイッチを明示的に有効にする必要があります。

この機能は Power BI Desktop または Power BI サービスのいずれかで有効にすることができます。

### <a name="in-power-bi-desktop"></a>Power BI Desktop の場合

Power BI Desktop でこの機能を有効にするには、 **[ファイル]**  >  **[オプションと設定]**  >  **[オプション]**  >  **[現在のファイル]**  >  **[レポート設定]** を選択します。 **[視覚エフェクトのカスタマイズ (プレビュー)]** が有効になっていることを確認します。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-settings-personalize-visual.png" alt-text="レポートの個人用設定を有効化する":::

### <a name="in-the-power-bi-service"></a>Power BI サービスの場合

代わりに、Power BI サービスでこの機能を有効にするには、レポートの **[設定]** にアクセスします。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-settings-personalize-visual.png" alt-text="Power BI サービスのレポート設定":::

**[視覚エフェクトのカスタマイズ (プレビュー)]**  >  **[保存]** をオンにします。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-report-service-personalize-visual.png" alt-text="サービスの [ビジュアルのカスタマイズ] をオンにする":::

## <a name="select-visuals-that-can-be-personalized"></a>個人用に設定できるビジュアルを選択する

特定のレポートに対してこの設定を有効にすると、既定では、そのレポート内のすべてのビジュアルをカスタマイズできます。 すべてのビジュアルをカスタマイズしたくない場合は、ビジュアルごとに設定をオンまたはオフにすることができます。

ビジュアルを選択し、 **[視覚化]** ペインで **[書式]** を選択し、 **[ビジュアル ヘッダー]** を展開します。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-header-personalize.png" alt-text="[ビジュアル ヘッダー] を選択する":::
 
**[視覚エフェクトのカスタマイズ]**  >   **[オン]** または **[オフ]** にスライドします。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-format-visual-personalize-on-off.png" alt-text="[視覚エフェクトのカスタマイズ] スライダーをオンまたはオフにする":::

## <a name="personalize-visuals-in-the-power-bi-service"></a>Power BI サービスでビジュアルをカスタマイズする

コンシューマーはビジュアルをカスタマイズすることで、レポートの読み取りビューを離れることなく、さまざまな方法でデータを探索できます。 次の例では、ユーザーがニーズに合わせて視覚化を変更するさまざまな方法を示します。 

1. Power BI サービスの読み取りビューでレポートを開きます。

2. ビジュアルの右上隅にある **[Personalize this visual]\(このビジュアルをカスタマイズする\)** ![[Personalize this visual]\(このビジュアルをカスタマイズする\) アイコン](media/power-bi-personalize-visuals/power-bi-personalize-visual-icon.png) アイコンを選択します。 

### <a name="change-the-visualization-type"></a>視覚化の種類の変更

**視覚化の種類**を変更することで、視覚エフェクトを別の表現で表示できます。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="視覚化の種類を変更する":::
 
### <a name="swap-out-a-measure-or-dimension"></a>メジャーまたはディメンションをスワップ アウトする
X 軸のメジャーまたはディメンションを置換するには、置換するフィールドを選択し、別のメジャーまたはディメンションを選択します。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="軸を変更する":::
 
### <a name="add-or-remove-a-legend"></a>凡例を追加または削除する
凡例を追加すると、カテゴリに基づいてビジュアルの色分けを設定できます。 **[個人用設定]** ペインの **[凡例]** ボックスをオフにすることで、カテゴリ別の色分けを除去できます。 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="凡例を追加または削除する":::

### <a name="compare-two-or-more-different-measures"></a>2 つ以上の異なるメジャーを比較する
[+] アイコンを使用してビジュアルの複数のメジャーを追加することにより、異なるメジャーの値を比較対照することができます。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="メジャーを比較する":::

### <a name="change-aggregations"></a>集計を変更する
**[個人用設定]** ペインで集計を変更することによって、メジャーの計算方法を変更できます。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="集計を変更する":::

### <a name="capture-changes"></a>変更をキャプチャする 
個人用ブックマークを使用して、カスタマイズされたビューに戻ることができるように変更をキャプチャします。 

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="ブックマークを作成する":::
 
また、ブックマークを既定のビューに設定することもできます。

### <a name="share-changes"></a>変更を共有する 
読み取りと再共有のアクセス許可を持っている場合は、レポートを共有するときに、自分の変更内容を含めることを選択できます。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="変更を共有する":::
 
### <a name="reset-all-your-changes-to-a-report"></a>レポートへのすべての変更をリセットする

**[既定値にリセット]** を選択すると、レポート内のすべての変更が削除され、作成者が最後に保存したレポートのビューに設定し直します。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="すべての変更をリセットする":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>ビジュアルへのすべての変更をリセットする

**[Reset this visual]\(このビジュアルをリセットする\)** を選択すると、特定のビジュアルへのすべての変更が削除され、作成者が最後に保存したそのビジュアルのビューに設定し直します。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="すべてのビジュアルの変更をリセットする":::
 
### <a name="clear-recent-changes"></a>最近の変更をクリアする

消しゴムアイコンを選択すると、 **[個人用設定]** ペインを開いた後に加えた最近の変更がすべてクリアされます。  

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="最近の変更を元に戻す":::

## <a name="limitations-and-known-issues"></a>制限事項と既知の問題

現在、この機能には注意すべきいくつかの制限事項があります。

- この機能は、Web に公開などの組み込みシナリオではサポートされていません。
- ユーザー探索は自動的に保持されません。 変更をキャプチャするには、個人用ブックマークとしてビューを保存する必要があります。
- Power BI モバイル アプリの使用中にビジュアルを変更することはできません。 ただし、Power BI サービスの使用中に個人用ブックマークに保存したビジュアルの変更は、モバイル アプリに適用されます。

また、現在対処中のいくつかの既知の問題もあります。

- 階層の追加はサポートされていません。個々の子項目を追加する必要があります。
- 日付の階層を日付に変更したり、その逆を行ったりすることはできません。 
- 個人用ブックマークを使用すると、選択した順序によって、得られる結果が多少異なる場合があります。 不一致が発生する場合があるのは、レポートの完全な状態をキャプチャするのではなく、加えた変更のみキャプチャするためです。 回避策として、 **[既定値にリセット]** を選択した後、表示するブックマークを選択します。 

## <a name="next-steps"></a>次の手順

新しいビジュアルの個人用設定のエクスペリエンスを試してみてください。 この機能のフィードバックや、機能改善を続けていくための方法に関するご意見については、[Power BI のアイデア サイト](https://ideas.powerbi.com/forums/265200-power-bi)からお寄せください。 

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。

