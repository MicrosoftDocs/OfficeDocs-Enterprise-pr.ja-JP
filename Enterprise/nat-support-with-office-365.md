---
title: Office 365 の NAT サポート
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: '概要: ネットワーク アドレス変換 (NAT) を使用して、組織内で IP アドレスごとに使用できるクライアントの正しい数を見積もる方法の詳細について説明します。'
ms.openlocfilehash: 04aec45b7d6c68b3e32d4ee384c9927896849bab
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998542"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="508f2-103">Office 365 の NAT サポート</span><span class="sxs-lookup"><span data-stu-id="508f2-103">NAT support with Office 365</span></span>

<span data-ttu-id="508f2-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="508f2-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="508f2-105">ガイダンスでは以前、Office 365 に接続するために IP アドレスごとに使用する必要がある Exchange クライアントの最大数は、ネットワーク ポート 1 つあたり約 2,000 と推奨していました。</span><span class="sxs-lookup"><span data-stu-id="508f2-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="508f2-106">NAT を使用する理由は何ですか。</span><span class="sxs-lookup"><span data-stu-id="508f2-106">Why use NAT?</span></span>

<span data-ttu-id="508f2-107">NAT の使用により、企業ネットワークの何千人ものユーザーが、少数のパブリック ルーティング可能な IP アドレスを「共有」することができます。</span><span class="sxs-lookup"><span data-stu-id="508f2-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="508f2-108">Most corporate networks use private (RFC1918) IP address space.</span><span class="sxs-lookup"><span data-stu-id="508f2-108">Most corporate networks use private (RFC1918) IP address space.</span></span> <span data-ttu-id="508f2-109">Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span><span class="sxs-lookup"><span data-stu-id="508f2-109">Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="508f2-110">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services.</span><span class="sxs-lookup"><span data-stu-id="508f2-110">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services.</span></span> <span data-ttu-id="508f2-111">These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses.</span><span class="sxs-lookup"><span data-stu-id="508f2-111">These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses.</span></span> <span data-ttu-id="508f2-112">Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span><span class="sxs-lookup"><span data-stu-id="508f2-112">Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="508f2-113">Office 365 に対して多数の接続を同時に開く必要があるのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="508f2-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="508f2-114">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.).</span><span class="sxs-lookup"><span data-stu-id="508f2-114">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.).</span></span> <span data-ttu-id="508f2-115">Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted.</span><span class="sxs-lookup"><span data-stu-id="508f2-115">Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted.</span></span> <span data-ttu-id="508f2-116">Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used.</span><span class="sxs-lookup"><span data-stu-id="508f2-116">Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used.</span></span> <span data-ttu-id="508f2-117">In this scenario, the maximum number of ports could be less than 64,000.</span><span class="sxs-lookup"><span data-stu-id="508f2-117">In this scenario, the maximum number of ports could be less than 64,000.</span></span> <span data-ttu-id="508f2-118">Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span><span class="sxs-lookup"><span data-stu-id="508f2-118">Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="508f2-119">Office 365 で単一のパブリック IP アドレスにサポートされるデバイスの最大数の計算</span><span class="sxs-lookup"><span data-stu-id="508f2-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="508f2-120">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client.</span><span class="sxs-lookup"><span data-stu-id="508f2-120">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="508f2-121">Also, a peak factor should be used for the port usage (minimum 4).</span><span class="sxs-lookup"><span data-stu-id="508f2-121">Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="508f2-122">**IP アドレスごとにサポートされるデバイスの数を計算するには、次の式を使用します。**</span><span class="sxs-lookup"><span data-stu-id="508f2-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="508f2-123">単一のパブリック IP アドレスにサポートされるデバイスの最大数 = (64,000 - 制限されたポート) / (ピーク ポート消費量 + ピーク係数)</span><span class="sxs-lookup"><span data-stu-id="508f2-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="508f2-124">**たとえば、次のような条件だとします。**</span><span class="sxs-lookup"><span data-stu-id="508f2-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="508f2-125">**制限されたポート:** オペレーティング システムで 4,000</span><span class="sxs-lookup"><span data-stu-id="508f2-125">**Restricted ports:** 4,000 for the operating system</span></span>

- <span data-ttu-id="508f2-126">**ピーク ポート消費量:** デバイスあたり 6</span><span class="sxs-lookup"><span data-stu-id="508f2-126">**Peak port consumption:** 6 per device</span></span>

- <span data-ttu-id="508f2-127">**ピーク係数:** 4</span><span class="sxs-lookup"><span data-stu-id="508f2-127">**Peak factor:** 4</span></span>

<span data-ttu-id="508f2-128">このような条件の場合、単一のパブリック IP アドレスにサポートされるデバイスの最大数 = (64,000 - 4,000) / (6 + 4) = 6,000 </span><span class="sxs-lookup"><span data-stu-id="508f2-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="508f2-129">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2.</span><span class="sxs-lookup"><span data-stu-id="508f2-129">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2.</span></span> <span data-ttu-id="508f2-130">You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span><span class="sxs-lookup"><span data-stu-id="508f2-130">You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="508f2-131">単一のパブリック IP アドレスでより多くのデバイスをサポートする場合、サポートできるデバイスの最大数を説明した手順に従って査定します。</span><span class="sxs-lookup"><span data-stu-id="508f2-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="508f2-132">Monitor network traffic to determine peak port consumption per client.</span><span class="sxs-lookup"><span data-stu-id="508f2-132">Monitor network traffic to determine peak port consumption per client.</span></span> <span data-ttu-id="508f2-133">You should collect this data:</span><span class="sxs-lookup"><span data-stu-id="508f2-133">You should collect this data:</span></span>
  
- <span data-ttu-id="508f2-134">複数の場所から収集する</span><span class="sxs-lookup"><span data-stu-id="508f2-134">From multiple locations</span></span>
    
- <span data-ttu-id="508f2-135">複数のデバイスから収集する</span><span class="sxs-lookup"><span data-stu-id="508f2-135">From multiple devices</span></span>
    
- <span data-ttu-id="508f2-136">複数回にわたって収集する</span><span class="sxs-lookup"><span data-stu-id="508f2-136">At multiple times</span></span>
    
<span data-ttu-id="508f2-137">上記の計算式を使い、クライアントの環境でサポート可能な IP アドレスあたりの最大ユーザー数を計算します。</span><span class="sxs-lookup"><span data-stu-id="508f2-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="508f2-138">There are various methods for distributing client load across additional public IP addresses.</span><span class="sxs-lookup"><span data-stu-id="508f2-138">There are various methods for distributing client load across additional public IP addresses.</span></span> <span data-ttu-id="508f2-139">Strategies available depend on the capabilities of the corporate gateway solution.</span><span class="sxs-lookup"><span data-stu-id="508f2-139">Strategies available depend on the capabilities of the corporate gateway solution.</span></span> <span data-ttu-id="508f2-140">The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway.</span><span class="sxs-lookup"><span data-stu-id="508f2-140">The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway.</span></span> <span data-ttu-id="508f2-141">Another alternative that many gateway devices offer is the ability to use a pool of IP addresses.</span><span class="sxs-lookup"><span data-stu-id="508f2-141">Another alternative that many gateway devices offer is the ability to use a pool of IP addresses.</span></span> <span data-ttu-id="508f2-142">The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span><span class="sxs-lookup"><span data-stu-id="508f2-142">The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="508f2-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="508f2-143">See also</span></span>

[<span data-ttu-id="508f2-144">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="508f2-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="508f2-145">Office 365 エンドポイントの FAQ</span><span class="sxs-lookup"><span data-stu-id="508f2-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
