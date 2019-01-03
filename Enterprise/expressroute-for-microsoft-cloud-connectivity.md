---
title: Microsoft クラウド接続のためのExpressRoute
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/02/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: '概要: ExpressRoute による Microsoft のクラウド サービスとプラットフォームへのより早く信頼できる接続が、どのように役立つか説明します。'
ms.openlocfilehash: b0f47278a94b2926cd540ce759ced9b2418aa598
ms.sourcegitcommit: 6e3bfe55a173a733d6696790b88efa39853ebdb9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "27470169"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="2cc52-103">Microsoft クラウド接続のためのExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2cc52-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="2cc52-104">**概要:** ExpressRoute による Microsoft のクラウド サービスとプラットフォームへのより早く信頼できる接続が、どのように役立つか説明します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="2cc52-105">ExpressRoute は、Microsoft のクラウドへのプライベート、専用、高スループットのネットワーク接続を提供します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="2cc52-106">Microsoft クラウドへの ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2cc52-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="2cc52-107">次の図は、ExpressRoute 接続を使用していない場合の Microsoft クラウドへのネットワーク パスを示しています。</span><span class="sxs-lookup"><span data-stu-id="2cc52-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="2cc52-108">**図 1:ExpressRoute のないネットワーク パス**</span><span class="sxs-lookup"><span data-stu-id="2cc52-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![図 1:ExpressRoute のないネットワーク パス](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="2cc52-p101">図 1 は、オンプレミスのネットワークと Microsoft クラウドとの間の一般的なパスを示しています。オンプレミスのネットワーク エッジは、ISP への WAN リンクを経由してインターネットに接続しています。トラフィックは、インターネットを通過して Microsoft クラウドのエッジに到達します。Microsoft クラウド内のクラウド サービスには、Office 365、Microsoft Azure、Microsoft Intune、Dynamics 365 があります。組織のユーザーは、オンプレミスのネットワークに配置することも、インターネットに配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="2cc52-115">ExpressRoute 接続がない場合、Microsoft クラウドへのトラフィック パスのうち制御可能な部分 (またサービス プロバイダーとの関係がある部分) は、オンプレミスのネットワーク エッジと ISP との間のリンクのみになります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="2cc52-116">ISP と Microsoft クラウド エッジとの間のパスは、インターネット上のベストエフォート配信システムになります。インターネットには、停止、トラフィックの輻輳、および悪意のあるユーザーによる監視の恐れがあります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="2cc52-117">インターネット上のユーザー (ローミング ユーザーやリモート ユーザー) は、Microsoft クラウドへのトラフィックをインターネット経由で送信します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="2cc52-118">次の図は、ExpressRoute 接続を使用している場合の Microsoft クラウドへのネットワーク パスを示しています。</span><span class="sxs-lookup"><span data-stu-id="2cc52-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="2cc52-119">**図 2: ExpressRoute のあるネットワーク パス**</span><span class="sxs-lookup"><span data-stu-id="2cc52-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![図 2: ExpressRoute のあるネットワーク パス](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="2cc52-p102">図 2 は、2 つのネットワーク パスを示しています。Microsoft Intune へのトラフィックは、通常のインターネットのトラフィックと同じパスを通過します。Office 365、Microsoft Azure、Dynamics 365 へのトラフィックは、ExpressRoute 接続を通過します。この接続は、オンプレミス ネットワークのエッジと Microsoft クラウドのエッジとの間の専用パスです。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="2cc52-p103">ExpressRoute 接続では、ここで、サービス ・ プロバイダーとの関係によって、コントロール、クラウドのエッジ、エッジからマイクロソフトへの全体のトラフィック パスを。この接続には、予測可能なパフォーマンスと、 [99.95% の稼働時間 SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/)を提供できます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="2cc52-p104">これにより、Office 365、Azure、Dynamics 365 サービスへの予測可能なスループットと待機時間は、サービス プロバイダーの接続に基づいて、信頼できるものになります。現時点では、Microsoft Intune への ExpressRoute 接続はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="2cc52-128">ExpressRoute 接続を通じて送信されるトラフィックは、インターネットの停止、トラフィックの輻輳、および監視についての恐れがなくなります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="2cc52-p105">インターネット上のユーザー (ローミング ユーザーやリモート ユーザーなど) は、この場合も、インターネットを通じて Microsoft クラウドへのトラフィックを送信します。1 つの例外として、Azure IaaS でホストされているイントラネットの基幹業務アプリケーションへのトラフィックが挙げられます。このトラフィックは、オンプレミスのネットワークへのリモート アクセス接続を経由して ExpressRoute で送信されます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="2cc52-131">ExpressRoute 接続を使用していても、一部のトラフィック (DNS クエリ、証明書失効リストによる確認、コンテンツ配信ネットワーク (CDN) の要求など) はインターネットを通じて送信されます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="2cc52-132">詳細については、次に示す追加の技術資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cc52-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="2cc52-133">Office 365 用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2cc52-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="2cc52-134">Azure 用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2cc52-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="2cc52-135">Azure 用 ExpressRoute の利点</span><span class="sxs-lookup"><span data-stu-id="2cc52-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="2cc52-136">ここでは、Azure ベースのクラウドサービスに ExpressRoute を使用するいくつかの利点を示します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="2cc52-p106">**予測可能なパフォーマンス:** Microsoft クラウドのエッジへの専用パスを使用することで、インターネット プロバイダーの停止とインターネット トラフィックの輻輳によるパフォーマンス低下の恐れがなくなります。Microsoft クラウドへのスループットおよび待機時間の SLA に対する責任があるプロバイダーを決定して保持できます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="2cc52-p107">**トラフィックのデータのプライバシー:** 専用の ExpressRoute 接続を通じて送信されるトラフィックには、悪意のあるユーザーによるインターネットの監視またはパケット キャプチャおよび分析の恐れがありません。これは、Multiprotocol Label Switching (MPLS) ベースの WAN リンクを使用することと同じように安全です。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="2cc52-141">**高スループットの接続:** 相互接続プロバイダーとネットワーク サービス プロバイダーによる ExpressRoute 接続の広範なサポートがあるため、Microsoft クラウドへの最大 10 Gbps のリンクが使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="2cc52-142">**構成によってはコストの低下につながる:** ExpressRoute 接続には追加のコストがかかりますが、Microsoft クラウド サービスへの十分なスループットが得られるように組織の複数の場所でインターネットのキャパシティを増やすよりも、1 つの ExpressRoute 接続にするほうがコストが低くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="2cc52-p108">ExpressRoute 接続は、すべての構成でパフォーマンスが向上するということを保証するものではありません。地域の Microsoft データセンターから数ホップしか離れていない高帯域幅のインターネット接続よりも、低帯域幅の ExpressRoute 接続のほうがパフォーマンスが低くなる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="2cc52-145">ExpressRoute with Office 365 の使用に関する最新の推奨事項については、「[Office 365 向け Azure ExpressRoute](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2cc52-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="2cc52-146">ExpressRoute の接続モデル</span><span class="sxs-lookup"><span data-stu-id="2cc52-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="2cc52-147">表 1 に、ExpressRoute 接続の 3 つの主要な接続モデルを示します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="2cc52-148">**Cloud Exchange でのコロケーション**</span><span class="sxs-lookup"><span data-stu-id="2cc52-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="2cc52-149">**ポイント ツー ポイントのイーサネット**</span><span class="sxs-lookup"><span data-stu-id="2cc52-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="2cc52-150">**Any-to-Any (IP VPN) 接続**</span><span class="sxs-lookup"><span data-stu-id="2cc52-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![ExpressRoute 接続モデル:Cloud Exchange でのコロケーション](media/Network-Poster/ER-Conn1.png)|![ExpressRoute 接続モデル:ポイント ツー ポイントのイーサネット](media/Network-Poster/ER-Conn2.png)|![ExpressRoute 接続モデル:Any-to-Any (IP VPN) 接続](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="2cc52-154">Could Exchange を備えた施設にデータセンターが併置されている場合は、併置プロバイダーのイーサネット交換機を通じた Microsoft クラウドへの仮想交差接続をオーダーできます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="2cc52-155">データセンターがオンプレミスに配置されている場合は、Microsoft クラウドへの接続に、ポイント ツー ポイントのイーサネット リンクを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="2cc52-156">既に、組織のサイトへの接続に IP VPN (MPLS) プロバイダーを使用している場合、Microsoft クラウドへの ExpressRoute 接続はプライベート WAN 上の別の場所と同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="2cc52-157">**表 1:ExpressRoute の接続モデル**</span><span class="sxs-lookup"><span data-stu-id="2cc52-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="2cc52-158">Microsoft クラウド サービスへの ExpressRoute ピアリング関係</span><span class="sxs-lookup"><span data-stu-id="2cc52-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="2cc52-p109">ExpressRoute の単一の接続を 2 つの罫線ゲートウェイ プロトコル (BGP) ピアリング関係が異なるマイクロソフト クラウドのさまざまな部分をサポートしています。BPG は、ピアリング関係を使用して信頼を確立し、ルーティング情報を交換します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p109">A single ExpressRoute connection supports up to two different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="2cc52-161">**図 3: 2 つ異なる BGP の関係で 1 つの ExpressRoute 接続**</span><span class="sxs-lookup"><span data-stu-id="2cc52-161">**Figure 3: The two different BGP relationships in a single ExpressRoute connection**</span></span>

![図 3: 2 つ異なる BGP の関係で 1 つの ExpressRoute 接続](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="2cc52-p110">図 3 は、オンプレミスのネットワークから、ExpressRoute の接続を示しています。ExpressRoute の接続には、2 つの論理ピアリング関係があります。マイクロソフトのピアリング関係は、Office 365、Dynamcs 365、Azure PaaS のサービスを含め、マイクロソフトの SaaS のサービスに移動します。プライベート ピアリング関係は、Azure IaaS と仮想マシンをホストする仮想ネットワークのゲートウェイに送られます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection has two logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365, Dynamcs 365, and Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="2cc52-167">Microsoft ピアリング BGP 関係:</span><span class="sxs-lookup"><span data-stu-id="2cc52-167">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="2cc52-168">Office 365、Dynamics 365 では、Azure のサービスのパブリック アドレスは、DMZ 内のルーターからです。</span><span class="sxs-lookup"><span data-stu-id="2cc52-168">Is from a router in your DMZ to the public addresses of Office 365, Dynamics 365, and Azure services.</span></span> 
    
- <span data-ttu-id="2cc52-169">双方向で開始される通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="2cc52-169">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="2cc52-170">プライベート ピアリング BGP 関係:</span><span class="sxs-lookup"><span data-stu-id="2cc52-170">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="2cc52-171">組織のネットワークのエッジにあるルーターから Azure VNet に割り当てられたプライベート IP アドレスに向けられています。</span><span class="sxs-lookup"><span data-stu-id="2cc52-171">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="2cc52-172">双方向で開始される通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="2cc52-172">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="2cc52-173">組織のネットワークのMicrosoft クラウドへの拡張であり、内部的に一貫したアドレス指定とルーティングを備えています。</span><span class="sxs-lookup"><span data-stu-id="2cc52-173">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>

>[!Note]
><span data-ttu-id="2cc52-174">この資料の以前のバージョンで記載されているパブリックのピアリング BGP 関係は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="2cc52-174">The public peering BGP relationship described in previous versions of this article has been deprecated.</span></span>
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="2cc52-175">ExpressRoute によるアプリケーション展開とトラフィック フローの例</span><span class="sxs-lookup"><span data-stu-id="2cc52-175">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="2cc52-p111">どのようにしてトラフィックが ExpressRoute 接続を通過して Microsoft クラウド内で移動するかは、送信元と送信先の間のパスにある各ホップでのルートとアプリケーションの動作という変数によって変化します。次に、Azure 仮想マシンで実行中のアプリケーションの例を示します。このアプリケーションは、サイト間 VPN 接続を通じてオンプレミスの SharePoint ファームにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p111">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="2cc52-178">**図 4:オンプレミス SharePoint ファームにアクセスする Azure 仮想マシン上のアプリケーション**</span><span class="sxs-lookup"><span data-stu-id="2cc52-178">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![図 4:オンプレミス SharePoint ファームにアクセスする Azure 仮想マシン上のアプリケーション](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="2cc52-180">図 4 は、オンプレミスの SharePoint ファーム、オンプレミス ネットワークと Azure IaaS の仮想ネットワークとの間のサイト間 VPN 接続、Azure IaaS 仮想マシンとして実行しているアプリケーション サーバー、およびアプリケーション サーバーと SharePoint ファームとの間のトラフィック フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="2cc52-180">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="2cc52-181">アプリケーションは、オンプレミスの DNS を使用して SharePoint ファームの IP アドレスを見つけます。また、すべてのトラフィックはサイト間 VPN 接続を通じて移動します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-181">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="2cc52-182">この組織は、オンプレミスの SharePoint ファームを Office 365 の SharePoint Online に移行して、ExpressRoute 接続を展開しました。</span><span class="sxs-lookup"><span data-stu-id="2cc52-182">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="2cc52-183">**図 5: オンプレミスの SharePoint ファームを SharePoint Online に移行する**</span><span class="sxs-lookup"><span data-stu-id="2cc52-183">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![図 5: オンプレミスの SharePoint ファームを SharePoint Online に移行する](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="2cc52-p112">図 5 は、Microsoft SaaS と Office 365 へのピアリング関係と、仮想ネットワーク上にアプリケーション サーバーを含む Azure IaaS へのピアリング関係を持つ ExpressRoute 接続の追加を示しています。オンプレミスの SharePoint ファームは、Office 365 に移行されています。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p112">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="2cc52-187">Microsoft ピアリング関係とプライベート ピアリング関係がある場合:</span><span class="sxs-lookup"><span data-stu-id="2cc52-187">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="2cc52-188">Azure 仮想ネットワーク ゲートウェイから、ExpressRoute 接続を通じてオンプレミスの場所が使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-188">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="2cc52-189">Office 365 サブスクリプションから、ExpressRoute 接続を通じてエッジ デバイス (プロキシ サーバーなど) のパブリック IP が使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-189">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="2cc52-190">オンプレミスのネットワーク エッジから、ExpressRoute 接続を通じて Azure VNet のプライベート IP アドレスと Office 365 のパブリック IP アドレスが使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-190">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="2cc52-191">アプリケーションが SharePoint Online の URL にアクセスすると、そのトラフィックは ExpressRoute 接続を通じてエッジにあるプロキシ サーバーに転送されます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-191">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="2cc52-p113">プロキシ サーバーが SharePoint Online の IP アドレスを見つけると、ExpressRoute 接続を通じてトラフィックが戻ります。応答トラフィックは逆方向のパスを通過します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p113">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="2cc52-194">**図 6:SharePoint ファームが Office 365 の SharePoint Online に移行したときのトラフィック フロー**</span><span class="sxs-lookup"><span data-stu-id="2cc52-194">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![図 6:SharePoint ファームが Office 365 の SharePoint Online に移行したときのトラフィック フロー](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="2cc52-196">図 6 は、アプリケーション サーバーと Office 365 の SharePoint Online との間で、トラフィックがプライベート ピアリング関係を通じてアプリケーション サーバーからオンプレミスのネットワーク エッジに流れ、Microsoft ピアリング関係を通じてエッジから Office 365 に流れる様子を示しています。</span><span class="sxs-lookup"><span data-stu-id="2cc52-196">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="2cc52-197">結果はヘアピン型になります (ルーティングとアプリケーション動作の結果)。</span><span class="sxs-lookup"><span data-stu-id="2cc52-197">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="2cc52-198">ExpressRoute と Microsoft のクラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="2cc52-198">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="2cc52-199">ExpressRoute 接続は、ExpressRoute と ExpressRoute Premium という 2 つのバージョンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-199">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="2cc52-200">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2cc52-200">ExpressRoute</span></span>

<span data-ttu-id="2cc52-201">組織のネットワークと Microsoft データセンターとの間でトラフィックが移動する方法は、次の場所の組み合わせになります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-201">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="2cc52-202">ユーザーの場所。</span><span class="sxs-lookup"><span data-stu-id="2cc52-202">Your locations.</span></span>
    
- <span data-ttu-id="2cc52-203">Microsoft クラウド ピアリングの場所 (Microsoft のエッジに接続する物理的な場所)。</span><span class="sxs-lookup"><span data-stu-id="2cc52-203">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="2cc52-204">Microsoft データセンターの場所。</span><span class="sxs-lookup"><span data-stu-id="2cc52-204">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="2cc52-205">Microsoft データセンターとクラウド ピアリングの場所は、すべて Microsoft クラウド ネットワークに接続されています。</span><span class="sxs-lookup"><span data-stu-id="2cc52-205">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="2cc52-p114">Microsoft クラウド ピアリングの場所への ExpressRoute 接続を作成すると、Microsoft クラウド ネットワークおよび同じ大陸内にあるすべての Microsoft データセンターの場所に接続されます。クラウド ピアリングの場所と宛先の Microsoft データセンターとの間のトラフィックは、Microsoft クラウド ネットワーク経由で転送されます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p114">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="2cc52-208">このため、Any-to-Any 接続モデルの場合は、ローカルの Microsoft データセンターへの配信が最適でなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-208">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="2cc52-209">**ExpressRoute の単一の接続を使用する地理的に分散組織の例を図 7:**</span><span class="sxs-lookup"><span data-stu-id="2cc52-209">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![ExpressRoute の単一の接続を使用する地理的に分散組織の例を図 7:](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="2cc52-p115">図 7 は、2 つの場所 (米国の北西にある Location 1 と北東にある Location 2) を持つ組織を示しています。これらは、Any-to-Any の WAN プロバイダーで接続されています。この組織には、西海岸にある Microsoft ピアリングの場所への ExpressRoute 接続もあります。北東にある Location 2 から東海岸のデータセンターに向かうトラフィックは、組織の WAN で西海岸に移動し、Microsoft ピアリングの場所に移動してから、Microsoft クラウド ネットワーク経由で国を横断して東海岸のデータセンターに戻ります。この経路をすべて通過する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p115">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="2cc52-215">配信を最適化するには、地域の Microsoft クラウド ピアリングの場所への複数の ExpressRoute 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-215">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="2cc52-216">**図 8: 地域のデータ センターへの最適な配信を確保するために複数の ExpressRoute 接続を使用する**</span><span class="sxs-lookup"><span data-stu-id="2cc52-216">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![図 8: 地域のデータ センターへの最適な配信を確保するために複数の ExpressRoute 接続を使用する](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="2cc52-p116">図 8 は、ExpressRoute 接続が 2 つある同じ組織を示しています。それぞれが地域的にローカルの Microsoft ピアリングの場所に接続しています。この構成では、北東にある Location 2 から東海岸のデータセンターに向かうトラフィックは、東海岸のピアリングの場所に直接移動し、Microsoft クラウド ネットワークに移動してから、東海岸のデータセンターに到達します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p116">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="2cc52-220">複数の ExpressRoute 接続には、次の利点があります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-220">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="2cc52-221">地域的にローカルな Microsoft データセンターの場所に対するパフォーマンスの向上。</span><span class="sxs-lookup"><span data-stu-id="2cc52-221">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="2cc52-222">ローカルの ExpressRoute 接続が使用不能になったときの Microsoft クラウドに対する可用性の向上。</span><span class="sxs-lookup"><span data-stu-id="2cc52-222">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="2cc52-p117">これは、複数の組織が同じ大陸内にある場合に最適に機能します。ただし、組織のある大陸の外側の Microsoft データセンターへのトラフィックはインターネット経由で移動します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p117">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="2cc52-225">Microsoft クラウド ネットワークを経由する大陸間トラフィックには、ExpressRoute Premium を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cc52-225">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="2cc52-226">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="2cc52-226">ExpressRoute Premium</span></span>

<span data-ttu-id="2cc52-227">大陸間にグローバルに分散している組織の場合は、ExpressRoute Premium を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-227">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="2cc52-p118">ExpressRoute Premium では、どの大陸にある Microsoft ピアリングの場所からでも、あらゆる大陸にある任意の Microsoft データセンターに到達できます。大陸間のトラフィックは、Microsoft クラウド ネットワークを通じて転送されます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p118">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="2cc52-230">複数の ExpressRoute Premium 接続を使用すると、次の利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-230">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="2cc52-231">大陸的にローカルな Microsoft データセンターに対するパフォーマンスの向上。</span><span class="sxs-lookup"><span data-stu-id="2cc52-231">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="2cc52-232">ローカルの ExpressRoute 接続が使用不能になったときのグローバルな Microsoft クラウドに対する可用性の向上。</span><span class="sxs-lookup"><span data-stu-id="2cc52-232">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="2cc52-233">ExpressRoute プレミアムは、Office 365 に基づく ExpressRoute の接続に必要です。</span><span class="sxs-lookup"><span data-stu-id="2cc52-233">ExpressRoute Premium is required for Office 365-based ExpressRoute connections.</span></span>
  
<span data-ttu-id="2cc52-234">**図 9: 全世界をカバーする Microsoft のクラウド ネットワーク**</span><span class="sxs-lookup"><span data-stu-id="2cc52-234">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![図 9: 全世界をカバーする Microsoft のクラウド ネットワーク](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="2cc52-p119">図 9 は、世界規模の Microsoft クラウド ネットワークの論理図を示しています。この図には、大陸間および地域間に広がるネットワークと、そのネットワークの相互接続が示されています。各大陸にある部分的な Microsoft クラウド ネットワークでは、グローバル企業が、地域拠点の支社からローカルの Microsoft ピアリングの場所までの ExpressRoute Premium 接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p119">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="2cc52-238">地域のオフィスで、次に示す宛先に該当する Office 365 トラフィックの移動:</span><span class="sxs-lookup"><span data-stu-id="2cc52-238">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="2cc52-239">大陸の Office 365 データセンターへのトラフィックは、その大陸内の Microsoft クラウド ネットワークを通じて移動します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-239">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="2cc52-240">別の大陸にある Office 365 データセンターへのトラフィックは、大陸間の Microsoft クラウド ネットワークを通じて移動します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-240">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="2cc52-241">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cc52-241">For more information, see:</span></span>
  
- [<span data-ttu-id="2cc52-242">Azure ExpressRoute for Office 365 のトレーニング</span><span class="sxs-lookup"><span data-stu-id="2cc52-242">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="2cc52-243">Office 365 のネットワーク計画とパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="2cc52-243">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="2cc52-244">Office 365 のパフォーマンス管理</span><span class="sxs-lookup"><span data-stu-id="2cc52-244">Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="2cc52-245">ExpressRoute のオプション</span><span class="sxs-lookup"><span data-stu-id="2cc52-245">ExpressRoute options</span></span>

<span data-ttu-id="2cc52-246">ExpressRoute の展開には、次に示すオプションを組み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-246">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="2cc52-247">**エッジでのセキュリティ:** ExpressRoute 接続を通じて送受信されるトラフィックに高度なセキュリティ (トラフィック検査や侵入/マルウェア検出など) を提供するには、DMZ 内のトラフィック パスまたはインターネット境界にセキュリティ アプライアンスを配置します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-247">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
- <span data-ttu-id="2cc52-p120">**Vm 用のインターネット トラフィック:** Azure の仮想マシンがインターネット上の場所に直接トラフィックを開始することを防ぐためには、Microsoft の既定のルートをアドバタイズします。インターネットへのトラフィックは、ExpressRoute 接続を経由し、オンプレミスのプロキシ サーバー経由でルーティングされます。Azure PaaS サービスまたは Office 365 に Azure の仮想マシンからのトラフィックは、ExpressRoute 接続経由でルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p120">**Internet traffic for VMs:** To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="2cc52-p121">**WAN オプティマイザー:** クロスプレミス Azure 仮想ネットワーク (VNet) のプライベート ピアリング接続の両側に WAN オプティマイザーを展開できます。Azure VNet の内部では、Azure マーケットプレースから得られる WAN オプティマイザー ネットワーク アプライアンスと、トラフィックがアプライアンスを通過するようにルーティングするユーザー定義のルーティングを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p121">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="2cc52-p122">**サービスの品質:** トラフィックの IPv4 ヘッダーで DSCP (Differentiated Services Code Point) の値を使用して、そのトラフィックに音声、ビデオ/インタラクティブまたはベストエフォート配信のマークを付けます。これは、Microsoft ピアリング関係と Skype for Business Online のトラフィックには特に重要です。</span><span class="sxs-lookup"><span data-stu-id="2cc52-p122">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="2cc52-255">詳細については、次に示す追加の技術資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cc52-255">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="2cc52-256">Office 365 用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2cc52-256">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="2cc52-257">Azure ExpressRoute for Office 365 のトレーニング</span><span class="sxs-lookup"><span data-stu-id="2cc52-257">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="2cc52-258">Azure 用 ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="2cc52-258">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="2cc52-259">次の手順</span><span class="sxs-lookup"><span data-stu-id="2cc52-259">Next step</span></span>

[<span data-ttu-id="2cc52-260">Microsoft SaaS のためのネットワーク デザイン</span><span class="sxs-lookup"><span data-stu-id="2cc52-260">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="2cc52-261">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cc52-261">See also</span></span>

[<span data-ttu-id="2cc52-262">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="2cc52-262">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="2cc52-263">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="2cc52-263">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

