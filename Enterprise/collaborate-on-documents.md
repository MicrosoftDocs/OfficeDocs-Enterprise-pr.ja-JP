---
title: ゲストと共同でドキュメントの作業をする
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.collection: SPO_Content
localization_priority: Normal
description: SharePoint および OneDrive のドキュメントでゲストと共同作業する方法について説明します。
ms.openlocfilehash: f2cecb086116e5ea3322a0fd87e5f07f5c30443c
ms.sourcegitcommit: b5992f367ccae97a8ea538738fe36d3d703cd6e7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "39919351"
---
# <a name="collaborate-with-guests-on-a-document"></a><span data-ttu-id="626f1-103">ゲストと共同でドキュメントの作業をする</span><span class="sxs-lookup"><span data-stu-id="626f1-103">Collaborate with guests on a document</span></span>

<span data-ttu-id="626f1-104">SharePoint または OneDrive のドキュメントで組織外のユーザーと共同作業を行う必要がある場合は、ドキュメントへの共有リンクを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="626f1-104">If you need to collaborate with people outside your organization on documents in SharePoint or OneDrive, you can send them a sharing link to the document.</span></span> <span data-ttu-id="626f1-105">この記事では、組織のニーズに合わせて SharePoint と OneDrive の共有リンクを設定するために必要な、Microsoft 365 の構成手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="626f1-105">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up sharing links for SharePoint and OneDrive for the needs of your organization.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="626f1-106">ビデオ デモンストレーション</span><span class="sxs-lookup"><span data-stu-id="626f1-106">Video demonstration</span></span>

<span data-ttu-id="626f1-107">このビデオでは、このドキュメントで説明されている構成手順を示します。</span><span class="sxs-lookup"><span data-stu-id="626f1-107">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE450Vt?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="626f1-108">Azure の組織上の関係の設定</span><span class="sxs-lookup"><span data-stu-id="626f1-108">Azure Organizational relationships settings</span></span>

