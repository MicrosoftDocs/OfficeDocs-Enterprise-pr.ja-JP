---
title: "Azure IaaS のハイブリッド クラウド シナリオ"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: "概要: ハイブリッド アーキテクチャと理解シナリオのインフラストラクチャのサービス (IaaS) としてのベースで、Azure クラウド サービスです。"
ms.openlocfilehash: 66024c708cb4fbc904de18f27077871d52f0e70c
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a><span data-ttu-id="5b45a-103">Azure IaaS のハイブリッド クラウド シナリオ</span><span class="sxs-lookup"><span data-stu-id="5b45a-103">Hybrid cloud scenarios for Azure IaaS</span></span>

 <span data-ttu-id="5b45a-104">**の概要:**サービス (IaaS) としてマイクロソフトのインフラストラクチャのハイブリッド アーキテクチャとシナリオを理解するので、Azure クラウド サービスをベースです。</span><span class="sxs-lookup"><span data-stu-id="5b45a-104">**Summary:** Understand the hybrid architecture and scenarios for Microsoft's Infrastructure as a Service (IaaS)-based cloud offerings in Azure.</span></span>
  
<span data-ttu-id="5b45a-105">クロスプレミスの Azure 仮想ネットワーク (VNet) で実行されている IT ワークロードをホストすることで、オンプレミスのコンピューティングおよび ID インフラストラクチャをクラウドに拡張します。 </span><span class="sxs-lookup"><span data-stu-id="5b45a-105">Extend your on-premises computing and identity infrastructure into the cloud by hosting IT workloads running in cross-premises Azure virtual networks (VNets).</span></span> 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a><span data-ttu-id="5b45a-106">Azure IaaS のハイブリッド シナリオ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="5b45a-106">Azure IaaS hybrid scenario architecture</span></span>

<span data-ttu-id="5b45a-107">図 1 は、Microsoft IaaS ベースの Azure 内ハイブリッド シナリオのアーキテクチャを示しています。</span><span class="sxs-lookup"><span data-stu-id="5b45a-107">Figure 1 shows the architecture of Microsoft IaaS-based hybrid scenarios in Azure.</span></span>
  
<span data-ttu-id="5b45a-108">**Azure で Microsoft ベースの IaaS ハイブリッド シナリオを図 1:**</span><span class="sxs-lookup"><span data-stu-id="5b45a-108">**Figure 1: Microsoft IaaS-based hybrid scenarios in Azure**</span></span>

![Microsoft IaaS ベースの Azure 内ハイブリッド シナリオ](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS.png)
  
<span data-ttu-id="5b45a-110">アーキテクチャの各レイヤーについて:</span><span class="sxs-lookup"><span data-stu-id="5b45a-110">For each layer of the architecture:</span></span>
  
- <span data-ttu-id="5b45a-111">アプリとシナリオ</span><span class="sxs-lookup"><span data-stu-id="5b45a-111">Apps and scenarios</span></span>
    
    <span data-ttu-id="5b45a-112">IT ワークロードは、通常、Azure 仮想マシン (VM) で構成されている可用性の高い多層アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="5b45a-112">An IT workload is typically a multi-tier, highly-available application composed of Azure virtual machines (VMs).</span></span>
    
- <span data-ttu-id="5b45a-113">ID</span><span class="sxs-lookup"><span data-stu-id="5b45a-113">Identity</span></span>
    
    <span data-ttu-id="5b45a-114">ローカル認証のために、Azure VNet で実行されているサーバーのセットに、Windows Server AD ドメイン コントローラーなどの ID サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-114">Add identity servers, such as Windows Server AD domain controllers, to the set of servers running in Azure VNets for local authentication.</span></span>
    
- <span data-ttu-id="5b45a-115">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="5b45a-115">Network</span></span>
    
    <span data-ttu-id="5b45a-116">インターネット経由でのサイト間 VPN 接続、または Azure IaaS に対するプライベート ピアリングとの ExpressRoute 接続を使用します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-116">Use either a site-to-site VPN connection over the Internet or an ExpressRoute connection with private peering to Azure IaaS.</span></span>
    
