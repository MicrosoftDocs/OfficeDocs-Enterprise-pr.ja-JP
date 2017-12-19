---
title: "Microsoft クラウド接続のためのExpressRoute"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: "概要: ExpressRoute による Microsoft のクラウド サービスとプラットフォームへのより早く信頼できる接続が、どのように役立つか説明します。"
ms.openlocfilehash: 69120d3237518be5d77716a106d2e75b64a4860e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="9a3f8-103">Microsoft クラウド接続のためのExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a3f8-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="9a3f8-104">**概要:** ExpressRoute による Microsoft のクラウド サービスとプラットフォームへのより早く信頼できる接続が、どのように役立つか説明します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="9a3f8-105">ExpressRoute は、Microsoft のクラウドへのプライベート、専用、高スループットのネットワーク接続を提供します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="9a3f8-106">Microsoft クラウドへの ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a3f8-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="9a3f8-107">次の図は、ExpressRoute 接続を使用していない場合の Microsoft クラウドへのネットワーク パスを示しています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="9a3f8-108">**図 1:ExpressRoute のないネットワーク パス**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![図 1:ExpressRoute のないネットワーク パス](images/Network_Poster/ExpressRoute.png)
  
<span data-ttu-id="9a3f8-p101">図 1 は、オンプレミスのネットワークと Microsoft クラウドとの間の一般的なパスを示しています。オンプレミスのネットワーク エッジは、ISP への WAN リンクを経由してインターネットに接続しています。トラフィックは、インターネットを通過して Microsoft クラウドのエッジに到達します。Microsoft クラウド内のクラウド サービスには、Office 365、Microsoft Azure、Microsoft Intune、Dynamics 365 があります。組織のユーザーは、オンプレミスのネットワークに配置することも、インターネットに配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="9a3f8-115">ExpressRoute 接続がない場合、Microsoft クラウドへのトラフィック パスのうち制御可能な部分 (またサービス プロバイダーとの関係がある部分) は、オンプレミスのネットワーク エッジと ISP との間のリンクのみになります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="9a3f8-116">ISP と Microsoft クラウド エッジとの間のパスは、インターネット上のベストエフォート配信システムになります。インターネットには、停止、トラフィックの輻輳、および悪意のあるユーザーによる監視の恐れがあります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="9a3f8-117">インターネット上のユーザー (ローミング ユーザーやリモート ユーザー) は、Microsoft クラウドへのトラフィックをインターネット経由で送信します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="9a3f8-118">次の図は、ExpressRoute 接続を使用している場合の Microsoft クラウドへのネットワーク パスを示しています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="9a3f8-119">**図 2: ExpressRoute のあるネットワーク パス**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![図 2: ExpressRoute のあるネットワーク パス](images/Network_Poster/ExpressRoute_post.png)
  
<span data-ttu-id="9a3f8-p102">図 2 は、2 つのネットワーク パスを示しています。Microsoft Intune へのトラフィックは、通常のインターネットのトラフィックと同じパスを通過します。Office 365、Microsoft Azure、Dynamics 365 へのトラフィックは、ExpressRoute 接続を通過します。この接続は、オンプレミス ネットワークのエッジと Microsoft クラウドのエッジとの間の専用パスです。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="9a3f8-p103">ExpressRoute 接続を使用すると、サービス プロバイダーとの関係を通じて、自社のエッジから Microsoft クラウドのヘッジまでのトラフィック パス全体を管理できるようになります。この接続では、予測可能なパフォーマンスと稼働時間 99.9% の SLA が得られます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a 99.9% uptime SLA.</span></span>
  
