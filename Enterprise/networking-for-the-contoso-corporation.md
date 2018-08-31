---
title: Contoso Corporation のネットワーク
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
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: '概要: は、contoso 社のネットワーク インフラストラクチャとマイクロソフトのクラウド サービスに最適化されたアクセスを ExpressRoute を使用してその方法を理解します。'
ms.openlocfilehash: 89d4182d8a5ef44f936977ec51cc002b51f4b379
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915222"
---
# <a name="networking-for-the-contoso-corporation"></a><span data-ttu-id="a8586-103">Contoso Corporation のネットワーク</span><span class="sxs-lookup"><span data-stu-id="a8586-103">Networking for the Contoso Corporation</span></span>

 <span data-ttu-id="a8586-104">**の概要:** Contoso 社のネットワーク インフラストラクチャとマイクロソフトのクラウド サービスに最適化されたアクセスを ExpressRoute を使用してその方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="a8586-104">**Summary:** Understand the Contoso networking infrastructure and how it can use ExpressRoute for optimized acccess to Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="a8586-p101">クラウドの包括的なインフラストラクチャを採用するには、contoso 社のネットワーク ・ エンジニアは、ネットワーク トラフィックをクラウド ベースのサービスを伝達する方法に根本的な変化を実現しました。オンプレミスのサーバーとデータ センターへのトラフィックを最適化するだけではなくインターネット エッジと、インターネット経由でのトラフィックを最適化するのには以下の注意を支払う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8586-p101">To adopt a cloud-inclusive infrastructure, Contoso's network engineers realized the fundamental shift in the way that network traffic to cloud-based services travels. Instead of only optimizing traffic to on-premises servers and datacenters, equal attention must be paid to optimizing traffic to the Internet edge and across the Internet.</span></span>
  
## <a name="contosos-networking-infrastructure"></a><span data-ttu-id="a8586-107">Contoso 社のネットワーク インフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="a8586-107">Contoso's networking infrastructure</span></span>

<span data-ttu-id="a8586-108">Contoso 社のネットワーク インフラストラクチャは図 1 に示すとおりです。</span><span class="sxs-lookup"><span data-stu-id="a8586-108">Contoso has the networking infrastructure shown in Figure 1.</span></span>
  
<span data-ttu-id="a8586-109">**図 1:Contoso 社の WAN インフラストラクチャ**</span><span class="sxs-lookup"><span data-stu-id="a8586-109">**Figure 1: Contoso's WAN infrastructure**</span></span>

![Contoso 社の本社、地域拠点やサテライト オフィスへリンクする WAN インフラストラクチャ](media/Contoso-Poster/Contoso-WW-Net.png)
  
<span data-ttu-id="a8586-111">図 1 は、世界中の Contoso 社のオフィス、および地域オフィスとサテライト オフィス間の WAN リンクのセットを示しています。</span><span class="sxs-lookup"><span data-stu-id="a8586-111">Figure 1 shows the Contoso's offices across the globe and the set of regional and satellite office WAN links between them.</span></span>
  
<span data-ttu-id="a8586-112">ネットワークの他の要素は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a8586-112">Additional elements of their network are the following:</span></span>
  
- <span data-ttu-id="a8586-113">オンプレミス ネットワーク</span><span class="sxs-lookup"><span data-stu-id="a8586-113">On-premises network</span></span>
    
    <span data-ttu-id="a8586-p102">WAN リンクでは、パリ本社を支店やサテライト オフィスは、スポークとハブの構成を地域のオフィスに接続します。各オフィスには、ルーターは、ホストまたはプライベート IP アドレス空間を使用して、サブネット上のワイヤレス アクセス ポイントにトラフィックを提供します。</span><span class="sxs-lookup"><span data-stu-id="a8586-p102">WAN links connect the Paris headquarters to regional offices and regional offices to satellite offices in a spoke and hub configuration. Within each office, routers deliver traffic to hosts or wireless access points on subnets, which use the private IP address space.</span></span>
    
- <span data-ttu-id="a8586-116">インターネット接続</span><span class="sxs-lookup"><span data-stu-id="a8586-116">Internet connectivity</span></span>
    
    <span data-ttu-id="a8586-p103">各オフィスには独自のプロキシ サーバー経由でインターネットに接続します。これは通常、WAN として実装されても、プロキシ サーバーのパブリック IP アドレスを提供するローカル ISP へのリンクです。</span><span class="sxs-lookup"><span data-stu-id="a8586-p103">Each office has its own Internet connectivity via a proxy server. This is typically implemented as a WAN link to a local ISP that also provides public IP addresses for the proxy server.</span></span>
    
