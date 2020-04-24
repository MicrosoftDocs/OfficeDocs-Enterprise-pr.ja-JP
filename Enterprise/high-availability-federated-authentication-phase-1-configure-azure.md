---
title: 高可用性フェデレーション認証のフェーズ 1 Azure を構成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 概要:Office 365 の高可用性フェデレーション認証をホストするように Microsoft Azure インフラストラクチャを構成します。
ms.openlocfilehash: 9f2991ef495093f2aed01e57f47dab3371b97de3
ms.sourcegitcommit: a578baeb0d8b85941c13afa268447d2592f89fae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "43793830"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a><span data-ttu-id="d375a-103">高可用性フェデレーション認証のフェーズ 1: Azure を構成する</span><span class="sxs-lookup"><span data-stu-id="d375a-103">High availability federated authentication Phase 1: Configure Azure</span></span>

<span data-ttu-id="d375a-104">このフェーズでは、フェーズ2、3、4で仮想マシンをホストする Azure で、リソースグループ、仮想ネットワーク (VNet)、および可用性セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="d375a-104">In this phase, you create the resource groups, virtual network (VNet), and availability sets in Azure that will host the virtual machines in phases 2, 3, and 4.</span></span> <span data-ttu-id="d375a-105">このフェーズは、「[Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)」に進む前に完了しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d375a-105">You must complete this phase before moving on to [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="d375a-106">すべてのフェーズについては、「[Azure に Office 365 の高可用性フェデレーション認証を展開する](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-106">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
<span data-ttu-id="d375a-107">Azure は、次の基本コンポーネントを使用してプロビジョニングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d375a-107">Azure must be provisioned with these basic components:</span></span>
  
- <span data-ttu-id="d375a-108">リソース グループ</span><span class="sxs-lookup"><span data-stu-id="d375a-108">Resource groups</span></span>
    
- <span data-ttu-id="d375a-109">Azure 仮想マシンをホストするためのサブネットを含むクロスプレミスの Azure 仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="d375a-109">A cross-premises Azure virtual network (VNet) with subnets for hosting the Azure virtual machines</span></span>
    
- <span data-ttu-id="d375a-110">サブネットの分離を実行するためのネットワーク セキュリティ グループ</span><span class="sxs-lookup"><span data-stu-id="d375a-110">Network security groups for performing subnet isolation</span></span>
    
- <span data-ttu-id="d375a-111">可用性セット</span><span class="sxs-lookup"><span data-stu-id="d375a-111">Availability sets</span></span>
    
## <a name="configure-azure-components"></a><span data-ttu-id="d375a-112">Azure のコンポーネントの構成</span><span class="sxs-lookup"><span data-stu-id="d375a-112">Configure Azure components</span></span>

<span data-ttu-id="d375a-113">Azure のコンポーネントの構成を開始する前に、次に示す表に必要事項を記入します。</span><span class="sxs-lookup"><span data-stu-id="d375a-113">Before you begin configuring Azure components, fill in the following tables.</span></span> <span data-ttu-id="d375a-114">Azure の構成の手順で役立つように、このセクションを印刷して、必要な情報を書き込むか、このセクションをドキュメントにコピーして必要事項を記入してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-114">To assist you in the procedures for configuring Azure, print this section and write down the needed information or copy this section to a document and fill it in.</span></span> <span data-ttu-id="d375a-115">VNet の設定は、「表 V」に記入します。</span><span class="sxs-lookup"><span data-stu-id="d375a-115">For the settings of the VNet, fill in Table V.</span></span>
  