<span data-ttu-id="9a3f8-p104">これにより、Office 365、Azure、Dynamics 365 サービスへの予測可能なスループットと待機時間は、サービス プロバイダーの接続に基づいて、信頼できるものになります。現時点では、Microsoft Intune への ExpressRoute 接続はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="9a3f8-128">ExpressRoute 接続を通じて送信されるトラフィックは、インターネットの停止、トラフィックの輻輳、および監視についての恐れがなくなります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="9a3f8-p105">インターネット上のユーザー (ローミング ユーザーやリモート ユーザーなど) は、この場合も、インターネットを通じて Microsoft クラウドへのトラフィックを送信します。1 つの例外として、Azure IaaS でホストされているイントラネットの基幹業務アプリケーションへのトラフィックが挙げられます。このトラフィックは、オンプレミスのネットワークへのリモート アクセス接続を経由して ExpressRoute で送信されます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="9a3f8-131">ExpressRoute 接続を使用していても、一部のトラフィック (DNS クエリ、証明書失効リストによる確認、コンテンツ配信ネットワーク (CDN) の要求など) はインターネットを通じて送信されます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="9a3f8-132">詳細については、次に示す追加の技術資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="9a3f8-133">Office 365 用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a3f8-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="9a3f8-134">Azure 用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a3f8-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="9a3f8-135">Azure 用 ExpressRoute の利点</span><span class="sxs-lookup"><span data-stu-id="9a3f8-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="9a3f8-136">ここでは、Azure ベースのクラウドサービスに ExpressRoute を使用するいくつかの利点を示します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="9a3f8-p106">**予測可能なパフォーマンス:** Microsoft クラウドのエッジへの専用パスを使用することで、インターネット プロバイダーの停止とインターネット トラフィックの輻輳によるパフォーマンス低下の恐れがなくなります。Microsoft クラウドへのスループットおよび待機時間の SLA に対する責任があるプロバイダーを決定して保持できます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="9a3f8-p107">**トラフィックのデータのプライバシー:** 専用の ExpressRoute 接続を通じて送信されるトラフィックには、悪意のあるユーザーによるインターネットの監視またはパケット キャプチャおよび分析の恐れがありません。これは、Multiprotocol Label Switching (MPLS) ベースの WAN リンクを使用することと同じように安全です。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="9a3f8-141">**高スループットの接続:** 相互接続プロバイダーとネットワーク サービス プロバイダーによる ExpressRoute 接続の広範なサポートがあるため、Microsoft クラウドへの最大 10 Gbps のリンクが使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="9a3f8-142">**構成によってはコストの低下につながる:** ExpressRoute 接続には追加のコストがかかりますが、Microsoft クラウド サービスへの十分なスループットが得られるように組織の複数の場所でインターネットのキャパシティを増やすよりも、1 つの ExpressRoute 接続にするほうがコストが低くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="9a3f8-p108">ExpressRoute 接続は、すべての構成でパフォーマンスが向上するということを保証するものではありません。地域の Microsoft データセンターから数ホップしか離れていない高帯域幅のインターネット接続よりも、低帯域幅の ExpressRoute 接続のほうがパフォーマンスが低くなる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="9a3f8-145">ExpressRoute with Office 365 の使用に関する最新の推奨事項については、「[Office 365 向け Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="9a3f8-146">ExpressRoute の接続モデル</span><span class="sxs-lookup"><span data-stu-id="9a3f8-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="9a3f8-147">表 1 に、ExpressRoute 接続の 3 つの主要な接続モデルを示します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="9a3f8-148">**Cloud Exchange でのコロケーション**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="9a3f8-149">**ポイント ツー ポイントのイーサネット**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="9a3f8-150">**Any-to-Any (IP VPN) 接続**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![ExpressRoute 接続モデル:Cloud Exchange でのコロケーション](images/Network_Poster/ER_Conn1.png)|![ExpressRoute 接続モデル:ポイント ツー ポイントのイーサネット](images/Network_Poster/ER_Conn2.png)|![ExpressRoute 接続モデル:Any-to-Any (IP VPN) 接続](images/Network_Poster/ER_Conn3.png)|
|<span data-ttu-id="9a3f8-154">Could Exchange を備えた施設にデータセンターが併置されている場合は、併置プロバイダーのイーサネット交換機を通じた Microsoft クラウドへの仮想交差接続をオーダーできます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="9a3f8-155">データセンターがオンプレミスに配置されている場合は、Microsoft クラウドへの接続に、ポイント ツー ポイントのイーサネット リンクを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="9a3f8-156">既に、組織のサイトへの接続に IP VPN (MPLS) プロバイダーを使用している場合、Microsoft クラウドへの ExpressRoute 接続はプライベート WAN 上の別の場所と同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="9a3f8-157">**表 1:ExpressRoute の接続モデル**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="9a3f8-158">Microsoft クラウド サービスへの ExpressRoute ピアリング関係</span><span class="sxs-lookup"><span data-stu-id="9a3f8-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="9a3f8-p109">1 つの ExpressRoute 接続では、Microsoft クラウドの異なる部分とのボーダー ゲートウェイ プロトコル (BGP) ピアリング関係を最大 3 つまでサポートします。BPG では、信頼を確立してルーティング情報を交換するために、ピアリング関係を使用します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p109">A single ExpressRoute connection supports up to three different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="9a3f8-161">**図 3: 単一の ExpressRoute 接続が対応する 3 つの異なる BGP 関係**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-161">**Figure 3: The three different BGP relationships in a single ExpressRoute connection**</span></span>

