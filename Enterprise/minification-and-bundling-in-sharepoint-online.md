---
title: SharePoint Online での縮小とバンドル
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: この資料では、SharePoint Online 内のページの読み込みにかかる時間を短縮して HTTP 要求の数を減らすために縮小し、Web の基礎とテクニックのバンドルを使用する方法について説明します。
ms.openlocfilehash: edc959e881b0f22b72fba64969e5984f30bce696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541499"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="5e454-103">SharePoint Online での縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="5e454-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="5e454-104">この資料では、SharePoint Online 内のページの読み込みにかかる時間を短縮して HTTP 要求の数を減らすために縮小し、Web の基礎とテクニックのバンドルを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e454-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="5e454-p101">Web サイトをカスタマイズする際、結局カスタマイズをサポートするために、サーバーに多数の余分なファイルが追加されてしまうことがあります。余分な JavaScript、CSS、および画像を追加すると、サーバーに対する HTTP 要求の数が増加し、結果として Web ページの表示にかかる時間が増加します。同種のファイルが複数ある場合、これらのファイルをバンドルすることにより、ファイルのダウンロードをさらに高速にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5e454-p101">When you customize your website you can end up adding a large number of extra files to the server to support the customization. Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page. If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="5e454-108">JavaScript、CSS ファイルでは、縮小、空白文字およびその他の必要のない文字を削除することによってファイルの合計サイズを小さくと呼ばれる手法を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5e454-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="5e454-109">Web Essentials による JavaScript ファイルと CSS ファイルの縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="5e454-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="5e454-110">Web Essentials などのサードパーティ製ソフトウェアを使用すると、CSS ファイルと JavaScript ファイルをバンドルできます。</span><span class="sxs-lookup"><span data-stu-id="5e454-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="5e454-p102">Web に関する重要事項は、サード ・ パーティ製、オープン ソース、コミュニティ ベースのプロジェクトです。ソフトウェアは、Visual Studio 2012 と 2013 の Visual Studio の拡張機能し、Microsoft ではサポートされていません。Web に関する重要事項をダウンロードするで web サイトを参照してください。 [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)。</span><span class="sxs-lookup"><span data-stu-id="5e454-p102">Web Essentials is a third-party, open-source, community-based project. The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft. To download Web Essentials, visit the website at [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="5e454-114">Web Essentials は、2 つの形式のバンドルを提供しています。</span><span class="sxs-lookup"><span data-stu-id="5e454-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="5e454-115">.bundle:CSS ファイルと JavaScript ファイル用</span><span class="sxs-lookup"><span data-stu-id="5e454-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="5e454-116">.sprite:画像用 (Visual Studio 2013 でのみ使用可能)</span><span class="sxs-lookup"><span data-stu-id="5e454-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="5e454-117">次のようなカスタム マスター ページの内部で参照されるブランド設定要素を持つ既存の機能がある場合は、Web Essentials を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5e454-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![ユーザー設定のマスター ページ内のブランド要素のスクリーンショット](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="5e454-119">**Web Essentials の TE000127218 と CSS のバンドルを作成するには**</span><span class="sxs-lookup"><span data-stu-id="5e454-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="5e454-120">Visual Studio のソリューション エクスプローラーで、バンドルに含めるファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e454-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="5e454-p103">選択したファイルを右クリックし、 **Web に関する重要事項**\>のコンテキスト メニューから**バンドル ファイルを作成する JavaScript** 。例えば：</span><span class="sxs-lookup"><span data-stu-id="5e454-p103">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu. For example:</span></span> 
    
    ![Web Essentials のメニュー オプションが表示されているスクリーンショット](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="5e454-124">JavaScript ファイルと CSS ファイルのバンドルの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="5e454-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="5e454-125">JavaScript と CSS のバンドルを作成すると、Web Essentials はレシピ ファイルという XML ファイルを作成します。レシピ ファイルでは、JavaScript ファイルと CSS ファイルとともに、その他の構成情報が特定されています。</span><span class="sxs-lookup"><span data-stu-id="5e454-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![JavaScript と CSS レシピ ファイルのスクリーンショット](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="5e454-p104">また、バンドル レシピで minify フラグが true に設定されている場合、ファイルのサイズが減少するとともに、一緒にバンドルされます。つまり、マスター ページで参照できる、縮小された新しいバージョンの JavaScript ファイルが作成されたということです。</span><span class="sxs-lookup"><span data-stu-id="5e454-p104">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together. This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![true に設定された minify フラグのスクリーンショット](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="5e454-130">Web サイトからページを読み込むとき、Internet Explorer 11 などの Web ブラウザーから、開発者向けのツールを使用して、サーバーに送信された要求の数と、各ファイルの読み込みにかかった時間を確認できます。</span><span class="sxs-lookup"><span data-stu-id="5e454-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="5e454-131">次の図は、縮小する前に JavaScript および CSS ファイルを読み込んだ結果です。</span><span class="sxs-lookup"><span data-stu-id="5e454-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![ダウンロードされている 80 のアイテムが表示されているスクリーンショット](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="5e454-133">CSS ファイルと JavaScript ファイルを一緒にバンドルした後、要求数は 74 に減少し、各ファイルは、元のファイルを個別にダウンロードするより若干長く時間がかかっただけです。</span><span class="sxs-lookup"><span data-stu-id="5e454-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![ダウンロードされている 74 のアイテムが表示されているスクリーンショット](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="5e454-135">バンドル後、JavaScript のバンドル ファイルは 815 KB から 365 KB と大幅に減少しています。</span><span class="sxs-lookup"><span data-stu-id="5e454-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![削減されたダウンロード サイズを示すスクリーンショット](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="5e454-137">イメージ スプライトを作成して画像をバンドルする</span><span class="sxs-lookup"><span data-stu-id="5e454-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="5e454-p105">JavaScript、CSS ファイルをバンドルする方法と同様より大きなスプライト シートに多数の小さいアイコンとその他の一般的なイメージを結合して個々 のイメージを表示するのには CSS を使用できます。各イメージをダウンロードするには、ユーザーの web ブラウザーはスプライト シートを 1 回ダウンロードし、し、それをローカル コンピューターにキャッシュします。ダウンロードし、web サーバーへのラウンド トリップの数を削減して、ページの読み込みのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="5e454-p105">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images. Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer. This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="5e454-141">**Web Essentials でイメージ スプライトを作成するには**</span><span class="sxs-lookup"><span data-stu-id="5e454-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="5e454-142">Visual Studio のソリューション エクスプローラーで、バンドルに含めるファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="5e454-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="5e454-p106">選択したファイルを右クリックし、 **Web に関する重要事項**\>のコンテキスト メニューから**画像のスプライトを作成**します。例えば：</span><span class="sxs-lookup"><span data-stu-id="5e454-p106">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu. For example:</span></span> 
    
    ![画像のスプライトを作成する方法を示したスクリーンショット](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="5e454-p107">スプライト ファイルを保存する場所を選択します。.sprite ファイルは、スプライトの設定とファイルについて記述された XML ファイルです。次の図は、スプライト PNG ファイルとその対応する .sprite XML ファイルの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="5e454-p107">Choose a location to save the sprite file. The .sprite file is an XML file that describes the settings and files in the sprite. The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![スプライト ファイルのスクリーンショット](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![スプライト XML ファイルのスクリーンショット](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

