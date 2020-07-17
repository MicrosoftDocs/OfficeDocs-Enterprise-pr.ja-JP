---
title: Office 365 サービスに接続するネットワーク デバイスの計画
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: '概要: Office 365 への接続に使用されるネットワーク容量、WAN アクセラレータ、および負荷分散デバイスに関する考慮事項について説明します。'
ms.openlocfilehash: 5015a146f92a32bd0200088517b6673ae00f8f64
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998636"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="201ed-103">Office 365 サービスに接続するネットワーク デバイスの計画</span><span class="sxs-lookup"><span data-stu-id="201ed-103">Plan for network devices that connect to Office 365 services</span></span>

<span data-ttu-id="201ed-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="201ed-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>
  
<span data-ttu-id="201ed-105">ネットワークハードウェアによっては、サポートされている同時セッション数に制限がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="201ed-105">Some network hardware may have limitations on the number of concurrent sessions that are supported.</span></span> <span data-ttu-id="201ed-106">ユーザー数が2000を超える組織では、ネットワークデバイスを監視して、追加の Office 365 サービストラフィックを処理できることを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="201ed-106">For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic.</span></span> <span data-ttu-id="201ed-107">簡易ネットワーク管理プロトコル (SNMP) 監視ソフトウェアを使用すると、この操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="201ed-107">Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="201ed-108">この記事は[、Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="201ed-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="201ed-109">オンプレミスの送信インターネットプロキシ設定も、クライアントアプリケーションの Office 365 サービスへの接続に影響します。</span><span class="sxs-lookup"><span data-stu-id="201ed-109">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications.</span></span> <span data-ttu-id="201ed-110">また、Microsoft クラウドサービスの Url とアプリケーションへの接続を許可するように、ネットワークプロキシデバイスを構成する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="201ed-110">You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications.</span></span> <span data-ttu-id="201ed-111">すべての組織が異なります。</span><span class="sxs-lookup"><span data-stu-id="201ed-111">Every organization is different.</span></span> <span data-ttu-id="201ed-112">Microsoft がこのプロセスと、プロビジョニングする帯域幅の量をどのように管理しているかを把握するには、[ケーススタディをお読み](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365)ください。</span><span class="sxs-lookup"><span data-stu-id="201ed-112">To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="201ed-113">次の Skype for Business ヘルプの記事には、Skype for Business の設定に関する詳細が記載されています。</span><span class="sxs-lookup"><span data-stu-id="201ed-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="201ed-114">管理者向けの Skype for Business Online サインインエラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="201ed-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="201ed-115">オンプレミスのファイアウォールによって接続がブロックされているため、Skype for Business に接続できないか、一部の機能が動作しません。</span><span class="sxs-lookup"><span data-stu-id="201ed-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="201ed-116">これらの設定の多くは Skype for Business に固有のものですが、ネットワーク構成に関する一般的なガイダンスはすべての Office 365 サービスで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="201ed-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="201ed-117">ネットワークの容量を決定する</span><span class="sxs-lookup"><span data-stu-id="201ed-117">Determining Network Capacity</span></span>

<span data-ttu-id="201ed-118">接続上に存在するすべてのネットワークデバイスに容量の制限があります。</span><span class="sxs-lookup"><span data-stu-id="201ed-118">Every network device that exists on a connection has its capacity limit.</span></span> <span data-ttu-id="201ed-119">これらのデバイスには、それらを相互に接続するクライアントおよびサーバーのネットワークアダプター、ルーター、スイッチ、ハブが含まれます。</span><span class="sxs-lookup"><span data-stu-id="201ed-119">These devices include the client and server network adapters, routers, switches, and hubs that interconnect them.</span></span> <span data-ttu-id="201ed-120">十分なネットワークの容量は、飽和していないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="201ed-120">Adequate network capacity means that none of them are saturated.</span></span> <span data-ttu-id="201ed-121">ネットワークアクティビティを監視することは、すべてのネットワークデバイスの実際の負荷が最大容量を下回っていることを確認するために不可欠です。</span><span class="sxs-lookup"><span data-stu-id="201ed-121">Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity.</span></span> <span data-ttu-id="201ed-122">ネットワーク容量は、プロキシデバイスのパフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="201ed-122">Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="201ed-123">ほとんどの場合、インターネット接続の帯域幅はトラフィック量の制限を設定します。</span><span class="sxs-lookup"><span data-stu-id="201ed-123">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic.</span></span> <span data-ttu-id="201ed-124">ピークトラフィック時間中のパフォーマンスが低い場合は、インターネットリンクの過剰な使用が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="201ed-124">Weak performance during peak traffic hours is probably caused by excessive use of the Internet link.</span></span> <span data-ttu-id="201ed-125">この状況は、ブランチオフィスのプロキシサーバーコンピューターが低速のワイドエリアネットワーク (WAN) リンクを介して支社の本社のプロキシデバイスに接続されている場合にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="201ed-125">This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="201ed-126">ネットワーク容量をテストするには、プロキシネットワークインターフェイスでネットワークアクティビティを監視します。</span><span class="sxs-lookup"><span data-stu-id="201ed-126">To test network capacity, monitor the network activity on the proxy network interface.</span></span> <span data-ttu-id="201ed-127">ネットワークインターフェイスの最大帯域幅が75% を超えている場合は、ネットワークインフラストラクチャの帯域幅が不十分であることを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="201ed-127">If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate.</span></span> <span data-ttu-id="201ed-128">または、HTTP 圧縮などの高度な機能を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="201ed-128">Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="201ed-129">WAN アクセラレータ</span><span class="sxs-lookup"><span data-stu-id="201ed-129">WAN Accelerators</span></span>

<span data-ttu-id="201ed-130">ワイドエリアネットワーク (WAN) アクセラレータプロキシアプライアンスを使用している場合は、Office 365 サービスにアクセスすると問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="201ed-130">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services.</span></span> <span data-ttu-id="201ed-131">ユーザーが Office 365 にアクセスするときに一貫した環境を確保するために、ネットワークデバイスを最適化する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="201ed-131">You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365.</span></span> <span data-ttu-id="201ed-132">たとえば、Office 365 サービスは一部の Office 365 コンテンツと TCP ヘッダーを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="201ed-132">For example, Office 365 services encrypt some Office 365 content and the TCP header.</span></span> <span data-ttu-id="201ed-133">デバイスがこの種のトラフィックを処理できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="201ed-133">Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="201ed-134">「 [Office 365 での WAN 最適化コントローラーまたはトラフィック/検査デバイスの使用](https://support.microsoft.com/kb/2690045)に関するサポートに関する声明」をお読みください。</span><span class="sxs-lookup"><span data-stu-id="201ed-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="201ed-135">ハードウェアおよびソフトウェア負荷分散デバイス</span><span class="sxs-lookup"><span data-stu-id="201ed-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="201ed-136">組織は、ハードウェアロードバランサー (HLB) またはネットワーク負荷分散 (NLB) ソリューションを使用して、Active Directory フェデレーションサービス (AD FS) サーバーまたは Exchange ハイブリッドサーバーに要求を分散する必要があります。</span><span class="sxs-lookup"><span data-stu-id="201ed-136">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers.</span></span> <span data-ttu-id="201ed-137">負荷分散デバイスは、社内サーバーへのネットワークトラフィックを制御します。</span><span class="sxs-lookup"><span data-stu-id="201ed-137">Load-balancing devices control the network traffic to the on-premises servers.</span></span> <span data-ttu-id="201ed-138">これらのサーバーは、シングルサインオンと Exchange ハイブリッド展開の可用性を確保するうえで非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="201ed-138">These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="201ed-139">Windows Server に組み込まれているソフトウェアベースの NLB ソリューションを提供しています。</span><span class="sxs-lookup"><span data-stu-id="201ed-139">We provide a software-based NLB solution built into Windows Server.</span></span> <span data-ttu-id="201ed-140">Office 365 は、このソリューションをサポートすることによって負荷分散を実現します。</span><span class="sxs-lookup"><span data-stu-id="201ed-140">Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="201ed-141">ファイアウォールとプロキシ</span><span class="sxs-lookup"><span data-stu-id="201ed-141">Firewalls and proxies</span></span>

<span data-ttu-id="201ed-142">Office 365 に接続するためのファイアウォールとプロキシの構成の詳細については、「 [office 365 エンドポイントの管理](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)」、「 [365 office 2013 のネットワーク接続の評価](assessing-network-connectivity.md)」、および「 [OFFICE 365 エンドポイントの FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) 」を参照して、デバイスと回線の選択についてご確認ください。</span><span class="sxs-lookup"><span data-stu-id="201ed-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Assessing Office 365 network connectivity](assessing-network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="201ed-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="201ed-143">See also</span></span>

[<span data-ttu-id="201ed-144">Office 365 サービスのセットアップガイド</span><span class="sxs-lookup"><span data-stu-id="201ed-144">Setup guides for Office 365 services</span></span>](setup-guides-for-office-365.md)

[<span data-ttu-id="201ed-145">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="201ed-145">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
