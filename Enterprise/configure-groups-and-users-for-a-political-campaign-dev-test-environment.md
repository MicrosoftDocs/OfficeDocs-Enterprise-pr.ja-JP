---
title: 選挙運動の開発/テスト環境用にグループとユーザーを構成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 0e22bcf3-bad3-42a4-b44f-276e0cf4790f
description: '要約: 選挙運動の開発/テスト環境向けのユーザーとグループで Office 365 と Enterprise Mobility + Security (EMS) の試用版サブスクリプションを作成します。'
ms.openlocfilehash: 8556040a648937d4c1bc338292be121e5d290dd9
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="configure-groups-and-users-for-a-political-campaign-devtest-environment"></a><span data-ttu-id="b030c-103">選挙運動の開発/テスト環境用にグループとユーザーを構成する</span><span class="sxs-lookup"><span data-stu-id="b030c-103">Configure groups and users for a political campaign dev/test environment</span></span>

 <span data-ttu-id="b030c-104">**要約:** 選挙運動の開発/テスト環境向けのユーザーとグループで Office 365 と Enterprise Mobility + Security (EMS) の試用版サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b030c-104">**Summary:** Create Office 365 and Enterprise Mobility + Security (EMS) trial subscriptions with users and groups for a political campaign dev/test environment.</span></span>
  
