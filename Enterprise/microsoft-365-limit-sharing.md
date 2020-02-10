---
title: Microsoft 365 の共有を制限する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
search.appverid:
- SPO160
- MET150
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Microsoft 365 で共有を制限または無効にするオプションについて説明します。
ms.openlocfilehash: 8e0488aae1d30d33b9046d4372707eb8d8635860
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844918"
---
# <a name="limit-sharing-in-microsoft-365"></a><span data-ttu-id="3cac0-103">Microsoft 365 の共有を制限する</span><span class="sxs-lookup"><span data-stu-id="3cac0-103">Limit sharing in Microsoft 365</span></span>

<span data-ttu-id="3cac0-104">内部共有を完全に無効にすることや、サイトから [共有] ボタンを削除することはできませんが、組織のニーズを満たすように Microsoft 365 の共有を制限する方法は多数あります。</span><span class="sxs-lookup"><span data-stu-id="3cac0-104">While you can't disable internal sharing entirely or remove the Share button from sites, there are a variety of ways that you can limit sharing in Microsoft 365 to meet the needs of your organization.</span></span>

<span data-ttu-id="3cac0-105">次の表に、ファイルの共有方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-105">The methods of sharing files are listed in the table below.</span></span> <span data-ttu-id="3cac0-106">詳細については、「**共有方法**」列のリンクをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="3cac0-106">Click the link in the **Sharing method** column for detailed information.</span></span>

