---
title: Power BI モバイル アプリで地理的な場所によりレポートをフィルターする
description: レポート所有者が場所タグを設定している場合に、Microsoft Power BI モバイル アプリで地理的な場所によりレポートをフィルターする方法について説明します。
author: mshenhav
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 02/09/2018
ms.author: mshenhav
ms.openlocfilehash: 828dcb4aeb8b7c5e69292685470f112a2d85cb71
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2019
ms.locfileid: "61349491"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>Power BI モバイル アプリで地理的な場所によりレポートをフィルターする
適用対象:

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Android フォン](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Android タブレット](./media/mobile-apps-geographic-filtering/android-tablet-logo-50-px.png) | ![Android タブレット](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Android フォン |Android タブレット |Windows 10 スマートフォン |

モバイル デバイスで Power BI レポートを開くと、右上に小さなプッシュピン アイコンが表示されることがあります。 プッシュピンが表示される場合、場所に基づいてそのレポートをフィルターできます。

> [!NOTE]
> 場所でフィルター処理できるのは、レポート内の地名が英語で書かれている場合のみです ("New York City"、"Germany" など)。 Windows 10 タブレットと PC は地理的なフィルタリングをサポートしていませんが、Windows 10 スマートフォンはサポートしています。
> 
> 

## <a name="filter-your-report-by-your-geographic-location"></a>地理的な場所でレポートをフィルターする
1. モバイル デバイスの Power BI モバイル アプリでレポートを開きます。
2. レポートに地理的なデータが含まれている場合、Power BI に位置情報へのアクセスを許可するように求めるメッセージが表示されます。 **[許可]** をクリックし、もう一度 **[許可]** をタップします。
3. 押しピン ![押しピン アイコンをタップします。](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). レポート内のデータに応じて、市、都道府県、または国/地域でフィルターすることができます。 フィルターを使用すると、現在地に一致する選択肢のみが一覧表示されます。
   
    ![押しピン フィルター](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>レポートに場所タグが表示されない場合
場所タグが表示されるには、3 つの条件がすべて満たされている必要があります。 

* Power BI Desktop でレポートを作成したユーザーが、少なくとも 1 つの列に対して[地理データを分類](../../desktop-mobile-geofiltering.md)していること (市区町村、都道府県、国/地域など)。
* レポートを表示するユーザーが、列内にデータがある場所のいずれかにいること。
* レポートを表示するユーザーが、次のモバイル デバイスのいずれかを使っていること。
  * iOS (iPad、iPhone、iPod)。
  * Android フォンまたはタブレット。
  * Windows 10 スマートフォン (PC やタブレットなどの他の Windows 10 デバイスは、地理的フィルタリングをサポートしません)。

Power BI Desktop での[地理的なフィルターの設定](../../desktop-mobile-geofiltering.md)の詳細を参照してください。

### <a name="next-steps"></a>次の手順
* [モバイル アプリで現実世界から Power BI データに接続する](mobile-apps-data-in-real-world-context.md)
* [Power BI Desktop でのデータ分類](../../desktop-data-categorization.md) 
* わからないことがある場合は、 [Power BI コミュニティで質問してみてください](http://community.powerbi.com/)。

