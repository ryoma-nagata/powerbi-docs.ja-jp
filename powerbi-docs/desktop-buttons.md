---
title: Power BI でボタンの使用
description: Power BI Desktop でボタンを使用すると、アプリのように動作するレポートとダッシュボードを作成し、ユーザーとの連携を深めることができます。
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 9d884df7fdfa6d0f16e7963c00a1100186d70546
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "65239498"
---
# <a name="using-buttons-in-power-bi"></a>Power BI でボタンの使用
Power BI で**ボタン**を使用すると、アプリと同様に動作するレポートとダッシュボードを作成できるため、興味をそそる環境を作成できます。これにより、ユーザーは Power BI コンテンツに対するマウスのポイント、クリック、および対話操作を行うことができます。 **Power BI Desktop** のレポートにボタンを追加して、Power BI サービスにレポートを共有および発行し、ユーザーのためにアプリのように動作するダッシュボードを作成できます。

![Power BI のボタン](media/desktop-buttons/desktop-buttons_01.png)

**Power BI Desktop** で作成するボタンは、**Power BI サービス**に発行されるレポートまたはダッシュボードで利用できます。

## <a name="creating-buttons-in-reports"></a>レポート内にボタンを作成する
**Power BI Desktop** レポートでボタンを作成するには、 **[ホーム]** リボンで **[ボタン]** リボンを選択すると、ドロップダウン メニューが表示されます。ここでは、次の図のように、オプションのコレクションからボタンを選択できます。 

![Power BI Desktop でボタン コントロールを追加する](media/desktop-buttons/desktop-buttons_02.png)

ボタンを作成してレポート キャンバス上で選択すると、 **[視覚化]** ウィンドウには、要件に合わせてボタンをカスタマイズできる多くの方法が示されます。 たとえば、 **[視覚化]** ウィンドウのカードでスライダーを切り替えて、 **[ボタン テキスト]** をオンまたはオフにできます。 また、ボタンのアイコン、ボタンの塗りつぶし、タイトル、およびその他のプロパティの間でユーザーがレポートまたはダッシュボードのボタンをクリックしたときに行われるアクションを変更することもできます。

![Power BI Desktop でボタンを書式設定する](media/desktop-buttons/desktop-buttons_03.png)

## <a name="set-button-properties-when-idle-hovered-over-or-selected"></a>アイドル状態、マウスのポイント時、または選択時のボタンのプロパティを設定する

Power BI のボタンには 3 つの状態があります: 既定 (マウスでポイントされていないとき、または選択されていないときに表示されます)、マウスのポイント時、または選択時 (通常、*クリック*時として参照されます)。 **[視覚化]** ウィンドウのカードの多くは、ボタンをカスタマイズするために十分な柔軟性があり、3 つの状態を基に個別に変更できます。

**[視覚化]** ウィンドウの次のカードでは、3 つの状態に基づいてボタンの書式設定または動作を調整できます。

* ボタンのテキスト
* アイコン
* アウトライン
* 塗りつぶし

各状態に表示されるボタンを選択するには、カードのいずれかを展開して、カードの上部に表示されるドロップダウンを選択します。 次の図では、 **[アウトライン]** カードが展開され、ドロップダウンが選択され、3 つの状態が表示されています。

![Power BI Desktop のボタンの 3 つの状態](media/desktop-buttons/desktop-buttons_04.png)


## <a name="select-the-action-for-a-button"></a>ボタンにアクションを選択する

ユーザーが Power BI でボタンを選択されたときに実行されるアクションを選択できます。 **[視覚化]** ウィンドウの **[アクション]** カードからボタン アクションのオプションにアクセスできます。

![Power BI 内のボタンのアクション](media/desktop-buttons/desktop-buttons_05.png)

ボタン アクションのオプションは次のとおりです。

* 戻る
* ブックマーク
* Q&A

**[戻る]** を選択すると、ユーザーはレポートの前のページに戻ります。 これは特に、ドリルダウン ページに便利です。

**[ブックマーク]** を選択すると、現在のレポートに定義されているブックマークに関連付けられたレポート ページが表示されます。 Power BI のブックマークについて詳しくは、[こちら](desktop-bookmarks.md)をご覧ください。 

ドロップダウンから **[Q&A]** を選択すると、 **[Q&A Explorer]** ウィンドウが表示されます。 

特定のボタンには、既定のアクションが自動的に選択されます。 たとえば、 **[Q&A]** ボタンの種類では、既定のアクションとして **[Q&A]** を自動的に選択します。 [このブログの投稿](https://powerbi.microsoft.com/blog/power-bi-desktop-april-2018-feature-summary/#Q&AExplorer)を確認すると、**Q&A Explorer** の詳細を確認できます。

使用するボタン上で *Ctrl キーを押しながらクリック*して、レポートを作成するボタンを試したり、テストしたりすることができます。 

## <a name="next-steps"></a>次の手順
ボタンと似た機能またはボタンと相互作用する機能の詳細については、次の記事をご覧ください。

* [Power BI Desktop でドリルスルーを使用する](desktop-drillthrough.md)
* [フォーカス モードでダッシュボード タイルまたはレポート ビジュアルを表示する](consumer/end-user-focus.md)
* [Power BI でブックマークを使用して詳細情報を共有し、ストーリーを作成する](desktop-bookmarks.md)

