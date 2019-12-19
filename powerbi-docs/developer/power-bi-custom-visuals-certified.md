---
title: 認定済み Power BI ビジュアル
description: 認定のためにカスタム ビジュアルを送信する場合の要件とプロセス。 および、既に認定されている Power BI ビジュアルの一覧。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: 0a39496ade27cd45fae116eea92ef4b472e04582
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999746"
---
# <a name="get-a-power-bi-visual-certified"></a>認定済みの Power BI ビジュアルを取得する

認定済み Power BI ビジュアルとは*マーケットプレース*内のビジュアルであり、*特定のコード*要件を満たしていることを *Microsoft Power BI チーム*がテストし、承認したものです。 テストは、ビジュアルで外部のサービスやリソースへのアクセスが行われないことを確認するように設計されています。

認定済み Power BI ビジュアルと[標準の Power BI ビジュアル](power-bi-custom-visuals.md)は、同じ方法で使用されます。 それらを [Power BI Desktop](../desktop-what-is-desktop.md) と [Power BI サービス](../power-bi-service-overview.md)に追加し、[Power BI Mobile](../consumer/mobile/mobile-apps-for-mobile-devices.md) と [Power BI Embedded](embedding.md) で表示できます。

認定プロセスは、オプションのプロセスです。 開発者が自分の Power BI ビジュアルを Marketplace で認定されるようにするかどうかの決定は、開発者に任されています。 Power BI ビジュアルが認定されると、提供される機能が増えます。 たとえば、[PowerPoint にエクスポート](../consumer/end-user-powerpoint.md)したり、ユーザーが[レポート ページをサブスクライブしている](../consumer/end-user-subscribe.md)ときに受信メールにビジュアルを表示したりできます。

未認定 Power BI ビジュアルは、安全ではないビジュアルを意味するわけではありません。 一部のビジュアルは 1 つまたは複数の[認定要件](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)を満たしていないために認定されていません。 たとえば、地図ビジュアルのような外部サービスや商用ライブラリを利用するビジュアルに接続する場合です。

