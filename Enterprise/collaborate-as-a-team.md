---
title: チームでゲストと共同で作業する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords:
- NOCSH
description: Teams でゲストと共同作業する方法について説明します。
ms.openlocfilehash: 61d45829071bf19bfbda4bbb80fc7b0af7472d7f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41845048"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="bb8bc-103">チームでゲストと共同で作業する</span><span class="sxs-lookup"><span data-stu-id="bb8bc-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="bb8bc-104">ドキュメント、タスク、会話でゲストと共同作業を行う必要がある場合は、Microsoft Teams を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="bb8bc-105">Teams は、常設チャットと、カスタマイズ可能で拡張可能なコラボレーションツールのセットを統合されたユーザーの環境で使用できる、Office および SharePoint で利用可能なすべてのコラボレーション機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="bb8bc-106">この記事では、ゲストとの共同作業のためにチームをセットアップするために必要な Microsoft 365 の構成手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="bb8bc-107">ビデオ デモンストレーション</span><span class="sxs-lookup"><span data-stu-id="bb8bc-107">Video demonstration</span></span>

<span data-ttu-id="bb8bc-108">このビデオでは、このドキュメントで説明されている構成手順を示します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-108">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="bb8bc-109">Azure の組織上の関係の設定</span><span class="sxs-lookup"><span data-stu-id="bb8bc-109">Azure Organizational relationships settings</span></span>

<span data-ttu-id="bb8bc-110">Microsoft 365 での共有は、Azure Active Directory の組織上の関係の設定によって最上位レベルで管理されます。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-110">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="bb8bc-111">Azure AD でゲストの共有が無効または制限されている場合、これは Microsoft 365 で構成した共有設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-111">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="bb8bc-112">組織上の関係の設定を確認して、ゲストとの共有がブロックされないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-112">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory における組織の関係の設定ページのスクリーンショット](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="bb8bc-114">組織上の関係の設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="bb8bc-114">To set organizational relationship settings</span></span>

