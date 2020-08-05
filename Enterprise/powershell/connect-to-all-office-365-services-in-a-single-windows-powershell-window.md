---
title: 単一の Windows PowerShell ウィンドウですべての Microsoft 365 サービスに接続する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: '概要: 単一の Windows PowerShell ウィンドウで Windows PowerShell をすべての Microsoft 365 サービスに接続します。'
ms.openlocfilehash: de6bb592233b44a14848b1512230197bb8eb75fb
ms.sourcegitcommit: 1aaa4c6d10eb14f4b3d5a452f2e64c96f5d96ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "46560062"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="86016-103">単一の Windows PowerShell ウィンドウですべての Microsoft 365 サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="86016-103">Connect to all Microsoft 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="86016-104">PowerShell を使用して Microsoft 365 を管理する場合は、Microsoft 365 管理センター、SharePoint Online、Exchange Online、Skype for Business Online、Microsoft Teams、および セキュリティ &amp; コンプライアンス センターに対応する最大 5 つの異なる Windows PowerShell セッションを同時に開くことができます。</span><span class="sxs-lookup"><span data-stu-id="86016-104">When you use PowerShell to manage Microsoft 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="86016-105">別々の Windows PowerShell セッションで 5 つの異なる接続方法を使用すると、デスクトップは以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="86016-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![一度に実行している 5 つの Windows PowerShell コンソール](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="86016-107">これは Microsoft 365 の管理に最適な状況ではありません。サービス間管理のために 5 つのウィンドウ間でデータを交換できないからです。</span><span class="sxs-lookup"><span data-stu-id="86016-107">This is not optimal for managing Microsoft 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="86016-108">このトピックでは、Microsoft 365アカウント、Skype for Business Online、Exchange Online、SharePoint Online、Microsoft Teams、およびセキュリティ &amp; コンプライアンス センターを管理する Windows PowerShell の単一のインスタンスを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="86016-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Microsoft 365 accounts, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="86016-109">この記事には現在、ワールドワイド (+ GCC) クラウドに接続するコマンドのみ含まれています。</span><span class="sxs-lookup"><span data-stu-id="86016-109">This article currently only contains the commands to connect to the Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="86016-110">追加のメモには、他の Microsoft 365 クラウドへの接続に関する情報が掲載されています。</span><span class="sxs-lookup"><span data-stu-id="86016-110">Additional notes provide links to articles with information about connecting to the other Microsoft 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="86016-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="86016-111">Before you begin</span></span>

