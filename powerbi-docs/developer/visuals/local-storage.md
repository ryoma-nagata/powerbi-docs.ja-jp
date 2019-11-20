---
title: Power BI ビジュアルのローカル ストレージ API
description: この記事では、Power BI ビジュアル API を使用してブラウザーのローカル ストレージにアクセスする方法について説明します
author: uve
ms.author: v-grniki
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 10/31/2019
ms.openlocfilehash: f69a3c8928b8079f79b8a6dd5f5b132235a7089c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879881"
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

既定では、ローカル ストレージ API はカスタム ビジュアルに対してアクティブにされません。 カスタム ビジュアルに対してアクティブにする場合は、要求を Power BI カスタム ビジュアル サポート (`pbicvsupport@microsoft.com`) に送信してください
