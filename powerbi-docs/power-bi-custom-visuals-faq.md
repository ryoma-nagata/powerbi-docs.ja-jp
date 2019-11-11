---
title: Power BI ビジュアルに関してよく寄せられる質問
description: Power BI ビジュアルについてよく寄せられる質問とその回答の一覧です
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: ff20ece0b96c5037e0ca98be953d77b921e37585
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874546"
---
# <a name="frequently-asked-questions-about-power-bi-visuals"></a>Power BI ビジュアルに関してよく寄せられる質問

## <a name="organizational-visuals"></a>組織のビジュアル

管理ポータルを使用すると、組織の Power BI ビジュアルを管理できます。

### <a name="how-can-the-admin-manage-the-organizational-power-bi-visuals"></a>管理者が組織の Power BI ビジュアルを管理するにはどうすればよいですか?

管理ポータルの [組織のビジュアル] タブから、管理者は[企業内のすべての組織の Power BI ビジュアルを管理](service-admin-portal.md#organizational-visuals)および確認できます (追加、無効化、有効化、削除)。
電子メールや共有フォルダーを使用してこれらのビジュアルを共有する必要はもうありません。 組織のリポジトリに展開すれば、組織のユーザーはこれらを簡単に見つけて、Power BI Desktop またはサービスから直接自分のレポートに組織のビジュアルをインポートできます。 組織のビジュアルは、 *[自分の所属組織]* タブの下にある (デスクトップおよびサービスの) 組み込みのストアから見つけることができます。管理者が組織のカスタム ビジュアルの新しいバージョンをアップロードすると、組織内の全員が同じ更新されたバージョンを取得できます。 レポート作成者が、ビジュアルの新しいバージョンを取得するためにレポート内のビジュアルを削除する必要はありません。これらのビジュアルを使用しているレポートは、すべて自動的に更新されるためです。 更新のメカニズムは、マーケットプレース ビジュアルと似ています。

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>管理者がパブリック マーケットプレースから組織のストアにカスタム ビジュアルをアップロードする場合、ベンダーがパブリック マーケットプレースのビジュアルを更新したらそれは自動的に更新されますか?

いいえ、パブリック マーケットプレースからの自動更新はありません。
管理者が組織のビジュアルのバージョンを更新する必要があります。

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>組織のストアを無効にする方法はありますか?

いいえ、ユーザーは常に Power BI Desktop およびサービスから [自分の所属組織] タブを表示します。 管理者は管理ポータルからすべての組織のビジュアルを無効化または削除することができ、組織のストアは空です。
  
### <a name="if-the-administrator-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-visuals"></a>管理者が管理ポータルから Power BI ビジュアルを無効にした場合 (テナント設定)、ユーザーは引き続き組織のビジュアルにアクセスできますか?

はい、管理者が管理ポータルから Power BI ビジュアルを無効にしても、組織のストアには影響しません。 一部の組織は、Power BI ビジュアルを無効にし、Power BI 管理者によって組織のストアにインポートおよびアップロードされた、手動で選択されたビジュアルのみを有効にする場合があります。 管理ポータルから Power BI ビジュアルを無効にしても、Power BI Desktop では適用されません。 デスクトップのユーザーは、引き続きパブリック マーケットプレースから Power BI ビジュアルを追加し、自分のレポートで使用することができます。 ただし、それらのパブリックな Power BI ビジュアルは、Power BI サービスに公開されるとレンダリングされなくなり、該当するエラーが発行されます。 Power BI サービスを使用する場合は、パブリック マーケットプレースから Power BI ビジュアルをインポートすることはできません。 管理ポータルでの Power BI ビジュアルの設定が Power BI サービスに適用されるため、インポートできるのは組織のストアのビジュアルのみです。

### <a name="why-does-the-organizational-store-and-organizational-visuals-make-a-great-enterprise-solution"></a>組織のストアと組織のビジュアルが優れた企業向けソリューションとなる理由を教えてください。

* すべてのユーザーが、Power BI 管理者によって制御される同じバージョンのビジュアルを取得できます。 管理者が管理ポータルでビジュアルのバージョンを更新すると、組織内のすべてのユーザーが更新されたバージョンを自動的に取得できます。

* ビジュアルのファイルを電子メールや共有フォルダーで共有する必要はありません。 1 つの場所での作業が、ログインしているすべてのユーザーに反映されます。

* セキュリティと保守性に優れています。組織のビジュアルの新しいバージョンは、マーケットプレースのビジュアルと同様に、すべてのレポート内で自動的に更新されます。

* 組織のビジュアルを使用している組織内のユーザーは、組織のセキュリティ要素である組織のビジュアルを表示および使用するためにログインする必要があります。

* 管理者は、組織内で使用できる Power BI ビジュアルを制御できます。

* 管理者は、テスト用のビジュアルを管理ポータルから有効または無効にできます。 各ビジュアルは組織のメンバーのみに許可されるため、セキュリティが強化されます。

## <a name="certified-power-bi-visuals"></a>認定済み Power BI ビジュアル

### <a name="what-are-certified-power-bi-visuals"></a>認定済み Power BI ビジュアルとは何ですか?

認定済み Power BI ビジュアルとは、[マーケットプレース](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)内のビジュアルで、[特定の](power-bi-custom-visuals-certified.md)コードの要件と Power BI チームによるテストを満たしたもののことです。  実行されたテストは、ビジュアルが外部のサービスやリソースにアクセスしないことを確認するように作られています。 ただし、Microsoft はサードパーティ製の Power BI ビジュアルの作成者ではありません。サードパーティ製のビジュアルの機能については、作成者に直接お問い合わせいただくことをお客様にお勧めしています。

### <a name="what-tests-are-done-during-the-certification-process"></a>認定プロセス中はどのようなテストが行われますか?

認定プロセスのテストには、次のようなものがあります (ただし、これらに限定されません)。コード レビュー、静的コード分析、データ漏えい、データ ファジー化、侵入テスト、アクセス XSS テスト、悪意のあるデータ挿入、入力の検証、機能テスト。
 
### <a name="do-you-certify-visuals-every-submission"></a>送信ごとにビジュアルを認定する必要がありますか?

はい。 認定済みビジュアルの新しいバージョンが Marketplace に送信されるたびに、ビジュアルのバージョン更新プログラムは、同じ証明書チェックを受けます。

開発者向けのメモ: 認定済みのビジュアルのバージョン更新プログラムを送信する場合、[最初の認定要求](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified#process-for-submitting-a-custom-visual-for-certification)のように電子メールを個別に送信する必要はありません。 バージョン更新プログラムの認定は自動的に行われます。違反が存在しそれが拒否の原因となる場合、修正するには何が必要かを説明するメールが送信されます。 

### <a name="is-it-possible-that-a-certified-visual-stops-being-certified-with-a-new-update"></a>認定済みビジュアルの新しい更新プログラムに対して行われる認定を停止することはできますか?

いいえ、それはできません。 認定済みビジュアルの新しい更新プログラムに対する認定を省略することはできません。 更新プログラムは拒否されます。
 
### <a name="do-i-need-to-share-my-code-in-public-repository-if-i-am-submitting-to-the-certification-process"></a>認定プロセスを受ける場合、自分のコードをパブリック リポジトリで共有する必要がありますか?

いいえ、ご自分のコードをパブリックに共有する必要はありません。 ただし、ビジュアル コードを確認するための読み取りアクセス許可を Microsoft に提供していただく必要があります。 たとえば、 GitHub のプライベート リポジトリ。
 
### <a name="do-we-have-to-publishhttpsdocsmicrosoftcompower-bideveloperoffice-store-the-visual-in-the-marketplacehttpsappsourcemicrosoftcommarketplaceappspage1productpower-bi-visuals-to-certify-it"></a>ビジュアルを認定するには、それを [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) に[発行](https://docs.microsoft.com/power-bi/developer/office-store)する必要がありますか?

はい。 最初にビジュアルを Marketplace に発行することは、認定のための必須の要件です。
カスタム ビジュアルを認定するには、それが Microsoft のサーバー内に置かれている必要があります。 プライベート ビジュアルを認定することはできません。
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>ビジュアルの認定にはどれくらいの時間がかかりますか?

更新の場合、最大 3 週間かかることがあります。 新しい送信 (初回の認定) については、最長で 4 週間かかる場合があります。 

### <a name="does-the-certification-process-ensure-that-no-data-leakage-occurs"></a>認定プロセスでは、データ漏えいが発生しないことが保証されていますか?

実行されたテストは、ビジュアルが外部のサービスやリソースにアクセスしないことを確認するように作られています。 ただし、Microsoft はサードパーティ製の Power BI ビジュアルの作成者ではありません。サードパーティ製のビジュアルの機能については、作成者に直接お問い合わせいただくことをお客様にお勧めしています。
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>未認定 Power BI ビジュアルは使用しても安全ですか?

未認定 Power BI ビジュアルは、安全ではないビジュアルを意味するわけではありません。
一部のビジュアルは 1 つまたは複数の[認定要件](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements)を満たしていないために認定されていません。 たとえば、地図ビジュアルのような外部サービスや商用ライブラリを利用するビジュアルに接続する場合です。
 
## <a name="visuals-with-additional-purchases"></a>ビジュアルの追加購入

### <a name="what-is-a-visual-with-additional-purchases"></a>ビジュアルの追加購入とは何ですか?

ビジュアルの追加購入は、マーケットプレースでのアプリ内購入 (IAP) アドインに似ています。これらのアドインには **[追加購入が必要になる場合があります]** という値札が付けられています。

IAP Power BI ビジュアルは無料のダウンロード可能な Power BI ビジュアルです。マーケットプレースからこれらの Power BI ビジュアルをダウンロードするために料金はかかりません。 高度な機能をアプリ内でオプション購入することもできます。  

### <a name="whats-the-benefit-to-developers"></a>開発者にとってのメリットは何ですか?

AppSource の IAP Power BI ビジュアルは、毎日、多くのサイト訪問者の目に触れ、貴重なトラフィックを獲得できます。また、IAP Power BI ビジュアルとその開発者であるご自分の認知度が高まります。

最近まで自分の Web サイトでビジュアルを管理していた開発者もビジュアルを AppSource に提出できるようになりました。 Power BI コミュニティで IAP ビジュアルが人目に触れやすくなります。

AppSource にビジュアルを公開すれば、ストア内のレビューや評価システムにより、IAP カスタム ビジュアルの利用者から直接フィードバックをもらうことができます。  

AppSource 検証チームが IAP ビジュアルを承認したら、そのビジュアルを認定してもらうこともできます。 これは任意のプロセスです。  

認定済み IAP Power BI ビジュアルは PowerPoint にエクスポートしたり、ユーザーがレポート ページをサブスクライブしたときに受け取るメールに表示したりできます。 つまり、現状では、IAP ビジュアルをマーケットプレースに提出することで、IAP Power BI ビジュアルを認定してもらい、追加機能セットを利用することもできます。  

### <a name="do-iap-visuals-need-to-be-certified"></a>IAP ビジュアルは認定する必要がありますか?

認定プロセスは任意です。 IAP Power BI ビジュアルを認定させ、無料のビジュアルとは別物にするかどうかは開発者次第です。

### <a name="what-is-changing-in-the-submission-process"></a>送信プロセスの変更点は何ですか?

IAP Power BI ビジュアルをマーケットプレースに送信するプロセスは無料のビジュアルの場合と同じです。 販売者のダッシュボード経由で行われます。  送信プロセスの唯一の変更点は、販売者のダッシュボードで開発者が開発者注記に "ビジュアル、アプリ内購入あり" と 明記する必要があることです。 また、有料の高度な機能を有効にするために必要な場合、ライセンス キー/トークンを提供する必要があります。  

販売者のダッシュボードでは "*無料、アプリ内購入あり*" を新しく選択することはできません。IAP ビジュアルは*無料*として提出する必要があります。

また、どの機能が無料で、どの機能に追加購入が必要か、ストアの説明文に記載して利用者に知らせてください。  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>IAP カスタム ビジュアルを提出する前に何をしますか?

IAP カスタム ビジュアルを作成している、あるいは既に用意している場合、それがガイドラインを満たしていることを確認してください。  

カスタム ビジュアルにロゴが入っている場合、それがロゴのガイドライン (色、場所、サイズ、アクション トリガー) を満たしていることを確認してください。

ガイドラインにはベスト プラクティスに関する注記もあります。  
> [!Note]
> すべての無料ビジュアルでは、以前に提供されていたものと同じ無料の機能をそのまま使用する必要があります。 古い無料機能の上に、オプションの高度な有料機能が追加されることがあります。 高度な機能を備えた IAP ビジュアルは新しいビジュアルとして送信し、古い無料のビジュアルを更新しないようにすることをお勧めします。

### <a name="can-i-get-my-iap-custom-visual-certified"></a>IAP カスタム ビジュアルを認定してもらうことはできますか。

はい。無料のビジュアルの場合と同じです。  AppSource チームが IAP カスタム ビジュアルを承認したら、そのビジュアルを認定プロセスに提出できます。

ビジュアルを認定してもらうには、認定要件を満たす必要があります。たとえば、ライセンスの有効性確認で外部サービスにアクセスすることができません。

繰り返しになりますが、認定は任意のプロセスです。IAP プロセスを認定してもらうかどうかは開発者次第です。

## <a name="additional-questions"></a>その他の質問

### <a name="how-to-get-support"></a>サポートを受ける方法は?

ご質問、ご意見、問題がございましたら、Power BI ビジュアルのサポート チームまでお気軽にお問い合わせください。アドレスは  *pbicvsupport@microsoft.com*   です。  

## <a name="next-steps"></a>次の手順

詳細については、[Power BI ビジュアルのトラブルシューティング](power-bi-custom-visuals-troubleshoot.md)に関する記事を参照してください。
