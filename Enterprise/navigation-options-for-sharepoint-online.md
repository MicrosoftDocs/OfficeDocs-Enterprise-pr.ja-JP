---
title: SharePoint Online のナビゲーション オプション
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: この資料では、クラシックの発行の管理または検索によるナビゲーションを使用して SharePoint Online のページの読み込み時間を改善する方法について説明します。
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541780"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="763e5-103">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="763e5-103">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="763e5-104">この資料では、クラシックの発行の管理または検索によるナビゲーションを使用して SharePoint Online のページの読み込み時間を改善する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="763e5-104">This article describes how to improve page load times for SharePoint Online by using managed navigation or search-driven navigation in Classic publishing.</span></span>
  
<span data-ttu-id="763e5-105">SharePoint Online クラシックの発行を有効になっているが 2 つのナビゲーション領域です。グローバル ナビゲーションと現在のナビゲーションです。</span><span class="sxs-lookup"><span data-stu-id="763e5-105">SharePoint Online with classic publishing enabled has two navigation areas; Global Navigation and Current Navigation.</span></span>
  
<span data-ttu-id="763e5-106">グローバル ナビゲーションは、現在のナビゲーションは、側またはコンテキストで左/右のナビゲーション言語の構成と使用するマスター ページに依存しているときに上部のナビゲーション メニューです。</span><span class="sxs-lookup"><span data-stu-id="763e5-106">Global navigation is the top navigation menu while Current Navigation is the side or in-context left/right navigation dependent on the language configuration and master page utilized.</span></span>
  
<span data-ttu-id="763e5-107">ナビゲーションできますパフォーマンスに悪影響全体のポータルのポータル全体での使用の構成は、多くの場合、任意の SharePoint サイトの重要な要素のようです。</span><span class="sxs-lookup"><span data-stu-id="763e5-107">Navigation can negatively impact performance for the entire Portal as it is often configured for portal-wide use and as such is an important element of any SharePoint site.</span></span>
  
<span data-ttu-id="763e5-108">構造のナビゲーションは、セキュリティ トリミングを使用する、設置型トポロジー向けに設計されて、このデザインはサーバーに過度な呼び出しが発生し、使用時のパフォーマンスに影響、SharePoint Online のナビゲーションの推奨されるオプションではありません。</span><span class="sxs-lookup"><span data-stu-id="763e5-108">Structural navigation is not the recommended navigation option in SharePoint Online as it was designed for an On-premise topology with security trimming and this design causes excessive server calls and impacts performance when it is used.</span></span>
  
<span data-ttu-id="763e5-p101">簡素化された統合されたサイト階層を持つ、現代モダンの SharePoint サイトの導入によりデザインが変更されています。ナビゲーションに関連するパフォーマンスの問題を解消するには、簡略化された階層を使用したナビゲーションを簡素化しました。</span><span class="sxs-lookup"><span data-stu-id="763e5-p101">That design has changed with the introduction of Modern SharePoint sites where Modern has a simplified flattened site hierarchy. This has simplified navigation with a simplified hierarchy that has eliminated performance issues related to navigation.</span></span>
  
<span data-ttu-id="763e5-p102">SharePoint と同様に 3 分の 1、カスタムの検索ベースのアプローチの 2 つのメイン ・ ボックスのナビゲーション オプションがあります。または、4 つ目と非常によく使用されるオプションは、カスタム ナビゲーション プロバイダーを作成します。このガイドには、カスタム ナビゲーション プロバイダーの[オンラインの SharePoint ポータルのナビゲーション ソリューション](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="763e5-p102">There are two main out-of-the-box navigation options in SharePoint as well as a third, custom, search-driven approach. Alternatively, a fourth and fairly popular option is to build a Custom Navigation Provider. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) for guidance on a Custom navigation provider.</span></span> 
  
<span data-ttu-id="763e5-114">各オプションには長所と短所を次の表で説明されています。</span><span class="sxs-lookup"><span data-stu-id="763e5-114">Each option has pros and cons as outlined in the following table.</span></span>
  
