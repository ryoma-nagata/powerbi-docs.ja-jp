---
title: Power BI レポート サーバーのブラウザーのサポート
description: Power BI レポート サーバーとレポート ビューアー コントロールで管理および表示するためにサポートされているブラウザーのバージョンについて説明します。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: maggies
ms.openlocfilehash: 5a2ca653a06efbde161899602536b05c8f6ab666
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769776"
---
# <a name="browser-support-for-power-bi-report-server"></a>Power BI レポート サーバーのブラウザーのサポート
Power BI レポート サーバーとレポート ビューアー コントロールで管理および表示するためにサポートされているブラウザーのバージョンについて説明します。

## <a name="browser-requirements-for-the-web-portal"></a>Web ポータルのブラウザー要件
Web ポータルでサポートされるブラウザーの最新の一覧を次に示します。

**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9 - 10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*iOS 10 の iPhone と iPad*

* Apple Safari (+)

**Google Android**  
*Android 4.4 (KitKat) 以降のスマートフォンとタブレット*

* Google Chrome (+)
  
  **(+)** 公式にリリースされている最新バージョン

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>レポート ビューアー Web コントロール (2015) のブラウザー要件
レポート ビューアー Web コントロールでサポートされるブラウザーの最新の一覧を次に示します。 レポート ビューアーでは、Web ポータルからのレポートの表示をサポートします。

**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9 - 10.11*

* Apple Safari (+)
  
  **(+)** 公式にリリースされている最新バージョン

### <a name="authentication-requirements"></a>認証の要件
ブラウザーでは、クライアントの要求を成功させるために、レポート サーバーで処理する必要がある特定の認証方法をサポートします。 次の表に、Windows オペレーティング システムで実行されている各ブラウザーでサポートされている既定の認証の種類を示します。

| **ブラウザーの種類** | **サポート** | **ブラウザーの既定** | **サーバーの既定** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |ネゴシエート、Kerberos、NTLM、基本 |ネゴシエート |はい。 Microsoft Edge で使用する既定の認証設定。 |
| **Microsoft Internet Explorer** |ネゴシエート、Kerberos、NTLM、基本 |ネゴシエート |はい。 Internet Explorer で使用する既定の認証設定。 |
| **Google Chrome**(+) |ネゴシエート、NTLM、基本 |ネゴシエート |はい。 Chrome で使用する既定の認証設定。 |
| **Mozilla Firefox**(+) |NTLM、基本 |NTLM |はい。 Firefox で使用する既定の認証設定。 |
| **Apple Safari**(+) |NTLM、基本 |基本 |はい。 Safari で使用する既定の認証設定。 |

 **(+)** 公式にリリースされている最新バージョン

### <a name="script-requirements-for-viewing-reports"></a>レポートを表示するためのスクリプト要件
レポート ビューアーを使用するには、スクリプトを実行するようにブラウザーを構成します。

スクリプトが有効になっていない場合は、レポートを開くときに、次のようなエラー メッセージが表示されます。

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 スクリプトをサポートしていないレポートを表示する場合は、レポート ツールバーやドキュメント マップなどのレポート ビューアー機能を使用しない HTML でレポートが表示されます。

> [!NOTE]
> レポート ツールバーは、HTML ビューアー コンポーネントの一部です。 既定では、ブラウザー ウィンドウに表示されるすべてのレポートの上部にツールバーが表示されます。 レポート ビューアーでは、レポート内の情報を検索したり、特定のページまでスクロールしたり、表示目的でページ サイズを調整するなどの機能を利用できます。 レポート ツールバーまたは HTML ビューアーの詳細については、「[HTML Viewer and the Report Toolbar](https://docs.microsoft.com/sql/reporting-services/html-viewer-and-the-report-toolbar)」 (HTML ビューアーとレポート ツールバー) を参照してください。
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Visual Studio でのレポート ビューアー Web サーバー コントロールのブラウザー サポート
レポート ビューアー Web サーバー コントロールは、ASP.NET Web アプリケーションにレポート機能を埋め込むために使用します。 レポート ビューアー コントロールを取得する方法の詳細については、「[Integrating Reporting Services Using Report Viewer Controls - Get Started](https://docs.microsoft.com/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)」 (レポート ビューアー コントロールを使用して Reporting Services を統合する - はじめに) を参照してください。

スクリプトのサポートが有効になっているブラウザーを使用します。 ブラウザーでスクリプトを実行できない場合は、レポートを表示することはできません。

**Microsoft Windows**  
*Windows 7、8.1、10、Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)** 公式にリリースされている最新バージョン

## <a name="next-steps"></a>次の手順
[管理者の概要](admin-handbook-overview.md)  
[Power BI レポート サーバーのインストール](install-report-server.md)  
[レポート ビルダーのダウンロード](https://www.microsoft.com/download/details.aspx?id=53613)  
[SQL Server Data Tools (SSDT) のダウンロード](http://go.microsoft.com/fwlink/?LinkID=616714)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。