- <span data-ttu-id="a8586-119">インターネット プレゼンス サイト</span><span class="sxs-lookup"><span data-stu-id="a8586-119">Internet presence</span></span>
    
    <span data-ttu-id="a8586-p104">Contoso 社では、contoso.com のパブリック ドメイン名を所有しています。製品を発注する contoso 社の公開 web サイトは、パリのキャンパス内でインターネット接続のデータ センター内のサーバーのセットです。Contoso 社は、/24 を使用してインターネット上のパブリックの IP アドレスの範囲です。</span><span class="sxs-lookup"><span data-stu-id="a8586-p104">Contoso owns the contoso.com public domain name. The Contoso public web site for ordering products is a set of servers in an Internet-connected datacenter in the Paris campus. Contoso uses a /24 public IP address range on the Internet.</span></span>
    
## <a name="contosos-app-infrastructure"></a><span data-ttu-id="a8586-123">Contoso 社のアプリケーション ・ インフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="a8586-123">Contoso's app infrastructure</span></span>

<span data-ttu-id="a8586-124">Contoso 社は、次のようなアプリケーションおよびサーバー インフラストラクチャを設計しました。



</span><span class="sxs-lookup"><span data-stu-id="a8586-124">Contoso has architected its application and server infrastructure for the following:</span></span>
  
<span data-ttu-id="a8586-125">**図 2:Contoso 社の内部アプリケーションのインフラストラクチャ**</span><span class="sxs-lookup"><span data-stu-id="a8586-125">**Figure 2: Contoso's infrastructure for internal applications**</span></span>

![Contoso 社の内部アプリケーションのインフラストラクチャ](media/Contoso-Poster/App-Infra.png)
  
- <span data-ttu-id="a8586-127">サテライト オフィスは、ローカル キャッシュ サーバーを使用して、アクセス頻度の高いドキュメントおよび内部 Web サイトを格納します。</span><span class="sxs-lookup"><span data-stu-id="a8586-127">Satellite offices use local caching servers to store frequently-accessed documents and internal web sites.</span></span>
    
- <span data-ttu-id="a8586-p105">
地域ハブは、地域オフィスとサテライト オフィスに地域アプリケーション サーバーを使用します。これらのサーバーは、パリ本社のサーバーと同期します。</span><span class="sxs-lookup"><span data-stu-id="a8586-p105">Regional hubs use regional application servers for the regional and satellite offices. These servers synchronize with servers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="a8586-130">パリ キャンパスには、組織全体にサービスを提供する集中管理されたアプリケーション サーバーを含むデータセンターが存在します。</span><span class="sxs-lookup"><span data-stu-id="a8586-130">The Paris campus has the datacenters that contain the centralized application servers that serve the entire organization.</span></span>
    
<span data-ttu-id="a8586-p106">サテライト オフィスまたは地域ハブ オフィスのユーザーについては、従業員が必要とするリソースの 60% をサテライト オフィスおよび地域ハブ オフィスのサーバーでまかなうことができます。リソース要求の残りの 40% は、WAN リンク経由でパリ キャンパスに引き継がれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8586-p106">For users in satellite or regional hub offices, 60% of the resources needed by employees can be served by satellite and regional hub office servers. The additional 40% of resource requests must go over the WAN link to the Paris campus.</span></span>
  
## <a name="contosos-network-analysis"></a><span data-ttu-id="a8586-133">Contoso 社のネットワークの分析</span><span class="sxs-lookup"><span data-stu-id="a8586-133">Contoso's network analysis</span></span>

<span data-ttu-id="a8586-134">マイクロソフトのクラウド ソリューションのさまざまなカテゴリに対応するため、ネットワークに必要な変更の contoso 社の分析の結果を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a8586-134">Here are the results of Contoso's analysis of the changes needed on their network to accommodate the different categories of Microsoft's cloud offerings:</span></span>
  
