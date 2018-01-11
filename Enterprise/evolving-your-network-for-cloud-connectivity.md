---
title: "クラウド接続のためにネットワークを進化させる"
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
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: "概要: クラウド導入において、新しいアプローチによるネットワーク インフラストラクチャ投資が必要となることを理解します。"
ms.openlocfilehash: 18b4e5e10094a43f0d2b10cd0f01684f2352a0a8
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="evolving-your-network-for-cloud-connectivity"></a><span data-ttu-id="a5c62-103">クラウド接続のためにネットワークを進化させる</span><span class="sxs-lookup"><span data-stu-id="a5c62-103">Evolving your network for cloud connectivity</span></span>

 <span data-ttu-id="a5c62-104">**概要:** クラウド導入において、新しいアプローチによるネットワーク インフラストラクチャ投資が必要となることを理解します。</span><span class="sxs-lookup"><span data-stu-id="a5c62-104">**Summary:** Understand how cloud adoption requires a new approach to network infrastructure investments.</span></span>
  
<span data-ttu-id="a5c62-p101">クラウド移行によって、企業ネットワークの内外でのトラフィック フローの容量と特性が変化します。また、セキュリティ リスクを軽減するためのアプローチにも影響します。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p101">Cloud migration changes the volume and nature of traffic flows within and outside a corporate network. It also affects approaches to mitigating security risk.</span></span>
  
- <span data-ttu-id="a5c62-107">クラウド導入前:</span><span class="sxs-lookup"><span data-stu-id="a5c62-107">Before the cloud</span></span>
    
    <span data-ttu-id="a5c62-p102">ネットワーク インフラストラクチャ投資の大半は、オンプレミスのデータセンターへの接続性を、利用可能で信頼性が高く、そして効率の良いものとすることに費やされてきました。多くの組織にとって、インターネット接続性は内部の事業運営において肝要なものではありませんでした。ネットワークの境界は、セキュリティ侵害に対する第一の防御の役割を果たしました。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p102">Most networking infrastructure investments were spent on ensuring available, reliable, and performant connectivity to on-premises datacenters. For many organizations, Internet connectivity was not critical for internal business operations. Network boundaries were primary defenses against security breaches.</span></span>
    
- <span data-ttu-id="a5c62-111">クラウド導入後:</span><span class="sxs-lookup"><span data-stu-id="a5c62-111">After the cloud</span></span>
    
    <span data-ttu-id="a5c62-p103">新しい移行後の生産性およびクラウド上で実行される IT ワークロードによって、インフラストラクチャ投資はオンプレミスのデータセンターから、内部の事業運営において肝要なものとなったインターネット接続性へとシフトします。フェデレーション接続により、ネットワーク上およびMicrosoft のクラウド サービスへの接続ポイント上を ID とデータが流れるため、セキュリティ戦略はそれら ID とデータを保護するものへとシフトします。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p103">With new and migrated productivity and IT workloads running in the cloud, infrastructure investments shift from on-premises datacenters to Internet connectivity, which is now critical for internal business operations. Federated connectivity shifts security strategy to protecting identities and data as they flow through the network and points of connectivity to Microsoft cloud services.</span></span>
    
<span data-ttu-id="a5c62-p104">ネットワーク インフラストラクチャ投資は、接続性から始まります。追加の投資は、クラウド サービスのカテゴリに応じたものとなります。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p104">Network infrastructure investments begin with connectivity. Additional investments depend on the category of cloud service.</span></span>
  
- <span data-ttu-id="a5c62-p105">**サービスとしてのソフトウェア (SaaS)** Microsoft SaaS サービスには、Office 365、Microsoft Intune および Microsoft Dynamics 365 が含まれます。ユーザーによる SaaS サービスの導入を成功させるためには、インターネットまたは直接的な Microsoft クラウド サービスへの可用性および効率性の高い接続が必要となります。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p105">**Software as a Service (SaaS)** Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365. Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>
    
    <span data-ttu-id="a5c62-p106">ネットワーク アーキテクチャは、信頼性および冗長性のある接続性と、十分な帯域幅に重点を置いています。継続的な投資には、パフォーマンスの監視およびチューニングが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p106">Network architecture focuses on reliable, redundant connectivity and ample bandwidth. Ongoing investments include performance monitoring and tuning.</span></span>
    
