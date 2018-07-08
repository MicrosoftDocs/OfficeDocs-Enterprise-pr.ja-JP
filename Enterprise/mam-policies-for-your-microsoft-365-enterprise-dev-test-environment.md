---
title: Microsoft 365 Enterprise 開発/テスト環境の MAM のポリシー
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: '概要: は、Microsoft 365 の開発/テスト環境に EMS のモバイル アプリケーションの管理 (MAM) ポリシーを追加するのには、このテスト ラボ ガイド 』 を使用します。'
ms.openlocfilehash: 0a5c81665edf06631b8cebc57c9e715c78d3d85e
ms.sourcegitcommit: c23b95d32a865e45be7843f38a1f23b5693ba76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "20188155"
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="a040e-103">Microsoft 365 Enterprise 開発/テスト環境の MAM のポリシー</span><span class="sxs-lookup"><span data-stu-id="a040e-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="a040e-104">**の概要:** Microsoft 365 開発/テスト環境に EMS のモバイル アプリケーションの管理 (MAM) ポリシーを追加するのにには、このテスト ラボ ガイド 』 を使用します。</span><span class="sxs-lookup"><span data-stu-id="a040e-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="a040e-p101">Microsoft エンタープライズ モビリティとセキュリティ (EMS) は、組織のデータを保護しながら、お気に入りのアプリケーションとデバイスを使用して生産性の高い従業員を保つことができます。詳細については、[エンタープライズ ・ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a040e-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="a040e-107">この資料の手順についてで Microsoft 365 の開発/テスト環境にモバイル アプリケーションの管理 (MAM) ポリシーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a040e-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="a040e-108">フェーズ 1: Microsoft 365 の開発/テスト環境を構築します。</span><span class="sxs-lookup"><span data-stu-id="a040e-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="a040e-109">[[Microsoft 365 エンタープライズ開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)での指示に従います。</span><span class="sxs-lookup"><span data-stu-id="a040e-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="a040e-110">フェーズ 2:iOS デバイスと Android デバイス用の MAM ポリシーを作成し展開する</span><span class="sxs-lookup"><span data-stu-id="a040e-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="a040e-111">このフェーズでは、2 つの異なる MAM ポリシー (1 つは iOS デバイス用、もう 1 つは Android デバイス用) を作成し展開します。</span><span class="sxs-lookup"><span data-stu-id="a040e-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="a040e-112">Office 365 ポータルに移動 ([https://portal.office.com](https://portal.office.com)) し、グローバル管理者アカウントを使用して、Office 365 の試用版サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="a040e-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="a040e-113">、お使いのブラウザーの新しいタブで開くには、Azure ポータル ([https://azure.portal.com](https://azure.portal.com)) し、Office 365 のグローバル管理者アカウントを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="a040e-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="a040e-114">[Azure ポータル] タブで、Internet Explorer のナビゲーション ウィンドウで**すべてのサービス**] をクリックし、入力**Intune**、 **Intune**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **All services**, type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="a040e-115">左側のナビゲーション ウィンドウで、**[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="a040e-116">**グループのグループのすべての**ブレードでは、[ **+ 新しいグループ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-116">On the **Groups-All groups** blade, click **+ New Group**.</span></span>
    
6. <span data-ttu-id="a040e-117">**グループ**・ ブレードの上の**Office 365**を選択**グループの種類ですか?** **iOS デバイスのユーザーの管理****名**、**メンバーシップの種類**、**割り当て**を選択して入力し、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-117">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span> 
    
7. <span data-ttu-id="a040e-118">**[グループ]** ブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a040e-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="a040e-119">**グループのグループのすべての**ブレードでは、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-119">On the **Groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="a040e-120">**グループ**・ ブレードの上の**Office 365**を選択**グループの種類ですか?** **Android 管理デバイスのユーザー** **名**、**メンバーシップの種類**、**割り当て**を選択して入力し、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-120">On the **Group** blade, select **Office 365** for **Group type?**, type **Managed Android device user** in **Name**, select **Assigned** in **Membership type**,  and then click **Create**.</span></span>
    
10. <span data-ttu-id="a040e-121">**グループのグループのすべての**ブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a040e-121">Close the **Groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="a040e-122">**[Intune]** ブレードの **[クイック タスク]** 一覧で、**[コンプライアンス ポリシーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="a040e-123">**[コンプライアンス ポリシー プロファイル]** ブレードで、**[ポリシーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="a040e-p102">**[ポリシーの作成]** ブレードの **[名前]** で、「**iOS**」と入力します。**[プラットフォーム]** で **[iOS]** を選択し、**[iOS コンプライアンス ポリシー]** ブレードで **[OK]** をクリックし、次いで **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="a040e-126">**[コンプライアンス ポリシー プロファイル]** ブレードで、**[ポリシーの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="a040e-p103">**[ポリシーの作成]** ブレードの **[名前]** で、「**Android**」と入力します。**[プラットフォーム]** で **[Android]** を選択し、**[Android コンプライアンス ポリシー]** ブレードで **[OK]** をクリックし、次いで **[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="a040e-129">**[コンプライアンス ポリシー プロファイル]** ブレードで、**Android** のポリシー名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="a040e-130">**[Android - プロパティ]** ブレードの左側のナビゲーションで、**[割り当て]**、**[グループの選択]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="a040e-131">**[グループの選択]** ブレードで、**[管理された Android デバイス ユーザー]** グループをクリックし、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="a040e-132">**保存**] をクリックして、**アプリの割り当て**のブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a040e-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="a040e-133">**[コンプライアンス ポリシー プロファイル]** ブレードで、**iOS** のポリシー名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="a040e-134">**[iOS - プロパティ]** ブレードの左側のナビゲーションで、**[割り当て]**、**[グループの選択]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="a040e-135">**[グループの選択]** ブレードで、**[管理された iOS デバイス ユーザー]** グループをクリックし、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="a040e-136">**保存**] をクリックし、 **iOS の割り当て**のブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a040e-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="a040e-137">**[コンプライアンス ポリシー プロファイル]** ブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a040e-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="a040e-138">**[Intune]** ブレードの左側のナビゲーションで、**[アプリの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="a040e-139">**[モバイル アプリ]** ブレードで、**[アプリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="a040e-140">アプリの一覧で、**[PowerPoint]** をクリックします。 </span><span class="sxs-lookup"><span data-stu-id="a040e-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="a040e-p104">**[PowerPoint の概要]** ブレードで、**[割り当て] > [グループの選択] > [iOS デバイスの管理] > [選択]** の順にクリックします。**[種類]** で、**[利用可能]** を選択して、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="a040e-143">以下のアプリで、手順 28 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a040e-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="a040e-144">Outlook for Android</span><span class="sxs-lookup"><span data-stu-id="a040e-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="a040e-145">Word for iOS</span><span class="sxs-lookup"><span data-stu-id="a040e-145">Word for iOS</span></span>
    
  - <span data-ttu-id="a040e-146">Excel for iOS</span><span class="sxs-lookup"><span data-stu-id="a040e-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="a040e-147">iOS 版 Outlook</span><span class="sxs-lookup"><span data-stu-id="a040e-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="a040e-148">Microsoft Dynamics CRM on iPad for iOS</span><span class="sxs-lookup"><span data-stu-id="a040e-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="a040e-149">Microsoft Dynamics CRM on iPhone for iOS</span><span class="sxs-lookup"><span data-stu-id="a040e-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="a040e-150">電話用 Dynamics CRM for Android</span><span class="sxs-lookup"><span data-stu-id="a040e-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="a040e-151">タブレット用 Dynamics CRM for Android</span><span class="sxs-lookup"><span data-stu-id="a040e-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="a040e-152">Excel for Android</span><span class="sxs-lookup"><span data-stu-id="a040e-152">Excel for Android</span></span>
    
  - <span data-ttu-id="a040e-153">Word for Android</span><span class="sxs-lookup"><span data-stu-id="a040e-153">Word for Android</span></span>
    
  - <span data-ttu-id="a040e-154">OneNote for iOS</span><span class="sxs-lookup"><span data-stu-id="a040e-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="a040e-155">**[モバイル アプリ - アプリ]** ブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a040e-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="a040e-156">**[モバイル アプリ]** ブレードで、**[アプリ保護ポリシー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="a040e-157">**[アプリ保護ポリシー]** ブレードで、**[ポリシーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="a040e-158">**[ポリシーの追加]** ブレードで、「**iOS**」と入力して、**[必要なアプリの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="a040e-159">**[アプリ]** ブレードで、**[PowerPoint]**、**[Microsoft Dynamics CRM on iPhone]**、**[Excel]**、**[Microsoft Dynamics CRM on iPhone]**、**[Word]**、**[OneNote]**、**[Outlook]** をクリックし、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="a040e-160">**[ポリシーの追加]** ブレードで、**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="a040e-161">**[アプリ保護ポリシー]** ブレードで、**[ポリシーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="a040e-162">**[ポリシーの追加]** ブレードで、「**Android**」と入力します。**[プラットフォーム]** で **[Android]** を選択して、**[必要なアプリの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="a040e-163">**[アプリ]** ブレードで、**[PowerPoint]**、**[タブレット用 Dynamics CRM]**、**[Excel]**、**[Word]**、**[Outlook]**、**[電話用 Dynamics CRM]** をクリックし、**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="a040e-164">**[ポリシーの追加]** ブレードで、**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a040e-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="a040e-165">これで、2 つの MAM ポリシー (1 つは iOS デバイス用、もう 1 つは Android デバイス用) が設定され、選択されたアプリの設定をテストする用意ができました。</span><span class="sxs-lookup"><span data-stu-id="a040e-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="a040e-166">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="a040e-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a040e-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="a040e-167">See Also</span></span>

[<span data-ttu-id="a040e-168">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="a040e-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="a040e-169">Microsoft 365 Enterprise 開発/テスト環境に iOS および Android デバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="a040e-169">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="a040e-170">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="a040e-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="a040e-171">エンタープライズ モビリティとセキュリティ (EMS)</span><span class="sxs-lookup"><span data-stu-id="a040e-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


