---
title: "Office 365 開発/テスト環境"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365, Strat_O365_Enterprise
ms.custom: Strat_O365_Enterprise, Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: "概要: ガイドを使用してこのテスト ラボの評価や開発/テスト用の Office 365 の試用版サブスクリプションを作成します。"
ms.openlocfilehash: b3c9e83dfab3aaf02ad598021e11965657e877bb
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="5ebd5-103">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="5ebd5-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="5ebd5-104">**の概要:**評価や開発/テスト用の Office 365 の試用版サブスクリプションを作成するのにには、このテスト ラボ ガイド 』 を使用します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="5ebd5-p101">Office 365 試用版サブスクリプションを使用できます。また、アプリケーションの Office 365 開発/テスト環境を作成したり、Office 365 の機能をデモンストレーションすることができます。次の 2 つのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="5ebd5-107">ライトウェイトの Office 365 開発/テスト環境は、メイン コンピューターからアクセスする Office 365 試用版サブスクリプションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="5ebd5-p102">機能をすばやくデモンストレーションする場合には、この環境を使用してください。ライトウェイトの Office 365 開発/テスト環境の場合は、この記事のフェーズ 2 と 3 を完了します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="5ebd5-p103">シミュレーションのエンタープライズ Office 365 開発/テスト環境は、Office 365 試用版サブスクリプションと、Microsoft Azure インフラストラクチャ サービスでホストされる、インターネットに接続されたシンプルな組織のイントラネットで構成されています。この構成は Microsoft クラウドで完全に構築できます。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="5ebd5-p104">この環境は、インターネットに接続された一般的な組織ネットワークと類似した環境で機能またはアプリをデモンストレーションする場合や、この種類の環境を必要とする機能に使用してください。シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合は、この記事のフェーズ 1、2、3 を完了します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="5ebd5-p105">この記事を印刷しておき、30 日間の Office 365 試用版サブスクリプションの終了後にこの環境で必要になる特定の値を記録しておくことをお勧めします。試用版サブスクリプションは、追加で 30 日間まで簡単に延長できます。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Microsoft Cloud のテスト ラボ ガイド](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="5ebd5-118">
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="5ebd5-119">フェーズ 1:Azure に基本構成を作成する</span><span class="sxs-lookup"><span data-stu-id="5ebd5-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="5ebd5-120">[開発/テスト環境の基本構成](base-configuration-dev-test-environment.md)の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="5ebd5-p106">Azure サブスクリプションを必要があります。この構成では、 [Azure の無料試用版](https://azure.microsoft.com/pricing/free-trial/)を使用できます。MSDN または Visual Studio のサブスクリプションがある場合は、 [Visual Studio のサブスクライバーに対して毎月 Azure のクレジット](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="5ebd5-124">最終的な構成は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-124">Here is the resulting configuration.</span></span>
  
![Azure の基本構成開発/テスト環境](images/63108214-f716-46ae-9974-072ff15b44a2.png)
  
<span data-ttu-id="5ebd5-126">この構成は、Azure 仮想ネットワーク上の仮想マシン DC1、APP1、および CLIENT1 で成立します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="5ebd5-127">フェーズ 2:Office 365 試用版サブスクリプションを作成する</span><span class="sxs-lookup"><span data-stu-id="5ebd5-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="5ebd5-128">Office 365 E5 試用版サブスクリプションを開始するには、最初に、架空の会社名と新しい Microsoft アカウントが必要になります。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="5ebd5-p107">必須ではありませんが、会社名は、Microsoft のコンテンツのサンプルで使用されている架空の会社である contoso 社の会社名のバリエーションを使用するをお勧めします。ここでは、架空の会社名を記録する: ___</span><span class="sxs-lookup"><span data-stu-id="5ebd5-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: _____________________________________</span></span>
    
