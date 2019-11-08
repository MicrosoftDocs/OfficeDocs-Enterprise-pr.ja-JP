---
title: SharePoint Online の最新のサイト ページでページのウエイトを最適化する
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
description: SharePoint Online の最新のサイト ページでページのウエイトを最適化する方法について説明します。
ms.openlocfilehash: 3079298781116c2664217f87715303c99e4d26b6
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032252"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="fe86f-103">SharePoint Online の最新のサイト ページでページのウエイトを最適化する</span><span class="sxs-lookup"><span data-stu-id="fe86f-103">Optimize page weight in SharePoint Online modern site pages</span></span>

<span data-ttu-id="fe86f-104">SharePoint Online の最新のサイト ページには、ページのコンテンツをレンダリングするのに必要なシリアル番号が含まれています。これには、ナビゲーション バーやコマンド バーと、ページの枠組みを構成するその他の HTML コードの下のコンテンツ領域にある画像、テキスト、オブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fe86f-104">SharePoint Online modern site pages contain serialized code that is required to render page content of the page, including images, text, objects in the content area underneath navigation/command bars and other HTML code that forms the framework of the page.</span></span> <span data-ttu-id="fe86f-105">ページのウエイトはこの HTML コードの測定値であり、ページの読み込み時間が最適になるように制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe86f-105">Page weight is a measurement of this HTML code, and should be limited to ensure optimal page load times.</span></span>

<span data-ttu-id="fe86f-106">この記事では、最新のサイト ページでページのウエイトを減らす方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fe86f-106">This article will help you understand how to reduce page weight in your modern site pages.</span></span>

>[!NOTE]
><span data-ttu-id="fe86f-107">Sharepoint Online の最新ポータルでのパフォーマンスの詳細については、「[SharePoint のモダン エクスペリエンスにおけるパフォーマンス](https://docs.microsoft.com/sharepoint/modern-experience-performance)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe86f-107">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a><span data-ttu-id="fe86f-108">SharePoint 用ページ診断ツールを使用してページのウエイトを分析する</span><span class="sxs-lookup"><span data-stu-id="fe86f-108">Use the Page Diagnostics for SharePoint tool to analyze page weight</span></span>

<span data-ttu-id="fe86f-109">**SharePoint 用ページ診断ツール**は、Chrome と [Microsoft Edge バージョン 77 以降](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)のブラウザー拡張機能であり、SharePoint の最新版と従来版両方の発行サイト ページを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fe86f-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="fe86f-110">このツールでは、定義されている一連のパフォーマンス条件に対するページのパフォーマンスを示す分析済みの各ページのレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fe86f-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="fe86f-111">SharePoint 用ページ診断ツールのインストール方法と詳細については、「[SharePoint Online 用ページ診断ツールを使用する](page-diagnostics-for-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe86f-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="fe86f-112">SharePoint のサイト ページを SharePoint 用ページ診断ツールを使用して分析すると、[_診断テスト_] ウィンドウの [**500 KB 未満のページのウエイト**] 結果にページに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe86f-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about page in the **Page weight under 500KB** result of the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="fe86f-113">結果は、ページのウエイトがベースライン値を下回る場合は緑色で、ページのウエイトが基準値を超える場合は赤色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe86f-113">The result will appear in green if the page weight is under the baseline value, and red if the page weight exceeds the baseline value.</span></span>

<span data-ttu-id="fe86f-114">考えられる結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fe86f-114">Possible results include:</span></span>

- <span data-ttu-id="fe86f-115">**要注意** (赤): ページのウエイトが 500 KB を超えています</span><span class="sxs-lookup"><span data-stu-id="fe86f-115">**Attention required** (red): Page weight exceeds 500KB</span></span>
- <span data-ttu-id="fe86f-116">**操作は不要** (緑): ページのウエイトが 500 KB を下回っています</span><span class="sxs-lookup"><span data-stu-id="fe86f-116">**No action required** (green): Page weight is under 500KB</span></span>

<span data-ttu-id="fe86f-117">[**500 KB 未満のページのウエイト**] の結果が [**要注意**] セクションに表示された場合、結果をクリックして詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="fe86f-117">If the **Page weight under 500KB** result appears in the **Attention required** section, you can click the result for details.</span></span>

![SharePoint 結果への要求](media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a><span data-ttu-id="fe86f-119">ページのウエイトの問題を修復する</span><span class="sxs-lookup"><span data-stu-id="fe86f-119">Remediate page weight issues</span></span>

<span data-ttu-id="fe86f-120">ページのウエイトが 500 KB を超える場合は、Web パーツの数を減らし、適度にページのコンテンツを制限することで、ページの読み込み時間全体を改善できます。</span><span class="sxs-lookup"><span data-stu-id="fe86f-120">If page weight exceeds 500KB, you can improve overall page load time by reducing the number of web parts and limiting page content to an appropriate degree.</span></span>

<span data-ttu-id="fe86f-121">ページのウエイトを減らすための一般的なガイダンスは以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fe86f-121">General guidance for reducing page weight includes:</span></span>

- <span data-ttu-id="fe86f-122">ページのコンテンツを妥当な量まで制限し、関連するコンテンツには複数のページを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe86f-122">Limit the page content to a reasonable amount and use multiple pages for related content.</span></span>
- <span data-ttu-id="fe86f-123">大きなプロパティ バッグがある Web パーツの使用を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="fe86f-123">Minimize the use of web parts that have large property bags.</span></span>
- <span data-ttu-id="fe86f-124">可能な場合は、非対話型ロールアップ ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe86f-124">Use non-interactive rollup views when possible.</span></span>
- <span data-ttu-id="fe86f-125">画像のサイズを最適化するには、画像のサイズを適度に変更し、圧縮された画像形式を使用して、CDN からダウンロードできるようにします。</span><span class="sxs-lookup"><span data-stu-id="fe86f-125">Optimize image sizes by sizing images appropriately, using compressed image formats and ensuring that they are downloaded from a CDN.</span></span>

<span data-ttu-id="fe86f-126">ページのウエイトを制限に関する追加のガイダンスについては、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe86f-126">You can find additional guidance for limiting page weight in the following article:</span></span>

- [<span data-ttu-id="fe86f-127">SharePoint でページ パフォーマンスを最適化する</span><span class="sxs-lookup"><span data-stu-id="fe86f-127">Optimize page performance in SharePoint</span></span>](https://docs.microsoft.com/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

<span data-ttu-id="fe86f-128">ページの変更を行ってパフォーマンスの問題を修復する前に、分析結果のページの読み込み時間をメモします。</span><span class="sxs-lookup"><span data-stu-id="fe86f-128">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="fe86f-129">修正後にツールをもう一度実行して新しい結果がベースライン基準内にあるかどうかを確認し、新しいページ読み込み時間をチェックして改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="fe86f-129">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![ページ読み込み時間の結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="fe86f-131">ページ読み込み時間は、ネットワーク負荷、時間帯、その他の一時的な状態など、さまざまな要素によって異なります。</span><span class="sxs-lookup"><span data-stu-id="fe86f-131">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="fe86f-132">結果を平均化するために、変更の前後に数回に渡ってページ読み込み時間をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe86f-132">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="fe86f-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe86f-133">Related topics</span></span>

[<span data-ttu-id="fe86f-134">SharePoint Online のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="fe86f-134">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="fe86f-135">Office 365 のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="fe86f-135">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="fe86f-136">SharePoint のモダン エクスペリエンスにおけるパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="fe86f-136">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="fe86f-137">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="fe86f-137">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="fe86f-138">SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用</span><span class="sxs-lookup"><span data-stu-id="fe86f-138">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
