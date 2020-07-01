---
title: ユーザーがレポート内のビジュアルをカスタマイズできるようにする
description: レポートの閲覧者は、レポートを編集することなく、独自のビューを作成できます。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 05/21/2020
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 0fdee37f682774e1dac2b1ac6a4fc7a6e8dabe91
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238086"
---
# <a name="let-users-personalize-visuals-in-a-report"></a>ユーザーがレポート内のビジュアルをカスタマイズできるようにする

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

多くの対象ユーザーとレポートを共有するとき、一部のユーザーが、特定のビジュアルの少し異なるビューを表示することが必要な場合もあります。 場合によっては、軸の内容を入れ替えたり、ビジュアルの種類を変更したり、ツールヒントに何かを追加したりする必要があります。 すべてのユーザーの要件を満たす 1 つのビジュアルを作成するのは困難です。 この新しい機能により、コンシューマーがレポートの読み取りビューで、ビジュアルを探索およびカスタマイズするための権限を与えることができます。 ビジュアルを必要に応じて調整し、戻るためのブックマークとして保存することができます。 レポートの編集アクセス許可を持っている必要はなく、変更のためにレポートの作成者に戻る必要もありません。

:::image type="content" source="media/power-bi-personalize-visuals/power-bi-personalize-visual.png" alt-text="ビジュアルをカスタマイズする":::
 
## <a name="what-report-consumers-can-change"></a>コンシューマーが変更できるレポート

この機能により、コンシューマーは Power BI レポートのビジュアルをアドホック探索することで、さらに洞察を得ることができます。 この機能をコンシューマーとして使用する方法については、[レポート内のビジュアルのカスタマイズ](../consumer/end-user-personalize-visuals.md)に関する記事をご覧ください。 この機能は、レポート閲覧者の基本的な調査シナリオを有効にする必要があるレポートの作成者にとって理想的です。 レポートの閲覧者が行うことができる変更を次に示します。

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


## <a name="limitations-and-known-issues"></a>制限事項と既知の問題

現在、この機能には注意すべきいくつかの制限事項があります。

- この機能は、Web に公開などの組み込みシナリオではサポートされていません。
- ユーザー探索は自動的に保持されません。 変更をキャプチャするには、個人用ブックマークとしてビューを保存する必要があります。
- この機能は、iOS と Android タブレット用の Power BI モバイルアプリ、および Power BI Windows アプリでサポートされています。スマートフォン用の Power BI モバイル アプリではサポートされていません。 ただし、Power BI サービスの使用中に個人用ブックマークに保存したビジュアルの変更は、すべての Power BI モバイル アプリに適用されます。

また、現在対処中のいくつかの既知の問題もあります。

- 階層の追加はサポートされていません。個々の子項目を追加する必要があります。
- 日付の階層を日付に変更したり、その逆を行ったりすることはできません。 
- 個人用ブックマークを使用すると、選択した順序によって、得られる結果が多少異なる場合があります。 不一致が発生する場合があるのは、レポートの完全な状態をキャプチャするのではなく、加えた変更のみキャプチャするためです。 回避策として、 **[既定値にリセット]** を選択した後、表示するブックマークを選択します。 

## <a name="next-steps"></a>次の手順

[レポート内のビジュアルをカスタマイズする](../consumer/end-user-personalize-visuals.md)。     

新しいビジュアルの個人用設定のエクスペリエンスを試してみてください。 この機能のフィードバックや、機能改善を続けていくための方法に関するご意見については、[Power BI のアイデア サイト](https://ideas.powerbi.com/forums/265200-power-bi)からお寄せください。 

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
