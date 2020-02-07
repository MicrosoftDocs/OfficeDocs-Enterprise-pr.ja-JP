---
title: アクセス可能な図 - Microsoft Office Server 製品のネットワーク統合
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
f1.keywords:
- NOCSH
description: この記事は、「Microsoft Office Server 製品のネットワーク統合」という名前の図のアクセス可能なテキスト バージョンです。
ms.openlocfilehash: def94a4523ad78676d6a9532a60dcba78032f23b
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843868"
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="bb93b-103">アクセス可能な図 - Microsoft Office Server 製品のネットワーク統合</span><span class="sxs-lookup"><span data-stu-id="bb93b-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="bb93b-104">**概要:** この記事は、「Microsoft Office Server 製品のネットワーク統合」という名前の図のアクセス可能なテキスト バージョンです。</span><span class="sxs-lookup"><span data-stu-id="bb93b-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="bb93b-p101">このポスターは Lync Server 2013、SharePoint 2013、および Exchange Server 2013 を含むネットワーク環境の概要図を示しています。また、これらの製品に共通のネットワーク要素である、リモート アクセスと内部アクセス、認証、クライアントのトラフィック、共有デバイス経由のトラフィックのルーティングについても説明しています。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="bb93b-107">Lync、Exchange、SharePoint サーバー、および Office Web Apps の大まかな概念</span><span class="sxs-lookup"><span data-stu-id="bb93b-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="bb93b-108">設計について</span><span class="sxs-lookup"><span data-stu-id="bb93b-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="bb93b-109">効率的なネットワーク設計</span><span class="sxs-lookup"><span data-stu-id="bb93b-109">Streamlined network design</span></span>

<span data-ttu-id="bb93b-p102">このトポロジは、SharePoint 2013、Exchange Server 2013、および Lync Server 2013 のオンプレミスのネットワーク展開を示しています。また、インターネットからの簡易メール転送プロトコル (SMTP) の受信トラフィック用のスパムやマルウェア保護を提供する、マイクロソフト クラウド ベースのサービスの Exchange Online Protection の使用法も示しています。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="bb93b-p103">このネットワーク設計は、ネットワーク機能の最小セットになるよう合理化されています。この設計は、一部の組織が必要とするアカウント追加セキュリティやインフラストラクチャ機能は考慮していません。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="bb93b-114">この図では次のようになっています。</span><span class="sxs-lookup"><span data-stu-id="bb93b-114">This diagram:</span></span> 
  
- <span data-ttu-id="bb93b-115">ゲートウェイ ルーターとクライアント セッションのトラフィック (外部および内部) の負荷分散を経由し、適切な SharePoint、Exchange、および Lync サーバー階層に到達する受信および送信トラフィックを示すネットワーク トポロジの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="bb93b-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="bb93b-116">ローミングやリモートの従業員に対して安全な通信を提供するための、サード パーティ製 VPN ゲートウェイや DirectAccess サーバーなどのオプションのリモート アクセス サーバーの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="bb93b-117">SharePoint、Exchange、および Lync のクライアントから各プラットフォーム サーバー層へのトラフィック フローの詳細を示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="bb93b-118">(パートナーまたは従業員などの) クライアント ベースのリモートおよび内部アクセスの接続の種類と、使用される認証方法を識別します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="bb93b-119">フロント エンド、アプリケーション、データベース、および他のレベルを識別する、必要なサーバーの役割によって、SharePoint、Exchange、および Lync プラットフォームを分割します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="bb93b-p104">SharePoint、Lync、および Exchange のためにここで使用されるアーキテクチャは、これらのプラットフォームの実装の推奨方法を示すものではありません。トポロジは固有のネットワーク要件やセキュリティ上の考慮事項に応じて異なるため、これらは単に例を示しているにすぎません。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="bb93b-122">ゲートウェイ ルーター</span><span class="sxs-lookup"><span data-stu-id="bb93b-122">Gateway router</span></span>