|<span data-ttu-id="a8586-135">**SaaS ソリューションをクラウド: Office 365、EMS、Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="a8586-135">**SaaS cloud offerings: Office 365, EMS, and Dynamics 365**</span></span>|<span data-ttu-id="a8586-136">**Azure PaaS: モバイル アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="a8586-136">**Azure PaaS: Mobile applications**</span></span>|<span data-ttu-id="a8586-137">**Azure IaaS: サーバー ベースのワークロード**</span><span class="sxs-lookup"><span data-stu-id="a8586-137">**Azure IaaS: Server-based workloads**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="a8586-138">ユーザーによる SaaS サービスの導入を成功させるためには、インターネットまたは直接的な Microsoft クラウド サービスへの可用性および効率性の高い接続が必要となります。
</span><span class="sxs-lookup"><span data-stu-id="a8586-138">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>  <br/> <span data-ttu-id="a8586-139">モバイル ユーザーについては、現在のインターネット アクセスが適切であると見なされます。
</span><span class="sxs-lookup"><span data-stu-id="a8586-139">For mobile users, their current Internet access is assumed to be adequate.</span></span>  <br/> <span data-ttu-id="a8586-140">Contoso イントラネット上のユーザーの各オフィスを分析され、インターネットへのスループットと Office 365、EMS、Dynamics 365 のテナントをホストしている Microsoft のヨーロッパのデータ センターへの往復時間の最適化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8586-140">For users on the Contoso intranet, each office must be analyzed and optimized for throughput to the Internet and round-trip times to Microsoft's Europe datacenter hosting the Office 365, EMS, and Dynamics 365 tenants.</span></span>  <br/> |<span data-ttu-id="a8586-p107">モバイル ユーザーのサポートを強化するため、レガシ アプリと一部のファイル共有サイトを再構築し、Azure PaaS アプリとして展開しています。最適なパフォーマンスを実現するため、Contoso 社は世界中にある複数の Azure データセンターから新しいアプリを展開する予定です。Azure Traffic Manager は、モバイル ユーザーから発信されたものかオフィスのコンピューターから発信されたものかに関わらず、クライアント アプリの要求を、アプリをホストする最も近い地域の Azure データセンターに送信します。</span><span class="sxs-lookup"><span data-stu-id="a8586-p107">To better support mobile workers, legacy apps and some file sharing sites are being reworked and deployed as Azure PaaS apps. For optimum performance, Contoso plans to deploy the new apps from multiple Azure datacenters across the world. Azure Traffic Manager to send client app requests, whether they originate from a mobile user or a computer in the office, to the nearest Azure datacenter hosting the app.</span></span>  <br/>  <span data-ttu-id="a8586-144"> 

IT 部門は、PaaS アプリケーションのパフォーマンスおよびトラフィック分散をネットワーク正常性監視ソリューションに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8586-144">The IT department will need to add PaaS application performance and traffic distribution to their network health monitoring solution.</span></span> <br/> |<span data-ttu-id="a8586-145">パリ キャンパスのデータセンターからいくつかのレガシ サーバーおよびアーカイブ サーバーを移動し、四半期末の処理に必要なサーバーを追加するために、Contoso 社は、Azure インフラストラクチャ サービスで実行されている仮想マシンを使用する予定です。 

</span><span class="sxs-lookup"><span data-stu-id="a8586-145">To move some legacy and archival servers out of the Paris campus datacenters and add servers as needed for quarter-end processing, Contoso plans to use virtual machines running in Azure infrastructure services.</span></span>  <br/> <span data-ttu-id="a8586-146">これらのサーバーを含む Azure Virtual Network は、重複しないアドレス空間、ルーティング、統合 DNS 用に設計する必要があります。

</span><span class="sxs-lookup"><span data-stu-id="a8586-146">The Azure virtual networks that contain these servers must be designed for non-overlapping address spaces, routing, and integrated DNS.</span></span>  <br/> <span data-ttu-id="a8586-147">IT 部門は、これらの新しいサーバーをネットワーク管理および監視システムに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8586-147">The IT department must include these new servers in their network management and monitoring system.</span></span>  <br/> |
   
## <a name="contosos-use-of-expressroute"></a><span data-ttu-id="a8586-148">Contoso 社の ExpressRoute を使用</span><span class="sxs-lookup"><span data-stu-id="a8586-148">Contoso's use of ExpressRoute</span></span>

<span data-ttu-id="a8586-p108">ExpressRoute は、マイクロソフトのクラウド ネットワークに、ネットワークを接続している Microsoft のピアリングの場所に自分の場所から専用の WAN 接続です。ExpressRoute 接続では、予測可能なパフォーマンスと 99.9% の稼働時間 SLA を提供します。.</span><span class="sxs-lookup"><span data-stu-id="a8586-p108">ExpressRoute is a dedicated WAN connection from your location to a Microsoft peering location that connects your network to the Microsoft cloud network. ExpressRoute connections provide predictable performance and a 99.9% uptime SLA. .</span></span>
  
