---
title: "分離した SharePoint Online チーム サイトの管理"
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
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Solutions
ms.assetid: 79a61003-4905-4ba8-9e8a-16def7add37c
description: "概要: 以下の手順を使用して、分離した SharePoint Online チーム サイトを管理します。"
ms.openlocfilehash: 516bf9d1c94992789bd8341b347a5788dbb04933
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="manage-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="521f0-103">分離した SharePoint Online チーム サイトの管理</span><span class="sxs-lookup"><span data-stu-id="521f0-103">Manage an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="521f0-104">**概要:** 以下の手順を使用して、分離した SharePoint Online チーム サイトを管理します。</span><span class="sxs-lookup"><span data-stu-id="521f0-104">**Summary:** Manage your isolated SharePoint Online team site with these procedures.</span></span>
  
<span data-ttu-id="521f0-105">この記事では、分離した SharePoint Online チーム サイトの一般的な管理操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="521f0-105">This article describes common management operations for an isolated SharePoint Online team site.</span></span>
  
## <a name="add-a-new-user"></a><span data-ttu-id="521f0-106">新しいユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="521f0-106">Add a new user</span></span>

<span data-ttu-id="521f0-107">他のユーザーが新しいサイトに参加する場合は、サイトでの参加レベルを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="521f0-107">When someone new joins the site, you must decide their level of participation in the site:</span></span>
  
- <span data-ttu-id="521f0-108">管理:サイト管理者のアクセス グループに新しいユーザー アカウントを追加する</span><span class="sxs-lookup"><span data-stu-id="521f0-108">Administration: Add the new user account to the site admins access group</span></span>
    
- <span data-ttu-id="521f0-109">アクティブ コラボレーション:サイト メンバーのアクセス グループにユーザー アカウントを追加する</span><span class="sxs-lookup"><span data-stu-id="521f0-109">Active collaboration: Add the user account to the site members access group</span></span>
    
- <span data-ttu-id="521f0-110">表示:サイト ビューアーのアクセス グループにユーザー アカウントを追加する</span><span class="sxs-lookup"><span data-stu-id="521f0-110">Viewing: Add the user account to the site viewers access group</span></span>
    
<span data-ttu-id="521f0-111">Windows Server Active Directory (AD) を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用して適切なユーザーを適切なアクセス グループに追加し、Office 365 サブスクリプションと同期されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="521f0-111">If you are managing user accounts and groups through Windows Server Active Directory (AD), add the appropriate users to the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="521f0-112">Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは Microsoft PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="521f0-112">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or Microsoft PowerShell:</span></span>
  
- <span data-ttu-id="521f0-113">Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なユーザーを適切なアクセス グループに追加します。</span><span class="sxs-lookup"><span data-stu-id="521f0-113">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate users to the appropriate access groups.</span></span>
    
- <span data-ttu-id="521f0-p101">PowerShell、最初の[Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)します。ユーザー プリンシパル名 (UPN) でのアクセス グループにユーザー アカウントを追加するには、次の PowerShell コマンドのブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="521f0-p101">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). To add a user account to an access group with its user principal name (UPN), use the following PowerShell command block:</span></span>
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

