---
title: SharePoint Online のモダン サイト ページでユーザー設定の拡張機能を最適化する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: SharePoint Online のモダン サイト ページでユーザー設定の拡張機能のパフォーマンスを最適化する方法について説明します。
ms.openlocfilehash: dbf0c3cba009a102bf37dd65f14e8cb882303cfe
ms.sourcegitcommit: bb122479c3a2757c0a5adde6c9f0c77c75ab3951
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "46548859"
---
# <a name="optimize-custom-extension-performance-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="d3e90-103">SharePoint Online のモダン サイト ページでユーザー設定の拡張機能のパフォーマンスを最適化する</span><span class="sxs-lookup"><span data-stu-id="d3e90-103">Optimize custom extension performance in SharePoint Online modern site pages</span></span>

<span data-ttu-id="d3e90-104">この記事では、ユーザー設定の拡張機能がユーザーに発生する可能性のある待ち時間や、一般的な問題の解決方法を判断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-104">This article will help you understand how to determine how custom extensions affect user perceived latency, and how to remediate common issues.</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-custom-extensions"></a><span data-ttu-id="d3e90-105">SharePoint 用ページ診断ツールを使用してユーザー設定の拡張機能を分析する</span><span class="sxs-lookup"><span data-stu-id="d3e90-105">Use the Page Diagnostics for SharePoint tool to analyze custom extensions</span></span>

