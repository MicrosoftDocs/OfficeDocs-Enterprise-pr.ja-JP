---
title: Office 365 のネットワーク接続の評価
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
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
ms.openlocfilehash: 3ea80ddccaf9fabbe158a10f0af1d35dbf3a9889
ms.sourcegitcommit: 0449c6f854c682719cac1bd0d086f2e3b20078b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "34724827"
---
# <a name="assessing-office-365-network-connectivity"></a><span data-ttu-id="2610e-104">Office 365 のネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="2610e-104">Assessing Office 365 network connectivity</span></span>

<span data-ttu-id="2610e-105">Office 365 は、世界中のお客様がインターネット接続を使用してサービスに接続できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="2610e-105">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection.</span></span> <span data-ttu-id="2610e-106">サービスの進化に伴って、Office 365 のセキュリティ、パフォーマンス、および信頼性は、インターネットを使用してサービスへの接続を確立するお客様によって改善されています。</span><span class="sxs-lookup"><span data-stu-id="2610e-106">As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="2610e-107">Office 365 の使用を計画しているお客様は、展開プロジェクトの一環として、既存および予測されるインターネット接続のニーズを評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2610e-107">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project.</span></span> <span data-ttu-id="2610e-108">エンタープライズクラスの展開の場合は、信頼性が高く、適切なサイズのインターネット接続は、Office 365 の機能とシナリオの重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="2610e-108">For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="2610e-109">ネットワークの評価は、サイズと基本設定に応じて、多くの人や組織が行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2610e-109">Network evaluations can be performed by many different people and organizations depending on your size and preferences.</span></span> <span data-ttu-id="2610e-110">評価のネットワークスコープは、展開プロセスのどこにいるかによっても異なります。</span><span class="sxs-lookup"><span data-stu-id="2610e-110">The network scope of the assessment can also vary depending on where you're at in your deployment process.</span></span> <span data-ttu-id="2610e-111">ネットワーク評価を実行するために必要なことを理解するのに役立つように、ネットワーク評価ガイドを作成しました。使用可能なオプションを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2610e-111">To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you.</span></span> <span data-ttu-id="2610e-112">この評価では、Office 365 を正常に導入できるようにするために、展開プロジェクトにどのような手順とリソースを追加する必要があるかを決定します。</span><span class="sxs-lookup"><span data-stu-id="2610e-112">This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="2610e-113">[Skype Operations Framework](https://www.skypeoperationsframework.com/)で規定されているような包括的なネットワーク評価は、実装の詳細に加えて、ネットワーク設計の課題に対するソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="2610e-113">A comprehensive network assessment, like those prescribed in the [Skype Operations Framework](https://www.skypeoperationsframework.com/) will provide possible solutions to networking design challenges along with implementation details.</span></span> <span data-ttu-id="2610e-114">ほとんどのネットワーク評価では、Office 365 へのネットワーク接続が可能であることを示しています。これは、小規模な構成や、既存のネットワークとインターネットの出口インフラストラクチャに[対する設計の変更](https://aka.ms/manageo365endpoints)に対応できます。</span><span class="sxs-lookup"><span data-stu-id="2610e-114">Most network assessments will indicate network connectivity to Office 365 can be accommodated with [minor configuration or design changes](https://aka.ms/manageo365endpoints) to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="2610e-115">一部の評価では、Office 365 へのネットワーク接続が必要になります。これには、ネットワークコンポーネントへの追加の投資が必要になります。</span><span class="sxs-lookup"><span data-stu-id="2610e-115">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components.</span></span> <span data-ttu-id="2610e-116">たとえば、WAN 帯域幅への投資、または Office 365 へのインターネット接続をサポートするための最適化されたルーティングインフラストラクチャ。</span><span class="sxs-lookup"><span data-stu-id="2610e-116">For example, investments in WAN bandwidth or optimized routing infrastructure to support internet connectivity to Office 365.</span></span> <span data-ttu-id="2610e-117">場合によっては、Office 365 へのネットワーク接続が表示されることがあります。 [Skype For Business Online メディア品質](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)などのシナリオの規制またはパフォーマンス要件の影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2610e-117">Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span> <span data-ttu-id="2610e-118">これらの追加要件により、インターネット接続インフラストラクチャ、ルーティングの最適化、および特別な直接接続への投資が可能になります。</span><span class="sxs-lookup"><span data-stu-id="2610e-118">These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2610e-119">Office 365 の ExpressRoute を使用するには、Microsoft の承認が必要です。</span><span class="sxs-lookup"><span data-stu-id="2610e-119">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="2610e-120">Microsoft は、お客様の規制要件で直接的な接続が義務付けられている場合に限り、お客様のすべての要求を見直し、Office 365 の ExpressRoute の使用を承認します。</span><span class="sxs-lookup"><span data-stu-id="2610e-120">Microsoft reviews every customer request and only authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="2610e-121">このような要件がある場合は、テキストの抜粋と web リンクを入力してください。これは、Microsoft レビューを開始するために、 [Office 365 の ExpressRoute の要求フォーム](https://aka.ms/O365ERReview)に直接接続する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2610e-121">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="2610e-122">承認されていないサブスクリプション Office 365 のルートフィルターを作成しようとすると、[エラーメッセージ](https://support.microsoft.com/kb/3181709)が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2610e-122">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="2610e-123">Office 365 のネットワーク評価を計画する際に考慮すべき重要な点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2610e-123">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="2610e-124">Office 365 は、パブリックインターネット上で動作する、セキュリティで保護された、信頼性の高い高パフォーマンスのサービスです。</span><span class="sxs-lookup"><span data-stu-id="2610e-124">Office 365 is a secure, reliable, high performance service that runs over the public internet.</span></span> <span data-ttu-id="2610e-125">弊社は、サービスのこれらの側面を強化するための投資を継続しています。</span><span class="sxs-lookup"><span data-stu-id="2610e-125">We continue to invest to enhance these aspects of the service.</span></span> <span data-ttu-id="2610e-126">すべての Office 365 サービスは、インターネット接続経由で利用できます。</span><span class="sxs-lookup"><span data-stu-id="2610e-126">All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="2610e-127">Microsoft は、可用性、グローバルなリーチ、およびインターネットベースの接続のパフォーマンスなど、Office 365 のコア要素を継続的に最適化しています。</span><span class="sxs-lookup"><span data-stu-id="2610e-127">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity.</span></span> <span data-ttu-id="2610e-128">たとえば、多くの Office 365 サービスでは、拡張されたインターネット上のエッジノードのセットが利用されます。</span><span class="sxs-lookup"><span data-stu-id="2610e-128">For example, many Office 365 services leverage an expanding set of internet facing edge nodes.</span></span> <span data-ttu-id="2610e-129">このエッジネットワークによって、インターネット経由で接続する際に最適な類似性とパフォーマンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="2610e-129">This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="2610e-130">Skype for Business Online の音声、ビデオ、会議の機能など、含まれるサービスのいずれかに Office 365 の使用を検討する場合、お客様は、Skype Operations Framework を使用してエンドツーエンドのネットワーク評価を完了し、要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="2610e-130">When considering using Office 365 for any of the included services such as Skype for Business Online voice, video, or meeting capabilities, customers must complete an end to end network assessment and meet requirements using our Skype Operations Framework.</span></span> <span data-ttu-id="2610e-131">これらのお客様には、ExpressRoute を含む、クラウド接続の特定の要件を満たすためのいくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="2610e-131">These customers will have several options to meet specific requirements for cloud connectivity, including ExpressRoute.</span></span>

