---
title: iOS モバイル アプリでの "通信障害" - Power BI の修正
description: この記事は、"通信エラーが発生しました。 Wi-Fi 接続のプロキシ設定に関係したエラーの可能性があります。" というメッセージが表示される場合に役に立ちます。
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/21/2018
ms.author: mshenhav
ms.openlocfilehash: 9e487f4305b663028714cbe45ab76abaaa4a6db9
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2019
ms.locfileid: "61135706"
---
# <a name="fixing-communication-failures-in-ios-mobile-apps---power-bi"></a>iOS モバイル アプリでの "通信障害" - Power BI の修正

| ![iPhone](./media/mobile-known-issues-with-the-iphone-app/iphone-logo-50-px.png) | ![iPad](./media/mobile-known-issues-with-the-iphone-app/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhone |iPad |

## <a name="we-encountered-communication-failures"></a>「通信障害が発生しました」
「通信障害が発生しました。 「この障害は Wi-Fi 接続のプロキシ設定と関係がある可能性があります。 別の Wi-Fi 接続に切り替えることによって、この問題が解決する場合があります。」

iPhone または iPad のインターネット接続で、明示的な HTTP プロキシ (手動または自動のいずれか) の構成が必須である場合に、このメッセージが表示されることがあります。 この場合、iOS デバイスで Power BI アプリが機能しません。

### <a name="workaround"></a>回避策
明示的な HTTP プロキシの設定を必要としない別の接続 (HTTP プロキシがオフに構成されている接続など) に iPhone または iPad を切り替えます。

## <a name="other-issues"></a>その他に問題がありますか。
[Power BI コミュニティ](http://community.powerbi.com/)で質問してみてください。

