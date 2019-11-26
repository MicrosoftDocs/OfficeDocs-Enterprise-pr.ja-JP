---
title: 単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/28/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: '概要: 単一の Windows PowerShell ウィンドウで Windows PowerShell をすべての Office 365 サービスに接続します。'
ms.openlocfilehash: c8390b3d704fa9df64f147a942891308b1ed825f
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257426"
---
# <a name="connect-to-all-office-365-services-in-a-single-windows-powershell-window"></a><span data-ttu-id="f24f8-103">単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="f24f8-103">Connect to all Office 365 services in a single Windows PowerShell window</span></span>

 <span data-ttu-id="f24f8-104">**概要:** 別々の PowerShell コンソール ウィンドウで各種 Office 365 サービスを管理するのではなく、1 つのコンソール ウィンドウからすべての Office 365 サービスに接続して管理できます。</span><span class="sxs-lookup"><span data-stu-id="f24f8-104">**Summary:** Instead of managing different Office 365 services in separate PowerShell console windows, you can connect to all Office 365 services and manage them from single console window.</span></span>
  
<span data-ttu-id="f24f8-105">PowerShell を使用して Office 365 を管理する場合は、Microsoft 365 管理センター、SharePoint Online、Exchange Online、Skype for Business Online、セキュリティ&amp;コンプライアンスセンターに対応して、最大5つの Windows PowerShell セッションを同時に開くことができます。</span><span class="sxs-lookup"><span data-stu-id="f24f8-105">When you use PowerShell to manage Office 365, it is possible to have up to five different Windows PowerShell sessions open at the same time corresponding to Microsoft 365 admin center, SharePoint Online, Exchange Online, Skype for Business Online, and the Security &amp; Compliance Center.</span></span> <span data-ttu-id="f24f8-106">別々の Windows PowerShell セッションで 5 つの異なる接続方法を使用すると、デスクトップは以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="f24f8-106">With five different connection methods in separate Windows PowerShell sessions, your desktop could look like this:</span></span>
  
![一度に実行している 5 つの Windows PowerShell コンソール](media/a1a852c2-89ea-4e8e-8d8b-dcdf596763d1.png)
  
<span data-ttu-id="f24f8-p102">これは Office 365 の管理に最適な状況ではありません。サービス間管理のために 5 つのウィンドウ間でデータを交換できないからです。このトピックでは、Office 365、Skype for Business Online、Exchange Online、SharePoint Online、および セキュリティ センターとコンプライアンス センター を管理する Windows PowerShell のインスタンスを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-p102">This is not optimal for managing Office 365 because you can't exchange data among those five windows for cross-service management. This topic describes how to use a single instance of Windows PowerShell from which you can manage Office 365, Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center.</span></span>

>[!Note]
><span data-ttu-id="f24f8-110">現時点では、Office 365 ワールドワイド (+ GCC) クラウドに接続するためのコマンドのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f24f8-110">This article currently only contains the commands to connect to the Office 365 Worldwide (+GCC) cloud.</span></span> <span data-ttu-id="f24f8-111">その他のノートには、他の Office 365 クラウドへの接続に関する情報を含む記事へのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="f24f8-111">Additional notes provide links to articles with information about connecting to the other Office 365 clouds.</span></span>
>

## <a name="before-you-begin"></a><span data-ttu-id="f24f8-112">始める前に</span><span class="sxs-lookup"><span data-stu-id="f24f8-112">Before you begin</span></span>

<span data-ttu-id="f24f8-113">Windows PowerShell の単一のインスタンスからすべての Office 365 を管理する前に、次の前提条件を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="f24f8-113">Before you can manage all of Office 365 from a single instance of Windows PowerShell, consider the following prerequisites:</span></span>
  
