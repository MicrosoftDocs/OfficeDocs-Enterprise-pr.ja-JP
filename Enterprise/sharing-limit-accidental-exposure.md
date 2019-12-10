---
title: 偶発的な公開を制限する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Priority
description: ゲストとファイルを共有するときに情報が偶発的に公開されることを防止する方法を説明します。
ms.openlocfilehash: 3a5a99e96207e407f15abb17d9e1903c8ba52339
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886476"
---
# <a name="limit-accidental-exposure-to-files-when-sharing-with-guests"></a><span data-ttu-id="022c2-103">ゲストと共有するときにファイルの偶発的な公開を制限する</span><span class="sxs-lookup"><span data-stu-id="022c2-103">Limit accidental exposure to files when sharing with guests</span></span>

<span data-ttu-id="022c2-104">ファイルやフォルダーをゲストと共有する場合、機密情報を誤って共有する可能性を減らすことができるさまざまなオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="022c2-104">When sharing files and folders with guests, there are a variety of options to reduce the chances of accidentally sharing confidential information.</span></span> <span data-ttu-id="022c2-105">組織のニーズに合わせて、この記事のオプションから選択できます。</span><span class="sxs-lookup"><span data-stu-id="022c2-105">You can choose from the options in this article to best meet the needs of your organization.</span></span>

## <a name="use-best-practices-for-anyone-links"></a><span data-ttu-id="022c2-106">[すべてのユーザー] リンクのベスト プラクティスを使用する</span><span class="sxs-lookup"><span data-stu-id="022c2-106">Use best practices for Anyone links</span></span>

