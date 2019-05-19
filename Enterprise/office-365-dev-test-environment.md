---
title: Office 365 開発/テスト環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/02/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 4f6035b8-2da3-4cf9-9657-5284d6364f7a
description: '概要: このテスト ラボ ガイドを使用すると、評価または開発/テスト用の Office 365 試用版サブスクリプションを作成できます。'
ms.openlocfilehash: 2f1856d203e892c98b44ccc1dbe1598d527165de
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "34162510"
---
# <a name="office-365-devtest-environment"></a><span data-ttu-id="d1650-103">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="d1650-103">Office 365 dev/test environment</span></span>

 <span data-ttu-id="d1650-104">**概要:** このテスト ラボ ガイドを使用すると、評価または開発/テスト用の Office 365 試用版サブスクリプションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1650-104">**Summary:** Use this Test Lab Guide to create an Office 365 trial subscription for evaluation or dev/test.</span></span>
  
<span data-ttu-id="d1650-p101">Office 365 試用版サブスクリプションを使用できます。また、アプリケーションの Office 365 開発/テスト環境を作成したり、Office 365 の機能をデモンストレーションすることができます。次の 2 つのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="d1650-p101">You can use an Office 365 trial subscription and create an Office 365 dev/test environment for applications or to demonstrate features and capabilities of Office 365. There are two versions:</span></span>
  
- <span data-ttu-id="d1650-107">軽量の Office 365 開発/テスト環境は、メイン コンピューターからアクセスする Office 365 試用版サブスクリプションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d1650-107">The lightweight Office 365 dev/test environment consists of an Office 365 trial subscription that you access from your main computer.</span></span>
    
    <span data-ttu-id="d1650-p102">機能をすばやくデモンストレーションする場合には、この環境を使用してください。軽量の Office 365 開発/テスト環境の場合は、この記事のフェーズ 2 と 3 のみを完了します。</span><span class="sxs-lookup"><span data-stu-id="d1650-p102">Use this environment when you want to quickly demonstrate a feature. For the lightweight Office 365 dev/test environment, complete only phases 2 and 3 of this article.</span></span>
    
- <span data-ttu-id="d1650-p103">シミュレーションのエンタープライズ Office 365 開発/テスト環境は、Office 365 試用版サブスクリプションと、Microsoft Azure インフラストラクチャ サービスでホストされる、インターネットに接続されたシンプルな組織のイントラネットで構成されています。この構成は Microsoft クラウドで完全に構築できます。</span><span class="sxs-lookup"><span data-stu-id="d1650-p103">The simulated enterprise Office 365 dev/test environment consists of an Office 365 trial subscription and a simplified organization intranet connected to the Internet, which is hosted in Microsoft Azure infrastructure services. You can build this configuration completely in the Microsoft cloud.</span></span>
    
    <span data-ttu-id="d1650-p104">この環境は、インターネットに接続された一般的な組織ネットワークと類似した環境で機能またはアプリをデモンストレーションする場合や、この種類の環境を必要とする機能に使用してください。シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合は、この記事のフェーズ 1、2、3 を完了します。</span><span class="sxs-lookup"><span data-stu-id="d1650-p104">Use this environment when you want to demonstrate a feature or an app in an environment that resembles a typical organization network connected to the Internet, or for features that require this type of environment. For the simulated enterprise Office 365 dev/test environment, complete phases 1, 2, and 3 of this article.</span></span>
    
