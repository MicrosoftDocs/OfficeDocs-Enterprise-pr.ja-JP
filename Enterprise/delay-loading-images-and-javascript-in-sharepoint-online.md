---
title: SharePoint Online での画像の読み込み遅延と JavaScript
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: この資料では、イメージの読み込みを遅延するのには JavaScript を使用してページの読み込みの後までの不要な JavaScript を読み込まないようにする、SharePoint Online のページの読み込み時間を小さく方法について説明します。
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541749"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="0756e-103">SharePoint Online での画像の読み込み遅延と JavaScript</span><span class="sxs-lookup"><span data-stu-id="0756e-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="0756e-104">この資料では、イメージの読み込みを遅延するのには JavaScript を使用してページの読み込みの後までの不要な JavaScript を読み込まないようにする、SharePoint Online のページの読み込み時間を小さく方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0756e-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="0756e-p101">画像は、SharePoint Online のページの読み込み速度に悪影響を与えることがあります。既定では、最新のインターネット ブラウザーは、HTML ページの読み込み時に画像をプリフェッチします。これにより、ユーザーが下にスクロールするまで画像が画面に表示されない場合、ページ読み込みに不必要に時間がかかることがあります。画像は、ブラウザーによるページの表示部分の読み込みを妨げる可能性があります。この問題を解決するには、JavaScript を使用して、画像を最初に読み込むことを省略します。また、重要でない JavaScript を読み込んだ場合も、SharePoint ページの読み込み時間が長くなることがあります。このトピックでは、SharePoint Online で JavaScript を使ってページの読み込み時間を短縮するいくつかの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0756e-p101">Images can negatively affect page load speeds on SharePoint Online. By default, most modern Internet browsers pre-fetch images when loading an HTML page. This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down. The images can block the browser from loading the visible part of the page. To work around this problem, you can use JavaScript to skip loading the images first. Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too. This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="0756e-112">JavaScript を使用して SharePoint Online のページで画像の読み込みを遅らせてページの読み込み時間を短縮する</span><span class="sxs-lookup"><span data-stu-id="0756e-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="0756e-p102">フェッチ済みの画像から web ブラウザーをしないようにするのには、JavaScript を使用できます。これは、全体のドキュメントのレンダリングが速くなります。Src 属性の値を削除するには、 \<img\>タグを付けるし、次のように、データ属性内のファイルへのパスに置き換えます。 データ ソースです。例えば：</span><span class="sxs-lookup"><span data-stu-id="0756e-p102">You can use JavaScript to prevent a web browser from pre-fetching images. This speeds up overall document rendering. To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="0756e-p103">このメソッドを使用すると、ブラウザーはすぐに画像をダウンロードしません。イメージがビューポート内に既に場合は、JavaScript はデータの属性から URL を取得し、src 属性の値として挿入するようブラウザーに指示します。イメージをユーザーがスクロールのみ読み込むし、表示になります。</span><span class="sxs-lookup"><span data-stu-id="0756e-p103">By using this method, the browser doesn't download the images immediately. If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute. The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="0756e-119">すべてこれの発生、する必要があります JavaScript を使用します。</span><span class="sxs-lookup"><span data-stu-id="0756e-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="0756e-120">テキスト ファイルに **isElementInViewport()** 関数を定義し、要素がブラウザーのユーザーに表示される部分にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0756e-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
```
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

<span data-ttu-id="0756e-p104">続いて、**loadItemsInView()** 関数で **isElementInViewport()** を使用します。**LoadItemsInView()** 関数は、画像がブラウザーのユーザーに表示される部分にある場合、data-src 属性の値を持つ画像をすべて読み込みます。テキスト ファイルに次の関数を追加します。</span><span class="sxs-lookup"><span data-stu-id="0756e-p104">Next, use **isElementInViewport()** in the **loadItemsInView()** function. The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user. Add the following function to the text file:</span></span> 
  
```
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