|<span data-ttu-id="763e5-115">**構造ナビゲーション**</span><span class="sxs-lookup"><span data-stu-id="763e5-115">**Structural navigation**</span></span>|<span data-ttu-id="763e5-116">**管理ナビゲーション**</span><span class="sxs-lookup"><span data-stu-id="763e5-116">**Managed navigation**</span></span>|<span data-ttu-id="763e5-117">**検索方式のナビゲーション**</span><span class="sxs-lookup"><span data-stu-id="763e5-117">**Search-driven navigation**</span></span>||<span data-ttu-id="763e5-118">**カスタム ナビゲーション プロバイダー**</span><span class="sxs-lookup"><span data-stu-id="763e5-118">**Custom Navigation Provider**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
| <span data-ttu-id="763e5-119">長所:</span><span class="sxs-lookup"><span data-stu-id="763e5-119">Pros:</span></span>  <br/>  <span data-ttu-id="763e5-120">構成しやすい</span><span class="sxs-lookup"><span data-stu-id="763e5-120">Easy to configure</span></span>  <br/>  <span data-ttu-id="763e5-121">セキュリティ トリミングされている</span><span class="sxs-lookup"><span data-stu-id="763e5-121">Security-trimmed</span></span>  <br/>  <span data-ttu-id="763e5-122">サイトが追加されると自動的に更新する</span><span class="sxs-lookup"><span data-stu-id="763e5-122">Automatically updates as sites are added</span></span>  <br/> | <span data-ttu-id="763e5-123">長所:</span><span class="sxs-lookup"><span data-stu-id="763e5-123">Pros:</span></span>  <br/>  <span data-ttu-id="763e5-124">メンテナンスしやすい</span><span class="sxs-lookup"><span data-stu-id="763e5-124">Easy to maintain</span></span>  <br/>  <span data-ttu-id="763e5-125">推奨オプション</span><span class="sxs-lookup"><span data-stu-id="763e5-125">Recommended option</span></span>  <br/> | <span data-ttu-id="763e5-126">長所:</span><span class="sxs-lookup"><span data-stu-id="763e5-126">Pros:</span></span>  <br/>  <span data-ttu-id="763e5-127">セキュリティ トリミングされている</span><span class="sxs-lookup"><span data-stu-id="763e5-127">Security-trimmed</span></span>  <br/>  <span data-ttu-id="763e5-128">サイトが追加されると自動的に更新する</span><span class="sxs-lookup"><span data-stu-id="763e5-128">Automatically updates as sites are added</span></span>  <br/>  <span data-ttu-id="763e5-129">読み込み時間が短く、ナビゲーション構造がローカルにキャッシュされている</span><span class="sxs-lookup"><span data-stu-id="763e5-129">Fast loading time and locally cached navigation structure</span></span>  <br/> || <span data-ttu-id="763e5-130">長所:</span><span class="sxs-lookup"><span data-stu-id="763e5-130">Pros:</span></span>  <br/>    <br/>  <span data-ttu-id="763e5-131">選択の幅オプションを利用可能と</span><span class="sxs-lookup"><span data-stu-id="763e5-131">Wider choice / options available</span></span>  <br/>  <span data-ttu-id="763e5-132">正しく使用されてキャッシュする場合の高速読み込み</span><span class="sxs-lookup"><span data-stu-id="763e5-132">Fast loading when caching is used correctly</span></span>  <br/> |
| <span data-ttu-id="763e5-133">短所:</span><span class="sxs-lookup"><span data-stu-id="763e5-133">Cons:</span></span>  <br/> <span data-ttu-id="763e5-134">**非推奨**</span><span class="sxs-lookup"><span data-stu-id="763e5-134">**Not recommended**</span></span> <br/> <span data-ttu-id="763e5-135">**パフォーマンスに与える影響**</span><span class="sxs-lookup"><span data-stu-id="763e5-135">**Impacts performance**</span></span> <br/> | <span data-ttu-id="763e5-136">短所:</span><span class="sxs-lookup"><span data-stu-id="763e5-136">Cons:</span></span>  <br/>  <span data-ttu-id="763e5-137">サイト構造を反映するように自動的に更新されない</span><span class="sxs-lookup"><span data-stu-id="763e5-137">Not automatically updated to reflect site structure</span></span>  <br/>  <span data-ttu-id="763e5-138">セキュリティ トリミングが有効になっている場合は、パフォーマンスに与える影響</span><span class="sxs-lookup"><span data-stu-id="763e5-138">Impacts performance if security trimming is enabled</span></span>  <br/> | <span data-ttu-id="763e5-139">短所:</span><span class="sxs-lookup"><span data-stu-id="763e5-139">Cons:</span></span>  <br/>  <span data-ttu-id="763e5-140">サイトを簡単に並べ替えられない</span><span class="sxs-lookup"><span data-stu-id="763e5-140">No ability to easily order sites</span></span>  <br/>  <span data-ttu-id="763e5-141">マスター ページのカスタマイズが必要 (技術的なスキルが必要)</span><span class="sxs-lookup"><span data-stu-id="763e5-141">Requires customization of the master page (technical skills required)</span></span>  <br/> || <span data-ttu-id="763e5-142">短所:</span><span class="sxs-lookup"><span data-stu-id="763e5-142">Cons:</span></span>  <br/>  <span data-ttu-id="763e5-143">カスタム開発が必要</span><span class="sxs-lookup"><span data-stu-id="763e5-143">Custom development is required</span></span>  <br/>  <span data-ttu-id="763e5-144">外部データ ソース キャッシュの保存が必要なと Azure など</span><span class="sxs-lookup"><span data-stu-id="763e5-144">External data source / cache stored is needed e.g. Azure</span></span>  <br/> |
   
