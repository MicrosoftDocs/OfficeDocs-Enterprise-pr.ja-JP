---
title: "アクセス可能な図 - Microsoft Azure に対する SharePoint の障害復旧"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: "この資料は、「Microsoft Azure に対する SharePoint の障害復旧」という名前の図のアクセス可能なテキスト バージョンです。"
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="24033-103">アクセス可能な図 - Microsoft Azure に対する SharePoint の障害復旧</span><span class="sxs-lookup"><span data-stu-id="24033-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="24033-104">**概要:** この資料は、「Microsoft Azure に対する SharePoint の障害復旧」という名前の図のアクセス可能なテキスト バージョンです。</span><span class="sxs-lookup"><span data-stu-id="24033-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="24033-105">このポスターは、Azure で回復環境を構築するためのアーキテクチャの例を示します。</span><span class="sxs-lookup"><span data-stu-id="24033-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="24033-106">Azure 回復環境のあるオンプレミスの環境</span><span class="sxs-lookup"><span data-stu-id="24033-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="24033-107">この図は、Azure を回復に使用するオンプレミス環境の運用環境のためのアーキテクチャの例を示します。</span><span class="sxs-lookup"><span data-stu-id="24033-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="24033-108">オンプレミスの運用環境</span><span class="sxs-lookup"><span data-stu-id="24033-108">On-premises production environment</span></span>

<span data-ttu-id="24033-109">付属する図は、サーバー ファーム内の 4 つの階層のある実際の運用環境サーバーを示します。</span><span class="sxs-lookup"><span data-stu-id="24033-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="24033-110">階層 1</span><span class="sxs-lookup"><span data-stu-id="24033-110">Tier 1</span></span>

<span data-ttu-id="24033-p101">フロント エンド サービスとクエリ処理の 2 つのサーバーがあります。両方のサーバーのレプリカを提供するインデックス パーティションがあります。</span><span class="sxs-lookup"><span data-stu-id="24033-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="24033-113">階層 2</span><span class="sxs-lookup"><span data-stu-id="24033-113">Tier 2</span></span>

<span data-ttu-id="24033-114">この層内には、分散キャッシュの 2 つのサーバーがあります。</span><span class="sxs-lookup"><span data-stu-id="24033-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="24033-115">階層 3</span><span class="sxs-lookup"><span data-stu-id="24033-115">Tier 3</span></span>

<span data-ttu-id="24033-p102">この階層には 3 つのサーバーがあります。各サーバーは、次のサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="24033-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="24033-118">バックエンド サービス</span><span class="sxs-lookup"><span data-stu-id="24033-118">Backend services</span></span> 
    
- <span data-ttu-id="24033-119">管理者</span><span class="sxs-lookup"><span data-stu-id="24033-119">Admin</span></span> 
    
- <span data-ttu-id="24033-120">Workflow Manager</span><span class="sxs-lookup"><span data-stu-id="24033-120">Workflow manager</span></span> 
    
- <span data-ttu-id="24033-121">クロール</span><span class="sxs-lookup"><span data-stu-id="24033-121">Crawl</span></span> 
    
- <span data-ttu-id="24033-122">コンテンツ処理</span><span class="sxs-lookup"><span data-stu-id="24033-122">Content processing</span></span> 
    
- <span data-ttu-id="24033-123">分析</span><span class="sxs-lookup"><span data-stu-id="24033-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="24033-124">階層 4</span><span class="sxs-lookup"><span data-stu-id="24033-124">Tier 4</span></span>

<span data-ttu-id="24033-p103">この階層には 2 つのサーバーがあります。両方のサーバーには次のような 3 つの可用性グループがあります。</span><span class="sxs-lookup"><span data-stu-id="24033-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="24033-127">可用性グループ 1 は検索機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="24033-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="24033-128">可用性グループ 2 は、コンテンツ、構成、およびサービス アプリケーションを提供します。</span><span class="sxs-lookup"><span data-stu-id="24033-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="24033-129">可用性グループ 3 はコンテンツを提供します。</span><span class="sxs-lookup"><span data-stu-id="24033-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="24033-p104">この階層には、ファイル共有サーバーもあります。階層 4 のサーバーは、このサーバーと通信するためにログ配布を使用します。次いで、このサーバーは、次のセクションで説明するように、通信分散ファイル システム レプリケーション (DFSR) 経由で、Azure ウォーム スタンバイ回復環境のファイル共有サーバーと通信します。</span><span class="sxs-lookup"><span data-stu-id="24033-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="24033-133">Azure 回復環境</span><span class="sxs-lookup"><span data-stu-id="24033-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="24033-134">仮想マシンを実行するウォーム スタンバイ環境</span><span class="sxs-lookup"><span data-stu-id="24033-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="24033-p105">付属する図は、Azure 回復環境に正確に複製されたオンプレミス環境を示します。この環境でのファイル共有サーバーは、オンプレミス環境に DFSR でリンクされます。DFSR は、ファイル共有サーバーにより、ログを運用環境から回復環境に転送します。</span><span class="sxs-lookup"><span data-stu-id="24033-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="24033-138">概要</span><span class="sxs-lookup"><span data-stu-id="24033-138">Overview</span></span>

