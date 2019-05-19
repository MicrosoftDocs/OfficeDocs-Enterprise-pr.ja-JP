---
title: ユーザーアカウントに Office 365 ライセンスを割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
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
description: ユーザーアカウントに Office 365 ライセンスを個別に、またはグループメンバーシップに基づいて割り当てる方法について説明します。
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164602"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="7547b-103">ユーザーアカウントに Office 365 ライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="7547b-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="7547b-104">クラウド専用の id モデルでは、作成方法に応じて、ユーザーアカウントの作成時に Office 365 ライセンスをユーザーアカウントに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="7547b-104">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="7547b-105">ハイブリッド id モデルでは、Active Directory ドメインサービス (AD DS) ユーザーアカウントが初めて同期されるときに、Office 365 ライセンスが自動的に割り当てられることはありません。</span><span class="sxs-lookup"><span data-stu-id="7547b-105">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="7547b-106">どちらの場合も、ユーザーが Office 365 サービス (電子メールや Microsoft Teams など) にアクセスできるように、ユーザーアカウントにライセンスを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7547b-106">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="7547b-107">ユーザーアカウントには、個別に、またはグループメンバーシップを使用して、自動的にライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="7547b-107">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="7547b-108">Office 365 ライセンスを個々のユーザーアカウントに割り当てるには、次のものを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7547b-108">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="7547b-109">Microsoft 365 管理センター</span><span class="sxs-lookup"><span data-stu-id="7547b-109">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="7547b-110">Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="7547b-110">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="7547b-111">自動ライセンス割り当ての場合は、「 [AZURE AD でのグループベースのライセンス](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7547b-111">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7547b-112">次の手順</span><span class="sxs-lookup"><span data-stu-id="7547b-112">Next steps</span></span>

<span data-ttu-id="7547b-113">ライセンスが割り当てられているユーザーアカウントの完全なセットにより、次の準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="7547b-113">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="7547b-114">Office 365 ProPlus などのクライアントソフトウェアを展開する</span><span class="sxs-lookup"><span data-stu-id="7547b-114">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="7547b-115">モバイルデバイス管理を構成する</span><span class="sxs-lookup"><span data-stu-id="7547b-115">Configure mobile device management</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="7547b-116">サービスとアプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="7547b-116">Configure services and applications</span></span>](configure-services-and-applications.md)
