---
title: Azure に Microsoft 365 の高可用性フェデレーション認証を展開する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: '概要: Microsoft Azure の Microsoft 365 サブスクリプションの高可用性フェデレーション認証を構成します。'
ms.openlocfilehash: 98b8bdff708d02f866a3e2f2d2521bec5b011bb7
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230053"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a><span data-ttu-id="3ba74-103">Azure に Microsoft 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="3ba74-103">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>

<span data-ttu-id="3ba74-104">この記事では、次の仮想マシンを使用した Azure インフラストラクチャサービスに Microsoft Microsoft 365 の高可用性フェデレーション認証を展開するための詳細な手順へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="3ba74-104">This article has links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Microsoft 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="3ba74-105">2 つの Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="3ba74-105">Two web application proxy servers</span></span>
    
- <span data-ttu-id="3ba74-106">2 つの Active Directory フェデレーション サービス (AD FS) サーバー</span><span class="sxs-lookup"><span data-stu-id="3ba74-106">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="3ba74-107">2 つのレプリカ ドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="3ba74-107">Two replica domain controllers</span></span>
    
- <span data-ttu-id="3ba74-108">Azure AD Connect を実行する 1 つのディレクトリ同期サーバー</span><span class="sxs-lookup"><span data-stu-id="3ba74-108">One directory synchronization server running Azure AD Connect</span></span>
    
<span data-ttu-id="3ba74-109">各サーバーのプレース ホルダー名を使用した構成がこちらです。</span><span class="sxs-lookup"><span data-stu-id="3ba74-109">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="3ba74-110">**Azure での Microsoft 365 インフラストラクチャの高可用性フェデレーション認証**</span><span class="sxs-lookup"><span data-stu-id="3ba74-110">**A high availability federated authentication for Microsoft 365 infrastructure in Azure**</span></span>

