---
title: SharePoint Online モダンポータルサイトの制限
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/9/2019
audience: Admin
ms.topic: interactive-tutorial
ms.service: o365-administration
localization_priority: Normal
ms.collection: Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
description: SharePoint Online のモダンサイトのパフォーマンスに関する推奨事項について説明します。
ms.openlocfilehash: 0f54520faaefcdfc66d10430c8d2a646696fc52b
ms.sourcegitcommit: 74b6d9fc3ce0873e8564fc4de51fe3afeb122447
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2019
ms.locfileid: "37441074"
---
# <a name="sharepoint-online-modern-portal-site-limits"></a><span data-ttu-id="f88a7-103">SharePoint Online モダンポータルサイトの制限</span><span class="sxs-lookup"><span data-stu-id="f88a7-103">SharePoint Online modern portal site limits</span></span>

<span data-ttu-id="f88a7-104">この記事では、SharePoint Online のモダンポータルサイトのパフォーマンスに関する推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="f88a7-104">This article provides performance recommendations for modern portal sites in SharePoint Online.</span></span> <span data-ttu-id="f88a7-105">この記事のガイドラインを使用して、最新のポータルサイトのパフォーマンスを最適化し、一般的なパフォーマンスの問題を回避します。</span><span class="sxs-lookup"><span data-stu-id="f88a7-105">Use the guidelines in this article to optimize modern portal site performance and avoid common performance issues.</span></span>

## <a name="performance-considerations-for-modern-portal-sites"></a><span data-ttu-id="f88a7-106">モダンポータルサイトのパフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="f88a7-106">Performance considerations for modern portal sites</span></span>

<span data-ttu-id="f88a7-107">パフォーマンスの最適化の観点から、モダンポータルサイトを一意にするためのいくつかの特性があります。</span><span class="sxs-lookup"><span data-stu-id="f88a7-107">From the standpoint of performance optimization, there are a few characteristics that make modern portal sites unique.</span></span> <span data-ttu-id="f88a7-108">SharePoint Online のグループ作業とポータルサイトの主な違いはスケールです。</span><span class="sxs-lookup"><span data-stu-id="f88a7-108">The principal difference between collaboration and portal sites in SharePoint Online is scale.</span></span> <span data-ttu-id="f88a7-109">一般に、ポータルサイトでは、グループ作業サイトより多くのユーザーに対してより多くのページビューを提供することが期待されます。多くの場合、より多くの静的コンテンツと編集可能なリソースが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f88a7-109">Portal sites are generally expected to serve more page views to a greater number of users than collaboration sites, and are likely to contain more static content and fewer editable resources.</span></span> <span data-ttu-id="f88a7-110">さらに、モダンサイトのアーキテクチャは従来のサイトとは異なります。これは、レンダリングページに含まれる処理のほとんどが、サーバーではなくクライアントで行われることです。</span><span class="sxs-lookup"><span data-stu-id="f88a7-110">Additionally, the architecture of modern sites differs from classic sites in that most of the processing involved in rendering pages and executing code takes place on the client rather than the server.</span></span>

<span data-ttu-id="f88a7-111">モダンポータルサイトのパフォーマンスの最適化は、主にいくつかの全体的な目標に重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="f88a7-111">Performance optimization for modern portal sites is primarily focused on a few overall objectives:</span></span>

- <span data-ttu-id="f88a7-112">各サイトページのコンポーネントの合計サイズを小さくする</span><span class="sxs-lookup"><span data-stu-id="f88a7-112">Reduce the total size of the components of each site page</span></span>
- <span data-ttu-id="f88a7-113">画像、スタイルシート、スクリプトなどの一般的な静的ファイルを CDN にオフロードする</span><span class="sxs-lookup"><span data-stu-id="f88a7-113">Offload hosting of common static files such as images, stylesheets and scripts to CDN</span></span>
- <span data-ttu-id="f88a7-114">SharePoint および外部エンドポイントへの呼び出しを、必要なものだけに制限する</span><span class="sxs-lookup"><span data-stu-id="f88a7-114">Limit calls to SharePoint and external endpoints to only what is necessary</span></span>
- <span data-ttu-id="f88a7-115">同じコンテンツに対して重複する要求を回避する</span><span class="sxs-lookup"><span data-stu-id="f88a7-115">Avoid duplicate requests for the same content</span></span>

