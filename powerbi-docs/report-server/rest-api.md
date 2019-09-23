---
title: Power BI Report Server 用の REST API を使って開発する
description: REST API を使うと、Power BI Report Server カタログ内のオブジェクトにプログラムでアクセスできます。
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: 8f35b7a3c19751b4537a49fa8cb30f4347f080ed
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770748"
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>Power BI Report Server 用の REST API を使って開発する

Power BI Report Server は、Representational State Transfer (REST) API をサポートします。 REST API は、一連の HTTP 操作 (メソッド) をサポートするサービス エンドポイントであり、レポート サーバー内のリソースに対する作成、取得、更新、削除アクセスを提供します。

REST API を使うと、Power BI Report Server カタログ内のオブジェクトにプログラムでアクセスできます。 オブジェクトの例としては、フォルダー、レポート、KPI、データ ソース、データセット、更新計画、サブスクリプションなどがあります。 REST API を使うと、たとえば、フォルダー階層内の移動、フォルダーの内容の検出、レポート定義のダウンロードなどを行うことができます。 オブジェクトを作成、更新、削除することもできます。 オブジェクトの操作の例は、レポートのアップロード、更新計画の実行、フォルダーの削除などです。

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>REST API の要求/応答のコンポーネント

REST API の要求/応答ペアは、5 つのコンポーネントに分けることができます。

* **要求 URI**。`{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}` で構成されます。 要求 URI は要求メッセージ ヘッダーに含まれていますが、ほとんどの言語やフレームワークでは要求メッセージとは別に渡す必要があるため、ここでは独立した項目にしてあります。
  
  * URI スキーム:要求の送信に使われるプロトコルを示します。 たとえば、`http` や `https` などです。
  * URI ホスト:REST サービス エンドポイントがホストされているサーバーのドメイン名または IP アドレスを指定します。たとえば、`myserver.contoso.com` などです。
  * リソース パス:リソースまたはリソース コレクションを指定します。リソースの選択を決定するときにサービスによって使われる複数のセグメントを含むことができます。 たとえば、`CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` を使って、CatalogItem の指定したプロパティを取得できます。
  * クエリ文字列 (省略可能):API のバージョンやリソースの選択条件など、簡単な追加パラメーターを提供します。
* HTTP 要求メッセージ ヘッダーのフィールド:
  
  * 必須の [HTTP メソッド](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (操作または動詞とも呼ばれます)。要求する操作の種類をサービスに通知します。 Reporting Services REST API は、DELETE、GET、HEAD、PUT、POST、PATCH の各メソッドをサポートします。
  * 省略可能な追加ヘッダー フィールド。指定されている URI および HTTP メソッドで必要な場合があります。
* 省略可能な HTTP **要求メッセージ本文**のフィールド。URI および HTTP 操作をサポートするためのフィールドです。 たとえば、POST 操作には、複雑なパラメーターとして渡される、MIME でエンコードされたオブジェクトが含まれます。 POST または PUT 操作の場合、本文の MIME エンコードの種類を、`Content-type` 要求ヘッダーでも指定する必要があります。 一部のサービスでは、`application/json` などの特定の MIME の種類を使う必要があります。
* HTTP **応答メッセージ ヘッダー**のフィールド:
  
  * [HTTP 状態コード](http://www.w3.org/Protocols/HTTP/HTRESP.html)。成功コードの 2xx から、エラー コードの 4xx または 5xx までの範囲です。 または、API のドキュメントに記載されているように、サービスで定義された状態コードが返されることもあります。
  * 省略可能な追加ヘッダー フィールド。要求の応答をサポートするために必要です (`Content-type` 応答ヘッダーなど)。
* 省略可能な HTTP **応答メッセージ本文**のフィールド。
  
  * MIME でエンコードされた応答オブジェクトが HTTP 応答の本文で返されます (データを返す GET メソッドからの応答など)。 通常、これらのオブジェクトは、`Content-type` 応答ヘッダーによって示される、JSON や XML などの構造化された形式で返されます。

## <a name="api-documentation"></a>API のドキュメント

最新の REST API には最新の API ドキュメントが必要です。 REST API は OpenAPI 仕様 ( Swagger 仕様とも呼ばれます) に基づいて構築されており、ドキュメントは [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) で入手できます。 SwaggerHub は、API のドキュメントだけでなく、JavaScript、TypeScript、C#, Java、Python、Ruby などの言語でのクライアント ライブラリの生成にも役立ちます。

## <a name="testing-api-calls"></a>API 呼び出しのテスト

HTTP 要求/応答メッセージをテストするためのツールは [Fiddler](http://www.telerik.com/fiddler) です。 Fiddler は、REST 要求をインターセプトできる無料の Web デバッグ プロキシであり、HTTP 要求/応答メッセージの診断が容易になります。

## <a name="next-steps"></a>次の手順

[SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0) で利用可能な API を確認してください。

サンプルは [GitHub](https://github.com/Microsoft/Reporting-Services) で入手できます。 このサンプルには、TypeScript、React、webpack で構築された HTML5 アプリと、PowerShell の例が含まれます。

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。