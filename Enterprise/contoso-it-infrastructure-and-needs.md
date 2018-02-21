---
title: "Contoso 社の IT インフラストラクチャおよびニーズ"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 5d6a58b8-bec3-4629-9737-8733c7b7ec92
description: "概要: Contoso 社のオンプレミスの IT インフラストラクチャの基本的な構造について、およびそのビジネス ニーズが Microsoft のクラウド サービスによってどのように満たされるかについて説明します。"
ms.openlocfilehash: b8282c4bd04448266bc68e65f95aaaff0a7a5db8
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="contosos-it-infrastructure-and-needs"></a><span data-ttu-id="21c83-103">Contoso 社の IT インフラストラクチャおよびニーズ</span><span class="sxs-lookup"><span data-stu-id="21c83-103">Contoso's IT infrastructure and needs</span></span>

 <span data-ttu-id="21c83-104">**概要:** Contoso 社のオンプレミスの IT インフラストラクチャの基本的な構造について、およびそのビジネス ニーズが Microsoft のクラウド サービスによってどのように満たされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="21c83-104">**Summary:** Understand the basic structure of Contoso's on-premises IT infrastructure and how its business needs can be met by Microsoft's cloud offerings.</span></span>
  
<span data-ttu-id="21c83-105">Contoso 社は、集中管理されたオンプレミスの IT インフラストラクチャから、クラウド包括型の IT インフラストラクチャへと移行中です。後者には、クラウドベースの個人生産性のワークロード、アプリケーション、およびハイブリッド シナリオが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="21c83-105">Contoso is in the process of transitioning from an on-premises, centralized IT infrastructure to a cloud-inclusive one that incorporates cloud-based personal productivity workloads, applications, and hybrid scenarios.</span></span>
  
## <a name="contosos-existing-it-infrastructure"></a><span data-ttu-id="21c83-106">Contoso 社の既存の IT インフラストラクチャ</span><span class="sxs-lookup"><span data-stu-id="21c83-106">Contoso's existing IT infrastructure</span></span>

<span data-ttu-id="21c83-107">Contoso 社では、ほとんど集中管理されたオンプレミスの IT インフラストラクチャを使用しており、アプリケーション データセンターはパリ本社に位置します。</span><span class="sxs-lookup"><span data-stu-id="21c83-107">Contoso uses a mostly centralized on-premises IT infrastructure, with application datacenters in the Paris headquarters.</span></span>
  
<span data-ttu-id="21c83-108">**図 1:Contoso 社の既存の IT インフラストラクチャ**</span><span class="sxs-lookup"><span data-stu-id="21c83-108">**Figure 1: Contoso's existing IT infrastructure**</span></span>

![Contoso 社の既存の IT インフラストラクチャ](images/Contoso_Poster/Existing_IT.png)
  
<span data-ttu-id="21c83-110">図 1 は、本社とアプリケーション データセンター、DMZ、およびインターネットを示しています。</span><span class="sxs-lookup"><span data-stu-id="21c83-110">Figure 1 shows a headquarters office with application datacenters, a DMZ, and the Internet.</span></span>
  
<span data-ttu-id="21c83-111">Contoso 社の DMZ では、サーバーのさまざまなセットが次のことを実現します。</span><span class="sxs-lookup"><span data-stu-id="21c83-111">In Contoso's DMZ, different sets of servers provide:</span></span>
  
- <span data-ttu-id="21c83-112">パリ本社のワーカーのための Contoso 社イントラネットおよび Web プロキシへのリモート アクセス。</span><span class="sxs-lookup"><span data-stu-id="21c83-112">Remote access to the Contoso intranet and web proxying for workers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="21c83-113">顧客が製品、部品、および備品を発注できる Contoso 社のパブリック Web サイトのホスティング。</span><span class="sxs-lookup"><span data-stu-id="21c83-113">Hosting for the Contoso public web site, from which customers can order products, parts, or supplies.</span></span>
    
- <span data-ttu-id="21c83-114">パートナーの通信およびコラボレーションのための Contoso 社のパートナー エクストラネットのホスティング。</span><span class="sxs-lookup"><span data-stu-id="21c83-114">Hosting for the Contoso partner extranet for partner communication and collaboration.</span></span>
    
## <a name="contosos-business-needs"></a><span data-ttu-id="21c83-115">Contoso 社のビジネス ニーズ</span><span class="sxs-lookup"><span data-stu-id="21c83-115">Contoso's business needs</span></span>

<span data-ttu-id="21c83-116">Contoso 社のビジネス ニーズの優先順位を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="21c83-116">Here are Contoso's business needs in priority order:</span></span>
  
