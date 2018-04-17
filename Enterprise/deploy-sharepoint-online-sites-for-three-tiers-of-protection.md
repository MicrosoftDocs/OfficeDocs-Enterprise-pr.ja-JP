---
title: 保護の 3 つの層を SharePoint Online サイトを展開します。
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: '概要: は、作成し、情報保護のさまざまなレベルの SharePoint Online のチーム サイトを構成します。'
ms.openlocfilehash: ddeb1885cbc74be6e7098660eb1d9906d43739fd
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="bdcea-103">保護の 3 つの層を SharePoint Online サイトを展開します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="bdcea-104">**の概要:**作成し、情報保護のさまざまなレベルの SharePoint Online のチーム サイトを構成します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="bdcea-p101">ベースライン、機密、および非常に機密性の高い社外秘の SharePoint Online チーム サイトを設計および展開するには、この記事の手順を実行してください。 これらの 3 層の保護の詳細については、「[Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md)」(SharePoint Online サイトとファイルのセキュリティ保護) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdcea-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="bdcea-107">ベースラインの SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="bdcea-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="bdcea-p102">ベースラインの保護には、パブリックおよびプライベートのチーム サイトが含まれます。 パブリック チーム サイトは、組織内の全ユーザーが検出し、アクセスすることができます。 プライベート サイトは、チーム サイトに関連付けられている Office 365 グループのメンバーのみが検出し、アクセスすることができます。 いずれの種類のチーム サイトも、メンバーがサイトを他のユーザーと共有することを許可しています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="bdcea-112">パブリック</span><span class="sxs-lookup"><span data-stu-id="bdcea-112">Public</span></span>

