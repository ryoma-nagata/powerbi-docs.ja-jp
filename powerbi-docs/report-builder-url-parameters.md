---
title: ページ分割されたレポートの URL パラメーター - Power BI レポート ビルダー
description: このトピックでは、Power BI の改ページ調整されたレポート ビルダーのレポート パラメーターの一般的な用途や設定できるプロパティなどについて説明します。
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: bda35bfb4690d8109f7bd611e3d319278d235f33
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302670"
---
# <a name="url-parameters-in-paginated-reports-in-power-bi"></a>Power BI のページ分割されたレポートの URL パラメーター

URL にパラメーターを追加することで、Power BI のページ分割されたレポートにコマンドを送信できます。 たとえば、特定のレポート パラメーター値セットを使用してレポートを表示しているとします。 定義済みの URL アクセス パラメーターを使用して、URL にこの情報をカプセル化します。 さらに、レンダリング フォーマットやレポート ツールバーの外観と雰囲気のパラメーターを埋め込んで Power BI のレポートの処理方法をカスタマイズします。 次に、この URL をメールまたは Web ページに直接貼り付けて、他のユーザーがブラウザーで同じ方法でレポートを使用できるようにします。 

URL アクセス パラメーターを使用して実行できるアクションを次に示します。 

- レポート パラメーターをレポートに送信します。 
- サポートされているファイル形式でレポート コンテンツのエクスポートを開始します。 
- パラメーター ウィンドウの表示と非表示を切り替えます。 
- DeviceInfo 設定を指定します。 

URL アクセスで使用できるコマンドと設定の詳細な一覧については、この記事で後述する  [URL アクセス パラメーターのリファレンス](#url-access-parameter-reference)に関する記事を参照してください。 

## <a name="url-access-concepts"></a>URL アクセスの概念 

Power BI への URL 要求には、サービスによって処理されるパラメーターが含まれます。 サービスによって URL 要求が処理される方法は、URL に含まれるパラメーター、パラメーターのプレフィックス、および項目の種類によって変わります。 ページ分割されたレポートの URL 機能は、標準的な URL アドレス指定をサポートするほとんどのブラウザーやアプリケーションと互換性があります。 

## <a name="url-access-syntax"></a>URL アクセスの構文 

URL 要求には、任意の順序で列挙した複数のパラメーターを含めることができます。 複数のパラメーターはアンパサンド (&) で区切られます。 名前と値のペアは等号 (=) で区切られます。 例:

```
powerbiserviceurl?rp:parametervalueh&rdl:parameter=value  
```

## <a name="syntax-description"></a>構文の説明 

### <a name="powerbiserviceurl"></a>powerbiserviceurl 

Power BI テナントの Web サービス URL。 例: 

**&** URL アクセス パラメーターの名前と値のペアを区切るために使用されます。

**プレフィックス** Power BI サービスのアクションを指定する URL パラメーターのプレフィックス (たとえば、rp: または rdl:)。 

> [!NOTE]
> レポート パラメーターにはパラメーターのプレフィックスが必要であり、大文字と小文字が区別されます。 

**パラメーター** パラメーター名。 

### <a name="value"></a>値 

使用されるパラメーターの値に対応する URL テキスト。 

URL でレポート パラメーターを渡す例については、 [URL 内でレポート パラメーターを渡す](report-builder-url-pass-parameters.md)方法に関する記事を参照してください。

## <a name="url-access-parameter-reference"></a>URL アクセス パラメーターのリファレンス

次のパラメーターを URL の一部として使用すると、Power BI のページ分割されたレポートの外観と雰囲気を構成できます。 このセクションでは、最も一般的なパラメーターについて説明します。 パラメーターは大文字と小文字が区別されず、出力形式に関連する場合はパラメーター プレフィックス  `rdl:`  で始まります。  

### <a name="report-commands-rdl"></a>レポート コマンド (`rdl:`) 

**エクスポート形式** レポートをレンダリングおよびエクスポートする形式を指定します。 使用可能な値は次のとおりです。 
- PPTX (PowerPoint)
- MHTML 
- イメージ 
- EXCELOPENXML (Excel) 
- WORDOPENXML (Word) 
- CSV 
- PDF 
- XML 

## <a name="next-steps"></a>次の手順

- [Power BI のページ分割されたレポートの URL 内でレポート パラメーターを渡す](report-builder-url-pass-parameters.md)
- [Power BI Premium のページ分割されたレポートとは](paginated-reports-report-builder-power-bi.md)
