---
title: 行を追加するためにデータセットを取得する
description: データをプッシュするチュートリアル - Power BI テーブルに行を追加するためにデータセットを取得する
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/05/2019
ms.openlocfilehash: f7dc84c9c6c84a30417d97f37d984b5f01ec9cd7
ms.sourcegitcommit: 3e72c6d564d930304886d51cdf12b8fc166aa33c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2019
ms.locfileid: "67596471"
---
# <a name="step-4-get-a-dataset-to-add-rows-into-a-power-bi-table"></a>手順 4:Power BI テーブルに行を追加するためにデータセットを取得する

この記事は、チュートリアル「[データセットにデータをプッシュする](walkthrough-push-data.md)」の一部です。

チュートリアル「データセットにデータをプッシュする」の**手順 3**「[Power BI でデータセットを作成する](walkthrough-push-data-create-dataset.md)」では、[データセットの作成](https://docs.microsoft.com/rest/api/power-bi/datasets)操作を呼び出して Power BI でデータセットを作成しました。 この手順では、[データセットの取得](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)操作と Newtonsoft.Json を使ってデータセット ID を取得します。データセットに行を追加するには、手順 4 で取得したデータセット ID を使います。 

Power BI データセットにデータをプッシュするには、データセット内のテーブルを参照する必要があります。 データセット内のテーブルを参照するには、まず **データセット ID**を取得する必要があります。 **データセット ID** は、[データセットの取得](/rest/api/power-bi/datasets/getdatasets)操作を使って取得します。 **データセットの取得**操作では、Power BI 内にあるすべてのデータセットのリストを含む JSON 文字列が返されます。 JSON 文字列を逆シリアル化するには、[Newtonsoft.Json](http://www.newtonsoft.com/json) を使うことをお勧めします。

データセットを取得する方法は次のとおりです。

## <a name="get-a-power-bi-dataset"></a>Power BI データセットを取得する

> **注**:作業を開始する前に、チュートリアル「[データセットにデータをプッシュする](walkthrough-push-data.md)」の前の手順を完了してください。

1. データをプッシュするチュートリアルの手順 2:「[認証アクセス トークンを取得する](walkthrough-push-data-get-token.md)」で作成したコンソール アプリケーション プロジェクトに、Newtonsoft.Json NuGet パッケージをインストールします。 パッケージをインストールする方法を次に示します。

     a. Visual Studio 2015 で、 **[ツール]**  >  **[NuGet パッケージ マネージャー]**  >  **[パッケージ マネージャー コンソール]** を選びます。

     b. **[パッケージ マネージャー コンソール]** で、「Install-Package Newtonsoft.Json」と入力します。
2. パッケージをインストールした後、「 **using Newtonsoft.Json;** 」を Program.cs に追加します。
3. Program.cs に、 **データセット ID**を取得するために以下のコードを追加します。
4. コンソール アプリを実行し、Power BI アカウントにログインします。 コンソール ウィンドウに、 **Dataset ID:** の後に ID が表示されるはずです。

**データセットの取得のサンプル**

このコードを Program.cs に追加します。

* static void Main(string[] args) では、以下のように入力します。
  
  ```csharp
  static void Main(string[] args)
  {
  
    //Get an authentication access token
    token = GetToken();
  
    //Create a dataset in Power BI
    CreateDataset();
  
    //Get a dataset to add rows into a Power BI table
    string datasetId = GetDataset();
  }
  ```
* GetDatset() メソッドを追加します。
  
  ```csharp
    #region Get a dataset to add rows into a Power BI table
    private static string GetDataset()
    {
        string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
        //POST web request to create a dataset.
        //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
        HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
        request.KeepAlive = true;
        request.Method = "GET";
        request.ContentLength = 0;
        request.ContentType = "application/json";
  
        //Add token to the request header
        request.Headers.Add("Authorization", String.Format("Bearer {0}", token));
  
        string datasetId = string.Empty;
        //Get HttpWebResponse from GET request
        using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
        {
            //Get StreamReader that holds the response stream
            using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
            {
                string responseContent = reader.ReadToEnd();
  
                //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                //and add using Newtonsoft.Json
                var results = JsonConvert.DeserializeObject<dynamic>(responseContent);
  
                //Get the first id
                datasetId = results["value"][0]["id"];
  
                Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                Console.ReadLine();
  
                return datasetId;
            }
        }
    }
    #endregion
  ```

次の手順では、[Power BI テーブルに行を追加する](walkthrough-push-data-add-rows.md)方法を説明します。

以下は、[完全なコード リスト](#code)です。

<a name="code"/>

## <a name="complete-code-listing"></a>完全なコード リスト

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System.Net;
using System.IO;
using Newtonsoft.Json;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

            //Create a dataset in Power BI
            CreateDataset();

            //Get a dataset to add rows into a Power BI table
            string datasetId = GetDataset();

        }

        #region Get an authentication access token
        private static string GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            string token = authContext.AcquireToken(resourceUri, clientID, new Uri(redirectUri)).AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

        #region Create a dataset in Power BI
        private static void CreateDataset()
        {
            //TODO: Add using System.Net and using System.IO

            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "POST";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            //Create dataset JSON for POST request
            string datasetJson = "{\"name\": \"SalesMarketing\", \"tables\": " +
                "[{\"name\": \"Product\", \"columns\": " +
                "[{ \"name\": \"ProductID\", \"dataType\": \"Int64\"}, " +
                "{ \"name\": \"Name\", \"dataType\": \"string\"}, " +
                "{ \"name\": \"Category\", \"dataType\": \"string\"}," +
                "{ \"name\": \"IsCompete\", \"dataType\": \"bool\"}," +
                "{ \"name\": \"ManufacturedOn\", \"dataType\": \"DateTime\"}" +
                "]}]}";

            //POST web request
            byte[] byteArray = System.Text.Encoding.UTF8.GetBytes(datasetJson);
            request.ContentLength = byteArray.Length;

            //Write JSON byte[] into a Stream
            using (Stream writer = request.GetRequestStream())
            {
                writer.Write(byteArray, 0, byteArray.Length);

                var response = (HttpWebResponse)request.GetResponse();

                Console.WriteLine(string.Format("Dataset {0}", response.StatusCode.ToString()));

                Console.ReadLine();
            }
        }
        #endregion

        #region Get a dataset to add rows into a Power BI table
        private static string GetDataset()
        {
            string powerBIDatasetsApiUrl = "https://api.powerbi.com/v1.0/myorg/datasets";
            //POST web request to create a dataset.
            //To create a Dataset in a group, use the Groups uri: https://api.PowerBI.com/v1.0/myorg/groups/{group_id}/datasets
            HttpWebRequest request = System.Net.WebRequest.Create(powerBIDatasetsApiUrl) as System.Net.HttpWebRequest;
            request.KeepAlive = true;
            request.Method = "GET";
            request.ContentLength = 0;
            request.ContentType = "application/json";

            //Add token to the request header
            request.Headers.Add("Authorization", String.Format("Bearer {0}", token));

            string datasetId = string.Empty;
            //Get HttpWebResponse from GET request
            using (HttpWebResponse httpResponse = request.GetResponse() as System.Net.HttpWebResponse)
            {
                //Get StreamReader that holds the response stream
                using (StreamReader reader = new System.IO.StreamReader(httpResponse.GetResponseStream()))
                {
                    string responseContent = reader.ReadToEnd();

                    //TODO: Install NuGet Newtonsoft.Json package: Install-Package Newtonsoft.Json
                    //and add using Newtonsoft.Json
                    var results = JsonConvert.DeserializeObject<dynamic>(responseContent);

                    //Get the first id
                    datasetId = results["value"][0]["id"];

                    Console.WriteLine(String.Format("Dataset ID: {0}", datasetId));
                    Console.ReadLine();

                    return datasetId;
                }
            }
        }
        #endregion
    }
}
```

[次の手順 >](walkthrough-push-data-add-rows.md)

## <a name="next-steps"></a>次の手順

[Power BI テーブルに行を追加する](walkthrough-push-data-add-rows.md)  
[Newtonsoft.Json](http://www.newtonsoft.com/json)  
[データセットの取得](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)  
[Power BI にデータをプッシュする](walkthrough-push-data.md)  
[Power BI REST API の概要](overview-of-power-bi-rest-api.md)  
[Power BI REST API リファレンス](https://docs.microsoft.com/rest/api/power-bi/)  

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。