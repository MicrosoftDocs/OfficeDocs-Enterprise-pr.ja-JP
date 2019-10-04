---
title: SharePoint Online のモダン サイト ページで Web パーツのパフォーマンスを最適化する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: Admin
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
description: SharePoint Online のモダン サイト ページで Web パーツのパフォーマンスを最適化する方法について説明します。
ms.openlocfilehash: 2fabfa44e29ac70d587ec2b6b95943a7c65632aa
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028244"
---
# <a name="optimize-web-part-performance-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="dbdd4-103">SharePoint Online のモダン サイト ページで Web パーツのパフォーマンスを最適化する</span><span class="sxs-lookup"><span data-stu-id="dbdd4-103">Optimize web part performance in SharePoint Online modern site pages</span></span>

>[!TIP]
><span data-ttu-id="dbdd4-104">SharePoint サイト ページで iFrame を最適化する方法の詳細については、「[SharePoint Online 最新版と従来版の発行サイト ページで iFrame を最適化する](modern-iframe-optimization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-104">For information about optimizing iFrames in SharePoint site pages, see [Optimize iFrames in SharePoint Online modern and classic publishing site pages](modern-iframe-optimization.md).</span></span>

<span data-ttu-id="dbdd4-105">SharePoint Online のモダン サイト ページには、ページの読み込み時間全体に影響する可能性のある Web パーツが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-105">SharePoint Online modern site pages contain web parts that can contribute to overall page load times.</span></span> <span data-ttu-id="dbdd4-106">この記事では、ページ内の Web パーツによるユーザーが感じる待機時間への影響を特定する方法と、一般的な問題を修復する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-106">This article will help you understand how to determine how web parts in your pages affect user perceived latency, and how to remediate common issues.</span></span>

>[!NOTE]
><span data-ttu-id="dbdd4-107">Sharepoint Online のモダン ポータルでのパフォーマンスの詳細については、「[SharePoint のモダン エクスペリエンスにおけるパフォーマンス](https://docs.microsoft.com/ja-JP/sharepoint/modern-experience-performance)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-107">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/ja-JP/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts"></a><span data-ttu-id="dbdd4-108">SharePoint 用ページ診断ツールを使用して Web パーツを分析する</span><span class="sxs-lookup"><span data-stu-id="dbdd4-108">Use the Page Diagnostics for SharePoint tool to analyze web parts</span></span>

<span data-ttu-id="dbdd4-109">**SharePoint 用ページ診断ツール**は、Chrome と [Microsoft Edge バージョン 77 以降](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8)のブラウザー拡張機能で、SharePoint の最新版と従来版両方の発行サイト ページの分析に利用できます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="dbdd4-110">このツールでは、定義されている一連のパフォーマンス条件に対するページのパフォーマンスを示す分析済みの各ページのレポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="dbdd4-111">SharePoint 用ページ診断ツールのインストール方法および詳細情報については、「[SharePoint Online 用ページ診断ツールを使用する](page-diagnostics-for-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="dbdd4-112">SharePoint のサイト ページを SharePoint 用ページ診断ツールを使用して分析すると、ベースライン メトリックを超えている Web パーツに関する情報が [_診断テスト_] ウィンドウ内の [**Web parts are impacting page load time**] (Web パーツがページの読み込み時間に影響を与えています) という結果に表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about web parts that exceed the baseline metric in the **Web parts are impacting page load time** result in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="dbdd4-113">表示される可能性のある結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-113">Possible results include:</span></span>

- <span data-ttu-id="dbdd4-114">[**Attention required**] (注意が必要です) (赤): 読み込みに **2** 秒以上かかる_カスタム_ Web パーツです。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-114">**Attention required** (red): Any _custom_ web part that takes longer than **two** seconds to load.</span></span> <span data-ttu-id="dbdd4-115">合計読み込み時間がテスト結果に表示される際は、モジュールの負荷、遅延読み込み、初期化、およびレンダリングに分けて表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-115">Total load time as displayed in test results is broken down by module load, lazy load, init and render.</span></span>
- <span data-ttu-id="dbdd4-116">[**Improvement opportunities**] (改善の余地あり) (黄): このセクションには、ページの読み込み時間に影響を与えている可能性があるアイテムが表示されます。これらのアイテムは、レビューと監視を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-116">**Improvement opportunities** (yellow): Items that may be impacting page load time are shown in this section and should be reviewed and monitored.</span></span> <span data-ttu-id="dbdd4-117">これには、"すぐに使用可能な" (OOTB) Microsoft Web パーツが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-117">This may include "out of the box" (OOTB) Microsoft web parts.</span></span> <span data-ttu-id="dbdd4-118">このセクションに表示される Microsoft Web パーツの結果は Microsoft に自動的に報告されるため、**必要な操作はありません**。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-118">Results for any Microsoft web parts shown in this section are automatically reported to Microsoft, so **no action is required**.</span></span> <span data-ttu-id="dbdd4-119">調査のためのサポート チケットを記録する必要があるのは、パフォーマンスの著しい低下がページで発生しており、ページの**すべての Microsoft Web パーツ**が結果の [**Improvement opportunities**] (改善の余地あり) セクションに表示される場合のみです。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-119">You should only log a support ticket for investigation if you are experiencing very slow performance on the page and **all Microsoft web parts** on the page appear in the results in the **Improvement opportunities** section.</span></span> <span data-ttu-id="dbdd4-120">今後のページ診断ツールの更新プログラムでは、Microsoft Web パーツの特定の構成に基づいて、結果がさらに細分化されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-120">Note that a future Page Diagnostics tool update will further break down the results based on the specific configuration of the Microsoft web part.</span></span>
- <span data-ttu-id="dbdd4-121">[**No action required**] (必要な操作はありません) (緑): データを返すのに **2** 秒以上かかっている Web パーツは 1 つもありません。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-121">**No action required** (green): No web part is taking longer than **two** seconds to return data.</span></span>

<span data-ttu-id="dbdd4-122">[**Web parts are impacting page load time**] (Web パーツがページの読み込み時間に影響を与えています) という結果が [**Attention required**] (注意が必要です) セクションまたは [**Improvement opportunities**] (改善の余地あり) セクションに表示された場合、結果をクリックすると読み込みが遅いページに関する詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-122">If the **Web parts are impacting page load time** result appears in either the **Attention required** or **Improvement opportunities** section of the results, click the result to see details about which web parts are loading slowly.</span></span> <span data-ttu-id="dbdd4-123">今後の SharePoint 用ページ診断ツールの更新プログラムでは分析ルールが更新される可能性があるため、常に最新バージョンのツールを使用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-123">Future updates to the Page Diagnostics for SharePoint tool may include updates to analysis rules, so please ensure you always have the latest version of the tool.</span></span>

![ページ診断ツールの結果](media/modern-portal-optimization/pagediag-web-part.png)

<span data-ttu-id="dbdd4-125">結果に含まれる情報は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-125">Information available in the results includes:</span></span>

- <span data-ttu-id="dbdd4-126">[**Made by**] (作成) には、Web パーツがカスタムなのか、Microsoft OOTB なのかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-126">**Made by** shows whether the web part is custom or Microsoft OOTB</span></span>
- <span data-ttu-id="dbdd4-127">[**Name and ID**] (名前と ID) には、ページで Web パーツを見つけるのに役立つ識別情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-127">**Name and ID** shows identifying information that can help you find the web part on the page</span></span>
- <span data-ttu-id="dbdd4-128">[**Total**] (合計) には、Web パーツの読み込みにかかる合計時間数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-128">**Total** shows the total time for the web part to load</span></span>
- <span data-ttu-id="dbdd4-129">[**Module Load**] (モジュールの負荷) には、Web パーツ コンポーネントを取得して読み込むのにかかる時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-129">**Module Load** shows the time taken to fetch and load the web part components</span></span>
- <span data-ttu-id="dbdd4-130">[**Lazy Load**] (遅延読み込み) には、ページのメインのセクションに表示されない Web パーツの遅延読み込み時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-130">**Lazy Load** shows the time for deferred loading of web parts not seen in the main section of the page</span></span>
- <span data-ttu-id="dbdd4-131">[**Init**] (初期化) には、Web パーツの初期化にかかる時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-131">**Init** shows the time taken for web part initialization</span></span>
- <span data-ttu-id="dbdd4-132">[**Render**] (レンダリング) には、Web パーツが結果を取得して表示するのにかかる時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-132">**Render** shows the time taken for the web part to fetch and render results</span></span>

<span data-ttu-id="dbdd4-133">この情報は、デザイナーと開発者が問題のトラブルシューティングを行えるように提供されています。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-133">This information is provided to help designers and developers troubleshoot issues.</span></span> <span data-ttu-id="dbdd4-134">この情報は、設計開発チームに提供するようにします。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-134">This information should be provided to your design and development team.</span></span>

## <a name="remediate-web-part-performance-issues"></a><span data-ttu-id="dbdd4-135">Web パーツのパフォーマンスの問題を修復する</span><span class="sxs-lookup"><span data-stu-id="dbdd4-135">Remediate web part performance issues</span></span>

<span data-ttu-id="dbdd4-136">[**Web parts are impacting page load time**] (Web パーツがページの読み込み時間に影響を与えています) という結果に表示されるパフォーマンスの問題を特定して修復するには、このセクションのガイダンスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-136">Follow the guidance in this section to identify and remediate performance issues with web parts listed in the **Web parts are impacting page load time** results.</span></span>

<span data-ttu-id="dbdd4-137">Web パーツのパフォーマンスが低い場合に考えられる原因のカテゴリには 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-137">There are three categories of possible causes for poor web part performance.</span></span> <span data-ttu-id="dbdd4-138">次の情報を使用して、お客様のシナリオに該当する問題を特定し、修復してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-138">Use the information below to determine which issues apply to your scenario and remediate them.</span></span>

- <span data-ttu-id="dbdd4-139">Web パーツ スクリプトのサイズと依存関係</span><span class="sxs-lookup"><span data-stu-id="dbdd4-139">Web part script size and dependencies</span></span>
  - <span data-ttu-id="dbdd4-140">メインのシナリオをレンダリングする初期スクリプトの最適化を_表示モードに対してのみ_行います。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-140">Optimize the initial script that renders the mainline scenario for _view mode only_.</span></span>
  - <span data-ttu-id="dbdd4-141">かたまりごとに分けるために、_import()_ ステートメントを使用して頻度が低いシナリオを移動し、モード コード (プロパティ ウィンドウなど) を編集します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-141">Move the less frequent scenarios and edit mode code (like the property pane) to separate chunks using the _import()_ statement.</span></span>
  - <span data-ttu-id="dbdd4-142">機能していないコードをすべて完全に削除するために、_package.json_ の依存関係を確認します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-142">Review dependencies of the _package.json_ file to remove any dead code completely.</span></span> <span data-ttu-id="dbdd4-143">テスト/ビルド専用依存関係があれば、すべて devDependencies に移動します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-143">Move any test/build only dependencies to devDependencies.</span></span>
  - <span data-ttu-id="dbdd4-144">静的リソースの最適なダウンロードを行うには、Office 365 CDN を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-144">Use of the Office 365 CDN is required for optimal static resource download.</span></span> <span data-ttu-id="dbdd4-145">_js/css_ ファイルの配信元として、パブリックの CDN 配信元が推奨されています。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-145">Public CDN origins are preferable for _js/css_ files.</span></span> <span data-ttu-id="dbdd4-146">Office 365 CDN の使用に関する詳細については、「[SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用](use-office-365-cdn-with-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-146">For information about how to use the Office 365 CDN, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="dbdd4-147">SharePoint Framework (SPFx) に付属する _React_ や _Fabric imports_ などのフレームワークを再利用してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-147">Reuse frameworks like _React_ and _Fabric imports_ that come as part of the SharePoint Framework (SPFx).</span></span> <span data-ttu-id="dbdd4-148">詳細については、「[SharePoint Framework の概要](https://docs.microsoft.com/ja-JP/sharepoint/dev/spfx/sharepoint-framework-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-148">For more information, see  [Overview of the SharePoint Framework](https://docs.microsoft.com/ja-JP/sharepoint/dev/spfx/sharepoint-framework-overview).</span></span>
  - <span data-ttu-id="dbdd4-149">最新バージョンの SharePoint Framework を使用するようにし、新しいバージョンがリリースされた場合にはアップグレードしてください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-149">Ensure that you are using the latest version of the SharePoint Framework, and upgrade to new versions as they become available.</span></span>
- <span data-ttu-id="dbdd4-150">データの取得/キャッシュ</span><span class="sxs-lookup"><span data-stu-id="dbdd4-150">Data fetching/caching</span></span>
  - <span data-ttu-id="dbdd4-151">表示するデータを取得するのに Web パーツが追加のサーバー呼び出しに依存している場合は、それらのサーバー API が高速で、(_localStorage_ や _IndexDB_ (大規模なセットの場合) などを使用する) クライアント側キャッシュが実装されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-151">If the web part relies on extra server calls to fetch data for display, ensure those server APIs are fast and/or implement client side caching (such as using _localStorage_ or _IndexDB_ for larger sets).</span></span>
  - <span data-ttu-id="dbdd4-152">重要なデータを表示するために複数の呼び出しが必要な場合は、サーバーへの呼び出しのバッチ処理または複数の要求を 1 つの呼び出しに統合する他の方法を検討してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-152">If multiple calls are required to render critical data, consider batching on the server or other methods of consolidating requests to a single call.</span></span>
  - <span data-ttu-id="dbdd4-153">または、データの一部の要素で低速の API が要求され、これらの要素が初期レンダリングには重要でない場合、これらを重要なデータのレンダリング後に実行される別の呼び出しに切り離します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-153">Alternatively, if some elements of data require a slower API, but are not critical to initial rendering, decouple these to a separate call that is executed after critical data is rendered.</span></span>
  - <span data-ttu-id="dbdd4-154">複数のパーツが同じデータを使用している場合、共通データ層を使用して呼び出しの重複を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-154">If multiple parts use the same data, utilize a common data layer to avoid duplicate calls.</span></span>
- <span data-ttu-id="dbdd4-155">レンダリング時間</span><span class="sxs-lookup"><span data-stu-id="dbdd4-155">Rendering time</span></span>
  - <span data-ttu-id="dbdd4-156">不必要な大きなアセットのダウンロードを防ぐために、画像やビデオなどのメディアのソースは、コンテナー、デバイス、およびネットワークの制限に合わせてサイズを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-156">Any media sources like images and videos should be sized to the limits of the container, device and/or network to avoid downloading unnecessary large assets.</span></span> <span data-ttu-id="dbdd4-157">コンテンツの依存関係の詳細については、「[SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用](use-office-365-cdn-with-spo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-157">For information about how to use the Office 365 CDN, see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>
  - <span data-ttu-id="dbdd4-158">再フロー、複雑な CSS ルール、複雑なアニメーションにつながる API 呼び出しを行わないようにします。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-158">Avoid API calls that cause re-flow, complex CSS rules or complicated animations.</span></span> <span data-ttu-id="dbdd4-159">詳細については、「[Minimizing browser reflow
(ブラウザーの再フローを最小化する)](https://developers.google.com/speed/docs/insights/browser-reflow)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-159">For more information, see [Minimizing browser reflow](https://developers.google.com/speed/docs/insights/browser-reflow).</span></span>
  - <span data-ttu-id="dbdd4-160">連結されている長時間実行タスクを使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-160">Avoid use of chained long running tasks.</span></span> <span data-ttu-id="dbdd4-161">代わりに、長時間実行タスクは個別のキューに分割します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-161">Instead, break long running tasks apart into separate queues.</span></span> <span data-ttu-id="dbdd4-162">詳細については、「[Optimize JavaScript Execution (JavaScript の実行を最適化する)](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-162">For more information, see [Optimize JavaScript Execution](https://developers.google.com/web/fundamentals/performance/rendering/optimize-javascript-execution).</span></span>
  - <span data-ttu-id="dbdd4-163">フレームの飛びや途切れ (_ジャンク_とも呼ばれます) を防ぐために、メディアの非同期的なレンダリング用に、対応するスペースを予約します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-163">Reserve corresponding space for asynchronously rendering media or visual elements to avoid skipped frames and stuttering (also known as _jank_).</span></span>
  - <span data-ttu-id="dbdd4-164">レンダリンで使用される機能が特定のブラウザーでサポートされていない場合は、ポリフィルを読み込むか、依存コードの実行を除外します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-164">If a certain browser doesn't support a feature used in rendering, either load a polyfill or exclude running dependent code.</span></span> <span data-ttu-id="dbdd4-165">その機能が重要ではない場合は、メモリ リークが発生しないようにイベント ハンドラーなどのリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-165">If the feature is not critical, dispose resources such as event handlers to avoid memory leaks.</span></span>

<span data-ttu-id="dbdd4-166">パフォーマンスの問題を修復するためにページを変更する前に、分析結果に表示されるページ読み込み時間をメモしてください。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-166">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="dbdd4-167">修正後にツールをもう一度実行して新しい結果がベースライン基準内にあるかどうかを確認し、新しいページ読み込み時間をチェックして改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-167">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![ページ読み込み時間の結果](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="dbdd4-169">ページ読み込み時間は、ネットワーク負荷、時間帯、その他の一時的な状態など、さまざまな要素によって異なります。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-169">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="dbdd4-170">結果を平均化するために、変更の前後に数回に渡ってページ読み込み時間をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbdd4-170">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="dbdd4-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbdd4-171">Related topics</span></span>

[<span data-ttu-id="dbdd4-172">SharePoint Online のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="dbdd4-172">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="dbdd4-173">Office 365 のパフォーマンスをチューニングする</span><span class="sxs-lookup"><span data-stu-id="dbdd4-173">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="dbdd4-174">SharePoint のモダン エクスペリエンスにおけるパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="dbdd4-174">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/ja-JP/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="dbdd4-175">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="dbdd4-175">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="dbdd4-176">SharePoint Online での Office 365 コンテンツ配信ネットワーク (CDN) の使用</span><span class="sxs-lookup"><span data-stu-id="dbdd4-176">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)