![図 3: 単一の ExpressRoute 接続が対応する 3 つの異なる BGP 関係](images/Network_Poster/ERPeering.png)
  
<span data-ttu-id="9a3f8-p110">図 3 は、オンプレミス ネットワークからの ExpressRoute 接続を示しています。ExpressRoute 接続には 3 つの論理ピアリング関係が含まれています。Microsoft ピアリング関係は、Office 365 と Dynamcs CRM Online を含む Microsoft SaaS サービスに向けられています。パブリック ピアリング関係は、Azure PaaS サービスに向けられています。プライベート ピアリング関係には、Azure IaaSに向けられたものと、仮想マシンをホストする仮想ネットワーク ゲートウェイに向けられたものがあります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection contains three logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365 and Dynamcs CRM Online. A public peering relationship goes to Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="9a3f8-168">Microsoft ピアリング BGP 関係:</span><span class="sxs-lookup"><span data-stu-id="9a3f8-168">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="9a3f8-169">DMZ のルーターから Office 365 および Dynamics 365 サービスのパブリック アドレスに向けられています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-169">Is from a router in your DMZ to the public addresses of Office 365 and Dynamics 365 services.</span></span> 
    
- <span data-ttu-id="9a3f8-170">双方向で開始される通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-170">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="9a3f8-171">パブリック ピアリング BGP 関係:</span><span class="sxs-lookup"><span data-stu-id="9a3f8-171">The public peering BGP relationship:</span></span>
  
- <span data-ttu-id="9a3f8-172">DMZ のルーターから Azure サービスのパブリック IP アドレスに向けられています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-172">Is from a router in your DMZ to the public IP addresses of Azure services.</span></span>
    
- <span data-ttu-id="9a3f8-p111">双方向で開始されないオンプレミスのシステムからのみの通信をサポートします。このピアリング関係は、Azure PaaS サービスから開始される通信をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p111">Supports unidirectional-initiated communication from on-premises systems only. The peering relationship does not support communication initiated from Azure PaaS services.</span></span>
    
<span data-ttu-id="9a3f8-175">プライベート ピアリング BGP 関係:</span><span class="sxs-lookup"><span data-stu-id="9a3f8-175">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="9a3f8-176">組織のネットワークのエッジにあるルーターから Azure VNet に割り当てられたプライベート IP アドレスに向けられています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-176">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="9a3f8-177">双方向で開始される通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-177">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="9a3f8-178">組織のネットワークのMicrosoft クラウドへの拡張であり、内部的に一貫したアドレス指定とルーティングを備えています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-178">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="9a3f8-179">ExpressRoute によるアプリケーション展開とトラフィック フローの例</span><span class="sxs-lookup"><span data-stu-id="9a3f8-179">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="9a3f8-p112">どのようにしてトラフィックが ExpressRoute 接続を通過して Microsoft クラウド内で移動するかは、送信元と送信先の間のパスにある各ホップでのルートとアプリケーションの動作という変数によって変化します。次に、Azure 仮想マシンで実行中のアプリケーションの例を示します。このアプリケーションは、サイト間 VPN 接続を通じてオンプレミスの SharePoint ファームにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p112">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="9a3f8-182">**図 4:オンプレミス SharePoint ファームにアクセスする Azure 仮想マシン上のアプリケーション**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-182">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![図 4:オンプレミス SharePoint ファームにアクセスする Azure 仮想マシン上のアプリケーション](images/Network_Poster/ER_App_Flow1.png)

  
<span data-ttu-id="9a3f8-184">図 4 は、オンプレミスの SharePoint ファーム、オンプレミス ネットワークと Azure IaaS の仮想ネットワークとの間のサイト間 VPN 接続、Azure IaaS 仮想マシンとして実行しているアプリケーション サーバー、およびアプリケーション サーバーと SharePoint ファームとの間のトラフィック フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-184">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="9a3f8-185">アプリケーションは、オンプレミスの DNS を使用して SharePoint ファームの IP アドレスを見つけます。また、すべてのトラフィックはサイト間 VPN 接続を通じて移動します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-185">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="9a3f8-186">この組織は、オンプレミスの SharePoint ファームを Office 365 の SharePoint Online に移行して、ExpressRoute 接続を展開しました。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-186">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="9a3f8-187">**図 5: オンプレミスの SharePoint ファームを SharePoint Online に移行する**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-187">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![図 5: オンプレミスの SharePoint ファームを SharePoint Online に移行する](images/Network_Poster/Hairpin1.png)
  
