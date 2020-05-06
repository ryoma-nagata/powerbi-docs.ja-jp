---
ms.openlocfilehash: f22c12ec0ad5bd413f3658704132143c878df1aa
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799967"
---
**変数**の使用は、DAX 式の中でも強力な部分を占めています。

![](media/7-4-dax-expressions/dax-variables_1.png)

次の構文を使用して、DAX 式の任意の場所で変数を定義できます。

    VARNAME = RETURNEDVALUE

変数には、テーブル全体を含む任意のデータ型を指定できます。

DAX 式で変数を参照するたびに、Power BI は定義に従ってその値を再計算する必要があることに注意してください。 このため、関数内で変数を繰り返さないようにすることをお勧めします。

> ビデオ コンテンツは、[SQLBI 社の Alberto Ferrari 氏](https://www.sqlbi.com/learning-dax)のご厚意によるものです。
> 
> 

