---
title: Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: 26b9ff81-93b0-4251-beaf-3c9f1d7c80c8
description: 概要:Office 365 PowerShell を使用してユーザー アカウントとライセンスを管理する方法について説明します。
ms.openlocfilehash: 333a9501d3dfcd2f9f254a7b58e9f8589b68f9cb
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748455"
---
# <a name="manage-user-accounts-and-licenses-with-office-365-powershell"></a><span data-ttu-id="51ff1-103">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="51ff1-103">Manage user accounts and licenses with Office 365 PowerShell</span></span>

<span data-ttu-id="51ff1-104">Office 365 管理者の主要なタスクの 1 つは、ユーザー アカウントとライセンスの管理です。</span><span class="sxs-lookup"><span data-stu-id="51ff1-104">One of the primary tasks of any Office 365 administrator is managing user accounts and licenses.</span></span> <span data-ttu-id="51ff1-105">Microsoft 365 管理センターでもこれらのタスクの一部を実行できますが、他のタスクについては、Office 365 PowerShell の方がより早く簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="51ff1-105">Although you can accomplish some of these tasks in the Microsoft 365 admin center, other tasks are much quicker and easier with Office 365 PowerShell.</span></span> <span data-ttu-id="51ff1-106">詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="51ff1-106">For more information, see the following topics:</span></span>
  
- [<span data-ttu-id="51ff1-107">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="51ff1-107">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-108">ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する</span><span class="sxs-lookup"><span data-stu-id="51ff1-108">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-109">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="51ff1-109">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-110">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="51ff1-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-111">Office 365 PowerShell でロールをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="51ff1-111">Assign roles to user accounts with Office 365 PowerShell</span></span>](assign-roles-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-112">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="51ff1-112">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-113">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="51ff1-113">Remove licenses from user accounts with Office 365 PowerShell</span></span>](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-114">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="51ff1-114">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-115">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="51ff1-115">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-116">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="51ff1-116">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-117">Office 365 PowerShell でユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="51ff1-117">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="51ff1-118">Office 365 PowerShell でユーザー アカウント プロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="51ff1-118">Configure user account properties with Office 365 PowerShell</span></span>](configure-user-account-properties-with-office-365-powershell.md)
    

