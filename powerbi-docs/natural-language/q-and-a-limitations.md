---
title: Power BI Q&A の制限事項
description: Power BI Q&A の現在の制限事項
author: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: 9f1beed3408d53a58a0fb725f9d98a4a95bb1b7c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874900"
---
# <a name="limitations-of-power-bi-qa"></a>Power BI Q&A の制限事項

Power BI Q&A には現在いくつかの制限事項があります。

## <a name="data-sources"></a>データ ソース

### <a name="supported-data-sources"></a>サポートされているデータ ソース

Power BI Q&A では、Power BI サービスにおけるデータ ソースの次の構成をサポートしています。

- Import モード
- Analysis Services へのライブ接続
- SQL Server Analysis Services へのライブ接続 (ゲートウェイを使用)
- Power BI データセット。 Power BI データセットを使用している場合、Power BI Desktop は Q&A を使ってエラーをレポートします。 ただし、Power BI サービスにレポートを公開すると、エラーは表示されなくなります。

これらの各構成では、行レベルのセキュリティもサポートされています。

### <a name="data-sources-not-supported"></a>サポートされていないデータ ソース

Power BI Q&A では、現在、次の構成はサポートされていません。

- オブジェクト レベルのセキュリティ (データ ソースの種類を問わず)
- DirectQuery (ソースを問わず)。 これをサポートするための回避策としては、Azure Analysis Services とのライブ接続を使用して、DirectQuery を利用します。
- 複合モデル
- Reporting Services 

## <a name="tooling-limitations"></a>ツールの制限事項

新しいツール ダイアログでは、ユーザーは Q&A の自然言語をカスタマイズおよび改善できます。 ツールの詳細については、[Q&A ツールの概要](q-and-a-tooling-intro.md)に関するページを参照してください。

## <a name="review-question-limitations"></a>[質問の確認] の制限事項

[質問の確認] では、実際のデータ モデルに対して寄せられた質問のみが最長 28 日間保存されます。 新しい [質問の確認] 機能を使用すると、一部の質問が記録されないことがあります。 これは仕様です。自然言語エンジンは、ユーザーによるすべてのキー ストロークが記録および表示されないようにするために、一連のデータ クレンジング手順を実行するからです。

テナント管理者は、テナント管理者設定を使用して、質問の保存機能を管理できます。 アクセス許可は、セキュリティ グループに基づいています。 

また、ユーザーは、 **[設定]**  >  **[全般]** の順に選択し、 **[Allow Q&A to record my utterance]\(Q&A で自分の発話を記録することを許可する\)** の選択を解除することで、自分の質問が記録されないようにすることもできます。 

## <a name="teach-qa-limitations"></a>[Q&A の学習] の制限事項

[Q&A の学習] を使用すると、次の 2 種類のエラーを修正できます。

- フィールドに単語を割り当てる。
- フィルター条件に単語を割り当てる。

現在、認識された用語の再定義に加え、その他の種類の条件や語句の定義はサポートされていません。 また、フィルター条件を定義するときは、次のような言語の限られたサブセットのみを使用できます。

- "Country" which is "USA"
- "Country" which is not "USA"
- "Weight" > 2000
- "Weight" = 2000
- "Weight" < 2000

> [!NOTE]
> Q&A ツールでは、インポート モードのみがサポートされています。 オンプレミスおよび Azure Analysis Services のデータ ソースへの接続はまだサポートされていません。 この現在の制限は、Power BI の今後のリリースでは削除される予定です。

### <a name="statements-not-supported"></a>サポートされないステートメント

- 条件でのメジャーの使用は現在サポートされていません。 代わりに、メジャーを計算列に変換して使用できるようにします。
- 複数の条件はサポートされていません。 回避策として、複数条件ステートメントのブール値を評価する DAX 計算列を作成し、このフィールドを代わりに使用します。
- Q&A からデータのサブセットの指定を求められたときにフィルター条件を指定しないと、ステートメント全体に赤色の下線が表示されていない場合でも、定義を保存することはできません。
