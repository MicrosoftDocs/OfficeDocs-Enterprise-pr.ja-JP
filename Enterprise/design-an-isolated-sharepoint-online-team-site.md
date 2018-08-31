---
title: 分離した SharePoint Online チーム サイトの設計
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: 概要:分離した SharePoint Online チーム サイトの設計プロセスをステップごとに示します。
ms.openlocfilehash: 4807b7cef0a401901eb5abec3d683ca67b2193db
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914842"
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a><span data-ttu-id="03dbe-103">分離した SharePoint Online チーム サイトの設計</span><span class="sxs-lookup"><span data-stu-id="03dbe-103">Design an isolated SharePoint Online team site</span></span>

 <span data-ttu-id="03dbe-104">**概要:** 分離した SharePoint Online チーム サイトの設計プロセスをステップごとに示します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-104">**Summary:** Step through the design process for isolated SharePoint Online team sites.</span></span>
  
<span data-ttu-id="03dbe-105">この記事では、分離した SharePoint Online チーム サイトを作成する前に行う必要がある設計上の主要な決定事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-105">This article takes you through the key design decisions you must make before creating an isolated SharePoint Online team site.</span></span>
  
## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a><span data-ttu-id="03dbe-106">フェーズ 1:SharePoint グループおよびアクセス許可レベルを決定します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-106">Phase 1: Determine your SharePoint groups and permission levels</span></span>

<span data-ttu-id="03dbe-107">既定では、すべての SharePoint Online チーム サイトは次の SharePoint グループを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="03dbe-107">Every SharePoint Online team site by default is created with the following SharePoint groups:</span></span>
  
- <span data-ttu-id="03dbe-108">\<サイト名 > のメンバー</span><span class="sxs-lookup"><span data-stu-id="03dbe-108">\<site name> Members</span></span>
    
- <span data-ttu-id="03dbe-109">\<サイト名 > の訪問者</span><span class="sxs-lookup"><span data-stu-id="03dbe-109">\<site name> Visitors</span></span>
    
- <span data-ttu-id="03dbe-110">\<サイト名 > の所有者</span><span class="sxs-lookup"><span data-stu-id="03dbe-110">\<site name> Owners</span></span>
    
<span data-ttu-id="03dbe-111">これらのグループは、Office 365 と Azure Active Directory (AD) のグループとは別であり、サイトのリソースにアクセス許可を割り当てるための基盤になります。</span><span class="sxs-lookup"><span data-stu-id="03dbe-111">These groups are separate from Office 365 and Azure Active Directory (AD) groups and are the basis for assigning permissions for the resources of the site.</span></span>
  
<span data-ttu-id="03dbe-p101">SharePoint グループのメンバーがサイトで実行できる内容を決定する特定のアクセス許可のセットが、アクセス許可レベルになります。SharePoint Online チーム サイトでは、既定では次の 3 つのアクセス許可レベルがあります。編集、読み取り、フル コントロールです。次の表は、SharePoint グループと割り当てられるアクセス許可レベルとの既定の相関関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p101">The set of specific permissions that determines what a member of a SharePoint group can do in a site is a permission level. There are three permission levels by default for a SharePoint Online team site: Edit, Read, and Full control. The following table shows the default correlation of SharePoint groups and assigned permission levels:</span></span>
  
|<span data-ttu-id="03dbe-115">**SharePoint グループ**</span><span class="sxs-lookup"><span data-stu-id="03dbe-115">**SharePoint group**</span></span>|<span data-ttu-id="03dbe-116">**アクセス許可レベル**</span><span class="sxs-lookup"><span data-stu-id="03dbe-116">**Permission level**</span></span>|
|:-----|:-----|
|<span data-ttu-id="03dbe-117">\<サイト名 > のメンバー</span><span class="sxs-lookup"><span data-stu-id="03dbe-117">\<site name> Members</span></span>  <br/> |<span data-ttu-id="03dbe-118">編集</span><span class="sxs-lookup"><span data-stu-id="03dbe-118">Edit</span></span>  <br/> |
|<span data-ttu-id="03dbe-119">\<サイト名 > の訪問者</span><span class="sxs-lookup"><span data-stu-id="03dbe-119">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="03dbe-120">読み取り</span><span class="sxs-lookup"><span data-stu-id="03dbe-120">Read</span></span>  <br/> |
|<span data-ttu-id="03dbe-121">\<サイト名 > の所有者</span><span class="sxs-lookup"><span data-stu-id="03dbe-121">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="03dbe-122">フル コントロール</span><span class="sxs-lookup"><span data-stu-id="03dbe-122">Full control</span></span>  <br/> |
   
 <span data-ttu-id="03dbe-p102">**ベスト プラクティス:** 追加の SharePoint グループおよびアクセス許可レベルを作成できます。ただし、分離した SharePoint Online サイトには、既定の SharePoint グループおよびアクセス許可レベルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p102">**Best practice:** You can create additional SharePoint groups and permission levels. However, we recommend using the default SharePoint groups and permission levels for your isolated SharePoint Online site.</span></span>
  