<span data-ttu-id="bdcea-113">パブリック アクセスとアクセス許可を使用するベースライン SharePoint Online チーム サイトを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="bdcea-p103">SharePoint Online チーム サイト (SharePoint Online 管理者) の管理にも使用されるアカウントを使用して Office 365 ポータルにサインインします。ヘルプについては、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdcea-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="bdcea-116">タイルのリストで、 **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="bdcea-117">ブラウザーの新しい **SharePoint** タブで、**[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="bdcea-118">**[サイトの作成]** ページで、**[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="bdcea-119">**[サイト名]** にパブリック チーム サイト名を入力します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="bdcea-120">**チーム サイトの説明**サイトの目的の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="bdcea-121">**[プライバシー設定]** で、 **[パブリック - 組織の全ユーザーがこのサイトにアクセス可能]** を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="bdcea-122">**[誰を追加しますか]** ウィンドウで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="bdcea-123">最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-123">Here is your resulting configuration.</span></span>
  
![パブリック SharePoint Online チーム サイトのベースライン レベルの保護。](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="bdcea-125">プライベート</span><span class="sxs-lookup"><span data-stu-id="bdcea-125">Private</span></span>

<span data-ttu-id="bdcea-126">プライベート アクセスとアクセス許可を使用するベースライン SharePoint Online チーム サイトを作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="bdcea-p104">SharePoint Online チーム サイト (SharePoint Online 管理者) の管理にも使用されるアカウントを使用して Office 365 ポータルにサインインします。ヘルプについては、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdcea-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="bdcea-129">タイルのリストで、 **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="bdcea-130">ブラウザーの新しい **SharePoint** タブで、**[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="bdcea-131">**[サイトの作成]** ページで、**[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="bdcea-132">**[サイト名]** にプライベート チーム サイト名を入力します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="bdcea-133">**チーム サイトの説明**では、サイトの目的の説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="bdcea-134">**[プライバシー設定]** で、 **[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="bdcea-135">**ユーザーは追加するですか?**ウィンドウの**メンバーの追加**] ボックスで、この秘密のチーム サイトにアクセスできるユーザー アカウントの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="bdcea-136">終了したら、サイトへのメンバーの初期セットを追加する場合は、**完了**する] をクリックして</span><span class="sxs-lookup"><span data-stu-id="bdcea-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="bdcea-137">最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-137">Here is your resulting configuration.</span></span>
  
![プライベート SharePoint Online チーム サイトのベースライン レベルの保護。](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="bdcea-139">機密 SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="bdcea-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="bdcea-140">機密 SharePoint Online チーム サイトは、独立したチーム サイトです。つまり、アクセス許可は、チーム サイトに関連付けられている Office 365 グループのメンバーシップではなく、SharePoint グループのメンバーシップを介して制御されます。</span><span class="sxs-lookup"><span data-stu-id="bdcea-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="bdcea-141">独立したチーム サイトを作成するには、2 つの主な手順があります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="bdcea-142">手順 1: 独立したサイトの設計</span><span class="sxs-lookup"><span data-stu-id="bdcea-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="bdcea-143">分離されたチーム サイトを設計するには、以下を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="bdcea-144">SharePoint グループおよびアクセス許可レベル。</span><span class="sxs-lookup"><span data-stu-id="bdcea-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="bdcea-145">SharePoint グループのメンバーとなるアクセス グループのセット。</span><span class="sxs-lookup"><span data-stu-id="bdcea-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="bdcea-146">アクセス グループの推奨される設定は、サイトのメンバーのいずれかのサイトの閲覧者、サイト管理者のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="bdcea-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="bdcea-147">アクセス グループ内で入れ子のグループを使用するかどうか。</span><span class="sxs-lookup"><span data-stu-id="bdcea-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="bdcea-148">たとえば、次のような推奨されるグループ構造とアクセス レベルです。</span><span class="sxs-lookup"><span data-stu-id="bdcea-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="bdcea-149">**SharePoint グループ**</span><span class="sxs-lookup"><span data-stu-id="bdcea-149">**SharePoint group**</span></span>|<span data-ttu-id="bdcea-150">**アクセス許可レベル**</span><span class="sxs-lookup"><span data-stu-id="bdcea-150">**Permission level**</span></span>|<span data-ttu-id="bdcea-151">**アクセス グループ (例)**</span><span class="sxs-lookup"><span data-stu-id="bdcea-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bdcea-152">[サイト名] のメンバー</span><span class="sxs-lookup"><span data-stu-id="bdcea-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="bdcea-153">編集</span><span class="sxs-lookup"><span data-stu-id="bdcea-153">Edit</span></span>  <br/> |<span data-ttu-id="bdcea-154">[サイト名] のメンバー</span><span class="sxs-lookup"><span data-stu-id="bdcea-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="bdcea-155">[サイト名] の閲覧者</span><span class="sxs-lookup"><span data-stu-id="bdcea-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="bdcea-156">読み取り</span><span class="sxs-lookup"><span data-stu-id="bdcea-156">Read</span></span>  <br/> |<span data-ttu-id="bdcea-157">[サイト名] の閲覧者</span><span class="sxs-lookup"><span data-stu-id="bdcea-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="bdcea-158">[サイト名] の所有者</span><span class="sxs-lookup"><span data-stu-id="bdcea-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="bdcea-159">フル コントロール</span><span class="sxs-lookup"><span data-stu-id="bdcea-159">Full control</span></span>  <br/> |<span data-ttu-id="bdcea-160">[サイト名] の管理者</span><span class="sxs-lookup"><span data-stu-id="bdcea-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="bdcea-p105">チーム サイトの既定で、SharePoint グループとアクセス許可レベルが作成されます。 アクセス グループの名前を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="bdcea-163">設計プロセスの詳細については、「[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdcea-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="bdcea-164">手順 2: 分離されたサイトを展開する</span><span class="sxs-lookup"><span data-stu-id="bdcea-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="bdcea-165">分離されたサイトを展開するには、まず以下を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="bdcea-166">各アクセス グループに追加するユーザー アカウントとグループを決定します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="bdcea-167">アクセス グループを作成し、ユーザーとグループ メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="bdcea-168">詳細な手順については、「[Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md)」(分離した SharePoint Online チーム サイトの展開) の「**Phase 1**」(フェーズ 1) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdcea-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="bdcea-169">次に、次の手順で SharePoint Online チーム サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="bdcea-p106">SharePoint Online チーム サイト (SharePoint Online 管理者) の管理にも使用されるアカウントを使用して Office 365 ポータルにサインインします。ヘルプについては、「[Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdcea-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="bdcea-172">タイルのリストで、 **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="bdcea-173">ブラウザーの新しい **[SharePoint]** タブで、 **[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="bdcea-174">**[サイトの作成]** ページで、 **[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="bdcea-175">**[サイト名]** にプライベート チーム サイト名を入力します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="bdcea-176">**チーム サイトの説明**] には、オプションの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="bdcea-177">**[プライバシー設定]** で、 **[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="bdcea-178">**[誰を追加しますか]** ウィンドウで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="bdcea-179">次に、新しい SharePoint Online チーム サイトから、以下の手順でアクセス許可を構成します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="bdcea-p107">サイトへのアクセス要求への対応を担当する IT 管理者または他のユーザーのユーザー プリンシパル名 (UPN) を決定します (belindan@contoso.com は、UPN の一例です)。その UPN をここに書き込みます。 _________________________________________。</span><span class="sxs-lookup"><span data-stu-id="bdcea-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="bdcea-182">ツールバーで、設定アイコンをクリックしてから、 **[サイトの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="bdcea-183">**[サイトの権限]** ウィンドウで、 **[高度な権限の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="bdcea-184">ブラウザーの新しい **[権限]** タブで、**[アクセス要求の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="bdcea-185">**[アクセス要求の設定]** ダイアログ ボックスで次のようにします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="bdcea-186">**[サイトと個別のファイルおよびフォルダーの共有をメンバーに許可します]** および **[メンバーが、他のユーザーをサイト メンバー グループ <グループ名> に招待することを許可します]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="bdcea-187">**[すべてのアクセス権要求を以下の電子メール アドレスに送信する]** に手順 1 の IT 管理者の UPN を入力します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="bdcea-188">**[OK]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="bdcea-189">ブラウザーの **[権限]** タブで、一覧の **[[サイト名] のメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="bdcea-190">**[ユーザーとグループ]** で、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="bdcea-191">[**共有**] ダイアログ ボックスでこのサイトのサイトのメンバーのアクセス グループの名前を入力、選択し、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="bdcea-192">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="bdcea-193">[ボックスの一覧には、**所有者 [のサイト名]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="bdcea-194">**[ユーザーとグループ]** で、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="bdcea-195">[**共有**] ダイアログ ボックスでこのサイトのサイト管理者のアクセス グループの名前を入力、選択し、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="bdcea-196">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="bdcea-197">一覧で、 **[サイト名] の閲覧者**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="bdcea-198">**[ユーザーとグループ]** で、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="bdcea-199">[**共有**] ダイアログ ボックスでこのサイトのサイトの閲覧者のアクセス グループの名前を入力、選択し、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="bdcea-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="bdcea-200">ブラウザーの **[アクセス権]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="bdcea-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="bdcea-201">これらのアクセス権の設定の結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdcea-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="bdcea-202">**[[サイト名] の所有者]** SharePoint グループには、サイト管理者アクセス グループが含まれます。このアクセス グループのすべてのメンバーは**フル コントロール** アクセス許可レベルを持っています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="bdcea-203">**[サイト名] のメンバー** SharePoint グループには、すべてのメンバーであるアクセス許可レベルの**編集**サイトのメンバー アクセス グループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="bdcea-204">**[[サイト名] の閲覧者]** SharePoint グループには、サイト閲覧者アクセス グループが含まれ、このアクセス グループのすべてのメンバーは**読み取り**アクセス許可レベルを持っています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="bdcea-205">メンバーが他のメンバーを招待する機能は無効にされています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="bdcea-206">メンバー以外がアクセスを要求する機能は有効にされています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="bdcea-207">最終的な構成をここに示します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-207">Here is your resulting configuration.</span></span>
  
![独立した SharePoint Online チーム サイトの機密レベルの保護。](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="bdcea-209">サイトのメンバーは、いずれかのアクセス グループのグループ メンバーシップを使用して、サイトのリソースについて安全に共同作業できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bdcea-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="bdcea-210">非常に機密性の高い社外秘 SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="bdcea-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="bdcea-211">非常に機密性の高い社外秘 SharePoint Online チーム サイトは、分離されたチーム サイトです。つまり、チーム サイトに関連付けられた Office 365 グループのメンバーシップではなく、SharePoint グループのメンバーシップを使用してアクセス許可を制御しています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="bdcea-212">非常に機密性の高い社外秘情報とコラボレーション用の分離されたチーム サイトを作成するには、主に 2 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="bdcea-213">手順 1: 分離されたサイトを設計する</span><span class="sxs-lookup"><span data-stu-id="bdcea-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="bdcea-214">分離されたチーム サイトを設計するには、以下を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="bdcea-215">SharePoint グループおよびアクセス許可レベル。</span><span class="sxs-lookup"><span data-stu-id="bdcea-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="bdcea-216">SharePoint グループのメンバーとなるアクセス グループのセット。</span><span class="sxs-lookup"><span data-stu-id="bdcea-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="bdcea-217">アクセス グループの推奨される設定は、サイトのメンバーのいずれかのサイトの閲覧者、サイト管理者のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="bdcea-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="bdcea-218">アクセス グループ内で入れ子のグループを使用するかどうか。</span><span class="sxs-lookup"><span data-stu-id="bdcea-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="bdcea-219">たとえば、次のような推奨されるグループ構造とアクセス レベルです。</span><span class="sxs-lookup"><span data-stu-id="bdcea-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="bdcea-220">**SharePoint グループ**</span><span class="sxs-lookup"><span data-stu-id="bdcea-220">**SharePoint group**</span></span>|<span data-ttu-id="bdcea-221">**アクセス許可レベル**</span><span class="sxs-lookup"><span data-stu-id="bdcea-221">**Permission level**</span></span>|<span data-ttu-id="bdcea-222">**アクセス グループ (例)**</span><span class="sxs-lookup"><span data-stu-id="bdcea-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="bdcea-223">[サイト名] のメンバー</span><span class="sxs-lookup"><span data-stu-id="bdcea-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="bdcea-224">編集</span><span class="sxs-lookup"><span data-stu-id="bdcea-224">Edit</span></span>  <br/> |<span data-ttu-id="bdcea-225">[サイト名] のメンバー</span><span class="sxs-lookup"><span data-stu-id="bdcea-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="bdcea-226">[サイト名] の閲覧者</span><span class="sxs-lookup"><span data-stu-id="bdcea-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="bdcea-227">読み取り</span><span class="sxs-lookup"><span data-stu-id="bdcea-227">Read</span></span>  <br/> |<span data-ttu-id="bdcea-228">[サイト名] の閲覧者</span><span class="sxs-lookup"><span data-stu-id="bdcea-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="bdcea-229">[サイト名] の所有者</span><span class="sxs-lookup"><span data-stu-id="bdcea-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="bdcea-230">フル コントロール</span><span class="sxs-lookup"><span data-stu-id="bdcea-230">Full control</span></span>  <br/> |<span data-ttu-id="bdcea-231">[サイト名] の管理者</span><span class="sxs-lookup"><span data-stu-id="bdcea-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="bdcea-p108">チーム サイトの既定で、SharePoint グループとアクセス許可レベルが作成されます。 アクセス グループの名前を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="bdcea-234">設計プロセスの詳細については、「[分離した SharePoint Online チーム サイトの設計](design-an-isolated-sharepoint-online-team-site.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdcea-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="bdcea-235">手順 2: 分離されたサイトを展開する</span><span class="sxs-lookup"><span data-stu-id="bdcea-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="bdcea-236">独立したサイトを展開するには、最初に次を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="bdcea-237">それぞれのアクセス グループに追加するユーザーとグループ メンバーを決定する</span><span class="sxs-lookup"><span data-stu-id="bdcea-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="bdcea-238">アクセス グループを作成し、ユーザーおよびグループ メンバーを追加する</span><span class="sxs-lookup"><span data-stu-id="bdcea-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="bdcea-239">アクセス グループを使用する独立したチーム サイトを作成する</span><span class="sxs-lookup"><span data-stu-id="bdcea-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="bdcea-240">詳細な手順については、「[Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md)」(分離した SharePoint Online チーム サイトの展開) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdcea-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="bdcea-241">このアクセス権の設定の結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdcea-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="bdcea-242">**[[サイト名] の所有者]** SharePoint グループには、サイト管理者アクセス グループが含まれます。このアクセス グループのすべてのメンバーは**フル コントロール** アクセス許可レベルを持っています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="bdcea-243">**[サイト名] のメンバー** SharePoint グループには、すべてのメンバーであるアクセス許可レベルの**編集**サイトのメンバー アクセス グループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="bdcea-244">**[[サイト名] の閲覧者]** SharePoint グループには、サイト閲覧者アクセス グループが含まれ、このアクセス グループのすべてのメンバーは**読み取り**アクセス許可レベルを持っています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="bdcea-245">メンバーが他のメンバーを招待する機能は無効にされています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="bdcea-246">メンバー以外がアクセスを要求する機能は無効にされています。</span><span class="sxs-lookup"><span data-stu-id="bdcea-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="bdcea-247">結果の構成は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-247">Here is your resulting configuration.</span></span>
  
![独立した SharePoint Online チーム サイトの高機密レベルの保護。](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="bdcea-249">いずれかのアクセス グループのグループ メンバーシップを介して、サイトのメンバーはサイトのリソースで安全に共同作業を行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="bdcea-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="bdcea-250">次の手順</span><span class="sxs-lookup"><span data-stu-id="bdcea-250">Next step</span></span>

[<span data-ttu-id="bdcea-251">Office 365 のラベルと DLP の SharePoint Online のファイルを保護します。</span><span class="sxs-lookup"><span data-stu-id="bdcea-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="bdcea-252">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdcea-252">See Also</span></span>

[<span data-ttu-id="bdcea-253">SharePoint Online サイトとファイルをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="bdcea-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="bdcea-254">開発/テスト環境の SharePoint Online サイトをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="bdcea-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="bdcea-255">選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス</span><span class="sxs-lookup"><span data-stu-id="bdcea-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="bdcea-256">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="bdcea-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




