---
title: SharePoint Online のパフォーマンスの問題の診断
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: この記事では、Internet Explorer 開発者ツールを使用して SharePoint Online サイトの一般的な問題を診断する方法について説明します。
ms.openlocfilehash: dfc66822a98ce26bfd9fd94d9d58882b8b140831
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067863"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="d8b96-103">SharePoint Online のパフォーマンスの問題の診断</span><span class="sxs-lookup"><span data-stu-id="d8b96-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="d8b96-104">この記事では、Internet Explorer 開発者ツールを使用して SharePoint Online サイトの一般的な問題を診断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="d8b96-105">SharePoint Online サイトのページに、カスタマイズに関するパフォーマンス上の問題があることを特定するには、3種類の方法があります。</span><span class="sxs-lookup"><span data-stu-id="d8b96-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="d8b96-106">F12 ツールバーのネットワークモニター</span><span class="sxs-lookup"><span data-stu-id="d8b96-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="d8b96-107">カスタマイズされていない基準を比較する</span><span class="sxs-lookup"><span data-stu-id="d8b96-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="d8b96-108">SharePoint Online 応答ヘッダーの指標</span><span class="sxs-lookup"><span data-stu-id="d8b96-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="d8b96-109">このトピックでは、これらの各方法を使用して、パフォーマンスの問題を診断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-109">This topic describes how to use each of these methods to diagnose performance issues.</span></span> <span data-ttu-id="d8b96-110">問題の原因を特定したら、SharePoint のパフォーマンスの向上に関する記事を使用して、ソリューションに向かって作業することがhttp://aka.ms/tuneできます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-110">Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="d8b96-111">F12 ツールバーを使用して SharePoint Online のパフォーマンスを診断する</span><span class="sxs-lookup"><span data-stu-id="d8b96-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="d8b96-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="d8b96-112"></span></span>

