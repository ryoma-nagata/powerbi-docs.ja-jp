---
title: 販売者ダッシュボードを使用して AppSource に Power BI ビジュアルを提出する
description: 販売者ダッシュボードを使用して AppSource に Power BI ビジュアルを提出する
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 12ecde787bb268190f9b94a2db5992d5840080ac
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2019
ms.locfileid: "75002537"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>販売者ダッシュボードを使用して AppSource に Power BI ビジュアルを提出する

AppSource に提出する前に、**pbiviz**ファイルと **pbix** ファイルをメールで Power BI チームに送る必要があります。 これにより、Power BI チームはパブリック共有サーバーにファイルをアップロードできるようになります。 それ以外の場合、ストアはファイルを取得できません。 新しく提出する Power BI ビジュアル、既存の Power BI ビジュアルの更新、および拒否された提出に対する修正が含まれるファイルを送信する必要があります。

>[!NOTE]
>[販売者ダッシュボード](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store)は段階的に廃止されています。それは、[パートナー センター](https://docs.microsoft.com/partner-center/)に置き換えられています。 販売者ダッシュボードは、Power BI ビジュアルの提出プロセスの途中である場合にのみ使用してください。 新しい Power BI ビジュアルを AppSource に提出する場合は、[パートナー センターを使用する方法](office-store.md#submitting-to-appsource)に従ってください。

### <a name="seller-dashboard-submission-process"></a>販売者ダッシュボードでの提出プロセス

[Office デベロッパー センター](https://dev.office.com/)にサインインするには、有効な Office 開発者アカウントが必要です。 Office 開発者アカウントは、hotmail.com や outlook.com などの Microsoft Account Live ID である必要があります。

1. [デベロッパー センター](https://sellerdashboard.microsoft.com/Application/Summary)に移動します。

2. **[新しいアプリの追加]** を選びます。

    ![アプリの追加](media/office-store/powerbi-custom-visual-add-an-app.png)

3. **[Power BI カスタム ビジュアル]** を選び、 **[次へ]** を選びます。

4. **[アプリ パッケージ]** の下の **[+]** を選び、[ファイルを開く] ダイアログ ボックスで、Power BI チームから提供されたアプリ パッケージ XML ファイルを選びます。

    ![アプリ パッケージ](media/office-store/powerbi-custom-visual-apppackage.png)

5. これが有効な Power BI アプリ パッケージである承認を受ける必要があります。

    ![承認されたマニフェスト](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. **[全般情報]** の詳細を入力します。

   * *[Submission title]\(送信タイトル\):* デベロッパー センターへの提出に付ける名前です。
   * *[バージョン]:* バージョン番号はアドイン アプリ パッケージから自動的に入力されます。
   * *[リリース日 (UTC)]:* 自分のアプリをストアにリリースする日付を選びます。 将来の日付を選んだ場合、その日になるまでアプリはストアで提供されません。
   * *[カテゴリ]:* 最初のカテゴリには、"データのビジュアル化 + BI" が自動的に入力されます。 すべての Power BI ビジュアルは、このようにタグ付けされます。 ユーザーがビジュアルを簡単に検索できるように、最大 2 つのカテゴリを追加指定できます。
   * *[テスト用メモ]:* (省略可能) Microsoft のテスト担当者に対する説明がある場合は入力します。
   * *[このアプリは、暗号化を呼び出したり、サポートしたり、組み込んだり、使用したりします]:* オフのままにします。
   * *[このアドインを iPad の Office アドイン カタログで利用できる状態にする]:* オフのままにします。
7. **[アプリ ロゴ]** の **[+]** を選んで、ビジュアルのロゴをアップロードします。 [ファイルを開く] ダイアログ ボックスでアイコン ファイルを選びます。 ファイルは、.png、.jpg、.jpeg、または .gif でなければなりません。 大きさはちょうど 300 (幅) x 300 (高さ) ピクセル、サイズは 512 KB 以下にする必要があります。

    ![アプリのロゴ](media/office-store/powerbi-custom-visual-app-logo.png)

8. **[サポート ドキュメント]** の詳細を入力します。

   * サポート ドキュメントへのリンク
   * プライバシーに関するドキュメントへのリンク
   * ビデオへのリンク
   * 使用許諾契約書 (EULA)

       EULA ファイルをアップロードする必要があります。 独自の EULA を使うことも、Office ストア内の Power BI ビジュアル用の既定の EULA を使うこともできます。 既定の EULA を使うには、販売者ダッシュボードの "使用許諾契約書" ファイル アップロード ダイアログ ボックスに[https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf) の URL を貼り付けます。

9. **[次へ]** を選び、 **[詳細]** ページに進みます。

10. **[言語]** を選び、一覧から言語を選びます。

    ![言語](media/office-store/powerbi-custom-visual-language.png)

11. [説明] の詳細を入力します。

    * *[アプリケーション名 (この言語)]:* ストアに表示するアプリのタイトルを入力します。
    * *[簡潔な説明]:* ストアに表示するアプリの簡単な説明を入力します (半角 100 文字以下)。 この説明は、ロゴと共に最上位のページに表示されます。 pbiviz パッケージの説明を使うことができます。
    * *[詳細な説明]:* 顧客がアプリの詳細ページで見るアプリのより詳細な説明を提供します。 コミュニティで改善できるようにビジュアルをオープン ソースにする場合は、GitHub などのパブリック リポジトリへのリンクをここで提供します。

12. 少なくとも 1 つのスクリーンショットをアップロードします。 使用できる形式は、.png、.jpg、.jpeg、.gif です。 大きさはちょうど 1366 (幅) x 768 (高さ) ピクセルにする必要があります。 ファイルのサイズは 1024 KB 以下でなければなりません。 *使いやすくするには、各スクリーンショットの重要な機能の価値提案がはっきりわかる吹き出しを追加します。*

12. 言語をさらに追加したい場合は、 **[言語の追加]** を選び、手順 10 と 11 を繰り返します。 言語を追加すると、ユーザーは自分の言語でカスタム ビジュアルの詳細を読むことができます。 一覧に表示されない言語は、既定で最初に選んだ言語に設定されます。

13. 言語の追加が済んだら、 **[次へ]** を選んで、 **[アクセス禁止]** ページに進みます。

14. 特定の国または地域の顧客がアプリを使用または購入できないようにする場合は、チェック ボックスをオンにして一覧から選びます。

15. **[次へ]** を選び、 **[価格]** ページに進みます。

16. 現在は、"*無料*" のビジュアルのみがサポートされており、ビジュアルの内部での追加購入 (アプリ内購入) は許可されていません。 **[このアプリは無料です]** を選びます。

    > [!NOTE]
    > 無料以外の他のオプションを選んだ場合、または提出されたビジュアルにアプリ内購入コンテンツが含まれる場合、申請は却下されます。

17. **[下書きとして保存]** を選んで後で送信するか、または **[承認のため送信]** を選んでカスタム ビジュアルを Office ストアに送信することができます。

## <a name="seller-dashboard-certification-submission-process"></a>販売者ダッシュボードでの認定提出プロセス

このセクションの手順に従って、販売者ダッシュボードで認定のために Power BI ビジュアルを提出します。 この方法は、過去に販売者ダッシュボードを使用して Power BI ビジュアルを AppSource に提出した場合に使用します。

1. Power BI ビジュアル サポート チーム (pbicvsupport@microsoft.com) にメールを送信します。 電子メールには、次の情報を含めます。
    * 件名:ビジュアル認定の要求
    * 人間が読めるソース コードがホストされている GitHub リポジトリへのリンク
    * [要件の遵守](power-bi-custom-visuals-certified.md#certification-requirements)
    * コード レビューに合格する

2. Power BI ビジュアルが認定されて[認定リスト](power-bi-custom-visuals-certified.md#list-of-power-bi-visuals-that-have-been-certified)に追加されたとき、または修正すべき問題のレポート付きで却下されたときに、Microsoft Power BI ビジュアル チームから通知が届きます。 Microsoft との連絡手段を維持し、必要に応じて認定済みのビジュアルを更新するのは、開発者の責任です。

## <a name="tracking-submission-status-and-usage"></a>送信の状態と使用状況の追跡

[検証ポリシー](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals)を確認できます。

送信後は、[アプリ ダッシュボード](https://sellerdashboard.microsoft.com/Application/Summary/)で送信の状態を見ることができます。

## <a name="certify-your-visual"></a>視覚エフェクトの認定

自分のビジュアルを作成した後、任意でそれに対する[認定](../developer/power-bi-custom-visuals-certified.md)を取得できます。

## <a name="next-steps"></a>次の手順

[Power BI カスタム ビジュアルの開発](visuals/custom-visual-develop-tutorial.md)  
[Power BI での視覚化](../visuals/power-bi-report-visualizations.md)  
[Power BI でのカスタム ビジュアル](../developer/power-bi-custom-visuals.md)  
[Power BI ビジュアルの認定を取得する](../developer/power-bi-custom-visuals-certified.md)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