<span data-ttu-id="9a3f8-p113">図 5 は、Microsoft SaaS と Office 365 へのピアリング関係と、仮想ネットワーク上にアプリケーション サーバーを含む Azure IaaS へのピアリング関係を持つ ExpressRoute 接続の追加を示しています。オンプレミスの SharePoint ファームは、Office 365 に移行されています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p113">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="9a3f8-191">Microsoft ピアリング関係とプライベート ピアリング関係がある場合:</span><span class="sxs-lookup"><span data-stu-id="9a3f8-191">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="9a3f8-192">Azure 仮想ネットワーク ゲートウェイから、ExpressRoute 接続を通じてオンプレミスの場所が使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-192">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="9a3f8-193">Office 365 サブスクリプションから、ExpressRoute 接続を通じてエッジ デバイス (プロキシ サーバーなど) のパブリック IP が使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-193">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="9a3f8-194">オンプレミスのネットワーク エッジから、ExpressRoute 接続を通じて Azure VNet のプライベート IP アドレスと Office 365 のパブリック IP アドレスが使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-194">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="9a3f8-195">アプリケーションが SharePoint Online の URL にアクセスすると、そのトラフィックは ExpressRoute 接続を通じてエッジにあるプロキシ サーバーに転送されます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-195">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="9a3f8-p114">プロキシ サーバーが SharePoint Online の IP アドレスを見つけると、ExpressRoute 接続を通じてトラフィックが戻ります。応答トラフィックは逆方向のパスを通過します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p114">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="9a3f8-198">**図 6:SharePoint ファームが Office 365 の SharePoint Online に移行したときのトラフィック フロー**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-198">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![図 6:SharePoint ファームが Office 365 の SharePoint Online に移行したときのトラフィック フロー](images/Network_Poster/Hairpin2.png)

  
<span data-ttu-id="9a3f8-200">図 6 は、アプリケーション サーバーと Office 365 の SharePoint Online との間で、トラフィックがプライベート ピアリング関係を通じてアプリケーション サーバーからオンプレミスのネットワーク エッジに流れ、Microsoft ピアリング関係を通じてエッジから Office 365 に流れる様子を示しています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-200">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="9a3f8-201">結果はヘアピン型になります (ルーティングとアプリケーション動作の結果)。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-201">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="9a3f8-202">ExpressRoute と Microsoft のクラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="9a3f8-202">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="9a3f8-203">ExpressRoute 接続は、ExpressRoute と ExpressRoute Premium という 2 つのバージョンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-203">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="9a3f8-204">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a3f8-204">ExpressRoute</span></span>

<span data-ttu-id="9a3f8-205">組織のネットワークと Microsoft データセンターとの間でトラフィックが移動する方法は、次の場所の組み合わせになります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-205">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="9a3f8-206">ユーザーの場所。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-206">Your locations.</span></span>
    
