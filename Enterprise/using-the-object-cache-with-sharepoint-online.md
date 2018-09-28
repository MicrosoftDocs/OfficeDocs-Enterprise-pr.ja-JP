---
title: SharePoint Online でのオブジェクト キャッシュの使用
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: この資料では、SharePoint Server 2013 設置し、SharePoint Online でのオブジェクト キャッシュを使用しての違いについて説明します。
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 7cd210c44622ea2de5fb0e8e91c7be4839c80205
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2018
ms.locfileid: "24056166"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="5023b-103">SharePoint Online でのオブジェクト キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="5023b-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="5023b-104">この資料では、SharePoint Server 2013 設置し、SharePoint Online でのオブジェクト キャッシュを使用しての違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5023b-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="5023b-p101">SharePoint Online の展開では、オブジェクト キャッシュに依存するという悪影響があります。SharePoint Online でのオブジェクト キャッシュの依存関係はすべて、ページの信頼性を低下させます。</span><span class="sxs-lookup"><span data-stu-id="5023b-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="5023b-107">SharePoint Online と SharePoint Server 2013 オブジェクトのキャッシュのしくみ</span><span class="sxs-lookup"><span data-stu-id="5023b-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="5023b-p102">SharePoint Server 2013 は、オンプレミスでホストされているが、お客様には、オブジェクト キャッシュをホストするプライベートのフロント エンド web サーバーが持っています。これは、キャッシュを選択し、1 人の顧客は、専用メモリの量は、使用可能で、オブジェクト キャッシュに割り当てられているによってのみ制限を意味します。設置型のシナリオで 1 つだけのお客様に配信されるためフロント エンド web サーバーはユーザーが同じサイトに要求を作成すると、何度でも通常あります。つまり、キャッシュが完全に迅速に取得し、クエリ結果のリストと、ユーザーが定期的に要求している SharePoint オブジェクトのフルのままです。</span><span class="sxs-lookup"><span data-stu-id="5023b-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![オンプレミスのフロントエンド Web サーバーへのトラフィックと負荷を示しています](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="5023b-p103">結果として、ユーザーが 2 回目にページにアクセスするとき、ページの読み込み時間が短縮します。同じページを 4 回以上読み込むと、ページはすべてのフロントエンド Web サーバーにキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="5023b-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="5023b-p104">対照的に、SharePoint Online は、多くのより多くのサーバがより多くのサイトもいます。各ユーザーは、キャッシュ設定を設定していない別のフロント エンド web サーバーに接続できます。または、おそらくキャッシュが値を設定、サーバーがフロント エンド web サーバーに次のユーザーが別のサイトからページを要求します。または、場合でも、次のユーザーは、同じページを要求の場合、前回の訪問と、キャッシュ内にそのページを持たない別のフロント エンド web サーバーに負荷分散します。この最後の場合では、キャッシュ問題が解決しないユーザーにします。</span><span class="sxs-lookup"><span data-stu-id="5023b-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="5023b-p105">次の図で、各ドットはユーザーが要求していて、キャッシュされているページを表しています。さまざまな色は、SaaS インフラストラクチャを共用しているさまざまな顧客を表します。</span><span class="sxs-lookup"><span data-stu-id="5023b-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![SharePoint Online におけるオブジェクト キャッシュの結果を示します](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="5023b-p106">図からわかるように、スリムには特定のユーザーにそのページのキャッシュされたバージョンのサーバーの可能性があります。また、大規模なスループットとサーバーは、多くのサイト間で共有されるという事実、キャッシュは最後のだけ領域をキャッシュするため、使用のために長いです。</span><span class="sxs-lookup"><span data-stu-id="5023b-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="5023b-125">これらすべての理由から、ユーザーがキャッシュされたオブジェクトを取得するのに依存することは、SharePoint Online でユーザー体験とページの読み込み時間の品質を保証する効果的な方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="5023b-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="5023b-126">SharePoint Online でパフォーマンスを向上させるためにオブジェクト キャッシュに依存できないとしたら、代わりに何を使用すればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="5023b-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="5023b-p107">SharePoint Online でのキャッシュに依存しないほうがよいため、オブジェクト キャッシュを使用する SharePoint のカスタマイズに関する代わりの設計アプローチを評価する必要があります。つまり、ユーザーに良い結果をもたらすため、オブジェクトのキャッシュに依存しないパフォーマンスの問題のアプローチを使用するということです。これについては、このシリーズの他の記事で説明しています。それらは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5023b-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="5023b-130">SharePoint Online のナビゲーション オプション</span><span class="sxs-lookup"><span data-stu-id="5023b-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="5023b-131">SharePoint Online での縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="5023b-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="5023b-132">コンテンツ配信ネットワークの使用</span><span class="sxs-lookup"><span data-stu-id="5023b-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="5023b-133">SharePoint Online での画像の読み込み遅延と JavaScript</span><span class="sxs-lookup"><span data-stu-id="5023b-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

