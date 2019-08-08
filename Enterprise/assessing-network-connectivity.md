---
title: Office 365 のネットワーク接続の評価
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/7/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 は、世界中のお客様がインターネット接続を使用してサービスに接続できるように設計されています。 サービスの進化に伴って、Office 365 のセキュリティ、パフォーマンス、および信頼性は、インターネットを使用してサービスへの接続を確立するお客様によって改善されています。
ms.openlocfilehash: 884c4c0d510de55da4125a3e3b80b4bd869ec697
ms.sourcegitcommit: c207aafc126a495e700552796ed89da3de254910
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2019
ms.locfileid: "36233427"
---
# <a name="assessing-office-365-network-connectivity"></a><span data-ttu-id="e1f52-104">Office 365 のネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="e1f52-104">Assessing Office 365 network connectivity</span></span>

<span data-ttu-id="e1f52-105">Office 365 は、世界中のお客様がインターネット接続を使用してサービスに接続できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e1f52-105">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection.</span></span> <span data-ttu-id="e1f52-106">サービスの進化に伴って、Office 365 のセキュリティ、パフォーマンス、および信頼性は、インターネットを使用してサービスへの接続を確立するお客様によって改善されています。</span><span class="sxs-lookup"><span data-stu-id="e1f52-106">As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="e1f52-107">Office 365 の使用を計画しているお客様は、展開プロジェクトの一環として、既存および予測されるインターネット接続のニーズを評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1f52-107">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project.</span></span> <span data-ttu-id="e1f52-108">エンタープライズクラスの展開の場合は、信頼性が高く、適切なサイズのインターネット接続は、Office 365 の機能とシナリオの重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="e1f52-108">For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="e1f52-109">ネットワークの評価は、サイズと基本設定に応じて、多くの人や組織が行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-109">Network evaluations can be performed by many different people and organizations depending on your size and preferences.</span></span> <span data-ttu-id="e1f52-110">評価のネットワークスコープは、展開プロセスのどこにいるかによっても異なります。</span><span class="sxs-lookup"><span data-stu-id="e1f52-110">The network scope of the assessment can also vary depending on where you're at in your deployment process.</span></span> <span data-ttu-id="e1f52-111">ネットワーク評価を実行するために必要なことを理解するのに役立つように、ネットワーク評価ガイドを作成しました。使用可能なオプションを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-111">To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you.</span></span> <span data-ttu-id="e1f52-112">この評価では、Office 365 を正常に導入できるようにするために、展開プロジェクトにどのような手順とリソースを追加する必要があるかを決定します。</span><span class="sxs-lookup"><span data-stu-id="e1f52-112">This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="e1f52-113">包括的なネットワーク評価では、実装の詳細に加えて、ネットワーク設計の課題に対して可能なソリューションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-113">A comprehensive network assessment will provide possible solutions to networking design challenges along with implementation details.</span></span> <span data-ttu-id="e1f52-114">ネットワークの評価によっては、Office 365 への最適なネットワーク接続には、小規模な構成や、既存のネットワークとインターネットの出口インフラストラクチャに対するデザイン変更が対応できることが示されています。</span><span class="sxs-lookup"><span data-stu-id="e1f52-114">Some network assessments will show that optimal network connectivity to Office 365 can be accommodated with minor configuration or design changes to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="e1f52-115">一部の評価では、Office 365 へのネットワーク接続が必要になります。これには、ネットワークコンポーネントへの追加の投資が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e1f52-115">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components.</span></span> <span data-ttu-id="e1f52-116">たとえば、ブランチオフィスと複数の地域地域にまたがるエンタープライズネットワークでは、Office 365 へのインターネット接続をサポートするために、SD ソリューションへの投資または最適化されたルーティングインフラストラクチャが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="e1f52-116">For example, enterprise networks that span branch offices and multiple geographic regions may require investments in SD-WAN solutions or optimized routing infrastructure to support internet connectivity to Office 365.</span></span> <span data-ttu-id="e1f52-117">場合によっては、Office 365 へのネットワーク接続が表示されることがあります。 [Skype For Business Online メディア品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)などのシナリオの規制またはパフォーマンス要件の影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e1f52-117">Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span> <span data-ttu-id="e1f52-118">これらの追加要件により、インターネット接続インフラストラクチャ、ルーティングの最適化、および特別な直接接続への投資が可能になります。</span><span class="sxs-lookup"><span data-stu-id="e1f52-118">These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>

