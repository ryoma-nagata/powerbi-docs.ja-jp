---
title: Power BI 用の資格情報をプログラムで構成する
description: Power BI 用の資格情報をプログラムで構成して自動化する方法
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: 222edd901409fa71d98308f27407838d54564834
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836593"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Power BI 用の資格情報をプログラムで構成する

以下の手順に従って、Power BI 用の資格情報をプログラムで構成します。

## <a name="configure-a-credential-flow-for-data-sources"></a>データ ソースの資格情報フローを構成する

1. [Get Datasources](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) を呼び出して、データセットのデータ ソースを検出します。 各データ ソースに対する応答本文には、種類、接続の詳細、ゲートウェイ、およびデータ ソース ID が含まれています。

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. [Update Datasource の例](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (資格情報の種類によって異なる) に従って、資格情報の文字列を作成します。

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. 資格情報の詳細を作成します。

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) を呼び出して資格情報を設定します。このとき、手順 1 のゲートウェイとデータ ソース ID、さらに手順 4 の資格情報の詳細を使用します。

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>有効期限切れになったオンプレミス データ ソース資格情報のフロー

1. [前のシナリオの手順 1 と手順 2 に従います](#configure-a-credential-flow-for-data-sources)。

2. [Get Gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) を呼び出して、ゲートウェイの公開キーを取得します。

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. ゲートウェイの公開キーを使用して、資格情報の文字列を暗号化します。 公開キーのサイズは、ゲートウェイのバージョンによって異なります。
    
    PowerBI-CSharp GitHub リポジトリにある [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2) の SDK コードの例を参照してください。
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)

4. 暗号化された資格情報を使用して資格情報の詳細を作成します。

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) を呼び出して資格情報を設定します。

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>データ ゲートウェイに対して新しいデータ ソースを構成する

1. ご利用のコンピューター上に[オンプレミス データ ゲートウェイ](https://powerbi.microsoft.com/gateway/)をインストールします。

2. [Get Gateways](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) を呼び出して、ゲートウェイ ID と公開キーを取得します。

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. 手順「[有効期限切れになったオンプレミス データ ソース資格情報のフロー](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway)」で取得したゲートウェイの公開キーを使用して、前のシナリオと同様に資格情報の詳細を作成します。

4. 要求本文を作成する

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

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>get data sources の呼び出し時にゲートウェイとデータ ソース ID が見つかりません

この問題は、データセットがゲートウェイにバインドされていないことを意味します。 新しいデータセットを作成すると、クラウド接続ごとに、資格情報を持たないデータ ソースがユーザーのクラウド ゲートウェイ上に自動的に作成されます。 このゲートウェイは、クラウド接続用の資格情報を格納するために使用されます。

データセットを作成したら、データセットと適切なゲートウェイとの間でバインディングが自動的に行われます。これには、すべての接続についてのデータ ソースの照合も含まれます。 このようなゲートウェイまたは複数の適切なゲートウェイが存在しない場合、自動バインディングは失敗します。

必要に応じて、不足しているオンプレミスのデータ ソースを作成し、[Bind To Gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway) を使用してデータセットをゲートウェイに手動でバインドします。

バインドすることが可能なゲートウェイを検出するには、[Discover Gateways](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways) を使用します。