<span data-ttu-id="86016-112">Windows PowerShell の単一のインスタンスからすべての Microsoft 365 を管理する前に、次の前提条件を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="86016-112">Before you can manage all of Microsoft 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="86016-113">これらの手順に使用する Microsoft 365 の職場または学校のアカウントは、Microsoft 365 管理者ロールのメンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="86016-113">The Microsoft 365 work or school account that you use for these procedures needs to be a member of a Microsoft 365 admin role.</span></span> <span data-ttu-id="86016-114">詳細については、[「管理者の役割について」](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86016-114">For more information, see [About admin roles](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).</span></span> <span data-ttu-id="86016-115">これは Microsoft 365向け PowerShell の要件であり、他のすべての Microsoft 365 サービスについては必ずしも当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="86016-115">This a requirement for PowerShell for Microsoft 365, not necessarily for all other Microsoft 365 services.</span></span>
    
- <span data-ttu-id="86016-116">次の Windows の 64 ビット バージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="86016-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="86016-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="86016-117">Windows 10</span></span>
    
  - <span data-ttu-id="86016-118">Windows 8.1 または Windows 8</span><span class="sxs-lookup"><span data-stu-id="86016-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="86016-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="86016-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="86016-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="86016-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="86016-121">Windows Server 2012 R2 または Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="86016-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="86016-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="86016-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="86016-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="86016-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="86016-124">\*Microsoft .NET Framework 4.5.*x* をインストールしてから、Windows Management Framework 3.0 または Windows Management Framework 4.0 のどちらかをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86016-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="86016-125">詳細については、「[.NET Framework のインストール](https://go.microsoft.com/fwlink/p/?LinkId=257868)」と、「[Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)」または「[Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86016-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="86016-126">Skype for Business Online モジュール、および Microsoft 365 モジュールの要件のため、64 ビット バージョンの Windows を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86016-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Microsoft 365 modules.</span></span>
    
- <span data-ttu-id="86016-127">Azure Active Directory (Azure AD)、Exchange Online、SharePoint Online、Skype for Business Online、および Teams に必要なモジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86016-127">You need to install the modules that are required for Azure Active Directory (Azure AD), Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="86016-128">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="86016-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="86016-129">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="86016-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="86016-130">Skype for Business Online、Windows PowerShell モジュール</span><span class="sxs-lookup"><span data-stu-id="86016-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="86016-131">Exchange Online PowerShell V2</span><span class="sxs-lookup"><span data-stu-id="86016-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="86016-132">Teams での PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="86016-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="86016-133">Skype for Business Online、およびセキュリティ &amp; コンプライアンス センターに対して署名付きスクリプトを実行するよう Windows PowerShell を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86016-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="86016-134">そのためには、管理者特権の Windows PowerShell セッション (Windows PowerShell ウィンドウで **[管理者として実行]** を選択して開きます) で、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="86016-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a><span data-ttu-id="86016-135">パスワードだけを使用する場合の接続手順</span><span class="sxs-lookup"><span data-stu-id="86016-135">Connection steps when using just a password</span></span>

<span data-ttu-id="86016-136">ここでは、サインインにパスワードだけを使用する場合に、単一の PowerShell ウィンドウ内ですべてのサービスに接続するための手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="86016-136">Here are the steps to connect to all the services in a single PowerShell window when you are using just a password for sign-in.</span></span>
  
1. <span data-ttu-id="86016-137">Windows PowerShell を開きます。</span><span class="sxs-lookup"><span data-stu-id="86016-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="86016-138">次のコマンドを実行し、Microsoft 365職場または学校のアカウントの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="86016-138">Run this command and enter your Microsoft 365 work or school account credentials.</span></span>
    
   ```powershell
   $credential = Get-Credential
   ```

3. <span data-ttu-id="86016-139">次のコマンドを実行して、Azure Active Directory PowerShell for Graph モジュールを使用して Azure AD に接続します。</span><span class="sxs-lookup"><span data-stu-id="86016-139">Run this command to connect to Azure AD using the Azure Active Directory PowerShell for Graph module.</span></span>
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   <span data-ttu-id="86016-140">または、Windows PowerShell モジュール用 Microsoft Azure Active Directory モジュールを使用する場合、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="86016-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > <span data-ttu-id="86016-141">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="86016-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="86016-142">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86016-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>

4. <span data-ttu-id="86016-143">次のコマンドを実行して、SharePoint Online に接続します。</span><span class="sxs-lookup"><span data-stu-id="86016-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="86016-144">ドメインの組織名を指定します。</span><span class="sxs-lookup"><span data-stu-id="86016-144">Specify the organization name for your domain.</span></span> <span data-ttu-id="86016-145">たとえば、"litwareinc.onmicrosoft.com" の場合、組織名の値は "litwareinc" です。</span><span class="sxs-lookup"><span data-stu-id="86016-145">For example, for "litwareinc.onmicrosoft.com", the  organization name value is "litwareinc".</span></span>
    
   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $userCredential
   ```

5. <span data-ttu-id="86016-p109">次のコマンドを実行して、Skype for Business Online に接続します。初めて接続する場合、`WSMan NetworkDelayms` の値を増やすようにという警告が出ますが、無視してください。</span><span class="sxs-lookup"><span data-stu-id="86016-p109">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
     
   ```powershell
   Import-Module SkypeOnlineConnector
   $sfboSession = New-CsOnlineSession -Credential $credential
   Import-PSSession $sfboSession
   ```

6. <span data-ttu-id="86016-148">次のコマンドを実行して、Exchange Online に接続します。</span><span class="sxs-lookup"><span data-stu-id="86016-148">Run this command to connect to Exchange Online.</span></span>
    
   ```powershell
   Connect-ExchangeOnline -Credential $credential -ShowProgress $true
   ```

   > [!Note]
   > <span data-ttu-id="86016-149">全世界以外の Exchange Online for Microsoft 365 クラウドに接続するには、**-ExchangeEnvironmentName** パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="86016-149">To connect to Exchange Online for Microsoft 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="86016-150">詳細については、[「Connect-ExchangeOnline」](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86016-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>

7. <span data-ttu-id="86016-151">次のコマンドを実行して、Teams PowerShell に接続します。</span><span class="sxs-lookup"><span data-stu-id="86016-151">Run these commands to connect to Teams PowerShell.</span></span>
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > <span data-ttu-id="86016-152">全世界以外の Microsoft Teams クラウドに接続する方法については、[「Connect-MicrosoftTeams」](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86016-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>

8. <span data-ttu-id="86016-153">次のコマンドを実行して、セキュリティ &amp; コンプライアンス センター に接続します。</span><span class="sxs-lookup"><span data-stu-id="86016-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
   ```powershell
   $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
   Import-PSSession $SccSession -Prefix cc
   ```

   > [!Note]
   > <span data-ttu-id="86016-154">Microsoft 365 クラウド向けセキュリティ &amp; コンプライアンス センターに接続するには、[「セキュリティ/コンプライアンス センター PowerShell に接続する」](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86016-154">To connect to the Security &amp; Compliance Center for Microsoft 365 clouds other than Worldwide, see [Connect to Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>

<span data-ttu-id="86016-155">Azure Active Directory PowerShell for Graph モジュールを使用しているときに、単一のブロック内のすべてのコマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="86016-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="86016-156">ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="86016-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="86016-157">または、Windows PowerShell モジュール用 Microsoft Azure Active Directory モジュールを使用しているときに、単一のブロック内のすべてのコマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="86016-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="86016-158">ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="86016-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="86016-159">Windows PowerShell ウィンドウを閉じる準備が整った段階で次のコマンドを実行し、Skype for Business Online、SharePoint Online、セキュリティ &amp; コンプライアンス センター、および Teams に対するアクティブなセッションを削除します。</span><span class="sxs-lookup"><span data-stu-id="86016-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="86016-160">多要素認証を使用する場合の接続手順</span><span class="sxs-lookup"><span data-stu-id="86016-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="86016-161">ここでは、Azure AD、SharePoint Online、Skype for Business、Exchange Online、および Azure Active Directory PowerShell for Graph モジュールを使用する単一のウィンドウ内で多要素認証を使用する Teams に接続するすべてのコマンドを示します。</span><span class="sxs-lookup"><span data-stu-id="86016-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="86016-162">ユーザー アカウントのユーザー プリンシパル名 (UPN)、およびドメインのホスト名を指定し、一度にそれらを実行します。</span><span class="sxs-lookup"><span data-stu-id="86016-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="86016-163">または、ここでは Windows PowerShell モジュール用 Microsoft Azure Active Directory モジュールを使用する場合のすべてのコマンドを示します。</span><span class="sxs-lookup"><span data-stu-id="86016-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="86016-164">セキュリティ &amp; コンプライアンス センター向けに、多要素認証を使用して接続する方法は、[「多要素認証を使用してセキュリティ/コンプライアンス センター PowerShell に接続する」](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86016-164">For the Security &amp; Compliance Center, see [Connect to Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="86016-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="86016-165">See also</span></span>

- [<span data-ttu-id="86016-166">PowerShell を使用して Microsoft 365 に接続する</span><span class="sxs-lookup"><span data-stu-id="86016-166">Connect to Microsoft 365 with PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="86016-167">PowerShell を使用して SharePoint Online を管理する</span><span class="sxs-lookup"><span data-stu-id="86016-167">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="86016-168">Microsoft 365 ユーザー アカウント、ライセンス、PowerShell を使用したグループを管理する</span><span class="sxs-lookup"><span data-stu-id="86016-168">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="86016-169">Windows PowerShell を使用して Microsoft 365 でレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="86016-169">Use Windows PowerShell to create reports in Microsoft 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