|<span data-ttu-id="d375a-116">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="d375a-116">**Item**</span></span>|<span data-ttu-id="d375a-117">**構成設定**</span><span class="sxs-lookup"><span data-stu-id="d375a-117">**Configuration setting**</span></span>|<span data-ttu-id="d375a-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="d375a-118">**Description**</span></span>|<span data-ttu-id="d375a-119">**値**</span><span class="sxs-lookup"><span data-stu-id="d375a-119">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d375a-120">1.</span><span class="sxs-lookup"><span data-stu-id="d375a-120">1.</span></span>  <br/> |<span data-ttu-id="d375a-121">VNet 名</span><span class="sxs-lookup"><span data-stu-id="d375a-121">VNet name</span></span>  <br/> |<span data-ttu-id="d375a-122">VNet に割り当てる名前 (例 FedAuthNet)。</span><span class="sxs-lookup"><span data-stu-id="d375a-122">A name to assign to the VNet (example FedAuthNet).</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-124">2.</span><span class="sxs-lookup"><span data-stu-id="d375a-124">2.</span></span>  <br/> |<span data-ttu-id="d375a-125">VNet の場所</span><span class="sxs-lookup"><span data-stu-id="d375a-125">VNet location</span></span>  <br/> |<span data-ttu-id="d375a-126">仮想ネットワークが含まれる地域の Azure データセンター。</span><span class="sxs-lookup"><span data-stu-id="d375a-126">The regional Azure datacenter that will contain the virtual network.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-128">3.</span><span class="sxs-lookup"><span data-stu-id="d375a-128">3.</span></span>  <br/> |<span data-ttu-id="d375a-129">VPN デバイスの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="d375a-129">VPN device IP address</span></span>  <br/> |<span data-ttu-id="d375a-130">インターネット上の VPN デバイスのインターフェイスのパブリック IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-130">The public IPv4 address of your VPN device's interface on the Internet.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-132">4.</span><span class="sxs-lookup"><span data-stu-id="d375a-132">4.</span></span>  <br/> |<span data-ttu-id="d375a-133">VNet アドレス空間</span><span class="sxs-lookup"><span data-stu-id="d375a-133">VNet address space</span></span>  <br/> |<span data-ttu-id="d375a-p103">仮想ネットワークのアドレス空間。このアドレス空間は、IT 部門と協議して決定してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-p103">The address space for the virtual network. Work with your IT department to determine this address space.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-137">5.</span><span class="sxs-lookup"><span data-stu-id="d375a-137">5.</span></span>  <br/> |<span data-ttu-id="d375a-138">IPsec 共有キー</span><span class="sxs-lookup"><span data-stu-id="d375a-138">IPsec shared key</span></span>  <br/> |<span data-ttu-id="d375a-p104">32 文字のランダムな英数字文字列。サイト間 VPN 接続の両側を認証するために使用されます。このキーの値は、IT 部門またはセキュリティ部門と協議して決定してください。または、「[IPsec 事前共有キーのランダム文字列を作成する](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx)」を参照してください。  </span><span class="sxs-lookup"><span data-stu-id="d375a-p104">A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value. Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  </span></span><br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d375a-143">**表 V:クロスプレミスの仮想ネットワーク構成**</span><span class="sxs-lookup"><span data-stu-id="d375a-143">**Table V: Cross-premises virtual network configuration**</span></span>
  
<span data-ttu-id="d375a-p105">次に、このソリューションのサブネットついて、「表 S」に必要事項を記入します。すべてのアドレス空間は、クラスレス ドメイン間ルーティング (CIDR) 形式 (別称: ネットワーク プレフィックス形式) にする必要があります。たとえば、10.24.64.0/20 のようにします。</span><span class="sxs-lookup"><span data-stu-id="d375a-p105">Next, fill in Table S for the subnets of this solution. All address spaces should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.</span></span>
  
<span data-ttu-id="d375a-p106">最初の 3 つのサブネットについて、仮想ネットワークのアドレス空間に基づいた名前と単一の IP アドレス空間を指定します。ゲートウェイ サブネットについて、次を実行して、Azure ゲートウェイ サブネットの 27 ビット アドレス空間 (プレフィックス長 /27) を決定します。</span><span class="sxs-lookup"><span data-stu-id="d375a-p106">For the first three subnets, specify a name and a single IP address space based on the virtual network address space. For the gateway subnet, determine the 27-bit address space (with a /27 prefix length) for the Azure gateway subnet with the following:</span></span>
  