<span data-ttu-id="f88a7-116">この記事のガイドラインの多くは、SharePoint Online への呼び出しを最小限に抑え、最適化することに重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="f88a7-116">Many of the guidelines in this article focus on minimizing and optimizing calls to SharePoint Online.</span></span> <span data-ttu-id="f88a7-117">ページが読み込まれるたびに反復呼び出しを行うと、情報が変更されていない場合でも、その情報が毎回サービスから取得されるため、ユーザーのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="f88a7-117">Making repetitive calls each time a page is loaded will impact performance for users as the information will be retrieved from the service each time even if it has not changed.</span></span> <span data-ttu-id="f88a7-118">そのため、SharePoint への要求は、すべてのユーザーに共通の呼び出しとして、または個々のユーザーごとに必要な呼び出しとして分類できます。</span><span class="sxs-lookup"><span data-stu-id="f88a7-118">As such, requests to SharePoint can be categorized either as calls that are common for all users or calls required for each individual user.</span></span> <span data-ttu-id="f88a7-119">これらの2つの呼び出しカテゴリからの結果は、ユーザーの利便性を最適化するためにキャッシュする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f88a7-119">Results from these two call categories should be cached to optimize the user experience.</span></span>

>[!NOTE]
><span data-ttu-id="f88a7-120">Sharepoint Online サイトページで特定のパフォーマンス指標を分析するための開始点として、 [sharepoint 用ページ診断ツール](https://aka.ms/perftool)を使用します。</span><span class="sxs-lookup"><span data-stu-id="f88a7-120">Use the [Page Diagnostics for SharePoint tool](https://aka.ms/perftool) as a starting point to analyze specific performance metrics on SharePoint Online site pages.</span></span>

## <a name="modern-portal-site-limits-and-recommendations"></a><span data-ttu-id="f88a7-121">モダンポータルサイトの制限と推奨事項</span><span class="sxs-lookup"><span data-stu-id="f88a7-121">Modern portal site limits and recommendations</span></span>

|<span data-ttu-id="f88a7-122">**制限**</span><span class="sxs-lookup"><span data-stu-id="f88a7-122">**Limit**</span></span>|<span data-ttu-id="f88a7-123">**推奨される最大値**</span><span class="sxs-lookup"><span data-stu-id="f88a7-123">**Maximum recommended value**</span></span>|<span data-ttu-id="f88a7-124">**注**</span><span class="sxs-lookup"><span data-stu-id="f88a7-124">**Notes**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="f88a7-125">ページとニュースアイテム</span><span class="sxs-lookup"><span data-stu-id="f88a7-125">Pages and news items</span></span>  <br/> |<span data-ttu-id="f88a7-126">サイトごとに 5,000 件</span><span class="sxs-lookup"><span data-stu-id="f88a7-126">5,000 per site</span></span>  <br/> |<span data-ttu-id="f88a7-127">モダンポータルサイトのページ数とニュースアイテム数を5000以下に制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f88a7-127">We recommend limiting the number of pages and news items in a modern portal site to below 5,000.</span></span>  <br/> |
|<span data-ttu-id="f88a7-128">ページ上の Web パーツ</span><span class="sxs-lookup"><span data-stu-id="f88a7-128">Web parts on a page</span></span>  <br/> |<span data-ttu-id="f88a7-129">ページごとに20個</span><span class="sxs-lookup"><span data-stu-id="f88a7-129">20 per page</span></span>  <br/> |<span data-ttu-id="f88a7-130">標準の Microsoft web パーツとカスタム web パーツの両方を含む、ページごとに20以下の web パーツを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f88a7-130">We recommend using 20 or fewer total web parts per page, including both out-of-the-box Microsoft web parts and custom web parts.</span></span> <br/> <span data-ttu-id="f88a7-131">詳細については、「 [SharePoint Online モダンサイトページで web パーツのパフォーマンスを最適化](modern-web-part-optimization.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f88a7-131">For more information, see [Optimize web part performance in SharePoint Online modern site pages](modern-web-part-optimization.md).</span></span>  <br/> |
|<span data-ttu-id="f88a7-132">ページ上の動的 web パーツ</span><span class="sxs-lookup"><span data-stu-id="f88a7-132">Dynamic web parts on a page</span></span>  <br/> |<span data-ttu-id="f88a7-133">ページごとに4個</span><span class="sxs-lookup"><span data-stu-id="f88a7-133">4 per page</span></span>  <br/> |<span data-ttu-id="f88a7-134">SharePoint に対して1つ以上のクエリを作成して最新のデータをフェッチする動的 web パーツは、1ページあたり4個に制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f88a7-134">Dynamic web parts that make one or more queries to SharePoint to fetch the latest data should be limited to 4 per page.</span></span> <span data-ttu-id="f88a7-135">_ニュース_web パーツは、動的な web パーツの例です。</span><span class="sxs-lookup"><span data-stu-id="f88a7-135">The _News_ web part is an example of a dynamic web part.</span></span> <br/> <span data-ttu-id="f88a7-136">詳細については、「 [SharePoint Online モダンサイトページで web パーツのパフォーマンスを最適化](modern-web-part-optimization.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f88a7-136">For more information, see [Optimize web part performance in SharePoint Online modern site pages](modern-web-part-optimization.md).</span></span>    <br/> |
|<span data-ttu-id="f88a7-137">セキュリティ グループ</span><span class="sxs-lookup"><span data-stu-id="f88a7-137">Security groups</span></span>  <br/> |<span data-ttu-id="f88a7-138">サイトごとに20個</span><span class="sxs-lookup"><span data-stu-id="f88a7-138">20 per site</span></span>  <br/> |<span data-ttu-id="f88a7-139">セキュリティグループの数は、モダンポータルサイトの多くのクエリのスケールに影響します。</span><span class="sxs-lookup"><span data-stu-id="f88a7-139">The number of security groups affects the scale of many queries in modern portal sites.</span></span> <span data-ttu-id="f88a7-140">セキュリティグループの数は、サイトごとに20を超えないように、できるだけ小さなセットに制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f88a7-140">We recommend that you limit the number of security groups to as small a set as possible, with no more than 20 per site.</span></span>  <br/> |
|<span data-ttu-id="f88a7-141">サイトナビゲーション内のアイテム</span><span class="sxs-lookup"><span data-stu-id="f88a7-141">Items in site navigation</span></span>  <br/> |<span data-ttu-id="f88a7-142">サイトごとに100</span><span class="sxs-lookup"><span data-stu-id="f88a7-142">100 per site</span></span>  <br/> |<span data-ttu-id="f88a7-143">サイトナビゲーションには100未満のアイテムを追加し、すぐに使用できるナビゲーションコントロールを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f88a7-143">We recommend adding fewer than 100 items to site navigation, and that you make use of out-of-the-box navigation controls.</span></span>  <br/> <span data-ttu-id="f88a7-144">詳細については、「 [SharePoint Online モダンサイトページでページのウエイトを最適化](modern-page-weight-optimization.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f88a7-144">For more information, see [Optimize page weight in SharePoint Online modern site pages](modern-page-weight-optimization.md).</span></span> <br/> |
|<span data-ttu-id="f88a7-145">画像の最大サイズ</span><span class="sxs-lookup"><span data-stu-id="f88a7-145">Maximum image size</span></span>  <br/> |<span data-ttu-id="f88a7-146">画像ごとに 300 Kb</span><span class="sxs-lookup"><span data-stu-id="f88a7-146">300 Kb per image</span></span>  <br/> |<span data-ttu-id="f88a7-147">画像のサイズを300kb 以下に制限し、CDN を使用して画像、スタイルシート、スクリプトをホストすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f88a7-147">We recommend limiting the size of images to 300kb or smaller, and using a CDN to host images, stylesheets and scripts.</span></span> <br/><span data-ttu-id="f88a7-148">詳細については、「 [Sharepoint online モダンサイトページで画像を最適化](modern-image-optimization.md)する」と「 [Sharepoint online で Office 365 コンテンツ配信ネットワーク (CDN) を使用する](use-office-365-cdn-with-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f88a7-148">For more information, see [Optimize images in SharePoint Online modern site pages](modern-image-optimization.md) and [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>  <br/> |
|<span data-ttu-id="f88a7-149">編集権限を持つユーザー</span><span class="sxs-lookup"><span data-stu-id="f88a7-149">Users with edit rights</span></span>  <br/> |<span data-ttu-id="f88a7-150">サイトごとに200ユーザー</span><span class="sxs-lookup"><span data-stu-id="f88a7-150">200 users per site</span></span>  <br/> |<span data-ttu-id="f88a7-151">SharePoint ポータルサイトは、コンテンツを表示および使用できるように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="f88a7-151">SharePoint portal sites are optimized for viewing and consuming content.</span></span> <span data-ttu-id="f88a7-152">[編集] アクセス許可は、追加のコントロールをダウンロードするため、アクセス許可を制限するユーザーのグループに制限する必要があります。そのため、これらのユーザーに対しては実行速度が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="f88a7-152">Edit permissions on a portal should be limited to a restricted group of users because edit permissions download additional controls and will therefore perform slower for those users.</span></span> <span data-ttu-id="f88a7-153">このため、編集アクセス許可を持つユーザーの数が多すぎると、全体的な操作に影響します。</span><span class="sxs-lookup"><span data-stu-id="f88a7-153">An excessive number of users with edit permissions will therefore affect the overall experience.</span></span> <br/> |
|<span data-ttu-id="f88a7-154">サードパーティの Iframe</span><span class="sxs-lookup"><span data-stu-id="f88a7-154">Third party iFrames</span></span>  <br/> |<span data-ttu-id="f88a7-155">ページごとに2個</span><span class="sxs-lookup"><span data-stu-id="f88a7-155">2 per page</span></span>  <br/> |<span data-ttu-id="f88a7-156">iFrames は、javascript、CSS、フレームワーク要素などの関連付けられたすべてのコンテンツを含む個別の外部ページを読み込むため、予想には時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="f88a7-156">iFrames are unpredictably slow because they load a separate external page including all associated content such as javascript, CSS and framework elements.</span></span> <span data-ttu-id="f88a7-157">Iframe を使用する必要がある場合は、ページごとに2個以下に制限します。</span><span class="sxs-lookup"><span data-stu-id="f88a7-157">If you must use iFrames, limit their number to 2 or fewer per page.</span></span><br/> <span data-ttu-id="f88a7-158">詳細については、「 [SharePoint Online モダンおよび従来の発行サイトページで iframe を最適化](modern-iframe-optimization.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f88a7-158">For more information, see [Optimize iFrames in SharePoint Online modern and classic publishing site pages](modern-iframe-optimization.md).</span></span> <br/> |
|<span data-ttu-id="f88a7-159">UPA サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="f88a7-159">Calls to the UPA service</span></span>  <br/> |<span data-ttu-id="f88a7-160">ユーザーごとに1時間ごとに1回</span><span class="sxs-lookup"><span data-stu-id="f88a7-160">1 per user per hour</span></span>  <br/> |<span data-ttu-id="f88a7-161">UPA (User Profile Application) サービスへの_要求ごと_に電話をかけないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f88a7-161">We recommend that you make no _per request_ calls to the UPA (User Profile Application) service.</span></span> <span data-ttu-id="f88a7-162">[Microsoft GRAPH API](https://docs.microsoft.com/en-us/graph/call-api)と[pagecontext](https://docs.microsoft.com/en-us/javascript/api/sp-page-context/pagecontext?view=sp-typescript-latest)を使用して、ユーザー情報のクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f88a7-162">The [Microsoft Graph API](https://docs.microsoft.com/en-us/graph/call-api) and [PageContext](https://docs.microsoft.com/en-us/javascript/api/sp-page-context/pagecontext?view=sp-typescript-latest) can be used to query for user information.</span></span>  <br/> <span data-ttu-id="f88a7-163">UPA サービス呼び出しが必要な場合は、必要に応じて1つの呼び出しを行ってから、同じセッションで再利用するために情報をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="f88a7-163">If a UPA service call is necessary, make a single call when required, and then cache the information for reuse in the same session.</span></span> |
|<span data-ttu-id="f88a7-164">分類サービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="f88a7-164">Calls to the Taxonomy service</span></span>  <br/> |<span data-ttu-id="f88a7-165">1時間あたりのユーザーごとに5個</span><span class="sxs-lookup"><span data-stu-id="f88a7-165">5 per user per hour</span></span>  <br/> |<span data-ttu-id="f88a7-166">分類サービスへの_要求ごと_に呼び出しを行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f88a7-166">We recommend that you make no _per request_ calls to the Taxonomy service.</span></span> <span data-ttu-id="f88a7-167">分類サービスの呼び出しが必要な場合は、同じセッションで再利用するために情報をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="f88a7-167">If Taxonomy service calls are necessary, cache the information for reuse in the same session.</span></span> <br/> <span data-ttu-id="f88a7-168">詳細については、「 [SharePoint Online モダンおよび従来の発行サイトページでページ呼び出しを最適化](modern-page-call-optimization.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f88a7-168">For more information, see [Optimize page calls in SharePoint Online modern and classic publishing site pages](modern-page-call-optimization.md).</span></span> <br/> |

## <a name="related-topics"></a><span data-ttu-id="f88a7-169">関連トピック</span><span class="sxs-lookup"><span data-stu-id="f88a7-169">Related topics</span></span>

[<span data-ttu-id="f88a7-170">正常な SharePoint ポータルを作成する</span><span class="sxs-lookup"><span data-stu-id="f88a7-170">Creating a healthy SharePoint portal</span></span>](https://docs.microsoft.com/sharepoint/portal-health)

[<span data-ttu-id="f88a7-171">SharePoint Online のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="f88a7-171">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="f88a7-172">Office 365 のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="f88a7-172">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="f88a7-173">SharePoint Online の制限</span><span class="sxs-lookup"><span data-stu-id="f88a7-173">SharePoint Online limits</span></span>](https://docs.microsoft.com/en-us/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[<span data-ttu-id="f88a7-174">SharePoint のモダン エクスペリエンスにおけるパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="f88a7-174">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/en-us/sharepoint/modern-experience-performance)

[<span data-ttu-id="f88a7-175">SharePoint Online ポータル パフォーマンス ガイダンス</span><span class="sxs-lookup"><span data-stu-id="f88a7-175">Performance guidance for SharePoint Online portals</span></span>](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-performance)