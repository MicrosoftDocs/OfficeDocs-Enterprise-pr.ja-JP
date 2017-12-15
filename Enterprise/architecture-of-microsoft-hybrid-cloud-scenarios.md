---
title: "Microsoft ハイブリッド クラウド シナリオのアーキテクチャ"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "概要: Microsoft のハイブリッド クラウド製品のアーキテクチャについて説明します。"
ms.openlocfilehash: 0909964421cecec455ed3c45c965a330501d361c
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="263d1-103">Microsoft ハイブリッド クラウド シナリオのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="263d1-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="263d1-104">**概要:** Microsoft のハイブリッド クラウド製品のアーキテクチャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="263d1-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="263d1-105">アーキテクチャ アプローチを使用して、Microsoft クラウド サービスおよびプラットフォームを使用するハイブリッド クラウド シナリオを計画して実装します。</span><span class="sxs-lookup"><span data-stu-id="263d1-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="263d1-106">**図 1:Microsoft ハイブリッド クラウド スタック**</span><span class="sxs-lookup"><span data-stu-id="263d1-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Microsoft ハイブリッド クラウド スタック](images/Hybrid_Poster/Hybrid_Cloud_Stack.png)
  
<span data-ttu-id="263d1-108">図 1 は、Microsoft ハイブリッド クラウド スタックとそのレイヤーを示しています。レイヤーには、オンプレミス、ネットワーク、ID、アプリとシナリオ、およびクラウド サービスのカテゴリ (Microsoft SaaS、Azure PaaS、Azure PaaS) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="263d1-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="263d1-p101">アプリとシナリオのレイヤーには、このモデルの他の記事で詳しく説明された特定のハイブリッド クラウド シナリオが含まれます。ID、ネットワーク、オンプレミスのレイヤーは、クラウド サービスのカテゴリ (SaaS、PaaS、または PaaS) では共通である場合があります。</span><span class="sxs-lookup"><span data-stu-id="263d1-p101">The Apps and scenarios layer contains the specific hybrid cloud scenarios that are detailed in the additional articles of this model. The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="263d1-111">オンプレミス</span><span class="sxs-lookup"><span data-stu-id="263d1-111">On-premises</span></span>
    
    <span data-ttu-id="263d1-p102">ハイブリッド シナリオのオンプレミス インフラストラクチャには、SharePoint、Exchange、Skype for Business のサーバーと、基幹業務アプリケーションが含まれます。データ ストア (データベース、リスト、ファイル) を含めることもできます。ExpressRoute 接続がない場合、オンプレミス データ ストアへのアクセスは、リバース プロキシを介すか、サーバーまたはデータを DMZ またはエクストラネットでアクセス可能にすることによって許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="263d1-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="263d1-115">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="263d1-115">Network</span></span>
    
    <span data-ttu-id="263d1-p103">Microsoft クラウド プラットフォームとサービスに接続するには、既存のインターネット パイプか ExpressRoute のいずれかを使用します。予測可能なパフォーマンスが重要な場合は、ExpressRoute 接続を使用します。ExpressRoute 接続を使用して、Microsoft SaaS サービス (Office 365 と Dynamics 365)、Azure PaaS サービス、および Azure PaaS サービスに直接接続できます。</span><span class="sxs-lookup"><span data-stu-id="263d1-p103">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute. Use an ExpressRoute connection if predictable performance is important. You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure PaaS services.</span></span>
    
- <span data-ttu-id="263d1-119">ID</span><span class="sxs-lookup"><span data-stu-id="263d1-119">Identity</span></span>
    
    <span data-ttu-id="263d1-p104">クラウド ID インフラストラクチャについては、Microsoft クラウド プラットフォームによって、2 つの方法があります。SaaS および Azure PaaS については、Azure AD にオンプレミス ID インフラストラクチャを統合するか、オンプレミス ID インフラストラクチャまたはサードパーティ ID プロバイダーでフェデレーションを行います。Azure で実行されている VM については、Windows Server AD などのオンプレミス ID インフラストラクチャを、VM が存在する仮想ネットワーク (VNet) に拡張できます。</span><span class="sxs-lookup"><span data-stu-id="263d1-p104">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform. For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers. For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Windows Server AD, to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="263d1-123">3 段階のクラウド導入プロセスのハイブリッド クラウド シナリオ</span><span class="sxs-lookup"><span data-stu-id="263d1-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="263d1-p105">Microsoft を含む多くの企業は、クラウドの採用に 3 段階のアプローチを使用します。ハイブリッド クラウド シナリオは各段階で役割を果たすことができます。</span><span class="sxs-lookup"><span data-stu-id="263d1-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="263d1-126">生産性ワークロードを SaaS に移行する</span><span class="sxs-lookup"><span data-stu-id="263d1-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="263d1-127">現状の生産性ワークロード、またはオンプレミスで維持する必要がある生産性ワークロードについて、ハイブリッド シナリオでは対応するクラウド ワークロードと統合できます。</span><span class="sxs-lookup"><span data-stu-id="263d1-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="263d1-128">Azure PaaS で最新のアプリケーションを開発する</span><span class="sxs-lookup"><span data-stu-id="263d1-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="263d1-129">Azure PaaS ハイブリッド アプリケーションは、オンプレミスのサーバーまたはストレージ リソースを安全に活用できます。</span><span class="sxs-lookup"><span data-stu-id="263d1-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="263d1-130">既存のアプリケーションを Azure IaaS に移動する</span><span class="sxs-lookup"><span data-stu-id="263d1-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="263d1-131">移行 (リフトアンドシフト) およびクラウド内構築シナリオでは、Azure VM で実行されているサーバーベースのアプリケーションが容易なプロビジョニングとスケーリングを提供します。</span><span class="sxs-lookup"><span data-stu-id="263d1-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="263d1-132">See Also</span><span class="sxs-lookup"><span data-stu-id="263d1-132">See Also</span></span>

[<span data-ttu-id="263d1-133">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="263d1-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="263d1-134">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="263d1-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="263d1-135">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="263d1-135">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



