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
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541521"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="bad9d-103">SharePoint Online のパフォーマンス チューニングの概要</span><span class="sxs-lookup"><span data-stu-id="bad9d-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="bad9d-104">この資料では、SharePoint Online での最適なパフォーマンスのページをデザインするときに考慮する必要がどのような特定の側面について説明します。</span><span class="sxs-lookup"><span data-stu-id="bad9d-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
  
## <a name="in-this-article"></a><span data-ttu-id="bad9d-105">この記事の内容</span><span class="sxs-lookup"><span data-stu-id="bad9d-105">In this article</span></span>

- <span data-ttu-id="bad9d-106">[SharePoint Online の測定値](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics)と[データのための結論に達すると](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span><span class="sxs-lookup"><span data-stu-id="bad9d-106">[SharePoint Online metrics](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) and [Conclusions reached because of the data](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span></span>
    
- [<span data-ttu-id="bad9d-107">パフォーマンスをチェックするときに、標準ユーザー アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bad9d-107">Use a standard user account when checking performance</span></span>](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- <span data-ttu-id="bad9d-108">[パフォーマンスをチューニングするための接続カテゴリ](introduction-to-performance-tuning-for-sharepoint-online.md#connect):[サーバー間の接続](introduction-to-performance-tuning-for-sharepoint-online.md#server)、[ネットワーク接続](introduction-to-performance-tuning-for-sharepoint-online.md#network)、および[ブラウザーの接続](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span><span class="sxs-lookup"><span data-stu-id="bad9d-108">[Connection categories for performance tuning](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server connection](introduction-to-performance-tuning-for-sharepoint-online.md#server), [Network connection](introduction-to-performance-tuning-for-sharepoint-online.md#network), and [Browser connection](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span></span>
    
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="bad9d-109">SharePoint Online のメトリックス</span><span class="sxs-lookup"><span data-stu-id="bad9d-109">SharePoint Online metrics</span></span>
<span data-ttu-id="bad9d-110"><a name="spometrics"> </a></span><span class="sxs-lookup"><span data-stu-id="bad9d-110"></span></span>

<span data-ttu-id="bad9d-111">以下の SharePoint Online の広範なメトリックスには、パフォーマンスに関する実際のデータが記載されています。</span><span class="sxs-lookup"><span data-stu-id="bad9d-111">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="bad9d-112">ページの読み取り速度</span><span class="sxs-lookup"><span data-stu-id="bad9d-112">How fast pages load</span></span>
    
- <span data-ttu-id="bad9d-113">ページごとに必要なラウンド トリップの数</span><span class="sxs-lookup"><span data-stu-id="bad9d-113">How many round trips required per page</span></span>
    
- <span data-ttu-id="bad9d-114">サービスの問題</span><span class="sxs-lookup"><span data-stu-id="bad9d-114">Issues with the service</span></span>
    
- <span data-ttu-id="bad9d-115">パフォーマンスの低下を引き起こすその他の事項</span><span class="sxs-lookup"><span data-stu-id="bad9d-115">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="bad9d-116">データからたどり着いた結論</span><span class="sxs-lookup"><span data-stu-id="bad9d-116">Conclusions reached because of the data</span></span>
<span data-ttu-id="bad9d-117"><a name="data"> </a></span><span class="sxs-lookup"><span data-stu-id="bad9d-117"></span></span>

<span data-ttu-id="bad9d-118">データは以下を示しています。</span><span class="sxs-lookup"><span data-stu-id="bad9d-118">The data tells us:</span></span>
  
- <span data-ttu-id="bad9d-119">ほとんどのページは SharePoint Online で良好に動作しています。</span><span class="sxs-lookup"><span data-stu-id="bad9d-119">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="bad9d-120">カスタマイズされていないページは、非常に速く読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="bad9d-120">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="bad9d-121">OneDrive for Business、チーム サイト、_layouts などのシステムのページは、すべて速く読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="bad9d-121">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="bad9d-122">1% の最も読み込み時間が長い SharePoint Online ページは、読み込みに 5,000 ミリ秒を超える時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="bad9d-122">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="bad9d-p101">使用できる 1 つの単純なベンチマーク テストは、自社のポータルの読み込み時間と OneDrive for Business のホーム ページの読み込み時間を比較してパフォーマンスを測定することです。OneDrive for Business のホーム ページではカスタマイズ機能がほとんど使用されないためです。これは、ネットワークのパフォーマンスの問題についてのトラブルシューティングを実行する際にサポート完了のためにお願いする最初の手順になることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="bad9d-125">パフォーマンスをチェックするときに、標準ユーザー アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bad9d-125">Use a standard user account when checking performance</span></span>
<span data-ttu-id="bad9d-126"><a name="standuser"> </a></span><span class="sxs-lookup"><span data-stu-id="bad9d-126"></span></span>

<span data-ttu-id="bad9d-127">サイト コレクションの管理者、サイト所有者、エディター、または共同作成者は、追加のセキュリティ グループに属しているし、追加のアクセス許可がある SharePoint は、ページに読み込まれるその他の要素があるため。</span><span class="sxs-lookup"><span data-stu-id="bad9d-127">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="bad9d-128">これは SharePoint 設置し、SharePoint Online に適用できるが、設置型のシナリオでの違いは簡単には気づかれない SharePoint Online のように。</span><span class="sxs-lookup"><span data-stu-id="bad9d-128">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="bad9d-129">ユーザーは、ページを実行する方法を正確に評価をするためにコントロールを作成し、セキュリティ グループに関連するその他のトラフィックが読み込まれないようにするのには、標準ユーザー アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bad9d-129">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="bad9d-130">パフォーマンス チューニングの接続のカテゴリ</span><span class="sxs-lookup"><span data-stu-id="bad9d-130">Connection categories for performance tuning</span></span>
<span data-ttu-id="bad9d-131"><a name="connect"> </a></span><span class="sxs-lookup"><span data-stu-id="bad9d-131"></span></span>

<span data-ttu-id="bad9d-p102">サーバーとユーザーの間の接続は、主な 3 つのコンポーネントに分類できます。読み込み時間の見通しについて SharePoint Online ページを設計する際は、これらのコンポーネントを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="bad9d-134">**サーバーです**。マイクロソフトがデータ センターでホストするサーバーです。</span><span class="sxs-lookup"><span data-stu-id="bad9d-134">**Server.** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="bad9d-135">**ネットワークです**。Microsoft のネットワーク、インターネット、およびデータ センターとユーザーの間で、オンプレミスのネットワークです。</span><span class="sxs-lookup"><span data-stu-id="bad9d-135">**Network.** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="bad9d-136">**ブラウザー** 。ページが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="bad9d-136">**Browser.** Where the page is loaded.</span></span>
    
<span data-ttu-id="bad9d-p103">これら 3 つの接続内では、一般的に、読み込み時間が長いページのうち 95% は 5 つの理由によるものです。この記事では、それぞれの理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="bad9d-139">ナビゲーションの問題</span><span class="sxs-lookup"><span data-stu-id="bad9d-139">Navigation issues</span></span>
    
- <span data-ttu-id="bad9d-140">コンテンツ ロールアップ</span><span class="sxs-lookup"><span data-stu-id="bad9d-140">Content roll up</span></span>
    
- <span data-ttu-id="bad9d-141">大きなファイル</span><span class="sxs-lookup"><span data-stu-id="bad9d-141">Large files</span></span>
    
- <span data-ttu-id="bad9d-142">サーバーへの多数の要求</span><span class="sxs-lookup"><span data-stu-id="bad9d-142">Many requests to the server</span></span>
    
- <span data-ttu-id="bad9d-143">Web パーツの処理</span><span class="sxs-lookup"><span data-stu-id="bad9d-143">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="bad9d-144">サーバーの接続</span><span class="sxs-lookup"><span data-stu-id="bad9d-144">Server connection</span></span>
<span data-ttu-id="bad9d-145"><a name="server"> </a></span><span class="sxs-lookup"><span data-stu-id="bad9d-145"></span></span>

<span data-ttu-id="bad9d-146">オンプレミスの SharePoint でのパフォーマンスに影響する問題の多くは、SharePoint Online にも該当します。</span><span class="sxs-lookup"><span data-stu-id="bad9d-146">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="bad9d-p104">予想どおり、サーバーがオンプレミスの SharePoint で実行する内容にははるかに多くの制御があります。SharePoint Online では、作業は少し異なります。サーバーが実行する作業を多くすればするほど、ページの表示に時間がかかります。SharePoint では、この点において最大の原因は、複数の Web パーツを含む複雑なページです。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="bad9d-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bad9d-151">SharePoint Online</span></span>
  
![オンラインのサーバーのスクリーンショット](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="bad9d-153">SharePoint</span><span class="sxs-lookup"><span data-stu-id="bad9d-153">SharePoint</span></span>
  
![オンプレミスのサーバーのスクリーンショット](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="bad9d-p105">SharePoint Online では、特定のページの要求が、実際は複数のサーバーを呼び出すという結果になります。個別の要求に対し、結果的としてサーバー間で要求の表が生成されることがあります。この通信は、ページの読み込みの観点から費用がかかり、動作を遅くします。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="bad9d-158">サーバー間の通信の例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bad9d-158">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="bad9d-159">Web サーバーと SQL サーバー</span><span class="sxs-lookup"><span data-stu-id="bad9d-159">Web to SQL Servers</span></span>
    
- <span data-ttu-id="bad9d-160">Web サーバーとアプリケーション サーバー</span><span class="sxs-lookup"><span data-stu-id="bad9d-160">Web to application servers</span></span>
    
<span data-ttu-id="bad9d-p106">サーバーの通信時間が長くなるもう 1 つの原因は、キャッシュ ミスです。オンプレミスの SharePoint とは異なり、以前アクセスしたページと同じサーバーに当たる機会は非常に少なくなり、オブジェクトのキャッシュが最新ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="bad9d-163">ネットワーク接続</span><span class="sxs-lookup"><span data-stu-id="bad9d-163">Network connection</span></span>
<span data-ttu-id="bad9d-164"><a name="network"> </a></span><span class="sxs-lookup"><span data-stu-id="bad9d-164"></span></span>

<span data-ttu-id="bad9d-p107">設置がないため、wan を使用する、データ ・ センターとエンド ・ ユーザーとの間の高速接続を使用することがあります。一般に、点は、ネットワークの観点から管理が容易です。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="bad9d-167">SharePoint Online では、さらにいくつか考慮する要因があります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bad9d-167">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="bad9d-168">Microsoft ネットワーク</span><span class="sxs-lookup"><span data-stu-id="bad9d-168">The Microsoft network</span></span>
    
- <span data-ttu-id="bad9d-169">インターネット</span><span class="sxs-lookup"><span data-stu-id="bad9d-169">The Internet</span></span>
    
- <span data-ttu-id="bad9d-170">ISP</span><span class="sxs-lookup"><span data-stu-id="bad9d-170">The ISP</span></span>
    
<span data-ttu-id="bad9d-171">どのバージョンの SharePoint (およびどのネットワーク) を使用するかに関係なく、一般的にネットワークをビジー状態にするものには以下があります。</span><span class="sxs-lookup"><span data-stu-id="bad9d-171">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="bad9d-172">大きいペイロード</span><span class="sxs-lookup"><span data-stu-id="bad9d-172">Large payload</span></span>
    
- <span data-ttu-id="bad9d-173">多数のファイル</span><span class="sxs-lookup"><span data-stu-id="bad9d-173">Many files</span></span>
    
- <span data-ttu-id="bad9d-174">サーバーへの物理的な距離が長いこと</span><span class="sxs-lookup"><span data-stu-id="bad9d-174">Large physical distance to the server</span></span>
    
<span data-ttu-id="bad9d-p108">SharePoint Online で利用できる機能の 1 つは、マイクロソフトの CDN (コンテンツ配信ネットワーク) です。CDN は、基本的に複数のデータ センターに展開サーバーの分散型のコレクションです。、CDN ではクライアントが元の SharePoint サーバーからは遠く離れている場合でもにページ上のコンテンツ クライアントにサーバーでホストできます。マイクロソフトが使用しているより、将来的にページをカスタマイズできない、たとえば、SharePoint Online 管理ホーム ページのローカル インスタンスを格納します。Cdn の詳細については、[コンテンツ配信ネットワーク](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="bad9d-p109">知っておく必要がありますがあまり多くはできないこととして、ISP の接続速度があります。単純な速度テスト ツールによって、接続速度が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="bad9d-182">ブラウザーの接続</span><span class="sxs-lookup"><span data-stu-id="bad9d-182">Browser connection</span></span>
<span data-ttu-id="bad9d-183"><a name="browser"> </a></span><span class="sxs-lookup"><span data-stu-id="bad9d-183"></span></span>

<span data-ttu-id="bad9d-184">パフォーマンスの観点から、Web ブラウザーで考慮するいくつかの要因があります。</span><span class="sxs-lookup"><span data-stu-id="bad9d-184">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="bad9d-p110">複雑なページを訪問するとパフォーマンスに影響します。ほとんどのブラウザーは、キャッシュを小さく (約 90 MB)、平均値の中にのみある web ページは、通常、約 1.6 MB です。これは、get 使用するのに時間はかかります。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="bad9d-p111">帯域幅も問題となる場合があります。などの場合は、ユーザーは、別のセッションでビデオを鑑賞するが、この SharePoint ページのパフォーマンスに影響が。ストリーミング メディアからユーザーを防ぐことはできません、中には、ユーザーのページが読み込まれます方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="bad9d-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="bad9d-191">SharePoint Online のページの別のカスタマイズ方法については、以下の資料および他の最適なパフォーマンスを実現するためのベスト プラクティスを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bad9d-191">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="bad9d-192">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="bad9d-192">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="bad9d-193">SharePoint Online のページの診断ツールを使用してください。</span><span class="sxs-lookup"><span data-stu-id="bad9d-193">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="bad9d-194">SharePoint Online のイメージの最適化</span><span class="sxs-lookup"><span data-stu-id="bad9d-194">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="bad9d-195">SharePoint Online での画像の読み込み遅延と JavaScript</span><span class="sxs-lookup"><span data-stu-id="bad9d-195">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="bad9d-196">SharePoint Online での縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="bad9d-196">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="bad9d-197">コンテンツ配信ネットワークの使用</span><span class="sxs-lookup"><span data-stu-id="bad9d-197">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="bad9d-198">コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用して SharePoint Online でのパフォーマンスを向上させる</span><span class="sxs-lookup"><span data-stu-id="bad9d-198">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="bad9d-199">容量計画および SharePoint Online のテスト負荷</span><span class="sxs-lookup"><span data-stu-id="bad9d-199">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="bad9d-200">SharePoint Online のパフォーマンスの問題の診断</span><span class="sxs-lookup"><span data-stu-id="bad9d-200">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="bad9d-201">SharePoint Online でのオブジェクト キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="bad9d-201">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="bad9d-202">SharePoint Online で調整またはブロックを回避する方法</span><span class="sxs-lookup"><span data-stu-id="bad9d-202">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

