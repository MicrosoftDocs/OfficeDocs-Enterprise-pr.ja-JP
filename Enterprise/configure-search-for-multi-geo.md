---
title: ビジネスの複数の地域の OneDrive の検索を構成します。
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: マルチ地域環境での検索を構成する方法について説明します。
ms.openlocfilehash: 5cf155c2c5bd2e27a54d84c4d5411e5b1afce568
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="e15b6-103">ビジネスの複数の地域の OneDrive の検索を構成します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="e15b6-104">マルチ Geo SharePoint オンライン (SPO) 環境で組織、1 つの Office 365 テナント、複数の地理的な場所に、SharePoint のコンテンツを格納する 1 つの場所と 1 つ以上サテライト地域の場所です。</span><span class="sxs-lookup"><span data-stu-id="e15b6-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="e15b6-p101">各の地理的な場所では、独自の検索インデックスと検索センターがあります。ユーザーが検索してクエリは、すべてのインデックスさばいたが返される結果がマージされます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="e15b6-p102">などの地域の 1 つの場所のユーザーは、地域の別の場所に保存されたコンテンツまたは地域の別の場所に制限されている SharePoint サイト上のコンテンツを検索できます。このコンテンツへのアクセスをユーザーには、検索で結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="e15b6-109">複数地域の環境でクライアントの作業を検索するでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e15b6-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="e15b6-110">これらのクライアントでは、地域のすべての場所から結果を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="e15b6-111">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="e15b6-111">OneDrive for Business</span></span>

-   <span data-ttu-id="e15b6-112">Delve</span><span class="sxs-lookup"><span data-stu-id="e15b6-112">Delve</span></span>

-   <span data-ttu-id="e15b6-113">SharePoint ホーム ページ</span><span class="sxs-lookup"><span data-stu-id="e15b6-113">The SharePoint home page</span></span>

-   <span data-ttu-id="e15b6-114">検索センター</span><span class="sxs-lookup"><span data-stu-id="e15b6-114">The Search Center</span></span>

-   <span data-ttu-id="e15b6-115">SharePoint 検索 API を使用するカスタムの検索アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e15b6-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="e15b6-116">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="e15b6-116">OneDrive for Business</span></span>

<span data-ttu-id="e15b6-117">複数地域の環境が設定されているとすぐに OneDrive で検索するユーザーは、地域のすべての場所から結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="e15b6-118">Delve</span><span class="sxs-lookup"><span data-stu-id="e15b6-118">Delve</span></span>

<span data-ttu-id="e15b6-119">複数地域の環境が設定されているとすぐに Delve で検索するユーザーは、地域のすべての場所から結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="e15b6-p103">Delve のフィード、プロファイルのカードは**中央**の場所に格納されているファイルのプレビューにのみ表示されます。サテライト地域の場所に格納されているファイルの場合は、代わりにファイルの種類のアイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="e15b6-122">SharePoint ホーム ページ</span><span class="sxs-lookup"><span data-stu-id="e15b6-122">The SharePoint home page</span></span>

<span data-ttu-id="e15b6-p104">ユーザー複数地域の環境が設定されているとすぐには、ニュースが、SharePoint のホーム ページに複数の地域の場所からのリンクと最近のサイトに表示されます。SharePoint ホーム ページで、[検索] ボックスを使用すると、それらが地域の複数の場所からマージされた結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="e15b6-125">検索センター</span><span class="sxs-lookup"><span data-stu-id="e15b6-125">The Search Center</span></span>

