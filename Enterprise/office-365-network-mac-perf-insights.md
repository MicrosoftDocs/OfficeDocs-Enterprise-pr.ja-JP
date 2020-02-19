---
title: Office 365 network performance insights (プレビュー)
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
description: Office 365 network performance insights (プレビュー)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106380"
---
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="a2c4d-103">Office 365 network performance insights (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="a2c4d-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="a2c4d-104">Microsoft 365 管理センターのネットワークパフォーマンスページには、office の場所のネットワーク境界を設計するのに役立つ Office 365 ネットワークの洞察が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="a2c4d-105">各オフィスの場所に対して表示される可能性のある特定のネットワーク洞察が5つあります。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a2c4d-106">Microsoft 365 管理センターでのネットワークパフォーマンスの推奨事項、洞察、評価は現在プレビュー状態であり、機能プレビュープログラムに登録されている Office 365 テナントに対してのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="a2c4d-107">Backhauled ネットワークの出口</span><span class="sxs-lookup"><span data-stu-id="a2c4d-107">Backhauled network egress</span></span>

<span data-ttu-id="a2c4d-108">ユーザーの場所からネットワーク出口への距離は500マイル (800 km) を超えるため、パフォーマンスに影響を与えることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="a2c4d-109">ユーザーに近いローカル出口をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="a2c4d-110">これは、オフィスの場所とネットワーク出口との間の距離が500マイルを超えていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="a2c4d-111">Office の場所は難読化されたクライアントコンピューターの場所で識別され、ネットワークの出口の場所は、逆引き IP アドレスを使用して場所データベースに識別されます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="a2c4d-112">Windows ロケーションサービスがコンピューターで無効になっている場合は、office の場所が不正確になることがあります。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="a2c4d-113">逆引き IP アドレスデータベースの情報が正確でない場合は、ネットワークの出口の場所が不正確になることがあります。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="a2c4d-114">この洞察の詳細には、オフィスの場所、ネットワークの出口の場所、およびそれらの間の距離が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="a2c4d-115">この情報については、office の場所へのネットワーク出口をお勧めします。これにより、インターネット上の Microsoft ネットワークと Office 365 service のフロントドアに、接続が最適に Microsoft のネットワークにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="a2c4d-116">また、ユーザーのオフィスの場所にネットワークを閉じることにより、将来的に、ネットワークポイントのプレゼンスと Office 365 サービスのフロントドアの両方が将来的に展開されるため、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="a2c4d-117">この洞察は、一部の要約ビューで "出口" として短縮されています。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="a2c4d-118">近距離のお客様のためのパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="a2c4d-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="a2c4d-119">このオフィスの場所では、組織内のユーザーに比べて、メトロエリア内の顧客数が多いため、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="a2c4d-120">これは、このオフィスの場所と同じ都市にある Office 365 の顧客の総合的なパフォーマンスを見ます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![ネットワークの相対パフォーマンス](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="a2c4d-122">同じ都市にある Office 365 のお客様の割合を、パフォーマンスのバケットが向上するように計算します。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="a2c4d-123">この数値が10% を超える場合は、ネットワークの洞察が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="a2c4d-124">この洞察は、一部の概要ビューでは "ピア" として短縮されています。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="a2c4d-125">Exchange Online サービスのフロントドアの非最適な使用</span><span class="sxs-lookup"><span data-stu-id="a2c4d-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="a2c4d-126">ユーザーが Office 365 の最適なフロントドアに接続しておらず、パフォーマンスに影響を与えることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="a2c4d-127">適切なパフォーマンスを備えた、office の場所の都市からの使用に適した Exchange Online サービスのフロントドアをリストしています。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="a2c4d-128">現在のテストで、この一覧にない Exchange Online サービスのフロントドアの使用が示されている場合は、この推奨事項を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="a2c4d-129">Exchange Online サービスのフロントドアを使用していない場合は、企業ネットワークの出口の前にネットワークのバックアウトが原因で、ローカルと直接のネットワーク出口が推奨されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="a2c4d-130">また、リモート DNS の再帰リゾルバーサーバーを使用して、DNS の再帰リゾルバーサーバーをネットワークの出口に配置することが推奨される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="a2c4d-131">この洞察は、一部の概要ビューに "ルーティング" として短縮されています。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="a2c4d-132">最適でない SharePoint Online サービスのフロントドアの使用</span><span class="sxs-lookup"><span data-stu-id="a2c4d-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="a2c4d-133">ユーザーが最も近い SharePoint Online サービスのフロントドアに接続していません。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="a2c4d-134">これはパフォーマンスに影響を与えることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="a2c4d-135">テストクライアントが接続している SharePoint Online サービスのフロントドアを特定します。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="a2c4d-136">次に、オフィスの所在地の市区町村に対して、その都市に対して予想される SharePoint Online サービスのフロントドアと比較します。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="a2c4d-137">一致しない場合は、この推奨事項を行います。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="a2c4d-138">この洞察は、一部の要約ビューでは "Afd" と略記されています。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="a2c4d-139">SharePoint フロントドアからのダウンロード速度が低い</span><span class="sxs-lookup"><span data-stu-id="a2c4d-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="a2c4d-140">Sub 最適なネットワークダウンロード速度が検出され、OneDrive for Business からドキュメントを読み込むのにかかる時間に影響します。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="a2c4d-141">ユーザーが SharePoint Online と OneDrive for business サービスのフロントドアから取得できるダウンロード速度は、1秒あたりのメガバイト数 (MBps) で測定されます。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="a2c4d-142">この値が 1 Mb 未満の場合は、この洞察を提供します。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="a2c4d-143">ユーザーが帯域幅を取得することができるダウンロード速度を向上させるには、帯域幅を増やす必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="a2c4d-144">または、オフィスの場所と SharePoint Online サービスのフロントドアで、ユーザーのコンピューター間にネットワークの輻輳が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="a2c4d-145">これは、congestive 損失とも呼ばれ、十分な帯域幅が利用可能な場合でも、ユーザーが使用できるダウンロード速度を制限します。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="a2c4d-146">この洞察は、一部の要約ビューで "スループット" と短縮されています。</span><span class="sxs-lookup"><span data-stu-id="a2c4d-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a2c4d-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2c4d-147">Related topics</span></span>

[<span data-ttu-id="a2c4d-148">Microsoft 365 管理センター (プレビュー) でのネットワークパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="a2c4d-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="a2c4d-149">Office 365 ネットワーク評価 (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="a2c4d-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="a2c4d-150">M365 管理センターの Office 365 ネットワークオンボードツール (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="a2c4d-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
