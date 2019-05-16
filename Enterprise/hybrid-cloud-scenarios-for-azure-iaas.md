---
title: Azure IaaS のハイブリッド クラウドのシナリオ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: '概要: Microsoft のサービスとしてのインフラストラクチャ (IaaS) ベースの Azure のクラウド製品のハイブリッドアーキテクチャとシナリオについて説明します。'
ms.openlocfilehash: 429af408ca3f21fe667b36cdb9767d3916a6b1a4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067353"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="4b474-103">Azure IaaS のハイブリッド クラウドのシナリオ</span><span class="sxs-lookup"><span data-stu-id="4b474-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="4b474-104">**概要:** Microsoft のサービスとしてのインフラストラクチャ (IaaS) ベースの Azure のクラウド製品のハイブリッドアーキテクチャとシナリオについて理解します。</span><span class="sxs-lookup"><span data-stu-id="4b474-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="4b474-105">クロスプレミスの Azure 仮想ネットワーク (Vnet) で実行されている IT ワークロードをホストすることにより、オンプレミスのコンピューティングおよび id インフラストラクチャをクラウドに拡張します。</span><span class="sxs-lookup"><span data-stu-id="4b474-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="4b474-106">Azure IaaS ハイブリッドシナリオのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="4b474-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="4b474-107">図1は、Microsoft IaaS ベースの Azure のハイブリッドシナリオのアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="4b474-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="4b474-108">**図 1: Microsoft IaaS ベースの Azure 内ハイブリッドシナリオ**</span><span class="sxs-lookup"><span data-stu-id="4b474-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Azure での Microsoft IaaS ベースのハイブリッドシナリオ](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="4b474-110">アーキテクチャの各レイヤーについて:</span><span class="sxs-lookup"><span data-stu-id="4b474-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="4b474-111">アプリとシナリオ</span><span class="sxs-lookup"><span data-stu-id="4b474-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="4b474-112">IT ワークロードは、通常、Azure 仮想マシン (Vm) で構成された複数層の高可用性アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="4b474-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="4b474-113">ID</span><span class="sxs-lookup"><span data-stu-id="4b474-113">Identity</span></span>
    
    <span data-ttu-id="4b474-114">Active Directory ドメインサービス (AD DS) ドメインコントローラーなどの id サーバーを、Azure Vnet で実行されているローカル認証用のサーバーのセットに追加します。</span><span class="sxs-lookup"><span data-stu-id="4b474-114">Add identity servers, such as Active Directory Domain Services (AD DS) domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="4b474-115">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="4b474-115">Network</span></span>
    
    <span data-ttu-id="4b474-116">インターネット経由でのサイト間 VPN 接続、または Azure IaaS に対するプライベートピアリングを備えた ExpressRoute 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b474-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="4b474-117">社内</span><span class="sxs-lookup"><span data-stu-id="4b474-117">On-premises</span></span>
    
    <span data-ttu-id="4b474-118">Azure で実行されている id サーバーと同期された id サーバーを含みます。</span><span class="sxs-lookup"><span data-stu-id="4b474-118">Contains identity servers that are synchronized with the identity servers running in Azure.</span></span> <span data-ttu-id="4b474-119">また、ストレージやシステム管理インフラストラクチャなど、Azure で実行されている Vm がアクセスできるリソースを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="4b474-119">Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="directory-synchronization-server-for-office-365"></a><span data-ttu-id="4b474-120">Office 用ディレクトリ同期サーバー365</span><span class="sxs-lookup"><span data-stu-id="4b474-120">Directory synchronization server for Office 365</span></span>

<span data-ttu-id="4b474-121">図2に示されているように、Azure VNet からディレクトリ同期サーバーを実行することは、コンピューティングおよび id インフラストラクチャをクラウドに拡張する例です。</span><span class="sxs-lookup"><span data-stu-id="4b474-121">Running your directory synchronization server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="4b474-122">**図 2: Azure IaaS の Office 365 用のディレクトリ同期サーバー**</span><span class="sxs-lookup"><span data-stu-id="4b474-122">**Figure 2: Directory synchronization server for Office 365 in Azure IaaS**</span></span>