<span data-ttu-id="a8586-p109">ExpressRoute 接続の場合では、マイクロソフトのクラウド ネットワークと同じ大陸のすべての Microsoft データ センターの場所に接続しています。ピアリング クラウド ストレージの場所とコピー先のマイクロソフトのデータ センター間のトラフィックがマイクロソフト クラウド ネットワーク経由で実行されます。</span><span class="sxs-lookup"><span data-stu-id="a8586-p109">With an ExpressRoute connection, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network</span></span>
  
<span data-ttu-id="a8586-154">**図 3:全世界をカバーする Microsoft のクラウド ネットワーク**</span><span class="sxs-lookup"><span data-stu-id="a8586-154">**Figure 3: The Microsoft cloud network worldwide**</span></span>

![全世界をカバーする Microsoft のクラウド ネットワーク](media/Contoso-Poster/MS-WW-Cloud.png)
  
<span data-ttu-id="a8586-156">図 3 は、世界中のさまざまな地域の相互接続された Microsoft のクラウド ネットワークを示しています。</span><span class="sxs-lookup"><span data-stu-id="a8586-156">Figure 3 shows the interconnected Microsoft cloud network for the various regions of the world.</span></span>
  
<span data-ttu-id="a8586-p110">ExpressRoute Premium では、どの大陸にある Microsoft ピアリングの場所からでも、あらゆる大陸にある任意の Microsoft データセンターに到達できます。大陸間のトラフィックは、Microsoft クラウド ネットワークを通じて転送されます。</span><span class="sxs-lookup"><span data-stu-id="a8586-p110">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="a8586-159">マイクロソフトのクラウド サービスへの現在および将来のトラフィックの分析に基づき、contoso 社がネットワーク評価を実行し、プライベートおよびパブリックのピアリングを使用して、Azure のリソースにアクセスするための任意の (MPLS ベースの) ExpressRoute 接続を実装ヨーロッパのマイクロソフトのピアリングの場所にパリの本社からの関係です。</span><span class="sxs-lookup"><span data-stu-id="a8586-159">Based on the analysis of current and future traffic to Microsoft's cloud offerings, Contoso has performed a network assessment and implemented an any-to-any (MPLS-based) ExpressRoute connection for access to Azure resources, with private and public peering relationships, from the Paris headquarters to the Microsoft peering location in Europe.</span></span>
  
<span data-ttu-id="a8586-160">この接続により、Contoso 社の IT 部門は次を実現できます。</span><span class="sxs-lookup"><span data-stu-id="a8586-160">This connection will give Contoso's IT department:</span></span>
  
- <span data-ttu-id="a8586-161">分散 Azure PaaS アプリの管理における一貫したパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="a8586-161">Consistent performance for administration of distributed Azure PaaS apps</span></span>
    
    <span data-ttu-id="a8586-p111">すべて contoso 社のアプリケーションの開発者と IT の中核となるインフラストラクチャの管理者は、パリのキャンパスで。Azure PaaS アプリケーションが世界中のさまざまな Azure データ センターに分散、contoso 社のアプリケーションおよびドキュメントの TB のストレージ ・ リソースを管理するのにはパリのキャンパスからの一貫したパフォーマンス必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8586-p111">All of Contoso's application developers and core infrastructure IT administrators are in the Paris campus. With Azure PaaS apps distributed to different Azure datacenters around the world, Contoso needs consistent performance from the Paris campus to administer the apps and their storage resources, which consist of TB of documents.</span></span>
    
- <span data-ttu-id="a8586-164">Azure IaaS 内のサーバー管理における一貫したパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="a8586-164">Consistent performance for administration of servers in Azure IaaS</span></span>
    
    <span data-ttu-id="a8586-p112">パリのキャンパスでは、contoso 社のデータ センターの管理者と、Azure に配置するサーバーは、パリのデータ センターの拡張機能です。Contoso 社では、レガシ アプリケーションおよびアーカイブ ・ ストレージにアクセスするため、四半期末の処理のためにこれらの新しいサーバーへの一貫したパフォーマンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="a8586-p112">Contoso's datacenter administrators are in the Paris campus and the servers to be deployed in Azure are an extension of the Paris datacenter. Contoso needs consistent performance to these new servers for access to legacy apps and archival storage and for end-of-quarter processing.</span></span>
    
