---
title: Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/31/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)
ms.openlocfilehash: 13ca35afe4bd375482a9fc924801e240c361bb6b
ms.sourcegitcommit: 6508db0a839427e1a21b1cde883d828e3c8886c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "43185728"
---
# <a name="microsoft-365-network-connectivity-location-services-preview"></a><span data-ttu-id="6f65a-103">Microsoft 365 ネットワーク接続ロケーションサービス (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="6f65a-103">Microsoft 365 Network Connectivity Location Services (preview)</span></span>

<span data-ttu-id="6f65a-104">Microsoft 365 管理センターには、Microsoft 365 テナントから収集され、テナントの管理ユーザーのみが閲覧できるライブパフォーマンス指標である、**ネットワークの洞察とパフォーマンスに関する推奨事項**が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f65a-104">The Microsoft 365 Admin Center now shows **Network Insights and performance recommendations**, which are live performance metrics collected from your Microsoft 365 tenant and available to view only by administrative users in your tenant.</span></span> <span data-ttu-id="6f65a-105">組織のネットワーク接続は、ネットワークの出口からインターネットへの場所によって、オフィスの場所ごとに設計されています。</span><span class="sxs-lookup"><span data-stu-id="6f65a-105">Organizational network connectivity is designed per office location through a network egress location to the Internet.</span></span> <span data-ttu-id="6f65a-106">Microsoft 365 クライアント接続は、そのルートを使用して、インターネットを介して Microsoft サービスのフロントドアサーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="6f65a-106">Microsoft 365 client connectivity uses that route and then across the Internet to Microsoft service front door servers.</span></span> <span data-ttu-id="6f65a-107">Office の場所を特定することは、これらのネットワーク洞察を表示できることを示す鍵となります。</span><span class="sxs-lookup"><span data-stu-id="6f65a-107">Identifying office locations is key to being able to show these network insights.</span></span>

## <a name="location-in-network-measurements"></a><span data-ttu-id="6f65a-108">ネットワーク測定の場所</span><span class="sxs-lookup"><span data-stu-id="6f65a-108">Location in network measurements</span></span>

<span data-ttu-id="6f65a-109">組織の管理者は、この機能で使用されるネットワーク測定に含める場所をオプトインすることができます。</span><span class="sxs-lookup"><span data-stu-id="6f65a-109">An organization's administrator can opt in for location to be included in the network measurements used by this feature.</span></span> <span data-ttu-id="6f65a-110">これにより、各オフィスが配置されている都市の自動検出が有効になります。</span><span class="sxs-lookup"><span data-stu-id="6f65a-110">This enables auto-discovery of the city where each office is located.</span></span> <span data-ttu-id="6f65a-111">場所情報が正確ではなく、300m にわかりにくくなり、都市ごとに分類されています。</span><span class="sxs-lookup"><span data-stu-id="6f65a-111">Location information is not precise and is obfuscated to 300m and categorized by city.</span></span> <span data-ttu-id="6f65a-112">場所が Windows デバイスでキャプチャされているときには、ツールトレイに**使用中の場所**のアイコンが表示されるため、管理者はそのことをユーザーに通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f65a-112">At the time when location is captured on a Windows device it will show a **Location In-Use** icon in the tool tray and administrators may want to notify users of this.</span></span> <span data-ttu-id="6f65a-113">この処理では、場所はユーザーまたはデバイスの場所ではなく、組織のオフィスの場所として扱われます。</span><span class="sxs-lookup"><span data-stu-id="6f65a-113">With this processing, the location is treated as the organization office location and not the location of a person or a device.</span></span> <span data-ttu-id="6f65a-114">ネットワーク insights は、検出されたオフィスの場所の都市に表示することができます。</span><span class="sxs-lookup"><span data-stu-id="6f65a-114">Network insights can be shown at these discovered office location cities.</span></span> <span data-ttu-id="6f65a-115">推奨事項の正確性が向上している場合は、管理者が特定のオフィスの場所のアドレスを入力すると、その場所にネットワーク洞察が集約されます。</span><span class="sxs-lookup"><span data-stu-id="6f65a-115">If greater accuracy of recommendations is desired, an administrator can enter specific office location addresses and the network insights will be aggregated to those instead.</span></span> <span data-ttu-id="6f65a-116">Office の場所を300メートルよりも詳細に集計することはできません。</span><span class="sxs-lookup"><span data-stu-id="6f65a-116">Office locations cannot be aggregated more closely than 300 meters.</span></span>

## <a name="location-in-the-microsoft-365-admin-center"></a><span data-ttu-id="6f65a-117">Microsoft 365 管理センターの場所</span><span class="sxs-lookup"><span data-stu-id="6f65a-117">Location in the Microsoft 365 Admin Center</span></span>

<span data-ttu-id="6f65a-118">Microsoft 365 管理センターでは、Bing マップコントロールを使用して、組織の場所の場所を示し、選択したオフィスの場所のネットワーク境界トポロジを表示します。</span><span class="sxs-lookup"><span data-stu-id="6f65a-118">In the Microsoft 365 Admin Center, Bing map controls are used to show where organization office locations are and to show network perimeter topology for a selected office location.</span></span> <span data-ttu-id="6f65a-119">管理者が office の場所に特定の住所の詳細を追加すると、データ入力を簡単にするためにアドレスを提案するために Bing Maps も使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f65a-119">When an administrator adds specific address details for office locations, Bing Maps is also used to suggest addresses to make data entry easier.</span></span>

## <a name="terms-of-use"></a><span data-ttu-id="6f65a-120">使用条件</span><span class="sxs-lookup"><span data-stu-id="6f65a-120">Terms of Use</span></span>

<span data-ttu-id="6f65a-121">Geocodes を含む Bing Maps で提供されるコンテンツは、そのコンテンツが提供される製品内でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6f65a-121">Any content provided through Bing Maps, including geocodes, can only be used within the product through which the content is provided.</span></span> <span data-ttu-id="6f65a-122">お客様による Microsoft 365 管理センターの場所サービス機能の使用 (Bing Maps による) は、 _Bing Maps エンドユーザー使用許諾契約_書<https://go.microsoft.com/?linkid=9710837> () およびで提供される_Microsoft のプライバシー_に関する声明に準拠しています。<https://go.microsoft.com/fwlink/?LinkID=248686.></span><span class="sxs-lookup"><span data-stu-id="6f65a-122">Customer's use of the Microsoft 365 Admin Center Location Services feature, powered by Bing Maps, is governed by the _Bing Maps End User Terms of Use_ available at <https://go.microsoft.com/?linkid=9710837> and the _Microsoft Privacy Statement_ available at <https://go.microsoft.com/fwlink/?LinkID=248686.></span></span>

<span data-ttu-id="6f65a-123">Bing Maps で提供されるこの機能は、この**テクノロジ**でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6f65a-123">This feature, provided through Bing Maps, is also supported by **Here Technologies**.</span></span> <span data-ttu-id="6f65a-124">Bing Maps_は、ここ_で提供される場所サービスを活用する方法について説明<https://legal.here.com/en-gb/terms>します。</span><span class="sxs-lookup"><span data-stu-id="6f65a-124">How Bing Maps leverages location services provided by Here Technologies is governed by the _Here Technologies Service Terms_ available at <https://legal.here.com/en-gb/terms>.</span></span>
