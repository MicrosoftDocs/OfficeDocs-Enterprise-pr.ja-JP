---
title: SharePoint Online でのコンテンツ配信ネットワークの使用
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: '概要: この記事では、コンテンツ配信ネットワーク (CDNs) と、それらを使用して SharePoint Online のパフォーマンスを向上させる方法について説明します。'
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070583"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="6bcdf-103">SharePoint Online でのコンテンツ配信ネットワークの使用</span><span class="sxs-lookup"><span data-stu-id="6bcdf-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="6bcdf-104">**概要:** この記事では、コンテンツ配信ネットワーク (CDNs) と、それらを使用して SharePoint Online のパフォーマンスを向上させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="6bcdf-105">今日の web 開発コミュニティには、SharePoint ソリューションに含めることができる一般的なライブラリ (JavaScript ファイルや CSS ファイルなど) が多数あります。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-105">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution.</span></span> <span data-ttu-id="6bcdf-106">これらの多くは、Microsoft によって ASP CDN にホストされています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-106">Many of these are hosted by Microsoft on their ASP CDN.</span></span> <span data-ttu-id="6bcdf-107">これは、これらの配布サーバーからこれらのライブラリを参照し、インターネットの組み込みの DNS ルーティングシステムがユーザーに最も近いサーバーを検索できるようにすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-107">This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user.</span></span> <span data-ttu-id="6bcdf-108">この記事の例では、SharePoint Online server と ASP CDN の間で人気のあるライブラリ jQuery をダウンロードする際の時差が非常に重要であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-108">The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant.</span></span> <span data-ttu-id="6bcdf-109">ユーザーは、ファイルをダウンロードする必要がないように、既に CDN バージョンをローカルコンピューターにキャッシュしておくこともできます。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-109">The user also may already have the CDN version cached on the local computer so that they do not have to download the file.</span></span> <span data-ttu-id="6bcdf-110">これは、ユーザーが世界中に分散されており、SharePoint Online サイトをホストするデータセンターから遠く離れている場合に重要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-110">This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="6bcdf-111">SharePoint Online のページを作成する場合、待機時間は、ユーザーと SharePoint Online インスタンスの場所の物理的な距離によって影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-111">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance.</span></span> <span data-ttu-id="6bcdf-112">これは、世界中のユーザーが自分のコンテンツにアクセスしているときに、ある大陸でサイトがホストされている場合に、グローバルなプレゼンスを持つ組織にとって特に重要です。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-112">This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content.</span></span> <span data-ttu-id="6bcdf-113">CDNs は、特定の人気のある web アセットをエンドユーザーに近い場所にホストすることで、このような状況を緩和するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-113">CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="6bcdf-114">CDN は、同じファイルをホストするサーバーの世界規模のネットワークであるため、CDNs に格納されているファイルのインターネット Url はクライアントコンピューターによって解釈されるため、ユーザーに最も近いサーバーがファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-114">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file.</span></span> <span data-ttu-id="6bcdf-115">これにより、ネットワークラウンドトリップによる遅延が大幅に軽減されます。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-115">Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="6bcdf-116">グローバルな対象ユーザーのために SharePoint Online サイトをホストするための課題</span><span class="sxs-lookup"><span data-stu-id="6bcdf-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="6bcdf-117">SharePoint Online サイトは、Office 365 でサインアップしたときに選択された場所 (ユーザーが指定) を基準にして、データセンターでホストされます。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-117">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365.</span></span> <span data-ttu-id="6bcdf-118">たとえば、サイトが米国内のサーバー上にあり、ユーザーが東アジアからサイトにアクセスしている場合、データが光ファイバーケーブルを通過するために必要な距離が原因で、待機時間の問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-118">For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="6bcdf-119">既定の SharePoint ユーザーインターフェイスで使用されている多くの静的ファイルは、既に Microsoft の世界規模の CDNs のネットワーク上にホストされています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-119">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs.</span></span> <span data-ttu-id="6bcdf-120">これにより、時間の経過とともにパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-120">This will improve performance over time.</span></span> <span data-ttu-id="6bcdf-121">ただし、一般的な JavaScript および CSS アセット (たとえば、次のようなもの) を使用している場合は、JQuery、Modernizr、ブートストラップ、または ASP.NET Ajax) フリーで利用可能な CDNs を使用して、これらのファイルの読み込み時間を短縮することができます。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-121">However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="6bcdf-122">ダウンロード速度を向上させるために CDNs を使用する利点</span><span class="sxs-lookup"><span data-stu-id="6bcdf-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="6bcdf-123">CDNs を使用すると、さまざまな理由からページの読み込み時間を短縮できます。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-123">Using CDNs can improve page load times for a variety of reasons.</span></span> <span data-ttu-id="6bcdf-124">1つの理由は、CDN とユーザーの間の距離が、SharePoint Online インスタンスまでの距離よりも短くなる可能性があることです。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-124">One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance.</span></span> <span data-ttu-id="6bcdf-125">これらのネットワークは十分に分散化されており、非常に高い可用性と応答時間が得られるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-125">These networks are highly distributed and are also designed to have very high availability and response times.</span></span> <span data-ttu-id="6bcdf-126">もう1つの理由として、CSS ファイルの一般的なライブラリを CDN と共に使用している場合、ユーザーは既にライブラリをキャッシュしていて、そのライブラリをまったくダウンロードする必要がない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-126">Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="6bcdf-127">次のスクリーンショットは、CDNs を使用する利点を示しています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-127">The following screen shots illustrate the advantages of using CDNs.</span></span> <span data-ttu-id="6bcdf-128">これらのスクリーンショットは、Internet Explorer 11 開発者ツールの [**ネットワーク**] タブにあります。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-128">These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools.</span></span> <span data-ttu-id="6bcdf-129">これらのスクリーンショットは、人気のあるライブラリ jQuery の待機時間を示しています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-129">These screen shots show the latency on the popular library jQuery.</span></span> <span data-ttu-id="6bcdf-130">この画面を表示するには、Internet Explorer で**F12**キーを押して、wi-fi アイコンで認識されている [**ネットワーク**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-130">To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![F12 ネットワークのスクリーンショット](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="6bcdf-132">このスクリーンショットは、SharePoint Online サイト自体のマスターページギャラリーにアップロードされたライブラリを示しています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-132">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself.</span></span> <span data-ttu-id="6bcdf-133">ライブラリのアップロードにかかった時間は1.51 秒です。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-133">The time it took to upload the library is 1.51 seconds.</span></span>
  
![読み込み時間 1.51 秒のスクリーン ショット](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="6bcdf-135">2番目のスクリーンショットは、Microsoft の CDN によって配信された同じファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-135">The second screen shot shows the same file delivered by Microsoft's CDN.</span></span> <span data-ttu-id="6bcdf-136">この時間が経過すると、遅延は約496ミリ秒になります。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-136">This time the latency is around 496 milliseconds.</span></span> <span data-ttu-id="6bcdf-137">これは大規模な改善で、ページコンテンツのダウンロードに合計時間が短縮されることを示しています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-137">This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![読み込み時間 469 ミリ秒のスクリーンショット](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="6bcdf-139">SharePoint Server 2013 での CDNs の使用</span><span class="sxs-lookup"><span data-stu-id="6bcdf-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="6bcdf-140">CDNs の使用は SharePoint Online のコンテキストでのみ有効であり、SharePoint Server 2013 で回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-140">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013.</span></span> <span data-ttu-id="6bcdf-141">これは、サーバーが社内に設置されている場合や、地理的に閉じている場合は、地理的な場所に関するすべての利点が true を保持しないためです。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-141">This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway.</span></span> <span data-ttu-id="6bcdf-142">また、ホストされているサーバーへのネットワーク接続がある場合は、インターネット接続を使用せずにサイトが使用される可能性があるため、CDN ファイルを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-142">Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files.</span></span> <span data-ttu-id="6bcdf-143">それ以外の場合は、使用可能で、サイトに必要なライブラリおよびファイルに対して安定したものがある場合は、CDN を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-143">Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="6bcdf-144">一般的な CDNs とその使用方法</span><span class="sxs-lookup"><span data-stu-id="6bcdf-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="6bcdf-145">Microsoft の Ajax CDN では、jQuery (およびその他のすべてのライブラリ)、ASP.NET Ajax、ブートストラップ、ノックアウトなど、よく使用されるライブラリのほとんどが提供されています。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="6bcdf-146">これらのスクリプトをプロジェクトに含めるには、プロジェクト自体に含めるのではなく、これらのパブリックなライブラリへの参照を CDN アドレスへの参照に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-146">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself.</span></span> <span data-ttu-id="6bcdf-147">たとえば、次のコードを使用して jQuery にリンクします。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-147">For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="6bcdf-148">CDNs の詳細については、「[コンテンツ配信ネットワーク](content-delivery-networks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bcdf-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="6bcdf-149">SharePoint での CDNs の使用に関するその他のトピック</span><span class="sxs-lookup"><span data-stu-id="6bcdf-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="6bcdf-150">Office 365 CDN からのクライアント側 web パーツのホスティング</span><span class="sxs-lookup"><span data-stu-id="6bcdf-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

