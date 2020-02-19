---
title: Office 365 ネットワーク評価 (プレビュー)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 ネットワーク評価 (プレビュー)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106373"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="9be46-103">Office 365 ネットワーク評価 (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="9be46-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="9be46-104">Office 365 ネットワーク評価は、顧客のネットワーク接続に対するユーザーの相対的な影響を示します。</span><span class="sxs-lookup"><span data-stu-id="9be46-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="9be46-105">Microsoft が所有しているネットワーク接続の影響は、お客様が責任を持つネットワーク設計を最適化できるように、このから除外されています。</span><span class="sxs-lookup"><span data-stu-id="9be46-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="9be46-106">これは、Office 365 の主要なワークロードのユーザーの環境に影響する測定値から計算され、0 ~ 100 の範囲のパーセンテージで表示されます。</span><span class="sxs-lookup"><span data-stu-id="9be46-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="9be46-107">非常に低いネットワークスコアを設定すると、Office 365 クライアントでは、ユーザーが応答しない、またはその他の問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9be46-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="9be46-108">80% のスコアは、ネットワークのパフォーマンスのために Office 365 のユーザー環境に関してユーザーの苦情を受けないようにする必要があるネットワーク接続を表します。</span><span class="sxs-lookup"><span data-stu-id="9be46-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="9be46-109">ネットワーク接続の改良が行われると、このスコアはユーザーの操作に合わせて向上します。</span><span class="sxs-lookup"><span data-stu-id="9be46-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9be46-110">Microsoft 365 管理センターでのネットワークパフォーマンスの推奨事項、洞察、評価は現在プレビュー状態であり、機能プレビュープログラムに登録されている Office 365 テナントに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9be46-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="9be46-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9be46-111">Exchange Online</span></span>

<span data-ttu-id="9be46-112">Exchange Online の場合、クライアントマシンから Exchange フロントエンドサーバーへの TCP 遅延が測定されます。</span><span class="sxs-lookup"><span data-stu-id="9be46-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="9be46-113">これは、ネットワークが顧客の LAN および WAN を通過する距離の影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9be46-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="9be46-114">また、ネットワークの仲介装置やサービスによって影響を受けたり、接続が遅延したり、パケットが再送信されたりする可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="9be46-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="9be46-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="9be46-115">SharePoint Online</span></span>

<span data-ttu-id="9be46-116">SharePoint Online の場合、ドキュメントにアクセスするユーザーが使用できるダウンロード速度が測定されます。</span><span class="sxs-lookup"><span data-stu-id="9be46-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="9be46-117">このことは、クライアントコンピューターと Microsoft のネットワーク間のネットワーク回線で利用可能な帯域幅の影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9be46-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="9be46-118">また、複雑なネットワークデバイスや、混雑している Wi-fi エリアでボトルネックに存在するネットワーク輻輳による影響を受けることもあります。</span><span class="sxs-lookup"><span data-stu-id="9be46-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="9be46-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9be46-119">Microsoft Teams</span></span>

<span data-ttu-id="9be46-120">Microsoft Teams では、ネットワーク品質は UDP 遅延、UDP ジッタ、および UDP パケット損失として測定されます。</span><span class="sxs-lookup"><span data-stu-id="9be46-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="9be46-121">UDP は、Microsoft Teams の通話と電話会議の音声およびビデオメディア接続に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9be46-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="9be46-122">これは、より一般的な TCP プロトコルに対して UDP が個別に構成されているため、ネットワークの UDP サポートの接続のギャップに加えて、遅延とダウンロードの速度の場合と同じ要因によって影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9be46-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="9be46-123">テナントのネットワークスコアとオフィスの場所のネットワークスコア</span><span class="sxs-lookup"><span data-stu-id="9be46-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="9be46-124">ネットワークスコアは、オフィスの場所のネットワーク境界の設計を Microsoft のネットワークに測定します。</span><span class="sxs-lookup"><span data-stu-id="9be46-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="9be46-125">ネットワーク境界の改善は、各オフィスの場所で行うことをお勧めします。または、ネットワーク接続が集約されている場合は、複数の場所に影響を与える改良が行われることがあります。</span><span class="sxs-lookup"><span data-stu-id="9be46-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="9be46-126">ネットワークパフォーマンスの概要ページにある Office 365 テナント全体のネットワークスコアと、その場所の要約ページにある検出された各オフィスの場所の特定のネットワークスコアを示します。</span><span class="sxs-lookup"><span data-stu-id="9be46-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="9be46-127">ネットワークスコアパネル</span><span class="sxs-lookup"><span data-stu-id="9be46-127">Network score panel</span></span>

<span data-ttu-id="9be46-128">各ネットワークスコアテナントに対して、または特定のオフィスの場所に対して、スコアの詳細が表示されているパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9be46-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="9be46-129">このパネルには、測定データを受信したワークロードのみを含む、各コンポーネントワークロードの割合と合計ポイントの両方で、スコアの棒グラフが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9be46-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="9be46-130">オフィスの場所のネットワークスコアについても、office の場所と同じ都市にデータを報告したすべての Office 365 クライアントの中央にあるベンチマークを示しています。</span><span class="sxs-lookup"><span data-stu-id="9be46-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="9be46-131">パネルのスコア表示には、各コンポーネントのワークロードのスコアが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9be46-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="9be46-132">スコア履歴には、過去30日間のスコアとベンチマークが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9be46-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="9be46-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="9be46-133">Related topics</span></span>

[<span data-ttu-id="9be46-134">Microsoft 365 管理センター (プレビュー) でのネットワークパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="9be46-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="9be46-135">Office 365 network performance insights (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="9be46-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="9be46-136">M365 管理センターの Office 365 ネットワークオンボードツール (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="9be46-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
