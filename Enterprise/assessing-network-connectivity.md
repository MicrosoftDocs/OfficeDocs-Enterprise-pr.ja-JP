---
title: Microsoft 365 ネットワーク接続の評価
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Microsoft 365 は、世界中のお客様がインターネット接続を使用してサービスに接続できるように設計されています。 サービスの進化に伴って、Microsoft 365 のセキュリティ、パフォーマンス、および信頼性は、インターネットを使用してサービスへの接続を確立するお客様によって改善されました。
ms.openlocfilehash: eae7e56c13ab0d0799226c834dd7d9092c8f9551
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605803"
---
# <a name="assessing-microsoft-365-network-connectivity"></a><span data-ttu-id="74ae0-104">Microsoft 365 ネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="74ae0-104">Assessing Microsoft 365 network connectivity</span></span>

<span data-ttu-id="74ae0-105">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="74ae0-105">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="74ae0-106">Microsoft 365 は、世界中のお客様がインターネット接続を使用してサービスに接続できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="74ae0-106">Microsoft 365 is designed to enable customers all over the world to connect to the service using an internet connection.</span></span> <span data-ttu-id="74ae0-107">サービスの進化に伴って、Microsoft 365 のセキュリティ、パフォーマンス、および信頼性は、インターネットを使用してサービスへの接続を確立するお客様によって改善されました。</span><span class="sxs-lookup"><span data-stu-id="74ae0-107">As the service evolves, the security, performance, and reliability of Microsoft 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="74ae0-108">Microsoft 365 の使用を計画しているお客様は、展開プロジェクトの一環として、既存および予測されるインターネット接続のニーズを評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74ae0-108">Customers planning to use Microsoft 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project.</span></span> <span data-ttu-id="74ae0-109">エンタープライズクラスの展開については、信頼性が高く、適切にサイズが変更されたインターネット接続は、Microsoft 365 の機能やシナリオを利用するうえで重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="74ae0-109">For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Microsoft 365 features and scenarios.</span></span>
  
<span data-ttu-id="74ae0-110">ネットワークの評価は、サイズと基本設定に応じて、多くの人や組織が行うことができます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-110">Network evaluations can be performed by many different people and organizations depending on your size and preferences.</span></span> <span data-ttu-id="74ae0-111">評価のネットワークスコープは、展開プロセスのどこにいるかによっても異なります。</span><span class="sxs-lookup"><span data-stu-id="74ae0-111">The network scope of the assessment can also vary depending on where you're at in your deployment process.</span></span> <span data-ttu-id="74ae0-112">ネットワーク評価を実行するために必要なことを理解するのに役立つように、ネットワーク評価ガイドを作成しました。使用可能なオプションを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-112">To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you.</span></span> <span data-ttu-id="74ae0-113">この評価では、Microsoft 365 を適切に導入できるようにするために、展開プロジェクトにどのような手順とリソースを追加する必要があるかを決定します。</span><span class="sxs-lookup"><span data-stu-id="74ae0-113">This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Microsoft 365.</span></span>
  
<span data-ttu-id="74ae0-114">包括的なネットワーク評価では、実装の詳細に加えて、ネットワーク設計の課題に対して可能なソリューションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-114">A comprehensive network assessment will provide possible solutions to networking design challenges along with implementation details.</span></span> <span data-ttu-id="74ae0-115">一部のネットワークの評価では、Microsoft 365 への最適なネットワーク接続には、小規模な構成や、既存のネットワークおよびインターネット出口インフラストラクチャの設計変更に対応できることが示されています。</span><span class="sxs-lookup"><span data-stu-id="74ae0-115">Some network assessments will show that optimal network connectivity to Microsoft 365 can be accommodated with minor configuration or design changes to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="74ae0-116">一部の評価では、Microsoft 365 へのネットワーク接続が必要になるため、ネットワークコンポーネントに追加の投資が必要になります。</span><span class="sxs-lookup"><span data-stu-id="74ae0-116">Some assessments will indicate network connectivity to Microsoft 365 will require additional investments in networking components.</span></span> <span data-ttu-id="74ae0-117">たとえば、ブランチオフィスと複数の地域地域にまたがるエンタープライズネットワークでは、Microsoft 365 へのインターネット接続をサポートするために、SD ソリューションへの投資または最適化されたルーティングインフラストラクチャが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="74ae0-117">For example, enterprise networks that span branch offices and multiple geographic regions may require investments in SD-WAN solutions or optimized routing infrastructure to support internet connectivity to Microsoft 365.</span></span> <span data-ttu-id="74ae0-118">場合によっては、Microsoft 365 へのネットワーク接続は、 [Skype For Business Online のメディア品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)などのシナリオの規制またはパフォーマンス要件の影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="74ae0-118">Occasionally an assessment will indicate network connectivity to Microsoft 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span> <span data-ttu-id="74ae0-119">これらの追加要件により、インターネット接続インフラストラクチャ、ルーティングの最適化、および特別な直接接続への投資が可能になります。</span><span class="sxs-lookup"><span data-stu-id="74ae0-119">These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>

