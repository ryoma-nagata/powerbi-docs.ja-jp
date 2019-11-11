---
title: 資格情報を暗号化する
description: チュートリアル - オンプレミス ゲートウェイのデータソース用の資格情報を暗号化する
author: mahirdiab
ms.author: madia
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/04/2019
ms.openlocfilehash: 4747d548f8b02806c1e7b1359d140b09039e09d8
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73863844"
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

```csharp
public static class AsymmetricKeyEncryptionHelper
{

    private const int SegmentLength = 85;
    private const int EncryptedLength = 128;

    public static string EncodeCredentials(string credentials, string publicKeyExponent, string publicKeyModulus)
    {
        using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
        {
            var parameters = rsa.ExportParameters(false);
            parameters.Exponent = Convert.FromBase64String(publicKeyExponent);
            parameters.Modulus = Convert.FromBase64String(publicKeyModulus);
            rsa.ImportParameters(parameters);
            return Encrypt(credentials, rsa);
        }
    }

    private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
    {
        byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

        // Split the message into different segments, each segment's length is 85. So the result may be 85,85,85,20.
        bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0;

        int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length / SegmentLength) + 1);

        byte[] encryptedData = new byte[segmentNumber * EncryptedLength];
        int encryptedDataPosition = 0;

        for (var i = 0; i < segmentNumber; i++)
        {
            int lengthToCopy;

            if (i == segmentNumber - 1 && hasIncompleteSegment)
                lengthToCopy = plainTextArray.Length % SegmentLength;
            else
                lengthToCopy = SegmentLength;

            var segment = new byte[lengthToCopy];

            Array.Copy(plainTextArray, i * SegmentLength, segment, 0, lengthToCopy);

            var segmentEncryptedResult = rsa.Encrypt(segment, true);

            Array.Copy(segmentEncryptedResult, 0, encryptedData, encryptedDataPosition, segmentEncryptedResult.Length);

            encryptedDataPosition += segmentEncryptedResult.Length;
        }

        return Convert.ToBase64String(encryptedData);
    }
}
```