1. <span data-ttu-id="21c83-117">地域の規制要件に準拠する</span><span class="sxs-lookup"><span data-stu-id="21c83-117">Adhere to regional regulatory requirements</span></span>
    
    <span data-ttu-id="21c83-118">罰金を防止し、地方自治体と良い関係を維持するために、Contoso 社はデータ ストレージおよび暗号化の規制に準拠していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21c83-118">To prevent fines and maintain good relations with local governments, Contoso must ensure compliance with data storage and encryption regulations.</span></span>
    
2. <span data-ttu-id="21c83-119">ベンダーおよびパートナー管理を向上させる</span><span class="sxs-lookup"><span data-stu-id="21c83-119">Improve vendor and partner management</span></span>
    
    <span data-ttu-id="21c83-p101">パートナー エクストラネットは古くなってきており、維持するには高額な費用がかかります。Contoso 社では、フェデレーション認証を使用するクラウドベースのソリューションに切り替えることを望んでいます。</span><span class="sxs-lookup"><span data-stu-id="21c83-p101">The partner extranet is aging and expensive to maintain. Contoso wants to replace it with a cloud-based solution that uses federated authentication.</span></span>
    
3. <span data-ttu-id="21c83-122">モバイル要員の生産性、デバイス管理、およびアクセスを向上させる</span><span class="sxs-lookup"><span data-stu-id="21c83-122">Improve mobile workforce productivity, device management, and access</span></span>
    
    <span data-ttu-id="21c83-123">Contoso 社のモバイル専門の要員は拡大しており、知的財産の保護とリソースへの効率的なアクセスを確保するためにデバイス管理を必要としています。</span><span class="sxs-lookup"><span data-stu-id="21c83-123">Contoso's mobile-only workforce is expanding and needs device management to ensure intellectual property protection and more efficient access to resources.</span></span>
    
4. <span data-ttu-id="21c83-124">リモート アクセス インフラストラクチャを縮小する</span><span class="sxs-lookup"><span data-stu-id="21c83-124">Reduce remote access infrastructure</span></span>
    
    <span data-ttu-id="21c83-125">リモート ワーカーによってよくアクセスされるリソースをクラウドに移動することで、Contoso 社は、リモート アクセス ソリューションの保守とサポートのコストを抑えて費用を削減します。</span><span class="sxs-lookup"><span data-stu-id="21c83-125">By moving resources commonly accessed by remote workers to the cloud, Contoso will save money by reducing maintenance and support costs for their remote access solution.</span></span>
    
5. <span data-ttu-id="21c83-126">オンプレミス データセンターをスケールダウンする</span><span class="sxs-lookup"><span data-stu-id="21c83-126">Scale down on-premises datacenters</span></span>
    
    <span data-ttu-id="21c83-127">Contoso 社のデータセンターには数百のサーバーが含まれ、その一部はレガシ機能またはアーカイブ機能を実行しており、IT スタッフがビジネス価値の高いワークロードを維持する上で妨げとなっています。</span><span class="sxs-lookup"><span data-stu-id="21c83-127">The Contoso datacenters contain hundreds of servers, some of which are running legacy or archival functions that distract IT staff from maintaining high business value workloads.</span></span>
    
6. <span data-ttu-id="21c83-128">四半期末の処理のためにコンピューティングおよびストレージ リソースをスケールアップする</span><span class="sxs-lookup"><span data-stu-id="21c83-128">Scale-up computing and storage resources for end-of-quarter processing</span></span>
    
    <span data-ttu-id="21c83-129">四半期末の財務会計、予測処理、および在庫管理では、サーバーおよびストレージを短期的に増大することが必要です。</span><span class="sxs-lookup"><span data-stu-id="21c83-129">End-of-quarter financial accounting and projection processing along with inventory management requires short-term increases in servers and storage.</span></span>
    
## <a name="mapping-contosos-business-needs-to-microsofts-cloud-offerings"></a><span data-ttu-id="21c83-130">Contoso 社のビジネス ニーズを Microsoft のクラウド製品にマッピングする</span><span class="sxs-lookup"><span data-stu-id="21c83-130">Mapping Contoso's business needs to Microsoft's cloud offerings</span></span>

<span data-ttu-id="21c83-131">Microsoft のクラウド サービスの分析に基づき、Contoso 社の IT 部門は次のマッピングを決定しました。</span><span class="sxs-lookup"><span data-stu-id="21c83-131">Based on an analysis of Microsoft's cloud offerings, Contoso's IT department determined the following mapping:</span></span>
  
