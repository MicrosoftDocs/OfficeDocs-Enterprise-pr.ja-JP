---
title: Office 365 の NAT サポート
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 1/24/2017
ms.audience: Admin
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
ms.openlocfilehash: 733d591bded599cfaece988a624baa7a3c0d4b06
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541496"
---
# <a name="nat-support-with-office-365"></a><span data-ttu-id="80754-103">Office 365 の NAT サポート</span><span class="sxs-lookup"><span data-stu-id="80754-103">NAT support with Office 365</span></span>

 <span data-ttu-id="80754-104">**概要: **ネットワーク アドレス変換 (NAT) を使用して、組織内で IP アドレスごとに使用できるクライアントの正しい数を見積もる方法の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="80754-104">**Summary:** Provides details about how to approximate the correct number of clients you can use per IP address within your organization using Network Address Translation (NAT).</span></span> 
  
<span data-ttu-id="80754-105">以前は、ガイダンスは、Office 365 に接続する 1 つの IP アドレスを使用する必要があります Exchange クライアントの最大数が約 2,000 のクライアント ネットワークのポート数をしたことを推奨します。</span><span class="sxs-lookup"><span data-stu-id="80754-105">Previously, guidance suggested that the maximum number of Exchange clients you should use per IP address to connect to Office 365 was about 2,000 clients per network port.</span></span>
  
## <a name="why-use-nat"></a><span data-ttu-id="80754-106">NAT を使用する理由は何ですか。</span><span class="sxs-lookup"><span data-stu-id="80754-106">Why use NAT?</span></span>

<span data-ttu-id="80754-107">NAT を使用すると、何千もの企業ネットワーク上のユーザーことができます「共有」、いくつかのパブリック ルーティング可能な IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="80754-107">By using NAT, thousands of people on a corporate network can "share" a few publicly routable IP addresses.</span></span>
  
<span data-ttu-id="80754-p101">ほとんどの企業ネットワークは、プライベート (RFC1918) の IP アドレス空間を使用しています。プライベートアドレス空間は Internet Assigned Numbers Authority (IANA) によって割り当てられたもので、グローバル インターネットに直接つながっていないネットワークのみを想定しています。</span><span class="sxs-lookup"><span data-stu-id="80754-p101">Most corporate networks use private (RFC1918) IP address space. Private address space is allocated by the Internet Assigned Numbers Authority (IANA) and intended solely for networks that do not route directly to and from the global Internet.</span></span>
  
<span data-ttu-id="80754-p102">プライベート IP アドレス空間のデバイスへのインターネット アクセスを提供するには、組織は、ファイアウォールやネットワーク アドレス変換 (NAT) やポート アドレス変換 (PAT) サービスを提供するプロキシ ゲートウェイ テクノロジを使用します。これらのゲートウェイは、内部からのトラフィックを行う 1 つまたは複数のパブリック ルーティング可能な IP アドレスから送信されたように (Office 365 を含む)、インターネットへのデバイスが表示されます。内蔵デバイスからの送信接続ごとにパブリック IP アドレスに別のソースの TCP ポートに変換します。</span><span class="sxs-lookup"><span data-stu-id="80754-p102">To provide Internet access to devices on a private IP address space, organizations use gateway technologies like firewalls and proxies that provide network address translation (NAT) or port address translation (PAT) services. These gateways make traffic from internal devices to the Internet (including Office 365) appear to be coming from one or more publicly routable IP addresses. Each outbound connection from an internal device translates to a different source TCP port on the public IP address.</span></span> 
  
## <a name="why-do-you-need-to-have-so-many-connections-open-to-office-365-at-the-same-time"></a><span data-ttu-id="80754-113">なぜ非常に多くの接続を同時に開くには Office 365 にする必要があるのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="80754-113">Why do you need to have so many connections open to Office 365 at the same time?</span></span>

