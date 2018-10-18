---
title: Office 365 PowerShell への接続
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/16/2018
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
ms.openlocfilehash: 2ea9c3eaa9a589bed6bf7ac575ffd241b7a72f01
ms.sourcegitcommit: 8cacedcba4627042d4bd17f1a94fddcfd87f77b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2018
ms.locfileid: "25601641"
---
# <a name="connect-to-office-365-powershell"></a><span data-ttu-id="d881d-103">Office 365 PowerShell への接続</span><span class="sxs-lookup"><span data-stu-id="d881d-103">Connect to Office 365 PowerShell</span></span>

 <span data-ttu-id="d881d-104">**の概要:** コマンドラインから管理タスクを実行するのには Office 365 の PowerShell を使用して、Office 365 の組織に接続します。</span><span class="sxs-lookup"><span data-stu-id="d881d-104">**Summary:** Connect to your Office 365 organization using Office 365 PowerShell to perform administration tasks from the command line.</span></span>
  
<span data-ttu-id="d881d-p101">Office 365 の PowerShell では、コマンド ・ ラインから、Office 365 の設定を管理することができます。Office 365 の PowerShell への接続で必要なソフトウェアをインストールし、Office 365 の組織に接続し、単純なプロセスです。</span><span class="sxs-lookup"><span data-stu-id="d881d-p101">Office 365 PowerShell lets you to manage your Office 365 settings from the command line. Connecting to Office 365 PowerShell is a simple process where you install the required software and then connect to your Office 365 organization.</span></span> 

<span data-ttu-id="d881d-107">Office 365 に接続し、ユーザー アカウント、グループ、およびライセンスの管理に使用する PowerShell モジュールの 2 つのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="d881d-107">There are two versions of the PowerShell module that you use to connect to Office 365 and administer user accounts, groups, and licenses:</span></span>

- <span data-ttu-id="d881d-108">Azure のアクティブ ディレクトリ PowerShell (コマンドレットは、その名前に**AzureAD**を含む) のグラフの</span><span class="sxs-lookup"><span data-stu-id="d881d-108">Azure Active Directory PowerShell for Graph (cmdlets include **AzureAD** in their name)</span></span> 
- <span data-ttu-id="d881d-109">Microsoft Azure Active Directory モジュールを Windows PowerShell (コマンドレットは、その名前で**MSol**を含む)</span><span class="sxs-lookup"><span data-stu-id="d881d-109">Microsoft Azure Active Directory Module for Windows PowerShell (cmdlets include **MSol** in their name)</span></span> 

<span data-ttu-id="d881d-p102">この資料の日付には、グラフ モジュールの Azure Active Directory PowerShell はない完全に機能を置き換えるユーザー、グループ、およびライセンスの管理については、Microsoft Azure Active Directory モジュールを Windows PowerShell モジュールのコマンドレットで.多くの場合、両方のバージョンを使用する必要があります。同じコンピューターに両方のバージョンを安全にインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="d881d-p102">As of the date of this article, the Azure Active Directory PowerShell for Graph module does not completely replace the functionality in the cmdlets of Microsoft Azure Active Directory Module for Windows PowerShell module for user, group, and license administration. In many cases, you need to use both versions. You can safely install both versions on the same computer.</span></span>

