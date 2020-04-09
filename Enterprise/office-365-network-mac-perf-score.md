---
title: Microsoft 365 ネットワーク評価 (プレビュー)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 ネットワーク評価 (プレビュー)
ms.openlocfilehash: 2ee18f50e841982e8f677964d2e7e57d95a209d8
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185748"
---
# <a name="microsoft-365-network-assessment-preview"></a><span data-ttu-id="adaa2-103">Microsoft 365 ネットワーク評価 (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="adaa2-103">Microsoft 365 network assessment (preview)</span></span>

<span data-ttu-id="adaa2-104">Microsoft 365 管理センターの Microsoft 365 ページへの接続において、**ネットワーク評価**は、多くのネットワークパフォーマンス指標の集合を、1-100 からのポイント値で表された、エンタープライズネットワークの正常性のスナップショットに分割します。</span><span class="sxs-lookup"><span data-stu-id="adaa2-104">In the Microsoft 365 Admin Center's Connectivity to Microsoft 365 page, **network assessments** distill an aggregate of many network performance metrics into a snapshot of your enterprise network health, represented by a points value from 1 - 100.</span></span> <span data-ttu-id="adaa2-105">ネットワーク評価は、テナント全体と、ユーザーがテナントに接続する各地理的位置の両方に適用されます。 Microsoft 365 管理者は、企業のネットワーク正常性の gestalt をすばやく把握して、グローバルなオフィスの場所についての詳細レポートにすばやくドリルダウンすることが簡単にできます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-105">Network assessments are scoped to both the entire tenant and for each geographic location from which users connect to your tenant, providing Microsoft 365 administrators with an easy way to instantly grasp a gestalt of the enterprise's network health and quickly drill down into a detailed report for any global office location.</span></span>

<span data-ttu-id="adaa2-106">ネットワーク評価ポイントの値は、表示時に有効になっている待機時間、帯域幅、ダウンロード速度、および接続品質指標の平均測定値です。</span><span class="sxs-lookup"><span data-stu-id="adaa2-106">The network assessment points value is an average measurement of latency, bandwidth, download speed and connection quality metrics compiled live at the time they are viewed.</span></span> <span data-ttu-id="adaa2-107">Microsoft が所有するネットワークのパフォーマンス指標は、これらの測定値から除外され、評価結果が明確になり、企業ネットワークに固有のものであることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-107">Performance metrics for Microsoft-owned networks are excluded from these measurements to ensure that assessment results are unambiguous and specific to the corporate network.</span></span>

