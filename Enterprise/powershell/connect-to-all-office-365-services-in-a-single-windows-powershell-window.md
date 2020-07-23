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
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="cd467-103">1つの Windows PowerShell ウィンドウですべての Microsoft 365 サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="cd467-103">Connect to all Microsoft 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="cd467-104">PowerShell を使用して Microsoft 365 を管理する場合は、Microsoft 365 管理センター、SharePoint Online、Exchange Online、Skype for Business Online、Microsoft Teams、セキュリティコンプライアンスセンターに対応して、最大5つの Windows PowerShell セッションを同時に開くことができ &amp; ます。</span><span class="sxs-lookup"><span data-stu-id="cd467-104">When you use PowerShell to manage Microsoft 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="cd467-105">別々の Windows PowerShell セッションで 5 つの異なる接続方法を使用すると、デスクトップは以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="cd467-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![一度に実行している 5 つの Windows PowerShell コンソール](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="cd467-107">これは、Microsoft 365 の管理には適していません。これら5つの windows 間でデータを交換することはできません。</span><span class="sxs-lookup"><span data-stu-id="cd467-107">This is not optimal for managing Microsoft 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="cd467-108">このトピックでは、Windows PowerShell の単一のインスタンスを使用する方法について説明します。これには、Microsoft 365 アカウント、Skype for Business Online、Exchange Online、SharePoint Online、Microsoft Teams、およびセキュリティコンプライアンスセンターを管理でき &amp; ます。</span><span class="sxs-lookup"><span data-stu-id="cd467-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Microsoft 365 accounts, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="cd467-109">現在、この記事には、ワールドワイド (+ GCC) クラウドに接続するためのコマンドのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cd467-109">This article currently only contains the commands to connect to the Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="cd467-110">その他のノートには、他の Microsoft 365 クラウドへの接続に関する情報を含む記事へのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="cd467-110">Additional notes provide links to articles with information about connecting to the other Microsoft 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="cd467-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="cd467-111">Before you begin</span></span>

<span data-ttu-id="cd467-112">Windows PowerShell の単一のインスタンスからすべての Microsoft 365 を管理するには、事前に次の前提条件を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="cd467-112">Before you can manage all of Microsoft 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="cd467-113">これらの手順で使用する Microsoft 365 職場または学校アカウントは、Microsoft 365 管理者ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd467-113">The Microsoft 365 work or school account that you use for these procedures needs to be a member of a Microsoft 365 admin role.</span></span> <span data-ttu-id="cd467-114">詳細については、[「管理者ロールについて」](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd467-114">For more information, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).</span></span> <span data-ttu-id="cd467-115">これは、Microsoft 365 用の PowerShell の要件です。これは、その他の Microsoft 365 サービスには必ずしも必要ありません。</span><span class="sxs-lookup"><span data-stu-id="cd467-115">This a requirement for PowerShell for Microsoft 365, not necessarily for all other Microsoft 365 services.</span></span>
    
