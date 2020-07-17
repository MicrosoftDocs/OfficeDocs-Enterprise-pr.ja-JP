---
title: Office 365 PowerShell への接続
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/30/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Office 365 PowerShell を使用して Office 365 組織に接続し、コマンド ラインから管理センター タスクを実行します。
ms.openlocfilehash: 0906da2b8773973236bc8cb6ef273d1a14528bfd
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997423"
---
# <a name="connect-to-office-365-powershell"></a>Office 365 PowerShell への接続

Office 365 PowerShell を使用すると、コマンド ラインから Office 365 の設定を管理できます。Office 365 PowerShell への接続は、必要なソフトウェアをインストールしてから Office 365 組織に接続するというシンプルなプロセスです。 

Office 365 および管理者のユーザー アカウント、グループ、ライセンスへの接続に使用する PowerShell モジュールには、次の 2 つのバージョンがあります。

- Graph 用 Azure Active Directory PowerShell (コマンドレット名に **AzureAD** が含まれる)
- Windows PowerShell 用 Microsoft Azure Active Directory モジュール (コマンドレット名に **MSol** が含まれる) 

この記事の日付の時点で、Graph 用 Azure Active Directory PowerShell モジュールは、ユーザー、グループ、およびライセンスの管理について Windows PowerShell 用 Microsoft Azure Active Directory モジュールのコマンドレットの機能に完全に置き換わるものではありません。多くの場合、両方のバージョンを使用する必要があります。同じコンピューターに両方のバージョンを安全にインストールできます。

## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

次の Windows のバージョンを使用できます。
    
  - Windows 10、Windows 8.1、Windows 8、または Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、または Windows Server 2008 R2 SP1

    > [!NOTE]
    > Graph 用 Azure Active Directory PowerShell モジュールでは、PowerShell バージョン 5.1 以降を使用する必要があります。 Windows PowerShell 用 Microsoft Azure Active Directory モジュールでは、PowerShell バージョン 5.1 から PowerShell バージョン 6 までを使用する必要があります。 PowerShell バージョン 7 は使用できません。 Windows 8.1、Windows 8、Windows 7 Service Pack 1 (SP1)、Windows Server 2012 R2、Windows Server 2012、および Windows Server 2008 R2 SP1 の場合は、[Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616) をダウンロードしてインストールします。 
    
    > [!NOTE]
    > 64 ビット バージョンの Windows を使用してください。Microsoft PowerShell の Microsoft Azure Active Directory モジュールの 32 ビット バージョンのサポートは 2014 年 10 月に終了しました。
    