![Azure IaaS の Office 365 用のディレクトリ同期サーバー](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="4b474-124">図2では、社内ネットワークが AD DS インフラストラクチャをホストしており、プロキシサーバーとルーターがエッジに配置されています。</span><span class="sxs-lookup"><span data-stu-id="4b474-124">In Figure 2, an on-premises network hosts a AD DS infrastructure, with a proxy server and a router at its edge.</span></span> <span data-ttu-id="4b474-125">ルーターは、サイト間 VPN または ExpressRoute 接続を使用して Azure VNet のエッジにある Azure ゲートウェイに接続します。</span><span class="sxs-lookup"><span data-stu-id="4b474-125">The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="4b474-126">VNet 内で、ディレクトリ同期サーバーは Azure AD Connect を実行します。</span><span class="sxs-lookup"><span data-stu-id="4b474-126">Inside the VNet, a directory synchronization server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="4b474-127">Office 365 用のディレクトリ同期サーバーは、AD DS 内のアカウントの一覧を Office 365 サブスクリプションの Azure AD テナントと同期します。</span><span class="sxs-lookup"><span data-stu-id="4b474-127">A directory synchronization server for Office 365 synchronizes the list of accounts in AD DS with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="4b474-128">ディレクトリ同期サーバーは、Azure AD Connect を実行する Windows ベースのサーバーです。</span><span class="sxs-lookup"><span data-stu-id="4b474-128">A directory synchronization server is a Windows-based server that runs Azure AD Connect.</span></span> <span data-ttu-id="4b474-129">プロビジョニングを高速化したり、組織内のオンプレミスサーバーの数を少なくしたりするには、Azure IaaS の仮想ネットワーク (VNet) にディレクトリ同期サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="4b474-129">For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your directory synchronization server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="4b474-130">ディレクトリ同期サーバーは、変更に関して AD DS をポーリングしてから、それらを Office 365 サブスクリプションと同期します。</span><span class="sxs-lookup"><span data-stu-id="4b474-130">The directory synchronization server polls AD DS for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="4b474-131">詳細については、「 [Deploy Office 365 Directory Synchronization In Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b474-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="4b474-132">基幹業務 (LOB) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="4b474-132">Line of business (LOB) application</span></span>

<span data-ttu-id="4b474-133">図3は、Azure IaaS で実行されているサーバーベースの LOB アプリケーションの構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="4b474-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="4b474-134">**図 3: Azure IaaS の LOB アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="4b474-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Azure IaaS のサーバーベースの LOB アプリケーション](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="4b474-136">図3では、社内ネットワークによって id インフラストラクチャとユーザーがホストされます。</span><span class="sxs-lookup"><span data-stu-id="4b474-136">In Figure 3, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="4b474-137">これは、サイト間 VPN または ExpressRoute 接続を使用して Azure IaaS gateway に接続されています。</span><span class="sxs-lookup"><span data-stu-id="4b474-137">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="4b474-138">Azure IaaS は、LOB アプリケーションのサーバーを含む仮想ネットワークをホストします。</span><span class="sxs-lookup"><span data-stu-id="4b474-138">Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="4b474-139">Azure Vm で実行されている LOB アプリケーションを作成できます。これは、azure データセンター (場所とも呼ばれる) の Azure VNet のサブネット上に存在します。</span><span class="sxs-lookup"><span data-stu-id="4b474-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="4b474-140">基本的に社内インフラストラクチャを Azure に拡張するので、一意のプライベートアドレス空間を Vnet に割り当て、オンプレミスルーティングテーブルを更新して、各 VNet に到達できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b474-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="4b474-141">接続すると、これらの Vm は、オンプレミスのサーバーの場合と同様に、リモートデスクトップ接続またはシステム管理ソフトウェアを使用して管理できます。</span><span class="sxs-lookup"><span data-stu-id="4b474-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="4b474-142">公的で公開されたポートを構成することで、これらの Vm は、モバイルまたはリモートユーザーがインターネットからアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4b474-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="4b474-143">概念実証の構成については、「 [Azure でのシミュレートされたクロスプレミスの仮想ネットワーク](simulated-cross-premises-virtual-network-in-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b474-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="4b474-144">Azure Vm でホストされている LOB アプリケーションの属性は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4b474-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="4b474-145">複数の階層</span><span class="sxs-lookup"><span data-stu-id="4b474-145">Multiple tiers</span></span>
    
    <span data-ttu-id="4b474-146">一般的な LOB アプリケーションは、階層型のアプローチを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b474-146">Typical LOB applications use a tiered approach.</span></span> <span data-ttu-id="4b474-147">サーバーのセットは、id、データベース処理、アプリケーションとロジックの処理、および社員または顧客へのアクセスのためのフロントエンド web サーバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="4b474-147">Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="4b474-148">高可用性</span><span class="sxs-lookup"><span data-stu-id="4b474-148">High availability</span></span>
    
    <span data-ttu-id="4b474-149">一般的な LOB アプリケーションでは、各層で複数のサーバーを使用することで高可用性が実現されます。</span><span class="sxs-lookup"><span data-stu-id="4b474-149">Typical LOB applications provide high availability by using multiple servers in each tier.</span></span> <span data-ttu-id="4b474-150">Azure IaaS では、Azure の可用性セットのサーバーに 99.9% の稼働時間の SLA が提供されます。</span><span class="sxs-lookup"><span data-stu-id="4b474-150">Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="4b474-151">負荷分散</span><span class="sxs-lookup"><span data-stu-id="4b474-151">Load distribution</span></span>
    
    <span data-ttu-id="4b474-152">階層内の複数のサーバー間でネットワークトラフィックの負荷を分散するには、インターネット接続または内部 Azure ロードバランサーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4b474-152">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer.</span></span> <span data-ttu-id="4b474-153">または、Azure marketplace から入手できる専用のロードバランサーアプライアンスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4b474-153">Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="4b474-154">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4b474-154">Security</span></span>
    
    <span data-ttu-id="4b474-155">インターネットからの一方的な着信トラフィックからサーバーを保護するには、Azure のネットワークセキュリティグループを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4b474-155">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups.</span></span> <span data-ttu-id="4b474-156">サブネットまたは個々の仮想マシンのネットワークインターフェイスに対して許可または拒否されるトラフィックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="4b474-156">You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="4b474-157">Azure の SharePoint Server 2016 ファーム</span><span class="sxs-lookup"><span data-stu-id="4b474-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="4b474-158">図4に示すように、Azure での多階層の高可用性 LOB アプリケーションの例としては、SharePoint Server 2016 ファームがあります。</span><span class="sxs-lookup"><span data-stu-id="4b474-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="4b474-159">**図 4: Azure IaaS の高可用性 SharePoint Server 2016 ファーム**</span><span class="sxs-lookup"><span data-stu-id="4b474-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS の高可用性 SharePoint Server 2016 ファーム](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="4b474-161">図4では、オンプレミスのネットワークが id インフラストラクチャとユーザーをホストしています。</span><span class="sxs-lookup"><span data-stu-id="4b474-161">In Figure 4, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="4b474-162">これは、サイト間 VPN または ExpressRoute 接続を使用して Azure IaaS gateway に接続されています。</span><span class="sxs-lookup"><span data-stu-id="4b474-162">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="4b474-163">Azure VNet には、フロントエンドサーバー、アプリケーションサーバー、SQL Server クラスター、およびドメインコントローラーの各層を含む SharePoint Server 2016 ファームのサーバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b474-163">The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="4b474-164">この構成には、Azure の LOB アプリケーションの次の属性があります。</span><span class="sxs-lookup"><span data-stu-id="4b474-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="4b474-165">階層</span><span class="sxs-lookup"><span data-stu-id="4b474-165">Tiers</span></span>
    
    <span data-ttu-id="4b474-166">ファーム内でさまざまな役割を実行しているサーバーは、層を作成し、各層には独自のサブネットがあります。</span><span class="sxs-lookup"><span data-stu-id="4b474-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="4b474-167">高可用性</span><span class="sxs-lookup"><span data-stu-id="4b474-167">High-availability</span></span>
    
    <span data-ttu-id="4b474-168">各層で複数のサーバーを使用して、層のすべてのサーバーを同じ可用性セットに配置することによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="4b474-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="4b474-169">負荷分散</span><span class="sxs-lookup"><span data-stu-id="4b474-169">Load distribution</span></span>
    
    <span data-ttu-id="4b474-170">内部 Azure ロードバランサーは、受信クライアント web トラフィックをフロントエンドサーバー (WEB1 および WEB2) と、SQL Server クラスターのリスナー IP アドレス (SQL1、: SQL2、および: MN1) に分配します。</span><span class="sxs-lookup"><span data-stu-id="4b474-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="4b474-171">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4b474-171">Security</span></span>
    
    <span data-ttu-id="4b474-172">各サブネットのネットワークセキュリティグループを使用すると、許可される受信および送信トラフィックを構成できます。</span><span class="sxs-lookup"><span data-stu-id="4b474-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="4b474-173">導入を成功させるには、次のパスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b474-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="4b474-174">評価とテスト</span><span class="sxs-lookup"><span data-stu-id="4b474-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="4b474-175">Azure で SharePoint Server 2016 を実行することの利点については、「 [Microsoft azure の Sharepoint server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b474-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="4b474-176">シミュレートされた開発/テスト環境を構築するには、「 [Azure 開発/テスト環境でのイントラネット SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b474-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="4b474-177">デザイン</span><span class="sxs-lookup"><span data-stu-id="4b474-177">Design</span></span>
    
    <span data-ttu-id="4b474-178">「 [SharePoint Server 2016 ファームを設計](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure)する」を参照して、プロセスをステップ実行し、ファームをホストする azure IaaS ネットワーク、コンピューティング、およびストレージ要素のセットとそれらの設定を確認してください。</span><span class="sxs-lookup"><span data-stu-id="4b474-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="4b474-179">展開</span><span class="sxs-lookup"><span data-stu-id="4b474-179">Deploy</span></span>
    
    <span data-ttu-id="4b474-180">高可用性ファームのエンドツーエンド構成を5段階で手順を追って説明するには、「 [Azure で SharePoint server 2016 を SQL Server AlwaysOn 可用性グループと共に展開](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b474-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="4b474-181">Azure での Office 365 のフェデレーション id</span><span class="sxs-lookup"><span data-stu-id="4b474-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="4b474-182">Azure で高可用性を備えた複数層の LOB アプリケーションの別の例として、Office 365 のフェデレーション id があります。</span><span class="sxs-lookup"><span data-stu-id="4b474-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="4b474-183">**図 5: Azure IaaS の Office 365 用の高可用性フェデレーション id インフラストラクチャ**</span><span class="sxs-lookup"><span data-stu-id="4b474-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Azure での高可用性 Office 365 フェデレーション認証インフラストラクチャ](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="4b474-185">図5では、オンプレミスのネットワークが id インフラストラクチャとユーザーをホストしています。</span><span class="sxs-lookup"><span data-stu-id="4b474-185">In Figure 5, an on-premises network hosts an identity infrastructure and users.</span></span> <span data-ttu-id="4b474-186">これは、サイト間 VPN または ExpressRoute 接続を使用して Azure IaaS gateway に接続されています。</span><span class="sxs-lookup"><span data-stu-id="4b474-186">It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection.</span></span> <span data-ttu-id="4b474-187">Azure VNet には、web プロキシサーバー、Active Directory フェデレーションサービス (AD FS) サーバー、および Active Directory ドメインサービス (AD DS) ドメインコントローラーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4b474-187">The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Active Directory Domain Services (AD DS) domain controllers.</span></span>
  
<span data-ttu-id="4b474-188">この構成には、Azure の LOB アプリケーションの次の属性があります。</span><span class="sxs-lookup"><span data-stu-id="4b474-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="4b474-189">**層:** Web プロキシサーバー、AD FS サーバー、AD DS ドメインコントローラーには階層があります。</span><span class="sxs-lookup"><span data-stu-id="4b474-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and AD DS domain controllers.</span></span>
    
- <span data-ttu-id="4b474-190">**負荷分散:** 外部の Azure ロードバランサーは、受信クライアント認証要求を web プロキシに配布し、内部 Azure ロードバランサーは、認証要求を AD FS サーバーに配信します。</span><span class="sxs-lookup"><span data-stu-id="4b474-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="4b474-191">導入を成功させるには、次のパスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4b474-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="4b474-192">評価とテスト</span><span class="sxs-lookup"><span data-stu-id="4b474-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="4b474-193">Office 365 を使用して、フェデレーション認証用のシミュレートされた開発/テスト環境を構築するには[、「office 365 開発/テスト環境のフェデレーション Id](federated-identity-for-your-office-365-dev-test-environment.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b474-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="4b474-194">展開</span><span class="sxs-lookup"><span data-stu-id="4b474-194">Deploy</span></span>
    
    <span data-ttu-id="4b474-195">高可用性 AD FS インフラストラクチャのエンドツーエンド構成を5段階で手順を追って説明するには、「 [Deploy high availability フェデレーション authentication For Office 365 For Azure」](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b474-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="4b474-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b474-196">See Also</span></span>

[<span data-ttu-id="4b474-197">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="4b474-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="4b474-198">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="4b474-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


