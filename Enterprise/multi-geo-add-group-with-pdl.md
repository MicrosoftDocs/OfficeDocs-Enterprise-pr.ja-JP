---
title: 特定の PDL を使用して Microsoft 365 グループを作成する
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: 複数地域環境で指定された優先するデータの場所を使用して、Microsoft 365 グループを作成する方法について説明します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1648a9c974e7d25d989156c5a8e2d6818727a3b6
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606833"
---
# <a name="create-a-microsoft-365-group-with-a-specific-pdl"></a><span data-ttu-id="ef2ac-103">特定の PDL を使用して Microsoft 365 グループを作成する</span><span class="sxs-lookup"><span data-stu-id="ef2ac-103">Create a Microsoft 365 Group with a specific PDL</span></span>

<span data-ttu-id="ef2ac-104">複数地域環境のユーザーが Microsoft 365 グループを作成すると、グループの優先データの場所が自動的にユーザーのグループに設定されます。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-104">When users in a multi-geo environment create a Microsoft 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="ef2ac-105">グローバル管理者、SharePoint 管理者、Exchange 管理者は、選択した任意の地域にグループを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="ef2ac-106">特定の PDL でグループを作成する必要がある場合は、SharePoint 管理センターから、または Exchange Online New-unifiedgroup Microsoft PowerShell コマンドレットを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-106">If you need to create a group with a specific PDL, you can do that using from the SharePoint admin center or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="ef2ac-107">これを実行すると、グループ メールボックスとグループに関連付けられている SharePoint サイトは両方とも、指定した PDL でプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="ef2ac-108">指定した PDL を使用して Microsoft 365 グループを作成するには、グループサイトを作成する地理的な場所の SharePoint 管理センターに移動します。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-108">To create a Microsoft 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="ef2ac-109">例:</span><span class="sxs-lookup"><span data-stu-id="ef2ac-109">For example:</span></span>

<span data-ttu-id="ef2ac-110">オーストラリアの場所でグループ サイトを作成する場合は、https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement に移動します</span><span class="sxs-lookup"><span data-stu-id="ef2ac-110">If you want to create a group site in your Australia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="ef2ac-111">**[+ 作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="ef2ac-112">プロセスに従って、グループ サイトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="ef2ac-113">グループ サイトは、サイト作成要求を開始した SharePoint 管理センターに対応する地域の場所にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="ef2ac-114">Exchange PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="ef2ac-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="ef2ac-115">Exchange Online PowerShell に接続して、パラメーター *-MailBoxRegion* を地域の場所コードとともに渡します。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-115">Connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="ef2ac-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![構文を使用した New-UnifiedGroup PowerShell コマンドレットのスクリーンショット](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="ef2ac-118">SharePoint グループのサイト プロビジョニングがオンデマンドであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="ef2ac-119">サイトは、グループの所有者またはメンバーが初めてアクセスを試みたときにプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="ef2ac-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="ef2ac-120">地域の場所コード</span><span class="sxs-lookup"><span data-stu-id="ef2ac-120">Geo location codes</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="related-topics"></a><span data-ttu-id="ef2ac-121">関連トピック</span><span class="sxs-lookup"><span data-stu-id="ef2ac-121">Related topics</span></span>

[<span data-ttu-id="ef2ac-122">Exchange Online PowerShell への接続</span><span class="sxs-lookup"><span data-stu-id="ef2ac-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