<span data-ttu-id="24033-139">オンプレミス SharePoint 2013 ファームの障害復旧環境は、Azure でホストできます。</span><span class="sxs-lookup"><span data-stu-id="24033-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="24033-140">Azure インフラストラクチャ サービスは、セカンダリ データ センターを提供します。</span><span class="sxs-lookup"><span data-stu-id="24033-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="24033-141">支払いは、使用したリソースの分だけです。</span><span class="sxs-lookup"><span data-stu-id="24033-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="24033-142">小規模の回復ファームは、障害後に目標とする規模と容量に合わせてスケール アウトできます。</span><span class="sxs-lookup"><span data-stu-id="24033-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="24033-143">Azure の回復ファームは、オンプレミスの運用ファームと可能な限り同じように構成されます。</span><span class="sxs-lookup"><span data-stu-id="24033-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="24033-144">サーバー ロールの同じ表現。</span><span class="sxs-lookup"><span data-stu-id="24033-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="24033-145">カスタマイズの同じ構成。</span><span class="sxs-lookup"><span data-stu-id="24033-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="24033-146">検索機能の同じ構成 (より小さいバージョンの運用ファーム上に構成できます)。</span><span class="sxs-lookup"><span data-stu-id="24033-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="24033-147">ログ配布と DFSR を使用して、データベース バックアップとトランザクション ログを Azure ファームへコピーします。</span><span class="sxs-lookup"><span data-stu-id="24033-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="24033-p106">DFSR を使用して、ログを運用環境から復旧環境に転送します。WAN シナリオの場合、DFSR の方が、ログを Azure 内のセカンダリ サーバーに直接配布するよりも効率的です。</span><span class="sxs-lookup"><span data-stu-id="24033-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="24033-150">Azure ベースの SQL Server コンピューターにログが再生されます。</span><span class="sxs-lookup"><span data-stu-id="24033-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="24033-151">ログ配布データベースは、復旧手順を実行するまで、ファームに接続されません。</span><span class="sxs-lookup"><span data-stu-id="24033-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="24033-152">フェイル オーバー手順:</span><span class="sxs-lookup"><span data-stu-id="24033-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="24033-153">ログ配布を停止します。</span><span class="sxs-lookup"><span data-stu-id="24033-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="24033-154">プライマリ ファームへのトラフィックの受け入れを停止します。</span><span class="sxs-lookup"><span data-stu-id="24033-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="24033-155">最後のトランザクション ログを再生します。</span><span class="sxs-lookup"><span data-stu-id="24033-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="24033-156">コンテンツ データベースをファームに接続します。</span><span class="sxs-lookup"><span data-stu-id="24033-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="24033-157">フル クロールを開始します。</span><span class="sxs-lookup"><span data-stu-id="24033-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="24033-158">レプリケートされたサービス データベースに基づいてサービス アプリケーションを復元します。</span><span class="sxs-lookup"><span data-stu-id="24033-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="24033-159">このソリューションによって提供される回復目標は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="24033-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="24033-160">サイトおよびコンテンツ</span><span class="sxs-lookup"><span data-stu-id="24033-160">Sites and content</span></span> 
    
- <span data-ttu-id="24033-161">検索 (再クロールされます。検索履歴はありません)</span><span class="sxs-lookup"><span data-stu-id="24033-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="24033-162">サービス</span><span class="sxs-lookup"><span data-stu-id="24033-162">Services</span></span>
    