- <span data-ttu-id="a5c62-p107">**サービスとしての Azure プラットフォーム (PaaS)** Microsoft SaaS サービスへの投資に加えて、複数サイトまたは地理的に分散したPaaS アプリケーションのために、Azure Traffic Manager はクライアント トラフィックを分散させるように設計する必要がある場合があります。継続的な投資には、パフォーマンスおよびトラフィック分散の監視、並びにフェールオーバーのテストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p107">**Azure Platform as a Service (PaaS)** In addition to the investments for Microsoft SaaS services, multi-site or geographically distributed PaaS applications might require architecting Azure Traffic Manager to distribute client traffic. Ongoing investments include performance and traffic distribution monitoring and failover testing.</span></span>
    
- <span data-ttu-id="a5c62-p108">**サービスとしての Azure インフラストラクチャ (IaaS)** Microsoft SaaS サービスおよび PaaS サービスへの投資に加えて、IaaS における IT ワークロードの実行においては、仮想マシンをホストする Azure 仮想ネットワーク、仮想マシン上で実行されるアプリケーションへのセキュアな接続、ルーティング、IP アドレス指定、DNS、および負荷分散の設計と構成が必要となります。継続的な投資には、パフォーマンスおよびセキュリティの監視、並びにトラブルシューティングが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p108">**Azure Infrastructure as a Service (IaaS)** In addition to the investments for Microsoft SaaS and PaaS services, running IT workloads in IaaS requires the design and configuration of Azure virtual networks that host virtual machines, secure connectivity to applications running on them, routing, IP addressing, DNS, and load balancing. Ongoing investments include performance and security monitoring and troubleshooting.</span></span>
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a><span data-ttu-id="a5c62-124">クラウドで成功するためのネットワーク投資の領域</span><span class="sxs-lookup"><span data-stu-id="a5c62-124">Areas of networking investment for success in the cloud</span></span>

<span data-ttu-id="a5c62-p109">エンタープライズ組織は、系統的なアプローチによってイントラネット内およびインターネットへのネットワーク スループットを最適化することができます。ExpressRoute 接続にも利点がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p109">Enterprise organizations benefit from taking a methodical approach to optimizing network throughput across your intranet and to the Internet. You might also benefit from an ExpressRoute connection.</span></span>
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a><span data-ttu-id="a5c62-127">イントラネットから境界ネットワークへの接続を最適化します。</span><span class="sxs-lookup"><span data-stu-id="a5c62-127">Optimize intranet connectivity to your edge network</span></span>

<span data-ttu-id="a5c62-p110">長年にわたって、多くの組織はオンプレミス データ センターで実行されているアプリケーションへのイントラネットの接続およびパフォーマンスを最適化してきました。Microsoft クラウド上の生産性および IT ワークロードを得た今、接続の高可用性を確保し、境界ネットワークおよびイントラネット ユーザー間のトラフィック パフォーマンスを最適化するための追加投資を行わなければなりません。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p110">Over the years, many organizations have optimized intranet connectivity and performance to applications running in on-premises datacenters. With productivity and IT workloads running in the Microsoft cloud, additional investment must ensure high connectivity availability and that traffic performance between your edge network and your intranet users is optimal.</span></span>
  
### <a name="optimize-throughput-at-your-edge-network"></a><span data-ttu-id="a5c62-130">境界ネットワークにおけるスループットの最適化</span><span class="sxs-lookup"><span data-stu-id="a5c62-130">Optimize throughput at your edge network</span></span>