独自の Power BI ビジュアルを作成し、それらを  [Microsoft AppSource](https://appsource.microsoft.com) に追加することに関心がある Web 開発者は、 [Power BI のビジュアルを開発する](visuals/custom-visual-develop-tutorial.md)ためのチュートリアルから始めてください。

> [!NOTE]
> **Microsoft** は、サードパーティの Power BI ビジュアルの作成者では "*ありません*"。 Microsoft では、サードパーティ製のビジュアルの機能については、ビジュアルの作成者に直接お問い合わせいただくことをユーザーにお勧めしています。

> [!IMPORTANT]
> Microsoft は、独自の裁量で[認定リスト](#list-of-power-bi-visuals-that-have-been-certified)から Power BI ビジュアルを削除できます。

## <a name="certification-requirements"></a>認定要件

自分の Power BI ビジュアルに対する[認定](#get-a-power-bi-visual-certified)を取得するには、その Power BI ビジュアルがこのセクションに記載されている要件に準拠していることを確認してください。 

> [!TIP]
> 送信する前に、EsLint と既定のセキュリティ ルール セットを使用して、コードを事前検証することをお勧めします。

* Microsoft 販売者ダッシュボードまたはパートナー センターで承認されている。 自分の Power BI ビジュアルが、Microsoft [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) に表示されている必要があります。
* Power BI ビジュアルが *API v2.5* 以降で記述されている。
* Power BI チームによるレビューでコード リポジトリを使用できる。 たとえば、読み取り可能な形式のソース コード (JavaScript または TypeScript) を GitHub から入手できます。

    >[!NOTE]
    > Github でコードを一般公開する必要はありません。

* コード リポジトリの要件:
  * 次のファイルが含まれている必要があります。
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * *node_modules* フォルダーを含めてはなりません (*node_modules* は .gitingore* ファイルに追加してください)。
  * *npm install* コマンドからエラーが返されてはなりません。
  * *npm audit* コマンドから高レベルまたは中レベルの警告が返されてはなりません。
  * *pbiviz package* コマンドからエラーが返されてはなりません。
  * オーバーライドされた構成を使用せずに [Microsoft からの TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib) を含める必要があります。 このコマンドから lint エラーが返されてはなりません。
   * Power BI ビジュアルのコンパイル済みパッケージが、提出されたパッケージと一致する必要があります (両方のファイルの md5 ハッシュが同じである必要があります)。
* ソース コードの要件:
   * Power BI ビジュアルで、[Rendering Events API](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/) がサポートされている必要があります。
   * 任意/動的コードが実行されていないことを確認します (不適切: eval()、確実に使用できない可能性のある settimeout()、requestAnimationFrame()、setinterval (ユーザー入力のある関数)、ユーザー入力/データの実行)。
   * DOM が問題なく操作されていることを確認します (不適切: innerHTML、D3.html(<一部のユーザー/データ入力>)、DOM に追加する前にユーザー入力/データにサニタイズを使用する)。
   * ブラウザー コンソールで、すべての入力データに対して javascript エラーまたは例外が発生しないことを確認します。 ユーザーは、異なる範囲の予期しないデータで Power BI ビジュアルを使用する可能性があるため、ビジュアルでエラーが発生しないようにする必要があります。 この[サンプル レポート](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix)をテスト データセットとして使用できます。

* *capabilities.json* ファイルのプロパティが変更された場合でも、既存のユーザーのレポートが破損しないことを確認します。

* Power BI ビジュアルが [Power BI ビジュアルのガイドライン](./guidelines-powerbi-visuals.md)に準拠していることを確認します。
    
* コードでは、公開されている Javascript や TypeScript ライブラリなどの公開レビュー可能な OSS コンポーネントのみを使用できます。 レビューするためにソース コードを入手可能であり、既知の脆弱性が含まれていてはなりません。 Microsoft は商用コンポーネントを利用してカスタム ビジュアルを検証することかできません。

* Power BI ビジュアルでは、外部のサービスまたはリソースにアクセスしてはなりません。 たとえば、Power BI から任意のサービスにアクセスできる HTTP/S または WebSocket 要求を含めることはできません。 

## <a name="submitting-a-power-bi-visual-for-certification"></a>認定されるための Power BI ビジュアルの提出

自分の Power BI ビジュアルに対する Power BI チームによる認定をパートナー センターを通して要求できます。

>[!TIP]
>Power BI 認定プロセスには時間がかかることがあります。 新しい Power BI ビジュアルを作成している場合は、Power BI 認定を要求する前に、パートナー センターを通して Power BI ビジュアルを発行しておくことをお勧めします。 これにより、自分のビジュアルの発行が遅れないようにすることができます。

Power BI 認定を要求するには:

1. パートナー センターにサインインします。
2. **[概要]** ページで、自分の Power BI ビジュアルを選択し、 **[製品]** 設定ページに移動します。
3. **[Power BI 認定を要求します]** チェック ボックスをオンにします。
4. **[確認と発行]** ページで、 **[認定の注意書き]** テキスト ボックスに、ソース コードへのリンクと、それにアクセスするために必要な資格情報を入力します。

>[!NOTE]
> Power BI ビジュアル提出プロセスの途中であり、[販売者ダッシュボード](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (旧管理ツール) を使用する必要がある場合は、「[販売者ダッシュボードでの提出プロセス](seller-dashboard.md#seller-dashboard-certification-submission-process)」の手順を確認してください。

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>認定された Power BI ビジュアルの一覧

| リンク | ビデオ |
| --- | --- |
| [3AG Systems - Bar Chart With Relative Variance (3AG Systems - 相対分散を含む横棒グラフ)](https://appsource.microsoft.com/en/product/power-bi-visuals/WA104381912) | |
| [3AG Systems - 相対差異を含む縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) | |
| [高度なドーナツ ビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) | |
| [高度なネットワークのビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) | |
| [高度な時系列ビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) | |
| [高度なコンボ ビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) | |
| [アスター プロット](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft カレンダー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) | |
| [MAQ Software による Bowtie Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) | [ビデオ](https://youtu.be/So5xKMSpVJI) |
| [箱ひげ図](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) | |
| [MAQ Software による箱ひげ図](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) | [ビデオ](https://youtu.be/JoHaFLfhXdo) |
| [MAQ Software によるブリック グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) | [ビデオ](https://youtu.be/hA3DOsvn2xY) |
| [Akvelon によるバブル グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) | |
| [箇条書きのグラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [ビデオ](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart by OKViz (OKViz による箇条書きグラフ)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) | [ビデオ](https://youtu.be/mtvUNl9bMjA) |
| [Calendar by Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) | |
| [OKViz によるローソク足](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) | [ビデオ](https://youtu.be/nT_18gyRxPo) |
| [OKViz の Card with States](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Chiclet Slicer (Chiclet スライサー)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) | |
| [弦](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) | [ビデオ](https://youtu.be/AQvd2FhRyCI) |
| [MAQ Software による円形ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) | [ビデオ](https://youtu.be/9NHXALkBXuY) |
| [クラスター マップ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) | |
| [MAQ Software による円筒ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | [ビデオ](https://youtu.be/DgdoWi7Gcxo) |
| [ダイヤル ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) | |
| [ドット プロット](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) | |
| [Dot Plot by MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) | [ビデオ](https://youtu.be/By16pX9KT40) |
| [ドリルダウン カルトグラム](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) | |
| [ドリルダウン コロプレス](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) | |
| [ドリル ダウン縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) | [ビデオ](https://youtu.be/lBy2gQQ5YsQ) |
| [時間基準データのドリルダウン縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [ビデオ](https://youtu.be/T_mRou18vx0) |
| [ドリルダウン ドーナツ グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | [ビデオ](https://youtu.be/AUVFrSHmPeo) |
| [デュアル KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [MAQ ソフトウェアによる動的なツールヒント](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) | [ビデオ](https://youtu.be/Z-tl97BpEr0) |
| [強化された散布図](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) | [ビデオ](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) | |
| [Enlighten スタック シャッフル](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) | |
| [Enlighten ワッフル グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) | |
| [Devscope による一覧でのフィルター](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [ビデオ](https://youtu.be/RetEWGwBu0I) |
| [力指向グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) | [ビデオ](https://youtu.be/YsTa7uyJ4sg) |
| [MAQ Softwareによるソースでのじょうご](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) | [ビデオ](https://youtu.be/R_EcimsLI8U) |
| [ガント](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [ビデオ](https://youtu.be/qJ7s_KrGiUU) |
| [MAQ Software による Gantt Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) | [ビデオ](https://youtu.be/vJLV9JRCpI8) |
| [地球データ バー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) | |
| [MAQ ソフトウェアによるグリッド](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) | [ビデオ](https://youtu.be/VOPoDJgZfOY) |
| [Akvelon による階層グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) | [ビデオ](https://youtu.be/0ZGzJaq_KT4) |
| [ヒストグラム グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) | |
| [MAQ Software によるポイント付きヒストグラム](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) | [ビデオ](https://youtu.be/-ILF--wExrw) |
| [MAQ Software による水平方向のじょうご](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) | [ビデオ](https://youtu.be/SudZei68PPo) |
| [CloudScope によるイメージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) | |
| [イメージ グリッド](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) | |
| [インフォグラフィック デザイナー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) | |
| [Akvelon による KPI グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) | |
| [MAQ Software による KPI 列](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) | [ビデオ](https://youtu.be/rU0xoOlIq1U) |
| [MAQ Software による KPI グリッド](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) | [ビデオ](https://youtu.be/dM4PvZh71V0) |
| [KPI インジケーター](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [MAQ Software による KPI ティッカー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) | [ビデオ](https://youtu.be/cudG4gsZ2V8) |
| [MAQ Software による線形ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) | [ビデオ](https://youtu.be/7_jFaM30dkc) |
| [LineDot グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) | |
| [Mekko グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) | [ビデオ](https://youtu.be/90FLCKpgicA) |
| [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) | |
| [CloudScope による概要](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) | |
| [Play Axis (動的スライサー)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [ビデオ](https://youtu.be/IvfIP3E6-1Q) |
| [累乗 KPI マトリックス](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) | [ビデオ](https://youtu.be/1enze8pcGzY) |
| [パルス グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) | [ビデオ](https://youtu.be/DQWdcQtjDVw) |
| [MAQ Software による四分割グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) | [ビデオ](https://youtu.be/ppBnyhqWNC0) |
| [Radar chart (レーダー チャート)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) | |
| [MAQ Software によるリング グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) | [ビデオ](https://youtu.be/pDToHDFHnq8) |
| [MAQ Software による回転グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) | [ビデオ](https://youtu.be/d5xBCMmb3hU) |
| [Sankey グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) | [ビデオ](https://youtu.be/WWP9wVUHGaA) |
| [Akvelon による散布図](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [スクローラー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Smart Filter by OKViz (OKViz でのスマート フィルター)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) | [ビデオ](https://youtu.be/gcJsDDRQq28) |
| [OKViz によるスパークライン](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) | [ビデオ](https://youtu.be/0m3Vnvso9tY) |
| [ストリーム グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) | |
| [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) | |
| [OKViz によるシノプティック パネル](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) | |
| [テーブル ヒートマップ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) | |
| [回転速度計](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [ビデオ](https://youtu.be/C3OXdETbS9o) |
| [テキスト フィルター](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) | |
| [MAQ ソフトウェアによるテキスト ラッパー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [MAQ Software による温度計](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) | [ビデオ](https://youtu.be/SPX9mgrAdBc) |
| [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) | |
| [タイムライン スライサー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) | [ビデオ](https://youtu.be/ozMtZ4_NZ10) |
| [CloudScope によるタイムライン](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) | [ビデオ](https://youtu.be/szNi9YgXFJc) |
| [トルネード チャート](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [ビデオ](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [MAQ Software による取引グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) | [ビデオ](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate の差異](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) | [ビデオ](https://youtu.be/pDYF8iZxERs) |
| [Ultimate のウォーターフォール](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) | [ビデオ](https://youtu.be/0BZsVCQdEkc) |
| [CloudScope によるユーザー一覧](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) | |
| [ワッフル グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) | [ビデオ](https://youtu.be/1vRqYUsm3Vk) |
| [ワード クラウド](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [ビデオ](https://youtu.be/AblTenl9fqo) |

## <a name="faq"></a>よく寄せられる質問

ビジュアルについて詳しくは、[認定済みのビジュアルに関してよく寄せられる質問](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)に関する記事をご覧ください。

## <a name="next-steps"></a>次の手順

* [Power BI カスタム ビジュアルの開発](../developer/custom-visual-develop-tutorial.md)
* [YouTube の Microsoft カスタム ビジュアル プレイリスト](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Power BI での視覚化](../visuals/power-bi-report-visualizations.md)  
* [Power BI でのカスタム ビジュアル](power-bi-custom-visuals.md)  
* [Microsoft AppSource に Power BI ビジュアルを発行する](../developer/office-store.md)  

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
