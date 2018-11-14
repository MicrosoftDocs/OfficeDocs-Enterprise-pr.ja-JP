---
title: SharePoint Online のパフォーマンス チューニングの概要
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: この資料では、SharePoint Online での最適なパフォーマンスのページをデザインするときに考慮する必要がどのような特定の側面について説明します。
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219877"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="1758d-103">SharePoint Online のパフォーマンス チューニングの概要</span><span class="sxs-lookup"><span data-stu-id="1758d-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="1758d-104">この資料では、SharePoint Online での最適なパフォーマンスのページをデザインするときに考慮する必要がどのような特定の側面について説明します。</span><span class="sxs-lookup"><span data-stu-id="1758d-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="1758d-105">SharePoint Online のメトリックス</span><span class="sxs-lookup"><span data-stu-id="1758d-105">SharePoint Online metrics</span></span>

<span data-ttu-id="1758d-106">以下の SharePoint Online の広範なメトリックスには、パフォーマンスに関する実際のデータが記載されています。</span><span class="sxs-lookup"><span data-stu-id="1758d-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="1758d-107">ページの読み取り速度</span><span class="sxs-lookup"><span data-stu-id="1758d-107">How fast pages load</span></span>
    
- <span data-ttu-id="1758d-108">ページごとに必要なラウンド トリップの数</span><span class="sxs-lookup"><span data-stu-id="1758d-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="1758d-109">サービスの問題</span><span class="sxs-lookup"><span data-stu-id="1758d-109">Issues with the service</span></span>
    
- <span data-ttu-id="1758d-110">パフォーマンスの低下を引き起こすその他の事項</span><span class="sxs-lookup"><span data-stu-id="1758d-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="1758d-111">データからたどり着いた結論</span><span class="sxs-lookup"><span data-stu-id="1758d-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="1758d-112">データは以下を示しています。</span><span class="sxs-lookup"><span data-stu-id="1758d-112">The data tells us:</span></span>
  
- <span data-ttu-id="1758d-113">ほとんどのページは SharePoint Online で良好に動作しています。</span><span class="sxs-lookup"><span data-stu-id="1758d-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="1758d-114">カスタマイズされていないページは、非常に速く読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="1758d-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="1758d-115">OneDrive for Business、チーム サイト、_layouts などのシステムのページは、すべて速く読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="1758d-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="1758d-116">1% の最も読み込み時間が長い SharePoint Online ページは、読み込みに 5,000 ミリ秒を超える時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="1758d-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="1758d-p101">使用できる 1 つの単純なベンチマーク テストは、自社のポータルの読み込み時間と OneDrive for Business のホーム ページの読み込み時間を比較してパフォーマンスを測定することです。OneDrive for Business のホーム ページではカスタマイズ機能がほとんど使用されないためです。これは、ネットワークのパフォーマンスの問題についてのトラブルシューティングを実行する際にサポート完了のためにお願いする最初の手順になることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="1758d-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="1758d-119">パフォーマンスをチェックするときに、標準ユーザー アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="1758d-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="1758d-120">サイト コレクションの管理者、サイト所有者、エディター、または共同作成者は、追加のセキュリティ グループに属しているし、追加のアクセス許可がある SharePoint は、ページに読み込まれるその他の要素があるため。</span><span class="sxs-lookup"><span data-stu-id="1758d-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="1758d-121">これは SharePoint 設置し、SharePoint Online に適用できるが、設置型のシナリオでの違いは簡単には気づかれない SharePoint Online のように。</span><span class="sxs-lookup"><span data-stu-id="1758d-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="1758d-122">ユーザーは、ページを実行する方法を正確に評価をするためにコントロールを作成し、セキュリティ グループに関連するその他のトラフィックが読み込まれないようにするのには、標準ユーザー アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1758d-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="1758d-123">パフォーマンス チューニングの接続のカテゴリ</span><span class="sxs-lookup"><span data-stu-id="1758d-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="1758d-p102">サーバーとユーザーの間の接続は、主な 3 つのコンポーネントに分類できます。読み込み時間の見通しについて SharePoint Online ページを設計する際は、これらのコンポーネントを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="1758d-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="1758d-126">**サーバー**マイクロソフトがデータ センターでホストするサーバーです。</span><span class="sxs-lookup"><span data-stu-id="1758d-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="1758d-127">**ネットワーク**Microsoft のネットワーク、インターネット、およびデータ センターとユーザーの間で、オンプレミスのネットワークです。</span><span class="sxs-lookup"><span data-stu-id="1758d-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="1758d-128">**ブラウザー**ページが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="1758d-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="1758d-p103">これら 3 つの接続内では、一般的に、読み込み時間が長いページのうち 95% は 5 つの理由によるものです。この記事では、それぞれの理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="1758d-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="1758d-131">ナビゲーションの問題</span><span class="sxs-lookup"><span data-stu-id="1758d-131">Navigation issues</span></span>
    
