---
title: OneDrive の複数地域機能および Office 365 の SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: OneDrive と SharePoint Online での複数地域機能を備えた複数の地理的な領域に、Office 365 のプレゼンスを展開します。
ms.openlocfilehash: 7387b267cbc925916b600a112d6911c97a971c36
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="30642-103">OneDrive の複数地域機能および Office 365 の SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="30642-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="30642-p101">OneDrive の複数地域機能と SharePoint Online を使用すれば、組織はその組織の Office 365 のプレゼンスを、その既存のテナント内の複数の地域または国に対して展開することができます。この機能は現在プレビューの段階です。お客様の Microsoft アカウント チームと連絡を取って、OneDrive の複数地域プレビューを入手するためにお客様の多国籍の企業をサインアップしてください。</span><span class="sxs-lookup"><span data-stu-id="30642-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. This feature is currently in preview. Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="30642-107">OneDrive 複数の地域でのプロビジョニングしデータ常駐サービスの要件を満たすために選択した地域の場所にデータを格納して、従業員に最新の生産性エクスペリエンスをグローバルの展開のロックを解除を同時にできます。</span><span class="sxs-lookup"><span data-stu-id="30642-107">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="30642-108">複数地域の機能による組織にとってのメリットを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="30642-108">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="30642-109">複数の地理的な場所にわたる単一の Office 365 テナントで、1 つのグローバルに接続された組織として事業活動を行う。</span><span class="sxs-lookup"><span data-stu-id="30642-109">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="30642-110">指定した地理的な場所内で保存データを作成してホストすることによって、データの常駐に関連する要件を満たす。</span><span class="sxs-lookup"><span data-stu-id="30642-110">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="30642-111">中央の場所のユーザーが恩恵を受けているモダンな生産性向上エクスペリエンスと同じエクスペリエンスをサテライトのユーザーに提供する。</span><span class="sxs-lookup"><span data-stu-id="30642-111">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="30642-112">ユーザーのロールが変更された場合に、そのユーザーのコンテンツへのアクセスをそのまま維持した状態で、ユーザーが地理的な場所を超えて移動することを可能にする。</span><span class="sxs-lookup"><span data-stu-id="30642-112">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="30642-113">地理的な場所ごとのポリシーと、サイトごとのデータ損失防止ポリシーの共有を調整する。</span><span class="sxs-lookup"><span data-stu-id="30642-113">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="30642-114">地理的な場所ごとに電子情報開示マネージャー (管理者) を指定し、自分の地理的な場所に合わせた問題に適用される原則を許可する。</span><span class="sxs-lookup"><span data-stu-id="30642-114">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="30642-115">追加の地理的な場所に対して固有の URL 名前空間 (たとえば、ContosoEUR.sharepoint.com) を選択する。</span><span class="sxs-lookup"><span data-stu-id="30642-115">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="30642-116">地域のオンプレミス データを Office 365 の複数地域テナントに統合する。</span><span class="sxs-lookup"><span data-stu-id="30642-116">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="30642-p102">構成では、複数地域、Office 365 テナントを中央の場所 (既定の場所とも呼ばれます) と 1 つまたは複数のサテライト地域のオフィスで構成されます。複数地域の重要な概念は、単一のテナントにまたがっているいずれかの間で複数の地域の場所です。複数地域のテナントでは、geo の場所、グループ、およびユーザーの情報に関する情報は Azure Active Directory (AAD) でを習得です。テナントについては、集中的にマスターで、各地域の場所に同期するための共有と経験、会社からのすべてのユーザーに関連するが含まれているグローバル認識します。</span><span class="sxs-lookup"><span data-stu-id="30642-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="30642-121">複数地域のテナント構成の例</span><span class="sxs-lookup"><span data-stu-id="30642-121">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="30642-122">北アメリカに中央拠点がある Contoso は、複数地域テナントを使用して、Contoso.com という単一組織の傘下のヨーロッパおよびオーストラリアにあるサテライトの地理的な場所に展開することができます。自分の優先されるデータの場所がヨーロッパに設定されているユーザーはヨーロッパに自分の OneDrive を保持している一方、自分の優先されるデータの場所が北アメリカにあるユーザーは米国に自分の OneDrive を保持しています。</span><span class="sxs-lookup"><span data-stu-id="30642-122">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Contoso 社の地域の場所とその他の利用可能な地域の場所を示す、世界中のマップ](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="30642-124">3 つの簡単な手順で複数地域機能を入手する</span><span class="sxs-lookup"><span data-stu-id="30642-124">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="30642-125">複数地域の構成は次のように簡単です。</span><span class="sxs-lookup"><span data-stu-id="30642-125">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="30642-p103">_Office 365 の機能を複数の地域_のサービス プランを追加するのには、アカウント ・ チームと協力します。必要なライセンス数を追加するには説明します。</span><span class="sxs-lookup"><span data-stu-id="30642-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="30642-128">サテライトの場所を追加します。</span><span class="sxs-lookup"><span data-stu-id="30642-128">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="30642-129">該当する場所用のユーザー アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="30642-129">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="30642-130">複数地域の状態と可用性</span><span class="sxs-lookup"><span data-stu-id="30642-130">Multi-Geo status and availability</span></span>

