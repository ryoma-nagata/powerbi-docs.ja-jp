---
title: Power BI ビジュアルのローカル ストレージ API
description: この記事では、Power BI ビジュアル API を使用してブラウザーのローカル ストレージにアクセスする方法について説明します
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/21/2019
ms.openlocfilehash: 7665f0c8e3c909263f194a0fd54a54ed2a752c8c
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819102"
---
# <a name="local-storage-api"></a>ローカル ストレージ API

ローカル ストレージ API は、デバイス ストレージのデータの保存または読み込みをホストに要求するために、カスタム ビジュアルが使用できる API です。 ビジュアルの種類ごとにストレージ アクセスが分けられているという意味で、分離されています。

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

既定では、ローカル ストレージ API はカスタム ビジュアルに対してアクティブにされません。 カスタム ビジュアルに対してアクティブにする場合は、要求を Power BI カスタム ビジュアル サポート (`pbicvsupport@microsoft.com`) に送信してください。  
**ビジュアルが [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) で利用可能であり、[認定されている](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/)必要があることに注意してください。**