- <span data-ttu-id="cd467-116">次の Windows の 64 ビット バージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cd467-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="cd467-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="cd467-117">Windows 10</span></span>
    
  - <span data-ttu-id="cd467-118">Windows 8.1 または Windows 8</span><span class="sxs-lookup"><span data-stu-id="cd467-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="cd467-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="cd467-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="cd467-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="cd467-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="cd467-121">Windows Server 2012 R2 または Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="cd467-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="cd467-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="cd467-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="cd467-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="cd467-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="cd467-124">\*Microsoft .NET Framework 4.5 をインストールする必要があります。*x*をクリックし、Windows management framework 3.0 または Windows management framework 4.0 のどちらかを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd467-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="cd467-125">詳細については、「.NET Framework と[Windows management framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)または[windows management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)[のインストール](https://go.microsoft.com/fwlink/p/?LinkId=257868)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd467-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="cd467-126">Skype for Business Online のモジュールと Microsoft 365 のモジュールのいずれかの要件があるため、64ビットバージョンの Windows を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd467-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Microsoft 365 modules.</span></span>
    
- <span data-ttu-id="cd467-127">Azure Active Directory (Azure AD)、Exchange Online、SharePoint Online、Skype for Business Online、Teams に必要なモジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd467-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="cd467-128">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="cd467-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="cd467-129">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="cd467-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="cd467-130">Skype for Business Online、Windows PowerShell モジュール</span><span class="sxs-lookup"><span data-stu-id="cd467-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="cd467-131">Exchange Online PowerShell V2</span><span class="sxs-lookup"><span data-stu-id="cd467-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="cd467-132">Teams PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="cd467-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="cd467-133">Windows PowerShell は、Skype for Business Online およびセキュリティ/コンプライアンスセンターの署名済みスクリプトを実行するように構成する必要があり &amp; ます。</span><span class="sxs-lookup"><span data-stu-id="cd467-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="cd467-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span><span class="sxs-lookup"><span data-stu-id="cd467-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-just-a-password"></a><span data-ttu-id="cd467-135">パスワードのみを使用する場合の接続手順</span><span class="sxs-lookup"><span data-stu-id="cd467-135">Connection steps when using just a password</span></span>

<span data-ttu-id="cd467-136">サインインのパスワードのみを使用している場合は、1つの PowerShell ウィンドウですべてのサービスに接続する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cd467-136">Here are the steps to connect to all the services in a single PowerShell window when you are using just a password for sign-in.</span></span>
  
1. <span data-ttu-id="cd467-137">Windows PowerShell を開きます。</span><span class="sxs-lookup"><span data-stu-id="cd467-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="cd467-138">このコマンドを実行して、Microsoft 365 職場または学校のアカウントの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="cd467-138">Run this command and enter your Microsoft 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="cd467-139">このコマンドを実行して、azure Active Directory PowerShell for Graph モジュールを使用して Azure AD に接続します。</span><span class="sxs-lookup"><span data-stu-id="cd467-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="cd467-140">または、Windows PowerShell 用 Microsoft Azure Active Directory モジュールモジュールを使用している場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cd467-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="cd467-141">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="cd467-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="cd467-142">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd467-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="cd467-143">次のコマンドを実行して、SharePoint Online に接続します。</span><span class="sxs-lookup"><span data-stu-id="cd467-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="cd467-144">ドメインの組織名を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd467-144">Specify the organization name for your domain.</span></span> <span data-ttu-id="cd467-145">たとえば、"litwareinc.onmicrosoft.com" の場合、組織名の値は "litwareinc" です。</span><span class="sxs-lookup"><span data-stu-id="cd467-145">For example, for "litwareinc.onmicrosoft.com", the  organization name value is "litwareinc".</span></span>
    
  ```powershell
  $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
  Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
  ```

5. <span data-ttu-id="cd467-p109">次のコマンドを実行して、Skype for Business Online に接続します。初めて接続する場合、`WSMan NetworkDelayms` の値を増やすようにという警告が出ますが、無視してください。</span><span class="sxs-lookup"><span data-stu-id="cd467-p109">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="cd467-148">Exchange Online に接続するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cd467-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="cd467-149">全世界以外の Microsoft 365 クラウドの Exchange Online に接続するには、 **-exchangeの name**パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd467-149">To connect to Exchange Online for Microsoft 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="cd467-150">詳細については[、「Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd467-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="cd467-151">これらのコマンドを実行して Teams PowerShell に接続します。</span><span class="sxs-lookup"><span data-stu-id="cd467-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="cd467-152">全世界以外の Microsoft Teams クラウドに接続する方法については、「 [connect-](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps)microsoft teams」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd467-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="cd467-153">次のコマンドを実行して、セキュリティ センターとコンプライアンス センター に接続します。</span><span class="sxs-lookup"><span data-stu-id="cd467-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="cd467-154">&amp;全世界以外の Microsoft 365 クラウドのセキュリティコンプライアンスセンターに接続する方法については、「 [Connect to Security & コンプライアンスセンター PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd467-154">To connect to the Security &amp; Compliance Center for Microsoft 365 clouds other than Worldwide, see [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="cd467-155">Azure Active Directory PowerShell for Graph モジュールを使用している場合、1つのブロック内のすべてのコマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="cd467-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="cd467-156">ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="cd467-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="cd467-157">また、「Windows PowerShell 用 Microsoft Azure Active Directory モジュール」モジュールを使用している場合は、1つのブロック内のすべてのコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cd467-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="cd467-158">ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="cd467-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="cd467-159">Windows PowerShell ウィンドウを閉じる準備ができたら、次のコマンドを実行して、Skype for Business Online、SharePoint Online、セキュリティ &amp; コンプライアンスセンター、および Teams へのアクティブなセッションを削除します。</span><span class="sxs-lookup"><span data-stu-id="cd467-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="cd467-160">多要素認証を使用する場合の接続手順</span><span class="sxs-lookup"><span data-stu-id="cd467-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="cd467-161">Azure AD、SharePoint Online、Skype for Business、Exchange Online、および複数要素認証を使用する1つのウィンドウで多要素認証を使用するすべてのコマンドを1つのブロックにまとめたものです。そのためには、Azure Active Directory PowerShell for Graph モジュールを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd467-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="cd467-162">ユーザーアカウントのユーザープリンシパル名 (UPN) 名とドメインホスト名を指定し、それらを一度にすべて実行します。</span><span class="sxs-lookup"><span data-stu-id="cd467-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="cd467-163">または、「Windows PowerShell 用 Microsoft Azure Active Directory モジュール」モジュールを使用する場合のすべてのコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cd467-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="cd467-164">セキュリティ/コンプライアンスセンターの場合は、多要素認証を使用 &amp; して接続するために、「 [Connect to Security & コンプライアンスセンターの PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd467-164">For the Security &amp; Compliance Center, see [Connect to Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="cd467-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd467-165">See also</span></span>

- [<span data-ttu-id="cd467-166">PowerShell を使用して Microsoft 365 に接続する</span><span class="sxs-lookup"><span data-stu-id="cd467-166">Connect to Microsoft 365 with PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="cd467-167">PowerShell を使用して SharePoint Online を管理する</span><span class="sxs-lookup"><span data-stu-id="cd467-167">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="cd467-168">PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="cd467-168">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="cd467-169">Windows PowerShell を使用して Microsoft 365 でレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="cd467-169">Use Windows PowerShell to create reports in Microsoft 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