<span data-ttu-id="b030c-105">簡略化されたユーザー アカウントとグループを含む開発/テスト環境を「[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)」ソリューション用に作成するには、この資料の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="b030c-105">Use the instructions in this article to create a dev/test environment that includes simplified user accounts and groups   for the [Microsoft Security Guidance for Political Campaigns, Nonprofit Organizations, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution.</span></span>
  
## <a name="phase-1-create-your-office-365-devtest-environment"></a><span data-ttu-id="b030c-106">フェーズ 1: Office 365 の開発/テスト環境を作成する</span><span class="sxs-lookup"><span data-stu-id="b030c-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="b030c-107">このフェーズでは、選挙運動を務める架空の組織用に Office 365 E5 と Enterprise Mobility + Security (EMS) E5 の試用版サブスクリプションを取得します。</span><span class="sxs-lookup"><span data-stu-id="b030c-107">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="b030c-108">まず、「[Office 365 開発/テスト環境](office-365-dev-test-environment.md)」の**フェーズ 2**に記されている手順を実行します</span><span class="sxs-lookup"><span data-stu-id="b030c-108">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="b030c-109">次に、EMS E5 試用版サブスクリプションにサインアップして、Office 365 試用版サブスクリプションと同じ組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="b030c-109">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="b030c-p101">必要に応じて、Office 365 ポータルに、試用版サブスクリプション用の全体管理者アカウントの資格情報でサインインします。ヘルプについては、「[一般法人向け Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b030c-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="b030c-112">
            **[管理]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-112">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="b030c-113">ブラウザーの **[Office 管理センター]** タブの左側のナビゲーションで **[請求] > [サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-113">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="b030c-p102">**[サービスを購入]** ページで、 **[Enterprise Mobility + Security E5]** 項目を探します。その項目の上にマウス ポインターを移動させ、 **[無料試用版を起動する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="b030c-116">**[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-116">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="b030c-117">**[注文の受領書]** ページで、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-117">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="b030c-118">次に、全体管理者アカウントの EMS E5 ライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b030c-118">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="b030c-119">ブラウザーの **[Office 365 管理センター]** タブの左側のナビゲーションで **[ユーザー] > [アクティブなユーザー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-119">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="b030c-120">全体管理者アカウントをクリックしてから、 **[製品ライセンス]** で **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-120">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="b030c-121">**[製品ライセンス]** ウィンドウで、 **Enterprise Mobility + Security E5** の製品ライセンスを **[オン]** にして、 **[保存]** をクリックしてから、 **[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-121">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups"></a><span data-ttu-id="b030c-122">フェーズ 2: Azure Active Directory (AD) グループを作成して構成する</span><span class="sxs-lookup"><span data-stu-id="b030c-122">Phase 2: Create and configure your Azure Active Directory (AD) groups</span></span>

<span data-ttu-id="b030c-123">このフェーズでは、選挙運動用に Azure AD グループを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="b030c-123">In this phase, you create and configure the Azure AD groups for your campaign.</span></span>
  
<span data-ttu-id="b030c-124">最初に、Azure portal で一般的な選挙運動グループのセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="b030c-124">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="b030c-125">ブラウザーの別タブで、Azure portal ([https://portal.azure.com](https://portal.azure.com)) に移動します。必要に応じて、Office 365 E5 試用版サブスクリプション用の全体管理者アカウントの資格情報でサインインします。</span><span class="sxs-lookup"><span data-stu-id="b030c-125">Create a separate tab in your browser, and then go to the Azure portal at https://portal.azure.com. If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="b030c-126">Azure portal で **[Azure Active Directory] > [ユーザーとグループ] > [すべてのグループ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-126">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="b030c-127">このリストのグループ名ごとに、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b030c-127">Do the following steps for each group name in this list:</span></span>
    
  - <span data-ttu-id="b030c-128">戦略的シニア スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-128">Senior and strategic staff</span></span>
    
  - <span data-ttu-id="b030c-129">IT スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-129">IT staff</span></span>
    
  - <span data-ttu-id="b030c-130">分析スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-130">Analytics staff</span></span>
    
  - <span data-ttu-id="b030c-131">正規のコア スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-131">Regular core staff</span></span>
    
  - <span data-ttu-id="b030c-132">運用スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-132">Operations staff</span></span>
    
  - <span data-ttu-id="b030c-133">フィールド スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-133">Field staff</span></span>
    
1. <span data-ttu-id="b030c-134">**[すべてのグループ]** ブレードで、**[+ 新しいグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-134">On the **All groups** blade, click **+ New group**.</span></span>
    
2. <span data-ttu-id="b030c-135">リストにあるグループ名を **[名前]** に入力します。</span><span class="sxs-lookup"><span data-stu-id="b030c-135">Type the group name from the list in **Name**.</span></span>
    
3. <span data-ttu-id="b030c-136">**[メンバーシップ]** で **[動的ユーザー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b030c-136">Select **Dynamic user** in **Membership**.</span></span>
    
4. <span data-ttu-id="b030c-137">**[Office の機能を有効にする]** で **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-137">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="b030c-138">**[動的クエリの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-138">Click **Add dynamic query**.</span></span>
    
6. <span data-ttu-id="b030c-139">**[ユーザーを追加する場所]** で、**[部署]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b030c-139">In **Add users where**, select **department**.</span></span>
    
7. <span data-ttu-id="b030c-140">次のフィールドで、**[等しい]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b030c-140">In the next field, select **Equals**.</span></span>
    
8. <span data-ttu-id="b030c-141">次のフィールドで、リストにあるグループ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="b030c-141">In the next field, type the group name from the list.</span></span>
    
9. <span data-ttu-id="b030c-142">**[クエリの追加]** をクリックしてから、**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-142">Click **Add**, and then click **OK**.</span></span>
    
10. <span data-ttu-id="b030c-143">**[ユーザーとグループ - すべてのグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-143">Click **Users and groups - All groups**.</span></span>
    
<span data-ttu-id="b030c-144">次に、メンバーに Office 365 E5 および EMS E5 のライセンスが自動的に割り当てられるようにグループを構成します。</span><span class="sxs-lookup"><span data-stu-id="b030c-144">Next, you configure the groups so that members are automatically assigned Office 365 E5 and EMS E5 licenses.</span></span>
  
1. <span data-ttu-id="b030c-145">Azure portal で **[Azure Active Directory] > [ライセンス] > [すべての製品]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-145">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="b030c-146">一覧で、**[Enterprise Mobility + Security E5]** と **[Office 365 Enterprise E5]** を選択して、**[+ 割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-146">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="b030c-147">**[ライセンスの割り当て]** ブレードで、**[ユーザーとグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-147">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="b030c-148">グループの一覧で、次を選択します。</span><span class="sxs-lookup"><span data-stu-id="b030c-148">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="b030c-149">分析スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-149">Analytics staff</span></span>
    
  - <span data-ttu-id="b030c-150">フィールド スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-150">Field staff</span></span>
    
  - <span data-ttu-id="b030c-151">IT スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-151">IT staff</span></span>
    
  - <span data-ttu-id="b030c-152">運用スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-152">Operations staff</span></span>
    
  - <span data-ttu-id="b030c-153">正規のコア スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-153">Regular core staff</span></span>
    
  - <span data-ttu-id="b030c-154">戦略的シニア スタッフ</span><span class="sxs-lookup"><span data-stu-id="b030c-154">Senior and strategic staff</span></span>
    
5. <span data-ttu-id="b030c-155">**[選択]** をクリックし、**[割り当て]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-155">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="b030c-156">ブラウザーの [Azure Portal] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b030c-156">Close the Azure portal tab in your browser.</span></span>
    
## <a name="phase-3-add-your-user-accounts"></a><span data-ttu-id="b030c-157">フェーズ 3:ユーザー アカウントを追加する</span><span class="sxs-lookup"><span data-stu-id="b030c-157">Phase 3: Add your user accounts</span></span>

<span data-ttu-id="b030c-158">このフェーズでは、選挙運動のサンプル ユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="b030c-158">In this phase, you add the example user accounts for your political campaign.</span></span>
  
<span data-ttu-id="b030c-159">まず、[Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)します。</span><span class="sxs-lookup"><span data-stu-id="b030c-159">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="b030c-160">次に、組織名、場所、および共通のパスワードを入力し、PowerShell コマンド プロンプトまたは Integrated Scripting Environment (ISE) からこれらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b030c-160">Next, you fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE):</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$deptName="Senior and strategic staff"
$userNames=@("Candidate","ChiefOfStaff","Strategic1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Analytics staff"
$userNames=@("DataScientist1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Regular core staff"
$userNames=@("Regular1","Regular2") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Operations staff"
$userNames=@("Operations1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }
$deptName="Field staff"
$userNames=@("FieldConsultant1") 
foreach ($element in $userNames){ New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -Department $deptName -UsageLocation $location }

```

> [!IMPORTANT]
> <span data-ttu-id="b030c-p103">ここでは共通のパスワードを使用することで、自動化と、開発/テスト環境の構成を容易にしています。運用サブスクリプションでの使用はお勧めしません。これらの新しいユーザー アカウントでサインインするときに、パスワードの変更を求めるダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b030c-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions. As you sign in with each of these new user accounts, you will be prompted to change the password.</span></span> 
  
<span data-ttu-id="b030c-164">動的グループのメンバーシップとグループ ベースのライセンスが正常に機能していることを確認するには、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="b030c-164">Use these steps to verify that dynamic group membership and group-based licensing are working correctly.</span></span>
  
1. <span data-ttu-id="b030c-165">ブラウザーの **[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-165">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="b030c-166">ブラウザーの新しい **Office 管理センター**のタブで、**[ユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-166">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="b030c-167">ユーザーの一覧で **[候補]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b030c-167">In the list of users, click **Candidate**.</span></span>
    
4. <span data-ttu-id="b030c-168">**[候補]** ユーザー アカウントのプロパティを一覧表示するウィンドウで、次を確認します。</span><span class="sxs-lookup"><span data-stu-id="b030c-168">In the pane that lists the properties of the **Candidate** user account, verify that:</span></span>
    
  - <span data-ttu-id="b030c-169">**[戦略的シニア スタッフ]** グループのメンバーである (**[グループ メンバーシップ]** 内)。</span><span class="sxs-lookup"><span data-stu-id="b030c-169">It is a member of the **Senior and strategic staff** group (in **Group memberships**).</span></span>
    
  - <span data-ttu-id="b030c-170">**[Enterprise Mobility + Security E5]** と **[Office 365 Enterprise E5]** のライセンスが割り当てられている (**[製品ライセンス]** 内)。</span><span class="sxs-lookup"><span data-stu-id="b030c-170">It has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
5. <span data-ttu-id="b030c-171">**[候補]** ユーザー アカウントのウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b030c-171">Close the **Candidate** user account pane.</span></span>
    
## <a name="record-values-for-future-reference"></a><span data-ttu-id="b030c-172">将来の参考のために値を記録する</span><span class="sxs-lookup"><span data-stu-id="b030c-172">Record values for future reference</span></span>

<span data-ttu-id="b030c-173">この開発/テスト環境で Office 365 と EMS の試用版サブスクリプションを使用するために、これらの値を記録します。</span><span class="sxs-lookup"><span data-stu-id="b030c-173">Record these values for working with the Office 365 and EMS trial subscriptions for this dev/test environment:</span></span>
  
- <span data-ttu-id="b030c-174">試用版サブスクリプションの組織名: _______________________________________________。</span><span class="sxs-lookup"><span data-stu-id="b030c-174">Your trial subscription organization name: _______________________________________________</span></span> 
    
    <span data-ttu-id="b030c-175">たとえば、試用版サブスクリプションのドメイン名 contoso.onmicrosoft.com の場合、組織名は "contoso" です。</span><span class="sxs-lookup"><span data-stu-id="b030c-175">For example, for the trial subscription domain name of contoso.onmicrosoft.com, the organization name is "contoso".</span></span>
    
- <span data-ttu-id="b030c-176">Office 365 グローバル管理者名: ____________________________________.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="b030c-176">Office 365 global administrator name: ____________________________________.onmicrosoft.com</span></span>
    
    <span data-ttu-id="b030c-177">このアカウントのパスワードや、その他のユーザー アカウントの共通のパスワードを安全な場所に記録します。</span><span class="sxs-lookup"><span data-stu-id="b030c-177">Record the password for this account and the common password for the other user accounts in a secure location.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="b030c-178">次の手順</span><span class="sxs-lookup"><span data-stu-id="b030c-178">Next step</span></span>

<span data-ttu-id="b030c-179">[Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md) を使用して、この開発/テスト環境で 4 つの異なる種類の SharePoint Online チーム サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b030c-179">Build the four different types of SharePoint Online team sites in this dev/test environment with [Create team sites in a political campaign dev/test environment](create-team-sites-in-a-political-campaign-dev-test-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b030c-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="b030c-180">See Also</span></span>

[<span data-ttu-id="b030c-181">選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス</span><span class="sxs-lookup"><span data-stu-id="b030c-181">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="b030c-182">選挙運動用の開発/テスト環境でチーム サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="b030c-182">Create team sites in a political campaign dev/test environment</span></span>](create-team-sites-in-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="b030c-183">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="b030c-183">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="b030c-184">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="b030c-184">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




