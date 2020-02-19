---
title: 中国ユーザー向けの Office 365 グローバルテナントのパフォーマンスの最適化
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/13/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
f1.keywords:
- NOCSH
description: この記事では、グローバル Office 365 テナントの中国ユーザーのネットワークパフォーマンスを最適化するためのガイダンスを提供します。
ms.openlocfilehash: 33e475dfbf4accf306a099542cf8cf2f22ff23a5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106381"
---
# <a name="office-365-global-tenant-performance-optimization-for-china-users"></a><span data-ttu-id="4ff4f-103">中国ユーザー向けの Office 365 グローバルテナントのパフォーマンスの最適化</span><span class="sxs-lookup"><span data-stu-id="4ff4f-103">Office 365 global tenant performance optimization for China users</span></span>

>[!IMPORTANT]
><span data-ttu-id="4ff4f-104">このガイダンスは、中国に配置されている**エンタープライズの office 365 ユーザー**がグローバルな**office 365 テナント**に接続する場合の使用シナリオに固有のものです。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-104">This guidance is specific to usage scenarios in which **enterprise Office 365 users located in China** connect to a **global Office 365 tenant**.</span></span> <span data-ttu-id="4ff4f-105">このガイダンスは、21Vianet が運用している Office 365 のテナントには適用**されません**。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-105">This guidance does **not** apply to tenants in Office 365 operated by 21Vianet.</span></span>

<span data-ttu-id="4ff4f-106">グローバルな Office 365 テナントと中国の企業のプレゼンスがある企業では、中国の電話会社のインターネットアーキテクチャに特有の要因によって、Office 365 クライアントのパフォーマンスが複雑になることがあります。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-106">For enterprises with global Office 365 tenants and a corporate presence in China, Office 365 client performance for China-based users can be complicated by factors unique to China Telco's Internet architecture.</span></span>

<span data-ttu-id="4ff4f-107">中国 Isp は、国境デバイスを通過するグローバルなパブリックインターネットへの海外の接続を規制しています。これは、境界を越えたネットワークの輻輳が発生する傾向があります。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-107">China ISPs have regulated offshore connections to the global public Internet that go through perimeter devices which are prone to high-levels of cross-border network congestion.</span></span> <span data-ttu-id="4ff4f-108">この輻輳により、中国に出入りするすべてのインターネットトラフィックに対してパケット損失と待機時間が発生します。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-108">This congestion creates packet loss and latency for all Internet traffic going into and out of China.</span></span>

![Office 365 のトラフィックが非最適化](media/O365-networking/China-O365-unoptimized.png)

<span data-ttu-id="4ff4f-110">パケット損失と遅延は、ネットワークサービス、特に大規模なデータ交換 (大規模なファイル転送など) や、ほぼリアルタイムのパフォーマンス (オーディオおよびビデオアプリケーション) を必要とするサービスのパフォーマンスに悪影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-110">Packet loss and latency is detrimental to the performance of network services, especially services that require large data exchanges (such as large file transfers) or requiring near real-time performance (audio and video applications).</span></span>

<span data-ttu-id="4ff4f-111">このトピックの目的は、Office 365 サービスにおける中国の国境を越えたネットワークの輻輳による影響を軽減するためのベストプラクティスを提供することです。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-111">The goal of this topic is to provide best practices for mitigating the impact of China cross-border network congestion on Office 365 services.</span></span> <span data-ttu-id="4ff4f-112">このトピックでは、中国の電話会社での複雑なルーティングによる高パケット待機時間の問題など、最終段階のパフォーマンスの問題に対処することはありません。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-112">This topic does not address other common last-mile performance issues such as issues of high packet latency due to complex routing within China carriers.</span></span>

## <a name="corporate-network-best-practices"></a><span data-ttu-id="4ff4f-113">企業ネットワークのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="4ff4f-113">Corporate network best practices</span></span>

<span data-ttu-id="4ff4f-114">グローバルな Office 365 テナントおよび中国のユーザーを有する多くの企業は、中国のオフィスの場所と世界中の海外の場所との間で企業ネットワークトラフィックを伝送するプライベートネットワークを実装しています。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-114">Many enterprises with global Office 365 tenants and users in China have implemented private networks that carry corporate network traffic between China office locations and offshore locations around the world.</span></span> <span data-ttu-id="4ff4f-115">これらの企業は、このネットワークインフラストラクチャを活用して、国境を越えたネットワーク輻輳を防ぎ、中国における Office 365 サービスのパフォーマンスを最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-115">These enterprises can leverage this network infrastructure to avoid cross-border network congestion and optimize their Office 365 service performance in China.</span></span>

>[!IMPORTANT]
><span data-ttu-id="4ff4f-116">すべてのプライベート WAN 実装と同様に、お客様の国や地域の規制要件を常に調べて、ネットワーク構成が準拠していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-116">As with all private WAN implementations, you should always consult regulatory requirements for your country and/or region to ensure that your network configuration is in compliance.</span></span>