<span data-ttu-id="bb93b-p105">このトポロジでは、ゲートウェイ ルーターはネットワークの端にあり、イントラネットのすべての着信および発信トラフィックをルーティングしています。また、ゲートウェイ ルーターと、図の複数のレイヤーのファイアウォールなどのロード バランサーのギャップを埋める、ほかのコンポーネントが存在する可能性もあります。このトポロジは、ネットワークを展開する多数の方法の 1 つを表しているにすぎません。この構成では、ルーター インターフェイス上の IP ベースの固有の着信および発信トラフィックを許可するアクセス制御リスト (ACL) を使用して、ゲートウェイが構成されています。ACL、高度な検査、またはネットワーク アドレス変換 (NAT) も、ネットワーク全体のファイアウォールなどのほかのデバイス上で実行できます。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="bb93b-128">ロード バランサーとリバース プロキシ デバイス</span><span class="sxs-lookup"><span data-stu-id="bb93b-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="bb93b-p106">SharePoint フロント エンド Web サーバーや Exchange クライアント アクセス サーバー (CAS) を含むセグメントのトラフィックをリダイレクトするのに、ハードウェアまたはソフトウェアの負荷分散ソリューションを使用できます。 要求内の cookie またはヘッダー情報のような情報を使用することでパフォーマンスが向上することがあるため、永続性の要件のためにレイヤー 7 のハードウェア ベースのロード バランサーを使用するのが最適な場合があります。ただし、コストと使用率の増加、ソリューションからの負荷などの要因により、特定のニーズには適さない可能性もあります。SharePoint、Exchange、および Lync での負荷分散では、次の点を検討します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="bb93b-p107">SharePoint - SharePoint 2013 では、フロント エンド Web サーバーのアフィニティを有効にする必要はありません。通常、これはスティッキー セッションの作成に使用され、各フロント エンド Web サーバーにクライアントから複数の認証要求を行うことを回避するために使用されます。SharePoint 2013 の新しい分散キャッシュ サービスは、SharePoint ファームの Web サーバー間のログオン トークンを保存して配布します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="bb93b-p108">Exchange - Exchange 2013 では、レイヤー 4 ロード バランシングを使用して、トランスポート層で要求を分散するよう CA の役割が設計されています。これにより、ロード バランサーの使用率と作業負荷を大幅に削減することができます。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="bb93b-p109">Lync - Lync のプールの セッション開始プロトコル (SIP) トラフィックでは、ドメイン ネーム システム (DNS) の負荷分散が推奨されています。ハードウェア負荷分散 (HLB) は、Lync Web (HTTPS) トラフィックのために必要です。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="bb93b-140">リモート アクセスのオプション</span><span class="sxs-lookup"><span data-stu-id="bb93b-140">Remote access options</span></span>

