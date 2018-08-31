---
title: SharePoint Online のイメージの最適化
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: レンディションとスプライトを使用して、SharePoint Online の web サイト上のイメージのパフォーマンスを向上させる方法について説明します。
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541534"
---
# <a name="image-optimization-for-sharepoint-online"></a><span data-ttu-id="10035-103">SharePoint Online のイメージの最適化</span><span class="sxs-lookup"><span data-stu-id="10035-103">Image optimization for SharePoint Online</span></span>

<span data-ttu-id="10035-p101">Web ページの読み込み速度は、画像、HTML、JavaScript、および CSS を含むページのレンダリングに必要なすべてのコンポーネントの合計サイズに依存します。イメージより魅力的なサイトを作成する優れた方法ですが、そのサイズがパフォーマンスに影響を与えます。圧縮とサイズを変更すると、スプライトを使用すると、イメージを最適化するには、非常に大きいイメージの効果を補うことができます。SharePoint のイメージのレンディションを使用すると、1 つの大きな画像をアップロードし、再読み込みするのではなく再利用することができるイメージのセクションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="10035-p101">The loading speed of a webpage depends on the combined size of all the components required to render the page including images, HTML, JavaScript, and CSS. Images are a great way to make your site more appealing, but their size can affect performance. By optimizing your images with compression and resizing, and using sprites, you can offset the effects of very large images. Using SharePoint image renditions, you can upload a single large image, and display sections of the image allowing it to be reused rather than reloaded.</span></span>
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a><span data-ttu-id="10035-108">スプライトを使用して SharePoint Online での画像読み込みを高速化する</span><span class="sxs-lookup"><span data-stu-id="10035-108">Using sprites to speed up image loading in SharePoint Online</span></span>

