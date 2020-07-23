---
title: 1つの Windows PowerShell ウィンドウですべての Microsoft 365 サービスに接続する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: '概要: Windows powershell を1つの Windows PowerShell ウィンドウですべての Microsoft 365 サービスに接続します。'
ms.openlocfilehash: a037de53dcbf8fed95b9b4d5f05677997135dfb3
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230843"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a>1つの Windows PowerShell ウィンドウですべての Microsoft 365 サービスに接続する

PowerShell を使用して Microsoft 365 を管理する場合は、Microsoft 365 管理センター、SharePoint Online、Exchange Online、Skype for Business Online、Microsoft Teams、セキュリティコンプライアンスセンターに対応して、最大5つの Windows PowerShell セッションを同時に開くことができ &amp; ます。 別々の Windows PowerShell セッションで 5 つの異なる接続方法を使用すると、デスクトップは以下のようになります。
  
![一度に実行している 5 つの Windows PowerShell コンソール](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
これは、Microsoft 365 の管理には適していません。これら5つの windows 間でデータを交換することはできません。 このトピックでは、Windows PowerShell の単一のインスタンスを使用する方法について説明します。これには、Microsoft 365 アカウント、Skype for Business Online、Exchange Online、SharePoint Online、Microsoft Teams、およびセキュリティコンプライアンスセンターを管理でき &amp; ます。

>[!Note]
>現在、この記事には、ワールドワイド (+ GCC) クラウドに接続するためのコマンドのみが含まれています。 その他のノートには、他の Microsoft 365 クラウドへの接続に関する情報を含む記事へのリンクが記載されています。
>

## <a name="before-you-begin"></a>はじめに

Windows PowerShell の単一のインスタンスからすべての Microsoft 365 を管理するには、事前に次の前提条件を考慮してください。
  
- これらの手順で使用する Microsoft 365 職場または学校アカウントは、Microsoft 365 管理者ロールのメンバーである必要があります。 詳細については、[「管理者ロールについて」](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide) を参照してください。 これは、Microsoft 365 用の PowerShell の要件です。これは、その他の Microsoft 365 サービスには必ずしも必要ありません。
    
- 次の Windows の 64 ビット バージョンを使用できます。
    
  - Windows 10
    
  - Windows 8.1 または Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 または Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Microsoft .NET Framework 4.5 をインストールする必要があります。*x*をクリックし、Windows management framework 3.0 または Windows management framework 4.0 のどちらかを選択します。 詳細については、「.NET Framework と[Windows management framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)または[windows management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)[のインストール](https://go.microsoft.com/fwlink/p/?LinkId=257868)」を参照してください。
    
    Skype for Business Online のモジュールと Microsoft 365 のモジュールのいずれかの要件があるため、64ビットバージョンの Windows を使用する必要があります。
    
- Azure Active Directory (Azure AD)、Exchange Online、SharePoint Online、Skype for Business Online、Teams に必要なモジュールをインストールする必要があります。
    
   - [Azure Active Directory V2](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [Skype for Business Online、Windows PowerShell モジュール](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [Exchange Online PowerShell V2](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [Teams PowerShell の概要](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  Windows PowerShell は、Skype for Business Online およびセキュリティ/コンプライアンスセンターの署名済みスクリプトを実行するように構成する必要があり &amp; ます。 To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-just-a-password"></a>パスワードのみを使用する場合の接続手順

サインインのパスワードのみを使用している場合は、1つの PowerShell ウィンドウですべてのサービスに接続する手順を次に示します。
  
1. Windows PowerShell を開きます。
    
2. このコマンドを実行して、Microsoft 365 職場または学校のアカウントの資格情報を入力します。
    
  ```powershell
  $credential = Get-Credential
  ```

3. このコマンドを実行して、azure Active Directory PowerShell for Graph モジュールを使用して Azure AD に接続します。
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  または、Windows PowerShell 用 Microsoft Azure Active Directory モジュールモジュールを使用している場合は、次のコマンドを実行します。
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

4. 次のコマンドを実行して、SharePoint Online に接続します。 ドメインの組織名を指定します。 たとえば、"litwareinc.onmicrosoft.com" の場合、組織名の値は "litwareinc" です。
    
  ```powershell
  $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
  Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
  ```

5. 次のコマンドを実行して、Skype for Business Online に接続します。初めて接続する場合、`WSMan NetworkDelayms` の値を増やすようにという警告が出ますが、無視してください。
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. Exchange Online に接続するには、次のコマンドを実行します。
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
>全世界以外の Microsoft 365 クラウドの Exchange Online に接続するには、 **-exchangeの name**パラメーターを使用します。 詳細については[、「Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) 」を参照してください。
>

7. これらのコマンドを実行して Teams PowerShell に接続します。
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
>全世界以外の Microsoft Teams クラウドに接続する方法については、「 [connect-](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps)microsoft teams」を参照してください。
>

8. 次のコマンドを実行して、セキュリティ センターとコンプライアンス センター に接続します。
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
>&amp;全世界以外の Microsoft 365 クラウドのセキュリティコンプライアンスセンターに接続する方法については、「 [Connect to Security & コンプライアンスセンター PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)」を参照してください。
>

Azure Active Directory PowerShell for Graph モジュールを使用している場合、1つのブロック内のすべてのコマンドがあります。 ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

また、「Windows PowerShell 用 Microsoft Azure Active Directory モジュール」モジュールを使用している場合は、1つのブロック内のすべてのコマンドを次に示します。 ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
Connect-ExchangeOnline -Credential $credential -ShowProgress $true
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

Windows PowerShell ウィンドウを閉じる準備ができたら、次のコマンドを実行して、Skype for Business Online、SharePoint Online、セキュリティ &amp; コンプライアンスセンター、および Teams へのアクティブなセッションを削除します。
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>多要素認証を使用する場合の接続手順

Azure AD、SharePoint Online、Skype for Business、Exchange Online、および複数要素認証を使用する1つのウィンドウで多要素認証を使用するすべてのコマンドを1つのブロックにまとめたものです。そのためには、Azure Active Directory PowerShell for Graph モジュールを使用します。 ユーザーアカウントのユーザープリンシパル名 (UPN) 名とドメインホスト名を指定し、それらを一度にすべて実行します。

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

または、「Windows PowerShell 用 Microsoft Azure Active Directory モジュール」モジュールを使用する場合のすべてのコマンドを次に示します。

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Skype for Business Online
$sfboSession = New-CsOnlineSession -UserName $acctName
Import-PSSession $sfboSession
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Teams
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

セキュリティ/コンプライアンスセンターの場合は、多要素認証を使用 &amp; して接続するために、「 [Connect to Security & コンプライアンスセンターの PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) 」を参照してください。

## <a name="see-also"></a>関連項目

- [PowerShell を使用して Microsoft 365 に接続する](connect-to-office-365-powershell.md)
- [PowerShell を使用して SharePoint Online を管理する](manage-sharepoint-online-with-office-365-powershell.md)
- [PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Windows PowerShell を使用して Microsoft 365 でレポートを作成する](use-windows-powershell-to-create-reports-in-office-365.md)
