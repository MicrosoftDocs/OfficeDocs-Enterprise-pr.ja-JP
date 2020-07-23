---
title: ユーザーアカウントに Microsoft 365 ライセンスを割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
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
description: Microsoft 365 ライセンスを個別に、またはグループメンバーシップに基づいてユーザーアカウントに割り当てる方法について説明します。
ms.openlocfilehash: 3a51f4966cdcfede57ad8a69546face160ae1750
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230003"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a><span data-ttu-id="16bf2-103">ユーザーアカウントに Microsoft 365 ライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="16bf2-103">Assign Microsoft 365 licenses to user accounts</span></span>

<span data-ttu-id="16bf2-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="16bf2-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="16bf2-105">クラウド専用の id モデルの場合は、作成方法に応じて、ユーザーアカウントの作成時に Microsoft 365 ライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="16bf2-105">For the cloud-only identity model, you can assign Microsoft 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="16bf2-106">ハイブリッド id モデルでは、Active Directory ドメインサービス (AD DS) ユーザーアカウントが初めて同期されるときに、Microsoft 365 ライセンスが自動的に割り当てられることはありません。</span><span class="sxs-lookup"><span data-stu-id="16bf2-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned a Microsoft 365 license.</span></span> <span data-ttu-id="16bf2-107">最初に、ユーザーの場所を使用して各ユーザーアカウントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16bf2-107">You must first configure each user account with a user location.</span></span>

<span data-ttu-id="16bf2-108">どちらの場合も、ユーザーが Microsoft 365 サービス (電子メールや Microsoft Teams など) にアクセスできるように、ユーザーアカウントにライセンスを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="16bf2-108">In either case, you must assign a license to user accounts so your users can access Microsoft 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="16bf2-109">ユーザーアカウントには、個別に、またはグループメンバーシップを使用して、自動的にライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="16bf2-109">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="16bf2-110">Microsoft 365 ライセンスを個々のユーザーアカウントに割り当てるには、次のものを使用できます。</span><span class="sxs-lookup"><span data-stu-id="16bf2-110">To assign Microsoft 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="16bf2-111">Microsoft 365 管理センター</span><span class="sxs-lookup"><span data-stu-id="16bf2-111">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
- [<span data-ttu-id="16bf2-112">PowerShell for Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="16bf2-112">PowerShell for Microsoft 365</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="16bf2-113">自動ライセンス割り当ての場合は、「 [AZURE AD でのグループベースのライセンス](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16bf2-113">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="16bf2-114">次の手順</span><span class="sxs-lookup"><span data-stu-id="16bf2-114">Next steps</span></span>

<span data-ttu-id="16bf2-115">ライセンスが割り当てられているユーザーアカウントの完全なセットにより、次の準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="16bf2-115">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="16bf2-116">セキュリティを実装する</span><span class="sxs-lookup"><span data-stu-id="16bf2-116">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="16bf2-117">Microsoft 365 アプリなどのクライアントソフトウェアを展開する</span><span class="sxs-lookup"><span data-stu-id="16bf2-117">Deploy client software, such as Microsoft 365 Apps</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [<span data-ttu-id="16bf2-118">Microsoft 365 でモバイルデバイス管理をセットアップする</span><span class="sxs-lookup"><span data-stu-id="16bf2-118">Set up Mobile Device Management in Microsoft 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="16bf2-119">サービスとアプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="16bf2-119">Configure services and applications</span></span>](configure-services-and-applications.md)
