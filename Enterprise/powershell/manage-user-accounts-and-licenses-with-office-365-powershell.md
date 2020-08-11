---
title: Microsoft 365 ユーザー アカウント、ライセンス、PowerShell を使用したグループを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: この記事では、PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する方法について説明します。
ms.openlocfilehash: b5a2d43ad4dee3a70f934f9fc52b93e7c99f3644
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605883"
---
# <a name="manage-microsoft-365-user-accounts-licenses-and-groups-with-powershell"></a><span data-ttu-id="3bb98-103">Microsoft 365 ユーザー アカウント、ライセンス、PowerShell を使用したグループを管理する</span><span class="sxs-lookup"><span data-stu-id="3bb98-103">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>

<span data-ttu-id="3bb98-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="3bb98-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="3bb98-105">Microsoft 365 管理者の主なタスクの1つは、ユーザーアカウント、ライセンス、およびグループを管理することです。</span><span class="sxs-lookup"><span data-stu-id="3bb98-105">One of the primary tasks of any Microsoft 365 administrator is managing user accounts, licenses, and groups.</span></span> <span data-ttu-id="3bb98-106">これらのタスクのほとんどの側面は、Microsoft 365 管理センターでも実行できますが、PowerShell を使用すると、他のタスクがより速く、簡単になります。</span><span class="sxs-lookup"><span data-stu-id="3bb98-106">Although you can accomplish most aspects of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with PowerShell.</span></span> 

<span data-ttu-id="3bb98-107">詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bb98-107">For more information, see these topics.</span></span>

## <a name="user-accounts"></a><span data-ttu-id="3bb98-108">ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="3bb98-108">User accounts</span></span>

- [<span data-ttu-id="3bb98-109">ユーザー アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="3bb98-109">Create user accounts</span></span>](create-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-110">ユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="3bb98-110">View user accounts</span></span>](view-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-111">ユーザー アカウントのプロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="3bb98-111">Configure user account properties</span></span>](configure-user-account-properties-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-112">ユーザー アカウントにロールを割り当てる</span><span class="sxs-lookup"><span data-stu-id="3bb98-112">Assign roles to user accounts</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-113">ユーザー アカウントを削除および復元する</span><span class="sxs-lookup"><span data-stu-id="3bb98-113">Delete and restore user accounts</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-114">ユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="3bb98-114">Block user accounts</span></span>](block-user-accounts-with-office-365-powershell.md)

## <a name="licenses-and-services"></a><span data-ttu-id="3bb98-115">ライセンスおよびサービス</span><span class="sxs-lookup"><span data-stu-id="3bb98-115">Licenses and services</span></span>
- [<span data-ttu-id="3bb98-116">ライセンスおよびサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="3bb98-116">View licenses and services</span></span>](view-licenses-and-services-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-117">ライセンスのあるユーザーとライセンスのないユーザーを表示する</span><span class="sxs-lookup"><span data-stu-id="3bb98-117">View licensed and unlicensed users</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-118">ユーザー アカウントにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="3bb98-118">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-119">アカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="3bb98-119">View account license and service details</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-120">サービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="3bb98-120">Disable access to services</span></span>](disable-access-to-services-with-office-365-powershell.md)
  - [<span data-ttu-id="3bb98-121">Sway へのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="3bb98-121">Disable access to Sway</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  - [<span data-ttu-id="3bb98-122">ユーザー ライセンスを割り当てる間、サービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="3bb98-122">Disable access to services while assigning user licenses</span></span>](disable-access-to-services-while-assigning-user-licenses.md)
- [<span data-ttu-id="3bb98-123">ユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="3bb98-123">Remove licenses from user accounts</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)

## <a name="groups"></a><span data-ttu-id="3bb98-124">グループ</span><span class="sxs-lookup"><span data-stu-id="3bb98-124">Groups</span></span>
- [<span data-ttu-id="3bb98-125">グループ メンバーシップを管理する</span><span class="sxs-lookup"><span data-stu-id="3bb98-125">Maintain group membership</span></span>](maintain-group-membership-with-office-365-powershell.md)
- [<span data-ttu-id="3bb98-126">Microsoft 365 グループを管理する</span><span class="sxs-lookup"><span data-stu-id="3bb98-126">Manage Microsoft 365 groups</span></span>](manage-office-365-groups-with-powershell.md)

