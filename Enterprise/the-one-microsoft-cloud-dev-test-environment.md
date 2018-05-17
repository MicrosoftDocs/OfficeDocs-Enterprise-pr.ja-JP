---
title: One Microsoft Cloud 開発/テスト環境
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: a1370fe4-2fd6-4fea-ad1d-3555433d6d2e
description: '概要: このテスト ラボ ガイドを使用して、Microsoft のクラウド サービスすべてを含む開発/テスト環境を作成します。'
ms.openlocfilehash: 29fcb1108ceac6aa488ca71d723789a7a2e6c409
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="the-one-microsoft-cloud-devtest-environment"></a><span data-ttu-id="ff079-103">One Microsoft Cloud 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="ff079-103">The One Microsoft Cloud dev/test environment</span></span>

 <span data-ttu-id="ff079-104">**概要:** このテスト ラボ ガイドを使用して、Microsoft のクラウド サービスすべてを含む開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="ff079-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes all of Microsoft’s cloud offerings.</span></span>
  
<span data-ttu-id="ff079-p101">この記事の手順に従い、Microsoft Azure インフラストラクチャ サービスでシミュレートされたイントラネットを作成し、Microsoft Office 365、Microsoft Enterprise Mobility + Security (EMS)、Microsoft Dynamics 365 のサブスクリプションを追加します。その結果として、1 つの開発/テスト環境で Microsoft のクラウド サービスすべてを同時に使用する、シンプルな組織になります。 </span><span class="sxs-lookup"><span data-stu-id="ff079-p101">With the instructions in this article, you create a simulated intranet in Microsoft Azure infrastructure services and then add Microsoft Office 365, Microsoft Enterprise Mobility + Security (EMS), and Microsoft Dynamics 365 subscriptions. The result is a simplified organization that uses all Microsoft's cloud offerings at the same time in a single dev/test environment.</span></span> 
  