- <span data-ttu-id="f24f8-p104">これらの手順に使用する Office 365職場または学校のアカウント は、Office 365 管理者役割のメンバーである必要があります。詳細については、「[Office 365 の管理者の役割](https://go.microsoft.com/fwlink/p/?LinkId=532367)」を参照してください。これは Office 365 PowerShell の要件であり、他のすべての Office 365 サービスについては必ずしも当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="f24f8-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367). This a requirement for Office 365 PowerShell, not necessarily for all other Office 365 services.</span></span>
    
- <span data-ttu-id="f24f8-117">次の Windows の 64 ビット バージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f24f8-117">You can use the following 64-bit versions of Windows:</span></span>
    
  - <span data-ttu-id="f24f8-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="f24f8-118">Windows 10</span></span>
    
  - <span data-ttu-id="f24f8-119">Windows 8.1 または Windows 8</span><span class="sxs-lookup"><span data-stu-id="f24f8-119">Windows 8.1 or Windows 8</span></span>
    
  - <span data-ttu-id="f24f8-120">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="f24f8-120">Windows Server 2019</span></span>
    
  - <span data-ttu-id="f24f8-121">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="f24f8-121">Windows Server 2016</span></span>
    
  - <span data-ttu-id="f24f8-122">Windows Server 2012 R2 または Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="f24f8-122">Windows Server 2012 R2 or Windows Server 2012</span></span>
    
  - <span data-ttu-id="f24f8-123">Windows 7 Service Pack 1 (SP1)\*</span><span class="sxs-lookup"><span data-stu-id="f24f8-123">Windows 7 Service Pack 1 (SP1)\*</span></span>
    
  - <span data-ttu-id="f24f8-124">Windows Server 2008 R2 SP1\*</span><span class="sxs-lookup"><span data-stu-id="f24f8-124">Windows Server 2008 R2 SP1\*</span></span>
    
    <span data-ttu-id="f24f8-125">\*Microsoft .NET Framework 4.5 をインストールする必要があります。*x*をクリックし、Windows management framework 3.0 または Windows management framework 4.0 のどちらかを選択します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-125">\* You need to install the Microsoft .NET Framework 4.5.*x* and then either the Windows Management Framework 3.0 or the Windows Management Framework 4.0.</span></span> <span data-ttu-id="f24f8-126">詳細については、「.NET Framework と[Windows management framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757)または[windows management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344)[のインストール](https://go.microsoft.com/fwlink/p/?LinkId=257868)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f24f8-126">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868) and [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757) or [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344).</span></span>
    
    <span data-ttu-id="f24f8-127">Skype for Business Online モジュール、および Office 365 モジュールの 1 つの要件のため、64 ビット バージョンの Windows を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f24f8-127">You need to use a 64-bit version of Windows because of the requirements for the Skype for Business Online module and one of the Office 365 modules.</span></span>
    
