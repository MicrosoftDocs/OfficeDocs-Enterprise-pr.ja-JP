---
title: "Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー"
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
description: "概要: は、Microsoft 365 の開発/テスト環境に EMS のモバイル アプリケーションの管理 (MAM) ポリシーを追加するのには、このテスト ラボ ガイド 』 を使用します。"
ms.openlocfilehash: 9eb636fe14b2fbd1fe45fb7dac528a0d4e31be36
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="mam-policies-for-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="a0eb1-103">Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー</span><span class="sxs-lookup"><span data-stu-id="a0eb1-103">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="a0eb1-104">**の概要:**Microsoft 365 開発/テスト環境に EMS のモバイル アプリケーションの管理 (MAM) ポリシーを追加するのにには、このテスト ラボ ガイド 』 を使用します。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-104">**Summary:** Use this Test Lab Guide to add EMS mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
<span data-ttu-id="a0eb1-p101">Microsoft エンタープライズ モビリティとセキュリティ (EMS) は、組織のデータを保護しながら、お気に入りのアプリケーションとデバイスを使用して生産性の高い従業員を保つことができます。詳細については、[エンタープライズ ・ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-p101">The Microsoft Enterprise Mobility + Security (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="a0eb1-107">この資料の手順についてで Microsoft 365 の開発/テスト環境にモバイル アプリケーションの管理 (MAM) ポリシーを追加します。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-107">With the instructions in this article, you add mobile application management (MAM) policies to your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-build-out-your-microsoft-365-devtest-environment"></a><span data-ttu-id="a0eb1-108">フェーズ 1: Microsoft 365 の開発/テスト環境を構築します。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-108">Phase 1: Build out your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="a0eb1-109">[[Microsoft 365 エンタープライズ開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)での指示に従います。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-109">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-create-and-deploy-mam-policies-for-ios-and-android-devices"></a><span data-ttu-id="a0eb1-110">フェーズ 2:iOS デバイスと Android デバイス用の MAM ポリシーを作成し展開する</span><span class="sxs-lookup"><span data-stu-id="a0eb1-110">Phase 2: Create and deploy MAM policies for iOS and Android devices</span></span>

<span data-ttu-id="a0eb1-111">このフェーズでは、2 つの異なる MAM ポリシー (1 つは iOS デバイス用、もう 1 つは Android デバイス用) を作成し展開します。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-111">In this phase, you create and deploy two different MAM policies: one for iOS devices and one for Android devices.</span></span>
  
1. <span data-ttu-id="a0eb1-112">Office 365 ポータル ([https://portal.office.com](https://portal.office.com)) に移動し、グローバル管理者アカウントで Office 365 試用版サブスクリプションにサインインします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-112">Go to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) and sign in to your Office 365 trial subscription with your global administrator account.</span></span>
    
2. <span data-ttu-id="a0eb1-113">、お使いのブラウザーの新しいタブで、Azure ポータル ([https://azure.portal.com](https://azure.portal.com)) を開き、Office 365 のグローバル管理者アカウントを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-113">On a new tab of your browser, open the Azure portal ([https://azure.portal.com](https://azure.portal.com)) and sign in using your Office 365 global administrator account.</span></span>
    
3. <span data-ttu-id="a0eb1-114">[Azure ポータル] タブで、Internet Explorer のナビゲーション ウィンドウで**その他のサービス**(または右矢印) をクリックしてし、入力**Intune**、 **Intune**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-114">On the Azure portal tab in Internet Explorer, in the navigation pane, click **More services** (or the right arrow), type **Intune**, and then click **Intune**.</span></span>
    
4. <span data-ttu-id="a0eb1-115">左側のナビゲーション ウィンドウで、**[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-115">In the left navigation pane, click **Groups**.</span></span>
    
5. <span data-ttu-id="a0eb1-116">**ユーザーおよびグループのすべてのグループ**のブレードでは、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-116">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
6. <span data-ttu-id="a0eb1-117">**グループ**ブレードの**名前**、 **iOS デバイスのユーザーの管理**を入力**割り当て****メンバーシップの種類**を選択**[はい]**の**を有効にする Office 機能ですか?**、し、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-117">On the **Group** blade, type **Managed iOS device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span> 
    
7. <span data-ttu-id="a0eb1-118">**グループ**のブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-118">Close the **Group** blade.</span></span>
    
8. <span data-ttu-id="a0eb1-119">**ユーザーおよびグループのすべてのグループ**のブレードでは、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-119">On the **Users and groups-All groups** blade, click **Add**.</span></span>
    
9. <span data-ttu-id="a0eb1-120">**グループ**のブレードで**Android 管理デバイスのユーザー** **名**、入力**割り当てられた****メンバーシップの種類**を選択**[はい]**の**を有効にする Office 機能ですか?**、し、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-120">On the **Group** blade, type **Managed Android device users** in **Name**, select **Assigned** in **Membership type**, select **Yes** for **Enable Office features?**, and then click **Create**.</span></span>
    
10. <span data-ttu-id="a0eb1-121">**ユーザーとグループのグループのすべての**ブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-121">Close the **Users and groups-All groups** blade.</span></span>
    
11. <span data-ttu-id="a0eb1-122">**クイック タスク**の一覧で、 **Intune**ブレードの**コンプライアンス ポリシーの作成**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-122">On the **Intune** blade, in the **Quick tasks** list, click **Create a compliance policy**.</span></span>
    
12. <span data-ttu-id="a0eb1-123">**コンプライアンス ・ ポリシーのプロファイル**のブレードでは、**ポリシーの作成**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-123">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
13. <span data-ttu-id="a0eb1-p102">**ポリシーの作成**・ ブレードの**名前**、 **iOS**を入力します。**プラットフォーム**では、 **iOS**を選択、 **iOS コンプライアンス ・ ポリシー** ・ ブレードの上の [ **OK** ] をクリックでし、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-p102">On the **Create Policy** blade, in **Name**, type **iOS**. In **Platform**, select **iOS**, click **OK** on the **iOS compliance policy** blade, and then click **Create**.</span></span>
    
14. <span data-ttu-id="a0eb1-126">**コンプライアンス ・ ポリシーのプロファイル**のブレードでは、**ポリシーの作成**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-126">On the **Compliance Policy Profiles** blade, click **Create Policy**.</span></span>
    
15. <span data-ttu-id="a0eb1-p103">**ポリシーの作成**のブレードで [**名前**を入力**Android**。**プラットフォーム**、 **Android**を選択、 **Android のコンプライアンス ・ ポリシー** ・ ブレードの上の [ **OK** ] をクリックでし、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-p103">On the **Create Policy** blade, in **Name**, type **Android**. In **Platform**, select **Android**, click **OK** on the **Android compliance policy** blade, and then click **Create**.</span></span>
    
16. <span data-ttu-id="a0eb1-129">**コンプライアンス ポリシーのプロファイル**のブレード、 **Android**のポリシー名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-129">On the **Compliance Policy Profiles** blade, click the **Android** policy name.</span></span>
    
17. <span data-ttu-id="a0eb1-130">**Android - プロパティ**のブレードの左側のナビゲーションでは、**割り当て**をクリックし、**グループの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-130">In the left navigation of the **Android - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
18. <span data-ttu-id="a0eb1-131">**グループを選択して**ブレードの**Android 管理デバイスのユーザー**グループをクリックし、**選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-131">On the **Select groups** blade, click the **Managed Android device users** group, and then click **Select**.</span></span>
    
19. <span data-ttu-id="a0eb1-132">**保存**] をクリックして、**アプリの割り当て**のブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-132">Click **Save**, and then close the **Android - Assignments** blade.</span></span>
    
20. <span data-ttu-id="a0eb1-133">**コンプライアンス ・ ポリシーのプロファイル**のブレードでは、 **iOS**のポリシー名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-133">On the **Compliance Policy Profiles** blade, click the **iOS** policy name.</span></span>
    
21. <span data-ttu-id="a0eb1-134">**IOS - プロパティ**のブレードの左側のナビゲーションでは、**割り当て**をクリックし、**グループの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-134">In the left navigation of the **iOS - Properties** blade, click **Assignments**, and then click **Select groups**.</span></span>
    
22. <span data-ttu-id="a0eb1-135">**グループを選択して**ブレードの**iOS デバイスのユーザーを管理**グループをクリックし、**選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-135">On the **Select groups** blade, click the **Managed iOS device users** group, and then click **Select**.</span></span>
    
23. <span data-ttu-id="a0eb1-136">**保存**] をクリックし、 **iOS の割り当て**のブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-136">Click **Save**, and then close the **iOS - Assignments** blade.</span></span>
    
24. <span data-ttu-id="a0eb1-137">**コンプライアンス ポリシーのプロファイル**のブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-137">Close the **Compliance Policy Profiles** blade.</span></span>
    
25. <span data-ttu-id="a0eb1-138">**Intune**ブレードの左側のナビゲーションで [**管理アプリケーション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-138">On the **Intune** blade, click **Manage apps** in the left navigation.</span></span>
    
26. <span data-ttu-id="a0eb1-139">**モバイル アプリケーション**のブレードでは、**アプリケーション**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-139">On the **Mobile Apps** blade, click **Apps**.</span></span>
    
27. <span data-ttu-id="a0eb1-140">アプリケーションの一覧で、 **PowerPoint**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-140">In the list of apps, click **PowerPoint**,</span></span> 
    
28. <span data-ttu-id="a0eb1-p104">**PowerPoint 概要**ブレードでは、をクリックして**の割り当て > グループを選択して > iOS デバイスを管理する > を選択して**。**型**の場合は、**利用可能**時間を選択し、し、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-p104">On the **PowerPoint Overview** blade, click **Assignments > Select groups > Managed iOS devices > Select**. In **Type**, select **Available**, and then click **Save**.</span></span>
    
29. <span data-ttu-id="a0eb1-143">以下のアプリで、手順 28 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-143">Repeat step 28 for the following apps:</span></span>
    
  - <span data-ttu-id="a0eb1-144">Outlook for Android</span><span class="sxs-lookup"><span data-stu-id="a0eb1-144">Outlook for Android</span></span>
    
  - <span data-ttu-id="a0eb1-145">Word for iOS</span><span class="sxs-lookup"><span data-stu-id="a0eb1-145">Word for iOS</span></span>
    
  - <span data-ttu-id="a0eb1-146">Excel for iOS</span><span class="sxs-lookup"><span data-stu-id="a0eb1-146">Excel for iOS</span></span>
    
  - <span data-ttu-id="a0eb1-147">iOS 版 Outlook</span><span class="sxs-lookup"><span data-stu-id="a0eb1-147">Outlook for iOS</span></span>
    
  - <span data-ttu-id="a0eb1-148">Microsoft Dynamics CRM on iPad for iOS</span><span class="sxs-lookup"><span data-stu-id="a0eb1-148">Microsoft Dynamics CRM on iPad for iOS</span></span>
    
  - <span data-ttu-id="a0eb1-149">Microsoft Dynamics CRM on iPhone for iOS</span><span class="sxs-lookup"><span data-stu-id="a0eb1-149">Microsoft Dynamics CRM on iPhone for iOS</span></span>
    
  - <span data-ttu-id="a0eb1-150">電話用 Dynamics CRM for Android</span><span class="sxs-lookup"><span data-stu-id="a0eb1-150">Dynamics CRM for Phones for Android</span></span>
    
  - <span data-ttu-id="a0eb1-151">タブレット用 Dynamics CRM for Android</span><span class="sxs-lookup"><span data-stu-id="a0eb1-151">Dynamics CRM for Tablets for Android</span></span>
    
  - <span data-ttu-id="a0eb1-152">Excel for Android</span><span class="sxs-lookup"><span data-stu-id="a0eb1-152">Excel for Android</span></span>
    
  - <span data-ttu-id="a0eb1-153">Word for Android</span><span class="sxs-lookup"><span data-stu-id="a0eb1-153">Word for Android</span></span>
    
  - <span data-ttu-id="a0eb1-154">OneNote for iOS</span><span class="sxs-lookup"><span data-stu-id="a0eb1-154">OneNote for iOS</span></span>
    
30. <span data-ttu-id="a0eb1-155">**モバイル アプリケーション - アプリケーション**のブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-155">Close the **Mobile Apps - Apps** blade.</span></span>
    
31. <span data-ttu-id="a0eb1-156">**モバイル アプリケーション**のブレードでは、**アプリケーション保護ポリシー**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-156">On the **Mobile Apps** blade, click **App Protection Policies**.</span></span>
    
32. <span data-ttu-id="a0eb1-157">**アプリケーション保護ポリシー** ・ ブレードの上には、**ポリシーの追加**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-157">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
33. <span data-ttu-id="a0eb1-158">**ポリシーの追加**のブレードでは、 **iOS**を入力し、**必要なアプリケーションの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-158">On the **Add a policy** blade, type **iOS**, and then click **Select required apps**.</span></span>
    
34. <span data-ttu-id="a0eb1-159">**アプリ**のブレードでは、 **PowerPoint** **iPhone 上の Microsoft Dynamics CRM**、 **Excel** **iPhone 上の Microsoft Dynamics CRM**、 **Word**、 **OneNote**、および**Outlook**をクリックし、**選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-159">On the **Apps** blade, click **PowerPoint**, **Microsoft Dynamics CRM on iPhone**, **Excel**, **Microsoft Dynamics CRM on iPhone**, **Word**, **OneNote**, and **Outlook**, and then click **Select**.</span></span>
    
35. <span data-ttu-id="a0eb1-160">**追加ポリシー**ブレードの**作成**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-160">On the **Add a policy** blade, click **Create**.</span></span>
    
36. <span data-ttu-id="a0eb1-161">**アプリケーション保護ポリシー** ・ ブレードの上には、**ポリシーの追加**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-161">On the **App Protection Policies** blade, click **Add a policy**.</span></span>
    
37. <span data-ttu-id="a0eb1-162">**追加ポリシー**ブレード、 **Android**を入力、**プラットフォーム**、 **Android**を選択および**必要なアプリケーションの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-162">On the **Add a policy** blade, type **Android**, select **Android** in **Platform**, and then click **Select required apps**.</span></span>
    
38. <span data-ttu-id="a0eb1-163">**アプリ**のブレードでは、 **PowerPoint****タブレットの Dynamics CRM**、 **Excel**、 **Word**、 **Outlook**、および**電話の Dynamics CRM**をクリックし、**選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-163">On the **Apps** blade, click **PowerPoint**, **Dynamics CRM for tablets**, **Excel**, **Word**, **Outlook**, and **Dynamics CRM for phones**, and then click **Select**.</span></span>
    
39. <span data-ttu-id="a0eb1-164">**追加ポリシー**ブレードの**作成**を] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-164">On the **Add a policy** blade, click **Create**.</span></span>
    
<span data-ttu-id="a0eb1-165">これで、2 つの MAM ポリシー (1 つは iOS デバイス用、もう 1 つは Android デバイス用) が設定され、選択されたアプリの設定をテストする用意ができました。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-165">You now have two MAM policies, one for iOS devices and one for Android devices, and are ready to experiment with testing settings for the selected apps.</span></span>
  
> [!TIP]
> <span data-ttu-id="a0eb1-166">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-166">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a0eb1-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0eb1-167">See Also</span></span>

[<span data-ttu-id="a0eb1-168">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="a0eb1-168">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="a0eb1-169">あっ、マイクロソフトのエンタープライズ 365 の開発/テスト環境でを登録します。</span><span class="sxs-lookup"><span data-stu-id="a0eb1-169">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[<span data-ttu-id="a0eb1-170">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="a0eb1-170">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="a0eb1-171">エンタープライズ モビリティとセキュリティ (EMS)</span><span class="sxs-lookup"><span data-stu-id="a0eb1-171">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


