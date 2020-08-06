---
title: SharePoint Online の最新および従来の発行サイト ページでページ呼び出しを最適化する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online サービス エンドポイントへの呼び出し数を制限することにより、SharePoint Onlineで最新および従来の発行サイト ページを最適化する方法を学びます。
ms.openlocfilehash: 063cf6d8c14f139f90e8bb19ca7ccd0833fc36ec
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571140"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="cb053-103">SharePoint Online の最新および従来の発行サイト ページでページ呼び出しを最適化する</span><span class="sxs-lookup"><span data-stu-id="cb053-103">Optimize page calls in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="cb053-104">SharePoint Online の最新の発行サイトと従来の発行サイトには、SharePoint 機能および CDN からデータを読み込む (またはを呼び出す) リンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cb053-104">Both SharePoint Online modern and classic publishing sites contain links that load data from (or make calls to) SharePoint features and CDNs.</span></span> <span data-ttu-id="cb053-105">ページからの呼び出しが多くなるほど、ページの読み込みには時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="cb053-105">The more calls made by a page, the longer the page takes to load.</span></span> <span data-ttu-id="cb053-106">これは、**エンドユーザーが認識する遅延**、または **EUPL (end user perceived latency)** として知られています。</span><span class="sxs-lookup"><span data-stu-id="cb053-106">This is known as **end user perceived latency** or **EUPL**.</span></span>

<span data-ttu-id="cb053-107">この記事は、最新および従来の発行サイト ページから外部エンドポイントへの呼び出しの数と影響を判断する方法、およびエンドユーザーが認識する遅延への影響を制限する方法を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cb053-107">This article will help you understand how to determine the number and impact of calls to external endpoints from your modern and classic publishing site pages and how to limit their effect on end user perceived latency.</span></span>

