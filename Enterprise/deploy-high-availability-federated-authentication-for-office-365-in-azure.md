---
title: Azure に Office 365 の高可用性フェデレーション認証を展開する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 概要:Microsoft Azure で Office 365 サブスクリプションの高可用性フェデレーション認証を構成します。
ms.openlocfilehash: 9e671cabf2e9ca764f4948822da6aa0fb57ef5b5
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "31038051"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a><span data-ttu-id="659af-103">Azure に Office 365 の高可用性フェデレーション認証を展開する</span><span class="sxs-lookup"><span data-stu-id="659af-103">Deploy high availability federated authentication for Office 365 in Azure</span></span>

 <span data-ttu-id="659af-104">**概要:** Microsoft Azure で Office 365 サブスクリプションの高可用性フェデレーション認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="659af-104">**Summary:** Configure high availability federated authentication for your Office 365 subscription in Microsoft Azure.</span></span>
  
<span data-ttu-id="659af-105">この記事には、次に示す仮想マシンを装備した Azure インフラストラクチャ サービスに Microsoft Office 365 の高可用性フェデレーション認証を展開するための詳細な手順へのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="659af-105">This article has links to the step-by-step instructions for deploying high availability federated authentication for Microsoft Office 365 in Azure infrastructure services with these virtual machines:</span></span>
  
- <span data-ttu-id="659af-106">2 つの Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="659af-106">Two web application proxy servers</span></span>
    
- <span data-ttu-id="659af-107">2 つの Active Directory フェデレーション サービス (AD FS) サーバー</span><span class="sxs-lookup"><span data-stu-id="659af-107">Two Active Directory Federation Services (AD FS) servers</span></span>
    
- <span data-ttu-id="659af-108">2 つのレプリカ ドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="659af-108">Two replica domain controllers</span></span>
    
- <span data-ttu-id="659af-109">Azure AD Connect を実行する 1 つのディレクトリ同期 (DirSync) サーバー</span><span class="sxs-lookup"><span data-stu-id="659af-109">One directory synchronization (DirSync) server running Azure AD Connect</span></span>
    
<span data-ttu-id="659af-110">各サーバーのプレース ホルダー名を使用した構成がこちらです。</span><span class="sxs-lookup"><span data-stu-id="659af-110">Here is the configuration, with placeholder names for each server.</span></span>
  
<span data-ttu-id="659af-111">**Azure での Office 365 インフラストラクチャの高可用性フェデレーション認証**</span><span class="sxs-lookup"><span data-stu-id="659af-111">**A high availability federated authentication for Office 365 infrastructure in Azure**</span></span>

