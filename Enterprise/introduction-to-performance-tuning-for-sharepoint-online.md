---
title: SharePoint Online のパフォーマンス チューニングの概要
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: この記事では、SharePoint Online で最適なパフォーマンスを得るためにページを設計するときに考慮する必要がある具体的な事柄について説明します。
ms.openlocfilehash: 3c2c6ccc58659aceaaf831b97eb8c4c05141afce
ms.sourcegitcommit: fa900775790eb369db1983cd3868b628b699f145
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033403"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="a15ed-103">SharePoint Online のパフォーマンス チューニングの概要</span><span class="sxs-lookup"><span data-stu-id="a15ed-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="a15ed-104">この記事では、SharePoint Online で最適なパフォーマンスを得るためにページを設計するときに考慮する必要がある具体的な事柄について説明します。</span><span class="sxs-lookup"><span data-stu-id="a15ed-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="a15ed-105">SharePoint Online の指標</span><span class="sxs-lookup"><span data-stu-id="a15ed-105">SharePoint Online metrics</span></span>

<span data-ttu-id="a15ed-106">次の広範な SharePoint Online の指標は、パフォーマンスに関する現実世界のデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="a15ed-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="a15ed-107">高速ページの読み込み方法</span><span class="sxs-lookup"><span data-stu-id="a15ed-107">How fast pages load</span></span>
    
- <span data-ttu-id="a15ed-108">ページごとに必要なラウンドトリップの数</span><span class="sxs-lookup"><span data-stu-id="a15ed-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="a15ed-109">サービスに関する問題</span><span class="sxs-lookup"><span data-stu-id="a15ed-109">Issues with the service</span></span>
    
- <span data-ttu-id="a15ed-110">パフォーマンス低下の原因となるその他の要因</span><span class="sxs-lookup"><span data-stu-id="a15ed-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="a15ed-111">データのために到着した結論</span><span class="sxs-lookup"><span data-stu-id="a15ed-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="a15ed-112">データは次のように伝えます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-112">The data tells us:</span></span>
  
- <span data-ttu-id="a15ed-113">ほとんどのページは SharePoint Online で適切に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="a15ed-114">カスタマイズされていないページは、非常に短時間で読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="a15ed-115">OneDrive for Business、チームサイト、およびシステムページ (_layouts など) はすべてすぐに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="a15ed-116">SharePoint Online のページのうち、最低でも1% の負荷は、5000ミリ秒を超えると読み込みが行われます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="a15ed-117">1つの簡単なベンチマークテストを使用して、OneDrive for Business のホームページの読み込み時間と、カスタマイズされた一部の機能を使用することで、パフォーマンスを測定できます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-117">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features.</span></span> <span data-ttu-id="a15ed-118">これは、多くの場合、ネットワークパフォーマンスの問題をトラブルシューティングするときに完了することを求める最初の手順のサポートになります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-118">This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="a15ed-119">パフォーマンスをチェックするときに標準ユーザーアカウントを使用する</span><span class="sxs-lookup"><span data-stu-id="a15ed-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="a15ed-120">サイトコレクション管理者、サイト所有者、編集者、または投稿者は、追加のセキュリティグループに属し、追加のアクセス許可が与えられるため、SharePoint がページに読み込む追加要素を持つことになります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="a15ed-121">これは、オンプレミスの sharepoint と SharePoint Online に適用されますが、オンプレミスのシナリオでは、相違点は SharePoint Online のように簡単にはわかりません。</span><span class="sxs-lookup"><span data-stu-id="a15ed-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="a15ed-122">ユーザーに対してページがどのように実行されるかを正しく評価するには、標準のユーザーアカウントを使用して、作成コントロールおよびセキュリティグループに関連する追加のトラフィックを読み込まないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="a15ed-123">パフォーマンスチューニングの接続カテゴリ</span><span class="sxs-lookup"><span data-stu-id="a15ed-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="a15ed-124">サーバーとユーザーの間の接続を、3つの主要なコンポーネントに分類できます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-124">You can categorize the connections between the server and the user into three main components.</span></span> <span data-ttu-id="a15ed-125">読み込み時間についての洞察を得るために SharePoint Online ページを設計する場合は、これらを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="a15ed-125">Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="a15ed-126">**サーバー**Microsoft がデータセンターでホストするサーバー。</span><span class="sxs-lookup"><span data-stu-id="a15ed-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="a15ed-127">**ネットワーク**データセンターとユーザーの間の Microsoft ネットワーク、インターネット、およびオンプレミスネットワーク。</span><span class="sxs-lookup"><span data-stu-id="a15ed-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="a15ed-128">**ブラウザー**ページが読み込まれている場所。</span><span class="sxs-lookup"><span data-stu-id="a15ed-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="a15ed-129">これら3つの接続では、通常、5つの理由で、低速ページの95% が発生します。</span><span class="sxs-lookup"><span data-stu-id="a15ed-129">Within these three connections there are typically five reasons that cause 95% of slow pages.</span></span> <span data-ttu-id="a15ed-130">この記事では、これらの各理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="a15ed-130">Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="a15ed-131">ナビゲーションの問題</span><span class="sxs-lookup"><span data-stu-id="a15ed-131">Navigation issues</span></span>
    