<span data-ttu-id="03dbe-125">既定の SharePoint グループおよびアクセス許可レベルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-125">Here are the default SharePoint groups and permission levels.</span></span>
  
![SharePoint Online サイトの既定の SharePoint グループおよびアクセス許可レベル。](media/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)
  
## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a><span data-ttu-id="03dbe-127">フェーズ 2:アクセス グループを使用してアクセス許可をユーザーに割り当てる</span><span class="sxs-lookup"><span data-stu-id="03dbe-127">Phase 2: Assign permissions to users with access groups</span></span>

<span data-ttu-id="03dbe-p103">ユーザー アカウント、またはユーザー アカウントがメンバーである Office 365 グループまたは Azure AD グループを SharePoint グループに追加すると、ユーザーにアクセス許可を割り当てることができます。直接的に、または Office 365 グループか Azure AD グループのメンバーシップを通して間接的に追加されると、Office 365 ユーザー アカウントには、SharePoint グループに関連付けられているアクセス許可レベルが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p103">You can assign permissions to users by adding their user account, or an Office 365 or Azure AD group of which the user account is a member, to the SharePoint groups. Once added, the Office 365 user accounts, either directly or indirectly via membership in an Office 365 or Azure AD group, are assigned the permission level associated with the SharePoint group.</span></span>
  
<span data-ttu-id="03dbe-130">既定の SharePoint グループを使用した例:</span><span class="sxs-lookup"><span data-stu-id="03dbe-130">Using the default SharePoint groups as an example:</span></span>
  
- <span data-ttu-id="03dbe-131">メンバー、**\<サイト名 > のメンバー** **の編集**のアクセス許可レベルを割り当てられた SharePoint グループは、ユーザー アカウントとグループの両方を含めることができます、</span><span class="sxs-lookup"><span data-stu-id="03dbe-131">Members of the **\<site name> Members** SharePoint group, which can include both user accounts and groups, are assigned the **Edit** permission level</span></span>
    
- <span data-ttu-id="03dbe-132">メンバー、**\<サイト名 > の訪問者**SharePoint グループは、ユーザー アカウントとグループの両方を含めることができます、**読み取り**のアクセス許可レベルを割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="03dbe-132">Members of the **\<site name> Visitors** SharePoint group, which can include both user accounts and groups, are assigned the **Read** permission level</span></span>
    
- <span data-ttu-id="03dbe-133">メンバー、**\<サイト名 > の所有者**SharePoint グループは、ユーザー アカウントとグループの両方を含めることができます、**フル コントロール**アクセス許可レベルを割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="03dbe-133">Members of the **\<site name> Owners** SharePoint group, which can include both user accounts and groups, are assigned the **Full control** permission level</span></span>
    
 <span data-ttu-id="03dbe-p104">**ベスト プラクティス:** 個々のユーザー アカウントを使用してアクセス許可を管理することもできますが、代わりにアクセス グループと呼ばれる 1 つの Azure AD グループを使用することをお勧めします。この方法は、SharePoint グループごとにユーザー アカウントのリストを管理するのではなく、アクセス グループのメンバーシップでアクセス許可の管理を簡略化するものです。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p104">**Best practice:** Although you can manage permissions through individual user accounts, we recommend that you use a single Azure AD group, known as an access group, instead. This simplifies the management of permissions through membership in the access group, rather than managing the list of user accounts for each SharePoint group.</span></span>
  
<span data-ttu-id="03dbe-p105">Office 365 の Azure AD グループは、Office 365 のグループとは異なります。Azure AD グループは、**タイプ**が**セキュリティ**に設定された状態で Office 管理センターに表示され、メール アドレスはありません。以下で Azure AD グループを管理できます。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p105">Azure AD groups for Office 365 are different than Office 365 groups. Azure AD groups appear in the Office Admin center with their **Type** set to **Security** and do not have an email address. Azure AD groups can be managed within:</span></span>
  