- <span data-ttu-id="9a3f8-207">Microsoft クラウド ピアリングの場所 (Microsoft のエッジに接続する物理的な場所)。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-207">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="9a3f8-208">Microsoft データセンターの場所。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-208">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="9a3f8-209">Microsoft データセンターとクラウド ピアリングの場所は、すべて Microsoft クラウド ネットワークに接続されています。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-209">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="9a3f8-p115">Microsoft クラウド ピアリングの場所への ExpressRoute 接続を作成すると、Microsoft クラウド ネットワークおよび同じ大陸内にあるすべての Microsoft データセンターの場所に接続されます。クラウド ピアリングの場所と宛先の Microsoft データセンターとの間のトラフィックは、Microsoft クラウド ネットワーク経由で転送されます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p115">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="9a3f8-212">このため、Any-to-Any 接続モデルの場合は、ローカルの Microsoft データセンターへの配信が最適でなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-212">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="9a3f8-213">**図 7: 単一の ExpressRoute 接続を使用する地理的に分散した組織の例**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-213">**Figure 7: Example of an geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![図 7: 単一の ExpressRoute 接続を使用する地理的に分散した組織の例](images/Network_Poster/MSNet1.png)
  
<span data-ttu-id="9a3f8-p116">図 7 は、2 つの場所 (米国の北西にある Location 1 と北東にある Location 2) を持つ組織を示しています。これらは、Any-to-Any の WAN プロバイダーで接続されています。この組織には、西海岸にある Microsoft ピアリングの場所への ExpressRoute 接続もあります。北東にある Location 2 から東海岸のデータセンターに向かうトラフィックは、組織の WAN で西海岸に移動し、Microsoft ピアリングの場所に移動してから、Microsoft クラウド ネットワーク経由で国を横断して東海岸のデータセンターに戻ります。この経路をすべて通過する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p116">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="9a3f8-219">配信を最適化するには、地域の Microsoft クラウド ピアリングの場所への複数の ExpressRoute 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-219">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="9a3f8-220">**図 8: 地域のデータ センターへの最適な配信を確保するために複数の ExpressRoute 接続を使用する**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-220">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![図 8: 地域のデータ センターへの最適な配信を確保するために複数の ExpressRoute 接続を使用する](images/Network_Poster/MSNet2.png)
  
<span data-ttu-id="9a3f8-p117">図 8 は、ExpressRoute 接続が 2 つある同じ組織を示しています。それぞれが地域的にローカルの Microsoft ピアリングの場所に接続しています。この構成では、北東にある Location 2 から東海岸のデータセンターに向かうトラフィックは、東海岸のピアリングの場所に直接移動し、Microsoft クラウド ネットワークに移動してから、東海岸のデータセンターに到達します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p117">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="9a3f8-224">複数の ExpressRoute 接続には、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-224">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="9a3f8-225">地域的にローカルな Microsoft データセンターの場所に対するパフォーマンスの向上。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-225">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="9a3f8-226">ローカルの ExpressRoute 接続が使用不能になったときの Microsoft クラウドに対する可用性の向上。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-226">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="9a3f8-p118">これは、複数の組織が同じ大陸内にある場合に最適に機能します。ただし、組織のある大陸の外側の Microsoft データセンターへのトラフィックはインターネット経由で移動します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p118">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="9a3f8-229">Microsoft クラウド ネットワークを経由する大陸間トラフィックには、ExpressRoute Premium を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-229">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="9a3f8-230">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="9a3f8-230">ExpressRoute Premium</span></span>

<span data-ttu-id="9a3f8-231">大陸間にグローバルに分散している組織の場合は、ExpressRoute Premium を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-231">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="9a3f8-p119">ExpressRoute Premium では、どの大陸にある Microsoft ピアリングの場所からでも、あらゆる大陸にある任意の Microsoft データセンターに到達できます。大陸間のトラフィックは、Microsoft クラウド ネットワークを通じて転送されます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p119">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="9a3f8-234">複数の ExpressRoute Premium 接続を使用すると、次の利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-234">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="9a3f8-235">大陸的にローカルな Microsoft データセンターに対するパフォーマンスの向上。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-235">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="9a3f8-236">ローカルの ExpressRoute 接続が使用不能になったときのグローバルな Microsoft クラウドに対する可用性の向上。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-236">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="9a3f8-p120">Office 365 ベースの ExpressRoute 接続には、ExpressRoute Premium が必要になります。ただし、ライセンス付与済みのユーザー数が 500 以上の企業には追加のコストは発生しません。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p120">ExpressRoute Premium is required for Office 365-based ExpressRoute connections. However, there is no additional cost for enterprises with 500 or more licensed users.</span></span>
  