- <span data-ttu-id="5b45a-117">オンプレミス</span><span class="sxs-lookup"><span data-stu-id="5b45a-117">On-premises</span></span>
    
    <span data-ttu-id="5b45a-p101">Azure で実行されている ID サーバーと同期している ID サーバーが含まれています。ストレージおよびシステムの管理インフラストラクチャなど、Azure で実行されている VM がアクセスできるリソースが含まれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5b45a-p101">Contains identity servers that are synchronized with the identity servers running in Azure. Can also contain resources that VMs running in Azure can access, such as storage and systems management infrastructure.</span></span>
    
## <a name="dirsync-server-for-office-365"></a><span data-ttu-id="5b45a-120">Office 365 向けの DirSync サーバー</span><span class="sxs-lookup"><span data-stu-id="5b45a-120">DirSync server for Office 365</span></span>

<span data-ttu-id="5b45a-121">図 2 に示すように、コンピューティングと ID インフラストラクチャをクラウドに拡張する一例として、ディレクトリ同期 (DirSync) サーバーを Azure VNet から実行するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="5b45a-121">Running your directory synchronization (DirSync) server from an Azure VNet, as shown in Figure 2, is an example of extending your computing and identity infrastructure to the cloud.</span></span>
  
<span data-ttu-id="5b45a-122">**Azure IaaS で Office 365 のディレクトリ同期サーバーを図 2:**</span><span class="sxs-lookup"><span data-stu-id="5b45a-122">**Figure 2: DirSync server for Office 365 in Azure IaaS**</span></span>

![Azure IaaS の Office 365 向けの DirSync サーバー](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_DirSync.png)
  
<span data-ttu-id="5b45a-p102">図 2 に、オンプレミスのネットワークは、プロキシ サーバーとルーターの端に、Windows サーバーの AD インフラストラクチャをホストします。ルーターは、サイト間の VPN または ExpressRoute の接続を使用して、Azure の VNet の端に、Azure のゲートウェイに接続します。VNet の内部は、ディレクトリ同期サーバーは、Azure AD 接続を実行します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-p102">In Figure 2, an on-premises network hosts a Windows Server AD infrastructure, with a proxy server and a router at its edge. The router connects to an Azure gateway at the edge of an Azure VNet with a site-to-site VPN or ExpressRoute connection. Inside the VNet, a DirSync server runs Azure AD Connect.</span></span>
  
<span data-ttu-id="5b45a-127">Office 365 向けの DirSync サーバーは、Windows Server AD のアカウントの一覧を Office 365 サブスクリプションの Azure AD テナントと同期します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-127">A DirSync server for Office 365 synchronizes the list of accounts in Windows Server AD with the Azure AD tenant of an Office 365 subscription.</span></span>
  
<span data-ttu-id="5b45a-p103">DirSync サーバーは、Azure AD Connect を実行する Windows ベースのサーバーです。迅速なプロビジョニングを実現し、組織内のオンプレミスのサーバーの数を減らすには、Azure IaaS の仮想ネットワーク (VNet) で DirSync サーバーを展開します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-p103">A DirSync server is a Windows-based server that runs Azure AD Connect. For faster provisioning or to reduce the number of on-premises servers in your organization, deploy your DirSync server in a virtual network (VNet) in Azure IaaS.</span></span>
  
<span data-ttu-id="5b45a-130">DirSync サーバーは、変更用に Windows Server AD をポーリングし、それらの変更点を Office 365 サブスクリプションと同期します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-130">The DirSync server polls Windows Server AD for changes and then synchronizes them with the Office 365 subscription.</span></span>
  
