---
title: SharePoint Online のパフォーマンスの問題の診断
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/9/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: この記事では、Internet Explorer 開発者ツールを使用して SharePoint Online サイトの一般的な問題を診断する方法について説明します。
ms.openlocfilehash: a4d66fd019a3b477a97dbf039144734dc7ee1288
ms.sourcegitcommit: cb338a74194ec9ba0913070e2b74c9f50caffb3b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "35605503"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="ee973-103">SharePoint Online のパフォーマンスの問題の診断</span><span class="sxs-lookup"><span data-stu-id="ee973-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="ee973-104">この記事では、Internet Explorer 開発者ツールを使用して SharePoint Online サイトの一般的な問題を診断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee973-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="ee973-105">SharePoint Online サイトのページに、カスタマイズに関するパフォーマンス上の問題があることを特定するには、3種類の方法があります。</span><span class="sxs-lookup"><span data-stu-id="ee973-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="ee973-106">F12 ツールバーのネットワークモニター</span><span class="sxs-lookup"><span data-stu-id="ee973-106">The F12 tool bar network monitor</span></span>

- <span data-ttu-id="ee973-107">カスタマイズされていない基準を比較する</span><span class="sxs-lookup"><span data-stu-id="ee973-107">Comparison to a non-customized baseline</span></span>

- <span data-ttu-id="ee973-108">SharePoint Online 応答ヘッダーの指標</span><span class="sxs-lookup"><span data-stu-id="ee973-108">SharePoint Online response header metrics</span></span>

<span data-ttu-id="ee973-109">このトピックでは、これらの各方法を使用して、パフォーマンスの問題を診断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee973-109">This topic describes how to use each of these methods to diagnose performance issues.</span></span> <span data-ttu-id="ee973-110">問題の原因を特定したら、SharePoint のパフォーマンスの向上に関する記事を使用して、ソリューションに向かって作業することがhttp://aka.ms/tuneできます。</span><span class="sxs-lookup"><span data-stu-id="ee973-110">Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="ee973-111">F12 ツールバーを使用して SharePoint Online のパフォーマンスを診断する</span><span class="sxs-lookup"><span data-stu-id="ee973-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="ee973-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="ee973-112"></span></span>

<span data-ttu-id="ee973-113">この記事では、Internet Explorer 11 を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee973-113">In this article we use Internet Explorer 11.</span></span> <span data-ttu-id="ee973-114">他のブラウザーの F12 開発者ツールのバージョンは、同様の機能を備えていますが、外観が若干異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ee973-114">Versions of the F12 developer tools on other browsers have similar features though they may look slightly different.</span></span> <span data-ttu-id="ee973-115">F12 開発者ツールの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee973-115">For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="ee973-116">F12 ツールの新機能</span><span class="sxs-lookup"><span data-stu-id="ee973-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)

