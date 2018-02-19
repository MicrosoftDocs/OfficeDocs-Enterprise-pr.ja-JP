---
title: "Microsoft クラウド接続の一般的な要素"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: "概要: ネットワーク インフラストラクチャの一般的な要素とネットワークを準備する方法を理解します。"
ms.openlocfilehash: b630daad3292976245c8cb5d3f493c32ad5be8a6
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="c9dee-103">Microsoft クラウド接続の一般的な要素</span><span class="sxs-lookup"><span data-stu-id="c9dee-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="c9dee-104">**概要:** ネットワーク インフラストラクチャの一般的な要素とネットワークを準備する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="c9dee-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="c9dee-105">ネットワーキングと Microsoft クラウドの統合によって、広範なサービスへの最適なアクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c9dee-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="c9dee-106">Microsoft クラウド サービスを利用するためのネットワークの準備の手順</span><span class="sxs-lookup"><span data-stu-id="c9dee-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="c9dee-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="c9dee-107"><a name="steps"> </a></span></span>

<span data-ttu-id="c9dee-108">オンプレミス ネットワークの場合:</span><span class="sxs-lookup"><span data-stu-id="c9dee-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="c9dee-109">クライアント コンピューターを分析し、ネットワーク ハードウェア、ソフトウェア ドライバー、プロトコル設定、およびインターネット ブラウザーに関して最適化します。</span><span class="sxs-lookup"><span data-stu-id="c9dee-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="c9dee-110">トラフィックの待機時間およびインターネット エッジ デバイスに最適化されたルーティングに関して、オンプレミス ネットワークを分析します。</span><span class="sxs-lookup"><span data-stu-id="c9dee-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="c9dee-111">インターネット エッジ デバイスの容量とパフォーマンスを分析し、より高いレベルのトラフィック向けに最適化します。</span><span class="sxs-lookup"><span data-stu-id="c9dee-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="c9dee-112">インターネット接続の場合:</span><span class="sxs-lookup"><span data-stu-id="c9dee-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="c9dee-113">インターネット エッジ デバイス (外部ファイアウォール等) と、接続先の Microsoft クラウド サービスの地域の間の待機時間を分析します。</span><span class="sxs-lookup"><span data-stu-id="c9dee-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="c9dee-p101">現在のインターネット接続の容量と使用率を分析し、必要に応じて容量を追加します。または、ExpressRoute 接続を追加します。</span><span class="sxs-lookup"><span data-stu-id="c9dee-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="c9dee-116">Microsoft クラウド接続のオプション</span><span class="sxs-lookup"><span data-stu-id="c9dee-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="c9dee-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="c9dee-117"><a name="steps"> </a></span></span>

<span data-ttu-id="c9dee-118">既存のインターネット パイプまたは ExpressRoute 接続により、Office 365、Azure、Dynamics 365 を使用します。</span><span class="sxs-lookup"><span data-stu-id="c9dee-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="c9dee-119">**図 1: Microsoft クラウド接続のオプション**</span><span class="sxs-lookup"><span data-stu-id="c9dee-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![図 1:Microsoft クラウド接続のオプション](images/Network_Poster/CommonElements.png)

  
<span data-ttu-id="c9dee-p102">図 1 は、既存のインターネット パイプまたは ExpressRoute を使用して、どのようにオンプレミスのネットワークを Microsoft クラウド製品に接続するかを示します。インターネット パイプは DMZ を表し、次のコンポーネントを有する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c9dee-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="c9dee-p103">**内部ファイアウォール:** 信頼されているネットワークと信頼されていないネットワーク間の障壁です。(ルールに基づいて) トラフィックのフィルター処理および監視を行います。</span><span class="sxs-lookup"><span data-stu-id="c9dee-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="c9dee-125">**外部ワークロード:** インターネット上で、外部のユーザーに対して利用可能になっている Web サイトまたはその他のワークロード。</span><span class="sxs-lookup"><span data-stu-id="c9dee-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="c9dee-p104">**プロキシ サーバー:** イントラネット ユーザーのための Web コンテンツの要求にサービスします。リバース プロキシは、未承諾の受信要求を許可します。</span><span class="sxs-lookup"><span data-stu-id="c9dee-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy allows unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="c9dee-p105">**外部ファイアウォール:** 送信トラフィックおよび指定した着信トラフィックを許可します。アドレス変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="c9dee-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation.</span></span>
    
- <span data-ttu-id="c9dee-130">**ISP への WAN 接続:** 接続およびルーティングに関してインターネットと同等であるキャリア ベースの ISP への接続。</span><span class="sxs-lookup"><span data-stu-id="c9dee-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="c9dee-131">すべての Microsoft クラウド サービスに共通のネットワークの領域</span><span class="sxs-lookup"><span data-stu-id="c9dee-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="c9dee-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="c9dee-132"><a name="steps"> </a></span></span>

<span data-ttu-id="c9dee-133">Microsoft クラウド サービスのいずれかを採用するときは、ネットワークに関する次の領域を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9dee-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="c9dee-134">**イントラネット パフォーマンス:** クライアント コンピューターを含むイントラネットが最適化されていない場合、インターネット ベースのリソースはパフォーマンスの低いものになります。</span><span class="sxs-lookup"><span data-stu-id="c9dee-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="c9dee-135">**エッジ デバイス:** ネットワークのエッジにあるデバイスは出口点であり、それにはネットワーク アドレス変換 (NAT)、プロキシ サーバー (リバース プロキシを含む)、ファイアウォール、侵入検出デバイス、またはこれらの組み合わせが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c9dee-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="c9dee-p106">**インターネット接続:** ISP とインターネットへの WAN 接続には、ピーク時の負荷を処理するのに十分な容量が必要です。ExpressRoute 接続を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9dee-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="c9dee-p107">**インターネット DNS:** Microsoft クラウドまたはクラウドでホストされているサービスを検索するための、A、AAAA、CNAME、MX、PTR、その他のレコード。たとえば、Azure PaaS でホストされているアプリのために、CNAME レコードが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="c9dee-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    

## <a name="next-step"></a><span data-ttu-id="c9dee-140">次の手順</span><span class="sxs-lookup"><span data-stu-id="c9dee-140">Next step</span></span>

[<span data-ttu-id="c9dee-141">Microsoft クラウド接続のための ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="c9dee-141">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="c9dee-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9dee-142">See also</span></span>

<span data-ttu-id="c9dee-143"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="c9dee-143"></span></span>

[<span data-ttu-id="c9dee-144">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="c9dee-144">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="c9dee-145">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="c9dee-145">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


