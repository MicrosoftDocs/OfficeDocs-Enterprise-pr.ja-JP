---
title: "Office 365 と Dynamics 365 の開発/テスト環境"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- jan17entnews
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 098c1a1d-83a1-40eb-bbc9-47de7af8bb23
description: "概要: は、Dynamics 365 を Office 365 の開発/テスト環境に追加するのには、このテスト ラボ ガイド 』 を使用します。"
ms.openlocfilehash: 49648dd357d23eaee2d08d35252e18edf6a5d2ec
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="office-365-and-dynamics-365-devtest-environment"></a><span data-ttu-id="05169-103">Office 365 と Dynamics 365 の開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="05169-103">Office 365 and Dynamics 365 dev/test environment</span></span>

 <span data-ttu-id="05169-104">**の概要:**Dynamics 365 を Office 365 の開発/テスト環境に追加するのにには、このテスト ラボ ガイド 』 を使用します。</span><span class="sxs-lookup"><span data-stu-id="05169-104">**Summary:** Use this Test Lab Guide to add Dynamics 365 to your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="05169-105">この記事の手順を使用して、Dynamics 365 試用版サブスクリプションを Office 365 開発/テスト環境と同じ組織に追加し、Office 365 と Dynamics 365 の開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="05169-105">With the instructions in this article, you add a Dynamics 365 trial subscription to the same organization as your Office 365 dev/test environment, creating an Office 365 and Dynamics 365 dev/test environment.</span></span>
  
<span data-ttu-id="05169-p101">Dynamics 365 試用版サブスクリプションを使用して、Dynamics 365 の機能をデモンストレーションすることができます。Dynamics 365 プラン 1、Enterprise Edition 試用版には、以下のソリューションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="05169-p101">You can use a Dynamics 365 trial subscription to demonstrate features and capabilities of Dynamics 365. The following solutions are included with a Dynamics 365 Plan 1, Enterprise Edition trial:</span></span>
  