<span data-ttu-id="e15b6-p105">複数の地域の後の環境が設定されて、各検索センターは引き続き表示結果だけが自分の地域の場所から。管理者は、[各検索センターの設定を変更する](#_Set_up_a_1)地域のすべての場所から結果を取得する必要があります。その後、検索センターで検索するユーザーは、地域のすべての場所から結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="e15b6-129">カスタムの検索アプリケーション</span><span class="sxs-lookup"><span data-stu-id="e15b6-129">Custom search applications</span></span>

<span data-ttu-id="e15b6-p106">いつものように、カスタム検索アプリケーションは、既存の SharePoint 検索 REST Api を使用しての検索用のインデックスと対話します。全部または一部の地域の場所から結果を得るには、アプリケーション[API を呼び出すし複数地域の新しいクエリのパラメーターは、](#_Get_custom_search)要求で必要があります。これにより、地域のすべての場所へのクエリからのファンがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="e15b6-133">マルチ地域環境での検索に関するさまざまなは何ですか。</span><span class="sxs-lookup"><span data-stu-id="e15b6-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="e15b6-134">いくつかの検索機能を学習し、する必要がありますが、複数地域環境で作業とは異なる。</span><span class="sxs-lookup"><span data-stu-id="e15b6-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e15b6-135"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="e15b6-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="e15b6-136"><strong>どのように動作します。</strong></span><span class="sxs-lookup"><span data-stu-id="e15b6-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="e15b6-137"><strong>回避策</strong></span><span class="sxs-lookup"><span data-stu-id="e15b6-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e15b6-138">昇格した結果</span><span class="sxs-lookup"><span data-stu-id="e15b6-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="e15b6-p107">クエリ ルールを作成するにはさまざまなレベルに昇格した結果: 全体のテナント、サイト コレクションまたはサイトです。マルチ地域環境では、地域の<strong>すべて</strong>の場所で検索センター結果を昇格する場合は、<strong>テナント</strong>のレベルに昇格した結果を定義します。場合<strong>のみ</strong>サイト コレクションまたはサイトの地域の場所にある検索センターでの結果を促進する、<strong>サイト コレクション</strong>または<strong>サイト</strong>レベルでの結果を定義します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="e15b6-142">個々 の地域の場所、旅をするなどの別のルールの異なる昇格した結果を必要としない場合は、テナントのレベルで結果を昇格を定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e15b6-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e15b6-143">検索の絞り込み条件</span><span class="sxs-lookup"><span data-stu-id="e15b6-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="e15b6-p108">検索では、テナントのすべての地域の場所から絞り込み条件が返されます、それが集計されます。集計は、絞り込み条件の数が 100% 正確な可能性がありますできないことを意味するよう、最善の努力です。ほとんどの検索ベースのシナリオでは、この精度で十分です。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="e15b6-147">絞り込み条件の完全性に依存する検索駆動型アプリケーションを照会しない各地域拠点個別に複数地域のファンを使用せず。</span><span class="sxs-lookup"><span data-stu-id="e15b6-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="e15b6-148">マルチ地域検索では、数値絞り込み条件の動的なバケットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e15b6-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="e15b6-149">数値絞り込み条件の<a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">「Discretize」パラメーター</a>を使用します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e15b6-150">ドキュメント Id</span><span class="sxs-lookup"><span data-stu-id="e15b6-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="e15b6-151">ドキュメント Id に依存している、検索駆動型アプリケーションを開発する場合は、地域拠点に複数地域の環境でドキュメント Id は一意、geo の場所ごとに一意であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e15b6-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="e15b6-p109">地域の場所を識別する列を追加しました。一意性を達成するためにこの列を使用します。この列を"GeoLocationSource"といいます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e15b6-155">結果の数</span><span class="sxs-lookup"><span data-stu-id="e15b6-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="e15b6-156">検索結果のページは、geo の場所からの結合された結果を示していますが、ページの 500 件の結果を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="e15b6-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="e15b6-157">マルチ地域環境での検索の内容はサポートされていませんでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e15b6-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="e15b6-158">複数地域の環境で学習し、する必要があります検索機能の一部がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e15b6-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e15b6-159"><strong>検索機能</strong></span><span class="sxs-lookup"><span data-stu-id="e15b6-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="e15b6-160"><strong>注</strong></span><span class="sxs-lookup"><span data-stu-id="e15b6-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e15b6-161">アプリケーション専用の認証</span><span class="sxs-lookup"><span data-stu-id="e15b6-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="e15b6-162">マルチ地域検索では、アプリケーション専用の認証 (サービスからのアクセス権限) はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e15b6-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e15b6-163">ゲスト ユーザー</span><span class="sxs-lookup"><span data-stu-id="e15b6-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="e15b6-164">ゲスト ユーザーは、検索をしている地域の場所からのみ結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="e15b6-165">検索の動作方法、複数地域の環境で</span><span class="sxs-lookup"><span data-stu-id="e15b6-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="e15b6-166">**すべて**検索クライアントを使用して、既存の SharePoint 検索 REST Api 検索用のインデックスを操作します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="e15b6-167">検索クライアントは、クエリのプロパティ EnableMultiGeoSearch を使用して検索 REST エンドポイントを呼び出す true です。</span><span class="sxs-lookup"><span data-stu-id="e15b6-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="e15b6-168">テナントのすべての地域の場所にクエリが送信されます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="e15b6-169">各地域の場所から検索結果がマージされ、ランク付けされます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="e15b6-170">クライアントでは、統合された検索結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-170">The client gets unified search results.</span></span>



<span data-ttu-id="e15b6-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>地域のすべての場所から結果を受信するまで検索結果をマージしてしないことを確認します。これは、複数地域の検索がある地域の 1 つだけの場所がある環境での検索と比較して追加の遅延を意味します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="e15b6-173">地域のすべての場所からの結果を表示する検索センターを取得します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="e15b6-174">各検索センターにはいくつかの業界を使用して個別にそれぞれの垂直方向を設定します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="e15b6-175">検索結果ページや検索結果の Web パーツを編集する権限を持つアカウントを使用して、次の手順を実行することを確認します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="e15b6-176">検索結果のページに移動します ([ボックスの一覧](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213)の検索結果のページを参照してください)</span><span class="sxs-lookup"><span data-stu-id="e15b6-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="e15b6-p111">設定し、上、右下の歯車アイコンの**設定**をクリックして、**ページの編集**] をクリックし、垂直方向を選択します。検索結果ページが編集モードで開きます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="e15b6-p112">検索結果の Web パーツで、上にポインターを移動、Web パーツの右にある矢印をクリックし、メニューの [ **Web パーツの編集**] をクリックします。上部のリボンの下の検索結果 Web パーツ ツール ウィンドウが開き、ページの右。![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="e15b6-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="e15b6-181">Web パーツ ツール ウィンドウの [**設定**] セクションの**設定を制御する結果**を、下には、地域のすべての場所からの結果を表示する検索結果 Web パーツを取得するのには**複数の地域の表示結果**を選択します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="e15b6-182">変更を保存し、Web パーツ ツール ウィンドウを閉じるには、 **[ok]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e15b6-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="e15b6-183">メイン メニューの [ページ] タブの [**チェックイン**] をクリックして、検索結果 Web パーツに加えた変更を確認します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="e15b6-184">ページの上部にあるメモに記載されているリンクを使用して変更内容を発行します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="e15b6-185">すべてまたは一部の地域の場所からの結果を表示するカスタムの検索アプリケーションを取得します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="e15b6-p113">カスタムの検索アプリケーションは、SharePoint 検索 REST API への要求にクエリ パラメーターを指定することにより全部または一部、地域の場所からの結果を得る。クエリのパラメーターによって、地域のすべての場所に、またはいくつかの地域拠点に、クエリさばいた。などの関連情報を検索する場所を地域のサブセットのクエリを実行する場合は、これらだけにファンを制御できます。要求が成功すると、SharePoint の検索 REST API は応答データを返します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="e15b6-190">クエリ パラメーター</span><span class="sxs-lookup"><span data-stu-id="e15b6-190">Query parameters</span></span>

<span data-ttu-id="e15b6-p114">EnableMultiGeoSearch - これは、クエリを複数地域テナントの他の地域の場所のインデックスさばいたものとするかどうかを指定するブール値です。に**true を指定**するクエリを設定します。**false を指定**しないクエリが 。既定値は、 **false を指定**します。このパラメーターを指定しない場合、クエリは、他の地域の場所に、**ない**さばいた。複数地域ではない環境で、パラメーターを使用する場合、パラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="e15b6-p115">顧客タイプ - これは、文字列です。検索アプリケーションごとに一意のクライアント名を入力します。このパラメーターを指定しない場合、クエリは、他の地域の場所に、**ない**さばいた。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="e15b6-p116">MultiGeoSearchConfiguration - これは、どの地域の複数の地域での場所のテナント**EnableMultiGeoSearch**が**true**の場合に、クエリをファンに省略可能な一覧です。、このパラメーターを指定するか、空欄のままにしない、クエリはすべての地域の場所さばいた。各地域の場所では、JSON 形式で次の項目を入力します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e15b6-202">項目</span><span class="sxs-lookup"><span data-stu-id="e15b6-202">Item</span></span></th>
<th align="left"><span data-ttu-id="e15b6-203">説明</span><span class="sxs-lookup"><span data-stu-id="e15b6-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e15b6-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="e15b6-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="e15b6-205">Geo 場所、たとえば名です。</span><span class="sxs-lookup"><span data-stu-id="e15b6-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e15b6-206">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="e15b6-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="e15b6-207">たとえば、接続するエンドポイントhttps://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="e15b6-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e15b6-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="e15b6-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="e15b6-209">結果のソース、たとえば B81EAB55-3140-4312-B0F4-9459D1B4FFEE の GUID です。</span><span class="sxs-lookup"><span data-stu-id="e15b6-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="e15b6-p117">DataLocation またはエンドポイントを省略した場合、または、DataLocation が重複している場合は、要求は失敗します。[Microsoft Graph を使用して、テナントの geo の場所のエンドポイントに関する情報を取得することができます](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery)。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="e15b6-212">応答データ</span><span class="sxs-lookup"><span data-stu-id="e15b6-212">Response data</span></span>

<span data-ttu-id="e15b6-p118">MultiGeoSearchStatus – これは、SharePoint Search API 要求への応答を返すプロパティです。プロパティの値は文字列であり、SharePoint Search API が返す結果をに関する次の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e15b6-215">値</span><span class="sxs-lookup"><span data-stu-id="e15b6-215">Value</span></span></th>
<th align="left"><span data-ttu-id="e15b6-216">説明</span><span class="sxs-lookup"><span data-stu-id="e15b6-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e15b6-217">完全</span><span class="sxs-lookup"><span data-stu-id="e15b6-217">Full</span></span></td>
<td align="left"><span data-ttu-id="e15b6-218">地域の場所から<strong>すべて</strong>の結果の完全な。</span><span class="sxs-lookup"><span data-stu-id="e15b6-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e15b6-219">一部</span><span class="sxs-lookup"><span data-stu-id="e15b6-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="e15b6-p119">1 つまたは複数の地域の場所からの部分的な結果です。結果では、一時的なエラーのため完了できません。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="e15b6-222">REST サービスを使用してクエリ</span><span class="sxs-lookup"><span data-stu-id="e15b6-222">Query using the REST service</span></span>

<span data-ttu-id="e15b6-p120">GET 要求では、URL にクエリ パラメーターを指定します。POST 要求では、JavaScript オブジェクト表記法 (JSON) 形式の本文にクエリのパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="e15b6-225">要求ヘッダー</span><span class="sxs-lookup"><span data-stu-id="e15b6-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e15b6-226">名前</span><span class="sxs-lookup"><span data-stu-id="e15b6-226">Name</span></span></th>
<th align="left"><span data-ttu-id="e15b6-227">値</span><span class="sxs-lookup"><span data-stu-id="e15b6-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e15b6-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="e15b6-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="e15b6-229">アプリケーションまたは json; odata = 詳細</span><span class="sxs-lookup"><span data-stu-id="e15b6-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="e15b6-230">地域の**すべて**の場所さばいたが GET 要求のサンプル</span><span class="sxs-lookup"><span data-stu-id="e15b6-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="e15b6-231">https://\<テナント\>/\_api/検索/query?querytext 'sharepoint' とプロパティを = 'EnableMultiGeoSearch:true' と顧客タイプを = =' 私\_クライアント\_id'</span><span class="sxs-lookup"><span data-stu-id="e15b6-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="e15b6-232">サンプル GET 要求で**いくつか**の地域拠点に広がる</span><span class="sxs-lookup"><span data-stu-id="e15b6-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="e15b6-233">https:// <tenant>/_api/search/query?querytext 'site' & 顧客タイプを = 'my_client_id' とプロパティを = ='EnableMultiGeoSearch:true、MultiGeoSearchConfiguration: [{DataLocation\:「名前」\,エンドポイント\:"https\:contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:」が「\,エンドポイント\:"https\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="e15b6-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="e15b6-234">地域の**すべて**の場所さばいた、POST 要求のサンプル</span><span class="sxs-lookup"><span data-stu-id="e15b6-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="e15b6-235">**いくつか**の地域拠点にさばいたは、POST 要求のサンプル</span><span class="sxs-lookup"><span data-stu-id="e15b6-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="e15b6-236">CSOM を使用してクエリ</span><span class="sxs-lookup"><span data-stu-id="e15b6-236">Query using CSOM</span></span>

<span data-ttu-id="e15b6-237">地域の**すべて**の場所さばいた、CSOM クエリの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="e15b6-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

