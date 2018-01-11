---
title: "Office 365 PowerShell への接続"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: "概要: Office 365 PowerShell を使用して Office 365 組織に接続し、コマンド ラインから Office 365 管理センター タスクを実行します。"
ms.openlocfilehash: 942c128d8cfbcf4e78f054a0ab3a51b05173073f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="f5dad-103">Office 365 PowerShell への接続</span><span class="sxs-lookup"><span data-stu-id="f5dad-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="f5dad-104">**概要:** Office 365 PowerShell を使用して Office 365 組織に接続し、コマンド ラインから Office 365 管理タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform Office 365 administration tasks from the command line.</span></span>
  
<span data-ttu-id="f5dad-p101">Office 365 PowerShell を使用して、コマンド ラインから Office 365 設定を管理します。Office 365 PowerShell への接続は、必要なソフトウェアのインストール、必要なソフトウェアの実行、Office 365 組織への接続という、シンプルな 3 段階のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple three-step process where you install the required software, run the required software, and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="f5dad-107">なお、これらの接続手順は、「[Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113)」というトピックで説明されているのと同じ手順です。</span><span class="sxs-lookup"><span data-stu-id="f5dad-107">Note that these connection instructions are the same as those in the topic [Azure ActiveDirectory (MSOnline)](https://go.microsoft.com/fwlink/p/?LinkId=528113).</span></span>
  
> [!TIP]
> <span data-ttu-id="f5dad-p102">**PowerShell を初めて使用されますか。**[PowerShell の概要に関するビデオ](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)を視聴し、LinkedIn Learning にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p102">**New to PowerShell?** See a [video Overview of PowerShell](http://technet.microsoft.com/library/https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="f5dad-110">はじめに把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="f5dad-110">What do you need to know before you begin?</span></span>

- <span data-ttu-id="f5dad-111">予想所要時間 : 5 分</span><span class="sxs-lookup"><span data-stu-id="f5dad-111">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="f5dad-112">次の Windows のバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5dad-112">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="f5dad-113">Windows 10、Windows 8.1、Windows 8 または Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="f5dad-113">Windows 10, Windows 8.1, Windows 8 or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="f5dad-114">Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、または Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="f5dad-114">Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="f5dad-p103">64 ビット バージョンの Windows を使用してください。Microsoft PowerShell の Microsoft Azure Active Directory モジュールの 32 ビット バージョンのサポートは 2014 年 10 月に終了しました。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p103">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="f5dad-p104">これらの手順に使用する Office 365 職場または学校のアカウントは、Office 365 管理者役割のメンバーである必要があります。詳細については、「[Office 365 の管理者の役割](https://go.microsoft.com/fwlink/p/?LinkId=532367)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p104">The Office 365 work or school account that you use for these procedures needs to be a member of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>
    
## <a name="step-1-install-required-software"></a><span data-ttu-id="f5dad-119">手順 1:必要なソフトウェアをインストールします</span><span class="sxs-lookup"><span data-stu-id="f5dad-119">Step 1: Install required software</span></span>

<span data-ttu-id="f5dad-p105">これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p105">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="f5dad-122">Microsoft Online Services サインイン アシスタントの 64 ビット バージョンをインストールします: [IT プロフェッショナル用 Microsoft Online Services サインイン アシスタント RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="f5dad-122">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="f5dad-123">以下の手順に従って、Microsoft PowerShell の Microsoft Azure Active Directory モジュール の 64 ビット バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-123">Install the 64-bit version of the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="f5dad-124">[Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) の Web ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="f5dad-124">Open the [Azure Active Directory Connection](http://connect.microsoft.com/site1164/Downloads/DownloadDetails.aspx?DownloadID=59185) web page.</span></span>
    
  - <span data-ttu-id="f5dad-125">ページの下部にある **[ダウンロードしたファイル]** で、 **AdministrationConfig-V1.1.166.0-GA.msi** ファイルの **[ダウンロード]** をクリックしてから、インストールします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-125">In **Files in Download** at the bottom of the page, click **Download** for the **AdministrationConfig-V1.1.166.0-GA.msi** file, and then install it.</span></span>
    
## <a name="step-2-open-the-windows-azure-active-directory-module"></a><span data-ttu-id="f5dad-126">手順 2: Windows Azure Active Directory モジュールを開く</span><span class="sxs-lookup"><span data-stu-id="f5dad-126">Step 2: Open the Windows Azure Active Directory Module</span></span>

1. <span data-ttu-id="f5dad-127">お使いの Windows のバージョンに応じて、次のいずれかの方法を使用して Microsoft PowerShell の Microsoft Azure Active Directory モジュール を検索して開きます。</span><span class="sxs-lookup"><span data-stu-id="f5dad-127">Find and open the Microsoft Azure Active Directory Module for Windows PowerShell by using one of the following methods based on your version of Windows:</span></span>
    
  - <span data-ttu-id="f5dad-128">**[スタート] メニューがある場合** デスクトップから **[スタート]** をクリックして、「Azure」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-128">**Start menu** From the desktop, click **Start**, and then type Azure.</span></span>
    
  - <span data-ttu-id="f5dad-129">**[スタート] メニューがない場合** 次の方法のいずれかを使用して、Azure を検索します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-129">**No Start menu** Search forAzure using any of these methods:</span></span>
    
  - <span data-ttu-id="f5dad-130">[スタート] 画面で空の領域をクリックして、「Azure」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-130">On the Start screen, click an empty area, and type Azure.</span></span>
    
  - <span data-ttu-id="f5dad-p106">デスクトップまたは [スタート] 画面で、Windows キー + Q キーを押します。[検索] チャームで、「Azure」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p106">On the desktop or the Start screen, press the Windows key+Q. In the Search charm, type Azure.</span></span>
    
  - <span data-ttu-id="f5dad-p107">デスクトップまたはスタート画面で、右上隅にカーソルを移動するか、または画面の右端から左にスワイプして、チャームを表示します。[検索] チャームを選択して、「**Azure**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p107">On the desktop or the Start screen, move your cursor to the upper-right corner, or swipe left from the right edge of the screen to show the charms. Select the Search charm, and type **Azure**.</span></span>
    
2. <span data-ttu-id="f5dad-135">結果から、 **Microsoft PowerShell の Microsoft Azure Active Directory モジュール** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-135">In the results, click **Microsoft Azure Active Directory Module for Windows PowerShell**.</span></span>
    
## <a name="step-3-connect-to-your-office-365-subscription"></a><span data-ttu-id="f5dad-136">手順 3:Office 365 サブスクリプションに接続する</span><span class="sxs-lookup"><span data-stu-id="f5dad-136">Step 3: Connect to your Office 365 subscription</span></span>
<span data-ttu-id="f5dad-137"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="f5dad-137"><a name="step3"> </a></span></span>

<span data-ttu-id="f5dad-138">*アカウント名とパスワード*  のみを使用して接続する場合:</span><span class="sxs-lookup"><span data-stu-id="f5dad-138">To connect with just an  *account name and password*  :</span></span>
  
1. <span data-ttu-id="f5dad-139">**Microsoft PowerShell の Microsoft Azure Active Directory モジュール** コマンド ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-139">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following commands.</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-MsolService -Credential $UserCredential
  ```

2. <span data-ttu-id="f5dad-140">**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-140">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
<span data-ttu-id="f5dad-141">*多要素認証 (MFA)*  を使用して接続する場合:</span><span class="sxs-lookup"><span data-stu-id="f5dad-141">To connect with  *multi-factor authentication (MFA)*  :</span></span>
  
1. <span data-ttu-id="f5dad-142">**Microsoft PowerShell の Microsoft Azure Active Directory モジュール** コマンド ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-142">In the **Microsoft Azure Active Directory Module for Windows PowerShell** command window, run the following command.</span></span>
    
  ```
  Connect-MsolService
  ```

2. <span data-ttu-id="f5dad-143">**[Azure Active Directory PowerShell]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-143">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
3. <span data-ttu-id="f5dad-144">**[Azure Active Directory PowerShell]** ダイアログ ボックスの手順に従って、検証コードなどの他の認証情報を提供してから、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-144">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
## <a name="how-do-you-know-this-worked"></a><span data-ttu-id="f5dad-145">正常な動作を確認する方法</span><span class="sxs-lookup"><span data-stu-id="f5dad-145">How do you know this worked?</span></span>
<span data-ttu-id="f5dad-146"><a name="step3"> </a></span><span class="sxs-lookup"><span data-stu-id="f5dad-146"><a name="step3"> </a></span></span>

<span data-ttu-id="f5dad-p108">何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Office 365 コマンドレット ( **Get-MsolUser** など) を実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="f5dad-149">エラーが表示された場合は、次の要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-149">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="f5dad-p109">**よくある原因は、正しくないパスワードです** 。手順 3 をもう一度実行して、ユーザー名とパスワードの入力に注意します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="f5dad-p110">**Microsoft PowerShell の Microsoft Azure Active Directory モジュール では、Microsoft .NET Framework 3.5. _x_ 機能がお使いのコンピューターで有効になっている必要があります** 。お使いのコンピューターに、より新しいバージョン (たとえば、4 または 4.5. _x_)がインストールされている場合でも, .NET Framework の古いバージョンとの下位互換性を有効または無効にすることができます。詳細については、以下のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5. _x_ feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5. _x_), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="f5dad-157">Windows Server 2012 または Windows Server 2012 R2 の場合、「[役割と機能の追加ウィザードを使用して .NET Framework 3.5 を有効にする](https://go.microsoft.com/fwlink/p/?LinkId=532368)」をご覧ください</span><span class="sxs-lookup"><span data-stu-id="f5dad-157">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="f5dad-158">Windows 8 または Windows 8.1 の場合、「[Windows 8 または Windows 8.1 への .NET Framework 3.5 のインストール](https://go.microsoft.com/fwlink/p/?LinkId=532369)」をご覧ください</span><span class="sxs-lookup"><span data-stu-id="f5dad-158">For Windows 8 or Windows 8.1, see [Installing the .NET Framework 3.5 on Windows 8 or 8.1](https://go.microsoft.com/fwlink/p/?LinkId=532369)</span></span>
    
  - <span data-ttu-id="f5dad-159">Windows 7 または Windows Server 2008 R2 の場合、「[Windows PowerShell 用 Azure Active Directory モジュールを開くことができない](https://go.microsoft.com/fwlink/p/?LinkId=532370)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="f5dad-159">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>
    
- <span data-ttu-id="f5dad-p111">**お使いの Microsoft PowerShell の Microsoft Azure Active Directory モジュール のバージョンは期限切れの可能性があります。** Office 365 PowerShell または Microsoft PowerShell の Microsoft Azure Active Directory モジュール で、次のコマンドを実行して確認します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="f5dad-162">返されたバージョン番号が 1.0.8070.2 の値より小さい場合は、Microsoft PowerShell の Microsoft Azure Active Directory モジュール をアンインストールして、手順 1 のリンクから最新バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-162">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="f5dad-163">**接続エラーが発生した場合、次のトピックをご覧ください: **["Connect-MsolService:型の例外がスローされました" というエラー](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="f5dad-163">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    
## <a name="connect-with-the-azure-active-directory-v2-powershell-module"></a><span data-ttu-id="f5dad-164">Azure Active Directory V2 PowerShell モジュールを使用した接続</span><span class="sxs-lookup"><span data-stu-id="f5dad-164">Connect with the Azure Active Directory V2 PowerShell module</span></span>
<span data-ttu-id="f5dad-165"><a name="ConnectV2"> </a></span><span class="sxs-lookup"><span data-stu-id="f5dad-165"><a name="ConnectV2"> </a></span></span>

<span data-ttu-id="f5dad-166">[Azure Active Directory V2 PowerShell モジュール](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)において新しいコマンドレットを必要とするプロシージャについては、以下のステップを実行してモジュールをインストールし、Office 365 のサブスクリプションに接続してください。</span><span class="sxs-lookup"><span data-stu-id="f5dad-166">For procedures that require the new cmdlets in the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory), use these steps to install the module and connect to your Office 365 subscription:</span></span>
  
1. <span data-ttu-id="f5dad-167">管理者特権で Windows PowerShell コマンド プロンプトを開きます (Windows PowerShell を管理者として実行)。</span><span class="sxs-lookup"><span data-stu-id="f5dad-167">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="f5dad-168">[ **Administrator:Windows PowerShell**] コマンド ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-168">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD 
  ```

<span data-ttu-id="f5dad-169">信頼されていないリポジトリからモジュールをインストールするようにプロンプトが出されたら、「 **Y**」と入力し、ENTER を押します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-169">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>
    
3. <span data-ttu-id="f5dad-170">新しいモジュールのインストールが完了したら、以下のコマンドを使用して Office 365 のサブスクリプションに接続します。</span><span class="sxs-lookup"><span data-stu-id="f5dad-170">When the installation of the new module is complete, use these commands to connect to your Office 365 subscription:</span></span>
    
  -  <span data-ttu-id="f5dad-171">*アカウント名とパスワード*  を使用する場合:</span><span class="sxs-lookup"><span data-stu-id="f5dad-171">With an *account name and password*  :</span></span>
    
  ```
  $UserCredential = Get-Credential
Connect-AzureAD -Credential $UserCredential
  ```

 <span data-ttu-id="f5dad-172">**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-172">In the **Windows PowerShell Credential Request** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>
    
  - <span data-ttu-id="f5dad-173">*多要素認証 (MFA)*  を使用する場合:</span><span class="sxs-lookup"><span data-stu-id="f5dad-173">With  *multi-factor authentication (MFA)*  :</span></span>
    
  ```
  Connect-AzureAD
  ```

<span data-ttu-id="f5dad-174">**[Azure Active Directory PowerShell]** ダイアログ ボックスで、Office 365職場または学校のアカウント ユーザー名とパスワードを入力してから、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-174">In the **Azure Active Directory PowerShell** dialog box, type your Office 365 work or school account user name and password, and then click **Sign in**.</span></span>
    
<span data-ttu-id="f5dad-175">**[Azure Active Directory PowerShell]** ダイアログ ボックスの手順に従って、検証コードなどの他の認証情報を提供してから、 **[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5dad-175">Follow the instructions in the **Azure Active Directory PowerShell** dialog box to provide additional authentication information, such as a verification code, and then click **Sign in**.</span></span>
    
<span data-ttu-id="f5dad-176">接続後は、[Azure Active Directory V2 PowerShell モジュール](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)の新しいコマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5dad-176">After connecting, you can use the new cmdlets for the [Azure Active Directory V2 PowerShell module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f5dad-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5dad-177">See also</span></span>

#### 

[<span data-ttu-id="f5dad-178">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="f5dad-178">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f5dad-179">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="f5dad-179">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="f5dad-180">単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="f5dad-180">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
#### 

[<span data-ttu-id="f5dad-181">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="f5dad-181">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
  
[<span data-ttu-id="f5dad-182">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="f5dad-182">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

