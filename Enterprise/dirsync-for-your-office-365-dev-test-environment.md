---
title: "Office 365 開発/テスト環境の DirSync"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- TLG
- Ent_TLGs
ms.assetid: e6b27e25-74ae-4b54-9421-c8e911aef543
description: "概要: Office 365 の開発/テスト環境のディレクトリ同期を構成します。"
ms.openlocfilehash: 8a656ea742af642a8b4dc3e096764f0e8cbde074
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="dirsync-for-your-office-365-devtest-environment"></a><span data-ttu-id="fbd21-103">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="fbd21-103">DirSync for your Office 365 dev/test environment</span></span>

 <span data-ttu-id="fbd21-104">**の概要:**Office 365 の開発/テスト環境のディレクトリ同期を構成します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-104">**Summary:** Configure directory synchronization for your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="fbd21-p101">多くの組織は、Azure AD Connect とディレクトリ同期 (DirSync) を使用して、オンプレミスの Windows Server Active Directory (AD) フォレスト内のアカウントのセットを Office 365 内のアカウントのセットに同期しています。この記事では、Office 365 の開発/テスト環境にパスワード同期を伴う DirSync を追加する方法について説明します。最終的な構成は、次のとおりになります。</span><span class="sxs-lookup"><span data-stu-id="fbd21-p101">Many organizations use Azure AD Connect and directory synchronization (DirSync) to synchronize the set of accounts in their on-premises Windows Server Active Directory (AD) forest to the set of accounts in Office 365. This article describes how you can add DirSync with password synchronization to the Office 365 dev/test environment, resulting in the following configuration.</span></span>
  
![DirSync を使用した Office 365 の開発/テスト環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="fbd21-108">この構成は、次の内容で成立します。 </span><span class="sxs-lookup"><span data-stu-id="fbd21-108">This configuration consists of:</span></span> 
  
- <span data-ttu-id="fbd21-109">Office 365 E5 試用版サブスクリプション。このサブスクリプションは、作成時から 30 日で有効期限が切れます。</span><span class="sxs-lookup"><span data-stu-id="fbd21-109">An Office 365 E5 Trial Subscription, which expires 30 days from when you create it.</span></span>
    
- <span data-ttu-id="fbd21-p102">インターネットに接続する組織の簡易型イントラネット。Azure 仮想ネットワークのサブネット上に配置された 3 つの仮想マシン (DC1、APP1、および CLIENT1) で構成されます。Azure AD Connect は、Windows Server AD ドメインを Office 365 に同期するために APP1 で実行します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-p102">A simplified organization intranet connected to the Internet, consisting of three virtual machines on a subnet of an Azure virtual network (DC1, APP1, and CLIENT1). Azure AD Connect runs on APP1 to synchronize the Windows Server AD domain to Office 365.</span></span>
    
<span data-ttu-id="fbd21-112">この開発/テスト環境は、次に示す 2 つのフェーズで構成します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-112">There are two phases to setting up this dev/test environment:</span></span>
  
1. <span data-ttu-id="fbd21-113">Office 365 の開発/テスト環境を作成します (Azure 仮想ネットワーク内の仮想マシン DC1、APP1、および CLIENT1 と、Office 365 E5 試用版サブスクリプションによる環境)。</span><span class="sxs-lookup"><span data-stu-id="fbd21-113">Create the Office 365 dev/test environment (the DC1, APP1, and CLIENT1 virtual machines in an Azure virtual network with an Office 365 E5 trial subscription).</span></span>
    
2. <span data-ttu-id="fbd21-114">APP1 に Azure AD Connect をインストールして構成します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-114">Install and configure Azure AD Connect on APP1.</span></span>
    
> [!TIP]
> <span data-ttu-id="fbd21-115">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="fbd21-115">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-an-office-365-devtest-environment"></a><span data-ttu-id="fbd21-116">フェーズ 1: Office 365 の開発/テスト環境を作成する</span><span class="sxs-lookup"><span data-stu-id="fbd21-116">Phase 1: Create an Office 365 dev/test environment</span></span>

<span data-ttu-id="fbd21-p103">フェーズ 1、2、および 3[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)の資料の指示に従います。ここでは、結果として得られる構成です。</span><span class="sxs-lookup"><span data-stu-id="fbd21-p103">Follow the instructions in phases 1, 2, and 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) article. Here is the resulting configuration.</span></span>
  
