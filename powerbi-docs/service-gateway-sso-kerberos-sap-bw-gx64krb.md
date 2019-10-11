---
title: gx64krb5 を用いた SAP BW へのシングル サインオン (SSO) に Kerberos を使用する
description: gx64krb5 を用いた Power BI サービスからの SSO を有効にするように SAP BW サーバーを構成します
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4932f00fa7585c6b4f9186c29b65700d7a14fbea
ms.sourcegitcommit: 9bf3cdcf5d8b8dd12aa1339b8910fcbc40f4cbe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2019
ms.locfileid: "71968708"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>gx64krb5 を用いた SAP BW へのシングル サインオン (SSO) に Kerberos を使用する

この記事では、gx64krb5 を用いた Power BI サービスからの SSO を有効にするように SAP BW データ ソースを構成する方法を説明します。

> [!NOTE]
> [Kerberos SSO の構成](service-gateway-sso-kerberos.md)に関する記事の手順に加えて、この記事の手順を完了することにより、Power BI サービスの SAP BW アプリケーション サーバー ベースのレポートについて SSO ベースの更新を有効にすることができます。 ただし、SNC ライブラリとしては gx64krb5 ではなく CommonCryptoLib を使用することをお勧めします。 SAP では gx64krb5 がサポートされなくなっており、ゲートウェイで使用するための構成に必要な手順は、CommonCryptoLib と比較すると大幅に複雑になります。 CommonCryptoLib を使用する SSO の構成方法については、「[CommonCryptoLib を使用して SSO 用に SAP BW を構成する](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md)」を参照してください。 CommonCryptoLib "_または_" gx64krb5 の構成を完了する必要があります。 両方のライブラリの構成手順を行わないでください。

### <a name="set-up-gx64krb5-on-gateway-machine-and-the-sap-bw-server"></a>ゲートウェイ コンピューターと SAP BW サーバーで gx64krb5 を設定する
このガイドは、可能な限り包括的になるように書かれています。 一部の手順を既に完了している場合は、それをスキップできます。 たとえば、gx64krb5 を使用して SSO 用に SAP BW サーバーを既に構成している場合があります。

### <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>ゲートウェイ コンピューターと SAP BW サーバーで gx64krb5/gsskrb5 を設定する

