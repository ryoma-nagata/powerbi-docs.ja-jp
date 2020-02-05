---
title: Power BI ビジュアルの開発方法に関するトラブルシューティング
description: この記事では、Power BI カスタム ビジュアルの開発または作成時に発生する一般的な問題について説明します。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: troubleshooting
ms.subservice: powerbi-custom-visuals
ms.date: 11/06/2018
ms.openlocfilehash: c2680a5818488a7822f38b8286a3e5a1782a487a
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "74999769"
---
# <a name="troubleshoot-power-bi-visuals"></a>Power BI ビジュアルのトラブルシューティング

## <a name="debug"></a>Debug

**Pbiviz コマンドが見つかりません (または類似のエラー)**

ターミナルのコマンド ラインで `pbiviz` を実行すると、ヘルプ画面が表示されるはずです。 ヘルプ画面が表示されない場合、コマンドは正しくインストールされていません。 バージョン 4.0 以降の NodeJS がインストールされていることを確認します。

**[視覚化] タブで "ビジュアルのデバッグ" が見つかりません**

"ビジュアルのデバッグ" は、 **[視覚化]** タブ内でプロンプト アイコンのように表示されます。

![ビジュアルの選択](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

表示されない場合は、Power BI の設定内で有効にされていることを確認してください。

> [!NOTE]
> ビジュアルのデバッグ機能は、現時点では、Power BI サービスでのみ使用可能で、Power BI Desktop とモバイル アプリでは使用できません。 パッケージ化したビジュアルはあらゆる場所で機能します。

**ビジュアル サーバーに接続できません**

ビジュアル プロジェクトのルートから、ターミナルのコマンド ラインで `pbiviz start` コマンドを使用してビジュアル サーバーを実行します。 サーバーが動作していない場合、SSL 証明書が正しくインストールされていない可能性があります。

ご質問、ご意見、問題がございましたら、Power BI ビジュアルのサポート チームまでお気軽にお問い合わせください。アドレスは  *pbicvsupport@microsoft.com*   です。

## <a name="next-steps"></a>次の手順

詳細については、「[Power BI ビジュアルに関してよく寄せられる質問](power-bi-custom-visuals-faq.md#organizational-power-bi-visuals)」を参照してください。