1. <span data-ttu-id="d375a-149">VNet アドレス空間の可変ビットを 1 に設定します (ゲートウェイ サブネットに使用しているビット数まで)。残りのビットは 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d375a-149">Set the variable bits in the address space of the VNet to 1, up to the bits being used by the gateway subnet, then set the remaining bits to 0.</span></span>
    
2. <span data-ttu-id="d375a-150">その結果のビットを 10 進数に変換して、ゲートウェイ サブネットのサイズに設定されたプレフィックス長のアドレス空間として表現します。</span><span class="sxs-lookup"><span data-stu-id="d375a-150">Convert the resulting bits to decimal and express it as an address space with the prefix length set to the size of the gateway subnet.</span></span>
    
<span data-ttu-id="d375a-151">この計算を実行する PowerShell コマンドブロックおよび C# または Python コンソールアプリケーションについては、「 [Azure gateway のサブネットのアドレス空間計算ツール](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-151">See [Address space calculator for Azure gateway subnets](https://gallery.technet.microsoft.com/scriptcenter/Address-prefix-calculator-a94b6eed) for a PowerShell command block and C# or Python console application that performs this calculation for you.</span></span>
  
<span data-ttu-id="d375a-152">これに該当するアドレス空間については、仮想ネットワークのアドレス空間に基づいて、IT 部門と協議して決定してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-152">Work with your IT department to determine these address spaces from the virtual network address space.</span></span>
  
|<span data-ttu-id="d375a-153">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="d375a-153">**Item**</span></span>|<span data-ttu-id="d375a-154">**サブネット名**</span><span class="sxs-lookup"><span data-stu-id="d375a-154">**Subnet name**</span></span>|<span data-ttu-id="d375a-155">**サブネット アドレス スペース**</span><span class="sxs-lookup"><span data-stu-id="d375a-155">**Subnet address space**</span></span>|<span data-ttu-id="d375a-156">**用途**</span><span class="sxs-lookup"><span data-stu-id="d375a-156">**Purpose**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d375a-157">1.</span><span class="sxs-lookup"><span data-stu-id="d375a-157">1.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="d375a-160">Active Directory ドメインサービス (AD DS) ドメインコントローラーとディレクトリ同期サーバー仮想マシン (Vm) によって使用されるサブネット。</span><span class="sxs-lookup"><span data-stu-id="d375a-160">The subnet used by the Active Directory Domain Services (AD DS) domain controller and directory synchronization server virtual machines (VMs).</span></span>  <br/> |
|<span data-ttu-id="d375a-161">2.</span><span class="sxs-lookup"><span data-stu-id="d375a-161">2.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="d375a-164">AD FS VM が使用するサブネット。</span><span class="sxs-lookup"><span data-stu-id="d375a-164">The subnet used by the AD FS VMs.</span></span>  <br/> |
|<span data-ttu-id="d375a-165">3.</span><span class="sxs-lookup"><span data-stu-id="d375a-165">3.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="d375a-168">Web アプリケーション プロキシ VM が使用するサブネット。</span><span class="sxs-lookup"><span data-stu-id="d375a-168">The subnet used by the web application proxy VMs.</span></span>  <br/> |
|<span data-ttu-id="d375a-169">4.</span><span class="sxs-lookup"><span data-stu-id="d375a-169">4.</span></span>  <br/> |<span data-ttu-id="d375a-170">GatewaySubnet</span><span class="sxs-lookup"><span data-stu-id="d375a-170">GatewaySubnet</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="d375a-172">Azure ゲートウェイ VM が使用するサブネット。</span><span class="sxs-lookup"><span data-stu-id="d375a-172">The subnet used by the Azure gateway VMs.</span></span>  <br/> |
   
 <span data-ttu-id="d375a-173">**表 S:仮想ネットワーク内のサブネット**</span><span class="sxs-lookup"><span data-stu-id="d375a-173">**Table S: Subnets in the virtual network**</span></span>
  
<span data-ttu-id="d375a-174">次に、仮想マシンとロード バランサーのインスタンスに割り当てる静的 IP について、「表 I」に必要事項を記入します。</span><span class="sxs-lookup"><span data-stu-id="d375a-174">Next, fill in Table I for the static IP addresses assigned to virtual machines and load balancer instances.</span></span>
  
