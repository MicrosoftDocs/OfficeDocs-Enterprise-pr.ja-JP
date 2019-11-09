---
title: SharePoint Online のパフォーマンスを向上させるために、コンテンツのクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: この記事では、コンテンツクエリ Web パーツを SharePoint Server 2013 および SharePoint Online のコンテンツ検索 Web パーツに置き換えることによって、パフォーマンスを向上させる方法について説明します。
ms.openlocfilehash: e2a3a1dd5a0010fcf1bbf61a039ca1d23292f70d
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077946"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="789c0-103">SharePoint Online のパフォーマンスを向上させるために、コンテンツのクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用する</span><span class="sxs-lookup"><span data-stu-id="789c0-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="789c0-104">この記事では、コンテンツクエリ Web パーツを SharePoint Server 2013 および SharePoint Online のコンテンツ検索 Web パーツに置き換えることによって、パフォーマンスを向上させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="789c0-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="789c0-105">SharePoint Server 2013 と SharePoint Online の最も強力な新機能の1つは、コンテンツ検索 Web パーツ (CSWP) です。</span><span class="sxs-lookup"><span data-stu-id="789c0-105">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP).</span></span> <span data-ttu-id="789c0-106">この Web パーツは、検索インデックスを使用して、ユーザーに表示される結果をすばやく取得します。</span><span class="sxs-lookup"><span data-stu-id="789c0-106">This Web Part uses the search index to quickly retrieve results which are shown to the user.</span></span> <span data-ttu-id="789c0-107">ページのコンテンツクエリ Web パーツ (CQWP) の代わりにコンテンツ検索 Web パーツを使用して、ユーザーのパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="789c0-107">Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="789c0-108">コンテンツクエリ Web パーツを使用してコンテンツ検索 Web パーツを使用すると、ほとんどの場合、SharePoint Online でのページ読み込みのパフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="789c0-108">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online.</span></span> <span data-ttu-id="789c0-109">適切なクエリを取得するには、さらに多くの構成がありますが、報奨はパフォーマンスが向上し、ユーザーの満足度が向上します。</span><span class="sxs-lookup"><span data-stu-id="789c0-109">There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="789c0-110">コンテンツクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用して得られるパフォーマンスの向上を比較する</span><span class="sxs-lookup"><span data-stu-id="789c0-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="789c0-111">次の例では、コンテンツクエリ Web パーツの代わりにコンテンツ検索 Web パーツを使用するときに表示される可能性があるパフォーマンスの向上を示します。</span><span class="sxs-lookup"><span data-stu-id="789c0-111">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part.</span></span> <span data-ttu-id="789c0-112">この効果は、複雑なサイト構造と非常に広範なコンテンツのクエリによって明確になります。</span><span class="sxs-lookup"><span data-stu-id="789c0-112">The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="789c0-113">この例のサイトには、次のような特徴があります。</span><span class="sxs-lookup"><span data-stu-id="789c0-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="789c0-114">サブサイトの8つのレベル。</span><span class="sxs-lookup"><span data-stu-id="789c0-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="789c0-115">カスタムの "フルーツ" コンテンツタイプを使用してリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="789c0-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="789c0-116">Web パーツでは、コンテンツクエリは広範で、コンテンツタイプが "フルーツ" のすべてのアイテムを返します。</span><span class="sxs-lookup"><span data-stu-id="789c0-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="789c0-117">この例では、8つのサイト全体で50アイテムのみを使用します。</span><span class="sxs-lookup"><span data-stu-id="789c0-117">The example only uses 50 items across the 8 sites.</span></span> <span data-ttu-id="789c0-118">この効果は、より多くのコンテンツがあるサイトに対してさらに顕著になります。</span><span class="sxs-lookup"><span data-stu-id="789c0-118">The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="789c0-119">ここでは、コンテンツクエリ Web パーツの結果のスクリーンショットを示します。</span><span class="sxs-lookup"><span data-stu-id="789c0-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Web パーツのクエリ結果を示すグラフィック](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="789c0-121">Internet Explorer で、F12 開発者ツールの [**ネットワーク**] タブを使用して、応答ヘッダーの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="789c0-121">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header.</span></span> <span data-ttu-id="789c0-122">次のスクリーンショットでは、このページ読み込みの**Sprequestduration**の値は924ミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="789c0-122">In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![924 の要求時間が表示されているスクリーンショット](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="789c0-124">**Sprequestduration**は、ページを準備するためにサーバー上で実行された作業量を示します。</span><span class="sxs-lookup"><span data-stu-id="789c0-124">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page.</span></span> <span data-ttu-id="789c0-125">コンテンツを検索する Web パーツを使用してコンテンツをクエリ Web パーツに切り替えることで、ページのレンダリングにかかる時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="789c0-125">Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page.</span></span> <span data-ttu-id="789c0-126">対照的に、このスクリーンショットに示されているように、同じコンテンツ検索 Web パーツを持つページは、同じ数の結果が106ミリ秒の**Sprequestduration**値を返します。</span><span class="sxs-lookup"><span data-stu-id="789c0-126">By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![106 の要求時間が表示されているスクリーンショット](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="789c0-128">SharePoint Online でコンテンツ検索 Web パーツを追加する</span><span class="sxs-lookup"><span data-stu-id="789c0-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="789c0-129">コンテンツ検索 Web パーツの追加は、通常のコンテンツクエリ Web パーツによく似ています。</span><span class="sxs-lookup"><span data-stu-id="789c0-129">Adding a Content Search Web Part is very similar to a regular Content Query Web Part.</span></span> <span data-ttu-id="789c0-130">「 [SharePoint でコンテンツ検索 Web パーツを構成](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)する」の「*コンテンツ検索 Web パーツを追加する」* セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="789c0-130">See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="789c0-131">コンテンツ検索 Web パーツ用の適切な検索クエリを作成する</span><span class="sxs-lookup"><span data-stu-id="789c0-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="789c0-132">コンテンツ検索 Web パーツを追加したら、検索を絞り込み、必要なアイテムを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="789c0-132">Once you have added a Content Search Web Part, you can refine the search and return the items you want.</span></span> <span data-ttu-id="789c0-133">この手順の詳細については、「 [SharePoint でコンテンツ検索 Web パーツを構成](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)する」の「コンテンツ*検索 web パーツの詳細なクエリを構成してコンテンツを表示*する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="789c0-133">For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="789c0-134">クエリ構築およびテストツール</span><span class="sxs-lookup"><span data-stu-id="789c0-134">Query building and testing tool</span></span>

<span data-ttu-id="789c0-135">複雑なクエリを作成およびテストするツールについては、Codeplex の[検索クエリツール](https://sp2013searchtool.codeplex.com/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="789c0-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

