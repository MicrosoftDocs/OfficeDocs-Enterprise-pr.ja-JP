---
title: "Azure に Office 365 の高可用性フェデレーション認証を展開する"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Hybrid
- Ent_O365_Top
ms.custom:
- apr17entnews
- DecEntMigration
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: "概要:Microsoft Azure で Office 365 サブスクリプションの高可用性フェデレーション認証を構成します。"
ms.openlocfilehash: 6e64912d6b115e3aee179509c504f3872ecea551
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="89c54-103">Azure に Office 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="89c54-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="89c54-104">**概要:**Microsoft Azure で Office 365 サブスクリプションの高可用性フェデレーション認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="89c54-105">この記事には、次に示す仮想マシンを装備した Azure インフラストラクチャ サービスに Microsoft Office 365 の高可用性フェデレーション認証を展開するための詳細な手順へのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="89c54-105">This article contains links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="89c54-106">2 つの Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="89c54-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="89c54-107">2 つの Active Directory フェデレーション サービス (AD FS) サーバー</span><span class="sxs-lookup"><span data-stu-id="89c54-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="89c54-108">2 つのレプリカ ドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="89c54-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="89c54-109">Azure AD Connect を実行する 1 つのディレクトリ同期 (DirSync) サーバー</span><span class="sxs-lookup"><span data-stu-id="89c54-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="89c54-110">各サーバーのプレースホルダー名を使用した構成がこちらです。</span><span class="sxs-lookup"><span data-stu-id="89c54-110">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="89c54-111">**Azure での Office 365 インフラストラクチャの高可用性フェデレーション認証**</span><span class="sxs-lookup"><span data-stu-id="89c54-111">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![Azure での高可用性 Office 365 フェデレーション認証インフラストラクチャの最終構成](images/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="89c54-113">すべての仮想マシンが単一のクロスプレミス Azure 仮想ネットワーク (VNet) に入っています。</span><span class="sxs-lookup"><span data-stu-id="89c54-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="89c54-p101">個々のユーザーのフェデレーション認証は、オンプレミスのリソースには依存しません。ただし、クロスプレミス接続が使用できなくなると、Windows Server AD で加えられたユーザー アカウントとグループに対する更新が VNet 内のドメイン コントローラーで受信されなくなります。これを回避するために、クロスプレミス接続で高可用性を構成できます。詳細については、「[高可用性のクロスプレミス接続および VNet 間接続](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89c54-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="89c54-118">特定の役割を持つ仮想マシンの各ペアが独自のサブネットと可用性セットに入っています。</span><span class="sxs-lookup"><span data-stu-id="89c54-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="89c54-p102">この VNet はオンプレミスのネットワークに接続されているため、この構成に管理サブネット上の jumpbox や仮想マシンの監視は含まれません。詳細については、「[N 層のアーキテクチャで Windows VM を実行する](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89c54-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="89c54-p103">この構成の結果として、すべての Office 365 ユーザーがフェデレーション認証を使用できるようになります。この認証では、Office 365 アカウントではなく、Windows Server Active Directory の資格情報を使用してサインインすることができます。フェデレーション認証インフラストラクチャでは、オンプレミスの境界ネットワークよりも Azure インフラストラクチャ サービスでより簡単に展開できるサーバーの冗長セットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="89c54-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="89c54-123">部品表</span><span class="sxs-lookup"><span data-stu-id="89c54-123">Bill of materials</span></span>

<span data-ttu-id="89c54-124">このベースライン構成には、Azure のサービスおよびコンポーネントの次のセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="89c54-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="89c54-125">7 つの仮想マシン</span><span class="sxs-lookup"><span data-stu-id="89c54-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="89c54-126">4 つのサブネットを持つ 1 つのクロスプレミス仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="89c54-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="89c54-127">7 つのストレージ アカウント</span><span class="sxs-lookup"><span data-stu-id="89c54-127">Four resource groups</span></span>
    
- <span data-ttu-id="89c54-128">4 つのリソース グループ</span><span class="sxs-lookup"><span data-stu-id="89c54-128">Three availability sets</span></span>
    
- <span data-ttu-id="89c54-129">3 つの可用性セット</span><span class="sxs-lookup"><span data-stu-id="89c54-129">One Azure subscription</span></span>
    
<span data-ttu-id="89c54-130">仮想マシンと、この構成用の既定サイズを次に示します。</span><span class="sxs-lookup"><span data-stu-id="89c54-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="89c54-131">**項目**</span><span class="sxs-lookup"><span data-stu-id="89c54-131">**Item**</span></span>|<span data-ttu-id="89c54-132">**仮想マシンの説明**</span><span class="sxs-lookup"><span data-stu-id="89c54-132">**Virtual machine description**</span></span>|<span data-ttu-id="89c54-133">**Azure ギャラリー イメージ**</span><span class="sxs-lookup"><span data-stu-id="89c54-133">**Azure gallery image**</span></span>|<span data-ttu-id="89c54-134">**既定のサイズ**</span><span class="sxs-lookup"><span data-stu-id="89c54-134">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="89c54-135">1.</span><span class="sxs-lookup"><span data-stu-id="89c54-135">1.</span></span>  <br/> |<span data-ttu-id="89c54-136">1 つ目のドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="89c54-136">First domain controller</span></span>  <br/> |<span data-ttu-id="89c54-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="89c54-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="89c54-138">D2</span><span class="sxs-lookup"><span data-stu-id="89c54-138">D2</span></span>  <br/> |
|<span data-ttu-id="89c54-139">2.</span><span class="sxs-lookup"><span data-stu-id="89c54-139">2.</span></span>  <br/> |<span data-ttu-id="89c54-140">2 つ目のドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="89c54-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="89c54-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="89c54-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="89c54-142">D2</span><span class="sxs-lookup"><span data-stu-id="89c54-142">D2</span></span>  <br/> |
|<span data-ttu-id="89c54-143">3.</span><span class="sxs-lookup"><span data-stu-id="89c54-143">3.</span></span>  <br/> |<span data-ttu-id="89c54-144">Azure AD Connect サーバー</span><span class="sxs-lookup"><span data-stu-id="89c54-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="89c54-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="89c54-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="89c54-146">D2</span><span class="sxs-lookup"><span data-stu-id="89c54-146">D2</span></span>  <br/> |
|<span data-ttu-id="89c54-147">4.</span><span class="sxs-lookup"><span data-stu-id="89c54-147">4.</span></span>  <br/> |<span data-ttu-id="89c54-148">1 つ目の AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="89c54-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="89c54-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="89c54-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="89c54-150">D2</span><span class="sxs-lookup"><span data-stu-id="89c54-150">D2</span></span>  <br/> |
|<span data-ttu-id="89c54-151">5.</span><span class="sxs-lookup"><span data-stu-id="89c54-151">5.</span></span>  <br/> |<span data-ttu-id="89c54-152">2 つ目の AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="89c54-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="89c54-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="89c54-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="89c54-154">D2</span><span class="sxs-lookup"><span data-stu-id="89c54-154">D2</span></span>  <br/> |
|<span data-ttu-id="89c54-155">6.</span><span class="sxs-lookup"><span data-stu-id="89c54-155">6.</span></span>  <br/> |<span data-ttu-id="89c54-156">1 つ目の Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="89c54-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="89c54-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="89c54-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="89c54-158">D2</span><span class="sxs-lookup"><span data-stu-id="89c54-158">D2</span></span>  <br/> |
|<span data-ttu-id="89c54-159">7.</span><span class="sxs-lookup"><span data-stu-id="89c54-159">7.</span></span>  <br/> |<span data-ttu-id="89c54-160">2 つ目の Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="89c54-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="89c54-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="89c54-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="89c54-162">D2</span><span class="sxs-lookup"><span data-stu-id="89c54-162">D2</span></span>  <br/> |
   
<span data-ttu-id="89c54-163">この構成の見積もりコストを計算するには、「[料金計算ツール](https://azure.microsoft.com/pricing/calculator/)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="89c54-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="89c54-164">展開のフェーズ</span><span class="sxs-lookup"><span data-stu-id="89c54-164">Phases of deployment</span></span>

<span data-ttu-id="89c54-165">次のフェーズでは、このワークロードを展開します。</span><span class="sxs-lookup"><span data-stu-id="89c54-165">You deploy this workload in the following phases:</span></span>
  
<span data-ttu-id="89c54-166"><<<<<<< ヘッド</span><span class="sxs-lookup"><span data-stu-id="89c54-166"><<<<<<< HEAD</span></span>
- <span data-ttu-id="89c54-p104">[高可用性の統合認証フェーズ 1: 構成の Azure](high-availability-federated-authentication-phase-1-configure-azure.md)。リソース グループ、ストレージ アカウント、可用性の設定、および設置型の間の仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-p104">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="89c54-p105">[高可用性の統合認証フェーズ 2: ドメイン コント ローラーを構成する](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)です。作成し、Windows サーバー ・ Active Directory (AD) ドメイン コント ローラーのレプリカと、ディレクトリ同期サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-p105">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="89c54-p106">[高可用性の統合認証フェーズ 3: AD FS サーバーを構成する](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)です。作成し、2 つの AD FS サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-p106">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="89c54-p107">[高可用性の統合認証フェーズ 4: web アプリケーションのプロキシを構成する](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)です。作成し、2 つの web アプリケーションのプロキシ サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-p107">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="89c54-p108">[高可用性の統合認証フェーズ 5: Office 365 のフェデレーション認証を構成する](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)です。Office 365 サブスクリプションのフェデレーション認証を構成します。=======</span><span class="sxs-lookup"><span data-stu-id="89c54-p108">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription. =======</span></span>
- <span data-ttu-id="89c54-177">[高可用性の統合認証フェーズ 1: Azure の構成](high-availability-federated-authentication-phase-1-configure-azure.md)-リソース グループ、ストレージ アカウント、可用性の設定、および設置型の間の仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-177">[High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md) - Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="89c54-178">[高可用性の統合認証フェーズ 2: ドメイン コント ローラーを構成する](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)- を作成し、Windows サーバー ・ Active Directory (AD) ドメイン コント ローラーのレプリカと、ディレクトリ同期サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-178">[High availability federated authentication Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) - Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="89c54-179">[高可用性の統合認証フェーズ 3: AD FS サーバーを構成する](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)- を作成し、2 つの AD FS サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-179">[High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) - Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="89c54-180">[高可用性の統合認証フェーズ 4: web アプリケーションのプロキシを構成する](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)- を作成し、2 つの web アプリケーションのプロキシ サーバーを構成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-180">[High availability federated authentication Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) - Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="89c54-181">[高可用性の統合認証フェーズ 5: Office 365 のフェデレーション認証を構成する](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)-Office 365 サブスクリプションのフェデレーション認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="89c54-181">[High availability federated authentication Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) - Configure federated authentication for your Office 365 subscription.</span></span>
>>>>>>> <span data-ttu-id="89c54-182">master</span><span class="sxs-lookup"><span data-stu-id="89c54-182">master</span></span>
    
<span data-ttu-id="89c54-p109">この記事では、定義済みのアーキテクチャを使用して、Azure インフラストラクチャ サービスに Office 365 の機能的な高可用性フェデレーション認証を作成するためのフェーズごとの規範となるガイドを提供します。以下の点にご注意ください。</span><span class="sxs-lookup"><span data-stu-id="89c54-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="89c54-185">経験豊富な AD FS の実行者である場合、フェーズ 3 と 4 の手順を自由に適応させて、自分のニーズに最適なサーバーのセットを構築できます。</span><span class="sxs-lookup"><span data-stu-id="89c54-185">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="89c54-186">既存のクロスプレミスの仮想ネットワークを使用した既存の Azure ハイブリッド クラウド展開がある場合は、フェーズ 1 と 2 の手順を自由に適応させるかスキップして、AD FS と Web アプリケーション プロキシ サーバーを適切なサブネットに配置できます。</span><span class="sxs-lookup"><span data-stu-id="89c54-186">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="89c54-187">開発/テスト環境、またはこの構成の概念実証を構築するには、「[Office 365 開発/テスト環境のフェデレーション ID](federated-identity-for-your-office-365-dev-test-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89c54-187">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="89c54-188">次の手順</span><span class="sxs-lookup"><span data-stu-id="89c54-188">Next step</span></span>

<span data-ttu-id="89c54-189">このワークロードの構成を「[高可用性フェデレーション認証のフェーズ 1:Azure を構成する](high-availability-federated-authentication-phase-1-configure-azure.md)」から開始します。</span><span class="sxs-lookup"><span data-stu-id="89c54-189">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
> [!TIP]
> <span data-ttu-id="89c54-190">Office 365 の高可用性フェデレーション認証を Azure に素早く展開するためのファイル セットについては、「[Azure への Office 365 のフェデレーション認証の展開キット](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89c54-190">For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="89c54-191">See Also</span><span class="sxs-lookup"><span data-stu-id="89c54-191">See Also</span></span>

[<span data-ttu-id="89c54-192">Office 365 開発/テスト環境のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="89c54-192">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="89c54-193">クラウド導入およびハイブリッド ソリューション</span><span class="sxs-lookup"><span data-stu-id="89c54-193">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="89c54-194">Office 365 のフェデレーション ID</span><span class="sxs-lookup"><span data-stu-id="89c54-194">Federated identity for Office 365</span></span>](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)