<span data-ttu-id="bb93b-p110">イントラネット リソースをインターネット上のパートナーのために発行したり、リモート ユーザーやローミングの従業員に安全なリモート アクセスを提供したりするための、いくつかのオプションがあります。例として、リバース プロキシ、DirectAccess、サード パーティ製 VPN ゲートウェイなどがあります。このセクションで後述するリモート アクセス ソリューションを、オンプレミス展開の SharePoint、Lync、および Exchange、またはこれらのサーバーの任意の組み合わせに対して選択できます。ただし、特定のソリューションで、一部のリモートのオプションが機能しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="bb93b-p111">リバース プロキシ - リバース プロキシは、Secure Sockets Layer (SSL) などのトラフィックの暗号化をサポートし、インターネットの認証ユーザーとパートナーにイントラネット アプリケーションと Web リソースを公開できます。例として、Microsoft Forefront Unified Access Gateway (UAG) があります。 多くのハードウェア ロード バランサーは、リバース プロキシの機能もサポートします。ただし、トラフィックの分離、セキュリティ区画化、パフォーマンスの最適化などのニーズと要件に応じて、スタンドアロンのソリューションを使用するための有効なシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="bb93b-149">リバース プロキシのメリットと注意事項:</span><span class="sxs-lookup"><span data-stu-id="bb93b-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="bb93b-150">イントラネット リソースにアクセスするパートナーまたはユーザーに、認証およびセキュリティで保護されたアクセスを提供します (クライアントとリバース プロキシ サーバー間で SSL (TCP 443) を使用)。</span><span class="sxs-lookup"><span data-stu-id="bb93b-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="bb93b-p112">Exchange では、Forefront UAG などのリバース プロキシを使用する利点は、Exchange クライアント アクセス サーバーにアクセスする前に事前認証できることです。Outlook Web Access (OWA) などの公開されたアプリケーションを使用するリモート アクセス ユーザーは、基本、NTLM、または Kerberos の方法を使用して、内部ネットワークに到達する前に認証できます。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="bb93b-153">Exchange および SharePoint では、Forefront UAG のようなソリューションが SSL 接続を終了し、内部リソースの負荷を減らしながら、証明書を一か所で管理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="bb93b-p113">Lync では、Web (HTTPS) トラフィックはクライアント通信のためにリバース プロキシ (TCP 443) を経由します。リバース プロキシは、Lync Web Services、Exchange CAS、および Office Web Apps への HTTPS 接続のプロキシを実行します。Lync Server 2013 は UAG をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="bb93b-p114">DirectAccess - インターネット プロトコル セキュリティ (IPsec) を DirectAccess クライアントとサーバー間の認証およびトラフィックの暗号化に使用するリモート アクセス テクノロジ。DirectAccess は接続を開始する必要性無しで、ローミングやリモートの従業員のインターネットとイントラネットの両方のリソースへの同時アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="bb93b-159">DirectAccess の考慮すべき事項:</span><span class="sxs-lookup"><span data-stu-id="bb93b-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="bb93b-160">DirectAccess は、IPsec で保護されたトラフィック (プロトコル 50、51 と UDP 500) を DirectAccess クライアントとサーバー間で使用します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="bb93b-161">Windows Server 2012 と Windows 8 用の DirectAccess では、サーバーとクライアントの認証に公開キー基盤 (PKI) の展開を必要としません。</span><span class="sxs-lookup"><span data-stu-id="bb93b-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="bb93b-162">IPsec の暗号化と復号化に関連するオーディオとビデオの遅延の問題のため、DirectAccess は Lync Server 2013 と共に使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bb93b-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="bb93b-p115">VPN ゲートウェイ - 典型的な VPN ゲートウェイは、トンネルおよびユーザーによる接続を使用してイントラネットにリモート アクセス クライアント コンピューターが論理的に投影されるリモート アクセス接続を提供します。イントラネットへのセキュリティで保護されたアクセスをローミングまたはリモートの従業員に提供するために、Windows Server 2012 のリモート アクセスの統合やサード パーティ製ソリューションを使用できます。VPN は Lync では推奨されません。Lync のリモート トラフィックは、エッジ サーバーとスプリット トンネリングを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="bb93b-167">ドメイン ネーム システム (DNS) の考慮事項</span><span class="sxs-lookup"><span data-stu-id="bb93b-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="bb93b-168">インターネットおよびイントラネットのユーザーが DNS 名を適切な IP アドレスに解決できるように、DNS レコードのセットを計画する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="bb93b-169">インターネット ベースのパートナー、およびローミングやリモートの従業員には、インターネット DNS サーバーに登録された DNS レコードが、ゲートウェイ ルーター、Lync エッジ サーバー、ロード バランサーの仮想 IP アドレス (VIP) のセット、および DirectAccess または VPN ゲートウェイに該当するパブリック IP アドレスのセットへの解決を、必要に応じて提供します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="bb93b-170">イントラネット ベースのユーザーには、イントラネット DNS サーバーに登録されている DNS レコードが、SharePoint、Lync、および Exchange のリソースにアクセスするために、ロード バランサーの仮想 IP アドレス (VIP) のセットへの解決を提供します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="bb93b-p116">DirectAccess クライアントはイントラネットの DNS サーバーを該当するイントラネットの DNS 名前空間の名前に使用し、インターネット DNS サーバーをそれ以外の名前に使用します。DirectAccess の運用を簡素化するために、イントラネットおよびインターネット ベースの名前に別の DNS 名前空間を使用するよう、分割 DNS の実装の使用を検討してください。たとえば、contoso.com をインターネット名前空間に使用し、corp.contoso.com をイントラネット名前空間に使用します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="bb93b-p117">Exchange は、IP 解決のホストが、パブリック ルーティング トラフィックと企業ネットワークで異なる分割 DNS モデルを使用します。最低限、クライアント トラフィックのための OWA、自動検出、ActiveSync の URL の DNS レコードと、受信メールのための MX レコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="bb93b-176">Exchange Online Protection (EOP) を使用している場合、MX レコードは Exchange ファームではなく、そのサービスを指します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="bb93b-177">Exchange では、パブリック DNS に TXT レコードの所有権の証明が必要であり、フェデレーションの共有の設定にフェデレーションの組織 ID が必要です。</span><span class="sxs-lookup"><span data-stu-id="bb93b-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="bb93b-178">リモート アクセス VPN クライアントは、リモート アクセス VPN 接続がアクティブな場合はイントラネットの DNS サーバーだけを使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="bb93b-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="bb93b-179">図の説明</span><span class="sxs-lookup"><span data-stu-id="bb93b-179">Diagram Description</span></span>

