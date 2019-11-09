---
title: SharePoint Online 最新版と従来版の発行サイト ページで iFrame を最適化する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/17/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online 最新版と従来版の発行サイト ページで iFrame のパフォーマンスを最適化する方法について説明します。
ms.openlocfilehash: 97848d28277f19e8984f1f08e90f07236fd5c85b
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078436"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="3e309-103">SharePoint Online 最新版と従来版の発行サイト ページで iFrame を最適化する</span><span class="sxs-lookup"><span data-stu-id="3e309-103">Optimize iFrames in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="3e309-104">iFrame は、動画やその他のメディアなどのリッチ コンテンツをプレビューするのに便利です。</span><span class="sxs-lookup"><span data-stu-id="3e309-104">iFrames can be useful for previewing rich content such as videos or other media.</span></span> <span data-ttu-id="3e309-105">ただし、iFrame には SharePoint サイト ページ内の別個のページが読み込まれるため、iFrame に読み込まれるコンテンツには大きな画像、動画、またはページの読み込み時間全体に影響する可能性のある他の要素が含まれていることがあり、ページで制御できません。</span><span class="sxs-lookup"><span data-stu-id="3e309-105">However, because iFrames load a separate page within the SharePoint site page, content loaded in the iFrame could contain large images, videos or other elements that can contribute to overall page load times and that you cannot control on the page.</span></span> <span data-ttu-id="3e309-106">この記事では、ページ内の iFrame がユーザーに発生する可能性のある待ち時間や、一般的な問題の解決方法を判断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e309-106">This article will help you understand how to determine how iFrames in your pages affect user perceived latency, and how to remediate common issues.</span></span>