<span data-ttu-id="24033-163">マイクロソフト コンサルティング サービスまたはパートナーによって対処できる追加項目:</span><span class="sxs-lookup"><span data-stu-id="24033-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="24033-164">カスタム ファーム ソリューションの同期</span><span class="sxs-lookup"><span data-stu-id="24033-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="24033-165">オンプレミスのデータ ソースへの接続 (ビジネス データ接続 (BDC) と検索コンテンツ ソース)</span><span class="sxs-lookup"><span data-stu-id="24033-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="24033-166">検索の復元シナリオ</span><span class="sxs-lookup"><span data-stu-id="24033-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="24033-167">回復時刻の目標 (RTO) と回復ポイントの目標 (RPO)</span><span class="sxs-lookup"><span data-stu-id="24033-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="24033-168">仮想マシンを実行するコールド スタンバイ環境</span><span class="sxs-lookup"><span data-stu-id="24033-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="24033-169">コールド スタンバイ環境は、起動に長い時間がかかりますが費用が安くてすみます。</span><span class="sxs-lookup"><span data-stu-id="24033-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="24033-p107">ファームが完全にビルドされますが、ファームの作成後に仮想マシンが停止します。処理コストが発生するのは仮想マシンの実行中のみですが、ストレージとネットワーク データ転送のコストはかかります。</span><span class="sxs-lookup"><span data-stu-id="24033-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="24033-172">障害時には、ファーム内のすべての仮想マシンを開始し修正プログラムを適用します。</span><span class="sxs-lookup"><span data-stu-id="24033-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="24033-173">バックアップとトランザクション ログがファーム データベースに適用されます。</span><span class="sxs-lookup"><span data-stu-id="24033-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="24033-174">コールド スタンバイ環境の追加の手順を次に示します。</span><span class="sxs-lookup"><span data-stu-id="24033-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="24033-175">仮想マシンの電源を定期的に入れ、修正、更新、環境の検証を行います。</span><span class="sxs-lookup"><span data-stu-id="24033-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="24033-176">DNS および IP アドレスを更新する手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="24033-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="24033-177">フェールオーバー後に SQL AlwaysOn を設定します。</span><span class="sxs-lookup"><span data-stu-id="24033-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="24033-p108">付属の図は、仮想マシン上のレプリケートされた回復環境を示します。コールド スタンバイ環境へのフェイル オーバー後、すべての仮想マシンが起動し、データベース サーバーを使用可能にする再生ログを使用して可用性グループを構成します。</span><span class="sxs-lookup"><span data-stu-id="24033-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="24033-180">Azure における SharePoint 回復環境</span><span class="sxs-lookup"><span data-stu-id="24033-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="24033-181">Azure でのフェールオーバー環境の設計と作成。</span><span class="sxs-lookup"><span data-stu-id="24033-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="24033-182">Azure で仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="24033-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="24033-p109">サイト間の VPN 接続によって、オンプレミスのネットワークを Azure の仮想ネットワークに接続します。この接続は Azure の動的なゲートウェイを使用します。</span><span class="sxs-lookup"><span data-stu-id="24033-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="24033-p110">1 つ以上のドメイン コントローラーを Azure 仮想ネットワークにデプロイし、オンプレミスのドメインと連携するよう構成します。これらのドメイン コントローラーはカタログ サーバーです。</span><span class="sxs-lookup"><span data-stu-id="24033-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="24033-187">SharePoint ファームをクラウド サービスと可用性の設定に適合させます。</span><span class="sxs-lookup"><span data-stu-id="24033-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="24033-188">SharePoint ファームとファイル サーバーをデプロイして、ファイル共有をホストします。</span><span class="sxs-lookup"><span data-stu-id="24033-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="24033-189">オンプレミス環境と Azure ベースの回復環境の間に、ログ配布と DFSR を設定します。</span><span class="sxs-lookup"><span data-stu-id="24033-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="24033-190">付属の図は、次の機能のある、オンプレミス環境と Azure 仮想ネットワークを示します。</span><span class="sxs-lookup"><span data-stu-id="24033-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="24033-191">社内環境</span><span class="sxs-lookup"><span data-stu-id="24033-191">On-premises environment</span></span>

- <span data-ttu-id="24033-192">Windows Server 2012 RRAS</span><span class="sxs-lookup"><span data-stu-id="24033-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="24033-193">Active Directory サーバー</span><span class="sxs-lookup"><span data-stu-id="24033-193">Active Directory server</span></span> 
    
