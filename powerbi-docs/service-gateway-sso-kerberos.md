---
title: オンプレミス データ ソースへのシングル サインオン (SSO) に Kerberos を使用する
description: Power BI からオンプレミス データ ソースへの SSO を有効にするようにゲートウェイの Kerberos を構成します
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/25/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 5445326f302f5ffef39ab387b3a22a336efb6550
ms.sourcegitcommit: c799941c8169cd5b6b6d63f609db66ab2af93891
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70391876"
---
# <a name="use-kerberos-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Power BI からオンプレミス データ ソースへの SSO (シングル サインオン) に Kerberos を使用する

[Kerberos の制約付き委任](/windows-server/security/kerberos/kerberos-constrained-delegation-overview)を使用して、シームレスなシングル サインオン (SSO) 接続を有効にします。 SSO を有効にすると、Power BI レポートおよびダッシュボードはオンプレミスのソースからデータを簡単に更新できるようになります。

## <a name="supported-data-sources"></a>サポートされているデータ ソース

現在サポートされているデータ ソースは次のとおりです。

* SQL Server
* SAP HANA
* SAP BW
* Teradata
* Spark
* Impala

[Security Assertion Markup Language (SAML)](service-gateway-sso-saml.md) を使用した SAP HANA もサポートされています。

### <a name="sap-hana"></a>SAP HANA

SAP HANA で SSO を有効にするには、次の手順に従います。