<span data-ttu-id="9a3f8-239">**図 9: 全世界をカバーする Microsoft のクラウド ネットワーク**</span><span class="sxs-lookup"><span data-stu-id="9a3f8-239">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![図 9: 全世界をカバーする Microsoft のクラウド ネットワーク](images/Network_Poster/MSNet3.png)
  
<span data-ttu-id="9a3f8-p121">図 9 は、世界規模の Microsoft クラウド ネットワークの論理図を示しています。この図には、大陸間および地域間に広がるネットワークと、そのネットワークの相互接続が示されています。各大陸にある部分的な Microsoft クラウド ネットワークでは、グローバル企業が、地域拠点の支社からローカルの Microsoft ピアリングの場所までの ExpressRoute Premium 接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p121">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="9a3f8-243">地域のオフィスで、次に示す宛先に該当する Office 365 トラフィックの移動:</span><span class="sxs-lookup"><span data-stu-id="9a3f8-243">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="9a3f8-244">大陸の Office 365 データセンターへのトラフィックは、その大陸内の Microsoft クラウド ネットワークを通じて移動します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-244">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="9a3f8-245">別の大陸にある Office 365 データセンターへのトラフィックは、大陸間の Microsoft クラウド ネットワークを通じて移動します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-245">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="9a3f8-246">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-246">For more information, see:</span></span>
  
- [<span data-ttu-id="9a3f8-247">Azure ExpressRoute for Office 365 のトレーニング</span><span class="sxs-lookup"><span data-stu-id="9a3f8-247">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="9a3f8-248">Office 365 のネットワーク計画とパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="9a3f8-248">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="9a3f8-249">Office 365 のパフォーマンス管理</span><span class="sxs-lookup"><span data-stu-id="9a3f8-249">Office 365 Performance Management</span></span>](https://mva.microsoft.com/ja-JP/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="9a3f8-250">ExpressRoute のオプション</span><span class="sxs-lookup"><span data-stu-id="9a3f8-250">ExpressRoute options</span></span>

<span data-ttu-id="9a3f8-251">ExpressRoute の展開には、次に示すオプションを組み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-251">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="9a3f8-252">**エッジでのセキュリティ:** ExpressRoute 接続を通じて送受信されるトラフィックに高度なセキュリティ (トラフィック検査や侵入/マルウェア検出など) を提供するには、DMZ 内のトラフィック パスまたはインターネット境界にセキュリティ アプライアンスを配置します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-252">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
    <span data-ttu-id="9a3f8-p122">VM のインターネット トラフィック: インターネットの場所で Azure VM が直接開始されないようにするために、Microsoft への既定のルートを公開します。インターネットへのトラフィックは、ExpressRoute 接続を経由して、オンプレミスのプロキシ サーバーを通過するようにルーティングされます。Azure VM から Azure PaaS サービスや Office 365 へのトラフィックは、ExpressRoute 接続を経由して戻るようにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p122">Internet traffic for VMs To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="9a3f8-p123">**WAN オプティマイザー:** クロスプレミス Azure 仮想ネットワーク (VNet) のプライベート ピアリング接続の両側に WAN オプティマイザーを展開できます。Azure VNet の内部では、Azure マーケットプレースから得られる WAN オプティマイザー ネットワーク アプライアンスと、トラフィックがアプライアンスを通過するようにルーティングするユーザー定義のルーティングを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p123">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="9a3f8-p124">**サービスの品質:** トラフィックの IPv4 ヘッダーで DSCP (Differentiated Services Code Point) の値を使用して、そのトラフィックに音声、ビデオ/インタラクティブまたはベストエフォート配信のマークを付けます。これは、Microsoft ピアリング関係と Skype for Business Online のトラフィックには特に重要です。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-p124">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="9a3f8-260">詳細については、次に示す追加の技術資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a3f8-260">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="9a3f8-261">Office 365 用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a3f8-261">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="9a3f8-262">Azure ExpressRoute for Office 365 のトレーニング</span><span class="sxs-lookup"><span data-stu-id="9a3f8-262">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="9a3f8-263">Azure 用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a3f8-263">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="see-also"></a><span data-ttu-id="9a3f8-264">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a3f8-264">See Also</span></span>

[<span data-ttu-id="9a3f8-265">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="9a3f8-265">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="9a3f8-266">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="9a3f8-266">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="9a3f8-267">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="9a3f8-267">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