<span data-ttu-id="24033-194">オンプレミスのネットワークは、仮想プライベート ネットワーク (VPN) ゲートウェイ経由で Azure 仮想ネットワークとインターフェイスをとります。</span><span class="sxs-lookup"><span data-stu-id="24033-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="24033-195">Azure 仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="24033-195">Azure virtual network</span></span>

<span data-ttu-id="24033-196">VPN ゲートウェイは、アクティブな VPN ゲートウェイのサブネットとインターフェイスをとります。</span><span class="sxs-lookup"><span data-stu-id="24033-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="24033-197">Azure 仮想ネットワークには 3 つのクラウド サービスがあります。</span><span class="sxs-lookup"><span data-stu-id="24033-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="24033-198">最初のクラウド サービスには、Active Directory サーバーと DNS サーバーという 2 つのサーバーと、1 つの可用性セットがあります。</span><span class="sxs-lookup"><span data-stu-id="24033-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="24033-p111">2 番目のクラウド サービスには、3 つのサーバー セットがあります。 2 つの分散キャッシュ サーバーと 1 つの可用性セット。 2 つの分散フロントエンド サーバーと 1 つの可用性セット。 3 つのバックエンド サーバーと 1 つの可用性セット。</span><span class="sxs-lookup"><span data-stu-id="24033-p111">The second cloud service has three sets of servers: Two distributed cache servers with an availability set. Two front-end servers with an availability set. Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="24033-p112">3 番目のクラウド サービスには、3 つのデータベース サーバーと 1 つの可用性セットがあります。これらのデータベース サーバーの 1 つは、ログ配布のファイル共有と SQL Server AlwaysOn のノード マジョリティの 3 番目のノードです。</span><span class="sxs-lookup"><span data-stu-id="24033-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="24033-204">AD DS ハイブリッド環境の構築</span><span class="sxs-lookup"><span data-stu-id="24033-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="24033-205">このソリューションの AD DS の構成は、ハイブリッド展開のシナリオを構成しています。このシナリオでは、AD DS はオンプレミスに部分的にデプロイされ、Azure 仮想マシンに部分的にデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="24033-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="24033-206">重要 — AD DS を Azure にデプロイする前に、「Microsoft Azure Virtual Machines での Windows Server Active Directory のデプロイ ガイドライン  (http://msdn.microsoft.com/ja-jp/library/windowsazure/jj156090.aspx)」をお読みください。</span><span class="sxs-lookup"><span data-stu-id="24033-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="24033-207">Active Directory 環境の設計およびデプロイに関する詳細なガイダンスについては、http://TechNet.microsoft.com を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24033-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="24033-p113">この参照アーキテクチャには、ドメイン コントローラーとして構成されている 2 つの仮想マシンが含まれています。それぞれ次のように構成されます。</span><span class="sxs-lookup"><span data-stu-id="24033-p113">This reference architecture includes two virtual machines configured as domain controllers. Each is configured as follows:</span></span> 
  
- <span data-ttu-id="24033-210">サイズ — 小。</span><span class="sxs-lookup"><span data-stu-id="24033-210">Size — Small.</span></span> 
    
- <span data-ttu-id="24033-211">オペレーティング システム — Windows Server 2012。</span><span class="sxs-lookup"><span data-stu-id="24033-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="24033-p114">ロール  グローバル カタログ サーバーとして割り当てられる AD DS ドメイン コントローラー。この構成は、VPN 接続経由の出力トラフィックを減少させます。変更度の高い複数ドメイン環境では、ドメイン コントローラーをオンプレミスで構成して、Azure のグローバル カタログ サーバーと同期しないようにします。</span><span class="sxs-lookup"><span data-stu-id="24033-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="24033-p115">データ ディスク  AD DS データベース、ログ、SYSVOL を Azure データ ディスクに配置します。オペレーティング システム ディスク、または Azure によって提供される一時ディスクには配置しないでください。これは重要です。</span><span class="sxs-lookup"><span data-stu-id="24033-p115">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure. This is important.</span></span> 
    
- <span data-ttu-id="24033-218">ロール  ドメイン コントローラーに Windows DNS をインストールして構成します。</span><span class="sxs-lookup"><span data-stu-id="24033-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="24033-p116">IP アドレス  動的 IP アドレスを使用します。そのため、Azure Virtual Network を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24033-p116">IP addresses — Use dynamic IP addresses. This requires you to create an Azure Virtual Network.</span></span> 
    

