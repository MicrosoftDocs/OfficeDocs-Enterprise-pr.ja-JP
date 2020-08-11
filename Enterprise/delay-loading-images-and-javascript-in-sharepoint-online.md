---
title: SharePoint Online での画像の読み込み遅延と JavaScript
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: JavaScript を使用して、画像および重要でない JavaScript の読み込みを遅延させることで、SharePoint Online ページの読み込み時間を短縮する方法について説明します。
ms.openlocfilehash: 72eabed2dd940bb07ece44bbc0dbc9d72e426a67
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605753"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="a5c9e-103">SharePoint Online での画像の読み込み遅延と JavaScript</span><span class="sxs-lookup"><span data-stu-id="a5c9e-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="a5c9e-104">この記事では、JavaScript を使用して画像の読み込みを遅延させることにより、SharePoint Online ページの読み込み時間を短縮する方法と、ページが読み込まれるまで重要でない JavaScript の読み込みを待機する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span>
  
<span data-ttu-id="a5c9e-105">SharePoint Online では、画像がページの読み込み速度に悪影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-105">Images can negatively affect page load speeds on SharePoint Online.</span></span> <span data-ttu-id="a5c9e-106">既定では、ほとんどのモダンインターネットブラウザーは、HTML ページの読み込み時に画像を事前に取得します。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-106">By default, most modern Internet browsers pre-fetch images when loading an HTML page.</span></span> <span data-ttu-id="a5c9e-107">このため、ユーザーが下にスクロールするまで画像が画面に表示されない場合は、ページが不必要に読み込まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-107">This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down.</span></span> <span data-ttu-id="a5c9e-108">画像は、ページの可視部分を読み込むことをブラウザーにブロックできます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-108">The images can block the browser from loading the visible part of the page.</span></span> <span data-ttu-id="a5c9e-109">この問題を回避するには、まず、JavaScript を使用して画像の読み込みをスキップします。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-109">To work around this problem, you can use JavaScript to skip loading the images first.</span></span> <span data-ttu-id="a5c9e-110">また、必須ではない JavaScript を読み込むと、SharePoint ページでダウンロード時間が長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-110">Also, loading non-essential JavaScript can slow download times on your SharePoint pages too.</span></span> <span data-ttu-id="a5c9e-111">このトピックでは、SharePoint Online の JavaScript を使用してページの読み込み時間を向上させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-111">This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span>
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="a5c9e-112">JavaScript を使用して SharePoint Online ページで画像の読み込みを遅延することで、ページの読み込み時間を短縮する</span><span class="sxs-lookup"><span data-stu-id="a5c9e-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="a5c9e-113">JavaScript を使用して、web ブラウザーが画像を事前に取得できないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-113">You can use JavaScript to prevent a web browser from pre-fetching images.</span></span> <span data-ttu-id="a5c9e-114">これにより、ドキュメント全体のレンダリングが高速化されます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-114">This speeds up overall document rendering.</span></span> <span data-ttu-id="a5c9e-115">これを行うには、タグから src 属性の値を削除し、次のよう \<img\> な data 属性のファイルへのパスに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-115">To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src.</span></span> <span data-ttu-id="a5c9e-116">例:</span><span class="sxs-lookup"><span data-stu-id="a5c9e-116">For example:</span></span>
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="a5c9e-117">この方法を使用すると、ブラウザーはすぐに画像をダウンロードしません。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-117">By using this method, the browser doesn't download the images immediately.</span></span> <span data-ttu-id="a5c9e-118">イメージがビューポートに既に含まれている場合、JavaScript はブラウザーに、データ属性から URL を取得して src 属性の値として挿入するよう指示します。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-118">If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute.</span></span> <span data-ttu-id="a5c9e-119">画像は、ユーザーがスクロールして表示されるときにのみ読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-119">The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="a5c9e-120">すべての操作を行うには、JavaScript を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-120">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="a5c9e-121">テキストファイルで、 **Iselementinviewport ()** 関数を定義し、要素がブラウザーのユーザーに表示される部分にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-121">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span>
  
```javascript
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
  );
}
```

<span data-ttu-id="a5c9e-122">次に、 **loadItemsInView ()** 関数で**Iselementinviewport ()** を使用します。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-122">Next, use **isElementInViewport()** in the **loadItemsInView()** function.</span></span> <span data-ttu-id="a5c9e-123">**LoadItemsInView ()** 関数は、データソース属性の値がユーザーに表示されるブラウザーの部分にある場合、その値を持つすべての画像を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-123">The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user.</span></span> <span data-ttu-id="a5c9e-124">テキストファイルに次の関数を追加します。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-124">Add the following function to the text file:</span></span>
  
