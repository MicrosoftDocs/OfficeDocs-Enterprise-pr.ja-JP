---
title: Microsoft Azure IaaS のためのネットワークの設計
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 9cb70c9d-9ed9-47cc-af5a-6403d87d3372
description: '概要: Microsoft Azure IaaS のワークロード用に最適化されたネットワークの設計方法について説明します。'
ms.openlocfilehash: 0e7af14768aa1a21548b25a20a465b644b749f3e
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915122"
---
# <a name="designing-networking-for-microsoft-azure-iaas"></a><span data-ttu-id="04962-103">Microsoft Azure IaaS のためのネットワークの設計</span><span class="sxs-lookup"><span data-stu-id="04962-103">Designing networking for Microsoft Azure IaaS</span></span>

 <span data-ttu-id="04962-104">**概要:** Microsoft Azure IaaS のワークロード用に最適化されたネットワークの設計方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="04962-104">**Summary:** Understand how to design optimized networking for workloads in Microsoft Azure IaaS.</span></span>
  
<span data-ttu-id="04962-105">Azure IaaS でホストされている IT ワークロード用のネットワーキングを最適化するには、Azure 仮想ネットワーク (VNet)、アドレス空間、ルーティング、DNS、および負荷分散に精通している必要があります。</span><span class="sxs-lookup"><span data-stu-id="04962-105">Optimizing networking for IT workloads hosted in Azure IaaS requires an understanding of Azure virtual networks (VNets), address spaces, routing, DNS, and load balancing.</span></span>
  
## <a name="planning-steps-for-any-vnet"></a><span data-ttu-id="04962-106">任意の VNet 用の手順を計画する</span><span class="sxs-lookup"><span data-stu-id="04962-106">Planning steps for any VNet</span></span>

<span data-ttu-id="04962-107">どの種類の VNet も、次の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="04962-107">Follow these steps for any type of VNet.</span></span>
  
### <a name="step-1-prepare-your-intranet-for-microsoft-cloud-services"></a><span data-ttu-id="04962-108">手順 1:Microsoft クラウド サービス用にインターネットを準備する。</span><span class="sxs-lookup"><span data-stu-id="04962-108">Step 1: Prepare your intranet for Microsoft cloud services.</span></span>

