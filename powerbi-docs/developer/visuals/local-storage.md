---
title: Power BI ビジュアルのローカル ストレージ API
description: この記事では、Power BI ビジュアル API を使用してブラウザーのローカル ストレージにアクセスする方法について説明します
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 01/21/2019
ms.openlocfilehash: e2cb11ea9be85916e6b5557e7933f6a6b5a7159a
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79380596"
---
# <a name="local-storage-api"></a>ローカル ストレージ API

ローカル ストレージ API は、デバイスのストレージにおけるデータの保存または読み込みをホストに要求するために、カスタム ビジュアルで使用できる API です。 ビジュアルの種類ごとにストレージ アクセスが分けられているという意味で、分離されています。

## <a name="sample"></a>サンプル

更新メソッドが呼び出されるたびにカスタム ビジュアルがカウンターを増やす必要があっても、カウンター値を保持し、ビジュアルの開始ごとにリセットしないようにする必要がある場合は、次のようにします。

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>既知の制限事項と問題

既定では、ローカル ストレージ API は Power BI ビジュアルに対してアクティブにされません。 Power BI ビジュアルに対してアクティブにする場合は、要求を Power BI ビジュアル サポート (`pbicvsupport@microsoft.com`) に送信します。  
**ビジュアルが [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) で利用可能であり、[認定されている](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/)必要があることに注意してください。**
