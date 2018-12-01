---
title: Azure IaaS のハイブリッド クラウド シナリオ
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: '概要: ハイブリッド アーキテクチャと理解シナリオのインフラストラクチャのサービス (IaaS) としてのベースで、Azure クラウド サービスです。'
ms.openlocfilehash: bb6611f51cc346273438e879d957597fe3299c58
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123244"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="beff9-103">Azure IaaS のハイブリッド クラウドのシナリオ</span><span class="sxs-lookup"><span data-stu-id="beff9-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="beff9-104">**の概要:** サービス (IaaS) としてマイクロソフトのインフラストラクチャのハイブリッド アーキテクチャとシナリオを理解するので、Azure クラウド サービスをベースです。</span><span class="sxs-lookup"><span data-stu-id="beff9-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="beff9-105">クロスプレミスの Azure 仮想ネットワーク (VNet) で実行されている IT ワークロードをホストすることで、オンプレミスのコンピューティングおよび ID インフラストラクチャをクラウドに拡張します。 </span><span class="sxs-lookup"><span data-stu-id="beff9-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="beff9-106">Azure IaaS のハイブリッド シナリオ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="beff9-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="beff9-107">図 1 は、Microsoft IaaS ベースの Azure 内ハイブリッド シナリオのアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="beff9-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="beff9-108">**図 1:Microsoft IaaS ベースの Azure 内ハイブリッド シナリオ**</span><span class="sxs-lookup"><span data-stu-id="beff9-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Microsoft IaaS ベースの Azure 内ハイブリッド シナリオ](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
<span data-ttu-id="beff9-110">アーキテクチャの各レイヤーについて:</span><span class="sxs-lookup"><span data-stu-id="beff9-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="beff9-111">アプリとシナリオ</span><span class="sxs-lookup"><span data-stu-id="beff9-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="beff9-112">IT ワークロードは、通常、Azure 仮想マシン (VM) で構成されている可用性の高い多層アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="beff9-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="beff9-113">ID</span><span class="sxs-lookup"><span data-stu-id="beff9-113">Identity</span></span>
    
    <span data-ttu-id="beff9-114">ローカル認証のために、Azure VNet で実行されているサーバーのセットに、Windows Server AD ドメイン コントローラーなどの ID サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="beff9-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="beff9-115">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="beff9-115">Network</span></span>
    
    <span data-ttu-id="beff9-116">インターネット経由でのサイト間 VPN 接続、または Azure IaaS に対するプライベート ピアリングとの ExpressRoute 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="beff9-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="beff9-117">オンプレミス</span><span class="sxs-lookup"><span data-stu-id="beff9-117">On-premises</span></span>
    
    <span data-ttu-id="beff9-p101">Azure で実行されている ID サーバーと同期している ID サーバーが含まれています。ストレージおよびシステムの管理インフラストラクチャなど、Azure で実行されている VM がアクセスできるリソースが含まれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="beff9-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="dirsync-server-for-office-365"></a><span data-ttu-id="beff9-120">Office 365 向けの DirSync サーバー</span><span class="sxs-lookup"><span data-stu-id="beff9-120">DirSync server for Office 365</span></span>

<span data-ttu-id="beff9-121">図 2 に示すように、コンピューティングと ID インフラストラクチャをクラウドに拡張する一例として、ディレクトリ同期 (DirSync) サーバーを Azure VNet から実行するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="beff9-121">Running your directory synchronization (DirSync) server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="beff9-122">**図 2: Azure IaaS の Office 365 向けの DirSync サーバー**</span><span class="sxs-lookup"><span data-stu-id="beff9-122">**Figure 2: DirSync server for Office 365 in Azure IaaS**</span></span>

