---
ms.openlocfilehash: 5c2b254f20bd1eba97840a464a1b554cc4fe1238
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273590"
---
**変数**の使用は、DAX 式の中でも強力な部分を占めています。

![](media/7-4-dax-expressions/dax-variables_1.png)

次の構文を使用して、DAX 式の任意の場所で変数を定義できます。

    VARNAME = RETURNEDVALUE

変数には、テーブル全体を含む任意のデータ型を指定できます。

DAX 式で変数を参照するたびに、Power BI は定義に従ってその値を再計算する必要があることに注意してください。 このため、関数内で変数を繰り返さないようにすることをお勧めします。

> ビデオ コンテンツは、[SQLBI 社の Alberto Ferrari 氏](http://www.sqlbi.com/learning-dax)のご厚意によるものです。
> 
> 

