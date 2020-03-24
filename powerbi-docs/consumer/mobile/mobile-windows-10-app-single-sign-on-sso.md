---
title: Power BI モバイルの Windows アプリでのシングル サインオン
description: Power BI モバイルの Windows アプリでのシングル サインオン (SSO) について確認します。 SSO は、1 つのユーザー アカウントで 1 回だけサインインすることにより、ビジネスを行うのに必要なすべてのアプリケーションとリソースにアクセスできることを意味します。
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: e9156e539ee9f1a344b89f7814c148829498e5fc
ms.sourcegitcommit: abc8419155dd869096368ba744883b865c5329fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2020
ms.locfileid: "79435929"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Power BI モバイルの Windows アプリでのシングル サインオン

Power BI モバイルの Windows アプリでのシングル サインオン (SSO) について確認します。 SSO は、1 つのユーザー アカウントで 1 回だけサインインすることにより、ビジネスを行うのに必要なすべてのアプリケーションとリソースにアクセスできることを意味します。 一度サインインすると、もう一度認証することなく、それらすべてのアプリケーションにアクセスできます。 

Power BI Windows アプリは Azure Active Directory に統合されているため、プライマリ組織アカウントを使用して、ドメインに参加しているデバイスにサインインするだけでなく、Power BI サービスにもサインインすることができます。 Windows Phone 上で Power BI を表示している場合、Power BI に使用するアカウントが、デバイスの設定で職場または学校のアカウントとして構成されていることを確認してください。  

SSO は、Windows Azure Active Directory で管理されている Windows デバイスに対してのみ有効です。

>[!NOTE]
>**Windows 10 Mobile を使用するスマートフォン**に対する Power BI モバイル アプリのサポートは、2021 年 3 月 16 日に廃止されます。 [詳細情報](https://go.microsoft.com/fwlink/?linkid=2121400)

## <a name="sign-in-with-sso"></a>SSO でのサインイン

サインイン プロセスを単純化するには、最初にアプリをインストールするときに、アプリによって自動的に SSO を使用して Power BI サービスに対してお客様を認証しようとします。 このプロセスが成功しなかった場合のみ、Power BI に対するお客様の資格情報を提供するようにアプリから求められます。  

既に Windows 用の Power BI モバイル アプリを使用している場合は、そのアプリの新しいバージョンにアップグレードするときに、SSO を使用することもできます。 アプリからサインアウトし、閉じてからもう一度開きます。 アプリがもう一度開くと、現在の Windows の資格情報を自動的に使用し、Power BI サービスに対して認証しようとします。 

Power BI にサインインする現在の Windows アクティブ セッションの資格情報を使用する必要がない場合、単に **[設定]** に移動し、サインアウトして異なる資格情報でサインインします。 
 
## <a name="next-steps"></a>次の手順

- [Windows 10 用の Power BI モバイル アプリの概要](mobile-windows-10-phone-app-get-started.md)
- わからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。

