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
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="c2a72-103">Office 365 PowerShell への接続</span><span class="sxs-lookup"><span data-stu-id="c2a72-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="c2a72-104">**の概要:** コマンドラインから管理タスクを実行するのには Office 365 の PowerShell を使用して、Office 365 の組織に接続します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="c2a72-p101">Office 365 PowerShell を使用して、コマンド ラインから Office 365 設定を管理します。Office 365 PowerShell への接続は、必要なソフトウェアのインストール、必要なソフトウェアの実行、Office 365 組織への接続という、シンプルな 3 段階のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

  
> [!TIP]
> <span data-ttu-id="c2a72-p102">**PowerShell を初めて使用されますか。**[PowerShell の概要に関するビデオ](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)を視聴し、LinkedIn Learning にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p102">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="c2a72-109">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="c2a72-109">What do you need to know before you begin?</span></span>

- <span data-ttu-id="c2a72-110">予想所要時間 : 5 分</span><span class="sxs-lookup"><span data-stu-id="c2a72-110">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="c2a72-111">次の Windows のバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2a72-111">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="c2a72-112">Windows 10、Windows 8.1、Windows 8 または Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="c2a72-112">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="c2a72-113">Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、または Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="c2a72-113">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="c2a72-p103">64 ビット バージョンの Windows を使用してください。Microsoft PowerShell の Microsoft Azure Active Directory モジュールの 32 ビット バージョンのサポートは 2014 年 10 月に終了しました。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="c2a72-p104">これらの手順は、Office 365 の管理者ロールのメンバーであるユーザーを意図しています。詳細については、 [Office 365 の管理者の役割](https://go.microsoft.com/fwlink/p/?LinkId=532367)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p104">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c2a72-118">Microsoft PowerShell の Microsoft Azure Active Directory モジュールとの接続</span><span class="sxs-lookup"><span data-stu-id="c2a72-118">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c2a72-119">Microsoft PowerShell の Microsoft Azure Active Directory モジュールには、コマンドレット名に **Msol** が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c2a72-119">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="c2a72-120">手順 1: 必要なソフトウェアをインストールします</span><span class="sxs-lookup"><span data-stu-id="c2a72-120">Step 1: Install required software</span></span>