これらの手順は、Office 365 管理者の役割のメンバーであるユーザーを対象としています。詳細については、「[Office 365 の管理者ロールについて](https://go.microsoft.com/fwlink/p/?LinkId=532367)」を参照してください。


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Graph 用 Azure Active Directory PowerShell モジュールに接続する

Graph 用 Azure Active Directory PowerShell モジュールのコマンドには、コマンドレット名に **AzureAD** が含まれます。 [Graph 用 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) モジュールか [Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-3.6.1) をインストールできます。

Graph 用 Azure Active Directory PowerShell モジュールにおいて新しいコマンドレットを必要とするプロシージャについては、以下の手順を実行して、モジュールをインストールし、Office 365 サブスクリプションに接続します。

>[!Note]
>Microsoft Windows のさまざまなバージョンに対するサポート情報については、[Graph 用 Azure Active Directory PowerShell モジュール](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)に関するページを参照してください。
>

### <a name="step-1-install-required-software"></a>手順 1: 必要なソフトウェアをインストールする

これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。
  
1. 管理者特権で Windows PowerShell コマンド プロンプトを開きます (Windows PowerShell を管理者として実行)。
    
2. [ **Administrator:Windows PowerShell**] コマンド ウィンドウで、次のコマンドを実行します。
    
  ```powershell
  Install-Module -Name AzureAD
  ```

信頼されていないリポジトリからモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、Enter を押します。

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>手順 2: Office 365 サブスクリプション用の Azure AD に接続する

アカウント名とパスワードまたは多要素認証 (MFA) を使用して Office 365 サブスクリプション用の Azure AD に接続するには、Windows PowerShell コマンド プロンプトから次のいずれかのコマンドを実行します (昇格する必要はありません)。

|||
|:-------|:-----|
| **Office 365 のクラウド** | **コマンド** |
| Office 365 ワールドワイド (+GCC) | `Connect-AzureAD` |
| 21 Vianet が運営する Office 365 | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Germany | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 U.S. Government DoD と Office 365 U.S. Government GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

[**アカウントにサインイン**] ダイアログ ボックスで、Office 365 の職場または学校のアカウントのユーザー名とパスワードを入力し、[**OK**] をクリックします。

MFA を使用している場合は、追加のダイアログ ボックスの手順に従って、確認コードなどのその他の認証情報を入力します。

接続後は、[Graph 用 Azure Active Directory PowerShell モジュール](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)のコマンドレットを使用できます。
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Microsoft PowerShell の Microsoft Azure Active Directory モジュールとの接続

Microsoft PowerShell の Microsoft Azure Active Directory モジュールには、コマンドレット名に **Msol** が含まれています。

PowerShell バージョン 7 以降は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 PowerShell バージョン 7 以降では、Graph 用 Azure Active Directory PowerShell モジュールか Azure PowerShell を使用する必要があります。

PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。 
    
### <a name="step-1-install-required-software"></a>手順 1: 必要なソフトウェアをインストールする

これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。
  
1.  Windows 10 を実行していない場合は、Microsoft Online Services サインインアシスタントの64ビットバージョンをインストールします: [IT プロフェッショナル用 Microsoft Online Services サインインアシスタント RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。
    
2. 以下の手順に従って、Windows PowerShell の Microsoft Azure Active Directory モジュールをインストールします。
    
  - 管理者特権で Windows PowerShell コマンド プロンプトを開きます (Windows PowerShell を管理者として実行)。
  - **Install-Module MSOnline** コマンドを実行します。
  - NuGet プロバイダーをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。
  - PSGallery からモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、Enter を押します。
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>手順 2: Office 365 サブスクリプション用の Azure AD に接続する

アカウント名とパスワードまたは多要素認証 (MFA) を使用して Office 365 サブスクリプション用の Azure AD に接続するには、Windows PowerShell コマンド プロンプトから次のいずれかのコマンドを実行します (昇格する必要はありません)。

|||
|:-------|:-----|
| **Office 365 のクラウド** | **コマンド** |
| Office 365 ワールドワイド (+GCC) | `Connect-MsolService` |
| 21 Vianet が運営する Office 365 | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Germany | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 U.S. Government DoD と Office 365 U.S. Government GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

[**アカウントにサインイン**] ダイアログ ボックスで、Office 365 の職場または学校のアカウントのユーザー名とパスワードを入力し、[**OK**] をクリックします。

MFA を使用している場合は、追加のダイアログ ボックスの手順に従って、確認コードなどのその他の認証情報を入力します。

### <a name="how-do-you-know-this-worked"></a>正常な動作を確認する方法

何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Office 365 コマンドレット ( **Get-MsolUser** など) を実行して結果を確認します。
  
エラーが表示された場合は、次の要件を確認します。
  
- **よくある原因は、正しくないパスワードです**。手順 2 をもう一度実行して、ユーザー名とパスワードの入力に注意します。
    
- **Windows PowerShell 用 Microsoft Azure Active Directory モジュールでは、Microsoft .NET Framework 3.5.* x* 機能がお使いのコンピューターで有効になっている必要があります。お使いのコンピューターに、より新しいバージョン (たとえば、4 または 4.5.* x*) がインストールされている場合でも、.NET Framework の古いバージョンとの下位互換性を有効または無効にすることができます。詳細については、以下のトピックをご覧ください。
    
  - Windows Server 2012 または Windows Server 2012 R2 の場合は、「[役割と機能の追加ウィザードを使用して .NET Framework 3.5 を有効にする](https://go.microsoft.com/fwlink/p/?LinkId=532368)」を参照してください
    
  - Windows 7 または Windows Server 2008 R2 の場合は、「[Windows PowerShell 用 Azure Active Directory モジュールを開くことができない](https://go.microsoft.com/fwlink/p/?LinkId=532370)」を参照してください

  - Windows 10、Windows 8.1、および Windows 8 の場合は、「[Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール](https://docs.microsoft.com/dotnet/framework/install/dotnet-35-windows-10)」を参照してください

  
- **お使いの Microsoft PowerShell の Microsoft Azure Active Directory モジュール のバージョンは期限切れの可能性があります。** Office 365 PowerShell または Microsoft PowerShell の Microsoft Azure Active Directory モジュール で、次のコマンドを実行して確認します。
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    返されたバージョン番号が1.0.8070.2 の値より小さい場合は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールをアンインストールし、上記の手順1からインストールします。

- **接続エラーが発生した場合は、**["Connect-MsolService: 例外がスローされました" というエラー](https://go.microsoft.com/fwlink/p/?LinkId=532377)に関するトピックをご覧ください。
    
- **「Get-Item: パスが見つかりません」エラーが表示された場合は、次のコマンドを使用してください:** 

```powershell
  (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
```

## <a name="see-also"></a>関連項目

- [Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
- [単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
