---
title: 管理者が Power BI Desktop のサインイン フォームを管理する方法
description: Power BI Desktop を開いたときの最初のサインイン フォームを管理する方法について説明します。
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: 49b7d1129f73e146db1e34b1ec7d39a176cb37ed
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85228904"
---
# <a name="administrators-manage-the-power-bi-desktop-sign-in-form"></a>管理者:Power BI Desktop のサインイン フォームを管理する
Power BI Desktop を初めて起動したときは、サインイン フォームが表示されます。 情報を入力するか、Power BI にサインインして続行できます。 管理者は、レジストリ キーを使ってこのフォームを管理します。 

![Power BI Desktop の初回サインイン フォーム](media/desktop-admin-sign-in-form/sign-in-form.png)

管理者は、次のレジストリ キーを使って、サインイン フォームを無効にします。 グローバル ポリシーを使って、これを組織全体に適用することもできます。

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
次のキーを試すこともできます。これは、構成に基づいて一部の顧客に対して成功しています。

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

値を 0 にすると、ダイアログ ボックスは無効になります。




他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。