<span data-ttu-id="2610e-132">Microsoft [Office 365 のネットワークパフォーマンスを最適化](https://msdn.microsoft.com/en-us/library/mt450488.aspx)する microsoft のケーススタディを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2610e-132">Have a look at Microsoft's case study [Optimizing network performance for Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx).</span></span> <span data-ttu-id="2610e-133">Office 365 を評価していて、ネットワーク評価の開始位置がわからない場合や、解決のためにサポートが必要なネットワーク設計の課題が見つかった場合は、Microsoft アカウントチームと協力してください。</span><span class="sxs-lookup"><span data-stu-id="2610e-133">If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>
  
<span data-ttu-id="2610e-134">また、「 [office 365 のネットワーク接続の原則](https://aka.ms/o365networkingprinciples)」を参照して、office 365 トラフィックを安全に管理し、最適なパフォーマンスを得るための接続の原則について理解します。</span><span class="sxs-lookup"><span data-stu-id="2610e-134">Also, read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.</span></span> <span data-ttu-id="2610e-135">この記事は、Office 365 ネットワーク接続を安全に最適化するための最新のガイダンスを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2610e-135">This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span>

## <a name="the-office-365-network-onboarding-tool"></a><span data-ttu-id="2610e-136">Office 365 ネットワークオンボードツール</span><span class="sxs-lookup"><span data-stu-id="2610e-136">The Office 365 Network Onboarding tool</span></span>

<span data-ttu-id="2610e-137">新しい概念実証 (POC) ツールである[office 365 ネットワークオンボードツール](https://aka.ms/netonboard)を使用して、特定のユーザーの場所と Office 365 の間で、ネットワーク接続の向上に関する具体的なガイダンスを提供する基本的な接続テストを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="2610e-137">You can use the [Office 365 Network Onboarding tool](https://aka.ms/netonboard), a new proof of concept (POC) tool, to run basic connectivity tests that provide specific guidance about networking connectivity improvements that can be made between a given user location and Office 365.</span></span>

<span data-ttu-id="2610e-138">ネットワークオンボードツールは、次の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="2610e-138">The Network Onboarding tool does the following:</span></span>

- <span data-ttu-id="2610e-139">場所を検出するか、テストする場所を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="2610e-139">Detects your location, or you can specify a location to test</span></span>
- <span data-ttu-id="2610e-140">ネットワークの出口の場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="2610e-140">Checks the location of your network egress</span></span>
- <span data-ttu-id="2610e-141">最も近い Office 365 サービスのフロントドアへのネットワークパスをテストします。</span><span class="sxs-lookup"><span data-stu-id="2610e-141">Tests the network path to the nearest Office 365 service front door</span></span>

<span data-ttu-id="2610e-142">このツールには、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2610e-142">The tool displays the following information:</span></span>

- <span data-ttu-id="2610e-143">[結果と影響] タブ</span><span class="sxs-lookup"><span data-stu-id="2610e-143">Results and impact tab</span></span>
  - <span data-ttu-id="2610e-144">使用中のサービスのフロントドアのマップ上の場所</span><span class="sxs-lookup"><span data-stu-id="2610e-144">The location on a map of the in-use service front door</span></span>
  - <span data-ttu-id="2610e-145">接続を最適化するために、他のサービスのフロントドアのマップ上にある場所</span><span class="sxs-lookup"><span data-stu-id="2610e-145">The location on a map of other service front doors that would provide optimal connectivity</span></span>
  - <span data-ttu-id="2610e-146">近辺の他の Office 365 のお客様と比較した場合の相対的なパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="2610e-146">Relative performance compared to other Office 365 customers near you</span></span>
- <span data-ttu-id="2610e-147">[詳細とソリューション] タブ</span><span class="sxs-lookup"><span data-stu-id="2610e-147">Details and solutions tab</span></span>
  - <span data-ttu-id="2610e-148">市区町村および国別のユーザーの場所</span><span class="sxs-lookup"><span data-stu-id="2610e-148">User location by city and country</span></span>
  - <span data-ttu-id="2610e-149">市区町村、都道府県、および国別のネットワーク出口の場所</span><span class="sxs-lookup"><span data-stu-id="2610e-149">Network egress location by city, state and country</span></span>
  - <span data-ttu-id="2610e-150">ユーザーからネットワークの出口までの距離</span><span class="sxs-lookup"><span data-stu-id="2610e-150">User to network egress distance</span></span>
  - <span data-ttu-id="2610e-151">Office 365 Exchange Online サービスのフロントドアの場所</span><span class="sxs-lookup"><span data-stu-id="2610e-151">Office 365 Exchange Online service front door location</span></span>
  - <span data-ttu-id="2610e-152">ユーザーの場所に最適な Office 365 Exchange Online サービスのフロントドア</span><span class="sxs-lookup"><span data-stu-id="2610e-152">Optimal Office 365 Exchange Online service front door(s) for user location</span></span>
  - <span data-ttu-id="2610e-153">優れたパフォーマンスを備えた、メトロエリア内のお客様</span><span class="sxs-lookup"><span data-stu-id="2610e-153">Customers in your metro area with better performance</span></span>

<span data-ttu-id="2610e-154">Office 365 ネットワークオンボードツールリリースに関する情報を参照して、 [office 365 Network Performance TOOL POC リリース](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102)ブログ投稿にフィードバックを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="2610e-154">You can read about the Office 365 Network Onboarding tool release and provide feedback at the [Office 365 Network Performance tool POC release](https://techcommunity.microsoft.com/t5/Office-365-Networking/Office-365-Network-Performance-tool-POC-release/m-p/319579#M102) blog post.</span></span> <span data-ttu-id="2610e-155">このツールおよびその他の Office 365 ネットワーク更新プログラムに関する今後の更新プログラムについては、「 [office 365 のネットワーク](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)ブログ」に掲載されています。</span><span class="sxs-lookup"><span data-stu-id="2610e-155">Information about future updates to this tool and other Office 365 networking updates will be posted to the [Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) blog.</span></span>
  
<span data-ttu-id="2610e-156">次の短いリンクを使用して、に戻ることができます。 [ https://aka.ms/o365networkconnectivity](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="2610e-156">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2610e-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="2610e-157">See also</span></span>

[<span data-ttu-id="2610e-158">Office 365 のネットワーク接続の概要</span><span class="sxs-lookup"><span data-stu-id="2610e-158">Office 365 Network Connectivity Overview</span></span>](office-365-networking-overview.md)

[<span data-ttu-id="2610e-159">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="2610e-159">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)

[<span data-ttu-id="2610e-160">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="2610e-160">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="2610e-161">Office 365 の URL と IP アドレスの範囲</span><span class="sxs-lookup"><span data-stu-id="2610e-161">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="2610e-162">Office 365 IP アドレスと URL の Web サービス </span><span class="sxs-lookup"><span data-stu-id="2610e-162">Office 365 IP Address and URL Web service</span></span>](office-365-ip-web-service.md)

[<span data-ttu-id="2610e-163">Office 365 のネットワークとパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="2610e-163">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