<span data-ttu-id="022c2-107">組織内のユーザーが認証されていない共有を行う必要があるが、認証されていないゲストがコンテンツを変更することを懸念している場合は、組織で認証されていない共有を行う方法のガイダンスについて、「[認証されていない共有のベスト プラクティス](best-practices-anonymous-sharing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="022c2-107">If people in your organization need to do anonymous sharing, but you're concerned about unauthenticated guests modifying content, read [Best practices for anonymous sharing](best-practices-anonymous-sharing.md) for guidance on how to work with anonymous sharing in your organization.</span></span>

## <a name="turn-off-anyone-links"></a><span data-ttu-id="022c2-108">[すべてのユーザー] リンクをオフにする</span><span class="sxs-lookup"><span data-stu-id="022c2-108">Turn off Anyone links</span></span>

<span data-ttu-id="022c2-109">適切なコンテンツに対して [*すべてのユーザー*] リンクを有効にしておくことをお勧めします。これは、共有の最も簡単な方法であり、ユーザーが IT 部門の管理外にある他のソリューションを求めるリスクを軽減できるためです。</span><span class="sxs-lookup"><span data-stu-id="022c2-109">We recommend leaving *Anyone* links enabled for appropriate content because it's the easiest way to share and can help reduce the risk of users seeking other solutions that are outside the control of your IT department.</span></span> <span data-ttu-id="022c2-110">[*すべてのユーザー*] リンクを他の人に転送できますが、リンクを持っているユーザーのみファイルへアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="022c2-110">*Anyone* links can be forwarded to others, but file access is only available to those who have the link.</span></span>

<span data-ttu-id="022c2-111">SharePoint、グループ、または Teams のコンテンツにアクセスするとき、ゲストに常に認証を要求する場合、[*すべてのユーザー*] 共有をオフにできます。</span><span class="sxs-lookup"><span data-stu-id="022c2-111">If you always want guests to authenticate when accessing content in SharePoint, Groups, or Teams, you can turn off *Anyone* sharing.</span></span> <span data-ttu-id="022c2-112">これにより、ユーザーは認証されていないコンテンツを共有することができなくなります。</span><span class="sxs-lookup"><span data-stu-id="022c2-112">This will prevent users from sharing content anonymously.</span></span>

<span data-ttu-id="022c2-113">[*すべてのユーザー*] リンクを無効にしても、ユーザーは [*特定のユーザー*] リンクを使用してゲストと簡単に共有できます。</span><span class="sxs-lookup"><span data-stu-id="022c2-113">If you disable *Anyone* links, users can still easily share with guests using *Specific people* links.</span></span> <span data-ttu-id="022c2-114">この場合、すべてのゲストは、共有コンテンツにアクセスする前に認証を受ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="022c2-114">In this case, all guests will be required to authenticate before they can access the shared content.</span></span>

<span data-ttu-id="022c2-115">ニーズに応じて、特定のサイトまたは組織全体の [*すべてのユーザー*] リンクを無効にできます。</span><span class="sxs-lookup"><span data-stu-id="022c2-115">Depending on your needs, you can disable *Anyone* links for specific sites, or for your whole organization.</span></span>

<span data-ttu-id="022c2-116">組織の [*すべてのユーザー*] リンクをオフにするには</span><span class="sxs-lookup"><span data-stu-id="022c2-116">To turn off *Anyone* links for your organization</span></span>
1. <span data-ttu-id="022c2-117">SharePoint 管理センターの左側のナビゲーションで、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-117">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="022c2-118">SharePoint 外部共有設定を [**新規および既存のゲスト**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="022c2-118">Set the SharePoint external sharing settings to **New and existing guests**.</span></span></br>
   <span data-ttu-id="022c2-119">![SharePoint サイトの外部共有設定のスクリーンショット](media/sharepoint-organization-external-sharing-controls-new-users.png)</span><span class="sxs-lookup"><span data-stu-id="022c2-119">![Screenshot of SharePoint site external sharing settings](media/sharepoint-organization-external-sharing-controls-new-users.png)</span></span>
3. <span data-ttu-id="022c2-120">[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-120">Click **Save**.</span></span>

<span data-ttu-id="022c2-121">サイトの [*すべてのユーザー*] リンクをオフにするには</span><span class="sxs-lookup"><span data-stu-id="022c2-121">To turn off *Anyone* links for a site</span></span>
1. <span data-ttu-id="022c2-122">SharePoint 管理センターの左側のナビゲーションで、[**サイト**] を展開して [**アクティブなサイト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-122">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="022c2-123">作成したチームのサイトを選択します。</span><span class="sxs-lookup"><span data-stu-id="022c2-123">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="022c2-124">リボンで [**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-124">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="022c2-125">共有が [**新規および既存のゲスト**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="022c2-125">Ensure that sharing is set to **New and existing guests**.</span></span></br>
   <span data-ttu-id="022c2-126">![SharePoint サイトの外部共有設定のスクリーンショット](media/sharepoint-site-external-sharing-settings.png)</span><span class="sxs-lookup"><span data-stu-id="022c2-126">![Screenshot of SharePoint site external sharing settings](media/sharepoint-site-external-sharing-settings.png)</span></span>
5. <span data-ttu-id="022c2-127">変更を加えた場合は、[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-127">If you made changes, click **Save**.</span></span>

## <a name="domain-filtering"></a><span data-ttu-id="022c2-128">ドメインのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="022c2-128">Domain filtering</span></span>

<span data-ttu-id="022c2-129">ドメイン許可または拒否リストを使用して、ユーザーがゲストを招待できるドメインを決定できます。</span><span class="sxs-lookup"><span data-stu-id="022c2-129">You can use domain allow or deny lists to determine which domains your users can invite guests from.</span></span>

<span data-ttu-id="022c2-130">許可リストを使用すると、組織内のユーザーがゲストを招待できるドメイン リストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="022c2-130">With an allow list, you can specify a list of domains from which users in your organization can invite guests.</span></span> <span data-ttu-id="022c2-131">他のドメインへのゲストの招待がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="022c2-131">Guest invitations to other domains are blocked.</span></span> <span data-ttu-id="022c2-132">組織が特定のドメイン リストのゲストとのみ共同作業を行う場合、この機能を使用して他のドメインとの共有を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="022c2-132">If your organization only collaborates with guests from a list of specific domains, you can use this feature to prevent sharing with other domains.</span></span>

<span data-ttu-id="022c2-133">拒否リストを使用すると、組織内のユーザーがゲストを招待できないドメイン リストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="022c2-133">With a deny list, you can specify a list of domains from which users in your organization cannot invite guests.</span></span> <span data-ttu-id="022c2-134">リストのドメインへのゲストの招待がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="022c2-134">Guest invitations to the listed domains are blocked.</span></span> <span data-ttu-id="022c2-135">これは、たとえば、組織内のゲストになることを避けたい競合他社がいる場合などに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="022c2-135">This can be useful if you have competitors, for example, who you want to prevent from becoming guests in your organization.</span></span>

<span data-ttu-id="022c2-136">許可リストと拒否リストは、認証されたゲストとの共有にのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="022c2-136">The allow and deny lists only affect sharing with authenticated guests.</span></span> <span data-ttu-id="022c2-137">禁止されたドメインのゲストは、無効にしていない場合は、[*すべてのユーザー*] リンクを使用して共有できます。</span><span class="sxs-lookup"><span data-stu-id="022c2-137">Users can still share with guests from prohibited domains by using *Anyone* links if you haven't disabled them.</span></span> <span data-ttu-id="022c2-138">ドメインの許可リストと拒否リストで最良の結果を得るには、上記のように [*すべてのユーザー*] リンクを無効にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="022c2-138">For best results with domain allow and deny lists, consider disabling *Anyone* links as described above.</span></span>

<span data-ttu-id="022c2-139">ゲスト共有用のドメイン許可リストまたは拒否リストを設定するには</span><span class="sxs-lookup"><span data-stu-id="022c2-139">To set up a domain allow or deny list for guest sharing</span></span>
1. <span data-ttu-id="022c2-140">SharePoint 管理センターの左側のナビゲーションで、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-140">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="022c2-141">[**外部共有の詳細設定**] で、[**ドメインごとに外部共有を制限する**] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="022c2-141">Under **Advanced settings for external sharing**, select the **Limit external sharing by domain** check box.</span></span>
3. <span data-ttu-id="022c2-142">[**ドメインを追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-142">Click **Add domains**.</span></span>
4. <span data-ttu-id="022c2-143">ドメインをブロックするかどうかを選択し、ドメインを入力して、[**OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-143">Select whether you want to block domains, type the domains, and click **OK**.</span></span></br>
   <span data-ttu-id="022c2-144">![ドメイン設定による SharePoint 制限外部共有のスクリーンショット](media/sharepoint-sharing-block-domain.png)</span><span class="sxs-lookup"><span data-stu-id="022c2-144">![Screenshot of SharePoint limit external sharing by domain setting](media/sharepoint-sharing-block-domain.png)</span></span>
5. <span data-ttu-id="022c2-145">[**保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-145">Click **Save**.</span></span>

<span data-ttu-id="022c2-146">SharePoint および OneDrive よりも高いレベルでドメインによる共有を制限する場合、Azure Active Directory で「[B2B ユーザーに対する特定組織からの招待を許可またはブロック](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)」できます。</span><span class="sxs-lookup"><span data-stu-id="022c2-146">If you want to limit sharing by domain at a higher level than SharePoint and OneDrive, you can [allow or block invitations to B2B users from specific organizations](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list) in Azure Active Directory.</span></span> <span data-ttu-id="022c2-147">(これらの設定を SharePoint と OneDrive に反映させるには、[SharePoint および OneDrive の Azure AD B2B プレビューとの統合](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview)を構成する必要があります。)</span><span class="sxs-lookup"><span data-stu-id="022c2-147">(You must configure the [SharePoint and OneDrive integration with Azure AD B2B Preview](https://docs.microsoft.com/sharepoint/sharepoint-azureb2b-integration-preview) for these settings to affect SharePoint and OneDrive.)</span></span>

## <a name="limit-guest-sharing-of-files-folders-and-sites-to-specified-security-groups"></a><span data-ttu-id="022c2-148">ファイル、フォルダー、およびサイトのゲスト共有を特定のセキュリティ グループに制限する</span><span class="sxs-lookup"><span data-stu-id="022c2-148">Limit guest sharing of files, folders, and sites to specified security groups</span></span>

<span data-ttu-id="022c2-149">ファイル、フォルダー、およびサイトのゲスト共有を特定のセキュリティ グループのメンバーに制限できます。</span><span class="sxs-lookup"><span data-stu-id="022c2-149">You can restrict guest sharing of files, folders, and sites to members of a specific security group.</span></span> <span data-ttu-id="022c2-150">これは、ゲスト共有を有効にしたいが、承認ワークフローまたは要求プロセスを使用する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="022c2-150">This is useful if you want to enable guest sharing, but with an approval workflow or request process.</span></span>

<span data-ttu-id="022c2-151">セキュリティ グループのメンバーへのゲスト共有を制限するには</span><span class="sxs-lookup"><span data-stu-id="022c2-151">To limit guest sharing to members of a security group</span></span>
1. <span data-ttu-id="022c2-152">SharePoint 管理センターの左側のナビゲーションで、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-152">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
2. <span data-ttu-id="022c2-153">[**その他の設定**] の下で、</span><span class="sxs-lookup"><span data-stu-id="022c2-153">Under **Other settings**.</span></span> <span data-ttu-id="022c2-154">[**外部共有を特定のセキュリティ グループに制限します**] に従います。</span><span class="sxs-lookup"><span data-stu-id="022c2-154">follow the **Limit external sharing to specific security groups** link.</span></span>
3. <span data-ttu-id="022c2-155">[**組織外のユーザーと共有できるユーザー**] の下で、チェックボックスの 1 つまたは両方を選択します。a.</span><span class="sxs-lookup"><span data-stu-id="022c2-155">Under **Who can share outside your organization**, select one or both of the check boxes: a.</span></span> <span data-ttu-id="022c2-156">[**選択したセキュリティ グループ内のユーザーにのみ認証済み外部ユーザーとの共有を許可します**] で、認証済みユーザーと共有できるセキュリティ グループを指定します。b.</span><span class="sxs-lookup"><span data-stu-id="022c2-156">**Let only users in selected security groups share with authenticated external users** to specify a security group that can share with authenticated users b.</span></span> <span data-ttu-id="022c2-157">[**選択したセキュリティ グループ内のユーザーにのみ、認証済み外部ユーザーとの共有および匿名リンクの使用を許可します**] で、[すべてのユーザー] リンクを使用して認証済みユーザーと共有できるセキュリティ グループを指定します。</span><span class="sxs-lookup"><span data-stu-id="022c2-157">**Let only users in selected security groups share with authenticated external users and using anonymous links** to specify a security group that can share with authenticated users and by using Anyone links</span></span>
4. <span data-ttu-id="022c2-158">[**OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="022c2-158">Click **OK**.</span></span>

<span data-ttu-id="022c2-159">これは、ファイル、フォルダー、およびサイトに影響しますが、Office 365 グループまたは Teams には影響しません。</span><span class="sxs-lookup"><span data-stu-id="022c2-159">Note that this affects files, folders, and sites, but not Office 365 groups or Teams.</span></span> <span data-ttu-id="022c2-160">メンバーがゲストを非公開 Office 365 グループまたは Microsoft Teams の非公開チームに招待すると、招待は認証のためにグループまたはチームの所有者に送信されます。</span><span class="sxs-lookup"><span data-stu-id="022c2-160">When members invite guests to a private Office 365 group or a private team in Microsoft Teams, the invitation is sent to the group or team owner for approval.</span></span>

## <a name="see-also"></a><span data-ttu-id="022c2-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="022c2-161">See Also</span></span>

[<span data-ttu-id="022c2-162">セキュリティで保護されたゲスト共有の環境を作成する</span><span class="sxs-lookup"><span data-stu-id="022c2-162">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

[<span data-ttu-id="022c2-163">匿名ユーザーとファイルおよびフォルダーを共有するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="022c2-163">Best practices for sharing files and folders with anonymous users</span></span>](best-practices-anonymous-sharing.md)