- <span data-ttu-id="a15ed-132">コンテンツロールアップ</span><span class="sxs-lookup"><span data-stu-id="a15ed-132">Content roll up</span></span>
    
- <span data-ttu-id="a15ed-133">大きなファイル</span><span class="sxs-lookup"><span data-stu-id="a15ed-133">Large files</span></span>
    
- <span data-ttu-id="a15ed-134">サーバーへの多くの要求</span><span class="sxs-lookup"><span data-stu-id="a15ed-134">Many requests to the server</span></span>
    
- <span data-ttu-id="a15ed-135">Web パーツの処理</span><span class="sxs-lookup"><span data-stu-id="a15ed-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="a15ed-136">サーバー接続</span><span class="sxs-lookup"><span data-stu-id="a15ed-136">Server connection</span></span>

<span data-ttu-id="a15ed-137">SharePoint オンプレミスのパフォーマンスに影響する問題の多くは、SharePoint Online にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="a15ed-138">ご想像のとおり、サーバーがオンプレミスの SharePoint で実行する方法をより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-138">As you would expect, you have far more control over how servers perform with on-premises SharePoint.</span></span> <span data-ttu-id="a15ed-139">SharePoint Online は少し異なります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-139">With SharePoint Online things are a little different.</span></span> <span data-ttu-id="a15ed-140">サーバーに対して実行する作業が多いほど、ページの表示に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-140">The more work you make a server do, the longer it takes to render a page.</span></span> <span data-ttu-id="a15ed-141">SharePoint では、この点で最も大きな原因は、複数の web パーツを持つ複雑なページです。</span><span class="sxs-lookup"><span data-stu-id="a15ed-141">With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="a15ed-142">オンプレミスの SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="a15ed-142">SharePoint Server on-premises</span></span>
  