## <a name="contosos-path-to-cloud-networking-readiness"></a><span data-ttu-id="a8586-167">Contoso 社のクラウド対応のネットワーク パス</span><span class="sxs-lookup"><span data-stu-id="a8586-167">Contoso's path to cloud networking readiness</span></span>

<span data-ttu-id="a8586-168">Contoso 社は、Microsoft クラウド用に自社のネットワークを準備するために、次の手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="a8586-168">Contoso uses the following steps to ready their network for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="a8586-169">インターネット アクセスのために従業員のコンピューターを最適化する
</span><span class="sxs-lookup"><span data-stu-id="a8586-169">Optimize employee computers for Internet access</span></span>
    
    <span data-ttu-id="a8586-170">個々のコンピューターで、最新の TCP/IP スタック、ブラウザー、NIC のドライバー、セキュリティとオペレーティング システムの更新プログラムがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a8586-170">Individual computers will be checked to ensure that the latest TCP/IP stack, browser, NIC drivers, and security and operating system updates are installed.</span></span>
    
2. <span data-ttu-id="a8586-171">各オフィスでのインターネット接続の使用率を分析し、必要に応じて増加させる</span><span class="sxs-lookup"><span data-stu-id="a8586-171">Analyze Internet connection utilization at each office and increase as needed</span></span>
    
    <span data-ttu-id="a8586-172">
オフィスごとに現在のインターネットの使用状況が分析され、70% 以上の使用率で動作している場合は、WAN リンクの帯域幅を増やします。</span><span class="sxs-lookup"><span data-stu-id="a8586-172">Each office will be analyzed for the current Internet usage and WAN link bandwidth will be increased if operating at 70% or above utilization.</span></span>
    
3. <span data-ttu-id="a8586-173">最適なパフォーマンスについて各オフィスの DMZ システムを分析する
</span><span class="sxs-lookup"><span data-stu-id="a8586-173">Analyze DMZ systems at each office for optimal performance</span></span>
    
    <span data-ttu-id="a8586-p113">最適なパフォーマンスについて、インターネット パス内のファイアウォール、IDS、その他のシステムが分析されます。必要に応じて、プロキシ サーバーが更新またはアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="a8586-p113">Firewalls, IDSs, and other systems in the Internet path will be analyzed for optimal performance. Proxy servers will be updated or upgraded as needed.</span></span>
    
4. <span data-ttu-id="a8586-176">パリ キャンパス用に ExpressRoute を追加する</span><span class="sxs-lookup"><span data-stu-id="a8586-176">Add ExpressRoute for the Paris campus</span></span>
    
    <span data-ttu-id="a8586-177">Azure PaaS と IaaS のワークロードを管理するための Azure リソースへの一貫したアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="a8586-177">Provides consistent access to Azure resources for administration of Azure PaaS and IaaS workloads.</span></span>
    
5. <span data-ttu-id="a8586-178">Azure PaaS アプリ用に Azure Traffic Manager プロファイルを作成してテストする</span><span class="sxs-lookup"><span data-stu-id="a8586-178">Create and test an Azure Traffic Manager profile for Azure PaaS apps</span></span>
    
    <span data-ttu-id="a8586-179">地域の各場所へのインターネット トラフィックの分散を体験するために、パフォーマンス ルーティング メソッドを使用する Azure Traffic Manager プロファイルをテストします。</span><span class="sxs-lookup"><span data-stu-id="a8586-179">Test an Azure Traffic Manager profile that uses the performance routing method to gain experience in distributing Internet traffic to regional locations.</span></span>
    
6. <span data-ttu-id="a8586-180">Azure VNet 用にプライベート アドレス空間を予約する
</span><span class="sxs-lookup"><span data-stu-id="a8586-180">Reserve private address space for Azure VNets</span></span>
    
    <span data-ttu-id="a8586-181">予測される Azure IaaS の短期的および長期的なサーバーの数に基づき、Azure VNet およびそのサブネット用にプライベート アドレス空間を予約します。</span><span class="sxs-lookup"><span data-stu-id="a8586-181">Based on the numbers of projected short and long-term servers in Azure IaaS, reserve private address space for Azure VNets and their subnets.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a8586-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8586-182">See Also</span></span>

[<span data-ttu-id="a8586-183">Microsoft Cloud の Contoso</span><span class="sxs-lookup"><span data-stu-id="a8586-183">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="a8586-184">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="a8586-184">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="a8586-185">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="a8586-185">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



