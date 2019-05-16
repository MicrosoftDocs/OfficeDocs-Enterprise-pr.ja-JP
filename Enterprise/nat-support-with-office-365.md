---
title: Office 365 の NAT サポート
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: 170e96ea-d65d-4e51-acac-1de56abe39b9
description: '概要: ネットワーク アドレス変換 (NAT) を使用して、組織内で IP アドレスごとに使用できるクライアントの正しい数を見積もる方法の詳細について説明します。'
ms.openlocfilehash: bdbf108163c7b22fd6d7583436af5f0ed655784c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069883"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="5289c-103">Office 365 の NAT サポート</span><span class="sxs-lookup"><span data-stu-id="5289c-103">NAT support with Office 365</span></span>

 <span data-ttu-id="5289c-104">**概要:** ネットワーク アドレス変換 (NAT) を使用して、組織内で IP アドレスごとに使用できるクライアントの正しい数を見積もる方法の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="5289c-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="5289c-105">ガイダンスでは以前、Office 365 に接続するために IP アドレスごとに使用する必要がある Exchange クライアントの最大数は、ネットワーク ポート 1 つあたり約 2,000 と推奨していました。</span><span class="sxs-lookup"><span data-stu-id="5289c-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="5289c-106">NAT を使用する理由は何ですか。</span><span class="sxs-lookup"><span data-stu-id="5289c-106">Why use NAT?</span></span>

<span data-ttu-id="5289c-107">NAT の使用により、企業ネットワークの何千人ものユーザーが、少数のパブリック ルーティング可能な IP アドレスを「共有」することができます。</span><span class="sxs-lookup"><span data-stu-id="5289c-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="5289c-p101">ほとんどの企業ネットワークは、プライベート (RFC1918) の IP アドレス空間を使用しています。プライベートアドレス空間は Internet Assigned Numbers Authority (IANA) によって割り当てられたもので、グローバル インターネットに直接つながっていないネットワークのみを想定しています。</span><span class="sxs-lookup"><span data-stu-id="5289c-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="5289c-p102">プライベート IP アドレス空間上のデバイスにインターネット アクセスを提供するには、ネットワーク アドレス変換 (NAT) またはポート アドレス変換 (PAT) サービスを提供するファイアウォールおよびプロキシのようなゲートウェイ技術を使用します。これらのゲートウェイは、内部デバイスからインターネットへのトラフィック (Office 365 など) を、1 つまたは複数のパブリック ルーティング可能な IP アドレスから来ているように見せます。内部デバイス変換から各アウトバウンド接続はパブリック IP アドレスの異なる送信元 TCP ポートに変換されます。</span><span class="sxs-lookup"><span data-stu-id="5289c-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="5289c-113">Office 365 に対して多数の接続を同時に開く必要があるのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="5289c-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="5289c-p103">Outlook は、(アドイン、共有の予定表、メールボックスなどが存在する状況で) 8 つ以上の接続を開くことができます。Windows ベースの NAT デバイス上では最大 64,000 ポートが利用可能なので、ポートを使い切るまでに 1 つの IP アドレスに最大 8,000 のユーザーを持つことができます。顧客が NAT に Windows OS ベース以外のデバイスを使用している場合、利用可能な合計ポート数は使用している NAT デバイスまたはソフトウェアに依存することに注意してください。このシナリオでは、ポートの最大数は 64,000 未満にすることができます。ポートの可用性は、Windows 自身が使用する 4,000 ポートを制限するなどの他の要因によっても影響を受け、これによって利用可能なポートの総数は 60,000 に減ります。Internet Explorer などのアプリケーションは同時接続が可能であり、さらにポートを必要とします。</span><span class="sxs-lookup"><span data-stu-id="5289c-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="5289c-119">Office 365 で単一のパブリック IP アドレスにサポートされるデバイスの最大数の計算</span><span class="sxs-lookup"><span data-stu-id="5289c-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="5289c-p104">単一のパブリック IP アドレスにあるデバイスの最大数を決定するには、ネットワーク トラフィックを監視し、クライアントごとのピーク ポート消費量を決定する必要があります。また、ポートの使用数にピーク係数を使用する必要があります (最小は 4)。</span><span class="sxs-lookup"><span data-stu-id="5289c-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="5289c-122">**IP アドレスごとにサポートされるデバイスの数を計算するには、次の式を使用します。**</span><span class="sxs-lookup"><span data-stu-id="5289c-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="5289c-123">単一のパブリック IP アドレスにサポートされるデバイスの最大数 = (64,000 - 制限されたポート) / (ピーク ポート消費量 + ピーク係数)</span><span class="sxs-lookup"><span data-stu-id="5289c-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="5289c-124">**たとえば、次のような条件だとします。**</span><span class="sxs-lookup"><span data-stu-id="5289c-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="5289c-125">**制限されたポート:** オペレーティング システムで 4,000</span><span class="sxs-lookup"><span data-stu-id="5289c-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="5289c-126">**ピーク ポート消費量:** デバイスあたり 6</span><span class="sxs-lookup"><span data-stu-id="5289c-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="5289c-127">**ピーク係数:** 4</span><span class="sxs-lookup"><span data-stu-id="5289c-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="5289c-128">このような条件の場合、単一のパブリック IP アドレスにサポートされるデバイスの最大数 = (64,000 - 4,000) / (6 + 4) = 6,000 </span><span class="sxs-lookup"><span data-stu-id="5289c-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="5289c-p105">Office 365 ホスティング パック (Microsoft Office Outlook 2007 用の 2011 年 9 月の更新プログラム、Microsoft Outlook 2010 用の 2011 年 11 月の更新プログラム、またはそれ以降の更新プログラムに含まれています) のリリースでの、Outlook (Office Outlook 2007 Service Pack 2 と Outlook 2010 の両方) から Exchange への最小接続数は 2 つです。ピーク時のネットワークに必要な最小または最大のポート数を決定するには、異なるオペレーティング システムやユーザーの行動などを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5289c-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="5289c-131">単一のパブリック IP アドレスでより多くのデバイスをサポートする場合、サポートできるデバイスの最大数を説明した手順に従って査定します。</span><span class="sxs-lookup"><span data-stu-id="5289c-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="5289c-p106">クライアントごとのピーク ポート消費量を決定するために、ネットワーク トラフィックを監視します。このデータは次の要領で収集します。</span><span class="sxs-lookup"><span data-stu-id="5289c-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="5289c-134">複数の場所から収集する</span><span class="sxs-lookup"><span data-stu-id="5289c-134">From multiple locations</span></span>
    