![オンプレミスのサーバーのスクリーンショット](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="a15ed-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a15ed-144">SharePoint Online</span></span>
  
![オンラインのサーバーのスクリーンショット](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="a15ed-146">SharePoint Online では、特定のページ要求が、実際には複数のサーバーを呼び出すことがあります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-146">With SharePoint Online, certain page requests may actually end up calling multiple servers.</span></span> <span data-ttu-id="a15ed-147">個々の要求について、サーバー間の要求のマトリックスが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-147">You could end up with a matrix of requests between servers for an individual request.</span></span> <span data-ttu-id="a15ed-148">これらの相互作用は、ページの読み込みの観点から費用がかかり、処理が遅くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-148">These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="a15ed-149">これらのサーバー間の相互作用の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a15ed-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="a15ed-150">Web サーバーと SQL Server</span><span class="sxs-lookup"><span data-stu-id="a15ed-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="a15ed-151">Web からアプリケーションサーバーへ</span><span class="sxs-lookup"><span data-stu-id="a15ed-151">Web to application servers</span></span>
    
<span data-ttu-id="a15ed-152">他にも、サーバーとの通信を遅くすることができますが、キャッシュミスがあります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-152">The other thing that can slow down server interactions is cache misses.</span></span> <span data-ttu-id="a15ed-153">オンプレミスの SharePoint とは異なり、以前に参照したページに対して同じサーバーがヒットする可能性が非常にスリムになります。これにより、オブジェクトキャッシュは廃止されます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-153">Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="a15ed-154">ネットワーク接続</span><span class="sxs-lookup"><span data-stu-id="a15ed-154">Network connection</span></span>

<span data-ttu-id="a15ed-155">WAN を使用していないオンプレミスの SharePoint では、データセンターとエンドユーザーの間で高速接続を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-155">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users.</span></span> <span data-ttu-id="a15ed-156">一般的に、ネットワークの観点からは管理が容易です。</span><span class="sxs-lookup"><span data-stu-id="a15ed-156">Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="a15ed-157">SharePoint Online では、いくつかの要素を考慮する必要があります。例えば：</span><span class="sxs-lookup"><span data-stu-id="a15ed-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="a15ed-158">Microsoft ネットワーク</span><span class="sxs-lookup"><span data-stu-id="a15ed-158">The Microsoft network</span></span>
    
- <span data-ttu-id="a15ed-159">インターネット</span><span class="sxs-lookup"><span data-stu-id="a15ed-159">The Internet</span></span>
    
- <span data-ttu-id="a15ed-160">ISP</span><span class="sxs-lookup"><span data-stu-id="a15ed-160">The ISP</span></span>
    
<span data-ttu-id="a15ed-161">どのバージョンの SharePoint (およびどのネットワーク) を使用しているかに関係なく、通常、ネットワークのビジー状態になるのは次のような状況です。</span><span class="sxs-lookup"><span data-stu-id="a15ed-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="a15ed-162">大きなペイロード</span><span class="sxs-lookup"><span data-stu-id="a15ed-162">Large payload</span></span>
    
- <span data-ttu-id="a15ed-163">多くのファイル</span><span class="sxs-lookup"><span data-stu-id="a15ed-163">Many files</span></span>
    
- <span data-ttu-id="a15ed-164">サーバーへの物理的な距離が大きい</span><span class="sxs-lookup"><span data-stu-id="a15ed-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="a15ed-165">SharePoint Online で利用できる機能の1つに、Microsoft CDN (コンテンツ配信ネットワーク) があります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-165">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network).</span></span> <span data-ttu-id="a15ed-166">CDN は基本的に、複数のデータセンターにまたがって展開されたサーバーの分散コレクションです。</span><span class="sxs-lookup"><span data-stu-id="a15ed-166">A CDN is basically a distributed collection of servers deployed across multiple datacenters.</span></span> <span data-ttu-id="a15ed-167">CDN を使用すると、クライアントが元の SharePoint サーバーから離れている場合でも、ページ上のコンテンツをクライアントに近いサーバーでホストできます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-167">With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server.</span></span> <span data-ttu-id="a15ed-168">Microsoft では、カスタマイズできないページのローカルインスタンス (SharePoint Online 管理者のホームページなど) を格納するために、今後もこれを使用しています。</span><span class="sxs-lookup"><span data-stu-id="a15ed-168">Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page.</span></span> <span data-ttu-id="a15ed-169">CDNs の詳細については、「[コンテンツ配信ネットワーク](https://docs.microsoft.com/office365/enterprise/content-delivery-networks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a15ed-169">For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="a15ed-170">知っておく必要があるものの、多くのことを行うことができないものは、ISP の接続速度です。</span><span class="sxs-lookup"><span data-stu-id="a15ed-170">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP.</span></span> <span data-ttu-id="a15ed-171">簡単なスピードテストツールを使用すると、接続速度がわかります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-171">A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="a15ed-172">ブラウザー接続</span><span class="sxs-lookup"><span data-stu-id="a15ed-172">Browser connection</span></span>

<span data-ttu-id="a15ed-173">パフォーマンスの観点から、web ブラウザーについて考慮するいくつかの要因があります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="a15ed-174">複雑なページにアクセスすると、パフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="a15ed-174">Visiting complex pages will affect performance.</span></span> <span data-ttu-id="a15ed-175">ほとんどのブラウザーでは、25 mb (約 90 MB) のキャッシュしかありませんが、平均的な web ページは通常 1.6 MB です。</span><span class="sxs-lookup"><span data-stu-id="a15ed-175">Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB.</span></span> <span data-ttu-id="a15ed-176">これを使用するには時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-176">This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="a15ed-177">また、帯域幅が問題になることもあります。</span><span class="sxs-lookup"><span data-stu-id="a15ed-177">Bandwidth may also be an issue.</span></span> <span data-ttu-id="a15ed-178">たとえば、ユーザーが別のセッションのビデオを視聴している場合、SharePoint ページのパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="a15ed-178">For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page.</span></span> <span data-ttu-id="a15ed-179">ユーザーがメディアをストリーミングするのを防ぐことはできませんが、ユーザーに対してページを読み込む方法を制御することができます。</span><span class="sxs-lookup"><span data-stu-id="a15ed-179">While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="a15ed-180">最適なパフォーマンスを実現するのに役立つ、SharePoint Online ページのカスタマイズ方法やその他のベストプラクティスについては、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a15ed-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="a15ed-181">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="a15ed-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="a15ed-182">SharePoint Online のページ診断ツールを使用する</span><span class="sxs-lookup"><span data-stu-id="a15ed-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="a15ed-183">SharePoint Online のイメージの最適化</span><span class="sxs-lookup"><span data-stu-id="a15ed-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="a15ed-184">SharePoint Online での画像の読み込み遅延と JavaScript</span><span class="sxs-lookup"><span data-stu-id="a15ed-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="a15ed-185">SharePoint Online での縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="a15ed-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="a15ed-186">コンテンツ配信ネットワークの使用</span><span class="sxs-lookup"><span data-stu-id="a15ed-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="a15ed-187">SharePoint Online のパフォーマンスを向上させるために、コンテンツのクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用する</span><span class="sxs-lookup"><span data-stu-id="a15ed-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="a15ed-188">SharePoint Online のキャパシティ プランニングとロード テスト</span><span class="sxs-lookup"><span data-stu-id="a15ed-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="a15ed-189">SharePoint Online のパフォーマンスの問題の診断</span><span class="sxs-lookup"><span data-stu-id="a15ed-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="a15ed-190">SharePoint Online でのオブジェクトキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="a15ed-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="a15ed-191">方法:SharePoint Online で調整またはブロックを回避する</span><span class="sxs-lookup"><span data-stu-id="a15ed-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/library/office/dn889829.aspx)
    

