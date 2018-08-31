---
title: SharePoint Online のパフォーマンスの問題の診断
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: この資料は、Internet Explorer の開発者ツールを使用して SharePoint Online サイトに関する一般的な問題を診断する方法を示します。
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541668"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="4aee6-103">SharePoint Online のパフォーマンスの問題の診断</span><span class="sxs-lookup"><span data-stu-id="4aee6-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="4aee6-104">この資料は、Internet Explorer の開発者ツールを使用して SharePoint Online サイトに関する一般的な問題を診断する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4aee6-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="4aee6-105">SharePoint Online サイトのページにカスタマイズによるパフォーマンスの問題があることを識別する 3 つの異なる方法があります。</span><span class="sxs-lookup"><span data-stu-id="4aee6-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="4aee6-106">F12 ツール バー ネットワーク モニター</span><span class="sxs-lookup"><span data-stu-id="4aee6-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="4aee6-107">カスタマイズされていないベースラインとの比較</span><span class="sxs-lookup"><span data-stu-id="4aee6-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="4aee6-108">SharePoint Online の応答ヘッダーのメトリックス</span><span class="sxs-lookup"><span data-stu-id="4aee6-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="4aee6-p101">このトピックでは、パフォーマンスの問題を診断するためにこれらの各メソッドを使用する方法について説明します。解決策を見つけることができる上、SharePoint のパフォーマンス向上に関する記事を使用して作業することができます問題の原因を理解したなら、 http://aka.ms/tune。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="4aee6-111">F12 ツール バーを使用して SharePoint Online のパフォーマンスを診断する</span><span class="sxs-lookup"><span data-stu-id="4aee6-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="4aee6-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="4aee6-112"></span></span>

