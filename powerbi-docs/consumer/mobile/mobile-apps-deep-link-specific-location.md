---
title: Power BI モバイル アプリの特定の場所へのリンクを作成する
description: URI (Uniform Resource Identifier) で Power BI モバイル アプリの特定のダッシュボード、タイル、またはレポートへのディープ リンクを作成する方法について説明します。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: mshenhav
ms.openlocfilehash: 4e09b10e38b018f8e5572343b343a243ace3bf81
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906526"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Power BI モバイル アプリの特定の場所へのリンクを作成する
リンクを使用して、Power BI での特定の項目に直接アクセスすることができます。レポート、ダッシュ ボードとタイル。

Power BI モバイルでのリンクを使用するための主に 2 つのシナリオがあります。 

* Power BI を開く **、アプリ外で**と特定のコンテンツ (レポート/ダッシュ ボードとアプリ) にします。 その他のアプリから Power BI Mobile を開きたい場合は通常、統合シナリオになります。 
* **移動**Power BI 内で。 これは、通常、Power BI でカスタム ナビゲーションを作成するときにします。


## <a name="use-links-from-outside-of-power-bi"></a>Power BI の外部からのリンクを使用して、
Power BI アプリの外部からのリンクを使用する場合は、アプリによって開かれることかどうかを確認して、アプリをインストールするユーザーを提供し、デバイス上にインストールされていない場合。 サポートするために特別なリンク形式を作成しました。 このリンク形式はことを確認、デバイスが、リンクを開く、アプリを使用して、アプリがデバイスにインストールされていない場合は、手をストアに移動するユーザーが提供されます。

次のように、リンクを開始する必要があります。  
```html
https://app.powerbi.com/Redirect?[**QUERYPARAMS**]
```

> [!IMPORTANT]
> 場合は、コンテンツは、政府、中国などの特殊なデータ センターでホストされます。リンクのような先頭には、右側の Power BI アドレス`app.powerbigov.us`または`app.powerbi.cn`します。   
>


**クエリ PARAMS**は。
* **action**(必須) = OpenApp/OpenDashboard/OpenTile/OpenReport
* **appId** = レポートまたはアプリの一部であるダッシュ ボードを開きたい場合 
* **groupObjectId** = レポートまたはワークスペース (ただし、マイ ワークスペースではなく) の一部であるダッシュ ボードを開きたい場合
* **dashboardObjectId** (操作が OpenDashboard または OpenTile) 場合は、ダッシュ ボード オブジェクトの ID を =
* **reportObjectId** = レポート オブジェクト ID (アクションが OpenReport の場合)
* **tileObjectId** = タイル オブジェクト ID(アクションが OpenTile の場合)
* **reportPage** = (action は、OpenReport) 場合は、特定のレポート セクションを開きたい場合
* **ctid** = 項目の組織 ID (B2B のシナリオに関連します。 これを省略できます、項目がユーザーの組織に属している場合)。

**例:**

* アプリを開くリンク 
  ```html
  https://app.powerbi.com/Redirect?action=OpenApp&appId=appidguid&ctid=organizationid
  ```

* アプリの一部であるダッシュ ボードを開く 
  ```html
  https://app.powerbi.com/Redirect?action=OpenDashboard&appId=**appidguid**&dashboardObjectId=**dashboardidguid**&ctid=**organizationid**
  ```

* ワークスペースの一部であるレポートを開く
  ```html
  https://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId=**reportidguid**&groupObjectId=**groupidguid**&reportPage=**ReportSectionName**
  ```

### <a name="how-to-get-the-right-link-format"></a>適切なリンク形式を取得する方法

#### <a name="links-of-apps-and-items-in-app"></a>アプリとアプリ内の項目のリンク

**アプリのレポートとダッシュ ボードはアプリの一部である**リンクを取得する最も簡単な方法は、アプリ ワークスペースに移動し、「アプリを更新」を選択します。 開き、「アプリの発行」エクスペリエンスとアクセス タブでは紹介を**リンク**セクション。 展開セクションとするアプリの一覧が表示され、そのすべてのコンテンツにリンクすることは、直接アクセスするために使用できます。

![Power BI アプリへのリンクを発行します。 ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-of-items-not-in-app"></a>アプリではなく項目のリンク 

レポートおよびダッシュ ボードをアプリの一部ではない、アイテムの URL から Id を抽出する必要があります。

たとえば、36 文字を検索する**ダッシュ ボード**オブジェクト ID、Power BI サービスで特定のダッシュ ボードに移動します 

```html
https://app.powerbi.com/groups/me/dashboards/**dashboard guid comes here**?ctid=**organization id comes here**`
```

36 文字を検索する**レポート**オブジェクト ID、Power BI サービスでは、特定のレポートに移動します。
これは、「マイ ワークスペース」からのレポートの例

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**`
```
上記の URL にも含まれる特定のレポート ページ **"ReportSection3"** します。

これは、ワークスペース (マイ ワークスペースではなく) からレポートの例

```html
https://app.powerbi.com/groups/**groupid comes here**/reports/**reportid comes here**/ReportSection1?ctid=**organizationid comes here**
```

## <a name="use-links-inside-power-bi"></a>Power BI 内のリンクを使用して、

Power BI 内のリンクは、Power BI サービス同様に、モバイル アプリで作業しています。

Power BI の別のアイテムを指すレポートへのリンクを追加する場合は、ブラウザーのアドレス バーからだけそのアイテムの URL をコピーできます。 詳細をご覧ください[レポート内のテキスト ボックスにハイパーリンクを追加する方法](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box)します。

## <a name="use-report-url-with-filter"></a>フィルターを使用してレポート URL を使用します。
同じ Power BI サービス、Power BI モバイル アプリもサポートしてフィルターのクエリ パラメーターを含むレポートの URL。 Power BI モバイル アプリでレポートを開くし、特定の状態をフィルター処理できます。 この URL の売上レポートを開くなどと Territory でフィルター処理

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**&filter=Store/Territory eq 'NC'
```

詳細を読む[レポートをフィルター処理するクエリ パラメーターを作成する方法](https://docs.microsoft.com/power-bi/service-url-filters)します。

## <a name="next-steps"></a>次の手順
Power BI モバイル アプリで使用したいその他の機能にぜひ投票してください。お客様からのフィードバックは、将来実装する機能を決めるのに役立ちます。 

* [モバイル デバイス用の Power BI アプリ](mobile-apps-for-mobile-devices.md)
* Twitter で @MSPowerBI をフォローする
* [Power BI コミュニティの会話](http://community.powerbi.com/)に参加する
* [Power BI とは?](../../power-bi-overview.md)

