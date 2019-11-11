---
title: Power BI Desktop でファイル (バイナリ) を結合する
description: Power BI Desktop でファイル (バイナリ) データ ソースを簡単に結合できます
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 03a6e044a55613d40a1cf195d6a0ad3b44a9f012
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73876553"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Power BI Desktop でファイル (バイナリ) を結合する
**Power BI Desktop** にデータをインポートする強力な方法の 1 つは、スキーマが一致している複数のファイルを単一の論理テーブルに組み合わせることです。 この記事で説明しているように、この便利で人気のある方法がいっそう強化され、拡張されています。

同じフォルダーのファイルを結合するプロセスを始めるには、 **[データの取得] > [ファイル] > [フォルダー]** の順に選択します。

![](media/desktop-combine-binaries/combine-binaries_1.png)


## <a name="combine-files-behavior"></a>ファイルの結合動作
**[クエリ エディター]** の **[ホーム]** リボン タブから、または列自体から **[ファイルの結合]** を選択することで**ファイル (バイナリ) を結合**できます。

![](media/desktop-combine-binaries/combine-binaries_2a.png)

**ファイルの結合**変換は次のように動作します。

* **ファイルの結合**変換は、各入力ファイルを分析し、使用する適切なファイル形式を決定します (*テキスト* ファイル、*Excel ブック* ファイル、*JSON* ファイルなど)。
* 変換では、最初のファイルから特定のオブジェクト (*Excel ブック*など) を選択して抽出できます。
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* **ファイルの結合**では、次のクエリが自動的に実行されます。
  
  * 単一のファイルで必要なすべての抽出手順を実行するクエリの例を作成します。
  * ファイル/バイナリ入力を*見本クエリ*にパラメーター化する*関数クエリ*を作成します。 見本クエリと関数クエリはリンクされており、見本クエリを変更すると関数クエリに反映されます。
  * 入力バイナリを持つ元のクエリ (たとえば、*フォルダー* クエリ) に*関数クエリ*を適用して各行のバイナリ入力に関数クエリを適用した後、結果のデータ抽出を最上位の列として展開します。
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> Excel ブックでの選択範囲は、バイナリ結合の動作に影響を与えます。 たとえば、特定のワークシートを選択してそのワークシートを結合したり、ルートを選択して完全なファイルを結合したりできます。 フォルダーを選択すると、そのフォルダー内のファイルが結合されます。 


**ファイルの結合**の動作では、ファイルの種類と構造が同じであれば (同じ列のように)、特定のフォルダー内のすべてのファイルを簡単に結合できます。

さらに、自動的に作成される*見本クエリ*を修正することで、適用される変換および抽出の手順を簡単に変更できます。*関数クエリ*の手順を変更したり追加作成したりする必要はありません。 *見本クエリ*に対するすべての変更は、リンクされた*関数クエリ*に自動的に生成されます。

## <a name="next-steps"></a>次の手順
Power BI Desktop を使用して接続できるデータの種類は他にもあります。 データ ソースの詳細については、次のリソースを参照してください。

* [Power BI Desktop とは何ですか?](desktop-what-is-desktop.md)
* [Power BI Desktop のデータ ソース](desktop-data-sources.md)
* [Power BI Desktop でのデータの整形と結合](desktop-shape-and-combine-data.md)
* [Power BI Desktop で CSV ファイルに接続する](desktop-connect-csv.md)   
* [Power BI Desktop にデータを直接入力する](desktop-enter-data-directly-into-desktop.md)   