<span data-ttu-id="a5c62-131">クラウドへの日々の生産性トラフィックが増えるにつれて、境界ネットワークにおけるシステムのセットを詳細に調べ、それらの処理が滞ることなく行われ、高可用性を有し、ピーク時の負荷に耐えるだけの十分な容量があるかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5c62-131">As more of your day-to-day productivity traffic travels to the cloud, you should closely examine the set of systems at your edge network to ensure that they are current, provide high availability, and have sufficient capacity to meet peak loads.</span></span>
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a><span data-ttu-id="a5c62-132">Azure への高い SLA のために、Office 365 および Dynamics 365 は ExpressRoute を使用します。</span><span class="sxs-lookup"><span data-stu-id="a5c62-132">For a high SLA to Azure, Office 365, and Dynamics 365, use ExpressRoute</span></span>

<span data-ttu-id="a5c62-p111">境界ネットワークから現行のインターネット接続を利用することができますが、Microsoft クラウド サービスとの間のトラフィックは、インターネットへ流れる他のイントラネット トラフィックとパイプを共有しなければなりません。また、Microsoft クラウドサービスへのトラフィックは、インターネット トラフィックの混雑の影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p111">Although you can utilize your current Internet connection from your edge network, traffic to and from Microsoft cloud services must share the pipe with other intranet traffic going to the Internet. Additionally, your traffic to Microsoft cloud services is subject to Internet traffic congestion.</span></span>
  
<span data-ttu-id="a5c62-135">高い SLA および最高のパフォーマンスを得るために、ExpressRoute、つまり自分のネットワークと Azure、Office 365、Dynamics 365 (またはこれら 3 つすべて) との間をつなぐ専用 WAN 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="a5c62-135">For a high SLA and the best performance, use ExpressRoute, a dedicated WAN connection between your network and Azure, Office 365, Dynamics 365, or all three.</span></span> 
  
<span data-ttu-id="a5c62-p112">ExpressRoute は、専用の接続のために既存ネットワーク プロバイダーを活用できます。ExpressRoute によって接続されているリソースは、地理的に分散する組織であっても、WAN 上にあるかのように見えます。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p112">ExpressRoute can leverage your existing network provider for a dedicated connection. Resources connected by ExpressRoute appear as if they are on your WAN, even for geographically-distributed organizations.</span></span>
  
