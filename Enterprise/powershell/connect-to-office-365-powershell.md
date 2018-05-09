---
title: Office 365 PowerShell への接続
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: '概要: は、コマンドラインから管理センターのタスクを実行するのには Office 365 の PowerShell を使用して、Office 365 の組織に接続します。'
ms.openlocfilehash: eac56ae28ab48bb53842725d703bf81fb37d31eb
ms.sourcegitcommit: def3e311db9322e469753bac59ff03624349b140
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2018
---
# <a name="connect-to-office-365-powershell"></a>Office 365 PowerShell への接続

 **の概要:** コマンドラインから管理タスクを実行するのには Office 365 の PowerShell を使用して、Office 365 の組織に接続します。
  
Office 365 PowerShell を使用して、コマンド ラインから Office 365 設定を管理します。Office 365 PowerShell への接続は、必要なソフトウェアのインストール、必要なソフトウェアの実行、Office 365 組織への接続という、シンプルな 3 段階のプロセスです。 

  
> [!TIP]
> **PowerShell を初めて使用されますか。**[PowerShell の概要に関するビデオ](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)を視聴し、LinkedIn Learning にアクセスしてください。 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

- 予想所要時間 : 5 分
    
- 次の Windows のバージョンを使用できます。
    
  - Windows 10、Windows 8.1、Windows 8 または Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、または Windows Server 2008 R2 SP1
    
    > [!NOTE]
    >64 ビット バージョンの Windows を使用してください。Microsoft PowerShell の Microsoft Azure Active Directory モジュールの 32 ビット バージョンのサポートは 2014 年 10 月に終了しました。
    