<span data-ttu-id="e1f52-119">ネットワークの評価に役立ついくつかのリソース:</span><span class="sxs-lookup"><span data-stu-id="e1f52-119">Some resources to help you assess your network:</span></span>

- <span data-ttu-id="e1f52-120">Office 365 ネットワークの概念については、「 [office 365 のネットワーク接続の概要](office-365-networking-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1f52-120">See [Office 365 network connectivity overview](office-365-networking-overview.md) for conceptual information about Office 365 networking.</span></span>
- <span data-ttu-id="e1f52-121">Office 365 のトラフィックを安全に管理し、最適なパフォーマンスを得るための接続の原則については、「 [office 365 のネットワーク接続の原則](https://aka.ms/o365networkingprinciples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1f52-121">See [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span>
- <span data-ttu-id="e1f52-122">Office 365 の計画、設計、展開に関する[Microsoft FastTrack](https://www.microsoft.com/en-us/fasttrack)のガイド付きサポートにサインアップします。</span><span class="sxs-lookup"><span data-stu-id="e1f52-122">Sign up for [Microsoft FastTrack](https://www.microsoft.com/en-us/fasttrack) for guided assistance with Office 365 planning, design and deployment.</span></span> 
- <span data-ttu-id="e1f52-123">特定のユーザーの場所と Office 365 の間で、ネットワーク接続の機能向上に関する具体的なガイダンスを提供する基本的な接続テストを実行するには、以下の「 [Office 365 ネットワークオンボードツール](assessing-network-connectivity.md#the-office-365-network-onboarding-tool)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1f52-123">See the [Office 365 Network Onboarding tool](assessing-network-connectivity.md#the-office-365-network-onboarding-tool) section below to run basic connectivity tests that provide specific guidance about networking connectivity improvements that can be made between a given user location and Office 365.</span></span>

> [!NOTE]
> <span data-ttu-id="e1f52-124">Office 365 の ExpressRoute を使用するには、Microsoft の承認が必要です。</span><span class="sxs-lookup"><span data-stu-id="e1f52-124">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="e1f52-125">Microsoft は、お客様の規制要件で直接的な接続が義務付けられている場合に限り、お客様のすべての要求を見直し、Office 365 の ExpressRoute の使用を承認します。</span><span class="sxs-lookup"><span data-stu-id="e1f52-125">Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="e1f52-126">このような要件がある場合は、テキストの抜粋と web リンクを入力してください。これは、Microsoft レビューを開始するために、 [Office 365 の ExpressRoute の要求フォーム](https://aka.ms/O365ERReview)に直接接続する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e1f52-126">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="e1f52-127">承認されていないサブスクリプション Office 365 のルートフィルターを作成しようとすると、[エラーメッセージ](https://support.microsoft.com/kb/3181709)が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-127">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="e1f52-128">Office 365 のネットワーク評価を計画する際に考慮すべき重要な点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e1f52-128">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="e1f52-129">Office 365 は、パブリックインターネット上で動作する、セキュリティで保護された、信頼性の高い高パフォーマンスのサービスです。</span><span class="sxs-lookup"><span data-stu-id="e1f52-129">Office 365 is a secure, reliable, high performance service that runs over the public internet.</span></span> <span data-ttu-id="e1f52-130">弊社は、サービスのこれらの側面を強化するための投資を継続しています。</span><span class="sxs-lookup"><span data-stu-id="e1f52-130">We continue to invest to enhance these aspects of the service.</span></span> <span data-ttu-id="e1f52-131">すべての Office 365 サービスは、インターネット接続経由で利用できます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-131">All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="e1f52-132">Microsoft は、可用性、グローバルなリーチ、およびインターネットベースの接続のパフォーマンスなど、Office 365 のコア要素を継続的に最適化しています。</span><span class="sxs-lookup"><span data-stu-id="e1f52-132">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity.</span></span> <span data-ttu-id="e1f52-133">たとえば、多くの Office 365 サービスでは、拡張されたインターネット上のエッジノードのセットが利用されます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-133">For example, many Office 365 services leverage an expanding set of internet facing edge nodes.</span></span> <span data-ttu-id="e1f52-134">このエッジネットワークによって、インターネット経由で接続する際に最適な類似性とパフォーマンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-134">This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="e1f52-135">Teams または Skype for Business Online の音声、ビデオ、会議の機能など、含まれるサービスのいずれかに Office 365 の使用を検討する場合、エンドツーエンドのネットワーク評価を完了し、Microsoft を使用して接続要件を満たす必要があります。 [FastTrack](https://www.microsoft.com/en-us/fasttrack)。</span><span class="sxs-lookup"><span data-stu-id="e1f52-135">When considering using Office 365 for any of the included services such as Teams or Skype for Business Online voice, video, or meeting capabilities, customers should complete an end to end network assessment and meet connectivity requirements using [Microsoft FastTrack](https://www.microsoft.com/en-us/fasttrack).</span></span>

<span data-ttu-id="e1f52-136">Office 365 を評価していて、ネットワーク評価の開始位置がわからない場合や、解決のためにサポートが必要なネットワーク設計の課題が見つかった場合は、Microsoft アカウントチームと協力してください。</span><span class="sxs-lookup"><span data-stu-id="e1f52-136">If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>

## <a name="the-office-365-network-onboarding-tool"></a><span data-ttu-id="e1f52-137">Office 365 ネットワークオンボードツール</span><span class="sxs-lookup"><span data-stu-id="e1f52-137">The Office 365 Network Onboarding tool</span></span>

<span data-ttu-id="e1f52-138">[Office 365 ネットワークオンボードツール](https://aka.ms/netonboard)は、office 365 テナントに対して基本的な接続テストを実行し、最適な office 365 パフォーマンスを得るための特定のネットワーク設計の推奨事項を実行する概念実証 (POC) ネットワーク評価ツールです。</span><span class="sxs-lookup"><span data-stu-id="e1f52-138">The [Office 365 Network Onboarding tool](https://aka.ms/netonboard) is a proof of concept (POC) network assessment tool that runs basic connectivity tests against your Office 365 tenant and makes specific network design recommendations for optimal Office 365 performance.</span></span> <span data-ttu-id="e1f52-139">このツールは、インターネット web ブラウジングに便利で、Office 365 などの大規模な SaaS アプリケーションのパフォーマンスに影響を与える大規模なエンタープライズネットワーク境界の一般的な設計上の選択項目を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="e1f52-139">The tool highlights common large enterprise network perimeter design choices which are useful for Internet web browsing but impact the performance of large SaaS applications such as Office 365.</span></span>

<span data-ttu-id="e1f52-140">ネットワークオンボードツールは、次の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="e1f52-140">The Network Onboarding tool does the following:</span></span>

- <span data-ttu-id="e1f52-141">場所を検出するか、テストする場所を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-141">Detects your location, or you can specify a location to test</span></span>
- <span data-ttu-id="e1f52-142">ネットワークの出口の場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="e1f52-142">Checks the location of your network egress</span></span>
- <span data-ttu-id="e1f52-143">最も近い Office 365 サービスのフロントドアへのネットワークパスをテストします。</span><span class="sxs-lookup"><span data-stu-id="e1f52-143">Tests the network path to the nearest Office 365 service front door</span></span>
- <span data-ttu-id="e1f52-144">プロキシサーバー、ファイアウォール、DNS に関連した境界ネットワーク設計の推奨事項を作成する、ダウンロード可能な Windows 10 アプリケーションを使用した高度なテストを提供します。</span><span class="sxs-lookup"><span data-stu-id="e1f52-144">Provides advanced tests using a downloadable Windows 10 application that makes perimeter network design recommendations related to proxy servers, firewalls, and DNS.</span></span> <span data-ttu-id="e1f52-145">このツールでは、Skype for Business Online、Microsoft Teams、SharePoint Online、Exchange Online のパフォーマンステストも実行されます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-145">The tool also runs performance tests for Skype for Business Online, Microsoft Teams, SharePoint Online and Exchange Online.</span></span>

<span data-ttu-id="e1f52-146">このツールには、基本的な接続情報を収集するブラウザベースの UI と、高度なテストを実行して追加の評価データを返す Windows 10 アプリケーションのダウンロード可能な2つのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="e1f52-146">The tool has two components: a browser-based UI that collects basic connectivity information, and a downloadable Windows 10 application that runs advanced tests and returns additional assessment data.</span></span>

<span data-ttu-id="e1f52-147">ブラウザベースのツールには、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-147">The browser-based tool displays the following information:</span></span>

- <span data-ttu-id="e1f52-148">[結果と影響] タブ</span><span class="sxs-lookup"><span data-stu-id="e1f52-148">Results and impact tab</span></span>
  - <span data-ttu-id="e1f52-149">使用中のサービスのフロントドアのマップ上の場所</span><span class="sxs-lookup"><span data-stu-id="e1f52-149">The location on a map of the in-use service front door</span></span>
  - <span data-ttu-id="e1f52-150">接続を最適化するために、他のサービスのフロントドアのマップ上にある場所</span><span class="sxs-lookup"><span data-stu-id="e1f52-150">The location on a map of other service front doors that would provide optimal connectivity</span></span>
  - <span data-ttu-id="e1f52-151">近辺の他の Office 365 のお客様と比較した場合の相対的なパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="e1f52-151">Relative performance compared to other Office 365 customers near you</span></span>
- <span data-ttu-id="e1f52-152">[詳細とソリューション] タブ</span><span class="sxs-lookup"><span data-stu-id="e1f52-152">Details and solutions tab</span></span>
  - <span data-ttu-id="e1f52-153">市区町村および国別のユーザーの場所</span><span class="sxs-lookup"><span data-stu-id="e1f52-153">User location by city and country</span></span>
  - <span data-ttu-id="e1f52-154">市区町村、都道府県、および国別のネットワーク出口の場所</span><span class="sxs-lookup"><span data-stu-id="e1f52-154">Network egress location by city, state and country</span></span>
  - <span data-ttu-id="e1f52-155">ユーザーからネットワークの出口までの距離</span><span class="sxs-lookup"><span data-stu-id="e1f52-155">User to network egress distance</span></span>
  - <span data-ttu-id="e1f52-156">Office 365 Exchange Online サービスのフロントドアの場所</span><span class="sxs-lookup"><span data-stu-id="e1f52-156">Office 365 Exchange Online service front door location</span></span>
  - <span data-ttu-id="e1f52-157">ユーザーの場所に最適な Office 365 Exchange Online サービスのフロントドア</span><span class="sxs-lookup"><span data-stu-id="e1f52-157">Optimal Office 365 Exchange Online service front door(s) for user location</span></span>
  - <span data-ttu-id="e1f52-158">優れたパフォーマンスを備えた、メトロエリア内のお客様</span><span class="sxs-lookup"><span data-stu-id="e1f52-158">Customers in your metro area with better performance</span></span>

<span data-ttu-id="e1f52-159">[高度なテスト] ダウンロード可能なアプリケーションは、次の追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e1f52-159">The Advanced Tests downloadable application provides the following additional information:</span></span>

- <span data-ttu-id="e1f52-160">[詳細とソリューション] タブ (追加)</span><span class="sxs-lookup"><span data-stu-id="e1f52-160">Details and solutions tab (appended)</span></span>
  - <span data-ttu-id="e1f52-161">ユーザーの既定のゲートウェイ</span><span class="sxs-lookup"><span data-stu-id="e1f52-161">User's default gateway</span></span>
  - <span data-ttu-id="e1f52-162">クライアント DNS サーバー</span><span class="sxs-lookup"><span data-stu-id="e1f52-162">Client DNS Server</span></span>
  - <span data-ttu-id="e1f52-163">クライアント DNS の再帰的なリゾルバー</span><span class="sxs-lookup"><span data-stu-id="e1f52-163">Client DNS Recursive Resolver</span></span>
  - <span data-ttu-id="e1f52-164">Exchange Online の DNS サーバー</span><span class="sxs-lookup"><span data-stu-id="e1f52-164">Exchange Online DNS server</span></span>
  - <span data-ttu-id="e1f52-165">SharePoint Online の DNS サーバー</span><span class="sxs-lookup"><span data-stu-id="e1f52-165">SharePoint Online DNS server</span></span>
  - <span data-ttu-id="e1f52-166">プロキシサーバーの識別</span><span class="sxs-lookup"><span data-stu-id="e1f52-166">Proxy server identification</span></span>
  - <span data-ttu-id="e1f52-167">メディアの接続チェック</span><span class="sxs-lookup"><span data-stu-id="e1f52-167">Media connectivity check</span></span>
  - <span data-ttu-id="e1f52-168">メディア品質のパケット損失</span><span class="sxs-lookup"><span data-stu-id="e1f52-168">Media quality packet loss</span></span>
  - <span data-ttu-id="e1f52-169">メディア品質の遅延</span><span class="sxs-lookup"><span data-stu-id="e1f52-169">Media quality latency</span></span>
  - <span data-ttu-id="e1f52-170">メディア品質のジッター</span><span class="sxs-lookup"><span data-stu-id="e1f52-170">Media quality jitter</span></span>
  - <span data-ttu-id="e1f52-171">メディア品質のパケットの順序変更</span><span class="sxs-lookup"><span data-stu-id="e1f52-171">Media quality packet reorder</span></span>
- <span data-ttu-id="e1f52-172">複数の機能固有のエンドポイントへの接続テスト</span><span class="sxs-lookup"><span data-stu-id="e1f52-172">Connectivity tests to multiple feature-specific endpoints</span></span>
- <span data-ttu-id="e1f52-173">Exchange Online、SharePoint Online、Teams サービスの tracert および待機時間データを含むネットワークパス診断</span><span class="sxs-lookup"><span data-stu-id="e1f52-173">Network path diagnostics that include tracert and latency data for the Exchange Online, SharePoint Online and Teams services</span></span>

<span data-ttu-id="e1f52-174">Office 365 ネットワークオンボードツールに関する情報を参照して、[新しいネットワーク設計の推奨事項に関するブログ投稿を使用して、更新された office 365 ネットワークオンボードツールの POC](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130)にフィードバックを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="e1f52-174">You can read about the Office 365 Network Onboarding tool and provide feedback at the [Updated Office 365 Network Onboarding Tool POC with new network design recommendations](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) blog post.</span></span> <span data-ttu-id="e1f52-175">このツールおよびその他の Office 365 ネットワーク更新プログラムに関する今後の更新プログラムについては、「 [office 365 のネットワーク](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)ブログ」に掲載されています。</span><span class="sxs-lookup"><span data-stu-id="e1f52-175">Information about future updates to this tool and other Office 365 networking updates will be posted to the [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) blog.</span></span>
  
<span data-ttu-id="e1f52-176">次の短いリンクを使用して、に戻ることができます。 [ https://aka.ms/o365networkconnectivity](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="e1f52-176">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e1f52-177">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1f52-177">See also</span></span>

[<span data-ttu-id="e1f52-178">Office 365 のネットワーク接続の概要</span><span class="sxs-lookup"><span data-stu-id="e1f52-178">Office 365 Network Connectivity Overview</span></span>](office-365-networking-overview.md)

[<span data-ttu-id="e1f52-179">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="e1f52-179">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)

[<span data-ttu-id="e1f52-180">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="e1f52-180">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="e1f52-181">Office 365 の URL と IP アドレスの範囲</span><span class="sxs-lookup"><span data-stu-id="e1f52-181">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="e1f52-182">Office 365 IP アドレスと URL の Web サービス </span><span class="sxs-lookup"><span data-stu-id="e1f52-182">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="e1f52-183">Office 365 のネットワークとパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="e1f52-183">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
