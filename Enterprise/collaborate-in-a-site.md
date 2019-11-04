---
title: サイトでゲストと共同で作業する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: SharePoint サイトでゲストと共同作業する方法について説明します。
ms.openlocfilehash: d0f4528db683795da0f3c949228f902d775f6b7e
ms.sourcegitcommit: f4469fee3e3f9665298d3052f30a4c6ab12643f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "37920170"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="d67fb-103">サイトでゲストと共同で作業する</span><span class="sxs-lookup"><span data-stu-id="d67fb-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="d67fb-104">ドキュメント、データ、およびリスト間でゲストと共同作業を行う必要がある場合は、SharePoint サイトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d67fb-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="d67fb-105">モダン SharePoint サイトは Office 365 グループに接続されており、サイトメンバーシップを管理したり、共有メールボックスや予定表などのその他のコラボレーションツールを提供したりできます。</span><span class="sxs-lookup"><span data-stu-id="d67fb-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="d67fb-106">この記事では、ゲストとのグループ作業のために SharePoint サイトをセットアップするために必要な Microsoft 365 の構成手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="d67fb-107">ビデオ デモンストレーション</span><span class="sxs-lookup"><span data-stu-id="d67fb-107">Video demonstration</span></span>

<span data-ttu-id="d67fb-108">このビデオでは、このドキュメントで説明されている構成手順を示します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-108">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="d67fb-109">Azure の組織上の関係の設定</span><span class="sxs-lookup"><span data-stu-id="d67fb-109">Azure Organizational relationships settings</span></span>

<span data-ttu-id="d67fb-110">Microsoft 365 での共有は、Azure Active Directory の組織上の関係の設定によって最上位レベルで管理されます。</span><span class="sxs-lookup"><span data-stu-id="d67fb-110">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="d67fb-111">Azure AD でゲストの共有が無効または制限されている場合、これは Microsoft 365 で構成した共有設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="d67fb-111">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="d67fb-112">組織上の関係の設定を確認して、ゲストとの共有がブロックされないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d67fb-112">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Azure Active Directory における組織の関係の設定ページのスクリーンショット](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="d67fb-114">組織上の関係の設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="d67fb-114">To set organizational relationship settings</span></span>

1. <span data-ttu-id="d67fb-115">Microsoft Azure にログイン[https://portal.azure.com](https://portal.azure.com)します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-115">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="d67fb-116">左側のナビゲーションで、[ **Azure Active Directory**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-116">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="d67fb-117">[**概要**] ウィンドウで、[組織上の**関係**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-117">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="d67fb-118">[組織上の**関係**] ウィンドウで、[**設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-118">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="d67fb-119">**管理者とゲスト招待元役割のユーザーが招待できる**ことと、**メンバーが招待**できることを確認します。どちらも **[はい]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="d67fb-119">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="d67fb-120">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-120">If you made changes, click **Save**.</span></span>

<span data-ttu-id="d67fb-121">[**共同作業の制限**] セクションの設定に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d67fb-121">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="d67fb-122">共同作業を行うゲストのドメインがブロックされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-122">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="d67fb-123">Office 365 グループのゲスト設定</span><span class="sxs-lookup"><span data-stu-id="d67fb-123">Office 365 Groups guest settings</span></span>

<span data-ttu-id="d67fb-124">モダン SharePoint サイトは、Office 365 グループを使用してサイトアクセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-124">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="d67fb-125">SharePoint サイトでゲストアクセスを機能させるには、Office 365 グループのゲスト設定をオンにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d67fb-125">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Microsoft 365 管理センターにおける Office 365 グループのゲスト設定のスクリーンショット](media/office-365-groups-guest-settings.png)

