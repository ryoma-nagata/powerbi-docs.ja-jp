---
title: データ ソースの管理 - Analysis Services
description: オンプレミス データ ゲートウェイとそのゲートウェイに属しているデータ ソースを管理する方法。 これは Analysis Services での多次元および表形式モードの両方に当てはまります。
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 93475f6476f8baad73229473bd3ce60db68a320b
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271637"
---
# <a name="manage-your-data-source---analysis-services"></a>データ ソースの管理 - Analysis Services

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

[オンプレミス データ ゲートウェイをインストール](/data-integration/gateway/service-gateway-install)したら、ゲートウェイで使用できる[データ ソースを追加する](service-gateway-data-sources.md#add-a-data-source)必要があります。 この記事では、スケジュールされた更新またはライブ接続に使用されるゲートウェイと Analysis Services データ ソースの操作方法について説明します。

Analysis Services へのライブ接続を設定する方法の詳細については、[こちらのビデオをご覧ください](https://www.youtube.com/watch?v=GPf0YS-Xbyo&feature=youtu.be)。

> [!NOTE]
> Analysis Services データ ソースを持っている場合は、Analysis Services サーバーと同じフォレストまたはドメインに結合しているコンピューターにゲートウェイをインストールする必要があります。

## <a name="add-a-data-source"></a>データ ソースの追加

データ ソースを追加する方法の詳細については、「[Add a data source](service-gateway-data-sources.md#add-a-data-source)」(データソースの追加) を参照してください。 多次元サーバーまたは表形式サーバーに接続している場合は、 **[データ ソースの種類]** として [Analysis Services] を選択します。

![Analysis Services データ ソースの追加](media/service-gateway-enterprise-manage-ssas/datasourcesettings2-ssas.png)

次に、 **[サーバー]** や **[データベース]** など、データ ソースの情報を入力する必要があります。 入力した **ユーザー名** と **パスワード** は、Analysis Services インスタンスに接続するために、ゲートウェイによって使用されます。

> [!NOTE]
> 入力した Windows アカウントには、接続先のインスタンスに対するサーバー管理者権限が必要です。 このアカウントのパスワードに有効期限が設定されている場合、データ ソースのパスワードが更新されないと、接続エラーになることがあります。 資格情報の格納方法の詳細については、「[Storing encrypted credentials in the cloud](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud)」(暗号化された資格情報のクラウドへの格納) を参照してください。

![データ ソース設定の入力](media/service-gateway-enterprise-manage-ssas/datasourcesettings3-ssas.png)

すべての情報を入力したら、 **[追加]** を選択します。 これで、オンプレミスである Analysis Services インスタンスに対するスケジュールされた更新またはライブ接続にこのデータ ソースを使用できます。 接続に成功すると、「 *接続成功* 」というメッセージが表示されます。

![接続の状態の表示](media/service-gateway-enterprise-manage-ssas/datasourcesettings4.png)

### <a name="advanced-settings"></a>詳細設定

必要に応じて、データ ソースのプライバシー レベルを構成できます。 これにより、データを結合できる方法を制御します。 これは、スケジュールされた更新にのみ使用します。 ライブ接続には適用されません。 データ ソースのプライバシー レベルの詳細については、「[プライバシーレベル (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540)」を参照してください。

![プライバシー レベルの設定](media/service-gateway-enterprise-manage-ssas/datasourcesettings9.png)

## <a name="usernames-with-analysis-services"></a>Analysis Services でのユーザー名

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qb5EEjkHoLg" frameborder="0" allowfullscreen></iframe>

Analysis Services に接続されているレポートをユーザーが操作するたびに、有効なユーザー名がゲートウェイに渡され、次にオンプレミスの Analysis Services サーバーに渡されます。 Power BI にサインインするときに使用する電子メール アドレスは、私たちが有効なユーザーとして Analysis Services に渡すものです。 これは、接続プロパティ [EffectiveUserName](https://msdn.microsoft.com/library/dn140245.aspx#bkmk_auth) に渡されます。 この電子メール アドレスは、ローカルの Active Directory ドメイン内で定義されているユーザー プリンシパル名 (UPN) と一致する必要があります。 UPN は、Active Directory アカウントのプロパティです。 その Windows アカウントは、Analysis Services ロールに存在する必要があります。 Active Directory での一致を検出できない場合は、ログインは正常に実行されません。 Active Directory とユーザーの名前付けの詳細については、「[User Naming Attributes](https://msdn.microsoft.com/library/ms677605.aspx)」(ユーザーの名前付け属性) を参照してください。

[Power BI のサインイン名をローカル ディレクトリの UPN にマップする](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources)こともできます。

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Analysis Services データ ソースのユーザー名をマッピングする

<iframe width="560" height="315" src="https://www.youtube.com/embed/eATPS-c7YRU" frameborder="0" allowfullscreen></iframe>

Power BI では、Analysis Services データ ソースのユーザー名をマッピングできます。 Power BI のログイン ユーザー名を、Analysis Services 接続の有効なユーザー名に渡される名前にマッピングする規則を構成できます。 ユーザー名のマッピング機能は、AAD のユーザー名がローカル Active Directory の UPN に一致しないときの回避策として優れています。 たとえば、メール アドレスが nancy@contoso.onmicrsoft.com の場合、それを nancy@contoso.com にマッピングできます。その値がゲートウェイに渡されます。

Analysis Services のユーザー名は、次の 2 つの方法でマッピングすることができます。

* 手動によるユーザーの再マッピング
* オンプレミスの Active Directory プロパティ参照を使用して Active Directory ユーザーに AAD UPN を再マップする (AD 参照マッピング)

2 つ目の方法を使用して手動でマッピングを実行することもできますが、その場合は時間がかかり、保守が困難になります。 パターン マッチングでは十分ではない場合は特に困難です。たとえば、AAD とオンプレミス AD の間でドメイン名が異なる場合や、ユーザー アカウント名が AAD と AD で異なる場合です。 そのため、2 番目の方法での手動マッピングはお勧めできません。

このような 2 つの方法を順番に次の 2 つのセクションで説明します。

### <a name="manual-user-name-re-mapping"></a>手動でのユーザー名の再マッピング

Analysis Services データ ソースの場合は、カスタムのユーザー プリンシパル名 (UPN) 規則を構成できます。 これは、Power BI サービスのログイン名とローカル ディレクトリの UPN が一致していない場合に役立ちます。 たとえば、john@contoso.com で Power BI にサインインしているものの、ローカル ディレクトリの UPN が john@contoso.local の場合は、john@contoso.local を Analysis Services に渡すマッピング規則を構成できます。

UPN マッピングの画面にアクセスするには、次のように操作します。

1. **歯車アイコン**をクリックし、 **[ゲートウェイの管理]** を選択します。
2. Analysis Services データ ソースを格納するゲートウェイを展開します。 または、Analysis Services データ ソースを作成していない場合は、この時点で作成します。
3. データ ソースを選択してから、 **[ユーザー]** タブを選択します。
4. **[ユーザー名のマップ]** を選択します。

    ![UPN マッピング画面](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_02.png)

ルールを追加するオプションと、特定のユーザーについてテストするオプションが表示されます。

> [!NOTE]
> 誤って別のユーザーを変更してしまう場合があります。 たとえば、 **[置換前] \(元の値)** が <em>@contoso.com</em> で **[置換後] \(新しい名前)** が <em>@contoso.local</em> の場合、<em>@contoso.com</em> を含むサインイン名を持つすべてのユーザーが <em>@contoso.local</em> に置き換えられます。 また、 **[置換前] \(元の名前)** が <em>dave@contoso.com</em> で **[置換後] \(新しい名前)** が <em>dave@contoso.local</em> の場合、v-dave@contoso.com でサインインしたユーザーは、v-dave<em>@contoso.local</em> として送信されます。

### <a name="ad-lookup-mapping"></a>AD 参照マッピング

オンプレミスの AD プロパティ参照を実行して AAD UPN を Active Directory ユーザーに再マップするには、次のセクションの手順に従ってください。 まず始めに、このしくみを確認しましょう。

**Power BI サービス**では、次の処理が実行されます。

* オンプレミスの SSAS サーバーに対して Power BI AAD ユーザーがクエリを実行するたびに、firstName.lastName@contoso.com のような UPN 文字列が渡されます。

> [!NOTE]
> Power BI データ ソースの構成内で手動 UPN ユーザー マッピングが定義されている場合は、それが適用されて "*から*"、ユーザー名文字列がオンプレミスのデータ ゲートウェイに送信されます。

構成可能なカスタム ユーザー マッピングを持つオンプレミス データ ゲートウェイで、次の操作を行います。

1. 検索する Active Directory を特定します (自動または構成可能)。
2. **Power BI サービス**から届いた UPN 文字列 (“firstName.lastName@contoso.com”) に基づいて AD ユーザーの属性 (*電子メール*など) を参照します。
3. AD 参照が失敗すると、SSAS への EffectiveUser として渡された UPN の使用を試みます。
4. AD 参照が成功すると、その AD ユーザーの *UserPrincipalName* が取得されます。
5. 次に、*UserPrincipalName* のメール アドレスが *EffectiveUser* として SSAS に渡されます (たとえば、<em>Alias@corp.on-prem.contoso</em>)。

AD 参照を実行するようにゲートウェイを構成するには:

1. [最新のゲートウェイをダウンロードしてインストールします](/data-integration/gateway/service-gateway-install)。

2. ゲートウェイでは、ドメイン アカウントで実行されるように**オンプレミスのデータ ゲートウェイ サービス**を変更する必要があります (ローカル サービス アカウントは使用しません。これを使用すると、実行時に AD 参照が正しく機能しません)。 マシン上で[オンプレミス データ ゲートウェイ アプリ](/data-integration/gateway/service-gateway-app)に移動し、 **[サービス設定] > [サービス アカウントの変更]** の順に移動します。 同じコンピューター上で新しいゲートウェイを作成しない場合はゲートウェイを復元する必要があるため、目的のゲートウェイの回復キーがあることを確認してください。 変更内容を有効にするには、ゲートウェイ サービスを再起動する必要があります。

3. ゲートウェイのインストール フォルダー (*C:\Program Files\On-premises data gateway*) に管理者として移動し、書き込みアクセス許可があることを確認して、*Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* ファイルを開きます。

4. AD ユーザーの *"ご自分の"* Active Directory 属性の構成に従って、次の 2 つの構成値を編集します。 次に示す構成値は単なる例です。Active Directory の構成に基づいて値を指定する必要があります。 これらの構成では大文字と小文字が区別されるので、必ず Active Directory の値と一致するようにします。

    ![Azure Active Directory の設定](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names_03.png)

    ADServerPath 構成の値を指定しない場合、ゲートウェイでは既定のグローバル カタログを使用します。 ADServerPath には複数の値を指定することも可能です。 次の例のとおり、各値はセミコロンで区切る必要があります。

    ```xml
    <setting name="ADServerPath" serializeAs="String">
        <value> >GC://serverpath1; GC://serverpath2;GC://serverpath3</value>
    </setting>
    ```

    このゲートウェイは、一致を検出するまで左から右に ADServerPath 値を解析します。 一致する値が見つからない場合、元の UPN が使用されます。 ゲートウェイ サービス (PBIEgwService) を実行しているアカウントが、ADServerPath で指定したすべての AD サーバーにクエリを実行する許可があることを確認します。

    ゲートウェイでは、次の例のように、2 種類の ADServerPath をサポートしています。

    **WinNT**

    ```xml
    <value="WinNT://usa.domain.corp.contoso.com,computer"/>
    ```

    **GC**

    ```xml
    <value> GC://USA.domain.com </value>
    ```

5. 構成の変更を有効にするには、**オンプレミスのデータ ゲートウェイ** サービスを再起動します。

### <a name="working-with-mapping-rules"></a>マッピング規則を作成する

マッピング規則を作成するには、 **[元の名前]** と **[新しい名前]** の値を入力し、 **[追加]** を選択します。

| フィールド | 説明 |
| --- | --- |
| 置換前 (元の名前) |Power BI へのサインインに使用している電子メール アドレス。 |
| 置換後 (新しい名前) |元の名前を置き換える値。 ここで置き換えた値が、Analysis Services 接続の *EffectiveUserName* プロパティに渡されます。 |

![マッピング規則の作成](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-effective-user-names.png)

一覧の項目を選択するときに、**シェブロン アイコン**を使用して項目を並べ替えたり、項目を**削除**したりできます。

![一覧内の項目の並べ替え](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-map-user-names-entry-selected.png)

### <a name="using-wildcard-"></a>ワイルドカード (\*) を使用する

**\[置換前] \(元の名前)** の文字列でワイルドカードを使用できます。 ワイルドカードは単独でのみ使用でき、その他の文字列パーツと併用はできません。 そのため、すべてのユーザーを取得してデータ ソースに単一の値を渡すことができます。 これは、組織内のすべてのユーザーにローカル環境内の同じユーザーを割り当てる場合に便利です。

### <a name="test-a-mapping-rule"></a>マッピング規則をテストする

**[元の名前]** に値を入力して **[ルールのテスト]** を選択すると、名前の置き換えを検証することができます。

![マッピング規則のテスト](media/service-gateway-enterprise-manage-ssas/gateway-enterprise-test-mapping-rule.png)

> [!NOTE]
> 保存された規則がサービスに使用されるようになるまでに数分かかります。 ブラウザー内では、ルールはすぐに有効になります。

### <a name="limitations-for-mapping-rules"></a>マッピング規則の制限事項

マッピングは、構成されている特定のデータ ソース向けです。 グローバルな設定ではありません。 複数の Analysis Services データ ソースがある場合は、データ ソースごとにユーザーをマッピングする必要があります。

## <a name="authentication-to-a-live-analysis-services-data-source"></a>ライブ Analysis Services データ ソースの認証

Analysis Services をユーザーが操作するたびに、有効なユーザー名がゲートウェイに渡され、次にオンプレミスの Analysis Services サーバーに渡されます。 ユーザー プリンシパル名 (UPN)、通常、クラウドにサインインするときに使用する電子メール アドレスは、有効なユーザーとして Analysis Services に渡すものです。 UPN は接続プロパティ EffectiveUserName に渡されます。 この電子メール アドレスは、ローカルの Active Directory ドメイン内で定義されている UPN と一致する必要があります。 UPN は、Active Directory アカウントのプロパティです。 サーバーにアクセスするには、その Windows アカウントが Analysis Services ロールに存在する必要があります。 Active Directory で一致を検出できない場合、ログインは正常に実行されません。

Analysis Services は、このアカウントに基づいて、フィルター処理も提供できます。 フィルター処理は、ロール ベースのセキュリティまたは行レベルのセキュリティで実行できます。

## <a name="role-based-security"></a>ロール ベース セキュリティ

モデルでは、ユーザー ロールに基づいてセキュリティが提供されます。 特定のモデル プロジェクトに対してロールが定義されるのは、SQL Server Data Tools – Business Intelligence (SSDT-BI) でのオーサリング中、または SQL Server Management Studio (SSMS) を使用してモデルをデプロイした後です。 ロールに含まれるメンバーは、Windows ユーザー名または Windows グループによって決まります。 ロールは、ユーザーがモデルに対してクエリまたは操作を実行するためのアクセス許可を定義します。 ほとんどのユーザーは、読み取りアクセス許可を持つロールに属します。 その他のロールは管理者向けで、項目を処理するアクセス許可、データベースの機能を管理するアクセス許可、他のロールを管理するアクセス許可を持つものがあります。

## <a name="row-level-security"></a>行レベルのセキュリティ

行レベルのセキュリティは、Analysis Services の行レベルのセキュリティに固有です。 モデルでは、動的な行レベルのセキュリティを提供できます。 ユーザーが少なくとも 1 つのロールに属する場合とは異なり、表形式モデルに動的なセキュリティは必要ではありません。 動的なセキュリティでは、上位レベルから、特定テーブル内の特定の行のデータに対してユーザーの読み取りアクセス権が定義されます。 ロールの場合と同様、動的な行レベルのセキュリティは、ユーザーの Windows ユーザー名に依存します。

ユーザーがモデルのデータを閲覧したりクエリを実行したりできるかどうかは、第 1 にそのユーザーの Windows ユーザー アカウントがメンバーとなっているロールによって決まり、第 2 に動的な行レベルのセキュリティ (構成されている場合) によって決まります。

モデルでのロールと動的な行レベル セキュリティの実装については、この記事では説明しません。 詳細については、MSDN の「[ロール (SSAS 表形式)](https://msdn.microsoft.com/library/hh213165.aspx)」と「[(Analysis Services - 多次元データ) のセキュリティ ロール](https://msdn.microsoft.com/library/ms174840.aspx)」を参照してください。 また、表形式モデルのセキュリティに関するさらに詳細な情報については、「[表形式 BI セマンティック モデルをセキュリティで保護する](https://msdn.microsoft.com/library/jj127437.aspx)」というホワイトペーパーをダウンロードしてお読みください。

## <a name="what-about-azure-active-directory"></a>Azure Active Directory の役割

Microsoft クラウド サービスは、ユーザーの認証を処理するために [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) を使用します。 Azure Active Directory は、ユーザー名とセキュリティ グループを含むテナントです。 通常、ユーザーがサインインに使用する電子メール アドレスはアカウントの UPN と同じです。

ローカル Active Directory の役割

Analysis Services に接続するユーザーがデータの読み取りアクセス許可を持つロールに属しているかどうかを判断するため、サーバーは、AAD からゲートウェイ、Analysis Services サーバーの順に渡された有効なユーザー名を変換する必要があります。 Analysis Services サーバーは、Windows Active Directory ドメイン コントローラー (DC) に有効なユーザー名を渡します。 Active Directory DC は、ローカル アカウントで、有効なユーザー名が有効 UPN であることを検証し、Analysis Services サーバーにそのユーザーの Windows ユーザー名を返します。

EffectiveUserName は、ドメインに参加していない Analysis Services サーバーで使用できません。 ログイン エラーを回避するには、Analysis Services サーバーをドメインに参加させる必要があります。

### <a name="how-do-i-tell-what-my-upn-is"></a>自分の UPN を確認する方法

自分の UPN がわからないけれども、自分がドメイン管理者ではない場合もあります。 ワークステーションから次のコマンドを実行して、自分のアカウントの UPN を確認できます。

    whoami /upn

結果はメール アドレスに似ていますが、これはドメイン アカウントの UPN です。 Analysis Services データ ソースをライブ接続に使用している場合に、これが Power BI へのサインインに使用しているメール アドレスと一致しない場合は、[ユーザー名をマッピング](#mapping-usernames-for-analysis-services-data-sources)する方法を参照してください。

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>オンプレミスの Active Directory を Azure Active Directory と同期する

Analysis Services ライブ接続を使用する場合、ローカル Active Directory アカウントが Azure Active Directory に一致すると便利です。 UPN はアカウント間で一致する必要があるためです。

クラウドサービスは、Azure Active Directory 内のアカウントのみを認識します。 ローカル Active Directory にアカウントを追加したかどうかは問題ではなく、AAD に存在しなければ、使用できません。 ローカル Active Directory アカウントと Azure Active Directory はさまざまな方法で一致させることができます。

1. Azure Active Directory にアカウントを手動で追加できます。

   アカウントは Azure portal 上で、または Microsoft 365 管理センター内で作成できます。アカウント名はローカル Active Directory アカウントの UPN と一致します。

2. [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-sync-whatis) ツールを使用し、ローカル アカウントと Azure Active Directory テナントを同期させることができます。

   Azure AD Connect ツールでは、パスワード ハッシュ同期、パススルー認証、フェデレーションなど、ディレクトリ同期と認証設定のオプションが提供されます。 テナント管理者またはローカル ドメイン管理者ではない場合、IT 管理者に問い合わせ、これを構成してもらう必要があります。

Azure AD Connect を利用すると、UPN は AAD とローカル Active Directory 間で一致します。

> [!NOTE]
> Azure AD Connect ツールでアカウントを同期させると、AAD テナント内に新しいアカウントが作成されます。

## <a name="using-the-data-source"></a>データ ソースの使用

作成したデータ ソースは、ライブ接続かスケジュールされた更新のいずれかによって使用されます。

> [!NOTE]
> Power BI Desktop とオンプレミス データ ゲートウェイ内のデータ ソースとの間で、サーバーとデータベース名が一致している必要があります。

データセットとゲートウェイ内のデータ ソース間のリンクは、サーバー名とデータベース名に基づいています。 このため、これらは一致している必要があります。 たとえば、Power BI Desktop 内でサーバー名の IP アドレスを指定する場合は、ゲートウェイ構成内のデータ ソースでもその IP アドレスを使用する必要があります。 Power BI Desktop で *SERVER\INSTANCE* を使用する場合は、ゲートウェイ用に構成されているデータ ソース内でも同じものを使用する必要があります。

これは、ライブ接続とスケジュールされた更新のどちらにも該当します。

### <a name="using-the-data-source-with-live-connections"></a>ライブ接続でデータ ソースを使用する

Power BI Desktop とゲートウェイ用に構成されているデータ ソースとの間では、サーバーとデータベース名が一致している必要があります。 また、ライブ接続のデータセットを公開するには、自分のアカウントがデータ ソースの **[ユーザー]** タブの一覧に表示されている必要があります。 ライブ接続の選択は、最初にデータをインポートする Power BI Desktop 内で発生します。

公開した後は、Power BI Desktop か **[データの取得]** のいずれかから、レポート機能が利用可能になります。 ゲートウェイ内にデータ ソースを作成してから、接続が使用できるようになるまでには、数分ほどかかることがあります。

### <a name="using-the-data-source-with-scheduled-refresh"></a>スケジュールされた更新でデータ ソースを使用する

ゲートウェイ内に構成されているデータ ソースの **[ユーザー]** タブの一覧に自分のアカウントが表示されていて、さらにサーバーとデータベース名が一致している場合は、スケジュールされた更新で使用するオプションとして、ゲートウェイが表示されます。

![ユーザーの表示](media/service-gateway-enterprise-manage-ssas/powerbi-gateway-enterprise-schedule-refresh.png)

### <a name="limitations-of-analysis-services-live-connections"></a>Analysis Services のライブ接続の制限事項

表形式または多次元インスタンスに対してライブ接続を使用することはできません。

| **サーバーのバージョン** | **必要な SKU** |
| --- | --- |
| 2012 SP1 CU4 以降 |Business Intelligence と Enterprise SKU |
| 2014 |Business Intelligence と Enterprise SKU |
| 2016 |Standard SKU 以上 |

* セル レベルの書式設定および変換機能はサポートされていません。
* アクションおよび名前付きセットは Power BI には公開されませんが、アクションまたは名前付きセットも含む多次元キューブに接続し、ビジュアルおよびレポートを作成することはできます。

## <a name="next-steps"></a>次の手順

* [オンプレミス データ ゲートウェイのトラブルシューティング](/data-integration/gateway/service-gateway-tshoot)
* [ゲートウェイのトラブルシューティング - Power BI](service-gateway-onprem-tshoot.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](http://community.powerbi.com/)。

