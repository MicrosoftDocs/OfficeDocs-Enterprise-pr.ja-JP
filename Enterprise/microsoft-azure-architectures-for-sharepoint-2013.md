---
title: SharePoint 2013 用の Microsoft Azure アーキテクチャ
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: 'Summary: SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines. Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.'
ms.openlocfilehash: fee388f56faf2b30534d9a56926d9d62a176df19
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997899"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a><span data-ttu-id="2ff47-104">SharePoint 2013 用の Microsoft Azure アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="2ff47-104">Microsoft Azure Architectures for SharePoint 2013</span></span>

<span data-ttu-id="2ff47-105">Azure は SharePoint Server 2013 ソリューションをホストするための優れた環境です。</span><span class="sxs-lookup"><span data-stu-id="2ff47-105">Azure is a good environment for hosting a SharePoint Server 2013 solution.</span></span> <span data-ttu-id="2ff47-106">ほとんどの場合、Microsoft 365 をお勧めしますが、Azure でホストされている SharePoint Server ファームは特定のソリューションに適したオプションになります。</span><span class="sxs-lookup"><span data-stu-id="2ff47-106">In most cases, we recommend Microsoft 365, but a SharePoint Server farm hosted in Azure can be a good option for specific solutions.</span></span> <span data-ttu-id="2ff47-107">この記事では、SharePoint ソリューションが Azure プラットフォームに適合するように設計する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-107">This article describes how to architect SharePoint solutions so they are a good fit in the Azure platform.</span></span> <span data-ttu-id="2ff47-108">次の 2 つのソリューションが例として使用されています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-108">The following two specific solutions are used as examples:</span></span>
  
