---
title: ブックマーク
description: Power BI ビジュアルではブックマークの切り替えを処理できます
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 90e3fc73cd49a5c84a5c2acc68a8cf5e0e4aa42b
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425507"
---
# <a name="add-bookmarks-support-for-power-bi-visuals"></a>Power BI ビジュアルのブックマーク サポートを追加する

Power BI レポートのブックマークを使用すると、レポート ページの構成済みビュー、ビジュアルの選択の状態、フィルター処理の状態をキャプチャできます。 しかし、ブックマークをサポートし、変更に適切に対応するには、カスタム ビジュアル側からの追加のアクションが必要です。

ブックマークの詳細については、[こちらのドキュメント](https://docs.microsoft.com/power-bi/desktop-bookmarks)を参照してください

## <a name="report-bookmarks-support-in-your-visual"></a>ビジュアルでのレポート ブックマークのサポート

自分のビジュアルで他のビジュアルとのやり取りが行われ、データ ポイントが選択されるか、他のビジュアルのフィルター処理が行われる場合は、プロパティから状態を復元する必要があります。

## <a name="how-to-add-report-bookmarks-support"></a>レポート ブックマーク サポートを追加する方法

1. 必要なユーティリティ `powerbi-visuals-utils-interactivityutils`(https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) バージョン 3.0.0 以降をインストール (または更新) します。 これには、状態の選択またはフィルターで操作するための追加のクラスが含まれています。 これは、ビジュアル、および `InteractivityService` を使用するすべてのビジュアルに必要です。

2. `SelectionManager` のインスタンスで `registerOnSelectCallback` を使用するために、ビジュアルの API を 1.11.0 に更新します。 これは、`InteractivityService` ではなく、プレーンの `SelectionManager` を使用する非フィルター ビジュアルに必要です。

### <a name="how-custom-visuals-interact-with-power-bi-in-the-report-bookmarks-scenario"></a>レポート ブックマーク シナリオでカスタム ビジュアルと Power BI とでどのようにやり取りされるか

次の例を考えてみましょう。ユーザーはレポート ページに複数のブックマークを作成し、各ブックマークでは異なる選択状態になっています。

まず、ユーザーはビジュアル内のデータ ポイントを選択します。 ビジュアルでは、ホストに選択を渡すことで、Power BI およびその他のビジュアルとやり取りします。 その後、ユーザーは [ブックマーク] パネルで [追加] を選択し、Power BI では新しいブックマークの現在の選択内容が保存されます。`Bookmark panel`

ユーザーが選択内容を変更し、新しいブックマークを追加するときに、これが繰り返し行われます。
作成されたら、ユーザーはブックマークを切り替えることができます。

ユーザーがブックマークを選択すると、Power BI によって保存されたフィルターまたは選択状態が復元され、ビジュアルに渡されます。 他のビジュアルは、ブックマークに格納されている状態に応じて、強調表示されるか、フィルター処理されます。 Power BI ホストではアクションを担当します。 ビジュアルでは、新しい選択状態 (レンダリングされるデータ ポイントの色の変更など) を正しく反映することを担当します。

新しい選択状態は、`update` メソッドを介してビジュアルに伝達されます。 `options` 引数には、特殊な `options.jsonFilters` プロパティが含まれます。 これは JSONFilter で、プロパティには `Advanced Filter`、および `Tuple Filter` を含めることができます。

ビジュアルでは、フィルター値を復元し、選択されたブックマークのビジュアルの対応する状態が表示されるようにする必要があります。

または、ビジュアルで選択のみが使用される場合は、特殊なコールバック関数呼び出しで登録された、ISelectionManager の `registerOnSelectCallback` メソッドを使用します。

### <a name="visuals-with-selections"></a>選択を使用するビジュアル

ビジュアルで[選択](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md)を使用して他のビジュアルとやり取りする場合。 ブックマークを追加する方法は 2 つあります。

* ビジュアルで以前に **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md) を使用しなかった**場合、`FilterManager.restoreSelectionIds` メソッドを使用できます。

