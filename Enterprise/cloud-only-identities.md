---
title: Office 365 のクラウド専用の id
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Office 365 サブスクリプションがクラウド専用の id を使用している場合に、ユーザーとグループを作成する方法について説明します。
ms.openlocfilehash: 6815c89821216416379a27eb525e66b90b828ea8
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813415"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="6ae17-103">Office 365 のクラウド専用の id</span><span class="sxs-lookup"><span data-stu-id="6ae17-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="6ae17-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="6ae17-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="6ae17-105">クラウド専用の id を使用すると、すべてのユーザー、グループ、および連絡先が Office 365 サブスクリプションの Azure Active Directory (Azure AD) テナントに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6ae17-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="6ae17-106">ここでは、クラウド専用の id の基本的なコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="6ae17-106">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="6ae17-107">組織内のユーザーとユーザーアカウントは、さまざまな方法で分類できます。</span><span class="sxs-lookup"><span data-stu-id="6ae17-107">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="6ae17-108">たとえば、一部は従業員で、恒久的な状態になっています。</span><span class="sxs-lookup"><span data-stu-id="6ae17-108">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="6ae17-109">一部のベンダー、請負業者、またはパートナーは、一時的な状態になっています。</span><span class="sxs-lookup"><span data-stu-id="6ae17-109">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="6ae17-110">ユーザーアカウントを持たない外部ユーザーも、対話とコラボレーションをサポートするために特定のサービスやリソースへのアクセスを引き続き付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae17-110">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="6ae17-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6ae17-111">For example:</span></span>

- <span data-ttu-id="6ae17-112">テナント アカウントは、組織内でクラウド サービスのライセンスを付与したユーザーを表します。</span><span class="sxs-lookup"><span data-stu-id="6ae17-112">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="6ae17-113">ビジネスツービジネス (B2B) アカウントは、グループ作業への参加を招待する組織外のユーザーを表します。組織内のユーザーの種類のストックを取得します。</span><span class="sxs-lookup"><span data-stu-id="6ae17-113">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="6ae17-114">グループ化とは</span><span class="sxs-lookup"><span data-stu-id="6ae17-114">What are the groupings?</span></span> <span data-ttu-id="6ae17-115">たとえば、組織に対して、レベルの高い機能または目的によってユーザーをグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="6ae17-115">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="6ae17-p104">また、一部のクラウド サービスを、ユーザー アカウントを持たない組織外のユーザーと共有できます。この場合、このような外部ユーザーのグループも指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae17-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="6ae17-118">Azure AD のグループは、クラウド環境の管理を簡素化するいくつかの目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ae17-118">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="6ae17-119">たとえば、Azure AD グループでは、次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6ae17-119">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="6ae17-120">グループベースのライセンスを使用して、Office 365 のライセンスを追加後すぐに自動的にユーザーアカウントに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6ae17-120">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="6ae17-121">ユーザー アカウントの属性 (部門など) に基づいて、ユーザー アカウントを特定のグループに動的に追加する。</span><span class="sxs-lookup"><span data-stu-id="6ae17-121">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="6ae17-122">Software as a Service (SaaS) アプリケーションのユーザーを自動的にプロビジョニングし、多要素認証やその他の条件付きアクセス ルールでこれらのアプリケーションへのアクセスを保護する。</span><span class="sxs-lookup"><span data-stu-id="6ae17-122">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="6ae17-123">SharePoint Online チームサイトのアクセス許可とアクセス許可のレベルをプロビジョニングします。</span><span class="sxs-lookup"><span data-stu-id="6ae17-123">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="6ae17-124">次の方法で新しい***ユーザー***を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6ae17-124">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="6ae17-125">Microsoft 365 管理センター</span><span class="sxs-lookup"><span data-stu-id="6ae17-125">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="6ae17-126">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ae17-126">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="6ae17-127">次の方法で新しい***グループ***を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6ae17-127">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="6ae17-128">Microsoft 365 管理センター</span><span class="sxs-lookup"><span data-stu-id="6ae17-128">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="6ae17-129">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="6ae17-129">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="6ae17-130">クラウド専用の id の次の手順</span><span class="sxs-lookup"><span data-stu-id="6ae17-130">Next step for cloud-only identities</span></span>

[<span data-ttu-id="6ae17-131">ユーザー アカウントにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="6ae17-131">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
