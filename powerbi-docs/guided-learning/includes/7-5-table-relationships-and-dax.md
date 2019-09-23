---
ms.openlocfilehash: cd6ea6fd52f929e2cd254214cf0e8c96e858f6c2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "61273638"
---
Power BI では、まったく異なるデータ ソースから取得したテーブルなど、複数のテーブル間にリレーションシップを作成することができます。 任意のデータ モデルにおけるこのようなリレーションシップは、Power BI Desktop の **[リレーションシップ]** ビューで確認できます。

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>DAX のリレーショナル関数
DAX には、リレーションシップが確立されたテーブルと対話するのに便利な**リレーショナル関数**が備わっています。

DAX 関数を使用して、列の値を返したり、リレーションシップを保っているすべての行を返したりすることができます。

たとえば、**RELATED** 関数は、リレーションシップに従って列の値を返します。**RELATEDTABLE** は、リレーションシップに従い、関連する行のみを含むようにフィルター処理されたテーブル全体を返します。

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

**RELATED** 関数は*多対一*のリレーションシップで、**RELATEDTABLE** 関数は*一対多*のリレーションシップで機能します。

リレーショナル関数を使用すると、複数のテーブルにまたがる値を含む式を構築できます。 DAX では、リレーションシップのチェーンの長さに関係なく、これらの関数の結果を返します。

> ビデオ コンテンツは、[SQLBI 社の Alberto Ferrari 氏](http://www.sqlbi.com/learning-dax)のご厚意によるものです。
> 
> 

