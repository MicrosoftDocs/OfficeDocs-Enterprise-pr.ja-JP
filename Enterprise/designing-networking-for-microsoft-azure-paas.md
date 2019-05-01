---
title: Microsoft Azure PaaS のためのネットワーク デザイン
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
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: '概要: Microsoft Azure PaaS へのアクセスのためにネットワークを最適化する方法を理解します。'
ms.openlocfilehash: 49096276a0e8356a11e52bc8765cc796eec32510
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491374"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="8d276-103">Microsoft Azure PaaS のためのネットワーク デザイン</span><span class="sxs-lookup"><span data-stu-id="8d276-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="8d276-104">**概要:** Microsoft Azure PaaS へのアクセスのためにネットワークを最適化する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="8d276-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="8d276-105">Azure PaaS アプリ用のネットワーキングを最適化するには、適切なインターネット帯域幅が必要であり、複数のサイトまたはアプリにまたがるネットワーク トラフィックの分散が必要とされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8d276-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="8d276-106">Azure において組織の PaaS アプリケーションをホストするための手順の計画</span><span class="sxs-lookup"><span data-stu-id="8d276-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

1. <span data-ttu-id="8d276-107">[Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。</span><span class="sxs-lookup"><span data-stu-id="8d276-107">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="8d276-108">[Microsoft SaaS のためのネットワーク デザイン](designing-networking-for-microsoft-saas.md)の「**Microsoft SaaS サービスを利用するためのネットワークの準備の手順**」セクションに記載されている手順 2 から 4 を使用して、インターネット帯域幅を最適化します。</span><span class="sxs-lookup"><span data-stu-id="8d276-108">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="8d276-109">Azure への ExpressRoute 接続が必要かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="8d276-109">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="8d276-110">Web ベースのワークロードに関して、Azure アプリケーション ゲートウェイが必要かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="8d276-110">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="8d276-111">異なるデータ センターの異なるエンドポイントへトラフィックを分散させるため、Azure Traffic Manager が必要かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="8d276-111">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="8d276-112">組織の PaaS アプリケーションのためのインターネット帯域幅</span><span class="sxs-lookup"><span data-stu-id="8d276-112">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="8d276-p101">Azure PaaS においてホストされている組織のアプリケーションは、イントラネット ユーザーのためのインターネット帯域幅を必要とします。次のような 2 つの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="8d276-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="8d276-p102">**オプション 1:** ピーク時の負荷を処理する能力を持つ、インターネット トラフィックに最適化された既存のパイプを使用します。インターネット エッジ、クライアントの使用、および IT 運用上の考慮事項については、[Microsoft SaaS のためのネットワーク デザイン](designing-networking-for-microsoft-saas.md) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d276-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="8d276-117">**オプション 2:** 高帯域幅または低遅延のニーズのため、ExpressRoute を使用して Azure に接続します。</span><span class="sxs-lookup"><span data-stu-id="8d276-117">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="8d276-118">**図 1: Azure PaaS サービスに接続するための接続オプション**</span><span class="sxs-lookup"><span data-stu-id="8d276-118">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![図 1: Azure PaaS サービスの接続オプション](media/Network-Poster/PaaS1.png)
  
<span data-ttu-id="8d276-120">図 1 はインターネット パイプまたは ExpressRoute によって Azure PaaS サービスに接続しているオンプレミスのネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="8d276-120">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="8d276-121">Azure アプリケーション ゲートウェイ</span><span class="sxs-lookup"><span data-stu-id="8d276-121">Azure Application Gateway</span></span>

<span data-ttu-id="8d276-122">アプリケーション レベルのルーティングおよび負荷分散サービスを使用して、Web アプリケーション、クラウド サービス、および仮想マシンのために、Azure における拡張性と可用性の高い Web フロント エンドを構築します。</span><span class="sxs-lookup"><span data-stu-id="8d276-122">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="8d276-123">**図 2: Azure アプリケーション ゲートウェイ**</span><span class="sxs-lookup"><span data-stu-id="8d276-123">**Figure 2: Azure Application Gateway**</span></span>

![図 2:Azure アプリケーション ゲートウェイ サービス](media/Network-Poster/PaaS2.png)
  
<span data-ttu-id="8d276-125">図 2 は、Azure アプリケーション ゲートウェイと、インターネットからのユーザー要求がどのように Azure の Web アプリケーション、クラウド サービス、または仮想マシンに送られるのかを示しています。</span><span class="sxs-lookup"><span data-stu-id="8d276-125">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="8d276-126">アプリケーション ゲートウェイは現在、以下のためにレイヤー 7 のアプリケーションの配信をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8d276-126">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="8d276-127">HTTP 負荷分散</span><span class="sxs-lookup"><span data-stu-id="8d276-127">HTTP load balancing</span></span>
    
- <span data-ttu-id="8d276-128">Cookie ベースのセッション類似性</span><span class="sxs-lookup"><span data-stu-id="8d276-128">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="8d276-129">SSL オフロード</span><span class="sxs-lookup"><span data-stu-id="8d276-129">SSL offload</span></span>
    
<span data-ttu-id="8d276-130">詳細については、[アプリケーション ゲートウェイ](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d276-130">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="8d276-131">Azure トラフィック マネージャー</span><span class="sxs-lookup"><span data-stu-id="8d276-131">Azure Traffic Manager</span></span>

<span data-ttu-id="8d276-132">トラフィックを異なるエンドポイントに分散させます。それには、異なるデータ センターまたは外部エンドポイントに置かれたクラウド サービスまたは Azure Web アプリケーションを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="8d276-132">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="8d276-133">Traffic Manager は、次のルーティング方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="8d276-133">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="8d276-134">**フェールオーバー:** エンドポイントは、同じまたは異なる Azure データ センターにあります。通常はすべてのトラフィックに、プライマリ エンドポイントを使用するとしても、プライマリ エンドポイントまたはバックアップ エンドポイントが使用不可になった場合には、バックアップを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d276-134">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="8d276-135">**ラウンド ロビン:** 同じデータ センター内または異なるデータ センターに置かれたエンドポイントのセットの間で負荷を分散します。</span><span class="sxs-lookup"><span data-stu-id="8d276-135">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="8d276-136">**パフォーマンス:** 複数の地理的な場所にエンドポイントを有し、要求元のクライアントは最小の待機時間となる "最も近い" エンドポイントを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="8d276-136">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="8d276-137">ここでは、3 つの地理的に分散した Web アプリケーションの例を挙げます。</span><span class="sxs-lookup"><span data-stu-id="8d276-137">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="8d276-138">**図 3: Azure Traffic Manager**</span><span class="sxs-lookup"><span data-stu-id="8d276-138">**Figure 3: Azure Traffic Manager**</span></span>

![図 3: Azure Traffic Manager](media/Network-Poster/PaaS3.png)
  
<span data-ttu-id="8d276-p103">図 3 は、Traffic Manager が米国、ヨーロッパ、アジアの 3 つの異なる Azure Web アプリに要求を送信するために使用する基本的なプロセスを示しています。例の中で:</span><span class="sxs-lookup"><span data-stu-id="8d276-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="8d276-142">Web サイト URL に関するユーザーの DNS クエリは Azure Traffic Manager に送信され、それはパフォーマンス ルーティング メソッドに基づいて地域の Web アプリの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="8d276-142">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="8d276-143">ユーザーは、ヨーロッパの地域の Web アプリケーションによってトラフィックを開始します。</span><span class="sxs-lookup"><span data-stu-id="8d276-143">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="8d276-144">詳細については、「[Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d276-144">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="8d276-145">次の手順</span><span class="sxs-lookup"><span data-stu-id="8d276-145">Next step</span></span>

[<span data-ttu-id="8d276-146">Microsoft Azure IaaS のためのネットワークの設計</span><span class="sxs-lookup"><span data-stu-id="8d276-146">Designing networking for Microsoft Azure IaaS</span></span>](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a><span data-ttu-id="8d276-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d276-147">See also</span></span>

[<span data-ttu-id="8d276-148">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="8d276-148">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="8d276-149">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="8d276-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

