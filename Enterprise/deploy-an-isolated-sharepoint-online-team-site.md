---
title: "分離した SharePoint Online チーム サイトの展開"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 3033614b-e23b-4f68-9701-f62525eafaab
description: "概要: ステップごとの手順を使用して、分離した新しい SharePoint Online チーム サイトを展開します。"
ms.openlocfilehash: 31a1f588aefccd9e2cb353af86d8aa0d598696af
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="deploy-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="62048-103">分離した SharePoint Online チーム サイトの展開</span><span class="sxs-lookup"><span data-stu-id="62048-103">Deploy an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="62048-104">**概要:** ステップごとの手順を使用して、分離した新しい SharePoint Online チーム サイトを展開します。</span><span class="sxs-lookup"><span data-stu-id="62048-104">**Summary:** Deploy a new isolated SharePoint Online team site with these step-by-step instructions.</span></span>
  
<span data-ttu-id="62048-p101">この記事は、分離した SharePoint Online チーム サイトを Microsoft Office 365 で作成および構成するためのステップごとの展開ガイドです。これらの手順は、アクセス レベルごとに 1 つの Azure Active Directory (AD) ベースのアクセス グループが含まれる、3 つの既定の SharePoint グループとそれに対応するアクセス許可レベルの使用を前提としています。</span><span class="sxs-lookup"><span data-stu-id="62048-p101">This article is a step-by-step deployment guide for creating and configuring an isolated SharePoint Online team site in Microsoft Office 365. These steps assume the use of the three default SharePoint groups and corresponding permission levels, with a single Azure Active Directory (AD)-based access group for each level of access.</span></span>
  
## <a name="phase-1-create-and-populate-the-team-site-access-groups"></a><span data-ttu-id="62048-107">フェーズ 1:チーム サイト アクセス グループの作成と設定</span><span class="sxs-lookup"><span data-stu-id="62048-107">Phase 1: Create and populate the team site access groups</span></span>

<span data-ttu-id="62048-108">このフェーズでは、3 つの既定の SharePoint グループに対して 3 つの Azure AD ベースのアクセス グループを作成し、それらに適切なユーザー アカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="62048-108">In this phase, you create the three Azure AD-based access groups for the three default SharePoint groups and populate them with the appropriate user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="62048-p102">次の手順は、すべての必要なユーザー アカウントが既に存在し、適切なライセンスが割り当てられていることを前提としています。そうでない場合は、それらを追加して、手順 1 に進む前にライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="62048-p102">The following steps assume that all necessary user accounts already exist and are assigned the appropriate licenses. If not, please add them and assign licenses before proceeding to step 1.</span></span> 
  
### <a name="step-1-list-the-sharepoint-online-admins-for-the-site"></a><span data-ttu-id="62048-111">手順 1:サイトの SharePoint Online 管理者を一覧表示する</span><span class="sxs-lookup"><span data-stu-id="62048-111">Step 1: List the SharePoint Online admins for the site</span></span>

<span data-ttu-id="62048-112">分離したチーム サイトの SharePoint Online 管理者に対応するユーザー アカウントのセットを決定します。</span><span class="sxs-lookup"><span data-stu-id="62048-112">Determine the set of user accounts corresponding to the SharePoint Online admins for the isolated team site.</span></span>
  