<span data-ttu-id="bb93b-p118">この図は、ゲートウェイ ルーターとクライアント セッションのトラフィック (外部および内部) の負荷分散を経由し、適切な SharePoint、Exchange、および Lync サーバー階層に到達する受信および送信トラフィックを示すネットワーク トポロジの例を示しています。この図の説明は次の 2 つの部分に分かれています。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="bb93b-182">図中のコンポーネントの説明</span><span class="sxs-lookup"><span data-stu-id="bb93b-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="bb93b-183">SharePoint、Exchange、Lync、および Office Web Apps サーバー層にコンポーネントを経由してトラフィックを移動する方法の説明。</span><span class="sxs-lookup"><span data-stu-id="bb93b-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="bb93b-184">図中のコンポーネントの説明</span><span class="sxs-lookup"><span data-stu-id="bb93b-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="bb93b-185">ユーザーの種類</span><span class="sxs-lookup"><span data-stu-id="bb93b-185">User types</span></span>

<span data-ttu-id="bb93b-186">4 つの異なる種類のユーザーがあります。ネットワークとクラウド サービスの外部にいる 3 種類のユーザーと内部にいる 1 種類のユーザーがあり、以下のようになっています。</span><span class="sxs-lookup"><span data-stu-id="bb93b-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="bb93b-187">パートナー企業 (企業間) – 外部</span><span class="sxs-lookup"><span data-stu-id="bb93b-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="bb93b-188">個々のパートナー (SharePoint と匿名 (Lync)) – 外部</span><span class="sxs-lookup"><span data-stu-id="bb93b-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="bb93b-189">ローミングとリモートの従業員 – 外部</span><span class="sxs-lookup"><span data-stu-id="bb93b-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="bb93b-190">内部の従業員</span><span class="sxs-lookup"><span data-stu-id="bb93b-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="bb93b-191">クラウド ベースの電子メール トラフィック</span><span class="sxs-lookup"><span data-stu-id="bb93b-191">Cloud-based email traffic</span></span>

<span data-ttu-id="bb93b-192">SMTP ベースの電子メール トラフィックに対して、インターネット メール ホストまたは Exchange Online Protection のいずれかのクラウド ベースのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="bb93b-193">外部アクセスの認証</span><span class="sxs-lookup"><span data-stu-id="bb93b-193">Authentication for external access</span></span>

<span data-ttu-id="bb93b-p119">それぞれの種類のユーザーに対して、Lync、SharePoint、および Exchange の認証手順の特定のセットがあります。それらについては、このドキュメントの後半で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="bb93b-196">ゲートウェイ ルーターと ACL</span><span class="sxs-lookup"><span data-stu-id="bb93b-196">Gateway router with ACLs</span></span>

<span data-ttu-id="bb93b-197">ゲートウェイ ルーターはネットワークの端にあり、イントラネットのすべての着信および発信トラフィックをルーティングします。</span><span class="sxs-lookup"><span data-stu-id="bb93b-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="bb93b-198">Lync と SharePoint のリモート アクセス サーバー</span><span class="sxs-lookup"><span data-stu-id="bb93b-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="bb93b-199">このトポロジには、Lync エッジ サーバーと、SharePoint の VPN ゲートウェイまたは DirectAccess サーバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb93b-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="bb93b-200">ロード バランサーとリバース プロキシ デバイス</span><span class="sxs-lookup"><span data-stu-id="bb93b-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="bb93b-p120">SharePoint フロント エンド Web サーバーや Exchange クライアント アクセス サーバー (CAS) を含むセグメントのトラフィックをリダイレクトするのに、ハードウェアまたはソフトウェアの負荷分散ソリューションを使用できます。このトポロジは、ロード バランサーでの Lync の VIP、SharePoint の VIP、Exchange の VIP のコンポーネントを示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="bb93b-203">サーバー</span><span class="sxs-lookup"><span data-stu-id="bb93b-203">Servers</span></span>

