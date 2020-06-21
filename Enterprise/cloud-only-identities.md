---
title: Microsoft 365 クラウドのみの id
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/09/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Microsoft 365 サブスクリプションがクラウド専用の id を使用しているときに、ユーザーとグループを作成する方法について説明します。
ms.openlocfilehash: f510d82186e9a44c20bd20f1c7b5a7a44c8b765b
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774832"
---
# <a name="microsoft-365-cloud-only-identity"></a><span data-ttu-id="3c0c0-103">Microsoft 365 クラウドのみの id</span><span class="sxs-lookup"><span data-stu-id="3c0c0-103">Microsoft 365 cloud-only identity</span></span>

<span data-ttu-id="3c0c0-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="3c0c0-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="3c0c0-105">クラウド専用の id を使用すると、すべてのユーザー、グループ、および連絡先が、Microsoft 365 サブスクリプションの Azure Active Directory (Azure AD) テナントに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="3c0c0-106">ここでは、クラウド専用の id の基本的なコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-106">Here are the basic components of cloud-only identity.</span></span>
 
![クラウド専用の id の基本コンポーネント](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="3c0c0-108">組織内のユーザーとユーザーアカウントは、さまざまな方法で分類できます。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-108">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="3c0c0-109">たとえば、一部は従業員で、恒久的な状態になっています。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-109">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="3c0c0-110">一部のベンダー、請負業者、またはパートナーは、一時的な状態になっています。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-110">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="3c0c0-111">ユーザーアカウントを持たない外部ユーザーも、対話とコラボレーションをサポートするために特定のサービスやリソースへのアクセスを引き続き付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-111">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="3c0c0-112">たとえば、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-112">For example:</span></span>

- <span data-ttu-id="3c0c0-113">テナント アカウントは、組織内でクラウド サービスのライセンスを付与したユーザーを表します。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-113">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="3c0c0-114">B2B (Business to Busines) アカウントは、コラボレーションへの参加のために招待された組織外部のユーザーを表します。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-114">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration</span></span>

<span data-ttu-id="3c0c0-115">組織内のユーザーの種類の株価を取得します。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-115">Take stock of the types of users in your organization.</span></span> <span data-ttu-id="3c0c0-116">グループ化とは</span><span class="sxs-lookup"><span data-stu-id="3c0c0-116">What are the groupings?</span></span> <span data-ttu-id="3c0c0-117">たとえば、組織に対して、レベルの高い機能または目的によってユーザーをグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-117">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="3c0c0-118">Additionally, some cloud services can be shared with users outside your organization without any user accounts.</span><span class="sxs-lookup"><span data-stu-id="3c0c0-118">Additionally, some cloud services can be shared with users outside your organization without any user accounts.</span></span> <span data-ttu-id="3c0c0-119">You'll need to identify these groups of users as well.</span><span class="sxs-lookup"><span data-stu-id="3c0c0-119">You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="3c0c0-120">Azure AD のグループは、クラウド環境の管理を簡素化するいくつかの目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-120">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="3c0c0-121">たとえば、Azure AD グループでは、次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-121">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="3c0c0-122">グループベースのライセンスを使用して、Microsoft 365 のライセンスをメンバーとして追加されるとすぐに、自動的にユーザーアカウントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-122">Use group-based licensing to assign licenses for Microsoft 365 to your user accounts automatically as soon as they are added as members.</span></span>
- <span data-ttu-id="3c0c0-123">ユーザーアカウントの属性 (部署名など) に基づいて、ユーザーアカウントを特定のグループに動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-123">Add user accounts to specific groups dynamically based on user account attributes, such as department name.</span></span>
- <span data-ttu-id="3c0c0-124">サービスとしてのソフトウェア (SaaS) アプリケーションのユーザーを自動的にプロビジョニングし、多要素認証 (MFA) やその他の条件付きアクセスルールを使用してそれらのアプリケーションへのアクセスを保護します。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-124">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication (MFA) and other Conditional Access rules.</span></span>
- <span data-ttu-id="3c0c0-125">SharePoint Online チームサイトのアクセス許可とアクセス許可のレベルをプロビジョニングします。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-125">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="3c0c0-126">次の方法で新しい***ユーザー***を作成します。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-126">You create new ***users*** with:</span></span>

- [<span data-ttu-id="3c0c0-127">Microsoft 365 管理センター</span><span class="sxs-lookup"><span data-stu-id="3c0c0-127">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="3c0c0-128">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c0c0-128">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="3c0c0-129">次のものを使用して、新しい***グループ***を作成します。</span><span class="sxs-lookup"><span data-stu-id="3c0c0-129">You create new ***groups*** with:</span></span>

- [<span data-ttu-id="3c0c0-130">Microsoft 365 管理センター</span><span class="sxs-lookup"><span data-stu-id="3c0c0-130">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="3c0c0-131">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c0c0-131">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identity"></a><span data-ttu-id="3c0c0-132">クラウド専用の id の次の手順</span><span class="sxs-lookup"><span data-stu-id="3c0c0-132">Next step for cloud-only identity</span></span>

[<span data-ttu-id="3c0c0-133">ユーザー アカウントにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="3c0c0-133">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