2. <span data-ttu-id="5ebd5-p108">、新しい Microsoft アカウントにサインアップするには、 [https://outlook.com](https://outlook.com)に移動し、新しい電子メール アカウントとアドレスを持つアカウントを作成します。Office 365 にサインアップするには、このアカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="5ebd5-133">ここに新しいアカウントの姓名を記録してください: _______________________________</span><span class="sxs-lookup"><span data-stu-id="5ebd5-133">Record the first and last name of your new account here: _______________________________</span></span>
    
  - <span data-ttu-id="5ebd5-134">ここに新しい電子メール アカウントのアドレスを記録してください: _____________________________@outlook.com</span><span class="sxs-lookup"><span data-stu-id="5ebd5-134">Record the new email account address here: _____________________________@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="5ebd5-135">Office 365 E5 試用版サブスクリプションにサインアップする</span><span class="sxs-lookup"><span data-stu-id="5ebd5-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="5ebd5-136">軽量の Office 365 の開発/テスト環境では、お使いのコンピューター上のインターネット ブラウザーを開くし、 [https://aka.ms/e5trial](https://aka.ms/e5trial)に移動します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="5ebd5-137">シミュレートされたエンタープライズ Office 365 の開発/テスト環境。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-137">For the simulated enterprise Office 365 dev/test environment:</span></span>
    
  - <span data-ttu-id="5ebd5-138">[Azure ポータル](https://portal.azure.com)では、CORP と CLIENT1 を接続\\User1 のアカウントです。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-138">From the [Azure portal](https://portal.azure.com), connect to CLIENT1 with the CORP\\User1 account.</span></span>
    
  - <span data-ttu-id="5ebd5-139">管理者レベルの Windows PowerShell コマンド プロンプトを起動して、次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-139">Open an administrator-level Windows PowerShell command prompt, and then run these commands:</span></span>
    
  ```
  Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Set-ItemProperty -Path "HKLM:\\SOFTWARE\\Microsoft\\Active Setup\\Installed Components\\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
Stop-Process -Name Explorer -Force
  ```

    > [!TIP]
    > <span data-ttu-id="5ebd5-140">クリックして[ここでは](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34)この資料ですべての PowerShell コマンドを含むテキスト ファイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-140">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
  - <span data-ttu-id="5ebd5-141">開始] 画面で、[ **Internet Explorer** ] をクリックし、 [https://aka.ms/e5trial](https://aka.ms/e5trial)に移動します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-141">From the Start screen, click **Internet Explorer** and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="5ebd5-142">[**ようこそ、認識するようにするを取得**] ページで次のコマンドを指定します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-142">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="5ebd5-143">所在地</span><span class="sxs-lookup"><span data-stu-id="5ebd5-143">Your physical location</span></span>
    
  - <span data-ttu-id="5ebd5-144">新しい Microsoft アカウントの姓名</span><span class="sxs-lookup"><span data-stu-id="5ebd5-144">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="5ebd5-145">新しい電子メール アドレス</span><span class="sxs-lookup"><span data-stu-id="5ebd5-145">Your new email account address</span></span>
    
  - <span data-ttu-id="5ebd5-146">勤務先電話番号</span><span class="sxs-lookup"><span data-stu-id="5ebd5-146">A business phone number</span></span>
    
  - <span data-ttu-id="5ebd5-147">架空の会社名</span><span class="sxs-lookup"><span data-stu-id="5ebd5-147">Your fictional company name</span></span>
    
  - <span data-ttu-id="5ebd5-148">組織の規模に [250-999 人]</span><span class="sxs-lookup"><span data-stu-id="5ebd5-148">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="5ebd5-149">**1 つ以上のステップ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-149">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="5ebd5-150">**自分のユーザー ID の作成**] ページで、入力、次のように新しいメール アドレス、架空の会社の後にユーザー名、@ 記号 (名にスペースをすべて削除])、し、この新しい Office 365 のアカウント、パスワード (2 回)。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-150">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="5ebd5-151">入力したパスワードを安全な場所に記録してください。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-151">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="5ebd5-152">と**組織名**をここに参照される、架空の会社名を記録する: ___</span><span class="sxs-lookup"><span data-stu-id="5ebd5-152">Record your fictional company name, to be referred to as the **organization name**, here: ________________________________________</span></span>
    
5. <span data-ttu-id="5ebd5-153">**自分のアカウントを作成する**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-153">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="5ebd5-p109">**で次のことを証明します。です。じゃない。A. ロボット**。ページで、テキストに対応した携帯電話の電話番号を入力し、**私のテキスト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="5ebd5-156">受信したテキスト メッセージを検証コードを入力し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-156">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="5ebd5-157">ここにサインイン ページの URL を記録してください (選択してコピー): ___________________________________________</span><span class="sxs-lookup"><span data-stu-id="5ebd5-157">Record the sign-in page URL here (select and copy): ___________________________________________</span></span>
    
9. <span data-ttu-id="5ebd5-158">ここにユーザー IDを記録してください (選択してコピー): __________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5ebd5-158">Record the user ID here (select and copy): __________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="5ebd5-159">この値は、 **Office 365 の管理者がグローバルの名前**と呼びます。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-159">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="5ebd5-160">**移動する準備が整ったら**が表示されたらをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-160">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="5ebd5-161">次のページでは、Office 365 には、上の設定が完了すると、すべてのタイルが使用可能になるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-161">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="5ebd5-162">Office 365 ポータルのメイン ページが表示されます。このページから、Office Online のサービスと Office 365 管理センターにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-162">You should see main Office 365 portal page from which you can access Office Online services and the Office 365 Admin center.</span></span>
  
<span data-ttu-id="5ebd5-163">シミュレーションのエンタープライズ Office 365 開発/テスト環境の、結果として得られる構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-163">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Office 365 開発/テスト環境](images/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="5ebd5-165">この構成は、次の内容で成立します。 </span><span class="sxs-lookup"><span data-stu-id="5ebd5-165">This configuration consists of:</span></span> 
  
- <span data-ttu-id="5ebd5-166">Azure 仮想ネットワークのサブネット上の仮想マシン DC1、APP1、および CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-166">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="5ebd5-167">Office 365 E5 試用版サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-167">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="5ebd5-168">フェーズ 3: Office 365 試用版サブスクリプションを構成する</span><span class="sxs-lookup"><span data-stu-id="5ebd5-168">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="5ebd5-169">このフェーズでは、追加のユーザーと SharePoint Online のチーム サイトで Office 365 のサブスクリプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-169">In this phase, you configure your Office 365 subscription with additional users and SharePoint Online team sites.</span></span>
  
<span data-ttu-id="5ebd5-170">まず、4 人分の新しいユーザーを追加して、E5 ライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-170">First, you add four new users and assign them E5 licenses.</span></span>
  
<span data-ttu-id="5ebd5-171">PowerShell モジュールをインストールしてから新しい Office 365 サービスに接続には、 [Office 365 の PowerShell への接続](https://technet.microsoft.com/library/dn975125.aspx)の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-171">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to install the PowerShell modules and connect to your new Office 365 subscription from:</span></span>
  
- <span data-ttu-id="5ebd5-172">自分のコンピューター (ライトウェイトの Office 365 開発/テスト環境の場合)。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-172">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="5ebd5-173">CLIENT1 仮想マシン (シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合)。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-173">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="5ebd5-174">Windows PowerShell の資格情報の要求] ダイアログ ボックスで、Office 365 グローバル管理者名を入力します (例: jdoe@contosotoycompany.onmicrosoft.com) とパスワードです。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-174">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="5ebd5-175">組織名 (例: contosotoycompany)、所属地域に該当する 2 文字の国別コードを入力して、Windows PowerShell 用 Windows Azure Active Directory モジュールのプロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-175">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "user2@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 2" -FirstName User -LastName 2 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="5ebd5-176">**新しい MsolUser**コマンドの表示から、生成されたアカウントのパスワード、ユーザー 2 に注意してくださいし、安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-176">From the display of the **New-MsolUser** command, note the generated password for the User 2 account and record it in a safe location.</span></span>
  
<span data-ttu-id="5ebd5-177">次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-177">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user3@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 3" -FirstName User -LastName 3 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="5ebd5-178">**新規 MsolUser**コマンドの表示、3 のユーザー アカウントのパスワードが生成されたパスワードを確認し、安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-178">From the display of the **New-MsolUser** command, note the generated password for the User 3 account and record it in a safe location.</span></span>
  
<span data-ttu-id="5ebd5-179">次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-179">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user4@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 4" -FirstName User -LastName 4 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="5ebd5-180">**新しい MsolUser**コマンドの表示、4 のユーザー アカウントのパスワードが生成されたパスワードを確認し、安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-180">From the display of the **New-MsolUser** command, note the generated password for the User 4 account and record it in a safe location.</span></span>
  
<span data-ttu-id="5ebd5-181">次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-181">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "user5@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "User 5" -FirstName User -LastName 5 -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment
```

<span data-ttu-id="5ebd5-182">**新規 MsolUser**コマンドの表示、5 のユーザー アカウントのパスワードが生成されたパスワードを確認し、安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-182">From the display of the **New-MsolUser** command, note the generated password for the User 5 account and record it in a safe location.</span></span>
  
<span data-ttu-id="5ebd5-183">次に、Sales (販売)、Production (生産)、および Support (サポート) の各部門ために、新しい SharePoint Online チーム サイトを 3 つ作成します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-183">Next, you create three new SharePoint Online team sites for the Sales, Production, and Support departments.</span></span>
  
### <a name="create-three-new-sharepoint-online-team-sites"></a><span data-ttu-id="5ebd5-184">新しい SharePoint Online チーム サイトを 3 つ作成する</span><span class="sxs-lookup"><span data-stu-id="5ebd5-184">Create three new SharePoint Online team sites</span></span>

1. <span data-ttu-id="5ebd5-185">[SharePoint のオンライン管理シェル](https://go.microsoft.com/fwlink/p/?LinkId=255251)をインストール (、x64 バージョン)。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-185">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="5ebd5-186">[**スタート**] ボタン、 **sharepoint**を入力し、 **SharePoint のオンライン管理シェル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-186">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="5ebd5-187">組織名 (example: contosotoycompany) を入力し、SharePoint Online Management Shell プロンプトから次に示すコマンドを実行して、SharePoint Online サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-187">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="5ebd5-188">**Microsoft SharePoint のオンライン管理シェル**] ダイアログ ボックスで Office 365 のグローバル管理者名を入力します (例: jdoe@contosotoycompany.onmicrosoft.com) とパスワード、し、[**サインイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-188">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="5ebd5-189">3 つの新しいチーム サイトを作成するのには、Office 365 のグローバル管理者名を入力 (販売、生産、およびサポート)、および SharePoint のオンライン管理シェル プロンプトから以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-189">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="5ebd5-190">このコマンドを実行して、これら 3 つの新しいサイトの URL を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-190">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="5ebd5-191">Internet Explorer で、Production サイトの URL を入力して、Production 部門の既定の SharePoint Online チーム サイトを確認します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-191">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="5ebd5-192">将来の参考のために値を記録する</span><span class="sxs-lookup"><span data-stu-id="5ebd5-192">Record values for future reference</span></span>

<span data-ttu-id="5ebd5-193">この環境で作業する場合や、この環境に追加のテスト ラボ ガイドラインを展開するために、次に示す値を記録しておきます。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-193">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="5ebd5-194">Office 365 全体管理者名: ____________________________________.onmicrosoft.com (フェーズ 2 の手順 9 で入力したもの)</span><span class="sxs-lookup"><span data-stu-id="5ebd5-194">Office 365 global administrator name: ____________________________________.onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="5ebd5-195">このアカウントのパスワードも安全な場所に記録してください。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-195">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="5ebd5-196">試用版サブスクリプションの組織名: _______________________________________________ (フェーズ 2 の手順 4 で入力したもの)</span><span class="sxs-lookup"><span data-stu-id="5ebd5-196">Your trial subscription organization name: _______________________________________________ (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="5ebd5-197">User 2、User 3、User 4、および User 5 のアカウントを一覧表示するには、次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-197">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="5ebd5-198">ここにアカウント名を記録してください:</span><span class="sxs-lookup"><span data-stu-id="5ebd5-198">Record the account names here:</span></span>
    
  - <span data-ttu-id="5ebd5-199">User 2 のアカウント名: user2@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5ebd5-199">User 2 account name: user2@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="5ebd5-200">User 3 のアカウント名: user3@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5ebd5-200">User 3 account name: user3@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="5ebd5-201">User 4 のアカウント名: user4@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5ebd5-201">User 4 account name: user4@_______________________________________________.onmicrosoft.com</span></span>
    
  - <span data-ttu-id="5ebd5-202">User 5 のアカウント名: user5@_______________________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="5ebd5-202">User 5 account name: user5@_______________________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="5ebd5-203">これらのアカウントのパスワードも安全な場所に記録してください。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-203">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="5ebd5-204">Sales、Production、および Support チーム サイトの URL を一覧表示するには、次に示すコマンドを SharePoint Online Management Shell プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-204">To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="5ebd5-205">本番サイトの URL: https://___.sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="5ebd5-205">Production site URL: https://______________________________________________.sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="5ebd5-206">Sales サイトの URL: https://______________________________________________.sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="5ebd5-206">Sales site URL: https://______________________________________________.sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="5ebd5-207">Support サイトの URL: https://______________________________________________.sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="5ebd5-207">Support site URL: https://______________________________________________.sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="5ebd5-208">次の手順</span><span class="sxs-lookup"><span data-stu-id="5ebd5-208">Next steps</span></span>

<span data-ttu-id="5ebd5-209">Office 365 の開発/テスト環境を構築するのに、これらの追加記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-209">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="5ebd5-210">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="5ebd5-210">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5ebd5-211">Office 365 開発/テスト環境用の多要素認証</span><span class="sxs-lookup"><span data-stu-id="5ebd5-211">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5ebd5-212">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="5ebd5-212">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5ebd5-213">Office 365 開発/テスト環境の Cloud App Security</span><span class="sxs-lookup"><span data-stu-id="5ebd5-213">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5ebd5-214">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="5ebd5-214">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5ebd5-215">Office 365 の開発/テスト環境のアドバンスト eDiscovery</span><span class="sxs-lookup"><span data-stu-id="5ebd5-215">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5ebd5-216">Office 365 の開発/テスト環境での機密性の高いファイルの保護</span><span class="sxs-lookup"><span data-stu-id="5ebd5-216">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="5ebd5-217">Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="5ebd5-217">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="5ebd5-218">Office 365 開発/テスト環境でのデータ分類とラベルの作成</span><span class="sxs-lookup"><span data-stu-id="5ebd5-218">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
<span data-ttu-id="5ebd5-219">他の Microsoft クラウド製品を含むように、Office 365 の開発/テスト環境を拡張します。</span><span class="sxs-lookup"><span data-stu-id="5ebd5-219">Extend your Office 365 dev/test environment to include additional Microsoft cloud offerings:</span></span>
  
- [<span data-ttu-id="5ebd5-220">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="5ebd5-220">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
    
- [<span data-ttu-id="5ebd5-221">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="5ebd5-221">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="5ebd5-222">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ebd5-222">See Also</span></span>

[<span data-ttu-id="5ebd5-223">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="5ebd5-223">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="5ebd5-224">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="5ebd5-224">Office 365 and Dynamics 365 dev/test environment</span></span>](office-365-and-dynamics-365-dev-test-environment.md)
  
[<span data-ttu-id="5ebd5-225">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="5ebd5-225">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