<span data-ttu-id="80754-p103">Outlook は、(アドイン、共有の予定表、メールボックスなどが存在する状況で) 8 つ以上の接続を開くことができます。Windows ベースの NAT デバイス上では最大 64,000 ポートが利用可能なので、ポートを使い切るまでに 1 つの IP アドレスに最大 8,000 のユーザーを持つことができます。顧客が NAT に Windows OS ベース以外のデバイスを使用している場合、利用可能な合計ポート数は使用している NAT デバイスまたはソフトウェアに依存することに注意してください。このシナリオでは、ポートの最大数は 64,000 未満にすることができます。ポートの可用性は、Windows 自身が使用する 4,000 ポートを制限するなどの他の要因によっても影響を受け、これによって利用可能なポートの総数は 60,000 に減ります。Internet Explorer などのアプリケーションは同時接続が可能であり、さらにポートを必要とします。</span><span class="sxs-lookup"><span data-stu-id="80754-p103">Outlook may open eight or more connections (in situations where there are add-ins, shared calendars, mailboxes, etc.). Because there are a maximum of 64,000 ports available on a Windows-based NAT device, there can be a maximum of 8,000 users behind an IP address before the ports are exhausted. Note that if customers are using non-Windows OS-based devices for NAT, the total available ports are dependent on what NAT device or software is being used. In this scenario, the maximum number of ports could be less than 64,000. Availability of ports is also affected by other factors such as Windows restricting 4,000 ports for its own use, which reduces the total number of available ports to 60,000.There may be other applications, such as Internet Explorer, that could connect at the same time, requiring additional ports.</span></span>
  
## <a name="calculating-maximum-supported-devices-behind-a-single-public-ip-address-with-office-365"></a><span data-ttu-id="80754-119">最大値を計算するには、Office 365 と単一のパブリック IP アドレスの背後にあるデバイスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="80754-119">Calculating maximum supported devices behind a single public IP address with Office 365</span></span>

<span data-ttu-id="80754-p104">単一のパブリック IP アドレスの背後にあるデバイスの最大数を確認するのには、クライアントごとの最大ポートの消費量を決定するネットワーク トラフィックを監視します。また、ポートの使用率 (最小 4) の最大使用率を使用してください。</span><span class="sxs-lookup"><span data-stu-id="80754-p104">To determine the maximum number of devices behind a single public IP address, you should monitor network traffic to determine peak port consumption per client. Also, a peak factor should be used for the port usage (minimum 4).</span></span> 
  
 <span data-ttu-id="80754-122">**IP アドレスごとにサポートされているデバイスの数を計算するのにには、次の数式を使用します。**</span><span class="sxs-lookup"><span data-stu-id="80754-122">**Use the following formula to calculate the number of supported devices per IP address:**</span></span>
  
<span data-ttu-id="80754-123">単一のパブリック IP アドレスの背後にあるデバイスがサポートされている最大 (64,000 に制限されるポート) を = (ピーク時のポートの使用量と最大使用率)/</span><span class="sxs-lookup"><span data-stu-id="80754-123">Maximum supported devices behind a single public IP address = (64,000 - restricted ports)/(Peak port consumption + peak factor)</span></span>
  
 <span data-ttu-id="80754-124">**たとえば、次に該当するいたとします。**</span><span class="sxs-lookup"><span data-stu-id="80754-124">**For example, if the following were true:**</span></span>
  
- <span data-ttu-id="80754-125">オペレーティング システムの**制限されたポート:** 4,000</span><span class="sxs-lookup"><span data-stu-id="80754-125">**Restricted ports:** 4,000 for the operating system</span></span> 
    
- <span data-ttu-id="80754-126">デバイス 1 台あたりの**ピーク時のポートの消費量:** 6</span><span class="sxs-lookup"><span data-stu-id="80754-126">**Peak port consumption:** 6 per device</span></span> 
    
- <span data-ttu-id="80754-127">**最大使用率:** 4</span><span class="sxs-lookup"><span data-stu-id="80754-127">**Peak factor:** 4</span></span> 
    
<span data-ttu-id="80754-128">最大値が 1 つのパブリック IP アドレスの背後にあるデバイスをサポートし、= (64,000 4,000)/(6 + 4) = 6,000</span><span class="sxs-lookup"><span data-stu-id="80754-128">Then, the maximum supported devices behind a single public IP address = (64,000 - 4,000)/(6 + 4) = 6,000</span></span>
  