<span data-ttu-id="bb93b-p121">4 台のサーバーがあります。 Lync、SharePoint、Exchange、および Office Web Apps サーバー。 各サーバーは、フロント エンドのクライアント アクセス層、アプリケーション層、およびデータベース/ストレージ層の 3 つの層を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="bb93b-206">フロント エンドのクライアント アクセス層</span><span class="sxs-lookup"><span data-stu-id="bb93b-206">Front-end, client-access tier</span></span>

<span data-ttu-id="bb93b-207">この層には、4 つのすべてのサーバーのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="bb93b-p122">Lync のプール (フロント エンド)。Lync の 2 つのデータベースを図に示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="bb93b-p123">SharePoint フロント エンド、および分散キャッシュ。3 つの SharePoint データベースを図に示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="bb93b-p124">Exchange CAS。2 つの SharePoint データベースを図に示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="bb93b-p125">Office Web Apps サーバー2 つの Office Web Apps データベースを図に示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="bb93b-216">アプリケーション層</span><span class="sxs-lookup"><span data-stu-id="bb93b-216">Application tier</span></span>

<span data-ttu-id="bb93b-217">この層には、SharePoint サーバーのみのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="bb93b-p126">検索 (クエリ、インデックス、管理)。3 つの SharePoint データベースを図に示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="bb93b-p127">バッチ処理。3 つの SharePoint データベースを図に示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="bb93b-222">データベース/ストレージ層</span><span class="sxs-lookup"><span data-stu-id="bb93b-222">Database/storage tier</span></span>