<span data-ttu-id="5b45a-131">詳細については、 [Azure で Office 365 のディレクトリ同期の展開](https://technet.microsoft.com/library/dn635310.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-131">For more information, see [Deploy Office 365 DirSync in Azure](https://technet.microsoft.com/library/dn635310.aspx).</span></span>
  
## <a name="line-of-business-lob-application"></a><span data-ttu-id="5b45a-132">基幹業務 (LOB) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="5b45a-132">Line of business (LOB) application</span></span>

<span data-ttu-id="5b45a-133">図 3 は、Azure IaaS で実行されているサーバーベース LOB アプリケーションの構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="5b45a-133">Figure 3 shows the configuration of a server-based LOB application running in Azure IaaS.</span></span>
  
<span data-ttu-id="5b45a-134">**Azure IaaS に LOB アプリケーションを図 3:**</span><span class="sxs-lookup"><span data-stu-id="5b45a-134">**Figure 3: LOB application in Azure IaaS**</span></span>

![Azure IaaS 内のサーバ ベース LOB アプリケーション](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_Ex.png)
  
<span data-ttu-id="5b45a-p104">図 3 では、オンプレミス ネットワークは、ID インフラストラクチャとユーザーをホストしています。サイト間 VPN または ExpressRoute の接続を使用して、Azure IaaS ゲートウェイに接続されています。Azure IaaS は、LOB アプリケーションのサーバーを含む仮想ネットワークをホストします。</span><span class="sxs-lookup"><span data-stu-id="5b45a-p104">In Figure 3, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. Azure IaaS hosts a virtual network containing the servers of the LOB application.</span></span>
  
<span data-ttu-id="5b45a-139">Azure データ センター (所在地) で、Azure VNet のサブネット上に存在、Azure の Vm で実行されている LOB アプリケーションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="5b45a-139">You can create LOB applications running on Azure VMs, which reside on subnets of an Azure VNet in an Azure datacenter (also known as a location).</span></span>
  
<span data-ttu-id="5b45a-140">本質的にはオンプレミス インフラストラクチャを Azure に拡張しているので、VNet に独自のプライベート アドレス空間を割り当て、オンプレミス ルーティング テーブルを更新して、各 VNet への到達可能性を確保する必要があります </span><span class="sxs-lookup"><span data-stu-id="5b45a-140">Because you are essentially extending your on-premises infrastructure to Azure, you must assign unique private address space to your VNets and update your on-premises routing tables to ensure reachability to each VNet.</span></span>
  
<span data-ttu-id="5b45a-141">接続が完了したら、オンプレミス サーバーと同様に、リモート デスクトップ接続またはシステム管理ソフトウェアを使用してこれらの VM を管理できます。</span><span class="sxs-lookup"><span data-stu-id="5b45a-141">Once connected, these VMs can be managed with remote desktop connections or with your systems management software, just like your on-premises servers.</span></span>
  
<span data-ttu-id="5b45a-142">一般に公開されるポートを構成すると、これらの VM には、モバイル ユーザーまたはリモート ユーザーによってインターネットからもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5b45a-142">By configuring publically-exposed ports, these VMs can also be accessed from the Internet by mobile or remote users.</span></span>
  
<span data-ttu-id="5b45a-143">概念実証の構成では、 [Simulated 間設置型で、Azure の仮想ネットワーク](simulated-cross-premises-virtual-network-in-azure.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-143">For a proof-of-concept configuration, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span>
  
<span data-ttu-id="5b45a-144">Azure VM でホストされている LOB アプリケーションの属性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-144">Attributes of LOB applications hosted on Azure VMs are the following:</span></span>
  
- <span data-ttu-id="5b45a-145">複数の階層</span><span class="sxs-lookup"><span data-stu-id="5b45a-145">Multiple tiers</span></span>
    
    <span data-ttu-id="5b45a-p105">通常の LOB アプリケーションでは、階層型アプローチを使用します。サーバーのセットが、従業員や顧客のアクセスのために ID、データベース処理、アプリケーションおよびロジック処理、フロントエンド Web サーバーを提供します。 </span><span class="sxs-lookup"><span data-stu-id="5b45a-p105">Typical LOB applications use a tiered approach. Sets of servers provide identity, database processing, application and logic processing, and front-end web servers for employee or customer access.</span></span> 
    
- <span data-ttu-id="5b45a-148">高可用性</span><span class="sxs-lookup"><span data-stu-id="5b45a-148">High availability</span></span>
    
    <span data-ttu-id="5b45a-p106">通常の LOB アプリケーションでは、層ごとに複数のサーバーを使用することによって高可用性が実現します。Azure IaaS では、Azure の可用性セットでサーバーに 99.9% の稼働時間 SLA を提供します。 </span><span class="sxs-lookup"><span data-stu-id="5b45a-p106">Typical LOB applications provide high availability by using multiple servers in each tier. Azure IaaS provides a 99.9% uptime SLA for servers in Azure availability sets.</span></span> 
    
- <span data-ttu-id="5b45a-151">負荷分散</span><span class="sxs-lookup"><span data-stu-id="5b45a-151">Load distribution</span></span>
    
    <span data-ttu-id="5b45a-p107">階層内の複数のサーバー間のネットワーク トラフィックの負荷を分散するには、インターネット接続済みまたは内部の Azure ロード バランサーを使用できます。または、Azure Marketplace から入手可能な専用のロード バランサー アプライアンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5b45a-p107">To distribute the load of network traffic among multiple servers in a tier, you can use an Internet-facing or internal Azure load balancer. Or, you can use a dedicated load balancer appliance available from the Azure marketplace.</span></span>
    
- <span data-ttu-id="5b45a-154">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5b45a-154">Security</span></span>
    
    <span data-ttu-id="5b45a-p108">インターネットからの未承諾の着信トラフィックからサーバーを保護するには、Azure ネットワーク セキュリティ グループを使用できます。サブネットの許可または拒否されたトラフィック、または個々の仮想マシンのネットワーク インターフェイスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="5b45a-p108">To protect servers from unsolicited incoming traffic from the Internet, you can use Azure network security groups. You can define allowed or denied traffic for a subnet or the network interface of an individual virtual machine.</span></span>
    
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="5b45a-157">Azure の SharePoint Server 2016 ファーム</span><span class="sxs-lookup"><span data-stu-id="5b45a-157">SharePoint Server 2016 farm in Azure</span></span>

<span data-ttu-id="5b45a-158">Azure での可用性の高い多層 LOB アプリケーションの例として、図 4 に示すように SharePoint Server 2016 ファームがあります。</span><span class="sxs-lookup"><span data-stu-id="5b45a-158">An example of a multi-tier, highly-available LOB application in Azure is a SharePoint Server 2016 farm, as shown in Figure 4.</span></span>
  
<span data-ttu-id="5b45a-159">**図 4: 高可用性サーバー 2016 の SharePoint ファーム Azure IaaS で**</span><span class="sxs-lookup"><span data-stu-id="5b45a-159">**Figure 4: A high-availability SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS の高可用性 SharePoint Server 2016 ファーム](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_SP2016.png)
  
<span data-ttu-id="5b45a-p109">図 4 では、オンプレミス ネットワークは、ID インフラストラクチャとユーザーをホストしています。サイト間 VPN または ExpressRoute に接続して、Azure IaaS ゲートウェイに接続されています。Azure VNet には、SharePoint Server 2016 ファームのサーバーが含まれています。これには、フロント エンド サーバー、アプリケーション サーバー、SQL Server クラスター、およびドメイン コントローラーごとに個別の階層が存在します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-p109">In Figure 4, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains the servers of the SharePoint Server 2016 farm, which includes separate tiers for the front-end servers, the application servers, the SQL Server cluster, and the domain controllers.</span></span>
  
<span data-ttu-id="5b45a-164">この構成には、次に示す Azure の LOB アプリケーションの属性が含まれています。 </span><span class="sxs-lookup"><span data-stu-id="5b45a-164">This configuration has the following attributes of LOB applications in Azure:</span></span> 
  
- <span data-ttu-id="5b45a-165">階層</span><span class="sxs-lookup"><span data-stu-id="5b45a-165">Tiers</span></span>
    
    <span data-ttu-id="5b45a-166">ファーム内のさまざまな役割を実行しているサーバーは、階層を作成し、各階層には独自のサブネットです。</span><span class="sxs-lookup"><span data-stu-id="5b45a-166">Servers running different roles within the farm create the tiers and each tier has its own subnet.</span></span>
    
- <span data-ttu-id="5b45a-167">高可用性</span><span class="sxs-lookup"><span data-stu-id="5b45a-167">High-availability</span></span>
    
    <span data-ttu-id="5b45a-168">各階層で複数のサーバーを使用して、階層のすべてのサーバーを同じ可用性セットに配置することによって実現します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-168">Achieved by using more than one server in each tier and placing all the servers of a tier in the same availability set.</span></span>
    
- <span data-ttu-id="5b45a-169">負荷分散</span><span class="sxs-lookup"><span data-stu-id="5b45a-169">Load distribution</span></span>
    
    <span data-ttu-id="5b45a-170">Azure の内部ロード バランサーは、クライアント Web の受信トラフィックをフロントエンド サーバー (WEB1 と WEB2) および SQL Server クラスターのリスナーの IP アドレス (SQL1、SQL2、MN1) に配布します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-170">Internal Azure load balancers distribute the incoming client web traffic to the front-end servers (WEB1 and WEB2) and to the listener IP address of the SQL Server cluster (SQL1, SQL2, and MN1).</span></span>
    
- <span data-ttu-id="5b45a-171">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5b45a-171">Security</span></span>
    
    <span data-ttu-id="5b45a-172">各サブネットのネットワーク セキュリティ グループを使用して、許可する受信トラフィックおよび送信トラフィックを構成できます。</span><span class="sxs-lookup"><span data-stu-id="5b45a-172">Network security groups for each subnet let you to configure allowed inbound and outbound traffic.</span></span>
    
<span data-ttu-id="5b45a-173">正常に導入するために次のパスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-173">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="5b45a-174">評価と試用</span><span class="sxs-lookup"><span data-stu-id="5b45a-174">Evaluate and experiment</span></span>
    
    <span data-ttu-id="5b45a-175">Azure で実行中の SharePoint サーバーの 2016年の利点を理解するのには、 [Microsoft Azure 内の SharePoint サーバーの 2016年](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-175">See [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) to understand the benefits of running SharePoint Server 2016 in Azure.</span></span>
    
    <span data-ttu-id="5b45a-176">[イントラネットの SharePoint サーバー 2016 Azure 開発/テスト環境で](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)シミュレートされた開発/テスト環境を構築を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-176">See [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) to build a simulated dev/test environment</span></span>
    
2. <span data-ttu-id="5b45a-177">デザイン</span><span class="sxs-lookup"><span data-stu-id="5b45a-177">Design</span></span>
    
    <span data-ttu-id="5b45a-178">Azure IaaS のネットワー キング、コンピューティング、およびファームとその設定をホストするストレージ ・ エレメントのセットを決定するためのプロセスをステップ実行するには[Azure の SharePoint サーバーの 2016年ファームの設計](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-178">See [Designing a SharePoint Server 2016 farm in Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) to step through a process to determine the set of Azure IaaS networking, compute, and storage elements to host your farm and their settings.</span></span>
    
3. <span data-ttu-id="5b45a-179">展開</span><span class="sxs-lookup"><span data-stu-id="5b45a-179">Deploy</span></span>
    
    <span data-ttu-id="5b45a-180">[Azure で AlwaysOn 可用性グループを SQL Server と SharePoint サーバー 2016 を展開する](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx)5 つの段階では、高可用性ファームのエンド ・ ツー ・ エンドの構成の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-180">See [Deploying SharePoint Server 2016 with SQL Server AlwaysOn Availability Groups in Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) to step through the end-to-end configuration of the high-availability farm in five phases.</span></span>
    
## <a name="federated-identity-for-office-365-in-azure"></a><span data-ttu-id="5b45a-181">Azure 内の Office 365 のフェデレートされた識別情報</span><span class="sxs-lookup"><span data-stu-id="5b45a-181">Federated identity for Office 365 in Azure</span></span>

<span data-ttu-id="5b45a-182">Azure 内の複数の層、および高可用性の LOB アプリケーションの別の例は、Office 365 のフェデレーションの id です。</span><span class="sxs-lookup"><span data-stu-id="5b45a-182">Another example of a multi-tier, highly-available LOB application in Azure is federated identity for Office 365.</span></span>
  
<span data-ttu-id="5b45a-183">**図 5: Azure IaaS で Office 365 のフェデレートされた識別情報の高可用性インフラストラクチャが、**</span><span class="sxs-lookup"><span data-stu-id="5b45a-183">**Figure 5: A high-availability federated identity infrastructure for Office 365 in Azure IaaS**</span></span>

![Azure での高可用性 Office 365 フェデレーション認証インフラストラクチャの最終構成](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_ADFS.png)
  
<span data-ttu-id="5b45a-p110">図 5 に、オンプレミスのネットワークとユーザーの識別情報のインフラストラクチャをホストします。サイト間の VPN または ExpressRoute の接続を使用して、Azure の IaaS のゲートウェイに接続されています。Azure VNet には、web プロキシ サーバー、Active Directory フェデレーション サービス (AD FS) サーバー、および Windows Server ・ Active Directory (AD) ドメイン コント ローラーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5b45a-p110">In Figure 5, an on-premises network hosts an identity infrastructure and users. It is connected to an Azure IaaS gateway with a site-to-site VPN or ExpressRoute connection. The Azure VNet contains web proxy servers, Active Directory Federation Services (AD FS) servers, and Windows Server Active Directory (AD) domain controllers.</span></span>
  
<span data-ttu-id="5b45a-188">この構成には、次に示す Azure の LOB アプリケーションの属性が含まれています。 </span><span class="sxs-lookup"><span data-stu-id="5b45a-188">This configuration has the following attributes of LOB applications in Azure:</span></span>
  
- <span data-ttu-id="5b45a-189">**層:**Web プロキシ サーバー、AD FS サーバー、および Windows Server AD ドメイン コント ローラーの階層があります。</span><span class="sxs-lookup"><span data-stu-id="5b45a-189">**Tiers:** There are tiers for web proxy servers, AD FS servers, and Windows Server AD domain controllers.</span></span>
    
- <span data-ttu-id="5b45a-190">**負荷分散:**Azure の外部のロード バランサーは、web プロキシを受信したクライアントの認証要求を分散し、Azure の内部ロード バランサーが AD FS サーバーに認証要求を配布します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-190">**Load distribution:** An external Azure load balancer distributes the incoming client authentication requests to the web proxies and an internal Azure load balancer distributes authentication requests to the AD FS servers.</span></span>
    
<span data-ttu-id="5b45a-191">正常に導入するために次のパスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-191">Follow this path for successful adoption:</span></span>
  
1. <span data-ttu-id="5b45a-192">評価と試用</span><span class="sxs-lookup"><span data-stu-id="5b45a-192">Evaluate and experiment</span></span>
    
    <span data-ttu-id="5b45a-193">Office 365 とフェデレーションの認証のためにシミュレートされた開発/テスト環境を構築するのには[、Office 365 の開発/テスト環境にフェデレーション ユーザー](federated-identity-for-your-office-365-dev-test-environment.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-193">See [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md) to build a simulated dev/test environment for federated authentication with Office 365.</span></span>
    
2. <span data-ttu-id="5b45a-194">展開</span><span class="sxs-lookup"><span data-stu-id="5b45a-194">Deploy</span></span>
    
    <span data-ttu-id="5b45a-195">5 つのフェーズでは、AD FS インフラストラクチャの高可用性のエンド ・ ツー ・ エンドの構成をステップ実行するには[Azure で Office 365 の展開の高可用性フェデレーション認証](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-195">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) to step through the end-to-end configuration of the high availability AD FS infrastructure in five phases.</span></span>
    
<span data-ttu-id="5b45a-196">これらのその他のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b45a-196">See these additional resources:</span></span>
  
- [<span data-ttu-id="5b45a-197">ハイブリッド クラウド環境の構築</span><span class="sxs-lookup"><span data-stu-id="5b45a-197">Architecting Hybrid Cloud Environments</span></span>](https://gallery.technet.microsoft.com/Architecting-Hybrid-Cloud-a7dc9f24/file/147475/1/Architecting%20Hybrid%20Cloud%20Environments%20V1.docx)
    
- [<span data-ttu-id="5b45a-198">クラウド マイクロソフト仮想アカデミー コースのページに、データ センターを拡張します。</span><span class="sxs-lookup"><span data-stu-id="5b45a-198">Extend Your Datacenter to the Cloud Microsoft Virtual Academy course</span></span>](https://mva.microsoft.com/en-US/training-courses/extend-your-datacenter-to-the-cloud-13908?l=7fG3tAouB_7100115881)
    
- [<span data-ttu-id="5b45a-199">設計して、Azure で LOB アプリケーションを作成</span><span class="sxs-lookup"><span data-stu-id="5b45a-199">Design and Build an LOB application in Azure </span></span>](https://techcommunity.microsoft.com/t5/CAAB-Cloud-Adoption-Advisory/EXTRA-November-2016-Webinar/m-p/30058#M41)
    
## <a name="see-also"></a><span data-ttu-id="5b45a-200">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b45a-200">See Also</span></span>

[<span data-ttu-id="5b45a-201">エンタープライズ アーキテクトのための Microsoft ハイブリッド クラウド</span><span class="sxs-lookup"><span data-stu-id="5b45a-201">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="5b45a-202">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="5b45a-202">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="5b45a-203">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="5b45a-203">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