> [!TIP]
> <span data-ttu-id="521f0-116">すべての PowerShell コマンドを記載したテキスト ファイルと、使用しているグループおよびユーザー アカウント名に基づいて PowerShell コマンドを生成する Excel 構成ワークシートについては、[分離した SharePoint Online チーム サイトの展開キット](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="521f0-116">For a text file that contains all the PowerShell commands and an Excel configuration worksheet that generates PowerShell commands based on your group and user account names, download the [Isolated SharePoint Online Team Site Deployment Kit](https://gallery.technet.microsoft.com/Isolated-SharePoint-Online-0b364907).</span></span> 

<span data-ttu-id="521f0-117">表示名を使ってユーザー アカウントをアクセス グループに追加するには、次の PowerShell コマンド ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="521f0-117">To add a user account to an access group with its display name, use the following PowerShell command block:</span></span>

```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="add-a-new-group"></a><span data-ttu-id="521f0-118">新しいグループを追加する</span><span class="sxs-lookup"><span data-stu-id="521f0-118">Add a new group</span></span>

<span data-ttu-id="521f0-119">グループ全体にアクセスを追加するには、サイト内のグループのすべてのメンバーへの参加レベルを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="521f0-119">To add access to an entire group, you must decide the level of participation of all the members of the group in the site:</span></span>
  
- <span data-ttu-id="521f0-120">管理:サイト管理者のアクセス グループにグループを追加する</span><span class="sxs-lookup"><span data-stu-id="521f0-120">Administration: Add the group to the site admins access group</span></span>
    
- <span data-ttu-id="521f0-121">アクティブ コラボレーション:サイト メンバーのアクセス グループにグループを追加する</span><span class="sxs-lookup"><span data-stu-id="521f0-121">Active collaboration: Add the group to the site members access group</span></span>
    
- <span data-ttu-id="521f0-122">表示:サイト ビューアーのアクセス グループにグループを追加する</span><span class="sxs-lookup"><span data-stu-id="521f0-122">Viewing: Add the group to the site viewers access group</span></span>
    
<span data-ttu-id="521f0-123">Windows Server AD を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用して適切なグループを適切なグループに追加し、Office 365 サブスクリプションと同期されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="521f0-123">If you are managing user accounts and groups through Windows Server AD, add the appropriate groups to the appropriate groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="521f0-124">Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="521f0-124">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="521f0-125">Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なアクセス グループを適切なグループに追加します。</span><span class="sxs-lookup"><span data-stu-id="521f0-125">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to add the appropriate groups to the appropriate access groups.</span></span>
    
- <span data-ttu-id="521f0-p102">PowerShell、最初の[Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)します。その後、次の PowerShell コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="521f0-p102">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). Then, use the following PowerShell commands:</span></span>
 
```
$newGroupName="<display name of the new group to add>"
$siteGrpName="<display name of the access group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $newGroupName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $siteGrpName }).ObjectID
```

## <a name="remove-a-user"></a><span data-ttu-id="521f0-128">ユーザーを削除する</span><span class="sxs-lookup"><span data-stu-id="521f0-128">Remove a user</span></span>

<span data-ttu-id="521f0-129">他のユーザーのアクセスをサイトから削除する必要がある場合は、サイトでの参加に基づいてそのユーザーが現在メンバーになっているアクセス グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="521f0-129">When someone's access must be removed from the site, you remove them from the access group for which they are currently a member based on their participation in the site:</span></span>
  
- <span data-ttu-id="521f0-130">管理:サイト管理者のアクセス グループからユーザー アカウントを削除する</span><span class="sxs-lookup"><span data-stu-id="521f0-130">Administration: Remove the user account from the site admins access group</span></span>
    
- <span data-ttu-id="521f0-131">アクティブ コラボレーション:サイト メンバーのアクセス グループからユーザー アカウントを削除する</span><span class="sxs-lookup"><span data-stu-id="521f0-131">Active collaboration: Remove the user account from the site members access group</span></span>
    
- <span data-ttu-id="521f0-132">表示:サイト ビューアーのアクセス グループからユーザー アカウントを削除する</span><span class="sxs-lookup"><span data-stu-id="521f0-132">Viewing: Remove the user account from the site viewers access group</span></span>
    
<span data-ttu-id="521f0-133">Windows Server AD を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用して適切なユーザーを適切なアクセス グループから削除し、Office 365 サブスクリプションと同期されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="521f0-133">If you are managing user accounts and groups through Windows Server AD, remove the appropriate users from the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="521f0-134">Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="521f0-134">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="521f0-135">Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なユーザーを適切なアクセス グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="521f0-135">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to remove the appropriate users from the appropriate access groups.</span></span>
    
- <span data-ttu-id="521f0-p103">PowerShell、最初の[Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)します。その UPN でアクセス グループからユーザー アカウントを削除するには、次の PowerShell コマンドのブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="521f0-p103">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218). To remove a user account from an access group with its UPN, use the following PowerShell command block:</span></span>
    
```
$userUPN="<UPN of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

<span data-ttu-id="521f0-138">表示名を使ってアクセス グループからユーザー アカウントを削除するには、次の PowerShell コマンド ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="521f0-138">To remove a user account from an access group with its display name, use the following PowerShell command block:</span></span>
    
```
$userDisplayName="<display name of the user account>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userDisplayName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="remove-a-group"></a><span data-ttu-id="521f0-139">グループを削除する</span><span class="sxs-lookup"><span data-stu-id="521f0-139">Remove a group</span></span>

<span data-ttu-id="521f0-140">グループ全体のアクセスを削除する必要がある場合は、サイトでの参加に基づいてそのグループが現在メンバーになっているアクセス グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="521f0-140">To remove access for an entire group, you remove the group from the access group for which they are currently a member based on their participation in the site:</span></span>
  
- <span data-ttu-id="521f0-141">管理:サイト管理者のアクセス グループからグループを削除する</span><span class="sxs-lookup"><span data-stu-id="521f0-141">Administration: Remove the group from the site admins access group</span></span>
    
- <span data-ttu-id="521f0-142">アクティブ コラボレーション:サイト メンバーのアクセス グループからグループを削除する</span><span class="sxs-lookup"><span data-stu-id="521f0-142">Active collaboration: Remove the group from the site members access group</span></span>
    
- <span data-ttu-id="521f0-143">表示:サイト ビューアーのアクセス グループからグループを削除する</span><span class="sxs-lookup"><span data-stu-id="521f0-143">Viewing: Remove the group from the site viewers access group</span></span>
    
<span data-ttu-id="521f0-144">Windows Server Active Directory を使用してユーザー アカウントとグループを管理している場合は、Windows Server AD ユーザーとグループの標準的な管理手順を使用して適切なグループを適切なアクセス グループから削除し、Office 365 サブスクリプションと同期されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="521f0-144">If you are managing user accounts and groups through Windows Server Active Directory, remove the appropriate groups from the appropriate access groups using your normal Windows Server AD user and group management procedures and wait for synchronization with your Office 365 subscription.</span></span>
  
<span data-ttu-id="521f0-145">Office 365 を使用してユーザー アカウントとグループを管理する場合は、Office 管理者センターまたは PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="521f0-145">If you are managing user accounts and groups through Office 365, you can use the Office Admin center or PowerShell:</span></span>
  
- <span data-ttu-id="521f0-146">Office 管理者センターでは、ユーザー アカウント管理者または会社管理者の役割が割り当てられているユーザー アカウントでサインインし、グループを使用して適切なグループを適切なアクセス グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="521f0-146">For the Office Admin center, sign in with a user account that has been assigned the User Account Administrator or Company Administrator role and use Groups to remove the appropriate groups from the appropriate access groups.</span></span>
    
- <span data-ttu-id="521f0-147">PowerShell については、まず「[Azure Active Directory V2 PowerShell モジュールを使用した接続](https://go.microsoft.com/fwlink/?linkid=842218)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="521f0-147">For PowerShell, first [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>    
<span data-ttu-id="521f0-148">表示名を使用してアクセス グループからグループを削除するには、次の PowerShell コマンド ブロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="521f0-148">To remove a group from an access group using their display names, use the following PowerShell command block:</span></span>
    
```
$groupMemberName="<display name of the group to remove>"
$grpName="<display name of the access group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $grpName }).ObjectID
```

## <a name="create-a-documents-subfolder-with-custom-permissions"></a><span data-ttu-id="521f0-149">カスタムのアクセス許可を持つドキュメントのサブフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="521f0-149">Create a documents subfolder with custom permissions</span></span>

<span data-ttu-id="521f0-p104">分離したサイト内で作業している人々のサブセットでは、コラボレーションするためにプライバシー性の高い場所が必要になることがあります。SharePoint Online サイトでは、サイトの [ドキュメント] フォルダーにサブフォルダーを作成し、カスタムのアクセス許可を割り当てることがことができます。アクセス許可を持たないユーザーはサブフォルダーを表示できません。</span><span class="sxs-lookup"><span data-stu-id="521f0-p104">In some cases, a subset of the people working within the isolated site need a more private place to collaborate. For SharePoint Online sites, you can create a subfolder in the Documents folder of the site and assign custom permissions. Those without permissions will not see the subfolder.</span></span>
  
<span data-ttu-id="521f0-153">カスタムのアクセス許可を持つドキュメントのサブフォルダーを作成するには、以下のことを行います。</span><span class="sxs-lookup"><span data-stu-id="521f0-153">To create a documents subfolder with custom permissions, do the following:</span></span>
  
1. <span data-ttu-id="521f0-p105">サイト管理者のアクセス グループのメンバーであるアカウントを使用して Office 365 にサインインします。ヘルプを表示するには、「[一般法人向け Office 365 にサインインする場所](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="521f0-p105">Sign in to Office 365 with an account that is a member of the admins access group for the site. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="521f0-156">分離したチーム サイトに移動し、 **[ドキュメント]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-156">Go to the isolated team site and click **Documents**.</span></span>
    
3. <span data-ttu-id="521f0-157">カスタムのアクセス許可を持つサブフォルダーを格納するフォルダーをドキュメントのフォルダーの中で参照し、そのフォルダーを作成して開きます。</span><span class="sxs-lookup"><span data-stu-id="521f0-157">Browse to the folder in the documents folder that will contain the subfolder with custom permissions, create the folder, and then open it.</span></span>
    
4. <span data-ttu-id="521f0-158">[ **共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-158">Click **Share**.</span></span>
    
5. <span data-ttu-id="521f0-159">**[共有相手] > [詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-159">Click **Shared with > Advanced**.</span></span>
    
6. <span data-ttu-id="521f0-160">**[アクセス許可の継承の中止]** をクリックしてから、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-160">Click **Stop inheriting permissions**, and then click **OK**.</span></span>
    
7. <span data-ttu-id="521f0-161">[ **共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-161">Click **Share**.</span></span>
    
8. <span data-ttu-id="521f0-162">**[共有相手] > [詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-162">Click **Shared with > Advanced**.</span></span>
    
9. <span data-ttu-id="521f0-163">**[アクセス許可を付与する] > [共有相手] > [詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-163">Click **Grant Permissions > Shared with > Advanced**.</span></span>
    
10. <span data-ttu-id="521f0-164">[アクセス許可] ページをクリックして**\<サイト名 > リスト内のメンバー**。</span><span class="sxs-lookup"><span data-stu-id="521f0-164">On the permissions page, click **\<site name> Members in the list**.</span></span>
    
11. <span data-ttu-id="521f0-165">**\<サイト名 > のメンバー**ページ サイトのメンバーのアクセス グループの横のチェック マークを選択して、[**アクション**] をクリックして、**グループからユーザーを削除**] をクリック、し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-165">On the **\<site name> Members** page, select the checkmark next to the site members access group, click **Actions**, click **Remove users from group**, and then click **OK**.</span></span>
    
12. <span data-ttu-id="521f0-166">特定のメンバーをこのサブフォルダーに追加するには、 **[新規] > [ユーザーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-166">To add specific members to this subfolder, click **New > Add users**.</span></span>
    
13. <span data-ttu-id="521f0-167">**[共有]** ダイアログ ボックスで、サブフォルダー内のファイルでコラボレーションできるユーザー アカウントの名前を入力してから、 **[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="521f0-167">In the **Share** dialog box, type the names of the user accounts that can collaborate on files in the subfolder, and then click **Share**.</span></span>
    
14. <span data-ttu-id="521f0-168">Web ページを更新して新しい結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="521f0-168">Refresh the web page to see the new results.</span></span>
    
15. <span data-ttu-id="521f0-169">**グループ**の左側のナビゲーションで、をクリックして、**\<サイト名 > の訪問者**をグループ化し、(必要に応じて)、サブフォルダーにファイルを表示できるユーザー アカウントのセットを指定するのには 11-14 の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="521f0-169">Under **Groups** in the left navigation, click the **\<site name> Visitors** group and use steps 11-14 to specify the set of user accounts that can view the files in the subfolder (as needed).</span></span>
    
16. <span data-ttu-id="521f0-170">**グループ**の左側のナビゲーションで、をクリックして、**\<サイト名 > の所有者**をグループ化し、(必要に応じて)、サブフォルダーにアクセス許可を管理できるユーザー アカウントのセットを指定するのには 11-14 の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="521f0-170">Under **Groups** in the left navigation, click the **\<site name> Owners** group and use steps 11-14 to specify the set of user accounts that can administer the permissions in the subfolder (as needed).</span></span>
    
17. <span data-ttu-id="521f0-171">ブラウザーで **[ユーザーとグループ]** タブを閉じます。</span><span class="sxs-lookup"><span data-stu-id="521f0-171">Close the **People and Groups** tab in your browser.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="521f0-172">See Also</span><span class="sxs-lookup"><span data-stu-id="521f0-172">See Also</span></span>

[<span data-ttu-id="521f0-173">分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="521f0-173">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="521f0-174">分離した SharePoint Online チーム サイトの設計</span><span class="sxs-lookup"><span data-stu-id="521f0-174">Design an isolated SharePoint Online team site</span></span>](design-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="521f0-175">セキュリティ ソリューション</span><span class="sxs-lookup"><span data-stu-id="521f0-175">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="521f0-176">分離した SharePoint Online チーム サイトの展開</span><span class="sxs-lookup"><span data-stu-id="521f0-176">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