> [!NOTE]
> <span data-ttu-id="d1650-p105">この記事を印刷しておき、30 日間の Office 365 試用版サブスクリプションの終了後にこの環境で必要になる特定の値を記録しておくことをお勧めします。試用版サブスクリプションは、追加で 30 日間まで簡単に延長できます。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1650-p105">You might want to print this article to record the specific values that you will need for this environment over the 30 days of the Office 365 trial subscription. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
![Microsoft Cloud のテスト ラボ ガイド](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="d1650-118">[ここ](http://aka.ms/catlgstack)をクリックして、Office 365 のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d1650-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-base-configuration-in-azure"></a><span data-ttu-id="d1650-119">フェーズ 1: Azure に基本構成を作成する</span><span class="sxs-lookup"><span data-stu-id="d1650-119">Phase 1: Create the base configuration in Azure</span></span>

<span data-ttu-id="d1650-120">「[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)」の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d1650-120">Follow the instructions in [Base Configuration dev/test environment](base-configuration-dev-test-environment.md).</span></span>
  
<span data-ttu-id="d1650-p106">Azure サブスクリプションが必要になります。この構成には、[Azure の無料試用版](https://azure.microsoft.com/pricing/free-trial/)を使用できます。MSDN や Visual Studio のサブスクリプションを取得している場合は、「[Visual Studio サブスクライバー向けの月単位の Azure クレジット](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1650-p106">You will need an Azure subscription. You can use the [Azure Free Trial](https://azure.microsoft.com/pricing/free-trial/) for this configuration. If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
<span data-ttu-id="d1650-124">最終的な構成は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d1650-124">Here is the resulting configuration.</span></span>
  
![Azure の基本構成開発/テスト環境](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


  
<span data-ttu-id="d1650-126">この構成は、Azure 仮想ネットワーク上の仮想マシン DC1、APP1、および CLIENT1 で成立します。</span><span class="sxs-lookup"><span data-stu-id="d1650-126">This configuration consists of the DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
  
## <a name="phase-2-create-an-office-365-trial-subscription"></a><span data-ttu-id="d1650-127">フェーズ 2:Office 365 試用版サブスクリプションを作成する</span><span class="sxs-lookup"><span data-stu-id="d1650-127">Phase 2: Create an Office 365 trial subscription</span></span>

<span data-ttu-id="d1650-128">Office 365 E5 試用版サブスクリプションを開始するには、最初に、架空の会社名と新しい Microsoft アカウントが必要になります。</span><span class="sxs-lookup"><span data-stu-id="d1650-128">To start your Office 365 E5 trial subscription, you first need a fictitious company name and a new Microsoft account.</span></span>
  
1. <span data-ttu-id="d1650-p107">この会社名には、会社名 Contoso のバリエーションを使用するようお勧めします (必須ではありません)。Contoso は、Microsoft のサンプル コンテンツで使用される架空の会社名です。ここに架空の会社名を記録してください: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="d1650-p107">We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![](./media/Common-Images/TableLine.png)</span></span>
    
2. <span data-ttu-id="d1650-p108">新しい Microsoft アカウントにサインアップするには、[https://outlook.com](https://outlook.com) に移動して、新しい電子メール アカウントとアドレスでアカウントを作成します。このアカウントを使用して、Office 365 にサインアップします。</span><span class="sxs-lookup"><span data-stu-id="d1650-p108">To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.</span></span>
    
  - <span data-ttu-id="d1650-133">ここに新しいアカウントの姓名を記録してください: ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="d1650-133">Record the first and last name of your new account here: ![](./media/Common-Images/TableLine.png)</span></span>
    
  - <span data-ttu-id="d1650-134">ここに新しい電子メール アカウントのアドレスを記録してください: ![](./media/Common-Images/TableLine.png)@outlook.com</span><span class="sxs-lookup"><span data-stu-id="d1650-134">Record the new email account address here: ![](./media/Common-Images/TableLine.png)@outlook.com</span></span>
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a><span data-ttu-id="d1650-135">Office 365 E5 試用版サブスクリプションにサインアップする</span><span class="sxs-lookup"><span data-stu-id="d1650-135">Sign up for an Office 365 E5 trial subscription</span></span>

1. <span data-ttu-id="d1650-136">軽量の Office 365 開発/テスト環境の場合は、自分のコンピューターでブラウザーを起動して、[https://aka.ms/e5trial](https://aka.ms/e5trial) に移動します。</span><span class="sxs-lookup"><span data-stu-id="d1650-136">For the lightweight Office 365 dev/test environment, open the Internet browser on your computer and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span> 
    
    <span data-ttu-id="d1650-137">シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合は、Azure portal から CORP\User1 アカウントを使用して CLIENT1 に接続します。</span><span class="sxs-lookup"><span data-stu-id="d1650-137">For the simulated enterprise Office 365 dev/test environment, connect to CLIENT1 with the CORP\User1 account from the Azure portal.</span></span>

    <span data-ttu-id="d1650-138">スタート画面から Microsoft Edge を起動して、[https://aka.ms/e5trial](https://aka.ms/e5trial) に移動します。</span><span class="sxs-lookup"><span data-stu-id="d1650-138">From the Start screen, run Microsoft Edge and go to [https://aka.ms/e5trial](https://aka.ms/e5trial).</span></span>
    
2. <span data-ttu-id="d1650-139">**[ようこそ、必要事項をご記入ください]** ページで、次に示す項目を指定します。</span><span class="sxs-lookup"><span data-stu-id="d1650-139">On the **Welcome, let's get to know you** page, specify:</span></span>
    
  - <span data-ttu-id="d1650-140">所在地</span><span class="sxs-lookup"><span data-stu-id="d1650-140">Your physical location</span></span>
    
  - <span data-ttu-id="d1650-141">新しい Microsoft アカウントの姓名</span><span class="sxs-lookup"><span data-stu-id="d1650-141">The first and last name of your new Microsoft account</span></span>
    
  - <span data-ttu-id="d1650-142">新しい電子メール アドレス</span><span class="sxs-lookup"><span data-stu-id="d1650-142">Your new email account address</span></span>
    
  - <span data-ttu-id="d1650-143">勤務先電話番号</span><span class="sxs-lookup"><span data-stu-id="d1650-143">A business phone number</span></span>
    
  - <span data-ttu-id="d1650-144">架空の会社名</span><span class="sxs-lookup"><span data-stu-id="d1650-144">Your fictional company name</span></span>
    
  - <span data-ttu-id="d1650-145">組織の規模に [250-999 人]</span><span class="sxs-lookup"><span data-stu-id="d1650-145">An organization size of 250-999 people</span></span>
    
3. <span data-ttu-id="d1650-146">**[手順はあと 1 つだけです]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1650-146">Click **Just one more step**.</span></span>
    
4. <span data-ttu-id="d1650-147">**[ユーザー ID の作成]** ページで、新しい電子メール アドレスに応じたユーザー名を入力し、@ 記号の後に架空の会社名を入力します (名前に含まれる空白はすべて削除します)。次に、この新しい Office 365 アカウントのパスワードを 2 回入力します。 </span><span class="sxs-lookup"><span data-stu-id="d1650-147">On the **Create your user ID** page, type a user name based on your new email address, your fictional company after the @ sign (remove all spaces in the name), then a password (twice) for this new Office 365 account.</span></span>
    
    <span data-ttu-id="d1650-148">入力したパスワードを安全な場所に記録してください。</span><span class="sxs-lookup"><span data-stu-id="d1650-148">Record the password that you typed in a secure location.</span></span>
    
    <span data-ttu-id="d1650-149">架空の会社名を記録してください (この名前を**組織名**と呼ぶことにします): ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="d1650-149">Record your fictional company name, to be referred to as the **organization name**, here: ![](./media/Common-Images/TableLine.png)</span></span>
    
5. <span data-ttu-id="d1650-150">**[アカウントの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1650-150">Click **Create my account**.</span></span>
    
6. <span data-ttu-id="d1650-p109">**[ロボットではないことを証明してください]** ページで、テキスト対応の電話の電話番号を入力して、**[自分にテキスト送信]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1650-p109">On the **Prove. You're. Not. A. Robot.** page, type the phone number of your text-capable phone, and then click **Text me**.</span></span>
    
7. <span data-ttu-id="d1650-153">受信したテキスト メッセージの認証コードを入力して、**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1650-153">Type the verification code from the received text message, and then click **Next**.</span></span>
    
8. <span data-ttu-id="d1650-154">ここにサインイン ページの URL を記録してください (選択してコピー): ![](./media/Common-Images/TableLine.png)</span><span class="sxs-lookup"><span data-stu-id="d1650-154">Record the sign-in page URL here (select and copy): ![](./media/Common-Images/TableLine.png)</span></span>
    
9. <span data-ttu-id="d1650-155">ここにユーザー ID を記録してください (選択してコピー): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="d1650-155">Record the user ID here (select and copy): ![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="d1650-156">この値を**Office 365 全体管理者名**と呼ぶことにします。</span><span class="sxs-lookup"><span data-stu-id="d1650-156">This value will be referred to as the **Office 365 global administrator name**.</span></span>
    
10. <span data-ttu-id="d1650-157">**[準備が整いました]** が表示されたら、その表示をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1650-157">When you see **You're ready to go**, click it.</span></span>
    
11. <span data-ttu-id="d1650-158">次のページで、Office 365 のセットアップが完了して、すべてのタイルが使用できるようになるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="d1650-158">On the next page, wait until Office 365 completes setting up and all the tiles are available.</span></span>
    
<span data-ttu-id="d1650-159">Office 365 ポータルのメイン ページが表示されます。このページから、Office Online のサービスと Microsoft 365 管理センターにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d1650-159">You should see main Office 365 portal page from which you can access Office Online services and the Microsoft 365 Admin center.</span></span>
  
<span data-ttu-id="d1650-160">シミュレーションのエンタープライズ Office 365 開発/テスト環境の、最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="d1650-160">For the simulated enterprise Office 365 dev/test environment, here is your resulting configuration.</span></span>
  
![Office 365 開発/テスト環境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
<span data-ttu-id="d1650-162">この構成は、次の内容で成立します。</span><span class="sxs-lookup"><span data-stu-id="d1650-162">This configuration consists of:</span></span> 
  
- <span data-ttu-id="d1650-163">Azure 仮想ネットワークのサブネット上の仮想マシン DC1、APP1、および CLIENT1。</span><span class="sxs-lookup"><span data-stu-id="d1650-163">The DC1, APP1, and CLIENT1 virtual machines on a subnet of an Azure virtual network.</span></span>
    
- <span data-ttu-id="d1650-164">Office 365 E5 試用版サブスクリプション。</span><span class="sxs-lookup"><span data-stu-id="d1650-164">An Office 365 E5 Trial Subscription.</span></span>
    
## <a name="phase-3-configure-your-office-365-trial-subscription"></a><span data-ttu-id="d1650-165">フェーズ 3: Office 365 試用版サブスクリプションを構成する</span><span class="sxs-lookup"><span data-stu-id="d1650-165">Phase 3: Configure your Office 365 trial subscription</span></span>

<span data-ttu-id="d1650-166">このフェーズでは、追加のユーザーで Office 365 のサブスクリプションを構成し、Office 365 E5 ライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d1650-166">In this phase, you configure your Office 365 subscription with additional users and assign them Office 365 E5 licenses.</span></span>
  
<span data-ttu-id="d1650-167">[「Office 365 PowerShell への接続」](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module)の手順を使用して、Azure Active Directory PowerShell for Graph モジュールで Office 365 のサブスクリプションに接続します。</span><span class="sxs-lookup"><span data-stu-id="d1650-167">Use the instructions in [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) to connect to your Office 365 subscription with the Azure Active Directory PowerShell for Graph module from:</span></span>
  
- <span data-ttu-id="d1650-168">自分のコンピューター (軽量の Office 365 開発/テスト環境の場合)。</span><span class="sxs-lookup"><span data-stu-id="d1650-168">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="d1650-169">CLIENT1 仮想マシン (シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合)。</span><span class="sxs-lookup"><span data-stu-id="d1650-169">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
 <span data-ttu-id="d1650-170">[Windows PowerShell 資格情報の要求] ダイアログ ボックスで、Office 365 全体管理者名 (例: jdoe@contosotoycompany.onmicrosoft.com) とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="d1650-170">In the Windows PowerShell Credential Request dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password.</span></span>
  
<span data-ttu-id="d1650-171">組織名 (例: contosotoycompany)、所属地域に該当する 2 文字の国別コード、共通のアカウント パスワードを入力して、PowerShellのプロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d1650-171">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, a common account password, and then run the following commands from the PowerShell prompt:</span></span>

```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

<!--
> [!TIP]
> Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-fe3d7a34) to get a text file that has all the PowerShell commands in this article.
-->

  
## <a name="phase-4-create-three-new-sharepoint-online-team-sites-optional"></a><span data-ttu-id="d1650-172">フェーズ 4: 新しい SharePoint Online チーム サイトを 3 つ作成する (省略可能)</span><span class="sxs-lookup"><span data-stu-id="d1650-172">Phase 4: Create three new SharePoint Online team sites (optional)</span></span>

<span data-ttu-id="d1650-173">このフェーズでは、一連の SharePoint Online チーム サイトを構成します。</span><span class="sxs-lookup"><span data-stu-id="d1650-173">In this phase, you configure a set of SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="d1650-174">[SharePoint Online 管理シェル](https://go.microsoft.com/fwlink/p/?LinkId=255251) (x64 バージョン) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="d1650-174">Install the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) (the x64 version).</span></span>
    
2. <span data-ttu-id="d1650-175">**[スタート]** をクリックし、「**sharepoint**」と入力してから、**[SharePoint Online 管理シェル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1650-175">Click **Start**, type **sharepoint**, and then click **SharePoint Online Management Shell**.</span></span>
    
3. <span data-ttu-id="d1650-176">組織名 (example: contosotoycompany) を入力し、SharePoint Online Management Shell プロンプトから次に示すコマンドを実行して、SharePoint Online サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d1650-176">Fill in your organization name (example: contosotoycompany), and then run the following commands from the SharePoint Online Management Shell prompt to connect to the SharePoint Online service</span></span>
```
$orgName="<organization name>"
$spURL="https://" + $orgName + "-admin.sharepoint.com"
Connect-SPOService -Url $spURL
```

4. <span data-ttu-id="d1650-177">**[Microsoft Office SharePoint Online 管理シェル]** ダイアログ ボックスで、Office 365 全体管理者名 (例: jdoe@contosotoycompany.onmicrosoft.com) とパスワードを入力してから、**[サインイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d1650-177">In the **Microsoft SharePoint Online Management Shell** dialog box, type the Office 365 global administrator name (example: jdoe@contosotoycompany.onmicrosoft.com) and password, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="d1650-178">新しい 3 つのチーム サイト (Sales、Production、および Support) を作成するには、Office 365 全体管理者名を入力して、SharePoint Online Management Shell プロンプトから次に示すコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d1650-178">To create three new team sites (Sales, Production, and Support), fill in the Office 365 global administrator name, and then run the following commands from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  $owner = "<global administrator account name>"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/sales"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Sales site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/production"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Production site collection" -Template "STS#0"
$siteURL = "https://" + $orgName + ".sharepoint.com/sites/support"
New-SPOSite -Url $siteURL -Owner $owner -StorageQuota 1000 -Title "Support site collection" -Template "STS#0"
  ```

6. <span data-ttu-id="d1650-179">このコマンドを実行して、これら 3 つの新しいサイトの URL を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d1650-179">Run this command to list the URLs of these new sites:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

7. <span data-ttu-id="d1650-180">Internet Explorer で、Production サイトの URL を入力して、Production 部門の既定の SharePoint Online チーム サイトを確認します。</span><span class="sxs-lookup"><span data-stu-id="d1650-180">In Internet Explorer, enter the URL of the Production site to see the default SharePoint Online team site for the Production department.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="d1650-181">将来の参考のために値を記録する</span><span class="sxs-lookup"><span data-stu-id="d1650-181">Record values for future reference</span></span>

<span data-ttu-id="d1650-182">この環境で作業する場合や、この環境に追加のテスト ラボ ガイドラインを展開するために、次に示す値を記録しておきます。</span><span class="sxs-lookup"><span data-stu-id="d1650-182">Record these values for working with or deploying additional Test Lab Guides in this test environment:</span></span>
  
- <span data-ttu-id="d1650-183">Office 365 全体管理者名: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (フェーズ 2 の手順 9 で入力したもの)</span><span class="sxs-lookup"><span data-stu-id="d1650-183">Office 365 global administrator name: ![](./media/Common-Images/TableLine.png).onmicrosoft.com (from step 9 of Phase 2)</span></span>
    
    <span data-ttu-id="d1650-184">このアカウントのパスワードも安全な場所に記録してください。</span><span class="sxs-lookup"><span data-stu-id="d1650-184">Also record the password for this account in a secure location.</span></span>
    
- <span data-ttu-id="d1650-185">試用版サブスクリプションの組織名: ![](./media/Common-Images/TableLine.png) (フェーズ 2 の手順 4 で入力したもの)</span><span class="sxs-lookup"><span data-stu-id="d1650-185">Your trial subscription organization name: ![](./media/Common-Images/TableLine.png) (from step 4 of Phase 2)</span></span>
    
- <span data-ttu-id="d1650-186">User 2、User 3、User 4、および User 5 のアカウントを一覧表示するには、次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="d1650-186">To list the accounts for User 2, User 3, User 4, and User 5, run the following command from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
    
  ```
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    <span data-ttu-id="d1650-187">ここにアカウント名を記録してください:</span><span class="sxs-lookup"><span data-stu-id="d1650-187">Record the account names here:</span></span>
    
  - <span data-ttu-id="d1650-188">User 2 のアカウント名: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="d1650-188">User 2 account name: user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="d1650-189">User 3 のアカウント名: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="d1650-189">User 3 account name: user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="d1650-190">User 4 のアカウント名: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="d1650-190">User 4 account name: user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
  - <span data-ttu-id="d1650-191">User 5 のアカウント名: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="d1650-191">User 5 account name: user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com</span></span>
    
    <span data-ttu-id="d1650-192">これらのアカウントのパスワードも安全な場所に記録してください。</span><span class="sxs-lookup"><span data-stu-id="d1650-192">Also record the passwords for these accounts in a secure location.</span></span>
    
- <span data-ttu-id="d1650-193">(省略可能) Sales、Production、および Support チーム サイトの URL を一覧表示するには、次に示すコマンドを SharePoint Online 管理シェル プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="d1650-193">(optional) To list the URLs for the Sales, Production, and Support team sites, run the following command from the SharePoint Online Management Shell prompt:</span></span>
    
  ```
  Get-SPOSite | Where URL -like "*/sites/*" | Sort URL | Select URL
  ```

  - <span data-ttu-id="d1650-194">Production サイトの URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span><span class="sxs-lookup"><span data-stu-id="d1650-194">Production site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/production</span></span>
    
  - <span data-ttu-id="d1650-195">Sales サイトの URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span><span class="sxs-lookup"><span data-stu-id="d1650-195">Sales site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/sales</span></span>
    
  - <span data-ttu-id="d1650-196">Support サイトの URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span><span class="sxs-lookup"><span data-stu-id="d1650-196">Support site URL: https://![](./media/Common-Images/TableLine.png).sharepoint.com/sites/support</span></span>
    
## <a name="next-steps"></a><span data-ttu-id="d1650-197">次の手順</span><span class="sxs-lookup"><span data-stu-id="d1650-197">Next steps</span></span>

<span data-ttu-id="d1650-198">この Office 365 開発/テスト環境に、次の追加記事を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1650-198">Use these additional articles in your Office 365 dev/test environment:</span></span>
  
- [<span data-ttu-id="d1650-199">Office 365 開発/テスト環境のディレクトリ同期</span><span class="sxs-lookup"><span data-stu-id="d1650-199">Directory Synchronization for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="d1650-200">Office 365 開発/テスト環境用の多要素認証</span><span class="sxs-lookup"><span data-stu-id="d1650-200">Multi-factor authentication for your Office 365 dev/test environment</span></span>](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="d1650-201">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="d1650-201">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="d1650-202">Office 365 開発/テスト環境の Advanced Threat Protection</span><span class="sxs-lookup"><span data-stu-id="d1650-202">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="d1650-203">Office 365 の開発/テスト環境の Advanced eDiscovery</span><span class="sxs-lookup"><span data-stu-id="d1650-203">Advanced eDiscovery for your Office 365 dev/test environment</span></span>](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="d1650-204">Office 365 の開発/テスト環境での機密性の高いファイルの保護</span><span class="sxs-lookup"><span data-stu-id="d1650-204">Sensitive file protection in the Office 365 dev/test environment</span></span>](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
- [<span data-ttu-id="d1650-205">Office 365 開発/テスト環境での分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="d1650-205">Isolated SharePoint Online team site dev/test environment</span></span>](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
- [<span data-ttu-id="d1650-206">Office 365 開発/テスト環境でのデータ分類とラベルの作成</span><span class="sxs-lookup"><span data-stu-id="d1650-206">Data classification and labeling in the Office 365 dev/test environment</span></span>](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
## <a name="see-also"></a><span data-ttu-id="d1650-207">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1650-207">See Also</span></span>

- [<span data-ttu-id="d1650-208">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="d1650-208">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
- [<span data-ttu-id="d1650-209">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="d1650-209">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