- <span data-ttu-id="03dbe-139">Windows Server Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="03dbe-139">Windows Server Active Directory (AD)</span></span>
    
    <span data-ttu-id="03dbe-p106">これらは、オンプレミス Windows Server AD インフラストラクチャで作成され、Office 365 サブスクリプションと同期されたグループです。Office 管理センターで、これらのグループの**状態**は **Active Directory と同期済み**になっています。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p106">These are groups that have been created in your on-premises Windows Server AD infrastructure and synchronized to your Office 365 subscription. In the Office Admin center, these groups have a **Status** of **Synched with active directory**.</span></span>
    
- <span data-ttu-id="03dbe-142">Office 365</span><span class="sxs-lookup"><span data-stu-id="03dbe-142">Office 365</span></span>
    
    <span data-ttu-id="03dbe-p107">これらは、Office 管理センター、Azure ポータル、Microsoft PowerShell を使用して作成されたグループです。Office 管理センターで、これらのグループの**状態**は**クラウド**になっています。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p107">These are groups that have been created using either the Office Admin center, the Azure portal, or Microsoft PowerShell. In the Office Admin center, these groups have a **Status** of **Cloud**.</span></span>
    
 <span data-ttu-id="03dbe-145">**ベスト プラクティス:** オンプレミスの Windows Server AD を使用しており、Office 365 サブスクリプションと同期している場合は、Windows Server AD でユーザーとグループの管理を実行します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-145">**Best practice:** If you are using Windows Server AD on-premises and synchronizing with your Office 365 subscription, perform your user and group management with Windows Server AD.</span></span>
  
<span data-ttu-id="03dbe-146">分離した SharePoint Online チーム サイトの場合、推奨されるグループ構造は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="03dbe-146">For isolated SharePoint Online team sites, the recommended group structure looks like this:</span></span>
  
|<span data-ttu-id="03dbe-147">**SharePoint グループ**</span><span class="sxs-lookup"><span data-stu-id="03dbe-147">**SharePoint group**</span></span>|<span data-ttu-id="03dbe-148">**Azure AD ベースのアクセス グループ**</span><span class="sxs-lookup"><span data-stu-id="03dbe-148">**Azure AD-based access group**</span></span>|<span data-ttu-id="03dbe-149">**アクセス許可レベル**</span><span class="sxs-lookup"><span data-stu-id="03dbe-149">**Permission level**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="03dbe-150">\<サイト名 > のメンバー</span><span class="sxs-lookup"><span data-stu-id="03dbe-150">\<site name> Members</span></span>  <br/> |<span data-ttu-id="03dbe-151">\<サイト名 > のメンバー</span><span class="sxs-lookup"><span data-stu-id="03dbe-151">\<site name> Members</span></span>  <br/> |<span data-ttu-id="03dbe-152">編集</span><span class="sxs-lookup"><span data-stu-id="03dbe-152">Edit</span></span>  <br/> |
|<span data-ttu-id="03dbe-153">\<サイト名 > の訪問者</span><span class="sxs-lookup"><span data-stu-id="03dbe-153">\<site name> Visitors</span></span>  <br/> |<span data-ttu-id="03dbe-154">\<サイト名 > の閲覧者</span><span class="sxs-lookup"><span data-stu-id="03dbe-154">\<site name> Viewers</span></span>  <br/> |<span data-ttu-id="03dbe-155">読み取り</span><span class="sxs-lookup"><span data-stu-id="03dbe-155">Read</span></span>  <br/> |
|<span data-ttu-id="03dbe-156">\<サイト名 > の所有者</span><span class="sxs-lookup"><span data-stu-id="03dbe-156">\<site name> Owners</span></span>  <br/> |<span data-ttu-id="03dbe-157">\<サイト名 > 管理者</span><span class="sxs-lookup"><span data-stu-id="03dbe-157">\<site name> Admins</span></span>  <br/> |<span data-ttu-id="03dbe-158">フル コントロール</span><span class="sxs-lookup"><span data-stu-id="03dbe-158">Full control</span></span>  <br/> |
   
 <span data-ttu-id="03dbe-p108">**ベスト プラクティス:** SharePoint グループのメンバーには Office 365 グループまたは Azure AD グループを使用できますが、Azure AD グループを使用することをお勧めします。Azure AD グループは、Windows Server AD または Office 365 を通して管理され、ネストされたグループを使用してアクセス許可を柔軟に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p108">**Best practice:** Although you can use either Office 365 or Azure AD groups as members of SharePoint groups, we recommend that you use Azure AD groups. Azure AD groups, managed either through Windows Server AD or Office 365, give you more flexibility to use nested groups to assign permissions.</span></span>
  