|<span data-ttu-id="d375a-175">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="d375a-175">**Item**</span></span>|<span data-ttu-id="d375a-176">**用途**</span><span class="sxs-lookup"><span data-stu-id="d375a-176">**Purpose**</span></span>|<span data-ttu-id="d375a-177">**サブネット上の IP アドレス**</span><span class="sxs-lookup"><span data-stu-id="d375a-177">**IP address on the subnet**</span></span>|<span data-ttu-id="d375a-178">**値**</span><span class="sxs-lookup"><span data-stu-id="d375a-178">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="d375a-179">1.</span><span class="sxs-lookup"><span data-stu-id="d375a-179">1.</span></span>  <br/> |<span data-ttu-id="d375a-180">最初のドメイン コントローラーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="d375a-180">Static IP address of the first domain controller</span></span>  <br/> |<span data-ttu-id="d375a-181">「表 S」の「項目 1」で定義されたサブネットのアドレス空間について、4 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-181">The fourth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-183">2.</span><span class="sxs-lookup"><span data-stu-id="d375a-183">2.</span></span>  <br/> |<span data-ttu-id="d375a-184">2 番目のドメイン コントローラーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="d375a-184">Static IP address of the second domain controller</span></span>  <br/> |<span data-ttu-id="d375a-185">「表 S」の「項目 1」で定義されたサブネットのアドレス空間について、5 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-185">The fifth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-187">3.</span><span class="sxs-lookup"><span data-stu-id="d375a-187">3.</span></span>  <br/> |<span data-ttu-id="d375a-188">ディレクトリ同期サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="d375a-188">Static IP address of the directory synchronization server</span></span>  <br/> |<span data-ttu-id="d375a-189">「表 S」の「項目 1」で定義されたサブネットのアドレス空間について、6 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-189">The sixth possible IP address for the address space of the subnet defined in Item 1 of Table S.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-191">4.</span><span class="sxs-lookup"><span data-stu-id="d375a-191">4.</span></span>  <br/> |<span data-ttu-id="d375a-192">AD FS サーバーの内部ロード バランサーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="d375a-192">Static IP address of the internal load balancer for the AD FS servers</span></span>  <br/> |<span data-ttu-id="d375a-193">「表 S」の「項目 2」で定義されたサブネットのアドレス空間について、4 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-193">The fourth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-195">5.</span><span class="sxs-lookup"><span data-stu-id="d375a-195">5.</span></span>  <br/> |<span data-ttu-id="d375a-196">最初の AD FS サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="d375a-196">Static IP address of the first AD FS server</span></span>  <br/> |<span data-ttu-id="d375a-197">「表 S」の「項目 2」で定義されたサブネットのアドレス空間について、5 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-197">The fifth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-199">6.</span><span class="sxs-lookup"><span data-stu-id="d375a-199">6.</span></span>  <br/> |<span data-ttu-id="d375a-200">2 番目の AD FS サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="d375a-200">Static IP address of the second AD FS server</span></span>  <br/> |<span data-ttu-id="d375a-201">「表 S」の「項目 2」で定義されたサブネットのアドレス空間について、6 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-201">The sixth possible IP address for the address space of the subnet defined in Item 2 of Table S.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-203">7.</span><span class="sxs-lookup"><span data-stu-id="d375a-203">7.</span></span>  <br/> |<span data-ttu-id="d375a-204">最初の Web アプリケーション プロキシ サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="d375a-204">Static IP address of the first web application proxy server</span></span>  <br/> |<span data-ttu-id="d375a-205">「表 S」の「項目 3」で定義されたサブネットのアドレス空間について、4 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-205">The fourth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-207">8.</span><span class="sxs-lookup"><span data-stu-id="d375a-207">8.</span></span>  <br/> |<span data-ttu-id="d375a-208">2 番目の Web アプリケーション プロキシ サーバーの静的 IP アドレス</span><span class="sxs-lookup"><span data-stu-id="d375a-208">Static IP address of the second web application proxy server</span></span>  <br/> |<span data-ttu-id="d375a-209">「表 S」の「項目 3」で定義されたサブネットのアドレス空間について、5 番目に考えられる IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-209">The fifth possible IP address for the address space of the subnet defined in Item 3 of Table S.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d375a-211">**表 I: 仮想ネットワークの静的 IP アドレス**</span><span class="sxs-lookup"><span data-stu-id="d375a-211">**Table I: Static IP addresses in the virtual network**</span></span>
  
