---
title: Microsoft ハイブリッド クラウドのシナリオのアーキテクチャ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: '概要: Microsoft のハイブリッド クラウド製品のアーキテクチャについて説明します。'
ms.openlocfilehash: f5493c0f008b22af412ee95ccb8b7581eee71476
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490270"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="c3c0c-103">Microsoft ハイブリッド クラウド シナリオのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="c3c0c-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="c3c0c-104">**概要:** Microsoft のハイブリッド クラウド製品のアーキテクチャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="c3c0c-105">アーキテクチャ アプローチを使用して、Microsoft クラウド サービスおよびプラットフォームを使用するハイブリッド クラウド シナリオを計画して実装します。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="c3c0c-106">**図 1:Microsoft ハイブリッド クラウド スタック**</span><span class="sxs-lookup"><span data-stu-id="c3c0c-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![Microsoft ハイブリッド クラウド スタック](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
<span data-ttu-id="c3c0c-108">図 1 は、Microsoft ハイブリッド クラウド スタックとそのレイヤーを示しています。レイヤーには、オンプレミス、ネットワーク、ID、アプリとシナリオ、およびクラウド サービスのカテゴリ (Microsoft SaaS、Azure PaaS、Azure PaaS) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="c3c0c-109">アプリとシナリオのレイヤーには、このモデルの追加記事で詳しく説明されている特定のハイブリッドクラウドのシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-109">The Apps and scenarios layer has the specific hybrid cloud scenarios that are detailed in the additional articles of this model.</span></span> <span data-ttu-id="c3c0c-110">ID、ネットワーク、オンプレミスのレイヤーは、クラウド サービスのカテゴリ (SaaS、PaaS、または PaaS) では共通である場合があります。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-110">The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="c3c0c-111">オンプレミス</span><span class="sxs-lookup"><span data-stu-id="c3c0c-111">On-premises</span></span>
    
    <span data-ttu-id="c3c0c-p102">ハイブリッド シナリオのオンプレミス インフラストラクチャには、SharePoint、Exchange、Skype for Business のサーバーと、基幹業務アプリケーションが含まれます。データ ストア (データベース、リスト、ファイル) を含めることもできます。ExpressRoute 接続がない場合、オンプレミス データ ストアへのアクセスは、リバース プロキシを介すか、サーバーまたはデータを DMZ またはエクストラネットでアクセス可能にすることによって許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="c3c0c-115">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="c3c0c-115">Network</span></span>
    
    <span data-ttu-id="c3c0c-116">Microsoft クラウド プラットフォームとサービスに接続するには、既存のインターネット パイプか ExpressRoute のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-116">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute.</span></span> <span data-ttu-id="c3c0c-117">予測可能なパフォーマンスが重要な場合は、ExpressRoute 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-117">Use an ExpressRoute connection if predictable performance is important.</span></span> <span data-ttu-id="c3c0c-118">1つの ExpressRoute 接続を使用して、Microsoft SaaS services (Office 365 および Dynamics 365)、azure PaaS サービス、および azure IaaS services に直接接続することができます。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-118">You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure IaaS services.</span></span>
    
- <span data-ttu-id="c3c0c-119">ID</span><span class="sxs-lookup"><span data-stu-id="c3c0c-119">Identity</span></span>
    
    <span data-ttu-id="c3c0c-120">クラウド ID インフラストラクチャについては、Microsoft クラウド プラットフォームによって、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-120">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform.</span></span> <span data-ttu-id="c3c0c-121">SaaS および Azure PaaS については、Azure AD にオンプレミス ID インフラストラクチャを統合するか、オンプレミス ID インフラストラクチャまたはサードパーティ ID プロバイダーでフェデレーションを行います。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-121">For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers.</span></span> <span data-ttu-id="c3c0c-122">Azure で実行されている vm では、Active Directory ドメインサービス (AD DS) などのオンプレミスの id インフラストラクチャを、vm が存在する仮想ネットワーク (vnet) に拡張できます。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-122">For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Active Directory Domain Services (AD DS), to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="c3c0c-123">3 段階のクラウド導入プロセスのハイブリッド クラウド シナリオ</span><span class="sxs-lookup"><span data-stu-id="c3c0c-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="c3c0c-p105">Microsoft を含む多くの企業は、クラウドの採用に 3 段階のアプローチを使用します。ハイブリッド クラウド シナリオは各段階で役割を果たすことができます。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="c3c0c-126">生産性ワークロードを SaaS に移行する</span><span class="sxs-lookup"><span data-stu-id="c3c0c-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="c3c0c-127">現状の生産性ワークロード、またはオンプレミスで維持する必要がある生産性ワークロードについて、ハイブリッド シナリオでは対応するクラウド ワークロードと統合できます。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="c3c0c-128">Azure PaaS で最新のアプリケーションを開発する</span><span class="sxs-lookup"><span data-stu-id="c3c0c-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="c3c0c-129">Azure PaaS ハイブリッド アプリケーションは、オンプレミスのサーバーまたはストレージ リソースを安全に活用できます。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="c3c0c-130">既存のアプリケーションを Azure IaaS に移動する</span><span class="sxs-lookup"><span data-stu-id="c3c0c-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="c3c0c-131">移行 (リフトアンドシフト) およびクラウド内構築シナリオでは、Azure VM で実行されているサーバーベースのアプリケーションが容易なプロビジョニングとスケーリングを提供します。</span><span class="sxs-lookup"><span data-stu-id="c3c0c-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="c3c0c-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3c0c-132">See Also</span></span>

[<span data-ttu-id="c3c0c-133">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="c3c0c-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="c3c0c-134">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="c3c0c-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