![Azure、Office 365、EMS、Dynamics 365 が追加された One Microsoft Cloud 開発/テスト環境のフェーズ 3](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
<span data-ttu-id="ff079-108">最終的な構成を、次の目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff079-108">You can use the resulting configuration to:</span></span>
  
- <span data-ttu-id="ff079-109">Azure Active Directory (AD) で提供される共通 ID インフラストラクチャなどの、Microsoft のクラウド サービス間の統合を体験します。</span><span class="sxs-lookup"><span data-stu-id="ff079-109">Experience the integration across Microsoft's cloud offerings, such as the common identity infrastructure provided by Azure Active Directory (AD).</span></span>
    
- <span data-ttu-id="ff079-110">複数の Microsoft Cloud のサービスを含む、エンド ツー エンドのシナリオを評価します。</span><span class="sxs-lookup"><span data-stu-id="ff079-110">Evaluate end-to-end scenarios that include multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="ff079-111">複数の Microsoft Cloud のサービスを使用する、デモ、概念実証、開発/テスト構成などを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff079-111">Create a demo, proof-of-concept, or dev/test configuration that uses multiple Microsoft Cloud offerings.</span></span>
    
- <span data-ttu-id="ff079-112">プロフェッショナルな開発のため、Microsoft Cloud のスキルを構築します。</span><span class="sxs-lookup"><span data-stu-id="ff079-112">Build your Microsoft Cloud skills for professional development.</span></span>
    
## <a name="phase-1-create-a-simulated-intranet-and-add-office-365"></a><span data-ttu-id="ff079-113">フェーズ 1: シミュレートされたイントラネットを作成し、Office 365 を追加する</span><span class="sxs-lookup"><span data-stu-id="ff079-113">Phase 1: Create a simulated intranet and add Office 365</span></span>

<span data-ttu-id="ff079-114">「[Office 365 開発/テスト環境の DirSync](dirsync-for-your-office-365-dev-test-environment.md)」の説明に従います。</span><span class="sxs-lookup"><span data-stu-id="ff079-114">If you want to test ATP in a simulated enterprise, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="ff079-115">図 1 は、作成した構成に、Office 365 および Azure インフラストラクチャ サービスで実行されるシミュレートされたイントラネットと、オンプレミスの Windows Server Active Directory (AD) フォレストからのディレクトリ同期が含まれることを示しています。</span><span class="sxs-lookup"><span data-stu-id="ff079-115">Figure 1 shows your resulting configuration, which includes a simulated intranet running in Azure infrastructure services and directory synchronization from an on-premises Windows Server Active Directory (AD) forest.</span></span>
  
<span data-ttu-id="ff079-116">**図 1: Azure でシミュレートされたイントラネットと Office 365**</span><span class="sxs-lookup"><span data-stu-id="ff079-116">**Figure 1: The simulated intranet in Azure with Office 365**</span></span>

![DirSync を使用した Office 365 の開発/テスト環境](images/be5b37b0-f832-4878-b153-436c31546e21.png)
  
> [!NOTE]
> <span data-ttu-id="ff079-p102">Azure 試用版は 30 日間有効です。Office 365 Enterprise E5 の試用版サブスクリプションは 30 日間有効ですが、追加で 30 日間、簡単に延長できます。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料 Azure サブスクリプション、および新しい有料 Office 365 Enterprise E5 サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff079-p102">The Azure trial  is 30 days. The Office 365 Enterprise E5 Trial subscription is 30 days, which can be easily extended for another 30 days. For a permanent dev/test environment, create a new paid Azure subscription and a new paid Office 365 Enterprise E5 subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="ff079-121">フェーズ 2: EMS を追加する</span><span class="sxs-lookup"><span data-stu-id="ff079-121">Phase 2: Add EMS</span></span>

<span data-ttu-id="ff079-122">このフェーズでは、EMS 試用版サブスクリプションにサインアップして、Office 365 試用版サブスクリプションと同じ組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ff079-122">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="ff079-123">デスクトップ コンピューターのブラウザーまたは CLIENT1 のブラウザーのいずれかを使用して、全体管理者アカウントの資格情報で Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="ff079-123">With a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at  https://portal.office.com https://portal.office.com  with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="ff079-124">**[管理]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-124">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="ff079-125">ブラウザーの **[Office 管理センター]** タブの左側のナビゲーションで **[請求] > [サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-125">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="ff079-p103">**[サービスを購入]** ページで、 **[Enterprise Mobility + Security E5]** 項目を探します。その項目の上にマウス ポインターを移動させ、 **[無料試用版を起動する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="ff079-128">**[注文の確認]** ページで、 **[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-128">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="ff079-129">**[注文の受領書]** ページで、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-129">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="ff079-p104">Enterprise Mobility + Security E5 試用版サブスクリプションの試用期間は 90 日間です。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff079-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="ff079-132">次に、すべてのユーザー アカウントに対して Enterprise Mobility + Security E5 ライセンスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ff079-132">Next, enable the Enterprise Mobility + Security E5 license for all user accounts.</span></span>
  
1. <span data-ttu-id="ff079-133">ブラウザーの **[Office 365 管理センター]** タブの左側のナビゲーションで **[ユーザー] > [アクティブなユーザー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-133">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="ff079-134">全体管理者アカウントをクリックしてから、 **[製品ライセンス]** で **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-134">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="ff079-135">**[製品ライセンス]** ウィンドウで、 **Enterprise Mobility + Security E5** の製品ライセンスを **[オン]** にして、 **[保存]** をクリックしてから、 **[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-135">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="ff079-136">他のすべてのアカウント (User1、User 2、User 3、User 4、User 5) に対して、手順 2 と 3 を実行します。</span><span class="sxs-lookup"><span data-stu-id="ff079-136">For all of your other accounts (User1, User 2, User 3, User 4, and User 5), do steps 2 and 3.</span></span>
    
<span data-ttu-id="ff079-137">開発/テスト環境には、以下が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ff079-137">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="ff079-138">Azure インフラストラクチャ サービスで実行されるシミュレートされたイントラネット。</span><span class="sxs-lookup"><span data-stu-id="ff079-138">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="ff079-139">Office 365 E5 Enterprise と EMS の試用版サブスクリプションが、ユーザー アカウントの一覧と同じ組織および同じ Azure AD テナントを共有している。</span><span class="sxs-lookup"><span data-stu-id="ff079-139">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="ff079-140">すべてのユーザー アカウントで Office 365 E5 Enterprise と EMS が使用可能になっている。</span><span class="sxs-lookup"><span data-stu-id="ff079-140">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
<span data-ttu-id="ff079-141">図 2 は、EMS が追加された結果的な構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff079-141">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="ff079-142">**図 2: Azure でシミュレートされたイントラネットと、Office 365 および EMS**</span><span class="sxs-lookup"><span data-stu-id="ff079-142">**Figure 2: The simulated intranet in Azure with Office 365 and EMS**</span></span>

![Azure、Office 365、EMS が追加された One Microsoft Cloud 開発/テスト環境のフェーズ 2](images/fdb520fe-ebbd-4681-a80e-b60df52f07c5.png)
  
## <a name="phase-3-add-dynamics-365"></a><span data-ttu-id="ff079-144">フェーズ 3: Dynamics 365 を追加する</span><span class="sxs-lookup"><span data-stu-id="ff079-144">Phase 3: Add a Dynamics 365 trial subscription</span></span>

<span data-ttu-id="ff079-145">このフェーズでは、Dynamics 365 試用版サブスクリプションにサインアップして、Office 365 と EMS の試用版サブスクリプションと同じ組織に追加します。</span><span class="sxs-lookup"><span data-stu-id="ff079-145">In this phase, you sign up for the Dynamics 365 trial subscription and add it to the same organization as your Office 365 and EMS trial subscriptions.</span></span>
  
1. <span data-ttu-id="ff079-146">デスクトップ コンピューターのブラウザーまたは CLIENT1 のブラウザーのいずれかを使用して、全体管理者アカウントの資格情報で Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) にサインインします。</span><span class="sxs-lookup"><span data-stu-id="ff079-146">Using a browser on either your desktop computer (lightweight) or from CLIENT1 (simulated enterprise), sign in to the Office 365 portal at  https://portal.office.com https://portal.office.com  with the credentials of your global administrator account.</span></span>
    
2. <span data-ttu-id="ff079-147">**[管理]** タイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-147">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="ff079-148">**[Office 管理センター]** タブの左側のナビゲーションで **[請求] > [サービスを購入する]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-148">On the **Office admin center** tab, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="ff079-p105">**[サービスを購入]** ページで、**[Dynamics 365 プラン 1 Enterprise Edition]** の項目を探します。その項目の上にマウス ポインターを移動させ、**[無料試用版を起動する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-p105">On the **Purchase services** page, find the **Dynamics 365 Plan 1 Enterprise Edition** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="ff079-151">**[注文の確認]** ページで、**[今すぐ実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-151">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="ff079-152">**[注文の受領書]** ページで、**[続行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-152">On the **Order receipt** page, click **Continue**.</span></span>
    
> [!NOTE]
> <span data-ttu-id="ff079-p106">Dynamics 365 Plan 1 Enterprise Edition の試用版サブスクリプションは 30 日間有効です。試用版サブスクリプションは、追加で 30 日間まで簡単に延長できます。永続的な開発/テスト環境では、少数のライセンスを使用して新しい有料サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="ff079-p106">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
<span data-ttu-id="ff079-156">次の手順を使用して、Dynamics 365 ライセンスをグローバル管理者、User 2、User 3 のアカウントに割り当て、システム管理者とします。</span><span class="sxs-lookup"><span data-stu-id="ff079-156">Use these steps to assign Dynamics 365 licenses to the global administrator, User 2, and User 3 accounts and make them system administrators.</span></span>
  
1. <span data-ttu-id="ff079-157">**[Office 管理センター]** タブで **[ユーザー] > [アクティブなユーザー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-157">On the **Office admin center** tab, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="ff079-158">アクティブ ユーザーの一覧で、全体管理者アカウントを選択し、**[製品ライセンス]** で **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-158">In the list of active users, click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="ff079-159">**[製品ライセンス]** ウィンドウで、**Dynamics 365 プラン 1 Enterprise Edition** の製品ライセンスを **[オン]** にして、**[保存]** をクリックし、**[閉じる]** を 2 回クリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-159">On the **Product licenses** pane, turn the product license for **Dynamics 365 Plan 1 Enterprise Edition** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
4. <span data-ttu-id="ff079-160">User 2 と User 3 のアカウントに対して、手順 2 と 3 を実行します。</span><span class="sxs-lookup"><span data-stu-id="ff079-160">Perform steps 2 and 3 for the User 2 and User 3 accounts.</span></span>
    
5. <span data-ttu-id="ff079-161">**[Office 管理センター]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ff079-161">Close the **Office admin center** tab.</span></span>
    
<span data-ttu-id="ff079-162">次の手順を使用して、Dynamics 365 のシステム管理者として User 2 と User 3 のアカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="ff079-162">Use these steps to configure the User 2 and User 3 accounts as Dynamics 365 system administrators.</span></span>
  
1. <span data-ttu-id="ff079-163">ブラウザーの **[Office 管理センター]** タブの左側のナビゲーションで、**[管理センター]** をクリックして、**[Dynamics 365]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-163">On the **Office Admin center** tab in your browser, in the left navigation, click **Admin centers**, and then click **Dynamics 365**.</span></span>
    
    <span data-ttu-id="ff079-164">Dynamics 365 がメニューに表示されるまで、Dynamics 365 のプロビジョニングの完了を待つ必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="ff079-164">You may need to wait for Dynamics 365 to finish provisioning before Dynamics 365 appears in the menu.</span></span>
    
2. <span data-ttu-id="ff079-165">[Dynamics 365] タブで、**[これらのすべて]**、**[セットアップの完了]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-165">On the Dynamics 365 tab, click **All of these**, and then click **Complete Setup.**</span></span>
    
    <span data-ttu-id="ff079-166">セットアップが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="ff079-166">Wait for setup to complete.</span></span>
    
    <span data-ttu-id="ff079-p107">セットアップが完了すると、試用版サブスクリプションの一部であるサンプル データに基づいて営業活動ダッシュボードが表示されます。**[試用版へようこそ]** の数分のビデオをご覧ください。終了したら、ビデオ ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ff079-p107">When setup completes, it displays a Sales Activity Dashboard based on sample data that is part of the trail subscription. Take a few moments to view the **Welcome to your trial** video. Close the video window when complete.</span></span>
    
3. <span data-ttu-id="ff079-170">上部のツールバーで、**[営業]** の横にある下矢印をクリックし、**[設定]**、**[セキュリティ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-170">On the toolbar at the top, click the down arrow next to **Sales**, click **Settings**, and then click **Security**.</span></span>
    
4. <span data-ttu-id="ff079-171">**[セキュリティ]** ページで **[ユーザー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-171">On the **Security** page, click **Users**.</span></span>
    
5. <span data-ttu-id="ff079-172">ユーザーの一覧で **[User 2]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-172">In the list of users, click **User 2**.</span></span>
    
6. <span data-ttu-id="ff079-173">ツール バーで、**[ロールの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-173">In the tool bar, click **Manage Roles**.</span></span>
    
7. <span data-ttu-id="ff079-174">**[ロールの管理]** で、**[システム管理者]**、**[OK]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-174">In **Manage Roles**, click **System Administrator**, and then click **OK**.</span></span>
    
8. <span data-ttu-id="ff079-175">上部のツールバーで **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ff079-175">In the tool bar at the top click **Security**.</span></span>
    
9. <span data-ttu-id="ff079-176">User 3 アカウントについて、手順 5 から 8 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="ff079-176">Repeat steps 5-8 for the User 3 account.</span></span>
    
10. <span data-ttu-id="ff079-177">**[ユーザー： User3]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ff079-177">Close the **User: User3** tab.</span></span>
    
> [!NOTE]
> <span data-ttu-id="ff079-178">Office 365 全体管理者アカウントに、Dynamics 365 のシステム管理者ロールが自動的に割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="ff079-178">Your Office 365 global administrator account was automatically assigned the Dynamics 365 system administrator role.</span></span> 
  
<span data-ttu-id="ff079-179">開発/テスト環境には、以下が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ff079-179">Your dev/test environment now has:</span></span>
  
- <span data-ttu-id="ff079-180">Azure インフラストラクチャ サービスで実行されるシミュレートされたイントラネット。</span><span class="sxs-lookup"><span data-stu-id="ff079-180">A simulated intranet running in Azure infrastructure services.</span></span>
    
- <span data-ttu-id="ff079-181">Office 365 E5 Enterprise、EMS、Dynamics 365 の試用版サブスクリプションが、ユーザー アカウントの一覧と同じ組織および同じ Azure AD テナントを共有している。</span><span class="sxs-lookup"><span data-stu-id="ff079-181">Office 365 E5 Enterprise, EMS, and Dynamics 365 trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
    
- <span data-ttu-id="ff079-182">すべてのユーザー アカウントで Office 365 E5 Enterprise と EMS が使用可能になっている。</span><span class="sxs-lookup"><span data-stu-id="ff079-182">All of your user accounts enabled to use Office 365 E5 Enterprise and EMS.</span></span>
    
- <span data-ttu-id="ff079-183">グローバル エンタープライズ管理者、User 2、および User 3 のアカウントが、Dynamics 365 を使用できるようになり、Dynamics 365 のシステム管理者になっている。</span><span class="sxs-lookup"><span data-stu-id="ff079-183">Your global enterprise administrator, User 2, and User 3 accounts are enabled to use Dynamics 365 and are Dynamics 365 system administrators.</span></span>
    
<span data-ttu-id="ff079-184">図 3 は、最終的な構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff079-184">Figure 3 shows your resulting configuration.</span></span>
  
<span data-ttu-id="ff079-185">**図 3: Azure でシミュレートされたイントラネットと、Office 365、EMS、および Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="ff079-185">**Figure 3: The simulated intranet in Azure with Office 365, EMS, and Dynamics 365**</span></span>

![Azure、Office 365、EMS、Dynamics 365 が追加された One Microsoft Cloud 開発/テスト環境のフェーズ 3](images/31714fcc-0c7d-411f-bcd1-c62d9be090ee.png)
  
## <a name="next-steps"></a><span data-ttu-id="ff079-187">次の手順</span><span class="sxs-lookup"><span data-stu-id="ff079-187">Next steps</span></span>

<span data-ttu-id="ff079-p108">これで、One Microsoft Cloud 開発/テスト環境を自由に試すことができます。ガイド付き体験のいくつかのアイデアを次に紹介します。</span><span class="sxs-lookup"><span data-stu-id="ff079-p108">You can now experiment with your One Microsoft Cloud dev/test environment. Here are some ideas for guided experiences:</span></span>
  
- [<span data-ttu-id="ff079-190">EMS で Office 365 アプリケーションのモバイル アプリケーション管理 (MAM) ポリシーを構成する</span><span class="sxs-lookup"><span data-stu-id="ff079-190">Configure mobile application management (MAM) policies in EMS for Office 365 applicationshttps://technet.microsoft.com/library/mt764059.aspx</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- [<span data-ttu-id="ff079-191">Dynamics 365 の連絡先と Office 365 の統合における Exchange Online のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="ff079-191">Demonstrate Exchange Online in Office 365 integration with Dynamics 365 contactshttps://technet.microsoft.com/library/mt798313.aspx</span></span>](https://technet.microsoft.com/library/mt798313.aspx)
    
- [<span data-ttu-id="ff079-192">サーバー ベースのワークロードをホストするために、Azure インフラストラクチャ サービスで、シミュレートされたクロスプレミス ネットワークを作成する</span><span class="sxs-lookup"><span data-stu-id="ff079-192">Create a simulated cross-premises network in Azure infrastructure services for hosting server-based workloadshttps://technet.microsoft.com/library/mt745150.aspx</span></span>](https://technet.microsoft.com/library/mt745150.aspx)
    
## <a name="see-also"></a><span data-ttu-id="ff079-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff079-193">See Also</span></span>

[<span data-ttu-id="ff079-194">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="ff079-194">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="ff079-195">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="ff079-195">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)
  
[<span data-ttu-id="ff079-196">ハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="ff079-196">Hybrid solutions</span></span>](hybrid-solutions.md)
  
[<span data-ttu-id="ff079-197">セキュリティ ソリューション</span><span class="sxs-lookup"><span data-stu-id="ff079-197">Security solutions</span></span>](security-solutions.md)





