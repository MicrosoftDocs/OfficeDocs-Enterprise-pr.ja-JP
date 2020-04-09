---
title: Microsoft 365 Network Insights (プレビュー)
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
description: Microsoft 365 Network Insights (プレビュー)
ms.openlocfilehash: baab4716ace0b15df5878d21987c037372a2754e
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185758"
---
# <a name="microsoft-365-network-insights-preview"></a><span data-ttu-id="4da16-103">Microsoft 365 Network Insights (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="4da16-103">Microsoft 365 Network Insights (preview)</span></span>

<span data-ttu-id="4da16-104">**Network insights**は、Microsoft 365 テナントから収集され、テナントの管理ユーザーのみが表示できるライブパフォーマンス指標です。</span><span class="sxs-lookup"><span data-stu-id="4da16-104">**Network insights** are live performance metrics collected from your Microsoft 365 tenant, and available to view only by administrative users in your tenant.</span></span> <span data-ttu-id="4da16-105">Insights は、Microsoft 365 管理センターのに表示<https://portal.microsoft.com/adminportal/home#/networkperformance>されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-105">Insights are displayed in the Microsoft 365 Admin Center at <https://portal.microsoft.com/adminportal/home#/networkperformance>.</span></span>

<span data-ttu-id="4da16-106">Insights は、オフィスの場所のネットワーク境界を設計するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4da16-106">Insights are intended to help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="4da16-107">各洞察では、ユーザーがテナントにアクセスする地理的な場所ごとに、特定の一般的な問題のパフォーマンス特性に関するライブ詳細が提供されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-107">Each insight provides live details about the performance characteristics for a specific common issue for each geographic location where users are accessing your tenant.</span></span>

<span data-ttu-id="4da16-108">各オフィスの場所には、次の5つの特定のネットワーク洞察が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="4da16-108">There are five specific network insights that may be shown for each office location:</span></span>

