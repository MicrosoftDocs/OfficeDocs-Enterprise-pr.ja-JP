---
title: 単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/17/2020
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
description: '概要: 単一の Windows PowerShell ウィンドウで Windows PowerShell をすべての Office 365 サービスに接続します。'
ms.openlocfilehash: d47f4dab4938bd02be25525d2912604f676079db
ms.sourcegitcommit: 58aa8b2e89685490f849e0392d566b7bfb7b933e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547755"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="05460-103">単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="05460-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

<span data-ttu-id="05460-104">PowerShell を使用して Office 365 を管理する場合は、Microsoft 365 管理センター、SharePoint Online、Exchange Online、Skype for Business Online、Microsoft Teams、セキュリティ&amp;コンプライアンスセンターに対応して、最大5つの Windows PowerShell セッションを同時に開くことができます。</span><span class="sxs-lookup"><span data-stu-id="05460-104">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="05460-105">別々の Windows PowerShell セッションで 5 つの異なる接続方法を使用すると、デスクトップは以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="05460-105">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![一度に実行している 5 つの Windows PowerShell コンソール](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="05460-107">これは、クロスサービス管理のための5つのウィンドウ間でデータを交換できないため、Office 365 の管理には最適ではありません。</span><span class="sxs-lookup"><span data-stu-id="05460-107">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management.</span></span> <span data-ttu-id="05460-108">このトピックでは、Office 365、Skype for Business Online、Exchange Online、SharePoint Online、Microsoft Teams、およびセキュリティ&amp;コンプライアンスセンターを管理できる、Windows PowerShell の単一のインスタンスを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="05460-108">This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, Microsoft Teams, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="05460-109">現時点では、Office 365 ワールドワイド (+ GCC) クラウドに接続するためのコマンドのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="05460-109">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="05460-110">その他のノートには、他の Office 365 クラウドへの接続に関する情報を含む記事へのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="05460-110">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="05460-111">はじめに</span><span class="sxs-lookup"><span data-stu-id="05460-111">Before you begin</span></span>

<span data-ttu-id="05460-112">Windows PowerShell の単一のインスタンスからすべての Office 365 を管理する前に、次の前提条件を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="05460-112">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="05460-p104">これらの手順に使用する Office 365職場または学校のアカウント は、Office 365 管理者役割のメンバーである必要があります。詳細については、「[Office 365 の管理者の役割](https://go.microsoft.com/fwlink/p/?LinkId=532367)」を参照してください。これは Office 365 PowerShell の要件であり、他のすべての Office 365 サービスについては必ずしも当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="05460-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="05460-116">次の Windows の 64 ビット バージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="05460-116">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="05460-117">Windows 10</span><span class="sxs-lookup"><span data-stu-id="05460-117">Windows 10</span></span>
    
  - <span data-ttu-id="05460-118">Windows 8.1 または Windows 8</span><span class="sxs-lookup"><span data-stu-id="05460-118">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="05460-119">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="05460-119">Windows Server 2019</span></span>
    
  - <span data-ttu-id="05460-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="05460-120">Windows Server 2016</span></span>
    
  - <span data-ttu-id="05460-121">Windows Server 2012 R2 または Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="05460-121">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="05460-122">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="05460-122">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="05460-123">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="05460-123">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="05460-124">\*Microsoft .NET Framework 4.5 をインストールする必要があります。*x*をクリックし、Windows management framework 3.0 または Windows management framework 4.0 のどちらかを選択します。</span><span class="sxs-lookup"><span data-stu-id="05460-124">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="05460-125">詳細については、「.NET Framework と[Windows management framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)または[windows management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)[のインストール](https://go.microsoft.com/fwlink/p/?LinkId=257868)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05460-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="05460-126">Skype for Business Online モジュール、および Office 365 モジュールの 1 つの要件のため、64 ビット バージョンの Windows を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05460-126">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="05460-127">Azure AD、Exchange Online、SharePoint Online、Skype for Business Online、Teams に必要なモジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="05460-127">You need to install the modules that are required for Azure AD, Exchange Online, SharePoint Online, Skype for Business Online and Teams:</span></span>
    
   - [<span data-ttu-id="05460-128">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="05460-128">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="05460-129">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="05460-129">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="05460-130">Skype for Business Online、Windows PowerShell モジュール</span><span class="sxs-lookup"><span data-stu-id="05460-130">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
   - [<span data-ttu-id="05460-131">Exchange Online PowerShell V2</span><span class="sxs-lookup"><span data-stu-id="05460-131">Exchange Online PowerShell V2</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell-v2/exchange-online-powershell-v2?view=exchange-ps#install-and-maintain-the-exchange-online-powershell-v2-module)
   - [<span data-ttu-id="05460-132">Teams PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="05460-132">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
    
-  <span data-ttu-id="05460-133">Windows PowerShell は、Skype for Business Online およびセキュリティ&amp; /コンプライアンスセンターの署名済みスクリプトを実行するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05460-133">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="05460-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span><span class="sxs-lookup"><span data-stu-id="05460-134">To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="05460-135">パスワードを使用する場合の接続手順</span><span class="sxs-lookup"><span data-stu-id="05460-135">Connection steps when using a password</span></span>

<span data-ttu-id="05460-136">1つの PowerShell ウィンドウですべてのサービスに接続する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="05460-136">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="05460-137">Windows PowerShell を開きます。</span><span class="sxs-lookup"><span data-stu-id="05460-137">Open Windows PowerShell.</span></span>
    
2. <span data-ttu-id="05460-138">このコマンドを実行して、Office 365 の職場または学校のアカウントの資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="05460-138">Run this command and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="05460-139">このコマンドを実行して、azure active directory PowerShell for Graph モジュールを使用して Azure Active Directory (AD) に接続します。</span><span class="sxs-lookup"><span data-stu-id="05460-139">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="05460-140">または、Windows PowerShell 用 Microsoft Azure Active Directory モジュールモジュールを使用している場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="05460-140">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="05460-141">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="05460-141">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="05460-142">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05460-142">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="05460-143">次のコマンドを実行して、SharePoint Online に接続します。</span><span class="sxs-lookup"><span data-stu-id="05460-143">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="05460-144">_ \<Domainhost>_ をドメインの実際の値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="05460-144">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="05460-145">たとえば、"litwareinc.onmicrosoft.com" の場合、 _ \<domainhost>_ の値は "litwareinc" です。</span><span class="sxs-lookup"><span data-stu-id="05460-145">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="05460-p109">次のコマンドを実行して、Skype for Business Online に接続します。初めて接続する場合、`WSMan NetworkDelayms` の値を増やすようにという警告が出ますが、無視してください。</span><span class="sxs-lookup"><span data-stu-id="05460-p109">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="05460-148">Exchange Online に接続するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="05460-148">Run this command to connect to Exchange Online.</span></span>
    
  ```powershell
  Connect-ExchangeOnline -Credential $credential -ShowProgress $true
  ```

>[!Note]
><span data-ttu-id="05460-149">全世界以外の Office 365 クラウドの Exchange Online に接続するには、 **-exchangeの name**パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="05460-149">To connect to Exchange Online for Office 365 clouds other than Worldwide, use the **-ExchangeEnvironmentName** parameter.</span></span> <span data-ttu-id="05460-150">詳細については[、「Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05460-150">See [Connect-ExchangeOnline](https://docs.microsoft.com/powershell/module/exchange/powershell-v2-module/connect-exchangeonline?view=exchange-ps) for more information.</span></span>
>

7. <span data-ttu-id="05460-151">これらのコマンドを実行して Teams PowerShell に接続します。</span><span class="sxs-lookup"><span data-stu-id="05460-151">Run these commands to connect to Teams PowerShell.</span></span>
    
  ```powershell
  Import-Module MicrosoftTeams
  Connect-MicrosoftTeams -Credential $credential
  ```
  
>[!Note]
><span data-ttu-id="05460-152">全世界以外の Microsoft Teams クラウドに接続する方法については、「 [connect-](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps)microsoft teams」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05460-152">To connect to Microsoft Teams clouds other than Worldwide, see [Connect-MicrosoftTeams](https://docs.microsoft.com/powershell/module/teams/connect-microsoftteams?view=teams-ps).</span></span>
>

8. <span data-ttu-id="05460-153">次のコマンドを実行して、セキュリティ センターとコンプライアンス センター に接続します。</span><span class="sxs-lookup"><span data-stu-id="05460-153">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="05460-154">全世界以外の Office 365 &amp;クラウドのセキュリティコンプライアンスセンターに接続する方法については、「 [connect To office 365 Security & コンプライアンスセンター PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05460-154">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="05460-155">Azure Active Directory PowerShell for Graph モジュールを使用している場合、1つのブロック内のすべてのコマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="05460-155">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="05460-156">ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="05460-156">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="05460-157">また、「Windows PowerShell 用 Microsoft Azure Active Directory モジュール」モジュールを使用している場合は、1つのブロック内のすべてのコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="05460-157">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="05460-158">ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="05460-158">Specify the name of your domain host, and then run them all at one time.</span></span>
  
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

<span data-ttu-id="05460-159">Windows PowerShell ウィンドウを閉じる準備ができたら、次のコマンドを実行して、Skype for Business Online、SharePoint Online、セキュリティ&amp;コンプライアンスセンター、および Teams へのアクティブなセッションを削除します。</span><span class="sxs-lookup"><span data-stu-id="05460-159">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, SharePoint Online, the Security &amp; Compliance Center, and Teams:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $SccSession ; Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="05460-160">多要素認証を使用する場合の接続手順</span><span class="sxs-lookup"><span data-stu-id="05460-160">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="05460-161">Azure AD、SharePoint Online、Skype for Business、Exchange Online、および複数要素認証を使用する1つのウィンドウで多要素認証を使用するすべてのコマンドを1つのブロックにまとめたものです。そのためには、Azure Active Directory PowerShell for Graph モジュールを使用します。</span><span class="sxs-lookup"><span data-stu-id="05460-161">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, Skype for Business, Exchange Online, and Teams using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="05460-162">ユーザーアカウントのユーザープリンシパル名 (UPN) 名とドメインホスト名を指定し、それらを一度にすべて実行します。</span><span class="sxs-lookup"><span data-stu-id="05460-162">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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

<span data-ttu-id="05460-163">または、「Windows PowerShell 用 Microsoft Azure Active Directory モジュール」モジュールを使用する場合のすべてのコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="05460-163">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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

<span data-ttu-id="05460-164">セキュリティ&amp; /コンプライアンスセンターについては、「 [connect To Office 365 Security & 多要素認証を使用して](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)多要素認証を使用して接続する PowerShell」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05460-164">For the Security &amp; Compliance Center, see [Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps) to connect using multi-factor authentication:</span></span>

## <a name="see-also"></a><span data-ttu-id="05460-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="05460-165">See also</span></span>

- [<span data-ttu-id="05460-166">Office 365 PowerShell への接続</span><span class="sxs-lookup"><span data-stu-id="05460-166">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="05460-167">Office 365 PowerShell を使用して SharePoint Online を管理する</span><span class="sxs-lookup"><span data-stu-id="05460-167">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="05460-168">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="05460-168">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="05460-169">Windows PowerShell を使用して Office 365 でレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="05460-169">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