<span data-ttu-id="04962-109">[Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。</span><span class="sxs-lookup"><span data-stu-id="04962-109">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-2-optimize-your-internet-bandwidth"></a><span data-ttu-id="04962-110">手順 2:インターネット帯域幅を最適化する。</span><span class="sxs-lookup"><span data-stu-id="04962-110">Step 2: Optimize your Internet bandwidth.</span></span>

<span data-ttu-id="04962-111">[Microsoft SaaS のためのネットワーク デザイン](designing-networking-for-microsoft-saas.md)の「**Microsoft SaaS サービスを利用するためのネットワークの準備の手順**」セクションに記載されている手順 2 から 4 を使用して、インターネット帯域幅を最適化します。</span><span class="sxs-lookup"><span data-stu-id="04962-111">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
  
### <a name="step-3-determine-the-type-of-vnet-cloud-only-or-cross-premises"></a><span data-ttu-id="04962-112">手順 3:VNet の種類を決定する (クラウド専用、またはクロスプレミス)。</span><span class="sxs-lookup"><span data-stu-id="04962-112">Step 3: Determine the type of VNet (cloud-only or cross-premises).</span></span>

<span data-ttu-id="04962-p101">クラウド専用の VNet には、オンプレミスのネットワークへの接続がありません。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="04962-p101">A cloud-only VNet has no connection to an on-premises network. Here is an example.</span></span>
  
<span data-ttu-id="04962-115">**図 1: クラウド専用の VNet**</span><span class="sxs-lookup"><span data-stu-id="04962-115">**Figure 1: A cloud-only VNet**</span></span>

![図 1:Azure でのクラウド専用の仮想ネットワーク](media/8be19104-02b3-4a7f-b0a0-30d6fcf8890b.png)
  
<span data-ttu-id="04962-117">図 1 は、クラウド専用の VNet の仮想マシンのセットを示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-117">Figure 1 shows a set of virtual machines in a cloud-only VNet.</span></span>
  
<span data-ttu-id="04962-p102">クロスプレミスの VNet には、Azure のゲートウェイを経由してオンプレミスのネットワークに接続する、サイト対サイト (S2S) VPN または ExpressRoute 接続があります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="04962-p102">A cross-premises VNet has a site-to-site (S2S) VPN or ExpressRoute connection to an on-premises network through an Azure gateway. Here is an example.</span></span>
  
<span data-ttu-id="04962-120">**図 2: クロスプレミスの VNet**</span><span class="sxs-lookup"><span data-stu-id="04962-120">**Figure 2: A cross-premises VNet**</span></span>

![図 2:Azure でのクロスプレミスの仮想ネットワーク](media/caacf007-e0dc-45d3-9531-441109776d25.png)
  
<span data-ttu-id="04962-122">図 2 は、オンプレミスのネットワークに接続される、クロスプレミスの VNet での仮想マシンのセットを示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-122">Figure 2 shows a set of virtual machines in a cross-premises VNet, which is connected to an on-premises network.</span></span>
  
<span data-ttu-id="04962-123">追加情報については、この記事の「[クロスプレミスの VNet 用の手順を計画する](designing-networking-for-microsoft-azure-iaas.md#cross_prem)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-123">See the additional [Planning steps for a cross-premises VNet](designing-networking-for-microsoft-azure-iaas.md#cross_prem) section in this article.</span></span>
  
### <a name="step-4-determine-the-address-space-of-the-vnet"></a><span data-ttu-id="04962-124">手順 4:VNet のアドレス空間を決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-124">Step 4: Determine the address space of the VNet.</span></span>

<span data-ttu-id="04962-125">表 1 は、VNet のさまざまな種類のアドレス空間を示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-125">Table 1 shows the address spaces for the different types of VNets.</span></span>
  
|<span data-ttu-id="04962-126">**VNet の種類**</span><span class="sxs-lookup"><span data-stu-id="04962-126">**Type of VNet**</span></span>|<span data-ttu-id="04962-127">**仮想ネットワークのアドレス スペース**</span><span class="sxs-lookup"><span data-stu-id="04962-127">**Virtual network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="04962-128">クラウド専用</span><span class="sxs-lookup"><span data-stu-id="04962-128">Cloud-only</span></span>  <br/> |<span data-ttu-id="04962-129">任意のプライベート アドレス空間</span><span class="sxs-lookup"><span data-stu-id="04962-129">Arbitrary private address space</span></span>  <br/> |
|<span data-ttu-id="04962-130">相互接続のクラウド専用</span><span class="sxs-lookup"><span data-stu-id="04962-130">Interconnected cloud-only</span></span>  <br/> |<span data-ttu-id="04962-131">任意のプライベート。ただし、接続された他の VNet と重複しない</span><span class="sxs-lookup"><span data-stu-id="04962-131">Arbitrary private, but not overlapping with other connected VNets</span></span>  <br/> |
|<span data-ttu-id="04962-132">クロスプレミス</span><span class="sxs-lookup"><span data-stu-id="04962-132">Cross-premises</span></span>  <br/> |<span data-ttu-id="04962-133">プライベート。ただし、オンプレミスと重複しない</span><span class="sxs-lookup"><span data-stu-id="04962-133">Private, but not overlapping with on-premises</span></span>  <br/> |
|<span data-ttu-id="04962-134">相互接続のクロスプレミス</span><span class="sxs-lookup"><span data-stu-id="04962-134">Interconnected cross-premises</span></span>  <br/> |<span data-ttu-id="04962-135">プライベート。ただし、オンプレミスおよび接続された他の VNet と重複しない</span><span class="sxs-lookup"><span data-stu-id="04962-135">Private, but not overlapping with on-premises and other connected VNets</span></span>  <br/> |
   
 <span data-ttu-id="04962-136">**表 1:VNet の種類と対応するアドレス空間**</span><span class="sxs-lookup"><span data-stu-id="04962-136">**Table 1: Types of VNets and their corresponding address space**</span></span>
  
<span data-ttu-id="04962-137">DHCP によって、仮想マシンにサブネットのアドレス空間からアドレス構成が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="04962-137">Virtual machines are assigned an address configuration from the address space of the subnet by DHCP:</span></span>
  
- <span data-ttu-id="04962-138">アドレス/サブネット マスク</span><span class="sxs-lookup"><span data-stu-id="04962-138">Address/subnet mask</span></span>
    
- <span data-ttu-id="04962-139">既定のゲートウェイ</span><span class="sxs-lookup"><span data-stu-id="04962-139">Default gateway</span></span>
    
- <span data-ttu-id="04962-140">DNS サーバーの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="04962-140">DNS server IP addresses</span></span>
    
<span data-ttu-id="04962-141">静的な IP アドレスを予約することもことができます。</span><span class="sxs-lookup"><span data-stu-id="04962-141">You can also reserve a static IP address.</span></span>
  
<span data-ttu-id="04962-142">仮想マシンには、個別にパブリック IP アドレスを割り当てることもできます。従来の展開のマシンの場合は、含まれているクラウド サービスからパブリック IP アドレスを割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="04962-142">Virtual machines can also be assigned a public IP address, either individually or from the containing cloud service (for classic deployment machines only).</span></span>
  
### <a name="step-5-determine-the-subnets-within-the-vnet-and-the-address-spaces-assigned-to-each"></a><span data-ttu-id="04962-143">手順 5:VNet 内のサブネットと、各サブネットに割り当てられているアドレス空間を決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-143">Step 5: Determine the subnets within the VNet and the address spaces assigned to each.</span></span>

<span data-ttu-id="04962-144">VNet には、ゲートウェイ サブネットと仮想マシン ホスト サブネットの、2 種類のサブネットがあります。</span><span class="sxs-lookup"><span data-stu-id="04962-144">There are two types of subnets in a VNet, a gateway subnet and a virtual machine-hosting subnet.</span></span>
  
<span data-ttu-id="04962-145">**図 3:Azure での 2 種類のサブネット**</span><span class="sxs-lookup"><span data-stu-id="04962-145">**Figure 3: The two types of subnets in Azure**</span></span>

![図 3:Azure での 2 種類のサブネット](media/2eaa512d-1293-4e9b-b927-6bfe0fc0acb4.png)
  
<span data-ttu-id="04962-147">図 3 は、ゲートウェイ サブネットを含む VNet を示しています。このゲートウェイ サブネットには、Azure ゲートウェイと、複数の仮想マシンを含む仮想マシン ホスト サブネットのセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="04962-147">Figure 3 shows a VNet containing a gateway subnet that contains an Azure gateway and a set of virtual machine-hosting subnets containing virtual machines.</span></span>
  
<span data-ttu-id="04962-p103">Azure ゲートウェイ サブネットは、Azure で Azure ゲートウェイの 2 つの仮想マシンをホストするために必要です。少なくとも 29 ビットのプレフィックス長でアドレス空間を指定します (例:192.168.15.248/29)。ExpressRoute を使用する予定の場合は、28 ビット以下のプレフィックス長をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="04962-p103">The Azure gateway subnet is needed by Azure to host the two virtual machines of your Azure gateway. Specify an address space with at least a 29-bit prefix length (example: 192.168.15.248/29). A 28-bit or smaller prefix length is recommended, especially if you are planning to use ExpressRoute.</span></span>
  
<span data-ttu-id="04962-151">Azure ゲートウェイ サブネットのアドレス空間を決定する場合のベスト プラクティスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="04962-151">A best practice for determining the address space of the Azure gateway subnet is the following:</span></span>
  
1. <span data-ttu-id="04962-152">ゲートウェイ サブネットのサイズを決定します。</span><span class="sxs-lookup"><span data-stu-id="04962-152">Decide on the size of the gateway subnet.</span></span>
    
2. <span data-ttu-id="04962-153">VNet のアドレス空間の可変ビットでは、ゲートウェイ サブネットに使用するビットを 0、残りのビットを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="04962-153">In the variable bits in the address space of the VNet, set the bits used for the gateway subnet to 0 and set the remaining bits to 1.</span></span>
    
3. <span data-ttu-id="04962-154">10 進数に変換して、ゲートウェイ サブネットのサイズに設定されたプレフィックス長のアドレス空間として表現します。</span><span class="sxs-lookup"><span data-stu-id="04962-154">Convert to decimal and express as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="04962-155">このメソッドでは、ゲートウェイ サブネットのアドレス空間は、常に VNet アドレス空間の最後尾になります。</span><span class="sxs-lookup"><span data-stu-id="04962-155">With this method, the address space for the gateway subnet is always at the farthest end of the VNet address space.</span></span>
  
<span data-ttu-id="04962-p104">ゲートウェイ サブネットのアドレス プレフィックスを定義する例を次に示します。VNet のアドレス空間は 10.119.0.0/16 です。組織では、初めはサイト対サイトの VPN 接続を使用しますが、最終的には ExpressRoute を入手することになります。ゲートウェイ サブネットのアドレス プレフィックスを決定する手順と結果をネットワークのプレフィックス表記 (CIDR とも呼ばれる) で表 2 に示します。</span><span class="sxs-lookup"><span data-stu-id="04962-p104">Here is an example of defining the address prefix for the gateway subnet: The address space of the VNet is 10.119.0.0/16. The organization will initially use a site-to-site VPN connection, but will eventually get ExpressRoute. Table 2 shows the steps and results of determining the gateway subnet address prefix in network prefix notation (also known as CIDR).</span></span>

<span data-ttu-id="04962-159">ゲートウェイ サブネットのアドレス プレフィックスを決定する手順と例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="04962-159">Here are the steps and example of determining the gateway subnet address prefix:</span></span>

1. <span data-ttu-id="04962-p105">ゲートウェイ サブネットのサイズを決定します。この例では、/28 を選択しました。</span><span class="sxs-lookup"><span data-stu-id="04962-p105">Decide on the size of the gateway subnet. For our example, we chose /28.</span></span>
2. <span data-ttu-id="04962-p106">Vnet アドレス空間 (b) の変数部分でのビットをゲートウェイ サブネット ビット (G) では 0、それ以外は 1 (v) に設定します。この例では、VNet に 10.119.0.0/16 アドレス空間を使用しています。</span><span class="sxs-lookup"><span data-stu-id="04962-p106">Set the bits in the variable portion of the VNet address space (b) to 0 for the gateway subnet bits (G), otherwise 1 (V). For our example, we are using the 10.119.0.0/16 address space for the VNet. </span></span><br/>
<br/><span data-ttu-id="04962-p107">10.119. bbbbbbbb . bbbbbbbb </span><span class="sxs-lookup"><span data-stu-id="04962-p107">10.119. bbbbbbbb . bbbbbbbb </span></span><br/><span data-ttu-id="04962-p108">10.119. VVVVVVVV . VVVVGGGG </span><span class="sxs-lookup"><span data-stu-id="04962-p108">10.119. VVVVVVVV . VVVVGGGG </span></span><br/><span data-ttu-id="04962-p109">10.119. 11111111 . 11110000</span><span class="sxs-lookup"><span data-stu-id="04962-p109">10.119. 11111111 . 11110000 </span></span><br/><br/>
3. <span data-ttu-id="04962-p110">手順 2 からの結果を 10 進数に変換し、アドレス空間として表現します。この例では、10.119. 11111111 . 11110000 は 10.119.255.240 となり、手順 1 からのプレフィックス長 (この例では 28) により、結果として得られるゲートウェイ サブネット アドレスのプレフィックスは 10.119.255.240/28 となります。</span><span class="sxs-lookup"><span data-stu-id="04962-p110">Convert the result from step 2 to decimal and express as an address space. For our example, 10.119. 11111111 . 11110000 is 10.119.255.240, and with the prefix length from step 1, (28 in our example), the resulting gateway subnet address prefix is 10.119.255.240/28.</span></span>
  
<span data-ttu-id="04962-177">詳細については、「[Azure ゲートウェイ サブネットのアドレス スペースの計算](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-177">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for more information.</span></span>
  
<span data-ttu-id="04962-178">Azure 仮想マシンは仮想マシン ホスト サブネットに配置します。これは一般的なオンプレミスのガイドライン (一般的なロール、アプリケーション層、サブネットの分離など) に従って行うことができます。</span><span class="sxs-lookup"><span data-stu-id="04962-178">Virtual machine-hosting subnets are where you place Azure virtual machines, which you can do according to typical on-premises guidelines, such as a common role or tier of an application or for subnet isolation.</span></span>
  
<span data-ttu-id="04962-p111">Azure は、各サブネット上の最初の 3 つのアドレスを使用します。したがって、Azure サブネット上の使用可能なアドレスの数は 2<sup>n</sup>の 5、ホスト ビットの数です。表 3 に示す必要な場合、ビットをホストする仮想マシンが、必要な数の範囲と対応するサブネットのサイズです。</span><span class="sxs-lookup"><span data-stu-id="04962-p111">Azure uses the first 3 addresses on each subnet. Therefore, the number of possible addresses on an Azure subnet is 2<sup>n</sup> - 5, where n is the number of host bits. Table 3 shows the range of virtual machines required, the number of hosts bits needed, and the corresponding subnet size.</span></span>
  
|<span data-ttu-id="04962-182">**必要な仮想マシン**</span><span class="sxs-lookup"><span data-stu-id="04962-182">**Virtual machines required**</span></span>|<span data-ttu-id="04962-183">**ホスト ビット**</span><span class="sxs-lookup"><span data-stu-id="04962-183">**Host bits**</span></span>|<span data-ttu-id="04962-184">**サブネットのサイズ**</span><span class="sxs-lookup"><span data-stu-id="04962-184">**Subnet size**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="04962-185">1-3</span><span class="sxs-lookup"><span data-stu-id="04962-185">1-3</span></span>  <br/> |<span data-ttu-id="04962-186">3</span><span class="sxs-lookup"><span data-stu-id="04962-186">3</span></span>  <br/> |<span data-ttu-id="04962-187">/29</span><span class="sxs-lookup"><span data-stu-id="04962-187">/29</span></span>  <br/> |
|<span data-ttu-id="04962-188">4-11</span><span class="sxs-lookup"><span data-stu-id="04962-188">4-11</span></span>  <br/> |<span data-ttu-id="04962-189">4</span><span class="sxs-lookup"><span data-stu-id="04962-189">4</span></span>  <br/> |<span data-ttu-id="04962-190">/28</span><span class="sxs-lookup"><span data-stu-id="04962-190">/28</span></span>  <br/> |
|<span data-ttu-id="04962-191">12-27</span><span class="sxs-lookup"><span data-stu-id="04962-191">12-27</span></span>  <br/> |<span data-ttu-id="04962-192">5</span><span class="sxs-lookup"><span data-stu-id="04962-192">5</span></span>  <br/> |<span data-ttu-id="04962-193">/27</span><span class="sxs-lookup"><span data-stu-id="04962-193">/27</span></span>  <br/> |
|<span data-ttu-id="04962-194">28-59</span><span class="sxs-lookup"><span data-stu-id="04962-194">28-59</span></span>  <br/> |<span data-ttu-id="04962-195">6</span><span class="sxs-lookup"><span data-stu-id="04962-195">6</span></span>  <br/> |<span data-ttu-id="04962-196">/26</span><span class="sxs-lookup"><span data-stu-id="04962-196">/26</span></span>  <br/> |
|<span data-ttu-id="04962-197">60-123</span><span class="sxs-lookup"><span data-stu-id="04962-197">60-123</span></span>  <br/> |<span data-ttu-id="04962-198">7</span><span class="sxs-lookup"><span data-stu-id="04962-198">7</span></span>  <br/> |<span data-ttu-id="04962-199">/25</span><span class="sxs-lookup"><span data-stu-id="04962-199">/25</span></span>  <br/> |
   
 <span data-ttu-id="04962-200">**表 3: 仮想マシンの要件とサブネットのサイズ**</span><span class="sxs-lookup"><span data-stu-id="04962-200">**Table 3: Virtual machine requirements and their subnet sizes**</span></span>
  
<span data-ttu-id="04962-201">サブネットまたは VNet 上の仮想マシンの最大数量の詳細については、「[ネットワークの制限](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-201">For more information about the maximum amount of virtual machines on a subnet or VNet, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="04962-202">詳細については、「[Azure 仮想ネットワークの計画と設計](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-202">For more information, see [Plan and design Azure Virtual Networks](https://azure.microsoft.com/documentation/articles/virtual-network-vnet-plan-design-arm/).</span></span>
  
### <a name="step-6-determine-the-dns-server-configuration-and-the-addresses-of-the-dns-servers-to-assign-to-vms-in-the-vnet"></a><span data-ttu-id="04962-203">手順 6:DNS サーバーの構成と DNS サーバーのアドレスを決定して、VNet の VM に割り当てる。</span><span class="sxs-lookup"><span data-stu-id="04962-203">Step 6: Determine the DNS server configuration and the addresses of the DNS servers to assign to VMs in the VNet.</span></span>

<span data-ttu-id="04962-p112">Azure は DHCP によって、仮想マシンに DNS サーバーのアドレスを割り当てます。DNS サーバーは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="04962-p112">Azure assigns virtual machines the addresses of DNS servers by DHCP. DNS servers can be:</span></span>
  
- <span data-ttu-id="04962-206">Azure で提供:ローカルでの名前登録と、ローカルおよびインターネットでの名前解決を提供します。</span><span class="sxs-lookup"><span data-stu-id="04962-206">Supplied by Azure: Provides local name registration and local and Internet name resolution</span></span>
    
- <span data-ttu-id="04962-207">ユーザーが提供:ローカルまたはイントラネットでの名前登録と、イントラネットまたはインターネットのいずれかでの名前解決を提供します。</span><span class="sxs-lookup"><span data-stu-id="04962-207">Provided by you: Provides local or intranet name registration and either intranet or Internet name resolution</span></span>
    
<span data-ttu-id="04962-208">表 4 は、DNS サーバーの異なる構成を、VNet の種類ごとに示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-208">Table 4 shows the different configurations of DNS servers for each type of VNet.</span></span>
    
|<span data-ttu-id="04962-209">**VNet の種類**</span><span class="sxs-lookup"><span data-stu-id="04962-209">**Type of VNet**</span></span>|<span data-ttu-id="04962-210">**DNS サーバー**</span><span class="sxs-lookup"><span data-stu-id="04962-210">**DNS server**</span></span>|
|:-----|:-----|
|<span data-ttu-id="04962-211">クラウド専用</span><span class="sxs-lookup"><span data-stu-id="04962-211">Cloud-only</span></span>  <br/> |<span data-ttu-id="04962-212">Azure で提供される場合は、ローカルおよびインターネットでの名前解決</span><span class="sxs-lookup"><span data-stu-id="04962-212">Azure-supplied for local and Internet name resolution</span></span>  <br/> <span data-ttu-id="04962-213">Azure 仮想マシンの場合は、ローカルおよびインターネットでの名前解決 (DNS 転送)</span><span class="sxs-lookup"><span data-stu-id="04962-213">Azure virtual machine for local and Internet name resolution (DNS forwarding)</span></span>  <br/> |
|<span data-ttu-id="04962-214">クロスプレミス</span><span class="sxs-lookup"><span data-stu-id="04962-214">Cross-premises</span></span>  <br/> |<span data-ttu-id="04962-215">オンプレミスの場合は、ローカルおよびイントラネットでの名前解決</span><span class="sxs-lookup"><span data-stu-id="04962-215">On-premises for local and intranet name resolution</span></span>  <br/> <span data-ttu-id="04962-216">Azure 仮想マシンの場合は、ローカルおよびイントラネットでの名前解決 (DNS レプリケーションおよび転送)</span><span class="sxs-lookup"><span data-stu-id="04962-216">Azure virtual machine for local and intranet name resolution (DNS replication and forwarding)</span></span>  <br/> |
   
 <span data-ttu-id="04962-217">**表 4: 異なる 2 つの種類の VNet 用の DNS サーバーのオプション**</span><span class="sxs-lookup"><span data-stu-id="04962-217">**Table 4: DNS server options for the two different types of VNets**</span></span>
  
<span data-ttu-id="04962-218">詳細については、「[VM とロール インスタンスの名前解決](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-218">For more information, see [Name Resolution for VMs and Role Instances](https://docs.microsoft.com/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances).</span></span>
  
### <a name="step-7-determine-the-load-balancing-configuration-internet-facing-or-internal"></a><span data-ttu-id="04962-219">手順 7:負荷分散の構成 (インターネット接続か内部接続か) を決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-219">Step 7: Determine the load balancing configuration (Internet-facing or internal).</span></span>

<span data-ttu-id="04962-p113">場合によっては、同じロールのサーバーのセットに着信トラフィックを分散する必要があります。Azure IaaS には、インターネット接続および内部トラフィックの負荷に対してこれを行うための機能が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="04962-p113">In some cases, you want to distribute incoming traffic to a set of servers that have the same role. Azure IaaS has a built-in facility to do this for Internet-facing and internal traffic loads.</span></span>
  
<span data-ttu-id="04962-222">Azure のインターネット接続の負荷分散は、インターネットから負荷分散セットのメンバーへの未承諾の着信トラフィックをランダムに分散します。</span><span class="sxs-lookup"><span data-stu-id="04962-222">Azure Internet-facing load balancing randomly distributes unsolicited incoming traffic from the Internet to the members of a load-balanced set.</span></span>
  
<span data-ttu-id="04962-223">**図 4: Azure の外部ロード バランサー**</span><span class="sxs-lookup"><span data-stu-id="04962-223">**Figure 4: An external load balancer in Azure**</span></span>

![図 4: Azure の外部ロード バランサー](media/eb5945e5-0c2b-40f1-b9ed-54bb2b0f9e59.png)
  
<span data-ttu-id="04962-225">図 4 は、受信 NAT 規則、または負荷分散セット内の仮想マシンへのエンドポイントに着信トラフィックを分散する、Azure の外部ロード バランサーを示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-225">Figure 4 shows an external load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="04962-226">Azure の内部負荷分散は、他の Azure VM またはイントラネット コンピューターから負荷分散セットのメンバーへの未承諾の着信トラフィックをランダムに分散します。</span><span class="sxs-lookup"><span data-stu-id="04962-226">Azure internal load balancing randomly distributes unsolicited incoming traffic from other Azure VMs or from intranet computers to the members of a load-balanced set.</span></span> 
  
<span data-ttu-id="04962-227">**図 5: Azure での内部ロード バランサー**</span><span class="sxs-lookup"><span data-stu-id="04962-227">**Figure 5: An internal load balancer in Azure**</span></span>

![図 5: Azure での内部ロード バランサー](media/d1451b73-6465-449d-b3e6-22160ce51f35.png)
  
<span data-ttu-id="04962-229">図 5 は、受信 NAT 規則、または負荷分散セット内の仮想マシンへのエンドポイントに着信トラフィックを分散する、Azure の内部ロード バランサーを示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-229">Figure 5 shows an internal load balancer in Azure that distributes incoming traffic on an inbound NAT rule or endpoint to a set of virtual machines in a load-balanced set.</span></span>
  
<span data-ttu-id="04962-230">詳細については、「[Azure ロード バランサー](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-230">For more information, see [Azure Load Balancer](https://docs.microsoft.com/azure/load-balancer/load-balancer-overview).</span></span>
  
### <a name="step-8-determine-the-use-of-virtual-appliances-and-user-defined-routes"></a><span data-ttu-id="04962-231">手順 8:仮想アプライアンスおよびユーザー定義ルートの使用を決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-231">Step 8: Determine the use of virtual appliances and user-defined routes.</span></span>

<span data-ttu-id="04962-232">トラフィックを VNet の仮想アプライアンスに転送する必要がある場合、サブネットに 1 つ以上のユーザー定義のルートを追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="04962-232">If you need to forward traffic to virtual appliances in your VNet, you may need to add one or more user-defined routes to a subnet.</span></span>
  
<span data-ttu-id="04962-233">**図 6: 仮想アプライアンスと Azure 内のユーザー定義ルート**</span><span class="sxs-lookup"><span data-stu-id="04962-233">**Figure 6: Virtual appliances and user-defined routes in Azure**</span></span>

![図 6: 仮想アプライアンスと Azure 内のユーザー定義ルート](media/f181d0f4-ebf9-439e-9c98-dec17428c32b.png)
  
<span data-ttu-id="04962-235">図 6 は、仮想アプライアンスを指す仮想マシン ホスト サブネットに割り当てられたクロスプレミスの VNet とユーザー定義のルートを示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-235">Figure 6 shows a cross-premises VNet and a user-defined route assigned to a virtual machine-hosting subnet that points to a virtual appliance.</span></span>
  
<span data-ttu-id="04962-236">詳細については、「[ユーザー定義のルートおよび IP 転送](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-236">For more information, see [User Defined Routes and IP Forwarding](https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview).</span></span>
  
### <a name="step-9-determine-how-computers-from-the-internet-will-connect-to-virtual-machines"></a><span data-ttu-id="04962-237">手順 9:インターネットからコンピューターが仮想マシンに接続する方法を決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-237">Step 9: Determine how computers from the Internet will connect to virtual machines.</span></span>

<span data-ttu-id="04962-238">VNet の仮想マシンへのインターネット アクセス (組織ネットワークからプロキシ サーバーや他のエッジ デバイスを経由するアクセスを含む) を提供する方法は複数あります。</span><span class="sxs-lookup"><span data-stu-id="04962-238">There are multiple ways to provide Internet access to the virtual machines on a VNet, which includes access from your organization network through your proxy server or other edge device.</span></span>
  
<span data-ttu-id="04962-239">未承諾の着信トラフィックをフィルター処理または検査する方法を表 5 に示します。</span><span class="sxs-lookup"><span data-stu-id="04962-239">Table 5 lists the methods for filtering or inspecting unsolicited incoming traffic.</span></span>
  
|<span data-ttu-id="04962-240">**メソッド**</span><span class="sxs-lookup"><span data-stu-id="04962-240">**Method**</span></span>|<span data-ttu-id="04962-241">**展開モデル**</span><span class="sxs-lookup"><span data-stu-id="04962-241">**Deployment model**</span></span>|
|:-----|:-----|
|<span data-ttu-id="04962-242">1.クラウド サービス上で構成されたエンドポイントおよび ACL</span><span class="sxs-lookup"><span data-stu-id="04962-242">1. Endpoints and ACLs configured on cloud services</span></span>  <br/> |<span data-ttu-id="04962-243">クラシック</span><span class="sxs-lookup"><span data-stu-id="04962-243">Classic</span></span>  <br/> |
|<span data-ttu-id="04962-244">2.ネットワーク セキュリティ グループ</span><span class="sxs-lookup"><span data-stu-id="04962-244">2. Network security groups</span></span>  <br/> |<span data-ttu-id="04962-245">リソース マネージャーおよびクラシック</span><span class="sxs-lookup"><span data-stu-id="04962-245">Resource Manager and classic</span></span>  <br/> |
|<span data-ttu-id="04962-246">3.受信 NAT 規則を使用するインターネット接続ロード バランサー</span><span class="sxs-lookup"><span data-stu-id="04962-246">3. Internet-facing load balancer with inbound NAT rules</span></span>  <br/> |<span data-ttu-id="04962-247">リソース管理者</span><span class="sxs-lookup"><span data-stu-id="04962-247">Resource Manager</span></span>  <br/> |
|<span data-ttu-id="04962-248">4.Azure Marketplace でのネットワーク セキュリティ アプライアンス (表示されていません)</span><span class="sxs-lookup"><span data-stu-id="04962-248">4. Network security appliances in the Azure Marketplace (not shown)</span></span>  <br/> |<span data-ttu-id="04962-249">リソース マネージャーおよびクラシック</span><span class="sxs-lookup"><span data-stu-id="04962-249">Resource Manager and classic</span></span>  <br/> |
   
 <span data-ttu-id="04962-250">**表 5: 仮想マシンと対応する Azure 展開モデルに接続する方法**</span><span class="sxs-lookup"><span data-stu-id="04962-250">**Table 5: Methods of connecting to virtual machines and their corresponding Azure deployment models**</span></span>
  
<span data-ttu-id="04962-251">**図 7: インターネット経由で Azure 仮想マシンに接続する**</span><span class="sxs-lookup"><span data-stu-id="04962-251">**Figure 7: Connecting to Azure virtual machines over the Internet**</span></span>

![図 7: インターネット経由で Azure 仮想マシンに接続する](media/c5e3531b-170a-4482-a6ff-fb8fbbe81b35.png)
  
<span data-ttu-id="04962-253">図 7 は、エンドポイントを使用してクラウド サービス内の仮想マシンに接続しているインターネットに接続されたコンピューター、ネットワーク セキュリティ グループを使用するサブネット上の仮想マシン、および外部ロード バランサーと受信 NAT 規則を使用するサブネット上の仮想マシンを示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-253">Figure 7 shows an Internet-connected computer connecting to a virtual machine in a cloud service using an endpoint, a virtual machine on a subnet using a network security group, and a virtual machine on a subnet using an external load balancer and inbound NAT rules.</span></span>
  
<span data-ttu-id="04962-254">追加のセキュリティは、以下のものから提供されます。</span><span class="sxs-lookup"><span data-stu-id="04962-254">Additional security is provided by:</span></span>
  
- <span data-ttu-id="04962-255">認証され、暗号化されたリモート デスクトップおよび SSH 接続。</span><span class="sxs-lookup"><span data-stu-id="04962-255">Remote Desktop and SSH connections, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="04962-256">認証され、暗号化されたリモート PowerShell セッション。</span><span class="sxs-lookup"><span data-stu-id="04962-256">Remote PowerShell sessions, which are authenticated and encrypted.</span></span>
    
- <span data-ttu-id="04962-257">エンド ツー エンドの暗号化に使用できる IPsec トランスポート モード。</span><span class="sxs-lookup"><span data-stu-id="04962-257">IPsec transport mode, which you can use for end-to-end encryption.</span></span>
    
- <span data-ttu-id="04962-258">Azure DDoS の保護。外部および内部の攻撃を防止するために有用。</span><span class="sxs-lookup"><span data-stu-id="04962-258">Azure DDOS protection, which helps prevent external and internal attacks</span></span>
    
<span data-ttu-id="04962-259">詳細については、「[エンタープライズ アーキテクトのための Microsoft クラウドのセキュリティ](https://aka.ms/cloudarchsecurity)」および「[Azure のネットワーク セキュリティ](https://azure.microsoft.com/blog/azure-network-security/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-259">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-10-for-multiple-vnets-determine-the-vnet-to-vnet-connection-topology"></a><span data-ttu-id="04962-260">手順 10:複数の VNet に対して、VNet 間の接続トポロジを決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-260">Step 10: For multiple VNets, determine the VNet-to-VNet connection topology.</span></span>

<span data-ttu-id="04962-261">VNet と VNet は、組織のサイトの接続に使用するトポロジと同様のトポロジを使用して、互いに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="04962-261">VNets can be connected to each other using topologies similar to those used for connecting the sites of an organization.</span></span>
  
<span data-ttu-id="04962-262">デイジー チェーン構成は、一連の VNet を接続します。</span><span class="sxs-lookup"><span data-stu-id="04962-262">A daisy chain configuration connects the VNets in a series.</span></span>
  
<span data-ttu-id="04962-263">**図 8: VNet のデイジー チェーン構成**</span><span class="sxs-lookup"><span data-stu-id="04962-263">**Figure 8: A daisy-chained configuration for VNets**</span></span>

![図 8:Azure 仮想ネットワークのデイジーチェーン構成](media/264d5dd4-06c5-483f-9428-a18cc1f68ac1.png)
  
<span data-ttu-id="04962-265">図 8 は、デイジー チェーン構成を使用して連続的に接続された 5 つの VNet を示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-265">Figure 8 shows five VNets connected in series using a daisy-chained configuration.</span></span>
  
<span data-ttu-id="04962-266">スポークおよびハブ構成は複数の VNet を中央の VNet のセットに接続します。中央の VNet のセットでは、VNet と VNet が互いに接続されています。</span><span class="sxs-lookup"><span data-stu-id="04962-266">A spoke and hub configuration connects multiple VNets to a set of central VNets, which are themselves connected to each other.</span></span>
  
<span data-ttu-id="04962-267">**図 9: VNet のスポークおよびハブ構成**</span><span class="sxs-lookup"><span data-stu-id="04962-267">**Figure 9: A spoke and hub configuration for VNets**</span></span>

![図 9: Azure 仮想ネットワークのスポークとハブ構成](media/dd442a38-5b76-4ac5-b743-8fc7711a91ba.png)
  
<span data-ttu-id="04962-269">図 9 は 6 つの VNet を示しています。2 つの VNet がハブになります。ハブは互いに接続し、他の 2 つのスポーク VNet にも接続しています。</span><span class="sxs-lookup"><span data-stu-id="04962-269">Figure 9 shows six VNets, two VNets are hubs that are connected to each other and also two other spoke VNets.</span></span>
  
<span data-ttu-id="04962-270">フル メッシュ構成は、すべての VNet を相互接続します。</span><span class="sxs-lookup"><span data-stu-id="04962-270">A full mesh configuration connects every VNet to each other.</span></span>
  
<span data-ttu-id="04962-271">**図 10: VNet のフル メッシュ構成**</span><span class="sxs-lookup"><span data-stu-id="04962-271">**Figure 10: A full mesh configuration for VNets**</span></span>

![図 10: Azure 仮想ネットワークのメッシュ構成](media/9dda0738-10db-4a63-95b3-79851a399b71.png)
  
<span data-ttu-id="04962-273">図 10 は、合計 6 つの VNet 間接続を使用する、すべてが互いに接続された 4 つの VNet を示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-273">Figure 10 shows four VNets that are all connected to each other, using a total of six VNet-to-VNet connections.</span></span>
  
## <a name="planning-steps-for-a-cross-premises-vnet"></a><span data-ttu-id="04962-274">クロスプレミスの VNet 用の手順を計画する</span><span class="sxs-lookup"><span data-stu-id="04962-274">Planning steps for a cross-premises VNet</span></span>
<span data-ttu-id="04962-275"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="04962-275"><a name="cross_prem"> </a></span></span>

<span data-ttu-id="04962-276">次に示すクロスプレミスの VNet 用の手順を実行してください。</span><span class="sxs-lookup"><span data-stu-id="04962-276">Follow these steps for a cross-premises VNet.</span></span>
  
> [!TIP]
> <span data-ttu-id="04962-277">シミュレートされたクロスプレミスの開発/テスト環境を作成するには、「[Azure でのシミュレートされたクロスプレミスの仮想ネットワーク](simulated-cross-premises-virtual-network-in-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-277">To create a simulated cross-premises dev/test environment, see [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).</span></span> 
  
### <a name="step-1-determine-the-cross-premises-connection-to-the-vnet-s2s-vpn-or-expressroute"></a><span data-ttu-id="04962-278">手順 1:VNet (S2S VPN または ExpressRoute) へのクロスプレミス接続を決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-278">Step 1: Determine the cross-premises connection to the VNet (S2S VPN or ExpressRoute).</span></span>

<span data-ttu-id="04962-279">異なる種類の接続を表 6 に示します。</span><span class="sxs-lookup"><span data-stu-id="04962-279">Table 6 lists the different types of connections.</span></span>
  
|<span data-ttu-id="04962-280">**接続の種類**</span><span class="sxs-lookup"><span data-stu-id="04962-280">**Type of connection**</span></span>|<span data-ttu-id="04962-281">**用途**</span><span class="sxs-lookup"><span data-stu-id="04962-281">**Purpose**</span></span>|
|:-----|:-----|
|<span data-ttu-id="04962-282">サイト対サイト (S2S) VPN</span><span class="sxs-lookup"><span data-stu-id="04962-282">Site-to-Site (S2S) VPN</span></span>  <br/> |<span data-ttu-id="04962-283">1 つの VNet に 1 から 10 のサイト (他の VNet を含む) を接続する。</span><span class="sxs-lookup"><span data-stu-id="04962-283">Connect 1-10 sites (including other VNets) to a single VNet.</span></span>  <br/> |
|<span data-ttu-id="04962-284">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="04962-284">ExpressRoute</span></span>  <br/> |<span data-ttu-id="04962-285">インターネット エクスチェンジ プロバイダー (IXP) またはネットワーク サービス プロバイダー (NSP) 経由で Azure に接続する、プライベートで安全なリンク。</span><span class="sxs-lookup"><span data-stu-id="04962-285">A private, secure link to Azure via an Internet Exchange Provider (IXP) or a Network Service Provider (NSP).</span></span>  <br/> |
|<span data-ttu-id="04962-286">ポイント対サイト (P2S) VPN</span><span class="sxs-lookup"><span data-stu-id="04962-286">Point-to-Site (P2S) VPN</span></span>  <br/> |<span data-ttu-id="04962-287">1 台のコンピューターを VNet に接続する。</span><span class="sxs-lookup"><span data-stu-id="04962-287">Connects a single computer to a VNet.</span></span>  <br/> |
|<span data-ttu-id="04962-288">VNet のピアリングまたは VNet-to-VNet (V2V) VPN</span><span class="sxs-lookup"><span data-stu-id="04962-288">VNet peering or VNet-to-VNet (V2V) VPN</span></span>  <br/> |<span data-ttu-id="04962-289">VNet を他の VNet に接続する。</span><span class="sxs-lookup"><span data-stu-id="04962-289">Connects a VNet to another VNet.</span></span>  <br/> |
   
 <span data-ttu-id="04962-290">**表 6: クロスプレミス VNet 用の接続の種類**</span><span class="sxs-lookup"><span data-stu-id="04962-290">**Table 6: The types of connections for cross-premises VNets**</span></span>
  
<span data-ttu-id="04962-291">接続の最大数の詳細については、「[ネットワークの制限](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-291">For more information on the maximum number of connections, see [Networking Limits](https://docs.microsoft.com/azure/azure-subscription-service-limits#networking-limits).</span></span>
  
<span data-ttu-id="04962-292">VPN デバイスの詳細については、「[サイト対サイトの仮想ネットワーク接続用の VPN デバイス](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-292">For more information about VPN devices, see [VPN devices for site-to-site virtual network connections](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="04962-293">VNet ピアリングの詳細については、「[VNet ピアリング](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-293">For more information about VNet peering, see [VNet peering](https://docs.microsoft.com/azure/virtual-network/virtual-network-peering-overview).</span></span>
  
<span data-ttu-id="04962-294">**図 11: クロスプレミス VNet に接続する 4 つの方法**</span><span class="sxs-lookup"><span data-stu-id="04962-294">**Figure 11: The four ways to connect to a cross-premises VNet**</span></span>

![図 11:クロスプレミスの Azure 仮想ネットワークに接続する 3 つの方法](media/d5d4a625-cfbd-4a77-9159-eaca69d07e93.png)
  
<span data-ttu-id="04962-296">図 11 は、VNet の 4 種類の接続方法 (コンピューターからの P2S 接続、オンプレミス ネットワークからの S2S VPN 接続、オンプレミス ネットワークからの ExpressRoute 接続、他の VNet からの VNet 対 VNet 接続) を示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-296">Figure 11 shows a VNet with the four types of connections: a P2S connection from a computer, an S2S VPN connection from an on-premises network, an ExpressRoute connection from an on-premises network, and a VNet-to-VNet connection from another VNet.</span></span> 
  
<span data-ttu-id="04962-297">VNet 内の VM には、次の方法で接続できます。</span><span class="sxs-lookup"><span data-stu-id="04962-297">You can connect to VMs in a VNet in the following ways:</span></span>
  
- <span data-ttu-id="04962-298">オンプレミス ネットワークまたはインターネットから VNet の VM を管理する</span><span class="sxs-lookup"><span data-stu-id="04962-298">Administration of VNet VMs from your on-premises network or the Internet</span></span>
    
- <span data-ttu-id="04962-299">オンプレミス ネットワークからの IT ワークロードのアクセス</span><span class="sxs-lookup"><span data-stu-id="04962-299">IT workload access from your on-premises network</span></span>
    
- <span data-ttu-id="04962-300">追加の VNet を通じてネットワークを拡張する</span><span class="sxs-lookup"><span data-stu-id="04962-300">Extension of your network through additional VNets</span></span>
    
<span data-ttu-id="04962-301">接続のセキュリティは、次のことから確保されます。</span><span class="sxs-lookup"><span data-stu-id="04962-301">Security for connections is provided by the following:</span></span>
  
- <span data-ttu-id="04962-302">P2S で Secure Socket トンネリング プロトコル (SSTP) を使用する</span><span class="sxs-lookup"><span data-stu-id="04962-302">P2S uses the Secure Socket Tunneling Protocol (SSTP)</span></span> 
    
- <span data-ttu-id="04962-303">S2S および VNet 対 VNet VPN 接続で AES256 を使用した IPsec トンネル モードを使用する</span><span class="sxs-lookup"><span data-stu-id="04962-303">S2S and VNet-to-VNet VPN connections use IPsec tunnel mode with AES256</span></span>
    
- <span data-ttu-id="04962-304">ExpressRoute はプライベート WAN 接続。</span><span class="sxs-lookup"><span data-stu-id="04962-304">ExpressRoute is a private WAN connection</span></span>
    
<span data-ttu-id="04962-305">詳細については、「[エンタープライズ アーキテクトのための Microsoft クラウドのセキュリティ](https://aka.ms/cloudarchsecurity)」および「[Azure のネットワーク セキュリティ](https://azure.microsoft.com/blog/azure-network-security/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-305">For more information, see [Microsoft Cloud Security for Enterprise Architects](https://aka.ms/cloudarchsecurity) and [Azure Network Security](https://azure.microsoft.com/blog/azure-network-security/).</span></span>
  
### <a name="step-2-determine-the-on-premises-vpn-device-or-router"></a><span data-ttu-id="04962-306">手順 2:オンプレミスの VPN デバイスまたはルーターを決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-306">Step 2: Determine the on-premises VPN device or router.</span></span>

<span data-ttu-id="04962-307">オンプレミスの VPN デバイスやルーターは、次のように機能します。</span><span class="sxs-lookup"><span data-stu-id="04962-307">Your on-premises VPN device or router acts as:</span></span>
  
- <span data-ttu-id="04962-308">Azure ゲートウェイからの S2S VPN 接続を終了する IPsec ピア。</span><span class="sxs-lookup"><span data-stu-id="04962-308">An IPsec peer, terminating the S2S VPN connection from the Azure gateway.</span></span>
    
- <span data-ttu-id="04962-309">プライベート ピアリング ExpressRoute 接続の BPG ピアおよび終端点。</span><span class="sxs-lookup"><span data-stu-id="04962-309">The BPG peer and termination point for the private peering ExpressRoute connection.</span></span>
    
<span data-ttu-id="04962-310">**図 12: オンプレミスの VPN ルーターまたはデバイス**</span><span class="sxs-lookup"><span data-stu-id="04962-310">**Figure 12: The on-premises VPN router or device**</span></span>

![図 12: オンプレミスの VPN ルーターまたはデバイス](media/bd221468-a660-4730-aa55-0426986480b9.png)
  
<span data-ttu-id="04962-312">図 12 は、オンプレミスの VPN ルーターまたはデバイスに接続されるクロスプレミスの VNet を示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-312">Figure 12 shows a cross-premises VNet connected to an on-premises VPN router or device.</span></span>
  
<span data-ttu-id="04962-313">詳細については、「[VPN Gateway について](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-313">For more information, see [About VPN gateway](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways).</span></span>
  
### <a name="step-3-add-routes-to-your-intranet-to-make-the-address-space-of-the-vnet-reachable"></a><span data-ttu-id="04962-314">手順 3: VNet のアドレス空間に到達可能なルートをイントラネットに追加する。</span><span class="sxs-lookup"><span data-stu-id="04962-314">Step 3: Add routes to your intranet to make the address space of the VNet reachable.</span></span>

<span data-ttu-id="04962-315">オンプレミスから VNet へのルーティングは、次のもので構成されています。</span><span class="sxs-lookup"><span data-stu-id="04962-315">Routing to VNets from on-premises consists of the following:</span></span>
  
1. <span data-ttu-id="04962-316">VPN デバイスを指す VNet アドレス空間のルート。</span><span class="sxs-lookup"><span data-stu-id="04962-316">A route for the VNet address space that points toward your VPN device.</span></span>
    
2. <span data-ttu-id="04962-317">S2S VPN または ExpressRoute 接続全体を指す VPN デバイス上の VNet アドレス空間のルート。</span><span class="sxs-lookup"><span data-stu-id="04962-317">A route for the VNet address space on your VPN device that points across the S2S VPN or ExpressRoute connection</span></span>
    
<span data-ttu-id="04962-318">**図 13: VNet へのアクセスを可能にするために必要なオンプレミスのルート**</span><span class="sxs-lookup"><span data-stu-id="04962-318">**Figure 13: The on-premises routes needed to make a VNet reachable**</span></span>

![図 13: Azure VNet に到達可能にする必要があるオンプレミスのルート](media/7a1e20c1-fbc4-4cb9-9961-735da4e23307.png)
  
<span data-ttu-id="04962-320">図 13 は、オンプレミスのルーターと、VNet のアドレス空間を表す VPN ルーターやデバイスに必要なルーティング情報を示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-320">Figure 13 shows the routing information needed by the on-premises routers and the VPN router or device that represents the address space of the VNet.</span></span>
  
### <a name="step-4-for-expressroute-plan-for-the-new-connection-with-your-provider"></a><span data-ttu-id="04962-321">手順 4:ExpressRoute 用にプロバイダーへの新しい接続を計画する。</span><span class="sxs-lookup"><span data-stu-id="04962-321">Step 4: For ExpressRoute, plan for the new connection with your provider.</span></span>

<span data-ttu-id="04962-322">次に示す 3 種類の方法で、オンプレミスのネットワークと Microsoft クラウドの間にプライベート ピアリングの ExpressRoute 接続を作成できます。</span><span class="sxs-lookup"><span data-stu-id="04962-322">You can create an ExpressRoute connection with private peering between your on-premises network and the Microsoft cloud in three different ways:</span></span>
  
- <span data-ttu-id="04962-323">Cloud Exchange でのコロケーション</span><span class="sxs-lookup"><span data-stu-id="04962-323">Co-located at a cloud exchange</span></span>
    
- <span data-ttu-id="04962-324">ポイント ツー ポイントのイーサネット接続</span><span class="sxs-lookup"><span data-stu-id="04962-324">Point-to-point Ethernet connections</span></span>
    
- <span data-ttu-id="04962-325">Any-to-any (IP VPN) ネットワーク</span><span class="sxs-lookup"><span data-stu-id="04962-325">Any-to-any (IP VPN) networks</span></span>
    
<span data-ttu-id="04962-326">**図 14: ExpressRoute を使用してクロスプレミスの VNet に接続する**</span><span class="sxs-lookup"><span data-stu-id="04962-326">**Figure 14: Using ExpressRoute to connect to a cross-premises VNet**</span></span>

![図 14:ExpressRoute を使用してクロスプレミスの Azure 仮想ネットワークに接続する](media/7030bd39-69a6-4283-8567-3434e1ab6ba6.png)
  
<span data-ttu-id="04962-328">図 14 は、オンプレミスのルーターから Microsoft Azure へのクロスプレミスの VNet と ExpressRoute 接続を示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-328">Figure 14 shows a cross-premises VNet and an ExpressRoute connection from an on-premises router to Microsoft Azure.</span></span>
  
<span data-ttu-id="04962-329">詳細については、「[Microsoft クラウド接続のための ExpressRoute](expressroute-for-microsoft-cloud-connectivity.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-329">For more information, see [ExpressRoute for Microsoft cloud connectivity](expressroute-for-microsoft-cloud-connectivity.md).</span></span>
  
### <a name="step-5-determine-the-local-network-address-space-for-the-azure-gateway"></a><span data-ttu-id="04962-330">手順 5:Azure ゲートウェイのローカル ネットのワーク アドレス空間を決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-330">Step 5: Determine the Local Network address space for the Azure gateway.</span></span>

<span data-ttu-id="04962-331">オンプレミスまたは VNet から他の VNet へのルーティングの場合、Azure はゲートウェイに割り当てられたローカル ネットワークのアドレス空間と一致する Azure ゲートウェイを経由して、トラフィックを転送します。</span><span class="sxs-lookup"><span data-stu-id="04962-331">For the routing to on-premises or other VNets from a VNet, Azure forwards traffic across an Azure gateway that matches the Local Network address space assigned to the gateway.</span></span>
  
<span data-ttu-id="04962-332">**図 15: クロスプレミスの VNet 用のローカル ネットワーク アドレス空間**</span><span class="sxs-lookup"><span data-stu-id="04962-332">**Figure 15: The Local Network address space for a cross-premises VNet**</span></span>

![図 15: クロスプレミス Azure 仮想ネットワーク用のローカル ネットワーク アドレス空間](media/e3af2652-8b8e-4551-9a0b-b550e6e7e3c0.png)
  
<span data-ttu-id="04962-334">図 15 は、クロスプレミス VNet と、オンプレミス ネットワークの到達可能なアドレス空間を表す Azure ゲートウェイのローカル ネットワークのアドレス空間を示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-334">Figure 15 shows a cross-premises VNet and the Local Network address space on the Azure gateway, which represents the reachable address space on the on-premises network.</span></span> 
  
<span data-ttu-id="04962-335">ローカル ネットワークのアドレス空間を定義する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="04962-335">You can define the Local Network address space in the following ways:</span></span>
  
- <span data-ttu-id="04962-336">オプション 1:現在必要か、使用中のアドレス空間のプレフィックスの一覧 (新しいサブネットを追加した場合は更新が必要)。</span><span class="sxs-lookup"><span data-stu-id="04962-336">Option 1: The list of prefixes for the address space currently needed or in use (updates might be needed when you add new subnets).</span></span>
    
- <span data-ttu-id="04962-337">オプション 2:すべてのオンプレミスのアドレス空間 (新しいアドレス空間を追加した場合のみ更新が必要)。</span><span class="sxs-lookup"><span data-stu-id="04962-337">Option 2: Your entire on-premises address space (updates only needed when you add new address space).</span></span>
    
<span data-ttu-id="04962-338">Azure ゲートウェイでは要約ルートが許可されないため、オプション 2 のローカル ネットワークのアドレス空間を定義して、VNet アドレス空間が含まれないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04962-338">Because the Azure gateway does not allow summarized routes, you must define the Local Network address space for option 2 so that it does not include the VNet address space.</span></span>
  
<span data-ttu-id="04962-339">**図 16: VNet アドレス空間によって作られたアドレス空間の穴**</span><span class="sxs-lookup"><span data-stu-id="04962-339">**Figure 16: The address space hole created by the VNet address space**</span></span>

![図 16: 仮想ネットワークのアドレス空間によって作られたアドレス空間の穴](media/e79c4840-f9e3-4741-9b72-59db6043aefa.png)
  
<span data-ttu-id="04962-341">図 16 は、アドレス空間 (ルート領域と VNet アドレス空間) を表しています。</span><span class="sxs-lookup"><span data-stu-id="04962-341">Figure 16 shows a representation of an address space, with the root space and the VNet address space.</span></span>
  
<span data-ttu-id="04962-342">次の例は、VNet によって作成されたアドレス空間の「穴」の周囲にあるローカル ネットワークのアドレス空間にプレフィックスを定義します。</span><span class="sxs-lookup"><span data-stu-id="04962-342">Here is an example of defining the prefixes for the Local Network address space around the address space "hole" created by the VNet:</span></span>
  
- <span data-ttu-id="04962-p114">組織はプライベートのアドレス空間 (10.0.0.0/8、172.16.0.0/12、および 192.168.0.0/16) の一部をオンプレミスのネットワーク経由で使用します。組織では VNet のアドレス空間として、オプション 2 と 10.100.100.0/24 を選択します。</span><span class="sxs-lookup"><span data-stu-id="04962-p114">An organization uses portions of the private address space (10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16) across their on-premises network. They chose option 2 and 10.100.100.0/24 as their VNet address space.</span></span>
    
<span data-ttu-id="04962-345">この例のローカル ネットワークのアドレス空間を定義する手順と、その結果生じるプレフィックスを表 7 に示します。</span><span class="sxs-lookup"><span data-stu-id="04962-345">Table 7 shows the steps and resulting prefixes that define the Local Network address space for this example.</span></span>
  
|<span data-ttu-id="04962-346">**手順**</span><span class="sxs-lookup"><span data-stu-id="04962-346">**Step**</span></span>|<span data-ttu-id="04962-347">**結果**</span><span class="sxs-lookup"><span data-stu-id="04962-347">**Results**</span></span>|
|:-----|:-----|
|<span data-ttu-id="04962-348">1. VNet アドレス空間のルート領域でないプレフィックスを一覧表示する。</span><span class="sxs-lookup"><span data-stu-id="04962-348">1. List the prefixes that are not the root space for the VNet address space.</span></span>  <br/> |<span data-ttu-id="04962-349">172.16.0.0/12 および 192.168.0.0/16</span><span class="sxs-lookup"><span data-stu-id="04962-349">172.16.0.0/12 and 192.168.0.0/16</span></span>  <br/> |
|<span data-ttu-id="04962-350">2.最後に使用した VNet アドレス空間内のオクテットの直前までの、変数オクテットの重複していないプレフィックスを一覧表示する。</span><span class="sxs-lookup"><span data-stu-id="04962-350">2. List the non-overlapping prefixes for variable octets up to but not including the last used octet in the VNet address space.</span></span>  <br/> |<span data-ttu-id="04962-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 プレフィックス、10.100.0.0/16 はスキップ)</span><span class="sxs-lookup"><span data-stu-id="04962-351">10.0.0.0/16, 10.1.0.0/16…10.99.0.0/16, 10.101.0.0/16…10.254.0.0/16, 10.255.0.0/16 (255 prefixes, skipping 10.100.0.0/16)</span></span>  <br/> |
|<span data-ttu-id="04962-352">3. VNet アドレス空間の最後に使用したオクテット内の重複していないプレフィックスを一覧表示する。</span><span class="sxs-lookup"><span data-stu-id="04962-352">3. List the non-overlapping prefixes within the last used octet of the VNet address space.</span></span>  <br/> |<span data-ttu-id="04962-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 プレフィックス、10.100.100.0/24 はスキップ)</span><span class="sxs-lookup"><span data-stu-id="04962-353">10.100.0.0/24, 10.100.1.0/24…10.100.99.0/24, 10.100.101.0/24…10.100.254.0/24, 10.100.0.255.0/24 (255 prefixes, skipping 10.100.100.0/24)</span></span>  <br/> |
   
 <span data-ttu-id="04962-354">**表 7: ローカル アドレスのネットワーク空間の例**</span><span class="sxs-lookup"><span data-stu-id="04962-354">**Table 7: Example Local Address network space**</span></span>
  
### <a name="step-6-configure-on-premises-dns-servers-for-dns-replication-with-dns-servers-hosted-in-azure"></a><span data-ttu-id="04962-355">手順 6: DNS レプリケーション用のオンプレミスの DNS サーバーと Azure でホストされる DNS サーバーを構成する</span><span class="sxs-lookup"><span data-stu-id="04962-355">Step 6: Configure on-premises DNS servers for DNS replication with DNS servers hosted in Azure.</span></span>

<span data-ttu-id="04962-356">オンプレミス コンピューターが Azure ベースのサーバーの名前を解決したり、Azure ベースのサーバーがオンプレミスのコンピューターの名前を解決するには、次に示す構成を行います。</span><span class="sxs-lookup"><span data-stu-id="04962-356">To ensure that on-premises computers can resolve the names of Azure-based servers and Azure-based servers can resolve the names of on-premises computers, configure:</span></span>
  
- <span data-ttu-id="04962-357">VNet 内の DNS サーバーを、オンプレミスの DNS サーバーに転送するように構成する</span><span class="sxs-lookup"><span data-stu-id="04962-357">The DNS servers in your VNet to forward to on-premises DNS servers</span></span>
    
- <span data-ttu-id="04962-358">オンプレミスおよび VNet の DNS サーバー間で適切なゾーンの DNS レプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="04962-358">DNS replication of the appropriate zones between DNS servers on-premises and in the VNet</span></span>
    
<span data-ttu-id="04962-359">**図 17: クロスプレミスの VNet 内 DNS サーバーの DNS のレプリケーションおよび転送**</span><span class="sxs-lookup"><span data-stu-id="04962-359">**Figure 17: DNS replication and forwarding for a DNS server in a cross-premises VNet**</span></span>

![図 17: クロスプレミスの Azure 仮想ネットワーク内 DNS サーバーに関する DNS のレプリケーションおよび転送](media/ab55e5ce-ccb0-49d4-a301-657a727f97b2.png)
  
<span data-ttu-id="04962-p115">図17 は、オンプレミス ネットワークと VNet のサブネットの、クロスプレミスの VNet と DNS サーバーを示しています。DNS レプリケーションと転送は、2 つの DNS サーバー間で構成されています。</span><span class="sxs-lookup"><span data-stu-id="04962-p115">Figure 17 shows a cross-premises VNet with DNS servers in the on-premises network and on a subnet in the VNet. DNS replication and forwarding has been configured between the two DNS servers.</span></span>
  
### <a name="step-7-determine-the-use-of-forced-tunneling"></a><span data-ttu-id="04962-363">手順 7:強制トンネリングの使用を決定する。</span><span class="sxs-lookup"><span data-stu-id="04962-363">Step 7: Determine the use of forced tunneling.</span></span>

<span data-ttu-id="04962-p116">Azure サブネットの既定のシステム ルートは、インターネットをポイントします。仮想マシンからのすべてのトラフィックがクロスプレミス接続全体を移動するようにするには、次ホップ アドレスとして Azure ゲートウェイを使用する既定のルートを指定したルーティング テーブルを作成します。次に、そのルート テーブルをサブネットに関連付けます。これを強制トンネリングといいます。詳細については、「[強制トンネリングの構成](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-p116">The default system route for Azure subnets points to the Internet. To ensure that all traffic from virtual machines travels across the cross-premises connection, create a routing table with the default route that uses the Azure gateway as its next-hop address. You then associate the route table with the subnet. This is known as forced tunneling. For more information, see [Configure forced tunneling](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-forced-tunneling-rm).</span></span>
  
<span data-ttu-id="04962-369">**図 18: ユーザー定義のルートおよびクロスプレミスの VNet の強制トンネリング**</span><span class="sxs-lookup"><span data-stu-id="04962-369">**Figure 18: User-defined routes and forced tunneling for a cross-premises VNet**</span></span>

![図 18:ユーザー定義のルートおよびクロスプレミスの Azure 仮想ネットワークの強制トンネリング](media/1e545ec6-c2d9-48d2-bb5e-e0a581fee004.png)
  
<span data-ttu-id="04962-371">図 18 は、クロスプレミスの VNet と、Azure ゲートウェイを指しているサブネットのユーザー定義のルートを示しています。</span><span class="sxs-lookup"><span data-stu-id="04962-371">Figure 18 shows a cross-premises VNet with a user-defined route for a subnet pointing to the Azure gateway.</span></span>
  
## <a name="sharepoint-server-2016-farm-in-azure"></a><span data-ttu-id="04962-372">Azure の SharePoint Server 2016 ファーム</span><span class="sxs-lookup"><span data-stu-id="04962-372">SharePoint Server 2016 farm in Azure</span></span>
<span data-ttu-id="04962-373"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="04962-373"><a name="cross_prem"> </a></span></span>

<span data-ttu-id="04962-374">Azure IaaS でホストされているイントラネット IT ワークロードの一例として、可用性の高い多層 SharePoint Server 2016 ファームがあります。</span><span class="sxs-lookup"><span data-stu-id="04962-374">An example of an intranet IT workload hosted in Azure IaaS is a highly-available, multi-tier SharePoint Server 2016 farm.</span></span>
  
<span data-ttu-id="04962-375">**図 19:Azure IaaS の高可用性イントラネット SharePoint Server 2016 ファーム**</span><span class="sxs-lookup"><span data-stu-id="04962-375">**Figure 19: A highly-available intranet SharePoint Server 2016 farm in Azure IaaS**</span></span>

![Azure IaaS の高可用性 SharePoint Server 2016 ファーム](media/3a922e21-df91-455f-ba90-78abdd48d98d.png)
  
<span data-ttu-id="04962-p117">図 19 は、フロントエンド層とデータ層に内部ロード バランサーを使用するクロスプレミス VNet で展開された SharePoint Server 2016 ファームの 9 台のサーバーを示しています。ステップ バイ ステップの設計と展開の手順を含む詳細については、「[Microsoft Azure での SharePoint Server 2016](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-p117">Figure 19 shows the nine servers of a SharePoint Server 2016 farm deployed in a cross-premises VNet that uses internal load balancers for the front-end and data tiers. For more information, including step-by-step design and deployment instructions, see [SharePoint Server 2016 in Microsoft Azure](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx).</span></span>
  
> [!TIP]
> <span data-ttu-id="04962-379">シミュレートされたクロスプレミス VNet で単一サーバーの SharePoint Server 2016 ファームを作成するには、「[Azure 開発/テスト環境でのイントラネット SharePoint Server 2016](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-379">To create a single-server SharePoint Server 2016 farm in a simulated cross-premises VNet, see [Intranet SharePoint Server 2016 in Azure dev/test environment](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx).</span></span> 
  
<span data-ttu-id="04962-380">クロスプレミスの Azure 仮想ネットワーク内の仮想マシンにデプロイされた IT ワークロードに関するその他の例については、「[Azure IaaS のハイブリッド クラウド シナリオ](https://technet.microsoft.com/library/mt750502.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04962-380">For additional examples of IT workloads deployed on virtual machines in a cross-premises Azure virtual network, see [Hybrid cloud scenarios for Azure IaaS](https://technet.microsoft.com/library/mt750502.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="04962-381">関連項目</span><span class="sxs-lookup"><span data-stu-id="04962-381">See also</span></span>

<span data-ttu-id="04962-382"><a name="cross_prem"> </a></span><span class="sxs-lookup"><span data-stu-id="04962-382"><a name="cross_prem"> </a></span></span>

[<span data-ttu-id="04962-383">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="04962-383">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="04962-384">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="04962-384">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="04962-385">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="04962-385">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



