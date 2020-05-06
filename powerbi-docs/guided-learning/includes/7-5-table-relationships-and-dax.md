---
ms.openlocfilehash: 679c3e8c3d94c93899e9dcfae1e57f4b678fb218
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "73799963"
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

> ビデオ コンテンツは、[SQLBI 社の Alberto Ferrari 氏](https://www.sqlbi.com/learning-dax)のご厚意によるものです。
> 
> 

