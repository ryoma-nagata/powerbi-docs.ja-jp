---
title: サービス プリンシパルの概要
description: サービス プリンシパルの概要
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 8482278d9054228dedafb6bd1b37368f5a4b5dce
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315815"
---
サービス プリンシパルとは、Azure AD アプリケーションが Power BI サービスのコンテンツと API にアクセスできるようにするための認証方法です。

Azure Active Directory (Azure AD) アプリを作成すると、[サービス プリンシパル オブジェクト](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)が作成されます。 サービス プリンシパル オブジェクト (単に "*サービス プリンシパル*" とも呼ばれる) を使用することで、Azure AD はご利用のアプリの認証を行うことができます。 認証が完了すると、アプリは Azure AD テナント リソースにアクセスできるようになります。

認証を行うために、サービス プリンシパルでは、Azure AD アプリの "*アプリケーション ID*" と次のいずれかが使用されます。

* アプリケーション シークレット
* 証明書