<span data-ttu-id="30642-131">OneDrive の複数地域は、現在次の地域と国で提供されています。</span><span class="sxs-lookup"><span data-stu-id="30642-131">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="30642-132">アジア太平洋</span><span class="sxs-lookup"><span data-stu-id="30642-132">Asia-Pacific</span></span>
    
- <span data-ttu-id="30642-133">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="30642-133">Australia</span></span>
    
- <span data-ttu-id="30642-134">カナダ</span><span class="sxs-lookup"><span data-stu-id="30642-134">Canada</span></span>
    
- <span data-ttu-id="30642-135">欧州連合 (EMEA)</span><span class="sxs-lookup"><span data-stu-id="30642-135">European Union (EMEA)</span></span>
    
- <span data-ttu-id="30642-136">日本</span><span class="sxs-lookup"><span data-stu-id="30642-136">Japan</span></span>
    
- <span data-ttu-id="30642-137">英国</span><span class="sxs-lookup"><span data-stu-id="30642-137">United Kingdom</span></span>
    
- <span data-ttu-id="30642-138">米国 (北アメリカ)</span><span class="sxs-lookup"><span data-stu-id="30642-138">United States (North America)</span></span>
    
- <span data-ttu-id="30642-139">韓国</span><span class="sxs-lookup"><span data-stu-id="30642-139">Korea</span></span>
      
<span data-ttu-id="30642-140">今後提供予定の地理的な場所:</span><span class="sxs-lookup"><span data-stu-id="30642-140">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="30642-141">フランス</span><span class="sxs-lookup"><span data-stu-id="30642-141">France</span></span>
- <span data-ttu-id="30642-142">インド</span><span class="sxs-lookup"><span data-stu-id="30642-142">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="30642-143">作業の開始</span><span class="sxs-lookup"><span data-stu-id="30642-143">Getting started</span></span>

<span data-ttu-id="30642-p104">開始する OneDrive を持つ複数の地域のビジネス、最初のステップは、[複数の地域のビジネス環境で、OneDrive を計画](plan-for-multi-geo.md)することです。次へ] は、[複数地域の環境を管理する方法について説明](administering-a-multi-geo-environment.md)、および[、ユーザーが複数の地域の環境を発生する方法](multi-geo-user-experience.md)です。OneDrive のビジネス マルチ ・地域、[複数地域でのテナントを構成する](multi-geo-tenant-configuration.md)ように設定する準備ができたら、[既存の OneDrive サイトの新しい地域の位置を移動](move-onedrive-between-geo-locations.md)し、[検索を設定](configure-search-for-multi-geo.md)します。</span><span class="sxs-lookup"><span data-stu-id="30642-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