<span data-ttu-id="d67fb-127">Office 365 グループのゲスト設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="d67fb-127">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="d67fb-128">Microsoft 365 管理センターの左側のナビゲーションで、[**設定**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-128">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="d67fb-129">[**サービス] [& アドイン**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-129">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="d67fb-130">リストで、[ **Office 365 グループ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-130">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="d67fb-131">[組織外のユーザーにグループの**コンテンツへのアクセス**を許可する] および [**グループの所有者に組織外のユーザーをグループに追加する**] チェックボックスの両方がオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-131">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="d67fb-132">変更を加えた場合は、[**変更の保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-132">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="d67fb-133">SharePoint 組織レベルの共有設定</span><span class="sxs-lookup"><span data-stu-id="d67fb-133">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="d67fb-134">ゲストが SharePoint サイトにアクセスできるようにするには、SharePoint の組織レベルの共有設定でゲストとの共有が許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d67fb-134">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="d67fb-135">組織レベルの設定によって、個々のサイトで使用可能な設定が決まります。</span><span class="sxs-lookup"><span data-stu-id="d67fb-135">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="d67fb-136">サイトの設定は、組織レベルの設定よりも制限することはできません。</span><span class="sxs-lookup"><span data-stu-id="d67fb-136">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="d67fb-137">匿名ユーザーとのファイルとフォルダーの共有を許可する場合は、[**すべて**のユーザー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-137">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="d67fb-138">すべてのゲストが認証を必要とするようにするには、[**新規および既存のゲスト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-138">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="d67fb-139">組織内のすべてのサイトで必要とされる最も厳しい設定を選択します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-139">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![SharePoint 組織レベルの共有設定のスクリーンショット](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="d67fb-141">SharePoint 組織レベルの共有設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="d67fb-141">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="d67fb-142">Microsoft 365 管理センターで、左側のナビゲーションの [**管理センター**] の下にある [ **SharePoint**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-142">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="d67fb-143">SharePoint 管理センターの左側のナビゲーションで、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-143">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="d67fb-144">SharePoint の外部共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-144">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="d67fb-145">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-145">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="d67fb-146">サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="d67fb-146">Create a site</span></span>

<span data-ttu-id="d67fb-147">次の手順では、ゲストとの共同作業に使用する予定のサイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-147">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="d67fb-148">サイトを作成するには</span><span class="sxs-lookup"><span data-stu-id="d67fb-148">To create a site</span></span>
1. <span data-ttu-id="d67fb-149">SharePoint 管理センターの [**サイト**] で、[**アクティブなサイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-149">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="d67fb-150">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-150">Click **Create**.</span></span>
3. <span data-ttu-id="d67fb-151">[**チームサイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-151">Click **Team site**.</span></span>
4. <span data-ttu-id="d67fb-152">サイト名を入力し、グループの所有者 (サイト所有者) の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-152">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="d67fb-153">[**詳細設定**] で、これをパブリックサイトまたはプライベートサイトにするかどうかを選択します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-153">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="d67fb-154">[ **次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-154">Click **Next**.</span></span>
7. <span data-ttu-id="d67fb-155">[**完了**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-155">Click **Finish**.</span></span>

<span data-ttu-id="d67fb-156">後でユーザーを招待します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-156">We'll invite users later.</span></span> <span data-ttu-id="d67fb-157">次に、このサイトのサイトレベルでの共有設定を確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="d67fb-157">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="d67fb-158">SharePoint サイトレベルの共有設定</span><span class="sxs-lookup"><span data-stu-id="d67fb-158">SharePoint site level sharing settings</span></span>

<span data-ttu-id="d67fb-159">サイトレベルの共有設定をチェックして、このサイトに必要なアクセスの種類が許可されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d67fb-159">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="d67fb-160">たとえば、組織レベルの設定をすべての**ユーザー**に設定した場合に、すべてのゲストがこのサイトの認証を行うようにするには、サイトレベルの共有設定が**新規および既存のゲスト**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-160">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="d67fb-161">匿名ユーザー (**すべて**のユーザーの設定) とサイトを共有することはできませんが、個別のファイルとフォルダーを使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="d67fb-161">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![SharePoint サイトの外部共有設定のスクリーンショット](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="d67fb-163">サイトレベルの共有設定を設定するには</span><span class="sxs-lookup"><span data-stu-id="d67fb-163">To set site-level sharing settings</span></span>
1. <span data-ttu-id="d67fb-164">SharePoint 管理センターの左側のナビゲーションで、[**サイト**] を展開して [**アクティブなサイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-164">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="d67fb-165">作成したサイトを選択します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-165">Select the site that you just created.</span></span>
3. <span data-ttu-id="d67fb-166">リボンで [**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-166">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="d67fb-167">共有が [**すべてのユーザー** ] または **[既存のゲスト**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-167">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="d67fb-168">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-168">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="d67fb-169">ユーザーを招待する</span><span class="sxs-lookup"><span data-stu-id="d67fb-169">Invite users</span></span>

<span data-ttu-id="d67fb-170">ゲスト共有の設定が構成されるようになったため、内部ユーザーとゲストのサイトへの追加を開始できます。</span><span class="sxs-lookup"><span data-stu-id="d67fb-170">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="d67fb-171">サイトアクセスは、関連付けられた Office 365 グループを通じて制御されるため、ユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-171">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="d67fb-172">内部ユーザーをグループに招待するには</span><span class="sxs-lookup"><span data-stu-id="d67fb-172">To invite internal users to a group</span></span>
1. <span data-ttu-id="d67fb-173">ユーザーを追加するサイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="d67fb-173">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="d67fb-174">右上の [**メンバー** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-174">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="d67fb-175">**[メンバーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-175">Click **Add members**.</span></span>
4. <span data-ttu-id="d67fb-176">サイトに招待するユーザーの名前または電子メールアドレスを入力し、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-176">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="d67fb-177">ゲストユーザーをサイトから追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="d67fb-177">Guest users can't be added from the site.</span></span> <span data-ttu-id="d67fb-178">Web 上の Outlook を使用してそれらを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d67fb-178">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="d67fb-179">サイトにゲストを招待するには</span><span class="sxs-lookup"><span data-stu-id="d67fb-179">To invite guests to a site</span></span>
1. <span data-ttu-id="d67fb-180">Web 上の Outlook の [**グループ**] で、メンバーを追加するグループをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-180">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="d67fb-181">グループの連絡先カードを開いて、[**その他のオプション**(...)] の下にある [**メンバーの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-181">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="d67fb-182">招待するゲストの電子メールアドレスを入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-182">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="d67fb-183">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d67fb-183">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="d67fb-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="d67fb-184">See Also</span></span>

[<span data-ttu-id="d67fb-185">匿名ユーザーとファイルおよびフォルダーを共有するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="d67fb-185">Best practices for sharing files and folders with anonymous users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="d67fb-186">ゲストと共有するときにファイルの偶発的な公開を制限する</span><span class="sxs-lookup"><span data-stu-id="d67fb-186">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

<span data-ttu-id="d67fb-187">[セキュリティで保護されたゲスト共有環境を作成する](create-a-secure-guest-sharing-environment.md))</span><span class="sxs-lookup"><span data-stu-id="d67fb-187">[Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md))</span></span>

