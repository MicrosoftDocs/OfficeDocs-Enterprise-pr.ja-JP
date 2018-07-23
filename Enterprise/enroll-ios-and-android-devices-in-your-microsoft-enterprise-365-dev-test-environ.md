---
title: Microsoft 365 Enterprise 開発/テスト環境に iOS および Android デバイスを登録する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/20/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: '概要: ガイドを使用してこのテスト ラボ Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理します。'
ms.openlocfilehash: e4b8491a70d0d0177e0a434d228136243201e788
ms.sourcegitcommit: c3869a332512dd1cc25cd5a92a340050f1da0418
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "20720413"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="bbcd4-103">Microsoft 365 Enterprise 開発/テスト環境に iOS および Android デバイスを登録する</span><span class="sxs-lookup"><span data-stu-id="bbcd4-103">Enroll iOS and Android devices in your Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="bbcd4-104">**の概要:** Microsoft 365、開発/テスト環境でデバイスを登録し、それらをリモートで管理するには、このテスト ラボ ガイド 』 を使用します。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-104">**Summary:** Use this Test Lab Guide to enroll devices in your Microsoft 365 dev/test environment and manage them remotely.</span></span>
  
<span data-ttu-id="bbcd4-p101">Microsoft エンタープライズ モビリティ スイート (EMS) では、組織のデータを保護しながら、お気に入りのアプリケーションとデバイスを使用して生産性の高い従業員を保つことができます。詳細については、[エンタープライズ ・ モビリティとセキュリティ (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-p101">The Microsoft Enterprise Mobility Suite (EMS) helps keep your employees productive using their favorite apps and devices while protecting your organization's data. For more information, see [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security).</span></span>
  
<span data-ttu-id="bbcd4-p102">デバイス ・ レベルでセキュリティを適用する場合は、Microsoft Intune にデバイスを登録する必要があります。デバイスの登録を組織が所有するデバイスを管理するために役立つだけでなく個人 (BYOD) と共有デバイスには、組織が法的なのもいますが、ポリシーです。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-p102">If you need to apply security at the device level, you must enroll devices into Microsoft Intune. Device enrollment not only helps you to manage organization-owned devices, but also personal (BYOD) and shared devices, depending on your organization's legal policies.</span></span>
  
<span data-ttu-id="bbcd4-109">によって、この資料に記載されている手順に従うことができます登録し、iOS および Android デバイスの基本的なモバイル デバイス管理の機能を Microsoft 365 開発/テスト環境でテストします。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-109">By following the instructions provided in this article, you'll be able to enroll and test basic mobile device management capabilities for iOS and Android devices in your Microsoft 365 dev/test environment.</span></span>
  
## <a name="phase-1-create-your-microsoft-365-devtest-environment"></a><span data-ttu-id="bbcd4-110">フェーズ 1: Microsoft 365 の開発/テスト環境を作成します。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-110">Phase 1: Create your Microsoft 365 dev/test environment</span></span>

<span data-ttu-id="bbcd4-111">[[Microsoft 365 エンタープライズ開発/テスト環境](the-microsoft-365-enterprise-dev-test-environment.md)での指示に従います。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-111">Follow the instructions in [The Microsoft 365 Enterprise dev/test environment](the-microsoft-365-enterprise-dev-test-environment.md).</span></span>
  
## <a name="phase-2-enroll-your-ios-and-android-devices"></a><span data-ttu-id="bbcd4-112">フェーズ 2: iOS および Android デバイスを登録します。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-112">Phase 2: Enroll your iOS and Android devices</span></span>

<span data-ttu-id="bbcd4-113">指示を使用して、最初に、[をインストールし、会社のポータル アプリケーションにサインイン](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios)、テスト環境を Microsoft Intune 会社のポータル アプリケーションをカスタマイズするのには。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-113">First, use the instructions in [Install and sign in to the Company Portal app](https://docs.microsoft.com/intune-user-help/install-and-sign-in-to-the-intune-company-portal-app-ios) to customize the Microsoft Intune Company Portal app for your test environment.</span></span>

<span data-ttu-id="bbcd4-114">次に、手順を使用[、会社のリソースへのアクセス権を設定](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)iOS デバイスを登録します。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-114">Next, use the instructions in [Set up access to your company resources](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) to enroll an iOS device.</span></span>

<span data-ttu-id="bbcd4-115">次に、手順を使用[Intune に Android デバイスの登録](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)Android のデバイスを登録します。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-115">Next, use the instructions in [Enroll your Android device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android) to enroll an Android device.</span></span>

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a><span data-ttu-id="bbcd4-116">フェーズ 3: は、iOS および Android のデバイスをリモートで管理します。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-116">Phase 3: Manage your iOS and Android devices remotely</span></span>

<span data-ttu-id="bbcd4-p103">Microsoft Intune では、リモート ロックとパスコードの両方のリセット機能を提供します。他のユーザーを失った場合、デバイス、デバイスをリモートでロックできます。パスコードを忘れてしまった人の場合リモートでリセットすることができます。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-p103">Microsoft Intune provides both remote lock and passcode reset capabilities. If someone loses their device, you can lock the device remotely. If someone forgets their passcode, you can reset it remotely.</span></span>
  
<span data-ttu-id="bbcd4-120">IOS または Android デバイスをリモートでロック。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-120">To lock an iOS or Android device remotely:</span></span>

1. <span data-ttu-id="bbcd4-121">Azure ポータルにサインインするのに[https://portal.azure.com](https://portal.azure.com)のグローバル管理者アカウントの資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-121">Sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="bbcd4-122">**すべてのサービス**をクリックして、 **Intune**を入力し、 **Intune**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-122">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="bbcd4-123">クリックして**デバイス > のすべてのデバイス**。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-123">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="bbcd4-124">デバイスの一覧で、iOS または Android デバイスをクリック**リモート ロック**の動作です。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-124">In the list of devices, click an iOS or Android device, and then click the **Remote lock** action.</span></span>

    
<span data-ttu-id="bbcd4-125">パスコードをリモートからリセットするには、</span><span class="sxs-lookup"><span data-stu-id="bbcd4-125">To reset the passcode remotely:</span></span>

1. <span data-ttu-id="bbcd4-126">必要な場合がある Azure ポータルにサインイン[https://portal.azure.com](https://portal.azure.com)のグローバル管理者アカウントの資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-126">If needed, sign in to the Azure portal at [https://portal.azure.com](https://portal.azure.com) with the credentials of your global administrator account.</span></span>
2. <span data-ttu-id="bbcd4-127">**すべてのサービス**をクリックして、 **Intune**を入力し、 **Intune**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-127">Click **All services**, type **Intune**, and then click **Intune**.</span></span>
3. <span data-ttu-id="bbcd4-128">クリックして**デバイス > のすべてのデバイス**。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-128">Click **Devices > All devices**.</span></span>
4. <span data-ttu-id="bbcd4-p104">デバイスの一覧から管理、iOS または Android デバイスをクリックして**を選択.詳細**。**パスコードを削除する**デバイスのリモート操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-p104">From the list of devices you manage, click an iOS or Android device, and choose **...More**. Then choose the **Remove passcode** device remote action.</span></span>

<span data-ttu-id="bbcd4-131">追加の実験を行うには、[利用可能なデバイスの操作](https://docs.microsoft.com/intune/device-management#available-device-actions)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-131">For additional experimentation, see [Available device actions](https://docs.microsoft.com/intune/device-management#available-device-actions).</span></span>

    

> [!TIP]
> <span data-ttu-id="bbcd4-132">[ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="bbcd4-132">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bbcd4-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbcd4-133">See Also</span></span>

[<span data-ttu-id="bbcd4-134">Microsoft 365 Enterprise 開発/テスト環境</span><span class="sxs-lookup"><span data-stu-id="bbcd4-134">The Microsoft 365 Enterprise dev/test environment</span></span>](the-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="bbcd4-135">Microsoft 365 エンタープライズ開発/テスト環境の MAM のポリシー</span><span class="sxs-lookup"><span data-stu-id="bbcd4-135">MAM policies for your Microsoft 365 Enterprise dev/test environment</span></span>](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[<span data-ttu-id="bbcd4-136">クラウド導入のテスト ラボ ガイド (TLG)</span><span class="sxs-lookup"><span data-stu-id="bbcd4-136">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)

[<span data-ttu-id="bbcd4-137">エンタープライズ モビリティとセキュリティ (EMS)</span><span class="sxs-lookup"><span data-stu-id="bbcd4-137">Enterprise Mobility + Security (EMS)</span></span>](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)


