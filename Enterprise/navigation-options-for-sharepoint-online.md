---
title: SharePoint Online のナビゲーション オプション
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: この記事では、SharePoint Publishing が有効化されている SharePoint Online サイトのナビゲーション オプションについて説明します。 ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスと拡張性に大きく影響します。 この記事は、従来のチーム サイトには適用されません。
ms.openlocfilehash: 410be307fca62c987baed39601e122717a6bebcc
ms.sourcegitcommit: b1042fa2d02f1bc74586751c542776325d3a170f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "43170655"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="6e19a-105">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="6e19a-105">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="6e19a-106">この記事では、SharePoint Publishing が有効化されている SharePoint Online サイトのナビゲーション オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-106">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="6e19a-107">ナビゲーションの選択と構成は、SharePoint Online のサイトのパフォーマンスとスケーラビリティに大きく影響します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-107">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span> <span data-ttu-id="6e19a-108">SharePoint 発行サイトテンプレートは、集中管理ポータルに必要な場合にのみ使用し、発行機能は特定のサイトに対してのみ有効にする必要があります。また、適切に使用しないと、必要な場合にのみ、パフォーマンスに影響することがあります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-108">The SharePoint Publishing site template should only be used if required for a centralized portal and the publishing feature should only be enabled on specific sites and only when absolutely required as it can impact performance when used incorrectly.</span></span>

>[!NOTE]
><span data-ttu-id="6e19a-109">メガメニュー、カスケードナビゲーション、ハブナビゲーションなどのモダン SharePoint ナビゲーションオプションを使用している場合、この記事はサイトに適用されません。</span><span class="sxs-lookup"><span data-stu-id="6e19a-109">If you're using modern SharePoint navigation options like mega menu, cascading navigation, or hub navigation, this article does not apply to your site.</span></span> <span data-ttu-id="6e19a-110">モダンな SharePoint サイトアーキテクチャは、よりフラット化されたサイト階層とハブアンドスポークモデルを活用します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-110">Modern SharePoint site architectures leverage a more flattened site hierarchy and a hub-and-spoke model.</span></span> <span data-ttu-id="6e19a-111">これにより、SharePoint 発行機能の使用を必要としない多くのシナリオを実現できます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-111">This allows many scenarios to be achieved that do NOT require use of the SharePoint Publishing feature.</span></span>

## <a name="overview"></a><span data-ttu-id="6e19a-112">概要</span><span class="sxs-lookup"><span data-stu-id="6e19a-112">Overview</span></span>

<span data-ttu-id="6e19a-113">ナビゲーション プロバイダーの構成はサイト全体のパフォーマンスに大きな影響を与える可能性があるため、SharePoint サイトの要件を満たすように効果的に対応できるナビゲーション プロバイダーと構成を慎重に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-113">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="6e19a-114">2 つの既成のナビゲーション プロバイダーの他、ナビゲーションのカスタム実装が提供されています。</span><span class="sxs-lookup"><span data-stu-id="6e19a-114">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="6e19a-115">**サイトの構造ナビゲーションキャッシュを有効にする場合**、最初のオプションである[**構造ナビゲーション**](#using-structural-navigation-in-sharepoint-online)は、従来の Sharepoint サイトの sharepoint Online で推奨されるナビゲーションオプションです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-115">The first option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), is the recommended navigation option in SharePoint Online for classic Sharepoint sites, **if you turn on structural navigation caching for your site**.</span></span> <span data-ttu-id="6e19a-116">このナビゲーションプロバイダは、現在のサイトの下にあるナビゲーションアイテム、および必要に応じて現在のサイトとその兄弟を表示します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-116">This navigation provider displays the navigation items below the current site, and optionally the current site and its siblings.</span></span> <span data-ttu-id="6e19a-117">これにより、セキュリティトリミングやサイト構造の列挙などの追加機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-117">It provides additional capabilities such as security trimming and site structure enumeration.</span></span> <span data-ttu-id="6e19a-118">キャッシュを無効にすると、パフォーマンスとスケーラビリティに悪影響を及ぼす可能性があり、調整の対象となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-118">If caching is disabled, this will negatively impact performance and scalability, and may be subject to throttling.</span></span>