<span data-ttu-id="4aee6-p102">この記事では、Internet Explorer 11 を使用します。他のブラウザーにある F12 開発者ツールのバージョンには、外観が若干異なりますが同様の機能があります。F12 開発者ツールの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="4aee6-116">F12 ツールの新機能</span><span class="sxs-lookup"><span data-stu-id="4aee6-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="4aee6-117">F12 開発者ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="4aee6-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="4aee6-118">開発者ツールを開くには、**F12** キーを押してから [Wi-Fi] アイコンをクリックします。 
</span><span class="sxs-lookup"><span data-stu-id="4aee6-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![F12 開発者ツールの Wi-Fi アイコンのスクリーンショット](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="4aee6-p103">**[ネットワーク]** タブで、緑色の再生ボタンをクリックすると、ページが読み込まれます。ユーザーが要求したページを取得するため、このツールは、ブラウザーが要求するファイルをすべて返します。次のスクリーン ショットは、このようなリストを示しています。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![ページ要求で返されるファイル リストのスクリーンショット。](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="4aee6-124">スクリーン ショットに示すように、右側でファイルのダウンロード時間も確認することができます。</span><span class="sxs-lookup"><span data-stu-id="4aee6-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![SharePoint から要求されたページを読み込むのにかかる時間を示す図](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="4aee6-p104">このように、ファイルの読み込みにかかった時間が視覚的に表示されます。緑色の線は、ブラウザーによってページが表示される準備ができたときを表します。これにより、サイトでページの読み込み時間が長い可能性があるさまざまなファイルをすばやく見ることができます。

</span><span class="sxs-lookup"><span data-stu-id="4aee6-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="4aee6-129">SharePoint Online のカスタマイズされていない基準計画の設定</span><span class="sxs-lookup"><span data-stu-id="4aee6-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="4aee6-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="4aee6-130"></span></span>

<span data-ttu-id="4aee6-p105">サイトのパフォーマンスの弱点を判断する最良の方法は、SharePoint Online に完全にアウト-の-標準のサイト コレクションを設定すること。この方法のカスタマイズが、ページ上で取得できるものを使用してサイトのすべてのさまざまな側面を比較できます。ビジネス ホーム ページの OneDrive は、すべてのカスタマイズがあると思われる別のサイト コレクションの良い例です。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="4aee6-134">SharePoint の応答ヘッダーの情報を表示する</span><span class="sxs-lookup"><span data-stu-id="4aee6-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="4aee6-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="4aee6-135"></span></span>

<span data-ttu-id="4aee6-p106">SharePoint Online と SharePoint Server 2013 では、各ファイルの応答ヘッダーで、ブラウザーに返信される情報にアクセスできます。パフォーマンスの問題を診断するのに最も役立つ 2 つの値は、SPRequestDuration と X-SharePointHealthScore です。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="4aee6-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="4aee6-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="4aee6-p107">サーバー上での要求の処理にかかる時間です。これは、要求が非常に高負荷でリソースを集中的に使用するかどうかを判断するのに役立ちます。ページを提供するためにどれくらいの操作をサーバーが実行しているかに関する最高の情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="4aee6-142">**X SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="4aee6-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="4aee6-p108">これは、サーバー、または、SharePoint のインスタンスが実行されている、CPU の使用率を示します。この番号範囲は 0 から 10 の 0 が、サーバがアイドル状態を示し、10 サーバーを示しますが、非常にビジー状態であります。常に 9 または 10 である HealthScore は、サーバーで継続的なパフォーマンスの問題を可能性があります。その他の任意の数は、そのサーバーが予期される範囲内で動作を示します。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="4aee6-147">**SharePoint の応答ヘッダーの情報を表示するには**</span><span class="sxs-lookup"><span data-stu-id="4aee6-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="4aee6-p109">F12 ツールがインストールされているがあることを確認します。ダウンロードしてこれらのツールをインストールする方法については、 [F12 ツールの新機能としては、何](https://go.microsoft.com/fwlink/p/?LinkId=522545)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="4aee6-150">F12 ツールの **[ネットワーク]** タブで、緑色の再生ボタンを押してページを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="4aee6-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="4aee6-151">このツールによって返される .aspx ファイルのいずれかをクリックしてから、**[詳細]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4aee6-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![応答ヘッダーの詳細を示しています](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="4aee6-153">**[応答ヘッダー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4aee6-153">Click **Response headers**.</span></span> 
    
    ![応答ヘッダーの URL を示す図](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="4aee6-155">SharePoint Online で何がパフォーマンスの問題を引き起こしているか</span><span class="sxs-lookup"><span data-stu-id="4aee6-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="4aee6-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="4aee6-156"></span></span>

<span data-ttu-id="4aee6-p110">記事[SharePoint Online のナビゲーション オプション](navigation-options-for-sharepoint-online.md)は、複雑な構造のナビゲーションがページをサーバー上の処理に時間がかかる原因であるかを決定する SPRequestDuration の値を使用する例を示します。(カスタマイズ) を行わなくても基準計画のサイトの値によって、いずれのファイルの読み込みに時間がかかってかどうかを決定することは。[SharePoint Online のナビゲーション オプション](navigation-options-for-sharepoint-online.md)の使用例は、メインの .aspx ファイルです。そのファイルには、ページの読み込みを実行している ASP.NET のコードの大部分が含まれています。によっては、サイト テンプレートを使用するこれは、start.aspx、home.aspx、default.aspx、または別の名前、ホーム ページをカスタマイズする場合。この番号では、ベースラインのサイトよりもかなり高く場合、は、パフォーマンスの問題の原因となっているページで起こっている複雑なものがあることがわかりますが。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="4aee6-p111">サイト固有の問題を特定したら、パフォーマンスの低下を引き起こしているものを見つけ出す推奨方法は、ページのカスタマイズなど、あり得る原因をすべて排除してから、1 つずつサイトに戻すことです。ページが正常に実行しているカスタマイズを十分に削除したら、特定のカスタマイズを 1 つずつ戻していきます。</span><span class="sxs-lookup"><span data-stu-id="4aee6-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="4aee6-p112">たとえば、非常に複雑なナビゲーションがある場合、ナビゲーションがサブサイトを表示しないように変更してみてください。その後、これが変化をもたらしたかどうかを開発者ツールで確認します。または、大量のコンテンツのロールアップがある場合は、ページから取り除き、状況が改善したか確認します。考えられる原因をすべて排除してから 1 つずつ追加すると、簡単にどの機能が最大の問題であるかを特定し、解決策を実行することができます。 
</span><span class="sxs-lookup"><span data-stu-id="4aee6-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