<span data-ttu-id="626f1-109">Microsoft 365 での共有は、Azure Active Directory の組織上の関係の設定によって最上位レベルで管理されます。</span><span class="sxs-lookup"><span data-stu-id="626f1-109">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="626f1-110">Azure AD でゲストの共有が無効または制限されている場合、これは Microsoft 365 で構成した共有設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="626f1-110">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="626f1-111">組織上の関係の設定を確認して、ゲストとの共有がブロックされないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="626f1-111">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory における組織の関係の設定ページのスクリーンショット](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="626f1-113">組織上の関係の設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="626f1-113">To set organizational relationship settings</span></span>

1. <span data-ttu-id="626f1-114">Microsoft Azure にログイン[https://portal.azure.com](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="626f1-114">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="626f1-115">左側のナビゲーションで、[ **Azure Active Directory**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-115">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="626f1-116">[**概要**] ウィンドウで、[組織上の**関係**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-116">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="626f1-117">[組織上の**関係**] ウィンドウで、[**設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-117">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="626f1-118">**管理者とゲスト招待元役割のユーザーが招待できる**ことと、**メンバーが招待**できることを確認します。どちらも **[はい]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="626f1-118">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="626f1-119">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-119">If you made changes, click **Save**.</span></span>

<span data-ttu-id="626f1-120">[**共同作業の制限**] セクションの設定に注意してください。</span><span class="sxs-lookup"><span data-stu-id="626f1-120">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="626f1-121">共同作業を行うゲストのドメインがブロックされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="626f1-121">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="626f1-122">SharePoint 組織レベルの共有設定</span><span class="sxs-lookup"><span data-stu-id="626f1-122">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="626f1-123">組織外のユーザーが SharePoint または OneDrive のドキュメントにアクセスできるようにするには、SharePoint および OneDrive の組織レベルでの共有設定で、組織外のユーザーとの共有が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="626f1-123">In order for people outside your organization to have access to a document in SharePoint or OneDrive, the SharePoint and OneDrive organization-level sharing settings must allow for sharing with people outside your organization.</span></span>

<span data-ttu-id="626f1-124">SharePoint の組織レベルの設定により、個々の SharePoint サイトで使用できる設定が決定されます。</span><span class="sxs-lookup"><span data-stu-id="626f1-124">The organization-level settings for SharePoint determine what settings are available for individual SharePoint sites.</span></span> <span data-ttu-id="626f1-125">サイトの設定は、組織レベルの設定よりも制限することはできません。</span><span class="sxs-lookup"><span data-stu-id="626f1-125">Site settings cannot be more permissive than the organization-level settings.</span></span> <span data-ttu-id="626f1-126">OneDrive の組織レベルの設定により、ユーザーの OneDrive ライブラリで利用可能な共有のレベルが決定されます。</span><span class="sxs-lookup"><span data-stu-id="626f1-126">The organization-level setting for OneDrive determines what level of sharing is available in users' OneDrive libraries.</span></span>

<span data-ttu-id="626f1-127">SharePoint と OneDrive の場合は、認証されていないファイルとフォルダーの共有を許可する場合は、[**すべて**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="626f1-127">For SharePoint and OneDrive, if you want to allow unauthenticated file and folder sharing, choose **Anyone**.</span></span> <span data-ttu-id="626f1-128">組織外のユーザーが認証を必要とするようにするには、[**新規および既存のゲスト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="626f1-128">If you want to ensure that people outside your organization have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="626f1-129">*すべて*のリンクが最も簡単に共有できます。組織外のユーザーは、認証なしでリンクを開くことができ、他のユーザーに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="626f1-129">*Anyone* links are the easiest way to share: people outside your organization can open the link without authentication and are free to pass it on to others.</span></span>

<span data-ttu-id="626f1-130">SharePoint の場合は、組織内のすべてのサイトで必要とされる最も寛容な設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="626f1-130">For SharePoint, choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 組織レベルの共有設定のスクリーンショット](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="626f1-132">SharePoint 組織レベルの共有設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="626f1-132">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="626f1-133">Microsoft 365 管理センターで、左側のナビゲーションの [**管理センター**] の下にある [ **SharePoint**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-133">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="626f1-134">SharePoint 管理センターの左側のナビゲーションで、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-134">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="626f1-135">SharePoint または OneDrive の外部共有が [すべての**ユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="626f1-135">Ensure that external sharing for SharePoint or OneDrive is set to **Anyone** or **New and existing guests**.</span></span> <span data-ttu-id="626f1-136">(OneDrive の設定は、SharePoint の設定よりも制限がないことに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="626f1-136">(Note that the OneDrive setting cannot be more permissive than the SharePoint setting.)</span></span>
4. <span data-ttu-id="626f1-137">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-137">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="626f1-138">SharePoint 組織レベルの既定のリンク設定</span><span class="sxs-lookup"><span data-stu-id="626f1-138">SharePoint organization level default link settings</span></span>

<span data-ttu-id="626f1-139">既定のファイルとフォルダーのリンク設定によって、ユーザーがファイルまたはフォルダーを共有するときに、どのリンクオプションが既定で表示されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="626f1-139">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="626f1-140">ユーザーは、必要に応じて、共有する前に、リンクの種類を他のオプションのいずれかに変更できます。</span><span class="sxs-lookup"><span data-stu-id="626f1-140">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="626f1-141">この設定は、組織内の SharePoint サイトや OneDrive に影響を与えることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="626f1-141">Keep in mind that this setting affects SharePoint sites in your organization, as well as OneDrive.</span></span>

<span data-ttu-id="626f1-142">ユーザーがファイルやフォルダーを共有するときに既定で選択されるリンクの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="626f1-142">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="626f1-143">**リンクを持つすべてのユーザー** -認証されていないファイルとフォルダーの共有が頻繁に行われるようにする場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="626f1-143">**Anyone with the link** - Choose this option if you expect to do a lot of unauthenticated file and folder sharing.</span></span> <span data-ttu-id="626f1-144">*すべて*のリンクを許可し、偶発的な認証されていない共有について懸念している場合は、他のオプションのいずれかを既定値として検討します。</span><span class="sxs-lookup"><span data-stu-id="626f1-144">If you want to allow *Anyone* links but are concerned about accidental unauthenticated sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="626f1-145">このリンクの種類は、**すべて**の共有を有効にした場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="626f1-145">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="626f1-146">[**組織内のユーザーのみ**]-ほとんどのファイルとフォルダーの共有が組織内のユーザーと想定される場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="626f1-146">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="626f1-147">**特定のユーザー** -多数のファイルとフォルダーをゲストで共有することが予想される場合は、このオプションを検討してください。</span><span class="sxs-lookup"><span data-stu-id="626f1-147">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="626f1-148">この種類のリンクはゲストと連動しており、認証を必要とします。</span><span class="sxs-lookup"><span data-stu-id="626f1-148">This type of link works with guests and requires them to authenticate.</span></span>
 
![SharePoint における組織レベルのファイルとフォルダー設定のスクリーンショット](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="626f1-150">SharePoint と OneDrive の組織レベルの既定のリンク設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="626f1-150">To set the SharePoint and OneDrive organization level default link settings</span></span>

1. <span data-ttu-id="626f1-151">SharePoint 管理センターの [共有] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="626f1-151">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="626f1-152">[**ファイルとフォルダーのリンク**] で、使用する既定の共有リンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="626f1-152">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="626f1-153">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-153">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="626f1-154">SharePoint サイトレベルの共有設定</span><span class="sxs-lookup"><span data-stu-id="626f1-154">SharePoint site level sharing settings</span></span>

<span data-ttu-id="626f1-155">SharePoint サイトにあるファイルや dler を共有している場合は、そのサイトのサイトレベルでの共有設定も確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="626f1-155">If you're sharing files and fodlers that are in a SharePoint site, you also need to check the site-level sharing settings for that site.</span></span>

![SharePoint サイトの外部共有設定のスクリーンショット](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="626f1-157">サイトレベルの共有設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="626f1-157">To set site-level sharing settings</span></span>
1. <span data-ttu-id="626f1-158">SharePoint 管理センターの左側のナビゲーションで、[**サイト**] を展開して [**アクティブなサイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-158">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="626f1-159">作成したサイトを選択します。</span><span class="sxs-lookup"><span data-stu-id="626f1-159">Select the site that you just created.</span></span>
3. <span data-ttu-id="626f1-160">リボンで [**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-160">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="626f1-161">共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="626f1-161">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="626f1-162">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="626f1-162">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="626f1-163">ユーザーを招待する</span><span class="sxs-lookup"><span data-stu-id="626f1-163">Invite users</span></span>

<span data-ttu-id="626f1-164">ゲスト共有の設定が構成されるようになったため、ユーザーが組織外のユーザーとファイルやフォルダーを共有できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="626f1-164">Guest sharing settings are now configured, so users can now share files and folders with people outside your organization.</span></span> <span data-ttu-id="626f1-165">詳細については、「 [OneDrive ファイルとフォルダーを共有](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07)する」および「 [SharePoint ファイルまたはフォルダーを共有](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="626f1-165">See [Share OneDrive files and folders](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) and [Share SharePoint files or folders](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="626f1-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="626f1-166">See Also</span></span>

[<span data-ttu-id="626f1-167">認証されていないユーザーとファイルおよびフォルダーを共有するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="626f1-167">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="626f1-168">ゲストと共有するときにファイルの偶発的な公開を制限する</span><span class="sxs-lookup"><span data-stu-id="626f1-168">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)