<span data-ttu-id="bb93b-223">この層には、Lync、SharePoint、および Exchange サーバーのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="bb93b-p128">Lync データベース (バックエンド)。Lync の 3 つのデータベースを図に示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="bb93b-p129">SharePoint データベース。3 つの SharePoint データベースを図に示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="bb93b-p130">Exchange メールボックス サーバー。2 つの Exchange メールボックス サーバーを図に示します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="bb93b-230">各 SharePoint サーバーにインストールされているコンポーネントの詳細については、「[SharePoint 2013 の効率化されたトポロジー](https://aka.ms/Ma5cgk)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb93b-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="bb93b-231">トラフィックがコンポーネントを経由して別のサーバー層に移動する方法の説明</span><span class="sxs-lookup"><span data-stu-id="bb93b-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="bb93b-232">このセクションでは、ユーザーの要求がネットワーク トポロジを移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="bb93b-233">外部アクセスのための認証とルーティング</span><span class="sxs-lookup"><span data-stu-id="bb93b-233">Authentication and routing for external access</span></span>

<span data-ttu-id="bb93b-234">ネットワークとクラウド サービスの外部に、次の 3 種類の異なるクライアントがあります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="bb93b-235">パートナー企業 (企業間) – 外部</span><span class="sxs-lookup"><span data-stu-id="bb93b-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="bb93b-236">個々のパートナー (SharePoint と匿名 (Lync)) – 外部</span><span class="sxs-lookup"><span data-stu-id="bb93b-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="bb93b-237">ローミングとリモートの従業員 – 外部</span><span class="sxs-lookup"><span data-stu-id="bb93b-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="bb93b-238">外部ユーザーの種類ごとの認証およびルーティング プロセスを個別に説明します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="bb93b-239">パートナー会社 (企業間) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="bb93b-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="bb93b-p131">Lync: 他の組織、Skype、および AOL を使用したパブリック IM 接続のフェデレーション信頼。Lync のフェデレーション トラフィックは、ゲートウェイ ルーターを介して、Lync エッジ サーバー、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Lync Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bb93b-p132">SharePoint:SAML 認証を使用する信頼できるパートナー ID プロバイダー。SharePoint のクライアント トラフィックは、ゲートウェイ ルーターを介して、SharePoint の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に SharePoint Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="bb93b-p133">Exchange:メール トラフィック用の相互認証 TLS、フェデレーション共有用の SAML 認証。Exchange のクライアント トラフィックは、ゲートウェイ ルーターを介して、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="bb93b-246">SMTP のトラフィックは、ゲートウェイ ルーターを介して、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="bb93b-247">個々のパートナー (SharePoint) と匿名 (Lync) (https://partnerweb.contoso.com および https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="bb93b-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="bb93b-p134">Lync: 匿名ユーザーは従業員別に整理された Lync 会議のみに参加できます。Lync のフェデレーション トラフィックは、ゲートウェイ ルーターを介して、Lync エッジ サーバー、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Lync Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bb93b-p135">SharePoint:SAML 認証またはフォーム ベース認証を使用する信頼できるパートナー ID プロバイダー。SharePoint のクライアント トラフィックは、ゲートウェイ ルーターを介して、SharePoint の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に SharePoint Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="bb93b-252">Exchange: 該当しません。</span><span class="sxs-lookup"><span data-stu-id="bb93b-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="bb93b-253">Lync の Web トラフィックは、ゲートウェイ ルーターを介して、Lync エッジ サーバー、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、ハードウェアのロード バランサー (HTTPS トラフィックで必要)、次に Lync Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="bb93b-254">ローミングとリモートの従業員</span><span class="sxs-lookup"><span data-stu-id="bb93b-254">Roaming and remote employees</span></span>

1. https://intranet.contoso.com 
    
2. https://teams.contoso.com 
    
3. https://my.contoso.com
    
4. https://partnerweb.contoso.com 
    
5. https://mail.contoso.com* 
    
6. https://dial.contoso.com*
    
7. https://meet.contoso.com*
    
* <span data-ttu-id="bb93b-255">Exchange の URL は次の仮想ディレクトリを持っています:Autodiscover、ecp、EWS、Microsoft-Server-ActiveSync、OAB、owa、PowerShell</span><span class="sxs-lookup"><span data-stu-id="bb93b-255">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="bb93b-p136">Lync:TLS-DSK または NTLM 認証。Lync のクライアント トラフィックは、ゲートウェイ ルーターを介して、Lync エッジ サーバー、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Lync Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bb93b-p137">SharePoint:Active Directory ドメイン サービス (AD DS)、フォームベース認証または SAML 認証。SharePoint のクライアント トラフィックは、VPN ゲートウェイまたは DirectAccess サーバーを介して、SharePoint の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に SharePoint Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="bb93b-p138">Exchange:SSL 経由の基本認証 (ActiveSync、自動検出)、フォーム ベース認証 (OWA)。Exchange のクライアント トラフィックは、ゲートウェイ ルーターを介して、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="bb93b-262">Lync のクライアント トラフィックは、ゲートウェイ ルーターを介して、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、ハードウェアのロード バランサー (HTTPS トラフィックで必要)、次に Lync Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-262">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="bb93b-263">内部アクセスの認証</span><span class="sxs-lookup"><span data-stu-id="bb93b-263">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="bb93b-264">内部の従業員</span><span class="sxs-lookup"><span data-stu-id="bb93b-264">Internal employees</span></span>

> https://intranet.contoso.com 
    
> https://teams.contoso.com 
    
> https://my.contoso.com
    
> https://partnerweb.contoso.com
    
> https://mail.contoso.com* 
    
> https://dial.contoso.com 
    
> https://meet.contoso.com
    
> https://admin.contoso.com
    
- <span data-ttu-id="bb93b-p139">Lync:Kerberos、TLS-DSK、または NTLM 認証。Lync のクライアント トラフィックは、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Lync Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="bb93b-p140">SharePoint:Active Directory ドメイン サービス (AD DS)、フォームベース認証または SAML 認証。SharePoint のクライアント トラフィックは、SharePoint の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に SharePoint Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="bb93b-p141">Exchange:AD DS、フォーム ベース認証。Exchange のクライアント トラフィックは、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="bb93b-271">Lync のクライアント トラフィックは、Lync の VIP (ロード バランサーまたはリバース プロキシ サーバー)、ハードウェアのロード バランサー (HTTPS トラフィックで必要)、次に Lync Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-271">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="bb93b-272">クラウド ベースの電子メール トラフィック</span><span class="sxs-lookup"><span data-stu-id="bb93b-272">Cloud-based email traffic</span></span>

<span data-ttu-id="bb93b-273">SMTP ベースの電子メール トラフィックのためのクラウド ベースのコンポーネントは、インターネット メール ホストまたは Exchange Online Protection のいずれかで構成されます。</span><span class="sxs-lookup"><span data-stu-id="bb93b-273">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="bb93b-p142">これらのコンポーネントは、SMTP を使用してネットワーク経由で電子メール トラフィックを移動します。トラフィックは、ゲートウェイ ルーターを介して、Exchange の VIP (ロード バランサーまたはリバース プロキシ サーバー)、次に Exchange Server に移動します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="bb93b-276">ネットワーク トラフィックの凡例</span><span class="sxs-lookup"><span data-stu-id="bb93b-276">Network traffic legend</span></span>

<span data-ttu-id="bb93b-277">凡例のボックスでは、次のように線に異なる色を付けて、各種のトラフィックをグラフィカルに示しています。</span><span class="sxs-lookup"><span data-stu-id="bb93b-277">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="bb93b-278">緑色の線: Lync の SIP トラフィック</span><span class="sxs-lookup"><span data-stu-id="bb93b-278">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="bb93b-279">青色の線:Lync の Web トラフィック</span><span class="sxs-lookup"><span data-stu-id="bb93b-279">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="bb93b-280">紫色の線:SharePoint クライアントのトラフィック</span><span class="sxs-lookup"><span data-stu-id="bb93b-280">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="bb93b-281">オレンジ色の線:Exchange クライアントのトラフィック</span><span class="sxs-lookup"><span data-stu-id="bb93b-281">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="bb93b-282">灰色の線:Exchange のオンプレミスと Exchange Online Protection の間の Exchange メール サーバーのトラフィック。</span><span class="sxs-lookup"><span data-stu-id="bb93b-282">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="bb93b-283">トラフィックと使用するポートの様々な種類も、凡例のボックスに記載されています。</span><span class="sxs-lookup"><span data-stu-id="bb93b-283">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="bb93b-284">Lync の SIP トラフィックと Lync の web トラフィック</span><span class="sxs-lookup"><span data-stu-id="bb93b-284">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="bb93b-285">Lync エッジ サーバーは、外部のユーザーの通信に次のポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-285">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="bb93b-286">信号/IM トラフィック (SIP/SIMPLE):TCP ポート 443 (着信トラフィック用に開いている)</span><span class="sxs-lookup"><span data-stu-id="bb93b-286">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="bb93b-287">Web 会議トラフィック (PSOM):TCP 443 (着信トラフィック用に開いている)</span><span class="sxs-lookup"><span data-stu-id="bb93b-287">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="bb93b-288">A/V のトラフィック (SRTP):TCP 443、UDP 3478、および TCP 50000 ～ 59999 (省略可能) (受信および送信トラフィック用に開いている)</span><span class="sxs-lookup"><span data-stu-id="bb93b-288">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="bb93b-289">Lync エッジ サーバーは、フェデレーションの通信に次のポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="bb93b-289">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="bb93b-290">TCP ポート 5061 (SIP)、5269 (XMPP)、443、および UDP 3478 (SRTP) (受信および送信トラフィック用に開いている)</span><span class="sxs-lookup"><span data-stu-id="bb93b-290">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="bb93b-291">SharePoint クライアントのトラフィック</span><span class="sxs-lookup"><span data-stu-id="bb93b-291">SharePoint client traffic</span></span>

<span data-ttu-id="bb93b-p143">SharePoint は、クライアントとロード バランサーの間の暗号化通信のために TCP ポート 443 (SSL) を使用できます。インターネットからの外部アクセスでは、ゲートウェイ ルーター (または外部ファイアウォール) 上の送受信トラフィックに対してこのポートを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="bb93b-294">Exchange クライアントのトラフィックと Exchange メール サーバーのトラフィック</span><span class="sxs-lookup"><span data-stu-id="bb93b-294">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="bb93b-p144">Exchange は、サーバーからサーバーへの通信に TCP ポート 25 (SMTP) を使用します。ほとんどのクライアント トラフィック (OWA、ActiveSync、自動検出、Outlook Anywhere) がポート 443 (HTTPS) 経由で処理されます。 POP または IMAP クライアントがある場合は、これらのクライアントをサポートするために、ポート 110 (POP3)、995 (暗号化された POP3)、143 (IMAP4)、993 (暗号化された IMAP4)、および 587 (SMTP) も使用されます。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="bb93b-298">Lync ネットワーク トラフィックの詳細について</span><span class="sxs-lookup"><span data-stu-id="bb93b-298">More on Lync network traffic?</span></span>

<span data-ttu-id="bb93b-p145">Lync Server が、インスタント メッセージング、web 会議、アプリケーション共有、および音声通信を提供する点で、組織を支援する方法を確認できます。詳細については、「[Microsoft Lync Server 2013 のプロトコル ワークロード ポスター](https://aka.ms/G5jzjo)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb93b-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="bb93b-301">ポスターには、この情報にアクセスする QR コードもあります。</span><span class="sxs-lookup"><span data-stu-id="bb93b-301">The poster also includes a QR code to access this information.</span></span> 
  

