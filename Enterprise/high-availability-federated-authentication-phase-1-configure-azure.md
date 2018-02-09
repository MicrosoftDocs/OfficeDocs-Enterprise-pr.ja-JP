---
title: "フェデレーション認証フェーズ 1 を構成する Azure を高可用性を実現"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: "概要: 高可用性をホストする Microsoft Azure インフラストラクチャを構成する Office 365 のフェデレーション認証します。"
ms.openlocfilehash: 829bad1dadc3c3987e42d32f8afe8c1f76459ff0
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="0d8c1-103">高可用性フェデレーション認証のフェーズ 1:Azure を構成する</span><span class="sxs-lookup"><span data-stu-id="0d8c1-103">High availability federated authentication Phase 1: Configure Azure</span></span>

 <span data-ttu-id="0d8c1-104">**の概要:**Office 365 のホストの高可用性の統合認証に Microsoft Azure インフラストラクチャを構成します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-104">**Summary:** Configure the Microsoft Azure infrastructure to host high availability federated authentication for Office 365.</span></span>
  
<span data-ttu-id="0d8c1-p101">このフェーズでは、リソース グループ、ストレージ アカウント、2、3、および 4 の段階で仮想マシンをホストする Azure 内の仮想ネットワーク (VNet)、および可用性を設定を作成します。上に移動する前に、このフェーズを完了する必要があります[高可用性の統合認証フェーズ 2: ドメイン コント ローラーを構成する](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)です。フェーズのすべては、 [Azure で Office 365 の展開の高可用性フェデレーション認証](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p101">In this phase, you create the resource groups, storage accounts, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4. You must complete this phase before moving on to [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="0d8c1-108">Azure は、これらの基本的なコンポーネントを準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-108">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="0d8c1-109">リソース グループ</span><span class="sxs-lookup"><span data-stu-id="0d8c1-109">Resource groups</span></span>
    
- <span data-ttu-id="0d8c1-110">Azure 仮想マシンをホストするためのサブネットを含むクロスプレミスの Azure 仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="0d8c1-110">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="0d8c1-111">サブネットの分離を実行するためのネットワーク セキュリティ グループ</span><span class="sxs-lookup"><span data-stu-id="0d8c1-111">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="0d8c1-112">可用性セット</span><span class="sxs-lookup"><span data-stu-id="0d8c1-112">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="0d8c1-113">Azure のコンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="0d8c1-113">Configure Azure components</span></span>

<span data-ttu-id="0d8c1-p102">Azure のコンポーネントの構成を開始する前に、次の表に入力します。Azure の構成の手順を支援する、このセクションを印刷する必要な情報をメモまたはこのセクションをドキュメントにコピーしで塗りつぶします。VNet の設定、テーブル V を入力します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p102">Before you begin configuring Azure components, fill in the following tables. To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in. For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="0d8c1-117">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-117">**Item**</span></span>|<span data-ttu-id="0d8c1-118">**構成の設定**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-118">**Configuration setting**</span></span>|<span data-ttu-id="0d8c1-119">**説明**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-119">**Description**</span></span>|<span data-ttu-id="0d8c1-120">**値**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-120">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="0d8c1-121">1.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-121">1.</span></span>  <br/> |<span data-ttu-id="0d8c1-122">VNet 名</span><span class="sxs-lookup"><span data-stu-id="0d8c1-122">VNet name</span></span>  <br/> |<span data-ttu-id="0d8c1-123">VNet に割り当てる名前 (例 FedAuthNet)。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-123">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |<span data-ttu-id="0d8c1-124">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-124"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-125">2.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-125">2.</span></span>  <br/> |<span data-ttu-id="0d8c1-126">VNet の場所</span><span class="sxs-lookup"><span data-stu-id="0d8c1-126">VNet location</span></span>  <br/> |<span data-ttu-id="0d8c1-127">仮想ネットワークが含まれる地域の Azure データセンター。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-127">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |<span data-ttu-id="0d8c1-128">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-128"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-129">3.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-129">3.</span></span>  <br/> |<span data-ttu-id="0d8c1-130">VPN デバイスの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0d8c1-130">VPN device IP address</span></span>  <br/> |<span data-ttu-id="0d8c1-131">インターネット上の VPN デバイスのインターフェイスのパブリック IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-131">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |<span data-ttu-id="0d8c1-132">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-132"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-133">4.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-133">4.</span></span>  <br/> |<span data-ttu-id="0d8c1-134">VNet アドレス空間</span><span class="sxs-lookup"><span data-stu-id="0d8c1-134">VNet address space</span></span>  <br/> |<span data-ttu-id="0d8c1-p103">仮想ネットワークのアドレス空間。このアドレス空間は、IT 部門と協議して決定してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |<span data-ttu-id="0d8c1-137">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-137"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-138">5.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-138">5.</span></span>  <br/> |<span data-ttu-id="0d8c1-139">IPsec 共有キー</span><span class="sxs-lookup"><span data-stu-id="0d8c1-139">IPsec shared key</span></span>  <br/> |<span data-ttu-id="0d8c1-p104">サイト間 VPN 接続の両方の側を認証するために使用される 32 文字のランダムな英数字文字列。It 機能またはこのキーの値を決定するセキュリティ部門。代わりに、 [IPsec の事前共有キーのランダムな文字列を作成する](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](http://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |<span data-ttu-id="0d8c1-143">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-143"></span></span>  <br/> |
   
 <span data-ttu-id="0d8c1-144">**表 V:クロスプレミスの仮想ネットワーク構成**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-144">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="0d8c1-p105">次に、このソリューションのサブネットついて、「表 S」に必要事項を記入します。すべてのアドレス空間は、クラスレス ドメイン間ルーティング (CIDR) 形式 (別称: ネットワーク プレフィックス形式) にする必要があります。たとえば、10.24.64.0/20 のようにします。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="0d8c1-p106">最初の 3 つのサブネットについて、仮想ネットワークのアドレス空間に基づいた名前と単一の IP アドレス空間を指定します。ゲートウェイ サブネットについて、次を実行して、Azure ゲートウェイ サブネットの 27 ビット アドレス空間 (プレフィックス長 /27) を決定します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="0d8c1-150">VNet アドレス空間の可変ビットを 1 に設定します (ゲートウェイ サブネットに使用しているビット数まで)。残りのビットは 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-150">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="0d8c1-151">その結果のビットを 10 進数に変換して、ゲートウェイ サブネットのサイズに設定されたプレフィックス長のアドレス空間として表現します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-151">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="0d8c1-152">PowerShell コマンドのブロックとするこの計算を実行するコンソール アプリケーションを C# または Python の[Azure ゲートウェイのサブネットのアドレス領域の計算](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-152">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="0d8c1-153">これに該当するアドレス空間については、仮想ネットワークのアドレス空間に基づいて、IT 部門と協議して決定してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-153">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="0d8c1-154">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-154">**Item**</span></span>|<span data-ttu-id="0d8c1-155">**サブネット名**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-155">**Subnet name**</span></span>|<span data-ttu-id="0d8c1-156">**サブネット アドレス スペース**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-156">**Subnet address space**</span></span>|<span data-ttu-id="0d8c1-157">**用途**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-157">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="0d8c1-158">1.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-158">1.</span></span>  <br/> |<span data-ttu-id="0d8c1-159">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-159"></span></span>  <br/> |<span data-ttu-id="0d8c1-160">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-160"></span></span>  <br/> |<span data-ttu-id="0d8c1-161">Windows Server Active Directory (AD) ドメイン コントローラーと DirSync サーバー仮想マシン (VM) が使用するサブネット。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-161">The subnet used by the Windows Server Active Directory (AD) domain controller and DirSync server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="0d8c1-162">2.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-162">2.</span></span>  <br/> |<span data-ttu-id="0d8c1-163">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-163"></span></span>  <br/> |<span data-ttu-id="0d8c1-164">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-164"></span></span>  <br/> |<span data-ttu-id="0d8c1-165">AD FS VM が使用するサブネット。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-165">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="0d8c1-166">3.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-166">3.</span></span>  <br/> |<span data-ttu-id="0d8c1-167">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-167"></span></span>  <br/> |<span data-ttu-id="0d8c1-168">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-168"></span></span>  <br/> |<span data-ttu-id="0d8c1-169">Web アプリケーション プロキシ VM が使用するサブネット。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-169">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="0d8c1-170">4.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-170">4.</span></span>  <br/> |<span data-ttu-id="0d8c1-171">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="0d8c1-171">GatewaySubnet</span></span>  <br/> |<span data-ttu-id="0d8c1-172">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-172"></span></span>  <br/> |<span data-ttu-id="0d8c1-173">Azure ゲートウェイ VM が使用するサブネット。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-173">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="0d8c1-174">**表 S:仮想ネットワーク内のサブネット**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-174">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="0d8c1-175">次に、仮想マシンとロード バランサーのインスタンスに割り当てる静的 IP について、「表 I」に必要事項を記入します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-175">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="0d8c1-176">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-176">**Item**</span></span>|<span data-ttu-id="0d8c1-177">**用途**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-177">**Purpose**</span></span>|<span data-ttu-id="0d8c1-178">**サブネット上の IP アドレス**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-178">**IP address on the subnet**</span></span>|<span data-ttu-id="0d8c1-179">**値**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-179">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="0d8c1-180">1.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-180">1.</span></span>  <br/> |<span data-ttu-id="0d8c1-181">最初のドメイン コントローラーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0d8c1-181">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="0d8c1-182">「表 S」の「項目 1」で定義されたサブネットのアドレス空間について、4 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-182">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="0d8c1-183">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-183"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-184">2.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-184">2.</span></span>  <br/> |<span data-ttu-id="0d8c1-185">2 番目のドメイン コントローラーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0d8c1-185">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="0d8c1-186">「表 S」の「項目 1」で定義されたサブネットのアドレス空間について、5 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-186">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="0d8c1-187">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-187"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-188">3.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-188">3.</span></span>  <br/> |<span data-ttu-id="0d8c1-189">DirSync サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0d8c1-189">Static IP address of the DirSync server</span></span>  <br/> |<span data-ttu-id="0d8c1-190">「表 S」の「項目 1」で定義されたサブネットのアドレス空間について、6 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-190">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |<span data-ttu-id="0d8c1-191">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-191"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-192">4.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-192">4.</span></span>  <br/> |<span data-ttu-id="0d8c1-193">AD FS サーバーの内部ロード バランサーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0d8c1-193">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="0d8c1-194">「表 S」の「項目 2」で定義されたサブネットのアドレス空間について、4 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-194">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="0d8c1-195">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-195"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-196">5.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-196">5.</span></span>  <br/> |<span data-ttu-id="0d8c1-197">最初の AD FS サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0d8c1-197">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="0d8c1-198">「表 S」の「項目 2」で定義されたサブネットのアドレス空間について、5 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-198">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="0d8c1-199">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-199"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-200">6.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-200">6.</span></span>  <br/> |<span data-ttu-id="0d8c1-201">2 番目の AD FS サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0d8c1-201">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="0d8c1-202">「表 S」の「項目 2」で定義されたサブネットのアドレス空間について、6 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-202">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |<span data-ttu-id="0d8c1-203">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-203"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-204">7.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-204">7.</span></span>  <br/> |<span data-ttu-id="0d8c1-205">最初の Web アプリケーション プロキシ サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0d8c1-205">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="0d8c1-206">「表 S」の「項目 3」で定義されたサブネットのアドレス空間について、4 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-206">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="0d8c1-207">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-207"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-208">8。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-208">8.</span></span>  <br/> |<span data-ttu-id="0d8c1-209">2 番目の Web アプリケーション プロキシ サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="0d8c1-209">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="0d8c1-210">「表 S」の「項目 3」で定義されたサブネットのアドレス空間について、5 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-210">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |<span data-ttu-id="0d8c1-211">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-211"></span></span>  <br/> |
   
 <span data-ttu-id="0d8c1-212">**仮想ネットワーク内の表 i: 静的 IP アドレス**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-212">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="0d8c1-213">仮想ネットワーク内のドメイン コントローラーを最初にセットアップするときに使用する、オンプレミス ネットワーク内の 2 つのドメイン ネーム システム (DNS) について、「表 D」に必要事項を記入します。IT 部門と協議して、このリストを決定してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-213">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="0d8c1-214">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-214">**Item**</span></span>|<span data-ttu-id="0d8c1-215">**DNS サーバーのフレンドリ名**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-215">**DNS server friendly name**</span></span>|<span data-ttu-id="0d8c1-216">**DNS サーバーの IP アドレス**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-216">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="0d8c1-217">1.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-217">1.</span></span>  <br/> |<span data-ttu-id="0d8c1-218">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-218"></span></span>  <br/> |<span data-ttu-id="0d8c1-219">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-219"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-220">2.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-220">2.</span></span>  <br/> |<span data-ttu-id="0d8c1-221">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-221"></span></span>  <br/> |<span data-ttu-id="0d8c1-222">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-222"></span></span>  <br/> |
   
 <span data-ttu-id="0d8c1-223">**表 D:オンプレミスの DNS サーバー**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-223">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="0d8c1-p107">クロスプレミス ネットワークからサイト間 VPN 接続を通過して組織ネットワークにパケットをルーティングするには、組織のオンプレミス ネットワーク上の到達可能なすべての場所についてのアドレス空間 (CIDR 表記) の一覧が含まれているローカル ネットワークで仮想ネットワークを構成する必要があります。このローカル ネットワークを定義するアドレス空間の一覧は、一意であることが必要であり、別の仮想ネットワークや別のローカル ネットワークとの重複がないことが必要になります。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p107">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that contains a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network. The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="0d8c1-p108">一連のローカル ネットワークのアドレス スペースに関しては表 L に記入します。3 つの空白のエントリが記載されていますが、通常はさらに必要となります。IT 部門に尋ねてこのアドレス スペースの一覧を特定してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="0d8c1-228">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-228">**Item**</span></span>|<span data-ttu-id="0d8c1-229">**ローカル ネットワークのアドレス スペース**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-229">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="0d8c1-230">1.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-230">1.</span></span>  <br/> |<span data-ttu-id="0d8c1-231">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-231"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-232">2.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-232">2.</span></span>  <br/> |<span data-ttu-id="0d8c1-233">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-233"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-234">3.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-234">3.</span></span>  <br/> |<span data-ttu-id="0d8c1-235">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-235"></span></span>  <br/> |
   
 <span data-ttu-id="0d8c1-236">**表 L:ローカル ネットワークのアドレス プレフィックス**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-236">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="0d8c1-237">ここからは、Office 365 のフェデレーション認証をホストするための Azure インフラストラクチャの構築を開始します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-237">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0d8c1-p109">次のコマンド セットは、Azure の PowerShell の最新バージョンを使用します。[Azure の PowerShell コマンドレットの入門](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="0d8c1-240">まず、Azure PowerShell プロンプトを起動して、自分のアカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-240">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="0d8c1-241">すべての PowerShell コマンドは、この資料で即座に実行の PowerShell コマンド ブロックが、カスタム設定に基づくを生成する Microsoft Excel の構成のブックに含まれているテキスト ファイルを参照してください[Office 365 のフェデレーション認証Azure 展開キット](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)です。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-241">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
<span data-ttu-id="0d8c1-242">次のコマンドを使用して、サブスクリプションの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-242">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="0d8c1-243">Azure PowerShell の以前のバージョンの代わりにこのコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-243">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="0d8c1-p110">Azure サブスクリプションを設定します。など、二重引用符内のすべてを交換して、\<と > 正しい名前の文字です。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p110">Set your Azure subscription. Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="0d8c1-p111">次に、新しいリソース グループを作成します。リソース グループ名の一意のセットを決定するために、このコマンドを使用して、既存のリソース グループを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="0d8c1-248">一意のリソース グループ名のセットについて、次に示す表に必要事項を記入します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-248">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="0d8c1-249">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-249">**Item**</span></span>|<span data-ttu-id="0d8c1-250">**リソース グループ名**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-250">**Resource group name**</span></span>|<span data-ttu-id="0d8c1-251">**用途**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-251">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="0d8c1-252">1.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-252">1.</span></span>  <br/> |<span data-ttu-id="0d8c1-253">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-253"></span></span>  <br/> |<span data-ttu-id="0d8c1-254">ドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="0d8c1-254">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="0d8c1-255">2.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-255">2.</span></span>  <br/> |<span data-ttu-id="0d8c1-256">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-256"></span></span>  <br/> |<span data-ttu-id="0d8c1-257">AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="0d8c1-257">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="0d8c1-258">3.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-258">3.</span></span>  <br/> |<span data-ttu-id="0d8c1-259">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-259"></span></span>  <br/> |<span data-ttu-id="0d8c1-260">Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="0d8c1-260">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="0d8c1-261">4.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-261">4.</span></span>  <br/> |<span data-ttu-id="0d8c1-262">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-262"></span></span>  <br/> |<span data-ttu-id="0d8c1-263">インフラストラクチャの要素</span><span class="sxs-lookup"><span data-stu-id="0d8c1-263">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="0d8c1-264">**テーブル r: リソース グループ**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-264">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="0d8c1-265">次に示すコマンドで、新しいリソース グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-265">Create your new resource groups with these commands.</span></span>
  
```
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="0d8c1-266">次に、Azure 仮想ネットワークとそのサブネットを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-266">Next, you create the Azure virtual network and its subnets.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzureRmResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzureRMVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="0d8c1-p112">次に、ネットワークを作成するセキュリティ グループを各サブネットに仮想マシンが含まれています。サブネットの分離を実行するのには、トラフィックを許可または拒否するサブネットのネットワークのセキュリティ グループの特定の種類の規則を追加できます。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p112">Next, you create network security groups for each subnet that contains virtual machines. To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```
# Create network security groups
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzureRMNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
```

<span data-ttu-id="0d8c1-269">次に、これらのコマンドを使用して、サイト間 VPN 接続のゲートウェイを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-269">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzureRMPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzureRMVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzureRMVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzureRMLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzureRMVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="0d8c1-p113">個々 のユーザーのフェデレーション認証は、社内設置型のリソースには依存しません。ただし、このサイト間 VPN 接続が利用できなくなった場合、VNet のドメイン コント ローラーではこのユーザー アカウントとグループの設置型の Windows Server AD に加えられた更新プログラムが受信しません。そうでないことを確認するには、サイト間 VPN 接続の高可用性を構成できます。詳細については、[高度利用可能な間、設置型および VNet-VNet への接続](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p113">Federated authentication of individual users does not rely on any on-premises resources. However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your site-to-site VPN connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="0d8c1-274">次に、このコマンドの表示から得られる、仮想ネットワーク用の Azure VPN ゲートウェイのパブリック IPv4 アドレスを記録します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-274">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```
Get-AzureRMPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="0d8c1-p114">次に、Azure の VPN ゲートウェイに接続するのには、設置型の VPN デバイスを構成します。詳細については、 [VPN デバイスの構成](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="0d8c1-277">オンプレミス VPN デバイスを構成するには、次のものが必要になります。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-277">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="0d8c1-278">Azure VPN ゲートウェイのパブリック IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-278">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="0d8c1-279">サイト間 VPN 接続 (テーブル V 項目 5: [値] 列) の IPsec 事前共有キーです。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-279">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="0d8c1-p115">次に、仮想ネットワークのアドレス空間がオンプレミスのネットワークからアクセスできることを確認します。一般に、これは、仮想ネットワークのアドレス空間から VPN デバイスに対応するルートを追加してから、そのルートを組織ネットワークの残りのルーティング インフラストラクチャに公示することで実行します。IT 部門と協議して、この方法について決定してください。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="0d8c1-p116">次に、3 つの可用性セットの名前を定義します。「表 A」に必要事項を記入します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="0d8c1-285">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-285">**Item**</span></span>|<span data-ttu-id="0d8c1-286">**用途**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-286">**Purpose**</span></span>|<span data-ttu-id="0d8c1-287">**可用性の名前を設定します。**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-287">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="0d8c1-288">1.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-288">1.</span></span>  <br/> |<span data-ttu-id="0d8c1-289">ドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="0d8c1-289">Domain controllers</span></span>  <br/> |<span data-ttu-id="0d8c1-290">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-290"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-291">2.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-291">2.</span></span>  <br/> |<span data-ttu-id="0d8c1-292">AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="0d8c1-292">AD FS servers</span></span>  <br/> |<span data-ttu-id="0d8c1-293">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-293"></span></span>  <br/> |
|<span data-ttu-id="0d8c1-294">3.</span><span class="sxs-lookup"><span data-stu-id="0d8c1-294">3.</span></span>  <br/> |<span data-ttu-id="0d8c1-295">Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="0d8c1-295">Web application proxy servers</span></span>  <br/> |<span data-ttu-id="0d8c1-296">_______________________________</span><span class="sxs-lookup"><span data-stu-id="0d8c1-296"></span></span>  <br/> |
   
 <span data-ttu-id="0d8c1-297">**表 a: 可用性を設定します。**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-297">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="0d8c1-298">これらの名前は、フェーズ 2、3、および 4 で仮想マシンを作成する際に必要になります。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-298">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="0d8c1-299">次に示す Azure PowerShell コマンドで、新しい可用性セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-299">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName -Location $locName
```

<span data-ttu-id="0d8c1-300">次に、このフェーズが正常に完了した結果の構成を示します。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-300">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="0d8c1-301">**フェーズ 1: Office 365 のフェデレーション認証を高可用性を実現するための Azure インフラストラクチャ**</span><span class="sxs-lookup"><span data-stu-id="0d8c1-301">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Azure インフラストラクチャによる Azure での高可用性 Office 365 フェデレーション認証のフェーズ 1](images/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="0d8c1-303">次の手順</span><span class="sxs-lookup"><span data-stu-id="0d8c1-303">Next step</span></span>

<span data-ttu-id="0d8c1-304">使用[高可用性の統合認証フェーズ 2: ドメイン コント ローラーを構成する](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)、この作業負荷の構成を続行するのには。</span><span class="sxs-lookup"><span data-stu-id="0d8c1-304">Use [High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0d8c1-305">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d8c1-305">See Also</span></span>

[<span data-ttu-id="0d8c1-306">Azure に Office 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="0d8c1-306">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="0d8c1-307">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="0d8c1-307">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="0d8c1-308">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="0d8c1-308">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="0d8c1-309">Office 365 のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="0d8c1-309">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


