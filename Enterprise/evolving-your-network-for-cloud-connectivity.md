---
title: クラウド接続のためにネットワークを進化させる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: '概要: クラウド導入において、新しいアプローチによるネットワーク インフラストラクチャ投資が必要となることを理解します。'
ms.openlocfilehash: c8fba120292b89894850312a84fd6067d925a07f
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872258"
---
# <a name="evolving-your-network-for-cloud-connectivity"></a><span data-ttu-id="5c13d-103">クラウド接続のためにネットワークを進化させる</span><span class="sxs-lookup"><span data-stu-id="5c13d-103">Evolving your network for cloud connectivity</span></span>

 <span data-ttu-id="5c13d-104">**概要:** クラウド導入において、新しいアプローチによるネットワーク インフラストラクチャ投資が必要となることを理解します。</span><span class="sxs-lookup"><span data-stu-id="5c13d-104">**Summary:** Understand how cloud adoption requires a new approach to network infrastructure investments.</span></span>
  
<span data-ttu-id="5c13d-p101">クラウド移行によって、企業ネットワークの内外でのトラフィック フローの容量と特性が変化します。また、セキュリティ リスクを軽減するためのアプローチにも影響します。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p101">Cloud migration changes the volume and nature of traffic flows within and outside a corporate network. It also affects approaches to mitigating security risk.</span></span>
  
- <span data-ttu-id="5c13d-107">クラウド導入前:</span><span class="sxs-lookup"><span data-stu-id="5c13d-107">Before the cloud</span></span>
    
    <span data-ttu-id="5c13d-p102">ネットワーク インフラストラクチャ投資の大半は、オンプレミスのデータセンターへの接続性を、利用可能で信頼性が高く、そして効率の良いものとすることに費やされてきました。多くの組織にとって、インターネット接続性は内部の事業運営において肝要なものではありませんでした。ネットワークの境界は、セキュリティ侵害に対する第一の防御の役割を果たしました。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p102">Most networking infrastructure investments were spent on ensuring available, reliable, and performant connectivity to on-premises datacenters. For many organizations, Internet connectivity was not critical for internal business operations. Network boundaries were primary defenses against security breaches.</span></span>
    
- <span data-ttu-id="5c13d-111">クラウド導入後:</span><span class="sxs-lookup"><span data-stu-id="5c13d-111">After the cloud</span></span>
    
    <span data-ttu-id="5c13d-p103">新しい移行後の生産性およびクラウド上で実行される IT ワークロードによって、インフラストラクチャ投資はオンプレミスのデータセンターから、内部の事業運営において肝要なものとなったインターネット接続性へとシフトします。フェデレーション接続により、ネットワーク上およびMicrosoft のクラウド サービスへの接続ポイント上を ID とデータが流れるため、セキュリティ戦略はそれら ID とデータを保護するものへとシフトします。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p103">With new and migrated productivity and IT workloads running in the cloud, infrastructure investments shift from on-premises datacenters to Internet connectivity, which is now critical for internal business operations. Federated connectivity shifts security strategy to protecting identities and data as they flow through the network and points of connectivity to Microsoft cloud services.</span></span>
    
<span data-ttu-id="5c13d-p104">ネットワーク インフラストラクチャ投資は、接続性から始まります。追加の投資は、クラウド サービスのカテゴリに応じたものとなります。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p104">Network infrastructure investments begin with connectivity. Additional investments depend on the category of cloud service.</span></span>
  
- <span data-ttu-id="5c13d-p105">**サービスとしてのソフトウェア (SaaS)** Microsoft SaaS サービスには、Office 365、Microsoft Intune および Microsoft Dynamics 365 が含まれます。ユーザーによる SaaS サービスの導入を成功させるためには、インターネットまたは直接的な Microsoft クラウド サービスへの可用性および効率性の高い接続が必要となります。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p105">**Software as a Service (SaaS)** Microsoft SaaS services include Office 365, Microsoft Intune, and Microsoft Dynamics 365. Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>
    
    <span data-ttu-id="5c13d-p106">ネットワーク アーキテクチャは、信頼性および冗長性のある接続性と、十分な帯域幅に重点を置いています。継続的な投資には、パフォーマンスの監視およびチューニングが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p106">Network architecture focuses on reliable, redundant connectivity and ample bandwidth. Ongoing investments include performance monitoring and tuning.</span></span>
    