![Azure での高可用性 Office 365 フェデレーション認証インフラストラクチャの最終構成](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
<span data-ttu-id="659af-113">すべての仮想マシンが単一のクロスプレミス Azure 仮想ネットワーク (VNet) に入っています。</span><span class="sxs-lookup"><span data-stu-id="659af-113">All of the virtual machines are in a single cross-premises Azure virtual network (VNet).</span></span> 
  
> [!NOTE]
> <span data-ttu-id="659af-p101">個々のユーザーのフェデレーション認証は、オンプレミスのリソースには依存しません。ただし、クロスプレミス接続が使用できなくなると、オンプレミスの Active Directory Domain Services (AD DS) で加えられたユーザー アカウントとグループに対する更新が VNet 内のドメイン コントローラーで受信されなくなります。これを回避するために、クロスプレミス接続で高可用性を構成できます。詳細については、「[高可用性のクロスプレミス接続および VNet 間接続](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="659af-p101">Federated authentication of individual users does not rely on any on-premises resources. However, if the cross-premises connection becomes unavailable, the domain controllers in the VNet will not receive updates to user accounts and groups made in the on-premises Windows Server AD. To ensure this does not happen, you can configure high availability for your cross-premises connection. For more information, see [Highly Available Cross-Premises and VNet-to-VNet Connectivity](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable)</span></span>
  
<span data-ttu-id="659af-118">特定の役割を持つ仮想マシンの各ペアが独自のサブネットと可用性セットに入っています。</span><span class="sxs-lookup"><span data-stu-id="659af-118">Each pair of virtual machines for a specific role is in its own subnet and availability set.</span></span>
  
> [!NOTE]
> <span data-ttu-id="659af-p102">この VNet はオンプレミスのネットワークに接続されているため、この構成に管理サブネット上の jumpbox や仮想マシンの監視は含まれません。詳細については、「[N 層のアーキテクチャで Windows VM を実行する](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="659af-p102">Because this VNet is connected to the on-premises network, this configuration does not include jumpbox or monitoring virtual machines on a management subnet. For more information, see [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm).</span></span> 
  
<span data-ttu-id="659af-p103">この構成の結果として、すべての Office 365 ユーザーがフェデレーション認証を使用できるようになります。この認証では、Office 365 アカウントではなく、Windows Server Active Directory の資格情報を使用してサインインすることができます。フェデレーション認証インフラストラクチャでは、オンプレミスの境界ネットワークよりも Azure インフラストラクチャ サービスでより簡単に展開できるサーバーの冗長セットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="659af-p103">The result of this configuration is that you will have federated authentication for all of your Office 365 users, in which they can use their Windows Server Active Directory credentials to sign in rather than their Office 365 account. The federated authentication infrastructure uses a redundant set of servers that are more easily deployed in Azure infrastructure services, rather than in your on-premises edge network.</span></span>
  
## <a name="bill-of-materials"></a><span data-ttu-id="659af-123">部品表</span><span class="sxs-lookup"><span data-stu-id="659af-123">Bill of materials</span></span>

<span data-ttu-id="659af-124">このベースライン構成には、Azure のサービスおよびコンポーネントの次のセットが必要です。</span><span class="sxs-lookup"><span data-stu-id="659af-124">This baseline configuration requires the following set of Azure services and components:</span></span>
  
- <span data-ttu-id="659af-125">7 つの仮想マシン</span><span class="sxs-lookup"><span data-stu-id="659af-125">Seven virtual machines</span></span>
    
- <span data-ttu-id="659af-126">4 つのサブネットを持つ 1 つのクロスプレミス仮想ネットワーク</span><span class="sxs-lookup"><span data-stu-id="659af-126">One cross-premises virtual network with four subnets</span></span>
    
- <span data-ttu-id="659af-127">4 つのリソース グループ</span><span class="sxs-lookup"><span data-stu-id="659af-127">Four resource groups</span></span>
    
- <span data-ttu-id="659af-128">3 つの可用性セット</span><span class="sxs-lookup"><span data-stu-id="659af-128">Three availability sets</span></span>
    
- <span data-ttu-id="659af-129">1 つの Azure サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="659af-129">One Azure subscription</span></span>
    
<span data-ttu-id="659af-130">仮想マシンと、この構成用の既定サイズを次に示します。</span><span class="sxs-lookup"><span data-stu-id="659af-130">Here are the virtual machines and their default sizes for this configuration.</span></span>
  
|<span data-ttu-id="659af-131">**アイテム**</span><span class="sxs-lookup"><span data-stu-id="659af-131">**Item**</span></span>|<span data-ttu-id="659af-132">**仮想マシンの説明**</span><span class="sxs-lookup"><span data-stu-id="659af-132">**Virtual machine description**</span></span>|<span data-ttu-id="659af-133">**Azure ギャラリー イメージ**</span><span class="sxs-lookup"><span data-stu-id="659af-133">**Azure gallery image**</span></span>|<span data-ttu-id="659af-134">**既定のサイズ**</span><span class="sxs-lookup"><span data-stu-id="659af-134">**Default size**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="659af-135">1.</span><span class="sxs-lookup"><span data-stu-id="659af-135">1.</span></span>  <br/> |<span data-ttu-id="659af-136">1 つ目のドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="659af-136">First domain controller</span></span>  <br/> |<span data-ttu-id="659af-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="659af-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="659af-138">D2</span><span class="sxs-lookup"><span data-stu-id="659af-138">D2</span></span>  <br/> |
|<span data-ttu-id="659af-139">2.</span><span class="sxs-lookup"><span data-stu-id="659af-139">2.</span></span>  <br/> |<span data-ttu-id="659af-140">2 つ目のドメイン コントローラー</span><span class="sxs-lookup"><span data-stu-id="659af-140">Second domain controller</span></span>  <br/> |<span data-ttu-id="659af-141">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="659af-141">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="659af-142">D2</span><span class="sxs-lookup"><span data-stu-id="659af-142">D2</span></span>  <br/> |
|<span data-ttu-id="659af-143">3.</span><span class="sxs-lookup"><span data-stu-id="659af-143">3.</span></span>  <br/> |<span data-ttu-id="659af-144">Azure AD Connect サーバー</span><span class="sxs-lookup"><span data-stu-id="659af-144">Azure AD Connect server</span></span>  <br/> |<span data-ttu-id="659af-145">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="659af-145">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="659af-146">D2</span><span class="sxs-lookup"><span data-stu-id="659af-146">D2</span></span>  <br/> |
|<span data-ttu-id="659af-147">4.</span><span class="sxs-lookup"><span data-stu-id="659af-147">4.</span></span>  <br/> |<span data-ttu-id="659af-148">1 つ目の AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="659af-148">First AD FS server</span></span>  <br/> |<span data-ttu-id="659af-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="659af-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="659af-150">D2</span><span class="sxs-lookup"><span data-stu-id="659af-150">D2</span></span>  <br/> |
|<span data-ttu-id="659af-151">5.</span><span class="sxs-lookup"><span data-stu-id="659af-151">5.</span></span>  <br/> |<span data-ttu-id="659af-152">2 つ目の AD FS サーバー</span><span class="sxs-lookup"><span data-stu-id="659af-152">Second AD FS server</span></span>  <br/> |<span data-ttu-id="659af-153">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="659af-153">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="659af-154">D2</span><span class="sxs-lookup"><span data-stu-id="659af-154">D2</span></span>  <br/> |
|<span data-ttu-id="659af-155">6.</span><span class="sxs-lookup"><span data-stu-id="659af-155">6.</span></span>  <br/> |<span data-ttu-id="659af-156">1 つ目の Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="659af-156">First web application proxy server</span></span>  <br/> |<span data-ttu-id="659af-157">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="659af-157">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="659af-158">D2</span><span class="sxs-lookup"><span data-stu-id="659af-158">D2</span></span>  <br/> |
|<span data-ttu-id="659af-159">7.</span><span class="sxs-lookup"><span data-stu-id="659af-159">7.</span></span>  <br/> |<span data-ttu-id="659af-160">2 つ目の Web アプリケーション プロキシ サーバー</span><span class="sxs-lookup"><span data-stu-id="659af-160">Second web application proxy server</span></span>  <br/> |<span data-ttu-id="659af-161">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="659af-161">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="659af-162">D2</span><span class="sxs-lookup"><span data-stu-id="659af-162">D2</span></span>  <br/> |
   
<span data-ttu-id="659af-163">この構成の見積もりコストを計算するには、「[料金計算ツール](https://azure.microsoft.com/pricing/calculator/)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="659af-163">To compute the estimated costs for this configuration, see the [Azure pricing calculator](https://azure.microsoft.com/pricing/calculator/)</span></span>
  
## <a name="phases-of-deployment"></a><span data-ttu-id="659af-164">展開のフェーズ</span><span class="sxs-lookup"><span data-stu-id="659af-164">Phases of deployment</span></span>

<span data-ttu-id="659af-165">次のフェーズでは、このワークロードを展開します。</span><span class="sxs-lookup"><span data-stu-id="659af-165">You deploy this workload in the following phases:</span></span>
  
- <span data-ttu-id="659af-p104">[フェーズ 1: Azure を構成する](high-availability-federated-authentication-phase-1-configure-azure.md)。リソース グループ、ストレージ アカウント、可用性セット、およびクロスプレミスの仮想ネットワークを作成します。</span><span class="sxs-lookup"><span data-stu-id="659af-p104">[Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Create resource groups, storage accounts, availability sets, and a cross-premises virtual network.</span></span>
    
- <span data-ttu-id="659af-p105">[フェーズ 2: ドメイン コントローラーを構成する](high-availability-federated-authentication-phase-2-configure-domain-controllers.md)。レプリカの Active Directory Domain Services (AD DS) ドメイン コントローラーと DirSync サーバーを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="659af-p105">[Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Create and configure replica Windows Server Active Directory (AD) domain controllers and the DirSync server.</span></span>
    
- <span data-ttu-id="659af-p106">[フェーズ 3: AD FS サーバーを構成する](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md)。2 つの AD FS サーバーを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="659af-p106">[Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Create and configure the two AD FS servers.</span></span>
    
- <span data-ttu-id="659af-p107">[フェーズ 4: Web アプリケーション プロキシを構成する](high-availability-federated-authentication-phase-4-configure-web-application-pro.md)。2 つの Web アプリケーション プロキシ サーバーを作成して構成します。</span><span class="sxs-lookup"><span data-stu-id="659af-p107">[Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Create and configure the two web application proxy servers.</span></span>
    
- <span data-ttu-id="659af-p108">[フェーズ 5: Office 365 のフェデレーション認証を構成する](high-availability-federated-authentication-phase-5-configure-federated-authentic.md)。Office 365 サブスクリプションのフェデレーション認証を構成します。</span><span class="sxs-lookup"><span data-stu-id="659af-p108">[Phase 5: Configure federated authentication for Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure federated authentication for your Office 365 subscription.</span></span>
    
<span data-ttu-id="659af-p109">この記事では、定義済みのアーキテクチャを使用して、Azure インフラストラクチャ サービスに Office 365 の機能的な高可用性フェデレーション認証を作成するためのフェーズごとの規範となるガイドを提供します。以下の点にご注意ください。</span><span class="sxs-lookup"><span data-stu-id="659af-p109">These articles provide a prescriptive, phase-by-phase guide for a predefined architecture to create a functional, high availability federated authentication for Office 365 in Azure infrastructure services. Keep the following in mind:</span></span>
  
- <span data-ttu-id="659af-178">経験豊富な AD FS の実行者である場合、フェーズ 3 と 4 の手順を自由に適応させて、自分のニーズに最適なサーバーのセットを構築できます。</span><span class="sxs-lookup"><span data-stu-id="659af-178">If you are an experienced AD FS implementer, feel free to adapt the instructions in phases 3 and 4 and build the set of servers that best suits your needs.</span></span>
    
- <span data-ttu-id="659af-179">既存のクロスプレミスの仮想ネットワークを使用した既存の Azure ハイブリッド クラウド展開がある場合は、フェーズ 1 と 2 の手順を自由に適応させるかスキップして、AD FS と Web アプリケーション プロキシ サーバーを適切なサブネットに配置できます。</span><span class="sxs-lookup"><span data-stu-id="659af-179">If you already have an existing Azure hybrid cloud deployment with an existing cross-premises virtual network, feel free to adapt or skip the instructions in phases 1 and 2 and place the AD FS and web application proxy servers on the appropriate subnets.</span></span>
    
<span data-ttu-id="659af-180">開発/テスト環境、またはこの構成の概念実証を構築するには、「[Office 365 開発/テスト環境のフェデレーション ID](federated-identity-for-your-office-365-dev-test-environment.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="659af-180">To build a dev/test environment or a proof-of-concept of this configuration, see [Federated identity for your Office 365 dev/test environment](federated-identity-for-your-office-365-dev-test-environment.md).</span></span>
  
## <a name="next-step"></a><span data-ttu-id="659af-181">次の手順</span><span class="sxs-lookup"><span data-stu-id="659af-181">Next step</span></span>

<span data-ttu-id="659af-182">このワークロードの構成を「[高可用性フェデレーション認証のフェーズ 1:Azure を構成する](high-availability-federated-authentication-phase-1-configure-azure.md)」から開始します。</span><span class="sxs-lookup"><span data-stu-id="659af-182">Start the configuration of this workload with [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span> 
  
<!--
> [!TIP]
> For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
--> 

