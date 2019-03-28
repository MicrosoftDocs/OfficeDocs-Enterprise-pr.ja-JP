---
title: Office 365 と Dynamics 365 の開発/テスト環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: '概要: このテスト ラボ ガイドを使用して、Dynamics 365 を Office 365 開発/テスト環境に追加します。'
ms.openlocfilehash: 9e4c98129c68ab5d2f0d9fc486ab62740c625af5
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "30574061"
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="e5d9b-103">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="e5d9b-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="e5d9b-104">**概要:** このテスト ラボ ガイドを使用して、Dynamics 365 を Office 365 開発/テスト環境に追加します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="e5d9b-105">この記事の手順を使用して、Dynamics 365 試用版サブスクリプションを Office 365 開発/テスト環境と同じ組織に追加し、Office 365 と Dynamics 365 の開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>

![Office 365 と Dynamics 365 の開発/テスト環境](media/o365-dynamics365-dev-test.png)
  
  
<span data-ttu-id="e5d9b-p101">Dynamics 365 試用版サブスクリプションを使用して、Dynamics 365 の機能をデモンストレーションすることができます。Dynamics 365 プラン 1、Enterprise Edition 試用版には、以下のソリューションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="e5d9b-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales)。営業担当者が専念して、効率的に業務を行えるようするオートメーションとデジタル インテリジェンスを使用して、売り上げを増加させます。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="e5d9b-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service)。シームレスなサービスの提供に必要な詳細な情報とデジタル インテリジェンスをエージェントに提供することで、ロイヤルティを獲得します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="e5d9b-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service)。スケジュールの最適化、人員の配置、および利益を向上させる予測ツールの使用により、保守サービスの訪問を有効活用します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="e5d9b-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/ja-JP/dynamics365/project-service-automation)。プロジェクトを成功裏に完了させ、生産性の高い従業員とインテリジェント ツールとの利益をもたらすリレーションシップを構築します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/ja-JP/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="e5d9b-117">Dynamics 365 試用版サブスクリプションでは、上記の 1 つ以上をお試しいただけます。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-117">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Microsoft Cloud のテスト ラボ ガイド](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="e5d9b-119">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-119">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="e5d9b-120">フェーズ 1: ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する</span><span class="sxs-lookup"><span data-stu-id="e5d9b-120">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="e5d9b-121">最小要件で、負荷の小さい方法で Office 365 と Dynamics 365 をテストする場合は、[Office 365 開発/テスト環境](office-365-dev-test-environment.md) のフェーズ 2 とフェーズ 3 の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-121">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="e5d9b-122">シミュレーションのエンタープライズの Office 365 と Dynamics 365 をテストする場合は、[Office 365 Dev/Test Environment 用の DirSync](dirsync-for-your-office-365-dev-test-environment.md) の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-122">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>

![Office 365 開発/テスト環境](media/48fb91aa-09b0-4020-a496-a8253920c45d.png)
  
> [!NOTE]
> <span data-ttu-id="e5d9b-p106">この記事の構成には、シミュレーションのエンタープライズ開発/テスト環境は必要ありません。シミュレーションのエンタープライズ開発/テスト環境には、インターネットに接続されたシミュレーションのイントラネット、Windows サーバー AD フォレスト用のディレクトリ同期が含まれています。この機能は、一般的な組織と類似した環境で Office 365 と Dynamics 365 を試していただけるようオプションとしてここで提供されています。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="e5d9b-126">フェーズ 2:Dynamics 365 試用版サブスクリプションを追加する</span><span class="sxs-lookup"><span data-stu-id="e5d9b-126">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="e5d9b-127">このフェーズでは、Office 365 試用版サブスクリプションにサインアップして、Office 365 試用版サブスクリプションと同じ組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-127">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="e5d9b-128">Dynamics 365 試用版サブスクリプションにサインアップする</span><span class="sxs-lookup"><span data-stu-id="e5d9b-128">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="e5d9b-129">デスクトップ コンピューター (ライトウェイト) のブラウザーまたは CLIENT1 (シミュレーションのエンタープライズ) のブラウザーのいずれかを使用して、全体管理者アカウントの資格情報で Microsoft 365 管理センター ([https://admin.microsoft.com](https://admin.microsoft.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-129">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://admin.microsoft.com](https://admin.microsoft.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="e5d9b-130">**[管理]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-130">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="e5d9b-131">**[Microsoft 365 管理センター]** タブの左側のナビゲーションで **[請求]、[サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-131">On the **Microsoft 365 admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="e5d9b-p107">**[サービスを購入]** ページで、**[Dynamics 365 プラン 1 Enterprise Edition]** の項目を探します。その項目の上にマウス ポインターを移動させ、**[無料試用版を起動する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="e5d9b-134">**[注文の確認]** ページで、**[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-134">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="e5d9b-135">**[注文の受領書]** ページで、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-135">On the **Order receipt** page, click **Continue**.</span></span>