>[!NOTE]
><span data-ttu-id="3e309-107">Sharepoint Online の最新版サイトでのパフォーマンスの詳細については、「[SharePoint のモダン エクスペリエンスにおけるパフォーマンス](https://docs.microsoft.com/sharepoint/modern-experience-performance)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e309-107">For more information about performance in SharePoint Online modern sites, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a><span data-ttu-id="3e309-108">SharePoint 用ページ診断ツールを使用して iFrame を使用する Web パーツを分析する</span><span class="sxs-lookup"><span data-stu-id="3e309-108">Use the Page Diagnostics for SharePoint tool to analyze web parts using iFrames</span></span>

<span data-ttu-id="3e309-109">**SharePoint 用ページ診断ツール**は、Chrome と [Microsoft Edge バージョン 77 以降](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8)のブラウザー拡張機能であり、SharePoint の最新版と従来版両方の発行サイト ページを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e309-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="3e309-110">このツールでは、定義されている一連のパフォーマンス条件に対するページのパフォーマンスを示す分析済みの各ページのレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3e309-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="3e309-111">SharePoint 用ページ診断ツールのインストール方法と詳細については、「[SharePoint Online 用ページ診断ツールを使用する](page-diagnostics-for-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e309-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="3e309-112">SharePoint のサイト ページを SharePoint 用ページ診断ツールを使用して分析すると、[_診断テスト_] ウィンドウに iFrame を含む Web パーツに関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3e309-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about web parts containing iFrames in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="3e309-113">ベースライン メトリックは、最新版ページと従来版ページで同じです。</span><span class="sxs-lookup"><span data-stu-id="3e309-113">The baseline metric is the same for modern and classic pages.</span></span>

<span data-ttu-id="3e309-114">考えられる結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3e309-114">Possible results include:</span></span>

- <span data-ttu-id="3e309-115">**要注意** (赤): このページには、iFrameを使用する Web パーツが **3 つ以上**含まれています</span><span class="sxs-lookup"><span data-stu-id="3e309-115">**Attention required** (red): The page contains **three or more** web parts using iFrames</span></span>
- <span data-ttu-id="3e309-116">**改善の余地あり** (黄): このページには、iFrameを使用する Web パーツが **1 つまたは 2 つ**含まれています</span><span class="sxs-lookup"><span data-stu-id="3e309-116">**Improvement opportunities** (yellow): The page contains **one or two** web parts using iFrames</span></span>
- <span data-ttu-id="3e309-117">**操作は不要** (緑): このページには iFrame を使用する Web パーツが含まれていません</span><span class="sxs-lookup"><span data-stu-id="3e309-117">**No action required** (green): The page contains no web parts using iFrames</span></span>

<span data-ttu-id="3e309-118">[**iFrame を使用する Web パーツが検出されました**] の結果が、結果の [**改善の余地あり**] セクションまたは [**要注意**] セクションのいずれかに表示されている場合は、結果をクリックして iframe が含まれる Web パーツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="3e309-118">If the **Web parts using iFrames detected** result appears in either the **Improvement opportunities** or **Attention required)** section of the results, you can click the result to see the web parts that contain iFrames.</span></span>

![ページ診断ツールの結果](media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a><span data-ttu-id="3e309-120">iFrame のパフォーマンスの問題を修復する</span><span class="sxs-lookup"><span data-stu-id="3e309-120">Remediate iFrame performance issues</span></span>

<span data-ttu-id="3e309-121">ページ診断ツールの [**iFrame を使用する Web パーツが検出されました**] の結果を使用して、iFrame を含み、ページの読み込み時間を遅らせる可能性のある Web パーツを特定します。</span><span class="sxs-lookup"><span data-stu-id="3e309-121">Use the **Web parts using iFrames detected** result in the Page Diagnostic tool to determine which web parts contain iFrames and may be contributing to slow page load times.</span></span>

<span data-ttu-id="3e309-122">iFrame は本来、javascript、CSS、framework の要素など、関連付けられているすべてのコンテンツを含む別個の外部ページを読み込むために遅く、サイト ページのオーバーヘッドが 2 倍以上になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3e309-122">iFrames are inherently slow because they load a separate external page including all associated content such as javascript, CSS and framework elements, potentially increasing the overhead of the site page by a factor of two or more.</span></span>

<span data-ttu-id="3e309-123">以下のガイドラインに従って、iFrame の使用を最適にしてください。</span><span class="sxs-lookup"><span data-stu-id="3e309-123">Follow the guidance below to ensure optimal use of iFrames.</span></span>

- <span data-ttu-id="3e309-124">プレビューのサイズが開始するには小さく、または非対話型の場合、可能であれば iFrame の代わりに画像を使用します。</span><span class="sxs-lookup"><span data-stu-id="3e309-124">When possible, use images instead of iFrames if the preview is small to begin with or non-interactive.</span></span>
- <span data-ttu-id="3e309-125">iFrame を使用する必要がある場合は、数値を最小限に抑えるか、ビューポートから移動させます。</span><span class="sxs-lookup"><span data-stu-id="3e309-125">If iFrames must be used, minimize the number and/or move them out of the viewport.</span></span>
- <span data-ttu-id="3e309-126">Word、Excel、PowerPoint などの埋め込まれた Office ファイルは対話型ですが、読み込みは遅くなります。</span><span class="sxs-lookup"><span data-stu-id="3e309-126">Embedded Office files like Word, Excel and PowerPoint are interactive, but are slow to load.</span></span> <span data-ttu-id="3e309-127">ドキュメント全体へのリンクが含まれている画像のサムネイルは、多くの場合パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="3e309-127">Image thumbnails with a link to the full document will often perform better.</span></span>
- <span data-ttu-id="3e309-128">埋め込みの YouTube ビデオと Twitter フィードにより、iFrame でのパフォーマンスは向上する傾向がありますが、こういった埋め込みは慎重に使用してください。</span><span class="sxs-lookup"><span data-stu-id="3e309-128">Embedded YouTube videos and Twitter feeds tend to perform better in iFrames, but use these kinds of embeds judiciously.</span></span>
- <span data-ttu-id="3e309-129">分離された Web パーツは当然例外ですが、ビューポートの数と配置は最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="3e309-129">Isolated web parts are a reasonable exception, but minimize their number and placement in the viewport.</span></span>
- <span data-ttu-id="3e309-130">iFrame がビューポートの外にある場合は、_IntersectionObserver_ を使用し、iFrame が表示されるまでレンダリングを遅らせることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3e309-130">If an iFrame is located out of the viewport, consider using an _IntersectionObserver_ to delay rendering the iFrame until it comes into view.</span></span>

<span data-ttu-id="3e309-131">ページの変更を行ってパフォーマンスの問題を修復する前に、分析結果のページの読み込み時間をメモします。</span><span class="sxs-lookup"><span data-stu-id="3e309-131">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="3e309-132">修正後にツールをもう一度実行して新しい結果がベースライン基準内にあるかどうかを確認し、新しいページ読み込み時間をチェックして改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e309-132">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![ページ読み込み時間の結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="3e309-134">ページ読み込み時間は、ネットワーク負荷、時間帯、その他の一時的な状態など、さまざまな要素によって異なります。</span><span class="sxs-lookup"><span data-stu-id="3e309-134">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="3e309-135">結果を平均化するために、変更の前後に数回に渡ってページ読み込み時間をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e309-135">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="3e309-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e309-136">Related topics</span></span>

[<span data-ttu-id="3e309-137">SharePoint Online のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="3e309-137">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="3e309-138">Office 365 のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="3e309-138">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="3e309-139">SharePoint のモダン エクスペリエンスにおけるパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="3e309-139">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance.md)
