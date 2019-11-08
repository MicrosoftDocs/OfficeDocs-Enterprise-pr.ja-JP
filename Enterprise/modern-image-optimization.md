---
title: SharePoint Online のモダン サイト ページで画像を最適化する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online のモダン サイト ページで画像を最適化する方法について説明します。
ms.openlocfilehash: dafa31f95babfe0389fd77bf4a25b5a346cf3474
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032272"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="00183-103">SharePoint Online のモダン サイト ページで画像を最適化する</span><span class="sxs-lookup"><span data-stu-id="00183-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="00183-104">この記事では SharePoint Online のモダン サイト ページで画像を最適化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="00183-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="00183-105">クラシック発行サイトで画像を最適化する方法の詳細については、「[SharePoint Online の画像の最適化](image-optimization-for-sharepoint-online.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00183-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="00183-106">Sharepoint Online の最新ポータルでのパフォーマンスの詳細については、「[SharePoint のモダン エクスペリエンスにおけるパフォーマンス](https://docs.microsoft.com/sharepoint/modern-experience-performance)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00183-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="00183-107">SharePoint 用ページ診断ツールを使用して画像の最適化を分析する</span><span class="sxs-lookup"><span data-stu-id="00183-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="00183-108">**SharePoint 用ページ診断ツール**は、Chrome および [バージョン 77 以降の Microsoft Edge](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) 用のブラウザー拡張機能で、これを使用して SharePoint のモダン発行サイト ページおよびクラシック発行サイト ページの両方を分析できます。</span><span class="sxs-lookup"><span data-stu-id="00183-108">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="00183-109">このツールでは、定義されている一連のパフォーマンス条件に対するページのパフォーマンスを示す分析済みの各ページのレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="00183-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="00183-110">SharePoint 用ページ診断ツールのインストール方法および詳細情報については、「[SharePoint Online 用ページ診断ツールを使用する](page-diagnostics-for-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00183-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="00183-111">SharePoint のモダン サイトを SharePoint 用ページ診断ツールを使用して分析すると、サイズの大きな画像に関する情報が [_診断テスト_] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="00183-111">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="00183-112">考えられる結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="00183-112">Possible results include:</span></span>

- <span data-ttu-id="00183-113">**注意が必要です** (赤): このページには大きさが 300KB 以上の画像が **1 つ以上**含まれています</span><span class="sxs-lookup"><span data-stu-id="00183-113">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="00183-114">**対処は不要です** (緑): このページには大きさが 300KB 以上の画像は含まれていません</span><span class="sxs-lookup"><span data-stu-id="00183-114">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="00183-115">結果の [**注意が必要です**] セクションに [**大きな画像が検出されました**] という結果が表示された場合は、結果をクリックすると追加の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="00183-115">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![ページ診断ツールの結果](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="00183-117">大きな画像に関する問題を修復する</span><span class="sxs-lookup"><span data-stu-id="00183-117">Remediate large image issues</span></span>

<span data-ttu-id="00183-118">大きさが 300KB 以上の画像がページに含まれている場合は、[**大きな画像が検出されました**] という結果を選択してサイズが大きすぎる画像を確認します。</span><span class="sxs-lookup"><span data-stu-id="00183-118">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="00183-119">SharePoint Online のモダン ページでは、画像の表示とサイズはブラウザー ウィンドウのサイズとクライアント モニターの解像度に応じて自動的に決定されます。</span><span class="sxs-lookup"><span data-stu-id="00183-119">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="00183-120">画像は、SharePoint Online にアップロードする前に、 Web での使用のために必ず最適化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00183-120">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="00183-121">サイズが非常に大きい画像のサイズと解像度が自動的に縮小されます。これにより、予期しない表示特性が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00183-121">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="00183-122">パフォーマンスの問題を修復するためにページを修正する前に、分析結果のページ読み込み時間をメモしてください。</span><span class="sxs-lookup"><span data-stu-id="00183-122">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="00183-123">修正後にツールをもう一度実行して新しい結果がベースライン基準内にあるかどうかを確認し、新しいページ読み込み時間をチェックして改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="00183-123">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![ページ読み込み時間の結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="00183-125">ページ読み込み時間は、ネットワーク負荷、時間帯、その他の一時的な状態など、さまざまな要素によって異なります。</span><span class="sxs-lookup"><span data-stu-id="00183-125">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="00183-126">結果を平均化するために、変更の前後に数回に渡ってページ読み込み時間をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="00183-126">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="00183-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="00183-127">Related topics</span></span>

[<span data-ttu-id="00183-128">SharePoint Online のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="00183-128">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="00183-129">Office 365 のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="00183-129">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="00183-130">SharePoint のモダン エクスペリエンスにおけるパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="00183-130">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="00183-131">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="00183-131">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="00183-132">SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用</span><span class="sxs-lookup"><span data-stu-id="00183-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
