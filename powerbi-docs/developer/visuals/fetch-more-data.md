---
title: より多くのデータをフェッチする
description: Power BI ビジュアルの大きいデータセットのセグメント化されたフェッチを有効にする
author: AviSander
ms.author: asander
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bc8ff673927fd66bf44164e4e9950c279b98c6c1
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425070"
---
# <a name="fetch-more-data-from-power-bi"></a>より多くのデータを Power BI からフェッチする

より多くのデータを読み込む API は、30 K のデータ ポイントというハードリミットを乗り越えます。 これはデータをチャンクで取り込みます。 チャンク サイズは、ユース ケースに従ってパフォーマンスを向上させるために構成できます。  

## <a name="enable-segmented-fetch-of-large-datasets"></a>大きいデータセットのセグメント化されたフェッチを有効にする

`dataview` セグメント モードでは、必要な dataViewMapping に対してビジュアルの `capabilities.json` 内の "window" dataReductionAlgorithm を定義します。
`count` はウィンドウ サイズを決定します。これにより、更新ごとに `dataview` に追加される新しいデータ行の数が制限されます。

capabilities.json に以下が追加されます

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

新しいセグメントが既存の `dataview` に追加され、`update` 呼び出しとしてビジュアルに提供されます。

## <a name="usage-in-the-custom-visual"></a>カスタム ビジュアルでの使用

データが存在するかどうかは、`dataView.metadata.segment` の存在を確認することによって判断できます。

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

また、`options.operationKind` をチェックすることで、それが最初の更新であるか、それとも後続の更新であるかを確認することもできます。

`VisualDataChangeOperationKind.Create` は最初のセグメントを意味し、`VisualDataChangeOperationKind.Append` は後続のセグメントを意味します。

実装の例については、次のコード スニペットを参照してください。

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subesquent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

`fetchMoreData` メソッドは UI イベント ハンドラーから呼び出すこともできます。

```typescript
btn_click(){
{
    // check if more data is expected for the current dataview
    if (dataView.metadata.segment) {
        //request for more data if available, as resopnce Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData();
        // handle rejection
        if (!request_accepted) {
            // for example when the 100 MB limit has been reached
        }
    }
}
```

Power BI は、`this.host.fetchMoreData` メソッドの呼び出しの応答として、新しいデータ セグメントを使用してビジュアルの `update` メソッドを呼び出します。

> [!NOTE]
> Power BI はクライアントのメモリ制約を回避するために、フェッチされるデータの合計を現時点では **100 MB** に制限しています。 fetchMoreData() で 'false' が返される場合、この制限に達していることが分かります。*