>[!NOTE]
><span data-ttu-id="cb053-108">Sharepoint Online の最新ポータルでのパフォーマンスの詳細については、「[SharePoint のモダン エクスペリエンスにおけるパフォーマンス](https://docs.microsoft.com/sharepoint/modern-experience-performance)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb053-108">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a><span data-ttu-id="cb053-109">SharePoint 用ページ診断ツールを使用してページ呼び出しを分析する</span><span class="sxs-lookup"><span data-stu-id="cb053-109">Use the Page Diagnostics for SharePoint tool to analyze page calls</span></span>

<span data-ttu-id="cb053-110">SharePoint 用ページ診断ツールは、新しい Microsoft Edge (https://www.microsoft.com/edge)) と Chrome のブラウザー拡張機能であり、SharePoint Online の最新ポータルと従来の発行サイト ページの両方を分析します。</span><span class="sxs-lookup"><span data-stu-id="cb053-110">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="cb053-111">このツールでは、定義されている一連のパフォーマンス条件に対するページのパフォーマンスを示す分析済みの各ページのレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb053-111">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="cb053-112">SharePoint 用ページ診断ツールのインストール方法と詳細については、「[SharePoint Online 用ページ診断ツールを使用する](page-diagnostics-for-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb053-112">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="cb053-113">ページ診断ツールは SharePoint Online でのみ機能し、SharePoint システム ページでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="cb053-113">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="cb053-114">SharePoint のサイト ページを SharePoint 用ページ診断ツールを使用して分析すると、[_診断テスト_] ウィンドウの [**SharePoint へのリクエスト**] 結果に外部呼び出しに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb053-114">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about external calls in the **Requests to SharePoint** result in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="cb053-115">サイト ページに含まれるコールの数がベースライン数より少ない場合、線は緑色で表示され、ページがベースライン数を超える場合は赤色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb053-115">The line will appear in green if the site page contains fewer than the baseline number of calls, and red if the page exceeds the baseline number.</span></span> <span data-ttu-id="cb053-116">クラシック サイト ページは HTTP1.1 を使用し、モダン ページは HTTP2.0 を使用するため、ベースライン数はモダン ページとクラシック ページで異なります。</span><span class="sxs-lookup"><span data-stu-id="cb053-116">The baseline number is different for modern and classic pages because classic site pages use HTTP1.1 and modern pages use HTTP2.0:</span></span>

- <span data-ttu-id="cb053-117">最新のサイト ページには **25** を超える呼び出しは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="cb053-117">Modern site pages should contain no more than **25** calls</span></span>
- <span data-ttu-id="cb053-118">従来の発行ページには **6** を超える呼び出しは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="cb053-118">Classic publishing pages should contain no more than **6** calls</span></span>

<span data-ttu-id="cb053-119">考えられる結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cb053-119">Possible results include:</span></span>

- <span data-ttu-id="cb053-120">**要注意** (赤): ページが呼び出しのベースライン数を超えています</span><span class="sxs-lookup"><span data-stu-id="cb053-120">**Attention required** (red): The page exceeds the baseline number of calls</span></span>
- <span data-ttu-id="cb053-121">**操作は不要** (緑): ページに含まれる呼び出しがベースライン数より少ないです</span><span class="sxs-lookup"><span data-stu-id="cb053-121">**No action required** (green): The page contains fewer than the baseline number of calls</span></span>

<span data-ttu-id="cb053-122">[**SharePoint へのリクエスト**] の結果が [**要注意**] セクションに表示されている場合は、結果をクリックして、ページ上の呼び出しの総数や URL のリストなどの詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="cb053-122">If the **Requests to SharePoint** result appears in the **Attention required** section, you can click the result for details, including the total number of calls on the page and a list of the URLs.</span></span>

![SharePoint 結果への要求](media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a><span data-ttu-id="cb053-124">ページ上の呼び出しが多すぎることに関連するパフォーマンスの問題を修復する</span><span class="sxs-lookup"><span data-stu-id="cb053-124">Remediate performance issues related to too many calls on a page</span></span>

<span data-ttu-id="cb053-125">ページに含まれる呼び出しが多すぎる場合、[**SharePoint へのリクエスト**] の結果の URL のリストを使用して、繰り返しの呼び出し、バッチ処理する必要のある呼び出し、またはキャッシュする必要のあるデータを返す呼び出しがあるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="cb053-125">If a page contains too many calls, you can use the list of URLs in the **Requests to Sharepoint** results to determine whether there are any repeated calls, calls that should be batched, or calls that return data that should be cached.</span></span>

<span data-ttu-id="cb053-126">**REST 呼び出しのバッチ処理**が、パフォーマンスのオーバーヘッド削減に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cb053-126">**Batching REST calls** can help to reduce performance overhead.</span></span> <span data-ttu-id="cb053-127">API 呼び出しのバッチ処理の詳細については、「[REST API によりバッチ要求を発行する](https://docs.microsoft.com/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb053-127">For more information about API call batching, see [Make batch requests with the REST APIs](https://docs.microsoft.com/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).</span></span>

<span data-ttu-id="cb053-128">**キャッシュを使用**して API 呼び出しの結果を保存すると、以降のページの読み込みごとに追加の呼び出しを行う代わりに、クライアントがキャッシュ データを使用できるようになるため、ウォーム リクエストのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="cb053-128">**Using a cache** to store the results of an API call can improve the performance of a warm request by allowing the client to use the cached data instead of making an additional call for each subsequent page load.</span></span> <span data-ttu-id="cb053-129">ビジネス要件に応じて、このソリューションにアプローチする方法は複数あります。</span><span class="sxs-lookup"><span data-stu-id="cb053-129">There are multiple ways to approach this solution depending on the business requirement.</span></span> <span data-ttu-id="cb053-130">通常、データがすべてのユーザーで同じ場合、ユーザーは SPO から直接ではなくキャッシュ サービスからデータを要求するため、[_Azure Redis_ キャッシュ](https://azure.microsoft.com/services/cache/)などの中間層キャッシュ サービスを使用することは、サイトに対する API トラフィックを大幅に削減する優れたオプションです。</span><span class="sxs-lookup"><span data-stu-id="cb053-130">Typically if the data will be the same for all users, using a middle-tier caching service like [_Azure Redis_ cache](https://azure.microsoft.com/services/cache/) is a great option to significantly reduce API traffic against a site, as the users would request the data from the caching service instead of directly from SPO.</span></span> <span data-ttu-id="cb053-131">必要な SPO 呼び出しは、中間層のキャッシュを更新することだけです。</span><span class="sxs-lookup"><span data-stu-id="cb053-131">The only SPO calls needed would be to refresh the middle-tier's cache.</span></span> <span data-ttu-id="cb053-132">データが個々のユーザーごとに変動する場合は、LocalStorage や Cookie などのクライアント側キャッシュを実装するのが最善かもしれません。</span><span class="sxs-lookup"><span data-stu-id="cb053-132">If the data will fluctuate on an individual user basis, it may be best to implement a client side cache, like LocalStorage or even a Cookie.</span></span> <span data-ttu-id="cb053-133">これにより、キャッシュ期間中に同じユーザーによって行われる後続のリクエストが排除されるため呼び出しの量は減少しますが、専用のキャッシュ サービスよりも効率が低下します。</span><span class="sxs-lookup"><span data-stu-id="cb053-133">This will still reduce call volumes by eliminating subsequent requests made by the same user for the cache duration, but will be less efficient than a dedicated caching service.</span></span> <span data-ttu-id="cb053-134">PnP を使用すると、追加の開発をほとんど必要とせずに LocalStorage を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cb053-134">PnP allows you to use LocalStorage with little additional development required.</span></span>

<span data-ttu-id="cb053-135">パフォーマンスの問題を修復するためにページを修正する前に、分析結果のページ読み込み時間をメモしてください。</span><span class="sxs-lookup"><span data-stu-id="cb053-135">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="cb053-136">修正後にツールをもう一度実行して新しい結果がベースライン基準内にあるかどうかを確認し、新しいページ読み込み時間をチェックして改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="cb053-136">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![ページ読み込み時間の結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="cb053-138">ページ読み込み時間は、ネットワーク負荷、時間帯、その他の一時的な状態など、さまざまな要素によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cb053-138">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="cb053-139">結果を平均化するために、変更の前後に数回に渡ってページ読み込み時間をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb053-139">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="cb053-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb053-140">Related topics</span></span>

[<span data-ttu-id="cb053-141">SharePoint Online のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="cb053-141">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="cb053-142">Office 365 のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="cb053-142">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="cb053-143">SharePoint のモダン エクスペリエンスにおけるパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="cb053-143">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="cb053-144">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="cb053-144">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="cb053-145">SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用</span><span class="sxs-lookup"><span data-stu-id="cb053-145">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
