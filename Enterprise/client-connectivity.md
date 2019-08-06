---
title: クライアント接続
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
audience: ITPro
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
description: '概要: クライアントコンピューターと Office 365 テナントデータセンターの場所に応じて、クライアントコンピューターが Office 365 テナントに接続する方法について説明します。'
ms.openlocfilehash: f7b41e1ff4fd8b30ed0f51641c479025b4e04ae5
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "34722696"
---
# <a name="client-connectivity"></a><span data-ttu-id="cc304-103">クライアント接続</span><span class="sxs-lookup"><span data-stu-id="cc304-103">Client connectivity</span></span>

 <span data-ttu-id="cc304-104">**概要:** クライアントコンピューターと Office 365 テナントデータセンターの場所に応じて、クライアントコンピューターが Office 365 テナントに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc304-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="cc304-105">Office 365 は、地震や停電などの1つの地域で重大な問題が発生した場合でも、サービスを継続して稼働させるための Microsoft データセンターに存在します。</span><span class="sxs-lookup"><span data-stu-id="cc304-105">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage.</span></span> <span data-ttu-id="cc304-106">Office 365 テナントに接続すると、クライアント接続はテナントがホストされている適切なデータセンターに転送されます。</span><span class="sxs-lookup"><span data-stu-id="cc304-106">When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted.</span></span> <span data-ttu-id="cc304-107">テナントをホストできる場所を決定するルールは、Microsoft との契約によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="cc304-107">The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft.</span></span> <span data-ttu-id="cc304-108">クライアントがデータセンターの場所からデータを取得する方法を決定するルールは、使用しているサービスのアーキテクチャによって異なります。</span><span class="sxs-lookup"><span data-stu-id="cc304-108">The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="cc304-109">たとえば、Office 365 ポータルにログオンすると、通常、クライアントに最も近いデータセンターに接続し、次に使用するサービスに応じて指示されます。</span><span class="sxs-lookup"><span data-stu-id="cc304-109">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next.</span></span> <span data-ttu-id="cc304-110">電子メールを起動しても、UI を表示するための最初の接続が最も近いデータセンターから提供される場合がありますが、ユーザーが読んだメールの内容を表示するために、最も近いデータセンターとテナントが配置されているデータセンターの間に2番目の接続が開かれることがあります。</span><span class="sxs-lookup"><span data-stu-id="cc304-110">If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read.</span></span> <span data-ttu-id="cc304-111">Microsoft は、世界中の上位10のネットワークの1つを運用しており、データセンター間接続が非常に高速になります。</span><span class="sxs-lookup"><span data-stu-id="cc304-111">Microsoft operates one of the top ten networks in the world, resulting in incredibly fast datacenter-to-datacenter connections.</span></span>
  