> [!NOTE]
> `gx64krb5` は、SAP によって積極的にサポートされなくなりました。 詳細については、[SAP Note 352295](https://launchpad.support.sap.com/#/notes/352295) をご覧ください。 また、データ ゲートウェイから SAP BW メッセージ サーバーへの SSO 接続が `gx64krb5` によって許可されない点についても注意してください。 SAP BW アプリケーション サーバーへの接続のみが可能です。 [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) を SNC ライブラリとして使用する場合、このアプリケーション サーバーのみの制限は存在しません。 他の SNC ライブラリが BW SSO で機能する可能性もありますが、Microsoft では公式にはサポートされていません。

ゲートウェイを介して SSO 接続を完了するには、クライアントとサーバーの両方で `gx64krb5` が使用されている必要があります。つまり、クライアントとサーバーの両方で、同じ SNC ライブラリが使用されている必要があります。

1. [SAP Note 2115486](https://launchpad.support.sap.com/) から `gx64krb5` をダウンロードします (SAP S-User が必要)。 バージョンが 1.0.11.x 以上になっていることを確認します。 ゲートウェイ経由で SSO 接続を試す前に SAP GUI で SSO 接続をテストする場合は、`gsskrb5` (32 ビット版のライブラリ) もダウンロードします (推奨)。 SAP GUI は 32 ビットのみで使用できるため、SAP GUI を使用してテストするには、32 ビット版が必要です。

1. ゲートウェイ サービス ユーザーがアクセスできるゲートウェイ コンピューター上の場所に `gx64krb5` を配置します。 SAP GUI を使用して SSO 接続をテストする場合は、そのマシンにも `gsskrb5` のコピーを配置し、それを指すように **SNC_LIB** 環境変数を設定します。 サービス ユーザーが偽装するゲートウェイ サービス ユーザーと Active Directory (AD) ユーザーの両方に、`gx64krb5` のコピーに対する読み取りおよび実行アクセス許可が必要です。 Authenticated Users グループに .dll ファイルに対するアクセス許可を付与することをお勧めします。 テスト目的の場合、ゲートウェイ サービス ユーザーと、テストに使用する Active Directory ユーザーの両方に、これらのアクセス許可を明示的に付与することもできます。

1. BW サーバーが gx64krb5 を用いた SSO 用にまだ構成されていない場合は、SAP BW サーバーからアクセスできる場所の SAP BW サーバー コンピューターに、.dll の別のコピーを配置します。 SAP BW サーバーで使用するための gx64krb5 の構成の詳細については、[SAP のドキュメント](https://launchpad.support.sap.com/#/notes/2115486) (s-user が必要) を参照してください。

1. クライアント コンピューターとサーバー コンピューターで、`SNC_LIB` および `SNC_LIB_64` 環境変数を設定します。 gsskrb5 を使用する場合は、`SNC_LIB` 変数に gsskrb5.dll の絶対パスを設定します。 gx64krb5 を使用する場合は、`SNC_LIB_64` 変数に gx64krb5.dll の絶対パスを設定します。

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>BW サーバー上で SAP BW サービス ユーザーを構成し、SNC 通信を有効にする

gx64krb5 を用いた SNC 通信 (SSO など) 用に SAP BW サーバーをまだ構成していない場合は、このセクションを完了します。

> [!NOTE]
> このセクションでは、BW 用のサービス ユーザーを既に作成し、それに適切な SPN をバインドしてあるものとします (たとえば、`SAP/` で始まるもの)。

1. サービス ユーザーに、SAP BW アプリケーション サーバーへのアクセス権を付与します。

    1. SAP BW サーバー コンピューターで、ローカル管理者グループにサービス ユーザーを追加します。 [コンピューターの管理] プログラムを開き、サーバーのローカル管理者グループを特定します。 例:

        ![[コンピューターの管理] プログラムのスクリーン ショット](media/service-gateway-sso-kerberos/computer-management.png)

    1. ローカル管理者グループをダブルクリックし、 **[追加]** を選んで、グループにサービス ユーザーを追加します。 **[名前の確認]** を選んで、名前を正しく入力したことを確認します。 **[OK]** を選択します。

1. SAP BW サーバーのサービス ユーザーを、SAP BW サーバー コンピューターで SAP BW サーバー サービスを開始するユーザーとして設定します。

    1. **[ファイル名を指定して実行]** を開き、「**Services.msc**」と入力します。 SAP BW アプリケーション サーバー インスタンスに対応するサービスを探します。 それを右クリックし、 **[プロパティ]** を選択します。

        ![[プロパティ] が強調表示されている [サービス] のスクリーン ショット](media/service-gateway-sso-kerberos/server-properties.png)

    1. **[ログオン]** タブに切り替えて、ユーザーを SAP BW サービス ユーザーに変更します。 ユーザーのパスワードを入力し、 **[OK]** を選択します。

1. SAP ログオンでサーバーにサインインし、RZ10 トランザクションを使用して次のプロファイル パラメーターを設定します。

    1. **snc/identity/as** プロファイル パラメーターを *p:&lt;作成した SAP BW サービス ユーザー&gt;* に設定します (たとえば、*p:BWServiceUser\@MYDOMAIN.COM*)。 サービス ユーザーの UPN の前にある p: に注意してください。 SNC ライブラリとして Common Crypto Lib を使用するときのような、p:CN= ではありません。

    1. **snc/gssapi\_lib** プロファイル パラメーターを *&lt;BW サーバー コンピューターの gx64krb5.dll のパス&gt;* に設定します。 SAP BW アプリケーション サーバーがアクセスできる場所にライブラリを配置してください。

    1. また、次の追加のプロファイル パラメーターを設定し、ニーズに合わせて値を変更します。 最後の 5 つのオプションでは、クライアントは SNC を構成することなく、SAP ログオンを使用して SAP BW サーバーに接続することができます。

        | **設定** | **値** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. プロパティ **snc/enable** を 1 に設定します。

1. これらのプロファイル パラメーターを設定してから、サーバー コンピューターで SAP 管理コンソールを開き、SAP BW インスタンスを再起動します。 サーバーが起動しない場合は、プロファイル パラメーターを正しく設定したことを確認します。 プロファイル パラメーターの設定の詳細については、[SAP のドキュメント](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm)を参照してください。 また、問題が発生した場合、このセクションで後述するトラブルシューティング情報も参照できます。

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>SAP BW ユーザーを Active Directory ユーザーにマップする

まだ行っていない場合は、Active Directory ユーザーを SAP BW アプリケーション サーバー ユーザーにマップし、SAP ログオンで SSO 接続をテストします。

1. SAP ログオンを使用して、SAP BW サーバーにサインインします。 トランザクション SU01 を実行します。

1. **[User]\(ユーザー\)** には、SSO 接続を有効にする SAP BW ユーザーを入力します (以下のスクリーンショットでは、BIUSER のアクセス許可を設定する準備をしています)。 SAP ログオン ウィンドウの左上隅近くにある**編集**アイコン (ペンのイメージ) を選択します。

    ![SAP BW [User maintenance]\(ユーザーの管理\) 画面のスクリーン ショット](media/service-gateway-sso-kerberos/user-maintenance.png)

1. **[SNC]** タブを選びます。SNC 名の入力ボックスに、「*p:&lt;Active Directory ユーザー&gt;@&lt;ドメイン&gt;* 」と入力します。 Active Directory ユーザーの UPN の前に指定する必須の p: に注意してください。 指定した Active Directory ユーザーは、SAP BW アプリケーション サーバーへの SSO アクセスを有効にする対象の個人または組織に属している必要があります。 たとえば、ユーザー *testuser\@TESTDOMAIN.COM* の SSO アクセスを有効にする場合は、「*p:testuser\@TESTDOMAIN.COM*」と入力します。

    ![SAP BW [Maintain Users]\(ユーザー管理\) 画面のスクリーン ショット](media/service-gateway-sso-kerberos/maintain-users.png)

1. 画面の左上隅近くにある **[保存]** アイコン (フロッピー ディスクのイメージ) を選択します。

### <a name="test-sign-in-via-sso"></a>SSO 経由のサインインをテストする

SSO 経由で SAP ログオンを使用して、先ほど SSO アクセスを有効にした対象の Active Directory ユーザーとして、サーバーにサインインできることを確認します。

1. 先ほど SSO アクセスを有効にした対象の Active Directory ユーザーとして、SAP ログオンがインストールされているドメイン内のコンピューターにサインインします。 SAP ログオンを起動し、新しい接続を作成します。

1. 先ほどダウンロードした `gsskrb5` .dll を、サインオンしたコンピューター上の場所にコピーします。 `SNC_LIB` 環境変数をこの場所の絶対パスに設定します。

1. SAP ログオンを起動し、新しい接続を作成します。

1. **[Create New System Entry]\(新しいシステム エントリの作成\)** 画面で **[User Specified System]\(ユーザー指定のシステム\)** 、 **[Next]\(次へ\)** の順に選択します。

    ![[Create New System Entry]\(新しいシステム エントリの作成\) 画面のスクリーン ショット](media/service-gateway-sso-kerberos/new-system-entry.png)

1. 次の画面で、アプリケーション サーバー、インスタンス番号、システムの ID などの該当する詳細情報を入力します。 その後、 **[完了]** を選択します。

1. 新しい接続を右クリックし、 **[プロパティ]** を選びます。 **[ネットワーク]** タブを選びます。 **[SNC Name]\(SNC 名\)** テキスト ボックスに「*p:&lt;SAP BW サービス ユーザーの UPN &gt;* 」と入力します (たとえば、*p:BWServiceUser\@MYDOMAIN.COM*)。 **[OK]** を選択します。

    ![[System Entry Properties]\(システム エントリ プロパティ\) 画面のスクリーン ショット](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. 先ほど作成した接続をダブルクリックして、SAP BW サーバーへの SSO 接続を試みます。 この接続に成功した場合は、次の手順に進みます。 そうでない場合は、このドキュメントの前述の手順を参照して、接続が正常に完了したことを確認するか、または次のトラブルシューティングのセクションを参照します。 このコンテキストで SSO を使用して SAP BW サーバーに接続できない場合は、ゲートウェイのコンテキストで SSO を使用して SAP BW サーバーに接続することはできません。

### <a name="add-registry-entries-to-the-gateway-machine"></a>ゲートウェイ コンピューターにレジストリ エントリを追加する

必要なレジストリ エントリを、ゲートウェイがインストールされているコンピューターのレジストリ、および Power BI Desktop から接続するためのコンピューターに追加します。 実行するコマンドを次に示します。

1. ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

1. ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Power BI サービスに新しい SAP BW アプリケーション サーバー データ ソースを追加するか、既存のものを編集する

1. データ ソース構成ウィンドウで、Power BI Desktop から SAP BW サーバーにサインインするときと同様に、アプリケーション サーバーの **[ホスト名]** 、 **[システム番号]** 、および **[クライアント ID]** を入力します。

1. **[SNC パートナー名]** フィールドに、「*p:&lt;SAP BW サービス ユーザーにマップした SPN&gt;* 」と入力します。 たとえば、SPN が **SAP/BWServiceUser\@MYDOMAIN.COM** の場合、 **[SNC パートナー名]** フィールドに「*p:SAP/BWServiceUser\@MYDOMAIN.COM*」と入力する必要があります。

1. SNC ライブラリでは、**SNC\_LIB** または **SNC\_LIB\_64** を選択します。 ゲートウェイ コンピューターの **SNC\_LIB\_64** が gx64krb5.dll を指していることを確認します。 または、[カスタム] オプションを選択し、gx64krb5.dll (ゲートウェイ コンピューター上) の絶対パスを指定することもできます。

1. **[DirectQuery クエリには Kerberos 経由で SSO を使用します]** ボックスをオンにして、 **[適用]** を選択します。 テスト接続が成功しなかった場合は、前のセットアップおよび構成手順が正常に完了したことを確認します。

1. [Power BI レポートを実行する](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>トラブルシューティング

### <a name="troubleshoot-gx64krb5-configuration"></a>gx64krb5 の構成のトラブルシューティング

何か問題が発生した場合は、次の手順に従って、gx64krb5 のインストールと SSO 接続のトラブルシューティングを行います。

* サーバー ログ (サーバー コンピューター上の …work\dev\_w0) を参照すると、gx64krb5 のセットアップ手順の実行時に発生したエラーのトラブルシューティングに役立ちます。 これは、プロファイル パラメーターが変更された後に SAP BW サーバーが起動しない場合に特に役立ちます。

* ログオンに失敗した ために SAP BW サービスを開始できない場合、SAP BW "開始" ユーザーを設定するときに正しくないパスワードを指定した可能性があります。 SAP BW サービス ユーザーとして Active Directory 環境内のコンピューターにログインして、パスワードを確認します。

* 基になるデータ ソースの資格情報 (SQL Server など) に関するエラーが発生してサーバーを起動できない場合は、サービス ユーザーに SAP BW データベースへのアクセス権が付与されていることを確認します。

* 次のようなメッセージを受け取ることがあります。" *(GSS-API) specified target is unknown or unreachable.* " ((GSS-API) 指定された対象は不明か、または到達できません。) これは通常、正しくない SNC 名が指定されていることを意味します。 サービス ユーザーの UPN 以外には、"p:CN =" やクライアント アプリケーション内の何らかの項目ではなく、必ず "P:" だけを使用してください。

* 次のようなメッセージを受け取ることがあります。" *(GSS-API) An invalid name was supplied.* " ((GSS-API) 無効な名前が指定されました。) サーバーの SNC ID プロファイル パラメーターの値に "p:" が含まれることを確認してください。

* 次のようなメッセージを受け取ることがあります。" *(SNC error) the specified module could not be found.* " ((SNC エラー) 指定されたモジュールが見つかりませんでした。) これは通常、アクセスするのに高度な特権 (管理者権限) を必要とする場所に `gx64krb5.dll` を配置したことが原因で発生します。

### <a name="troubleshoot-gateway-connectivity-issues"></a>ゲートウェイ接続の問題のトラブルシューティングを行う

1. ゲートウェイのログを確認します。 ゲートウェイ構成アプリケーションを開き、 **[診断]** 、 **[ログのエクスポート]** の順に選択します。 最新のエラーは、確認するログ ファイルの下部に記載されています。

    ![[診断] が強調表示されているオンプレミス データ ゲートウェイ アプリケーションのスクリーン ショット](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. SAP BW トレースを有効にし、生成されたログ ファイルを確認します。 使用できる SAP BW トレースにはいくつかの種類があります (CPIC トレースなど)。 詳細については、SAP のドキュメントを参照してください。

## <a name="next-steps"></a>次の手順

**オンプレミス データ ゲートウェイ**と **DirectQuery** の詳細については、次のリソースをご覧ください。

* [オンプレミス データ ゲートウェイとは](/data-integration/gateway/service-gateway-onprem)
* [Power BI の DirectQuery](desktop-directquery-about.md)
* [DirectQuery でサポートされるデータ ソース](desktop-directquery-data-sources.md)
* [DirectQuery と SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
