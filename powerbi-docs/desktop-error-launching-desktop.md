---
title: Power BI Desktop の起動時の問題を解決する
description: Power BI Desktop の起動時の問題を解決する
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 90debd0a24485c2d2a0bb82fcb2478089aee7719
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2020
ms.locfileid: "75761090"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Power BI Desktop の起動に関するトラブルシューティング
**Power BI Desktop** では、以前のバージョンの **Power BI オンプレミス データ ゲートウェイ**をインストールして実行していたユーザーが Power BI Desktop を起動できないことがあります。これは、Power BI オンプレミス データ ゲートウェイがローカル コンピューターの名前付きパイプに設定した管理ポリシー制限が原因で発生します。 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>オンプレミス データ ゲートウェイと Power BI Desktop での問題を解決する
オンプレミス データ ゲートウェイに関する問題を解決して、Power BI Desktop を起動できるようにするには、3 つのオプションがあります。

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>解決方法 1:最新バージョンの Power BI オンプレミス データ ゲートウェイをインストールする
Power BI オンプレミス データ ゲートウェイの最新バージョンでは、ローカル コンピューターの名前付きパイプに制限が設定されないため、Power BI Desktop を正常に起動できます。 引き続き Power BI オンプレミス データ ゲートウェイを使う必要がある場合は、この解決方法をお勧めします。 最新バージョンの Power BI オンプレミス データ ゲートウェイは、[こちら](https://go.microsoft.com/fwlink/?LinkId=698863)からダウンロードできます。 なお、このリンクはインストール用の実行可能ファイルへの直接ダウンロード リンクですのでご注意ください。

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>解決方法 2:Power BI オンプレミス データ ゲートウェイの Windows サービスをアンインストールまたは停止する
Power BI オンプレミス データ ゲートウェイが不要になった場合は、これをアンインストールするか、Power BI オンプレミス データ ゲートウェイの Windows サービスを停止すれば、ポリシー制限が解除され、Power BI Desktop を起動できるようになります。

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>解決方法 3:管理者特権を使って Power BI Desktop を実行する
別の方法として、Power BI Desktop を管理者として正常に起動できれば、Power BI Desktop も正常に起動できます。 この場合でも、前述のとおり Power BI オンプレミス データ ゲートウェイの最新バージョンをインストールすることを勧めします。

Power BI Desktop はマルチプロセス アーキテクチャとして設計されており、複数のプロセスが Windows 名前付きパイプを使って通信していることに注意することが重要です。 これらの名前付きパイプを干渉する他のプロセスがある可能性があります。 このような干渉の最も一般的な理由はセキュリティであり、ウイルス対策ソフトウェアやファイアウォールがパイプをブロックしたり、特定のポートにトラフィックをリダイレクトしたりしている場合があります。 管理者特権で Power BI Desktop を起動すると、その問題が解決する可能性があります。 管理者特権で起動できない場合は、管理者に連絡し、適用されているどのセキュリティ ルールによって名前付きパイプの正しい通信が妨げられているかを確認し、Power BI Desktop とその各サブプロセスをホワイトリストに登録してください。

## <a name="resolve-issues-when-connecting-to-sql-server"></a>SQL Server に接続するときの問題を解決する
SQL Server データベースに接続したとき、次のようなエラー メッセージが表示されたら、多くの場合、管理者として **Power BI Desktop** を起動し、SQL Server 接続を行うことで問題を解決できます。

    "An error happened while reading data from the provider: 'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies. Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"

管理者として起動し、接続を確立すると、必要な DLL が適宜登録されます。 その後、管理者として Power BI Desktop を起動する必要がなくなります。

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Power BI Desktop 起動時の他の問題に関するヘルプ
**Power BI Desktop** で発生するできる限り多くの問題に対応するように作業しています。 多くのお客様に影響を与える可能性がある問題を常に注視し、記事にしています。

**Power BI Desktop** の起動時の問題がオンプレミス データ ゲートウェイと関係ない場合、または前記の解決方法で解決しないときは、[Power BI のサポート](https://support.powerbi.com) (https://support.powerbi.com) ) にサポート インシデントを送信して、問題の特定と解決を依頼できます。

今後 **Power BI Desktop** で他の問題が発生した場合は (発生しないか非常に少ないことが望ましい)、トレースを有効にしてログ ファイルを収集すると、問題の分離と特定に役立ちます。 トレースを有効にするには、 **[ファイル] > [オプションと設定] > [オプション]** を選び、 **[診断]** を選んだ後、 *[診断オプション]* の **[トレースを有効にする]** をオンにします。 このオプションを設定するには **Power BI Desktop** が動作している必要があることはわかっていますが、**Power BI Desktop** の起動に関する将来の問題にはいっそう有用です。