![Office 365 開発/テスト環境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="fbd21-120">この構成は、次の内容で成立します。 </span><span class="sxs-lookup"><span data-stu-id="fbd21-120">This configuration consists of:</span></span> 
  
- <span data-ttu-id="fbd21-121">Office 365 E5 試用版サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="fbd21-121">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="fbd21-122">インターネットに接続する組織の簡易型イントラネット。Azure 仮想ネットワークのサブネット上に配置された仮想マシン DC1、APP1、および CLIENT1 で構成されます。</span><span class="sxs-lookup"><span data-stu-id="fbd21-122">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
## <a name="phase-2-install-azure-ad-connect-on-app1"></a><span data-ttu-id="fbd21-123">フェーズ 2: APP1 に Azure AD Connect をインストールする</span><span class="sxs-lookup"><span data-stu-id="fbd21-123">Phase 2: Install Azure AD Connect on APP1</span></span>

<span data-ttu-id="fbd21-p104">インストールと構成が済ませてあると、Azure AD Connect は CORP Windows Server AD ドメインのアカウントのセットを Office 365 試用版サブスクリプションのアカウントのセットと同期します。次に示す手順を実行して、APP1 に Azure AD をインストールして、その動作を確認します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-p104">Once installed and configured, Azure AD Connect synchronizes the set of accounts in the CORP Windows Server AD domain with the set of accounts in your Office 365 trial subscription. The following procedure steps you through installing Azure AD Connect on APP1 and verifying that it works.</span></span>
  
### <a name="install-and-configure-azure-ad-connect-on-app1"></a><span data-ttu-id="fbd21-126">インストールし、APP1 の Azure AD 接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-126">Install and configure Azure AD Connect on APP1</span></span>

1. <span data-ttu-id="fbd21-127">APP1 CORP でへの接続を[Azure ポータル](https://portal.azure.com)から\\User1 のアカウントです。</span><span class="sxs-lookup"><span data-stu-id="fbd21-127">From the [Azure portal](https://portal.azure.com), connect to APP1 with the CORP\\User1 account.</span></span>
    
2. <span data-ttu-id="fbd21-128">APP1 から、管理者レベルの Windows PowerShell コマンド プロンプトを起動して、次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-128">From APP1, open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force

  ```

3. <span data-ttu-id="fbd21-129">タスク バーから [ **Internet Explorer** ] をクリックし、 [https://aka.ms/aadconnect](https://aka.ms/aadconnect)に移動します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-129">From the task bar, click **Internet Explorer** and go to [https://aka.ms/aadconnect](https://aka.ms/aadconnect).</span></span>
    
4. <span data-ttu-id="fbd21-130">Microsoft Azure Active Directory に接続] ページで、[**ダウンロード**] をクリックし、[**実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-130">On the Microsoft Azure Active Directory Connect page, click **Download**, and then click **Run**.</span></span>
    
5. <span data-ttu-id="fbd21-131">**Azure AD 接続へようこそ**] ページで、[**同意する**] をクリックし、[**続行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-131">On the **Welcome to Azure AD Connect** page, click **I agree**, and then click **Continue**.</span></span>
    
6. <span data-ttu-id="fbd21-132">[**高速の設定**] ページで、**高速の設定を使用する**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-132">On the **Express Settings** page, click **Use express settings**.</span></span>
    
7. <span data-ttu-id="fbd21-133">**Azure AD への接続**] ページで、そのパスワードを [**パスワード**] に**ユーザー名**種類で、グローバル管理者のアカウント名を入力し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-133">On the **Connect to Azure AD** page, type your global administrator account name in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="fbd21-134">[ **AD DS への接続**] ページで、次のように入力します。**株式会社\\User1**で**ユーザー名、** **パスワード**にパスワードを入力し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-134">On the **Connect to AD DS** page, type **CORP\\User1** in **Username,** type its password in **Password**, and then click **Next**.</span></span>
    
9. <span data-ttu-id="fbd21-135">**Azure AD サインインの構成**] ページで、**検証済みの任意のドメインなしで続行する**] をクリックし、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-135">On the **Azure AD sign-in configuration** page, click **Continue without any verified domains**, and then click **Next**.</span></span>
    
10. <span data-ttu-id="fbd21-136">**[構成の準備完了]** ページで、 **[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-136">On the **Ready to configure** page, click **Install**.</span></span>
    
11. <span data-ttu-id="fbd21-137">[**構成の完了**] ページで [**終了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-137">On the **Configuration complete** page, click **Exit**.</span></span>
    
12. <span data-ttu-id="fbd21-138">Internet Explorer のでは、Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) に移動し、Office 365 試用版サブスクリプションのグローバル管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-138">In Internet Explorer, go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
13. <span data-ttu-id="fbd21-139">ポータルのメイン ページで、 **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-139">From the main portal page, click **Admin**.</span></span>
    
14. <span data-ttu-id="fbd21-140">左側のナビゲーションで、 **[ユーザー] > [アクティブなユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-140">In the left navigation, click **Users > Active users**.</span></span>
    
    <span data-ttu-id="fbd21-p105">**User1**をという名前のアカウントに注意してください。このアカウントは CORP Windows サーバーの AD ドメインとは、ディレクトリ同期が動作していたことの証明です。</span><span class="sxs-lookup"><span data-stu-id="fbd21-p105">Note the account named **User1**. This account is from the CORP Windows Server AD domain and is proof that DirSync has worked.</span></span>
    
15. <span data-ttu-id="fbd21-p106">**User1**アカウントをクリックします。製品のライセンスの [**編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-p106">Click the **User1** account. For product licenses, click **Edit**.</span></span>
    
16. <span data-ttu-id="fbd21-p107">**製品のライセンス**では、国または地域を選択する.」をクリックして**Office 365 エンタープライズ E5** (へ**の**切り替え) の**電源を**コントロール、ページの下部にある**保存**を] をクリックし、[**閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbd21-p107">In **Product licenses**, select your country, and then click the **Off** control for **Office 365 Enterprise E5** (switching it to **On**). Click **Save** at the bottom of the page, and then click **Close**.</span></span>
    
<span data-ttu-id="fbd21-147">最終的な構成を示します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-147">This is the resulting configuration.</span></span>
  
![DirSync を使用した Office 365 の開発/テスト環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
<span data-ttu-id="fbd21-149">この構成は、次の内容で成立します。 </span><span class="sxs-lookup"><span data-stu-id="fbd21-149">This configuration consists of:</span></span> 
  
- <span data-ttu-id="fbd21-150">Office 365 E5 試用版サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="fbd21-150">An Office 365 E5 Trial Subscription.</span></span>
    
- <span data-ttu-id="fbd21-p108">インターネットに接続する組織の簡易型イントラネット。Azure 仮想ネットワークのサブネット上に配置された仮想マシン DC1、APP1、および CLIENT1 で構成されます。Azure AD Connect は APP1 上で実行され、CORP Windows Server AD ドメインを 30 分ごとに Office 365 に同期します。</span><span class="sxs-lookup"><span data-stu-id="fbd21-p108">A simplified organization intranet connected to the Internet, consisting of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network. Azure AD Connect runs on APP1 to synchronize the CORP Windows Server AD domain to Office 365 every 30 minutes.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="fbd21-153">次のステップ</span><span class="sxs-lookup"><span data-stu-id="fbd21-153">Next Step</span></span>

<span data-ttu-id="fbd21-154">組織のディレクトリ同期を展開する準備ができたら、[展開 Office 365 ディレクトリ同期 (DirSync) で、Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbd21-154">When you are ready to deploy DirSync for your organization, see [Deploy Office 365 Directory Synchronization (DirSync) in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbd21-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbd21-155">See Also</span></span>

[<span data-ttu-id="fbd21-156">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="fbd21-156">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="fbd21-157">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="fbd21-157">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="fbd21-158">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="fbd21-158">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="fbd21-159">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="fbd21-159">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="fbd21-160">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="fbd21-160">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="fbd21-161">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="fbd21-161">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




