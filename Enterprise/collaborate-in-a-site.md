---
title: サイト内のゲストと共同作業する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: SharePoint サイトでゲストと共同作業する方法について説明します。
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017315"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="39a6b-103">サイト内のゲストと共同作業する</span><span class="sxs-lookup"><span data-stu-id="39a6b-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="39a6b-104">ドキュメント、データ、およびリスト間でゲストと共同作業を行う必要がある場合は、SharePoint サイトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="39a6b-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="39a6b-105">モダン SharePoint サイトは Office 365 グループに接続されており、サイトメンバーシップを管理したり、共有メールボックスや予定表などのその他のコラボレーションツールを提供したりできます。</span><span class="sxs-lookup"><span data-stu-id="39a6b-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="39a6b-106">この記事では、ゲストとのグループ作業のために SharePoint サイトをセットアップするために必要な Microsoft 365 の構成手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="39a6b-107">Azure の組織上の関係の設定</span><span class="sxs-lookup"><span data-stu-id="39a6b-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="39a6b-108">Microsoft 365 での共有は、Azure Active Directory の組織上の関係の設定によって最上位レベルで管理されます。</span><span class="sxs-lookup"><span data-stu-id="39a6b-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="39a6b-109">Azure AD でゲストの共有が無効または制限されている場合、これは Microsoft 365 で構成した共有設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="39a6b-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="39a6b-110">組織上の関係の設定を確認して、ゲストとの共有がブロックされないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="39a6b-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory の組織上の関係の設定ページのスクリーンショット](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="39a6b-112">組織上の関係の設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="39a6b-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="39a6b-113">Microsoft Azure にログイン[https://portal.azure.com](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="39a6b-114">左側のナビゲーションで、[ **Azure Active Directory**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="39a6b-115">[**概要**] ウィンドウで、[組織上の**関係**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="39a6b-116">[組織上の**関係**] ウィンドウで、[**設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="39a6b-117">**管理者とゲスト招待元役割のユーザーが招待できる**ことと、**メンバーが招待**できることを確認します。どちらも **[はい]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="39a6b-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="39a6b-118">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="39a6b-119">[**共同作業の制限**] セクションの設定に注意してください。</span><span class="sxs-lookup"><span data-stu-id="39a6b-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="39a6b-120">共同作業を行うゲストのドメインがブロックされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="39a6b-121">Office 365 グループのゲスト設定</span><span class="sxs-lookup"><span data-stu-id="39a6b-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="39a6b-122">モダン SharePoint サイトは、Office 365 グループを使用してサイトアクセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="39a6b-123">SharePoint サイトでゲストアクセスを機能させるには、Office 365 グループのゲスト設定をオンにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39a6b-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Microsoft 365 管理センターの Office 365 グループのゲスト設定のスクリーンショット](media/office-365-groups-guest-settings.png)