- [<span data-ttu-id="4da16-109">Backhauled ネットワークの出口</span><span class="sxs-lookup"><span data-stu-id="4da16-109">Backhauled network egress</span></span>](#backhauled-network-egress)
- [<span data-ttu-id="4da16-110">近距離のお客様のためのパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="4da16-110">Better performance detected for customers near you</span></span>](#better-performance-detected-for-customers-near-you)
- [<span data-ttu-id="4da16-111">Exchange Online サービスのフロントドアの非最適な使用</span><span class="sxs-lookup"><span data-stu-id="4da16-111">Use of a non-optimal Exchange Online service front door</span></span>](#use-of-a-non-optimal-exchange-online-service-front-door)
- [<span data-ttu-id="4da16-112">最適ではない SharePoint Online サービスのフロントドアの使用</span><span class="sxs-lookup"><span data-stu-id="4da16-112">Use of a non-optimal SharePoint Online service front door</span></span>](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [<span data-ttu-id="4da16-113">SharePoint フロントドアからのダウンロード速度が低い</span><span class="sxs-lookup"><span data-stu-id="4da16-113">Low download speed from SharePoint front door</span></span>](#low-download-speed-from-sharepoint-front-door)

>[!IMPORTANT]
><span data-ttu-id="4da16-114">Network insights、Microsoft 365 Admin Center でのパフォーマンスに関する推奨事項と評価は現在プレビュー状態であり、機能プレビュープログラムに登録されている Microsoft 365 テナントに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4da16-114">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Microsoft 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="4da16-115">Backhauled ネットワークの出口</span><span class="sxs-lookup"><span data-stu-id="4da16-115">Backhauled network egress</span></span>

<span data-ttu-id="4da16-116">Network insights service が、特定のユーザーの場所からネットワークの出口までの距離が500マイル (800 km) よりも大きいことを検出した場合に、この洞察が表示されます。これは、Microsoft 365 トラフィックが共通のインターネットエッジデバイスまたはプロキシに backhauled されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="4da16-116">This insight will be displayed if the network insights service detects that the distance from a given user location to the network egress is greater than 500 miles (800 kilometers), indicating that Microsoft 365 traffic is being backhauled to a common Internet edge device or proxy.</span></span>

<span data-ttu-id="4da16-117">この洞察は、一部の要約ビューで "出口" として短縮されています。</span><span class="sxs-lookup"><span data-stu-id="4da16-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

![Backhauled ネットワークの出口](Media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="4da16-119">シナリオ</span><span class="sxs-lookup"><span data-stu-id="4da16-119">What does this mean?</span></span>

<span data-ttu-id="4da16-120">これは、オフィスの場所とネットワーク出口との間の距離が500マイル (800 km) を超えていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="4da16-120">This identifies that the distance between the office location and the network egress is more than 500 miles (800 kilometers).</span></span> <span data-ttu-id="4da16-121">Office の場所は難読化されたクライアントコンピューターの場所で識別され、ネットワークの出口の場所は、逆引き IP アドレスを使用して場所データベースに識別されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-121">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="4da16-122">Windows ロケーションサービスがコンピューターで無効になっている場合は、office の場所が不正確になることがあります。</span><span class="sxs-lookup"><span data-stu-id="4da16-122">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="4da16-123">逆引き IP アドレスデータベースの情報が正確でない場合は、ネットワークの出口の場所が不正確になることがあります。</span><span class="sxs-lookup"><span data-stu-id="4da16-123">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="4da16-124">この洞察の詳細には、オフィスの場所、現在のネットワーク出口の位置、出口位置の関連性、位置と現在の出口ポイント間の距離、条件が最初に検出された日付、および条件が解決された日付が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4da16-124">Details for this insight include the office location, estimated percentage of total tenant user at the location, the current network egress location, relevance of the egress location, the distance between the location and the current egress point, the date the condition was first detected, and the date the condition was resolved.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4da16-125">どうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="4da16-125">What should I do?</span></span>

<span data-ttu-id="4da16-126">この情報については、office の場所へのネットワーク出口をお勧めします。これにより、接続が Microsoft のグローバルネットワークおよび最寄りの Microsoft 365 service フロントドアに最適にルーティングされるようになります。</span><span class="sxs-lookup"><span data-stu-id="4da16-126">For this insight, we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's global network and to the nearest Microsoft 365 service front door.</span></span> <span data-ttu-id="4da16-127">また、ユーザーのオフィスの場所に対してネットワークを閉じることにより、将来的に、Microsoft がネットワークポイントプレゼンスと Microsoft 365 サービスのフロントドアの両方を展開した場合にもパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="4da16-127">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Microsoft 365 service front doors in the future.</span></span>

<span data-ttu-id="4da16-128">この問題を解決する方法の詳細については、「 [Office 365 のネットワーク接続の原則](office-365-network-connectivity-principles.md)」の「[ネットワーク接続をローカル](office-365-network-connectivity-principles.md#egress-network-connections-locally)に出力する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4da16-128">For more information about how to resolve this issue, see [Egress network connections locally](office-365-network-connectivity-principles.md#egress-network-connections-locally) in [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="4da16-129">近距離のお客様のためのパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="4da16-129">Better performance detected for customers near you</span></span>

<span data-ttu-id="4da16-130">この洞察は、このオフィスの場所にある組織のユーザーに比べて、メトロエリア内の多数の顧客の方がパフォーマンスが優れていることを network insights service が検出した場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-130">This insight will be displayed if the network insights service detects that a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="4da16-131">この洞察は、一部の概要ビューでは "ピア" として短縮されています。</span><span class="sxs-lookup"><span data-stu-id="4da16-131">This insight is abbreviated as "Peers" in some summary views.</span></span>

![ネットワークの相対パフォーマンス](Media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="4da16-133">シナリオ</span><span class="sxs-lookup"><span data-stu-id="4da16-133">What does this mean?</span></span>

<span data-ttu-id="4da16-134">この洞察は、このオフィスの場所と同じ都市にある Microsoft 365 の顧客の総合的なパフォーマンスを調査します。</span><span class="sxs-lookup"><span data-stu-id="4da16-134">This insight examines the aggregate performance of Microsoft 365 customers in the same city as this office location.</span></span> <span data-ttu-id="4da16-135">この洞察は、ユーザーの平均待機時間が近隣テナントの平均待機時間を10% 上回る場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-135">This insight is displayed if the average latency of your users is 10% greater than the average latency of neighboring tenants.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4da16-136">どうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="4da16-136">What should I do?</span></span>

<span data-ttu-id="4da16-137">この条件には、企業ネットワークまたは ISP の待機時間、ボトルネック、アーキテクチャ設計上の問題など、さまざまな理由が考えられます。</span><span class="sxs-lookup"><span data-stu-id="4da16-137">There could be many reasons for this condition, including latency in your corporate network or ISP, bottlenecks, or architecture design issues.</span></span> <span data-ttu-id="4da16-138">Office ネットワークと現在の Microsoft 365 フロントドア間のルートで、各ホップ間の待機時間を調べます。</span><span class="sxs-lookup"><span data-stu-id="4da16-138">Examine the latency between each hop in the route between your office network and the current Microsoft 365 front door.</span></span> <span data-ttu-id="4da16-139">詳細については、「 [Office 365 のネットワーク接続の原則](office-365-network-connectivity-principles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4da16-139">For more information, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="4da16-140">Exchange Online サービスのフロントドアの非最適な使用</span><span class="sxs-lookup"><span data-stu-id="4da16-140">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="4da16-141">ネットワークインサイト内のユーザーが、最適な Exchange Online サービスのフロントドアに接続されていないことを検出した場合、この洞察が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-141">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to an optimal Exchange Online service front door.</span></span>

<span data-ttu-id="4da16-142">この洞察は、一部の概要ビューに "ルーティング" として短縮されています。</span><span class="sxs-lookup"><span data-stu-id="4da16-142">This insight is abbreviated as "Routing" in some summary views.</span></span>

![非最適なフロントドア](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="4da16-144">シナリオ</span><span class="sxs-lookup"><span data-stu-id="4da16-144">What does this mean?</span></span>

<span data-ttu-id="4da16-145">適切なパフォーマンスを備えた、office の場所の都市からの使用に適した Exchange Online サービスのフロントドアをリストしています。</span><span class="sxs-lookup"><span data-stu-id="4da16-145">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="4da16-146">現在のテストで、この一覧にない Exchange Online サービスのフロントドアの使用が示されている場合は、この推奨事項を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4da16-146">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4da16-147">どうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="4da16-147">What should I do?</span></span>

<span data-ttu-id="4da16-148">Exchange Online サービスのフロントドアを使用していない場合は、企業ネットワークの出口の前にネットワークのバックアウトが原因で、ローカルと直接のネットワーク出口が推奨されることがあります。</span><span class="sxs-lookup"><span data-stu-id="4da16-148">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="4da16-149">また、リモート DNS の再帰リゾルバーサーバーを使用して、DNS の再帰リゾルバーサーバーをネットワークの出口に配置することが推奨される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4da16-149">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="4da16-150">最適ではない SharePoint Online サービスのフロントドアの使用</span><span class="sxs-lookup"><span data-stu-id="4da16-150">Use of a non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="4da16-151">ネットワーク insights サービスが、特定の場所にいるユーザーが最も近い SharePoint Online サービスのフロントドアに接続していないことを検出した場合、この洞察が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-151">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to the closest SharePoint Online service front door.</span></span>

<span data-ttu-id="4da16-152">この洞察は、一部の要約ビューでは "Afd" と略記されています。</span><span class="sxs-lookup"><span data-stu-id="4da16-152">This insight is abbreviated as "Afd" in some summary views.</span></span>

![非最適なフロントドア](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="4da16-154">シナリオ</span><span class="sxs-lookup"><span data-stu-id="4da16-154">What does this mean?</span></span>

<span data-ttu-id="4da16-155">テストクライアントが接続している SharePoint Online サービスのフロントドアを特定します。</span><span class="sxs-lookup"><span data-stu-id="4da16-155">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="4da16-156">次に、オフィスの所在地の市区町村に対して、その都市に対して予想される SharePoint Online サービスのフロントドアと比較します。</span><span class="sxs-lookup"><span data-stu-id="4da16-156">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="4da16-157">一致しない場合は、この推奨事項を行います。</span><span class="sxs-lookup"><span data-stu-id="4da16-157">If it doesn't match, then we make this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4da16-158">どうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="4da16-158">What should I do?</span></span>

<span data-ttu-id="4da16-159">最適でない SharePoint Online サービスのフロントドアの使用は、企業ネットワークの出口の前にネットワークバックが発生した場合に発生することがあります。これは、ローカルおよび直接ネットワークを出口にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4da16-159">Use of a non-optimal SharePoint Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="4da16-160">また、リモート DNS の再帰リゾルバーサーバーを使用して、DNS の再帰リゾルバーサーバーをネットワークの出口に配置することが推奨される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4da16-160">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="4da16-161">SharePoint フロントドアからのダウンロード速度が低い</span><span class="sxs-lookup"><span data-stu-id="4da16-161">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="4da16-162">Network insights service が、特定のオフィスの場所と SharePoint Online の間の帯域幅が 1 MBps 未満であることを検出すると、この洞察が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-162">This insight will be displayed if the network insights service detects that bandwidth between the specific office location and SharePoint Online is less than 1 MBps.</span></span>

<span data-ttu-id="4da16-163">この洞察は、一部の要約ビューで "スループット" と短縮されています。</span><span class="sxs-lookup"><span data-stu-id="4da16-163">This insight is abbreviated as "Throughput" in some summary views.</span></span>

### <a name="what-does-this-mean"></a><span data-ttu-id="4da16-164">シナリオ</span><span class="sxs-lookup"><span data-stu-id="4da16-164">What does this mean?</span></span>

<span data-ttu-id="4da16-165">ユーザーが SharePoint Online と OneDrive for business サービスのフロントドアから取得できるダウンロード速度は、1秒あたりのメガバイト数 (MBps) で測定されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-165">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="4da16-166">この値が 1 Mb 未満の場合は、この洞察を提供します。</span><span class="sxs-lookup"><span data-stu-id="4da16-166">If this value is less than 1 MBps then we provide this insight.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4da16-167">どうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="4da16-167">What should I do?</span></span>

<span data-ttu-id="4da16-168">ダウンロード速度を向上させるには、帯域幅を増やす必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="4da16-168">To improve download speeds, bandwidth may need to be increased.</span></span> <span data-ttu-id="4da16-169">または、オフィスの場所と SharePoint Online サービスのフロントドアで、ユーザーのコンピューター間にネットワークの輻輳が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4da16-169">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="4da16-170">これは、congestive 損失とも呼ばれ、十分な帯域幅が利用可能な場合でも、ユーザーが使用できるダウンロード速度を制限します。</span><span class="sxs-lookup"><span data-stu-id="4da16-170">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

## <a name="china-user-optimal-network-egress"></a><span data-ttu-id="4da16-171">中国ユーザーにとって最適なネットワークの出口</span><span class="sxs-lookup"><span data-stu-id="4da16-171">China user optimal network egress</span></span>

<span data-ttu-id="4da16-172">この洞察は、中国のユーザーが他の地理的な場所にある Microsoft 365 テナントに接続している場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4da16-172">This insight will be displayed if your organization has users in China connecting to your Microsoft 365 tenant in other geographic locations.</span></span> 

### <a name="what-does-this-mean"></a><span data-ttu-id="4da16-173">シナリオ</span><span class="sxs-lookup"><span data-stu-id="4da16-173">What does this mean?</span></span>

<span data-ttu-id="4da16-174">組織のプライベート WAN 接続がある場合は、次のいずれかの場所でインターネットへのネットワーク出口を備えた中国のオフィスの場所からネットワーク WAN 回線を構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4da16-174">If your organization has private WAN connectivity, we recommend configuring a network WAN circuit from your office locations in China that has network egress to the Internet in any of the following locations:</span></span>

- <span data-ttu-id="4da16-175">香港特別行政区</span><span class="sxs-lookup"><span data-stu-id="4da16-175">Hong Kong</span></span>
- <span data-ttu-id="4da16-176">日本</span><span class="sxs-lookup"><span data-stu-id="4da16-176">Japan</span></span>
- <span data-ttu-id="4da16-177">台湾</span><span class="sxs-lookup"><span data-stu-id="4da16-177">Taiwan</span></span>
- <span data-ttu-id="4da16-178">韓国</span><span class="sxs-lookup"><span data-stu-id="4da16-178">South Korea</span></span>
- <span data-ttu-id="4da16-179">シンガポール</span><span class="sxs-lookup"><span data-stu-id="4da16-179">Singapore</span></span>
- <span data-ttu-id="4da16-180">マレーシア</span><span class="sxs-lookup"><span data-stu-id="4da16-180">Malaysia</span></span>

<span data-ttu-id="4da16-181">このような場所を超えるユーザーからのインターネット出口はパフォーマンスを低下させ、中国での出口によって、クロスボーダー輻輳が発生して遅延と接続の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4da16-181">Internet egress further away from users than these locations will reduce performance, and egress in China may cause high latency and connectivity issues due to cross-border congestion.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="4da16-182">どうすればよいですか?</span><span class="sxs-lookup"><span data-stu-id="4da16-182">What should I do?</span></span>

<span data-ttu-id="4da16-183">この洞察に関連するパフォーマンスの問題を軽減する方法の詳細については、「 [Office 365 グローバルテナントパフォーマンスの最適化 (中国ユーザー向け](https://docs.microsoft.com/office365/enterprise/office-365-networking-china))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4da16-183">For more information about how to mitigate performance issues related to this insight, see [Office 365 global tenant performance optimization for China users](https://docs.microsoft.com/office365/enterprise/office-365-networking-china).</span></span>

## <a name="related-topics"></a><span data-ttu-id="4da16-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="4da16-184">Related topics</span></span>

[<span data-ttu-id="4da16-185">Microsoft 365 管理センター (プレビュー) でのネットワークパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="4da16-185">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="4da16-186">Microsoft 365 ネットワーク評価 (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="4da16-186">Microsoft 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="4da16-187">M365 管理センターの Microsoft 365 ネットワークオンボードツール (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="4da16-187">Microsoft 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)

[<span data-ttu-id="4da16-188">Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="4da16-188">Microsoft 365 Network Connectivity Location Services (preview)</span></span>](office-365-network-mac-location-services.md)
