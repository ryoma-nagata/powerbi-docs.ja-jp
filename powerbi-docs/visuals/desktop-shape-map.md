---
title: Power BI Desktop で図形マップを使用する (プレビュー)
description: Power BI Desktop で図形マップを使用して領域間の相対比較を作成する
author: mihart
ms.reviewer: justyna, sujata
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/18/2020
ms.author: mihart
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 67c2acad74827c515c92ed0d16dd642170b8dc61
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "79525662"
---
# <a name="create-shape-map-visualizations-in-power-bi-desktop-preview"></a>Power BI Desktop で図形マップのビジュアルを作成する (プレビュー)

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

色を使用して、マップで領域を比較するために **[図形マップ]** ビジュアルを作成します。 **[マップ]** ビジュアルとは異なり、 **[図形マップ]** ではマップ上の地理的な場所を正確には表示できません。 代わりに、これの主な用途は、違う色を適用することにより、マップ上の領域を相対的に比較できます。

**[図形マップ]** のビジュアルは TopoJSON マップをベースにしています。このマップの強みは、ユーザー作成のカスタム マップを使用できることです。 地理、座席配置、フロア プランなどがカスタム マップの例です。 カスタム マップを利用する機能は、このプレビュー リリースの**マップのシェイプ**では使用できません。

## <a name="creating-shape-maps"></a>図形マップを作成する
このプレビュー リリースに付属するマップで**マップのシェイプ** コントロールをテストできます。あるいは、次のセクション (**カスタム マップの使用**) にある要件を満たす限り、独自のカスタム マップを使用できます。

**[マップのシェイプ]** のビジュアルは、プレビュー段階にあるため、Power BI Desktop でこれを有効にする作業が必要です。 **[マップのシェイプ]** を有効にするには、 **[ファイル] > [オプションと設定] > [オプション] > [プレビュー機能]** の順に選択し、 **[図形マップのビジュアル]** チェック ボックスをオンにします。 選択を行った後、Power BI Desktop を再起動する必要があります。

![[マップのシェイプ] プレビュー機能の有効化](media/desktop-shape-map/power-bi-preview-features.png)

**[マップのシェイプ]** が有効になったら、 **[視覚化]** ウィンドウで **[マップのシェイプ]** アイコンを選択します。

![図形マップ用のテンプレートを選択する](media/desktop-shape-map/power-bi-shape-map-template2.png)

Power BI Desktop は、 **[マップのシェイプ]** のビジュアルのデザイン キャンバスを作成します。

![自分のキャンバス上に空の図形マップが表示される](media/desktop-shape-map/shape-map-3.png)

次の手順に従って、 **[マップのシェイプ]** を作成します。

1. **[フィールド]** ウィンドウで、地域名 (または省略形) が含まれているデータ フィールドを **[地域]** バケットにドラッグし、データ メジャー フィールドを **[色の彩度]** バケットにドラッグします (地図はまだ表示されません)。

   > [!NOTE]
   > **[マップのシェイプ]** をテストするためのマップ データを迅速に取得する方法については、後述する「**マップ データの取得**」セクションを参照してください。
   > 
   > 

   ![自分の図形マップを作成する](media/desktop-shape-map/shape-map-3a.png)
2. **[形式]** 設定ウィンドウで、 **[図形]** を展開し、 **[標準マップ]** ドロップダウンから選択して、目的のデータを表示します。 この時点で、次の図に示すようにレンダリングが行われます。

   ![[書式設定] ウィンドウを開き、[図形] を選択する](media/desktop-shape-map/shape-map-3b-new.png)

   > [!NOTE]
   > この記事の最後に記載した「**地域キー**」セクションは、 **[マップのシェイプ]** のビジュアルをテストするのに使用できる地図の地域キーが含まれる表のコレクションです。
   > 
   > 
3. **[既定の色]** や **[ズーム]** などの [書式設定] オプションを使用してマップを変更することができます。 また、カテゴリ データ列を **[凡例]** バケットに追加し、カテゴリに基づいて地図の地域を分類することもできます。