<span data-ttu-id="0756e-p105">最後に、次の例に示すように、**loadItemsInView()** を **window.onscroll()** 内から呼び出します。これにより、ビューポートにあるすべての画像が、ユーザーが必要なときに読み込まれますが、事前に読み込まれることはありません。テキスト ファイルに以下を追加します。</span><span class="sxs-lookup"><span data-stu-id="0756e-p105">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example. This ensures that any images that are in the viewport are loaded as the user needs them, but not before. Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="0756e-p106">SharePoint online では、スクロール イベント #s4 のワークスペース上に次の関数をアタッチする必要があります\<div\>タグです。ウィンドウ イベントは、リボンは、ページの上部に接続されていることを確認するためにオーバーライドされるためです。</span><span class="sxs-lookup"><span data-stu-id="0756e-p106">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag. This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="0756e-129">テキスト ファイルに拡張子 .js を付けて JavaScript ファイルとして保存します (例: delayLoadImages.js)。</span><span class="sxs-lookup"><span data-stu-id="0756e-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="0756e-p107">DelayLoadImages.js の書き込みが終了したら、SharePoint Online でマスター ページに、ファイルの内容を追加できます。マスター ページのヘッダーにスクリプトのリンクを追加するこれを行います。マスター ページが、JavaScript は、そのマスター ページ レイアウトを使用する、SharePoint Online サイト内のすべてのページに適用されます。または、サイトの 1 つのページでのみ使用する場合は、JavaScript をページに埋め込むには、スクリプト エディター Web パーツを使用します。詳細については、これらのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0756e-p107">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online. You do this by adding a script link to the header in the master page. Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout. Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page. See these topics for more information:</span></span>
  
- [<span data-ttu-id="0756e-135">方法: SharePoint 2013 でサイトにマスター ページを適用</span><span class="sxs-lookup"><span data-stu-id="0756e-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- <span data-ttu-id="0756e-136">[[方法]: SharePoint 2013 でページ レイアウトを作成する方法](https://go.microsoft.com/fwlink/p/?LinkId=525628)</span><span class="sxs-lookup"><span data-stu-id="0756e-136">[How to: Create a page layout in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)</span></span>
    
 <span data-ttu-id="0756e-137">**例:SharePoint Online でマスター ページから JavaScript の delayLoadImages.js ファイルを参照する**</span><span class="sxs-lookup"><span data-stu-id="0756e-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="0756e-p108">これが機能するためには、マスター ページで jQuery を参照する必要もあります。次の例では、最初のページの読み込みで、1 つの画像のみが読み込まれていますが、このページにはさらに複数の画像があることが分かります。</span><span class="sxs-lookup"><span data-stu-id="0756e-p108">In order for this to work, you also need to reference jQuery in the master page. In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![ページ上に読み込まれる 1 つのイメージが表示されたスクリーンショット](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="0756e-141">次のスクリーン ショットは、スクロール後にダウンロードされ、表示された残りの画像を示しています。</span><span class="sxs-lookup"><span data-stu-id="0756e-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![ページ上に読み込まれる複数のイメージが表示されたスクリーンショット](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="0756e-p109">JavaScript を使用して画像の読み込みを遅らせることは、パフォーマンスの向上に有効な手法ですが、この手法を公開用の Web サイトに適用する場合、検索エンジンは、通常の形式の画像をクロールするように画像をクロールすることはできません。このことは、ページが読み込まれるまで画像自体のメタデータが実際にないため、検索エンジンのランキングに影響を与えます。検索エンジンのクローラーは HTML のみを読み取るため、画像をページのコンテンツとみなしません。画像は、検索結果でページのランキングに使用される要素の 1 つです。この問題を回避する方法の 1 つは、画像に導入部のテキストを使用することです。</span><span class="sxs-lookup"><span data-stu-id="0756e-p109">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image. This can affect rankings on search engines because metadata on the image itself is not really there until the page loads. Search engine crawlers only read the HTML and therefore will not see the images as content on the page. Images are one of the factors used to rank pages in search results. One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="0756e-148">GitHub コードのサンプル:JavaScript を挿入してパフォーマンスを向上</span><span class="sxs-lookup"><span data-stu-id="0756e-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="0756e-149">GitHub 上で提供される[JavaScript インジェクション](https://go.microsoft.com/fwlink/p/?LinkId=524759)の資料とコード サンプルをお見逃しなきます。</span><span class="sxs-lookup"><span data-stu-id="0756e-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="0756e-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="0756e-150">See also</span></span>

[<span data-ttu-id="0756e-151">Office 2013 および Office 365 用リソースでサポートされているブラウザー</span><span class="sxs-lookup"><span data-stu-id="0756e-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="0756e-152">方法: SharePoint 2013 でサイトにマスター ページを適用</span><span class="sxs-lookup"><span data-stu-id="0756e-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
<span data-ttu-id="0756e-153">[[方法]: SharePoint 2013 でページ レイアウトを作成する方法](https://go.microsoft.com/fwlink/p/?LinkId=525628)</span><span class="sxs-lookup"><span data-stu-id="0756e-153">[How to: Create a page layout in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)</span></span>