<span data-ttu-id="4ff4f-117">最初の手順として、「 [Office 365 のネットワーク計画とパフォーマンスチューニング](https://aka.ms/tune)」にあるベンチマークネットワークガイダンスに従うことが重要です。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-117">As a first step, it is crucial that you follow our benchmark network guidance at [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span> <span data-ttu-id="4ff4f-118">主要な目標は、可能であれば、中国のインターネットからのグローバルな Office 365 サービスへのアクセスを回避することです。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-118">The primary goal should be to avoid accessing global Office 365 services from the Internet in China if possible.</span></span>

- <span data-ttu-id="4ff4f-119">既存のプライベートネットワークを利用して、中国オフィスのネットワークと、中国外のパブリックインターネットで出てきた海外の場所との間で Office 365 のネットワークトラフィックを行います。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-119">Leverage your existing private network to carry Office 365 network traffic between China office networks and offshore locations that egress on the public Internet outside China.</span></span> <span data-ttu-id="4ff4f-120">中国外のほとんどすべての場所では、明確なメリットが得られます。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-120">Almost any location outside China will provide a clear benefit.</span></span> <span data-ttu-id="4ff4f-121">ネットワーク管理者は、egressing を使用して、 [Microsoft グローバルネットワーク](https://docs.microsoft.com/azure/networking/microsoft-global-network)との間で遅延のない相互接続を行うことにより、さらに多くの機能を最適化できます。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-121">Network administrators can further optimize by egressing in areas with low-latency interconnect with the [Microsoft global network](https://docs.microsoft.com/azure/networking/microsoft-global-network).</span></span> <span data-ttu-id="4ff4f-122">香港、日本、南韓国の例を示します。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-122">Hong Kong, Japan, and South Korea are examples.</span></span>
- <span data-ttu-id="4ff4f-123">VPN 接続経由で企業ネットワークにアクセスするようにユーザーデバイスを構成し、Office 365 トラフィックが企業ネットワークのプライベートな海外リンクを通過できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-123">Configure user devices to access the corporate network over a VPN connection to allow Office 365 traffic to transit the corporate network's private offshore link.</span></span> <span data-ttu-id="4ff4f-124">VPN クライアントが分割トンネリングを使用するように構成されていないか、またはユーザーデバイスが Office 365 トラフィックの分割トンネリングを無視するように構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-124">Ensure that VPN clients are either not configured to use split tunneling, or that user devices are configured to ignore split tunneling for Office 365 traffic.</span></span>
- <span data-ttu-id="4ff4f-125">プライベートな海外リンクを介してすべての Office 365 トラフィックをルーティングするようにネットワークを構成します。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-125">Configure your network to route all Office 365 traffic across your private offshore link.</span></span> <span data-ttu-id="4ff4f-126">プライベートリンク上のトラフィックの量を最小限に抑える必要がある場合は、[**最適化**] カテゴリでのみエンドポイントをルーティングするように選択し、[**許可**] と [**既定**のエンドポイントを通過する要求をインターネットに転送できるようにする] を選択できます。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-126">If you must minimize the volume of traffic on your private link, you can choose to only route endpoints in the **Optimize** category, and allow requests to **Allow** and **Default** endpoints to transit the Internet.</span></span> <span data-ttu-id="4ff4f-127">これにより、高遅延およびパケット損失に最も敏感になる重要なサービスに対して最適化されたトラフィックを制限することで、パフォーマンスが向上し、帯域幅の消費を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-127">This will improve performance and minimize bandwidth consumption by limiting optimized traffic to critical services that are most sensitive to high latency and packet loss.</span></span>
- <span data-ttu-id="4ff4f-128">可能であれば、ライブメディアストリーミングトラフィック (Teams など) に TCP の代わりに UDP を使用します。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-128">If possible, use UDP instead of TCP for live media streaming traffic, such as for Teams.</span></span> <span data-ttu-id="4ff4f-129">UDP は、TCP よりも優れたライブメディアストリーミングパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-129">UDP offers better live media streaming performance than TCP.</span></span>

<span data-ttu-id="4ff4f-130">Office 365 のトラフィックを選択的にルーティングする方法については、「 [office 365 エンドポイントの管理](managing-office-365-endpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-130">For information about how to selectively route Office 365 traffic, see [Managing Office 365 endpoints](managing-office-365-endpoints.md).</span></span> <span data-ttu-id="4ff4f-131">全世界の Office 365 の Url と IP アドレスの一覧については、「 [office 365 の url と ip アドレスの範囲](urls-and-ip-address-ranges.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-131">For a list of all worldwide Office 365 URLs and IP addresses, see [Office 365 URLs and IP address ranges](urls-and-ip-address-ranges.md).</span></span>

![Office 365 のトラフィック最適化](media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a><span data-ttu-id="4ff4f-133">ユーザーのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="4ff4f-133">User best practices</span></span>

<span data-ttu-id="4ff4f-134">中国のユーザーは、企業ネットワークに接続されていない自宅、コーヒーショップ、ホテル、支社などのリモートの場所からグローバルな Office 365 テナントに接続することにより、デバイスとオフィスの間のトラフィックが原因でネットワークのパフォーマンスが低下する可能性があります。365は、中国の混雑したクロスボーダーネットワーク回路を転送する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-134">Users in China who connect to global Office 365 tenants from remote locations such as homes, coffee shops, hotels and branch offices with no connection to enterprise networks can experience poor network performance because traffic between their devices and Office 365 must transit China's congested cross-border network circuits.</span></span>

<span data-ttu-id="4ff4f-135">国境を越えたプライベートネットワークや、企業ネットワークへの VPN アクセスがオプションではない場合でも、ユーザー単位のパフォーマンスの問題は、次のベストプラクティスに従って中国ベースのユーザーをトレーニングすることによって軽減できます。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-135">If cross-border private networks and/or VPN access into the corporate network are not an option, per-user performance issues can still be mitigated by training your China-based users to follow these best practices.</span></span>

- <span data-ttu-id="4ff4f-136">キャッシュ (Outlook、Teams、OneDrive など) をサポートするリッチな Office クライアントを利用し、web ベースのクライアントを使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-136">Utilize rich Office clients that support caching (e.g. Outlook, Teams, OneDrive, etc.), and avoid web-based clients.</span></span> <span data-ttu-id="4ff4f-137">Office クライアントのキャッシュおよびオフラインアクセスの機能により、ネットワークの輻輳と遅延の影響が大幅に軽減されます。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-137">Office client caching and offline access features can dramatically reduce the impact of network congestion and latency.</span></span>
- <span data-ttu-id="4ff4f-138">Office 365 テナントが_電話会議_機能を使用して構成されている場合、Teams ユーザーは公衆交換電話網 (PSTN) 経由で会議に参加できます。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-138">If your Office 365 tenant has been configured with the _Audio Conferencing_ feature, Teams users can join meetings via the public switched telephone network (PSTN).</span></span> <span data-ttu-id="4ff4f-139">詳細については、「 [Office 365 の電話会議](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-139">For more information, see [Audio Conferencing in Office 365](https://docs.microsoft.com/microsoftteams/audio-conferencing-in-office-365).</span></span>
- <span data-ttu-id="4ff4f-140">ユーザーがネットワークのパフォーマンスの問題に直面した場合は、トラブルシューティングのために IT 部門に報告し、Office 365 サービスで問題が発生した場合に Microsoft サポートにエスカレートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-140">If users experience network performance issues, they should report to their IT department for troubleshooting, and escalate to Microsoft support if trouble with Office 365 services is suspected.</span></span> <span data-ttu-id="4ff4f-141">境界を越えたネットワークのパフォーマンスが原因で発生する問題があるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-141">Not all issues are caused by cross-border network performance.</span></span>

<span data-ttu-id="4ff4f-142">Microsoft は、さまざまな種類のネットワークアーキテクチャおよび特性を使用して、Office 365 ユーザーの利便性とクライアントのパフォーマンスを改善するために継続的に取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-142">Microsoft is continually working to improve the Office 365 user experience and the performance of clients over the widest possible range of network architectures and characteristics.</span></span> <span data-ttu-id="4ff4f-143">[Office 365 技術コミュニティ](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General)にアクセスして、会話の開始や参加、リソースの検索、機能のリクエストと提案の提出を行います。</span><span class="sxs-lookup"><span data-stu-id="4ff4f-143">Visit the [Office 365 Tech Community](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General) to start or join a conversation, find resources, and submit feature requests and suggestions.</span></span>

## <a name="related-topics"></a><span data-ttu-id="4ff4f-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ff4f-144">Related topics</span></span>

[<span data-ttu-id="4ff4f-145">Office 365 のネットワーク計画とパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="4ff4f-145">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="4ff4f-146">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="4ff4f-146">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="4ff4f-147">Office 365 エンドポイントの管理</span><span class="sxs-lookup"><span data-stu-id="4ff4f-147">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)

[<span data-ttu-id="4ff4f-148">Office 365 の URL と IP アドレスの範囲</span><span class="sxs-lookup"><span data-stu-id="4ff4f-148">Office 365 URLs and IP address ranges</span></span>](urls-and-ip-address-ranges.md)

[<span data-ttu-id="4ff4f-149">Microsoft グローバルネットワーク</span><span class="sxs-lookup"><span data-stu-id="4ff4f-149">Microsoft global network</span></span>](https://docs.microsoft.com/azure/networking/microsoft-global-network)
