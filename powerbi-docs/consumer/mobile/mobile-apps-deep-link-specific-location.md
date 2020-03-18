---
title: Power BI モバイル アプリの特定の場所へのリンクを作成する
description: URI (Uniform Resource Identifier) で Power BI モバイル アプリの特定のダッシュボード、タイル、またはレポートへのディープ リンクを作成する方法について説明します。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: f0a72cf315c8ad911414274daae11b712971b305
ms.sourcegitcommit: 480bba9c745cb9af2005637e693c5714b3c64a8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2020
ms.locfileid: "79114498"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Power BI モバイル アプリの特定の場所へのリンクを作成する
Power BI では、リンクを使用し、レポート、ダッシュボード、タイルといった特定の項目に直接アクセスできます。

Power BI Mobile におけるリンクの使用には主に 2 つのシナリオがあります。 

* **アプリの外部**から Power BI を開き、特定のコンテンツ (レポート/ダッシュボード/アプリ) にアクセスするため。 これは通常、他のアプリから Power BI Mobile を開くような統合シナリオです。 
* Power BI 内で**移動**するため。 これは通常、Power BI でカスタム ナビゲーションを作成するときです。


## <a name="use-links-from-outside-of-power-bi"></a>Power BI の外部からリンクを使用する
Power BI アプリの外部からリンクを使用するとき、アプリによってリンクが開くことを確認し、アプリがデバイスにインストールされていない場合、それをインストールすることをユーザーに提案します。 まさにこれをサポートする目的で Microsoft では特別なリンク形式を作成しました。 このリンク形式によって、デバイスではアプリを使用してリンクが開きます。アプリがデバイスにインストールされていない場合、ストアに移動してアプリを入手するようにユーザーに提案されます。

リンクは次から始めてください。  
```html
https://app.powerbi.com/Redirect?[**QUERYPARAMS**]
```

> [!IMPORTANT]
> コンテンツが政府や中国など特別なデータセンターでホストされている場合、`app.powerbigov.us` や `app.powerbi.cn` のような正しい Power BI アドレスでリンクを始める必要があります。   
>


**QUERY PARAMS** には次があります。
* **action** (必須) = OpenApp / OpenDashboard / OpenTile / OpenReport
* **appId** = アプリに含まれるレポートまたはダッシュボードを開く場合 
* **groupObjectId** = ワークスペース (ただし、個人用ワークスペースではない) に含まれるレポートまたはダッシュボードを開く場合
* **dashboardObjectId** = ダッシュボード オブジェクト ID (アクションが OpenDashboard または OpenTile の場合)
* **reportObjectId** = レポート オブジェクト ID (アクションが OpenReport の場合)
* **tileObjectId** = タイル オブジェクト ID (アクションが OpenTile の場合)
* **reportPage** = 特定のレポート セクションを開く場合 (アクションが OpenReport の場合)
* **ctid** = 項目の編成 ID (B2B シナリオ関連。 ユーザーの組織に項目が属する場合、これは省略できます)。

**例:**

* アプリ リンクを開く 
  ```html
  https://app.powerbi.com/Redirect?action=OpenApp&appId=appidguid&ctid=organizationid
  ```

* アプリに含まれるダッシュボードを開く 
  ```html
  https://app.powerbi.com/Redirect?action=OpenDashboard&appId=**appidguid**&dashboardObjectId=**dashboardidguid**&ctid=**organizationid**
  ```

* ワークスペースに含まれるレポートを開く
  ```html
  https://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId=**reportidguid**&groupObjectId=**groupidguid**&reportPage=**ReportSectionName**
  ```

### <a name="how-to-get-the-right-link-format"></a>正しいリンク形式を取得する方法

#### <a name="links-of-apps-and-items-in-app"></a>アプリに含まれるアプリ/項目のリンク

**アプリに含まれるアプリ、レポート、ダッシュボード**の場合、リンクを取得する最も簡単な方法は、ワークスペースに移動し、[アプリを更新] を選択することです。 これで "アプリの発行" エクスペリエンスが開きます。[アクセス] タブには **[リンク]** セクションがあります。 そのセクションを展開すると、アプリの一覧とそのコンテンツ リンクがすべて表示されます。このリンクを利用すると、アプリに直接アクセスできます。

![Power BI でアプリ リンクを発行する ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-of-items-not-in-app"></a>アプリに含まれない項目のリンク 

アプリに含まれないレポートやダッシュボードについては、項目 URL から ID を抽出する必要があります。

たとえば、36 文字の**ダッシュボード** オブジェクト ID を検索するには、Power BI サービスでその特定のダッシュボードに移動します。 

```html
https://app.powerbi.com/groups/me/dashboards/**dashboard guid comes here**?ctid=**organization id comes here**`
```

36 文字の**レポート** オブジェクト ID を検索するには、Power BI サービスでその特定のレポートに移動します。
これは "個人用ワークスペース" からのレポートの例です

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**`
```
上の URL には、 **"ReportSection3"** という特定のレポート ページも含まれています。

これはワークスペース (個人用ワークスペースではなく) からのレポートの例です

```html
https://app.powerbi.com/groups/**groupid comes here**/reports/**reportid comes here**/ReportSection1?ctid=**organizationid comes here**
```

## <a name="use-links-inside-power-bi"></a>Power BI 内でリンクを使用する

Power BI 内のリンクは、Power BI Service とまったく同じようにモバイル アプリで機能します。

別の Power BI 項目を指すレポートにリンクを追加する場合、ブラウザーのアドレス バーからその項目 URL をコピーできます。 レポートのテキスト ボックスにハイパーリンクを追加する方法については[こちら](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box)をご覧ください。

## <a name="use-report-url-with-filter"></a>フィルターを含むレポート URL を使用する
Power BI サービスと同様に、Power BI Mobile アプリでも、フィルター クエリ パラメーターを含む URL がサポートされています。 Power BI Mobile アプリでレポートを開き、フィルターを適用して特定の状態のものに絞り込むことができます。 たとえば、この URL の場合、売上レポートが開き、担当地域でフィルター処理されます

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**&filter=Store/Territory eq 'NC'
```

レポートをフィルター処理するためのクエリ パラメーターを構築する方法については[こちら](https://docs.microsoft.com/power-bi/service-url-filters)をご覧ください。

## <a name="next-steps"></a>次の手順
Power BI モバイル アプリで使用したいその他の機能にぜひ投票してください。お客様からのフィードバックは、将来実装する機能を決めるのに役立ちます。 

* [モバイル デバイス用の Power BI アプリ](mobile-apps-for-mobile-devices.md)
* Twitter で @MSPowerBI をフォローする
* [Power BI コミュニティの会話](https://community.powerbi.com/)に参加する
* [Power BI とは?](../../fundamentals/power-bi-overview.md)

