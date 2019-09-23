---
title: Power BI REST API の制限事項
description: Power BI REST API には、次のような制限があります
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 6699167cecebea5085eff4621c077096fd4c6c2e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61385145"
---
# <a name="power-bi-rest-api-limitations"></a>Power BI REST API の制限事項  
  
**行を POST するには**
  
* 列数の上限は 75
* テーブル数の上限は 75
* 1 つの「行の POST」要求の最大行数は 10,000 行  
* 1 つのデータセットの 1 時間あたりの追加行数は 1,000,000 行  
* 1 つのデータセットの保留の「行の POST」要求の数は 5 つまで  
* 1 つのデータセットの「行の POST」要求数は 1 分間あたり 120 個
* テーブルの行数が 250,000 以上の場合は、1 つのデータセットの「行の POST」要求数は 1 時間あたり 120 個
* FIFO データセット内の 1 テーブルごとに保存される最大行数は 200,000 行
* 「保持ポリシーなし」のデータセット内の 1 テーブルごとに保存される最大行数は 5,000,000 行  
* 行の POST 操作における文字列型の列の値 1 つあたりの最大文字数は 4,000 文字
  
## <a name="see-also"></a>参照

[Azure AD サービスの制限と制約](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[Power BI REST API の概要](https://docs.microsoft.com/rest/api/power-bi/)