---
title: ビジュアルの相互作用
description: Power BI ビジュアルでビジュアルの相互作用を許可する必要があることを確認する方法
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 739e59c6da3c1e464e0462a928bc4f33ea0d01f8
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68424495"
---
# <a name="visuals-interactions"></a>ビジュアルの相互作用

ビジュアルでは、"allowInteractions" フラグの値にクエリを実行できます。このフラグは、ビジュアルでビジュアルの相互作用を許可する必要があるかどうかを示します。
たとえば、ビジュアルはレポートの表示や編集の間、インタラクティブになりますが、ダッシュボードで表示されるときはインタラクティブになりません。
このようなは相互作用には、クリック、パン、ズーム、選択などがあります。
このフラグに関係なく、あらゆるシナリオにおいてツールヒントを有効にする必要があることにご留意ください。

"allowInteractions" フラグは (IVisualHost インターフェイスのメンバーとしての) ビジュアルの初期化中、ブール値として渡されます。

Power BI でビジュアルのインタラクティブ性が求められない場合 (ダッシュボード タイルなど)、"allowInteractions" フラグは false に設定されます。
それ以外の場合 (レポートなど)、"allowInteractions" フラグは true に設定されます。

詳細は、「[SampleBarChart ビジュアル リポジトリ](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/59a47935d8f5272ce145fe804193599ddb7e2001)」を参照してください。

```typescript
   ...
   let allowInteractions = options.host.allowInteractions;
   bars.on('click', function(d) {
       if (allowInteractions) {
           selectionManager.select(d.selectionId);
           ...
       }
   });
```
