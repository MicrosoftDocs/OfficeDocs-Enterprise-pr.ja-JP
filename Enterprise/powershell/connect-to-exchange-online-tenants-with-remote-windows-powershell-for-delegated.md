---
title: 委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ae5f1a87-8b77-4f93-a1b8-56f800aeb283
description: '概要: リモート Windows PowerShell で DelegatedOrg 値を使用して、Exchange Online に接続します。'
ms.openlocfilehash: 4a9f08325fc56308b27467423b047375985562c5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997373"
---
# <a name="connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="fa8cf-103">委任アクセス許可 (DAP) パートナー用リモート Windows PowerShell で Exchange Online テナントに接続する</span><span class="sxs-lookup"><span data-stu-id="fa8cf-103">Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa8cf-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-104">The procedures in this topic are only for Delegated Access Permission (DAP) partners.</span></span> <span data-ttu-id="fa8cf-105">If you aren't a DAP partner, don't use the procedures in this topic.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-105">If you aren't a DAP partner, don't use the procedures in this topic.</span></span> 
  
<span data-ttu-id="fa8cf-106">DAP パートナーとは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-106">DAP partners are Syndication and Cloud Solution Providers (CSP) partners.</span></span> <span data-ttu-id="fa8cf-107">他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="fa8cf-108">それらのパートナーは、顧客に提供するサービスにサブスクリプションをバンドルします。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-108">They bundle subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="fa8cf-109">お客様は、Microsoft 365 カスタマーテナンシーに対して (AOBO) アクセス許可を自動的に付与されたパートナーテナントを所有しており、すべての顧客テナンシーの管理とレポートを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-109">They own a partner tenancy that is automatically granted Administer On Behalf Of (AOBO) permissions to their Microsoft 365 customer tenancies so they can administer and report on all of their customer tenancies.</span></span>

<span data-ttu-id="fa8cf-110">DAP パートナーは、Exchange Online PowerShell を使用して、ユーザーの Exchange Online の設定を管理したり、Microsoft 365 レポートをコマンドラインから取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-110">DAP partners can use Exchange Online PowerShell to manage customer Exchange Online settings and get Microsoft 365 reports from the command line.</span></span> <span data-ttu-id="fa8cf-111">ローカル コンピューター上で Windows PowerShell を使用して Exchange Online に対するリモート PowerShell セッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-111">You use Windows PowerShell on your local computer to create a remote PowerShell session to Exchange Online.</span></span> <span data-ttu-id="fa8cf-112">これは、資格情報を入力し、必要な接続設定を指定してから、Exchange Online コマンドレットをローカルの Windows PowerShell セッションにインポートして使用できるようにする、簡単な3段階のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-112">It's a simple three-step process where you enter your credentials, provide the required connection settings, and then import the Exchange Online cmdlets into your local Windows PowerShell session so that you can use them.</span></span>

> [!NOTE]
> <span data-ttu-id="fa8cf-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-113">DAP partners can't use the procedures in [Connect to Exchange Online PowerShell using multi-factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell) to connect to their customer tenant organizations in Exchange Online PowerShell.</span></span> <span data-ttu-id="fa8cf-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-114">MFA and the Exchange Online Remote PowerShell Module don't work with delegated authentication.</span></span>
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="fa8cf-115">はじめに把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="fa8cf-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="fa8cf-116">予想所要時間 : 5 分</span><span class="sxs-lookup"><span data-stu-id="fa8cf-116">Estimated time to complete: 5 minutes</span></span>