<span data-ttu-id="cc304-112">記事を読むと、 [Office 365 の url と IP アドレスの範囲](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)をデータセンターごとに提供していない理由を理解することができます。これは単に相互に相互に相互に接続されていて、そのような場合には相互に依存しています。</span><span class="sxs-lookup"><span data-stu-id="cc304-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="cc304-113">Office 365 用の Azure ExpressRoute を使用している場合、ほとんどの場合、接続は、ここで説明するパブリック接続ではなく、Office 365 へのプライベート接続を経由して行われます。</span><span class="sxs-lookup"><span data-stu-id="cc304-113">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here.</span></span> <span data-ttu-id="cc304-114">クライアントの接続方法に関する原則は、それでも正確です。</span><span class="sxs-lookup"><span data-stu-id="cc304-114">The principles about how clients connect are still accurate.</span></span> <span data-ttu-id="cc304-115">[Office 365 の Azure ExpressRoute の](azure-expressroute.md)詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc304-115">Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="cc304-116">Skype for business のネットワーク要求の詳細については、「 [skype For Business Online でのメディア品質とネットワーク接続性のパフォーマンス」](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc304-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="cc304-117">この記事は[、Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc304-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="cc304-118">お客様のデータを管理して、データセンターでのセキュリティを確保し、機密データを公開するように注意してください。</span><span class="sxs-lookup"><span data-stu-id="cc304-118">We take great care to manage customer data so it's secure and private in our datacenters.</span></span> <span data-ttu-id="cc304-119">プライバシーを管理するために講じる手順についての詳細は、[セキュリティセンター](https://go.microsoft.com/fwlink/?LinkID=397383)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc304-119">Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="cc304-120">最も近いデータセンターに接続する</span><span class="sxs-lookup"><span data-stu-id="cc304-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="cc304-121">これは最も一般的な接続の種類であり、Office 365 ポータルと Exchange Online の両方で使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc304-121">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online.</span></span> <span data-ttu-id="cc304-122">このような状況では、クライアントが Office 365 に接続しようとすると、そのコンピューターの DNS クエリによって、コンピューターの受信元の世界の地域が決定されます。 Office 365 は、要求を最も近いデータセンターにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="cc304-122">In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="cc304-123">最も近いデータセンターにあるポータルの停止に接続すると、クライアントコンピューターにその場所からのクライアントのテナントに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc304-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="cc304-124">Exchange Online は、さらに一歩進んでいきます。</span><span class="sxs-lookup"><span data-stu-id="cc304-124">Exchange Online goes a step further.</span></span> <span data-ttu-id="cc304-125">クライアントコンピューターが最も近いデータセンターに接続されると、そのデータセンターの Exchange サーバーは、以下の *「How to the this work」セクション*に示されているように、テナントが実際に存在するデータセンターに接続されます。</span><span class="sxs-lookup"><span data-stu-id="cc304-125">Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below.</span></span> <span data-ttu-id="cc304-126">その後、最も近いデータセンターの Exchange Online サーバーは、クライアントコンピューターからメールボックスサーバーに要求をプロキシします。</span><span class="sxs-lookup"><span data-stu-id="cc304-126">The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server.</span></span> <span data-ttu-id="cc304-127">これにより、電子メールや予定表のアイテムを Microsoft ネットワークに取得する処理が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="cc304-127">This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="cc304-128">これは標準的なクラウド製品でどのように機能しますか?</span><span class="sxs-lookup"><span data-stu-id="cc304-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="cc304-129">この接続プロセスは、高トラフィック、高価値 web アプリケーション (Office 365 など) のための標準です。</span><span class="sxs-lookup"><span data-stu-id="cc304-129">This connection process is standard for high traffic, high value web applications like Office 365.</span></span> <span data-ttu-id="cc304-130">このセクションでは、プロセスの手順の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="cc304-130">In this section, we outline and illustrate the steps in the process.</span></span> <span data-ttu-id="cc304-131">クライアントコンピューターがテナントと同じリージョンにない場合、接続はクライアントが接続しているサービスに応じて、多くの異なる外観になります。</span><span class="sxs-lookup"><span data-stu-id="cc304-131">When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="cc304-132">この図は、標準の Office 365 を使用した、北米のテナントでのお客様を示しています。</span><span class="sxs-lookup"><span data-stu-id="cc304-132">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America.</span></span> <span data-ttu-id="cc304-133">このシナリオでは、要求を行っているユーザーがヨーロッパに出張ており、その場所から Office 365 を使用しています。</span><span class="sxs-lookup"><span data-stu-id="cc304-133">In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="cc304-134">クライアントコンピューターは、Office 365 に関連付けられている IP アドレスのローカル DNS サーバーに問い合わせます。</span><span class="sxs-lookup"><span data-stu-id="cc304-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="cc304-135">クライアントコンピューターのローカル DNS サーバーは、Office 365 に関連付けられている IP アドレスを Microsoft DNS サーバーに要求します。</span><span class="sxs-lookup"><span data-stu-id="cc304-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="cc304-136">Microsoft の DNS サーバーは (クライアントの DNS サーバーの場所に基づいて) 地域サーバー名を返し、クライアントコンピューターは手順1と手順2を繰り返して、地域の Office 365 データセンターの IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc304-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="cc304-137">クライアントコンピューターは、地域のデータセンターの IP アドレスに接続します。</span><span class="sxs-lookup"><span data-stu-id="cc304-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="cc304-138">Exchange Online サーバーは、お客様のテナントが存在するアクティブなデータセンターへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="cc304-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最も近い地域のデータセンター](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="cc304-140">これは、独立クラウド製品でどのように動作しますか?</span><span class="sxs-lookup"><span data-stu-id="cc304-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="cc304-141">この接続は、Office 365 が 21 Vianet で運用している独立クラウド製品とは少し異なります。</span><span class="sxs-lookup"><span data-stu-id="cc304-141">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet.</span></span> <span data-ttu-id="cc304-142">Office 365 の独立インスタンスでテナントを使用すると、ポータル接続を受け付ける、最も近い Office 365 サーバーが、テナントが存在する独立地域内のサーバーになります。</span><span class="sxs-lookup"><span data-stu-id="cc304-142">With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides.</span></span> <span data-ttu-id="cc304-143">同様に、独立クラウドまたは標準オファーリングで SharePoint Online にアクセスするお客様は、テナントが存在するフロントエンドサーバーに転送されます。</span><span class="sxs-lookup"><span data-stu-id="cc304-143">Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides.</span></span> <span data-ttu-id="cc304-144">下の「アクティブなデータセンターへの接続」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc304-144">See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="cc304-145">クライアントコンピューターは、Office 365 に関連付けられている IP アドレスのローカル DNS サーバーに問い合わせます。</span><span class="sxs-lookup"><span data-stu-id="cc304-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="cc304-146">クライアントコンピューターのローカル DNS サーバーは、Office 365 に関連付けられている IP アドレスを Microsoft DNS サーバーに要求します。</span><span class="sxs-lookup"><span data-stu-id="cc304-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="cc304-147">Microsoft の DNS サーバーは (クライアントの DNS サーバーの場所に基づいて) 地域サーバー名を返し、クライアントコンピューターは手順1と手順2を繰り返して、地域の Office 365 データセンターの IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc304-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="cc304-148">クライアントコンピューターは、地域のデータセンターの IP アドレスに接続します。</span><span class="sxs-lookup"><span data-stu-id="cc304-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="cc304-149">Exchange Online サーバーは、お客様のテナントが存在するアクティブなデータセンターへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="cc304-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![最も近い米国地域のデータセンター](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="cc304-151">アクティブなデータセンターへの接続</span><span class="sxs-lookup"><span data-stu-id="cc304-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="cc304-152">アクティブなデータセンターへの接続は、より重いデータ転送のワークロード用に設計されており、現在 SharePoint Online で使用されています。</span><span class="sxs-lookup"><span data-stu-id="cc304-152">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online.</span></span> <span data-ttu-id="cc304-153">この状況では、クライアントが Office 365 に接続しようとすると、そのブラウザーは SharePoint Online テナントのアクティブなデータセンターにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="cc304-153">In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="cc304-154">これはどのように動作しますか?</span><span class="sxs-lookup"><span data-stu-id="cc304-154">How does this work?</span></span>

<span data-ttu-id="cc304-155">クライアントコンピューターが別の地域から SharePoint Online に接続している場合、接続はアクティブな SharePoint Online データセンターにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="cc304-155">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter.</span></span> <span data-ttu-id="cc304-156">このシナリオでは、お客様は標準のオファーリングを使用しており、ポータル接続はローカルに残り、SharePoint Online 接続がアクティブなデータセンターに転送されるようになっています。</span><span class="sxs-lookup"><span data-stu-id="cc304-156">In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="cc304-157">クライアントコンピューターは、Office 365 に関連付けられている IP アドレスのローカル DNS サーバーに問い合わせます。</span><span class="sxs-lookup"><span data-stu-id="cc304-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="cc304-158">クライアントコンピューターのローカル DNS サーバーは、Office 365 に関連付けられている IP アドレスを Microsoft DNS サーバーに要求します。</span><span class="sxs-lookup"><span data-stu-id="cc304-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="cc304-159">Microsoft の DNS サーバーは、アクティブな SharePoint Online データセンターのサーバー名 (クライアントの Office 365 テナントの場所に基づいて) を返し、クライアントコンピューターは手順1と2を繰り返して、アクティブな Office 365 データセンターの IP アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="cc304-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="cc304-160">クライアントコンピューターは、アクティブなデータセンターの IP アドレスに接続します。</span><span class="sxs-lookup"><span data-stu-id="cc304-160">The client computer connects to the active datacenter IP address.</span></span>

![米国のアクティブなデータセンター](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="cc304-162">仮想プライベートネットワーク (Vpn) 経由の接続</span><span class="sxs-lookup"><span data-stu-id="cc304-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="cc304-163">この種類の接続は、クライアントコンピューターが仮想プライベートネットワーク (VPN) を使用している場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="cc304-163">This type of connection applies only when a virtual private network (VPN) is used by client computers.</span></span> <span data-ttu-id="cc304-164">実際には、VPN が使用されているため、Office 365 の動作が変更されることはありませんが、一般に、クライアントコンピューターが Office 365 への接続を確立する方法を制御するために Vpn が使用されているため、通常は機能が低下しているため、それをカバーすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="cc304-164">In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="cc304-165">これはどのように動作しますか?</span><span class="sxs-lookup"><span data-stu-id="cc304-165">How does this work?</span></span>

<span data-ttu-id="cc304-166">クライアントコンピューターが別の地域にある企業オフィスへの VPN 接続を確立する場合、クライアントコンピューターの場所にある DNS サーバーの代わりに、そのオフィスの DNS サーバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc304-166">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location.</span></span> <span data-ttu-id="cc304-167">ほとんどの場合、VPN 経由のこの特別な接続により、Office 365 の動作が低下します。</span><span class="sxs-lookup"><span data-stu-id="cc304-167">In most cases, this extra connection over the VPN will degrade the Office 365 experience.</span></span> <span data-ttu-id="cc304-168">Office 365 サービスは、お客様の接続をエンドユーザーにできるだけ近いものにサービスするように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="cc304-168">The Office 365 services are optimized to service customer connections as close to the end user as possible.</span></span> <span data-ttu-id="cc304-169">多くのサービスでは、Microsoft ネットワーク上の Azure エッジネットワーク、コンテンツ配信ネットワーク、信頼性の高いネットワーク容量を活用して、Office 365 サービスのネットワーク要求がクライアントコンピューターの近くになるときに、最適なユーザー環境を実現します。可能な限り。</span><span class="sxs-lookup"><span data-stu-id="cc304-169">Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="cc304-170">クライアントコンピューターは、Office 365 に関連付けられている IP アドレスを VPN DNS サーバーに要求します。</span><span class="sxs-lookup"><span data-stu-id="cc304-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="cc304-171">クライアントコンピューターの VPN DNS サーバーは、Office 365 に関連付けられている IP アドレスを Microsoft DNS サーバーに要求します。</span><span class="sxs-lookup"><span data-stu-id="cc304-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="cc304-172">Microsoft の DNS サーバーは、(VPN DNS サーバーの場所に基づいて) 地域サーバー名を返し、クライアントコンピューターは手順1と2を繰り返して、地域の Office 365 データセンターの IP アドレス情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="cc304-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="cc304-173">クライアントコンピューターは、VPN 接続を確立した企業オフィスに最も近いデータセンターの IP アドレスに接続します。</span><span class="sxs-lookup"><span data-stu-id="cc304-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![VPN データセンターの接続](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="cc304-175">ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="cc304-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cc304-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc304-176">See also</span></span>

[<span data-ttu-id="cc304-177">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="cc304-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="cc304-178">Office 365 のネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="cc304-178">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)
