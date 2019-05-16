---
title: SharePoint Online での縮小とバンドル
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: この記事では、Web Essentials での縮小とバンドルの手法を使用して、HTTP 要求の数を減らし、SharePoint Online でページを読み込むのにかかる時間を短縮する方法について説明します。
ms.openlocfilehash: d73bc6cc86ea1ea4ecba5395f22a20befdc64b13
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070263"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="b1e67-103">SharePoint Online での縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="b1e67-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="b1e67-104">この記事では、Web Essentials での縮小とバンドルの手法を使用して、HTTP 要求の数を減らし、SharePoint Online でページを読み込むのにかかる時間を短縮する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="b1e67-105">Web サイトをカスタマイズする場合は、カスタマイズをサポートするために、多数の追加ファイルをサーバーに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1e67-105">When you customize your website you can end up adding a large number of extra files to the server to support the customization.</span></span> <span data-ttu-id="b1e67-106">JavaScript、CSS、画像を追加すると、サーバーに対する HTTP 要求の数が増加し、web ページの表示にかかる時間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="b1e67-106">Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page.</span></span> <span data-ttu-id="b1e67-107">同じ種類のファイルが複数ある場合は、これらのファイルをバンドルして、これらのファイルをすばやくダウンロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="b1e67-107">If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="b1e67-108">JavaScript ファイルと CSS ファイルでは、必要のないスペースやその他の文字を削除することで、ファイルの合計サイズを小さくするために、縮小というアプローチを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b1e67-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="b1e67-109">Web Essentials を使用した JavaScript および CSS ファイルの縮小とバンドル</span><span class="sxs-lookup"><span data-stu-id="b1e67-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="b1e67-110">Web Essentials などのサードパーティ製ソフトウェアを使用して、CSS ファイルと JavaScript ファイルをバンドルできます。</span><span class="sxs-lookup"><span data-stu-id="b1e67-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="b1e67-111">Web エッセンシャルは、サードパーティのオープンソースのコミュニティベースのプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="b1e67-111">Web Essentials is a third-party, open-source, community-based project.</span></span> <span data-ttu-id="b1e67-112">このソフトウェアは、Visual Studio 2012 と Visual Studio 2013 の拡張機能であり、Microsoft ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="b1e67-112">The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft.</span></span> <span data-ttu-id="b1e67-113">Web Essentials をダウンロードするには、の[http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)web サイトにアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="b1e67-113">To download Web Essentials, visit the website at [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="b1e67-114">Web Essentials には、次の2つのバンドル形式が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b1e67-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="b1e67-115">. バンドル: CSS および JavaScript ファイル用</span><span class="sxs-lookup"><span data-stu-id="b1e67-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="b1e67-116">sprite: 画像の場合 (Visual Studio 2013 でのみ使用可能)</span><span class="sxs-lookup"><span data-stu-id="b1e67-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="b1e67-117">既存のフィーチャーに、次のようなカスタムマスターページの内部で参照されている一部のブランド要素がある場合は、Web Essentials を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b1e67-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![ユーザー設定のマスター ページ内のブランド要素のスクリーンショット](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="b1e67-119">**Web Essentials で TE000127218 および CSS バンドルを作成するには**</span><span class="sxs-lookup"><span data-stu-id="b1e67-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="b1e67-120">Visual Studio の [ソリューションエクスプローラー] で、バンドルに含めるファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="b1e67-121">選択したファイルを右クリックし、コンテキストメニューから [ **Web Essentials** \> **作成 JavaScript バンドルファイル**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-121">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu.</span></span> <span data-ttu-id="b1e67-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-122">For example:</span></span> 
    
    ![Web Essentials のメニュー オプションが表示されているスクリーンショット](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="b1e67-124">JavaScript ファイルと CSS ファイルをバンドルした結果の表示</span><span class="sxs-lookup"><span data-stu-id="b1e67-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="b1e67-125">JavaScript と CSS のバンドルを作成する場合、Web Essentials は、JavaScript ファイルと CSS ファイル、およびその他の構成情報を識別するレシピファイルと呼ばれる XML ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![JavaScript と CSS レシピ ファイルのスクリーンショット](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="b1e67-127">また、[バンドル] で [縮小フラグ] が true に設定されている場合は、ファイルがバンドルされるだけでなく、サイズが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="b1e67-127">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together.</span></span> <span data-ttu-id="b1e67-128">これは、マスターページで参照できる、新しい縮小版の JavaScript ファイルが作成されたことを意味します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-128">This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![true に設定された minify フラグのスクリーンショット](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="b1e67-130">Web サイトからページを読み込む場合、Internet Explorer 11 などの web ブラウザーの開発者ツールを使用して、サーバーに送信された要求の数と、各ファイルの読み込みにかかった時間を確認できます。</span><span class="sxs-lookup"><span data-stu-id="b1e67-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="b1e67-131">次の図は、縮小前に JavaScript および CSS ファイルを読み込んだ結果です。</span><span class="sxs-lookup"><span data-stu-id="b1e67-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![ダウンロードされている 80 のアイテムが表示されているスクリーンショット](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="b1e67-133">CSS ファイルと JavaScript ファイルを一緒にバンドルした後、要求数が74に落ち、各ファイルは、元のファイルを個別にダウンロードするよりわずかに時間がかかりすぎたことになります。</span><span class="sxs-lookup"><span data-stu-id="b1e67-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![ダウンロードされている 74 のアイテムが表示されているスクリーンショット](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="b1e67-135">バンドル後、JavaScript バンドルファイルは815KB から365KB に大幅に減少します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![削減されたダウンロード サイズを示すスクリーンショット](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="b1e67-137">イメージスプライトを作成してイメージをバンドルする</span><span class="sxs-lookup"><span data-stu-id="b1e67-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="b1e67-138">JavaScript ファイルと CSS ファイルをバンドルする方法と同様に、多くの小さいアイコンやその他の一般的な画像を大きなスプライトシートに結合し、CSS を使用して個々の画像を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="b1e67-138">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images.</span></span> <span data-ttu-id="b1e67-139">個々の画像をダウンロードするのではなく、ユーザーの web ブラウザーはスプライトシートを一度ダウンロードしてからローカルコンピューターにキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="b1e67-139">Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer.</span></span> <span data-ttu-id="b1e67-140">これにより、web サーバーへのダウンロード回数とラウンドトリップを減らすことで、ページの読み込みのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-140">This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="b1e67-141">**Web Essentials でイメージスプライトを作成するには**</span><span class="sxs-lookup"><span data-stu-id="b1e67-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="b1e67-142">Visual Studio の [ソリューションエクスプローラー] で、バンドルに含めるファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="b1e67-143">選択したファイルを右クリックし、コンテキストメニューから [ **Web Essentials** \> **Create image sprite** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-143">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu.</span></span> <span data-ttu-id="b1e67-144">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-144">For example:</span></span> 
    
    ![画像のスプライトを作成する方法を示したスクリーンショット](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="b1e67-146">スプライトファイルを保存する場所を選択します。</span><span class="sxs-lookup"><span data-stu-id="b1e67-146">Choose a location to save the sprite file.</span></span> <span data-ttu-id="b1e67-147">Sprite ファイルは、スプライト内の設定とファイルを記述する XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="b1e67-147">The .sprite file is an XML file that describes the settings and files in the sprite.</span></span> <span data-ttu-id="b1e67-148">次の図は、sprite PNG ファイルとそれに対応する sprite XML ファイルの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="b1e67-148">The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![スプライト ファイルのスクリーンショット](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![スプライト XML ファイルのスクリーンショット](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

