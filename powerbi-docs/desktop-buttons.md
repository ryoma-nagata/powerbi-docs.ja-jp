---
title: Power BI でボタンを使用する
description: Power BI レポートにボタンを追加すると、アプリのように動作するご自分のレポートを作成し、ユーザーとの連携を深めることができます。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/12/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: c703a4b67b642af5199413e80ff1e140905a2338
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "81439827"
---
# <a name="use-buttons-in-power-bi"></a>Power BI でボタンを使用する
Power BI で**ボタン**を使用したレポートを作成すると、ユーザーが Power BI コンテンツにマウス ポインターを重ねたり、クリックや対話操作を行うことができる、アプリのように動作する魅力的な環境を作成できます。 ボタンは、**Power BI Desktop** と **Power BI サービス**のレポートに追加できます。 ご自分のレポートを Power BI サービスで共有すると、それらはあなたのユーザーに対してアプリのように動作します。

![Power BI のボタン](media/desktop-buttons/power-bi-buttons.png)

## <a name="create-buttons-in-reports"></a>レポート内にボタンを作成する

### <a name="create-a-button-in-power-bi-desktop"></a>Power BI Desktop でボタンを設定する

**Power BI Desktop** でボタンを作成するには、 **[挿入]** リボンで **[ボタン]** を選択すると、ドロップダウン メニューが表示されます。ここでは、次の図のように、オプションのコレクションからボタンを選択できます。 

![Power BI Desktop でボタン コントロールを追加する](media/desktop-buttons/power-bi-button-dropdown.png)

### <a name="create-a-button-in-the-power-bi-service"></a>Power BI サービスでボタンを作成する

**Power BI サービス**でボタンを作成するには、レポートを編集ビューで開きます。 上部のメニュー バーで **[ボタン]** を選択すると、次の図のように、オプションの集合から希望するボタンを選択できるドロップダウン メニューが表示されます。 

![Power BI サービスにボタン コントロールを追加する](media/desktop-buttons/power-bi-button-service-dropdown.png)

## <a name="customize-a-button"></a>ボタンをカスタマイズする

ボタンは、Power BI Desktop で作成しても、Power BI サービスで作成しても、残りの手順は同じです。 そのボタンをレポート キャンバス上で選択すると、 **[視覚化]** ウィンドウに、あなたの要件に合わせてボタンをカスタマイズできる多くの方法が示されます。 たとえば、 **[視覚化]** ウィンドウのカードでスライダーを切り替えると、 **[ボタン テキスト]** をオンまたはオフにできます。 また、さまざまなプロパティのうち、ボタンのアイコン、ボタンの塗りつぶし、タイトル、およびユーザーがレポートまたはボタンを選択したときに行われるアクションを変更することができます。

![Power BI レポートのボタンを書式設定する](media/desktop-buttons/power-bi-button-properties.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>アイドル状態、マウスのポイント時、または選択時のボタンのプロパティを設定する

Power BI のボタンには 3 つの状態があります: 既定 (マウスでポイントされていないとき、または選択されていないときに表示されます)、マウスのポイント時、または選択時 (通常、*クリック*時として参照されます)。 **[視覚化]** ウィンドウのカードの多くは、ボタンをカスタマイズするために十分な柔軟性があり、3 つの状態を基に個別に変更できます。

**[視覚化]** ウィンドウの次のカードでは、3 つの状態に基づいてボタンの書式設定または動作を調整できます。

* ボタンのテキスト
* アイコン
* 枠線
* 塗りつぶし

各状態に表示されるボタンを選択するには、カードのいずれかを展開して、カードの上部に表示されるドロップダウンを選択します。 次の図では、 **[アイコン]** カードが展開され、ドロップダウンが選択され、3 つの状態が表示されています。

![Power BI レポートのボタンの 3 つの状態](media/desktop-buttons/power-bi-button-format.png)


## <a name="select-the-action-for-a-button"></a>ボタンにアクションを選択する

ユーザーが Power BI でボタンを選択されたときに実行されるアクションを選択できます。 **[視覚化]** ウィンドウの **[アクション]** カードからボタン アクションのオプションにアクセスできます。

![Power BI 内のボタンのアクション](media/desktop-buttons/power-bi-button-action.png)

ボタン アクションのオプションは次のとおりです。

- **[戻る]** では、ユーザーはレポートの前のページに戻ります。 これは、ドリルスルー ページで便利です。
- **[ブックマーク]** では、現在のレポートに定義されたブックマークに関連付けられたレポート ページを表示できます。 [Power BI のブックマークについて詳しくは、こちら](desktop-bookmarks.md)をご覧ください。 
- **[ドリルスルー (プレビュー)]** では、ユーザーの選択に基づいてフィルタリング処理されたドリルスルー ページに、ブックマークを使用せずに、ユーザーを移動できます。 [レポートのドリルスルー ボタンについて、詳しくはこちら](desktop-drill-through-buttons.md)をご覧ください。
- **[ページ ナビゲーション]** では、レポート内の別のページに、この場合もブックマークを使用せずに、ユーザーを移動できます。 詳細については、この記事の「[ページ ナビゲーションの作成](#create-page-navigation)」を参照してください。
- **[Q&A]** では、 **[Q&A Explorer]** \(Q&A エクスプローラー\) ウィンドウが開きます。 

特定のボタンには、既定のアクションが自動的に選択されます。 たとえば、 **[Q&A]** ボタンの種類では、既定のアクションとして **[Q&A]** を自動的に選択します。 **このブログの投稿**を確認すると、[Q&A Explorer](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer) の詳細を確認できます。

使用するボタン上で *Ctrl キーを押しながらクリック*して、レポートを作成するボタンを試したり、テストしたりすることができます。 

### <a name="create-page-navigation"></a>ページ ナビゲーションを作成する

**[アクション]** の種類の **[ページ ナビゲーション]** では、ブックマークをまったく保存または管理せずに、ナビゲーション エクスペリエンス全体をすばやく作成できます。

ページ ナビゲーション ボタンを設定するには、アクションの種類が **[ページ ナビゲーション]** のボタンを作成し、 **[宛先]** ページを選択します。

![ページ ナビゲーションのアクション](media/desktop-buttons/power-bi-page-navigation.png)

カスタム ナビゲーション ウィンドウをすばやく作成できます。 ご自分のナビゲーション ウィンドウに表示するページを変更するときに、ブックマークを編集して管理する必要はありません。

![ナビゲーション ページを作成する](media/desktop-buttons/power-bi-build-navigation-pane.png)

また、他の種類のボタンで行えるのと同様に、ヒントを条件付きで書式設定することもできます。

## <a name="next-steps"></a>次のステップ
ボタンと似た機能またはボタンと相互作用する機能の詳細については、次の記事をご覧ください。

* [Power BI レポートでドリルスルーを使用する](desktop-drillthrough.md)
* [Power BI でブックマークを使用して詳細情報を共有し、ストーリーを作成する](desktop-bookmarks.md)

