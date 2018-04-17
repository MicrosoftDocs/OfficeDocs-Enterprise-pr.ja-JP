---
title: OneDrive の複数地域機能および Office 365 の SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expand your Office 365 presence to multiple geographic regions with multi-geo capabilities in OneDrive and SharePoint Online.
ms.openlocfilehash: 3f72158fe05aadfe8a08a5520bf65cd2d0aaa1c6
ms.sourcegitcommit: a81d08c7e8771cb2c232435971e3169d4f7428dc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="da76f-103">OneDrive の複数地域機能および Office 365 の SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="da76f-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="da76f-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="da76f-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="da76f-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span><span class="sxs-lookup"><span data-stu-id="da76f-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="da76f-107">Here's how multi-geo features can benefit your organization:</span><span class="sxs-lookup"><span data-stu-id="da76f-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="da76f-108">複数の地理的な場所にわたる単一の Office 365 テナントで、1 つのグローバルに接続された組織として事業活動を行う。</span><span class="sxs-lookup"><span data-stu-id="da76f-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="da76f-109">指定した地理的な場所内で保存データを作成してホストすることによって、データの常駐に関連する要件を満たす。</span><span class="sxs-lookup"><span data-stu-id="da76f-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="da76f-110">中央の場所のユーザーが恩恵を受けているモダンな生産性向上エクスペリエンスと同じエクスペリエンスをサテライトのユーザーに提供する。</span><span class="sxs-lookup"><span data-stu-id="da76f-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="da76f-111">ユーザーのロールが変更された場合に、そのユーザーのコンテンツへのアクセスをそのまま維持した状態で、ユーザーが地理的な場所を超えて移動することを可能にする。</span><span class="sxs-lookup"><span data-stu-id="da76f-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="da76f-112">地理的な場所ごとのポリシーと、サイトごとのデータ損失防止ポリシーの共有を調整する。</span><span class="sxs-lookup"><span data-stu-id="da76f-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="da76f-113">地理的な場所ごとに電子情報開示マネージャー (管理者) を指定し、自分の地理的な場所に合わせた問題に適用される原則を許可する。</span><span class="sxs-lookup"><span data-stu-id="da76f-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="da76f-114">追加の地理的な場所に対して固有の URL 名前空間 (たとえば、ContosoEUR.sharepoint.com) を選択する。</span><span class="sxs-lookup"><span data-stu-id="da76f-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="da76f-115">地域のオンプレミス データを Office 365 の複数地域テナントに統合する。</span><span class="sxs-lookup"><span data-stu-id="da76f-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="da76f-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span><span class="sxs-lookup"><span data-stu-id="da76f-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="da76f-120">Sample multi-geo tenant configuration</span><span class="sxs-lookup"><span data-stu-id="da76f-120">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="da76f-121">北アメリカに中央拠点がある Contoso は、複数地域テナントを使用して、Contoso.com という単一組織の傘下のヨーロッパおよびオーストラリアにあるサテライトの地理的な場所に展開することができます。自分の優先されるデータの場所がヨーロッパに設定されているユーザーはヨーロッパに自分の OneDrive を保持している一方、自分の優先されるデータの場所が北アメリカにあるユーザーは米国に自分の OneDrive を保持しています。</span><span class="sxs-lookup"><span data-stu-id="da76f-121">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Map of the world, showing geo locations for Contoso and other available geo locations](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="da76f-123">3 つの簡単な手順で複数地域機能を入手する</span><span class="sxs-lookup"><span data-stu-id="da76f-123">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="da76f-124">複数地域の構成は次のように簡単です。</span><span class="sxs-lookup"><span data-stu-id="da76f-124">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="da76f-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span><span class="sxs-lookup"><span data-stu-id="da76f-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="da76f-127">サテライトの場所を追加します。</span><span class="sxs-lookup"><span data-stu-id="da76f-127">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="da76f-128">該当する場所用のユーザー アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="da76f-128">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="da76f-129">複数地域の状態と可用性</span><span class="sxs-lookup"><span data-stu-id="da76f-129">Multi-Geo status and availability</span></span>

<span data-ttu-id="da76f-130">OneDrive の複数地域は、現在次の地域と国で提供されています。</span><span class="sxs-lookup"><span data-stu-id="da76f-130">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="da76f-131">アジア太平洋</span><span class="sxs-lookup"><span data-stu-id="da76f-131">Asia-Pacific</span></span>
    
- <span data-ttu-id="da76f-132">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="da76f-132">Australia</span></span>
    
- <span data-ttu-id="da76f-133">カナダ</span><span class="sxs-lookup"><span data-stu-id="da76f-133">Canada</span></span>
    
- <span data-ttu-id="da76f-134">欧州連合 (EMEA)</span><span class="sxs-lookup"><span data-stu-id="da76f-134">European Union (EMEA)</span></span>
    
- <span data-ttu-id="da76f-135">日本</span><span class="sxs-lookup"><span data-stu-id="da76f-135">Japan</span></span>
    
- <span data-ttu-id="da76f-136">英国</span><span class="sxs-lookup"><span data-stu-id="da76f-136">United Kingdom</span></span>
    
- <span data-ttu-id="da76f-137">米国 (北アメリカ)</span><span class="sxs-lookup"><span data-stu-id="da76f-137">United States (North America)</span></span>
    
- <span data-ttu-id="da76f-138">韓国</span><span class="sxs-lookup"><span data-stu-id="da76f-138">Korea</span></span>
      
<span data-ttu-id="da76f-139">今後提供予定の地理的な場所:</span><span class="sxs-lookup"><span data-stu-id="da76f-139">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="da76f-140">フランス</span><span class="sxs-lookup"><span data-stu-id="da76f-140">France</span></span>
- <span data-ttu-id="da76f-141">インド</span><span class="sxs-lookup"><span data-stu-id="da76f-141">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="da76f-142">はじめに</span><span class="sxs-lookup"><span data-stu-id="da76f-142">Getting started</span></span>

<span data-ttu-id="da76f-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="da76f-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