> [!TIP]
> <span data-ttu-id="d881d-p103">**PowerShell を初めて使用されますか。**[PowerShell の概要に関するビデオ](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx)を視聴し、LinkedIn Learning にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="d881d-p103">**New to PowerShell?** See a [video Overview of PowerShell](https://support.office.com/en-us/article/7d0107d4-f672-4d0f-ad7d-417844b926c7.aspx), brought to you by LinkedIn Learning.</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="d881d-115">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="d881d-115">What do you need to know before you begin?</span></span>

- <span data-ttu-id="d881d-116">予想所要時間 : 5 分</span><span class="sxs-lookup"><span data-stu-id="d881d-116">Estimated time to complete: 5 minutes</span></span>
    
- <span data-ttu-id="d881d-117">次の Windows のバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d881d-117">You can use the following versions of Windows:</span></span>
    
  - <span data-ttu-id="d881d-118">10 の Windows、Windows 8.1、Windows 8、または Windows 7 Service Pack 1 (SP1)</span><span class="sxs-lookup"><span data-stu-id="d881d-118">Windows 10, Windows 8.1, Windows 8, or Windows 7 Service Pack 1 (SP1)</span></span> 
    
  - <span data-ttu-id="d881d-119">Windows Server 2019、2016 の Windows サーバー、Windows Server 2012 R2、Windows Server 2012 では、または Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d881d-119">Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1</span></span>
    
    > [!NOTE]
    ><span data-ttu-id="d881d-p104">64 ビット バージョンの Windows を使用してください。Microsoft PowerShell の Microsoft Azure Active Directory モジュールの 32 ビット バージョンのサポートは 2014 年 10 月に終了しました。</span><span class="sxs-lookup"><span data-stu-id="d881d-p104">Use a 64-bit version of Windows. Support for the 32-bit version the Microsoft Azure Active Directory Module for Windows PowerShell was discontinued in October of 2014.</span></span>
    
-  <span data-ttu-id="d881d-p105">これらの手順は、Office 365 の管理者ロールのメンバーであるユーザーを意図しています。詳細については、 [Office 365 の管理者の役割](https://go.microsoft.com/fwlink/p/?LinkId=532367)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d881d-p105">These procedures are intended for users who are members of an Office 365 admin role. For more information, see [About Office 365 admin roles](https://go.microsoft.com/fwlink/p/?LinkId=532367).</span></span>


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d881d-124">グラフ モジュールの Azure Active Directory PowerShell を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="d881d-124">Connect with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d881d-125">[グラフでは、Azure Active ディレクトリ PowerShell](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)モジュール内のコマンドでは、そのコマンドレット名に**AzureAD**があります。</span><span class="sxs-lookup"><span data-stu-id="d881d-125">Commands in the [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) module have **AzureAD** in their cmdlet name.</span></span>

<span data-ttu-id="d881d-126">グラフ モジュール用の新しい Azure Active Directory の PowerShell コマンドレットを必要とする手順は、モジュールをインストールし、Office 365 サブスクリプションに接続する手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="d881d-126">For procedures that require the new cmdlets in the Azure Active Directory PowerShell for Graph module, use these steps to install the module and connect to your Office 365 subscription.</span></span>

>[!Note]
><span data-ttu-id="d881d-127">異なるバージョンの Microsoft Windows のサポートについては、[グラフのモジュールのアクティブなディレクトリの PowerShell を Azure](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d881d-127">See [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory) for information about the support for different versions of Microsoft Windows.</span></span>
>

### <a name="step-1-install-required-software"></a><span data-ttu-id="d881d-128">手順 1: 必要なソフトウェアをインストールします</span><span class="sxs-lookup"><span data-stu-id="d881d-128">Step 1: Install required software</span></span>

<span data-ttu-id="d881d-p106">これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d881d-p106">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1. <span data-ttu-id="d881d-131">管理者特権で Windows PowerShell コマンド プロンプトを開きます (Windows PowerShell を管理者として実行)。</span><span class="sxs-lookup"><span data-stu-id="d881d-131">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
    
2. <span data-ttu-id="d881d-132">[ **Administrator:Windows PowerShell**] コマンド ウィンドウで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d881d-132">In the **Administrator: Windows PowerShell** command window, run this command:</span></span>
    
  ```
  Install-Module -Name AzureAD
  ```

<span data-ttu-id="d881d-133">信頼されていないリポジトリからモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。</span><span class="sxs-lookup"><span data-stu-id="d881d-133">If prompted about installing a module from an untrusted repository, type **Y** and press ENTER.</span></span>

### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="d881d-134">手順 2: Office 365 サブスクリプションの Azure AD に接続します。</span><span class="sxs-lookup"><span data-stu-id="d881d-134">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="d881d-135">アカウント名とパスワード、または*多要素認証 (MFA)* では、Office 365 サブスクリプションの Azure AD に接続するには、(昇格するは必要ありません)、Windows PowerShell コマンド プロンプトからこのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d881d-135">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-AzureAD
```

<span data-ttu-id="d881d-136">**自分のアカウントにサインイン**] ダイアログ ボックスで、Office 365 の作業時間や学校のアカウントのユーザー名とパスワードを入力し、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d881d-136">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="d881d-137">MFA を使用する場合は、検証コードなどの追加の認証情報を提供する追加のダイアログ ボックスの指示に従います。</span><span class="sxs-lookup"><span data-stu-id="d881d-137">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

>[!Tip]
><span data-ttu-id="d881d-138">Office 365 のドイツに接続するには、 [PowerShell を使用して、Azure のドイツへの接続](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d881d-138">To connect to Office 365 Germany, see [Connect to Azure Germany by using PowerShell](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps).</span></span>
>
    
<span data-ttu-id="d881d-139">接続した後、[グラフのモジュールのアクティブなディレクトリの PowerShell を Azure](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory)の新しいコマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d881d-139">After connecting, you can use the new cmdlets for the [Azure Active Directory PowerShell for Graph module](https://docs.microsoft.com/powershell/azuread/v2/azureactivedirectory).</span></span>
  

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d881d-140">Microsoft PowerShell の Microsoft Azure Active Directory モジュールとの接続</span><span class="sxs-lookup"><span data-stu-id="d881d-140">Connect with the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d881d-141">Microsoft PowerShell の Microsoft Azure Active Directory モジュールには、コマンドレット名に **Msol** が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d881d-141">Commands in the Microsoft Azure Active Directory Module for Windows PowerShell have **Msol** in their cmdlet name.</span></span>
    
### <a name="step-1-install-required-software"></a><span data-ttu-id="d881d-142">手順 1: 必要なソフトウェアをインストールします</span><span class="sxs-lookup"><span data-stu-id="d881d-142">Step 1: Install required software</span></span>

<span data-ttu-id="d881d-p107">これらの手順は、お使いのコンピューターで 1 度だけ必要となり、接続する度に実行する必要はありません。しかし、定期的にソフトウェアの新しいバージョンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d881d-p107">These steps are required once on your computer, not every time you connect. However, you'll likely need to install newer versions of the software periodically.</span></span>
  
1.  <span data-ttu-id="d881d-145">Microsoft Online Services サインイン アシスタントの 64 ビット バージョンをインストールします: [IT プロフェッショナル用 Microsoft Online Services サインイン アシスタント RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152)。</span><span class="sxs-lookup"><span data-stu-id="d881d-145">Install the 64-bit version of the Microsoft Online Services Sign-in Assistant: [Microsoft Online Services Sign-in Assistant for IT Professionals RTW](https://go.microsoft.com/fwlink/p/?LinkId=286152).</span></span>
    
2. <span data-ttu-id="d881d-146">以下の手順に従って、Windows PowerShell の Microsoft Azure Active Directory モジュールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d881d-146">Install the Microsoft Azure Active Directory Module for Windows PowerShell with these steps:</span></span>
    
  - <span data-ttu-id="d881d-147">管理者特権で Windows PowerShell コマンド プロンプトを開きます (Windows PowerShell を管理者として実行)。</span><span class="sxs-lookup"><span data-stu-id="d881d-147">Open an elevated Windows PowerShell command prompt (run Windows PowerShell as an administrator).</span></span>
  - <span data-ttu-id="d881d-148">**Install-Module MSOnline** コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d881d-148">Run the **Install-Module MSOnline** command.</span></span>
  - <span data-ttu-id="d881d-149">NuGet プロバイダーをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。</span><span class="sxs-lookup"><span data-stu-id="d881d-149">If prompted to install the NuGet provider, type **Y** and press ENTER.</span></span>
  - <span data-ttu-id="d881d-150">PSGallery からモジュールをインストールするようにメッセージが表示されたら、「**Y**」と入力し、ENTER を押します。</span><span class="sxs-lookup"><span data-stu-id="d881d-150">If prompted to install the module from PSGallery, type **Y** and press ENTER.</span></span>
    
### <a name="step-2-connect-to-azure-ad-for-your-office-365-subscription"></a><span data-ttu-id="d881d-151">手順 2: Office 365 サブスクリプションの Azure AD に接続します。</span><span class="sxs-lookup"><span data-stu-id="d881d-151">Step 2: Connect to Azure AD for your Office 365 subscription</span></span>

<span data-ttu-id="d881d-152">アカウント名とパスワード、または*多要素認証 (MFA)* では、Office 365 サブスクリプションの Azure AD に接続するには、(昇格するは必要ありません)、Windows PowerShell コマンド プロンプトからこのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d881d-152">To connect to Azure AD for your Office 365 subscription with an account name and password or with *multi-factor authentication (MFA)*, run this command from a Windows PowerShell command prompt (it does not have to be elevated):</span></span>
    
```
Connect-MsolService
```

<span data-ttu-id="d881d-153">**自分のアカウントにサインイン**] ダイアログ ボックスで、Office 365 の作業時間や学校のアカウントのユーザー名とパスワードを入力し、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d881d-153">In the **Sign into your account** dialog box, type your Office 365 work or school account user name and password, and then click **OK**.</span></span>

<span data-ttu-id="d881d-154">MFA を使用する場合は、検証コードなどの追加の認証情報を提供する追加のダイアログ ボックスの指示に従います。</span><span class="sxs-lookup"><span data-stu-id="d881d-154">If you are using MFA, follow the instructions in the additional dialog boxes to provide more authentication information, such as a verification code.</span></span>

>[!Tip]
><span data-ttu-id="d881d-155">Office 365 のドイツに接続するには、 [PowerShell を使用して、Azure のドイツへの接続](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d881d-155">To connect to Office 365 Germany, see [Connect to Azure Germany by using PowerShell](https://docs.microsoft.com/azure/germany/germany-get-started-connect-with-ps).</span></span>
>
    
### <a name="how-do-you-know-this-worked"></a><span data-ttu-id="d881d-156">これが機能したことを知る方法</span><span class="sxs-lookup"><span data-stu-id="d881d-156">How do you know this worked?</span></span>

<span data-ttu-id="d881d-p108">何もエラーが表示されなければ、正常に接続されています。簡単に確かめるには、Office 365 コマンドレット ( **Get-MsolUser** など) を実行して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="d881d-p108">If you don't receive any errors, you connected successfully. A quick test is to run an Office 365 cmdlet—for example, **Get-MsolUser** —and see the results.</span></span>
  
<span data-ttu-id="d881d-159">エラーが表示された場合は、次の要件を確認します。</span><span class="sxs-lookup"><span data-stu-id="d881d-159">If you receive errors, check the following requirements:</span></span>
  
- <span data-ttu-id="d881d-p109">**よくある原因は、正しくないパスワードです** 。手順 3 をもう一度実行して、ユーザー名とパスワードの入力に注意します。</span><span class="sxs-lookup"><span data-stu-id="d881d-p109">**A common problem is an incorrect password**. Run Step 3 again. and pay close attention to the user name and password you enter.</span></span>
    
- <span data-ttu-id="d881d-p110">\* *、Microsoft Azure Active ディレクトリ モジュールを Windows PowerShell には、Microsoft.NET Framework 3.5* 。上のコンピューター \* \* x \* 機能を有効にします。お使いのコンピューターがインストールされている新しいバージョンを持っている可能性があります (たとえば、4 または 4.5\* 。x \*)、.NET Framework の以前のバージョンとの互換性を有効または無効になっている下位ですが。詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d881d-p110">**The Microsoft Azure Active Directory Module for Windows PowerShell requires that the Microsoft .NET Framework 3.5.* x* feature is enabled on your computer**. It's likely that your computer has a newer version installed (for example, 4 or 4.5.* x*), but backwards compatibility with older versions of the .NET Framework can be enabled or disabled. For more information, see the following topics:</span></span>
    
  - <span data-ttu-id="d881d-165">Windows Server 2012 または Windows Server 2012 R2 の場合、「[役割と機能の追加ウィザードを使用して .NET Framework 3.5 を有効にする](https://go.microsoft.com/fwlink/p/?LinkId=532368)」をご覧ください</span><span class="sxs-lookup"><span data-stu-id="d881d-165">For Windows Server 2012 or Windows Server 2012 R2, see [Enable .NET Framework 3.5 by using the Add Roles and Features Wizard](https://go.microsoft.com/fwlink/p/?LinkId=532368)</span></span>
    
  - <span data-ttu-id="d881d-166">Windows 7 または Windows Server 2008 R2 の場合、「[Windows PowerShell 用 Azure Active Directory モジュールを開くことができない](https://go.microsoft.com/fwlink/p/?LinkId=532370)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="d881d-166">For Windows 7 or Windows Server 2008 R2, see [You can't open the Azure Active Directory Module for Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=532370)</span></span>

  - <span data-ttu-id="d881d-167">10 の Windows、Windows 8.1 では、Windows 8 の[10 の Windows、Windows 8.1 では、Windows 8 に.NET Framework 3.5 のインストール](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)を参照してください.</span><span class="sxs-lookup"><span data-stu-id="d881d-167">For Windows 10, Windows 8.1, and Windows 8, see [Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](https://docs.microsoft.com/en-us/dotnet/framework/install/dotnet-35-windows-10)</span></span>

  
- <span data-ttu-id="d881d-p111">**お使いの Microsoft PowerShell の Microsoft Azure Active Directory モジュール のバージョンは期限切れの可能性があります。** Office 365 PowerShell または Microsoft PowerShell の Microsoft Azure Active Directory モジュール で、次のコマンドを実行して確認します。</span><span class="sxs-lookup"><span data-stu-id="d881d-p111">**Your version of the Microsoft Azure Active Directory Module for Windows PowerShell might be out of date.** To check, run the following command in Office 365 PowerShell or the Microsoft Azure Active Directory Module for Windows PowerShell:</span></span>
    
  ```
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    <span data-ttu-id="d881d-170">返されたバージョン番号が 1.0.8070.2 の値より小さい場合は、Microsoft PowerShell の Microsoft Azure Active Directory モジュール をアンインストールして、手順 1 のリンクから最新バージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d881d-170">If the version number returned is lower than the value 1.0.8070.2, uninstall the Microsoft Azure Active Directory Module for Windows PowerShell and install the latest version from the link in Step 1.</span></span>
    
- <span data-ttu-id="d881d-171">\*\*接続エラーが発生した場合、次のトピックをご覧ください: \*\*["Connect-MsolService:型の例外がスローされました" というエラー](https://go.microsoft.com/fwlink/p/?LinkId=532377)。</span><span class="sxs-lookup"><span data-stu-id="d881d-171">**If you receive a connection error, see this topic:** ["Connect-MsolService: Exception of type was thrown" error](https://go.microsoft.com/fwlink/p/?LinkId=532377).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="d881d-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="d881d-172">See also</span></span>

- [<span data-ttu-id="d881d-173">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="d881d-173">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="d881d-174">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="d881d-174">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="d881d-175">単一の Windows PowerShell ウィンドウですべての Office 365 サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="d881d-175">Connect to all Office 365 services in a single Windows PowerShell window</span></span>](connect-to-all-office-365-services-in-a-single-windows-powershell-window.md)
- [<span data-ttu-id="d881d-176">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="d881d-176">Get-Credential</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=389618)
- [<span data-ttu-id="d881d-177">Connect-MsolService</span><span class="sxs-lookup"><span data-stu-id="d881d-177">Connect-MsolService</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532375)