![ネットワーク評価の値](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

<span data-ttu-id="adaa2-109">非常に低いネットワーク評価の値は、Microsoft 365 クライアントがテナントに接続したり、応答性の高いユーザー操作を維持したりする際に重大な問題が発生することを示唆していますが、高価値は、継続的なパフォーマンスの問題があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="adaa2-109">A very low network assessment value suggests that Microsoft 365 clients will have significant problems connecting to the tenant or maintaining a responsive user experience, while a high value indicates a properly configured network with few ongoing performance issues.</span></span> <span data-ttu-id="adaa2-110">80% の値は、ネットワークパフォーマンスによって Microsoft 365 接続または応答性に関して通常のユーザーからの苦情を受けないようにする必要がある正常な基準を表します。</span><span class="sxs-lookup"><span data-stu-id="adaa2-110">A value of 80% represents a healthy baseline where you should not expect to receive regular user complaints about Microsoft 365 connectivity or responsiveness due to network performance.</span></span> <span data-ttu-id="adaa2-111">ネットワーク接続の反復的な改善が行われると、この値はユーザーの操作に合わせて増加します。</span><span class="sxs-lookup"><span data-stu-id="adaa2-111">As iterative network connectivity improvements are made, this value will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="adaa2-112">Network insights、Microsoft 365 Admin Center でのパフォーマンスに関する推奨事項と評価は現在プレビュー状態であり、機能プレビュープログラムに登録されている Microsoft 365 テナントに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-112">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Microsoft 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="network-assessment-panel"></a><span data-ttu-id="adaa2-113">ネットワーク評価パネル</span><span class="sxs-lookup"><span data-stu-id="adaa2-113">Network assessment panel</span></span>

<span data-ttu-id="adaa2-114">テナントまたは特定のオフィスの場所にスコープが設定されているかどうかにかかわらず、各ネットワーク評価には、評価に関する詳細情報がパネルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-114">Each network assessment, whether scoped to the tenant or to a specific office location, shows a panel with details about the assessment.</span></span> <span data-ttu-id="adaa2-115">このパネルには、評価の棒グラフがパーセンテージとして表示されます。また、測定データを受け取ったワークロードのみを含む各コンポーネントワークロードの合計ポイントとして評価されます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-115">This panel shows a bar chart of the assessment both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="adaa2-116">オフィスの場所のネットワーク評価では、office の場所と同じ都市にデータを報告したすべての Microsoft 365 クライアントの中央にあるベンチマークも示しています。</span><span class="sxs-lookup"><span data-stu-id="adaa2-116">For an office location network assessment, we also show a benchmark which is the median of all Microsoft 365 clients that reported data in the same city as your office location.</span></span>

![ネットワーク評価の値の例](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

<span data-ttu-id="adaa2-118">パネルの [**評価] ブレークダウン**には、各コンポーネントのワークロードの評価が表示されます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-118">The **Assessment breakdown** in the panel shows the assessment for each of the component workloads.</span></span>

<span data-ttu-id="adaa2-119">**評価履歴**には、過去30日間の評価とベンチマークが表示されます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-119">The **Assessment history** shows the past 30 days of the assessment and the benchmark.</span></span>

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a><span data-ttu-id="adaa2-120">テナントのネットワーク評価とオフィスの場所ネットワークの評価</span><span class="sxs-lookup"><span data-stu-id="adaa2-120">Tenant network assessments and office location network assessments</span></span>

<span data-ttu-id="adaa2-121">ネットワーク評価は、Microsoft のネットワークへのオフィスの場所のネットワーク境界の設計を測定します。</span><span class="sxs-lookup"><span data-stu-id="adaa2-121">A network assessment measures the design of the network perimeter of an office location to Microsoft's network.</span></span> <span data-ttu-id="adaa2-122">ネットワーク境界の改善は、各オフィスの場所で行うことをお勧めします。または、ネットワーク接続が集約されている場合は、複数の場所に影響を与える改良が行われることがあります。</span><span class="sxs-lookup"><span data-stu-id="adaa2-122">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>

<span data-ttu-id="adaa2-123">ネットワークパフォーマンスの概要ページにある Microsoft 365 テナント全体のネットワーク評価の値と、その場所の要約ページにある検出された各オフィスの場所の特定の値を示します。</span><span class="sxs-lookup"><span data-stu-id="adaa2-123">We show a network assessment value for the whole Microsoft 365 tenant on the network performance overview page and a specific value for each detected office location on that location's summary page.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="adaa2-124">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="adaa2-124">Exchange Online</span></span>

<span data-ttu-id="adaa2-125">Exchange Online の場合、クライアントマシンから Exchange フロントエンドサーバーへの TCP 遅延が測定されます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-125">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="adaa2-126">これは、ネットワークが顧客の LAN および WAN を通過する距離の影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="adaa2-126">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="adaa2-127">また、ネットワークの仲介装置やサービスによって影響を受けたり、接続が遅延したり、パケットが再送信されたりする可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="adaa2-127">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="adaa2-128">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="adaa2-128">SharePoint Online</span></span>

<span data-ttu-id="adaa2-129">SharePoint Online の場合、ドキュメントにアクセスするユーザーが使用できるダウンロード速度が測定されます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-129">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="adaa2-130">このことは、クライアントコンピューターと Microsoft のネットワーク間のネットワーク回線で利用可能な帯域幅の影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="adaa2-130">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft's network.</span></span> <span data-ttu-id="adaa2-131">また、複雑なネットワークデバイスや、混雑している Wi-fi エリアでボトルネックに存在するネットワーク輻輳による影響を受けることもあります。</span><span class="sxs-lookup"><span data-stu-id="adaa2-131">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="adaa2-132">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="adaa2-132">Microsoft Teams</span></span>

<span data-ttu-id="adaa2-133">Microsoft Teams では、ネットワーク品質は UDP 遅延、UDP ジッタ、および UDP パケット損失として測定されます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-133">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="adaa2-134">UDP は、Microsoft Teams の通話と電話会議の音声およびビデオメディア接続に使用されます。</span><span class="sxs-lookup"><span data-stu-id="adaa2-134">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="adaa2-135">これは、より一般的な TCP プロトコルに対して UDP が個別に構成されているため、ネットワークの UDP サポートの接続のギャップに加えて、遅延とダウンロードの速度の場合と同じ要因によって影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="adaa2-135">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network's UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="related-topics"></a><span data-ttu-id="adaa2-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="adaa2-136">Related topics</span></span>

[<span data-ttu-id="adaa2-137">Microsoft 365 管理センター (プレビュー) でのネットワークパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="adaa2-137">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="adaa2-138">Microsoft 365 network performance insights (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="adaa2-138">Microsoft 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="adaa2-139">M365 管理センターの Microsoft 365 ネットワークオンボードツール (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="adaa2-139">Microsoft 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)

[<span data-ttu-id="adaa2-140">Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="adaa2-140">Microsoft 365 Network Connectivity Location Services (preview)</span></span>](office-365-network-mac-location-services.md)