<span data-ttu-id="80754-p105">Pack は、Microsoft Office Outlook 2007 では、2011 年の 9 月または Microsoft Outlook 2010 では、の 2011 年 11 月から更新プログラムまたはそれ以降の更新、Outlook (両方 Office Outlook 2007 では、サービスからの接続の数に含まれるホストしている Office 365 のリリースでは、2 および Outlook 2010 をパック) に交換を 2 のものにすることができます。異なるオペレーティング ・ システム、ピーク時に、ネットワークを必要とするポートの最小値と最大数を決定していうように、ユーザーの動作を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80754-p105">With the release of Office 365 hosting pack, included in the updates from September 2011 for Microsoft Office Outlook 2007, or November 2011 for Microsoft Outlook 2010, or a later update, the number of connections from Outlook (both Office Outlook 2007 with Service Pack 2 and Outlook 2010) to Exchange can be as few as 2. You'll need to factor in the different operating systems, user behaviors, and so on to determine the minimum and maximum number of ports that your network will require at peak.</span></span>
  
<span data-ttu-id="80754-131">単一のパブリック IP アドレスの背後にあるより多くのデバイスをサポートする場合は、サポートできるデバイスの最大数を評価するのには以下の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="80754-131">If you want to support more devices behind a single public IP address, follow the steps outlined to assess the maximum number of devices that can be supported:</span></span>
  
<span data-ttu-id="80754-p106">クライアントあたりのピーク時のポートの消費量を決定するのにはネットワーク トラフィックを監視します。このデータを収集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80754-p106">Monitor network traffic to determine peak port consumption per client. You should collect this data:</span></span>
  
- <span data-ttu-id="80754-134">複数の場所から収集する</span><span class="sxs-lookup"><span data-stu-id="80754-134">From multiple locations</span></span>
    
- <span data-ttu-id="80754-135">複数のデバイスから収集する</span><span class="sxs-lookup"><span data-stu-id="80754-135">From multiple devices</span></span>
    
- <span data-ttu-id="80754-136">複数回にわたって収集する</span><span class="sxs-lookup"><span data-stu-id="80754-136">At multiple times</span></span>
    
<span data-ttu-id="80754-137">自分の環境でサポートできる IP アドレスあたりの最大ユーザー数を計算する上述の計算式を使用します。</span><span class="sxs-lookup"><span data-stu-id="80754-137">Use the preceding formula to calculate the maximum users per IP address that can be supported in their environment.</span></span>
  
<span data-ttu-id="80754-p107">追加のパブリック IP アドレスでクライアントの負荷を配布するためのさまざまなメソッドがあります。利用可能な戦略は、企業のゲートウェイ ・ ソリューションの機能に依存します。最も簡単なソリューションは、ユーザーのアドレス空間をセグメント化し、静的に割り当てる方法」「IP アドレスの数各ゲートウェイにします。ゲートウェイ デバイスの多くを提供する別の方法としては、IP アドレスのプールを使用する機能です。アドレス プールの利点とは大幅に向上動的と、ユーザー ベースが大きくなるように調整を必要とする可能性は低くします。</span><span class="sxs-lookup"><span data-stu-id="80754-p107">There are various methods for distributing client load across additional public IP addresses. Strategies available depend on the capabilities of the corporate gateway solution. The simplest solution is to segment your user address space and statically "assign" a number of IP addresses to each gateway. Another alternative that many gateway devices offer is the ability to use a pool of IP addresses. The benefit of the address pool is that it is much more dynamic and less likely to require adjustment as your user base grows.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="80754-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="80754-143">See also</span></span>

[<span data-ttu-id="80754-144">Office 365 エンドポイントを管理します。</span><span class="sxs-lookup"><span data-stu-id="80754-144">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="80754-145">Office 365 エンドポイントに関する FAQ</span><span class="sxs-lookup"><span data-stu-id="80754-145">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