- <span data-ttu-id="1758d-132">コンテンツ ロールアップ</span><span class="sxs-lookup"><span data-stu-id="1758d-132">Content roll up</span></span>
    
- <span data-ttu-id="1758d-133">大きなファイル</span><span class="sxs-lookup"><span data-stu-id="1758d-133">Large files</span></span>
    
- <span data-ttu-id="1758d-134">サーバーへの多数の要求</span><span class="sxs-lookup"><span data-stu-id="1758d-134">Many requests to the server</span></span>
    
- <span data-ttu-id="1758d-135">Web パーツの処理</span><span class="sxs-lookup"><span data-stu-id="1758d-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="1758d-136">サーバーの接続</span><span class="sxs-lookup"><span data-stu-id="1758d-136">Server connection</span></span>

<span data-ttu-id="1758d-137">オンプレミスの SharePoint でのパフォーマンスに影響する問題の多くは、SharePoint Online にも該当します。</span><span class="sxs-lookup"><span data-stu-id="1758d-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="1758d-p104">予想どおり、サーバーがオンプレミスの SharePoint で実行する内容にははるかに多くの制御があります。SharePoint Online では、作業は少し異なります。サーバーが実行する作業を多くすればするほど、ページの表示に時間がかかります。SharePoint では、この点において最大の原因は、複数の Web パーツを含む複雑なページです。</span><span class="sxs-lookup"><span data-stu-id="1758d-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="1758d-142">オンプレミスの SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="1758d-142">SharePoint Server on-premises</span></span>
  