- <span data-ttu-id="5c13d-p107">**サービスとしての Azure プラットフォーム (PaaS)** Microsoft SaaS サービスへの投資に加えて、複数サイトまたは地理的に分散したPaaS アプリケーションのために、Azure Traffic Manager はクライアント トラフィックを分散させるように設計する必要がある場合があります。継続的な投資には、パフォーマンスおよびトラフィック分散の監視、並びにフェールオーバーのテストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p107">**Azure Platform as a Service (PaaS)** In addition to the investments for Microsoft SaaS services, multi-site or geographically distributed PaaS applications might require architecting Azure Traffic Manager to distribute client traffic. Ongoing investments include performance and traffic distribution monitoring and failover testing.</span></span>
    
- <span data-ttu-id="5c13d-p108">**サービスとしての Azure インフラストラクチャ (IaaS)** Microsoft SaaS サービスおよび PaaS サービスへの投資に加えて、IaaS における IT ワークロードの実行においては、仮想マシンをホストする Azure 仮想ネットワーク、仮想マシン上で実行されるアプリケーションへのセキュアな接続、ルーティング、IP アドレス指定、DNS、および負荷分散の設計と構成が必要となります。継続的な投資には、パフォーマンスおよびセキュリティの監視、並びにトラブルシューティングが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p108">**Azure Infrastructure as a Service (IaaS)** In addition to the investments for Microsoft SaaS and PaaS services, running IT workloads in IaaS requires the design and configuration of Azure virtual networks that host virtual machines, secure connectivity to applications running on them, routing, IP addressing, DNS, and load balancing. Ongoing investments include performance and security monitoring and troubleshooting.</span></span>