<span data-ttu-id="62048-113">Office 365 を使用してユーザー アカウントとグループを管理していて、Windows PowerShell を使用する場合は、そのユーザー プリンシパル名 (UPN) のリストを作成します (UPN の例: belindan@contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="62048-113">If you are managing user accounts and groups through Office 365 and want to use Windows PowerShell, make a list of their user principal names (UPNs) (example UPN: belindan@contoso.com).</span></span>
  
### <a name="step-2-list-the-members-for-the-site"></a><span data-ttu-id="62048-114">手順 2: サイトのメンバーを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="62048-114">Step 2: List the members for the site</span></span>

<span data-ttu-id="62048-115">分離したチーム サイトのメンバーに対応するユーザー アカウントのセットを決定します。メンバーはサイト内に格納されているリソースで共同作業を行います。</span><span class="sxs-lookup"><span data-stu-id="62048-115">Determine the set of user accounts corresponding to the members for the isolated team site, those who will be collaborating on resources stored within the site.</span></span>
  
<span data-ttu-id="62048-p103">Office 365 を使用してユーザー アカウントとグループを管理していて、PowerShell を使用する場合は、その UPN の一覧を作成します。サイト メンバーが数多く存在する場合は、UPN の一覧をテキスト ファイルに格納し、PowerShell コマンドを 1 回実行することですべて追加できます。</span><span class="sxs-lookup"><span data-stu-id="62048-p103">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
### <a name="step-3-list-the-viewers-for-the-site"></a><span data-ttu-id="62048-118">手順 3:サイトのビューアーを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="62048-118">Step 3: List the viewers for the site</span></span>

<span data-ttu-id="62048-119">分離したチーム サイトのビューアーに対応するユーザー アカウントのセットを決定します。ビューアーは、サイトに格納されているリソースを表示できますが、リソースを変更したり、そのコンテンツで直接共同作業を行ったりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="62048-119">Determine the set of user accounts corresponding to the viewers of the isolated team site, those who can view the resources stored in the site but not modify them or directly collaborate on their contents.</span></span>
  
<span data-ttu-id="62048-p104">Office 365 を使用してユーザー アカウントとグループを管理していて、PowerShell を使用する場合は、その UPN の一覧を作成します。サイト メンバーが数多く存在する場合は、UPN の一覧をテキスト ファイルに格納し、PowerShell コマンドを 1 回実行することですべて追加できます。</span><span class="sxs-lookup"><span data-stu-id="62048-p104">If you are managing user accounts and groups through Office 365 and want to use PowerShell, make a list of their UPNs. If there are a lot of site members, you can store the list of UPNs in a text file and add them all with a single PowerShell command.</span></span>
  
<span data-ttu-id="62048-122">サイトのビューアーには、経営幹部、弁護士、または部門間の利害関係者などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="62048-122">Viewers for the site might include executive management, legal counsel, or inter-departmental stakeholders.</span></span>
  
### <a name="step-4-create-the-three-access-groups-for-the-site-in-azure-ad"></a><span data-ttu-id="62048-123">手順 4:Azure AD でサイト用の 3 つのアクセス グループを作成する</span><span class="sxs-lookup"><span data-stu-id="62048-123">Step 4: Create the three access groups for the site in Azure AD</span></span>

<span data-ttu-id="62048-124">Azure AD で次のアクセス グループを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62048-124">You need to create the following access groups in Azure AD:</span></span>
  
- <span data-ttu-id="62048-125">サイト管理者 (手順 1 のリストが含まれます)</span><span class="sxs-lookup"><span data-stu-id="62048-125">Site admins (which will contain the list from step 1)</span></span>
    
- <span data-ttu-id="62048-126">サイト メンバー (手順 2 のリストが含まれます)</span><span class="sxs-lookup"><span data-stu-id="62048-126">Site members (which will contain the list from step 2)</span></span>
    
- <span data-ttu-id="62048-127">サイト ビューアー (手順 3 のリストが含まれます)</span><span class="sxs-lookup"><span data-stu-id="62048-127">Site viewers (which will contain the list from step 3)</span></span>
    
1. <span data-ttu-id="62048-128">お使いのブラウザーで、Azure Portal [(https://portal.azure.com)]((https://portal.azure.com)) に移動し、ユーザー管理の管理者または会社管理者のロールに割り当てられたアカウントの資格情報でサインインします。</span><span class="sxs-lookup"><span data-stu-id="62048-128">In your browser, go to the Azure portal at [(https://portal.azure.com)]((https://portal.azure.com)) and sign in with the credentials of an account that has been assigned with User Management Admin or Company Administrator role.</span></span>
    
2. <span data-ttu-id="62048-129">Azure Portal で **[Azure Active Directory] > [ユーザーとグループ] > [すべてのグループ]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-129">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="62048-130">**[すべてのグループ]** ブレードで、 **[+ 新しいグループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-130">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="62048-131">**[グループ]** ブレードでの手順:</span><span class="sxs-lookup"><span data-stu-id="62048-131">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="62048-132">**[名前]** にグループ名を入力します。</span><span class="sxs-lookup"><span data-stu-id="62048-132">Type the group name in **Name**.</span></span>
    
  - <span data-ttu-id="62048-133">**[メンバーシップ]** で **[割り当て済み]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62048-133">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="62048-134">**[Office の機能を有効にする]** で **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-134">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="62048-135">**[作成]** をクリックして、 **[グループ]** ブレードを閉じます。</span><span class="sxs-lookup"><span data-stu-id="62048-135">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="62048-136">追加グループについて手順 3 から 5 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="62048-136">Repeat steps 3-5 for your additional groups.</span></span>
    
> [!NOTE]
> <span data-ttu-id="62048-p105">Office の機能を有効にできるグループを作成するには、Azure Portal を使用する必要があります。SharePoint Online の独立したサイトを、後から Azure Information Protection (AIP) のラベルを使用して高機密サイトとして構成し、ファイルを暗号化して特定のグループにアクセス許可を割り当てる場合、許可されるグループは Office の機能を有効にして作成する必要があります。Azure AD グループが作成された後は、その Office の機能の設定は変更できません。</span><span class="sxs-lookup"><span data-stu-id="62048-p105">You need to use the Azure portal to create the groups so that they have Office features enabled. If a SharePoint Online isolated site is later configured as a Highly Confidential site with an Azure Information Protection (AIP) label to encrypt files and assign permission to specific groups, the permitted groups must have been created with Office features enabled. You cannot change the Office features setting of an Azure AD group after it has been created.</span></span> 
  
<span data-ttu-id="62048-140">これで 3 つのサイトのアクセス グループの構成が完了します。</span><span class="sxs-lookup"><span data-stu-id="62048-140">Here is your resulting configuration with the three site access groups.</span></span>
  
![独立した SharePoint Online サイトの展開用の 3 つのアクセス グループ。](images/c2557f61-478b-4494-95e9-d79fe5909e8b.png)
  
### <a name="step-5-add-the-user-accounts-to-the-access-groups"></a><span data-ttu-id="62048-p106">手順 5:アクセス グループにユーザー アカウントを追加する</span><span class="sxs-lookup"><span data-stu-id="62048-p106">Step 5. Add the user accounts to the access groups</span></span>

<span data-ttu-id="62048-144">この手順では、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="62048-144">In this step, do the following:</span></span>
  
1. <span data-ttu-id="62048-145">手順 1 のユーザーの一覧をサイト管理者のアクセス グループに追加する</span><span class="sxs-lookup"><span data-stu-id="62048-145">Add the list of users from step 1 to the site admins access group</span></span>
    
2. <span data-ttu-id="62048-146">手順 2 のユーザーの一覧をサイト メンバーのアクセス グループに追加する</span><span class="sxs-lookup"><span data-stu-id="62048-146">Add the list of users from step 2 to the site members access group</span></span>
    
3. <span data-ttu-id="62048-147">手順 3 のユーザーの一覧をサイト ビューアーのアクセス グループに追加する</span><span class="sxs-lookup"><span data-stu-id="62048-147">Add the list of users from step 3 to the site viewers access group</span></span>
    
<span data-ttu-id="62048-148">Windows Server AD を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用してユーザーを適切なアクセス グループに追加し、Office 365 サブスクリプションと同期されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="62048-148">If you are managing user accounts and groups through Windows Server AD, add users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="62048-p107">Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは PowerShell を使用できます。アクセス グループのいずれかでグループ名が重複している場合、Office 管理者センターをご使用ください。</span><span class="sxs-lookup"><span data-stu-id="62048-p107">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell. If you have duplicate group names for any of the access groups, you should use the Office Admin center.</span></span>
  
<span data-ttu-id="62048-151">Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なユーザー アカウントおよびグループを適切なアクセス グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="62048-151">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate user accounts and groups to the appropriate access groups.</span></span>
  
<span data-ttu-id="62048-152">PowerShell については、まず「[Azure Active Directory V2 PowerShell モジュールを使用した接続](https://go.microsoft.com/fwlink/?linkid=842218)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62048-152">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="62048-153">次に、以下のコマンド ブロックを使用して、個々のユーザー アカウントをアクセス グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="62048-153">Next, use the following command block to add an individual user account to an access group:</span></span>
  
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="62048-154">すべての PowerShell コマンドを記載したテキスト ファイルと、使用しているグループおよびユーザー アカウント名に基づいて PowerShell コマンドを生成する Excel 構成ワークシートについては、[分離した SharePoint Online チーム サイトの展開キット]((https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907))をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="62048-154">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit]((https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)).</span></span> 
  
<span data-ttu-id="62048-155">いずれかのアクセス グループのユーザー アカウントの UPN をテキスト ファイルに格納した場合は、次の PowerShell コマンド ブロックを使用して、それらすべてのユーザー アカウントを一度に追加します。</span><span class="sxs-lookup"><span data-stu-id="62048-155">If you stored the UPNs of user accounts for any of the access groups in a text file, you can use the following PowerShell command block to add them all at one time:</span></span>
  
```
$grpName="<display name of the access group>"
$fileName="<path and name of the file containing the list of account UPNs>"
$grpID=(Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
Get-Content $fileName | ForEach { $userUPN=$_; Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID $grpID }
```

<span data-ttu-id="62048-156">PowerShell の場合、次のコマンド ブロックを使用して、個々のグループをアクセス グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="62048-156">For PowerShell, use the following command block to add an individual group to an access group:</span></span>
  
```
$nestedGrpName="<display name of the group to add to the access group>"
$grpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $nestedGrpName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID

```

<span data-ttu-id="62048-157">次のような結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="62048-157">The results should be the following:</span></span>
  
- <span data-ttu-id="62048-158">サイト管理者の Azure AD グループには、サイト管理者のユーザー アカウントまたはグループが含まれる</span><span class="sxs-lookup"><span data-stu-id="62048-158">The site admins Azure AD group contains the site admin user accounts or groups</span></span>
    
- <span data-ttu-id="62048-159">サイト メンバーの Azure AD グループには、サイト メンバーのユーザー アカウントまたはグループが含まれる</span><span class="sxs-lookup"><span data-stu-id="62048-159">The site members Azure AD group contains the site member user accounts or groups</span></span>
    
- <span data-ttu-id="62048-160">サイト ビューアーの Azure AD グループには、サイトのコンテンツを表示できるユーザー アカウントまたはグループのみが含まれる</span><span class="sxs-lookup"><span data-stu-id="62048-160">The site viewers Azure AD group contains the user accounts or groups that can only view the site contents</span></span>
    
<span data-ttu-id="62048-161">Office 管理者センターまたは次の PowerShell コマンド ブロックを使用して、各アクセス グループのグループ メンバーの一覧を検証します。</span><span class="sxs-lookup"><span data-stu-id="62048-161">Validate the list of group members for each access group with the Office Admin center or with the following PowerShell command block:</span></span>
  
```
$grpName="<display name of the access group>"
Get-AzureADGroupMember -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID | Sort UserPrincipalName | Select UserPrincipalName,DisplayName,UserType
```

<span data-ttu-id="62048-162">以下に示すのが、でき上がった構成で、この構成にはユーザー アカウントとグループが設定された3 つのサイトのアクセス グループが含まれます。</span><span class="sxs-lookup"><span data-stu-id="62048-162">Here is your resulting configuration with the three site access groups populated with user accounts or groups.</span></span>
  
![ユーザー アカウントが設定された 3 つのアクセス グループ。](images/2320107c-dad6-4c8f-94e5-f6427c125e71.png)
  
## <a name="phase-2-create-and-configure-the-isolated-team-site"></a><span data-ttu-id="62048-164">フェーズ 2:分離したチーム サイトを作成し構成する</span><span class="sxs-lookup"><span data-stu-id="62048-164">Phase 2: Create and configure the isolated team site</span></span>

<span data-ttu-id="62048-165">このフェーズでは、分離した SharePoint Online サイトを作成し、新しい Azure AD ベースのアクセス グループを使用するために既定の SharePoint Online アクセス許可レベルのアクセス許可を構成します。</span><span class="sxs-lookup"><span data-stu-id="62048-165">In this phase, you create the isolated SharePoint Online site and configure the permissions for the default SharePoint Online permission levels to use your new Azure AD-based access groups.</span></span>
  
<span data-ttu-id="62048-166">最初に、次の手順で SharePoint Online チーム サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="62048-166">First, create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="62048-p108">SharePoint Online チーム サイト (SharePoint Online 管理者) の管理にも使用されるアカウントを使用して Office 365 ポータルにサインインします。ヘルプを表示するには、「[Office 365 にサインインする場所]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62048-p108">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365]((https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)).</span></span>
    
2. <span data-ttu-id="62048-169">タイルのリストで、 **[SharePoint]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-169">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="62048-170">ブラウザーの新しい **[SharePoint]** タブで、 **[+ サイトの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-170">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="62048-171">**[サイトの作成]** ページで、 **[チーム サイト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-171">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="62048-172">**[サイト名]** にチーム サイトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="62048-172">In **Site name**, type a name for the team site.</span></span> 
    
6. <span data-ttu-id="62048-173">**[チーム サイトの説明]** に、サイトの目的の説明 (オプション) を入力します。</span><span class="sxs-lookup"><span data-stu-id="62048-173">In **Team site description,** type an optional description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="62048-174">**[プライバシー設定]** で、 **[プライベート - メンバーのみがこのサイトにアクセス可能**」を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-174">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="62048-175">**[誰を追加しますか]** ウィンドウで、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-175">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="62048-176">次に、新しい SharePoint Online チーム サイトから、アクセス許可を構成します。</span><span class="sxs-lookup"><span data-stu-id="62048-176">Next, from the new SharePoint Online team site, configure permissions.</span></span>
  
1. <span data-ttu-id="62048-177">ツールバーで、設定アイコンをクリックしてから、 **[サイトの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-177">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
2. <span data-ttu-id="62048-178">**[サイトの権限]** ウィンドウで、 **[高度な権限の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-178">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
3. <span data-ttu-id="62048-179">ブラウザーの新しい **[権限]** タブで、 **[アクセス要求の設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-179">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
4. <span data-ttu-id="62048-180">**[アクセス要求の設定]** ダイアログ ボックスの **[サイトと個別のファイルおよびフォルダーの共有をメンバーに許可します]** と **[アクセス要求の許可]** をクリアし (これによって、3 つのチェック ボックスがすべてクリアされる)、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-180">In the **Access Requests Settings** dialog box, clear **Allow member to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
5. <span data-ttu-id="62048-181">ブラウザーの **[アクセス権]** タブで、リスト内の **[\<サイト名> のメンバー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-181">On the **Permissions** tab of your browser, click **\<site name> Members** in the list.</span></span>
    
6. <span data-ttu-id="62048-182">**[ユーザーとグループ]** で、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-182">In **People and Groups**, click **New**.</span></span>
    
7. <span data-ttu-id="62048-183">**[共有]** ダイアログ ボックスで、サイト メンバーのアクセス グループの名前を入力し、それを選択してから、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-183">In the **Share** dialog box, type the name of the site members access group, select it, and then click **Share**.</span></span>
    
8. <span data-ttu-id="62048-184">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-184">Click the back button on your browser.</span></span>
    
9. <span data-ttu-id="62048-185">リスト内の **[\<サイト名> の所有者]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-185">Click **\<site name> Owners** in the list.</span></span>
    
10. <span data-ttu-id="62048-186">**[ユーザーとグループ]** で、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-186">In **People and Groups**, click **New**.</span></span>
    
11. <span data-ttu-id="62048-187">**[共有]** ダイアログ ボックスで、サイト管理者のアクセス グループの名前を入力し、それを選択してから、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-187">In the **Share** dialog box, type the name of the site admins access group, select it, and then click **Share**.</span></span>
    
12. <span data-ttu-id="62048-188">ブラウザーの戻るボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-188">Click the back button on your browser.</span></span>
    
13. <span data-ttu-id="62048-189">リスト内の **[\<サイト名> の閲覧者]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-189">Click **\<site name> Visitors** in the list.</span></span>
    
14. <span data-ttu-id="62048-190">**[ユーザーとグループ]** で、 **[新規]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-190">In **People and Groups**, click **New**.</span></span>
    
15. <span data-ttu-id="62048-191">**[共有]** ダイアログ ボックスで、サイト ビューアーのアクセス グループの名前を入力し、それを選択してから、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="62048-191">In the **Share** dialog box, type the name of the site viewers access group, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="62048-192">ブラウザーの **[アクセス権]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="62048-192">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="62048-193">これらのアクセス権の設定の結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="62048-193">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="62048-194">**[\<サイト名> の所有者]** の SharePoint グループには、サイト管理者のアクセス グループが含まれます。このグループではすべてのメンバーに**フル コントロール** アクセス許可レベルが付与されています。</span><span class="sxs-lookup"><span data-stu-id="62048-194">The **\<site name> Owners** SharePoint group contains the site admins access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="62048-195">**[\<サイト名> のメンバー**]の SharePoint グループには、サイト メンバーのアクセス グループが含まれます。このグループではすべてのメンバーに**編集**アクセス許可レベルが付与されています。</span><span class="sxs-lookup"><span data-stu-id="62048-195">The **\<site name> Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="62048-196">**[\<サイト名> の閲覧者]**の SharePoint グループには、サイト ビューアーのアクセス グループが含まれます。このグループではすべてのメンバーに**読み取り**アクセス許可レベルが付与されています。</span><span class="sxs-lookup"><span data-stu-id="62048-196">The **\<site name> Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="62048-197">メンバーが他のメンバーを招待したり、メンバー以外のユーザーがアクセス権を要求したりする機能は無効です。</span><span class="sxs-lookup"><span data-stu-id="62048-197">The ability for members to invite other members or for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="62048-198">以下に示すのができ上がった構成で、この構成にはユーザー アカウントと Azure AD グループが設定された 3 つのアクセス グループを使用するように構成されたサイト用の 3 つの SharePoint グループ含まれます。</span><span class="sxs-lookup"><span data-stu-id="62048-198">Here is your resulting configuration with the three SharePoint groups for the site configured to use the three access groups, which are populated with user accounts or Azure AD groups.</span></span>
  
![アクセス グループおよびユーザー アカウントが設定された、独立した SharePoint Online サイトの最終的な構成。](images/e7618971-06ab-447b-90ff-d8be3790fe63.png)
  
<span data-ttu-id="62048-200">いずれかのアクセス グループのグループ メンバーシップを介して、サイトのメンバーとともにサイトのリソースを使用して共同作業を行えるようになります。</span><span class="sxs-lookup"><span data-stu-id="62048-200">You and the members of the site, through group membership in one of the access groups, can now collaborate using the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="62048-201">次の手順</span><span class="sxs-lookup"><span data-stu-id="62048-201">Next step</span></span>

<span data-ttu-id="62048-202">サイト アクセス グループ メンバーシップを変更したり、カスタム アクセス許可を持つドキュメント フォルダーを作成したりする必要がある場合は、「[分離した SharePoint Online チーム サイトの管理](manage-an-isolated-sharepoint-online-team-site.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62048-202">When you need to change site access group membership or create a document folder with custom permissions, see [Manage an isolated SharePoint Online team site](manage-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="62048-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="62048-203">See Also</span></span>

[<span data-ttu-id="62048-204">分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="62048-204">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="62048-205">分離した SharePoint Online チーム サイトの設計</span><span class="sxs-lookup"><span data-stu-id="62048-205">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="62048-206">分離した SharePoint Online チーム サイトの管理</span><span class="sxs-lookup"><span data-stu-id="62048-206">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="62048-207">セキュリティ ソリューション</span><span class="sxs-lookup"><span data-stu-id="62048-207">Security solutions</span></span>](security-solutions.md)



