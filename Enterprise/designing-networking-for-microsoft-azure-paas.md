---
title: "Microsoft Azure PaaS のためのネットワーク デザイン"
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
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: "概要: Microsoft Azure PaaS へのアクセスのためにネットワークを最適化する方法を理解します。"
ms.openlocfilehash: 8ea344b5c18f9224b1a939a05c6e5a4eda2eeec5
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="d81e0-103">Microsoft Azure PaaS のためのネットワーク デザイン</span><span class="sxs-lookup"><span data-stu-id="d81e0-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="d81e0-104">**概要:** Microsoft Azure PaaS へのアクセスのためにネットワークを最適化する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="d81e0-105">Azure PaaS アプリ用のネットワーキングを最適化するには、適切なインターネット帯域幅が必要であり、複数のサイトまたはアプリにまたがるネットワーク トラフィックの分散が必要とされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d81e0-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="d81e0-106">Azure において組織の PaaS アプリケーションをホストするための手順の計画</span><span class="sxs-lookup"><span data-stu-id="d81e0-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

<span data-ttu-id="d81e0-107">ここにセクション本文を挿入します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-107">Insert section body here.</span></span>
  
1. <span data-ttu-id="d81e0-108">[Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。</span><span class="sxs-lookup"><span data-stu-id="d81e0-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="d81e0-109">[Microsoft SaaS のためのネットワーク デザイン](designing-networking-for-microsoft-saas.md)の「**Microsoft SaaS サービスを利用するためのネットワークの準備の手順**」セクションに記載されている手順 2 から 4 を使用して、インターネット帯域幅を最適化します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-109">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="d81e0-110">Azure への ExpressRoute 接続が必要かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-110">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="d81e0-111">Web ベースのワークロードに関して、Azure アプリケーション ゲートウェイが必要かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-111">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="d81e0-112">異なるデータ センターの異なるエンドポイントへトラフィックを分散させるため、Azure Traffic Manager が必要かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-112">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="d81e0-113">組織の PaaS アプリケーションのためのインターネット帯域幅</span><span class="sxs-lookup"><span data-stu-id="d81e0-113">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="d81e0-p101">Azure PaaS においてホストされている組織のアプリケーションは、イントラネット ユーザーのためのインターネット帯域幅を必要とします。次のような 2 つの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="d81e0-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="d81e0-p102">**オプション 1:** ピーク時の負荷を処理する能力を持つ、インターネット トラフィックに最適化された既存のパイプを使用します。インターネット エッジ、クライアントの使用、および IT 運用上の考慮事項については、[Microsoft SaaS のためのネットワーク デザイン](designing-networking-for-microsoft-saas.md) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d81e0-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="d81e0-118">**オプション 2:** 高帯域幅または低遅延のニーズのため、ExpressRoute を使用して Azure に接続します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-118">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="d81e0-119">**図 1: Azure PaaS サービスに接続するための接続オプション**</span><span class="sxs-lookup"><span data-stu-id="d81e0-119">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![図 1: Azure PaaS サービスの接続オプション](images/Network_Poster/PaaS1.png)
  
<span data-ttu-id="d81e0-121">図 1 はインターネット パイプまたは ExpressRoute によって Azure PaaS サービスに接続しているオンプレミスのネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="d81e0-121">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="d81e0-122">Azure アプリケーション ゲートウェイ</span><span class="sxs-lookup"><span data-stu-id="d81e0-122">Azure Application Gateway</span></span>

<span data-ttu-id="d81e0-123">アプリケーション レベルのルーティングおよび負荷分散サービスを使用して、Web アプリケーション、クラウド サービス、および仮想マシンのために、Azure における拡張性と可用性の高い Web フロント エンドを構築します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-123">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="d81e0-124">**図 2: Azure アプリケーション ゲートウェイ**</span><span class="sxs-lookup"><span data-stu-id="d81e0-124">**Figure 2: Azure Application Gateway**</span></span>

![図 2:Azure アプリケーション ゲートウェイ サービス](images/Network_Poster/PaaS2.png)
  
<span data-ttu-id="d81e0-126">図 2 は、Azure アプリケーション ゲートウェイと、インターネットからのユーザー要求がどのように Azure の Web アプリケーション、クラウド サービス、または仮想マシンに送られるのかを示しています。</span><span class="sxs-lookup"><span data-stu-id="d81e0-126">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="d81e0-127">アプリケーション ゲートウェイは現在、以下のためにレイヤー 7 のアプリケーションの配信をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d81e0-127">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="d81e0-128">HTTP 負荷分散</span><span class="sxs-lookup"><span data-stu-id="d81e0-128">HTTP load balancing</span></span>
    
- <span data-ttu-id="d81e0-129">Cookie ベースのセッション類似性</span><span class="sxs-lookup"><span data-stu-id="d81e0-129">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="d81e0-130">SSL オフロード</span><span class="sxs-lookup"><span data-stu-id="d81e0-130">SSL offload</span></span>
    
<span data-ttu-id="d81e0-131">詳細については、[アプリケーション ゲートウェイ](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d81e0-131">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="d81e0-132">Azure トラフィック マネージャー</span><span class="sxs-lookup"><span data-stu-id="d81e0-132">Azure Traffic Manager</span></span>

<span data-ttu-id="d81e0-133">トラフィックを異なるエンドポイントに分散させます。それには、異なるデータ センターまたは外部エンドポイントに置かれたクラウド サービスまたは Azure Web アプリケーションを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d81e0-133">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="d81e0-134">Traffic Manager は、次のルーティング方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-134">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="d81e0-135">**フェールオーバー:** エンドポイントは、同じまたは異なる Azure データ センターにあります。通常はすべてのトラフィックに、プライマリ エンドポイントを使用するとしても、プライマリ エンドポイントまたはバックアップ エンドポイントが使用不可になった場合には、バックアップを提供します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-135">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="d81e0-136">**ラウンド ロビン:** 同じデータ センター内または異なるデータ センターに置かれたエンドポイントのセットの間で負荷を分散します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-136">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="d81e0-137">**パフォーマンス:** 複数の地理的な場所にエンドポイントを有し、要求元のクライアントは最小の待機時間となる "最も近い" エンドポイントを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="d81e0-137">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="d81e0-138">ここでは、3 つの地理的に分散した Web アプリケーションの例を挙げます。</span><span class="sxs-lookup"><span data-stu-id="d81e0-138">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="d81e0-139">**図 3: Azure Traffic Manager**</span><span class="sxs-lookup"><span data-stu-id="d81e0-139">**Figure 3: Azure Traffic Manager**</span></span>

![図 3: Azure Traffic Manager](images/Network_Poster/PaaS3.png)
  
<span data-ttu-id="d81e0-p103">図 3 は、Traffic Manager が米国、ヨーロッパ、アジアの 3 つの異なる Azure Web アプリに要求を送信するために使用する基本的なプロセスを示しています。例の中で:</span><span class="sxs-lookup"><span data-stu-id="d81e0-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="d81e0-143">Web サイト URL に関するユーザーの DNS クエリは Azure Traffic Manager に送信され、それはパフォーマンス ルーティング メソッドに基づいて地域の Web アプリの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-143">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="d81e0-144">ユーザーは、ヨーロッパの地域の Web アプリケーションによってトラフィックを開始します。</span><span class="sxs-lookup"><span data-stu-id="d81e0-144">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="d81e0-145">詳細については、「[Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d81e0-145">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d81e0-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="d81e0-146">See Also</span></span>

[<span data-ttu-id="d81e0-147">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="d81e0-147">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="d81e0-148">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="d81e0-148">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="d81e0-149">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="d81e0-149">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