<span data-ttu-id="74ae0-120">ネットワークの評価に役立ついくつかのリソース:</span><span class="sxs-lookup"><span data-stu-id="74ae0-120">Some resources to help you assess your network:</span></span>

- <span data-ttu-id="74ae0-121">Microsoft 365 ネットワークの概念については、「 [microsoft 365 のネットワーク接続の概要](office-365-networking-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74ae0-121">See [Microsoft 365 network connectivity overview](office-365-networking-overview.md) for conceptual information about Microsoft 365 networking.</span></span>
- <span data-ttu-id="74ae0-122">Microsoft [365 のネットワーク接続の原則](https://aka.ms/o365networkingprinciples)を参照して、microsoft 365 のトラフィックを安全に管理し、最高のパフォーマンスを得るための接続の原則について理解します。</span><span class="sxs-lookup"><span data-stu-id="74ae0-122">See [Microsoft 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Microsoft 365 traffic and getting the best possible performance.</span></span>
- <span data-ttu-id="74ae0-123">Microsoft 365 の計画、設計、展開に関する[Microsoft FastTrack](https://www.microsoft.com/fasttrack)のガイド付きサポートにサインアップします。</span><span class="sxs-lookup"><span data-stu-id="74ae0-123">Sign up for [Microsoft FastTrack](https://www.microsoft.com/fasttrack) for guided assistance with Microsoft 365 planning, design and deployment.</span></span> 
- <span data-ttu-id="74ae0-124">特定のユーザーの場所と Microsoft の365の間では、ネットワーク接続の機能向上に関する具体的なガイダンスを提供する基本的な接続テストを実行するには、以下の「 [Microsoft 365 connectivity test](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="74ae0-124">See the [Microsoft 365 connectivity test](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) section below to run basic connectivity tests that provide specific guidance about networking connectivity improvements that can be made between a given user location and Microsoft 365.</span></span>

> [!NOTE]
> <span data-ttu-id="74ae0-125">Office 365 の ExpressRoute を使用するには、Microsoft の承認が必要です。</span><span class="sxs-lookup"><span data-stu-id="74ae0-125">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="74ae0-126">Microsoft は、お客様の規制要件で直接的な接続が義務付けられている場合に限り、お客様のすべての要求を見直し、Office 365 の ExpressRoute の使用を承認します。</span><span class="sxs-lookup"><span data-stu-id="74ae0-126">Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="74ae0-127">このような要件がある場合は、テキストの抜粋と web リンクを入力してください。これは、Microsoft レビューを開始するために、 [Office 365 の ExpressRoute の要求フォーム](https://aka.ms/O365ERReview)に直接接続する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="74ae0-127">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="74ae0-128">承認されていないサブスクリプション Office 365 のルートフィルターを作成しようとすると、[エラーメッセージ](https://support.microsoft.com/kb/3181709)が表示されます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-128">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="74ae0-129">Microsoft 365 のネットワーク評価を計画する際に考慮すべき重要な点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="74ae0-129">Key points to consider when planning your network assessment for Microsoft 365:</span></span>
  
- <span data-ttu-id="74ae0-130">Microsoft 365 は、パブリックインターネット上で動作する、セキュリティで保護された、信頼性の高い高パフォーマンスのサービスです。</span><span class="sxs-lookup"><span data-stu-id="74ae0-130">Microsoft 365 is a secure, reliable, high performance service that runs over the public internet.</span></span> <span data-ttu-id="74ae0-131">弊社は、サービスのこれらの側面を強化するための投資を継続しています。</span><span class="sxs-lookup"><span data-stu-id="74ae0-131">We continue to invest to enhance these aspects of the service.</span></span> <span data-ttu-id="74ae0-132">すべての Microsoft 365 サービスは、インターネット接続経由で利用できます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-132">All Microsoft 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="74ae0-133">可用性、グローバルなリーチ、インターネットベースの接続のパフォーマンスなど、Microsoft 365 の主要な側面を継続的に最適化しています。</span><span class="sxs-lookup"><span data-stu-id="74ae0-133">We are continually optimizing core aspects of Microsoft 365 such as availability, global reach, and performance for internet based connectivity.</span></span> <span data-ttu-id="74ae0-134">たとえば、多くの Microsoft 365 サービスでは、拡張されたインターネット上のエッジノードのセットを利用します。</span><span class="sxs-lookup"><span data-stu-id="74ae0-134">For example, many Microsoft 365 services leverage an expanding set of internet facing edge nodes.</span></span> <span data-ttu-id="74ae0-135">このエッジネットワークによって、インターネット経由で接続する際に最適な類似性とパフォーマンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-135">This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="74ae0-136">Teams または Skype for Business Online の音声、ビデオ、会議の機能など、含まれるサービスのいずれかに対して Microsoft 365 の使用を検討する場合は、エンドツーエンドのネットワーク評価を完了し、 [Microsoft FastTrack](https://www.microsoft.com/fasttrack)を使用して接続要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="74ae0-136">When considering using Microsoft 365 for any of the included services such as Teams or Skype for Business Online voice, video, or meeting capabilities, customers should complete an end to end network assessment and meet connectivity requirements using [Microsoft FastTrack](https://www.microsoft.com/fasttrack).</span></span>

<span data-ttu-id="74ae0-137">Microsoft 365 を評価していて、ネットワーク評価の開始位置がわからない場合や、解決のためにサポートが必要なネットワーク設計の課題が見つかった場合は、Microsoft アカウントチームと協力してください。</span><span class="sxs-lookup"><span data-stu-id="74ae0-137">If you're evaluating Microsoft 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>

## <a name="the-microsoft-365-connectivity-test"></a><span data-ttu-id="74ae0-138">Microsoft 365 接続テスト</span><span class="sxs-lookup"><span data-stu-id="74ae0-138">The Microsoft 365 connectivity test</span></span>

<span data-ttu-id="74ae0-139">[Microsoft 365 connectivity test](https://aka.ms/netonboard)は、microsoft 365 テナントに対して基本的な接続テストを実行し、最適な microsoft 365 パフォーマンスを得るための特定のネットワーク設計の推奨事項を作成する概念 (POC) ネットワーク評価ツールです。</span><span class="sxs-lookup"><span data-stu-id="74ae0-139">The [Microsoft 365 connectivity test](https://aka.ms/netonboard) is a proof of concept (POC) network assessment tool that runs basic connectivity tests against your Microsoft 365 tenant and makes specific network design recommendations for optimal Microsoft 365 performance.</span></span> <span data-ttu-id="74ae0-140">このツールは、インターネット web 閲覧には便利ですが、Microsoft 365 などの大規模な SaaS アプリケーションのパフォーマンスに影響を与える、大規模なエンタープライズネットワーク境界の一般的な設計上の選択項目を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="74ae0-140">The tool highlights common large enterprise network perimeter design choices which are useful for Internet web browsing but impact the performance of large SaaS applications such as Microsoft 365.</span></span>

<span data-ttu-id="74ae0-141">ネットワークオンボードツールは、次の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="74ae0-141">The Network Onboarding tool does the following:</span></span>

- <span data-ttu-id="74ae0-142">場所を検出するか、テストする場所を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-142">Detects your location, or you can specify a location to test</span></span>
- <span data-ttu-id="74ae0-143">ネットワークの出口の場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="74ae0-143">Checks the location of your network egress</span></span>
- <span data-ttu-id="74ae0-144">最も近い Microsoft 365 サービスのフロントドアへのネットワークパスをテストします。</span><span class="sxs-lookup"><span data-stu-id="74ae0-144">Tests the network path to the nearest Microsoft 365 service front door</span></span>
- <span data-ttu-id="74ae0-145">プロキシサーバー、ファイアウォール、DNS に関連した境界ネットワーク設計の推奨事項を作成する、ダウンロード可能な Windows 10 アプリケーションを使用した高度なテストを提供します。</span><span class="sxs-lookup"><span data-stu-id="74ae0-145">Provides advanced tests using a downloadable Windows 10 application that makes perimeter network design recommendations related to proxy servers, firewalls, and DNS.</span></span> <span data-ttu-id="74ae0-146">このツールでは、Skype for Business Online、Microsoft Teams、SharePoint Online、Exchange Online のパフォーマンステストも実行されます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-146">The tool also runs performance tests for Skype for Business Online, Microsoft Teams, SharePoint Online and Exchange Online.</span></span>

<span data-ttu-id="74ae0-147">このツールには、基本的な接続情報を収集するブラウザベースの UI と、高度なテストを実行して追加の評価データを返す Windows 10 アプリケーションのダウンロード可能な2つのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="74ae0-147">The tool has two components: a browser-based UI that collects basic connectivity information, and a downloadable Windows 10 application that runs advanced tests and returns additional assessment data.</span></span>

<span data-ttu-id="74ae0-148">ブラウザベースのツールには、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-148">The browser-based tool displays the following information:</span></span>

- <span data-ttu-id="74ae0-149">[結果と影響] タブ</span><span class="sxs-lookup"><span data-stu-id="74ae0-149">Results and impact tab</span></span>
  - <span data-ttu-id="74ae0-150">使用中のサービスのフロントドアのマップ上の場所</span><span class="sxs-lookup"><span data-stu-id="74ae0-150">The location on a map of the in-use service front door</span></span>
  - <span data-ttu-id="74ae0-151">接続を最適化するために、他のサービスのフロントドアのマップ上にある場所</span><span class="sxs-lookup"><span data-stu-id="74ae0-151">The location on a map of other service front doors that would provide optimal connectivity</span></span>
  - <span data-ttu-id="74ae0-152">近辺の他の Microsoft 365 お客様と比較した場合の相対的なパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="74ae0-152">Relative performance compared to other Microsoft 365 customers near you</span></span>
- <span data-ttu-id="74ae0-153">[詳細とソリューション] タブ</span><span class="sxs-lookup"><span data-stu-id="74ae0-153">Details and solutions tab</span></span>
  - <span data-ttu-id="74ae0-154">市区町村および国別のユーザーの場所</span><span class="sxs-lookup"><span data-stu-id="74ae0-154">User location by city and country</span></span>
  - <span data-ttu-id="74ae0-155">市区町村、都道府県、および国別のネットワーク出口の場所</span><span class="sxs-lookup"><span data-stu-id="74ae0-155">Network egress location by city, state and country</span></span>
  - <span data-ttu-id="74ae0-156">ユーザーからネットワークの出口までの距離</span><span class="sxs-lookup"><span data-stu-id="74ae0-156">User to network egress distance</span></span>
  - <span data-ttu-id="74ae0-157">Microsoft 365 Exchange Online サービスのフロントドアの場所</span><span class="sxs-lookup"><span data-stu-id="74ae0-157">Microsoft 365 Exchange Online service front door location</span></span>
  - <span data-ttu-id="74ae0-158">ユーザーの場所に最適な Microsoft 365 Exchange Online サービスのフロントドア</span><span class="sxs-lookup"><span data-stu-id="74ae0-158">Optimal Microsoft 365 Exchange Online service front door(s) for user location</span></span>
  - <span data-ttu-id="74ae0-159">優れたパフォーマンスを備えた、メトロエリア内のお客様</span><span class="sxs-lookup"><span data-stu-id="74ae0-159">Customers in your metro area with better performance</span></span>

<span data-ttu-id="74ae0-160">[高度なテスト] ダウンロード可能なアプリケーションは、次の追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="74ae0-160">The Advanced Tests downloadable application provides the following additional information:</span></span>

- <span data-ttu-id="74ae0-161">[詳細とソリューション] タブ (追加)</span><span class="sxs-lookup"><span data-stu-id="74ae0-161">Details and solutions tab (appended)</span></span>
  - <span data-ttu-id="74ae0-162">ユーザーの既定のゲートウェイ</span><span class="sxs-lookup"><span data-stu-id="74ae0-162">User's default gateway</span></span>
  - <span data-ttu-id="74ae0-163">クライアント DNS サーバー</span><span class="sxs-lookup"><span data-stu-id="74ae0-163">Client DNS Server</span></span>
  - <span data-ttu-id="74ae0-164">クライアント DNS の再帰的なリゾルバー</span><span class="sxs-lookup"><span data-stu-id="74ae0-164">Client DNS Recursive Resolver</span></span>
  - <span data-ttu-id="74ae0-165">Exchange Online の DNS サーバー</span><span class="sxs-lookup"><span data-stu-id="74ae0-165">Exchange Online DNS server</span></span>
  - <span data-ttu-id="74ae0-166">SharePoint Online の DNS サーバー</span><span class="sxs-lookup"><span data-stu-id="74ae0-166">SharePoint Online DNS server</span></span>
  - <span data-ttu-id="74ae0-167">プロキシサーバーの識別</span><span class="sxs-lookup"><span data-stu-id="74ae0-167">Proxy server identification</span></span>
  - <span data-ttu-id="74ae0-168">メディアの接続チェック</span><span class="sxs-lookup"><span data-stu-id="74ae0-168">Media connectivity check</span></span>
  - <span data-ttu-id="74ae0-169">メディア品質のパケット損失</span><span class="sxs-lookup"><span data-stu-id="74ae0-169">Media quality packet loss</span></span>
  - <span data-ttu-id="74ae0-170">メディア品質の遅延</span><span class="sxs-lookup"><span data-stu-id="74ae0-170">Media quality latency</span></span>
  - <span data-ttu-id="74ae0-171">メディア品質のジッター</span><span class="sxs-lookup"><span data-stu-id="74ae0-171">Media quality jitter</span></span>
  - <span data-ttu-id="74ae0-172">メディア品質のパケットの順序変更</span><span class="sxs-lookup"><span data-stu-id="74ae0-172">Media quality packet reorder</span></span>
- <span data-ttu-id="74ae0-173">複数の機能固有のエンドポイントへの接続テスト</span><span class="sxs-lookup"><span data-stu-id="74ae0-173">Connectivity tests to multiple feature-specific endpoints</span></span>
- <span data-ttu-id="74ae0-174">Exchange Online、SharePoint Online、Teams サービスの tracert および待機時間データを含むネットワークパス診断</span><span class="sxs-lookup"><span data-stu-id="74ae0-174">Network path diagnostics that include tracert and latency data for the Exchange Online, SharePoint Online and Teams services</span></span>

<span data-ttu-id="74ae0-175">Microsoft の365接続テストに関する情報を参照して、[新しいネットワーク設計に関する推奨事項のブログ投稿を使用して、更新された microsoft 365 接続テスト POC](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130)にフィードバックを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-175">You can read about the Microsoft 365 connectivity test and provide feedback at the [Updated Microsoft 365 connectivity test POC with new network design recommendations](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) blog post.</span></span> <span data-ttu-id="74ae0-176">このツールおよびその他の Microsoft 365 ネットワークの更新プログラムに関する情報は、 [Office 365 のネットワーク](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)のブログに投稿されます。</span><span class="sxs-lookup"><span data-stu-id="74ae0-176">Information about future updates to this tool and other Microsoft 365 networking updates will be posted to the [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) blog.</span></span>
  
<span data-ttu-id="74ae0-177">次の短いリンクを使用して、に戻ることができ[ https://aka.ms/o365networkconnectivity ます。](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="74ae0-177">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="related-topics"></a><span data-ttu-id="74ae0-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="74ae0-178">Related topics</span></span>

[<span data-ttu-id="74ae0-179">Microsoft 365 ネットワーク接続の概要</span><span class="sxs-lookup"><span data-stu-id="74ae0-179">Microsoft 365 Network Connectivity Overview</span></span>](office-365-networking-overview.md)

[<span data-ttu-id="74ae0-180">Microsoft 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="74ae0-180">Microsoft 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)

[<span data-ttu-id="74ae0-181">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="74ae0-181">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="74ae0-182">Office 365 の URL および IP アドレスの範囲</span><span class="sxs-lookup"><span data-stu-id="74ae0-182">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="74ae0-183">Office 365 IP アドレスと URL の Web サービス </span><span class="sxs-lookup"><span data-stu-id="74ae0-183">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="74ae0-184">Microsoft 365 のネットワークとパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="74ae0-184">Microsoft 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="74ae0-185">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="74ae0-185">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