-  これらの手順は、Office 365 の管理者ロールのメンバーであるユーザーを意図しています。詳細については、 [Office 365 の管理者の役割](https://go.microsoft.com/fwlink/p/?LinkId=532367)を参照してください。

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Microsoft PowerShell の Microsoft Azure Active Directory モジュールとの接続

Microsoft PowerShell の Microsoft Azure Active Directory モジュールには、コマンドレット名に **Msol** が含まれています。
    
### <a name="step-1-install-required-software"></a>手順 1: 必要なソフトウェアをインストールします

これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。
  
1.  Microsoft Online Services サインイン アシスタントの 64 ビット バージョンをインストールします: [IT プロフェッショナル用 Microsoft Online Services サインイン アシスタント RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。
    
2. 以下の手順に従って、Windows PowerShell の Microsoft Azure Active Directory モジュールをインストールします。
    
  - 管理者レベルの PowerShell コマンド プロンプトを開きます。
  - **Install-Module MSOnline** コマンドを実行します。
  - NuGet プロバイダーをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。
  - PSGallery からモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。
  - インストール後、PowerShell コマンド ウィンドウを閉じます。
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>手順 2: Office 365 サブスクリプションの Azure AD に接続します。

*アカウント名とパスワード* のみを使用して接続する場合:
  
1. Windows PowerShell コマンド プロンプトを実行します。
2. **Windows PowerShell** コマンド ウィンドウで次のコマンドを実行します。
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. **[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから **[OK]** をクリックします。
    
*多要素認証 (MFA)* を使用して接続する場合:
  
1. Windows PowerShell コマンド プロンプトを実行します。
2. **Microsoft PowerShell の Microsoft Azure Active Directory モジュール** コマンド ウィンドウで、次のコマンドを実行します。
    
```
Connect-MsolService
```

3. **[Azure Active Directory PowerShell]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから、 **[サインイン]** をクリックします。
    
4. **[Azure Active Directory PowerShell]** ダイアログ ボックスの手順に従って、検証コードなどの他の認証情報を提供してから、 **[サインイン]** をクリックします。
    
### <a name="how-do-you-know-this-worked"></a>正常な動作を確認する方法

何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Office 365 コマンドレット ( **Get-MsolUser** など) を実行して結果を確認します。
  
エラーが表示された場合は、次の要件を確認します。
  
- **よくある原因は、正しくないパスワードです** 。手順 3 をもう一度実行して、ユーザー名とパスワードの入力に注意します。
    
- * *、Microsoft Azure Active ディレクトリ モジュールを Windows PowerShell には、Microsoft.NET Framework 3.5* 。上のコンピューター * * x * 機能を有効にします。お使いのコンピューターがインストールされている新しいバージョンを持っている可能性があります (たとえば、4 または 4.5* 。x *)、.NET Framework の以前のバージョンとの互換性を有効または無効になっている下位ですが。詳細については、次のトピックを参照してください。
    
  - Windows Server 2012 または Windows Server 2012 R2 の場合、「[役割と機能の追加ウィザードを使用して .NET Framework 3.5 を有効にする](https://go.microsoft.com/fwlink/p/?LinkId=532368)」をご覧ください
    
  - Windows 8 または Windows 8.1 の場合、「[Windows 8 または Windows 8.1 への .NET Framework 3.5 のインストール](https://go.microsoft.com/fwlink/p/?LinkId=532369)」をご覧ください
    
  - Windows 7 または Windows Server 2008 R2 の場合、「[Windows PowerShell 用 Azure Active Directory モジュールを開くことができない](https://go.microsoft.com/fwlink/p/?LinkId=532370)」を参照してください
    
- **お使いの Microsoft PowerShell の Microsoft Azure Active Directory モジュール のバージョンは期限切れの可能性があります。** Office 365 PowerShell または Microsoft PowerShell の Microsoft Azure Active Directory モジュール で、次のコマンドを実行して確認します。
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    返されたバージョン番号が 1.0.8070.2 の値より小さい場合は、Microsoft PowerShell の Microsoft Azure Active Directory モジュール をアンインストールして、手順 1 のリンクから最新バージョンをインストールします。
    
- **接続エラーが発生した場合、次のトピックをご覧ください: **["Connect-MsolService:型の例外がスローされました" というエラー](https://go.microsoft.com/fwlink/p/?LinkId=532377)。
    
<a name="ConnectV2"> </a>
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>グラフ モジュールの Azure Active Directory PowerShell を使用して接続します。

[グラフ モジュールのアクティブなディレクトリの PowerShell を Azure](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)のモジュール内のコマンドでは、コマンドレット名に**AzureAD**があります。

グラフ モジュール用の新しい Azure Active Directory の PowerShell コマンドレットを必要とする手順は、モジュールをインストールし、Office 365 サブスクリプションに接続する手順を使用します。

>[!Note]
>異なるバージョンの Microsoft Windows のサポートについては、[グラフのモジュールのアクティブなディレクトリの PowerShell を Azure](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)を参照してください。
>

### <a name="step-1-install-required-software"></a>手順 1: 必要なソフトウェアをインストールします

これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。

  
1. 管理者特権で Windows PowerShell コマンド プロンプトを開きます (Windows PowerShell を管理者として実行)。
    
2. [ **Administrator:Windows PowerShell**] コマンド ウィンドウで、次のコマンドを実行します。
    
  ```
  Install-Module -Name AzureAD 
  ```

信頼されていないリポジトリからモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。


### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a>手順 2: Office 365 サブスクリプションの Azure AD に接続します。

*アカウント名とパスワード*を使用して Office 365 サブスクリプションに接続するには、以下の操作を実行します。
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから **[OK]** をクリックします。
    
*多要素認証 (MFA)* を使用して Office 365 サブスクリプションに接続するには、以下の操作を実行します。

```
Connect-AzureAD
```

**[Azure Active Directory PowerShell]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから、 **[サインイン]** をクリックします。
    
**[Azure Active Directory PowerShell]** ダイアログ ボックスの手順に従って、検証コードなどの他の認証情報を提供してから、 **[サインイン]** をクリックします。
    
接続した後、[グラフのモジュールのアクティブなディレクトリの PowerShell を Azure](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)の新しいコマンドレットを使用できます。
  
## <a name="see-also"></a>関連項目

- [Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
- [単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [Get-Credential](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [Connect-MsolService](https://go.microsoft.com/fwlink/p/?LinkId=532375)

