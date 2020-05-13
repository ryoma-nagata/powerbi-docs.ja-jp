---
title: Power BI からオンプレミス データ ソースへの SSO に Security Assertion Markup Language (SAML) を使用する
description: Security Assertion Markup Language (SAML) でゲートウェイを構成し、Power BI からオンプレミス データ ソースへの SSO を有効にします。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 87684ee408663d3d3e68534fa89fd227327b6ac7
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83328452"
---
# <a name="use-security-assertion-markup-language-saml-for-sso-from-power-bi-to-on-premises-data-sources"></a>Power BI からオンプレミス データ ソースへの SSO に Security Assertion Markup Language (SAML) を使用する

SSO を有効にすると、Power BI レポートおよびダッシュボードでは、オンプレミスのソース上で構成されているユーザー レベルのアクセス許可を考慮しながら、それらのソースからのデータを簡単に更新できるようになります。 [Security Assertion Markup Language (SAML)](https://www.onelogin.com/pages/saml) を使用し、シームレスなシングル サインオン接続を有効にします。 

## <a name="supported-data-sources"></a>サポートされるデータ ソース

現在、SAP HANA に SAML をご利用いただけます。 SAML を使用した SAP HANA のシングル サインオンの設定と構成の詳細については、「[BI プラットフォームから HANA への SAML SSO](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA)」を参照してください。

[Kerberos](service-gateway-sso-kerberos.md) では、追加のデータ ソース (SAP HANA を含む) をサポートしています。

SAP HANA については、SAML SSO 接続を確立する前に暗号化を有効にすることをお勧めします。 暗号化を有効にするには、暗号化された接続を許可するよう HANA サーバーを構成し、HANA サーバーとの通信に暗号化を使用するようゲートウェイを構成します。 HANA ODBC ドライバーは既定で SAML アサーションを暗号化しないため、署名された SAML アサーションは、ゲートウェイから HANA サーバーに "*プレーンテキスト*" で送信され、第三者による傍受や再利用に対して脆弱になります。 OpenSSL ライブラリを使用して HANA の暗号化を有効にする方法については、「[SAP HANA の暗号化を有効にする](/power-bi/desktop-sap-hana-encryption)」を参照してください。

## <a name="configuring-the-gateway-and-data-source"></a>ゲートウェイとデータ ソースを構成する

SAML を使用するには、SSO を有効にする HANA サーバーとゲートウェイの間に信頼関係を確立する必要があります。 このシナリオでは、ゲートウェイは SAML ID プロバイダー (IdP) として機能します。 この関係を確立するにはさまざまな方法があります。たとえば、ゲートウェイ IdP の x509 証明書を HANA サーバーの信頼ストアにインポートしたり、HANA サーバーが信頼するルート証明機関 (CA) によって署名されたゲートウェイの X509 証明書を用意したりします。 このガイドでは後者の方法について説明しますが、もう一方が都合が良い場合はそちらを使用してかまいません。

このガイドでは HANA サーバーの暗号化サービス プロバイダーとして OpenSSL を使用しますが、SAP では、OpenSSL ではなく SAP 暗号化ライブラリ (CommonCryptoLib または sapcrypto とも呼ばれる) を使用して、信頼関係を確立するための設定手順を完了することを推奨しています。 詳細については、SAP の公式ドキュメントを参照してください。

次の手順では、HANA サーバーによって信頼されたルート CA を使用してゲートウェイ IdP の X509 証明書に署名することで、HANA サーバーとゲートウェイ IdP の間の信頼関係を確立する方法について説明します。 このルート CA を作成します。

1. ルート CA の X509 証明書と秘密キーを作成します。 たとえば、ルート CA の X509 証明書と .pem 形式の秘密キーを作成するには、次のコマンドを入力します。

   ```
   openssl req -new -x509 -newkey rsa:2048 -days 3650 -sha256 -keyout CA_Key.pem -out CA_Cert.pem -extensions v3_ca
   ```

    ルート CA の秘密キーが適切にセキュリティで保護されていることを確認します。 第三者の手に渡った場合、HANA サーバーへの不正アクセスに使用されるおそれがあります。 

 1. 作成したルート CA によって署名された証明書が HANA サーバーから信頼されるように、HANA サーバーの信頼ストアに証明書 (CA_Cert.pem など) を追加します。 

    ご利用の HANA サーバーの信頼ストアの場所は、**ssltruststore** 構成設定を調べると見つかります。 OpenSSL の構成方法について説明した SAP ドキュメントの手順に従っている場合、再利用できるルート CA は既にご使用の HANA サーバーによって信頼されている可能性があります。 詳細については、「[SAP HANA Studio と SAP HANA Server 間に Open SSL を構成する方法](https://archive.sap.com/documents/docs/DOC-39571)」を参照してください。 SAML SSO を有効にする HANA サーバーが複数ある場合は、このルート CA が各サーバーによって信頼されていることを確認します。

1. ゲートウェイ IdP の X509 証明書を作成します。 

   たとえば、1 年間有効な証明書署名要求 (IdP_Req.pem) と秘密キー (IdP_Key.pem) を作成するには、次のコマンドを実行します。

   ```
   openssl req -newkey rsa:2048 -days 365 -sha256 -keyout IdP_Key.pem -out IdP_Req.pem -nodes
   ```

 1. ご利用の HANA サーバーによって信頼されるように構成したルート CA を使用して証明書署名要求に署名します。 

    たとえば、CA_Cert.pem と CA_Key.pem (ルート CA の証明書とキー) を使用して IdP_Req.pem に署名するには、次のコマンドを実行します。

    ```
    openssl x509 -req -days 365 -in IdP_Req.pem -sha256 -extensions usr_cert -CA CA_Cert.pem -CAkey CA_Key.pem -CAcreateserial -out IdP_Cert.pem
    ```

     結果として生成される IdP 証明書は 1 年間有効です (-days オプションを参照)。 

ご自分の IdP の証明書を HANA Studio にインポートして、新しい SAML ID プロバイダーを作成します。

1. SAP HANA Studio で、SAP HANA サーバー名を右クリックし、 **[Security]\(セキュリティ\)** &gt; **[Open Security Console]\(セキュリティ コンソールを開く\)** &gt; **[SAML Identity Provider]\(SAML ID プロバイダー\)** &gt; **[OpenSSL Cryptographic Library]\(OpenSSL 暗号化ライブラリ\)** の順に移動します。

    ![ID プロバイダー](media/service-gateway-sso-saml/identity-providers.png)

1. **[Import]\(インポート\)** を選択し、IdP_Cert.pem に移動し、これをインポートします。

1. SAP HANA Studio で **[Security]\(セキュリティ\)** フォルダーを選択します。

    ![[Security] フォルダー](media/service-gateway-sso-saml/security-folder.png)

1. **[User]\(ユーザー\)** を展開し、Power BI ユーザーをマップするユーザーを選択します。

1. **[SAML]** を選択し、 **[Configure]\(構成\)** を選択します。

    ![SAML を構成する](media/service-gateway-sso-saml/configure-saml.png)

1. 手順 2 で作成した ID プロバイダーを選択します。 **[External Identity]\(外部 ID\)** に Power BI ユーザーの UPN (通常は、Power BI へのログインにユーザーが使用するメール アドレス) を入力し、 **[Add]\(追加\)** を選択します。 *ADUserNameReplacementProperty* 構成オプションを使用するようゲートウェイを構成した場合は、Power BI ユーザーの元の UPN を置き換える値を入力します。 

   たとえば、*ADUserNameReplacementProperty* を **SAMAccountName** に設定する場合は、ユーザーの **SAMAccountName** を入力する必要があります。

    ![ID プロバイダーを選択する](media/service-gateway-sso-saml/select-identity-provider.png)

これでゲートウェイの証明書と ID を構成できたので、証明書を pfx 形式に変換し、この証明書を使用するようゲートウェイを構成します。

1. 次のコマンドを実行し、証明書を pfx 形式に変換します。 このコマンドでは、結果として作成される .pfx ファイルに samlcert.pfx という名前を設定し、そのパスワードを *root* に設定します。

    ```
    openssl pkcs12 -export -out samltest.pfx -in IdP_Cert.pem -inkey IdP_Key.pem -passin pass:root -passout pass:root
    ```

1. ゲートウェイ コンピューターに pfx ファイルをコピーします。

    1. samltest.pfx をダブルクリックし、 **[ローカル コンピューター]** &gt; **[次へ]** の順に選択します。

    1. パスワードを入力し、 **[次へ]** を選択します。

    1. **[証明書をすべて次のストアに配置する]** を選択し、 **[参照]** &gt; **[個人]** &gt; **[OK]** の順に選択します。

    1. **[次へ]** を選択し、 **[完了]** を選択します。

       ![証明書をインポートする](media/service-gateway-sso-saml/import-certificate.png)

1. 証明書の秘密キーにアクセスする許可をゲートウェイ サービス アカウントに付与します。

    1. ゲートウェイ コンピューターで、Microsoft 管理コンソール (MMC) を実行します。

        ![MMC を実行する](media/service-gateway-sso-saml/run-mmc.png)

    1. **[ファイル]** で **[スナップインの追加と削除]** を選択します。

        ![スナップインを追加する](media/service-gateway-sso-saml/add-snap-in.png)

    1. **[証明書]** &gt; **[追加]** の順に選択し、 **[コンピューター アカウント]** &gt; **[次へ]** の順に選択します。

    1. **[ローカル コンピューター]** &gt; **[完了]** &gt; **[OK]** の順に選択します。

    1. **[証明書]** &gt; **[個人]** &gt; **[証明書]** の順に展開し、証明書を見つけます。

    1. 証明書を右クリックし、 **[すべてのタスク]** &gt; **[秘密キーの管理]** の順に移動します。

        ![秘密キーを管理する](media/service-gateway-sso-saml/manage-private-keys.png)

    1. ゲートウェイ サービス アカウントを一覧に追加します。 既定では、アカウントは **NT SERVICE\PBIEgwService** です。 **services.msc** を実行してゲートウェイ サービスを実行しているアカウントを見つけ、**オンプレミス データ ゲートウェイ サービス**を特定することができます。

        ![ゲートウェイ サービス](media/service-gateway-sso-saml/gateway-service.png)

最後に、次の手順を実行して、証明書の拇印をゲートウェイ構成に追加します。

1. 次の PowerShell コマンドを実行して、マシン上の証明書を一覧表示します。

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```

1. 作成した証明書の拇印をコピーします。

1. ゲートウェイ ディレクトリ (既定では C:\Program Files\On-premises data gateway) に移動します。

1. PowerBI.DataMovement.Pipeline.GatewayCore.dll.config を開き、*SapHanaSAMLCertThumbprint* セクションを見つけます。 コピーした拇印を貼り付けます。

1. ゲートウェイ サービスを再起動します。

## <a name="running-a-power-bi-report"></a>Power BI レポートを実行する

Power BI の **[Manage Gateway]\(ゲートウェイの管理\)** ページを使用して SAP HANA データ ソースを構成できるようになりました。 **[詳細設定]** で、SAML 経由で SSO を有効にします。 こうすることで、そのデータ ソースにバインドされているレポートやデータセットを発行できます。

   ![詳細設定](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>トラブルシューティング

SAML ベースの SSO を構成した後、Power BI ポータルで次のエラーが表示される場合があります: "*指定された資格情報は SapHana のソースに使用できません*"。 このエラーは、SAML 資格情報が SAP HANA によって拒否されたことを示します。

サーバー側の認証トレースを利用すれば、SAP HANA での資格情報の問題をトラブルシューティングするための詳細情報が得られます。 以下の手順に従って、ご利用の SAP HANA サーバーに対するトレースを構成します。

1. SAP HANA サーバー上で、次のクエリを実行して認証トレースをオンにします。

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. 問題を再現します。

1. HANA Studio で、管理コンソールを開いて、 **[Diagnosis Files]\(診断ファイル\)** タブを選択します。

1. 最新のインデックス サーバー トレースを開いて、*SAMLAuthenticator.cpp* を検索します。

    次のように、根本原因を示す詳細なエラー メッセージを見つける必要があります。

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. トラブルシューティングが完了したら、次のクエリを実行して認証トレースをオフにします。

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>次の手順

オンプレミス データ ゲートウェイと DirectQuery の詳細については、次のリソースを参照してください。

* [オンプレミス データ ゲートウェイとは](/data-integration/gateway/service-gateway-onprem)
* [Power BI の DirectQuery](desktop-directquery-about.md)
* [DirectQuery でサポートされるデータ ソース](power-bi-data-sources.md)
* [DirectQuery と SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery と SAP HANA](desktop-directquery-sap-hana.md)