<span data-ttu-id="763e5-p103">サイトの最適なオプションと技術的な機能をサイトの要件に依存します。カスタム マスター ページを使用して快適なしている SharePoint Online の既定のマスター ページで発生する変更内容を維持するために組織の一部の機能がある場合、[検索ベース] オプションの間で最高のユーザー エクスペリエンスが生成されます。ボックスの構造的なナビゲーションと検索の間の単純な妥協点を設定する場合、管理対象のナビゲーションは非常に良いオプションです。管理ナビゲーションのオプションを維持できる構成では、コードのカスタマイズ ファイルは関与しませんし、ボックスの構造上のナビゲーションよりも大幅に高速ですが。</span><span class="sxs-lookup"><span data-stu-id="763e5-p103">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the search-driven option will produce the best user experience. If you want a simple middle ground between the out-of-the-box structural navigation and search, then the managed navigation is a very good option. The managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than the out-of-the-box structural navigation.</span></span>
  
<span data-ttu-id="763e5-p104">現代と同様に、従来のポータルの全体的な構造の簡素化は、全体のパフォーマンスと拡張性にも同様のことができます。内容には、何百もの単一のサイト コレクションではなく/何千ものサイト (サブ)、適切なアプローチは、非常にいくつかサブサイト (サブ web) の多くのサイト コレクションです。</span><span class="sxs-lookup"><span data-stu-id="763e5-p104">Simplifying the overall structure of your Classic Portal much like Modern, helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds / thousands of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>
  
