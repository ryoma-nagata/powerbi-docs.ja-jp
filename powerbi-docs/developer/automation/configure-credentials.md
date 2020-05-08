---
title: Power BI 用の資格情報をプログラムで構成する
description: Power BI を自動化する場合に資格情報をプログラムで構成する方法
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/23/2020
ms.openlocfilehash: bd7758be32d18fd3be06a7847edc7795c2b5f9e1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114775"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Power BI 用の資格情報をプログラムで構成する

以下の手順に従って、Power BI 用の資格情報をプログラムで構成します。

## <a name="update-credentials-flow-for-data-sources"></a>データ ソースの資格情報フローを更新する

1. [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) を呼び出して、データセットのデータ ソースを検出します。 各データ ソースの応答本文には、種類、接続の詳細、ゲートウェイ、およびデータ ソース ID が含まれています。

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. [Update Datasource の例](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (資格情報の種類によって異なる) に従って、資格情報の文字列を作成します。

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) を呼び出して、ゲートウェイの公開キーを取得します。

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. 資格情報を暗号化します。

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    手順 2 で取得したゲートウェイの公開キーを使用して、資格情報の文字列を暗号化します。 ゲートウェイのバージョンによって、公開キーのサイズは異なる場合があります。 SDK コードに含まれている以下の例を参照してください。これは [PowerBI-CSharp GitHub リポジトリ](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions)から入手できます。
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. 暗号化された資格情報を使用して資格情報の詳細を作成します。

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    **手順 3** で取得した公開キーを指定して AssymetricKeyEncriptor クラスを使用します。

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) を呼び出して資格情報を設定します。

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>データ ゲートウェイに対して新しいデータ ソースを構成する

1. ご利用のコンピューター上に[オンプレミス データ ゲートウェイ](https://powerbi.microsoft.com/gateway/)をインストールします。

2. [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) を呼び出して、ゲートウェイ ID と公開キーを取得します。

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. [手順 2](#update-credentials-flow-for-data-sources) で取得したゲートウェイの公開キーを使用して、「**データ ソースの資格情報フローを更新する**」で説明されているのと同じ方法で資格情報の詳細を作成します。

4. 要求本文を作成します。

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) API を呼び出します。

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>資格情報の種類

[Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) を使用して[エンタープライズ オンプレミス ゲートウェイ](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource)で**データソースの作成**または[データソースの更新](https://docs.microsoft.com/rest/api/power-bi/)を呼び出すときは、ゲートウェイの公開キーを使用して資格情報の値を暗号化する必要があります。

>[!NOTE]
>.NET SDK v3 では、以下に示す .NET SDK v2 の例も実行できます。

### <a name="windows-and-basic-credentials"></a>Windows 資格情報と基本資格情報

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>キー資格情報

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**OAuth2 資格情報**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**匿名資格情報**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>get data sources の呼び出し時にゲートウェイとデータ ソース ID が見つかりません

この問題は、データセットがゲートウェイにバインドされていないことを意味します。 新しいデータセットを作成すると、クラウド接続ごとに、資格情報を持たないデータ ソースがユーザーのクラウド ゲートウェイ上に自動的に作成されます。 このゲートウェイは、クラウド接続用の資格情報を格納するために使用されます。

データセットを作成したら、データセットと適切なゲートウェイとの間でバインドが自動的に作成されます。これには、すべての接続についてのデータ ソースの照合も含まれます。 このようなゲートウェイまたは複数の適切なゲートウェイが存在しない場合、自動バインディングは失敗します。

オンプレミスのデータセットを使用している場合は、不足しているオンプレミスのデータ ソースを作成し、[Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) を使用してデータセットをゲートウェイに手動でバインドします。

バインドすることが可能なゲートウェイを検出するには、[Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) を使用します。