## <a name="use-custom-maps"></a>カスタム マップの使用
それが **TopoJSON** 形式であれば、**マップのシェイプ**でカスタム マップを使用できます。 マップが別の形式の場合、[**Map Shaper**](https://mapshaper.org/) などのオンライン ツールを使用し、*シェイプ ファイル*や *GeoJSON* マップを **TopoJSON** 形式に変換できます。

**TopoJSON** マップ ファイルを使用するには、ShapeMap ビジュアルをレポートに追加し、データを *[場所]* バケットと *[色の彩度]* バケットに追加します。 その後、 **[視覚化]** ウィンドウで **[形式]** セクションを選択し (次の画像の (1))、 **[図形]** セクションを展開し、 **[+ マップの追加]** を選択します。

![[書式設定] ウィンドウを開き、[マップの追加] を選択する](media/desktop-shape-map/shape-map-6-new.png)

## <a name="sample-custom-map"></a>サンプル カスタム マップ
*米国連邦地検* は、訴訟および取扱件数データに関する年次会計報告を公表しました。  これらすべてのレポートは以下のリンクで確認できます。

https://www.justice.gov/usao/resources/annual-statistical-reports

州は複数の区に分けられるため、カスタム シェイプ マップを使用する必要があります。  米国司法管轄区の **TopoJSON** マップを **Power BI Desktop** にインポートすることで、地区検事長の年次会計報告データを視覚化できます。  次の画像はこのマップの例を示しています。

![ユーザー設定の図形マップ](media/desktop-shape-map/shape-map-7a.png)

個々の州マップについても、含まれる区に基づいて詳細を表示することができます。 

![テキサスの図形マップ](media/desktop-shape-map/shape-map-7b.png)

このデータセットと視覚エフェクトを試したい場合は、以下のリンクを使用して、このレポートの生成に使用された元の PBIX ファイルをダウンロードできます。

* [カスタム シェイプ マップのデモ .PBIX ファイル](https://download.microsoft.com/download/1/2/8/128943FB-9231-42BD-8A5D-5E2362C9D589/DistrictAttorneyFiscalReport.pbix)

## <a name="getting-map-data"></a>マップ データの取得
**[マップのシェイプ]** をテストできるようにモデルに迅速にデータを入力するには、 **[ホーム]** リボンから **[データの入力]** を選択します。

![Desktop で、[データの入力] を選択する](media/desktop-shape-map/shape-map-4-new.png)

データに複数の列がある場合は、Excel などのエディターを使用してデータを貼り付け、各データ列を個別にコピーする必要があります。 このデータは Power BI Desktop に貼り付けることができます。 一番上の行は、自動的に見出しとして識別されます。

![[テーブルの作成] ウィンドウ](media/desktop-shape-map/shape-map-5.png)

新しい列は簡単に入力できます。新しい列名を入力し (右側の空の列に)、各セルに値を追加します。この方法は Excel で行う操作と同じです。 列の作成が完了したら、 **[読み込み]** を選択します。表が Power BI Desktop のデータ モデルに追加されます。

> [!NOTE]
> 国または地域を扱うとき、3 文字の省略形を使用し、マップ視覚エフェクトでジオコーディングが正しく機能するようにします。 2 文字の省略形は *使用しない* でください。正しく認識されない国や地域があります。
> 
> 省略形が 2 文字しかない場合、[この外部ブログ投稿](https://blog.ailon.org/how-to-display-2-letter-country-data-on-a-power-bi-map-85fc738497d6#.yudauacxp)を参照してください。2 文字の国/地域コードを 3 文字の国/地域コードに関連付ける方法が紹介されています。
> 
> 

## <a name="preview-behavior-and-requirements"></a>プレビューの動作と要件
**[マップのシェイプ]** 機能を提供するこのプレビュー リリースには、いくつかの考慮事項と要件があります。

* **[マップのシェイプ]** のビジュアルは、プレビュー段階にあるため、Power BI Desktop でこれを有効にする作業が必要です。 **[マップのシェイプ]** を有効にするには、 **[ファイル] > [オプションと設定] > [オプション] > [プレビュー機能]** の順に選択し、 **[図形マップのビジュアル]** チェック ボックスをオンにします。
* 現時点で、 **[凡例]** の分類が適切に機能するには、 **[色の彩度]** バケットも設定されている必要があります。
* **マップのシェイプ**の最終リリース版には、現在選択されているマップのマップ キーが表示されるユーザー インターフェイスが搭載される予定です (最終リリースの日付は未定であり、**マップのシェイプ**はまだプレビュー段階です)。 このプレビュー リリースでは、この記事の次の「**地域キー**」セクションにある表のマップの地域キーを参照してください。
* **マップのシェイプ** ビジュアルで最大 1,500 個のデータ ポイントが描かれます。

## <a name="region-keys"></a>地域キー

このプレビュー リリースでは、次の**地域キー**を使用して、 **[マップのシェイプ]** をテストしてください。

### <a name="australia-states"></a>オーストラリア: 州

| ID | 省略形 | ISO | 名前 | 郵便 |
| --- | --- | --- | --- | --- |
| au-wa |WA |AU-WA |Western Australia |WA |
| au-vic |Vic |AU-VIC |Victoria |VIC |
| au-tas |Tas |AU-TAS |Tasmania |TAS |
| au-sa |SA |AU-SA |South Australia |SA |
| au-qld |Qld |AU-QLD |クイーンズランド |QLD |
| au-nt |NT |AU-NT |Northern Territory |NT |
| au-nsw |NSW |AU-NSW |New South Wales |NSW |
| au-act |ACT |AU-ACT |Australian Capital Territory |ACT |

### <a name="austria-states"></a>オーストリア: 州

| ID | ISO | 名前 | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- |
| at-wi |AT-9 |Wien |Vienna (ウィーン) |WI |
| at-vo |AT-8 |Vorarlberg |Vorarlberg |VO |
| at-tr |AT-7 |Tirol |Tyrol (チロル) |TR |
| at-st |AT-6 |Steiermark |Styria (シュタイアーマルク) |ST |
| at-sz |AT-5 |Salzburg |Salzburg |SZ |
| at-oo |AT-4 |Oberösterreich |Upper Austria (オーバーエスターライヒ) |OO |
| at-no |AT-3 |Niederösterreich |Lower Austria (ニーダーエスターライヒ) |いいえ |
| at-ka |AT-2 |Kärnten |Carinthia (ケルンテン) |KA |
| at-bu |AT-1 |Burgenland |Burgenland |BU |

### <a name="brazil-states"></a>ブラジル: 州

| ID |
| --- |
| Tocantins |
| Pernambuco |
| Goias |
| Sergipe |
| サンパウロ |
| Santa Catarina |
| Roraima |
| Rondonia |
| Rio Grande do Sul |
| Rio Grande do Norte |
| Rio de Janeiro |
| Piaui |
| Parana |
| Paraiba |
| Para |
| Minas Gerais |
| Mato Grosso |
| Maranhao |
| Mato Grosso do Sul |
| Distrito Federal |
| Ceara |
| Espirito Santo |
| Bahia |
| Amazonas |
| Amapa |
| Alagoas |
| Acre |
| Litigated Zone 1 |
| Litigated Zone 2 |
| Litigated Zone 3 |
| Litigated Zone 4 |

### <a name="canada-provinces"></a>カナダ: 州

| ID | ISO | 名前 | 郵便 |
| --- | --- | --- | --- |
| ca-nu |CA-NU |Nunavut |NU |
| ca-nt |CA-NT |Northwest Territories |NT |
| ca-yt |CA-YT |Yukon |YT |
| ca-sk |CA-SK |Saskatchewan |SK |
| ca-qc |CA-QC |ケベック |QC |
| ca-pe |CA-PE |Prince Edward Island |PE |
| ca-on |CA-ON |Ontario |オン |
| ca-ns |CA-NS |Nova Scotia |NS |
| ca-nl |CA-NL |Newfoundland and Labrador |NL |
| ca-nb |CA-NB |New Brunswick |NB |
| ca-mb |CA-MB |マニトバ |MB |
| ca-bc |CA-BC |British Columbia |BC |
| ca-ab |CA-AB |Alberta |AB |

### <a name="france-regions"></a>フランス: 地域圏

| ID | 名前 | 名前 (英語) |
| --- | --- | --- |
| Auvergne-Rhone-Alpes |  |  |
| Bourgogne-Franche-Comte |  |  |
| Bretagne |Bretagne |Brittany (ブルターニュ) |
| Centre-Val de Loire |Centre-Val de Loire |Centre-Val de Loire |
| Corse |Corse |Corse (コルシカ島) |
| Grand Est |  |  |
| グアドループ | |   |
| Hauts-de-France |  |  |
| Ile-de-France (イル ド フランス) |Île-de-France |Ile-de-France (イル ド フランス) |
| La Reunion |  |  |
| Mayotte  |  |  |
| Normandie (ノルマンディー) |Normandie (ノルマンディー) |  |
| Nouvelle-Aquitaine |  |  |
| Occitanie  |  |  |
| Pays de la Loire |Pays de la Loire |Pays de la Loire |
| Provence-Alpes-Cote d'Azur |Provence-Alpes-Côte d'Azur |Provence-Alpes-Cote d'Azur |
|  |  |  |

### <a name="germany-states"></a>ドイツ: 州

| ID | ISO | 名前 | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- |
| de-be |DE-BE |Berlin (ベルリン) |Berlin (ベルリン) |BE |
| de-th |DE-TH |Thüringen |Thuringia (チューリンゲン) |TH |
| de-st |DE-ST |Sachsen-Anhalt |Saxony-Anhalt (ザクセン=アンハルト) |ST |
| de-sn |DE-SN |Sachsen |Saxony (サクソニー) |SN |
| de-mv |DE-MV |Mecklenburg-Vorpommern |Mecklenburg-Vorpommern |MV |
| de-bb |DE-BB |Brandenburg |Brandenburg |BB |
| de-sh |DE-SH |Schleswig-Holstein |Schleswig-Holstein |SH |
| de-sl |DE-SL |Saarland |Saarland |SL |
| de-rp |DE-RP |Rheinland-Pfalz |Rhineland-Palatinate (ラインラント=プファルツ) |RP |
| de-nw |DE-NW |Nordrhein-Westfalen |North Rhine-Westphalia (ノルトライン=ウェストファーレン) |NW |
| de-ni |DE-NI |Niedersachsen |Lower Saxony (ニーダーザクセン) |NI |
| de-he |DE-HE |Hessen |Hesse (ヘッセン) |HE |
| de-hh |DE-HH |Hamburg |Hamburg |HH |
| de-hb |DE-HB |Bremen (ブレーメン) |Bremen (ブレーメン) |HB |
| de-by |DE-BY |Bayern |Bavaria (バイエルン) |別 |
| de-bw |DE-BW |Baden-Württemberg |Baden-Wurttemberg (バーデン=ウュルテンベルク) |BW |

### <a name="ireland-counties"></a>アイルランド: 州

| ID |
| --- |
| Wicklow |
| Wexford |
| Westmeath |
| Waterford |
| Sligo |
| Tipperary |
| Roscommon |
| Offaly |
| Monaghan |
| Meath |
| Mayo |
| Louth |
| Longford |
| Limerick |
| Leitrim |
| Laoighis |
| Kilkenny |
| Kildare |
| Kerry |
| Galway |
| Dublin |
| Donegal |
| Cork |
| Clare |
| Cavan |
| Carlow |

### <a name="italy-regions"></a>イタリア: 州

| ID | ISO | 名前 | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- |
| it-vn |IT-34 |Veneto (ベネト) |Veneto (ベネト) |VN |
| it-vd |IT-23 |Valle d'Aosta |Aosta Valley (ヴァッレ ダオスタ) |VD |
| it-um |IT-55 |Umbria (ウンブリア) |Umbria (ウンブリア) |UM |
| it-tt |IT-32 |Trentino-Alto Adige |Trentino-South Tyrol (トレンティーノ=アルト アディジェ) |TT |
| it-tc |IT-52 |Toscana |Tuscany (トスカナ) |TC |
| it-sc |IT-82 |Sicilia |Sicily (シチリア島) |SC |
| it-sd |IT-88 |Sardegna |Sardinia (サルディニア) |SD |
| it-pm |IT-21 |Piemonte |Piedmont (ピエモンテ) |午後 |
| it-ml |IT-67 |Molise |Molise |ML |
| it-mh |IT-57 |Marche (マルケ) |Marche (マルケ) |MH |
| it-lm |IT-25 |Lombardia |Lombardy (ロンバルディア) |LM |
| it-lg |IT-42 |Liguria |Liguria |LG |
| it-lz |IT-62 |Lazio |Lazio |LZ |
| it-fv |IT-36 |Friuli-Venezia Giulia |Friuli-Venezia Giulia |FV |
| it-er |IT-45 |Emilia-Romagna |Emilia-Romagna |ER |
| it-cm |IT-72 |Campania (カンパニア) |Campania (カンパニア) |CM |
| it-lb |IT-78 |Calabria |Calabria |LB |
| it-bc |IT-77 |Basilicata (バシリカータ) |Basilicata (バシリカータ) |BC |
| it-pu |IT-75 |Apulia |Puglia (プーリア) |PU |
| it-ab |IT-65 |Abruzzo |Abruzzo |AB |

### <a name="mexico-states"></a>メキシコ: 州

| ID | 省略形 | ISO | 名前 | 名前 (英語) | 郵便 |
| --- | --- | --- | --- | --- | --- |
| mx-zac |Zac. |MX-ZAC |Zacatecas |Zacatecas |ZA |
| mx-yuc |Yuc. |MX-YUC |Yucatán |Yucatan (ユカタン) |YU |
| mx-ver |Ver. |MX-VER |Veracruz |Veracruz |VE |
| mx-tla |Tlax. |MX-TLA |Tlaxcala (トラスカラ) |Tlaxcala (トラスカラ) |TL |
| mx-tam |Tamps. |MX-TAM |Tamaulipas (タマウリパス) |Tamaulipas (タマウリパス) |TM |
| mx-tab |Tab. |MX-TAB |Tabasco (タバスコ) |Tabasco (タバスコ) |TB |
| mx-son |Son. |MX-SON |Sonora |Sonora |SO |
| mx-sin |Sin. |MX-SIN |Sinaloa (シナロア) |Sinaloa (シナロア) |SI |
| mx-slp |S.L.P. |MX-SLP |San Luis Potosí |San Luis Potosi (サン ルイス ポトシ) |SL |
| mx-roo |Q.R. |MX-ROO |Quintana Roo |Quintana Roo |QR |
| mx-que |Qro. |MX-QUE |Querétaro |Queretaro (ケレタロ) |QE |
| mx-pue |Pue. |MX-PUE |Puebla (プエブラ) |Puebla (プエブラ) |PU |
| mx-oax |Oax. |MX-OAX |Oaxaca (オアハカ) |Oaxaca (オアハカ) |OA |
| mx-nle |N.L. |MX-NLE |Nuevo León |Nuevo Leon (ヌエボレオン) |NL |
| mx-nay |Nay. |MX-NAY |Nayarit (ナヤリト) |Nayarit (ナヤリト) |NA |
| mx-mor |Mor. |MX-MOR |Morelos (モレロス) |Morelos (モレロス) |MR |
| mx-mic |Mich. |MX-MIC |Michoacán |Michoacan (ミチョアカン) |MC |
| mx-mex |Méx. |MX-MEX |Estado de México |Mexico State (メヒコ) |MX |
| mx-jal |Jal. |MX-JAL |Jalisco (ハリスコ) |Jalisco (ハリスコ) |JA |
| mx-hid |Hgo. |MX-HID |Hidalgo (イダルゴ) |Hidalgo (イダルゴ) |HI |
| mx-gro |Gro. |MX-GRO |Guerrero |Guerrero |GR |
| mx-gua |Gto. |MX-GUA |Guanajuato (グアナフアト) |Guanajuato (グアナフアト) |GT |
| mx-dur |Dgo. |MX-DUR |Durango (ドゥランゴ) |Durango (ドゥランゴ) |DU |
| mx-dif |CDMX. |MX-DIF |Ciudad de México |Mexico City (メキシコシティー) |DF |
| mx-col |Col. |MX-COL |Colima (コリマ) |Colima (コリマ) |CL |
| mx-coa |Coah. |MX-COA |Coahuila (コアウイラ) |Coahuila (コアウイラ) |CA |
| mx-chh |Chih. |MX-CHH |Chihuahua (チワワ) |Chihuahua (チワワ) |CH |
| mx-chp |Chis. |MX-CHP |Chiapas (チャパス) |Chiapas (チャパス) |CP |
| mx-cam |Camp. |MX-CAM |Campeche |Campeche |CM |
| mx-bcs |B.C.S. |MX-BCS |Baja California Sur (バハ カリフォルニア スル) |Baja California Sur (バハ カリフォルニア スル) |BS |
| mx-bcn |B.C. |MX-BCN |Baja California (バハ カリフォルニア) |Baja California (バハ カリフォルニア) |BN |
| mx-agu |Ags. |MX-AGU |Aguascalientes (アグアスカリエンテス) |Aguascalientes (アグアスカリエンテス) |AG |

### <a name="netherlands-provinces"></a>オランダ: 州

| ID | ISO | 名前 | 名前 (英語) |
| --- | --- | --- | --- |
| nl-zh |NL-ZH |Zuid-Holland |South Holland (南ホラント) |
| nl-ze |NL-ZE |Zeeland (ゼーラント) |Zeeland (ゼーラント) |
| nl-ut |NL-UT |Utrecht (ユトレヒト) |Utrecht (ユトレヒト) |
| nl-ov |NL-OV |Overijssel (オーバーアイセル) |Overijssel (オーバーアイセル) |
| nl-nh |NL-NH |Noord-Holland |North Holland (北ホラント) |
| nl-nb |NL-NB |Noord-Brabant |North Brabant (北ブラバント) |
| nl-li |NL-LI |Limburg (リンブルフ) |Limburg (リンブルフ) |
| nl-gr |NL-GR |Groningen |Groningen |
| nl-ge |NL-GE |Gelderland (ヘルデルラント) |Gelderland (ヘルデルラント) |
| nl-fr |NL-FR |Fryslân |Friesland (フリースラント) |
| nl-fl |NL-FL |Flevoland (フレヴォラント) |Flevoland (フレヴォラント) |
| nl-dr |NL-DR |Drenthe |Drenthe |

### <a name="uk-countries"></a>英国: 地方

| ID | ISO | 名前 |
| --- | --- | --- |
| gb-wls |GB-WLS |Wales |
| gb-sct |GB-SCT |Scotland |
| gb-nir |GB-NIR |Northern Ireland |
| gb-eng |GB-ENG |England |

### <a name="usa-states"></a>米国: 州

| ID | 名前 | 郵便 |
| --- | --- | --- |
| us-mi |Michigan |MI |
| us-ak |アラスカ |AK |
| us-hi |Hawaii |HI |
| us-fl |Florida |FL |
| us-la |ルイジアナ |LA |
| us-ar |アーカンソー |AR |
| us-sc |South Carolina |SC |
| us-ga |ジョージア |GA |
| us-ms |Mississippi |MS |
| us-al |Alabama |AL |
| us-nm |New Mexico |NM |
| us-tx |Texas |TX |
| us-tn |Tennessee |TN |
| us-nc |ノースカロライナ |NC |
| us-ok |オクラホマ |OK |
| us-az |アリゾナ |AZ |
| us-mo |Missouri |MO |
| us-va |バージニア州 |VA |
| us-ks |カンサス |KS |
| us-ky |Kentucky |KY |
| us-co |Colorado |CO |
| us-md |メリーランド |MD |
| us-wv |West Virginia |WV |
| us-de |デラウェア |DE |
| us-dc |District of Columbia |DC |
| us-il |イリノイ州 |IL |
| us-oh |Ohio |OH |
| us-ca |California |CA |
| us-ut |Utah |UT |
| us-nv |Nevada |NV |
| us-in |Indiana |IN |
| us-nj |New Jersey |NJ |
| us-ri |Rhode Island |RI |
| us-ct |Connecticut |CT |
| us-pa |ペンシルベニア |PA |
| us-ny |New York |NY |
| us-ne |Nebraska |NE |
| us-ma |Massachusetts |MA |
| us-ia |Iowa |IA |
| us-nh |ニューハンプシャー |NH |
| us-or |オレゴン |または |
| us-mn |Minnesota |MN |
| us-vt |Vermont |VT |
| us-id |アイダホ |ID |
| us-wi |ウィスコンシン |WI |
| us-wy |Wyoming |WY |
| us-sd |South Dakota |SD |
| us-nd |North Dakota |ND |
| us-me |Maine |ME |
| us-mt |Montana |MT |
| us-wa |ワシントン |WA |

## <a name="next-steps"></a>次のステップ

* [Power BI のマトリックス ビジュアル](desktop-matrix-visual.md)

* [Power BI での視覚化の種類](power-bi-visualization-types-for-reports-and-q-and-a.md)