<span data-ttu-id="763e5-151">すべてのコンテンツを 1 つの巨大なデータベースに配置することを避けることができます、およびナビゲーションおよびさらに重要なセキュリティの柔軟性により、最終的にこのサービスの他の拡大・縮小オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="763e5-151">This provides additional scaling options in the service, avoids putting all content into one big database and ultimately allows greater flexibility for navigation and more importantly security.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="763e5-152">SharePoint Online で構造ナビゲーションを使用する</span><span class="sxs-lookup"><span data-stu-id="763e5-152">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="763e5-p105">これは、既定で使用される、標準のナビゲーションと最も簡単なソリューションが、コスト パフォーマンスのトレードオフが。カスタマイズする必要がないと非技術的なユーザーことができますも簡単に項目を追加、アイテムを非表示しナビゲーションの設定] ページから管理します。管理のナビゲーションもできるとナビゲーションの管理を使用することを推奨するような場合は true がただしも容易にするこれは、管理し、同様に制御します。</span><span class="sxs-lookup"><span data-stu-id="763e5-p105">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well.</span></span>
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="763e5-156">SharePoint Online で構造ナビゲーションを有効にする</span><span class="sxs-lookup"><span data-stu-id="763e5-156">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="763e5-p106">構造のナビゲーションと表示する場合は、標準的な SharePoint Online ソリューションのパフォーマンスでのオプションのサブサイトを説明するために有効にします。次の例を [**サイトの設定**] ページの設定\>**ナビゲーション**します。</span><span class="sxs-lookup"><span data-stu-id="763e5-p106">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screen shot settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![サブサイトが表示されているスクリーンショット](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="763e5-160">SharePoint Online で構造ナビゲーションのパフォーマンスを分析する</span><span class="sxs-lookup"><span data-stu-id="763e5-160">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="763e5-161">SharePoint のページのパフォーマンスを分析するには、Internet Explorer の F12 開発者ツールの **[ネットワーク]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="763e5-161">To analyze the performance of a SharePoint page use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![F12 開発者ツールの [ネットワーク] タブが表示されているスクリーンショット](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
<span data-ttu-id="763e5-163">**[ネットワーク]** タブで、読み込まれている .aspx ページ、**[詳細]** タブの順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="763e5-163">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span> 
  
![[詳細] タブが表示されているスクリーンショット](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
<span data-ttu-id="763e5-165">**[応答ヘッダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="763e5-165">Click **Response headers**.</span></span>
  
![[詳細] タブのスクリーンショット](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
<span data-ttu-id="763e5-p107">SharePoint は、その応答ヘッダー内で、有益な診断情報を返します。最も便利な診断情報の 1 つは **SPRequestDuration** です。これは、サーバー上で要求の処理にかかった時間の値 (ミリ秒単位) です。</span><span class="sxs-lookup"><span data-stu-id="763e5-p107">SharePoint returns some useful diagnostic information in its response headers. One of the most useful is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> 
  
<span data-ttu-id="763e5-p108">次のスクリーン ショットの**サブサイトを表示するの**には構造のナビゲーションを確認です。これは、グローバル ナビゲーションにサイト コレクションのリンクがあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="763e5-p108">In the following screen shot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span> 
  
![要求時間として負荷時間が表示されているスクリーンショット](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
<span data-ttu-id="763e5-p109">**SPRequestDuration**キーには、245 のミリ秒単位の値があります。これは、要求を取得するにかかった時間を表します。サイトのナビゲーション アイテムを 1 つだけなので、これは、SharePoint Online を実行する方法なく大量のナビゲーションのための良いベンチマークです。次のスクリーン ショットでは、サブサイトに追加すると、このキーにどのように影響する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="763e5-p109">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span> 
  
![2,502 ミリ秒の要求時間が表示されているスクリーンショット](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
<span data-ttu-id="763e5-177">サブサイトの追加により、ページ要求に返答するまでにかかる時間が大きく増加しました。</span><span class="sxs-lookup"><span data-stu-id="763e5-177">Adding the subsites has significantly increased the time it takes to return the page request.</span></span>
  
<span data-ttu-id="763e5-178">標準の構造化ナビゲーションを使用する利点は、することができます簡単に順番を整理する、サイトを非表示、ページを追加、セキュリティ トリミングされた結果は、SharePoint Online でサポートされているマスター ページから逸脱していないです。</span><span class="sxs-lookup"><span data-stu-id="763e5-178">The advantages of using the regular structured navigation is that you can easily organize the order, hide sites, add pages, the results are security-trimmed, and you are not deviating from the supported master pages used in SharePoint Online.</span></span>
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a><span data-ttu-id="763e5-179">SharePoint Online で管理ナビゲーションと管理されたメタデータを使用する</span><span class="sxs-lookup"><span data-stu-id="763e5-179">Using managed navigation and managed metadata in SharePoint Online</span></span>

<span data-ttu-id="763e5-180">管理ナビゲーションは、構造ナビゲーションと同じ種類の機能を再作成するために使用できる別のそのまま使用できるオプションです。</span><span class="sxs-lookup"><span data-stu-id="763e5-180">Managed navigation is another out-of-the-box option that you can use to recreate the same sort of functionality as structural navigation.</span></span>
  
<span data-ttu-id="763e5-p110">マネージ メタデータを使用する利点は、サイトのナビゲーションを作成するクエリでのコンテンツを使用するよりもデータを取得するためにはるかに高速であります。高速にはセキュリティをトリムするための方法、結果が、ユーザーでは、特定のサイトにアクセスがない場合リンクは表示されますが、エラー メッセージに 。</span><span class="sxs-lookup"><span data-stu-id="763e5-p110">The advantage of using managed metadata is that it is much faster to retrieve the data than using content by query to build the site navigation. Although it is much faster there is no way to security trim the results so if a user doesn't have access to a given site, the link will still show but will lead to an error message.</span></span>
  
 <span data-ttu-id="763e5-183">**管理ナビゲーションと結果を実装する方法**</span><span class="sxs-lookup"><span data-stu-id="763e5-183">**How to implement managed navigation and the results**</span></span>
  
<span data-ttu-id="763e5-184">上にある記事がいくつか TechNet 管理ナビゲーションの詳細については、 [SharePoint Server 2013 でのナビゲーションの管理の概要](https://go.microsoft.com/fwlink/?LinkId=708689)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="763e5-184">There are several articles on TechNet about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span></span>
  
<span data-ttu-id="763e5-p111">管理ナビゲーションを実装するためには、用語ストア管理者のアクセス許可が必要です。サイト コレクションの構造と一致する URL 付き用語を設定すると、管理ナビゲーションを使用して構造ナビゲーションと置き換えることができます。例:</span><span class="sxs-lookup"><span data-stu-id="763e5-p111">In order to implement managed navigation, you need to have term store administrator permissions. By setting up terms with URLs that match the structure of a site collection, managed navigation can be used to replace structural navigation. For example:</span></span>
  
![Subsite1 の例のスクリーンショット](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
<span data-ttu-id="763e5-189">次の例は、管理ナビゲーションを使用した複雑なナビゲーションのパフォーマンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="763e5-189">The following example shows the performance of the complex navigation using managed navigation.</span></span>
  
![SPRequestDuration の例のスクリーンショット](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
<span data-ttu-id="763e5-191">常に管理ナビゲーションを使用すると、クエリによるコンテンツの構造ナビゲーションのアプローチと比較してパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="763e5-191">Using managed navigation consistently improves performance compared to the content by query structural navigation approach.</span></span>
  
## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="763e5-192">検索駆動のクライアント側スクリプトを使用する</span><span class="sxs-lookup"><span data-stu-id="763e5-192">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="763e5-p112">検索を使用すると、継続的クロールによってバックグラウンドでビルドされたインデックスを活用できます。つまり、負荷の高いコンテンツのクエリはありません。検索結果が検索インデックスから取り込まれ、結果はセキュリティ トリミングされます。通常のコンテンツのクエリを使用するよりも高速です。構造のナビゲーション用の検索を使用すると、特に複雑なサイト構造がある場合は、ページの読み込み時間が大幅に短縮します。この管理ナビゲーションの主な利点は、セキュリティ トリミングの恩恵を受けられることです。</span><span class="sxs-lookup"><span data-stu-id="763e5-p112">Using search you can leverage the indexes that are built up in the background using continuous crawl. This means there are no heavy content queries. The search results are pulled from the search index and the results are security-trimmed. This is faster than using regular content queries. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>
  
<span data-ttu-id="763e5-p113">このアプローチには、カスタム マスター ページの作成、そのまま使用できるナビゲーションのコードのカスタム HTML への置き換えなどが含まれます。ファイル seattle.html のナビゲーション コードを置き換えるには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="763e5-p113">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure to replace the navigation code in the file seattle.html.</span></span>
  
<span data-ttu-id="763e5-201">次の使用例では、seattle.html ファイルを開くし、全体の要素を置き換える**id ="DeltaTopNavigation"** カスタム HTML コードとします。</span><span class="sxs-lookup"><span data-stu-id="763e5-201">In this example, you will open the seattle.html file and replace the whole element **id="DeltaTopNavigation"** with the custom HTML code.</span></span> 
  
 <span data-ttu-id="763e5-202">**例: マスター ページでそのまま使用できるナビゲーションのコードを置き換えるには**</span><span class="sxs-lookup"><span data-stu-id="763e5-202">**Example: To replace the out-of-the-box navigation code in a master page**</span></span>
  
1. <span data-ttu-id="763e5-203">**[サイト設定]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="763e5-203">Navigate to the **Site Settings** page.</span></span> 
    
2. <span data-ttu-id="763e5-204">**[マスター ページ]** をクリックして、マスター ページ ギャラリーを開きます。</span><span class="sxs-lookup"><span data-stu-id="763e5-204">Open the master page gallery by clicking **Master Pages**.</span></span>
    
3. <span data-ttu-id="763e5-205">ここから、ライブラリ内を移動してファイル **seattle.master** をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="763e5-205">From here you can navigate through the library and download the file **seattle.master**.</span></span>
    
4. <span data-ttu-id="763e5-206">テキスト エディターでコードを編集し、次のスクリーン ショットにあるコード ブロックを削除します。</span><span class="sxs-lookup"><span data-stu-id="763e5-206">Edit the code using a text editor and delete the code block in the following screen shot.</span></span>
    
    ![削除する DeltaTopNavigation コードのスクリーンショット](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. <span data-ttu-id="763e5-208">間のコードを削除する、 \<SharePoint:AjaxDelta id ="DeltaTopNavigation"\>と\<\SharePoint:AjaxDelta\>タグし、次のスニペットに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="763e5-208">Remove the code between the \<SharePoint:AjaxDelta id="DeltaTopNavigation"\> and \<\SharePoint:AjaxDelta\> tags and replace it with the following snippet:</span></span>
    
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

6. <span data-ttu-id="763e5-p114">読み込まれる URL を交換してイメージを読み込み、サイト コレクションのイメージへのリンクで、最初にアンカー タグです。変更を行った後は、ファイルの名前を変更し、マスター ページ ギャラリーにアップロードしています。新しい .master ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="763e5-p114">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span>
    
7. <span data-ttu-id="763e5-p115">この HTML は、JavaScript コードから返された検索結果が表示されますが、基本的なマークアップです。値を変更するのには次のコードを編集する必要がありますが、 `var root = "site collection URL"` 、次のスニペットで示すように。</span><span class="sxs-lookup"><span data-stu-id="763e5-p115">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the following code to change the value for the  `var root = "site collection URL"` as demonstrated in the following snippet:</span></span> 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

    <span data-ttu-id="763e5-214">JavaScript ファイル全体は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="763e5-214">The entire JavaScript file is as follows:</span></span>
    
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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     <span data-ttu-id="763e5-215">$("li.level1").mouseover (関数 () {</span><span class="sxs-lookup"><span data-stu-id="763e5-215">$("li.level1").mouseover(function () {</span></span> 
  
<span data-ttu-id="763e5-216">var 位置 = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="763e5-216">var position = $(this).position();</span></span>
  
<span data-ttu-id="763e5-217">(この) $.find("ul.level2").css ({幅: 100、左: 上の position.left + 10: 50})。</span><span class="sxs-lookup"><span data-stu-id="763e5-217">$(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });</span></span>
    
     }) 
  
<span data-ttu-id="763e5-218">.mouseout (関数 () {</span><span class="sxs-lookup"><span data-stu-id="763e5-218">.mouseout(function () {</span></span>
  
<span data-ttu-id="763e5-219">(この) $.find("ul.level2").css ({左:-99999、上部: 0})。</span><span class="sxs-lookup"><span data-stu-id="763e5-219">$(this).find("ul.level2").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="763e5-220">});</span><span class="sxs-lookup"><span data-stu-id="763e5-220"></span></span>
  
<span data-ttu-id="763e5-221">$("li.level2").mouseover (関数 () {</span><span class="sxs-lookup"><span data-stu-id="763e5-221">$("li.level2").mouseover(function () {</span></span>
  
<span data-ttu-id="763e5-222">var 位置 = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="763e5-222">var position = $(this).position();</span></span>
  
<span data-ttu-id="763e5-223">console.log(JSON.stringify(position)) です。</span><span class="sxs-lookup"><span data-stu-id="763e5-223">console.log(JSON.stringify(position));</span></span>
  
<span data-ttu-id="763e5-224">(この) $.find("ul.level3").css ({幅: 100、左: position.left + 95 の場合、トップ: position.top})。</span><span class="sxs-lookup"><span data-stu-id="763e5-224">$(this).find("ul.level3").css({ width: 100, left: position.left + 95, top: position.top});</span></span>
    
     }) 
  
<span data-ttu-id="763e5-225">.mouseout (関数 () {</span><span class="sxs-lookup"><span data-stu-id="763e5-225">.mouseout(function () {</span></span>
  
<span data-ttu-id="763e5-226">(この) $.find("ul.level3").css ({左:-99999、上部: 0})。</span><span class="sxs-lookup"><span data-stu-id="763e5-226">$(this).find("ul.level3").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="763e5-227">});</span><span class="sxs-lookup"><span data-stu-id="763e5-227"></span></span>
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. <span data-ttu-id="763e5-p116">次に、結果は、 **[self.nodes]** の配列に割り当てられているし、linq.js は配列の **[self.heirarchy]** への出力の割り当てを使用してオブジェクト階層を構築します。この配列は、HTML にバインドされているオブジェクトです。Self オブジェクトを **[ko.applyBinding()]** 関数に渡すことによって **[toggleView()]** 関数の中でこれです。これは、し、次の HTML にバインドするのには階層構造の配列を発生します。</span><span class="sxs-lookup"><span data-stu-id="763e5-p116">Next, the results are assigned to the **[self.nodes]** array and a hierarchy is built out of the objects using linq.js assigning the output to an array **[self.heirarchy]**. This array is the object that is bound to the HTML. This is done in the **[toggleView()]** function by passing the self object to the **[ko.applyBinding()]** function. This then causes the hierarchy array to be bound to the following HTML:</span></span> 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    <span data-ttu-id="763e5-232">最後に、 **[mouseenter]** と **[mouseexit]** のイベント ハンドラーは、 **[addEventsToElements()]** 関数の中でこれはサブサイトのドロップ ダウン メニューを処理するために最上位レベルのナビゲーションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="763e5-232">Finally, the event handlers for **[mouseenter]** and **[mouseexit]** are added to the top-level navigation to handle the subsite drop-down menus which is done in the **[addEventsToElements()]** function.</span></span> 
    
    <span data-ttu-id="763e5-233">ナビゲーションの結果は、以下のスクリーン ショットで確認できます。</span><span class="sxs-lookup"><span data-stu-id="763e5-233">The results of the navigation can be seen in the screen shot below:</span></span>
    
    ![ナビゲーションの結果のスクリーン ショット](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    <span data-ttu-id="763e5-235">この複雑なナビゲーションの例では、ローカル キャッシュがない新しいページの読み込みにおいて、管理ナビゲーションのアプローチと似た結果を得るため、サーバーで費やした時間がベンチマークの構造ナビゲーションから短縮されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="763e5-235">In our complex navigation example a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>
    
    ![SPRequestDuration 301 のスクリーンショット](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    <span data-ttu-id="763e5-237">このアプローチの主な利点の 1 つは、ナビゲーションが、HTML5 のローカルの記憶域を使用して、ユーザーによる次回のページの読み込みのため、ローカルに格納されることです。</span><span class="sxs-lookup"><span data-stu-id="763e5-237">One major benefit of this approach is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span>
    
<span data-ttu-id="763e5-p117">構造ナビゲーション用に検索 API を使用することで、パフォーマンスが大きく向上します。ただし、この機能の実行とカスタマイズには技術的な能力が必要になります。実装の例では、サイトはそのまま使用できる構造ナビゲーションと同じ順序 (アルファベット順) に並べられています。この順序から逸脱する場合は、開発とメンテナンスがより複雑になります。また、このアプローチでは、サポートされているマスター ページから逸脱する必要があります。カスタム マスター ページをメンテナンスしないと、サイトは Microsoft がマスター ページに対して加える更新と改善を逃してしまいます。</span><span class="sxs-lookup"><span data-stu-id="763e5-p117">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality. In the example implementation, the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>
  
<span data-ttu-id="763e5-243">上記のコードには、次の依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="763e5-243">The above code has the following dependencies:</span></span>
  
- <span data-ttu-id="763e5-244">jQuery[http://jquery.com/](http://jquery.com/)</span><span class="sxs-lookup"><span data-stu-id="763e5-244">jQuery - [http://jquery.com/](http://jquery.com/)</span></span>
    
- <span data-ttu-id="763e5-245">KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)</span><span class="sxs-lookup"><span data-stu-id="763e5-245">KnockoutJS - [http://knockoutjs.com/](http://knockoutjs.com/)</span></span>
    
- <span data-ttu-id="763e5-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/)、または[github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span><span class="sxs-lookup"><span data-stu-id="763e5-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), or [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span></span>
    
<span data-ttu-id="763e5-p118">LinqJS の現在のバージョンでは、上記のコードで使用されている ByHierarchy メソッドが含まれていないと、ナビゲーション コードが破損します。この問題を解決するには、行の前に Linq.js ファイルに次のメソッドを追加」平展開: () の機能」です。</span><span class="sxs-lookup"><span data-stu-id="763e5-p118">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line "Flatten: function ()".</span></span>
  
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