|<span data-ttu-id="21c83-132">**サービスとしてのソフトウェア (SaaS)**</span><span class="sxs-lookup"><span data-stu-id="21c83-132">**Software as a Service (SaaS)**</span></span>|<span data-ttu-id="21c83-133">**サービスとしてのプラットフォーム (Azure PaaS )**</span><span class="sxs-lookup"><span data-stu-id="21c83-133">**Platform as a Service (Azure PaaS )**</span></span>|<span data-ttu-id="21c83-134">**サービスとしてのインフラストラクチャ (Azure IaaS )**</span><span class="sxs-lookup"><span data-stu-id="21c83-134">**Infrastructure as a Service (Azure IaaS )**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="21c83-135">**Office 365:** クラウド内の主要な、個人およびグループ生産性のアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="21c83-135">**Office 365:** Primary personal and group productivity applications in the cloud.</span></span> <br/> <span data-ttu-id="21c83-136">ビジネス ニーズ:1 3 5</span><span class="sxs-lookup"><span data-stu-id="21c83-136">Business needs: 1 3 5</span></span>  <br/> |<span data-ttu-id="21c83-137">クラウドベースのアプリを使用して、販売のホストおよびドキュメントと情報システムのサポートを行います。</span><span class="sxs-lookup"><span data-stu-id="21c83-137">Host sales and support documents and information systems using cloud-based apps.</span></span>  <br/> <span data-ttu-id="21c83-138">ビジネス ニーズ:3</span><span class="sxs-lookup"><span data-stu-id="21c83-138">Business need: 3</span></span>  <br/> |<span data-ttu-id="21c83-139">アーカイブ システムおよびレガシ システムをクラウドベースのサーバーに移動します。</span><span class="sxs-lookup"><span data-stu-id="21c83-139">Move archival and legacy systems to cloud-based servers.</span></span>  <br/> <span data-ttu-id="21c83-140">ビジネス ニーズ:5</span><span class="sxs-lookup"><span data-stu-id="21c83-140">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="21c83-p102">**Dynamics 365:** クラウド ベースの顧客およびベンダーの管理を使用します。DMZ からパートナー エクストラネットを削除します。</span><span class="sxs-lookup"><span data-stu-id="21c83-p102">**Dynamics 365:** Use cloud-based customer and vendor management. Remove partner extranet in the DMZ. </span></span><br/> <span data-ttu-id="21c83-143">ビジネス ニーズ:2</span><span class="sxs-lookup"><span data-stu-id="21c83-143">Business need: 2</span></span>  <br/> |<span data-ttu-id="21c83-144">モバイル アプリケーションはクラウドベースであり、パリのデータセンターベースではありません。</span><span class="sxs-lookup"><span data-stu-id="21c83-144">Mobile applications are cloud-based, rather than Paris datacenter-based.</span></span>  <br/> <span data-ttu-id="21c83-145">ビジネス ニーズ:3 4</span><span class="sxs-lookup"><span data-stu-id="21c83-145">Business needs: 3 4</span></span>  <br/> |<span data-ttu-id="21c83-146">使用頻度の低いアプリおよびデータをオンプレミス データセンターから移行します。</span><span class="sxs-lookup"><span data-stu-id="21c83-146">Migrate low-use apps and data out of on-premises datacenters.</span></span>  <br/> <span data-ttu-id="21c83-147">ビジネス ニーズ:5</span><span class="sxs-lookup"><span data-stu-id="21c83-147">Business need: 5</span></span>  <br/> |
|<span data-ttu-id="21c83-148">**Intune/EMS:** iOS および Android デバイスを管理します。</span><span class="sxs-lookup"><span data-stu-id="21c83-148">**Intune/EMS:** Manage iOS and Android devices.</span></span> <br/> <span data-ttu-id="21c83-149">ビジネス ニーズ:3</span><span class="sxs-lookup"><span data-stu-id="21c83-149">Business need: 3</span></span>  <br/> ||<span data-ttu-id="21c83-150">四半期末の処理のニーズに合わせて一時的なサーバーおよびストレージを追加します。</span><span class="sxs-lookup"><span data-stu-id="21c83-150">Add temporary servers and storage for end-of-quarter processing needs.</span></span>  <br/> <span data-ttu-id="21c83-151">ビジネス ニーズ:6</span><span class="sxs-lookup"><span data-stu-id="21c83-151">Business need: 6</span></span>  <br/> |
   
## <a name="see-also"></a><span data-ttu-id="21c83-152">See Also</span><span class="sxs-lookup"><span data-stu-id="21c83-152">See Also</span></span>

[<span data-ttu-id="21c83-153">Microsoft Cloud の Contoso</span><span class="sxs-lookup"><span data-stu-id="21c83-153">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="21c83-154">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="21c83-154">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="21c83-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span><span class="sxs-lookup"><span data-stu-id="21c83-155">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


