---
title: 認定済み Power BI ビジュアル
description: 認定を受けるためにカスタム ビジュアルを提出する場合の要件とプロセス、認定済み Power BI ビジュアルの一覧。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 03/01/2020
ms.openlocfilehash: 8aea9041665de69b2c5be954dc8f13a6402a06e0
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260763"
---
# <a name="get-a-power-bi-visual-certified"></a>認定済みの Power BI ビジュアルを取得する

認定済み Power BI ビジュアルとは、Microsoft Power BI チームの[コード要件](#certification-requirements)に適合している [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) の Power BI ビジュアルです。 これらのビジュアルは、外部のサービスやリソースにアクセスしないこと、およびセキュリティで保護されたコーディング パターンとガイドラインに従っていることを検証するテストを受けています。

Power BI ビジュアルが認定されると、提供される機能が増えます。 たとえば、[PowerPoint にエクスポート](../consumer/end-user-powerpoint.md)したり、ユーザーが[レポート ページをサブスクライブしている](../consumer/end-user-subscribe.md)ときに受信メールにビジュアルを表示したりできます。

認定プロセスは任意です。 認定されていない Power BI ビジュアルは、安全ではない Power BI ビジュアルとは限りません。 一部の Power BI ビジュアルは 1 つまたは複数の[認定要件](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)を満たしていないために認定されていません。 たとえば、外部サービスに接続するマップ Power BI ビジュアルや、商用ライブラリを使用する Power BI ビジュアルです。

> [!NOTE]
> Microsoft は、サードパーティの Power BI ビジュアルの作成者ではありません。 サードパーティのビジュアルの機能を確認するには、ビジュアルの作成者に直接問い合わせてください。

## <a name="certification-requirements"></a>認定要件

Power BI ビジュアルの[認定を受ける](#get-a-power-bi-visual-certified)には、Power BI ビジュアルがこのセクションに記載されている要件を満たしている必要があります。 

### <a name="general-requirements"></a>一般的な要件

Power BI ビジュアルは、販売者ダッシュボードまたはパートナー センターによって承認される必要があります。 Power BI ビジュアルはあらかじめ [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) に発行しておくことをお勧めします。 Power BI ビジュアルを AppSource に発行する方法については、「[Power BI ビジュアルをパートナー センターに発行する](office-store.md)」を参照してください。

認定対象の Power BI ビジュアルを提出する前に、「[Power BI ビジュアルの ガイドライン](./guidelines-powerbi-visuals.md)」に準拠していることを確認してください。

Power BI ビジュアルを提出する場合は、コンパイルされたパッケージが、提出されるパッケージと完全に一致していることを確認します。

### <a name="code-repository-requirements"></a>コード リポジトリの要件

GitHub でコードをパブリックに共有する必要はありませんが、コード リポジトリは Power BI チームがレビューのために使用できる必要があります。 これを行う最適な方法は、GitHub でソース コード (JavaScript または TypeScript) を提供することです。

リポジトリには、次のものが含まれている必要があります。
* 1 つだけの Power BI ビジュアルのコード。 複数の Power BI ビジュアルのコード、または関連のないコードを含めることはできません。
* **certification** (必ず小文字) という名前のブランチ。 このブランチのソース コードは、提出されたパッケージと一致している必要があります。 このコードは、次回の提出プロセス中に、Power BI ビジュアルを再提出する場合にのみ、更新できます。

Power BI ビジュアルにプライベート npm パッケージまたは git サブ モジュールを使用している場合は、そのコードを含む追加のリポジトリへのアクセスを提供する必要があります。

Power BI ビジュアルのリポジトリの外観を把握するには、GitHub リポジトリで[Power BI ビジュアルのサンプル横棒グラフ](https://github.com/microsoft/PowerBI-visuals-sampleBarChartgi)を確認してください。

### <a name="file-requirements"></a>ファイルの要件

Power BI ビジュアルを作成するには、最新バージョンの API を使用します。

リポジトリには、次のファイルを含める必要があります。
* **.gitignore** - `node_modules`、`.tmp`、`dist` をこのファイルに追加します。 コードに *node_modules*、 *.tmp*、または *dist* フォルダーを含めることはできません。
* **capabilities.json** - このファイルのプロパティに変更を加えた Power BI ビジュアルの新しいバージョンを提出する場合は、既存のユーザーのレポートを破損しないことを確認します。
* **pbiviz.json** 
* **package.json**。 ビジュアルには、次のパッケージがインストールされている必要があります。
   * ["tslint"](https://www.npmjs.com/package/tslint):"5.18.0" 以上
   * ["typescript"](https://www.npmjs.com/package/typescript):"3.0.0" 以上
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib):"6.2.0" 以上
   * ファイルには、linter を実行するためのコマンドが含まれている必要があります ("lint": "tslint -c tslint.json -p tsconfig.json")
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>コマンドの要件

次のコマンドでエラーが返されないことを確認します。

* `npm install`
* `pbiviz package`
* `npm audit` - 高レベルまたは中レベルの警告を返してはなりません。
* [必要な構成](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json)を備えた [Microsoft の TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib)。 このコマンドから lint エラーが返されてはなりません。

### <a name="compiling-requirements"></a>コンパイルの要件

Power BI ビジュアルを作成するには、最新バージョンの [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) を使用します。

`pbiviz package` を使用して Power BI ビジュアルをコンパイルする必要があります。 独自のビルド スクリプトを使用している場合は、`npm run package` カスタム ビルド コマンドを用意します。



### <a name="source-code-requirements"></a>ソース コードの要件

[Power BI ビジュアルの追加の認定](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification)ポリシー一覧に従っていることを確認します。 提出がこれらのガイドラインに従っていない場合、パートナー センターからの却下メールには、このリンクに記載されているポリシー番号が記載されます。

次に示すコードの要件に従って、コードが Power BI 認定ポリシーに準拠していることを確認します。  

**必須**
* 公開されている Javascript や TypeScript ライブラリなどの公開レビュー可能な OSS コンポーネントのみを使用します。
* このコードでは、[レンダリング イベント API](./visuals/event-service.md) をサポートする必要があります。
* DOM が安全に操作されていることを確認します。 ユーザー入力またはユーザー データにサニタイズを使用してから DOM に追加します。
* テスト データセットとして[サンプル レポート](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix)を使用します。

**禁止**
* 外部のサービスまたはリソースへのアクセス。 たとえば、Power BI から任意のサービスにアクセスできる HTTP/S または WebSocket 要求を含めることはできません。
* `innerHTML` または `D3.html(user data or user input)` の使用。
* すべて入力データに対するブラウザー コンソールの JavaScript エラーまたは例外。
* `eval()`、`settimeout()`、`requestAnimationFrame()`、`setinterval(user input function)` の安全ではない使用、ユーザー入力またはユーザー データなどの任意のコードまたは動的コード。
* 縮小された JavaScript ファイルまたはプロジェクト。

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

### <a name="private-repository-submission-process"></a>プライベート リポジトリの提出プロセス

GitHub などのプライベート リポジトリを使用して、認定を受けるために Power BI ビジュアルを送信する場合は、このセクションの手順に従ってください。
1. 検証チーム用の新しいアカウントを作成します。
2. アカウントに対して [2 要素認証](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa)を構成します。
3. [新しい回復用コードのセットを生成します](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes)。
4. Power BI ビジュアルを提出する際に、以下を指定します。
    * リポジトリへのリンク
    * ログイン資格情報 (パスワードを含む)
    * 回復用コード
    * アカウントに対する読み取り専用アクセス許可 ([pbicvsupport](https://github.com/pbicvsupport))

## <a name="certified-power-bi-visuals"></a>認定済み Power BI ビジュアル

下記に認定 Power BI ビジュアルのリストを示します。 リンクをクリックすると、AppSource で Power BI ビジュアルが開きます。 動画が利用可能な場合は、ビデオ リンクをクリックすると視聴できます。

* [3AG Systems - 絶対分散を含む横棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [3AG Systems - Bar Chart With Relative Variance (3AG Systems - 相対分散を含む横棒グラフ)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912)
*  [3AG Systems - 相対差異を含む縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803)
*  [3AG Systems - 差異を含む縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [高度なドーナツ ビジュアル (完全版)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [高度なドーナツ ビジュアル (軽量版)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [高度なグラフ ビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [高度なネットワークのビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [高度な時系列ビジュアル (完全版)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [アスター プロット](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Beyondsoft カレンダー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [MAQ Software による Bowtie Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [箱ひげ図](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [MAQ Software による箱ひげ図](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [MAQ Software によるブリック グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Akvelon によるバブル グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [箇条書きのグラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)、 **[ビデオ リンク](https://youtu.be/AOlsFYkfkcw)**
* [箇条書きのグラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [OKViz による箇条書きグラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953)、 **[ビデオ リンク](https://youtu.be/mtvUNl9bMjA)**
* [MAQ ソフトウェアによるカレンダー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Calendar by Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [OKViz によるローソク足](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952)、 **[ビデオ リンク](https://youtu.be/nT_18gyRxPo)**
*  [OKViz の Card with States](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Chiclet Slicer (Chiclet スライサー)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761)、 **[ビデオ リンク](https://youtu.be/AQvd2FhRyCI)**
*  [MAQ Software による円形ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [クラスター マップ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Akvelon によるカスタム カレンダー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [MAQ Software による円筒ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [ダイヤル ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[ドット プロット](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Dot Plot by OKViz (OKViz によるドット プロット)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949)、 **[ビデオ リンク](https://youtu.be/By16pX9KT40)**
*  [ドリルダウン カルトグラム](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [ドリルダウン コロプレス](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [ドリル ダウン縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857)、 **[ビデオ リンク](https://youtu.be/lBy2gQQ5YsQ)**
*  [時間基準データのドリルダウン縦棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881)、 **[ビデオ リンク](https://youtu.be/T_mRou18vx0)**
*  [ドリル ダウン ドーナツ グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)、 **[ビデオ リンク](https://youtu.be/AUVFrSHmPeo)**
*  [デュアル KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [MAQ ソフトウェアによる動的なツールヒント](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [強化された散布図](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762)、 **[ビデオ リンク](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten スタック シャッフル](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Enlighten ワッフル グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Devscope による一覧でのフィルター](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413)、 **[ビデオ リンク](https://youtu.be/RetEWGwBu0I)**
*  [力指向グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764)、 **[ビデオ リンク](https://youtu.be/YsTa7uyJ4sg)**
*  [MAQ Softwareによるソースでのじょうご](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765)、 **[ビデオ リンク](https://youtu.be/qJ7s_KrGiUU)**
* [MAQ Software による Gantt Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [地球データ バー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [MAQ ソフトウェアによるグリッド](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Akvelon による階層グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333)、 **[ビデオ リンク](https://youtu.be/0ZGzJaq_KT4)**
*  [ヒストグラム グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [MAQ Software によるポイント付きヒストグラム](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [横棒グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [MAQ Software による水平方向のじょうご](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [CloudScope によるイメージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [イメージ グリッド](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [インフォグラフィック デザイナー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [Akvelon による KPI グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [MAQ Software による KPI 列](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [MAQ Software による KPI グリッド](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [KPI インジケーター](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [MAQ Software による KPI ティッカー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [MAQ Software による線形ゲージ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [LineDot グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Mekko グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785)、 **[ビデオ リンク](https://youtu.be/90FLCKpgicA)**
*  [Multi KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [CloudScope による概要](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Play Axis (動的スライサー)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083)、[ビデオ リンク](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI マトリックス](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299)、 **[ビデオ リンク](https://youtu.be/1enze8pcGzY)**
*  [Pulse グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006)、 **[ビデオ リンク](https://youtu.be/DQWdcQtjDVw)**
*  [MAQ Software による四分割グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Radar chart (レーダー チャート)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [MAQ Software によるリング グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [MAQ Software による回転グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankey グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777)、 **[ビデオ リンク](https://youtu.be/WWP9wVUHGaA)**
*  [Akvelon による散布図](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [スクローラー](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [OKViz でのスマート フィルター](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859)、 **[ビデオ リンク](https://youtu.be/gcJsDDRQq28)**
*  [OKViz でのスパークライン](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910)、 **[ビデオ リンク](https://youtu.be/0m3Vnvso9tY)**
*  [ストリーム グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Sunburst](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [OKViz によるシノプティック パネル](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [テーブル ヒートマップ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [回転速度計](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937)、 **[ビデオ リンク](https://youtu.be/C3OXdETbS9o)**
*  [テキスト フィルター](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [MAQ ソフトウェアによるテキスト ラッパー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [MAQ Software による温度計](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Time Brush Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [タイムライン スライサー](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786)、 **[ビデオ リンク](https://youtu.be/ozMtZ4_NZ10)**
*  [CloudScope によるタイムライン](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427)、[ビデオ リンク](https://youtu.be/szNi9YgXFJc)
*  [Tornado グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768)、 **[ビデオ リンク](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [MAQ Software による取引グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Ultimate KPI カード](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Ultimate の差異](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140)、 **[ビデオ リンク](https://youtu.be/pDYF8iZxERs)**
*  [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956)、 **[ビデオ リンク](https://youtu.be/0BZsVCQdEkc)**
*  [CloudScope によるユーザー一覧](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [MAQ Software による Venn ダイアグラム](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [バイオリン プロット](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visio ビジュアル](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [ワッフル グラフ](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049)、 **[ビデオ リンク](https://youtu.be/1vRqYUsm3Vk)**
*  [ワード クラウド](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752)、 **[ビデオ リンク](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>FAQ

ビジュアルについて詳しくは、[認定済みのビジュアルに関してよく寄せられる質問](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)に関する記事をご覧ください。

## <a name="next-steps"></a>次の手順

* [Power BI カスタム ビジュアルの開発](../developer/custom-visual-develop-tutorial.md)
* [YouTube の Microsoft カスタム ビジュアル プレイリスト](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Power BI での視覚化](../visuals/power-bi-report-visualizations.md)  
* [Power BI でのカスタム ビジュアル](power-bi-custom-visuals.md)  
* [Microsoft AppSource に Power BI ビジュアルを発行する](../developer/office-store.md) 
* 独自の Power BI ビジュアルを作成し、それらを  [Microsoft AppSource](https://appsource.microsoft.com) に追加することに関心がある Web 開発者は、 [Power BI のビジュアルを開発する](visuals/custom-visual-develop-tutorial.md)ためのチュートリアルから始めてください。 

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