- <span data-ttu-id="f24f8-128">Azure AD、SharePoint Online、Skype for Business Online に必要なモジュールをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f24f8-128">You need to install the modules that are required for Azure AD, SharePoint Online, and Skype for Business Online:</span></span>
    
   - [<span data-ttu-id="f24f8-129">Azure Active Directory V2</span><span class="sxs-lookup"><span data-stu-id="f24f8-129">Azure Active Directory V2</span></span>](connect-to-office-365-powershell.md##connect-with-the-azure-active-directory-powershell-for-graph-module)
   - [<span data-ttu-id="f24f8-130">SharePoint Online Management Shell</span><span class="sxs-lookup"><span data-stu-id="f24f8-130">SharePoint Online Management Shell</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=255251)
   - [<span data-ttu-id="f24f8-131">Skype for Business Online、Windows PowerShell モジュール</span><span class="sxs-lookup"><span data-stu-id="f24f8-131">Skype for Business Online, Windows PowerShell Module</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532439)
    
-  <span data-ttu-id="f24f8-p106">Skype for Business Online、Exchange Online、およびセキュリティ/コンプライアンス センターに対して署名付きスクリプトを実行するよう Windows PowerShell を構成する必要があります。そのためには、管理者特権の Windows PowerShell セッション (Windows PowerShell ウィンドウで **[管理者として実行]** を選択して開きます) で、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-p106">Windows PowerShell needs to be configured to run signed scripts for Skype for Business Online, Exchange Online, and the Security &amp; Compliance Center. To do this, run the following command in an elevated Windows PowerShell session (a Windows PowerShell window you open by selecting **Run as administrator**).</span></span>
    
  ```powershell
  Set-ExecutionPolicy RemoteSigned
  ```

## <a name="connection-steps-when-using-a-password"></a><span data-ttu-id="f24f8-134">パスワードを使用する場合の接続手順</span><span class="sxs-lookup"><span data-stu-id="f24f8-134">Connection steps when using a password</span></span>

<span data-ttu-id="f24f8-135">1つの PowerShell ウィンドウですべてのサービスに接続する手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-135">Here are the steps to connect to all the services in a single PowerShell window.</span></span>
  
1. <span data-ttu-id="f24f8-136">管理者として Windows PowerShell を開きます ( **[管理者として実行]** を使用)。</span><span class="sxs-lookup"><span data-stu-id="f24f8-136">Open Windows PowerShell as an administrator (use **Run as administrator**).</span></span>
    
2. <span data-ttu-id="f24f8-137">次のコマンドを実行し、Office 365職場または学校のアカウント の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-137">Run this command, and enter your Office 365 work or school account credentials.</span></span>
    
  ```powershell
  $credential = Get-Credential
  ```

3. <span data-ttu-id="f24f8-138">このコマンドを実行して、azure active directory PowerShell for Graph モジュールを使用して Azure Active Directory (AD) に接続します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-138">Run this command to connect to Azure Active Directory (AD) using the Azure Active Directory PowerShell for Graph module.</span></span>
    
  ```powershell
  Connect-AzureAD -Credential $credential
  ```
  
  <span data-ttu-id="f24f8-139">または、Windows PowerShell 用 Microsoft Azure Active Directory モジュールモジュールを使用している場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-139">Alternately, if you are using the Microsoft Azure Active Directory Module for Windows PowerShell module, run this command.</span></span>
      
  ```powershell
  Connect-MsolService -Credential $credential
 ```

>[!Note]
><span data-ttu-id="f24f8-140">PowerShell Core では、Microsoft Azure Active Directory モジュール for Windows PowerShell モジュールと、名前に**Msol**を指定したコマンドレットはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f24f8-140">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="f24f8-141">これらのコマンドレットを引き続き使用するには、これらのコマンドレットを Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f24f8-141">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

4. <span data-ttu-id="f24f8-142">次のコマンドを実行して、SharePoint Online に接続します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-142">Run these commands to connect to SharePoint Online.</span></span> <span data-ttu-id="f24f8-143">_ \<Domainhost>_ をドメインの実際の値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f24f8-143">Replace  _\<domainhost>_ with the actual value for your domain.</span></span> <span data-ttu-id="f24f8-144">たとえば、"litwareinc.onmicrosoft.com" の場合、 _ \<domainhost>_ の値は "litwareinc" です。</span><span class="sxs-lookup"><span data-stu-id="f24f8-144">For example, for "litwareinc.onmicrosoft.com", the  _\<domainhost>_ value is "litwareinc".</span></span>
    
  ```powershell
  Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
  Connect-SPOService -Url https://<domainhost>-admin.sharepoint.com -credential $credential
  ```

5. <span data-ttu-id="f24f8-p109">次のコマンドを実行して、Skype for Business Online に接続します。初めて接続する場合、`WSMan NetworkDelayms` の値を増やすようにという警告が出ますが、無視してください。</span><span class="sxs-lookup"><span data-stu-id="f24f8-p109">Run these commands to connect to Skype for Business Online. A warning about increasing the `WSMan NetworkDelayms` value is expected the first time you connect and should be ignored.</span></span>
    
  ```powershell
  Import-Module SkypeOnlineConnector
  $sfboSession = New-CsOnlineSession -Credential $credential
  Import-PSSession $sfboSession
  ```

6. <span data-ttu-id="f24f8-147">次のコマンドを実行して、Exchange Online に接続します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-147">Run these commands to connect to Exchange Online.</span></span>
    
  ```powershell
  $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $exchangeSession -DisableNameChecking
  ```

>[!Note]
><span data-ttu-id="f24f8-148">全世界以外の Office 365 クラウドの Exchange Online に接続する方法については、「 [Exchange Online PowerShell への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f24f8-148">To connect to Exchange Online for Office 365 clouds other than Worldwide, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).</span></span>
>

7. <span data-ttu-id="f24f8-149">次のコマンドを実行して、セキュリティ センターとコンプライアンス センター に接続します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-149">Run these commands to connect to the Security &amp; Compliance Center.</span></span>
    
  ```powershell
  $SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
  Import-PSSession $SccSession -Prefix cc
  ```

>[!Note]
><span data-ttu-id="f24f8-150">全世界以外の Office 365 &amp;クラウドのセキュリティコンプライアンスセンターに接続する方法については、「 [connect To office 365 Security & コンプライアンスセンター PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f24f8-150">To connect to the Security &amp; Compliance Center for Office 365 clouds other than Worldwide, see [Connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span></span>
>

<span data-ttu-id="f24f8-151">Azure Active Directory PowerShell for Graph モジュールを使用している場合、1つのブロック内のすべてのコマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="f24f8-151">Here are all the commands in a single block when using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="f24f8-152">ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-152">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-AzureAD -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="f24f8-153">また、「Windows PowerShell 用 Microsoft Azure Active Directory モジュール」モジュールを使用している場合は、1つのブロック内のすべてのコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-153">Alternately, here are all the commands in a single block when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span> <span data-ttu-id="f24f8-154">ドメイン ホストの名前を指定してから、それらすべてを同時に実行します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-154">Specify the name of your domain host, and then run them all at one time.</span></span>
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$credential = Get-Credential
Connect-MsolService -Credential $credential
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
Import-Module SkypeOnlineConnector
$sfboSession = New-CsOnlineSession -Credential $credential
Import-PSSession $sfboSession
$exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $exchangeSession -DisableNameChecking
$SccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $credential -Authentication "Basic" -AllowRedirection
Import-PSSession $SccSession -Prefix cc
```

<span data-ttu-id="f24f8-155">Windows PowerShell ウィンドウを閉じる準備が整った段階でこのコマンドを実行し、Skype for Business Online、Exchange Online、SharePoint Online、セキュリティ/コンプライアンス センターに対するアクティブなセッションを削除します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-155">When you are ready to close down the Windows PowerShell window, run this command to remove the active sessions to Skype for Business Online, Exchange Online, SharePoint Online, and the Security &amp; Compliance Center:</span></span>
  
```powershell
Remove-PSSession $sfboSession ; Remove-PSSession $exchangeSession ; Remove-PSSession $SccSession ; Disconnect-SPOService
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a><span data-ttu-id="f24f8-156">多要素認証を使用する場合の接続手順</span><span class="sxs-lookup"><span data-stu-id="f24f8-156">Connection steps when using multi-factor authentication</span></span>

<span data-ttu-id="f24f8-157">Azure Active Directory PowerShell for Graph モジュールを使用して、単一のウィンドウで多要素認証を使用して、Azure AD、SharePoint Online、および Skype for Buiness 接続するすべてのコマンドが、1つのブロックに含まれています。</span><span class="sxs-lookup"><span data-stu-id="f24f8-157">Here are all the commands in a single block to connect to Azure AD, SharePoint Online, and Skype for Buiness using multi-factor authentication in a single window using the Azure Active Directory PowerShell for Graph module.</span></span> <span data-ttu-id="f24f8-158">ユーザーアカウントのユーザープリンシパル名 (UPN) 名とドメインホスト名を指定し、それらを一度にすべて実行します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-158">Specify the user principal name (UPN) name of a user account and your domain host name, and then run them all at one time.</span></span>

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
```

<span data-ttu-id="f24f8-159">または、「Windows PowerShell 用 Microsoft Azure Active Directory モジュール」モジュールを使用する場合のすべてのコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-159">Alternately, here are all the commands when using the Microsoft Azure Active Directory Module for Windows PowerShell module.</span></span>

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
```

<span data-ttu-id="f24f8-160">Exchange Online およびセキュリティ&amp;コンプライアンスセンターでは、多要素認証を使用して接続するための次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f24f8-160">For Exchange Online and the Security &amp; Compliance Center, see the following topics to connect using multi-factor authentication:</span></span>

- [<span data-ttu-id="f24f8-161">多要素認証を使用して Exchange Online PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="f24f8-161">Connect to Exchange Online PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell)
- [<span data-ttu-id="f24f8-162">多要素認証を使用して Office 365 セキュリティ & コンプライアンスセンターの PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="f24f8-162">Connect to Office 365 Security & Compliance Center PowerShell using multi-factor authentication</span></span>](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)
 
<span data-ttu-id="f24f8-163">どちらの場合も、Exchange Online リモート PowerShell モジュールの個別のセッションを使用して接続する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f24f8-163">Note that in both cases, you must connect using separate sessions of the Exchange Online Remote PowerShell Module.</span></span>


## <a name="see-also"></a><span data-ttu-id="f24f8-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="f24f8-164">See also</span></span>

- [<span data-ttu-id="f24f8-165">Office 365 PowerShell への接続</span><span class="sxs-lookup"><span data-stu-id="f24f8-165">Connect to Office 365 PowerShell</span></span>](connect-to-office-365-powershell.md)
- [<span data-ttu-id="f24f8-166">Office 365 PowerShell を使用して SharePoint Online を管理する</span><span class="sxs-lookup"><span data-stu-id="f24f8-166">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
- [<span data-ttu-id="f24f8-167">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="f24f8-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="f24f8-168">Windows PowerShell を使用して Office 365 でレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="f24f8-168">Use Windows PowerShell to create reports in Office 365</span></span>](use-windows-powershell-to-create-reports-in-office-365.md)
