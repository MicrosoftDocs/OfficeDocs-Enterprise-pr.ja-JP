---
title: SharePoint サイトのコンテンツを地域の場所に制限する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 複数地域環境で SharePoint サイトを指定の地域の場所に制限する方法について説明します。
ms.openlocfilehash: 9319ed6229acc7cda48cc52b3a27681c53f1359c
ms.sourcegitcommit: 7bb48195079ce14aabfa0384771b17db0e4908b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "36828481"
---
# <a name="restrict-sharepoint-site-content-to-a-geo-location"></a><span data-ttu-id="6aa34-103">SharePoint サイトのコンテンツを地域の場所に制限する</span><span class="sxs-lookup"><span data-stu-id="6aa34-103">Restrict content to a geo location</span></span>

<span data-ttu-id="6aa34-104">状況によっては、サイトが移動されないようにするか、サイトのファイル コンテンツが別の地域の場所にキャッシュされないようにすることで、サイトが作成された地域の場所にサイトとそのファイル コンテンツを保持するように選択できます。</span><span class="sxs-lookup"><span data-stu-id="6aa34-104">Under some circumstances you may choose to enforce a site and its file content to remain in the geo location where the site was created, either by preventing the site from being moved or by preventing the caching of the site's file content in another geo location.</span></span>

<span data-ttu-id="6aa34-105">これを行うには、[Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) コマンドレットを **RestrictedToGeo** パラメーターと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="6aa34-105">You can do this by using the [Set-SPOSite](https://docs.microsoft.com/powershell/module/sharepoint-online/set-sposite) cmdlet with the **RestrictedToGeo** parameter.</span></span> <span data-ttu-id="6aa34-106">このパラメーターの既定値は NULL ですが、次のいずれかに変更できます。</span><span class="sxs-lookup"><span data-stu-id="6aa34-106">This parameter has a default value of NULL, but you can change it to one of the following:</span></span>

|<span data-ttu-id="6aa34-107">制限</span><span class="sxs-lookup"><span data-stu-id="6aa34-107">Restriction</span></span>|<span data-ttu-id="6aa34-108">説明</span><span class="sxs-lookup"><span data-stu-id="6aa34-108">Description</span></span>|
|:----------|:----------|
|<span data-ttu-id="6aa34-109">NoRestriction</span><span class="sxs-lookup"><span data-stu-id="6aa34-109">NoRestriction</span></span>|<span data-ttu-id="6aa34-110">サイトを別の地域の場所に移動できます。</span><span class="sxs-lookup"><span data-stu-id="6aa34-110">The site can be moved to another geo location.</span></span>|
|<span data-ttu-id="6aa34-111">BlockMoveOnly</span><span class="sxs-lookup"><span data-stu-id="6aa34-111">BlockMoveOnly</span></span>|<span data-ttu-id="6aa34-112">サイトを別の地域の場所に移動することはできませんが、サイトのコンテンツを別の地域の場所にキャッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="6aa34-112">Site cannot be moved to another geo location, but site content can be cached in other geo locations.</span></span>|
|<span data-ttu-id="6aa34-113">BlockFull</span><span class="sxs-lookup"><span data-stu-id="6aa34-113">BlockFull</span></span>|<span data-ttu-id="6aa34-114">サイトを別の地域の場所に移動することはできません。また、ファイルのすべてのコンテンツも他の地域の場所にキャッシュされません。</span><span class="sxs-lookup"><span data-stu-id="6aa34-114">Site cannot be moved to another geo location, and full file content is not cached in other geo locations.</span></span> <span data-ttu-id="6aa34-115">ファイルのタイトル (コンテンツから取得)、ファイル名、およびファイルの他のプロパティは、引き続き別の地域の場所にキャッシュできます。</span><span class="sxs-lookup"><span data-stu-id="6aa34-115">Files' title (harvested from the content), file name, and other properties of the file can still be cached in other geo-locations.</span></span><br><span data-ttu-id="6aa34-116">BlockFull に構成される前にサイトに保存されたコンテンツは、引き続き他の地域の場所にキャッシュされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6aa34-116">Content stored in the site before it was configured to BlockFull, may continue to be cached in other geo locations.</span></span>|

<span data-ttu-id="6aa34-117">次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="6aa34-117">Use the following syntax:</span></span>

`Set-SPOSite -Identity <siteURL> -RestrictedToGeo <restriction>`

<span data-ttu-id="6aa34-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6aa34-118">For example:</span></span>

`Set-SPOSite -Identity https://contoso.sharepoint.com/sites/RegionRestrictedTeamSite -RestrictedToGeo BlockFull`
