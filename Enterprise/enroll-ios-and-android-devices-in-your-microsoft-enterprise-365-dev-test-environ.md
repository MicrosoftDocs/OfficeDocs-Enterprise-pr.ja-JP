---
title: あっ、マイクロソフトのエンタープライズ 365 の開発/テスト環境でを登録します。
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: '概要: ガイドを使用してこのテスト ラボ Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理します。'
ms.openlocfilehash: 8765a7ffb1bff1f257d7cd1ce5181561c2cf0080
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-devtest-environment"></a><span data-ttu-id="d82e9-103">あっ、マイクロソフトのエンタープライズ 365 の開発/テスト環境でを登録します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-103">Enroll iOS and Android devices in your Microsoft Enterprise 365 dev/test environment</span></span>

 <span data-ttu-id="d82e9-104">**の概要:** Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理するには、このテスト ラボ ガイド 』 を使用します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="d82e9-p101">Microsoft エンタープライズ モビリティ スイート (EMS) では、組織のデータを保護しながら、お気に入りのアプリケーションとデバイスを使用して生産性の高い従業員を保つことができます。詳細については、[エンタープライズ ・ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d82e9-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="d82e9-p102">デバイス ・ レベルでセキュリティを適用する場合は、Microsoft Intune にデバイスを登録する必要があります。デバイスの登録を組織が所有するデバイスを管理するために役立つだけでなく個人 (BYOD) と共有デバイスには、組織が法的なのもいますが、ポリシーです。</span><span class="sxs-lookup"><span data-stu-id="d82e9-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="d82e9-109">によって、この資料に記載されている手順に従うことができます登録し、iOS および Android デバイスの基本的なモバイル デバイス管理の機能を Microsoft 365 開発/テスト環境でテストします。</span><span class="sxs-lookup"><span data-stu-id="d82e9-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="d82e9-110">フェーズ 1: Microsoft 365 の開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="d82e9-111">[[Microsoft 365 エンタープライズ開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)での指示に従います。</span><span class="sxs-lookup"><span data-stu-id="d82e9-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="d82e9-112">フェーズ 2: iOS および Android デバイスを登録します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="d82e9-113">指示を使用して、最初に、[をインストールし、会社のポータル アプリケーションにサインイン](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)、開発/テストのテナントの Microsoft Intune 会社のポータル アプリケーションをカスタマイズするのには。</span><span class="sxs-lookup"><span data-stu-id="d82e9-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your dev/test tenant.</span></span>

<span data-ttu-id="d82e9-114">次に、手順を使用[、会社のリソースへのアクセス権を設定](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)iOS デバイスを登録します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="d82e9-115">次に、手順を使用[Intune に Android デバイスの登録](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)Android のデバイスを登録します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-2-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="d82e9-116">フェーズ 2: は、iOS および Android のデバイスをリモートで管理します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-116">Phase 2: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="d82e9-p103">Microsoft Intune には、リモート ロック機能とパスコードのリセット機能あります。ユーザーがデバイスを紛失した場合は、デバイスをリモートからロックできます。ユーザーがパスコードを忘れた場合は、パスコードをリモートから削除できます。</span><span class="sxs-lookup"><span data-stu-id="d82e9-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can remove the passcode remotely.</span></span>
  
<span data-ttu-id="d82e9-120">iOS デバイスをリモートからロックするには、</span><span class="sxs-lookup"><span data-stu-id="d82e9-120">To lock an iOS device remotely:</span></span>
  
1.  <span data-ttu-id="d82e9-121">新しいタブを開きに移動http://manage.microsoft.com(必要な場合)。</span><span class="sxs-lookup"><span data-stu-id="d82e9-121">Open a new tab and go to http://manage.microsoft.com (if needed).</span></span> 

2.  <span data-ttu-id="d82e9-122">お使いのブラウザーの Microsoft Intune 管理コンソールで、左側のナビゲーションの**グループ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d82e9-122">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>

3. <span data-ttu-id="d82e9-123">**グループ**ウィンドウで開くには**のすべてのデバイス > すべてのモバイル デバイス > すべての直接管理されているデバイス**。</span><span class="sxs-lookup"><span data-stu-id="d82e9-123">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
4. <span data-ttu-id="d82e9-124">**すべての直接管理されているデバイス**のウィンドウで、[**デバイス**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d82e9-124">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
5. <span data-ttu-id="d82e9-125">デバイスの一覧で、対象の iOS デバイスをクリックします。 </span><span class="sxs-lookup"><span data-stu-id="d82e9-125">In the devices list, click your iOS device.</span></span> 
    
6. <span data-ttu-id="d82e9-126">iOS デバイスから、そのデバイスのメイン画面が表示されていることを確認します。 </span><span class="sxs-lookup"><span data-stu-id="d82e9-126">From your iOS device, make sure it is at the main screen.</span></span> 
    
7. <span data-ttu-id="d82e9-p104">管理コンピューターから、タスク バーをクリックして**リモート タスク > リモート ロック**。ロックアウトの画面に切り替わると、iOS のデバイスを監視します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-p104">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. Watch your iOS device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="d82e9-129">パスコードを削除するには、</span><span class="sxs-lookup"><span data-stu-id="d82e9-129">To remove the passcode:</span></span>
  
1. <span data-ttu-id="d82e9-130">管理コンピューターから、**すべての直接管理されているデバイス**のウィンドウで、[**デバイス**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d82e9-130">From your administration computer, in the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
2. <span data-ttu-id="d82e9-p105">の一覧では、iOS デバイスをクリックします。タスク バーをクリックして**リモート タスク > パスコード リセット**。1 分間待機します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-p105">In the list, click your iOS device. On the taskbar, click **Remote Tasks > Passcode Reset**. Wait for one minute.</span></span>
    
3. <span data-ttu-id="d82e9-p106">お使いの iOS デバイスからロックを解除して、パスコードが不要になったことに注意してください。再度パスコードを変更するには、し、**パスコード****の設定**[に移動します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-p106">From your iOS device, unlock it and notice that there is no longer a passcode. To change the passcode back, go into **Settings**, and then **Passcode**.</span></span>
    
<span data-ttu-id="d82e9-136">Android デバイスをリモートからロックするには、</span><span class="sxs-lookup"><span data-stu-id="d82e9-136">To lock an Android device remotely:</span></span>
  
1. <span data-ttu-id="d82e9-137">お使いのブラウザーの Microsoft Intune 管理コンソールで、左側のナビゲーションの**グループ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d82e9-137">From the Microsoft Intune administration console of your browser, click **Groups** in the left navigation.</span></span>
    
2. <span data-ttu-id="d82e9-138">**グループ**ウィンドウで開くには**のすべてのデバイス > すべてのモバイル デバイス > すべての直接管理されているデバイス**。</span><span class="sxs-lookup"><span data-stu-id="d82e9-138">In the **Groups** pane, open **All devices > All Mobile devices > All Direct Managed Devices**.</span></span>
    
3. <span data-ttu-id="d82e9-139">**すべての直接管理されているデバイス**のウィンドウで、[**デバイス**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d82e9-139">In the **All Direct Managed Devices** pane, click the **Devices** tab.</span></span>
    
4. <span data-ttu-id="d82e9-140">デバイスの一覧で、目的の Android デバイスをクリックします。 </span><span class="sxs-lookup"><span data-stu-id="d82e9-140">In the devices list, click your Android device.</span></span> 
    
5. <span data-ttu-id="d82e9-141">対象の Android デバイスから、そのデバイスのメイン画面が表示されていることを確認します。 </span><span class="sxs-lookup"><span data-stu-id="d82e9-141">From your Android device, make sure it is at the main screen.</span></span> 
    
6. <span data-ttu-id="d82e9-p107">管理コンピューターから、タスク バーをクリックして**リモート タスク > リモート ロック**。ダイアログ ボックスが表示されたら、[**はい**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d82e9-p107">From your administration computer, on the taskbar, click **Remote Tasks > Remote Lock**. When prompted, click **Yes**.</span></span>
    
7. <span data-ttu-id="d82e9-144">対象の Android デバイスがロックアウト画面に切り替わる様子を確認します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-144">Watch your Android device as it switches to the lockout screen.</span></span>
    
<span data-ttu-id="d82e9-145">Android デバイスのパスコードをリセットすると、Intune 管理ポータルを生成し、強力なパスコードを設定します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-145">When you reset the passcode for Android devices, the Intune administration portal generates and configures a strong passcode.</span></span>
  
<span data-ttu-id="d82e9-146">パスコードをリモートからリセットするには、</span><span class="sxs-lookup"><span data-stu-id="d82e9-146">To reset the passcode remotely:</span></span>
  
1. <span data-ttu-id="d82e9-147">管理コンピューターから Microsoft Intune 管理コンソール] タブの**すべての直接管理されているデバイス**のウィンドウに、ブラウザーの上には、Android デバイスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d82e9-147">From your administration computer, on the Microsoft Intune administration console tab of your browser, in the **All Direct Managed Devices** pane, click your Android device.</span></span>
    
2. <span data-ttu-id="d82e9-148">タスク バーをクリックして**リモート タスク > パスコード リセット**。</span><span class="sxs-lookup"><span data-stu-id="d82e9-148">On the taskbar, click **Remote Tasks > Passcode Reset**.</span></span>
    
3. <span data-ttu-id="d82e9-p108">**リモート タスク: パスコード リセット**プロンプトで、[**はい**] をクリックします。1 分間待機します。</span><span class="sxs-lookup"><span data-stu-id="d82e9-p108">On the **Remote Task: Passcode Reset** prompt, click **Yes**. Wait for one minute.</span></span>
    
4. <span data-ttu-id="d82e9-151">**すべての直接管理されているデバイス**のウィンドウで、**ビューのプロパティ**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d82e9-151">In the **All Direct Managed Devices** pane, click **View Properties**.</span></span>
    
5. <span data-ttu-id="d82e9-152">**パスコードのリセット**では、新しいパスコードを注意してください。</span><span class="sxs-lookup"><span data-stu-id="d82e9-152">Under **Passcode Reset**, note the new passcode.</span></span>
    
6. <span data-ttu-id="d82e9-153">Android でデバイスのロックアウト画面から、新しいパスコードを入力します。 </span><span class="sxs-lookup"><span data-stu-id="d82e9-153">From your Android device, enter the new passcode from the lockout screen.</span></span> 
    
7. <span data-ttu-id="d82e9-154">再度パスコードを変更するに**設定**に**デバイス**をタップ、**ロック画面**をタップして、パスコードの新しいパスコードをもう一度、タップして**画面のロック**、および選択を入力してください。</span><span class="sxs-lookup"><span data-stu-id="d82e9-154">To change the passcode back, go into **Settings**, tap **Device**, tap **Lock screen**, enter the new passcode again, tap **Screen lock**, and then your choice for the passcode.</span></span>
    

> [!TIP]
> <span data-ttu-id="d82e9-155">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="d82e9-155">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d82e9-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="d82e9-156">See Also</span></span>

[<span data-ttu-id="d82e9-157">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="d82e9-157">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="d82e9-158">Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー</span><span class="sxs-lookup"><span data-stu-id="d82e9-158">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="d82e9-159">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="d82e9-159">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="d82e9-160">エンタープライズ モビリティとセキュリティ (EMS)</span><span class="sxs-lookup"><span data-stu-id="d82e9-160">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