<span data-ttu-id="a5c62-138">詳細については、「[Microsoft クラウド接続のためのExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5c62-138">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
## <a name="scope-of-network-investments"></a><span data-ttu-id="a5c62-139">ネットワーク投資の範囲</span><span class="sxs-lookup"><span data-stu-id="a5c62-139">Scope of network investments</span></span>

<span data-ttu-id="a5c62-p113">ネットワーク投資の範囲は、クラウド サービスのカテゴリに応じたものとなります。全面的に Microsoft のクラウドに投資することにより、ネットワーク チームの投資を最大化することができます。たとえば、IaaS サービスへの投資は、すべての投資領域に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a5c62-p113">The scope of network investments depend on the category of cloud service. Investing across Microsoft's cloud maximizes the investments of networking teams. For example, investments for IaaS services apply to all investment areas.</span></span>
  
|||||
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="a5c62-143">投資領域</span><span class="sxs-lookup"><span data-stu-id="a5c62-143">Investment area</span></span>  <br/> |<span data-ttu-id="a5c62-144">SaaS</span><span class="sxs-lookup"><span data-stu-id="a5c62-144">SaaS</span></span>  <br/> |<span data-ttu-id="a5c62-145">PaaS</span><span class="sxs-lookup"><span data-stu-id="a5c62-145">PaaS</span></span>  <br/> |<span data-ttu-id="a5c62-146">IaaS</span><span class="sxs-lookup"><span data-stu-id="a5c62-146">IaaS</span></span>  <br/> |
|<span data-ttu-id="a5c62-147">十分な帯域幅を備えた、信頼性および冗長性のあるインターネット接続を設計します</span><span class="sxs-lookup"><span data-stu-id="a5c62-147">Architect reliable, redundant Internet connectivity with ample bandwidth</span></span>  <br/> |<span data-ttu-id="a5c62-148">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-148">Applies</span></span>  <br/> |<span data-ttu-id="a5c62-149">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-149">Applies</span></span>  <br/> |<span data-ttu-id="a5c62-150">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-150">Applies</span></span>  <br/> |
|<span data-ttu-id="a5c62-151">パフォーマンスのためにインターネット スループットの監視およびチューニングを行います</span><span class="sxs-lookup"><span data-stu-id="a5c62-151">Monitor and tune Internet throughput for performance</span></span>  <br/> |<span data-ttu-id="a5c62-152">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-152">Applies</span></span>  <br/> |<span data-ttu-id="a5c62-153">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-153">Applies</span></span>  <br/> |<span data-ttu-id="a5c62-154">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-154">Applies</span></span>  <br/> |
|<span data-ttu-id="a5c62-155">インターネットの接続性およびスループットの問題に関するトラブルシューティングを行います</span><span class="sxs-lookup"><span data-stu-id="a5c62-155">Troubleshoot Internet connectivity and throughput issues</span></span>  <br/> |<span data-ttu-id="a5c62-156">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-156">Applies</span></span>  <br/> |<span data-ttu-id="a5c62-157">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-157">Applies</span></span>  <br/> |<span data-ttu-id="a5c62-158">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-158">Applies</span></span>  <br/> |
|<span data-ttu-id="a5c62-159">異なるエンドポイントへとトラフィックの負荷分散ができるように、Azure Traffic Manager の設計を行います</span><span class="sxs-lookup"><span data-stu-id="a5c62-159">Design Azure Traffic Manager to load balance traffic to different endpoints</span></span>  <br/> ||<span data-ttu-id="a5c62-160">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-160">Applies</span></span>  <br/> |<span data-ttu-id="a5c62-161">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-161">Applies</span></span>  <br/> |
|<span data-ttu-id="a5c62-162">信頼性および冗長性があり、効率的な Azure 仮想ネットワークへの接続を設計します</span><span class="sxs-lookup"><span data-stu-id="a5c62-162">Architect reliable, redundant, and performant connectivity to Azure virtual networks</span></span>  <br/> |||<span data-ttu-id="a5c62-163">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-163">Applies</span></span>  <br/> |
|<span data-ttu-id="a5c62-164">Azure 仮想マシンへのセキュアな接続を設計します</span><span class="sxs-lookup"><span data-stu-id="a5c62-164">Design secure connectivity to Azure virtual machines</span></span>  <br/> |||<span data-ttu-id="a5c62-165">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-165">Applies</span></span>  <br/> |
|<span data-ttu-id="a5c62-166">オンプレミスの場所と仮想ネットワークとの間のルーティングを設計し、実装します</span><span class="sxs-lookup"><span data-stu-id="a5c62-166">Design and implement routing between on-premises locations and virtual networks</span></span>  <br/> |||<span data-ttu-id="a5c62-167">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-167">Applies</span></span>  <br/> |
|<span data-ttu-id="a5c62-168">内部およびインターネットに接続する IT ワークロードのために、負荷分散を設計し、実装します</span><span class="sxs-lookup"><span data-stu-id="a5c62-168">Architect and implement load balancing for internal and Internet-facing IT workloads</span></span>  <br/> |||<span data-ttu-id="a5c62-169">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-169">Applies</span></span>  <br/> |
|<span data-ttu-id="a5c62-170">仮想マシンの接続性およびスループットの問題に関するトラブルシューティングを行います</span><span class="sxs-lookup"><span data-stu-id="a5c62-170">Troubleshoot virtual machine connectivity and throughput issues</span></span>  <br/> |||<span data-ttu-id="a5c62-171">適用</span><span class="sxs-lookup"><span data-stu-id="a5c62-171">Applies</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="a5c62-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5c62-172">See Also</span></span>

[<span data-ttu-id="a5c62-173">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="a5c62-173">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="a5c62-174">Microsoft クラウド接続のためのExpressRoute</span><span class="sxs-lookup"><span data-stu-id="a5c62-174">ExpressRoute for Microsoft cloud connectivity</span></span>](expressroute-for-microsoft-cloud-connectivity.md)
  
[<span data-ttu-id="a5c62-175">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="a5c62-175">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="a5c62-176">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="a5c62-176">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