|||
|:-----|:-----|
| <span data-ttu-id="10035-p102">画像をスプライトには、多くの小さな画像が含まれています。CSS を使用して絶対位置を使用してページの特定の部分に表示する複合イメージの一部を選択します。基本的には、複数のイメージをロードするのではなくページの周りに 1 つの画像を移動しをエンド ・ ユーザーにそのイメージの一部をスプライトのイメージの必要な部分が表示されている小さなウィンドウで表示されるようにします。SharePoint Online は、スプライトの spcommon.png で、さまざまなアイコンを表示するのにスプライトを使用します。</span><span class="sxs-lookup"><span data-stu-id="10035-p102">An image sprite contains many smaller images. Using CSS you select a part of the composite image to display on a particular part of the page with absolute positioning. Basically, you move a single image around the page instead of loading multiple images, and make a small part of that image visible through a small window where the required part of the sprite image is shown to the end user. SharePoint Online uses sprites to display its various icons in the sprite spcommon.png.</span></span>  <br/>  <span data-ttu-id="10035-113">内容はここで説明します。</span><span class="sxs-lookup"><span data-stu-id="10035-113">What's covered here:</span></span>  <br/>  <span data-ttu-id="10035-114">画像の圧縮</span><span class="sxs-lookup"><span data-stu-id="10035-114">Image compression</span></span>  <br/>  <span data-ttu-id="10035-115">イメージの最適化</span><span class="sxs-lookup"><span data-stu-id="10035-115">Image optimization</span></span>  <br/>  <span data-ttu-id="10035-116">SharePoint のイメージのレンディション</span><span class="sxs-lookup"><span data-stu-id="10035-116">SharePoint image renditions</span></span>  <br/> |![Spcommon のスクリーン ショット](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
<span data-ttu-id="10035-p103">キャッシュされますし、そのイメージを再利用するいくつかの代わりに 1 つだけのイメージをダウンロードするために、パフォーマンスを向上させることができます。イメージ状態が持続しないキャッシュされた、複数のイメージの代わりに単一のイメージのことで、たとえこのメソッドは、ページの読み込み時間が短縮されるサーバーに HTTP 要求の合計数を減少します。これは、実際にイメージのバンドルの形式です。これは、非常に便利な手法場合イメージを変更しない非常に多くの場合、たとえば、アイコン、前述した SharePoint の使用例に示すようにします。[Web に関する重要事項](http://vswebessentials.com/)、Microsoft Visual Studio でこれを簡単に達成するためにサード ・ パーティ製、オープン ソース、コミュニティ ベースのプロジェクトを使用する方法を実行できます。詳細については、[縮小し SharePoint Online のバンドル](https://go.microsoft.com/fwlink/?LinkId=708698)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10035-p103">This can increase performance because you download only one image instead of several and then cache and reuse that image. Even if the image does not remain cached, by having a single image instead of multiple images, this method reduces the total number of HTTP requests to the server which will reduce page loading times. This is really a form of image bundling. This is a very useful technique if the images are not changing very often, for example, icons, as shown in the SharePoint example provided above. You can how to use [Web Essentials](http://vswebessentials.com/), a third-party, open-source, community-based project to achieve this easily in Microsoft Visual Studio. For more information, see [Minification and bundling in SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).</span></span>
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a><span data-ttu-id="10035-124">SharePoint で画像の圧縮および最適化を使用してページの読み込みを高速化する</span><span class="sxs-lookup"><span data-stu-id="10035-124">Using image compression and optimization to speed up page loading in SharePoint</span></span>

<span data-ttu-id="10035-p104">画像の圧縮および最適化とは、サイトで使用する画像のファイル サイズを減らすことです。多くの場合、画像のサイズを小さくする最適な手法は、画像のサイズをサイトで表示できる最大サイズに変更することです。表示されるより大きい画像を持つことは意味を成しません。画像エディターを使用して、必ず画像を適切なサイズにすることは、ページのサイズをすばやく簡単に小さくする方法です。</span><span class="sxs-lookup"><span data-stu-id="10035-p104">Image compression and optimization is about reducing the file size of the images you use on your site. Often, the best technique to reduce the size of an image is to resize the image to the maximum dimensions that it will be viewed on the site. There is no sense in having an image larger than it will ever be viewed. Making sure images are of the correct dimensions using an image editor is a quick and easy way to reduce the size of your page.</span></span>
  
<span data-ttu-id="10035-p105">イメージが適切なサイズではこれらの画像の圧縮を最適化するためには次の手順です。圧縮と最適化、フォト ギャラリーなど、サードパーティ製のツールを使用するさまざまなツールがあります。圧縮するキーは、エンド ・ ユーザーを認識できるような品質を保ったまま可能な限りファイルサイズを小さくこと。でも見栄えよくすることを確認するのには高解像度のディスプレイで圧縮されたファイルをテストすることを確認します。</span><span class="sxs-lookup"><span data-stu-id="10035-p105">Once images are the right size, the next step is to optimize the compression of these images. There are various tools available to use for compression and optimization, including Photo Gallery and third-party tools. The key to compression is to reduce the file size as much as possible without losing any discernible quality for end users. Make sure you test your compressed files on a high-definition display to ensure they will still look good.</span></span>
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a><span data-ttu-id="10035-133">SharePoint のイメージ レンディションを使用してページのダウンロードを高速化する</span><span class="sxs-lookup"><span data-stu-id="10035-133">Speed up page downloads by using SharePoint image renditions</span></span>

<span data-ttu-id="10035-p106">イメージのレンディションは、SharePoint online を使用すると、定義済みの画像のサイズに基づいて画像の異なるバージョンを提供する機能です。イメージのユーザーが生成したコンテンツまたはサイトの CSS で幅や高さなどの画像の寸法を修正するとき、これは特に重要です。CSS でイメージが固定されて、フル解像度イメージは読み込まれたままです。ここではイメージのレンディションを使用してファイル サイズを削減できます。</span><span class="sxs-lookup"><span data-stu-id="10035-p106">Image renditions are a feature in SharePoint Online that allows you to serve up different versions of images based on pre-defined image dimensions. This is especially important when there is user-generated image content or the image dimensions such as width and height are fixed by the CSS on the site. Even if an image is fixed by CSS, the full resolution image is still loaded. In this case the file size can be reduced by using image renditions.</span></span>
  
> [!NOTE]
> <span data-ttu-id="10035-p107">レンディションを SharePoint で使用できるは、発行が有効な場合だけです。[設定] での公開を有効にすることができます\>サイトの設定\>サイトの機能を管理する\>SharePoint サーバーの公開。それ以外の場合、オプションは表示されません。</span><span class="sxs-lookup"><span data-stu-id="10035-p107">Renditions are only available for SharePoint when publishing is enabled. You can enable publishing under Settings \> Site Settings \> Manage site features \> SharePoint Server Publishing. The option will not appear otherwise.</span></span> 
  
<span data-ttu-id="10035-p108">幅または高さのいずれかを定義する最小サイズにしてから画像のサイズを変更することで、イメージ レンディションのサイズ変更が機能します。そうすることで、ロックされた縦横比に基づいてもう一方のサイズが自動的に変更されます。既定では、残りのサイズによって中央から画像がトリミングされます。たとえば、横 100px 縦 50px のレンディションを定義し、元の画像が横 1000px 縦 800px の場合、800px のサイズは 50px になり、1000px のサイズ (現在は 62.5px) は画像の中央からトリミングされます。</span><span class="sxs-lookup"><span data-stu-id="10035-p108">The image rendition resizing works by taking the smallest dimension you define, either width or height, and then resizing the image so that the other dimension is automatically resized based on the locked aspect ratio. By default, it will crop the image from the center by the remaining dimensions. For example, if you define a rendition of 100px wide and 50px high and your original image is 1000px wide and 800px high, it will be resized so that the 800px dimension is now 50px and the 1000px dimension (now 62.5px) is cropped from the center of the image.</span></span>
  
<span data-ttu-id="10035-p109">手順は比較的簡単ですが、レンディションを使用する画像では、画像を追加する前にレンディションが SharePoint サイト上にある必要があります。加えて、SharePoint Server Publishing Infrastructure (サイト コレクション レベル) と SharePoint Server Publishing (サイト レベル) 機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="10035-p109">The steps are relatively simple but for images to use the renditions, the renditions need to be on the SharePoint site before you add the images. In addition, you also need to have the SharePoint Server Publishing Infrastructure (Site Collection Level) and SharePoint Server Publishing (Site Level) features turned on.</span></span>
  
 <span data-ttu-id="10035-146">**ページの読み込みを高速化するのには、イメージのレンディションを追加します。**</span><span class="sxs-lookup"><span data-stu-id="10035-146">**Add an image rendition to speed up page loading**</span></span>
  
1. <span data-ttu-id="10035-147">この手順を実行しているユーザー アカウントに、少なくとも、サイト コレクションのトップレベル サイトには、デザイン アクセスを許可し、サイトの web ページに発行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="10035-147">Verify that the user account that is performing this procedure has, at minimum, Design permissions to the top-level site of the site collection, and that the site is being published to a webpage.</span></span>
    
2. <span data-ttu-id="10035-148">Web ブラウザーで、発行サイト コレクションのトップレベルのサイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="10035-148">In a web browser, go to the top-level site of the publishing site collection.</span></span>
    
3. <span data-ttu-id="10035-149">**[設定]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="10035-149">Choose the **Settings** icon.</span></span> 
    
4. <span data-ttu-id="10035-150">**[サイトの設定]** ページの **[ルック アンド フィール]** セクションに、組み込みのイメージ レンディションがあることが分かります。</span><span class="sxs-lookup"><span data-stu-id="10035-150">On the **Site Settings** page, in the **Look and Feel** section, you will see the built-in image renditions.</span></span> 
    
    <span data-ttu-id="10035-151">そのまま使用できるレンディションを使用するか、**[イメージ レンディション]** を選択して新規作成します。</span><span class="sxs-lookup"><span data-stu-id="10035-151">You can use the out of the box renditions or choose **Image Renditions** to create a new one.</span></span> 
    
    ![レンディションのイメージのスクリーン ショット](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. <span data-ttu-id="10035-153">**[イメージ レンディション]** ページで、**[新しい項目の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="10035-153">On the **Image Renditions** page, choose **Add new item**.</span></span>
    
    ![[新しい項目の追加] のスクリーンショット](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. <span data-ttu-id="10035-155">**[新しいイメージ レンディション]** ページの **[名前]** ボックスで、表示の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="10035-155">On the **New Image Rendition** page, in the **Name** box, enter a name for the rendition.</span></span> 
    
7. <span data-ttu-id="10035-156">**[幅]** と **[高さ]** テキスト ボックスに、レンディションの幅と高さをピクセル単位で入力してから、**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10035-156">In the **Width** and **Height** text boxes, enter the width and height, in pixels, of the rendition, and then choose **Save**.</span></span>
    
    ![イメージ表示名のスクリーンショット](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a><span data-ttu-id="10035-158">SharePoint におけるイメージ レンディションのカスタム トリミング</span><span class="sxs-lookup"><span data-stu-id="10035-158">Custom cropping with image renditions in SharePoint</span></span>

<span data-ttu-id="10035-p110">既定では、画像の中心から、イメージのレンディションが生成されます。個々 のイメージのイメージのレンディションを調整するには、使用するイメージの一部をトリミングします。レンディションごと、個々 の画像をトリミングすることができます。画像のトリミングは、ページの各レンディションのイメージのバージョンを作成する SharePoint の blob キャッシュを使用して、読み込みが速くなります。画像だけサイズを変更した 1 回と、複数回のエンド ・ ユーザーに提供する準備が整いますので、この方法はサーバーの負荷が減少します。イメージのレンディションをトリミングする方法の詳細については、[トリミング画像のレンディション](https://go.microsoft.com/fwlink/p/?LinkId=525626)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10035-p110">By default, an image rendition is generated from the center of the image. You can adjust the image rendition for individual images by cropping the portion of the image that you want to use. You can crop the images on an individual basis, per rendition. Cropping the images speeds up page loading by using SharePoint's blob cache to create a version of the image for each rendition. This way the server load is reduced because the image is only resized once and is then ready to serve to end users multiple times. For more information on how to crop an image rendition, see [Crop an image rendition](https://go.microsoft.com/fwlink/p/?LinkId=525626).</span></span>
  

