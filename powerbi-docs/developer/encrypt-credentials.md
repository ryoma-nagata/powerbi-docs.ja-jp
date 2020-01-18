---
title: 資格情報を暗号化する
description: チュートリアル - オンプレミス ゲートウェイのデータソース用の資格情報を暗号化する
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836625"
---
# <a name="encrypt-credentials"></a>資格情報を暗号化する

[Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/) を使用して**エンタープライズ オンプレミス ゲートウェイ**で[データソースの作成](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource)または[データソースの更新](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)を呼び出すときは、ゲートウェイの公開キーを使用して資格情報の値を暗号化する必要があります。

.NET で資格情報を暗号化する方法については、下のコード例をご覧ください。

下の EncodeCredentials メソッドに渡す資格情報は、資格情報の種類に応じて、次のいずれかの形式にする必要があります。

**基本/Windows 資格情報**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**キー資格情報**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**OAuth2 資格情報**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**匿名資格情報**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**資格情報を暗号化する**

ゲートウェイの公開キーを使用して資格情報の値を暗号化します。 ゲートウェイのバージョンによって、公開キーのサイズは異なる場合があります。

PowerBI-CSharp GitHub リポジトリにある [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2) の SDK コードの例を参照してください。

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)