<span data-ttu-id="6e19a-119">2番目のオプションである[**managed (メタデータ) ナビゲーション**](#using-managed-navigation-and-metadata-in-sharepoint-online)は、管理されたメタデータ用語セットを使用したナビゲーションアイテムを表します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-119">The second option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), represents navigation items using a Managed Metadata term set.</span></span> <span data-ttu-id="6e19a-120">必要でない限り、セキュリティによるトリミングを無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6e19a-120">We recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="6e19a-121">セキュリティ トリミングは既定によるセキュリティ保護としてこのナビゲーション プロバイダーで有効化されていますが、多くのサイトでは、サイトのすべてのユーザーに対して一貫性のあるナビゲーション要素を提供しているため、セキュリティ トリミングのオーバーヘッドは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="6e19a-121">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="6e19a-122">推奨されているセキュリティトリミングを無効にする構成にした場合、このナビゲーション プロバイダーではサイト構造を列挙する必要がなく、パフォーマンスへの影響を許容範囲に抑えながら高い拡張性が提供されます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-122">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="6e19a-123">既成のナビゲーション プロバイダーに加えて、多くのお客様が代替のカスタム ナビゲーション実装を正常に実装しています。</span><span class="sxs-lookup"><span data-stu-id="6e19a-123">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="6e19a-124">この記事の「[検索型クライアント側スクリプト](#using-search-driven-client-side-scripting)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e19a-124">See [Search-driven client-side scripting](#using-search-driven-client-side-scripting) in this article.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="6e19a-125">SharePoint Online ナビゲーション オプションの長所と短所</span><span class="sxs-lookup"><span data-stu-id="6e19a-125">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="6e19a-126">次の表は、各オプションの長所と短所をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-126">The following table summarizes the pros and cons of each option.</span></span>

|<span data-ttu-id="6e19a-127">構造ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="6e19a-127">Structural navigation</span></span>  |<span data-ttu-id="6e19a-128">管理ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="6e19a-128">Managed navigation</span></span>  |<span data-ttu-id="6e19a-129">検索型ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="6e19a-129">Search-driven navigation</span></span>  |<span data-ttu-id="6e19a-130">カスタム ナビゲーション プロバイダー</span><span class="sxs-lookup"><span data-stu-id="6e19a-130">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="6e19a-131">長所:</span><span class="sxs-lookup"><span data-stu-id="6e19a-131">Pros:</span></span><br/><br/><span data-ttu-id="6e19a-132">メンテナンスしやすい</span><span class="sxs-lookup"><span data-stu-id="6e19a-132">Easy to maintain</span></span><br/><span data-ttu-id="6e19a-133">セキュリティ トリミングが行われる</span><span class="sxs-lookup"><span data-stu-id="6e19a-133">Security trimmed</span></span><br/><span data-ttu-id="6e19a-134">コンテンツが変更されたときに24時間以内に自動更新される</span><span class="sxs-lookup"><span data-stu-id="6e19a-134">Automatically updates within 24 hours when content is changed</span></span><br/>     |<span data-ttu-id="6e19a-135">長所:</span><span class="sxs-lookup"><span data-stu-id="6e19a-135">Pros:</span></span><br/><br/><span data-ttu-id="6e19a-136">メンテナンスしやすい</span><span class="sxs-lookup"><span data-stu-id="6e19a-136">Easy to maintain</span></span><br/>|<span data-ttu-id="6e19a-137">長所:</span><span class="sxs-lookup"><span data-stu-id="6e19a-137">Pros:</span></span><br/><br/><span data-ttu-id="6e19a-138">セキュリティ トリミングが行われる</span><span class="sxs-lookup"><span data-stu-id="6e19a-138">Security trimmed</span></span><br/><span data-ttu-id="6e19a-139">サイトが追加されると自動的に更新される</span><span class="sxs-lookup"><span data-stu-id="6e19a-139">Automatically updates as sites are added</span></span><br/><span data-ttu-id="6e19a-140">読み込み時間が短く、ナビゲーション構造がローカルにキャッシュされている</span><span class="sxs-lookup"><span data-stu-id="6e19a-140">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="6e19a-141">長所:</span><span class="sxs-lookup"><span data-stu-id="6e19a-141">Pros:</span></span><br/><br/><span data-ttu-id="6e19a-142">使用可能なオプションの選択肢が広い</span><span class="sxs-lookup"><span data-stu-id="6e19a-142">Wider choice of options available</span></span><br/><span data-ttu-id="6e19a-143">キャッシュが正常に使用された場合、高速の読み込み</span><span class="sxs-lookup"><span data-stu-id="6e19a-143">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="6e19a-144">多くのオプションが、応答性の高いページ デザインで適正に動作する</span><span class="sxs-lookup"><span data-stu-id="6e19a-144">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="6e19a-145">短所:</span><span class="sxs-lookup"><span data-stu-id="6e19a-145">Cons:</span></span><br/><br/><span data-ttu-id="6e19a-146">**キャッシュが無効な場合のパフォーマンスへの影響**</span><span class="sxs-lookup"><span data-stu-id="6e19a-146">**Impacts performance if caching is disabled**</span></span><br/><span data-ttu-id="6e19a-147">調整の対象</span><span class="sxs-lookup"><span data-stu-id="6e19a-147">Subject to throttling</span></span><br/>|<span data-ttu-id="6e19a-148">短所:</span><span class="sxs-lookup"><span data-stu-id="6e19a-148">Cons:</span></span><br/><br/><span data-ttu-id="6e19a-149">サイト構造を反映するように自動的に更新されない</span><span class="sxs-lookup"><span data-stu-id="6e19a-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="6e19a-150">**セキュリティによるトリミングが有効な場合**、またはナビゲーション構造が複雑な場合は、パフォーマンスに影響を与える</span><span class="sxs-lookup"><span data-stu-id="6e19a-150">**Impacts performance if security trimming is enabled** or when navigation structure is complex</span></span><br/>|<span data-ttu-id="6e19a-151">短所:</span><span class="sxs-lookup"><span data-stu-id="6e19a-151">Cons:</span></span><br/><br/><span data-ttu-id="6e19a-152">サイトの順序を簡単に変更できない</span><span class="sxs-lookup"><span data-stu-id="6e19a-152">No ability to easily order sites</span></span><br/><span data-ttu-id="6e19a-153">マスター ページのカスタマイズが必要 (技術的なスキルが必要)</span><span class="sxs-lookup"><span data-stu-id="6e19a-153">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="6e19a-154">短所:</span><span class="sxs-lookup"><span data-stu-id="6e19a-154">Cons:</span></span><br/><br/><span data-ttu-id="6e19a-155">カスタム開発が必要</span><span class="sxs-lookup"><span data-stu-id="6e19a-155">Custom development is required</span></span><br/><span data-ttu-id="6e19a-156">外部データ ソース / 格納されたキャッシュが必要 (例: Azure)</span><span class="sxs-lookup"><span data-stu-id="6e19a-156">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="6e19a-157">サイトに最適なオプションは、サイトの要件と技術的な能力に依存しています。</span><span class="sxs-lookup"><span data-stu-id="6e19a-157">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="6e19a-158">コンテンツが変更されたときに自動的に更新される、簡単に構成できるナビゲーションプロバイダが必要な場合は、[キャッシュが有効](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)な構造ナビゲーションを有効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6e19a-158">If you want an easy-to-configure navigation provider that automatically updates when content is changed, then structural navigation [with caching enabled](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) is a good option.</span></span>

>[!NOTE]
><span data-ttu-id="6e19a-159">Flatter の全体的なサイト構造を簡素化して、最新の SharePoint サイトと同じ原則を適用すると、階層構造ではない構造でパフォーマンスが向上し、最新の SharePoint サイトへの移行が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-159">Applying the same principle as modern SharePoint sites by simplifying the overall site structure to a flatter, non-hierarchical structure improves performance and simplifies moving to modern SharePoint sites.</span></span> <span data-ttu-id="6e19a-160">これは、数百のサイト (サブ web) を持つ単一のサイトコレクションを使用するのではなく、多くのサイトコレクションを非常に少数のサブサイト (サブ web) で使用するということです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-160">What this means is that instead of having a single site collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="6e19a-161">SharePoint Online でナビゲーションパフォーマンスを分析する</span><span class="sxs-lookup"><span data-stu-id="6e19a-161">Analyzing navigation performance in SharePoint Online</span></span>

<span data-ttu-id="6e19a-162">[Sharepoint 用ページ診断ツール](https://aka.ms/perftool)は、sharepoint Online モダンポータルと従来の発行サイトページの両方を分析する Microsoft Edge および Chrome ブラウザー用のブラウザー拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="6e19a-162">The [Page Diagnostics for SharePoint tool](https://aka.ms/perftool) is a browser extension for Microsoft Edge and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="6e19a-163">このツールは、SharePoint Online に対してのみ機能し、SharePoint システムページでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="6e19a-163">This tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="6e19a-164">解析された各ページに対して、定義済みのルールセットに対してページがどのように表示されるかを示すレポートを生成し、テストの結果が基準値の範囲外にある場合に詳細情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-164">The tool generates a report for each analyzed page showing how the page performs against a pre-defined set of rules and displays detailed information when results for a test fall outside the baseline value.</span></span> <span data-ttu-id="6e19a-165">SharePoint Online の管理者および設計者は、このツールを使用してパフォーマンス上の問題をトラブルシューティングして、新しいページが発行される前に最適化されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-165">SharePoint Online administrators and designers can use the tool to troubleshoot performance issues to ensure that new pages are optimized prior to publishing.</span></span>

<span data-ttu-id="6e19a-166">特に、 **Sprequestduration**は、SharePoint がページを処理するのにかかる時間です。</span><span class="sxs-lookup"><span data-stu-id="6e19a-166">**SPRequestDuration** in particular is the time it takes for SharePoint to process the page.</span></span> <span data-ttu-id="6e19a-167">ヘビーナビゲーション (ナビゲーションにページを含めるなど)、複雑なサイト階層、およびその他の構成およびトポロジオプションは、長い期間に劇的に貢献します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-167">Heavy navigation (like including pages in navigation), complex site hierarchies, and other configuration and topology options can all dramatically contribute to longer durations.</span></span>

## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="6e19a-168">SharePoint Online で構造ナビゲーションを使用する</span><span class="sxs-lookup"><span data-stu-id="6e19a-168">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="6e19a-169">これは既定で使用される既定のナビゲーションで、最も簡単なソリューションです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-169">This is the out-of-the-box navigation used by default and is the most straightforward solution.</span></span> <span data-ttu-id="6e19a-170">カスタマイズの必要がなく、非技術者のユーザーでもアイテムの追加、アイテムの非表示、ナビゲーションの管理を [設定] ページから簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-170">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="6e19a-171">キャッシュを[有効にする](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)ことをお勧めします。それ以外の場合は、高価なパフォーマンスのトレードオフがあります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-171">We recommend [enabling caching](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), otherwise there is an expensive performance trade-off.</span></span>

### <a name="how-to-implement-structural-navigation-caching"></a><span data-ttu-id="6e19a-172">構造ナビゲーションキャッシュを実装する方法</span><span class="sxs-lookup"><span data-stu-id="6e19a-172">How to implement structural navigation caching</span></span>

<span data-ttu-id="6e19a-173">[**サイト設定** > の**ルックアンドフィール** > **ナビゲーション**] で、グローバルナビゲーションまたは現在のナビゲーションのいずれかで構造ナビゲーションが選択されているかどうかを検証できます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-173">Under **Site Settings** > **Look and Feel** > **Navigation**, you can validate if structural navigation is selected for either global navigation or current navigation.</span></span> <span data-ttu-id="6e19a-174">[**ページの表示]** を選択すると、パフォーマンスに悪影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-174">Selecting **Show pages** will have negative impact on performance.</span></span>

![[サブサイトを表示する] が選択されている構造ナビゲーション](media/SPONavOptionsStructuredShowSubsites.png)

<span data-ttu-id="6e19a-176">キャッシュは、サイトコレクションレベルおよびサイトレベルで有効または無効にできます。既定では、両方に対して有効になっています。</span><span class="sxs-lookup"><span data-stu-id="6e19a-176">Caching can be enabled or disabled at the site collection level and at the site level, and is enabled for both by default.</span></span> <span data-ttu-id="6e19a-177">サイトコレクションレベルで有効にするには、サイト**設定** > **サイトコレクション管理** > **サイトコレクションナビゲーション**で、[**キャッシュを有効にする**] のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6e19a-177">To enable at the site collection level, under **Site Settings** > **Site Collection Administration** > **Site Collection Navigation**, check the box for **Enable caching**.</span></span>

![サイトレベルでキャッシュを有効にする](media/structural-nav/structural-nav-caching-site-coll.png)

<span data-ttu-id="6e19a-179">サイトレベルで有効にするには、[**サイトの設定** > ]**ナビゲーション**で、[**キャッシュを有効**にする] のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6e19a-179">To enable at the site level, under **Site Settings** > **Navigation**, check the box for **Enable caching**.</span></span>

![サイトレベルでキャッシュを有効にする](media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="6e19a-181">SharePoint Online で管理ナビゲーションおよび管理されたメタデータを使用する</span><span class="sxs-lookup"><span data-stu-id="6e19a-181">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="6e19a-182">別の既成のオプションとして管理ナビゲーションがあり、このオプションを使用して構造ナビゲーションの機能のほとんどを再現できます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-182">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="6e19a-183">管理されたメタデータの構成では、セキュリティ トリミングは有効にも無効にもできます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-183">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="6e19a-184">構成でセキュリティ トリミングが無効化されている場合、管理ナビゲーションは、一定数のサーバー呼び出しを使用してすべてのナビゲーション リンクを読み込むので、比較的効率的です。</span><span class="sxs-lookup"><span data-stu-id="6e19a-184">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="6e19a-185">ただし、セキュリティによるトリミングを有効にすると、管理ナビゲーションのパフォーマンス上の利点の一部を否定できます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-185">Enabling security trimming, however, negates some of the performance advantages of managed navigation.</span></span>

<span data-ttu-id="6e19a-186">セキュリティによるトリミングを有効にする必要がある場合は、次のことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6e19a-186">If you need to enable security trimming, we recommend that you:</span></span>

- <span data-ttu-id="6e19a-187">すべてのフレンドリ URL のリンクを簡単なリンクに更新する</span><span class="sxs-lookup"><span data-stu-id="6e19a-187">Update all friendly URL links to simple links</span></span>
- <span data-ttu-id="6e19a-188">フレンドリ Url として必要なセキュリティトリミングノードを追加する</span><span class="sxs-lookup"><span data-stu-id="6e19a-188">Add required security trimming nodes as friendly URLs</span></span>
- <span data-ttu-id="6e19a-189">ナビゲーションアイテムの数を100以下に制限し、深さが3レベルを超えないようにする</span><span class="sxs-lookup"><span data-stu-id="6e19a-189">Limit the number of navigation items to no more than 100 and no more than 3 levels deep</span></span>

<span data-ttu-id="6e19a-190">多くのサイトではセキュリティ トリミングは必要ありません。これは、サイトのすべてのユーザーのナビゲーション構造が多くの場合共通であるためです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-190">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="6e19a-191">セキュリティ トリミングが無効になっていて、アクセス権を持たないユーザーもいるナビゲーションにリンクが追加された場合、リンクは表示されますが、アクセスが拒否されたというメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-191">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="6e19a-192">コンテンツへの偶発的なアクセスが発生する危険はありません。</span><span class="sxs-lookup"><span data-stu-id="6e19a-192">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="6e19a-193">管理ナビゲーションと結果を実装する方法</span><span class="sxs-lookup"><span data-stu-id="6e19a-193">How to implement managed navigation and the results</span></span>

<span data-ttu-id="6e19a-194">管理ナビゲーションの詳細については、docs.microsoft.com にいくつかの記事があります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-194">There are several articles on docs.microsoft.com about the details of managed navigation.</span></span> <span data-ttu-id="6e19a-195">例については、「 [SharePoint Server の管理ナビゲーションの概要](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e19a-195">For example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="6e19a-196">管理ナビゲーションを実装するために、サイトのナビゲーション構造に対応する Url を使用して用語を設定します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-196">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of the site.</span></span> <span data-ttu-id="6e19a-197">管理ナビゲーションは多くの場合、手動で監督することにより構造ナビゲーションと置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-197">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="6e19a-198">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-198">For example:</span></span>

![SharePoint Online サイトの構造](media/SPONavOptionsListOfSites.png)<span data-ttu-id="6e19a-200">)</span><span class="sxs-lookup"><span data-stu-id="6e19a-200">)</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="6e19a-201">検索型のクライアント側スクリプトを使用する</span><span class="sxs-lookup"><span data-stu-id="6e19a-201">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="6e19a-202">カスタム ナビゲーション実装の一般的なクラスの 1 つとして、ナビゲーション ノードのローカル キャッシュを格納するクライアント レンダリングによるデザイン パターンがあります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-202">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span>

<span data-ttu-id="6e19a-203">これらのナビゲーション プロバイダーには、いくつかの大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-203">These navigation providers have a couple of key advantages:</span></span>

- <span data-ttu-id="6e19a-204">これらのナビゲーション プロバイダーは通常、応答性の高いページ デザインに適しています。</span><span class="sxs-lookup"><span data-stu-id="6e19a-204">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="6e19a-205">リソース コストをかけずにレンダリングできるため、拡張性が高く、高性能です (また、タイムアウト後にバックグラウンドでの更新が可能です)。</span><span class="sxs-lookup"><span data-stu-id="6e19a-205">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span>
- <span data-ttu-id="6e19a-206">これらのナビゲーション プロバイダーは、単純な静的構成からさまざまな動的データ プロバイダーまでを含む、さまざまな方法を使用してナビゲーション データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-206">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span>

<span data-ttu-id="6e19a-207">データ プロバイダーの例として、ナビゲーション ノードの列挙とセキュリティ トリミングの効率的な処理が可能な**検索型ナビゲーション**を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-207">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span>

<span data-ttu-id="6e19a-208">**カスタム ナビゲーション プロバイダー**を構築するための一般的なオプションは他にもあります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-208">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="6e19a-209">カスタム ナビゲーション プロバイダーを構築する方法に関するより詳細なガイダンスついては、「[SharePoint Online ポータル用のナビゲーション ソリューション](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e19a-209">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>

<span data-ttu-id="6e19a-210">検索を使用すると、継続的クロールによってバックグラウンドでビルドされたインデックスを活用できます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-210">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="6e19a-211">検索結果が検索インデックスから取り込まれ、結果はセキュリティ トリミングされます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-211">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="6e19a-212">通常、セキュリティ トリミングが必要な場合は、既成のナビゲーション プロバイダーより高速です。</span><span class="sxs-lookup"><span data-stu-id="6e19a-212">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="6e19a-213">構造ナビゲーションで検索を使用すると、特に複雑なサイト構造がある場合は、ページの読み込み時間が大幅に短縮します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-213">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="6e19a-214">管理ナビゲーションに対するこの方法の主な利点は、セキュリティ トリミングの恩恵を受けられることです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-214">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="6e19a-215">このアプローチには、カスタム マスター ページの作成、既成のナビゲーション コードのカスタム HTML への置き換えなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-215">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="6e19a-216">ファイル `seattle.html` のナビゲーション コードを置き換えるには、次の例に示す手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-216">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="6e19a-217">この例では、`seattle.html`ファイルを開き、`id="DeltaTopNavigation"` という要素全体をカスタム HTML コードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-217">In this example, you will open the `seattle.html` file and replace the whole element `id="DeltaTopNavigation"` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="6e19a-218">例: マスター ページの既成のナビゲーション コードを置き換える</span><span class="sxs-lookup"><span data-stu-id="6e19a-218">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1. <span data-ttu-id="6e19a-219">[サイト設定] ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-219">Navigate to the Site Settings page.</span></span>
2. <span data-ttu-id="6e19a-220">[**マスター ページ**] をクリックして、マスター ページ ギャラリーを開きます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-220">Open the master page gallery by clicking **Master Pages**.</span></span>
3. <span data-ttu-id="6e19a-221">ここから、ライブラリ内を移動してファイル `seattle.master` をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-221">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4. <span data-ttu-id="6e19a-222">テキスト エディターでコードを編集し、次のスクリーン ショットにあるコード ブロックを削除します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-222">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![示されたコードブロックを削除する](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="6e19a-224">タグ `<SharePoint:AjaxDelta id="DeltaTopNavigation">` と `<\SharePoint:AjaxDelta>` の間のコードを削除し、次のスニペットに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-224">Remove the code between the `<SharePoint:AjaxDelta id="DeltaTopNavigation">` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```javascript
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
6. <span data-ttu-id="6e19a-225">冒頭の読み込みイメージのアンカー タグの URL を、サイト コレクションの読み込みイメージへのリンクに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-225">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="6e19a-226">変更を加えたら、ファイルの名前を変更し、マスター ページ ギャラリーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="6e19a-226">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="6e19a-227">これにより、新しい .master ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-227">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="6e19a-228">この HTML は、JavaScript のコードから返される検索結果によって入力される基本的なマークアップです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-228">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="6e19a-229">次のスニペットで示すように、var root = "site collection URL" の値を変更するコードを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-229">You will need to edit the code to change the value for var root = "site collection URL" as demonstrated in the following snippet:</span></span><br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. <span data-ttu-id="6e19a-230">結果は self.nodes 配列に割り当てられ、linq.js を使用してオブジェクトから階層が構築され、出力が配列 self.hierarchy に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-230">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="6e19a-231">この配列は、HTML にバインドされているオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-231">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="6e19a-232">これは、toggleView() 関数でセルフ オブジェクトを ko.applyBindings() 関数に渡すことにより実行されます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-232">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="6e19a-233">続いて、階層の配列が次の HTML にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-233">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

<span data-ttu-id="6e19a-234">サブサイトのドロップダウン メニューを処理するために`mouseenter` および `mouseexit` のイベント ハンドラーがトップレベルのナビゲーションに追加されます。これは、`addEventsToElements()` 関数で実行されます。 </span><span class="sxs-lookup"><span data-stu-id="6e19a-234">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="6e19a-235">この複雑なナビゲーションの例では、ローカル キャッシュがない新しいページの読み込みにおいて、管理ナビゲーションのアプローチと似た結果を得るため、サーバーで費やした時間がベンチマークの構造ナビゲーションから短縮されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="6e19a-235">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="6e19a-236">JavaScript ファイルについて</span><span class="sxs-lookup"><span data-stu-id="6e19a-236">About the JavaScript file...</span></span>

>[!NOTE]
><span data-ttu-id="6e19a-237">カスタム JavaScript を使用する場合は、パブリック CDN が有効であり、ファイルが CDN の場所にあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6e19a-237">If using custom JavaScript, ensure that public CDN is enabled and the file is in a CDN location.</span></span>

<span data-ttu-id="6e19a-238">JavaScript ファイルの全体は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-238">The entire JavaScript file is as follows:</span></span>

```javascript
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

    // ByHierarchy method breaks the sorting in chrome and firefox
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

<span data-ttu-id="6e19a-239">上記の `jQuery $(document).ready` 関数のコードの概要を説明するために `viewModel object` が作成され、次にそのオブジェクトに対する `loadNavigationNodes()` 関数が呼び出されています。</span><span class="sxs-lookup"><span data-stu-id="6e19a-239">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="6e19a-240">この関数は、クライアント ブラウザーの HTML5 ローカル ストレージに格納されている以前に作成されたナビゲーション階層を読み込むか、`queryRemoteInterface()` 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-240">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="6e19a-241">`QueryRemoteInterface()` は、スクリプトの前の方で定義されているクエリ パラメーターを使用する `getRequest()` 関数を使用して要求を作成し、次にサーバーからのデータを返します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-241">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="6e19a-242">このデータは基本的に、さまざまなプロパティを持つデータ転送オブジェクトとして表されるサイト コレクション内のすべてのサイトの配列です。</span><span class="sxs-lookup"><span data-stu-id="6e19a-242">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span>

<span data-ttu-id="6e19a-243">その後、このデータは、解析されて既に定義されている `SPO.Models.NavigationNode` オブジェクトになります。このオブジェクトは、`Knockout.js` を使用して観測可能なプロパティを作成します。このプロパティは、上で定義した HTML に値をバインディングするデータによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-243">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span>

<span data-ttu-id="6e19a-244">オブジェクトは結果の配列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-244">The objects are then put into a results array.</span></span> <span data-ttu-id="6e19a-245">この配列は、Knockout によって解析されて JSON になり、将来ページを読み込む際のパフォーマンス向上のため、ローカル ブラウザー ストレージに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6e19a-245">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="6e19a-246">このアプローチの利点</span><span class="sxs-lookup"><span data-stu-id="6e19a-246">Benefits of this approach</span></span>

<span data-ttu-id="6e19a-247">[このアプローチ](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)の主な利点の 1 つは、ナビゲーションが、HTML5 のローカルの記憶域を使用して、ユーザーによる次回のページの読み込みのため、ローカルに格納されることです。</span><span class="sxs-lookup"><span data-stu-id="6e19a-247">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="6e19a-248">構造ナビゲーション用に検索 API を使用することで、パフォーマンスが大きく向上します。ただし、この機能の実行とカスタマイズには技術的な能力が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-248">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span>

<span data-ttu-id="6e19a-249">[実装の例](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)では、サイトは既成の構造ナビゲーションと同じ順序 (アルファベット順) に並べられています。</span><span class="sxs-lookup"><span data-stu-id="6e19a-249">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="6e19a-250">これとは異なる順序を使用する場合は、開発とメンテナンスがより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-250">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="6e19a-251">また、このアプローチでは、サポートされているマスター ページから逸脱する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-251">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="6e19a-252">カスタム マスター ページの管理が行われない場合、サイトは Microsoft がマスター ページに対して加える更新と改善を利用できません。</span><span class="sxs-lookup"><span data-stu-id="6e19a-252">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="6e19a-253">[上記のコード](#about-the-javascript-file)には次のような依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-253">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="6e19a-254">jQuery - https://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="6e19a-254">jQuery - https://jquery.com/</span></span>
- <span data-ttu-id="6e19a-255">KnockoutJS - https://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="6e19a-255">KnockoutJS - https://knockoutjs.com/</span></span>
- <span data-ttu-id="6e19a-256">Linq.js - https://linqjs.codeplex.com/、または github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="6e19a-256">Linq.js - https://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="6e19a-257">LinqJS の現在のバージョンには、上記のコードで使用されている ByHierarchy メソッドが含まれておらず、ナビゲーション コードが機能しなくなります。</span><span class="sxs-lookup"><span data-stu-id="6e19a-257">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="6e19a-258">これを解決するには、Linq.js ファイルの `Flatten: function ()` の行の前に次のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="6e19a-258">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```javascript
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
  
## <a name="related-topics"></a><span data-ttu-id="6e19a-259">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e19a-259">Related topics</span></span>

[<span data-ttu-id="6e19a-260">SharePoint Server の管理ナビゲーションの概要</span><span class="sxs-lookup"><span data-stu-id="6e19a-260">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

[<span data-ttu-id="6e19a-261">構造ナビゲーションのキャッシュとパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="6e19a-261">Structural navigation caching and performance</span></span>](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)