* 選択の管理に既に **[`InteractivityService`](https://github.com/Microsoft/powerbi-visuals-utils-interactivityutils/blob/master/docs/api/interactivityService.md)** を使用している場合。 `InteractivityService` のインスタンスで `applySelectionFromFilter` メソッドを使用する必要があります。

#### <a name="using-iselectionmanagerregisteronselectcallback"></a>`ISelectionManager.registerOnSelectCallback` の使用

ユーザーがブックマークをクリックすると、Power BI によって、対応する選択でビジュアルの `callback` メソッドが呼び出されます。 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

[`'visualTransform'`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74) メソッドで作成されたビジュアルのデータ ポイントがあるとします。

`datapoints` は次のようになっています。

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

したがって、データ ポイントとして `visualDataPoints` があり、`ids` 配列は `callback` 関数に渡されます。

この時点で、ビジュアルでは `ISelectionId[]` の配列と、`visualDataPoints` 配列の選択が比較され、対応するデータ ポイントを選択されたものとしてマークする必要があります。

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

データ ポイントの更新後に、`filter` オブジェクトに格納されている現在の選択状態が反映されます。 その後、データ ポイントがレンダリングされると、カスタム ビジュアルの選択状態がブックマークの状態と一致するようになります。

### <a name="using-interactivityservice-for-control-selections-in-the-visual"></a>ビジュアルのコントロール選択での `InteractivityService` の使用

ビジュアルで `InteractivityService` が使用されている場合、ビジュアルでブックマークをサポートするための追加の操作は必要ありません。

ユーザーがブックマークを選択すると、ユーティリティでビジュアルの選択状態が処理されます。

### <a name="visuals-with-filter"></a>フィルターを使用するビジュアル

ビジュアルによって、データのフィルターが日付範囲で作成されるとします。 したがって、`startDate` と `endDate` が範囲の開始と終了となります。
ビジュアルで高度なフィルターが作成され、ホスト メソッド `applyJsonFilter` が呼び出され、関連条件でデータがフィルター処理されます。
`target` はフィルター処理のためのテーブルです。

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

ユーザーがブックマークをクリックするたびに、カスタム ビジュアルで `update` 呼び出しが取得されます。

カスタム ビジュアルでは、オブジェクト内のフィルターを確認する必要があります。

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

`filter` オブジェクトが null でない場合、ビジュアルでオブジェクトからフィルター条件を復元する必要があります。

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

その後、ビジュアルでその内部状態 - データ ポイントと視覚化オブジェクト (線や四角形など) - を変更し、現在の条件を反映させる必要があります。

> [!IMPORTANT]
> レポート ブックマークのシナリオでは、ビジュアルで `applyJsonFilter` を呼び出して他のビジュアルをフィルター処理する必要はありません。これらは既に Power BI によってフィルター処理されています。

タイムライン スライサー ビジュアルでは、範囲セレクターを対応するデータ範囲に変更します。

詳細については、[タイムライン スライサー リポジトリ](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df)に関するページを参照してください。

### <a name="filter-state-to-save-visual-properties-in-bookmarks"></a>状態をフィルター処理してビジュアル プロパティをブックマークに保存する

`filterState` プロパティでは、プロパティがフィルター処理の一部と見なされます。 ビジュアルでは、さまざまな値をブックマークに格納できます。

プロパティ値をフィルター状態として保存するには、オブジェクト プロパティを `capabilities.json` で `"filterState": true` としてマークする必要があります。

例: `Timeline Slicer` では、フィルターに `Granularity` プロパティ値が格納されます。 また、ユーザーがブックマークを変更するときに、現在の細分性を変更できるようにします。

詳細については、[タイムライン スライサー リポジトリ](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334)に関するページを参照してください。