* SAP HANA サーバーが必要な最小バージョンを実行していることを確認します。これは、SAP HANA サーバー プラットフォームのレベルによって異なります。
  * [HANA 2 SPS 01 改訂 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 改訂 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 改訂 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* ゲートウェイ マシンに、SAP の最新の HANA ODBC ドライバーをインストールする。  最小バージョンは 2017 年 8 月の HANA ODBC バージョン 2.00.020.00 です。

Kerberos を使用した SAP HANA の SSO の設定に関する詳細については、SAP HANA セキュリティ ガイドの「[「Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html)」(Kerberos を用いたシングル サインオン) をご覧ください。 また、このページからのリンク (特に SAP Note 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory) もご確認ください。

## <a name="prepare-for-kerberos-constrained-delegation"></a>Kerberos の制約付き委任のために準備する

Kerberos の制約付き委任が正しく機能するためには、"*サービス プリンシパル名*" (SPN) やサービス アカウントでの委任の設定など、いくつかの項目の構成を行う必要があります。

### <a name="prerequisite-1-install-and-configure-the-microsoft-on-premises-data-gateway"></a>前提条件 1:Microsoft オンプレミス データ ゲートウェイをインストールして構成する

オンプレミス データ ゲートウェイのこのリリースでは、インプレース アップグレードだけでなく既存のゲートウェイの引き継ぎの設定がサポートされています。

### <a name="prerequisite-2-run-the-gateway-windows-service-as-a-domain-account"></a>前提条件 2:ゲートウェイの Windows サービスをドメイン アカウントとして実行する

標準のインストールでは、ゲートウェイは、コンピューター ローカル サービス アカウントとして実行されます (具体的には、*NT Service\PBIEgwService*)。

![サービス アカウントのスクリーン ショット](media/service-gateway-sso-kerberos/service-account.png)

Azure Active Directory (Azure AD) インスタンスが既に (Azure AD DirSync/Connect を使って) ローカルの Active Directory インスタンスと同期されている場合を除き、Kerberos の制約付き委任を有効にするには、ゲートウェイをドメイン アカウントとして実行する必要があります。 ドメイン アカウントに切り替えるには、「[ゲートウェイ サービス アカウントの変更](/data-integration/gateway/service-gateway-service-account)」を参照してください。

> [!NOTE]
> Azure AD Connect が構成済みで、かつユーザー アカウントが同期済みの場合、実行時にゲートウェイ サービスでローカル Azure AD 参照を実行する必要はありません。 ゲートウェイ サービスに対してローカル サービス SID を使用できます (ドメイン アカウントは必要ありません)。 この記事で説明する Kerberos の制約付き委任の構成手順は、その構成と同じです。 それらは、ドメイン アカウントではなく、Azure AD でゲートウェイのコンピューター オブジェクトに単に適用されます。

### <a name="prerequisite-3-have-domain-admin-rights-to-configure-spns-setspn-and-kerberos-constrained-delegation-settings"></a>前提条件 3:SPN (SetSPN) および Kerberos 制約付き委任の設定を構成するためのドメイン管理者権限がある

ドメイン管理者権限を要求せず、ドメイン管理者が SPN および Kerberos 委任を構成する権限を一時的または永続的に他のユーザーに許可することはお勧めしません。 次のセクションでは、推奨される構成手順について詳しく説明します。

## <a name="configure-kerberos-constrained-delegation-for-the-gateway-and-data-source"></a>ゲートウェイとデータ ソースに対して Kerberos の制約付き委任を構成する

ドメイン管理者は、ゲートウェイ サービスのドメイン アカウントの SPN を構成し、ゲートウェイ サービスのドメイン アカウントに委任設定を構成します。

### <a name="configure-an-spn-for-the-gateway-service-account"></a>ゲートウェイ サービス アカウントに SPN を構成する

最初に、ゲートウェイ サービス アカウントとして使われるドメイン アカウントに SPN が既に作成されているかどうかを調べます。

1. ドメイン管理者として **[Active Directory ユーザーとコンピューター]** を開きます。

2. ドメインを右クリックし、 **[検索]** を選んで、ゲートウェイ サービス アカウントのアカウント名を入力します。

3. 検索結果で、ゲートウェイ サービス アカウントを右クリックして、 **[プロパティ]** を選択します。

4. **[委任]** タブが **[プロパティ]** ダイアログ ボックスに表示されている場合、SPN は既に作成されています。 委任設定の構成に進むことができます。

    **[委任]** タブが **[プロパティ]** ダイアログ ボックスにない場合、そのアカウントに SPN を手動で作成できます。 これにより、 **[委任]** タブが追加されます。Windows に付属する [setspn ツール](https://technet.microsoft.com/library/cc731241.aspx)を使用してください (SPN を作成するにはドメイン管理者権限が必要です)。

    たとえば、ゲートウェイ サービス アカウントが "PBIEgwTest\GatewaySvc" で、ゲートウェイ サービスを実行しているコンピューターの名前が **Machine1** であるとします。 この例のコンピューターにゲートウェイ サービス アカウントの SPN を設定するには、次のコマンドを実行します。

    ![SPN を設定するコマンドのイメージ](media/service-gateway-sso-kerberos/set-spn.png)

    このステップが完了したら、委任設定の構成に進むことができます。

### <a name="configure-delegation-settings-on-the-gateway-service-account"></a>ゲートウェイ サービス アカウントで委任設定を構成する

2 番目の構成要件は、ゲートウェイ サービス アカウントでの委任の設定です。 この手順は複数のツールを使って実行できます。 ここでは [Active Directory ユーザーとコンピューター] を使用します。これは、ディレクトリ内の情報の管理と発行を行うための Microsoft 管理コンソール (MMC) のスナップインです。 既定ではドメイン コントローラーで使用できます。 他のコンピューターで Windows 機能の構成を使用してこれを有効にすることもできます。

プロトコル遷移のある Kerberos の制約付き委任を構成する必要があります。 制約付き委任では、委任先のサービスを明示的に指定する必要があります。 たとえば、SQL Server または SAP HANA サーバーだけが、ゲートウェイ サービス アカウントからの委任呼び出しを受け入れます。

このセクションでは、基になるデータ ソース (SQL Server、SAP HANA、Teradata、Spark など) に対して SPN を既に構成してあるものとします。 これらのデータ ソース サーバーの SPN を構成する方法については、それぞれのデータベース サーバーの技術ドキュメントを参照してください。 「[My Kerberos Checklist](https://techcommunity.microsoft.com/t5/SQL-Server-Support/My-Kerberos-Checklist-8230/ba-p/316160)」 (私の Kerberos チェックリスト) というブログ投稿の「*What SPN does your app require?* 」 (あなたのアプリに必要な SPN は?) という見出しで始まる内容も参照できます。

次の手順では、ゲートウェイ コンピューターと、SQL Server を実行しているデータベース サーバーの 2 つのコンピューターで構成されるオンプレミス環境を想定しています。 また、この例では次の設定と名前を使用します。

* ゲートウェイ コンピューターの名前:**PBIEgwTestGW**
* ゲートウェイ サービス アカウント:**PBIEgwTest\GatewaySvc** (アカウントの表示名:Gateway Connector)
* SQL Server データ ソースのコンピューター名:**PBIEgwTestSQL**
* SQL Server データ ソースのサービス アカウント:**PBIEgwTest\SQLService**

委任設定を構成する方法を次に示します。

1. ドメイン管理者権限で、 **[Active Directory ユーザーとコンピューター]** を開きます。

2. ゲートウェイのサービス アカウント (**PBIEgwTest\GatewaySvc**) を右クリックし、 **[プロパティ]** を選択します。

3. **[委任]** タブを選びます。

4. **[指定されたサービスへの委任でのみこのコンピューターを信頼する]**  >  **[任意の認証プロトコルを使う]** をオンにします。

5. **[このアカウントが委任された資格情報を提示できるサービス]** で **[追加]** を選択します。

6. 新しいダイアログ ボックスで、 **[ユーザーまたはコンピューター]** を選びます。

7. データ ソースのサービス アカウントを入力します。たとえば、SQL Server データ ソースに **PBIEgwTest\SQLService** のようなサービス アカウントが存在することがあります。 アカウントが追加されたら、 **[OK]** を選択します。

8. データベース サーバー用に作成した SPN を選びます。 この例では、SPN は **MSSQLSvc** で始まります。 データベース サービスに FQDN と NetBIOS 両方の SPN を追加した場合は、両方とも選びます。 1 つだけしか表示されない場合があります。

9. **[OK]** を選択します。 リストに SPN が表示されます。

    必要に応じて、 **[展開済み]** を選んで FQDN SPN と NetBIOS SPN を両方表示できます。 **[展開済み]** をオンにした場合、ダイアログ ボックスの表示は次のようになります。 **[OK]** を選択します。

    ![[ゲートウェイ コネクタのプロパティ] ダイアログ ボックスのスクリーン ショット](media/service-gateway-sso-kerberos/gateway-connector-properties.png)

最後に、ゲートウェイ サービス (この例では **PBIEgwTestGW**) が実行されているコンピューターで、ゲートウェイ サービス アカウントにローカル ポリシーの **[認証後にクライアントを偽装]** と **[オペレーティング システムの一部として機能]** (SeTcbPrivilege) を付与する必要があります。 この構成は、ローカル グループ ポリシー エディター (**gpedit**) で実行と確認ができます。

1. ゲートウェイ コンピューターで、*gpedit.msc* を実行します。

1. **[ローカル コンピューター ポリシー]**  >  **[コンピューターの構成]**  >  **[Windows の設定]**  >  **[セキュリティの設定]**  >  **[ローカル ポリシー]**  >  **[ユーザー権利の割り当て]** の順に移動します。

    ![ローカル コンピューター ポリシーのフォルダー構造のスクリーン ショット](media/service-gateway-sso-kerberos/user-rights-assignment.png)

1. **[ユーザー権利の割り当て]** で、ポリシーの一覧から **[認証後にクライアントを偽装]** を選択します。

    ![クライアント ポリシーの偽装のスクリーン ショット](media/service-gateway-sso-kerberos/impersonate-client.png)

    右クリックして、 **[プロパティ]** を開きます。 アカウントの一覧を確認します。 ゲートウェイ サービス アカウント (**PBIEgwTest\GatewaySvc**) が含まれている必要があります。

1. **[ユーザー権利の割り当て]** で、ポリシーの一覧から **[オペレーティング システムの一部として機能 (SeTcbPrivilege)]** を選択します。 アカウントの一覧にゲートウェイ サービス アカウントが含まれることも確認します。

1. **オンプレミス データ ゲートウェイ** サービス プロセスを再起動します。

SAP HANA を使用している場合は、次のパフォーマンスが若干向上させるために次の追加手順を実行することをお勧めします。

1. ゲートウェイのインストール ディレクトリで、次の構成ファイルを見つけて開きます: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*。

1. *FullDomainResolutionEnabled* プロパティを見つけて、その値を *True* に変更します。

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

## <a name="run-a-power-bi-report"></a>Power BI レポートを実行する

すべての構成手順が完了すると、Power BI の **[Manage Gateway]\(ゲートウェイの管理\)** ページを使ってデータ ソースを構成することができます。 その後、 **[詳細設定]** で SSO を有効にし、そのデータ ソースに対するレポートとデータセットのバインドを発行します。

![詳細設定オプションのスクリーンショット](media/service-gateway-sso-kerberos/advanced-settings.png)

この構成は、ほとんどの場合に機能します。 ただし、Kerberos については、環境に応じて構成が異なる可能性があります。 レポートがまだ読み込まれない場合は、ドメイン管理者に連絡してさらに詳しく調査します。

## <a name="configure-sap-bw-for-sso-using-commoncryptolib"></a>CommonCryptoLib を使用して SSO 用に SAP BW を構成する

Kerberos がゲートウェイと連携するしくみを理解できたので、SAP Business Warehouse (SAP BW) に対して SSO を構成できます。 次の手順は、この記事で前述したように、[Kerberos の制約付き委任の準備](#prepare-for-kerberos-constrained-delegation)が既にできていることを前提としています。

> [!NOTE]
> これらの手順では、SAP BW **アプリケーション** サーバーの SSO 設定について説明しています。 現在、Microsoft では、SAP BW **メッセージ** サーバーへの SSO 接続をサポートしていません。

1. 自分の BW サーバーが Kerberos SSO 用に正しく構成されていることを確認します。 そうなっていれば、SSO を使用して、SAP GUI などの SAP ツールで自分の BW サーバーにアクセスできるはずです。 設定の手順の詳細については、次を参照してください: 「[SAP シングル サインオン: Kerberos/SPNEGO による認証](https://blogs.sap.com/2017/07/27/sap-single-sign-on-authenticate-with-kerberosspnego/)」。 自分の BW サーバーでは、SNC ライブラリとして CommonCryptoLib を使用し、"CN=" で始まる SNC 名 (たとえば "CN=BW1") を付ける必要があります。 SNC 名の要件の詳細については、「[Kerberos 構成の SNC パラメーター](https://help.sap.com/viewer/df185fd53bb645b1bd99284ee4e4a750/3.0/en-US/360534094511490d91b9589d20abb49a.html)」(snc/identity/as パラメーター) を参照してください。

1. まだ行っていない場合は、「[Kerberos の制約付き委任のために準備する](https://docs.microsoft.com/power-bi/service-gateway-sso-kerberos#prepare-for-kerberos-constrained-delegation)」の手順を完了してください。 自分のゲートウェイ サービス ユーザーが、Active Directory 環境内で自分の BW アプリケーション サーバーを表すサービス ユーザーに、委任された資格情報を提示するように構成されていることを確認します。

1. まだ行っていない場合は、x64 バージョンの [SAP .NET Connector](https://support.sap.com/en/product/connectors/msnet.html) を、ゲートウェイがインストールされているコンピューターにインストールしてください。 コンポーネントがインストールされているかどうかを確認するには、Power BI Desktop で自分の BW サーバーに接続してみます。 2\.0 実装を使用して接続できない場合は、.NET Connector がインストールされていません。

1. ゲートウェイがインストールされているコンピューター上で、SAP Secure Login Client (SLC) が実行されていないことを確認します。 SLC は、SSO のために Kerberos を使用するゲートウェイの機能を妨げる可能性がある方法で、Kerberos チケットをキャッシュします。 SLC がインストールされている場合は、アンインストールするか、SAP Secure Login Client を必ず終了します。ゲートウェイを使用して SSO 接続を試行する前に、システム トレイ内のアイコンを右クリックし、[Log Out and Exit]\(ログアウトして終了\) を選択します。 SLC では、Windows Server マシン上での使用はサポートされていません。 詳細については、[SAP Note 2780475](https://launchpad.support.sap.com/#/notes/2780475) を参照してください (s-user が必要)。

    ![SAP Secure Login Client](media/service-gateway-sso-kerberos/sap-secure-login-client.png)

    SLC をアンインストールするか、 **[Log Out** and **Exit]\(ログアウトして終了\)** を選択した場合は、コマンド ウィンドウを開いて「`klist purge`」と入力して、ゲートウェイ経由で SSO 接続を試行する前に、キャッシュされた Kerberos チケットをクリアします。

1. SAP スタート パッドから CommonCryptoLib (sapcrypto.dll) バージョン **8.5.25 以上**をダウンロードし、それを自分のゲートウェイ マシン上のフォルダーにコピーします。 sapcrypto.dll をコピーしたのと同じディレクトリに、次の内容が含まれた sapcrypto.ini という名前のファイルを作成します。

    ```
    ccl/snc/enable_kerberos_in_client_role = 1
    ```

    .ini ファイルには、ゲートウェイ シナリオで SSO を有効にするために CommonCryptoLib が必要とする構成情報が含まれています。

    > [!NOTE]
    > これらのファイルは同じ場所に格納する必要があります。つまり、 _/path/to/sapcrypto/_ に sapcrypto.ini と sapcrypto.dll の両方を含める必要があります。

    サービス ユーザーが偽装するゲートウェイ サービス ユーザーと Active Directory (AD) ユーザーの両方に、両方のファイルに対する読み取りおよび実行アクセス許可が必要です。 Authenticated Users グループに .ini ファイルと .dll ファイルの両方に対するアクセス許可を付与することをお勧めします。 テストを目的として、ゲートウェイ サービス ユーザーと偽装したユーザーの両方に、これらのアクセス許可を明示的に付与することもできます。 次のスクリーンショットでは、Authenticated Users グループに sapcrypto.dll に対する**読み取りと実行**のアクセス許可を付与しました。

    ![Authenticated Users](media/service-gateway-sso-kerberos/authenticated-users.png)

1. SAP Business Warehouse サーバーのデータ ソースがない場合は、Power BI サービスの **[ゲートウェイの管理]** ページで、データ ソースを追加します。 SSO 接続を通らせるゲートウェイに関連付けられている BW データ ソースが既にある場合は、それを編集する準備をします。

    **SNC ライブラリ**には、**SNC\_LIB または SNC\_LIB\_64 環境変数**か、**カスタム**を選択してください。 **SNC\_LIB** オプションを選択する場合は、ゲートウェイ マシン上の SNC\_LIB\_64 環境変数の値を、ゲートウェイ マシン上の sapcrypto.dll のコピーの絶対パス (C:\Users\Test\Desktop\sapcrypto.dll など) に設定する必要があります。 **[カスタム]** を選択した場合は、 **[ゲートウェイの管理]** ページに表示される [カスタム SNC ライブラリ パス] フィールドに、sapcrypto .dll の絶対パスを貼り付けます。

    **[詳細設定]** の下で、 **[DirectQuery クエリには Kerberos 経由で SSO を使用します]** チェック ボックスがオンになっていることを確認してください。 入力するユーザー名は、BW サーバーに接続するためのアクセス許可だけを備えている必要があります。また、これは主に、データ ソース接続の作成後、それをテストするために使用されます。 ユーザーは、インポートベースのデータセットから作成されたレポートを更新するためにも使用されます (存在する場合)。 **[基本]** 認証を選択した場合は、BW ユーザーを指定する必要があります。 **[Windows]** 認証を選択した場合は、SAP GUI の SU01 トランザクションを通じて BW ユーザーにマップされている Windows Active Directory ユーザーを指定する必要があります。 残りのフィールド ( **[システム番号] **、** [クライアント ID] **、** [SNC パートナー名]** など) は、SSO を介して自分の BW サーバーに接続するために Power BI Desktop に入力する情報と一致する必要があります。 **[適用]** を選択し、テスト接続が成功したことを確認します。

    ![認証方法](media/service-gateway-sso-kerberos/authentication-method.png)

1. CCL\_PROFILE システム環境変数を作成し、sapcrypto.ini を指すように設定します。

    ![CCL\_PROFILE システム環境変数](media/service-gateway-sso-kerberos/ccl-profile-variable.png)

    sapcrypto .dll と .ini ファイルは同じ場所に存在する必要があることに注意してください。 sapcrypto.ini がデスクトップ上にある上の例では、sapcrypto.dll もデスクトップ上にある必要があります。

1. ゲートウェイ サービスを再起動します。

    ![ゲートウェイ サービスを再起動する](media/service-gateway-sso-kerberos/restart-gateway-service.png)

1. Power BI Desktop で **DirectQuery ベースの** BW レポートを発行します。 このレポートでは、Power BI サービスにサインインする Azure Active Directory (AAD) ユーザーにマップされている BW ユーザーがアクセスできるデータを使用する必要があります。 更新がどのように動作するかによっては、インポートの代わりに DirectQuery を使用する必要があります。 インポートベースのレポートを更新する場合、ゲートウェイでは、BW データ ソースを作成したときに **[ユーザー名]** と **[パスワード]** のフィールドに入力した資格情報が使用されます。 言い換えると、Kerberos SSO は使用**されません**。 また、複数のゲートウェイがある場合は、発行時に、BW SSO 用に構成したゲートウェイを選択してください。 これで、Power BI サービスで、発行したデータセットに基づいて、レポートを更新したり新しいレポートを作成したりできるようになりました。

### <a name="troubleshooting"></a>トラブルシューティング

Power BI サービスでレポートを更新できない場合は、ゲートウェイ トレース、CPIC トレース、および CommonCryptoLib トレースを使用して、問題の診断に役立てることができます。 CPIC トレースと CommonCryptoLib は SAP 製品であるため、Microsoft ではそれらを直接サポートすることはできません。 BW への SSO アクセスを許可される Active Directory ユーザーについては、一部の Active Directory 構成で、ゲートウェイがインストールされているマシンの Administrators グループのメンバーであることが必要になる場合があります。

1. **ゲートウェイ ログ:** 単に問題を再現し、[ゲートウェイ アプリ](https://docs.microsoft.com/data-integration/gateway/service-gateway-app)を開き、 **[診断]** タブに移動して、 **[ログのエクスポート]** を選択します。

    ![ゲートウェイ ログをエクスポートする](media/service-gateway-sso-kerberos/export-gateway-logs.png)

1. **CPIC トレース:** CPIC トレースを有効にするには、次の 2 つの環境変数を設定します。CPIC\_TRACE と CPIC\_TRACE\_DIR です。 最初の変数はトレース レベルを設定し、2 番目の変数はトレース ファイルのディレクトリを設定します。 ディレクトリは、Authenticated Users グループのメンバーが書き込み可能な場所である必要があります。 CPIC\_TRACE を 3 に設定し、CPIC\_TRACE\_DIR をトレース ファイルの書き込み先にする任意のディレクトリに設定します。

    ![CPIC トレース](media/service-gateway-sso-kerberos/cpic-tracing.png)

    問題を再現し、CPIC\_TRACE\_DIR にトレース ファイルが含まれていることを確認します。

1. **CommonCryptoLib トレース:** 前に作成した sapcrypto.ini ファイルに 2 行を追加して、CommonCryptoLib トレースを有効にします。

    ```
    ccl/trace/level=5
    ccl/trace/directory=<drive>:\logs\sectrace
    ```

    _ccl/trace/directory_ オプションを、Authenticated Users グループのメンバーが書き込み可能な場所に必ず変更します。 または、新しい .ini ファイルを作成して、この動作を変更します。 sapcrypto.ini および sapcrypto.dll と同じディレクトリに、次の内容が含まれた sectrace.ini という名前のファイルを作成します。  DIRECTORY オプションを、認証されたユーザーが書き込むことができる自分のマシン上の場所に置き換えます。

    ```
    LEVEL = 5
    
    DIRECTORY = <drive>:\logs\sectrace
    ```

    ここで問題を再現し、DIRECTORY によって指されている場所にトレース ファイルが含まれていることを確認します。 完了したら、CPIC および CCL トレースを無効にしてください。

    CommonCryptoLib トレースの詳細については、[SAP Note 2491573](https://launchpad.support.sap.com/#/notes/2491573) (s-user が必要) を参照してください。

## <a name="configure-sap-bw-for-sso-using-gsskrb5gx64krb5"></a>gsskrb5 または gx64krb5 を使用して SAP BW を SSO 用に構成する

自分の SNC ライブラリとして CommonCryptoLib を使用できない場合は、代わりに gsskrb5 または gx64krb5 を使用できます。 ただし、設定手順はかなり複雑であり、SAP では gsskrb5 のサポートが提供されなくなっています。

このガイドは、可能な限り包括的になるように書かれています。 一部の手順を既に完了している場合は、それをスキップできます。 たとえば、SAP BW サーバーのサービス ユーザーを既に作成して SPN をマップしてある場合や、`gsskrb5` ライブラリを既にインストールしてある場合です。

### <a name="set-up-gsskrb5gx64krb5-on-client-machines-and-the-sap-bw-server"></a>クライアント コンピューターと SAP BW サーバーに gsskrb5/gx64krb5 を設定する

> [!NOTE]
> `gsskrb5/gx64krb5` は、SAP によって積極的にサポートされなくなりました。 詳細については、[SAP Note 352295](https://launchpad.support.sap.com/#/notes/352295) をご覧ください。 また、データ ゲートウェイから SAP BW メッセージ サーバーへの SSO 接続が `gsskrb5/gx64krb5` によって許可されない点についても注意してください。 SAP BW アプリケーション サーバーへの接続のみが可能です。 これで、セットアップ プロセスを簡単にする SNC ライブラリとして、sapcrypto/CommonCryptoLib を使用できるようになりました。 

ゲートウェイを介して SSO 接続を完了するには、クライアントとサーバーの両方で `gsskrb5` が使用されている必要があります。

1. お使いのビットに合わせて `gsskrb5` または `gx64krb5` をダウンロードします。詳細は [SAP Note 2115486](https://launchpad.support.sap.com/) にあります (SAP s-user が必要です)。 バージョンが 1.0.11.x 以上になっていることを確認します。

1. ゲートウェイ インスタンスによって (また、SAP ログオンを使用して SSO 接続をテストする場合は、SAP GUI によっても) アクセスできるゲートウェイ コンピューター上の場所に、ライブラリを配置します。

1. SAP BW サーバーによってアクセスできる SAP BW サーバー コンピューター上の場所に、別のコピーを配置します。

1. クライアント コンピューターとサーバー コンピューター上で、`SNC_LIB` 環境変数または `SNC_LIB_64` 環境変数を、それぞれ gsskrb5.dll または gx64krb5.dll の場所を指すように設定します。 これらのライブラリのうち、両方ではなく、1 つだけ必要であることにご留意ください。

### <a name="create-a-sap-bw-service-user-and-enable-snc-communication"></a>SAP BW サービス ユーザーを作成し、SNC の通信を有効にする

既に実行したゲートウェイ構成に加えて、SAP BW 固有のいくつかの追加手順があります。 このドキュメントの「[ゲートウェイ サービス アカウントで委任設定を構成する](#configure-delegation-settings-on-the-gateway-service-account)」セクションは、基になるデータ ソースに対して SPN を既に構成していることを前提としています。 SAP BW に対してこの構成を実行するには、次の手順に従います。

1. Active Directory ドメイン コントローラー サーバーで、Active Directory 環境内の SAP BW アプリケーション サーバーに対してサービス ユーザー (最初は単純な Active Directory ユーザー) を作成します。 その後、このユーザーに SPN を割り当てます。

    SAP では `SAP/` で SPN を始めることが推奨されていますが、`HTTP/` などの他のプレフィックスも使用できるはずです。 `SAP/` の後に続く文字は開発者次第です。1 つのオプションとしては、SAP BW サーバーのサービス ユーザーのユーザー名を使用します。 たとえば、サービス ユーザーとして `BWServiceUser@\<DOMAIN\>` を作成した場合、SPN `SAP/BWServiceUser` を使用できます。 SPN のマッピングを設定する方法の 1 つは、setspn コマンドです。 たとえば、先ほど作成したサービス ユーザーの SPN を設定するには、ドメイン コントローラー コンピューターでコマンド ウィンドウからコマンド: `setspn -s SAP/ BWServiceUser DOMAIN\ BWServiceUser` を実行します。 詳しくは、SAP BW のドキュメントをご覧ください。

1. サービス ユーザーに、SAP BW アプリケーション サーバーへのアクセス権を付与します。

    1. SAP BW サーバー コンピューターで、SAP BW サーバーのローカル管理者グループにサービス ユーザーを追加します。 [コンピューターの管理] プログラムを開き、サーバーのローカル管理者グループをダブルクリックします。

        ![[コンピューターの管理] プログラムのスクリーン ショット](media/service-gateway-sso-kerberos/computer-management.png)

    1. ローカル管理者グループをダブルクリックし、 **[追加]** を選んで、グループにサービス ユーザーを追加します。 **[名前の確認]** を選んで、名前を正しく入力したことを確認します。 **[OK]** を選択します。

1. SAP BW サーバーのサービス ユーザーを、SAP BW サーバー コンピューターで SAP BW サーバー サービスを開始するユーザーとして設定します。

    1. **[ファイル名を指定して実行]** を開き、「Services.msc」と入力します。 SAP BW アプリケーション サーバー インスタンスに対応するサービスを探します。 それを右クリックし、 **[プロパティ]** を選択します。

        ![[プロパティ] が強調表示されている [サービス] のスクリーン ショット](media/service-gateway-sso-kerberos/server-properties.png)

    1. **[ログオン]** タブに切り替えて、ユーザーを SAP BW サービス ユーザーに変更します。 ユーザーのパスワードを入力し、 **[OK]** を選択します。

1. SAP ログオンでサーバーにサインインし、RZ10 トランザクションを使用して次のプロファイル パラメーターを設定します。

    1. snc/identity/as プロファイル パラメーターを p:\<作成した SAP BW サービス ユーザー\> (p:BWServiceUser@MYDOMAIN.COM など) に設定します。 サービス ユーザーの UPN の前にある p: に注意してください。 SNC ライブラリとして Common Crypto Lib を使用するときのような、p:CN= ではありません。

    1. snc/gssapi\_lib プロファイル パラメーターを \<サーバー コンピューター上の gsskrb5.dll/gx64krb5.dll へのパス (使用するライブラリは OS のビット数によって異なります)\> に設定します。 SAP BW アプリケーション サーバーがアクセスできる場所にライブラリを配置してください。

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

    1. プロパティ snc/enable を 1 に設定します。

1. これらのプロファイル パラメーターを設定してから、サーバー コンピューターで SAP 管理コンソールを開き、SAP BW インスタンスを再起動します。 サーバーが起動しない場合は、プロファイル パラメーターを正しく設定したことを確認します。 プロファイル パラメーターの設定の詳細については、[SAP のドキュメント](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm)を参照してください。 また、問題が発生した場合、このセクションで後述するトラブルシューティング情報も参照できます。

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>SAP BW ユーザーを Active Directory ユーザーにマップする

Active Directory ユーザーを SAP BW アプリケーション サーバー ユーザーにマップし、SAP ログオンで SSO 接続をテストします。

1. SAP ログオンを使用して、SAP BW サーバーにサインインします。 トランザクション SU01 を実行します。

1. **[ユーザー]** で、SSO 接続を有効にする対象の SAP BW ユーザーを入力します (前のスクリーンショットでは、BIUSER のアクセス許可を設定しています)。 SAP ログオン ウィンドウの左上隅近くにある**編集**アイコン (ペンのイメージ) を選択します。

    ![SAP BW [User maintenance]\(ユーザーの管理\) 画面のスクリーン ショット](media/service-gateway-sso-kerberos/user-maintenance.png)

1. **[SNC]** タブを選びます。SNC 名の入力ボックスに、「p:\<Active Directory ユーザー\>@\<ドメイン\>」と入力します。 Active Directory ユーザーの UPN の前に指定する必須の p: に注意してください。 指定した Active Directory ユーザーは、SAP BW アプリケーション サーバーへの SSO アクセスを有効にする対象の個人または組織に属している必要があります。 たとえば、ユーザー testuser\@TESTDOMAIN.COM に対して SSO アクセスを有効にする場合、「p:testuser@TESTDOMAIN.COM」と入力します。

    ![SAP BW [Maintain Users]\(ユーザー管理\) 画面のスクリーン ショット](media/service-gateway-sso-kerberos/maintain-users.png)

1. 画面の左上隅近くにある **[保存]** アイコン (フロッピー ディスクのイメージ) を選択します。

### <a name="test-sign-in-by-using-sso"></a>SSO を使用したサインインをテストする

サーバーにサインインできることを確認します。 先ほど SSO アクセスを有効にした対象の Active Directory ユーザーとして、SSO を介した SAP ログオンを使用します。

1. 先ほど SSO アクセスを有効にした対象の Active Directory ユーザーとして、SAP ログオンがインストールされているコンピューターにサインインします。 SAP ログオンを起動し、新しい接続を作成します。

1. **[Create New System Entry]\(新しいシステム エントリの作成\)** 画面で **[User Specified System]\(ユーザー指定のシステム\)**  >  **[次へ]** を選択します。

    ![[Create New System Entry]\(新しいシステム エントリの作成\) 画面のスクリーン ショット](media/service-gateway-sso-kerberos/new-system-entry.png)

1. 次の画面で、アプリケーション サーバー、インスタンス番号、システムの ID などの該当する詳細情報を入力します。 その後、 **[完了]** を選択します。

1. 新しい接続を右クリックし、 **[プロパティ]** を選びます。 **[ネットワーク]** タブを選びます。 **[SNC Name]\(SNC 名\)** テキスト ボックスに、「p:\<SAP BW サービス ユーザーの UPN\>」(p:BWServiceUser@MYDOMAIN.COM など) と入力します。 **[OK]** を選択します。

    ![[System Entry Properties]\(システム エントリ プロパティ\) 画面のスクリーン ショット](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. 先ほど作成した接続をダブルクリックして、SAP BW サーバーへの SSO 接続を試みます。 この接続に成功した場合は、次の手順に進みます。 そうでない場合は、このドキュメントの前述の手順を参照して、接続が正常に完了したことを確認するか、または次のトラブルシューティングのセクションを参照します。 このコンテキストで SSO を使用して SAP BW サーバーに接続できない場合は、ゲートウェイのコンテキストで SSO を使用して SAP BW サーバーに接続することはできません。

### <a name="troubleshoot-installation-and-connections"></a>インストールと接続のトラブルシューティングを行う

問題が発生した場合は、以下の手順に従って、SAP ログオンから gsskrb5 インストールと SSO 接続のトラブルシューティングを行います。

* サーバー ログ (サーバー コンピューター上の …work\dev\_w0) を参照すると、gsskrb5 のセットアップ手順の実行時に発生したエラーのトラブルシューティングに役立ちます。 これは、プロファイル パラメーターが変更された後に SAP BW サーバーが起動しない場合に特に役立ちます。

* ログオンに失敗した ために SAP BW サービスを開始できない場合、SAP BW "開始" ユーザーを設定するときに正しくないパスワードを指定した可能性があります。 SAP BW サービス ユーザーとして Active Directory 環境内のコンピューターにログインして、パスワードを確認します。

* SQL 資格情報に関するエラーが発生してサーバーが起動できない場合は、SAP BW データベースへの アクセス権がサービス ユーザーに付与されていることを確認してください。

* メッセージ "(GSS-API) specified target is unknown or unreachable (指定されたターゲットが不明であるか、または到達不能)" が表示される場合があります。 これは通常、正しくない SNC 名が指定されていることを意味します。 サービス ユーザーの UPN 以外には、"p:CN =" やクライアント アプリケーション内の何らかの項目ではなく、必ず "P:" だけを使用してください。

* メッセージ "(GSS-API) An invalid name was supplied (無効な名前が指定されました)" が表示される場合があります。 サーバーの SNC ID プロファイル パラメーターの値に "p:" が含まれることを確認してください。

* メッセージ "(SNC エラー) the specified module could not be found (指定したモジュールが見つかりませんでした)" が表示される場合があります。 これは通常、アクセスするのに高度な特権 (管理者権限) を必要とする場所に `gsskrb5.dll/gx64krb5.dll` を配置したことが原因で発生します。

### <a name="add-registry-entries-to-the-gateway-machine"></a>ゲートウェイ コンピューターにレジストリ エントリを追加する

必要なレジストリ エントリを、ゲートウェイがインストールされているコンピューターのレジストリ、および Power BI Desktop から接続するためのコンピューターに追加します。 実行するコマンドを次に示します。

1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="set-configuration-parameters-on-the-gateway-machine"></a>ゲートウェイ コンピューターで構成パラメーターを設定する

ユーザーが Azure AD ユーザーとして Power BI サービスにサインインできるように Azure AD Connect を構成しているかどうかにより、構成パラメーターの設定には 2 つのオプションがあります。

Azure AD Connect が構成されている場合は、以下の手順のようにします。

1. メインのゲートウェイの構成ファイル `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll` を開きます。 このファイルは、既定では C:\Program Files\On-premises data gateway に格納されています。

1. **FullDomainResolutionEnabled** プロパティが **True** に設定されていて、**SapHanaSsoRemoveDomainEnabled** が **False** に設定されていることを確認します。

1. 構成ファイルを保存します。

1. タスク マネージャーの **[サービス]** タブで、ゲートウェイ サービスを右クリックして **[再起動]** を選択します。

    ![タスク マネージャーの [サービス] タブのスクリーン ショット](media/service-gateway-sso-kerberos/restart-gateway.png)

Azure AD Connect を構成していない場合は、Azure AD ユーザーにマップするすべての Power BI サービス ユーザーに対して次の手順を実行します。 次の手順では、SAP BW にサインインするアクセス許可を持つ Active Directory ユーザーに、Power BI サービス ユーザーを手動でリンクします。

1. メインのゲートウェイの構成ファイル `Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll` を開きます。 このファイルは、既定では C:\Program Files\On-premises data gateway に格納されています。

1. **ADUserNameLookupProperty** を `msDS-cloudExtensionAttribute1` に、**ADUserNameReplacementProperty** を `SAMAccountName` に設定します。 構成ファイルを保存します。

1. タスク マネージャーの **[サービス]** タブで、ゲートウェイ サービスを右クリックして **[再起動]** を選択します。

    ![タスク マネージャーの [サービス] タブのスクリーン ショット](media/service-gateway-sso-kerberos/restart-gateway.png)

1. Active Directory ユーザーの `msDS-cloudExtensionAttribute1` プロパティを設定します。 これは、SAP BW ユーザーにマップしたユーザーです。 Kerberos SSO を有効にする対象の Power BI サービス ユーザーに、このプロパティを設定します。 `msDS-cloudExtensionAttribute1` プロパティを設定する方法の 1 つは、[Active Directory ユーザーとコンピューター] MMC スナップインを使用することです (他の方法を使用することもできます)。

    1. 管理者ユーザーとしてドメイン コントローラー コンピューターにサインインします。

    1. スナップイン ウィンドウで**ユーザー** フォルダーを開き、SAP BW ユーザーにマップした Active Directory ユーザーをダブルクリックします。

    1. **[属性エディター]** タブを選びます。

        このタブが表示されない場合は、このタブを有効にする手順を確認するか、または別の方法を使用してプロパティを設定する必要があります。 いずれかの属性を選び、'M' キーを押して、先頭文字が 'm' の Active Directory プロパティに移動します。 `msDS-cloudExtensionAttribute1` プロパティを見つけてダブルクリックします。 その値を、Power BI サービスへのサインインに使用するユーザー名 (YourUser@YourDomain の形式) に設定します。

    1. **[OK]** を選択します。

        ![[文字列属性エディター] ダイアログ ボックスのスクリーン ショット](media/service-gateway-sso-kerberos/edit-attribute.png)

    1. **[適用]** を選びます。 **[値]** 列に正しい値が設定されていることを確認します。

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service"></a>Power BI サービスに新しい SAP BW アプリケーション サーバー データ ソースを追加する

この記事で前述した[レポートの実行](#run-a-power-bi-report)に関する手順に従って、ゲートウェイに SAP BW データ ソースを追加します。

1. データ ソース構成ウィンドウで、Power BI Desktop から SAP BW サーバーにサインインするときと同様に、アプリケーション サーバーの **[ホスト名]** 、 **[システム番号]** 、および **[クライアント ID]** を入力します。

1. **[SNC パートナー名]** フィールドに、「p:\<SAP BW サービス ユーザーにマップした SPN\>」と入力します。 たとえば、SPN が SAP/BWServiceUser@MYDOMAIN.COM の場合は、 **[SNC パートナー名]** フィールドに「p:SAP/BWServiceUser@MYDOMAIN.COM」と入力する必要があります。

1. SNC ライブラリには、**SNC_LIB** または **SNC_LIB_64** を選択します。 32 ビット シナリオには **SNC_LIB** を、64 ビット シナリオには **SNC_LIB_64** を使用します。 これらの環境変数がお使いのビットに基づき、それぞれ、gsskrb5.dll または gx64krb5.dll を指していることを確認します。

1. **[認証方法]** に **[Windows]** を選択した場合、 **[ユーザー名]** と **[パスワード]** は、SSO を使用して SAP BW サーバーにサインインする権限のある Active Directory ユーザーのユーザー名とパスワードにする必要があります。 つまり、これらは、SU01 トランザクションを使用して SAP BW ユーザーにマップされている Active Directory ユーザーに属している必要があります。 **[基本]** を選択した場合、 **[ユーザー名]** と **[パスワード]** をそれぞれ SAP BW ユーザーの名前とパスワードに設定してください。 これらの資格情報は、 **[DirectQuery クエリには Kerberos 経由で SSO を使用します]** ボックスがオンになっていない場合にのみ使用されます。

1. **[DirectQuery クエリには Kerberos 経由で SSO を使用します]** ボックスをオンにして、 **[適用]** を選択します。 テスト接続が成功しなかった場合は、前のセットアップおよび構成手順が正常に完了したことを確認します。

    ゲートウェイは常に入力された資格情報を使用してサーバーへのテスト接続を確立し、インポート ベースのレポートのスケジュールされた更新を行います。 **[DirectQuery クエリには Kerberos 経由で SSO を使用します]** がオンになっていて、ユーザーが直接クエリ ベースのレポートまたはデータセットにアクセスしている場合にのみ、ゲートウェイは SSO 接続の確立を試みます。

### <a name="test-your-setup"></a>セットアップをテストする

セットアップをテストするには、Power BI Desktop から Power BI サービスに DirectQuery レポートを発行します。 Azure AD ユーザーとして、または Azure AD ユーザーの `msDS-cloudExtensionAttribute1` プロパティにマップしたユーザーとして、Power BI サービスにサインインしていることを確認します。 セットアップが正常に完了したら、Power BI サービスで発行済みのデータセットからレポートを作成できます。 レポート内のビジュアルを通してデータを取り込むこともできます。

### <a name="troubleshoot-gateway-connectivity-issues"></a>ゲートウェイ接続の問題のトラブルシューティングを行う

1. ゲートウェイのログを確認します。 ゲートウェイ構成アプリケーションを開き、 **[診断]**  >  **[ログのエクスポート]** を選択します。 最新のエラーは、確認するログ ファイルの下部に記載されています。

    ![[診断] が強調表示されているオンプレミス データ ゲートウェイ アプリケーションのスクリーン ショット](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. SAP BW トレースを有効にし、生成されたログ ファイルを確認します。 さまざまな種類の SAP BW トレースを使用できます。 詳細については、SAP のドキュメントを参照してください。

## <a name="errors-from-an-insufficient-kerberos-configuration"></a>Kerberos の不適切な構成によるエラー

基になっているデータベース サーバーとゲートウェイが Kerberos の制約付き委任用に正しく構成されていない場合、データの読み込み失敗に関する次のエラー メッセージが表示される可能性があります。

![エラー メッセージのスクリーン ショット](media/service-gateway-sso-kerberos/load-data-error.png)

エラー メッセージ (DM_GWPipeline_Gateway_ServerUnreachable) に関連付けられている技術的な詳細は次のようになります。

![エラー メッセージの技術的な詳細のスクリーン ショット](media/service-gateway-sso-kerberos/server-unreachable.png)

つまり、ゲートウェイは元のユーザーを適切に偽装できず、データベース接続の試行は失敗しました。

## <a name="next-steps"></a>次の手順

**オンプレミス データ ゲートウェイ**と **DirectQuery** の詳細については、次のリソースをご覧ください。

* [オンプレミス データ ゲートウェイとは](/data-integration/gateway/service-gateway-onprem)
* [Power BI の DirectQuery](desktop-directquery-about.md)
* [DirectQuery でサポートされるデータ ソース](desktop-directquery-data-sources.md)
* [DirectQuery と SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
