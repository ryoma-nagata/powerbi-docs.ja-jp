---
title: Power BI 用の独自の暗号化キーを使用する (プレビュー)
description: Power BI Premium で独自の暗号化キーを使用する方法を学習します。
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 7adcfeec771796aa9fe322512f8ca8584559cea0
ms.sourcegitcommit: c122c1a8c9f502a78ccecd32d2708ab2342409f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829390"
---
# <a name="bring-your-own-encryption-keys-for-power-bi-preview"></a>Power BI 用の独自の暗号化キーを使用する (プレビュー)

Power BI では、"_保存_" データと "_処理中_" のデータが暗号化されます。 既定では、Power BI で Microsoft マネージド キーを使用してデータを暗号化します。 Power BI Premium では、データセットにインポートされる、保存データに対して独自のキーを使用することもできます (詳細については、「[データ ソースとストレージに関する考慮事項](#data-source-and-storage-considerations)」を参照)。 このアプローチは多くの場合、_Bring Your Own Key_ (BYOK) と説明されます。

## <a name="why-use-byok"></a>BYOK を使用する理由

BYOK によって、クラウド サービス プロバイダー (この場合、Microsoft) でキー配置を指定するコンプライアンス要件を満たすことがより簡単になります。 BYOK では、アプリケーション レベルで Power BI の保存データ用の暗号化キーを提供し、制御します。 その結果、組織のキーを制御でき、サービスを終了することにした場合は、それを取り消すことができます。 キーを取り消すことで、データはサービスで読み取れなくなります。

## <a name="data-source-and-storage-considerations"></a>データ ソースとストレージに関する考慮事項

BYOK を使用するには、Power BI Desktop (PBIX) ファイルから Power BI サービスにデータをアップロードする必要があります。 Power BI Desktop でデータ ソースに接続する場合は、インポートのストレージ モードを指定する必要があります。 次のシナリオでは、BYOK を使用することはできません。

- DirectQuery
- Analysis Services ライブ接続
- Excel ブック (データが最初に Power BI Desktop にインポートされる場合を除く)
- プッシュ データセット

次のセクションでは、BYOK の暗号化キーを格納する場所である、Azure Key Vault を構成する方法を学習します。

## <a name="configure-azure-key-vault"></a>Azure Key Vault を構成する

Azure Key Vault は、暗号化キーなどのシークレットを安全に格納し、そのシークレットにアクセスするためのツールです。 既存のキー コンテナーを使って暗号化キーを格納することも、Power BI 専用の新しいものを作成することもできます。

このセクションの手順では、Azure Key Vault の基本的な知識があることを想定しています。 詳細については、「[Azure Key Vault とは](/azure/key-vault/key-vault-whatis)」を参照してください。 次のように、キー コンテナーを構成します。

1. 折り返しおよび折り返し解除のアクセス許可を使用して、キー コンテナーのサービス プリンシパルとして Power BI サービスを追加します。

1. 折り返しおよび折り返し解除のアクセス許可を使用して、長さが 4096 ビットの RSA キーを作成します (またはこの種の既存のキーを使用します)。

1. 推奨: キー コンテナーで "_論理的な削除_" オプションが有効になっていることを確認します。

### <a name="add-the-service-principal"></a>サービス プリンシパルを追加する

1. Azure portal のキー コンテナーで、 **[アクセス ポリシー]** の  **[新規追加]** を選択します。

1. **[プリンシパルの選択]** で、Microsoft.Azure.AnalysisServices を検索して選択します。

1. **[キーのアクセス許可]** で、 **[キーの折り返しを解除]** および **[キーを折り返す]** を選択します。

    ![PBIX ファイル コンポーネント](media/service-encryption-byok/service-principal.png)

1. **[OK]** 、 **[保存]** の順に選択します。

### <a name="create-an-rsa-key"></a>RSA キーを作成する

1. キー コンテナーの **[キー]** で、 **[生成/インポート]** を選択します。

1. **[キーの種類]** では RSA を、 **[RSA キー サイズ]** では 4096 を選択します。

    ![PBIX ファイル コンポーネント](media/service-encryption-byok/create-rsa-key.png)

1. **[作成]** を選択します。

1. **[キー]** で、作成したキーを選択します。

1. キーの **[現在のバージョン]** では、GUID を選択します。

1. **[キーを折り返す]** と **[キーの折り返しを解除]** の両方が選択されていることを確認します。 Power BI で BYOK を有効にしたときに使用する **[キー識別子]** をコピーします。

    ![PBIX ファイル コンポーネント](media/service-encryption-byok/key-properties.png)

### <a name="soft-delete-option"></a>論理的な削除のオプション

誤ってキー (またはキー コンテナー) を削除した場合にデータの損失から保護するために、キー コンテナーで[論理的な削除](/azure/key-vault/key-vault-ovw-soft-delete)を有効にすることをお勧めします。 Azure Portal からはまだこのオプションを使用できないため、キー コンテナーでは [PowerShell を使って "soft-delete" プロパティを有効にする](/azure/key-vault/key-vault-soft-delete-powershell)必要があります。

Azure Key Vault が正しく構成されたら、テナントで BYOK を有効にすることができます。

## <a name="enable-byok-on-your-tenant"></a>テナントで BYOK を有効にする

PowerShell を使用してテナント レベルで BYOK を有効にします。その場合、まず、Power BI テナントに、Azure Key Vault で作成して格納した暗号化キーを導入します。 その後、容量のコンテンツを暗号化するために、Premium 容量ごとにこれらの暗号化キーを割り当てます。

### <a name="important-considerations"></a>重要な考慮事項

BYOK を有効にする前に、次の考慮事項に注意してください。

- この時点では、BYOK を有効にした後で無効にすることはできません。 `Add-PowerBIEncryptionKey` のパラメーターを指定する方法に応じて、1 つまたは複数の容量に対して BYOK を使用する方法を制御できます。 しかし、テナントに対するキーの導入を元に戻すことはできません。 詳細については、「[BYOK を有効にする](#enable-byok)」を参照してください。

- 共有されている容量に、Power BI Premium の専用容量から BYOK を使用するワークスペースを "_直接_" 移動することはできません。 まず、BYOK が有効になっていない専用容量にワークスペースを移動する必要があります。

### <a name="enable-byok"></a>BYOK を有効にする

BYOK を有効にするには、`Connect-PowerBIServiceAccount` コマンドレットを使用してサインインした、Power BI サービスのテナント管理者である必要があります。 その後、以下の例に示すように、`Add-PowerBIEncryptionKey` を使用して BYOK を有効にします。

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

コマンドレットでは、現在および今後の容量の暗号化に影響する、3 つのスイッチ パラメーターが受け入れられます。 既定では、どのスイッチも設定されません。

- `-Activate`:このキーがテナント内の既存のすべての容量に対して使用されることを示します。

- `-Default`:このキーが現在、テナント全体の既定値であることを示します。 新しい容量を作成するときに、容量ではこのキーが継承されます。

- `-DefaultAndActivate`:このキーが既存のすべての容量と、作成する新しい容量に対して使用されることを示します。

`-Default` または `-DefaultAndActivate` を指定した場合、この時点からこのテナントで作成されたすべての容量が、指定するキー (または更新された既定のキー) を使用して暗号化されます。 既定の操作を元に戻すことはできません。したがって、テナントで BYOK が使用されない Premium 容量は作成できなくなります。

テナント全体で BYOK を使用する方法を制御することができます。 たとえば、単一の容量を暗号化するには、`-Activate`、`-Default`、`-DefaultAndActivate` なしで `Add-PowerBIEncryptionKey` を呼び出します。 その後、BYOK を有効にする容量に対して、`Set-PowerBICapacityEncryptionKey` を呼び出します。

## <a name="manage-byok"></a>BYOK を管理する

Power BI では、テナントでの BYOK の管理に役立つ追加のコマンドレットが提供されます。

- テナントで現在使用されているキーを取得するには、`Get-PowerBIEncryptionKey` を使用します。

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- ワークスペースのデータセットが暗号化されているかどうかと、その暗号化状態がワークスペースと同期されているかどうかを確認するには、`Get-PowerBIWorkspaceEncryptionStatus` を使用します。

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    暗号化は容量レベルで有効になっていますが、暗号化状態は指定されたワークスペースのデータセット レベルで取得することに注意してくだささい。

- Power BI 容量の暗号化キーを更新するには、`Set-PowerBICapacityEncryptionKey` を使用します。

    ```powershell
    Set-PowerBICapacityEncryptionKey-CapacityId 08d57fce-9e79-49ac-afac-d61765f97f6f -KeyName 'Contoso Sales'
    ```

- 現在、暗号化で使用されているキーを切り替える (または "_ローテーション_" する) には、`Use Switch-PowerBIEncryptionKey`。 コマンドレットでは単にキー `-Name` の `-KeyVaultKeyUri` を更新します。

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```