![Azure での高可用性 Microsoft 365 フェデレーション認証インフラストラクチャの最終構成](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="3ba74-112">すべての仮想マシンが単一のクロスプレミス Azure 仮想ネットワーク (VNet) に入っています。</span><span class="sxs-lookup"><span data-stu-id="3ba74-112">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="3ba74-p101">個々のユーザーのフェデレーション認証は、オンプレミスのリソースには依存しません。ただし、クロスプレミス接続が使用できなくなると、オンプレミスの Active Directory Domain Services (AD DS) で加えられたユーザー アカウントとグループに対する更新が VNet 内のドメイン コントローラーで受信されなくなります。これを回避するために、クロスプレミス接続で高可用性を構成できます。詳細については、「[高可用性のクロスプレミス接続および VNet 間接続](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ba74-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Active Directory Domain Services (AD DS). To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="3ba74-117">特定の役割を持つ仮想マシンの各ペアが独自のサブネットと可用性セットに入っています。</span><span class="sxs-lookup"><span data-stu-id="3ba74-117">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="3ba74-p102">この VNet はオンプレミスのネットワークに接続されているため、この構成に管理サブネット上の jumpbox や仮想マシンの監視は含まれません。詳細については、「[N 層のアーキテクチャで Windows VM を実行する](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ba74-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="3ba74-120">この構成の結果として、microsoft 365 のすべてのユーザーに対してフェデレーション認証を受けることができます。これにより、自分の AD DS の資格情報を使用して、Microsoft 365 アカウントではなくサインインすることができます。</span><span class="sxs-lookup"><span data-stu-id="3ba74-120">The result of this configuration is that you will have federated authentication for all of your Microsoft 365 users, in which they can use their AD DS credentials to sign in rather than their Microsoft 365 account.</span></span> <span data-ttu-id="3ba74-121">フェデレーション認証インフラストラクチャでは、オンプレミスの境界ネットワークよりも Azure インフラストラクチャ サービスでより簡単に展開できるサーバーの冗長セットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3ba74-121">The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="3ba74-122">部品表</span><span class="sxs-lookup"><span data-stu-id="3ba74-122">Bill of materials</span></span>

<span data-ttu-id="3ba74-123">このベースライン構成には、Azure のサービスおよびコンポーネントの次のセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="3ba74-123">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="3ba74-124">7 つの仮想マシン</span><span class="sxs-lookup"><span data-stu-id="3ba74-124">Seven virtual machines</span></span>
    
- <span data-ttu-id="3ba74-125">4 つのサブネットを持つ 1 つのクロスプレミス仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="3ba74-125">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="3ba74-126">4 つのリソース グループ</span><span class="sxs-lookup"><span data-stu-id="3ba74-126">Four resource groups</span></span>
    
- <span data-ttu-id="3ba74-127">3 つの可用性セット</span><span class="sxs-lookup"><span data-stu-id="3ba74-127">Three availability sets</span></span>
    
- <span data-ttu-id="3ba74-128">1 つの Azure サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="3ba74-128">One Azure subscription</span></span>
    
<span data-ttu-id="3ba74-129">仮想マシンと、この構成用の既定サイズを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3ba74-129">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="3ba74-130">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="3ba74-130">**Item**</span></span>|<span data-ttu-id="3ba74-131">**仮想マシンの説明**</span><span class="sxs-lookup"><span data-stu-id="3ba74-131">**Virtual machine description**</span></span>|<span data-ttu-id="3ba74-132">**Azure ギャラリー イメージ**</span><span class="sxs-lookup"><span data-stu-id="3ba74-132">**Azure gallery image**</span></span>|<span data-ttu-id="3ba74-133">**既定のサイズ**</span><span class="sxs-lookup"><span data-stu-id="3ba74-133">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="3ba74-134">1.</span><span class="sxs-lookup"><span data-stu-id="3ba74-134">1.</span></span>  <br/> |<span data-ttu-id="3ba74-135">1 つ目のドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="3ba74-135">First domain controller</span></span>  <br/> |<span data-ttu-id="3ba74-136">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3ba74-136">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3ba74-137">D2</span><span class="sxs-lookup"><span data-stu-id="3ba74-137">D2</span></span>  <br/> |
|<span data-ttu-id="3ba74-138">2.</span><span class="sxs-lookup"><span data-stu-id="3ba74-138">2.</span></span>  <br/> |<span data-ttu-id="3ba74-139">2 つ目のドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="3ba74-139">Second domain controller</span></span>  <br/> |<span data-ttu-id="3ba74-140">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3ba74-140">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3ba74-141">D2</span><span class="sxs-lookup"><span data-stu-id="3ba74-141">D2</span></span>  <br/> |
|<span data-ttu-id="3ba74-142">3.</span><span class="sxs-lookup"><span data-stu-id="3ba74-142">3.</span></span>  <br/> |<span data-ttu-id="3ba74-143">Azure AD Connect サーバー</span><span class="sxs-lookup"><span data-stu-id="3ba74-143">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="3ba74-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3ba74-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3ba74-145">D2</span><span class="sxs-lookup"><span data-stu-id="3ba74-145">D2</span></span>  <br/> |
|<span data-ttu-id="3ba74-146">4.</span><span class="sxs-lookup"><span data-stu-id="3ba74-146">4.</span></span>  <br/> |<span data-ttu-id="3ba74-147">1 つ目の AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="3ba74-147">First AD FS server</span></span>  <br/> |<span data-ttu-id="3ba74-148">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3ba74-148">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3ba74-149">D2</span><span class="sxs-lookup"><span data-stu-id="3ba74-149">D2</span></span>  <br/> |
|<span data-ttu-id="3ba74-150">5.</span><span class="sxs-lookup"><span data-stu-id="3ba74-150">5.</span></span>  <br/> |<span data-ttu-id="3ba74-151">2 つ目の AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="3ba74-151">Second AD FS server</span></span>  <br/> |<span data-ttu-id="3ba74-152">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3ba74-152">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3ba74-153">D2</span><span class="sxs-lookup"><span data-stu-id="3ba74-153">D2</span></span>  <br/> |
|<span data-ttu-id="3ba74-154">6.</span><span class="sxs-lookup"><span data-stu-id="3ba74-154">6.</span></span>  <br/> |<span data-ttu-id="3ba74-155">1 つ目の Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="3ba74-155">First web application proxy server</span></span>  <br/> |<span data-ttu-id="3ba74-156">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3ba74-156">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3ba74-157">D2</span><span class="sxs-lookup"><span data-stu-id="3ba74-157">D2</span></span>  <br/> |
|<span data-ttu-id="3ba74-158">7.</span><span class="sxs-lookup"><span data-stu-id="3ba74-158">7.</span></span>  <br/> |<span data-ttu-id="3ba74-159">2 つ目の Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="3ba74-159">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="3ba74-160">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="3ba74-160">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="3ba74-161">D2</span><span class="sxs-lookup"><span data-stu-id="3ba74-161">D2</span></span>  <br/> |
   
<span data-ttu-id="3ba74-162">この構成の見積もりコストを計算するには、「[料金計算ツール](https://azure.microsoft.com/pricing/calculator/)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="3ba74-162">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="3ba74-163">展開のフェーズ</span><span class="sxs-lookup"><span data-stu-id="3ba74-163">Phases of deployment</span></span>

<span data-ttu-id="3ba74-164">次のフェーズでは、このワークロードを展開します。</span><span class="sxs-lookup"><span data-stu-id="3ba74-164">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="3ba74-p104">[フェーズ 1: Azure を構成する](high-availability-federated-authentication-phase-1-configure-azure.md)。リソース グループ、ストレージ アカウント、可用性セット、およびクロスプレミスの仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ba74-p104">[Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="3ba74-167">[フェーズ 2: ドメイン コントローラーを構成する](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。</span><span class="sxs-lookup"><span data-stu-id="3ba74-167">[Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md).</span></span> <span data-ttu-id="3ba74-168">レプリカの AD DS ドメイン コントローラーとディレクトリ同期サーバーを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="3ba74-168">Create and configure replica AD DS domain controllers and the directory synchronization server.</span></span>
    
- <span data-ttu-id="3ba74-p106">[フェーズ 3: AD FS サーバーを構成する](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。2 つの AD FS サーバーを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="3ba74-p106">[Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="3ba74-p107">[フェーズ 4: Web アプリケーション プロキシを構成する](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。2 つの Web アプリケーション プロキシ サーバーを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="3ba74-p107">[Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="3ba74-p108">[フェーズ 5: Microsoft 365 のフェデレーション認証を構成](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)します。Microsoft 365 サブスクリプションのフェデレーション認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="3ba74-p108">[Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Microsoft 365 subscription.</span></span>
    
<span data-ttu-id="3ba74-p109">これらの記事では、Azure インフラストラクチャサービスで Microsoft 365 の機能的な高可用性フェデレーション認証を作成するための、事前定義されたアーキテクチャに関する規範的なフェーズごとのガイドを提供します。次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3ba74-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Microsoft 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="3ba74-177">経験豊富な AD FS の実行者である場合、フェーズ 3 と 4 の手順を自由に適応させて、自分のニーズに最適なサーバーのセットを構築できます。</span><span class="sxs-lookup"><span data-stu-id="3ba74-177">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="3ba74-178">既存のクロスプレミスの仮想ネットワークを使用した既存の Azure ハイブリッド クラウド展開がある場合は、フェーズ 1 と 2 の手順を自由に適応させるかスキップして、AD FS と Web アプリケーション プロキシ サーバーを適切なサブネットに配置できます。</span><span class="sxs-lookup"><span data-stu-id="3ba74-178">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="3ba74-179">開発/テスト環境、またはこの構成の概念実証を構築するには、「 [Microsoft 365 開発/テスト環境のフェデレーション id](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ba74-179">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Microsoft 365 dev/test environment](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="3ba74-180">次の手順</span><span class="sxs-lookup"><span data-stu-id="3ba74-180">Next step</span></span>

<span data-ttu-id="3ba74-181">このワークロードの構成を「[フェーズ 1: Azure を構成する](high-availability-federated-authentication-phase-1-configure-azure.md)」から開始します。 </span><span class="sxs-lookup"><span data-stu-id="3ba74-181">Start the configuration of this workload with [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
