---
title: SSL 証明書を作成する
description: 開発者向けサーバー用に手動で証明書を作成する場合の対処方法
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 06/18/2019
ms.openlocfilehash: 3287e8a7eb1c36c3f0d8a1fc24faa0442de2dddf
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425438"
---
# <a name="creating-ssl-certificate"></a>SSL 証明書を作成する

次のコマンドを実行し、Windows 8 以降の powershell New-SelfSignedCertificate コマンドレットを使用して証明書を生成します。

ツールを使用するには、**Windows** **7** 用の OpenSSL をインストールする必要があります。 `openssll` ユーティリティはコマンド ラインから使用できる必要があります。

OpenSSL のインストールについては、[https://www.openssl.org](https://www.openssl.org) または [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries) を参照してください

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-mac-os-x"></a>証明書を作成する (Mac OS X)

通常、OpenSSL ユーティリティは、Linux または Mac OS X のオペレーション システムで使用できます。

それ以外の場合は、次のようにしてインストールすることができます

*brew* パッケージ マネージャーからの場合

```cmd
brew install openssl
brew link openssl --force
```

*MacPorts* を使用する場合

```cmd
sudo port install openssl
```

新しい証明書を生成するために OpenSSL をインストールした後、以下を呼び出します。

```cmd
pbiviz --create-cert
```

## <a name="create-certificate-linux"></a>証明書を作成する (Linux)

OpenSSL ユーティリティは Linux オペレーティング システムでは使用できません。次のコマンドを使用してインストールできます。

*APT* パッケージ マネージャーの場合:

```cmd
sudo apt-get install openssl
```

*Yellowdog アップデーター* の場合:

```cmd
yum install openssl
```

*Redhat パッケージ マネージャー* の場合:

```cmd
rpm install openssl
```

オペレーティング システムで OpenSSl が既に使用可能な場合は、以下を呼び出します

```cmd
pbiviz --create-cert
```

これで新しい証明書が生成されます。

または、[https://www.openssl.org](https://www.openssl.org) あるいは [https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries) から取得します

## <a name="generate-certificate-manually"></a>証明書を手動で生成する

任意のツールで生成された証明書を指定できます。

システムに OpenSSL がインストールされている場合は、次のコマンドを実行して新しい証明書を生成できます。

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBICustomVisualTest_private.key -out PowerBICustomVisualTest_public.crt -days 365
```

通常、PowerBI-visuals-tools の Web サーバー証明書は以下の場所にあります。

```cmd
%appdata%\npm\node_modules\PowerBI-visuals-tools\certs
```

これはツールのグローバル インスタンスの場合です。

または

```cmd
<custom visual project root>\node_modules\PowerBI-visuals-tools\certs
```

これはツールのローカル インスタンスの場合です。

PEM 形式を使用する場合は、証明書ファイルを `PowerBICustomVisualTest_public.cer` として、秘密キーを `PowerBICustomVisualTest_public.key` として保存する必要があります。
PFX 形式を使用する場合は、証明書ファイルを `PowerBICustomVisualTest_public.pfx` として保存します。

PFX 証明書ファイルにパスフレーズが必要な場合は、次のように指定する必要があります。

```cmd
\PowerBI-visuals-tools\config.json
```

サーバー セクションでは、次のようにします。

```cmd
"server":{
    "root":"webRoot",
    "assetsRoute":"/assets",
    "privateKey":"certs/PowerBICustomVisualTest_private.key",
    "certificate":"certs/PowerBICustomVisualTest_public.crt",
    "pfx":"certs/PowerBICustomVisualTest_public.pfx",
    "port":"8080",
    "passphrase":"YOUR PASSPHRASE"
}
```