![Azure IaaS の Office 365 向けの DirSync サーバー](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
<span data-ttu-id="beff9-p102">図 2 に、オンプレミスのネットワークは、プロキシ サーバーとルーターの端に、Windows サーバーの AD インフラストラクチャをホストします。ルーターは、サイト間の VPN または ExpressRoute の接続を使用して、Azure の VNet の端に、Azure のゲートウェイに接続します。VNet の内部は、ディレクトリ同期サーバーは、Azure AD 接続を実行します。</span><span class="sxs-lookup"><span data-stu-id="beff9-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a DirSync server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="beff9-127">Office 365 向けの DirSync サーバーは、Windows Server AD のアカウントの一覧を Office 365 サブスクリプションの Azure AD テナントと同期します。</span><span class="sxs-lookup"><span data-stu-id="beff9-127">A DirSync server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="beff9-p103">DirSync サーバーは、Azure AD Connect を実行する Windows ベースのサーバーです。迅速なプロビジョニングを実現し、組織内のオンプレミスのサーバーの数を減らすには、Azure IaaS の仮想ネットワーク (VNet) で DirSync サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="beff9-p103">A DirSync server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your DirSync server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="beff9-130">DirSync サーバーは、変更用に Windows Server AD をポーリングし、それらの変更点を Office 365 サブスクリプションと同期します。</span><span class="sxs-lookup"><span data-stu-id="beff9-130">The DirSync server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="beff9-131">詳細については、 [Microsoft Azure で Office 365 ディレクトリ同期を展開](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beff9-131">For more information, see [Deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="beff9-132">基幹業務 (LOB) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="beff9-132">Line of business (LOB) application</span></span>

<span data-ttu-id="beff9-133">図 3 は、Azure IaaS で実行されているサーバーベース LOB アプリケーションの構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="beff9-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="beff9-134">**図 3: Azure IaaS 内の LOB アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="beff9-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Azure IaaS 内のサーバ ベース LOB アプリケーション](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
<span data-ttu-id="beff9-p104">図 3 では、オンプレミス ネットワークは、ID インフラストラクチャとユーザーをホストしています。サイト間 VPN または ExpressRoute の接続を使用して、Azure IaaS ゲートウェイに接続されています。Azure IaaS は、LOB アプリケーションのサーバーを含む仮想ネットワークをホストします。</span><span class="sxs-lookup"><span data-stu-id="beff9-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="beff9-139">Azure データセンター (場所) 内の Azure VNet のサブネット上に存在する、Azure VM で実行される LOB アプリケーションを作成することができます。 


</span><span class="sxs-lookup"><span data-stu-id="beff9-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="beff9-140">本質的にはオンプレミス インフラストラクチャを Azure に拡張しているので、VNet に独自のプライベート アドレス空間を割り当て、オンプレミス ルーティング テーブルを更新して、各 VNet への到達可能性を確保する必要があります </span><span class="sxs-lookup"><span data-stu-id="beff9-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="beff9-141">接続が完了したら、オンプレミス サーバーと同様に、リモート デスクトップ接続またはシステム管理ソフトウェアを使用してこれらの VM を管理できます。</span><span class="sxs-lookup"><span data-stu-id="beff9-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="beff9-142">一般に公開されるポートを構成すると、これらの VM には、モバイル ユーザーまたはリモート ユーザーによってインターネットからもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="beff9-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="beff9-143">概念実証構成については、「[Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beff9-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="beff9-144">Azure VM でホストされている LOB アプリケーションの属性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="beff9-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="beff9-145">複数の階層</span><span class="sxs-lookup"><span data-stu-id="beff9-145">Multiple tiers</span></span>
    
    <span data-ttu-id="beff9-p105">通常の LOB アプリケーションでは、階層型アプローチを使用します。サーバーのセットが、従業員や顧客のアクセスのために ID、データベース処理、アプリケーションおよびロジック処理、フロントエンド Web サーバーを提供します。 </span><span class="sxs-lookup"><span data-stu-id="beff9-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="beff9-148">高可用性</span><span class="sxs-lookup"><span data-stu-id="beff9-148">High availability</span></span>
    
    <span data-ttu-id="beff9-p106">通常の LOB アプリケーションでは、層ごとに複数のサーバーを使用することによって高可用性が実現します。Azure IaaS では、Azure の可用性セットでサーバーに 99.9% の稼働時間 SLA を提供します。 </span><span class="sxs-lookup"><span data-stu-id="beff9-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="beff9-151">負荷分散</span><span class="sxs-lookup"><span data-stu-id="beff9-151">Load distribution</span></span>
    
    <span data-ttu-id="beff9-p107">階層内の複数のサーバー間のネットワーク トラフィックの負荷を分散するには、インターネット接続済みまたは内部の Azure ロード バランサーを使用できます。または、Azure Marketplace から入手可能な専用のロード バランサー アプライアンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="beff9-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="beff9-154">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="beff9-154">Security</span></span>
    
    <span data-ttu-id="beff9-p108">インターネットからの未承諾の着信トラフィックからサーバーを保護するには、Azure ネットワーク セキュリティ グループを使用できます。サブネットの許可または拒否されたトラフィック、または個々の仮想マシンのネットワーク インターフェイスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="beff9-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="beff9-157">Azure の SharePoint Server 2016 ファーム</span><span class="sxs-lookup"><span data-stu-id="beff9-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="beff9-158">Azure での可用性の高い多層 LOB アプリケーションの例として、図 4 に示すように SharePoint Server 2016 ファームがあります。</span><span class="sxs-lookup"><span data-stu-id="beff9-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="beff9-159">**図 4:Azure IaaS の高可用性 SharePoint Server 2016 ファーム**</span><span class="sxs-lookup"><span data-stu-id="beff9-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS の高可用性 SharePoint Server 2016 ファーム](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
<span data-ttu-id="beff9-p109">図 4 では、オンプレミス ネットワークは、ID インフラストラクチャとユーザーをホストしています。サイト間 VPN または ExpressRoute に接続して、Azure IaaS ゲートウェイに接続されています。Azure VNet には、SharePoint Server 2016 ファームのサーバーが含まれています。これには、フロント エンド サーバー、アプリケーション サーバー、SQL Server クラスター、およびドメイン コントローラーごとに個別の階層が存在します。</span><span class="sxs-lookup"><span data-stu-id="beff9-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="beff9-164">この構成には、次に示す Azure の LOB アプリケーションの属性が含まれています。 </span><span class="sxs-lookup"><span data-stu-id="beff9-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="beff9-165">階層</span><span class="sxs-lookup"><span data-stu-id="beff9-165">Tiers</span></span>
    
    <span data-ttu-id="beff9-166">ファーム内でさまざまな役割を実行するサーバーは、階層を作成し、各階層には独自のサブネットが存在します。
</span><span class="sxs-lookup"><span data-stu-id="beff9-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="beff9-167">高可用性</span><span class="sxs-lookup"><span data-stu-id="beff9-167">High-availability</span></span>
    
    <span data-ttu-id="beff9-168">各階層で複数のサーバーを使用して、階層のすべてのサーバーを同じ可用性セットに配置することによって実現します。</span><span class="sxs-lookup"><span data-stu-id="beff9-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="beff9-169">負荷分散</span><span class="sxs-lookup"><span data-stu-id="beff9-169">Load distribution</span></span>
    
    <span data-ttu-id="beff9-170">Azure の内部ロード バランサーは、クライアント Web の受信トラフィックをフロントエンド サーバー (WEB1 と WEB2) および SQL Server クラスターのリスナーの IP アドレス (SQL1、SQL2、MN1) に配布します。</span><span class="sxs-lookup"><span data-stu-id="beff9-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="beff9-171">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="beff9-171">Security</span></span>
    
    <span data-ttu-id="beff9-172">各サブネットのネットワーク セキュリティ グループを使用して、許可する受信トラフィックおよび送信トラフィックを構成できます。</span><span class="sxs-lookup"><span data-stu-id="beff9-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="beff9-173">正常に導入するために次のパスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="beff9-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="beff9-174">評価と試用</span><span class="sxs-lookup"><span data-stu-id="beff9-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="beff9-175">Azure で実行中の SharePoint サーバーの 2016年の利点を理解するのには、 [Microsoft Azure 内の SharePoint サーバーの 2016年](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beff9-175">See [SharePoint Server 2016 in Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="beff9-176">[イントラネットの SharePoint サーバー 2016 Azure 開発/テスト環境で](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)シミュレートされた開発/テスト環境を構築を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beff9-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="beff9-177">デザイン</span><span class="sxs-lookup"><span data-stu-id="beff9-177">Design</span></span>
    
    <span data-ttu-id="beff9-178">Azure IaaS のネットワー キング、コンピューティング、およびファームとその設定をホストするストレージ ・ エレメントのセットを決定するためのプロセスをステップ実行するには[Azure の SharePoint サーバーの 2016年ファームの設計](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beff9-178">See [Designing a SharePoint Server 2016 farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="beff9-179">展開</span><span class="sxs-lookup"><span data-stu-id="beff9-179">Deploy</span></span>
    
    <span data-ttu-id="beff9-180">[Azure で AlwaysOn 可用性グループを SQL Server と SharePoint サーバー 2016 を展開する](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in)5 つの段階では、高可用性ファームのエンド ・ ツー ・ エンドの構成の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beff9-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="beff9-181">Azure 内の Office 365 のフェデレートされた識別情報</span><span class="sxs-lookup"><span data-stu-id="beff9-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="beff9-182">Azure 内の複数の層、および高可用性の LOB アプリケーションの別の例は、Office 365 のフェデレーションの id です。</span><span class="sxs-lookup"><span data-stu-id="beff9-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="beff9-183">**図 5: Azure IaaS で Office 365 のフェデレートされた識別情報の高可用性インフラストラクチャが、**</span><span class="sxs-lookup"><span data-stu-id="beff9-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![高可用性の Office 365 は、Azure での認証インフラストラクチャを連合](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
<span data-ttu-id="beff9-p110">図 5 に、オンプレミスのネットワークとユーザーの識別情報のインフラストラクチャをホストします。サイト間の VPN または ExpressRoute の接続を使用して、Azure の IaaS のゲートウェイに接続されています。Azure VNet には、web プロキシ サーバー、Active Directory フェデレーション サービス (AD FS) サーバー、および Windows Server ・ Active Directory (AD) ドメイン コント ローラーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="beff9-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="beff9-188">この構成には、次に示す Azure の LOB アプリケーションの属性が含まれています。 </span><span class="sxs-lookup"><span data-stu-id="beff9-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="beff9-189">**層:** Web プロキシ サーバー、AD FS サーバー、および Windows Server AD ドメイン コント ローラーの階層があります。</span><span class="sxs-lookup"><span data-stu-id="beff9-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="beff9-190">**負荷分散:** Azure の外部のロード バランサーは、web プロキシを受信したクライアントの認証要求を分散し、Azure の内部ロード バランサーが AD FS サーバーに認証要求を配布します。</span><span class="sxs-lookup"><span data-stu-id="beff9-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="beff9-191">正常に導入するために次のパスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="beff9-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="beff9-192">評価と試用</span><span class="sxs-lookup"><span data-stu-id="beff9-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="beff9-193">Office 365 とフェデレーションの認証のためにシミュレートされた開発/テスト環境を構築するのには[、Office 365 の開発/テスト環境にフェデレーション ユーザー](federated-identity-for-your-office-365-dev-test-environment.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beff9-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="beff9-194">展開</span><span class="sxs-lookup"><span data-stu-id="beff9-194">Deploy</span></span>
    
    <span data-ttu-id="beff9-195">5 つのフェーズでは、AD FS インフラストラクチャの高可用性のエンド ・ ツー ・ エンドの構成をステップ実行するには[Azure で Office 365 の展開の高可用性フェデレーション認証](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="beff9-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
    
## <a name="see-also"></a><span data-ttu-id="beff9-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="beff9-196">See Also</span></span>

[<span data-ttu-id="beff9-197">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="beff9-197">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="beff9-198">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="beff9-198">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)


