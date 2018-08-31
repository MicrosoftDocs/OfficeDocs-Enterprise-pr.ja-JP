---
title: クライアント接続
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: '概要:  クライアント コンピューターおよび Office 365 テナント データセンターの場所に応じて、クライアント コンピューターが Office 365 テナントに接続する方法について説明します。'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223039"
---
# <a name="client-connectivity"></a><span data-ttu-id="1d229-103">クライアント接続</span><span class="sxs-lookup"><span data-stu-id="1d229-103">Client connectivity</span></span>

 <span data-ttu-id="1d229-104">**概要: ** クライアント コンピューターおよび Office 365 テナント データセンターの場所に応じて、クライアント コンピューターが Office 365 テナントに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1d229-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="1d229-p101">Office 365 は、マイクロソフトのデータ センター世界中のサービスと、地震や停電など、特定の地域で主要な問題がある場合でも実行するために存在します。接続すると、Office 365 テナントに、クライアントの接続が表示されます、適切なデータ ・ センターに、テナントがホストされています。テナントをホストすることを決定する規則は、マイクロソフトとの契約によって定義されます。クライアントがそのデータ センターの場所からデータを取得する方法を決定する規則を使用しているサービスのアーキテクチャによって異なります。</span><span class="sxs-lookup"><span data-stu-id="1d229-p101">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage. When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted. The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft. The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="1d229-p102">などの Office 365 ポータルにログオンするときは通常、クライアントに最も近いデータ センターに接続し、[次へ] を使用するサービスによって指示しています。メールを起動すると、UI を表示する最初の接続が最も近いデータ センターから決まることがありますが、最も近いデータ センターと、テナントの場所を参照する電子メールには表示するデータ ・ センター間で 2 番目の接続を開くことがあります。マイクロソフトでは、非常に高速データ センターへのデータ センター内の接続が高速で世界のトップ 10 のネットワークの 1 つは動作します。</span><span class="sxs-lookup"><span data-stu-id="1d229-p102">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next. If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read. Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="1d229-112">[Office 365 の Url と IP アドレスの範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)を提供していない理由を理解する記事を参照した後可能性がありますがデータ センターでは、あたりは単に相互接続されたすぎると、それを実現する互いに依存します。</span><span class="sxs-lookup"><span data-stu-id="1d229-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="1d229-p103">Office 365 の Azure ExpressRoute を使用する場合ほとんどの場合、接続に送られますプライベート接続経由で Office 365 は、ここに記載されているパブリック接続ではなく。クライアントの接続に関する原則は、正確です。[Office 365 の Azure ExpressRoute](azure-expressroute.md)の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="1d229-p103">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here. The principles about how clients connect are still accurate. Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="1d229-116">ビジネス ネットワーク要求の詳細 Skype では、[メディアの品質とビジネス オンラインの Skype でのネットワーク接続のパフォーマンス](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d229-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="1d229-117">この資料は、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://aka.ms/tune)の一部です。</span><span class="sxs-lookup"><span data-stu-id="1d229-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="1d229-p104">我々 は、安全性とプライバシー、データ センターでは、顧客データを管理するために十分な注意をとる。プライバシーを管理するため手順の詳細については、[セキュリティ センター](https://go.microsoft.com/fwlink/?LinkID=397383)に含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d229-p104">We take great care to manage customer data so it's secure and private in our datacenters. Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="1d229-120">最も近いデータ センターへの接続</span><span class="sxs-lookup"><span data-stu-id="1d229-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="1d229-p105">これは、接続の最も一般的な種類であり、Office 365 ポータルとオンラインの Exchange で使用されています。このような場合は、クライアントが Office 365 に接続しようとすると、各自のコンピューターの DNS クエリが自分のコンピューターから来て、世界の地域を決定し、Office 365 は、最も近いデータ センターに要求をリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="1d229-p105">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online. In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="1d229-123">ポータルへの接続は、最も近いデータ センターで停止し、クライアント コンピューターがその場所からクライアントのテナントについての情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="1d229-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="1d229-p106">Exchange オンライン段階に進んでいます。クライアント コンピューターを最も近いデータ センターに接続すると、そのデータ センター内の Exchange サーバーに接続するデータ ・ センター、テナントに示すように実際に存在、*はこのセクションの作業*の下。プロキシの最も近いデータ センターにオンラインの Exchange サーバーのメールボックス サーバーにクライアント コンピューターから要求します。これは、メールと Microsoft ネットワークへの予定表アイテムを取得するの面倒な作業を移動してクライアント コンピューターの経験を迅速化します。</span><span class="sxs-lookup"><span data-stu-id="1d229-p106">Exchange Online goes a step further. Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below. The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server. This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="1d229-128">標準的なクラウド サービスの動作のでしょうか。</span><span class="sxs-lookup"><span data-stu-id="1d229-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="1d229-p107">この接続プロセスは、高トラフィックの標準的な価値の高い web アプリケーションは、Office 365 をください。、ここでは、概要を説明し、プロセスの手順を説明します。クライアント コンピューターは、テナントと同じ領域では、接続に接続されているクライアント サービスによって非常に異なる検索します。</span><span class="sxs-lookup"><span data-stu-id="1d229-p107">This connection process is standard for high traffic, high value web applications like Office 365. In this section, we outline and illustrate the steps in the process. When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="1d229-p108">この図では、北米のテナントを持つ標準的な Office 365 サービスを使用して顧客を使用します。このシナリオでは、要求を行っている人はヨーロッパを旅行したし、その場所から Office 365 を使用しています。</span><span class="sxs-lookup"><span data-stu-id="1d229-p108">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America. In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="1d229-134">クライアント コンピューターでは、Office 365 に関連付けられている IP アドレスをローカルの DNS サーバーを要求します。</span><span class="sxs-lookup"><span data-stu-id="1d229-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="1d229-135">クライアント コンピューターのローカルの DNS サーバーは、Office 365 に関連付けられている IP アドレスの Microsoft DNS サーバーを問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="1d229-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="1d229-136">Microsoft の DNS サーバー (クライアントの DNS サーバーの場所に基づく) を地域のサーバー名を取得して、クライアント コンピューターが Office 365 の地域データ センターの IP アドレスを取得する手順 1 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1d229-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="1d229-137">クライアント コンピューターは、その地域のデータセンターの IP アドレスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1d229-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="1d229-138">オンラインの Exchange サーバーでは、お客様のテナントが存在するアクティブなデータ センターへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="1d229-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最も近い地域のデータセンター](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="1d229-140">Sovereign のこの作業のサービスへのクラウド</span><span class="sxs-lookup"><span data-stu-id="1d229-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="1d229-p109">この接続は、21 の Vianet によって運営されて Office 365 などの君主のクラウド サービスには少し異なります。Office 365 の君主のインスタンスでは、テナントには、ポータルの接続を許可する Office 365 の最も近いサーバーは、テナントが存在する君主の領域内にあるサーバーです。同様に、テナントが存在するフロント エンド サーバーに、君主のクラウドまたは標準的なソリューションで SharePoint Online にアクセスする顧客が表示されます。以下の作業中のデータ センターへの接続を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d229-p109">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet. With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides. Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides. See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="1d229-145">クライアント コンピューターでは、Office 365 に関連付けられている IP アドレスをローカルの DNS サーバーを要求します。</span><span class="sxs-lookup"><span data-stu-id="1d229-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="1d229-146">クライアント コンピューターのローカルの DNS サーバーは、Office 365 に関連付けられている IP アドレスの Microsoft DNS サーバーを問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="1d229-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="1d229-147">Microsoft の DNS サーバー (クライアントの DNS サーバーの場所に基づく) を地域のサーバー名を取得して、クライアント コンピューターが Office 365 の地域データ センターの IP アドレスを取得する手順 1 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1d229-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="1d229-148">クライアント コンピューターは、その地域のデータセンターの IP アドレスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1d229-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="1d229-149">オンラインの Exchange サーバーでは、お客様のテナントが存在するアクティブなデータ センターへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="1d229-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最も近い米国地域のデータセンター](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="1d229-151">アクティブなデータセンターへの接続</span><span class="sxs-lookup"><span data-stu-id="1d229-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="1d229-p110">作業中のデータ センターに接続するでは、厚めのデータ転送の負荷を目的し、SharePoint Online によって使用されています。このような場合は、クライアントは、Office 365 に接続しようとしています、ブラウザーにリダイレクトされます、作業中のデータ センター、SharePoint Online のテナントの。</span><span class="sxs-lookup"><span data-stu-id="1d229-p110">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online. In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="1d229-154">動作方法</span><span class="sxs-lookup"><span data-stu-id="1d229-154">How does this work?</span></span>

<span data-ttu-id="1d229-p111">さまざまな領域からクライアント コンピューターが SharePoint Online に接続すると、接続がアクティブな SharePoint Online データ センターにリダイレクトされます。このシナリオでは、お客様は、標準を提供する、最終的に残り、ローカル ポータルの接続と作業中のデータ センターに送信されている SharePoint のオンライン接続を使用しています。</span><span class="sxs-lookup"><span data-stu-id="1d229-p111">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter. In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="1d229-157">クライアント コンピューターでは、Office 365 に関連付けられている IP アドレスをローカルの DNS サーバーを要求します。</span><span class="sxs-lookup"><span data-stu-id="1d229-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="1d229-158">クライアント コンピューターのローカルの DNS サーバーは、Office 365 に関連付けられている IP アドレスの Microsoft DNS サーバーを問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="1d229-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="1d229-159">Microsoft の DNS サーバー (クライアントの Office 365 のテナントの場所に基づいて) 有効な SharePoint Online データ センターのサーバー名を取得して、クライアント コンピューターが作業中の Office 365 のデータ センターの IP アドレスを取得する手順 1 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1d229-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="1d229-160">クライアント コンピューターは、そのアクティブなデータセンターの IP アドレスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1d229-160">The client computer connects to the active datacenter IP address.</span></span>

![米国のアクティブなデータセンター](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="1d229-162">仮想プライベート ネットワーク (VPN) 経由での接続</span><span class="sxs-lookup"><span data-stu-id="1d229-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="1d229-p112">この種類の接続は、クライアント コンピューターが仮想プライベート ネットワーク (VPN) が使用される場合にのみ適用されます。実際には、Office 365 の動作は単に変更、VPN を使用すると、劣化した経験では、クライアント コンピューターが Office 365 と通常の結果への接続を確立する方法を制御するのには Vpn が使用される一般的ので、したがってことが重要をカバーします。</span><span class="sxs-lookup"><span data-stu-id="1d229-p112">This type of connection applies only when a virtual private network (VPN) is used by client computers. In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="1d229-165">動作方法</span><span class="sxs-lookup"><span data-stu-id="1d229-165">How does this work?</span></span>

<span data-ttu-id="1d229-p113">クライアント コンピューターは、別の地域の本社への VPN 接続を確立するとき、クライアント コンピューターの場所にある DNS サーバーの代わりにそのオフィスにある DNS サーバーが使用されます。ほとんどの場合、この余分な接続を VPN 経由で Office 365 の操作性が低下します。として可能なエンド ・ ユーザーにサービスの顧客を接続するには、Office 365 サービスが最適化されています。Azure エッジ ネットワーク、コンテンツ配信ネットワーク、およびクライアント コンピューターに Office 365 サービスのネットワーク要求が行われたときに、最高の可能なユーザー エクスペリエンスを提供する Microsoft のネットワークで信頼性の高いネットワークの容量を活用して、多くのサービス可能な限り。</span><span class="sxs-lookup"><span data-stu-id="1d229-p113">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location. In most cases, this extra connection over the VPN will degrade the Office 365 experience. The Office 365 services are optimized to service customer connections as close to the end user as possible. Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="1d229-170">クライアント コンピューターでは、Office 365 に関連付けられている IP アドレスの VPN の DNS サーバーを確認します。</span><span class="sxs-lookup"><span data-stu-id="1d229-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="1d229-171">VPN の DNS サーバーのクライアント コンピューターの IP アドレスを Office 365 に関連する Microsoft DNS サーバーを求めています。</span><span class="sxs-lookup"><span data-stu-id="1d229-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="1d229-172">Microsoft の DNS サーバー (VPN の DNS サーバーの場所に基づく)、地域のサーバー名を取得して、クライアント コンピューターが Office 365 の地域データ センターの IP アドレス情報を取得するのには手順 1 を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="1d229-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="1d229-173">クライアント コンピューターは、本社オフィスとの VPN 接続を確立するに最も近い IP アドレスをデータ センターに接続します。</span><span class="sxs-lookup"><span data-stu-id="1d229-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![VPN データセンターの接続](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="1d229-175">戻るを使用することができます短いリンクを以下に示します。[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="1d229-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1d229-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d229-176">See also</span></span>

[<span data-ttu-id="1d229-177">Office 365 エンドポイントを管理します。</span><span class="sxs-lookup"><span data-stu-id="1d229-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="1d229-178">Office 365 へのネットワーク接続</span><span class="sxs-lookup"><span data-stu-id="1d229-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