- <span data-ttu-id="05169-p102">[Microsoft Dynamics 365 販売](https://www.microsoft.com/dynamics365/sales)します。オートメーションと販売員の対応に専念し、手際よく作業を支援するデジタル インテリジェンスの売上を増加します。</span><span class="sxs-lookup"><span data-stu-id="05169-p102">[Microsoft Dynamics 365 for Sales](https://www.microsoft.com/dynamics365/sales). Increase your sales with automation and digital intelligence helping your salespeople stay focused and work smarter.</span></span>
    
- <span data-ttu-id="05169-p103">[Microsoft Dynamics 365 の顧客サービス](https://www.microsoft.com/dynamics365/customer-service)です。ロイヤルティを獲得するには、完全な情報とデジタル情報のシームレスなサービスを提供する必要があるエージェントを提供します。</span><span class="sxs-lookup"><span data-stu-id="05169-p103">[Microsoft Dynamics 365 for Customer Service](https://www.microsoft.com/dynamics365/customer-service). Earn loyalty by giving your agents the complete information and digital intelligence they need to provide seamless service.</span></span>
    
- <span data-ttu-id="05169-p104">[フィールド サービス用の Microsoft Dynamics 365](https://www.microsoft.com/dynamics365/field-service)です。マスター サービスを呼び出す、スケジュールを最適化する、離れたり、人員、および予測ツールを使用して利益を向上させます。</span><span class="sxs-lookup"><span data-stu-id="05169-p104">[Microsoft Dynamics 365 for Field Service](https://www.microsoft.com/dynamics365/field-service). Master the service call by optimizing your schedules, equipping your workforce, and using predictive tools to increase profit.</span></span>
    
- <span data-ttu-id="05169-p105">[Microsoft Dynamics 365 プロジェクト サービスの自動化のため](https://www.microsoft.com/en-us/dynamics365/project-service-automation)です。プロジェクトが正常に完了し、従業員の生産性を向上し、インテリジェントなツールを使用して収益性の高い関係を作成します。</span><span class="sxs-lookup"><span data-stu-id="05169-p105">[Microsoft Dynamics 365 for Project Service Automation](https://www.microsoft.com/en-us/dynamics365/project-service-automation). Complete your projects successfully and create profitable relationships with productive employees and intelligent tools.</span></span>
    
<span data-ttu-id="05169-116">Dynamics 365 試用版サブスクリプションでは、上記の 1 つ以上をお試しいただけます。</span><span class="sxs-lookup"><span data-stu-id="05169-116">You can explore one or more of the above for your Dynamics 365 trial subscription.</span></span>
  
![Microsoft Cloud のテスト ラボ ガイド](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="05169-118">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="05169-118">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="05169-119">フェーズ 1:ライトウェイトの、またはシミュレーションのエンタープライズ Office 365 開発/テスト環境を構築する</span><span class="sxs-lookup"><span data-stu-id="05169-119">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="05169-120">最小要件で軽量な方法で Office 365 と Dynamics 365 をテストする場合は、フェーズ 2 と 3[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="05169-120">If you just want to test Office 365 and Dynamics 365 in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="05169-121">シミュレートされた企業の Office 365 と Dynamics 365 をテストする場合は、 [Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)に指示します。</span><span class="sxs-lookup"><span data-stu-id="05169-121">If you want to test Office 365 and Dynamics 365 for a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="05169-p106">この記事の構成には、シミュレーションのエンタープライズ開発/テスト環境は必要ありません。シミュレーションのエンタープライズ開発/テスト環境には、インターネットに接続されたシミュレーションのイントラネット、Windows サーバー AD フォレスト用のディレクトリ同期が含まれています。この機能は、一般的な組織と類似した環境で Office 365 と Dynamics 365 を試していただけるようオプションとしてここで提供されています。</span><span class="sxs-lookup"><span data-stu-id="05169-p106">The configuration in this article does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can experiment with Office 365 and Dynamics 365 in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-add-a-dynamics-365-trial-subscription"></a><span data-ttu-id="05169-124">フェーズ 2:Dynamics 365 試用版サブスクリプションを追加する</span><span class="sxs-lookup"><span data-stu-id="05169-124">Phase 2: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="05169-125">このフェーズでは、Office 365 試用版サブスクリプションにサインアップして、Office 365 試用版サブスクリプションと同じ組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="05169-125">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
### <a name="sign-up-for-a-dynamics-365-trial-subscription"></a><span data-ttu-id="05169-126">Dynamics 365 試用版サブスクリプションにサインアップする</span><span class="sxs-lookup"><span data-stu-id="05169-126">Sign up for a Dynamics 365 trial subscription</span></span>

1. <span data-ttu-id="05169-127">デスクトップ コンピューター (軽量) のいずれかのブラウザーを使用してまたは CLIENT1 から (エンタープライズをシミュレートする)、グローバル管理者アカウントの資格情報を持つ[https://portal.office.com](https://portal.office.com)で、Office 365 ポータルにサインインします。</span><span class="sxs-lookup"><span data-stu-id="05169-127">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at [https://portal.office.com](https://portal.office.com) with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="05169-128">**[管理]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-128">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="05169-129">[ **Office 管理者センター** ] タブで、左側のナビゲーションでは、をクリックして**請求 > サービスを購入する**です。</span><span class="sxs-lookup"><span data-stu-id="05169-129">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="05169-p107">**購買サービス**ページでは、 **Dynamics 365 1 Enterprise Edition の計画**の項目を検索します。上にマウス ポインターをポイントし、**無料の試用期間の開始**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-p107">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="05169-132">**[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-132">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="05169-133">**[注文の受領書]** ページで、 **[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-133">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="05169-p108">Dynamics 365 Plan 1 Enterprise Edition の試用版サブスクリプションは 30 日間有効です。試用版サブスクリプションは、追加で 30 日間まで簡単に延長できます。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="05169-p108">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-3-assign-dynamics-365-licenses-and-system-administrators"></a><span data-ttu-id="05169-137">フェーズ 3：Dynamics 365 ライセンスとシステム管理者を割り当てる</span><span class="sxs-lookup"><span data-stu-id="05169-137">Phase 3: Assign Dynamics 365 licenses and system administrators</span></span>

<span data-ttu-id="05169-138">このフェーズでは、Dynamics 365 ライセンスをグローバル管理者、User 2、User 3 のアカウントに割り当て、システム管理者とします。</span><span class="sxs-lookup"><span data-stu-id="05169-138">In this phase, you assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
<span data-ttu-id="05169-139">Dynamics 365 ライセンスを割り当てるには次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="05169-139">Use these steps to assign Dynamics 365 licenses.</span></span>
  
1. <span data-ttu-id="05169-140">[ **Office 管理者センター** ] タブをクリックして**ユーザー > アクティブなユーザー**。</span><span class="sxs-lookup"><span data-stu-id="05169-140">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="05169-141">、アクティブなユーザーの一覧で、グローバル管理者アカウント] をクリックし、**製品ライセンス**の**編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-141">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="05169-142">[**製品ライセンス**] ウィンドウで、**上**に**Dynamics 365 計画 1 のエンタープライズ エディション**の製品のライセンスを有効にする**、保存**、**閉じる**を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-142">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="05169-143">User 2 と User 3 のアカウントに対して、手順 2 と 3 を実行します。</span><span class="sxs-lookup"><span data-stu-id="05169-143">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="05169-144">**Office 管理者センター** ] タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="05169-144">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="05169-145">次の手順を使用して、Dynamics 365 のシステム管理者として User 2 と User 3 のアカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="05169-145">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="05169-146">**Microsoft Office ホーム**] タブから、[**管理**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-146">From the **Microsoft Office Home** tab, click **Admin**.</span></span>
    
2. <span data-ttu-id="05169-147">[ **Office 管理者センター** ] タブで、左側のナビゲーションでは、**管理センター**をを**Dynamics 365**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-147">On the **Office Admin center** tab, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="05169-148">Dynamics 365 がメニューに表示されるまで、Dynamics 365 のプロビジョニングの完了を待つ必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="05169-148">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
3. <span data-ttu-id="05169-149">Dynamics 365] タブで**これらのすべて**] をクリックし、**セットアップを完了します**。</span><span class="sxs-lookup"><span data-stu-id="05169-149">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="05169-150">セットアップが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="05169-150">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="05169-p109">セットアップが完了すると、サブスクリプション記録の一部であるサンプル データに基づく販売活動のダッシュ ボードが表示されます。ビデオの**試用版の開始**を表示するのには、いくつかの時間がかかります。完了時にビデオ ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="05169-p109">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
4. <span data-ttu-id="05169-154">ツールバーの上部にある、**販売**の横にある下向き矢印をクリックを選択し、**設定**] をクリックし、[**セキュリティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-154">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
5. <span data-ttu-id="05169-155">[**セキュリティ**] ページで [**ユーザー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-155">On the **Security** page, click **Users**.</span></span>
    
6. <span data-ttu-id="05169-156">ユーザーの一覧では、**ユーザー 2**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-156">In the list of users, click **User 2**.</span></span>
    
7. <span data-ttu-id="05169-157">ツール ・ バーでは、**ロールの管理**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-157">In the tool bar, click **Manage Roles**.</span></span>
    
8. <span data-ttu-id="05169-158">**ロールの管理**は、**システム管理者**をクリックし、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-158">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
9. <span data-ttu-id="05169-159">上部にあるツールバーの [**セキュリティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="05169-159">In the tool bar at the top click **Security**.</span></span>
    
10. <span data-ttu-id="05169-160">User 3 アカウントについて、手順 5 から 8 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="05169-160">Repeat steps 5-8 for the User 3 account.</span></span>
    
11. <span data-ttu-id="05169-161">閉じる、**ユーザー: User3**タブします。</span><span class="sxs-lookup"><span data-stu-id="05169-161">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="05169-162">Office 365 全体管理者アカウントに、Dynamics 365 のシステム管理者ロールが自動的に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="05169-162">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="05169-163">この段階で、Office 365 と Dynamics 365 の開発/テスト環境の状態は次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="05169-163">Your Office 365 and Dynamics 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="05169-164">Office 365 E5 Enterprise と Dynamics 365 の試用版サブスクリプションが、ユーザー アカウントの一覧と同じ組織および同じ Azure AD テナントを共有している。</span><span class="sxs-lookup"><span data-stu-id="05169-164">Office 365 E5 Enterprise and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="05169-165">グローバル エンタープライズ管理者、User 2、User 3 のアカウントが、Office 365 E5 Enterprise と Dynamics 365 の両方を使用できるようになり、Dynamics 365 のシステム管理者になっている。</span><span class="sxs-lookup"><span data-stu-id="05169-165">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use both Office 365 E5 Enterprise and Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="05169-166">次の手順</span><span class="sxs-lookup"><span data-stu-id="05169-166">Next step</span></span>

<span data-ttu-id="05169-167">構成し、Office 365 と Dynamics 365 のしくみまとめて[Office 365 と Dynamics 365 の開発/テスト環境に Exchange Online](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md)の統合オンラインの Exchange メールボックスを示します。</span><span class="sxs-lookup"><span data-stu-id="05169-167">Configure and then demonstrate how Office 365 and Dynamics 365 work together in Exchange Online mailboxes with [Exchange Online integration for your Office 365 and Dynamics 365 dev/test environment](exchange-online-integration-for-your-office-365-and-dynamics-365-dev-test-enviro.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="05169-168">See Also</span><span class="sxs-lookup"><span data-stu-id="05169-168">See Also</span></span>

[<span data-ttu-id="05169-169">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="05169-169">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="05169-170">基本構成開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="05169-170">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="05169-171">Office 365 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="05169-171">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="05169-172">Office 365 開発/テスト環境の DirSync</span><span class="sxs-lookup"><span data-stu-id="05169-172">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)

[<span data-ttu-id="05169-173">Dynamics 365 (オンライン) のサブスクリプション管理</span><span class="sxs-lookup"><span data-stu-id="05169-173">Subscription Management for Dynamics 365 (online)</span></span>](https://technet.microsoft.com/library/jj679903.aspx)
  
[<span data-ttu-id="05169-174">Dynamics 365 の管理</span><span class="sxs-lookup"><span data-stu-id="05169-174">Administering Dynamics 365</span></span>](https://technet.microsoft.com/library/dn531101.aspx)