<span data-ttu-id="5c13d-p109">[Microsoft 365](https://www.microsoft.com/microsoft-365)は、Office 365、エンタープライズ管理 + セキュリティ (EMS)、および Windows の 10 の組み合わせです。Microsoft 365 サービスを組み合わせて複数 SaaS Azure のインテリジェントな包括的なソリューションを創造するすべてのユーザーを強力に支援し、安全に共同作業します。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p109">[Microsoft 365](https://www.microsoft.com/microsoft-365) is a combination of Office 365, Enterprise Management + Security (EMS), and Windows 10. Microsoft 365 combines multiple SaaS and Azure services for a complete, intelligent solution that empowers everyone to be creative and work together securely.</span></span>
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a><span data-ttu-id="5c13d-126">クラウドで成功するためのネットワーク投資の領域</span><span class="sxs-lookup"><span data-stu-id="5c13d-126">Areas of networking investment for success in the cloud</span></span>

<span data-ttu-id="5c13d-p110">エンタープライズ組織は、系統的なアプローチによってイントラネット内およびインターネットへのネットワーク スループットを最適化することができます。ExpressRoute 接続にも利点がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p110">Enterprise organizations benefit from taking a methodical approach to optimizing network throughput across your intranet and to the Internet. You might also benefit from an ExpressRoute connection.</span></span>
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a><span data-ttu-id="5c13d-129">イントラネットから境界ネットワークへの接続を最適化します。</span><span class="sxs-lookup"><span data-stu-id="5c13d-129">Optimize intranet connectivity to your edge network</span></span>

<span data-ttu-id="5c13d-p111">長年にわたって、多くの組織はオンプレミス データ センターで実行されているアプリケーションへのイントラネットの接続およびパフォーマンスを最適化してきました。Microsoft クラウド上の生産性および IT ワークロードを得た今、接続の高可用性を確保し、境界ネットワークおよびイントラネット ユーザー間のトラフィック パフォーマンスを最適化するための追加投資を行わなければなりません。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p111">Over the years, many organizations have optimized intranet connectivity and performance to applications running in on-premises datacenters. With productivity and IT workloads running in the Microsoft cloud, additional investment must ensure high connectivity availability and that traffic performance between your edge network and your intranet users is optimal.</span></span>
  
### <a name="optimize-throughput-at-your-edge-network"></a><span data-ttu-id="5c13d-132">境界ネットワークにおけるスループットの最適化</span><span class="sxs-lookup"><span data-stu-id="5c13d-132">Optimize throughput at your edge network</span></span>

<span data-ttu-id="5c13d-133">クラウドへの日々の生産性トラフィックが増えるにつれて、境界ネットワークにおけるシステムのセットを詳細に調べ、それらの処理が滞ることなく行われ、高可用性を有し、ピーク時の負荷に耐えるだけの十分な容量があるかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5c13d-133">As more of your day-to-day productivity traffic travels to the cloud, you should closely examine the set of systems at your edge network to ensure that they are current, provide high availability, and have sufficient capacity to meet peak loads.</span></span>
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a><span data-ttu-id="5c13d-134">Azure への高い SLA のために、Office 365 および Dynamics 365 は ExpressRoute を使用します。</span><span class="sxs-lookup"><span data-stu-id="5c13d-134">For a high SLA to Azure, Office 365, and Dynamics 365, use ExpressRoute</span></span>

<span data-ttu-id="5c13d-p112">エッジ ネットワークから、現在のインターネット接続を使用できますが、マイクロソフトのクラウド サービスとの間のトラフィックを他のイントラネット トラフィックをインターネットにパイプを共有しなければなりません。また、マイクロソフトのクラウド サービスへのトラフィックは、インターネット トラフィックの輻輳の対象です。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p112">Although you can use your current Internet connection from your edge network, traffic to and from Microsoft cloud services must share the pipe with other intranet traffic going to the Internet. Additionally, your traffic to Microsoft cloud services is subject to Internet traffic congestion.</span></span>
  
<span data-ttu-id="5c13d-137">高い SLA および最高のパフォーマンスを得るために、ExpressRoute、つまり自分のネットワークと Azure、Office 365、Dynamics 365 (またはこれら 3 つすべて) との間をつなぐ専用 WAN 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="5c13d-137">For a high SLA and the best performance, use ExpressRoute, a dedicated WAN connection between your network and Azure, Office 365, Dynamics 365, or all three.</span></span> 
  
<span data-ttu-id="5c13d-p113">ExpressRoute は、専用の接続のために既存ネットワーク プロバイダーを活用できます。ExpressRoute によって接続されているリソースは、地理的に分散する組織であっても、WAN 上にあるかのように見えます。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p113">ExpressRoute can leverage your existing network provider for a dedicated connection. Resources connected by ExpressRoute appear as if they are on your WAN, even for geographically-distributed organizations.</span></span>
  
<span data-ttu-id="5c13d-140">詳細については、「[Microsoft クラウド接続のためのExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c13d-140">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
## <a name="scope-of-network-investments"></a><span data-ttu-id="5c13d-141">ネットワーク投資の範囲</span><span class="sxs-lookup"><span data-stu-id="5c13d-141">Scope of network investments</span></span>

<span data-ttu-id="5c13d-p114">ネットワーク投資の範囲は、クラウド サービスのカテゴリに応じたものとなります。全面的に Microsoft のクラウドに投資することにより、ネットワーク チームの投資を最大化することができます。たとえば、IaaS サービスへの投資は、すべての投資領域に適用されます。</span><span class="sxs-lookup"><span data-stu-id="5c13d-p114">The scope of network investments depend on the category of cloud service. Investing across Microsoft's cloud maximizes the investments of networking teams. For example, investments for IaaS services apply to all investment areas.</span></span>
  
|||||
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="5c13d-145">投資領域</span><span class="sxs-lookup"><span data-stu-id="5c13d-145">Investment area</span></span>  <br/> |<span data-ttu-id="5c13d-146">SaaS</span><span class="sxs-lookup"><span data-stu-id="5c13d-146">SaaS</span></span>  <br/> |<span data-ttu-id="5c13d-147">PaaS</span><span class="sxs-lookup"><span data-stu-id="5c13d-147">PaaS</span></span>  <br/> |<span data-ttu-id="5c13d-148">IaaS</span><span class="sxs-lookup"><span data-stu-id="5c13d-148">IaaS</span></span>  <br/> |
|<span data-ttu-id="5c13d-149">十分な帯域幅を備えた、信頼性および冗長性のあるインターネット接続を設計します</span><span class="sxs-lookup"><span data-stu-id="5c13d-149">Architect reliable, redundant Internet connectivity with ample bandwidth</span></span>  <br/> |<span data-ttu-id="5c13d-150">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-150">Applies</span></span>  <br/> |<span data-ttu-id="5c13d-151">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-151">Applies</span></span>  <br/> |<span data-ttu-id="5c13d-152">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-152">Applies</span></span>  <br/> |
|<span data-ttu-id="5c13d-153">パフォーマンスのためにインターネット スループットの監視およびチューニングを行います</span><span class="sxs-lookup"><span data-stu-id="5c13d-153">Monitor and tune Internet throughput for performance</span></span>  <br/> |<span data-ttu-id="5c13d-154">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-154">Applies</span></span>  <br/> |<span data-ttu-id="5c13d-155">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-155">Applies</span></span>  <br/> |<span data-ttu-id="5c13d-156">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-156">Applies</span></span>  <br/> |
|<span data-ttu-id="5c13d-157">インターネットの接続性およびスループットの問題に関するトラブルシューティングを行います</span><span class="sxs-lookup"><span data-stu-id="5c13d-157">Troubleshoot Internet connectivity and throughput issues</span></span>  <br/> |<span data-ttu-id="5c13d-158">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-158">Applies</span></span>  <br/> |<span data-ttu-id="5c13d-159">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-159">Applies</span></span>  <br/> |<span data-ttu-id="5c13d-160">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-160">Applies</span></span>  <br/> |
|<span data-ttu-id="5c13d-161">異なるエンドポイントへとトラフィックの負荷分散ができるように、Azure Traffic Manager の設計を行います</span><span class="sxs-lookup"><span data-stu-id="5c13d-161">Design Azure Traffic Manager to load balance traffic to different endpoints</span></span>  <br/> ||<span data-ttu-id="5c13d-162">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-162">Applies</span></span>  <br/> |<span data-ttu-id="5c13d-163">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-163">Applies</span></span>  <br/> |
|<span data-ttu-id="5c13d-164">信頼性および冗長性があり、効率的な Azure 仮想ネットワークへの接続を設計します</span><span class="sxs-lookup"><span data-stu-id="5c13d-164">Architect reliable, redundant, and performant connectivity to Azure virtual networks</span></span>  <br/> |||<span data-ttu-id="5c13d-165">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-165">Applies</span></span>  <br/> |
|<span data-ttu-id="5c13d-166">Azure 仮想マシンへのセキュアな接続を設計します</span><span class="sxs-lookup"><span data-stu-id="5c13d-166">Design secure connectivity to Azure virtual machines</span></span>  <br/> |||<span data-ttu-id="5c13d-167">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-167">Applies</span></span>  <br/> |
|<span data-ttu-id="5c13d-168">オンプレミスの場所と仮想ネットワークとの間のルーティングを設計し、実装します</span><span class="sxs-lookup"><span data-stu-id="5c13d-168">Design and implement routing between on-premises locations and virtual networks</span></span>  <br/> |||<span data-ttu-id="5c13d-169">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-169">Applies</span></span>  <br/> |
|<span data-ttu-id="5c13d-170">内部およびインターネットに接続する IT ワークロードのために、負荷分散を設計し、実装します</span><span class="sxs-lookup"><span data-stu-id="5c13d-170">Architect and implement load balancing for internal and Internet-facing IT workloads</span></span>  <br/> |||<span data-ttu-id="5c13d-171">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-171">Applies</span></span>  <br/> |
|<span data-ttu-id="5c13d-172">仮想マシンの接続性およびスループットの問題に関するトラブルシューティングを行います</span><span class="sxs-lookup"><span data-stu-id="5c13d-172">Troubleshoot virtual machine connectivity and throughput issues</span></span>  <br/> |||<span data-ttu-id="5c13d-173">適用</span><span class="sxs-lookup"><span data-stu-id="5c13d-173">Applies</span></span>  <br/> |
   
## <a name="next-step"></a><span data-ttu-id="5c13d-174">次の手順</span><span class="sxs-lookup"><span data-stu-id="5c13d-174">Next step</span></span>

[<span data-ttu-id="5c13d-175">Microsoft クラウド接続の一般的な要素</span><span class="sxs-lookup"><span data-stu-id="5c13d-175">Common elements of Microsoft cloud connectivity</span></span>](common-elements-of-microsoft-cloud-connectivity.md)

## <a name="see-also"></a><span data-ttu-id="5c13d-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c13d-176">See also</span></span>

[<span data-ttu-id="5c13d-177">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="5c13d-177">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="5c13d-178">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="5c13d-178">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)