- <span data-ttu-id="ee973-117">
  [F12 開発者ツールの使用](https://go.microsoft.com/fwlink/p/?LinkId=522546)</span><span class="sxs-lookup"><span data-stu-id="ee973-117">[Using the F12 developer tools](https://go.microsoft.com/fwlink/p/?LinkId=522546)</span></span>

<span data-ttu-id="ee973-118">開発者ツールを起動するには、 **F12**キーを押してから、wi-fi アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee973-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span>
  
![F12 開発者ツールの Wi-Fi アイコンのスクリーンショット](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="ee973-120">[**ネットワーク**] タブで、緑色の再生ボタンを押してページをロードします。</span><span class="sxs-lookup"><span data-stu-id="ee973-120">On the **Network** tab, press the green play button to load a page.</span></span> <span data-ttu-id="ee973-121">このツールは、要求されたページを取得するために、ブラウザーが要求するすべてのファイルを返します。</span><span class="sxs-lookup"><span data-stu-id="ee973-121">The tool returns all of the files that the browser requests in order to get the page you asked for.</span></span> <span data-ttu-id="ee973-122">次のスクリーンショットは、このような一覧を示しています。</span><span class="sxs-lookup"><span data-stu-id="ee973-122">The following screen shot shows one such list.</span></span>
  
![ページ要求で返されるファイル リストのスクリーンショット。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="ee973-124">このスクリーンショットに示されているように、右側のファイルのダウンロード時間を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee973-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![SharePoint から要求されたページを読み込むのにかかる時間を示す図](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="ee973-126">これにより、ファイルの読み込みにかかった時間を視覚的に表現できます。</span><span class="sxs-lookup"><span data-stu-id="ee973-126">This gives you a visual representation of how long the file took to load.</span></span> <span data-ttu-id="ee973-127">緑色の線は、ページがブラウザーでレンダリングできる状態になったことを表します。</span><span class="sxs-lookup"><span data-stu-id="ee973-127">The green line represents when the page is ready to be rendered by the browser.</span></span> <span data-ttu-id="ee973-128">これにより、サイトでのページの読み込みが低速になる原因となる可能性のあるさまざまなファイルを簡単に確認できます。</span><span class="sxs-lookup"><span data-stu-id="ee973-128">This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="ee973-129">SharePoint Online のカスタマイズされていないベースラインの設定</span><span class="sxs-lookup"><span data-stu-id="ee973-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="ee973-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="ee973-130"></span></span>

<span data-ttu-id="ee973-131">サイトのパフォーマンスの強度を判断する最良の方法は、SharePoint Online に完全に使用されていないサイトコレクションをセットアップすることです。</span><span class="sxs-lookup"><span data-stu-id="ee973-131">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online.</span></span> <span data-ttu-id="ee973-132">このようにすると、サイトのさまざまな要素を、ページ上でカスタマイズしなくても、その内容と比較できます。</span><span class="sxs-lookup"><span data-stu-id="ee973-132">This way you can compare all the various aspects of your site with what you would get with no customization on the page.</span></span> <span data-ttu-id="ee973-133">OneDrive for Business ホームページは、カスタマイズが必要となる可能性がある別のサイトコレクションの良い例です。</span><span class="sxs-lookup"><span data-stu-id="ee973-133">The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="ee973-134">SharePoint 応答ヘッダー情報を表示する</span><span class="sxs-lookup"><span data-stu-id="ee973-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="ee973-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="ee973-135"></span></span>

<span data-ttu-id="ee973-136">SharePoint Online では、各ファイルの応答ヘッダーでブラウザーに送り返される情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ee973-136">In SharePoint Online, you can access the information that is sent back to the browser in the response header for each file.</span></span> <span data-ttu-id="ee973-137">パフォーマンスの問題を診断するのに最も役立つ値は**Sprequestduration**で、サーバーで要求が処理されるのにかかった時間を表示します。</span><span class="sxs-lookup"><span data-stu-id="ee973-137">The most useful value for diagnosing performance issues is **SPRequestDuration**, which displays the amount of time that the request took on the server to be processed.</span></span> <span data-ttu-id="ee973-138">これにより、要求が非常に重いもので、リソースを大量に消費しているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="ee973-138">This can help determine if the request is very heavy and resource intensive.</span></span> <span data-ttu-id="ee973-139">これは、サーバーがページにサービスを提供するために実行している作業の量を理解するのに最適です。</span><span class="sxs-lookup"><span data-stu-id="ee973-139">This is the best insight you have into how much work the server is doing to serve the page.</span></span>

### <a name="to-view-sharepoint-response-header-information"></a><span data-ttu-id="ee973-140">SharePoint 応答ヘッダー情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="ee973-140">To view SharePoint response header information</span></span>
  
1. <span data-ttu-id="ee973-141">F12 ツールがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee973-141">Ensure that you have the F12 tools installed.</span></span> <span data-ttu-id="ee973-142">これらのツールのダウンロードとインストールの詳細については、「 [F12 ツールの新機能](https://go.microsoft.com/fwlink/p/?LinkId=522545)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee973-142">For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>

2. <span data-ttu-id="ee973-143">F12 ツールの [**ネットワーク**] タブで、緑色の再生ボタンを押してページを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="ee973-143">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span>

3. <span data-ttu-id="ee973-144">ツールによって返される .aspx ファイルのいずれかをクリックし、[**詳細**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee973-144">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span>

    ![応答ヘッダーの詳細を示しています](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="ee973-146">[**応答ヘッダー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ee973-146">Click **Response headers**.</span></span>

    ![応答ヘッダーの URL を示す図](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="ee973-148">SharePoint Online でパフォーマンスの問題が発生する原因</span><span class="sxs-lookup"><span data-stu-id="ee973-148">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="ee973-149"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="ee973-149"></span></span>

<span data-ttu-id="ee973-150">「 [SharePoint Online のナビゲーションオプション](navigation-options-for-sharepoint-online.md)」では、SPRequestDuration 値を使用して、複雑な構造ナビゲーションによって、ページの処理に長い時間がかかることを判断する例を示します。</span><span class="sxs-lookup"><span data-stu-id="ee973-150">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server.</span></span> <span data-ttu-id="ee973-151">ベースラインサイト (カスタマイズなし) の値を取得することによって、特定のファイルの読み込みに時間がかかるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="ee973-151">By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load.</span></span> <span data-ttu-id="ee973-152">[SharePoint Online のナビゲーションオプション](navigation-options-for-sharepoint-online.md)で使用されている例は、主に .aspx ファイルです。</span><span class="sxs-lookup"><span data-stu-id="ee973-152">The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file.</span></span> <span data-ttu-id="ee973-153">このファイルには、ページの読み込みに対して実行される ASP.NET コードの大部分が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee973-153">That file contains most of the ASP.NET code that runs for your page load.</span></span> <span data-ttu-id="ee973-154">使用するサイトテンプレートによっては、ホームページをカスタマイズする場合、default.aspx、default.aspx、default.aspx、またはその他の名前の場合があります。</span><span class="sxs-lookup"><span data-stu-id="ee973-154">Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page.</span></span> <span data-ttu-id="ee973-155">この数値がベースラインサイトよりかなり大きい場合は、パフォーマンスの問題を発生させる、ページに複雑な処理が発生していることを示しています。</span><span class="sxs-lookup"><span data-stu-id="ee973-155">If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span>
  
<span data-ttu-id="ee973-156">サイトに固有の問題を特定した後、パフォーマンスが低下していることを確認するには、ページのカスタマイズなど、考えられるすべての原因を除去して、それらを1つずつサイトに追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ee973-156">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one.</span></span> <span data-ttu-id="ee973-157">ページが正常に実行されているカスタマイズを削除すると、特定のカスタマイズを1つずつ追加することができます。</span><span class="sxs-lookup"><span data-stu-id="ee973-157">Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="ee973-158">たとえば、非常に複雑なナビゲーションの場合は、サブサイトを表示しないようにナビゲーションを変更してから、開発者ツールをチェックして、それに違いがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee973-158">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference.</span></span> <span data-ttu-id="ee973-159">または、大量のコンテンツロールアップを使用している場合は、それらをページから削除して、問題が改善されるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ee973-159">Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things.</span></span> <span data-ttu-id="ee973-160">考えられる原因をすべて排除して、一度に1つずつ追加し直すと、どの機能が最大の問題であるかを簡単に特定して、ソリューションに向けて作業できます。</span><span class="sxs-lookup"><span data-stu-id="ee973-160">If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