<span data-ttu-id="39a6b-125">Office 365 グループのゲスト設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="39a6b-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="39a6b-126">Microsoft 365 管理センターの左側のナビゲーションで、[**設定**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="39a6b-127">[**サービス] [& アドイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="39a6b-128">リストで、[ **Office 365 グループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="39a6b-129">[組織外のユーザーにグループの**コンテンツへのアクセス**を許可する] および [**グループの所有者に組織外のユーザーをグループに追加する**] チェックボックスの両方がオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="39a6b-130">変更を加えた場合は、[**変更の保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="39a6b-131">SharePoint 組織レベルの共有設定</span><span class="sxs-lookup"><span data-stu-id="39a6b-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="39a6b-132">ゲストが SharePoint サイトにアクセスできるようにするには、SharePoint の組織レベルの共有設定でゲストとの共有が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39a6b-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="39a6b-133">組織レベルの設定によって、個々のサイトで使用可能な設定が決まります。</span><span class="sxs-lookup"><span data-stu-id="39a6b-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="39a6b-134">サイトの設定は、組織レベルの設定よりも制限することはできません。</span><span class="sxs-lookup"><span data-stu-id="39a6b-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="39a6b-135">匿名ユーザーとのファイルとフォルダーの共有を許可する場合は、[**すべて**のユーザー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="39a6b-136">すべてのゲストが認証を必要とするようにするには、[**新規および既存のゲスト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="39a6b-137">組織内のすべてのサイトで必要とされる最も厳しい設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 組織レベルの共有設定のスクリーンショット](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="39a6b-139">SharePoint 組織レベルの共有設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="39a6b-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="39a6b-140">Microsoft 365 管理センターで、左側のナビゲーションの [**管理センター**] の下にある [ **SharePoint**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="39a6b-141">SharePoint 管理センターの左側のナビゲーションで、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="39a6b-142">SharePoint の外部共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="39a6b-143">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-143">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="39a6b-144">サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="39a6b-144">Create a site</span></span>

<span data-ttu-id="39a6b-145">次の手順では、ゲストとの共同作業に使用する予定のサイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-145">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="39a6b-146">サイトを作成するには</span><span class="sxs-lookup"><span data-stu-id="39a6b-146">To create a site</span></span>
1. <span data-ttu-id="39a6b-147">SharePoint 管理センターの [**サイト**] で、[**アクティブなサイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-147">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="39a6b-148">[**作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-148">Click **Create**.</span></span>
3. <span data-ttu-id="39a6b-149">[**チームサイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-149">Click **Team site**.</span></span>
4. <span data-ttu-id="39a6b-150">サイト名を入力し、グループの所有者 (サイト所有者) の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-150">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="39a6b-151">[**詳細設定**] で、これをパブリックサイトまたはプライベートサイトにするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-151">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="39a6b-152">[ **次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-152">Click **Next**.</span></span>
7. <span data-ttu-id="39a6b-153">[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-153">Click **Finish**.</span></span>

<span data-ttu-id="39a6b-154">後でユーザーを招待します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-154">We'll invite users later.</span></span> <span data-ttu-id="39a6b-155">次に、このサイトのサイトレベルでの共有設定を確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="39a6b-155">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="39a6b-156">SharePoint サイトレベルの共有設定</span><span class="sxs-lookup"><span data-stu-id="39a6b-156">SharePoint site level sharing settings</span></span>

<span data-ttu-id="39a6b-157">サイトレベルの共有設定をチェックして、このサイトに必要なアクセスの種類が許可されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="39a6b-157">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="39a6b-158">たとえば、組織レベルの設定をすべての**ユーザー**に設定した場合に、すべてのゲストがこのサイトの認証を行うようにするには、サイトレベルの共有設定が**新規および既存のゲスト**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-158">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="39a6b-159">匿名ユーザー (**すべて**のユーザーの設定) とサイトを共有することはできませんが、個別のファイルとフォルダーを使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="39a6b-159">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![SharePoint サイトの外部共有設定のスクリーンショット](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="39a6b-161">サイトレベルの共有設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="39a6b-161">To set site-level sharing settings</span></span>
1. <span data-ttu-id="39a6b-162">SharePoint 管理センターの左側のナビゲーションで、[**サイト**] を展開し、[**アクティブなサイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-162">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="39a6b-163">作成したサイトを選択します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-163">Select the site that you just created.</span></span>
3. <span data-ttu-id="39a6b-164">リボンの [**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-164">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="39a6b-165">共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-165">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="39a6b-166">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-166">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="39a6b-167">ユーザーを招待する</span><span class="sxs-lookup"><span data-stu-id="39a6b-167">Invite users</span></span>

<span data-ttu-id="39a6b-168">ゲスト共有の設定が構成されるようになったため、内部ユーザーとゲストのサイトへの追加を開始できます。</span><span class="sxs-lookup"><span data-stu-id="39a6b-168">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="39a6b-169">サイトアクセスは、関連付けられた Office 365 グループを通じて制御されるため、ユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-169">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="39a6b-170">内部ユーザーをグループに招待するには</span><span class="sxs-lookup"><span data-stu-id="39a6b-170">To invite internal users to a group</span></span>
1. <span data-ttu-id="39a6b-171">ユーザーを追加するサイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="39a6b-171">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="39a6b-172">右上の [**メンバー** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-172">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="39a6b-173">**[メンバーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-173">Click **Add members**.</span></span>
4. <span data-ttu-id="39a6b-174">サイトに招待するユーザーの名前または電子メールアドレスを入力し、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-174">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="39a6b-175">ゲストユーザーをサイトから追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="39a6b-175">Guest users can't be added from the site.</span></span> <span data-ttu-id="39a6b-176">Web 上の Outlook を使用してそれらを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39a6b-176">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="39a6b-177">サイトにゲストを招待するには</span><span class="sxs-lookup"><span data-stu-id="39a6b-177">To invite guests to a site</span></span>
1. <span data-ttu-id="39a6b-178">Web 上の Outlook の [**グループ**] で、メンバーを追加するグループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-178">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="39a6b-179">グループの連絡先カードを開いて、[**その他のオプション**(...)] の下にある [**メンバーの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-179">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="39a6b-180">招待するゲストの電子メールアドレスを入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-180">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="39a6b-181">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39a6b-181">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="39a6b-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="39a6b-182">See Also</span></span>