|<span data-ttu-id="3cac0-107">共有方法</span><span class="sxs-lookup"><span data-stu-id="3cac0-107">Sharing method</span></span>|<span data-ttu-id="3cac0-108">説明</span><span class="sxs-lookup"><span data-stu-id="3cac0-108">Description</span></span>|<span data-ttu-id="3cac0-109">制限のオプション</span><span class="sxs-lookup"><span data-stu-id="3cac0-109">Limiting options</span></span>|
|:-------------|:----------|:-------------|
|[<span data-ttu-id="3cac0-110">Office 365 グループまたはチーム</span><span class="sxs-lookup"><span data-stu-id="3cac0-110">Office 365 group or team</span></span>](#office-365-group-or-team)|<span data-ttu-id="3cac0-111">Microsoft Teams チームまたは Office 365 グループへのアクセスを許可されているユーザーは、関連付けられた SharePoint サイトのファイルに対する編集アクセス許可を持ちます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-111">People granted access to a Microsoft Teams team or Office 365 group have edit access to files in the associated SharePoint site.</span></span>|<span data-ttu-id="3cac0-112">グループまたはチームがプライベートの場合は、チームに参加するための共有の招待は承認を得るために所有者に回送されます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-112">If the group or team is private, sharing invitations to join the team go to the owner for approval.</span></span> <span data-ttu-id="3cac0-113">管理者は、組織の部外者からのアクセスを禁止するために、ゲスト アクセスを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-113">Admins can disable guest access to prevent access by people from outside the organization.</span></span>|
|[<span data-ttu-id="3cac0-114">SharePoint サイト</span><span class="sxs-lookup"><span data-stu-id="3cac0-114">SharePoint site</span></span>](#sharepoint-site)|<span data-ttu-id="3cac0-115">ユーザーには SharePoint サイトに対する所有者、メンバー、または閲覧者のアクセス権を付与できます。ユーザーは、サイト内のファイルに対して、そのレベルに応じたアクセス権を持ちます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-115">People can be granted Owner, Member, or Visitor access to a SharePoint site and will have that level of access to files in the site.</span></span>|<span data-ttu-id="3cac0-116">サイトのアクセス許可は、サイトの所有者のみがサイトの共有を可能にするように制限できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-116">Site permissions can be restricted so that only site owners can share the site.</span></span>|
|[<span data-ttu-id="3cac0-117">特定のユーザーとの共有</span><span class="sxs-lookup"><span data-stu-id="3cac0-117">Sharing with specific people</span></span>](#sharing-with-specific-people)|<span data-ttu-id="3cac0-118">サイトのメンバーと編集アクセス許可を持つユーザーは、*特定のユーザー* リンクを使用することで、ファイルおよびフォルダーへの直接のアクセス許可を付与することや共有することができます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-118">Site members and people with edit permissions can give direct permissions to files and folders or share them by using *Specific people* links.</span></span>|<span data-ttu-id="3cac0-119">サイトのアクセス許可は、サイトの所有者のみがファイルおよびフォルダーの共有を可能にするように制限できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-119">Site permissions can be restricted so that only site owners can share files and folders.</span></span> <span data-ttu-id="3cac0-120">この場合、サイトのメンバーによる直接アクセス権および*特定のユーザー* リンクの共有は、承認を得るためにサイト所有者に回送されます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-120">In this case, direct access and *Specific people* link sharing by site members goes to site owner for approval.</span></span>|
|[<span data-ttu-id="3cac0-121">SharePoint ゲスト共有</span><span class="sxs-lookup"><span data-stu-id="3cac0-121">SharePoint guest sharing</span></span>](#sharepoint-guest-sharing)|<span data-ttu-id="3cac0-122">SharePoint サイトの所有者とメンバーは、組織外のユーザーとファイルおよびフォルダーを共有できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-122">SharePoint site owners and members can share files and folders with people outside the organization.</span></span>|<span data-ttu-id="3cac0-123">ゲスト共有は組織全体または個別のサイトごとに無効化できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-123">Guest sharing can be disabled for the entire organization or for individual sites.</span></span>|
|[<span data-ttu-id="3cac0-124">*組織内のユーザー*共有リンク</span><span class="sxs-lookup"><span data-stu-id="3cac0-124">*People in your organization* sharing links</span></span>](#people-in-your-organization-sharing-links)|<span data-ttu-id="3cac0-125">SharePoint サイトの所有者とメンバーは、*組織内のユーザー* リンクを使用することでファイルを共有できます。このリンクは、組織内のすべてのユーザーに対して機能します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-125">SharePoint site owners and members can share files using *People in your organization* links, which will work for anyone inside the organization.</span></span>|<span data-ttu-id="3cac0-126">*組織内のユーザー* リンクは、サイト レベルで無効化できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-126">*People in your organization* links can be disabled at the site level.</span></span>|
|[<span data-ttu-id="3cac0-127">電子メール</span><span class="sxs-lookup"><span data-stu-id="3cac0-127">Email</span></span>](#email)|<span data-ttu-id="3cac0-128">ファイルにアクセスできるユーザーは、そのファイルを電子メールで別のユーザーに送信できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-128">People with access to a file can send it to others via email.</span></span>|<span data-ttu-id="3cac0-129">管理者は、秘密度ラベルを使用してファイルを暗号化することで、許可されていないユーザーとのファイルの共有を防止できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-129">Admins can encrypt files by using sensitivity labels to prevent them being shared with unauthorized people.</span></span>|
|[<span data-ttu-id="3cac0-130">ダウンロードまたはファイルのコピー</span><span class="sxs-lookup"><span data-stu-id="3cac0-130">Download or file copy</span></span>](#download-or-file-copy)|<span data-ttu-id="3cac0-131">ファイルにアクセスできるユーザーは、ファイルをダウンロードまたはコピーして Microsoft 365 の適用範囲外のユーザーと共有できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-131">People with access to a file can download or copy it and share it with others outside the scope of Microsoft 365.</span></span>|<span data-ttu-id="3cac0-132">管理者は、秘密度ラベルを使用してファイルを暗号化することで、許可されていないユーザーとのファイルの共有を防止できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-132">Admins can encrypt files by using sensitivity labels to prevent them being shared with unauthorized people.</span></span>|

<span data-ttu-id="3cac0-133">組織内の共有は、この記事で説明する管理者コントロールを使用して制限できますが、安全な共有環境を作成するために Microsoft 365 で使用可能なセキュリティとコンプライアンスの機能を使用することを検討するようお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-133">While you can use the admin controls described in this article to limit sharing in your organization, we highly recommend that you consider using the security and compliance features available in Microsoft 365 to create a secure sharing environment.</span></span> <span data-ttu-id="3cac0-134">詳細については、「[Microsoft 365 による SharePoint のファイルの共同作業](https://docs.microsoft.com/sharepoint/deploy-file-collaboration)」と「[厳しく規制されたデータに Teams で対応する](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cac0-134">See [File collaboration in SharePoint with Microsoft 365](https://docs.microsoft.com/sharepoint/deploy-file-collaboration) and [Teams for highly regulated data](https://docs.microsoft.com/microsoft-365/enterprise/secure-teams-highly-regulated-data-scenario) for information.</span></span>

<span data-ttu-id="3cac0-135">組織内で使用されている共有方法を理解するには、[ファイルとフォルダーの共有に関するレポートを実行](https://docs.microsoft.com/sharepoint/sharing-reports)してください。</span><span class="sxs-lookup"><span data-stu-id="3cac0-135">To understand how sharing is being used in your organization, [run a report on file and folder sharing](https://docs.microsoft.com/sharepoint/sharing-reports).</span></span>

## <a name="office-365-group-or-team"></a><span data-ttu-id="3cac0-136">Office 365 グループまたはチーム</span><span class="sxs-lookup"><span data-stu-id="3cac0-136">Office 365 group or team</span></span>

<span data-ttu-id="3cac0-137">Office 365 グループまたは Microsoft Teams チームで共有を制限する場合は、グループまたはチームをプライベートにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="3cac0-137">If you want to limit sharing in an Office 365 group or Microsoft Teams team, it's important to make the group or team private.</span></span> <span data-ttu-id="3cac0-138">組織内のユーザーは、パブリック グループまたはチームにいつでも参加できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-138">People inside your organization can join a public group or team anytime.</span></span> <span data-ttu-id="3cac0-139">グループまたはチームをプライベートにしていないと、チームの共有またはそのファイルの組織内での共有を制限する方法がなくなります。</span><span class="sxs-lookup"><span data-stu-id="3cac0-139">Unless the group or team is private, there's no way to limit sharing of the team or its files within the organization.</span></span>

### <a name="guest-sharing"></a><span data-ttu-id="3cac0-140">ゲスト共有</span><span class="sxs-lookup"><span data-stu-id="3cac0-140">Guest sharing</span></span>

<span data-ttu-id="3cac0-141">Teams のゲスト アクセスを禁止する場合は、Teams 管理センターでゲスト共有をオフにします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-141">If you want to prevent guest access in Teams, you can turn off guest sharing in the Teams admin center.</span></span>

<span data-ttu-id="3cac0-142">Teams のゲスト共有をオフにするには</span><span class="sxs-lookup"><span data-stu-id="3cac0-142">To turn off guest sharing for Teams</span></span>
1. <span data-ttu-id="3cac0-143">Teams 管理センターで、**[組織全体の設定]** を展開して **[ゲスト アクセス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-143">In the Teams admin center, expand **Org-wide settings**, and then click **Guest access**.</span></span>
2. <span data-ttu-id="3cac0-144">**[Teams のゲスト アクセスを許可する]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-144">Turn off **Allow guest access in Teams**.</span></span>
3. <span data-ttu-id="3cac0-145">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-145">Click **Save**.</span></span>

<span data-ttu-id="3cac0-146">Office 365 グループのゲスト アクセスを禁止する場合は、Microsoft 365 管理センターでグループのゲスト アクセス設定をオフにします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-146">If you want to prevent guest access in Office 365 groups, you can turn off the groups guest access settings in the Microsoft 365 admin center.</span></span>

<span data-ttu-id="3cac0-147">Office 365 グループのゲスト共有をオフにするには</span><span class="sxs-lookup"><span data-stu-id="3cac0-147">To turn off guest sharing in Office 365 groups</span></span>
1. <span data-ttu-id="3cac0-148">Microsoft 365 管理センターで、**[設定]** をクリックしてから **[設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-148">In the Microsoft 365 admin center, click **Settings**, and then click **Settings**.</span></span>
2. <span data-ttu-id="3cac0-149">**[サービス]** タブで、**[Office 365 グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-149">On the **Services** tab, click **Office 365 Groups**.</span></span>
3. <span data-ttu-id="3cac0-150">チェックボックスの **[組織外のグループ メンバーがグループ コンテンツにアクセスできるようにします]** と **[グループの所有者が組織外のユーザーをグループに追加できるようにします]** をオフにします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-150">Clear the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes.</span></span>
4. <span data-ttu-id="3cac0-151">**[変更の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-151">Click **Save changes**.</span></span>

    ![Microsoft 365 管理センターの Office 365 グループ共有設定のスクリーンショット](media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> <span data-ttu-id="3cac0-153">特定のグループまたはチームのゲスト共有を禁止する場合には、Microsoft PowerShell を使用します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-153">If you want to prevent guest sharing for a particular group or team, you can do so by using Microsoft PowerShell.</span></span> <span data-ttu-id="3cac0-154">詳細については、「[特定のグループに対してゲスト ユーザーをブロックする](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cac0-154">See [Block guest users from a specific group](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups?view=o365-worldwide#block-guest-users-from-a-specific-group) for details.</span></span>

<span data-ttu-id="3cac0-155">特定のドメインのユーザーに対するゲスト共有は、Azure Active Directory でドメインを許可またはブロックすることで制限できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-155">You can limit guest sharing to users from specific domains by allowing or blocking domains in Azure Active Directory.</span></span> <span data-ttu-id="3cac0-156">[SharePoint および OneDrive の Azure AD B2B との統合](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)を有効にしている場合、この制限は SharePoint のゲスト共有にも影響します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-156">This will also affect guest sharing in SharePoint if you have enabled [SharePoint and OneDrive integration with Azure AD B2B](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview).</span></span>

<span data-ttu-id="3cac0-157">特定のドメインからの共有招待状のみを許可するには</span><span class="sxs-lookup"><span data-stu-id="3cac0-157">To allow sharing invitations only from specified domains</span></span>
1. <span data-ttu-id="3cac0-158">Azure Active Directory の [概要] ページで、**[組織の関係]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-158">In Azure Active Directory, on the Overview page, click **Organizational relationships**.</span></span>
2. <span data-ttu-id="3cac0-159">**[設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-159">Click **Settings**.</span></span>
3. <span data-ttu-id="3cac0-160">**[コラボレーションの制限]** の下側にある **[指定したドメインのへの招待を拒否します]** または **[指定したドメインに対してのみ招待を許可します]** を選択して、その設定に使用するドメインを入力します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-160">Under **Collaboration restrictions**, select **Deny invitations to the specified domains** or **Allow invitations only to the specified domains**, and then type the domains that you want to use.</span></span>
4. <span data-ttu-id="3cac0-161">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-161">Click **Save**.</span></span>

    ![Azure Active Directory の [コラボレーションの制限] 設定のスクリーンショット](media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a><span data-ttu-id="3cac0-163">SharePoint サイト</span><span class="sxs-lookup"><span data-stu-id="3cac0-163">SharePoint site</span></span>

<span data-ttu-id="3cac0-164">SharePoint サイトの共有は、サイト所有者のみに制限できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-164">You can limit SharePoint site sharing to site owners only.</span></span> <span data-ttu-id="3cac0-165">これにより、サイト メンバーはサイトの共有ができなくなります。</span><span class="sxs-lookup"><span data-stu-id="3cac0-165">This prevents site members from sharing the site.</span></span> <span data-ttu-id="3cac0-166">サイトが Office 365 グループに接続されていると、グループ メンバーは別のユーザーをグループに招待できます。そのように招待したユーザーはサイトにアクセスできるようになる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3cac0-166">Keep in mind that if the site is connected to an Office 365 group, group members can invite others to the group and those users will have site access.</span></span>

<span data-ttu-id="3cac0-167">サイト共有を所有者に制限するには</span><span class="sxs-lookup"><span data-stu-id="3cac0-167">To limit site sharing to owners</span></span>
1. <span data-ttu-id="3cac0-168">サイトにある歯車アイコンをクリックして、**[サイトの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-168">In the site, click the gear icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="3cac0-169">**[共有の設定]** の下側にある **[共有設定を変更します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-169">Under **Sharing settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="3cac0-170">**[サイトの所有者とメンバー、および編集アクセス許可を持つユーザーは、ファイルとフォルダーを共有できますが、サイトの所有者のみがサイトを共有できます]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-170">Select **Site owners and members, and people with Edit permissions can share files and folders, but only site owners can share the site**.</span></span>
4. <span data-ttu-id="3cac0-171">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-171">Click **Save**.</span></span>

    ![SharePoint サイトの [共有アクセス許可] 設定のスナップショット](media/sharepoint-site-sharing-permissions-level-two.png)

<span data-ttu-id="3cac0-173">サイトのメンバー以外のユーザーによるアクセスの要求は、アクセス要求をオフにすることで禁止できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-173">You can prevent users who are not members of the site from requesting access by turning off access requests.</span></span>

<span data-ttu-id="3cac0-174">アクセス要求をオフにするには</span><span class="sxs-lookup"><span data-stu-id="3cac0-174">To turn off access requests</span></span>
1. <span data-ttu-id="3cac0-175">サイトにある歯車アイコンをクリックして、**[サイトの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-175">In the site, click the gear icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="3cac0-176">**[共有の設定]** の下側にある **[共有設定を変更します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-176">Under **Sharing settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="3cac0-177">**[アクセス要求の許可]** をオフにして、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-177">Turn off **Allow access requests**, and then click **Save**.</span></span>

<span data-ttu-id="3cac0-178">サイトの共有は、そのサイトに対してドメインを許可またはブロックすることで特定のドメインに制限できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-178">You can limit site sharing to specific domains by allowing or blocking domains for the site.</span></span>

<span data-ttu-id="3cac0-179">ドメイン単位でサイトの共有を制限するには</span><span class="sxs-lookup"><span data-stu-id="3cac0-179">To limit site sharing by domain</span></span>
1. <span data-ttu-id="3cac0-180">SharePoint 管理センターで、**[サイト]** の下側にある **[アクティブなサイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-180">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="3cac0-181">構成するサイトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-181">Click the site that you want to configure.</span></span>
3. <span data-ttu-id="3cac0-182">**[ポリシー]** タブで、**[外部共有]** の下側にある **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-182">On the **Policies** tab, under **External sharing** click **Edit**.</span></span>
4. <span data-ttu-id="3cac0-183">**[外部共有の詳細設定]** の下側にある **[ドメインで外部共有を制限する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-183">Under **Advanced settings for external sharing**, select the **Limit sharing by domain**.</span></span>
5. <span data-ttu-id="3cac0-184">許可またはブロックするドメインを追加して、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-184">Add the domains that you want to allow or block, and then click **Save**.</span></span>
6. <span data-ttu-id="3cac0-185">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-185">Click **Save**.</span></span>

    ![許可されたドメインのサイトレベル設定のスクリーンショット](media/limit-site-sharing-by-domain.png)

## <a name="sharing-with-specific-people"></a><span data-ttu-id="3cac0-187">特定のユーザーとの共有</span><span class="sxs-lookup"><span data-stu-id="3cac0-187">Sharing with specific people</span></span>

<span data-ttu-id="3cac0-188">サイトまたはそのコンテンツの共有を制限する場合は、サイト所有者のみがファイル、フォルダー、およびサイトを共有できるようにサイトを構成します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-188">if you want to limit the sharing of a site or its contents, you can configure the site to only allow site owners to share files, folders, and the site.</span></span> <span data-ttu-id="3cac0-189">このように構成すると、サイト メンバーが*特定のユーザー* リンクを使用してファイルやフォルダーを共有しようとしたときに、その操作は承認を得るためにサイト所有者に回送されます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-189">When this is configured, site members' attempts to share files or folders by using *Specific people* links will go to the site owner for approval.</span></span>

<span data-ttu-id="3cac0-190">サイト、ファイル、およびフォルダーの共有を所有者に制限するには</span><span class="sxs-lookup"><span data-stu-id="3cac0-190">To limit site, file, and folder sharing to owners</span></span>
1. <span data-ttu-id="3cac0-191">サイトにある歯車アイコンをクリックして、**[サイトの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-191">In the site, click the gear icon, and then click **Site permissions**.</span></span>
2. <span data-ttu-id="3cac0-192">**[共有の設定]** の下側にある **[共有設定を変更します]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-192">Under **Sharing settings**, click **Change sharing settings**.</span></span>
3. <span data-ttu-id="3cac0-193">**[サイト所有者のみが、ファイル、フォルダー、サイトを共有できます]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-193">Select **Only site owners can share files, folders, and the site**.</span></span>
4. <span data-ttu-id="3cac0-194">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-194">Click **Save**.</span></span>

    ![SharePoint サイトの [共有アクセス許可] 設定のスナップショット](media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a><span data-ttu-id="3cac0-196">SharePoint ゲスト共有</span><span class="sxs-lookup"><span data-stu-id="3cac0-196">SharePoint guest sharing</span></span>

<span data-ttu-id="3cac0-197">SharePoint または OneDrive のファイルおよびフォルダーの組織外のユーザーとの共有を禁止する場合は、組織全体または個別サイトのゲスト共有をオフにします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-197">If you want to prevent sharing SharePoint or OneDrive files and folders with people outside your organization, you can turn off guest sharing for the entire organization or for an individual site.</span></span>

<span data-ttu-id="3cac0-198">組織の SharePoint ゲスト共有をオフにするには</span><span class="sxs-lookup"><span data-stu-id="3cac0-198">To turn off SharePoint guest sharing for your organization</span></span>
1. <span data-ttu-id="3cac0-199">SharePoint 管理センターで、**[ポリシー]** の下側にある **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-199">In the SharePoint admin center, under **Policies**, click **Sharing**.</span></span>
2. <span data-ttu-id="3cac0-200">**[外部共有]** で、SharePoint のスライダーを **[自分の組織内のユーザーのみ]** に下げます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-200">Under **External sharing**, drag the SharePoint slider down to **Only people in your organization**.</span></span>
3. <span data-ttu-id="3cac0-201">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-201">Click **Save**.</span></span>

    ![SharePoint 組織レベルの共有設定のスクリーンショット](media/sharepoint-tenant-sharing-off.png)


<span data-ttu-id="3cac0-203">サイトのゲスト共有をオフにするには</span><span class="sxs-lookup"><span data-stu-id="3cac0-203">To turn off guest sharing for a site</span></span>
1. <span data-ttu-id="3cac0-204">SharePoint 管理センターで、**[サイト]** の下側にある **[アクティブなサイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-204">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="3cac0-205">構成するサイトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-205">Click the site that you want to configure.</span></span>
3. <span data-ttu-id="3cac0-206">**[ポリシー]** タブで、**[外部共有]** の下側にある **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-206">On the **Policies** tab, under **External sharing** click **Edit**.</span></span>
4. <span data-ttu-id="3cac0-207">**[外部共有]** で、**[組織内のユーザーのみ]** を選択して **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-207">Under **External sharing**, choose **Only people in your organization**, and then click **Save**.</span></span>

    ![SharePoint のサイト レベル共有設定のスクリーンショット](media/sharepoint-site-external-sharing-settings-off.png)

<span data-ttu-id="3cac0-209">組織外のユーザーとの共有を許可するときに、すべてのユーザーが認証されているようにするには、組織全体または個別サイトの*すべてのユーザー* (匿名の共有) リンクを無効にします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-209">If you would like to allow sharing with people outside your organization but you want to make sure that everyone authenticates, you can disable *Anyone* (anonymous sharing) links for the entire organization or for an individual site.</span></span>

<span data-ttu-id="3cac0-210">組織レベルで*すべてのユーザー* リンクをオフにするには</span><span class="sxs-lookup"><span data-stu-id="3cac0-210">To turn off *Anyone* links at the organization level</span></span>
1. <span data-ttu-id="3cac0-211">SharePoint 管理センターで、**[ポリシー]** の下側にある **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-211">In the SharePoint admin center, under **Policies**, click **Sharing**.</span></span>
2. <span data-ttu-id="3cac0-212">**[外部共有]** で、SharePoint のスライダーを **[新規および既存のゲスト]** に下げます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-212">Under **External sharing**, drag the SharePoint slider down to **New and existing guests**.</span></span>
3. <span data-ttu-id="3cac0-213">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-213">Click **Save**.</span></span>

    ![SharePoint のサイト レベル共有設定のスクリーンショット](media/sharepoint-guest-sharing-new-and-existing-guests.png)

<span data-ttu-id="3cac0-215">サイトの*すべてのユーザー* リンクをオフにするには</span><span class="sxs-lookup"><span data-stu-id="3cac0-215">To turn off *Anyone* links for a site</span></span>
1. <span data-ttu-id="3cac0-216">SharePoint 管理センターで、**[サイト]** の下側にある **[アクティブなサイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-216">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="3cac0-217">構成するサイトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-217">Click the site that you want to configure.</span></span>
3. <span data-ttu-id="3cac0-218">**[ポリシー]** タブで、**[外部共有]** の下側にある **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-218">On the **Policies** tab, under **External sharing** click **Edit**.</span></span>
4. <span data-ttu-id="3cac0-219">**[外部共有]** で、**[新規および既存のゲスト]** を選択して **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3cac0-219">Under **External sharing**, choose **New and existing guests**, and then click **Save**.</span></span>

    ![SharePoint のサイト レベル共有設定のスクリーンショット](media/sharepoint-site-external-sharing-settings-new-and-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a><span data-ttu-id="3cac0-221">*組織内のユーザー*共有リンク</span><span class="sxs-lookup"><span data-stu-id="3cac0-221">*People in your organization* sharing links</span></span>

<span data-ttu-id="3cac0-222">既定では、サイトのメンバーは組織外のユーザーとファイルおよびフォルダーを共有するために、*組織外のユーザー* リンクを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-222">By default, members of a site can share files and folders with other people in your organization by using a *People in your organization* link.</span></span> <span data-ttu-id="3cac0-223">*組織外のユーザー* リンクは、PowerShell を使用して無効化できます</span><span class="sxs-lookup"><span data-stu-id="3cac0-223">You can disable *People in your organization* links by using PowerShell:</span></span>

`Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks`

<span data-ttu-id="3cac0-224">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="3cac0-224">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks`

## <a name="email"></a><span data-ttu-id="3cac0-225">電子メール</span><span class="sxs-lookup"><span data-stu-id="3cac0-225">Email</span></span>

<span data-ttu-id="3cac0-226">電子メールの不要な共有は、暗号化を使用することで防止できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-226">You can prevent unwanted sharing of emails by using encryption.</span></span> <span data-ttu-id="3cac0-227">これにより、電子メールの転送や許可されていないユーザーとの共有を防止できます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-227">This prevents emails being forwarded or otherwise shared with unauthorized users.</span></span> <span data-ttu-id="3cac0-228">電子メールの暗号化は、秘密度ラベルを使用することで有効にできます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-228">Email encryption can be enabled by using sensitivity labels.</span></span> <span data-ttu-id="3cac0-229">詳細については、「[機密ラベルの暗号化を使用してコンテンツへのアクセスを制限する](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cac0-229">See [Restrict access to content by using encryption in sensitivity labels](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels) for details.</span></span>

## <a name="download-or-file-copy"></a><span data-ttu-id="3cac0-230">ダウンロードまたはファイルのコピー</span><span class="sxs-lookup"><span data-stu-id="3cac0-230">Download or file copy</span></span>

<span data-ttu-id="3cac0-231">Microsoft 365 のファイルとフォルダーにアクセスできるユーザーは、ファイルをダウンロードして外部メディアにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="3cac0-231">Users who have access to files and folders in Microsoft 365 can download files and copy them to external media.</span></span> <span data-ttu-id="3cac0-232">不要なファイル共有のリスクを軽減するために、機密度ラベルを使用して内容を暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="3cac0-232">To reduce the risk of unwanted file sharing, you can encrypt the content by using sensitivity labels.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cac0-233">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cac0-233">See also</span></span>

[<span data-ttu-id="3cac0-234">Microsoft 365 ゲストの共有設定のリファレンス</span><span class="sxs-lookup"><span data-stu-id="3cac0-234">Microsoft 365 guest sharing settings reference</span></span>](microsoft-365-guest-settings.md)