![Office 365 と Dynamics 365 の開発/テスト環境](media/o365-dynamics365-dev-test.png)
    
> [!NOTE]
> <span data-ttu-id="e5d9b-p108">Dynamics 365 Plan 1 Enterprise Edition の試用版サブスクリプションは 30 日間有効です。試用版サブスクリプションは、追加で 30 日間まで簡単に延長できます。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="e5d9b-140">フェーズ 3：Dynamics 365 ライセンスとシステム管理者を割り当てる</span><span class="sxs-lookup"><span data-stu-id="e5d9b-140">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="e5d9b-141">このフェーズでは、Dynamics 365 ライセンスをグローバル管理者、User 2、User 3 のアカウントに割り当て、システム管理者とします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-141">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="e5d9b-142">Dynamics 365 ライセンスを割り当てるには次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-142">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="e5d9b-143">**[Microsoft 365 管理センター]** タブで **[ユーザー]、[アクティブなユーザー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-143">On the **Microsoft 365 admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="e5d9b-144">アクティブ ユーザーの一覧で、全体管理者アカウントを選択し、**[製品ライセンス]** で **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-144">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="e5d9b-145">**[製品ライセンス]** ウィンドウで、**Dynamics 365 プラン 1 Enterprise Edition** の製品ライセンスを **[オン]** にして、**[保存]** をクリックし、**[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-145">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="e5d9b-146">User 2 と User 3 のアカウントに対して、手順 2 と 3 を実行します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-146">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="e5d9b-147">**[Microsoft 365 管理センター]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-147">Close the **Microsoft 365 admin center** tab.</span></span>
    
<span data-ttu-id="e5d9b-148">次の手順を使用して、Dynamics 365 のシステム管理者として User 2 と User 3 のアカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-148">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="e5d9b-149">**[Microsoft Office Home]** タブで、**[管理者]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-149">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="e5d9b-150">**[Office 管理センター]** タブで、左側のナビゲーションで **[管理センター]** をクリックして、**[Dynamics 365]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-150">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="e5d9b-151">Dynamics 365 がメニューに表示されるまで、Dynamics 365 のプロビジョニングの完了を待つ必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-151">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="e5d9b-152">[Dynamics 365] タブで、**[これらのすべて]**、**[セットアップの完了]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-152">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="e5d9b-153">セットアップが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-153">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="e5d9b-p109">セットアップが完了すると、試用版サブスクリプションの一部であるサンプル データに基づいて営業活動ダッシュボードが表示されます。**[試用版へようこそ]** の数分のビデオをご覧ください。終了したら、ビデオ ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="e5d9b-157">上部のツールバーで、**[営業]** の横にある下矢印をクリックし、**[設定]**、**[セキュリティ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-157">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="e5d9b-158">**[セキュリティ]** ページで **[ユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-158">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="e5d9b-159">ユーザーの一覧で **[User 2]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-159">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="e5d9b-160">ツール バーで、**[ロールの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-160">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="e5d9b-161">**[ロールの管理]** で、**[システム管理者]**、**[OK]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-161">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="e5d9b-162">上部のツールバーで **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-162">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="e5d9b-163">User 3 アカウントについて、手順 5 から 8 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-163">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="e5d9b-164">**[ユーザー： User3]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-164">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="e5d9b-165">Office 365 全体管理者アカウントに、Dynamics 365 のシステム管理者ロールが自動的に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-165">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="e5d9b-166">この段階で、Office 365 と Dynamics 365 の開発/テスト環境の状態は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-166">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="e5d9b-167">Office 365 E5 Enterprise と Dynamics 365 の試用版サブスクリプションが、ユーザー アカウントの一覧と同じ組織および同じ Azure AD テナントを共有している。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-167">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="e5d9b-168">グローバル エンタープライズ管理者、User 2、User 3 のアカウントが、Office 365 E5 Enterprise と Dynamics 365 の両方を使用できるようになり、Dynamics 365 のシステム管理者になっている。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-168">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="e5d9b-169">次の手順</span><span class="sxs-lookup"><span data-stu-id="e5d9b-169">Next step</span></span>

<span data-ttu-id="e5d9b-170">「[Office 365 と Dynamics 365 の開発/テスト環境用での Exchange Online の統合](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)」で、Exchange Online のメールボックスで Office 365 と Dynamics 365 を併用するための構成と方法ついて説明します。</span><span class="sxs-lookup"><span data-stu-id="e5d9b-170">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e5d9b-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5d9b-171">See Also</span></span>

[<span data-ttu-id="e5d9b-172">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="e5d9b-172">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="e5d9b-173">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="e5d9b-173">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="e5d9b-174">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="e5d9b-174">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="e5d9b-175">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="e5d9b-175">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="e5d9b-176">Dynamics 365 (オンライン) のサブスクリプション管理</span><span class="sxs-lookup"><span data-stu-id="e5d9b-176">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="e5d9b-177">Dynamics 365 の管理</span><span class="sxs-lookup"><span data-stu-id="e5d9b-177">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