```javascript
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

<span data-ttu-id="a5c9e-125">最後に、次の例に示されているように、 **loadItemsInView ()** をウィンドウから呼び出し**ます。**</span><span class="sxs-lookup"><span data-stu-id="a5c9e-125">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example.</span></span> <span data-ttu-id="a5c9e-126">これにより、ユーザーが必要とするときに、ビューポートに含まれるすべてのイメージが読み込まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-126">This ensures that any images that are in the viewport are loaded as the user needs them, but not before.</span></span> <span data-ttu-id="a5c9e-127">次の内容をテキストファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-127">Add the following to the text file:</span></span>
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="a5c9e-128">SharePoint Online では、#s4 workspace タグの scroll イベントに次の関数を関連付ける必要があり \<div\> ます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-128">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag.</span></span> <span data-ttu-id="a5c9e-129">これは、リボンがページの上部に常に接続されていることを確認するために、ウィンドウイベントがオーバーライドされるためです。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-129">This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="a5c9e-130">テキストファイルを拡張子 .js の JavaScript ファイルとして保存します (例: delayLoadImages.js)。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-130">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="a5c9e-131">delayLoadImages.js の記述が終了したら、ファイルの内容を SharePoint Online のマスターページに追加できます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-131">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online.</span></span> <span data-ttu-id="a5c9e-132">これを行うには、マスターページのヘッダーにスクリプトリンクを追加します。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-132">You do this by adding a script link to the header in the master page.</span></span> <span data-ttu-id="a5c9e-133">マスターページでは、そのマスターページレイアウトを使用する SharePoint Online サイトのすべてのページに JavaScript が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-133">Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout.</span></span> <span data-ttu-id="a5c9e-134">または、サイトの1つのページでのみこれを使用する場合は、スクリプトエディター Web パーツを使用して JavaScript をページに埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-134">Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page.</span></span> <span data-ttu-id="a5c9e-135">詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-135">See these topics for more information:</span></span>
  
- <span data-ttu-id="a5c9e-136">[[方法]: SharePoint Server 2013 のサイトにマスター ページを適用する](https://go.microsoft.com/fwlink/p/?LinkId=525627)</span><span class="sxs-lookup"><span data-stu-id="a5c9e-136">[How to: Apply a master page to a site in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)</span></span>

- <span data-ttu-id="a5c9e-137">[[方法]: SharePoint 2013 でページ レイアウトを作成する方法](https://go.microsoft.com/fwlink/p/?LinkId=525628)</span><span class="sxs-lookup"><span data-stu-id="a5c9e-137">[How to: Create a page layout in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)</span></span>

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a><span data-ttu-id="a5c9e-138">例: SharePoint Online のマスターページから JavaScript delayLoadImages.js ファイルを参照する</span><span class="sxs-lookup"><span data-stu-id="a5c9e-138">Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online</span></span>
  
<span data-ttu-id="a5c9e-139">これを動作させるには、マスターページで jQuery を参照する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-139">In order for this to work, you also need to reference jQuery in the master page.</span></span> <span data-ttu-id="a5c9e-140">次の例では、最初のページの読み込みで、読み込まれたイメージは1つだけですが、ページ上にはさらにいくつかのページがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-140">In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![ページ上に読み込まれる 1 つのイメージが表示されたスクリーンショット](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="a5c9e-142">次のスクリーンショットは、スクロール後にダウンロードされた残りの画像を示しています。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-142">The following screenshot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![ページ上に読み込まれる複数のイメージが表示されたスクリーンショット](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="a5c9e-144">JavaScript を使用して画像の読み込みを延期することは、パフォーマンスを向上させる効果的な手法になる可能性があります。ただし、この手法がパブリック web サイトに適用されている場合、検索エンジンは、通常の形式の画像をクロールするのと同じ方法で画像をクロールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-144">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image.</span></span> <span data-ttu-id="a5c9e-145">これは、ページが読み込まれるまで画像自体のメタデータが実際には存在しないため、検索エンジンのランキングに影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-145">This can affect rankings on search engines because metadata on the image itself is not really there until the page loads.</span></span> <span data-ttu-id="a5c9e-146">検索エンジンのクローラーは HTML のみを読み取るため、画像はページ上のコンテンツとして表示されません。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-146">Search engine crawlers only read the HTML and therefore will not see the images as content on the page.</span></span> <span data-ttu-id="a5c9e-147">画像は、検索結果内のページのランク付けに使用する要因の1つです。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-147">Images are one of the factors used to rank pages in search results.</span></span> <span data-ttu-id="a5c9e-148">これを回避する方法の1つは、画像の導入テキストを使用することです。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-148">One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="a5c9e-149">GitHub コードサンプル: JavaScript を挿入してパフォーマンスを向上させる</span><span class="sxs-lookup"><span data-stu-id="a5c9e-149">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="a5c9e-150">GitHub で提供されている[JavaScript インジェクション](https://go.microsoft.com/fwlink/p/?LinkId=524759)に関する記事やコードサンプルを見逃さないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a5c9e-150">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a5c9e-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5c9e-151">See also</span></span>

[<span data-ttu-id="a5c9e-152">Office 2013 でサポートされているブラウザーおよびエンタープライズ向け Microsoft 365 アプリ</span><span class="sxs-lookup"><span data-stu-id="a5c9e-152">Supported browsers in Office 2013 and Microsoft 365 Apps for enterprise</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
<span data-ttu-id="a5c9e-153">[[方法]: SharePoint Server 2013 のサイトにマスター ページを適用する](https://go.microsoft.com/fwlink/p/?LinkId=525627)</span><span class="sxs-lookup"><span data-stu-id="a5c9e-153">[How to: Apply a master page to a site in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)</span></span>
  
<span data-ttu-id="a5c9e-154">[[方法]: SharePoint 2013 でページ レイアウトを作成する方法](https://go.microsoft.com/fwlink/p/?LinkId=525628)</span><span class="sxs-lookup"><span data-stu-id="a5c9e-154">[How to: Create a page layout in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)</span></span>
