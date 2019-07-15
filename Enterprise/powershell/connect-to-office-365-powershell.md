---
title: Office 365 PowerShell への接続
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: '概要: Office 365 PowerShell を使用して Office 365 組織に接続し、コマンド ラインから管理センター タスクを実行します。'
ms.openlocfilehash: aea7cb638cb866374af6b33d6d1848a7cb6d304c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069093"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="9444f-103">Office 365 PowerShell への接続</span><span class="sxs-lookup"><span data-stu-id="9444f-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="9444f-104">**概要:** Office 365 PowerShell を使用して Office 365 組織に接続し、コマンド ラインから管理タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="9444f-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="9444f-p101">Office 365 PowerShell を使用すると、コマンド ラインから Office 365 の設定を管理できます。Office 365 PowerShell への接続は、必要なソフトウェアをインストールしてから Office 365 組織に接続するというシンプルなプロセスです。</span><span class="sxs-lookup"><span data-stu-id="9444f-p101">Office 365 PowerShell lets you manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="9444f-107">Office 365 および管理者のユーザー アカウント、グループ、ライセンスへの接続に使用する PowerShell モジュールには、次の 2 つのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="9444f-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="9444f-108">Graph 用 Azure Active Directory PowerShell (コマンドレット名に **AzureAD** が含まれる)</span><span class="sxs-lookup"><span data-stu-id="9444f-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="9444f-109">Windows PowerShell 用 Microsoft Azure Active Directory モジュール (コマンドレット名に **MSol** が含まれる)</span><span class="sxs-lookup"><span data-stu-id="9444f-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="9444f-p102">この記事の日付の時点で、Graph 用 Azure Active Directory PowerShell モジュールは、ユーザー、グループ、およびライセンスの管理について Windows PowerShell 用 Microsoft Azure Active Directory モジュールのコマンドレットの機能に完全に置き換わるものではありません。多くの場合、両方のバージョンを使用する必要があります。同じコンピューターに両方のバージョンを安全にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="9444f-p102">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration. In many cases, you need to use both versions. You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="9444f-p103">**PowerShell を初めて使用されますか。** [PowerShell の概要に関するビデオ](https://support.office.com/ja-JP/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)を視聴し、LinkedIn ラーニングにアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="9444f-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="9444f-115">はじめに把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="9444f-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="9444f-116">予想所要時間 : 5 分</span><span class="sxs-lookup"><span data-stu-id="9444f-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="9444f-117">次の Windows のバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9444f-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="9444f-118">Windows 10、Windows 8.1、Windows 8、または Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="9444f-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="9444f-119">Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、または Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="9444f-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="9444f-p104">64 ビット バージョンの Windows を使用してください。Microsoft PowerShell の Microsoft Azure Active Directory モジュールの 32 ビット バージョンのサポートは 2014 年 10 月に終了しました。</span><span class="sxs-lookup"><span data-stu-id="9444f-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="9444f-p105">これらの手順は、Office 365 管理者の役割のメンバーであるユーザーを対象としています。詳細については、「[Office 365 の管理者ロールについて](https://go.microsoft.com/fwlink/p/?LinkId=532367)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9444f-p105">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="9444f-124">Graph 用 Azure Active Directory PowerShell モジュールに接続する</span><span class="sxs-lookup"><span data-stu-id="9444f-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="9444f-125">[Graph 用 Azure Active Directory PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) モジュールのコマンドには、コマンドレット名に **AzureAD** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9444f-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="9444f-126">Graph 用 Azure Active Directory PowerShell モジュールにおいて新しいコマンドレットを必要とするプロシージャについては、以下の手順を実行して、モジュールをインストールし、Office 365 サブスクリプションに接続します。</span><span class="sxs-lookup"><span data-stu-id="9444f-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="9444f-127">Microsoft Windows のさまざまなバージョンに対するサポート情報については、[Graph 用 Azure Active Directory PowerShell モジュール](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9444f-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="9444f-128">手順 1: 必要なソフトウェアをインストールする</span><span class="sxs-lookup"><span data-stu-id="9444f-128">Step 1: Install required software</span></span>

<span data-ttu-id="9444f-p106">これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9444f-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="9444f-131">管理者特権で Windows PowerShell コマンド プロンプトを開きます (Windows PowerShell を管理者として実行)。</span><span class="sxs-lookup"><span data-stu-id="9444f-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="9444f-132">[ **Administrator:Windows PowerShell**] コマンド ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9444f-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="9444f-133">信頼されていないリポジトリからモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、Enter を押します。</span><span class="sxs-lookup"><span data-stu-id="9444f-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="9444f-134">手順 2: Office 365 サブスクリプション用の Azure AD に接続する</span><span class="sxs-lookup"><span data-stu-id="9444f-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="9444f-135">アカウント名とパスワードまたは*多要素認証 (MFA)* を使用して Office 365 サブスクリプション用の Azure AD に接続するには、Windows PowerShell コマンド プロンプトから次のいずれかのコマンドを実行します (昇格する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="9444f-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="9444f-136">**Office 365 のクラウド**</span><span class="sxs-lookup"><span data-stu-id="9444f-136">**Office 365 cloud**</span></span> | <span data-ttu-id="9444f-137">**コマンド**</span><span class="sxs-lookup"><span data-stu-id="9444f-137">**Command**</span></span> |
| <span data-ttu-id="9444f-138">Office 365 ワールドワイド (+GCC)</span><span class="sxs-lookup"><span data-stu-id="9444f-138">Office 365 Worldwide (+GCC)</span></span> | `Connect-AzureAD` |
| <span data-ttu-id="9444f-139">21 Vianet が運営する Office 365</span><span class="sxs-lookup"><span data-stu-id="9444f-139">Office 365 operated by 21 Vianet</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| <span data-ttu-id="9444f-140">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="9444f-140">Office 365 Germany</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| <span data-ttu-id="9444f-141">Office 365 U.S. Government DoD と Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="9444f-141">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

<span data-ttu-id="9444f-142">[**アカウントにサインイン**] ダイアログ ボックスで、Office 365 の職場または学校のアカウントのユーザー名とパスワードを入力し、[**OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9444f-142">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="9444f-143">MFA を使用している場合は、追加のダイアログ ボックスの手順に従って、確認コードなどのその他の認証情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="9444f-143">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>


<span data-ttu-id="9444f-144">接続後は、[Graph 用 Azure Active Directory PowerShell モジュール](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)の新しいコマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9444f-144">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="9444f-145">Microsoft PowerShell の Microsoft Azure Active Directory モジュールとの接続</span><span class="sxs-lookup"><span data-stu-id="9444f-145">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="9444f-146">Microsoft PowerShell の Microsoft Azure Active Directory モジュールには、コマンドレット名に **Msol** が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9444f-146">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="9444f-147">手順 1: 必要なソフトウェアをインストールします</span><span class="sxs-lookup"><span data-stu-id="9444f-147">Step 1: Install required software</span></span>

<span data-ttu-id="9444f-p107">これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9444f-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="9444f-150">Microsoft Online Services サインイン アシスタントの 64 ビット バージョンをインストールします: [IT プロフェッショナル用 Microsoft Online Services サインイン アシスタント RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="9444f-150">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="9444f-151">以下の手順に従って、Windows PowerShell の Microsoft Azure Active Directory モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="9444f-151">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="9444f-152">管理者特権で Windows PowerShell コマンド プロンプトを開きます (Windows PowerShell を管理者として実行)。</span><span class="sxs-lookup"><span data-stu-id="9444f-152">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="9444f-153">**Install-Module MSOnline** コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="9444f-153">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="9444f-154">NuGet プロバイダーをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。</span><span class="sxs-lookup"><span data-stu-id="9444f-154">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="9444f-155">PSGallery からモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、Enter を押します。</span><span class="sxs-lookup"><span data-stu-id="9444f-155">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="9444f-156">手順 2: Office 365 サブスクリプション用の Azure AD に接続する</span><span class="sxs-lookup"><span data-stu-id="9444f-156">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="9444f-157">アカウント名とパスワードまたは*多要素認証 (MFA)* を使用して Office 365 サブスクリプション用の Azure AD に接続するには、Windows PowerShell コマンド プロンプトから次のいずれかのコマンドを実行します (昇格する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="9444f-157">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run one of these commands from a Windows PowerShell command prompt (it does not have to be elevated).</span></span>

|||
|:-------|:-----|
| <span data-ttu-id="9444f-158">**Office 365 のクラウド**</span><span class="sxs-lookup"><span data-stu-id="9444f-158">**Office 365 cloud**</span></span> | <span data-ttu-id="9444f-159">**コマンド**</span><span class="sxs-lookup"><span data-stu-id="9444f-159">**Command**</span></span> |
| <span data-ttu-id="9444f-160">Office 365 ワールドワイド (+GCC)</span><span class="sxs-lookup"><span data-stu-id="9444f-160">Office 365 Worldwide (+GCC)</span></span> | `Connect-MsolService` |
| <span data-ttu-id="9444f-161">21 Vianet が運営する Office 365</span><span class="sxs-lookup"><span data-stu-id="9444f-161">Office 365 operated by 21 Vianet</span></span> | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| <span data-ttu-id="9444f-162">Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="9444f-162">Office 365 Germany</span></span> | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| <span data-ttu-id="9444f-163">Office 365 U.S. Government DoD と Office 365 U.S. Government GCC High</span><span class="sxs-lookup"><span data-stu-id="9444f-163">Office 365 U.S. Government DoD and Office 365 U.S. Government GCC High</span></span> | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

<span data-ttu-id="9444f-164">[**アカウントにサインイン**] ダイアログ ボックスで、Office 365 の職場または学校のアカウントのユーザー名とパスワードを入力し、[**OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9444f-164">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="9444f-165">MFA を使用している場合は、追加のダイアログ ボックスの手順に従って、確認コードなどのその他の認証情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="9444f-165">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="9444f-166">正常な動作を確認する方法</span><span class="sxs-lookup"><span data-stu-id="9444f-166">How do you know this worked?</span></span>

<span data-ttu-id="9444f-p108">何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Office 365 コマンドレット ( **Get-MsolUser** など) を実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="9444f-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="9444f-169">エラーが表示された場合は、次の要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="9444f-169">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="9444f-p109">**よくある原因は、正しくないパスワードです**。手順 2 をもう一度実行して、ユーザー名とパスワードの入力に注意します。</span><span class="sxs-lookup"><span data-stu-id="9444f-p109">**A common problem is an incorrect password**. Run Step 2 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="9444f-p110">**Windows PowerShell 用 Microsoft Azure Active Directory モジュールでは、Microsoft .NET Framework 3.5.* x* 機能がお使いのコンピューターで有効になっている必要があります。お使いのコンピューターに、より新しいバージョン (たとえば、4 または 4.5.\* x\*) がインストールされている場合でも、.NET Framework の古いバージョンとの下位互換性を有効または無効にすることができます。詳細については、以下のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9444f-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="9444f-175">Windows Server 2012 または Windows Server 2012 R2 の場合は、「[役割と機能の追加ウィザードを使用して .NET Framework 3.5 を有効にする](https://go.microsoft.com/fwlink/p/?LinkId=532368)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="9444f-175">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="9444f-176">Windows 7 または Windows Server 2008 R2 の場合は、「[Windows PowerShell 用 Azure Active Directory モジュールを開くことができない](https://go.microsoft.com/fwlink/p/?LinkId=532370)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="9444f-176">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="9444f-177">Windows 10、Windows 8.1、および Windows 8 の場合は、「[Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール](https://docs.microsoft.com/ja-JP/dotnet/framework/install/dotnet-35-windows-10)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="9444f-177">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="9444f-p111">**お使いの Microsoft PowerShell の Microsoft Azure Active Directory モジュール のバージョンは期限切れの可能性があります。** Office 365 PowerShell または Microsoft PowerShell の Microsoft Azure Active Directory モジュール で、次のコマンドを実行して確認します。</span><span class="sxs-lookup"><span data-stu-id="9444f-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="9444f-180">返されたバージョン番号が 1.0.8070.2 の値より小さい場合は、Microsoft PowerShell の Microsoft Azure Active Directory モジュール をアンインストールして、手順 1 のリンクから最新バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="9444f-180">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="9444f-181">**接続エラーが発生した場合は、**["Connect-MsolService: 例外がスローされました" というエラー](https://go.microsoft.com/fwlink/p/?LinkId=532377)に関するトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9444f-181">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="9444f-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="9444f-182">See also</span></span>

- [<span data-ttu-id="9444f-183">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="9444f-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="9444f-184">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="9444f-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="9444f-185">単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="9444f-185">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="9444f-186">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="9444f-186">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="9444f-187">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="9444f-187">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