- <span data-ttu-id="fa8cf-117">次の Windows のバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="fa8cf-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="fa8cf-118">Windows 10</span></span>

  - <span data-ttu-id="fa8cf-119">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="fa8cf-119">Windows 8.1</span></span>

  - <span data-ttu-id="fa8cf-120">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="fa8cf-120">Windows Server 2016</span></span>

  - <span data-ttu-id="fa8cf-121">Windows Server 2012 または Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fa8cf-121">Windows Server 2012 or Windows Server 2012 R2</span></span>

  - <span data-ttu-id="fa8cf-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="fa8cf-122">Windows 7 Service Pack 1 (SP1)<sup>\*</sup></span></span>

  - <span data-ttu-id="fa8cf-123">Windows Server 2008 R2 SP1<sup>\*</sup></span><span class="sxs-lookup"><span data-stu-id="fa8cf-123">Windows Server 2008 R2 SP1<sup>\*</sup></span></span>

    <span data-ttu-id="fa8cf-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span><span class="sxs-lookup"><span data-stu-id="fa8cf-124"><sup>\*</sup> For older versions of Windows, you need to install the Microsoft.NET Framework 4.5 or later and then an updated version of the Windows Management Framework: 3.0, 4.0, or 5.1 (only one).</span></span> <span data-ttu-id="fa8cf-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span><span class="sxs-lookup"><span data-stu-id="fa8cf-125">For more information, see [Installing the .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=257868), [Windows Management Framework 3.0](https://go.microsoft.com/fwlink/p/?LinkId=272757), [Windows Management Framework 4.0](https://go.microsoft.com/fwlink/p/?LinkId=391344), and [Windows Management Framework 5.1](https://aka.ms/wmf5download).</span></span>

- <span data-ttu-id="fa8cf-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-126">Windows PowerShell needs to be configured to run scripts, and by default, it isn't.</span></span> <span data-ttu-id="fa8cf-127">You'll get the following error when you try to connect:</span><span class="sxs-lookup"><span data-stu-id="fa8cf-127">You'll get the following error when you try to connect:</span></span>

  `Files cannot be loaded because running scripts is disabled on this system. Provide a valid certificate with which to sign the files.`

  <span data-ttu-id="fa8cf-128">インターネットからダウンロードしたすべての PowerShell スクリプトが信頼された発行元によって署名されていることを要求するには、管理者特権の Windows PowerShell ウィンドウ (**[管理者として実行]** を選択したときに開く Windows PowerShell ウィンドウ) で次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-128">To require all PowerShell scripts that you download from the internet are signed by a trusted publisher, run the following command in an elevated Windows PowerShell window (a Windows PowerShell window you open by selecting **Run as administrator**):</span></span>

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

  <span data-ttu-id="fa8cf-129">この設定は、コンピューターで一度だけ構成すれば、接続ごとに行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-129">You need to configure this setting only once on your computer, not every time you connect.</span></span>

- <span data-ttu-id="fa8cf-130">このトピックの手順に適用されるキーボード ショートカットについては、「[Exchange 管理センターのキーボード ショートカット](https://go.microsoft.com/fwlink/p/?LinkId=534017)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-130">For information about keyboard shortcuts that might apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](https://go.microsoft.com/fwlink/p/?LinkId=534017).</span></span>

## <a name="connect-to-exchange-online-for-customer-organizations"></a><span data-ttu-id="fa8cf-131">顧客の組織の Exchange Online に接続する</span><span class="sxs-lookup"><span data-stu-id="fa8cf-131">Connect to Exchange Online for customer organizations</span></span>

1. <span data-ttu-id="fa8cf-132">ローカル コンピューターで、Windows PowerShell を開き、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-132">On your local computer, open Windows PowerShell and run the following command.</span></span>
    
    ```
    $UserCredential = Get-Credential
    ```

    <span data-ttu-id="fa8cf-133">**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、DAP 管理者のユーザー名とパスワードを入力してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-133">In the **Windows PowerShell Credential Request** dialog box, enter your DAP administrator user name and password, and then click **OK**.</span></span>
    
2. <span data-ttu-id="fa8cf-134">_\<customer tenant domain name\>_ を接続先のテナントドメインの名前に置き換えて、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-134">Replace _\<customer tenant domain name\>_ with the name of the tenant domain that you want to connect to, and run the following command:</span></span>
    
    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid?DelegatedOrg=<customer tenant domain name> -Credential $UserCredential -Authentication Basic -AllowRedirection
    ```

    <span data-ttu-id="fa8cf-135">このコマンドの重要な手順は、レポート情報にアクセスする顧客を指定することです。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-135">The key step in this command is specifying which customer to access for the reporting information.</span></span> <span data-ttu-id="fa8cf-136">この操作は、 _Connectionuri_パラメーターで行います。この場合、最初のドメイン名の FQDN をの値として指定し `?DelegatedOrg=` ます。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-136">You do this in the  _ConnectionURI_ parameter, where you provide the FQDN of the initial domain name as the value for `?DelegatedOrg=`.</span></span> <span data-ttu-id="fa8cf-137">この値は、接続先の正しい Exchange Online PowerShell エンドポイントを示します。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-137">This value indicates the correct Exchange Online PowerShell endpoint to connect to.</span></span> <span data-ttu-id="fa8cf-138">リモート PowerShell は、レポートが実行されるたびに、特定の顧客のコンテキストで、Microsoft 365 reporting に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-138">Remote PowerShell must connect to Microsoft 365 reporting in the context of a specific customer each time a report is run.</span></span> <span data-ttu-id="fa8cf-139">Exchange Online の PowerShell に接続すると、これ以降のすべてのコマンドが顧客のコンテキストで実行されます。これにより、お客様に対して利用可能なすべてのレポートにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-139">After you connect to Exchange Online PowerShell, all subsequent commands are run in the context of the customer, which gives you access to all of the available reports for the customer.</span></span>
    
3. <span data-ttu-id="fa8cf-140">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-140">Run the following command.</span></span>
    
    ```
    Import-PSSession $Session
    ```

> [!NOTE]
> <span data-ttu-id="fa8cf-141">There's a limit of three simultaneous sessions that can run under one account.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-141">There's a limit of three simultaneous sessions that can run under one account.</span></span> <span data-ttu-id="fa8cf-142">Be sure to disconnect the remote PowerShell session when you're finished.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-142">Be sure to disconnect the remote PowerShell session when you're finished.</span></span> <span data-ttu-id="fa8cf-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-143">If you close the Windows PowerShell window without disconnecting the session, you can use up all the remote PowerShell sessions available to you, and you'll need to wait for the sessions to expire.</span></span> <span data-ttu-id="fa8cf-144">To disconnect the remote PowerShell session, run the following command:</span><span class="sxs-lookup"><span data-stu-id="fa8cf-144">To disconnect the remote PowerShell session, run the following command:</span></span>

```
Remove-PSSession $Session
```
  
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="fa8cf-145">正常な動作を確認する方法</span><span class="sxs-lookup"><span data-stu-id="fa8cf-145">How do you know this worked?</span></span>

<span data-ttu-id="fa8cf-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-146">After Step 3, the Exchange Online cmdlets are imported into your local Windows PowerShell session as tracked by a progress bar.</span></span> <span data-ttu-id="fa8cf-147">If you don't receive any errors, you connected successfully.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-147">If you don't receive any errors, you connected successfully.</span></span> <span data-ttu-id="fa8cf-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-148">A quick test is to run an Exchange Online cmdlet (for example, **Get-Mailbox**) and see the results.</span></span>
  
<span data-ttu-id="fa8cf-149">エラーが表示された場合は、次の要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="fa8cf-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="fa8cf-150">A common problem is an incorrect password.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-150">A common problem is an incorrect password.</span></span> <span data-ttu-id="fa8cf-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-151">Run the three steps again and pay close attention to the user name and password you enter in Step 1.</span></span>
    
- <span data-ttu-id="fa8cf-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-152">The account you use to connect to Exchange Online must be enabled for remote PowerShell.</span></span> <span data-ttu-id="fa8cf-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span><span class="sxs-lookup"><span data-stu-id="fa8cf-153">For more information, see [Enable or disable access to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534018).</span></span>
    
- <span data-ttu-id="fa8cf-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-154">TCP port 80 traffic needs to be open between your local computer and Exchange Online.</span></span> <span data-ttu-id="fa8cf-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-155">It's probably open, but it's something to consider if your organization has a restrictive Internet access policy.</span></span>
    
## <a name="call-the-cmdlet-directly-with-invoke-command"></a><span data-ttu-id="fa8cf-156">Invoke-Command で直接コマンドレットを呼び出す</span><span class="sxs-lookup"><span data-stu-id="fa8cf-156">Call the cmdlet directly with Invoke-Command</span></span>

<span data-ttu-id="fa8cf-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-157">Importing a remote PowerShell session (Step 3) can be a lengthy process because it brings in _all_ Exchange Online cmdlets.</span></span> <span data-ttu-id="fa8cf-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span><span class="sxs-lookup"><span data-stu-id="fa8cf-158">This can be an issue in batch processing (for example, when you're running reports or making bulk changes for different tenants).</span></span> <span data-ttu-id="fa8cf-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-159">As an alternative to using **Import-PSSession**, you can call cmdlets you want to use directly with **Invoke-Command**.</span></span> <span data-ttu-id="fa8cf-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span><span class="sxs-lookup"><span data-stu-id="fa8cf-160">For example, to call the **Get-Milbox** cmdlet, substitute this syntax for the `Import-PSSession $Session` command in Step 3:</span></span>
  
```
Invoke-Command -Session $Session -ScriptBlock {Get-Mailbox}
```

## <a name="more-reporting-cmdlets"></a><span data-ttu-id="fa8cf-161">その他のレポート コマンドレット</span><span class="sxs-lookup"><span data-stu-id="fa8cf-161">More reporting cmdlets</span></span>

<span data-ttu-id="fa8cf-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fa8cf-162">The cmdlets that you used in this topic are Windows PowerShell cmdlets.</span></span> <span data-ttu-id="fa8cf-163">For more information about these cmdlets, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="fa8cf-163">For more information about these cmdlets, see the following topics:</span></span>
  
- [<span data-ttu-id="fa8cf-164">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="fa8cf-164">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
    
- [<span data-ttu-id="fa8cf-165">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa8cf-165">New-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389621)
    
- [<span data-ttu-id="fa8cf-166">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa8cf-166">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389619)
    
- [<span data-ttu-id="fa8cf-167">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="fa8cf-167">Remove-PSSession</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389620)
    
- [<span data-ttu-id="fa8cf-168">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="fa8cf-168">Set-ExecutionPolicy</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389623)
    