<span data-ttu-id="03dbe-161">ここでは、既定の SharePoint グループの Azure AD ベースのアクセス グループを使用するように構成します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-161">Here are the default SharePoint groups configured to use Azure AD-based access groups.</span></span>
  
![既定の SharePoint Online サイト グループのメンバーとしてアクセス グループを使用する。](media/50a76328-ae69-483e-9029-ac4e7357b5ef.png)
  
<span data-ttu-id="03dbe-163">3 つのアクセス グループを設計するときは、以下の点にご注意ください。</span><span class="sxs-lookup"><span data-stu-id="03dbe-163">When designing the three access groups, keep the following in mind:</span></span>
  
- <span data-ttu-id="03dbe-164">内のいくつかのメンバーのみが存在する必要があります、**\<サイト名 > 管理者**アクセス グループ、チーム サイトの管理は、SharePoint Online の管理者の数が少ないに対応します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-164">There should be only a few members in the **\<site name> Admins** access group, corresponding to a small number of SharePoint Online administrators who are managing the team site.</span></span>
    
- <span data-ttu-id="03dbe-p109">サイトのメンバーのほとんど、**\<サイト名 > のメンバー**または**\<サイト名 > ビューアー**グループにアクセスします。サイト内のメンバー、**\<サイト名 > のメンバー**アクセス グループが削除、またはサイト内のリソースを変更、そのメンバーシップを慎重に検討することにあります。判断に迷う場合、サイト メンバーの追加、**\<サイト名 > の閲覧者**アクセス グループ。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p109">Most of your site members are in the **\<site name> Members** or **\<site name> Viewers** access groups. Because site members in the **\<site name> Members** access group have the ability to delete or modify resources in the site, carefully consider its membership. When in doubt, add the site member to the **\<site name> Viewers** access group.</span></span>
    
<span data-ttu-id="03dbe-168">ここでは、SharePoint グループおよび ProjectX という名前の独立したサイトのアクセス グループの例です。</span><span class="sxs-lookup"><span data-stu-id="03dbe-168">Here is an example of the SharePoint groups and access groups for an isolated site named ProjectX.</span></span>
  
![ProjectX という名前の SharePoint Online サイトのアクセス グループを使用する場合の例。](media/13afe542-9ffd-4671-9f48-210a0e2a502a.png)
  
## <a name="phase-3-use-nested-azure-ad-groups"></a><span data-ttu-id="03dbe-170">フェーズ 3: ネストされた Azure AD グループを使用する</span><span class="sxs-lookup"><span data-stu-id="03dbe-170">Phase 3: Use nested Azure AD groups</span></span>

<span data-ttu-id="03dbe-p110">少数のユーザーに限定されるプロジェクトの場合、ほとんどのシナリオはサイトの SharePoint グループに追加される単一レベルの Azure AD ベースのアクセス グループに収まります。ただし、多数のユーザーがおり、それらのユーザーが既に確立された Azure AD グループのメンバーである場合、ネストされたグループ、つまり他のグループがメンバーとして含まれるグループを使用することで簡単に SharePoint アクセス許可を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p110">For a project confined to a small number of people, a single level of Azure AD-based access groups added to the SharePoint groups of the site will fit most scenarios. However, if you have a large number of people and those people are already members of established Azure AD groups, you can more easily assign SharePoint permissions by using nested groups, or groups that contain other groups as members.</span></span>
  
