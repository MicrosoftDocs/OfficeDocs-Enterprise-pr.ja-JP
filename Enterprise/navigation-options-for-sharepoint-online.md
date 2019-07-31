---
title: SharePoint Online のナビゲーション オプション
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: この記事では、SharePoint Publishing が有効化されている SharePoint Online サイトのナビゲーション オプションについて説明します。 ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスとスケーラビリティに大きく影響します。
ms.openlocfilehash: b3194009d21f60093ec80cb2e138df34df60e22e
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616860"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="65812-104">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="65812-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="65812-105">この記事では、SharePoint Publishing が有効化されている SharePoint Online サイトのナビゲーション オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="65812-105">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="65812-106">ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスとスケーラビリティに大きく影響します。</span><span class="sxs-lookup"><span data-stu-id="65812-106">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="65812-107">概要</span><span class="sxs-lookup"><span data-stu-id="65812-107">Overview</span></span>

<span data-ttu-id="65812-108">ナビゲーション プロバイダーの構成はサイト全体のパフォーマンスに大きな影響を与える可能性があるため、SharePoint サイトの要件を満たすように効果的に対応できるナビゲーション プロバイダーと構成を慎重に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65812-108">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="65812-109">2 つの既成のナビゲーション プロバイダーの他、ナビゲーションのカスタム実装が提供されています。</span><span class="sxs-lookup"><span data-stu-id="65812-109">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="65812-110">1 番目のオプションの[**管理 (メタデータ) ナビゲーション**](#using-managed-navigation-and-metadata-in-sharepoint-online)をお勧めします。これは、SharePoint Online の既定のオプションの 1 つでもあります。ただし、必要がない場合は、セキュリティ トリミングを無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="65812-110">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="65812-111">セキュリティ トリミングは既定によるセキュリティ保護としてこのナビゲーション プロバイダーで有効化されていますが、多くのサイトでは、サイトのすべてのユーザーに対して一貫性のあるナビゲーション要素を提供しているため、セキュリティ トリミングのオーバーヘッドは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="65812-111">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="65812-112">推奨されているセキュリティトリミングを無効にする構成にした場合、このナビゲーション プロバイダーではサイト構造を列挙する必要がなく、パフォーマンスへの影響を許容範囲に抑えながら高い拡張性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="65812-112">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="65812-113">2 番目のオプションの[**構造ナビゲーション**](#using-structural-navigation-in-sharepoint-online)は、**SharePoint Online で推奨されるナビゲーション オプションではありません**。 </span><span class="sxs-lookup"><span data-stu-id="65812-113">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="65812-114">このナビゲーション プロバイダーは、オンプレミスのトポロジ用に設計されており、SharePoint Online でのサポートは限定的です。</span><span class="sxs-lookup"><span data-stu-id="65812-114">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="65812-115">このプロバイダーでは他のナビゲーション オプションで提供されていない追加の機能が提供されますが、このプロバイダーを使用する場合、セキュリティ トリミングやサイト構造の列挙などを含むこれらの機能は過度のサーバーの呼び出しやスケーラビリティおよびパフォーマンスの低下を引き起こします。</span><span class="sxs-lookup"><span data-stu-id="65812-115">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="65812-116">構造ナビゲーションを使用するサイトのうち、リソースの消費が過剰なサイトは調整の対象になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="65812-116">Sites using structured navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="65812-117">既成のナビゲーション プロバイダーに加えて、多くのお客様が代替のカスタム ナビゲーション実装を正常に実装しています。</span><span class="sxs-lookup"><span data-stu-id="65812-117">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="65812-118">カスタム ナビゲーション実装の一般的なクラスの 1 つとして、ナビゲーション ノードのローカル キャッシュを格納するクライアント レンダリングによるデザイン パターンがあります。</span><span class="sxs-lookup"><span data-stu-id="65812-118">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="65812-119">(この記事の「**[検索型クライアント側スクリプト ](#using-search-driven-client-side-scripting)**」を参照してください。)</span><span class="sxs-lookup"><span data-stu-id="65812-119">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="65812-120">これらのナビゲーション プロバイダーには、いくつかの大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="65812-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="65812-121">これらのナビゲーション プロバイダーは通常、応答性の高いページ デザインに適しています。</span><span class="sxs-lookup"><span data-stu-id="65812-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="65812-122">リソース コストをかけずにレンダリングできるため、拡張性が高く、高性能です (また、タイムアウト後にバックグラウンドでの更新が可能です)。</span><span class="sxs-lookup"><span data-stu-id="65812-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="65812-123">これらのナビゲーション プロバイダーは、単純な静的構成からさまざまな動的データ プロバイダーまでを含む、さまざまな方法を使用してナビゲーション データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="65812-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="65812-124">データ プロバイダーの例として、ナビゲーション ノードの列挙とセキュリティ トリミングの効率的な処理が可能な**検索型ナビゲーション**を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="65812-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="65812-125">**カスタム ナビゲーション プロバイダー**を構築するための一般的なオプションは他にもあります。</span><span class="sxs-lookup"><span data-stu-id="65812-125">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="65812-126">カスタム ナビゲーション プロバイダーを構築する方法に関するより詳細なガイダンスついては、「[SharePoint Online ポータル用のナビゲーション ソリューション](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65812-126">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="65812-127">SharePoint Online ナビゲーション オプションの長所と短所</span><span class="sxs-lookup"><span data-stu-id="65812-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="65812-128">次の表は、各オプションの長所と短所をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="65812-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="65812-129">管理ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="65812-129">Managed navigation</span></span>  |<span data-ttu-id="65812-130">構造ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="65812-130">Structural navigation</span></span>  |<span data-ttu-id="65812-131">検索型ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="65812-131">Search-driven navigation</span></span>  |<span data-ttu-id="65812-132">カスタム ナビゲーション プロバイダー</span><span class="sxs-lookup"><span data-stu-id="65812-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="65812-133">長所:</span><span class="sxs-lookup"><span data-stu-id="65812-133">Pros</span></span><br/><br/><span data-ttu-id="65812-134">メンテナンスしやすい</span><span class="sxs-lookup"><span data-stu-id="65812-134">Easy to maintain</span></span><br/><span data-ttu-id="65812-135">推奨されるオプション</span><span class="sxs-lookup"><span data-stu-id="65812-135">Recommended option</span></span><br/>     |<span data-ttu-id="65812-136">長所:</span><span class="sxs-lookup"><span data-stu-id="65812-136">Pros</span></span><br/><br/><span data-ttu-id="65812-137">構成しやすい</span><span class="sxs-lookup"><span data-stu-id="65812-137">Easy to configure</span></span><br/><span data-ttu-id="65812-138">セキュリティ トリミングが行われる</span><span class="sxs-lookup"><span data-stu-id="65812-138">Security trimmed</span></span><br/><span data-ttu-id="65812-139">コンテンツが追加されると自動的に更新される</span><span class="sxs-lookup"><span data-stu-id="65812-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="65812-140">長所:</span><span class="sxs-lookup"><span data-stu-id="65812-140">Pros</span></span><br/><br/><span data-ttu-id="65812-141">セキュリティ トリミングが行われる</span><span class="sxs-lookup"><span data-stu-id="65812-141">Security trimmed</span></span><br/><span data-ttu-id="65812-142">サイトが追加されると自動的に更新される</span><span class="sxs-lookup"><span data-stu-id="65812-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="65812-143">読み込み時間が短く、ナビゲーション構造がローカルにキャッシュされている</span><span class="sxs-lookup"><span data-stu-id="65812-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="65812-144">長所:</span><span class="sxs-lookup"><span data-stu-id="65812-144">Pros</span></span><br/><br/><span data-ttu-id="65812-145">使用可能なオプションの選択肢が広い</span><span class="sxs-lookup"><span data-stu-id="65812-145">Wider choice of options available</span></span><br/><span data-ttu-id="65812-146">キャッシュが正常に使用された場合、高速の読み込み</span><span class="sxs-lookup"><span data-stu-id="65812-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="65812-147">多くのオプションが、応答性の高いページ デザインで適正に動作する</span><span class="sxs-lookup"><span data-stu-id="65812-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="65812-148">短所:</span><span class="sxs-lookup"><span data-stu-id="65812-148">Cons</span></span><br/><br/><span data-ttu-id="65812-149">サイト構造を反映するように自動的に更新されない</span><span class="sxs-lookup"><span data-stu-id="65812-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="65812-150">セキュリティ トリミングが有効になっている場合、パフォーマンスが低下する</span><span class="sxs-lookup"><span data-stu-id="65812-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="65812-151">短所:</span><span class="sxs-lookup"><span data-stu-id="65812-151">Cons</span></span><br/><br/><span data-ttu-id="65812-152">**非推奨**</span><span class="sxs-lookup"><span data-stu-id="65812-152">**Not recommended.**</span></span><br/><span data-ttu-id="65812-153">**パフォーマンスとスケーラビリティへの影響**</span><span class="sxs-lookup"><span data-stu-id="65812-153">**Improved performance and scalability**</span></span><br/><span data-ttu-id="65812-154">**調整の対象**</span><span class="sxs-lookup"><span data-stu-id="65812-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="65812-155">短所:</span><span class="sxs-lookup"><span data-stu-id="65812-155">Cons</span></span><br/><br/><span data-ttu-id="65812-156">サイトの順序を簡単に変更できない</span><span class="sxs-lookup"><span data-stu-id="65812-156">No ability to easily order sites</span></span><br/><span data-ttu-id="65812-157">マスター ページのカスタマイズが必要 (技術的なスキルが必要)</span><span class="sxs-lookup"><span data-stu-id="65812-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="65812-158">短所:</span><span class="sxs-lookup"><span data-stu-id="65812-158">Cons</span></span><br/><br/><span data-ttu-id="65812-159">カスタム開発が必要</span><span class="sxs-lookup"><span data-stu-id="65812-159">Custom development is required</span></span><br/><span data-ttu-id="65812-160">外部データ ソース / 格納されたキャッシュが必要 (例: Azure)</span><span class="sxs-lookup"><span data-stu-id="65812-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="65812-161">サイトに最適なオプションは、サイトの要件と技術的な能力に依存しています。</span><span class="sxs-lookup"><span data-stu-id="65812-161">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="65812-162">スケーラブルな既成のナビゲーションプロバイダーが必要な場合は、セキュリティ トリミングを無効化した管理ナビゲーションが適しています。</span><span class="sxs-lookup"><span data-stu-id="65812-162">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span>

<span data-ttu-id="65812-163">管理ナビゲーション オプションは構成を介して管理でき、コードのカスタマイズ ファイルは必要ないため、構造ナビゲーションよりはるかに高速です。</span><span class="sxs-lookup"><span data-stu-id="65812-163">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="65812-164">セキュリ ティトリミングを必要とし、カスタム マスター ページを使用する能力があり、SharePoint Online の既定のマスター ページで発生する変更に対する管理能力が組織にある場合、検索型オプションを使用するとより優れたユーザー エクスペリエンスを構築できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65812-164">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="65812-165">より複雑な要件がある場合は、カスタム ナビゲーションプロバイダーが適している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65812-165">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="65812-166">構造ナビゲーションは非推奨です。</span><span class="sxs-lookup"><span data-stu-id="65812-166">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="65812-167">最後に、SharePoint では、SharePoint ハブ サイトのよりフラットなサイト階層とハブアンドスポーク モデルを活用して、モダンな SharePoint サイト アーキテクチャ用に追加のナビゲーション プロバイダーや機能を追加しています。</span><span class="sxs-lookup"><span data-stu-id="65812-167">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="65812-168">これにより、SharePoint 発行機能を必要としないシナリオを多数実現できるようになります。これらのナビゲーション構成は、SharePoint Online 内の拡張性と遅延に合わせて最適化されています。</span><span class="sxs-lookup"><span data-stu-id="65812-168">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="65812-169">これと同じ、SharePoint 発行サイトの全体的な構造をよりフラットな構造にして簡素化するという原則を適用した場合、多くの場合、全体的なパフォーマンスと拡張性の向上にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="65812-169">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="65812-170">これは、大量のサイト (サブ Web) を含む単一のサイト コレクションを使用するのではなく、それぞれはごく少数のサブサイト (サブ Web) しか含まないサイト コレクションを多数使用する方が優れたアプローチであることを意味します。</span><span class="sxs-lookup"><span data-stu-id="65812-170">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="65812-171">SharePoint Online で管理ナビゲーションおよび管理されたメタデータを使用する</span><span class="sxs-lookup"><span data-stu-id="65812-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="65812-172">別の既成のオプションとして管理ナビゲーションがあり、このオプションを使用して構造ナビゲーションの機能のほとんどを再現できます。</span><span class="sxs-lookup"><span data-stu-id="65812-172">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="65812-173">管理されたメタデータの構成では、セキュリティ トリミングは有効にも無効にもできます。</span><span class="sxs-lookup"><span data-stu-id="65812-173">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="65812-174">構成でセキュリティ トリミングが無効化されている場合、管理ナビゲーションは、一定数のサーバー呼び出しを使用してすべてのナビゲーション リンクを読み込むので、比較的効率的です。</span><span class="sxs-lookup"><span data-stu-id="65812-174">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="65812-175">一方、セキュリティ トリミングを有効化した場合は管理ナビゲーションの利点が打ち消されるため、最適なパフォーマンスとスケーラビリティを実現するには、いずれかのカスタム ナビゲーション ソリューションを試すという選択の方が有効である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65812-175">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="65812-176">多くのサイトではセキュリティ トリミングは必要ありません。これは、サイトのすべてのユーザーのナビゲーション構造が多くの場合共通であるためです。</span><span class="sxs-lookup"><span data-stu-id="65812-176">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="65812-177">セキュリティ トリミングが無効になっていて、アクセス権を持たないユーザーもいるナビゲーションにリンクが追加された場合、リンクは表示されますが、アクセスが拒否されたというメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="65812-177">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="65812-178">コンテンツへの偶発的なアクセスが発生する危険はありません。</span><span class="sxs-lookup"><span data-stu-id="65812-178">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="65812-179">管理ナビゲーションと結果を実装する方法</span><span class="sxs-lookup"><span data-stu-id="65812-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="65812-180">管理ナビゲーションの詳細については、Docs.Microsoft.com にいくつかの記事が掲載されています。たとえば、「[SharePoint Server の管理ナビゲーションの概要](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65812-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="65812-181">管理ナビゲーションを実装するには、サイトのナビゲーション構造に対応する URL を使用して用語を設定します。</span><span class="sxs-lookup"><span data-stu-id="65812-181">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="65812-182">管理ナビゲーションは多くの場合、手動で監督することにより構造ナビゲーションと置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="65812-182">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="65812-183">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="65812-183">For example:</span></span>

![SharePoint Online サイトの構造](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="65812-185">次の例は、管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="65812-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンス](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="65812-187">常に管理ナビゲーションを使用すると、構造ナビゲーションのアプローチと比較してパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="65812-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="65812-188">SharePoint Online で構造ナビゲーションを使用する</span><span class="sxs-lookup"><span data-stu-id="65812-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="65812-189">これは既定で使用される既成のナビゲーションで、最も単純なソリューションですが、その反面、パフォーマンスが大きく低下するデメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="65812-189">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="65812-190">カスタマイズの必要がなく、非技術者のユーザーでもアイテムの追加、アイテムの非表示、ナビゲーションの管理を [設定] ページから簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="65812-190">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="65812-191">ただし、これは管理ナビゲーションの場合も同様です。この理由から、管理および制御が同じく簡単に行え、パフォーマンスも向上する管理ナビゲーションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="65812-191">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![[サブサイトを表示する] が選択されている構造ナビゲーション](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="65812-193">SharePoint Online で構造ナビゲーションを有効にする</span><span class="sxs-lookup"><span data-stu-id="65812-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="65812-194">標準の SharePoint Online ソリューションで構造ナビゲーションを使用し、サブサイトを表示するオプションに設定した場合のパフォーマンスへの影響を示します。</span><span class="sxs-lookup"><span data-stu-id="65812-194">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="65812-195">以下は、[**サイトの設定**] \> [**ナビゲーション**] ページの設定のスクリーンショットです。</span><span class="sxs-lookup"><span data-stu-id="65812-195">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![サブサイトを示すスクリーンショット](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="65812-197">SharePoint Online で構造ナビゲーションのパフォーマンスを分析する</span><span class="sxs-lookup"><span data-stu-id="65812-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="65812-198">SharePoint のページのパフォーマンスを分析するには、Internet Explorer の F12 開発者ツールの [**ネットワーク**] タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="65812-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![F12 開発者ツールの [ネットワーク] タブを示すスクリーンショット](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="65812-200">[**ネットワーク**] タブで、読み込み中の .aspx ページをクリックして、[**詳細**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="65812-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="65812-201">![[詳細] タブを示すスクリーンショット](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="65812-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="65812-202">[**応答ヘッダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="65812-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="65812-203">![[詳細] タブのスクリーンショット](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="65812-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="65812-204">SharePoint は、その応答ヘッダー内で、有益な診断情報を返します。</span><span class="sxs-lookup"><span data-stu-id="65812-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="65812-205">最も便利な情報の 1 つは **SPRequestDuration** です。これは、サーバー上で要求の処理にかかった時間の値 (ミリ秒単位) です。</span><span class="sxs-lookup"><span data-stu-id="65812-205">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="65812-206">次のスクリーン ショットでは、構造ナビゲーションの [**サブサイトを表示する**] のチェックがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="65812-206">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="65812-207">これは、グローバル ナビゲーションにはサイト コレクションのリンクのみがあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="65812-207">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="65812-208">![要求時間として負荷時間を示すスクリーンショット](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="65812-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="65812-209">**SPRequestDuration** キーの値は 245 ミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="65812-209">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="65812-210">これは、要求を返すまでにかかった時間を表します。</span><span class="sxs-lookup"><span data-stu-id="65812-210">This represents the time it took to return the request.</span></span> <span data-ttu-id="65812-211">サイトにあるナビゲーション アイテムが 1 つのみであるため、これは高負荷のナビゲーションがない場合の SharePoint Online のパフォーマンスに関する優れたベンチマークです。</span><span class="sxs-lookup"><span data-stu-id="65812-211">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="65812-212">次のスクリーン ショットは、サブサイトを追加した場合に、このキーにどう影響するかを示しています。</span><span class="sxs-lookup"><span data-stu-id="65812-212">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="65812-213">![2,502 ミリ秒の要求時間を示すスクリーンショット](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="65812-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="65812-214">サブサイトの追加により、この比較的単純なサンプルサイトでページ要求に返答するまでにかかる時間が大きく増加しました。</span><span class="sxs-lookup"><span data-stu-id="65812-214">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="65812-215">ナビゲーションのページなどの複雑なサイト階層や、その他の構成およびトポロジ オプションを使用する場合は、影響がさらに大きくなります。</span><span class="sxs-lookup"><span data-stu-id="65812-215">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="65812-216">検索型のクライアント側スクリプトを使用する</span><span class="sxs-lookup"><span data-stu-id="65812-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="65812-217">検索を使用すると、継続的クロールによってバックグラウンドでビルドされたインデックスを活用できます。</span><span class="sxs-lookup"><span data-stu-id="65812-217">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="65812-218">検索結果が検索インデックスから取り込まれ、結果はセキュリティ トリミングされます。</span><span class="sxs-lookup"><span data-stu-id="65812-218">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="65812-219">通常、セキュリティ トリミングが必要な場合は、既成のナビゲーション プロバイダーより高速です。</span><span class="sxs-lookup"><span data-stu-id="65812-219">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="65812-220">構造ナビゲーションで検索を使用すると、特に複雑なサイト構造がある場合は、ページの読み込み時間が大幅に短縮します。</span><span class="sxs-lookup"><span data-stu-id="65812-220">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="65812-221">管理ナビゲーションに対するこの方法の主な利点は、セキュリティ トリミングの恩恵を受けられることです。</span><span class="sxs-lookup"><span data-stu-id="65812-221">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="65812-222">このアプローチには、カスタム マスター ページの作成、既成のナビゲーション コードのカスタム HTML への置き換えなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="65812-222">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="65812-223">ファイル `seattle.html` のナビゲーション コードを置き換えるには、次の例に示す手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="65812-223">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="65812-224">この例では、`seattle.html`ファイルを開き、`id=”DeltaTopNavigation”` という要素全体をカスタム HTML コードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65812-224">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="65812-225">例: マスター ページの既成のナビゲーション コードを置き換える</span><span class="sxs-lookup"><span data-stu-id="65812-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="65812-226">[サイト設定] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="65812-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="65812-227">[**マスター ページ**] をクリックして、マスター ページ ギャラリーを開きます。</span><span class="sxs-lookup"><span data-stu-id="65812-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="65812-228">ここから、ライブラリ内を移動してファイル `seattle.master` をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="65812-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="65812-229">テキスト エディターでコードを編集し、次のスクリーン ショットにあるコード ブロックを削除します。</span><span class="sxs-lookup"><span data-stu-id="65812-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![示されたコードブロックを削除する](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="65812-231">タグ `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` と `<\SharePoint:AjaxDelta>` の間のコードを削除し、次のスニペットに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65812-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
               
                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->   
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->   
                </a>
               
                <!-- ko if: children.length > 0-->                                                       
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
         
          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>                 
          <!-- /ko -->   
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```
<br/>
6. <span data-ttu-id="65812-232">冒頭の読み込みイメージのアンカー タグの URL を、サイト コレクションの読み込みイメージへのリンクに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="65812-232">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="65812-233">変更を加えたら、ファイルの名前を変更し、マスター ページ ギャラリーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="65812-233">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="65812-234">これにより、新しい .master ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="65812-234">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="65812-235">この HTML は、JavaScript のコードから返される検索結果によって入力される基本的なマークアップです。</span><span class="sxs-lookup"><span data-stu-id="65812-235">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="65812-236">次のスニペットに示すとおり、var root = “site collection URL” の値を変更するためにコードを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65812-236">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="65812-237">結果は self.nodes 配列に割り当てられ、linq.js を使用してオブジェクトから階層が構築され、出力が配列 self.hierarchy に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="65812-237">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="65812-238">この配列は、HTML にバインドされているオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="65812-238">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="65812-239">これは、toggleView() 関数でセルフ オブジェクトを ko.applyBindings() 関数に渡すことにより実行されます。</span><span class="sxs-lookup"><span data-stu-id="65812-239">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="65812-240">続いて、階層の配列が次の HTML にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="65812-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="65812-241">サブサイトのドロップダウン メニューを処理するために`mouseenter` および `mouseexit` のイベント ハンドラーがトップレベルのナビゲーションに追加されます。これは、`addEventsToElements()` 関数で実行されます。 </span><span class="sxs-lookup"><span data-stu-id="65812-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="65812-242">この複雑なナビゲーションの例では、ローカル キャッシュがない新しいページの読み込みにおいて、管理ナビゲーションのアプローチと似た結果を得るため、サーバーで費やした時間がベンチマークの構造ナビゲーションから短縮されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="65812-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="65812-243">JavaScript ファイルについて</span><span class="sxs-lookup"><span data-stu-id="65812-243">About the JavaScript file...</span></span>

<span data-ttu-id="65812-244">JavaScript ファイルの全体は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="65812-244">The entire JavaScript file is as follows:</span></span>

```
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefix 
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

``` 

<span data-ttu-id="65812-245">上記の `jQuery $(document).ready` 関数のコードの概要を説明するために `viewModel object` が作成され、次にそのオブジェクトに対する `loadNavigationNodes()` 関数が呼び出されています。</span><span class="sxs-lookup"><span data-stu-id="65812-245">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="65812-246">この関数は、クライアント ブラウザーの HTML5 ローカル ストレージに格納されている以前に作成されたナビゲーション階層を読み込むか、`queryRemoteInterface()` 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="65812-246">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="65812-247">`QueryRemoteInterface()` は、スクリプトの前の方で定義されているクエリ パラメーターを使用する `getRequest()` 関数を使用して要求を作成し、次にサーバーからのデータを返します。</span><span class="sxs-lookup"><span data-stu-id="65812-247">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="65812-248">このデータは基本的に、さまざまなプロパティを持つデータ転送オブジェクトとして表されるサイト コレクション内のすべてのサイトの配列です。</span><span class="sxs-lookup"><span data-stu-id="65812-248">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="65812-249">その後、このデータは、解析されて既に定義されている `SPO.Models.NavigationNode` オブジェクトになります。このオブジェクトは、`Knockout.js` を使用して観測可能なプロパティを作成します。このプロパティは、上で定義した HTML に値をバインディングするデータによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="65812-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="65812-250">オブジェクトは結果の配列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="65812-250">The objects are then put into a results array.</span></span> <span data-ttu-id="65812-251">この配列は、Knockout によって解析されて JSON になり、将来ページを読み込む際のパフォーマンス向上のため、ローカル ブラウザー ストレージに格納されます。</span><span class="sxs-lookup"><span data-stu-id="65812-251">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="65812-252">このアプローチの利点</span><span class="sxs-lookup"><span data-stu-id="65812-252">Benefits of this tool:</span></span>

<span data-ttu-id="65812-253">[このアプローチ](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)の主な利点の 1 つは、ナビゲーションが、HTML5 のローカルの記憶域を使用して、ユーザーによる次回のページの読み込みのため、ローカルに格納されることです。</span><span class="sxs-lookup"><span data-stu-id="65812-253">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="65812-254">構造ナビゲーション用に検索 API を使用することで、パフォーマンスが大きく向上します。ただし、この機能の実行とカスタマイズには技術的な能力が必要になります。</span><span class="sxs-lookup"><span data-stu-id="65812-254">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="65812-255">[実装の例](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)では、サイトは既成の構造ナビゲーションと同じ順序 (アルファベット順) に並べられています。</span><span class="sxs-lookup"><span data-stu-id="65812-255">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="65812-256">これとは異なる順序を使用する場合は、開発とメンテナンスがより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="65812-256">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="65812-257">また、このアプローチでは、サポートされているマスター ページから逸脱する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65812-257">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="65812-258">カスタム マスター ページの管理が行われない場合、サイトは Microsoft がマスター ページに対して加える更新と改善を利用できません。</span><span class="sxs-lookup"><span data-stu-id="65812-258">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="65812-259">[上記のコード](#about-the-javascript-file)には次のような依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="65812-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="65812-260">jQuery - http://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="65812-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="65812-261">KnockoutJS - http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="65812-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="65812-262">Linq.js - http://linqjs.codeplex.com/、または github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="65812-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="65812-263">LinqJS の現在のバージョンには、上記のコードで使用されている ByHierarchy メソッドが含まれておらず、ナビゲーション コードが機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="65812-263">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="65812-264">これを解決するには、Linq.js ファイルの `Flatten: function ()` の行の前に次のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="65812-264">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);
    
     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a><span data-ttu-id="65812-265">関連項目</span><span class="sxs-lookup"><span data-stu-id="65812-265">Related topics</span></span>

[<span data-ttu-id="65812-266">SharePoint Server の管理ナビゲーションの概要</span><span class="sxs-lookup"><span data-stu-id="65812-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

