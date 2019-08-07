---
title: Windows PowerShell を使用して Office 365 でレポートを作成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/22/2018
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: '概要: Office 365 PowerShell を使用して、Microsoft 365 管理センターでは作成できないレポートを作成します。'
ms.openlocfilehash: 6ad41169c11150706381c45bf13e24a2ac1baf5c
ms.sourcegitcommit: 1c97471f47e1869f6db684f280f9085b7c2ff59f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "35782577"
---
# <a name="use-windows-powershell-to-create-reports-in-office-365"></a><span data-ttu-id="65a00-103">Windows PowerShell を使用して Office 365 でレポートを作成する</span><span class="sxs-lookup"><span data-stu-id="65a00-103">Use Windows PowerShell to create reports in Office 365</span></span>

 <span data-ttu-id="65a00-104">**概要:** Office 365 PowerShell を使用して、Microsoft 365 管理センターでは作成できないレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="65a00-104">**Summary:** Use Office 365 PowerShell to create reports that you cannot produce in the Office 365 Admin center.</span></span>
  
<span data-ttu-id="65a00-105">Microsoft 365 管理者センターでは、数多くのさまざまなレポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="65a00-105">There are many different reports available in the Office 365 Admin center.</span></span> <span data-ttu-id="65a00-106">ただし、これらのレポートは大量の情報を提供するだけで、さらに詳細が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="65a00-106">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="65a00-107">そんなときに、Office 365 PowerShell が必要になります。</span><span class="sxs-lookup"><span data-stu-id="65a00-107">That's when you need Office 365 PowerShell</span></span>
  
<span data-ttu-id="65a00-108">次に示す記事では、Office 365 PowerShell を使用して Office 365 テナントから情報を取得する方法について説明しています。</span><span class="sxs-lookup"><span data-stu-id="65a00-108">These articles that describe how to use Office 365 PowerShell to obtain information from your Office 365 tenant:</span></span>
  
- <span data-ttu-id="65a00-109">Office 365 PowerShell を使用したレポート作成の概要。</span><span class="sxs-lookup"><span data-stu-id="65a00-109">Getting started with reporting using Office 365 PowerShell:</span></span>
    
  - [<span data-ttu-id="65a00-110">Office 365 PowerShell では、Office 365 管理センターに表示されない追加情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="65a00-110">Office 365 PowerShell can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="65a00-111">Office 365 PowerShell はデータのフィルター処理に優れています。</span><span class="sxs-lookup"><span data-stu-id="65a00-111">Office 365 PowerShell is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="65a00-112">Office 365 PowerShell を使用すると、データの印刷や保存が簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="65a00-112">Office 365 PowerShell makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="65a00-113">ユーザー アカウントおよびライセンスのレポート:</span><span class="sxs-lookup"><span data-stu-id="65a00-113">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="65a00-114">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="65a00-114">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="65a00-115">ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する</span><span class="sxs-lookup"><span data-stu-id="65a00-115">View licensed and unlicensed users with Office 365 PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="65a00-116">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="65a00-116">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="65a00-117">Office 365 PowerShell でユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="65a00-117">View user accounts with Office 365 PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="65a00-118">SharePoint Online のレポート:</span><span class="sxs-lookup"><span data-stu-id="65a00-118">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="65a00-119">Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する</span><span class="sxs-lookup"><span data-stu-id="65a00-119">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](http://technet.microsoft.com/library/9680af2e-a965-4e62-92ee-da72105c7800.aspx)
    
  - [<span data-ttu-id="65a00-120">Manage SharePoint Online site groups with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="65a00-120">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>](http://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="65a00-121">Exchange Online のレポート:</span><span class="sxs-lookup"><span data-stu-id="65a00-121">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="65a00-122">Display Exchange Online mailbox information with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="65a00-122">Display Exchange Online mailbox information with Office 365 PowerShell</span></span>](http://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="65a00-123">Display Exchange Online reports with Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="65a00-123">Display Exchange Online reports with Office 365 PowerShell</span></span>](http://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="65a00-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="65a00-124">See also</span></span>

#### 

[<span data-ttu-id="65a00-125">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="65a00-125">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="65a00-126">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="65a00-126">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="65a00-127">Office 365 PowerShell を使用して SharePoint Online を管理する</span><span class="sxs-lookup"><span data-stu-id="65a00-127">Manage SharePoint Online with Office 365 PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="65a00-128">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="65a00-128">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
