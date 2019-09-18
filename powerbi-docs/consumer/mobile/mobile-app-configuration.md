---
title: Power BI iOS アプリ構成設定
description: MDM ツールを使用して iOS 用 Power BI の動作をカスタマイズする方法
author: paulinbar
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: bc9c6dd8cd892ab0304cc5a99a3bb780486f32f0
ms.sourcegitcommit: 52aa112ac9194f4bb62b0910c4a1be80e1bf1276
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2019
ms.locfileid: "70160156"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>モバイル デバイス管理 (MDM) ツールを使用して Power BI iOS アプリをリモートで構成する

iOS 用 Power BI Mobile アプリでは、Office 365 とモバイル デバイス管理 (MDM) (Intune など) の管理者がアプリの動作をカスタマイズできるようにするアプリ設定をサポートします。

iOS 用 Power BI Mobile アプリでは、次の構成シナリオをサポートします。

- レポート サーバーの構成
- データ保護の設定

## <a name="report-server-configuration"></a>レポート サーバーの構成

Power BI iOS アプリでは、管理者が登録済みデバイスを使用してレポート サーバーの構成をリモートで "プッシュ" することができます。

| キー | 種類 | 説明 |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | 文字列 | レポート サーバー URL。<br><br>先頭は http/https である必要があります。|
| com.microsoft.powerbi.mobile.ServerUsername | 文字列 | (省略可能)<br><br>サーバーの接続に使用するユーザー名。<br><br>存在しない場合、アプリで、ユーザーに接続用のユーザー名の入力を求めるメッセージが表示されます。|
| com.microsoft.powerbi.mobile.ServerDisplayName | 文字列 | (省略可能)<br><br>既定値は "Report server" です<br><br>サーバーを表すためにアプリで使用されるフレンドリ名。 |
| com.microsoft.powerbi.mobile.OverrideServerDetails | ブール値 | (省略可能)<br><br>既定値は True です。 True に設定されている場合、モバイル デバイスに既にあるレポート サーバーのすべての定義がオーバーライドされます。 既に構成されているサーバーは、削除されます。 また、オーバーライドを True に設定すると、ユーザーはその構成を削除できなくなります。<br><br>False に設定すると、既存の設定はそのままで、プッシュされた値が追加されます。 同じサーバー URL がモバイル アプリに既に構成されている場合、アプリはその構成をそのままにします。 アプリで同じサーバーへの再認証をユーザーに求めることはありません。 |

## <a name="data-protection-setting"></a>データ保護の設定

Power BI iOS アプリでは、管理者にセキュリティとプライバシーの設定に対する既定の構成をカスタマイズする機能が提供されます。 Power BI アプリにアクセスしている場合、ユーザーに自分の Face ID、Touch ID、またはパスコードを提供するように強制できます。

| キー | 種類 | 説明 |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | ブール値 | 既定値は False です。 <br><br>デバイス上のアプリにアクセスするために、ユーザーに TouchID や FaceID などの生体測定を要求することができます。 必要に応じて、認証に加えて生体測定が使用されます。<br><br>アプリ保護ポリシーを使用している場合、Microsoft ではデュアル アクセスのプロンプトを防ぐために、この設定を無効にすることをお勧めします。 |

## <a name="deploying-app-configuration-settings"></a>アプリ構成設定を配置する

次の手順によって、アプリ構成ポリシーを作成できるようにします。 構成ポリシーが作成されたら、ユーザーのグループにその設定を割り当てることができます。

1. MDM ツールを接続します。

2. 新しいアプリ構成ポリシーを作成して名前を付けます。

3. このアプリ構成ポリシーを配布するユーザーを選択します。

4. ユーザーにプッシュする設定に対してキー値のペアを作成します。

Intune ポータルでは、管理者がアプリ構成ポリシーによって Power BI iOS アプリにこれらの設定を簡単に配置できます。
しかし、任意の MDM プロバイダーがサポートされています。 Intune を使用していない場合は、これらの設定を配置する方法で、ご利用の MDM ドキュメントを参照する必要があります。

## <a name="next-steps"></a>次の手順

* [Power BI iPhone モバイル アプリ](http://go.microsoft.com/fwlink/?LinkId=522062)をダウンロードする
* Twitter で [@MSPowerBI をフォローする](https://twitter.com/MSPowerBI)
* [Power BI コミュニティの会話](http://community.powerbi.com/)に参加する