<span data-ttu-id="d8b96-113">この記事では、Internet Explorer 11 を使用します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-113">In this article we use Internet Explorer 11.</span></span> <span data-ttu-id="d8b96-114">他のブラウザーの F12 開発者ツールのバージョンは、同様の機能を備えていますが、外観が若干異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d8b96-114">Versions of the F12 developer tools on other browsers have similar features though they may look slightly different.</span></span> <span data-ttu-id="d8b96-115">F12 開発者ツールの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8b96-115">For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="d8b96-116">F12 ツールの新機能</span><span class="sxs-lookup"><span data-stu-id="d8b96-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- <span data-ttu-id="d8b96-117">
  [F12 開発者ツールの使用](https://go.microsoft.com/fwlink/p/?LinkId=522546)</span><span class="sxs-lookup"><span data-stu-id="d8b96-117">[Using the F12 developer tools](https://go.microsoft.com/fwlink/p/?LinkId=522546)</span></span>
    
<span data-ttu-id="d8b96-118">開発者ツールを起動するには、 **F12**キーを押してから、wi-fi アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8b96-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![F12 開発者ツールの Wi-Fi アイコンのスクリーンショット](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="d8b96-120">[**ネットワーク**] タブで、緑色の再生ボタンを押してページをロードします。</span><span class="sxs-lookup"><span data-stu-id="d8b96-120">On the **Network** tab, press the green play button to load a page.</span></span> <span data-ttu-id="d8b96-121">このツールは、要求されたページを取得するために、ブラウザーが要求するすべてのファイルを返します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-121">The tool returns all of the files that the browser requests in order to get the page you asked for.</span></span> <span data-ttu-id="d8b96-122">次のスクリーンショットは、このような一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="d8b96-122">The following screen shot shows one such list.</span></span> 
  
![ページ要求で返されるファイル リストのスクリーンショット。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="d8b96-124">このスクリーンショットに示されているように、右側のファイルのダウンロード時間を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![SharePoint から要求されたページを読み込むのにかかる時間を示す図](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="d8b96-126">これにより、ファイルの読み込みにかかった時間を視覚的に表現できます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-126">This gives you a visual representation of how long the file took to load.</span></span> <span data-ttu-id="d8b96-127">緑色の線は、ページがブラウザーでレンダリングできる状態になったことを表します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-127">The green line represents when the page is ready to be rendered by the browser.</span></span> <span data-ttu-id="d8b96-128">これにより、サイトでのページの読み込みが低速になる原因となる可能性のあるさまざまなファイルを簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-128">This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="d8b96-129">SharePoint Online のカスタマイズされていないベースラインの設定</span><span class="sxs-lookup"><span data-stu-id="d8b96-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="d8b96-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="d8b96-130"></span></span>

<span data-ttu-id="d8b96-131">サイトのパフォーマンスの強度を判断する最良の方法は、SharePoint Online に完全に使用されていないサイトコレクションをセットアップすることです。</span><span class="sxs-lookup"><span data-stu-id="d8b96-131">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online.</span></span> <span data-ttu-id="d8b96-132">このようにすると、サイトのさまざまな要素を、ページ上でカスタマイズしなくても、その内容と比較できます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-132">This way you can compare all the various aspects of your site with what you would get with no customization on the page.</span></span> <span data-ttu-id="d8b96-133">OneDrive for Business ホームページは、カスタマイズが必要となる可能性がある別のサイトコレクションの良い例です。</span><span class="sxs-lookup"><span data-stu-id="d8b96-133">The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="d8b96-134">SharePoint 応答ヘッダー情報を表示する</span><span class="sxs-lookup"><span data-stu-id="d8b96-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="d8b96-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="d8b96-135"></span></span>

<span data-ttu-id="d8b96-136">SharePoint Online と SharePoint Server 2013 では、各ファイルの応答ヘッダーでブラウザーに送り返される情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-136">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file.</span></span> <span data-ttu-id="d8b96-137">パフォーマンスの問題を診断するための最も有用な2つの値は、SPRequestDuration および SharePointHealthScore です。</span><span class="sxs-lookup"><span data-stu-id="d8b96-137">The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="d8b96-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="d8b96-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="d8b96-139">これは、要求がサーバーで処理されるのにかかった時間の長さです。</span><span class="sxs-lookup"><span data-stu-id="d8b96-139">This is the amount of time that the request took on the server to be processed.</span></span> <span data-ttu-id="d8b96-140">これにより、要求が非常に重いもので、リソースを大量に消費しているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-140">This can help determine if the request is very heavy and resource intensive.</span></span> <span data-ttu-id="d8b96-141">これは、サーバーがページにサービスを提供するために実行している作業の量を理解するのに最適です。</span><span class="sxs-lookup"><span data-stu-id="d8b96-141">This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="d8b96-142">**SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="d8b96-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="d8b96-143">これは、SharePoint インスタンスが実行されているサーバーまたは CPU の使用率を示します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-143">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs.</span></span> <span data-ttu-id="d8b96-144">この数は0から10の範囲です。0はサーバーがアイドル状態であることを示し、10はサーバーがビジーであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-144">This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy.</span></span> <span data-ttu-id="d8b96-145">常に9または10になる正常性スコアは、サーバーのパフォーマンスに関する継続的な問題を示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d8b96-145">A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server.</span></span> <span data-ttu-id="d8b96-146">その他の番号は、サーバーが予期された範囲内で動作していることを示します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-146">Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="d8b96-147">**SharePoint 応答ヘッダー情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="d8b96-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="d8b96-148">F12 ツールがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-148">Ensure that you have the F12 tools installed.</span></span> <span data-ttu-id="d8b96-149">これらのツールのダウンロードとインストールの詳細については、「 [F12 ツールの新機能](https://go.microsoft.com/fwlink/p/?LinkId=522545)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8b96-149">For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="d8b96-150">F12 ツールの [**ネットワーク**] タブで、緑色の再生ボタンを押してページを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="d8b96-151">ツールによって返される .aspx ファイルのいずれかをクリックし、[**詳細**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8b96-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![応答ヘッダーの詳細を示しています](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="d8b96-153">[**応答ヘッダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8b96-153">Click **Response headers**.</span></span> 
    
    ![応答ヘッダーの URL を示す図](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="d8b96-155">SharePoint Online でパフォーマンスの問題が発生する原因</span><span class="sxs-lookup"><span data-stu-id="d8b96-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="d8b96-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="d8b96-156"></span></span>

<span data-ttu-id="d8b96-157">「 [SharePoint Online のナビゲーションオプション](navigation-options-for-sharepoint-online.md)」では、SPRequestDuration 値を使用して、複雑な構造ナビゲーションによって、ページの処理に長い時間がかかることを判断する例を示します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-157">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server.</span></span> <span data-ttu-id="d8b96-158">ベースラインサイト (カスタマイズなし) の値を取得することによって、特定のファイルの読み込みに時間がかかるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-158">By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load.</span></span> <span data-ttu-id="d8b96-159">[SharePoint Online のナビゲーションオプション](navigation-options-for-sharepoint-online.md)で使用されている例は、主に .aspx ファイルです。</span><span class="sxs-lookup"><span data-stu-id="d8b96-159">The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file.</span></span> <span data-ttu-id="d8b96-160">このファイルには、ページの読み込みに対して実行される ASP.NET コードの大部分が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d8b96-160">That file contains most of the ASP.NET code that runs for your page load.</span></span> <span data-ttu-id="d8b96-161">使用するサイトテンプレートによっては、ホームページをカスタマイズする場合、default.aspx、default.aspx、default.aspx、またはその他の名前の場合があります。</span><span class="sxs-lookup"><span data-stu-id="d8b96-161">Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page.</span></span> <span data-ttu-id="d8b96-162">この数値がベースラインサイトよりかなり大きい場合は、パフォーマンスの問題を発生させる、ページに複雑な処理が発生していることを示しています。</span><span class="sxs-lookup"><span data-stu-id="d8b96-162">If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="d8b96-163">サイトに固有の問題を特定した後、パフォーマンスが低下していることを確認するには、ページのカスタマイズなど、考えられるすべての原因を除去して、それらを1つずつサイトに追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d8b96-163">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one.</span></span> <span data-ttu-id="d8b96-164">ページが正常に実行されているカスタマイズを削除すると、特定のカスタマイズを1つずつ追加することができます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-164">Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="d8b96-165">たとえば、非常に複雑なナビゲーションの場合は、サブサイトを表示しないようにナビゲーションを変更してから、開発者ツールをチェックして、それに違いがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-165">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference.</span></span> <span data-ttu-id="d8b96-166">または、大量のコンテンツロールアップを使用している場合は、それらをページから削除して、問題が改善されるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d8b96-166">Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things.</span></span> <span data-ttu-id="d8b96-167">考えられる原因をすべて排除して、一度に1つずつ追加し直すと、どの機能が最大の問題であるかを簡単に特定して、ソリューションに向けて作業できます。</span><span class="sxs-lookup"><span data-stu-id="d8b96-167">If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

