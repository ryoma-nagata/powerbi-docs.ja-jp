---
title: Power BI Desktop ビジュアルでのデータの確認とレコードの確認
description: Power BI Desktop のデータの確認機能とレコードの確認機能を使用して、詳細情報にドリルダウンします
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 6e425f146228d0139b9eec914a44ed5dc732fe98
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514765"
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>Power BI Desktop のデータの確認とレコードの確認を使用する
**Power BI Desktop** では、視覚エフェクトの詳細にドリルダウンして、基になるデータのテキスト表現または選択したビジュアルの個々のデータ レコードを見ることができます。 これらの機能は、"*クリックスルー*"、"*ドリルスルー*"、"*詳細情報へのドリルスルー*" などとも呼ばれます。

**[データの確認]** を使うと選択した視覚エフェクトで使われている値のテキスト版を表示でき、 **[レコードの確認]** を使うと選択した 1 つのレコードまたはデータ ポイントのすべてのデータを表示できます。 

![[データの確認] と [レコードの確認]](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>**[データの確認]**  と **[レコードの確認]** では、次の視覚エフェクトの種類のみがサポートされます。
>  - 横棒グラフ
>  - 縦棒グラフ
>  - ドーナツ グラフ
>  - 塗り分け地図
>  - じょうごグラフ
>  - マップ
>  - 円グラフ
>  - ツリーマップ

## <a name="use-see-data-in-power-bi-desktop"></a>Power BI Desktop での [データの確認] の使用

**[データの確認]** では、視覚エフェクトの基になるデータが表示されます。 **[データの確認]** は、視覚エフェクトを選択したときにリボンの **[ビジュアル ツール]** セクションの **[データ/ドリル]** タブに表示されます。

![リボンの [データの確認]](media/desktop-see-data-see-records/see-data1.png)

データは、視覚エフェクトを右クリックし、表示されるメニューから **[データの表示]** を選択するか、視覚エフェクトの右上隅で **その他のオプション**の省略記号 (...) を選択し、 **[データの表示]** を選択することでも表示できます。

![右クリックの [データの表示]](media/desktop-see-data-see-records/see-data2.png)&nbsp;&nbsp;![その他のオプションの [データの表示]](media/desktop-see-data-see-records/see-data3.png)

> [!NOTE]
> 右クリック メニューを使うには、ビジュアル内のデータ ポイントの上にマウス ポインターを移動する必要があります。

**[データの確認]** または **[データの表示]** を選択すると、Power BI Desktop キャンバスに、データのビジュアル表現とテキスト表現の両方が表示されます。 "*横表示*" では、ビジュアルがキャンバスの上部に表示され、データが下部に表示されます。 

![横表示](media/desktop-see-data-see-records/see-data4a.png)

キャンバスの右上隅のアイコンを選ぶことで、横表示と "*縦表示*" の間を切り替えることができます。

![縦表示の切り替え](media/desktop-see-data-see-records/see-data4.png)

レポートに戻るには、キャンバスの左上隅にある **[< レポートに戻る]** を選びます。

![レポートに戻る](media/desktop-see-data-see-records/see-data5.png)

## <a name="use-see-records-in-power-bi-desktop"></a>Power BI Desktop での [レコードの確認] の使用

視覚エフェクト内の 1 つのデータ レコードに注目して、その背後にあるデータにドリルダウンできます。 **[レコードの確認]** を使用するには、視覚エフェクトを選択し、リボンの **[ビジュアル ツール]** セクションの **[データ/ドリル]** タブで **[レコードの確認]** を選択し、視覚エフェクト上のデータ ポイントまたは行を選択します。 

![リボンの [レコードの確認]](media/desktop-see-data-see-records/see-record1.png)

> [!NOTE]
> リボンで **[レコードの確認]** が無効になってグレー表示されている場合は、選択した視覚エフェクトで **[レコードの確認]** がサポートされていないことを意味します。

データ要素を右クリックし、表示されるメニューから **[レコードの確認]** を選択することもできます。

![右クリックによる [レコードの確認]](media/desktop-see-data-see-records/see-record2.png)

データ要素に対して **[レコードの確認]** を選択すると、Power BI Desktop キャンバスに、選択した要素に関連付けられているすべてのデータが表示されます。 

![](media/desktop-see-data-see-records/see-record3.png)

レポートに戻るには、キャンバスの左上隅にある **[< レポートに戻る]** を選びます。

![](media/desktop-see-data-see-records/see-record4.png)

> [!NOTE]
>**[レコードの確認]** には次の制限事項があります。
> - **[レコードの確認]** ビュー内のデータを変更してレポートに保存することはできません。
> - 計算されるメジャーがビジュアルで使われている場合は、 **[レコードの確認]** を使用できません。
> - ライブ多次元 (MD) モデルに接続されている場合は、 **[レコードの確認]** を使用できません。

## <a name="next-steps"></a>次の手順
**Power BI Desktop** には、あらゆる種類のレポートの書式指定とデータ管理機能があります。 例については、次のリソースをご覧ください。

* [Power BI Desktop でグループ化とビン分割を使用する](desktop-grouping-and-binning.md)
* [Power BI Desktop レポートで、グリッド線、グリッドへのスナップ、重ね順、配置、および分布を使用する](desktop-gridlines-snap-to-grid.md)

