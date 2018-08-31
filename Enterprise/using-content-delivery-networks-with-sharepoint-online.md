---
title: SharePoint Online のコンテンツ配信ネットワークを使用します。
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: '概要: この資料は、コンテンツ配信ネットワーク (Cdn) し、使用して SharePoint Online のパフォーマンスを向上する方法について説明します。'
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541624"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="2594d-103">SharePoint Online のコンテンツ配信ネットワークを使用します。</span><span class="sxs-lookup"><span data-stu-id="2594d-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="2594d-104">**の概要:** この資料では、コンテンツ配信ネットワーク (Cdn) し、使用して SharePoint Online のパフォーマンスを向上する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2594d-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="2594d-p101">今日の web 開発コミュニティでは、SharePoint ソリューションに含める場合があります (JavaScript、CSS ファイルなど) の多くの一般的なライブラリがあります。これらの多くは、ASP の CDN にマイクロソフトによってホストされています。これは、これらの分散サーバーからこれらのライブラリを参照してインターネットの組み込み DNS ルーティング システムができるよう、ユーザーに最も近いサーバーを見つけることを意味します。この資料の例では、ASP CDN とオンラインの SharePoint サーバーから一般的なライブラリ jQuery をダウンロードする間の時間差が非常に大きくする方法をデモンストレーションします。ユーザーも既に CDN のバージョンがキャッシュされ、ローカル コンピューターのため、ファイルをダウンロードする必要はありません。SharePoint Online サイトをホストするデータ センターから世界と距離を分散するユーザーがいる場合に重要なことができます。</span><span class="sxs-lookup"><span data-stu-id="2594d-p101">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution. Many of these are hosted by Microsoft on their ASP CDN. This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user. The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant. The user also may already have the CDN version cached on the local computer so that they do not have to download the file. This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="2594d-p102">SharePoint Online のページを作成する場合、ユーザーと SharePoint Online インスタンスの場所の物理的な距離が待ち時間に影響を与えます。このことは、世界的に展開していて、サイトがある大陸にホストされ、世界の反対側にいるユーザーがそのコンテンツにアクセスする組織には特に重要になります。エンドユーザーの近くにある別の場所に特定の一般的な Web 資産をホストすることで、CDN はこのような状況を和らげます。</span><span class="sxs-lookup"><span data-stu-id="2594d-p102">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance. This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content. CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="2594d-p103">CDN は、同じファイルをホストする世界規模のサーバーのネットワークであるため、ユーザーに最も近いサーバーがファイルに対応するように、CDN に格納されたファイルのインターネットの URL がクライアントのコンピューターによって解釈されます。これにより、ネットワークのラウンド トリップによって発生する遅延が大きく低減します。</span><span class="sxs-lookup"><span data-stu-id="2594d-p103">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file. Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="2594d-116">グローバルな対象ユーザー用の SharePoint Online サイトをホストする際の課題</span><span class="sxs-lookup"><span data-stu-id="2594d-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="2594d-p104">SharePoint Online サイトは、Office 365 にサインアップしたときに選択された場所 (ユーザーが指定する) に関連するデータ センターにホストされます。たとえば、サイトが米国内のサーバー上にあり、ユーザーは東アジアからサイトにアクセスする場合、データが光ファイバー ケーブルで伝送する距離があるため、遅延の問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="2594d-p104">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365. For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="2594d-p105">既定の SharePoint ユーザー インターフェイスで使用される多くの静的なファイルは、既に Cdn のマイクロソフトの世界中のネットワークでホストされます。時間の経過とともにパフォーマンスが向上します。ただし (たとえば、一般的な JavaScript、CSS の資産を使用する場合、JQuery、Modernizr、ブートス トラップ、または ASP.NET Ajax) 自由に利用可能な Cdn を使用してこれらのファイルの読み込み時間を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="2594d-p105">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs. This will improve performance over time. However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="2594d-122">CDN を使用してダウンロード速度を向上させる利点</span><span class="sxs-lookup"><span data-stu-id="2594d-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="2594d-p106">Cdn を使用すると、さまざまな理由からページの読み込み時間を改善できます。理由の 1 つは、SharePoint Online のインスタンスまでの距離よりも短い、CDN とユーザー間の距離である可能性があります。これらのネットワークは、広範囲にわたって分散し、の可用性と応答時間が非常に高いものも。理由の 1 つをされていると、CSS ファイルの一般的なライブラリを使用して、CDN と協力して、ユーザーはキャッシュ ライブラリに既にあり、ダウンロードする必要はありませんも場合。</span><span class="sxs-lookup"><span data-stu-id="2594d-p106">Using CDNs can improve page load times for a variety of reasons. One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance. These networks are highly distributed and are also designed to have very high availability and response times. Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="2594d-p107">次のスクリーン ショットでは、Cdn を使用する利点について説明します。Internet Explorer 11 の開発者ツールの [**ネットワーク**] タブでは、これらのスクリーン ショットです。これらのスクリーン ショットでは、人気のあるライブラリ jQuery の待機時間を表示します。Internet Explorer で、この画面を表示するのには**f12 キー**を押すし、Wi-fi のアイコンを導入するケースでは、 **[ネットワーク**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="2594d-p107">The following screen shots illustrate the advantages of using CDNs. These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools. These screen shots show the latency on the popular library jQuery. To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![F12 ネットワークのスクリーンショット](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="2594d-p108">このスクリーン ショットは、SharePoint Online サイト自体のマスター ページ ギャラリーにアップロードされたライブラリを示しています。ライブラリにアップロードするにかかった時間は、1.51 秒です。</span><span class="sxs-lookup"><span data-stu-id="2594d-p108">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself. The time it took to upload the library is 1.51 seconds.</span></span>
  
![読み込み時間 1.51 秒のスクリーン ショット](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="2594d-p109">2 番目のスクリーン ショットは、マイクロソフトによって提供される同じファイルを示しています CDN。この時間の遅延時間は、約 496 ミリ秒です。これは大きな改善であり、全体の 2 番目がページのコンテンツをダウンロードする時間を短縮ことを示しています。</span><span class="sxs-lookup"><span data-stu-id="2594d-p109">The second screen shot shows the same file delivered by Microsoft's CDN. This time the latency is around 496 milliseconds. This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![読み込み時間 469 ミリ秒のスクリーンショット](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="2594d-139">SharePoint Server 2013 で CDN を使用する</span><span class="sxs-lookup"><span data-stu-id="2594d-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="2594d-p110">Cdn を使用してだけは、SharePoint Online のコンテキストで意味が、SharePoint Server 2013 を避ける必要があります。地理的な場所の周囲の利点のすべてを保持しないサーバーがある設置型の場合は true または地理的に閉じるためにです。さらに、ホストされているサーバーへのネットワーク接続がある場合は、サイト インターネットに接続せずに使用することがあり、CDN のファイルを取得できません。それ以外の場合は利用可能なライブラリとファイルの安定性が必要な場合、サイトの CDN を使用してください。</span><span class="sxs-lookup"><span data-stu-id="2594d-p110">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013. This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway. Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files. Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="2594d-144">一般的な CDN とその使用方法</span><span class="sxs-lookup"><span data-stu-id="2594d-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="2594d-145">JQuery (およびすべての他のライブラリ) を含む一般的なライブラリのほとんどを提供する Microsoft Ajax CDN ASP.NET Ajax、ブートス トラップ、Knockout.js、および多く。</span><span class="sxs-lookup"><span data-stu-id="2594d-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="2594d-p111">これらのスクリプトをプロジェクトに含めるには、CDN のアドレスをプロジェクト自体に含めるのではなく、一般的に利用可能なライブラリへの参照を CDN のアドレスへの参照に置き換えます。たとえば、次のコードを使用して jQuery にリンクさせます。</span><span class="sxs-lookup"><span data-stu-id="2594d-p111">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself. For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="2594d-148">Cdn の詳細については、[コンテンツ配信ネットワーク](content-delivery-networks.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2594d-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="2594d-149">SharePoint で Cdn を使用する方法のより多くのトピック</span><span class="sxs-lookup"><span data-stu-id="2594d-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="2594d-150">Office 365 の CDN からクライアント側の web パーツをホストしています。</span><span class="sxs-lookup"><span data-stu-id="2594d-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