<span data-ttu-id="03dbe-p111">たとえば、営業部門、マーケティング部門、エンジニアリング部門、法律部門の役員間でコラボレーションするための分離した SharePoint Online チーム サイトを作成したいと考えており、それらの部門には既に役員のユーザー アカウントのメンバーシップを持つ独自のグループが存在するとします。この場合、新しいサイト メンバー用に新しいグループを作成して、それぞれの役員ユーザー アカウントをすべてそこに含めるのではなく、各部門の既存の役員グループを新しいグループに入れます。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p111">For example, you want to create an isolated SharePoint online team site for collaboration among the executives of the sales, marketing, engineering, legal, and support departments and those departments already their own groups with executive user account membership. Rather than creating a new group for the new site members and placing all the individual executive user accounts in it, put the existing executive groups for each department in the new group.</span></span>
  
 <span data-ttu-id="03dbe-p112"> 複数の組織間で 1 つの Office 365 サブスクリプションを共有している場合、1 つの組織の 1 つの分離したサイトに単一レベルのグループ メンバーシップが存在することになり、膨大な数のユーザー アカウントを処理しなければならないため、管理が難しくなる可能性があります。この場合、組織内のグループが含まれるネストされた Azure AD グループを組織ごとに使用して、アクセス許可を管理することができます。</span><span class="sxs-lookup"><span data-stu-id="03dbe-p112">If you are sharing an Office 365 subscription between multiple organizations, a single level of group membership for an isolated site for an organization might become difficult to manage due to the sheer number of user accounts. In this case, you can use nested Azure AD groups for each organization that contain the groups within their organizations to manage the permissions.</span></span>
  
<span data-ttu-id="03dbe-177">ネストされた Azure AD グループを使用するには、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-177">To use nested Azure AD groups:</span></span>
  
1. <span data-ttu-id="03dbe-178">ユーザー アカウントを含める Azure AD グループを特定するか作成し、適切なユーザー アカウントをメンバーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-178">Identify or create the Azure AD groups that will contain user accounts and add the appropriate user accounts as members.</span></span>
    
2. <span data-ttu-id="03dbe-179">他の Azure AD グループを含めるコンテナーとなる Azure AD ベースのアクセス グループを作成し、それらのグループをメンバーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-179">Create the container Azure AD-based access group that will contain the other Azure AD groups and add those groups as members.</span></span>
    
3.  <span data-ttu-id="03dbe-180"> コンテナー アクセス グループの適切なアクセス レベルについては、SharePoint グループと、対応するアクセス許可レベルを識別します。</span><span class="sxs-lookup"><span data-stu-id="03dbe-180">For the appropriate level of access for the container access group, identify the SharePoint group and corresponding permission level.</span></span>
    
> [!NOTE]
> <span data-ttu-id="03dbe-181">ネストされた Office 365 グループを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="03dbe-181">You cannot use nested Office 365 groups.</span></span> 
  
<span data-ttu-id="03dbe-182">ProjectX メンバー アクセス グループのグループの入れ子になった Azure AD の例を次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="03dbe-182">Here is an example of nested Azure AD groups for the ProjectX member access group.</span></span>
  
![ProjectX サイトのメンバー アクセス グループの入れ子になったアクセス グループを使用する場合の例。](media/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)
  
<span data-ttu-id="03dbe-184">研究、エンジニア リング、およびプロジェクト内のユーザー アカウントのすべての潜在顧客のため、チーム サイトのメンバーにするものでは、ProjectX のメンバーのアクセス グループに、Azure AD グループを追加する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="03dbe-184">Because all of the user accounts in the Research, Engineering, and Project leads teams are intended to be site members, it is easier to add their Azure AD groups to the ProjectX Members access group.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="03dbe-185">次の手順</span><span class="sxs-lookup"><span data-stu-id="03dbe-185">Next step</span></span>

<span data-ttu-id="03dbe-186">分離したサイトを運用環境で作成および構成する準備ができたら、「[Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03dbe-186">When you are ready to create and configure an isolated site in production, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="03dbe-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="03dbe-187">See Also</span></span>

[<span data-ttu-id="03dbe-188">分離した SharePoint Online チーム サイト</span><span class="sxs-lookup"><span data-stu-id="03dbe-188">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="03dbe-189">分離した SharePoint Online チーム サイトの管理</span><span class="sxs-lookup"><span data-stu-id="03dbe-189">Manage an isolated SharePoint Online team site</span></span>](manage-an-isolated-sharepoint-online-team-site.md)
  
[<span data-ttu-id="03dbe-190">セキュリティ ソリューション</span><span class="sxs-lookup"><span data-stu-id="03dbe-190">Security solutions</span></span>](security-solutions.md)

[<span data-ttu-id="03dbe-191">分離した SharePoint Online チーム サイトの展開</span><span class="sxs-lookup"><span data-stu-id="03dbe-191">Deploy an isolated SharePoint Online team site</span></span>](deploy-an-isolated-sharepoint-online-team-site.md)



