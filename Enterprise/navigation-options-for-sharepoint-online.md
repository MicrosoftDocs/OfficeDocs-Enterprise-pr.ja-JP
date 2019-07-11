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
description: この記事では、sharepoint Online で SharePoint の発行が有効になっているナビゲーションオプションサイトについて説明します。 ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスとスケーラビリティに大きく影響します。
ms.openlocfilehash: b3194009d21f60093ec80cb2e138df34df60e22e
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616860"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="fe074-104">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="fe074-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="fe074-105">この記事では、sharepoint Online で SharePoint の発行が有効になっているナビゲーションオプションサイトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fe074-105">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="fe074-106">ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスとスケーラビリティに大きく影響します。</span><span class="sxs-lookup"><span data-stu-id="fe074-106">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="fe074-107">概要</span><span class="sxs-lookup"><span data-stu-id="fe074-107">Overview</span></span>

<span data-ttu-id="fe074-108">ナビゲーションプロバイダーの構成は、サイト全体のパフォーマンスに大きな影響を与える可能性があります。また、SharePoint サイトの要件を効果的に拡大できるようにするナビゲーションプロバイダーと構成を選択するには、慎重に検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-108">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="fe074-109">すぐに使えるナビゲーションプロバイダー、およびカスタムナビゲーションの実装は、2つあります。</span><span class="sxs-lookup"><span data-stu-id="fe074-109">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="fe074-110">最初のオプションである [ [**Managed (Metadata)] ナビゲーション**](#using-managed-navigation-and-metadata-in-sharepoint-online)は推奨されており、SharePoint Online の既定のオプションの1つです。ただし、セキュリティによるトリミングは必要でない限り無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fe074-110">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="fe074-111">セキュリティによるトリミングは、このナビゲーションプロバイダの既定の設定では有効になっています。ただし、多くのサイトでは、サイトのすべてのユーザーに対してナビゲーション要素の一貫性が保たれるため、セキュリティによるトリミングのオーバーヘッドが必要になることはありません。</span><span class="sxs-lookup"><span data-stu-id="fe074-111">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="fe074-112">セキュリティによるトリミングを無効にするために推奨される構成を使用すると、このナビゲーションプロバイダーはサイト構造の列挙を必要とせず、パフォーマンスへの影響が許容される高い拡張性を備えています。</span><span class="sxs-lookup"><span data-stu-id="fe074-112">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="fe074-113">2番目のオプションである[**構造ナビゲーション**](#using-structural-navigation-in-sharepoint-online)**は、SharePoint Online では推奨されていないナビゲーションオプションではありません**。</span><span class="sxs-lookup"><span data-stu-id="fe074-113">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="fe074-114">このナビゲーションプロバイダーは、オンプレミスのトポロジ向けに設計されており、SharePoint Online でのサポートに制限があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-114">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="fe074-115">他のナビゲーションオプションに加えて、その他の機能のセットが提供されていますが、これらの機能 (セキュリティトリミングやサイト構造の列挙を含む) には、サーバー呼び出しのコストがかかり、使用時のスケーラビリティとパフォーマンスに影響を与えるものがあります。</span><span class="sxs-lookup"><span data-stu-id="fe074-115">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="fe074-116">構造化されたナビゲーションを使用するサイトは、過剰なリソースを消費する場合があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-116">Sites using structured navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="fe074-117">すぐに利用できるナビゲーションプロバイダーに加えて、多くのお客様は、代替のカスタムナビゲーション実装を適切に実装しています。</span><span class="sxs-lookup"><span data-stu-id="fe074-117">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="fe074-118">カスタムナビゲーション実装の一般的なクラスの1つとして、ナビゲーションノードのローカルキャッシュを格納するクライアントレンダリングの設計パターンがあります。</span><span class="sxs-lookup"><span data-stu-id="fe074-118">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="fe074-119">(この記事の「**[検索型クライアント側スクリプト](#using-search-driven-client-side-scripting)**」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="fe074-119">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="fe074-120">これらのナビゲーションプロバイダーには、主にいくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="fe074-121">通常は、応答性の高いページデザインに対して適切に動作します。</span><span class="sxs-lookup"><span data-stu-id="fe074-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="fe074-122">リソースコストを使用せずにレンダリングでき、タイムアウト後にバックグラウンドで更新されるので、これらは非常にスケーラブルでパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="fe074-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="fe074-123">これらのナビゲーションプロバイダーは、単純な静的構成からさまざまな動的データプロバイダーまでのさまざまな戦略を使用してナビゲーションデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="fe074-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="fe074-124">データプロバイダーの例としては、**検索型ナビゲーション**を使用して、ナビゲーションノードをより柔軟に列挙し、セキュリティによるトリミングを効率的に処理する方法があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="fe074-125">**カスタムナビゲーションプロバイダー**を構築するには、他にも一般的なオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="fe074-125">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="fe074-126">カスタムナビゲーションプロバイダーを構築する方法については、「 [SharePoint Online ポータルのナビゲーションソリューション](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe074-126">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="fe074-127">SharePoint Online ナビゲーションオプションの長所と短所</span><span class="sxs-lookup"><span data-stu-id="fe074-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="fe074-128">次の表に、各オプションの長所と短所の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="fe074-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="fe074-129">管理ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="fe074-129">Managed navigation</span></span>  |<span data-ttu-id="fe074-130">構造ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="fe074-130">Structural navigation</span></span>  |<span data-ttu-id="fe074-131">検索型ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="fe074-131">Search-driven navigation</span></span>  |<span data-ttu-id="fe074-132">カスタムナビゲーションプロバイダー</span><span class="sxs-lookup"><span data-stu-id="fe074-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="fe074-133">専門</span><span class="sxs-lookup"><span data-stu-id="fe074-133">Pros:</span></span><br/><br/><span data-ttu-id="fe074-134">保守が容易</span><span class="sxs-lookup"><span data-stu-id="fe074-134">Easy to maintain</span></span><br/><span data-ttu-id="fe074-135">推奨されるオプション</span><span class="sxs-lookup"><span data-stu-id="fe074-135">Recommended option</span></span><br/>     |<span data-ttu-id="fe074-136">専門</span><span class="sxs-lookup"><span data-stu-id="fe074-136">Pros:</span></span><br/><br/><span data-ttu-id="fe074-137">構成が容易</span><span class="sxs-lookup"><span data-stu-id="fe074-137">Easy to configure</span></span><br/><span data-ttu-id="fe074-138">セキュリティによるトリミング</span><span class="sxs-lookup"><span data-stu-id="fe074-138">Security trimmed</span></span><br/><span data-ttu-id="fe074-139">コンテンツが追加されたときに自動的に更新する</span><span class="sxs-lookup"><span data-stu-id="fe074-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="fe074-140">専門</span><span class="sxs-lookup"><span data-stu-id="fe074-140">Pros:</span></span><br/><br/><span data-ttu-id="fe074-141">セキュリティによるトリミング</span><span class="sxs-lookup"><span data-stu-id="fe074-141">Security trimmed</span></span><br/><span data-ttu-id="fe074-142">サイトが追加されたときに自動的に更新する</span><span class="sxs-lookup"><span data-stu-id="fe074-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="fe074-143">高速読み込み時間とローカルにキャッシュされたナビゲーション構造</span><span class="sxs-lookup"><span data-stu-id="fe074-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="fe074-144">専門</span><span class="sxs-lookup"><span data-stu-id="fe074-144">Pros:</span></span><br/><br/><span data-ttu-id="fe074-145">利用可能なオプションの幅広い選択肢</span><span class="sxs-lookup"><span data-stu-id="fe074-145">Wider choice of options available</span></span><br/><span data-ttu-id="fe074-146">キャッシュが正しく使用されている場合の高速読み込み</span><span class="sxs-lookup"><span data-stu-id="fe074-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="fe074-147">応答性の高いページデザインでは、多くのオプションが適切に機能します。</span><span class="sxs-lookup"><span data-stu-id="fe074-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="fe074-148">連続</span><span class="sxs-lookup"><span data-stu-id="fe074-148">Cons:</span></span><br/><br/><span data-ttu-id="fe074-149">サイトの構造を反映するように自動的に更新されません</span><span class="sxs-lookup"><span data-stu-id="fe074-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="fe074-150">セキュリティによるトリミングが有効な場合のパフォーマンスへの影響</span><span class="sxs-lookup"><span data-stu-id="fe074-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="fe074-151">連続</span><span class="sxs-lookup"><span data-stu-id="fe074-151">Cons:</span></span><br/><br/><span data-ttu-id="fe074-152">**推奨されない**</span><span class="sxs-lookup"><span data-stu-id="fe074-152">**Not recommended**</span></span><br/><span data-ttu-id="fe074-153">**パフォーマンスとスケーラビリティに影響を与える**</span><span class="sxs-lookup"><span data-stu-id="fe074-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="fe074-154">**調整の対象**</span><span class="sxs-lookup"><span data-stu-id="fe074-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="fe074-155">連続</span><span class="sxs-lookup"><span data-stu-id="fe074-155">Cons:</span></span><br/><br/><span data-ttu-id="fe074-156">サイトを簡単に並べ替える機能がない</span><span class="sxs-lookup"><span data-stu-id="fe074-156">No ability to easily order sites</span></span><br/><span data-ttu-id="fe074-157">マスターページのカスタマイズが必要 (技術的なスキルが必要)</span><span class="sxs-lookup"><span data-stu-id="fe074-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="fe074-158">連続</span><span class="sxs-lookup"><span data-stu-id="fe074-158">Cons:</span></span><br/><br/><span data-ttu-id="fe074-159">カスタム開発が必要</span><span class="sxs-lookup"><span data-stu-id="fe074-159">Custom development is required</span></span><br/><span data-ttu-id="fe074-160">Azure などの外部データソース/キャッシュが必要です。</span><span class="sxs-lookup"><span data-stu-id="fe074-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="fe074-161">サイトに最適なオプションは、サイトの要件および技術的な機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="fe074-161">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="fe074-162">拡張可能なすぐに使用できるナビゲーションプロバイダーが必要な場合は、セキュリティによるトリミングを無効にした管理ナビゲーションは、非常に優れたオプションになります。</span><span class="sxs-lookup"><span data-stu-id="fe074-162">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span>

<span data-ttu-id="fe074-163">管理ナビゲーションオプションは、構成によって維持でき、コードカスタマイズファイルは含まれません。構造ナビゲーションよりも大幅に高速です。</span><span class="sxs-lookup"><span data-stu-id="fe074-163">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="fe074-164">セキュリティによるトリミングが必要で、カスタムマスターページを使用して、SharePoint Online の既定のマスターページで発生する可能性のある変更を維持する機能がある場合は、検索ドリブンオプションの方が良い場合があります。ユーザーの利便性。</span><span class="sxs-lookup"><span data-stu-id="fe074-164">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="fe074-165">より複雑な要件がある場合は、カスタムナビゲーションプロバイダーが正しい選択になることがあります。</span><span class="sxs-lookup"><span data-stu-id="fe074-165">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="fe074-166">構造ナビゲーションは推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="fe074-166">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="fe074-167">最後に、sharepoint は、よりフラット化されたサイト階層および SharePoint ハブサイトを使用したハブアンドスポークモデルを活用して、最新の SharePoint サイトアーキテクチャに対して追加のナビゲーションプロバイダーと機能を追加していることに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-167">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="fe074-168">これにより、SharePoint 発行機能の使用を必要としないさまざまなシナリオを実現することができます。これらのナビゲーション構成は、SharePoint Online 内のスケーラビリティと遅延のために最適化されています。</span><span class="sxs-lookup"><span data-stu-id="fe074-168">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="fe074-169">同じ原則を適用することによって、SharePoint 発行サイトの全体的な構造を flatter 構造に簡素化することで、多くの場合、全体的なパフォーマンスとスケールにも役立つことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fe074-169">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="fe074-170">これは、数百のサイト (サブ web) を持つ単一のサイトコレクションを使用するのではなく、多くのサイトコレクションを非常に少数のサブサイト (サブ web) で使用するということです。</span><span class="sxs-lookup"><span data-stu-id="fe074-170">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="fe074-171">SharePoint Online での管理ナビゲーションとメタデータの使用</span><span class="sxs-lookup"><span data-stu-id="fe074-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="fe074-172">管理ナビゲーションは、構造ナビゲーションと同じ機能のほとんどを再作成するための、すぐに使用できるもう1つのオプションです。</span><span class="sxs-lookup"><span data-stu-id="fe074-172">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="fe074-173">管理されたメタデータは、セキュリティによるトリミングを有効または無効にするように構成できます。</span><span class="sxs-lookup"><span data-stu-id="fe074-173">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="fe074-174">セキュリティによるトリミングが無効で構成されている場合、管理ナビゲーションは、一定数のサーバー呼び出しを使用してすべてのナビゲーションリンクを読み込むため、非常に効率的です。</span><span class="sxs-lookup"><span data-stu-id="fe074-174">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="fe074-175">ただし、セキュリティによるトリミングを有効にすると、管理ナビゲーションの利点の一部が否定され、お客様は最適なパフォーマンスとスケーラビリティを得るためにカスタムナビゲーションソリューションの1つを調査することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="fe074-175">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="fe074-176">多くのサイトでは、サイトのすべてのユーザーに対してナビゲーション構造が一貫しているため、セキュリティによるトリミングは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="fe074-176">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="fe074-177">セキュリティによるトリミングが無効で、すべてのユーザーがアクセスできないナビゲーションにリンクが追加されても、リンクは表示されますが、アクセス拒否メッセージになります。</span><span class="sxs-lookup"><span data-stu-id="fe074-177">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="fe074-178">コンテンツに偶発的にアクセスする危険性はありません。</span><span class="sxs-lookup"><span data-stu-id="fe074-178">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="fe074-179">管理ナビゲーションと結果を実装する方法</span><span class="sxs-lookup"><span data-stu-id="fe074-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="fe074-180">管理ナビゲーションの詳細については、「 [SharePoint Server の管理ナビゲーションの概要](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)」を参照してください。たとえば、Docs.Microsoft.com に関する記事があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="fe074-181">管理ナビゲーションを実装するために、サイトのナビゲーション構造に対応する Url を使用して用語を設定します。</span><span class="sxs-lookup"><span data-stu-id="fe074-181">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="fe074-182">管理ナビゲーションでは、多くの場合、構造ナビゲーションを手動で置き換えることもできます合わせ。</span><span class="sxs-lookup"><span data-stu-id="fe074-182">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="fe074-183">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="fe074-183">For example:</span></span>

![SharePoint Online サイト構造](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="fe074-185">次の例は、管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="fe074-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンス](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="fe074-187">管理ナビゲーションを使用すると、構造ナビゲーション手法と比較してパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="fe074-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="fe074-188">SharePoint Online で構造ナビゲーションを使用する</span><span class="sxs-lookup"><span data-stu-id="fe074-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="fe074-189">これは既定で使用される既定のナビゲーションですが、これは最も簡単な方法ですが、高コストのパフォーマンスのトレードオフがあります。</span><span class="sxs-lookup"><span data-stu-id="fe074-189">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="fe074-190">これはカスタマイズを必要とせず、技術的ではないユーザーも簡単にアイテムを追加したり、アイテムを非表示にしたり、設定ページからナビゲーションを管理したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="fe074-190">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="fe074-191">ただし、管理ナビゲーションでは、管理ナビゲーションを使用することをお勧めします。これは、パフォーマンスの向上にも容易に管理および制御できるので、管理ナビゲーションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fe074-191">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![サブサイトの表示が選択された構造ナビゲーション](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="fe074-193">SharePoint Online で構造ナビゲーションを有効にする</span><span class="sxs-lookup"><span data-stu-id="fe074-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="fe074-194">構造ナビゲーションと [サブサイトの表示] オプションがオンになっている標準的な SharePoint Online ソリューションのパフォーマンスがどのように機能するかを説明します。</span><span class="sxs-lookup"><span data-stu-id="fe074-194">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="fe074-195">[ページ**サイトの設定** \> ]**ナビゲーション**にある設定のスクリーンショットを次に示します。</span><span class="sxs-lookup"><span data-stu-id="fe074-195">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![サブサイトが表示されているスクリーンショット](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="fe074-197">SharePoint Online で構造ナビゲーションのパフォーマンスを分析する</span><span class="sxs-lookup"><span data-stu-id="fe074-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="fe074-198">SharePoint ページのパフォーマンスを分析するには、Internet Explorer の F12 開発者ツールの [**ネットワーク**] タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe074-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![F12 開発者ツールの [ネットワーク] タブが表示されているスクリーンショット](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="fe074-200">[**ネットワーク**] タブで、読み込まれている .aspx ページをクリックし、[**詳細**] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe074-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="fe074-201">![[詳細] タブが表示されているスクリーンショット](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="fe074-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="fe074-202">[**応答ヘッダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fe074-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="fe074-203">![[詳細] タブのスクリーンショット](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="fe074-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="fe074-204">SharePoint は、応答ヘッダーに有用な診断情報を返します。</span><span class="sxs-lookup"><span data-stu-id="fe074-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="fe074-205">最も有用な情報の1つは**Sprequestduration**で、サーバー上での要求の処理にかかった時間をミリ秒単位で示した値です。</span><span class="sxs-lookup"><span data-stu-id="fe074-205">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="fe074-206">次のスクリーンショットでは、構造ナビゲーションに対して [**サブサイトの表示]** がオフになっています。</span><span class="sxs-lookup"><span data-stu-id="fe074-206">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="fe074-207">これは、グローバルナビゲーションにサイトコレクションリンクのみが存在することを意味します。</span><span class="sxs-lookup"><span data-stu-id="fe074-207">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="fe074-208">![要求時間として負荷時間が表示されているスクリーンショット](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="fe074-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="fe074-209">**Sprequestduration**キーの値は245ミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="fe074-209">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="fe074-210">これは、要求を返すのにかかった時間を表します。</span><span class="sxs-lookup"><span data-stu-id="fe074-210">This represents the time it took to return the request.</span></span> <span data-ttu-id="fe074-211">サイトにはナビゲーションアイテムが1つしか存在しないため、これは、SharePoint Online が大きなナビゲーションなしでどのように動作するかについて適切なベンチマークです。</span><span class="sxs-lookup"><span data-stu-id="fe074-211">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="fe074-212">次のスクリーンショットは、サブサイトへの追加がこのキーに与える影響を示しています。</span><span class="sxs-lookup"><span data-stu-id="fe074-212">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="fe074-213">![2,502 ミリ秒の要求時間が表示されているスクリーンショット](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="fe074-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="fe074-214">サブサイトを追加すると、この比較的単純なサンプルサイトのページ要求を返すのにかかる時間が大幅に増加しました。</span><span class="sxs-lookup"><span data-stu-id="fe074-214">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="fe074-215">ナビゲーション内のページやその他の構成およびトポロジオプションを含む、複雑なサイト階層は、この影響をさらに大きく増加させる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-215">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="fe074-216">検索型クライアント側スクリプトを使用する</span><span class="sxs-lookup"><span data-stu-id="fe074-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="fe074-217">検索を使用すると、継続的クロールを使用してバックグラウンドで構築されたインデックスを活用できます。</span><span class="sxs-lookup"><span data-stu-id="fe074-217">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="fe074-218">検索結果は検索インデックスから取り出され、結果はセキュリティによってトリミングされます。</span><span class="sxs-lookup"><span data-stu-id="fe074-218">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="fe074-219">通常、セキュリティによるトリミングが必要な場合は、標準のナビゲーションプロバイダーよりも高速です。</span><span class="sxs-lookup"><span data-stu-id="fe074-219">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="fe074-220">構造ナビゲーションで検索を使用すると、特に複雑なサイト構造の場合は、ページの読み込み時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="fe074-220">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="fe074-221">この管理ナビゲーション全体の主な利点は、セキュリティによるトリミングによる恩恵を受けることです。</span><span class="sxs-lookup"><span data-stu-id="fe074-221">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="fe074-222">この方法では、カスタムマスターページを作成し、すぐに使用できないナビゲーションコードをカスタム HTML に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-222">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="fe074-223">次の例に示されている手順に従って、ファイル`seattle.html`のナビゲーションコードを置換します。</span><span class="sxs-lookup"><span data-stu-id="fe074-223">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="fe074-224">この例では、 `seattle.html`ファイルを開き、要素`id=”DeltaTopNavigation”`全体をカスタム HTML コードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="fe074-224">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="fe074-225">例: マスターページですぐに使用するナビゲーションコードを置換する</span><span class="sxs-lookup"><span data-stu-id="fe074-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="fe074-226">[サイトの設定] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="fe074-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="fe074-227">[**マスター**ページ] をクリックして、マスターページギャラリーを開きます。</span><span class="sxs-lookup"><span data-stu-id="fe074-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="fe074-228">ここから、ライブラリ内を移動して、ファイル`seattle.master`をダウンロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="fe074-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="fe074-229">テキストエディターを使用してコードを編集し、次のスクリーンショットのコードブロックを削除します。</span><span class="sxs-lookup"><span data-stu-id="fe074-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![表示されているコードブロックを削除する](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="fe074-231">タグとタグの間`<SharePoint:AjaxDelta id=”DeltaTopNavigation”>`のコードを削除し、次のスニペットに置き換えます。 `<\SharePoint:AjaxDelta>`</span><span class="sxs-lookup"><span data-stu-id="fe074-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

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
6. <span data-ttu-id="fe074-232">読み込みイメージのアンカータグの URL を、サイトコレクションの読み込み中の画像へのリンクを使用して、先頭に置きます。</span><span class="sxs-lookup"><span data-stu-id="fe074-232">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="fe074-233">変更を行った後、ファイルの名前を変更して、マスターページギャラリーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="fe074-233">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="fe074-234">これにより、新しい .master ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="fe074-234">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="fe074-235">この HTML は、JavaScript コードから返される検索結果によって設定される基本的なマークアップです。</span><span class="sxs-lookup"><span data-stu-id="fe074-235">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="fe074-236">次のスニペットで示すように、var root = "site collection URL" の値を変更するコードを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-236">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="fe074-237">結果は、自身の nodes 配列に割り当てられ、そのオブジェクトから階層が構築されます。このオブジェクトには、出力を配列 self に割り当てるための linq を使用します。</span><span class="sxs-lookup"><span data-stu-id="fe074-237">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="fe074-238">この配列は、HTML にバインドされたオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="fe074-238">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="fe074-239">これは、ko-kr () 関数に self オブジェクトを渡すことによって、toggleView () 関数で行われます。</span><span class="sxs-lookup"><span data-stu-id="fe074-239">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="fe074-240">これにより、階層配列が次の HTML にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="fe074-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="fe074-241">の`mouseenter`イベントハンドラーは、 `mouseexit` `addEventsToElements()`関数で実行されるサブサイトのドロップダウンメニューを処理するために、トップレベルのナビゲーションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="fe074-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="fe074-242">複雑なナビゲーションの例では、ローカルキャッシュを使用せずに新しいページ読み込みを行うと、ベンチマーク構造ナビゲーションからサーバーにかかった時間が短縮され、管理ナビゲーション方法と同様の結果が得られることがわかります。</span><span class="sxs-lookup"><span data-stu-id="fe074-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="fe074-243">JavaScript ファイルについて...</span><span class="sxs-lookup"><span data-stu-id="fe074-243">About the JavaScript file...</span></span>

<span data-ttu-id="fe074-244">JavaScript ファイル全体は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fe074-244">The entire JavaScript file is as follows:</span></span>

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

<span data-ttu-id="fe074-245">この`jQuery $(document).ready`関数の上記のコードを要約するには、 `viewModel object`が作成され`loadNavigationNodes()`ていて、そのオブジェクトの関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="fe074-245">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="fe074-246">この関数は、クライアントブラウザーの HTML5 ローカルストレージに格納されている、以前に作成したナビゲーション階層`queryRemoteInterface()`を読み込むか、または関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fe074-246">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="fe074-247">`QueryRemoteInterface()`スクリプト内で事前に`getRequest()`定義されたクエリパラメーターを使用して、関数を使用して要求を作成し、サーバーからデータを返します。</span><span class="sxs-lookup"><span data-stu-id="fe074-247">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="fe074-248">このデータは基本的に、サイトコレクション内のすべてのサイトの配列であり、さまざまなプロパティを持つデータ転送オブジェクトとして表されます。</span><span class="sxs-lookup"><span data-stu-id="fe074-248">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="fe074-249">このデータは、以前に定義した`SPO.Models.NavigationNode` HTML に値`Knockout.js`をデータバインドすることによって使用される観測可能なプロパティを作成するために使用する、以前に定義したオブジェクトに解析されます。</span><span class="sxs-lookup"><span data-stu-id="fe074-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="fe074-250">その後、オブジェクトは結果配列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="fe074-250">The objects are then put into a results array.</span></span> <span data-ttu-id="fe074-251">この配列は、今後のページ読み込み時のパフォーマンスを向上させるために、ノックアウトを使用して JSON に解析され、ローカルブラウザーストレージに格納されます。</span><span class="sxs-lookup"><span data-stu-id="fe074-251">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="fe074-252">このアプローチの利点</span><span class="sxs-lookup"><span data-stu-id="fe074-252">Benefits of this approach</span></span>

<span data-ttu-id="fe074-253">[このアプローチ](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)の主な利点の1つは、HTML5 ローカルストレージを使用することによって、ユーザーが次回ページを読み込むときに、ナビゲーションがローカルに保存されることです。</span><span class="sxs-lookup"><span data-stu-id="fe074-253">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="fe074-254">構造化ナビゲーションで検索 API を使用することによって、パフォーマンスが大幅に向上しました。ただし、この機能を実行してカスタマイズするには、いくつかの技術的な機能が必要です。</span><span class="sxs-lookup"><span data-stu-id="fe074-254">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="fe074-255">[実装例](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)では、サイトは、すぐに使用できる構造ナビゲーションと同じ方法で並べられています。アルファベット順</span><span class="sxs-lookup"><span data-stu-id="fe074-255">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="fe074-256">この順序から逸脱する必要がある場合は、開発と管理がより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="fe074-256">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="fe074-257">また、この方法では、サポートされているマスタページから逸脱する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-257">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="fe074-258">カスタムマスターページが保持されていない場合、サイトは、Microsoft がマスターページに加えた更新プログラムと機能強化を見逃さないようになります。</span><span class="sxs-lookup"><span data-stu-id="fe074-258">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="fe074-259">[上記のコード](#about-the-javascript-file)には、次のような依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="fe074-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="fe074-260">jQueryhttp://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="fe074-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="fe074-261">KnockoutJS -http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="fe074-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="fe074-262">Linq- http://linqjs.codeplex.com/、または github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="fe074-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="fe074-263">LinqJS の現在のバージョンには、上記のコードで使用されている ByHierarchy メソッドは含まれていません。また、ナビゲーションコードが破損します。</span><span class="sxs-lookup"><span data-stu-id="fe074-263">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="fe074-264">この問題を解決するには、次のメソッドを Linq ファイルに追加し`Flatten: function ()`て、行の前に追加します。</span><span class="sxs-lookup"><span data-stu-id="fe074-264">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

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
  
## <a name="related-topics"></a><span data-ttu-id="fe074-265">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe074-265">Related topics</span></span>

[<span data-ttu-id="fe074-266">SharePoint Server の管理ナビゲーションの概要</span><span class="sxs-lookup"><span data-stu-id="fe074-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