<span data-ttu-id="d3e90-106">SharePoint 用ページ診断ツールは、新しい Microsoft Edge (https://www.microsoft.com/edge) と Chrome のブラウザー拡張機能であり、SharePoint Online の最新ポータルと従来の発行サイト ページの両方を分析します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-106">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="d3e90-107">このツールでは、定義されている一連のパフォーマンス条件に対するページのパフォーマンスを示す分析済みの各ページのレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-107">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="d3e90-108">SharePoint 用ページ診断ツールのインストール方法と詳細については、「[SharePoint Online 用ページ診断ツールを使用する](page-diagnostics-for-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-108">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="d3e90-109">ページ診断ツールは SharePoint Online でのみ機能し、SharePoint システム ページでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d3e90-109">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="d3e90-110">SharePoint のサイト ページを SharePoint 用ページ診断ツールを使用して分析すると、ベースライン メトリックを超えているユーザー設定の拡張機能に関する情報が、 _[診断テスト]_ ウィンドウ内の **拡張機能がページの読み込み時間に影響を与えています**および/または**使用する機能拡張が多すぎる** という結果に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-110">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about custom extensions that exceed the baseline metric in the **Extensions are impacting load time** and/or the **Too many extensions used** result in the _Diagnostic tests_ pane</span></span> 

<span data-ttu-id="d3e90-111">考えられる結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d3e90-111">Possible results include:</span></span>

- <span data-ttu-id="d3e90-112">**要注意** (赤): _ユーザー設定の_拡張機能で、読み込み時間が **1** 秒を超えるもの。</span><span class="sxs-lookup"><span data-stu-id="d3e90-112">**Attention required** (red): Any _custom_ extension that takes longer than **one** second to load.</span></span> <span data-ttu-id="d3e90-113">合計読み込み時間がテスト結果に表示される際は、モジュールの読み込みおよび初期化に分けて表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-113">Total load time as displayed in test results is broken down by module load and init.</span></span> <span data-ttu-id="d3e90-114">さらに、ページの拡張機能が多すぎる場合は、ページの読み込み時間に影響する可能性があります。また、ページで**7** つ以上の拡張機能が使用されている場合は、これが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-114">Additionally, if there are too many extensions on a page they can impact the page load time and this will be highlighted if **seven** or more extensions are used on the page.</span></span>
- <span data-ttu-id="d3e90-115">**改善の機会** (黄) **5** 個以上の拡張機能が使用されている場合、このセクションでは、[要確認] として強調表示される 7 個以上の拡張機能が使用されるまで、警告として強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-115">**Improvement Opportunities** (yellow) If **five** or more extensions are used they will be highlighted in this section as a warning until seven or more are used which will then be highlighted as Attention Required.</span></span>
- <span data-ttu-id="d3e90-116">**操作不要** (緑): 読み込み時間が 1 秒を超える拡張機能はありません。</span><span class="sxs-lookup"><span data-stu-id="d3e90-116">**No action required** (green): No extension is taking longer than one second to load.</span></span>

<span data-ttu-id="d3e90-117">拡張機能がページの読み込み時間に影響を与えている、またはページ上に多くの機能拡張がある場合は、結果の **[要確認]** セクションにその結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-117">If an extension is impacting page load time or there are too many extsnions on the page, the result appears in the **Attention required** section of the results.</span></span> <span data-ttu-id="d3e90-118">その結果をクリックして、どの機能拡張の読み込みが遅いのか、またはどの強調表示されている機能拡張が多すぎるのかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-118">Click the result to see details about which extension is loading slowly or too many extensions has been highlighted.</span></span> <span data-ttu-id="d3e90-119">今後の SharePoint 用ページ診断ツールの更新プログラムでは分析ルールが更新される可能性があるため、常に最新バージョンのツールを使用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-119">Future updates to the Page Diagnostics for SharePoint tool may include updates to analysis rules, so please ensure you always have the latest version of the tool.</span></span>

![ページ読み込み時間の結果](media/page-diagnostics-for-spo/pagediag-extensions-load-time.png)

<span data-ttu-id="d3e90-121">結果に含まれる情報は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d3e90-121">Information available in the results includes:</span></span>

- <span data-ttu-id="d3e90-122">**[名前と ID]** には、ページで拡張機能を見つけるのに役立つ識別情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-122">**Name and ID** shows identifying information that can help you find the extension on the page</span></span>
- <span data-ttu-id="d3e90-123">**[合計]** には、拡張機能が初期化されて読み込まれるまでの合計時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-123">**Total** shows the total time for the extension to initialize and load</span></span>
- <span data-ttu-id="d3e90-124">**[モジュールの読み込み]** には、拡張機能を取得して読み込むのにかかる時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-124">**Module Load** shows the time taken to fetch and load the extension</span></span>
- <span data-ttu-id="d3e90-125">**[初期化]** には、拡張機能の初期化にかかる時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-125">**Init** shows the time taken for the extension to initialize</span></span>

<span data-ttu-id="d3e90-126">この情報は、デザイナーと開発者が問題のトラブルシューティングを行えるように提供されています。</span><span class="sxs-lookup"><span data-stu-id="d3e90-126">This information is provided to help designers and developers troubleshoot issues.</span></span> <span data-ttu-id="d3e90-127">この情報は、設計開発チームに提供するようにします。</span><span class="sxs-lookup"><span data-stu-id="d3e90-127">This information should be provided to your design and development team.</span></span>

## <a name="overview-of-extensions"></a><span data-ttu-id="d3e90-128">拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="d3e90-128">Overview of extensions</span></span>

<span data-ttu-id="d3e90-129">SharePoint Framework (SPFx) 拡張機能は、SharePoint のユーザー エクスペリエンスを拡張するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-129">SharePoint Framework (SPFx) Extensions can be used to extend the SharePoint user experience.</span></span> <span data-ttu-id="d3e90-130">SharePoint Framework 拡張機能を使用すると、通知領域、ツールバー、リスト データ ビューなど、SharePoint エクスペリエンスのより多くのファセットをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-130">With SharePoint Framework Extensions, you can customize more facets of the SharePoint experience, including notification areas, toolbars, and list data views.</span></span>

<span data-ttu-id="d3e90-131">拡張機能は、必要な作業を行うために CPU やネットワーク リソースを消費するので、SharePoint ページのパフォーマンスに悪い影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d3e90-131">Extensions can have a bad influence on the performance of a SharePoint page as it also takes CPU and network resources to do required work.</span></span>

<span data-ttu-id="d3e90-132">拡張機能には次の 4 種類があります。</span><span class="sxs-lookup"><span data-stu-id="d3e90-132">There are four types of extensions:</span></span>

- <span data-ttu-id="d3e90-133">**アプリケーション カスタマイザー**は、ページにスクリプトを追加したり、既知の HTML 要素のプレースホルダーにアクセスしてカスタム レンダリングで拡張したりします。</span><span class="sxs-lookup"><span data-stu-id="d3e90-133">**Application Customizers** adds scripts to the page, and accesses well-known HTML element placeholders and extends them with custom renderings.</span></span>
- <span data-ttu-id="d3e90-134">**フィールド カスタマイザー**は、変更したビューをリスト内のフィールドのデータに提供します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-134">**Field Customizers** provides modified views to data for fields within a list.</span></span>
- <span data-ttu-id="d3e90-135">**コマンド セット**は、SharePoint コマンド表面を拡張して新しいアクションを追加し、動作を実装するために使用できるクライアント側のコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-135">**Command Sets** extend the SharePoint command surfaces to add new actions, and provides client-side code that you can use to implement behaviors.</span></span>
- <span data-ttu-id="d3e90-136">**検索クエリ修飾子 (プレビューのみ)** は、検索クエリが実行される直前に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-136">**Search Query Modifier (preview only)** are invoked just before the search query is executed.</span></span>

## <a name="remediate-extension-performance-issues"></a><span data-ttu-id="d3e90-137">拡張機能のパフォーマンスの問題を修復する</span><span class="sxs-lookup"><span data-stu-id="d3e90-137">Remediate extension performance issues</span></span>

<span data-ttu-id="d3e90-138">**[Extensions are impacting load time]** (拡張機能がページの読み込み時間に影響を与えています) という結果に表示されるパフォーマンスの問題を特定して修復するには、このセクションのガイダンスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-138">Follow the guidance in this section to identify and remediate performance issues with extensions listed in the **Extensions are impacting page load time** results.</span></span>

>[!NOTE]
><span data-ttu-id="d3e90-139">アプリケーション カスタマイザーは、ページのライフサイクルの中で初期の段階で実行される場合があり、そのページの他の拡張機能のパフォーマンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d3e90-139">Application customizers may be executed in the early stage during the lifecycle of a page and it may influence the performance of other extensions on the page.</span></span>

<span data-ttu-id="d3e90-140">ページ診断ツールの監査結果は、パフォーマンスへの潜在的な影響を特定するため、拡張機能を実行する 2 つの段階が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-140">The audit results in the Page Diagnostic Tool will display two stages of executing an extension in order to help identify the potential performance impact.</span></span>

- <span data-ttu-id="d3e90-141">**モジュールの読み込み**は、拡張機能の読み込みにかかる時間です。これは拡張機能の大きさの影響を受けるため、必要なライブラリのみを拡張機能にまとめたり、より軽いライブラリを選択したりすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d3e90-141">**Module load** is how long it takes to load the extension, which is impacted by the size of an extension so it is a good idea to only bundle the necessary libraries in the extension and to also choose lighter libraries.</span></span>
- <span data-ttu-id="d3e90-142">**初期化**は、拡張機能を初期化する時間です。拡張機能の開発者は、初期化の段階で拡張機能が不要な作業を行っていないか、またはコマンドを実行しすぎていないかを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3e90-142">**Init** is the initialization time of the extension and extension developers should consider whether the extension is doing unnecessary work or executing too many commands during the initializing stage.</span></span>

<span data-ttu-id="d3e90-143">ページ作成者は、監査結果を利用して、ページに含まれる拡張機能が多すぎないかどうかを確認することもできます。拡張機能が多すぎると、ページのパフォーマンスに悪影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-143">Page authors can also use the audit result to see whether a page has too many extensions as too many extensions will negatively impact the performance of a page.</span></span>

- <span data-ttu-id="d3e90-144">**拡張機能の大きさと依存関係**</span><span class="sxs-lookup"><span data-stu-id="d3e90-144">**Extension size and dependencies**</span></span>
  - <span data-ttu-id="d3e90-145">静的リソースの最適なダウンロードを行うには、Office 365 CDN を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3e90-145">Use of the Office 365 CDN is required for optimal static resource download.</span></span> <span data-ttu-id="d3e90-146">_js/css_ ファイルの配信元として、パブリックの CDN 配信元が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="d3e90-146">Public CDN origins are preferable for _js/css_ files.</span></span> <span data-ttu-id="d3e90-147">Office 365 CDN の使用に関する詳細については、「[SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用](use-office-365-cdn-with-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-147">For more information about using the Office 365 CDN, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="d3e90-148">SharePoint Framework (SPFx) に付属する _React_ や _Fabric imports_ などのフレームワークを再利用してください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-148">Reuse frameworks like _React_ and _Fabric imports_ that come as part of the SharePoint Framework (SPFx).</span></span> <span data-ttu-id="d3e90-149">詳細については、「[SharePoint Framework の概要](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-149">For more information, see [Overview of the SharePoint Framework](https://docs.microsoft.com/sharepoint/dev/spfx/sharepoint-framework-overview).</span></span>
  - <span data-ttu-id="d3e90-150">最新バージョンの SharePoint Framework を使用するようにし、新しいバージョンがリリースされた場合にはアップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-150">Ensure that you are using the latest version of the SharePoint Framework, and upgrade to new versions as they become available.</span></span>
- <span data-ttu-id="d3e90-151">**データの取得/キャッシュ**</span><span class="sxs-lookup"><span data-stu-id="d3e90-151">**Data fetching/caching**</span></span>
  - <span data-ttu-id="d3e90-152">表示するデータを取得するのに拡張機能が追加のサーバー呼び出しに依存している場合は、それらのサーバー API が高速で、(_localStorage_ や _IndexDB_ (大規模なセットの場合) などを使用する) クライアント側キャッシュが実装されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-152">If the extension relies on extra server calls to fetch data for display, ensure those server APIs are fast and/or implement client side caching (such as using _localStorage_ or _IndexDB_ for larger sets).</span></span>
  - <span data-ttu-id="d3e90-153">重要なデータを表示するために複数の呼び出しが必要な場合は、サーバーへの呼び出しのバッチ処理または複数の要求を 1 つの呼び出しに統合する他の方法を検討してください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-153">If multiple calls are required to render critical data, consider batching on the server or other methods of consolidating requests to a single call.</span></span>
  - <span data-ttu-id="d3e90-154">または、データの一部の要素で低速の API が要求され、これらの要素が初期レンダリングには重要でない場合、これらを重要なデータのレンダリング後に実行される別の呼び出しに切り離します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-154">Alternatively, if some elements of data require a slower API, but are not critical to initial rendering, decouple these to a separate call that is executed after critical data is rendered.</span></span>
  - <span data-ttu-id="d3e90-155">複数のパーツが同じデータを使用している場合、共通データ層を使用して呼び出しの重複を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="d3e90-155">If multiple parts use the same data, utilize a common data layer to avoid duplicate calls.</span></span>
- <span data-ttu-id="d3e90-156">**レンダリング時間**</span><span class="sxs-lookup"><span data-stu-id="d3e90-156">**Rendering time**</span></span>
  - <span data-ttu-id="d3e90-157">不必要な大きなアセットのダウンロードを防ぐために、画像やビデオなどのメディアのソースは、コンテナー、デバイス、およびネットワークの制限に合わせてサイズを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3e90-157">Any media sources like images and videos should be sized to the limits of the container, device and/or network to avoid downloading unnecessary large assets.</span></span> <span data-ttu-id="d3e90-158">コンテンツの依存関係の詳細については、「[SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用](use-office-365-cdn-with-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-158">For more information about content dependencies, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="d3e90-159">再フロー、複雑な CSS ルール、複雑なアニメーションにつながる API 呼び出しを行わないようにします。</span><span class="sxs-lookup"><span data-stu-id="d3e90-159">Avoid API calls that cause re-flow, complex CSS rules or complicated animations.</span></span> <span data-ttu-id="d3e90-160">詳細については、「[Minimizing browser reflow
(ブラウザーの再フローを最小化する)](https://developers.google.com/speed/docs/insights/browser-reflow)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-160">For more information, see [Minimizing browser reflow](https://developers.google.com/speed/docs/insights/browser-reflow).</span></span>
  - <span data-ttu-id="d3e90-161">連結されている長時間実行タスクを使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="d3e90-161">Avoid use of chained long running tasks.</span></span> <span data-ttu-id="d3e90-162">代わりに、長時間実行タスクは個別のキューに分割します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-162">Instead, break long running tasks apart into separate queues.</span></span> <span data-ttu-id="d3e90-163">詳細については、「[Optimize JavaScript Execution (JavaScript の実行を最適化する)](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-163">For more information, see [Optimize JavaScript Execution](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).</span></span>
  - <span data-ttu-id="d3e90-164">フレームの飛びや途切れ (_ジャンク_とも呼ばれます) を防ぐために、メディアの非同期的なレンダリング用に、対応するスペースを予約します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-164">Reserve corresponding space for asynchronously rendering media or visual elements to avoid skipped frames and stuttering (also known as _jank_).</span></span>
  - <span data-ttu-id="d3e90-165">レンダリンで使用される機能が特定のブラウザーでサポートされていない場合は、ポリフィルを読み込むか、依存コードの実行を除外します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-165">If a certain browser doesn't support a feature used in rendering, either load a polyfill or exclude running dependent code.</span></span> <span data-ttu-id="d3e90-166">その機能が重要ではない場合は、メモリ リークが発生しないようにイベント ハンドラーなどのリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-166">If the feature is not critical, dispose resources such as event handlers to avoid memory leaks.</span></span>

<span data-ttu-id="d3e90-167">パフォーマンスの問題を修復するためにページを変更する前に、分析結果に表示されるページ読み込み時間をメモしてください。</span><span class="sxs-lookup"><span data-stu-id="d3e90-167">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="d3e90-168">修正後にツールをもう一度実行して新しい結果がベースライン基準内にあるかどうかを確認し、新しいページ読み込み時間をチェックして改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3e90-168">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![ページ読み込み時間の結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="d3e90-170">ページ読み込み時間は、ネットワーク負荷、時間帯、その他の一時的な状態など、さまざまな要素によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d3e90-170">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="d3e90-171">結果を平均化するために、変更の前後に数回に渡ってページ読み込み時間をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3e90-171">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="d3e90-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3e90-172">Related topics</span></span>

[<span data-ttu-id="d3e90-173">SharePoint Online のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="d3e90-173">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="d3e90-174">Office 365 のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="d3e90-174">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="d3e90-175">SharePoint のモダン エクスペリエンスにおけるパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="d3e90-175">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="d3e90-176">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="d3e90-176">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="d3e90-177">SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用</span><span class="sxs-lookup"><span data-stu-id="d3e90-177">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