<span data-ttu-id="c2a72-p105">これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="c2a72-123">Microsoft Online Services サインイン アシスタントの 64 ビット バージョンをインストールします: [IT プロフェッショナル用 Microsoft Online Services サインイン アシスタント RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="c2a72-123">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="c2a72-124">以下の手順に従って、Windows PowerShell の Microsoft Azure Active Directory モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c2a72-124">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="c2a72-125">管理者レベルの PowerShell コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="c2a72-125">Open an administrator-level PowerShell command prompt.</span></span>
  - <span data-ttu-id="c2a72-126">**Install-Module MSOnline** コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-126">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="c2a72-127">NuGet プロバイダーをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-127">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="c2a72-128">PSGallery からモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-128">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="c2a72-129">インストール後、PowerShell コマンド ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c2a72-129">After installation, close the PowerShell command window.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="c2a72-130">手順 2: Office 365 サブスクリプションの Azure AD に接続します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-130">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="c2a72-131">*アカウント名とパスワード* のみを使用して接続する場合:</span><span class="sxs-lookup"><span data-stu-id="c2a72-131">To connect with just an *account name and password*:</span></span>
  
1. <span data-ttu-id="c2a72-132">Windows PowerShell コマンド プロンプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-132">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="c2a72-133">**Windows PowerShell** コマンド ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-133">In the **Windows PowerShell** command window, run the following commands:</span></span>
    
```
$UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
```

3. <span data-ttu-id="c2a72-134">**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2a72-134">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="c2a72-135">*多要素認証 (MFA)* を使用して接続する場合:</span><span class="sxs-lookup"><span data-stu-id="c2a72-135">To connect with *multi-factor authentication (MFA)*:</span></span>
  
1. <span data-ttu-id="c2a72-136">Windows PowerShell コマンド プロンプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-136">Run a Windows PowerShell command prompt.</span></span>
2. <span data-ttu-id="c2a72-137">**Microsoft PowerShell の Microsoft Azure Active Directory モジュール** コマンド ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-137">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
```
Connect-MsolService
```

3. <span data-ttu-id="c2a72-138">**[Azure Active Directory PowerShell]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2a72-138">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
4. <span data-ttu-id="c2a72-139">**[Azure Active Directory PowerShell]** ダイアログ ボックスの手順に従って、検証コードなどの他の認証情報を提供してから、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2a72-139">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="c2a72-140">正常な動作を確認する方法</span><span class="sxs-lookup"><span data-stu-id="c2a72-140">How do you know this worked?</span></span>

<span data-ttu-id="c2a72-p106">何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Office 365 コマンドレット ( **Get-MsolUser** など) を実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p106">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="c2a72-143">エラーが表示された場合は、次の要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-143">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="c2a72-p107">**よくある原因は、正しくないパスワードです** 。手順 3 をもう一度実行して、ユーザー名とパスワードの入力に注意します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p107">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="c2a72-p108">* *、Microsoft Azure Active ディレクトリ モジュールを Windows PowerShell には、Microsoft.NET Framework 3.5* 。上のコンピューター * * x * 機能を有効にします。お使いのコンピューターがインストールされている新しいバージョンを持っている可能性があります (たとえば、4 または 4.5* 。x *)、.NET Framework の以前のバージョンとの互換性を有効または無効になっている下位ですが。詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p108">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="c2a72-149">Windows Server 2012 または Windows Server 2012 R2 の場合、「[役割と機能の追加ウィザードを使用して .NET Framework 3.5 を有効にする](https://go.microsoft.com/fwlink/p/?LinkId=532368)」をご覧ください</span><span class="sxs-lookup"><span data-stu-id="c2a72-149">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="c2a72-150">Windows 8 または Windows 8.1 の場合、「[Windows 8 または Windows 8.1 への .NET Framework 3.5 のインストール](https://go.microsoft.com/fwlink/p/?LinkId=532369)」をご覧ください</span><span class="sxs-lookup"><span data-stu-id="c2a72-150">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="c2a72-151">Windows 7 または Windows Server 2008 R2 の場合、「[Windows PowerShell 用 Azure Active Directory モジュールを開くことができない](https://go.microsoft.com/fwlink/p/?LinkId=532370)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="c2a72-151">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="c2a72-p109">**お使いの Microsoft PowerShell の Microsoft Azure Active Directory モジュール のバージョンは期限切れの可能性があります。** Office 365 PowerShell または Microsoft PowerShell の Microsoft Azure Active Directory モジュール で、次のコマンドを実行して確認します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p109">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="c2a72-154">返されたバージョン番号が 1.0.8070.2 の値より小さい場合は、Microsoft PowerShell の Microsoft Azure Active Directory モジュール をアンインストールして、手順 1 のリンクから最新バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="c2a72-154">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="c2a72-155">**接続エラーが発生した場合、次のトピックをご覧ください: **["Connect-MsolService:型の例外がスローされました" というエラー](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="c2a72-155">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
<span data-ttu-id="c2a72-156"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="c2a72-156"></span></span>
## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c2a72-157">グラフ モジュールの Azure Active Directory PowerShell を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-157">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c2a72-158">[グラフ モジュールのアクティブなディレクトリの PowerShell を Azure](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)のモジュール内のコマンドでは、コマンドレット名に**AzureAD**があります。</span><span class="sxs-lookup"><span data-stu-id="c2a72-158">Commands in the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="c2a72-159">グラフ モジュール用の新しい Azure Active Directory の PowerShell コマンドレットを必要とする手順は、モジュールをインストールし、Office 365 サブスクリプションに接続する手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-159">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="c2a72-160">異なるバージョンの Microsoft Windows のサポートについては、[グラフのモジュールのアクティブなディレクトリの PowerShell を Azure](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2a72-160">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="c2a72-161">手順 1: 必要なソフトウェアをインストールします</span><span class="sxs-lookup"><span data-stu-id="c2a72-161">Step 1: Install required software</span></span>

<span data-ttu-id="c2a72-p110">これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2a72-p110">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>

  
1. <span data-ttu-id="c2a72-164">管理者特権で Windows PowerShell コマンド プロンプトを開きます (Windows PowerShell を管理者として実行)。</span><span class="sxs-lookup"><span data-stu-id="c2a72-164">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="c2a72-165">[ **Administrator:Windows PowerShell**] コマンド ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-165">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="c2a72-166">信頼されていないリポジトリからモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-166">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>


### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="c2a72-167">手順 2: Office 365 サブスクリプションの Azure AD に接続します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-167">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="c2a72-168">*アカウント名とパスワード*を使用して Office 365 サブスクリプションに接続するには、以下の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-168">To connect to your Office 365 subscription with an *account name and password*:</span></span>
    
```
$UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
```

<span data-ttu-id="c2a72-169">**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2a72-169">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="c2a72-170">*多要素認証 (MFA)* を使用して Office 365 サブスクリプションに接続するには、以下の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="c2a72-170">To connect to your Office 365 subscription with *multi-factor authentication (MFA)*:</span></span>

```
Connect-AzureAD
```

<span data-ttu-id="c2a72-171">**[Azure Active Directory PowerShell]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2a72-171">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="c2a72-172">**[Azure Active Directory PowerShell]** ダイアログ ボックスの手順に従って、検証コードなどの他の認証情報を提供してから、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2a72-172">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="c2a72-173">接続した後、[グラフのモジュールのアクティブなディレクトリの PowerShell を Azure](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)の新しいコマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2a72-173">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c2a72-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2a72-174">See also</span></span>

- [<span data-ttu-id="c2a72-175">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="c2a72-175">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="c2a72-176">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="c2a72-176">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="c2a72-177">単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="c2a72-177">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="c2a72-178">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="c2a72-178">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="c2a72-179">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="c2a72-179">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

