---
title: コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用して SharePoint Online でのパフォーマンスを向上させる
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: この資料では、コンテンツ クエリ Web パーツを SharePoint Server 2013 と SharePoint Online のコンテンツ検索 Web パーツで置き換えることによってパフォーマンスを向上させる方法について説明します。
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541831"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="6afbe-103">コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用して SharePoint Online でのパフォーマンスを向上させる</span><span class="sxs-lookup"><span data-stu-id="6afbe-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="6afbe-104">この資料では、コンテンツ クエリ Web パーツを SharePoint Server 2013 と SharePoint Online のコンテンツ検索 Web パーツで置き換えることによってパフォーマンスを向上させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6afbe-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="6afbe-p101">SharePoint Server 2013 と SharePoint Online の最も強力な新機能の 1 つは、コンテンツ検索 Web パーツ (CSWP) です。この Web パーツは、ユーザーに示されている結果を迅速に取得するのには、検索インデックスを使用します。ユーザーのパフォーマンスを向上させるためにではなく、コンテンツ クエリ Web パーツ (CQWP)、ページのコンテンツ検索 Web パーツを使用します。</span><span class="sxs-lookup"><span data-stu-id="6afbe-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="6afbe-p102">コンテンツ クエリ Web パーツにコンテンツ検索 Web パーツを使用するほとんどの場合、SharePoint Online のページ読み込みのパフォーマンスを大幅に向上されます。右のクエリを取得するのには少し追加の構成がありますが、パフォーマンスを向上させるとすれば、ユーザーは。</span><span class="sxs-lookup"><span data-stu-id="6afbe-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="6afbe-110">コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用してから取得したパフォーマンスの向上を比較します。</span><span class="sxs-lookup"><span data-stu-id="6afbe-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="6afbe-p103">次の例では、コンテンツ クエリ Web パーツではなくコンテンツ検索 Web パーツを使用すると表示される相対的なパフォーマンス上の利点を示しています。効果は、複雑なサイト構造と非常に広範なコンテンツ クエリではわかりやすい。</span><span class="sxs-lookup"><span data-stu-id="6afbe-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="6afbe-113">この例のサイトには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="6afbe-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="6afbe-114">サブサイトの 8 レベルです。</span><span class="sxs-lookup"><span data-stu-id="6afbe-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="6afbe-115">「フルーツ」のカスタム コンテンツ タイプを使用して一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="6afbe-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="6afbe-116">Web パーツでコンテンツのクエリは全体を見て、「フルーツ」のコンテンツ タイプのすべての項目を返すことです。</span><span class="sxs-lookup"><span data-stu-id="6afbe-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="6afbe-p104">のみ 8 のサイト間で 50 の項目を使用します。効果がもより顕著になるサイトのより多くのコンテンツを持つ。</span><span class="sxs-lookup"><span data-stu-id="6afbe-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="6afbe-119">コンテンツ クエリ Web パーツの結果のスクリーン ショットを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6afbe-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Web パーツのクエリ結果を示すグラフィック](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="6afbe-p105">Internet Explorer では、F12 開発者ツールの [**ネットワーク**] タブを使用して、応答ヘッダーの詳細を確認します。次のスクリーン ショットでは、このページの読み込みの**SPRequestDuration**の値は、924 ミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="6afbe-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![924 の要求時間が表示されているスクリーンショット](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="6afbe-p106">**SPRequestDuration**では、ページを準備するのにはサーバー上で実行された作業量を示します。検索 Web パーツでコンテンツ クエリ Web パーツでコンテンツを大幅に切り替え、ページのレンダリングにかかる時間が減少します。対照的に、同等でコンテンツ検索 Web パーツをページには、106 時間をミリ秒単位でこのスクリーン ショットに示すように、 **SPRequestDuration**値が含まれて同じ数の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="6afbe-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![106 の要求時間が表示されているスクリーンショット](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="6afbe-128">SharePoint のオンライン コンテンツの検索 Web パーツを追加します。</span><span class="sxs-lookup"><span data-stu-id="6afbe-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="6afbe-p107">コンテンツ検索 Web パーツを追加する、正規のコンテンツ クエリ Web パーツに似ています。セクションでは、 [SharePoint のコンテンツ検索 Web パーツを構成する](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a) *」、コンテンツ検索 Web パーツの追加」* を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6afbe-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="6afbe-131">コンテンツ検索 Web パーツの適切な検索クエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="6afbe-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="6afbe-p108">コンテンツ検索 Web パーツを追加すると、検索を絞り込むし、目的のアイテムを取得できます。これを行う方法の詳細については、 [SharePoint のコンテンツ検索 Web パーツの構成](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a)での *「コンテンツ検索 Web パーツでの高度なクエリを構成することでコンテンツ表示を」* のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6afbe-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="6afbe-134">クエリを構築およびテスト ツール</span><span class="sxs-lookup"><span data-stu-id="6afbe-134">Query building and testing tool</span></span>

<span data-ttu-id="6afbe-135">ビルドし、複雑なクエリをテストするツール、Codeplex で[検索クエリ ツール](https://sp2013searchtool.codeplex.com/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6afbe-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