<span data-ttu-id="d375a-212">仮想ネットワーク内のドメイン コントローラーを最初にセットアップするときに使用する、オンプレミス ネットワーク内の 2 つのドメイン ネーム システム (DNS) について、「表 D」に必要事項を記入します。IT 部門と協議して、このリストを決定してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-212">For two Domain Name System (DNS) servers in your on-premises network that you want to use when initially setting up the domain controllers in your virtual network, fill in Table D. Work with your IT department to determine this list.</span></span>
  
|<span data-ttu-id="d375a-213">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="d375a-213">**Item**</span></span>|<span data-ttu-id="d375a-214">**DNS サーバーのフレンドリ名**</span><span class="sxs-lookup"><span data-stu-id="d375a-214">**DNS server friendly name**</span></span>|<span data-ttu-id="d375a-215">**DNS サーバーの IP アドレス**</span><span class="sxs-lookup"><span data-stu-id="d375a-215">**DNS server IP address**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d375a-216">1.</span><span class="sxs-lookup"><span data-stu-id="d375a-216">1.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-219">2.</span><span class="sxs-lookup"><span data-stu-id="d375a-219">2.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d375a-222">**表 D:オンプレミスの DNS サーバー**</span><span class="sxs-lookup"><span data-stu-id="d375a-222">**Table D: On-premises DNS servers**</span></span>
  
<span data-ttu-id="d375a-223">クロスプレミスネットワークから組織のネットワークへのパケットをサイト間 VPN 接続を介してルーティングするには、組織のオンプレミスネットワーク上のすべての到達可能な場所に対するアドレススペース (CIDR 表記) のリストを持つローカルネットワークを使用して仮想ネットワークを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d375a-223">To route packets from the cross-premises network to your organization network across the site-to-site VPN connection, you must configure the virtual network with a local network that has a list of the address spaces (in CIDR notation) for all of the reachable locations on your organization's on-premises network.</span></span> <span data-ttu-id="d375a-224">このローカル ネットワークを定義するアドレス空間の一覧は、一意であることが必要であり、別の仮想ネットワークや別のローカル ネットワークとの重複がないことが必要になります。</span><span class="sxs-lookup"><span data-stu-id="d375a-224">The list of address spaces that define your local network must be unique and must not overlap with the address space used for other virtual networks or other local networks.</span></span>
  
<span data-ttu-id="d375a-p108">一連のローカル ネットワークのアドレス スペースに関しては表 L に記入します。3 つの空白のエントリが記載されていますが、通常はさらに必要となります。IT 部門に尋ねてこのアドレス スペースの一覧を特定してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-p108">For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list of address spaces.</span></span>
  
|<span data-ttu-id="d375a-227">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="d375a-227">**Item**</span></span>|<span data-ttu-id="d375a-228">**ローカル ネットワークのアドレス スペース**</span><span class="sxs-lookup"><span data-stu-id="d375a-228">**Local network address space**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d375a-229">1.</span><span class="sxs-lookup"><span data-stu-id="d375a-229">1.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-231">2.</span><span class="sxs-lookup"><span data-stu-id="d375a-231">2.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-233">3.</span><span class="sxs-lookup"><span data-stu-id="d375a-233">3.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d375a-235">**表 L:ローカル ネットワークのアドレス プレフィックス**</span><span class="sxs-lookup"><span data-stu-id="d375a-235">**Table L: Address prefixes for the local network**</span></span>
  
