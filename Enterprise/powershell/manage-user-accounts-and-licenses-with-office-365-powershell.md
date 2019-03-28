---
title: Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 概要:Office 365 PowerShell を使用してユーザー アカウントとライセンスを管理する方法について説明します。
ms.openlocfilehash: 604f0e6926936473f4b8e13546cdf0d7d839c667
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "30573891"
---
# <a name="manage-user-accounts-and-licenses-with-office-365-powershell"></a><span data-ttu-id="40d8d-103">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="40d8d-103">Manage user accounts and licenses with Office 365 PowerShell</span></span>

 <span data-ttu-id="40d8d-104">**概要:** Office 365 PowerShell を使用してユーザー アカウントとライセンスを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="40d8d-104">**Summary:** Learn how to manage user accounts and licenses with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="40d8d-105">Office 365 管理者の主要なタスクの 1 つは、ユーザー アカウントとライセンスの管理です。</span><span class="sxs-lookup"><span data-stu-id="40d8d-105">One of the primary tasks of any Office 365 administrator is managing user accounts and licenses.</span></span> <span data-ttu-id="40d8d-106">Microsoft 365 管理センターでもこれらのタスクの一部を実行できますが、他のタスクについては、Office 365 PowerShell の方がより早く簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="40d8d-106">Although you can accomplish some of these tasks in the Office 365 admin center, other tasks are much quicker and easier with Office 365 PowerShell.</span></span> <span data-ttu-id="40d8d-107">詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="40d8d-107">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="40d8d-108">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="40d8d-108">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-109">ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する</span><span class="sxs-lookup"><span data-stu-id="40d8d-109">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-110">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="40d8d-110">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-111">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="40d8d-111">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-112">Office 365 PowerShell でロールをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="40d8d-112">Assign roles to user accounts with Office 365 PowerShell</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-113">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="40d8d-113">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-114">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="40d8d-114">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-115">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="40d8d-115">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-116">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="40d8d-116">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-117">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="40d8d-117">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-118">Office 365 PowerShell でユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="40d8d-118">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="40d8d-119">Office 365 PowerShell でユーザー アカウント プロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="40d8d-119">Configure user account properties with Office 365 PowerShell</span></span>](configure-user-account-properties-with-office-365-powershell.md)
    