- <span data-ttu-id="5289c-135">複数のデバイスから収集する</span><span class="sxs-lookup"><span data-stu-id="5289c-135">From multiple devices</span></span>
    
- <span data-ttu-id="5289c-136">複数回にわたって収集する</span><span class="sxs-lookup"><span data-stu-id="5289c-136">At multiple times</span></span>
    
<span data-ttu-id="5289c-137">上記の計算式を使い、クライアントの環境でサポート可能な IP アドレスあたりの最大ユーザー数を計算します。</span><span class="sxs-lookup"><span data-stu-id="5289c-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="5289c-p107">追加のパブリック IP アドレス間でクライアント負荷を分散するにはさまざまな方法があります。利用可能な方法は企業のゲートウェイ ソリューションの機能によって決まります。最も簡単な方法は、ユーザー アドレス空間をセグメントに分けて、静的に各ゲートウェイに IP アドレスの数を「割り当て」る方法です。多くのゲートウェイ デバイスでサポートされている別の方法としては、IP アドレスのプールの機能を使用できます。アドレス プールの利点は、非常に動的で、ユーザー ベースの増加に合わせて調整する必要があまりないということです。</span><span class="sxs-lookup"><span data-stu-id="5289c-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5289c-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="5289c-143">See also</span></span>

[<span data-ttu-id="5289c-144">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="5289c-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="5289c-145">Office 365 エンドポイントの FAQ</span><span class="sxs-lookup"><span data-stu-id="5289c-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

