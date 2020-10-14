---
title: サービス プリンシパルの概要
description: サービス プリンシパルの概要
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 6086185fb671b9f418ef2ec070b762020fbe8f75
ms.sourcegitcommit: 02484b2d7a352e96213353702d60c21e8c07c6c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/13/2020
ms.locfileid: "91989767"
---
サービス プリンシパルとは、Azure AD アプリケーションが Power BI サービスのコンテンツと API にアクセスできるようにするための認証方法です。

Azure Active Directory (Azure AD) アプリを作成すると、[サービス プリンシパル オブジェクト](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)が作成されます。 サービス プリンシパル オブジェクト (単に "*サービス プリンシパル*" とも呼ばれる) を使用することで、Azure AD はご利用のアプリの認証を行うことができます。 認証が完了すると、アプリは Azure AD テナント リソースにアクセスできるようになります。

認証を行うために、サービス プリンシパルでは、Azure AD アプリの "*アプリケーション ID*" と次のいずれかが使用されます。

* アプリケーション シークレット
* 証明書