<span data-ttu-id="d375a-236">ここからは、Office 365 のフェデレーション認証をホストするための Azure インフラストラクチャの構築を開始します。</span><span class="sxs-lookup"><span data-stu-id="d375a-236">Now let's begin building the Azure infrastructure to host your federated authentication for Office 365.</span></span>
  
> [!NOTE]
> <span data-ttu-id="d375a-237">次のコマンド セットは、Azure PowerShell の最新版を使用します。</span><span class="sxs-lookup"><span data-stu-id="d375a-237">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="d375a-238">「 [Azure PowerShell の概要」を](https://docs.microsoft.com/powershell/azure/get-started-azureps)参照してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-238">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="d375a-239">まず、Azure PowerShell プロンプトを起動して、自分のアカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="d375a-239">First, start an Azure PowerShell prompt and login to your account.</span></span>
  
```powershell
Connect-AzAccount
```

> [!TIP]
> <span data-ttu-id="d375a-240">カスタム設定に基づいて、すぐに実行できる PowerShell コマンドブロックを生成するには、この[Microsoft Excel 構成ブック](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx)を使用します。</span><span class="sxs-lookup"><span data-stu-id="d375a-240">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

<span data-ttu-id="d375a-241">次のコマンドを使用して、サブスクリプションの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="d375a-241">Get your subscription name using the following command.</span></span>
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="d375a-242">以前のバージョンの Azure PowerShell では、代わりにこのコマンドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-242">For older versions of Azure PowerShell, use this command instead.</span></span>
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

<span data-ttu-id="d375a-243">Azure サブスクリプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="d375a-243">Set your Azure subscription.</span></span> <span data-ttu-id="d375a-244">引用符で囲まれたすべてのもの\< (および > 文字を含む) を正しい名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d375a-244">Replace everything within the quotes, including the \< and > characters, with the correct name.</span></span>
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="d375a-p111">次に、新しいリソース グループを作成します。リソース グループ名の一意のセットを決定するために、このコマンドを使用して、既存のリソース グループを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d375a-p111">Next, create the new resource groups. To determine a unique set of resource group names, use this command to list your existing resource groups.</span></span>
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="d375a-247">一意のリソース グループ名のセットについて、次に示す表に必要事項を記入します。</span><span class="sxs-lookup"><span data-stu-id="d375a-247">Fill in the following table for the set of unique resource group names.</span></span>
  
|<span data-ttu-id="d375a-248">**項目**</span><span class="sxs-lookup"><span data-stu-id="d375a-248">**Item**</span></span>|<span data-ttu-id="d375a-249">**リソース グループ名**</span><span class="sxs-lookup"><span data-stu-id="d375a-249">**Resource group name**</span></span>|<span data-ttu-id="d375a-250">**用途**</span><span class="sxs-lookup"><span data-stu-id="d375a-250">**Purpose**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d375a-251">1.</span><span class="sxs-lookup"><span data-stu-id="d375a-251">1.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="d375a-253">ドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="d375a-253">Domain controllers</span></span>  <br/> |
|<span data-ttu-id="d375a-254">2.</span><span class="sxs-lookup"><span data-stu-id="d375a-254">2.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="d375a-256">AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="d375a-256">AD FS servers</span></span>  <br/> |
|<span data-ttu-id="d375a-257">3.</span><span class="sxs-lookup"><span data-stu-id="d375a-257">3.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="d375a-259">Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="d375a-259">Web application proxy servers</span></span>  <br/> |
|<span data-ttu-id="d375a-260">4.</span><span class="sxs-lookup"><span data-stu-id="d375a-260">4.</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |<span data-ttu-id="d375a-262">インフラストラクチャの要素</span><span class="sxs-lookup"><span data-stu-id="d375a-262">Infrastructure elements</span></span>  <br/> |
   
 <span data-ttu-id="d375a-263">**表 R: リソース グループ**</span><span class="sxs-lookup"><span data-stu-id="d375a-263">**Table R: Resource groups**</span></span>
  
<span data-ttu-id="d375a-264">次に示すコマンドで、新しいリソース グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="d375a-264">Create your new resource groups with these commands.</span></span>
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="d375a-265">次に、Azure 仮想ネットワークとそのサブネットを作成します。</span><span class="sxs-lookup"><span data-stu-id="d375a-265">Next, you create the Azure virtual network and its subnets.</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

<span data-ttu-id="d375a-266">次に、仮想マシンを持つ各サブネットのネットワークセキュリティグループを作成します。</span><span class="sxs-lookup"><span data-stu-id="d375a-266">Next, you create network security groups for each subnet that has virtual machines.</span></span> <span data-ttu-id="d375a-267">サブネットを分離するには、サブネットのネットワーク セキュリティ グループでの特定の種類のトラフィックを許可または拒否する規則を追加できます。</span><span class="sxs-lookup"><span data-stu-id="d375a-267">To perform subnet isolation, you can add rules for the specific types of traffic allowed or denied to the network security group of a subnet.</span></span>
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="d375a-268">次に、これらのコマンドを使用して、サイト間 VPN 接続のゲートウェイを作成します。</span><span class="sxs-lookup"><span data-stu-id="d375a-268">Next, use these commands to create the gateways for the site-to-site VPN connection.</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> <span data-ttu-id="d375a-269">個々のユーザーのフェデレーション認証は、オンプレミスのリソースには依存しません。</span><span class="sxs-lookup"><span data-stu-id="d375a-269">Federated authentication of individual users does not rely on any on-premises resources.</span></span> <span data-ttu-id="d375a-270">ただし、このサイト間 VPN 接続が使用できなくなった場合、VNet 内のドメインコントローラーは、オンプレミスの Active Directory ドメインサービスで行われたユーザーアカウントとグループの更新を受信しません。</span><span class="sxs-lookup"><span data-stu-id="d375a-270">However, if this site-to-site VPN connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services.</span></span> <span data-ttu-id="d375a-271">これが行われないようにするには、サイト間 VPN 接続の高可用性を構成します。</span><span class="sxs-lookup"><span data-stu-id="d375a-271">To ensure this does not happen, you can configure high availability for your site-to-site VPN connection.</span></span> <span data-ttu-id="d375a-272">詳細については、「[高可用性のクロスプレミス接続および VNet 間接続](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-272">For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="d375a-273">次に、このコマンドの表示から得られる、仮想ネットワーク用の Azure VPN ゲートウェイのパブリック IPv4 アドレスを記録します。</span><span class="sxs-lookup"><span data-stu-id="d375a-273">Next, record the public IPv4 address of the Azure VPN gateway for your virtual network from the display of this command:</span></span>
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

<span data-ttu-id="d375a-p114">次に、Azure VPN ゲートウェイに接続するようにオンプレミスの VPN デバイスを構成します。詳細については、「[サイト間 VPN Gateway 接続の VPN デバイスについて](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-p114">Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [Configure your VPN device](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpn-devices).</span></span>
  
<span data-ttu-id="d375a-276">オンプレミス VPN デバイスを構成するには、次のものが必要になります。</span><span class="sxs-lookup"><span data-stu-id="d375a-276">To configure your on-premises VPN device, you will need the following:</span></span>
  
- <span data-ttu-id="d375a-277">Azure VPN ゲートウェイのパブリック IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="d375a-277">The public IPv4 address of the Azure VPN gateway.</span></span>
    
- <span data-ttu-id="d375a-278">サイト間 VPN 接続の IPsec 事前共有キー (「表 V」-「項目 5」-「値」列)。</span><span class="sxs-lookup"><span data-stu-id="d375a-278">The IPsec pre-shared key for the site-to-site VPN connection (Table V - Item 5 - Value column).</span></span>
    
<span data-ttu-id="d375a-p115">次に、仮想ネットワークのアドレス空間がオンプレミスのネットワークからアクセスできることを確認します。一般に、これは、仮想ネットワークのアドレス空間から VPN デバイスに対応するルートを追加してから、そのルートを組織ネットワークの残りのルーティング インフラストラクチャに公示することで実行します。IT 部門と協議して、この方法について決定してください。</span><span class="sxs-lookup"><span data-stu-id="d375a-p115">Next, ensure that the address space of the virtual network is reachable from your on-premises network. This is usually done by adding a route corresponding to the virtual network address space to your VPN device and then advertising that route to the rest of the routing infrastructure of your organization network. Work with your IT department to determine how to do this.</span></span>
  
<span data-ttu-id="d375a-p116">次に、3 つの可用性セットの名前を定義します。「表 A」に必要事項を記入します。</span><span class="sxs-lookup"><span data-stu-id="d375a-p116">Next, define the names of three availability sets. Fill out Table A.</span></span> 
  
|<span data-ttu-id="d375a-284">**項目**</span><span class="sxs-lookup"><span data-stu-id="d375a-284">**Item**</span></span>|<span data-ttu-id="d375a-285">**用途**</span><span class="sxs-lookup"><span data-stu-id="d375a-285">**Purpose**</span></span>|<span data-ttu-id="d375a-286">**可用性セット名**</span><span class="sxs-lookup"><span data-stu-id="d375a-286">**Availability set name**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="d375a-287">1.</span><span class="sxs-lookup"><span data-stu-id="d375a-287">1.</span></span>  <br/> |<span data-ttu-id="d375a-288">ドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="d375a-288">Domain controllers</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-290">2.</span><span class="sxs-lookup"><span data-stu-id="d375a-290">2.</span></span>  <br/> |<span data-ttu-id="d375a-291">AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="d375a-291">AD FS servers</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
|<span data-ttu-id="d375a-293">3.</span><span class="sxs-lookup"><span data-stu-id="d375a-293">3.</span></span>  <br/> |<span data-ttu-id="d375a-294">Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="d375a-294">Web application proxy servers</span></span>  <br/> |![線](./media/Common-Images/TableLine.png)  <br/> |
   
 <span data-ttu-id="d375a-296">**表 A: 可用性セット**</span><span class="sxs-lookup"><span data-stu-id="d375a-296">**Table A: Availability sets**</span></span>
  
<span data-ttu-id="d375a-297">これらの名前は、フェーズ 2、3、および 4 で仮想マシンを作成する際に必要になります。</span><span class="sxs-lookup"><span data-stu-id="d375a-297">You will need these names when you create the virtual machines in phases 2, 3, and 4.</span></span>
  
<span data-ttu-id="d375a-298">次に示す Azure PowerShell コマンドで、新しい可用性セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="d375a-298">Create the new availability sets with these Azure PowerShell commands.</span></span>
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

<span data-ttu-id="d375a-299">次に、このフェーズが正常に完了した結果の構成を示します。</span><span class="sxs-lookup"><span data-stu-id="d375a-299">This is the configuration resulting from the successful completion of this phase.</span></span>
  
<span data-ttu-id="d375a-300">**フェーズ 1:Office 365 の高可用性フェデレーション認証用の Azure インフラストラクチャ**</span><span class="sxs-lookup"><span data-stu-id="d375a-300">**Phase 1: The Azure infrastructure for high availability federated authentication for Office 365**</span></span>

![Azure インフラストラクチャによる Azure での高可用性 Office 365 フェデレーション認証のフェーズ1](media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a><span data-ttu-id="d375a-302">次の手順</span><span class="sxs-lookup"><span data-stu-id="d375a-302">Next step</span></span>

<span data-ttu-id="d375a-303">[「フェーズ 2: ドメインコントローラーを構成](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)する」を使用して、このワークロードの構成を続行します。</span><span class="sxs-lookup"><span data-stu-id="d375a-303">Use [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) to continue with the configuration of this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d375a-304">関連項目</span><span class="sxs-lookup"><span data-stu-id="d375a-304">See Also</span></span>

[<span data-ttu-id="d375a-305">Azure に Office 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="d375a-305">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="d375a-306">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="d375a-306">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="d375a-307">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="d375a-307">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)

[<span data-ttu-id="d375a-308">Office 365 ID と Azure Active Directory について</span><span class="sxs-lookup"><span data-stu-id="d375a-308">Understanding Office 365 identity and Azure Active Directory</span></span>](about-office-365-identity.md)