1. <span data-ttu-id="bb8bc-115">Microsoft Azure にログイン[https://portal.azure.com](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-115">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="bb8bc-116">左側のナビゲーションで、[ **Azure Active Directory**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-116">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="bb8bc-117">[**概要**] ウィンドウで、[組織上の**関係**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-117">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="bb8bc-118">[組織上の**関係**] ウィンドウで、[**設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-118">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="bb8bc-119">**管理者とゲスト招待元役割のユーザーが招待できる**ことと、**メンバーが招待**できることを確認します。どちらも **[はい]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-119">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="bb8bc-120">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-120">If you made changes, click **Save**.</span></span>

<span data-ttu-id="bb8bc-121">[**共同作業の制限**] セクションの設定に注意してください。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-121">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="bb8bc-122">共同作業を行うゲストのドメインがブロックされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-122">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="bb8bc-123">Teams ゲストアクセス設定</span><span class="sxs-lookup"><span data-stu-id="bb8bc-123">Teams guest access settings</span></span>

<span data-ttu-id="bb8bc-124">Teams には、ゲストアクセス用のマスターオン/オフスイッチ、およびチーム内でゲストが実行できることを制御するさまざまな設定があります。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-124">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="bb8bc-125">Teams でゲストアクセスを有効にする**には、** マスタースイッチで、 **teams でゲストアクセスを許可**する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-125">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="bb8bc-126">Teams でゲストアクセスが有効になっていることを確認し、ビジネスニーズに基づいてゲスト設定を調整してください。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-126">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="bb8bc-127">これらの設定はすべてのチームに影響を与えることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-127">Keep in mind that these settings affect all teams.</span></span>

![Teams ゲスト アクセスのトグルのスクリーンショット](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="bb8bc-129">Teams ゲストアクセス設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="bb8bc-129">To set Teams guest access settings</span></span>

1. <span data-ttu-id="bb8bc-130">Microsoft 365 管理センターにログイン[https://admin.microsoft.com](https://admin.microsoft.com)します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-130">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="bb8bc-131">左側のナビゲーションで、[**すべて表示**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-131">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="bb8bc-132">[**管理センター**] で [ **Teams**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-132">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="bb8bc-133">Teams 管理センターの左側のナビゲーションで、[**組織全体の設定**] を展開し、[**ゲストアクセス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-133">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="bb8bc-134">[ **Teams でのゲストアクセスを許可**する] が **[オン**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-134">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="bb8bc-135">追加のゲスト設定に必要な変更を加え、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-135">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="bb8bc-136">Teams のゲスト設定が有効になるまでに最大で24時間かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-136">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="bb8bc-137">Office 365 グループのゲスト設定</span><span class="sxs-lookup"><span data-stu-id="bb8bc-137">Office 365 Groups guest settings</span></span>

<span data-ttu-id="bb8bc-138">Teams では、チームメンバーシップに Office 365 グループを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-138">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="bb8bc-139">Teams でゲストアクセスを機能させるには、Office 365 グループのゲスト設定をオンにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-139">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Microsoft 365 管理センターにおける Office 365 グループのゲスト設定のスクリーンショット](media/office-365-groups-guest-settings.png)

<span data-ttu-id="bb8bc-141">Office 365 グループのゲスト設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="bb8bc-141">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="bb8bc-142">Microsoft 365 管理センターの左側のナビゲーションで、[**設定**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-142">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="bb8bc-143">[**サービス] [& アドイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-143">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="bb8bc-144">リストで、[ **Office 365 グループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-144">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="bb8bc-145">[組織外のユーザーにグループの**コンテンツへのアクセス**を許可する] および [**グループの所有者に組織外のユーザーをグループに追加する**] チェックボックスの両方がオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-145">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="bb8bc-146">変更を加えた場合は、[**変更の保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-146">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="bb8bc-147">SharePoint 組織レベルの共有設定</span><span class="sxs-lookup"><span data-stu-id="bb8bc-147">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="bb8bc-148">ファイル、フォルダー、リストなどの Teams コンテンツはすべて SharePoint に格納されます。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-148">Teams content such as files, folders, and lists are all stored in SharePoint.</span></span> <span data-ttu-id="bb8bc-149">ゲストがこれらのアイテムに Teams でアクセスできるようにするには、SharePoint の組織レベルの共有設定でゲストとの共有が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-149">In order for guests to have access to these items in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="bb8bc-150">組織レベルの設定は、teams に関連付けられたサイトを含む、個々のサイトで使用可能な設定を決定します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-150">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="bb8bc-151">サイトの設定は、組織レベルの設定よりも制限することはできません。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-151">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="bb8bc-152">認証されていないユーザーとのファイルとフォルダーの共有を許可する場合は、[**すべて**のユーザー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-152">If you want to allow file and folder sharing with unauthenticated people, choose **Anyone**.</span></span> <span data-ttu-id="bb8bc-153">すべてのゲストが認証を必要とするようにするには、[**新規および既存のゲスト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-153">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="bb8bc-154">組織内のすべてのサイトで必要とされる最も厳しい設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-154">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 組織レベルの共有設定のスクリーンショット](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="bb8bc-156">SharePoint 組織レベルの共有設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="bb8bc-156">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="bb8bc-157">Microsoft 365 管理センターで、左側のナビゲーションの [**管理センター**] の下にある [ **SharePoint**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-157">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="bb8bc-158">SharePoint 管理センターの左側のナビゲーションで、**[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-158">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="bb8bc-159">SharePoint の外部共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-159">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="bb8bc-160">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-160">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="bb8bc-161">SharePoint 組織レベルの既定のリンク設定</span><span class="sxs-lookup"><span data-stu-id="bb8bc-161">SharePoint organization level default link settings</span></span>

<span data-ttu-id="bb8bc-162">既定のファイルとフォルダーのリンク設定によって、ユーザーがファイルまたはフォルダーを共有するときに、どのリンクオプションが既定で表示されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-162">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="bb8bc-163">ユーザーは、必要に応じて、共有する前に、リンクの種類を他のオプションのいずれかに変更できます。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-163">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="bb8bc-164">この設定は、組織内のすべての teams および SharePoint サイトに影響を与えることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-164">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="bb8bc-165">ユーザーがファイルやフォルダーを共有するときに既定で選択されるリンクの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-165">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="bb8bc-166">**リンクを持つすべてのユーザー** -ファイルとフォルダーの認証されていない共有を頻繁に行う場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-166">**Anyone with the link** - Choose this option if you expect to do a lot of unauthenticated sharing of files and folders.</span></span> <span data-ttu-id="bb8bc-167">*すべて*のリンクを許可し、偶発的な認証されていない共有について懸念している場合は、他のオプションのいずれかを既定値として検討します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-167">If you want to allow *Anyone* links but are concerned about accidental unauthenticated sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="bb8bc-168">このリンクの種類は、**すべて**の共有を有効にした場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-168">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="bb8bc-169">[**組織内のユーザーのみ**]-ほとんどのファイルとフォルダーの共有が組織内のユーザーと想定される場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-169">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="bb8bc-170">**特定のユーザー** -多数のファイルとフォルダーをゲストで共有することが予想される場合は、このオプションを検討してください。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-170">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="bb8bc-171">この種類のリンクはゲストと連動しており、認証を必要とします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-171">This type of link works with guests and requires them to authenticate.</span></span>
 
![SharePoint における組織レベルのファイルとフォルダー設定のスクリーンショット](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="bb8bc-173">SharePoint 組織レベルの既定のリンク設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="bb8bc-173">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="bb8bc-174">SharePoint 管理センターの [共有] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-174">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="bb8bc-175">[**ファイルとフォルダーのリンク**] で、使用する既定の共有リンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-175">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="bb8bc-176">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-176">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="bb8bc-177">チームの作成</span><span class="sxs-lookup"><span data-stu-id="bb8bc-177">Create a team</span></span>

<span data-ttu-id="bb8bc-178">次の手順では、ゲストとの共同作業に使用する予定のチームを作成します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-178">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="bb8bc-179">チームを作成するには</span><span class="sxs-lookup"><span data-stu-id="bb8bc-179">To create a team</span></span>
1. <span data-ttu-id="bb8bc-180">Teams の [ **teams** ] タブで、左側のウィンドウの下部にある [**参加] または [チームの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-180">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="bb8bc-181">[**チームの作成] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-181">Click **Create a team**.</span></span>
3. <span data-ttu-id="bb8bc-182">[**チームの新規作成] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-182">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="bb8bc-183">[**プライベート**] または [**パブリック**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-183">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="bb8bc-184">チームの名前と説明を入力し、[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-184">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="bb8bc-185">[**スキップ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-185">Click **Skip**.</span></span>

<span data-ttu-id="bb8bc-186">後でユーザーを招待します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-186">We'll invite users later.</span></span> <span data-ttu-id="bb8bc-187">次に、チームに関連付けられている SharePoint サイトのサイトレベルでの共有設定を確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-187">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="bb8bc-188">SharePoint サイトレベルの共有設定</span><span class="sxs-lookup"><span data-stu-id="bb8bc-188">SharePoint site level sharing settings</span></span>

<span data-ttu-id="bb8bc-189">サイトレベルの共有設定をチェックして、このチームに必要なアクセスの種類が許可されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-189">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="bb8bc-190">たとえば、組織レベルの設定をすべての**ユーザー**に設定しているが、すべてのゲストがこのチームの認証を必要とする場合は、サイトレベルの共有設定が**新規および既存のゲスト**に設定されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-190">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![SharePoint サイトの外部共有設定のスクリーンショット](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="bb8bc-192">サイトレベルの共有設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="bb8bc-192">To set site-level sharing settings</span></span>
1. <span data-ttu-id="bb8bc-193">SharePoint 管理センターの左側のナビゲーションで、[**サイト**] を展開して [**アクティブなサイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-193">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="bb8bc-194">作成したチームのサイトを選択します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-194">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="bb8bc-195">リボンで [**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-195">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="bb8bc-196">共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-196">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="bb8bc-197">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-197">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="bb8bc-198">ユーザーを招待する</span><span class="sxs-lookup"><span data-stu-id="bb8bc-198">Invite users</span></span>

<span data-ttu-id="bb8bc-199">これでゲスト共有の設定が構成されるようになり、チームへの内部ユーザーとゲストの追加を開始できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-199">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="bb8bc-200">内部ユーザーをチームに招待するには</span><span class="sxs-lookup"><span data-stu-id="bb8bc-200">To invite internal users to a team</span></span>
1. <span data-ttu-id="bb8bc-201">チームで、[**その他**のオプション**\*\***] () をクリックし、[**メンバーの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-201">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="bb8bc-202">招待するユーザーの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-202">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="bb8bc-203">**[追加]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-203">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="bb8bc-204">ゲストをチームに招待するには</span><span class="sxs-lookup"><span data-stu-id="bb8bc-204">To invite guests to a team</span></span>
1. <span data-ttu-id="bb8bc-205">チームで、[**その他**のオプション**\*\***] () をクリックし、[**メンバーの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-205">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="bb8bc-206">招待するゲストの電子メールアドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-206">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="bb8bc-207">[**ゲスト情報の編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-207">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="bb8bc-208">ゲストの完全な名前を入力し、チェックマークをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-208">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="bb8bc-209">**[追加]** をクリックして、**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bb8bc-209">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb8bc-210">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb8bc-210">See Also</span></span>

[<span data-ttu-id="bb8bc-211">認証されていないユーザーとファイルおよびフォルダーを共有するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="bb8bc-211">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="bb8bc-212">ゲストと共有するときにファイルの偶発的な公開を制限する</span><span class="sxs-lookup"><span data-stu-id="bb8bc-212">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

[<span data-ttu-id="bb8bc-213">セキュリティで保護されたゲスト共有環境を作成する</span><span class="sxs-lookup"><span data-stu-id="bb8bc-213">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

[<span data-ttu-id="bb8bc-214">管理対象ゲストを使用して B2B エクストラネットを作成する</span><span class="sxs-lookup"><span data-stu-id="bb8bc-214">Create a B2B extranet with managed guests</span></span>](b2b-extranet.md)