![オンプレミスのサーバーのスクリーンショット](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="1758d-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1758d-144">SharePoint Online</span></span>
  
![オンラインのサーバーのスクリーンショット](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="1758d-p105">SharePoint Online では、特定のページの要求が、実際は複数のサーバーを呼び出すという結果になります。個別の要求に対し、結果的としてサーバー間で要求の表が生成されることがあります。この通信は、ページの読み込みの観点から費用がかかり、動作を遅くします。</span><span class="sxs-lookup"><span data-stu-id="1758d-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="1758d-149">サーバー間の通信の例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1758d-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="1758d-150">Web サーバーと SQL サーバー</span><span class="sxs-lookup"><span data-stu-id="1758d-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="1758d-151">Web サーバーとアプリケーション サーバー</span><span class="sxs-lookup"><span data-stu-id="1758d-151">Web to application servers</span></span>
    
<span data-ttu-id="1758d-p106">サーバーの通信時間が長くなるもう 1 つの原因は、キャッシュ ミスです。オンプレミスの SharePoint とは異なり、以前アクセスしたページと同じサーバーに当たる機会は非常に少なくなり、オブジェクトのキャッシュが最新ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="1758d-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="1758d-154">ネットワーク接続</span><span class="sxs-lookup"><span data-stu-id="1758d-154">Network connection</span></span>

<span data-ttu-id="1758d-p107">設置がないため、wan を使用する、データ ・ センターとエンド ・ ユーザーとの間の高速接続を使用することがあります。一般に、点は、ネットワークの観点から管理が容易です。</span><span class="sxs-lookup"><span data-stu-id="1758d-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="1758d-157">SharePoint Online では、さらにいくつか考慮する要因があります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="1758d-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="1758d-158">Microsoft ネットワーク</span><span class="sxs-lookup"><span data-stu-id="1758d-158">The Microsoft network</span></span>
    
- <span data-ttu-id="1758d-159">インターネット</span><span class="sxs-lookup"><span data-stu-id="1758d-159">The Internet</span></span>
    
- <span data-ttu-id="1758d-160">ISP</span><span class="sxs-lookup"><span data-stu-id="1758d-160">The ISP</span></span>
    
<span data-ttu-id="1758d-161">どのバージョンの SharePoint (およびどのネットワーク) を使用するかに関係なく、一般的にネットワークをビジー状態にするものには以下があります。</span><span class="sxs-lookup"><span data-stu-id="1758d-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="1758d-162">大きいペイロード</span><span class="sxs-lookup"><span data-stu-id="1758d-162">Large payload</span></span>
    
- <span data-ttu-id="1758d-163">多数のファイル</span><span class="sxs-lookup"><span data-stu-id="1758d-163">Many files</span></span>
    
- <span data-ttu-id="1758d-164">サーバーへの物理的な距離が長いこと</span><span class="sxs-lookup"><span data-stu-id="1758d-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="1758d-p108">SharePoint Online で利用できる機能の 1 つは、マイクロソフトの CDN (コンテンツ配信ネットワーク) です。CDN は、基本的に複数のデータ センターに展開サーバーの分散型のコレクションです。、CDN ではクライアントが元の SharePoint サーバーからは遠く離れている場合でもにページ上のコンテンツ クライアントにサーバーでホストできます。マイクロソフトが使用しているより、将来的にページをカスタマイズできない、たとえば、SharePoint Online 管理ホーム ページのローカル インスタンスを格納します。Cdn の詳細については、[コンテンツ配信ネットワーク](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1758d-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="1758d-p109">知っておく必要がありますがあまり多くはできないこととして、ISP の接続速度があります。単純な速度テスト ツールによって、接続速度が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1758d-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="1758d-172">ブラウザーの接続</span><span class="sxs-lookup"><span data-stu-id="1758d-172">Browser connection</span></span>

<span data-ttu-id="1758d-173">パフォーマンスの観点から、Web ブラウザーで考慮するいくつかの要因があります。</span><span class="sxs-lookup"><span data-stu-id="1758d-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="1758d-p110">複雑なページを訪問するとパフォーマンスに影響します。ほとんどのブラウザーは、キャッシュを小さく (約 90 MB)、平均値の中にのみある web ページは、通常、約 1.6 MB です。これは、get 使用するのに時間はかかります。</span><span class="sxs-lookup"><span data-stu-id="1758d-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="1758d-p111">帯域幅も問題となる場合があります。などの場合は、ユーザーは、別のセッションでビデオを鑑賞するが、この SharePoint ページのパフォーマンスに影響が。ストリーミング メディアからユーザーを防ぐことはできません、中には、ユーザーのページが読み込まれます方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="1758d-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="1758d-180">SharePoint Online のページの別のカスタマイズ方法については、以下の資料および他の最適なパフォーマンスを実現するためのベスト プラクティスを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1758d-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="1758d-181">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="1758d-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="1758d-182">SharePoint Online のページの診断ツールを使用してください。</span><span class="sxs-lookup"><span data-stu-id="1758d-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="1758d-183">SharePoint Online のイメージの最適化</span><span class="sxs-lookup"><span data-stu-id="1758d-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="1758d-184">SharePoint Online での画像の読み込み遅延と JavaScript</span><span class="sxs-lookup"><span data-stu-id="1758d-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="1758d-185">SharePoint Online での縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="1758d-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="1758d-186">コンテンツ配信ネットワークの使用</span><span class="sxs-lookup"><span data-stu-id="1758d-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="1758d-187">コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用して SharePoint Online でのパフォーマンスを向上させる</span><span class="sxs-lookup"><span data-stu-id="1758d-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="1758d-188">容量計画および SharePoint Online のテスト負荷</span><span class="sxs-lookup"><span data-stu-id="1758d-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="1758d-189">SharePoint Online のパフォーマンスの問題の診断</span><span class="sxs-lookup"><span data-stu-id="1758d-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="1758d-190">SharePoint Online でのオブジェクト キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="1758d-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="1758d-191">SharePoint Online で調整またはブロックを回避する方法</span><span class="sxs-lookup"><span data-stu-id="1758d-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