- [<span data-ttu-id="2ff47-109">Microsoft Azure での SharePoint Server 2013 の障害復旧</span><span class="sxs-lookup"><span data-stu-id="2ff47-109">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [<span data-ttu-id="2ff47-110">SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="2ff47-110">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a><span data-ttu-id="2ff47-111">推奨されている Azure インフラストラクチャ サービスの SharePoint ソリューション</span><span class="sxs-lookup"><span data-stu-id="2ff47-111">Recommended SharePoint solutions for Azure Infrastructure Services</span></span>

<span data-ttu-id="2ff47-112">Azure infrastructure services is a compelling option for hosting SharePoint solutions.</span><span class="sxs-lookup"><span data-stu-id="2ff47-112">Azure infrastructure services is a compelling option for hosting SharePoint solutions.</span></span> <span data-ttu-id="2ff47-113">Some solutions are a better fit for this platform than others.</span><span class="sxs-lookup"><span data-stu-id="2ff47-113">Some solutions are a better fit for this platform than others.</span></span> <span data-ttu-id="2ff47-114">The following table shows recommended solutions.</span><span class="sxs-lookup"><span data-stu-id="2ff47-114">The following table shows recommended solutions.</span></span>
  
|<span data-ttu-id="2ff47-115">**解決方法**</span><span class="sxs-lookup"><span data-stu-id="2ff47-115">**Solution**</span></span>|<span data-ttu-id="2ff47-116">**Azure でそのソリューションが推奨されている理由**</span><span class="sxs-lookup"><span data-stu-id="2ff47-116">**Why this solution is recommended for Azure**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2ff47-117">開発環境とテスト環境</span><span class="sxs-lookup"><span data-stu-id="2ff47-117">Development and test environments</span></span>  <br/> |<span data-ttu-id="2ff47-118">これらの環境を簡単に作成して管理できます。</span><span class="sxs-lookup"><span data-stu-id="2ff47-118">It's easy to create and manage these environments.</span></span>  <br/> |
|<span data-ttu-id="2ff47-119">Azure に対するオンプレミス SharePoint ファームの障害復旧</span><span class="sxs-lookup"><span data-stu-id="2ff47-119">Disaster recovery of on-premises SharePoint farms to Azure</span></span>  <br/> |<span data-ttu-id="2ff47-120">**ホストされているセカンダリ データセンター** 別の地域にあるセカンダリ データセンターに投資するのではなく、Azure を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-120">**Hosted secondary datacenter** Use Azure instead of investing in a secondary datacenter in a different region.</span></span> <br/> <span data-ttu-id="2ff47-121">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment.</span><span class="sxs-lookup"><span data-stu-id="2ff47-121">**Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment.</span></span> <span data-ttu-id="2ff47-122">The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby.</span><span class="sxs-lookup"><span data-stu-id="2ff47-122">The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby.</span></span> <br/> <span data-ttu-id="2ff47-123">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements.</span><span class="sxs-lookup"><span data-stu-id="2ff47-123">**More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements.</span></span> <span data-ttu-id="2ff47-124">Scale in when you no longer need the resources.</span><span class="sxs-lookup"><span data-stu-id="2ff47-124">Scale in when you no longer need the resources.</span></span> <br/> <span data-ttu-id="2ff47-125">「[Microsoft Azure での SharePoint Server 2013 の障害復旧](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2ff47-125">See [SharePoint Server 2013 Disaster Recovery in Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).</span></span>  <br/> |
|<span data-ttu-id="2ff47-126">Microsoft 365 で利用できない機能とスケールを使用する、インターネットに接続されたサイト</span><span class="sxs-lookup"><span data-stu-id="2ff47-126">Internet-facing sites that use features and scale not available in Microsoft 365</span></span>  <br/> |<span data-ttu-id="2ff47-127">**作業の重点** インフラストラクチャの構築ではなく、魅力的なサイトの構築のほうに集中できます。</span><span class="sxs-lookup"><span data-stu-id="2ff47-127">**Focus your efforts** Concentrate on building a great site rather than building infrastructure.</span></span> <br/> <span data-ttu-id="2ff47-128">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need.</span><span class="sxs-lookup"><span data-stu-id="2ff47-128">**Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need.</span></span> <span data-ttu-id="2ff47-129">Dynamic machine allocation is not supported (auto scale).</span><span class="sxs-lookup"><span data-stu-id="2ff47-129">Dynamic machine allocation is not supported (auto scale).</span></span> <br/> <span data-ttu-id="2ff47-130">**Azure Active Directory (AD) の使用** ユーザー アカウントに関して Azure AD を活用します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-130">**Use Azure Active Directory (AD)** Take advantage of Azure AD for customer accounts.</span></span> <br/> <span data-ttu-id="2ff47-131">**Microsoft 365 で利用できない SharePoint 機能の追加**詳細なレポートおよび web 分析を追加します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-131">**Add SharePoint functionality not available in Microsoft 365** Add deep reporting and web analytics.</span></span> <br/> <span data-ttu-id="2ff47-132">「[SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2ff47-132">See [Internet Sites in Microsoft Azure using SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).</span></span>  <br/> |
|<span data-ttu-id="2ff47-133">Microsoft 365 またはオンプレミス環境をサポートするためのアプリファーム</span><span class="sxs-lookup"><span data-stu-id="2ff47-133">App farms to support Microsoft 365 or on-premises environments</span></span>  <br/> |<span data-ttu-id="2ff47-134">**アプリのビルド、テスト、ホスト** Azure で、オンプレミス環境とクラウド環境の両方をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="2ff47-134">**Build, test, and host apps** in Azure to support both on-premises and cloud environments.</span></span> <br/> <span data-ttu-id="2ff47-135">**このロールのホスト** オンプレミス環境用の新しいハードウェアを購入する代わりに、Azure で行います。</span><span class="sxs-lookup"><span data-stu-id="2ff47-135">**Host this role** in Azure instead of buying new hardware for on-premises environments.</span></span> <br/> |
   
<span data-ttu-id="2ff47-136">イントラネットとコラボレーションのソリューション、およびワークロードに関しては、以下の選択肢を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="2ff47-136">For intranet and collaboration solutions and workloads, consider the following options:</span></span>
  
- <span data-ttu-id="2ff47-137">Microsoft 365 がビジネス要件を満たしているかどうか、またはソリューションの一部であるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-137">Determine if Microsoft 365 meets your business requirements or can be part of the solution.</span></span> <span data-ttu-id="2ff47-138">Microsoft 365 には、常に最新の豊富な機能セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-138">Microsoft 365 provides a rich feature set that is always up to date.</span></span>
    
- <span data-ttu-id="2ff47-139">Microsoft 365 がお客様のすべてのビジネス要件を満たしていない場合は、Microsoft コンサルティングサービス (MCS) からの SharePoint 2013 の標準実装を検討してください。</span><span class="sxs-lookup"><span data-stu-id="2ff47-139">If Microsoft 365 does not meet all your business requirements, consider a standard implementation of SharePoint 2013 on premises from Microsoft Consulting Services (MCS).</span></span> <span data-ttu-id="2ff47-140">標準のアーキテクチャは、カスタマイズされたアーキテクチャよりもソリューションの実装が迅速かつ安価で、なおかつ簡単です。</span><span class="sxs-lookup"><span data-stu-id="2ff47-140">A standard architecture can be a quicker, cheaper, and easier solution for you to support than a customized one.</span></span> 
    
- <span data-ttu-id="2ff47-141">標準実装がビジネス要件を満たさない場合には、カスタマイズされたオンプレミスのソリューションを考慮します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-141">If a standard implementation doesn't meet your business requirements, consider a customized on-premises solution.</span></span>
    
- <span data-ttu-id="2ff47-142">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services.</span><span class="sxs-lookup"><span data-stu-id="2ff47-142">If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services.</span></span> <span data-ttu-id="2ff47-143">SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span><span class="sxs-lookup"><span data-stu-id="2ff47-143">SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.</span></span>
    
## <a name="before-you-design-the-azure-environment"></a><span data-ttu-id="2ff47-144">Azure 環境を設計する前に</span><span class="sxs-lookup"><span data-stu-id="2ff47-144">Before you design the Azure environment</span></span>

<span data-ttu-id="2ff47-145">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology.</span><span class="sxs-lookup"><span data-stu-id="2ff47-145">While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology.</span></span> <span data-ttu-id="2ff47-146">Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span><span class="sxs-lookup"><span data-stu-id="2ff47-146">Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:</span></span>
  
- [<span data-ttu-id="2ff47-147">SharePoint 2013 の IT 担当者向けアーキテクチャ設計</span><span class="sxs-lookup"><span data-stu-id="2ff47-147">Architecture design for SharePoint 2013 IT pros</span></span>](https://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [<span data-ttu-id="2ff47-148">Plan for performance and capacity management in SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="2ff47-148">Plan for performance and capacity management in SharePoint Server 2013</span></span>](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a><span data-ttu-id="2ff47-149">Active Directory ドメインの種類の決定</span><span class="sxs-lookup"><span data-stu-id="2ff47-149">Determine the Active Directory domain type</span></span>

<span data-ttu-id="2ff47-150">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup.</span><span class="sxs-lookup"><span data-stu-id="2ff47-150">Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup.</span></span> <span data-ttu-id="2ff47-151">At this time, there are two options for SharePoint solutions in Azure.</span><span class="sxs-lookup"><span data-stu-id="2ff47-151">At this time, there are two options for SharePoint solutions in Azure.</span></span> <span data-ttu-id="2ff47-152">These are described in the following table.</span><span class="sxs-lookup"><span data-stu-id="2ff47-152">These are described in the following table.</span></span>
  
|<span data-ttu-id="2ff47-153">**オプション**</span><span class="sxs-lookup"><span data-stu-id="2ff47-153">**Option**</span></span>|<span data-ttu-id="2ff47-154">**説明**</span><span class="sxs-lookup"><span data-stu-id="2ff47-154">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2ff47-155">専用ドメイン</span><span class="sxs-lookup"><span data-stu-id="2ff47-155">Dedicated domain</span></span>  <br/> |<span data-ttu-id="2ff47-156">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm.</span><span class="sxs-lookup"><span data-stu-id="2ff47-156">You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm.</span></span> <span data-ttu-id="2ff47-157">This is a good choice for public-facing Internet sites.</span><span class="sxs-lookup"><span data-stu-id="2ff47-157">This is a good choice for public-facing Internet sites.</span></span>  <br/> |
|<span data-ttu-id="2ff47-158">クロスプレミス接続を使用したオンプレミス ドメインの拡張</span><span class="sxs-lookup"><span data-stu-id="2ff47-158">Extend the on-premises domain through a cross-premises connection</span></span>  <br/> |<span data-ttu-id="2ff47-159">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises.</span><span class="sxs-lookup"><span data-stu-id="2ff47-159">When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises.</span></span> <span data-ttu-id="2ff47-160">You can take advantage of your on-premises Active Directory and DNS implementation.</span><span class="sxs-lookup"><span data-stu-id="2ff47-160">You can take advantage of your on-premises Active Directory and DNS implementation.</span></span>  <br/> <span data-ttu-id="2ff47-161">オンプレミスのファームとの間でフェールオーバーするために Azure で障害復旧環境を構築するには、クロスプレミス接続が必要になります。</span><span class="sxs-lookup"><span data-stu-id="2ff47-161">A cross-premises connection is required for building a disaster-recovery environment in Azure to fail over to from your on-premises farm.</span></span>  <br/> |
   
<span data-ttu-id="2ff47-162">This article includes design concepts for extending the on-premises domain through a cross-premises connection.</span><span class="sxs-lookup"><span data-stu-id="2ff47-162">This article includes design concepts for extending the on-premises domain through a cross-premises connection.</span></span> <span data-ttu-id="2ff47-163">If your solution uses a dedicated domain, you don't need a cross-premises connection.</span><span class="sxs-lookup"><span data-stu-id="2ff47-163">If your solution uses a dedicated domain, you don't need a cross-premises connection.</span></span>
  
## <a name="design-the-virtual-network"></a><span data-ttu-id="2ff47-164">仮想ネットワークの設計</span><span class="sxs-lookup"><span data-stu-id="2ff47-164">Design the virtual network</span></span>

<span data-ttu-id="2ff47-165">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines.</span><span class="sxs-lookup"><span data-stu-id="2ff47-165">First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines.</span></span> <span data-ttu-id="2ff47-166">The virtual network needs a private IP address space, portions of which you assign to the subnets.</span><span class="sxs-lookup"><span data-stu-id="2ff47-166">The virtual network needs a private IP address space, portions of which you assign to the subnets.</span></span>
  
<span data-ttu-id="2ff47-167">クロスプレミス接続を使用して Azure にオンプレミス ネットワークを拡張する場合は (このことは障害回復環境で必要となります)、オンプレミス環境と他の Azure 仮想ネットワークを含む組織ネットワークの他のどの場所にも使用されていないプライベート アドレス空間を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ff47-167">If you are extending your on-premises network to Azure through a cross-premises connection (required for a disaster recovery environment), you must choose a private address space that is not already in use elsewhere in your organization network, which can include your on-premises environment and other Azure virtual networks.</span></span> 
  
<span data-ttu-id="2ff47-168">**図 1:Azure での仮想ネットワークを使用したオンプレミス環境**</span><span class="sxs-lookup"><span data-stu-id="2ff47-168">**Figure 1: On-premises environment with a virtual network in Azure**</span></span>

![Microsoft Azure virtual network design for a SharePoint solution.](media/OPrrasconWA-AZarch.png)
  
<span data-ttu-id="2ff47-172">この図では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-172">In this diagram:</span></span>
  
- <span data-ttu-id="2ff47-173">A virtual network in Azure is illustrated side-by-side to the on-premises environment.</span><span class="sxs-lookup"><span data-stu-id="2ff47-173">A virtual network in Azure is illustrated side-by-side to the on-premises environment.</span></span> <span data-ttu-id="2ff47-174">The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="2ff47-174">The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="2ff47-175">At this point, the virtual network just includes the subnets and no other architectural elements.</span><span class="sxs-lookup"><span data-stu-id="2ff47-175">At this point, the virtual network just includes the subnets and no other architectural elements.</span></span> <span data-ttu-id="2ff47-176">One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span><span class="sxs-lookup"><span data-stu-id="2ff47-176">One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.</span></span>
    
## <a name="add-cross-premises-connectivity"></a><span data-ttu-id="2ff47-177">クロスプレミス接続の追加</span><span class="sxs-lookup"><span data-stu-id="2ff47-177">Add cross-premises connectivity</span></span>

<span data-ttu-id="2ff47-178">The next deployment step is to create the cross-premises connection (if this applies to your solution).</span><span class="sxs-lookup"><span data-stu-id="2ff47-178">The next deployment step is to create the cross-premises connection (if this applies to your solution).</span></span> <span data-ttu-id="2ff47-179">For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span><span class="sxs-lookup"><span data-stu-id="2ff47-179">For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space.</span></span> 
  
<span data-ttu-id="2ff47-180">クロスプレミス接続を計画する場合は、Azure ゲートウェイと、オンプレミス ゲートウェイ デバイスへの接続を定義して作成します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-180">When you plan for a cross-premises connection, you define and create an Azure gateway and connection to an on-premises gateway device.</span></span>
  
<span data-ttu-id="2ff47-181">**図 2:オンプレミス環境と Azure 間でサイト間接続を提供するための Azure ゲートウェイとオンプレミス ゲートウェイ デバイスの使用**</span><span class="sxs-lookup"><span data-stu-id="2ff47-181">**Figure 2: Using an Azure gateway and an on-premises gateway device to provide site-to-site connectivity between the on-premises environment and Azure**</span></span>

![オンプレミス環境はクロスプレミス接続 (サイト間 VPN 接続または ExpressRoute が可能) を介して Azure 仮想ネットワークに接続されています](media/AZarch-VPNgtwyconnct.png)
  
<span data-ttu-id="2ff47-183">この図では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-183">In this diagram:</span></span>
  
- <span data-ttu-id="2ff47-184">前述の図に加えられた点として、オンプレミス環境がクロスプレミス接続 (サイト間 VPN 接続または ExpressRoute である場合もあります) を介して Azure 仮想ネットワークに接続されています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-184">Adding to the previous diagram, the on-premises environment is connected to the Azure virtual network by a cross-premise connection, which can be a site-to-site VPN connection or ExpressRoute.</span></span>
    
- <span data-ttu-id="2ff47-185">Azure ゲートウェイはゲートウェイ サブネット上に配置します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-185">An Azure gateway is on a gateway subnet.</span></span>
    
- <span data-ttu-id="2ff47-186">オンプレミス環境には、ルーターまたは VPN サーバーなどのゲートウェイ デバイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2ff47-186">The on-premises environment includes a gateway device, such as a router or VPN server.</span></span>
    
<span data-ttu-id="2ff47-187">クロスプレミス仮想ネットワークの計画と作成に関する詳細については、「[オンプレミス ネットワークを Microsoft Azure 仮想ネットワークに接続する](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="2ff47-187">For additional information to plan for and create a cross-premises virtual network, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).</span></span>
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a><span data-ttu-id="2ff47-188">Active Directory ドメインサービス (AD DS) と DNS を追加する</span><span class="sxs-lookup"><span data-stu-id="2ff47-188">Add Active Directory Domain Services (AD DS) and DNS</span></span>

<span data-ttu-id="2ff47-189">Azure における障害復旧の場合、Windows Server AD と DNS をハイブリッド シナリオで展開します。このとき、Windows Server AD は、オンプレミスと Azure 仮想マシンの両方に展開されます。</span><span class="sxs-lookup"><span data-stu-id="2ff47-189">For disaster recovery in Azure, you deploy Windows Server AD and DNS in a hybrid scenario where Windows Server AD is deployed both on-premises and on Azure virtual machines.</span></span>
  
<span data-ttu-id="2ff47-190">**図 3: Active Directory ドメインのハイブリッド構成**</span><span class="sxs-lookup"><span data-stu-id="2ff47-190">**Figure 3: Hybrid Active Directory domain configuration**</span></span>

![Azure の仮想ネットワークと SharePoint ファームのサブネットに配置された 2 つの仮想マシンは、レプリカ ドメイン コントローラーおよび DNS サーバーです](media/AZarch-HyADdomainConfig.png)
  
<span data-ttu-id="2ff47-192">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet.</span><span class="sxs-lookup"><span data-stu-id="2ff47-192">This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet.</span></span> <span data-ttu-id="2ff47-193">These virtual machines are replica domain controllers and DNS servers.</span><span class="sxs-lookup"><span data-stu-id="2ff47-193">These virtual machines are replica domain controllers and DNS servers.</span></span> <span data-ttu-id="2ff47-194">They are an extension of the on-premises Windows Server AD environment.</span><span class="sxs-lookup"><span data-stu-id="2ff47-194">They are an extension of the on-premises Windows Server AD environment.</span></span> 
  
<span data-ttu-id="2ff47-195">The following table provides configuration recommendations for these virtual machines in Azure.</span><span class="sxs-lookup"><span data-stu-id="2ff47-195">The following table provides configuration recommendations for these virtual machines in Azure.</span></span> <span data-ttu-id="2ff47-196">Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span><span class="sxs-lookup"><span data-stu-id="2ff47-196">Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.</span></span>
  
|<span data-ttu-id="2ff47-197">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="2ff47-197">**Item**</span></span>|<span data-ttu-id="2ff47-198">**構成**</span><span class="sxs-lookup"><span data-stu-id="2ff47-198">**Configuration**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2ff47-199">Azure での仮想マシンのサイズ</span><span class="sxs-lookup"><span data-stu-id="2ff47-199">Virtual machine size in Azure</span></span>  <br/> |<span data-ttu-id="2ff47-200">標準層の A1 または A2 サイズ</span><span class="sxs-lookup"><span data-stu-id="2ff47-200">A1 or A2 size in the Standard tier</span></span>  <br/> |
|<span data-ttu-id="2ff47-201">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="2ff47-201">Operating system</span></span>  <br/> |<span data-ttu-id="2ff47-202">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2ff47-202">Windows Server 2012 R2</span></span>  <br/> |
|<span data-ttu-id="2ff47-203">Active Directory ロール</span><span class="sxs-lookup"><span data-stu-id="2ff47-203">Active Directory role</span></span>  <br/> |<span data-ttu-id="2ff47-204">AD DS domain controller designated as a global catalog server.</span><span class="sxs-lookup"><span data-stu-id="2ff47-204">AD DS domain controller designated as a global catalog server.</span></span> <span data-ttu-id="2ff47-205">This configuration reduces egress traffic across the cross-premises connection.</span><span class="sxs-lookup"><span data-stu-id="2ff47-205">This configuration reduces egress traffic across the cross-premises connection.</span></span>  <br/> <span data-ttu-id="2ff47-206">変更率の高いマルチドメイン環境の場合 (一般的ではありません)、オンプレミスのドメイン コントローラーが、Azure 内のグローバル カタログ サーバーと同期しないように構成して、レプリケーション トラフィックを削減します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-206">In a multidomain environment with high rates of change (this is not common), configure domain controllers on premises not to sync with the global catalog servers in Azure, to reduce replication traffic.</span></span>  <br/> |
|<span data-ttu-id="2ff47-207">DNS ロール</span><span class="sxs-lookup"><span data-stu-id="2ff47-207">DNS role</span></span>  <br/> |<span data-ttu-id="2ff47-208">ドメイン コントローラーで DNS サーバー サービスをインストールして構成します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-208">Install and configure the DNS Server service on the domain controllers.</span></span>  <br/> |
|<span data-ttu-id="2ff47-209">データ ディスク</span><span class="sxs-lookup"><span data-stu-id="2ff47-209">Data disks</span></span>  <br/> |<span data-ttu-id="2ff47-210">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks.</span><span class="sxs-lookup"><span data-stu-id="2ff47-210">Place the Active Directory database, logs, and SYSVOL on additional Azure data disks.</span></span> <span data-ttu-id="2ff47-211">Do not place these on the operating system disk or the temporary disks provided by Azure.</span><span class="sxs-lookup"><span data-stu-id="2ff47-211">Do not place these on the operating system disk or the temporary disks provided by Azure.</span></span>  <br/> |
|<span data-ttu-id="2ff47-212">IP アドレス</span><span class="sxs-lookup"><span data-stu-id="2ff47-212">IP addresses</span></span>  <br/> |<span data-ttu-id="2ff47-213">静的 IP アドレスを使用して仮想ネットワークを構成し、ドメイン コントローラーの構成後にこれらのアドレスを仮想ネットワーク内の仮想マシンに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="2ff47-213">Use static IP addresses and configure the virtual network to assign these addresses to the virtual machines in the virtual network after the domain controllers have been configured.</span></span>  <br/> |
   
> [!IMPORTANT]
> <span data-ttu-id="2ff47-214">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681).</span><span class="sxs-lookup"><span data-stu-id="2ff47-214">Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681).</span></span> <span data-ttu-id="2ff47-215">These help you determine if a different architecture or different configuration settings are needed for your solution.</span><span class="sxs-lookup"><span data-stu-id="2ff47-215">These help you determine if a different architecture or different configuration settings are needed for your solution.</span></span> 
  
## <a name="add-the-sharepoint-farm"></a><span data-ttu-id="2ff47-216">SharePoint ファームの追加</span><span class="sxs-lookup"><span data-stu-id="2ff47-216">Add the SharePoint farm</span></span>

<span data-ttu-id="2ff47-217">該当するサブネット上の層に SharePoint ファームの仮想マシンを配置します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-217">Place the virtual machines of the SharePoint farm in tiers on the appropriate subnets.</span></span>
  
<span data-ttu-id="2ff47-218">**図 4: SharePoint 仮想マシンの配置**</span><span class="sxs-lookup"><span data-stu-id="2ff47-218">**Figure 4: Placement of SharePoint virtual machines**</span></span>

![SharePoint ファーム サブネット内の Azure 仮想ネットワークに追加された、データベース サーバーと SharePoint サーバーの役割](media/AZarch-SPVMsinCloudSer.png)
  
<span data-ttu-id="2ff47-220">この図は前の図に基づいて作成されていて、それぞれの層で SharePoint ファーム サーバー ロールが追加されています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-220">This diagram builds on the previous diagrams by adding the SharePoint farm server roles in their respective tiers.</span></span>
  
- <span data-ttu-id="2ff47-221">SQL Server を実行する 2 つのデータベース仮想マシンによってデータベース層が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2ff47-221">Two database virtual machines running SQL Server create the database tier.</span></span>
    
- <span data-ttu-id="2ff47-222">それぞれのロール (フロント エンド サーバー、分散キャッシュ サーバー、バック エンド サーバー) ごとに、SharePoint Server 2013 を実行する 2 つの仮想マシンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-222">Two virtual machines running SharePoint Server 2013 for each of the following tiers: front end servers, distributed cache servers, and back end servers.</span></span>
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a><span data-ttu-id="2ff47-223">可用性セットと障害ドメイン用のサーバー ロールの設計と調整</span><span class="sxs-lookup"><span data-stu-id="2ff47-223">Design and fine tune server roles for availability sets and fault domains</span></span>

<span data-ttu-id="2ff47-224">A fault domain is a grouping of hardware in which role instances run.</span><span class="sxs-lookup"><span data-stu-id="2ff47-224">A fault domain is a grouping of hardware in which role instances run.</span></span> <span data-ttu-id="2ff47-225">Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time.</span><span class="sxs-lookup"><span data-stu-id="2ff47-225">Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time.</span></span> <span data-ttu-id="2ff47-226">Or, they can fail at the same time because they share the same rack.</span><span class="sxs-lookup"><span data-stu-id="2ff47-226">Or, they can fail at the same time because they share the same rack.</span></span> <span data-ttu-id="2ff47-227">To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain.</span><span class="sxs-lookup"><span data-stu-id="2ff47-227">To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain.</span></span> <span data-ttu-id="2ff47-228">If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span><span class="sxs-lookup"><span data-stu-id="2ff47-228">If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.</span></span>
  
<span data-ttu-id="2ff47-229">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set.</span><span class="sxs-lookup"><span data-stu-id="2ff47-229">When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set.</span></span> <span data-ttu-id="2ff47-230">This ensures that your virtual machines are spread across multiple fault domains.</span><span class="sxs-lookup"><span data-stu-id="2ff47-230">This ensures that your virtual machines are spread across multiple fault domains.</span></span>
  
<span data-ttu-id="2ff47-231">**図 5: SharePoint ファーム層の高可用性を確保するための Azure 可用性セットの使用**</span><span class="sxs-lookup"><span data-stu-id="2ff47-231">**Figure 5: Use Azure Availability Sets to provide high availability for the SharePoint farm tiers**</span></span>

![SharePoint 2013 ソリューションのための Azure インフラストラクチャ内の可用性セットの構成](media/AZenv-WinAzureAvailSetsHA.png)
  
<span data-ttu-id="2ff47-233">This diagram calls out the configuration of availability sets within the Azure infrastructure.</span><span class="sxs-lookup"><span data-stu-id="2ff47-233">This diagram calls out the configuration of availability sets within the Azure infrastructure.</span></span> <span data-ttu-id="2ff47-234">Each of the following roles share a separate availability set:</span><span class="sxs-lookup"><span data-stu-id="2ff47-234">Each of the following roles share a separate availability set:</span></span>
  
- <span data-ttu-id="2ff47-235">Active Directory と DNS</span><span class="sxs-lookup"><span data-stu-id="2ff47-235">Active Directory and DNS</span></span>
    
- <span data-ttu-id="2ff47-236">データベース</span><span class="sxs-lookup"><span data-stu-id="2ff47-236">Database</span></span>
    
- <span data-ttu-id="2ff47-237">バック エンド</span><span class="sxs-lookup"><span data-stu-id="2ff47-237">Back end</span></span>
    
- <span data-ttu-id="2ff47-238">分散キャッシュ</span><span class="sxs-lookup"><span data-stu-id="2ff47-238">Distribute cache</span></span>
    
- <span data-ttu-id="2ff47-239">フロント エンド</span><span class="sxs-lookup"><span data-stu-id="2ff47-239">Front end</span></span>
    
<span data-ttu-id="2ff47-240">The SharePoint farm might need to be fine tuned in the Azure platform.</span><span class="sxs-lookup"><span data-stu-id="2ff47-240">The SharePoint farm might need to be fine tuned in the Azure platform.</span></span> <span data-ttu-id="2ff47-241">To ensure high availability of all components, ensure that the server roles are all configured identically.</span><span class="sxs-lookup"><span data-stu-id="2ff47-241">To ensure high availability of all components, ensure that the server roles are all configured identically.</span></span>
  
<span data-ttu-id="2ff47-242">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals.</span><span class="sxs-lookup"><span data-stu-id="2ff47-242">Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals.</span></span> <span data-ttu-id="2ff47-243">This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span><span class="sxs-lookup"><span data-stu-id="2ff47-243">This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).</span></span>
  
<span data-ttu-id="2ff47-244">**図 6: 3 層ファームにおけるキャパシティとパフォーマンスの目標に関する計画例**</span><span class="sxs-lookup"><span data-stu-id="2ff47-244">**Figure 6: Planning example for capacity and performance goals in a three-tier farm**</span></span>

![特定の容量とパフォーマンスの目標を達成するコンポーネント割り当てを含む標準的な SharePoint 2013 のインターネット サイトのアーキテクチャ](media/AZarch-CapPerfexmpArch.png)
  
<span data-ttu-id="2ff47-246">この図では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-246">In this diagram:</span></span>
  
- <span data-ttu-id="2ff47-247">3 層ファームは、Web サーバー、アプリケーション サーバー、データベース サーバーで表されます。</span><span class="sxs-lookup"><span data-stu-id="2ff47-247">A three-tier farm is represented: web servers, application servers, and database servers.</span></span>
    
- <span data-ttu-id="2ff47-248">3 つの Web サーバーは複数のコンポーネントを含んでおり、同一に構成されています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-248">The three web servers are configured identically with multiple components.</span></span>
    
- <span data-ttu-id="2ff47-249">2 つのデータベース サーバーは同一に構成されています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-249">The two database servers are configured identically.</span></span>
    
- <span data-ttu-id="2ff47-250">The three application servers are not configured identically.</span><span class="sxs-lookup"><span data-stu-id="2ff47-250">The three application servers are not configured identically.</span></span> <span data-ttu-id="2ff47-251">These server roles require fine tuning for availability sets in Azure.</span><span class="sxs-lookup"><span data-stu-id="2ff47-251">These server roles require fine tuning for availability sets in Azure.</span></span>
    
<span data-ttu-id="2ff47-252">アプリケーション サーバー層について詳しく見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="2ff47-252">Let's look closer at the application server tier.</span></span>
  
<span data-ttu-id="2ff47-253">**図 7: 調整前のアプリケーション サーバー層**</span><span class="sxs-lookup"><span data-stu-id="2ff47-253">**Figure 7: Application server tier before fine tuning**</span></span>

![Microsoft Azure 可用性セットのために調整する前の SharePoint Server 2013 アプリケーション サーバー層の例](media/AZarch-AppServtierBefore.png)
  
<span data-ttu-id="2ff47-255">この図では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-255">In this diagram:</span></span>
  
- <span data-ttu-id="2ff47-256">3 つのサーバーがアプリケーション層に含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-256">Three servers are included in the application tier.</span></span>
    
- <span data-ttu-id="2ff47-257">最初のサーバーには 4 つのコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-257">The first server includes four components.</span></span>
    
- <span data-ttu-id="2ff47-258">2　番目のサーバーには、3 つのコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-258">The second server includes three components.</span></span>
    
- <span data-ttu-id="2ff47-259">3 番目のサーバーには、2 つのコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-259">The third server includes two components.</span></span>
    
<span data-ttu-id="2ff47-260">You determine the number of components by the performance and capacity targets for the farm.</span><span class="sxs-lookup"><span data-stu-id="2ff47-260">You determine the number of components by the performance and capacity targets for the farm.</span></span> <span data-ttu-id="2ff47-261">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span><span class="sxs-lookup"><span data-stu-id="2ff47-261">To adapt this architecture for Azure, we'll replicate the four components across all three servers.</span></span> <span data-ttu-id="2ff47-262">This increases the number of components beyond what is necessary for performance and capacity.</span><span class="sxs-lookup"><span data-stu-id="2ff47-262">This increases the number of components beyond what is necessary for performance and capacity.</span></span> <span data-ttu-id="2ff47-263">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span><span class="sxs-lookup"><span data-stu-id="2ff47-263">The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.</span></span>
  
<span data-ttu-id="2ff47-264">**図 8: 調整後のアプリケーション サーバー層**</span><span class="sxs-lookup"><span data-stu-id="2ff47-264">**Figure 8: Application server tier after fine tuning**</span></span>

![Microsoft Azure 可用性セットのために調整した後の SharePoint Server 2013 アプリケーション サーバー層の例](media/AZarch-AppServtierAfter.png)
  
<span data-ttu-id="2ff47-266">この図は、同じ 4 つのコンポーネントを含み、同一に構成されている 3 つのアプリケーション サーバーすべてを示しています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-266">This diagram shows all three application servers configured identically with the same four components.</span></span>
  
<span data-ttu-id="2ff47-267">SharePoint ファームの各層に可用性セットを追加すると、実装作業が完了します。</span><span class="sxs-lookup"><span data-stu-id="2ff47-267">When we add availability sets to the tiers of the SharePoint farm, the implementation is complete.</span></span>
  
<span data-ttu-id="2ff47-268">**図 9:Azure インフラストラクチャ サービスに実装された SharePoint ファーム**</span><span class="sxs-lookup"><span data-stu-id="2ff47-268">**Figure 9: The completed SharePoint farm in Azure infrastructure services**</span></span>

![仮想ネットワーク、クロスプレミス接続、サブネット、VM、および可用性の設定を含む Azure インフラストラクチャ サービスの SharePoint 2013 ファームの例](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
<span data-ttu-id="2ff47-270">この図は、Azure インフラストラクチャ サービスに実装された、各層内のサーバー用の障害ドメインを提供する可用性セットを備えた SharePoint ファームを示しています。</span><span class="sxs-lookup"><span data-stu-id="2ff47-270">This diagram shows the SharePoint farm implemented in Azure infrastructure services, with availability sets to provide fault domains for the servers in each tier.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2ff47-271">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ff47-271">See Also</span></span>

[<span data-ttu-id="2ff47-272">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="2ff47-272">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)
  
[<span data-ttu-id="2ff47-273">SharePoint Server 2013 を使用した Microsoft Azure のインターネット サイト</span><span class="sxs-lookup"><span data-stu-id="2ff47-273">Internet Sites in Microsoft Azure using SharePoint Server 2013</span></span>](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[<span data-ttu-id="2ff47-274">Microsoft Azure での SharePoint Server 2013 の障害復旧</span><span class="sxs-lookup"><span data-stu-id="2ff47-274">SharePoint Server 2013 Disaster Recovery in Microsoft Azure</span></span>](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


