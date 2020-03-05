---
title: Power BI サービスでページ分割されたレポートのパラメーターを表示する
description: この記事では、Power BI サービスでページ分割されたレポートのパラメーターを操作する方法を学びます。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: 50de63aed17d9fab695119d5c94fa4a5d9312702
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "74834588"
---
# <a name="view-parameters-for-paginated-reports-in-the-power-bi-service"></a>Power BI サービスでページ分割されたレポートのパラメーターを表示する

この記事では、Power BI サービスでページ分割されたレポートのパラメーターを操作する方法を学びます。  レポート パラメーターでは、レポート データをフィルター処理する手段が提供されます。 パラメーターでは使用可能な値の一覧が提供され、1 つまたは複数の値を選択できます。 一部のパラメーターには既定値があり、レポートを表示する前に値を選択する必要があります。  

パラメーターのあるレポートを表示すると、レポート ビューアーのツール バーに各パラメーターが表示されて、対話的に値を指定できます。 次の図では、**Buying Group**、**Location**、**From Date**、**To Date** の各パラメーターを含むレポートのパラメーター領域を示します。  

## <a name="parameters-pane-in-the-power-bi-service"></a>Power BI サービスの [パラメーター] ウィンドウ

![パラメーターがあるページ分割されたレポートを表示する](media/paginated-reports-view-parameters/power-bi-paginated-view-parameters.png)
  
1.  **[パラメーター] ウィンドウ**: レポート ビューアーのツール バーには、"必須" や、各パラメーターの既定値などのプロンプトが表示されます。    
  
2.  **Invoices From / To Date パラメーター**: 2 つのデータ パラメーターには既定値があります。 日付を変更するには、テキスト ボックスに日付を入力するか、またはカレンダーで日付を選択します。  
  
3.  **Location パラメーター**: Location パラメーターは、1 つ、複数、または全部の値を選択できるように設定されています。 
  
4.  **[レポートの表示]** : パラメーターの値を入力または変更した後、 **[レポートの表示]** をクリックしてレポートを実行します。 

5. **既定値**: すべてのパラメーターに既定値がある場合、レポートは最初に表示した時点で自動的に実行されます。 このレポートでは一部のパラメーターに既定値がないため、値を選択するまでレポートは表示されません。  

## <a name="next-steps"></a>次の手順

[Power BI サービスでのページ分割されたレポート](end-user-paginated-report.md)
