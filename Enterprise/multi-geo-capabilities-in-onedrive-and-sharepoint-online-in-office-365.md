---
title: Office 365 の OneDrive の複数地域機能
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: OneDrive Online の複数地域機能を使用して、複数の地域に Office 365 のプレゼンスを展開します。
ms.openlocfilehash: f89bfe7cb9a287200591746dc6d22430cd6eed1b
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "30052991"
---
# <a name="multi-geo-capabilities-in-onedrive-in-office-365"></a><span data-ttu-id="bc2c6-103">Office 365 の OneDrive の複数地域機能</span><span class="sxs-lookup"><span data-stu-id="bc2c6-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="bc2c6-p101">OneDrive Online の複数地域機能を使用すれば、組織はその組織の Office 365 のプレゼンスを、その既存のテナント内の複数の地域または国に対して展開することができます。お客様の Microsoft アカウント チームに問い合わせて、OneDrive for Business 複数地域用にお客様の多国籍企業のサインアップを行ってください。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-p101">With Multi-Geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="bc2c6-106">OneDrive の複数地域機能を使用すれば、データの常駐に関連する要件を満たすと同時に、モダンな生産性向上エクスペリエンスのグローバル展開を要員に開放するために、選択した地理的な場所に保存 (休眠) データをプロビジョニングして蓄えることができます。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="bc2c6-107">複数地域機能が組織にどのようにメリットをもたらすことができるかを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="bc2c6-108">複数の地理的な場所にわたる単一の Office 365 テナントで、1 つのグローバルに接続された組織として事業活動を行う。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="bc2c6-109">指定した地理的な場所内で保存データを作成してホストすることによって、データの常駐に関連する要件を満たす。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="bc2c6-110">中央の場所のユーザーが恩恵を受けているモダンな生産性向上エクスペリエンスと同じエクスペリエンスをサテライトのユーザーに提供する。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="bc2c6-111">ユーザーのロールが変更された場合に、そのユーザーのコンテンツへのアクセスをそのまま維持した状態で、ユーザーが地理的な場所を超えて移動することを可能にする。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="bc2c6-112">地理的な場所ごとのポリシーと、サイトごとのデータ損失防止ポリシーの共有を調整する。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="bc2c6-113">地理的な場所ごとに電子情報開示マネージャー (管理者) を指定し、自分の地理的な場所に合わせた問題に適用される原則を許可する。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="bc2c6-114">追加の地理的な場所に対して固有の URL 名前空間 (たとえば、ContosoEUR.sharepoint.com) を選択する。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="bc2c6-115">地域のオンプレミス データを Office 365 の複数地域テナントに統合する。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="bc2c6-p102">Multi-Geo 構成では、Office 365 テナントは中央の場所 (Office 365 サブスクリプションが最初にプロビジョニングされた場所) と、1 つ以上のサテライトの地理的な場所から構成されます。Multi-Geo の重要な概念は、単一のテナントが複数の地理的な場所全体に及ぶことです。複数地域テナント内では、地理的な場所、グループ、およびユーザー情報に関する情報が、Azure Active Directory (AAD) 内でマスター管理されます。テナント情報が集中的にマスター管理され、個々の地理的な場所に同期されるので、その企業のすべてのユーザーが関わる共有とエクスペリエンスにグローバルな情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="bc2c6-120">ビデオ: Office 365 複数地域の紹介</span><span class="sxs-lookup"><span data-stu-id="bc2c6-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="bc2c6-121">3 つの簡単な手順で複数地域機能を入手する</span><span class="sxs-lookup"><span data-stu-id="bc2c6-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="bc2c6-122">複数地域の構成は次のように簡単です。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="bc2c6-p103">アカウント チームと協力して、_Office 365 複数地域機能_サービス プランを追加します。チームから、必要な数のライセンスを追加するように説明があります。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="bc2c6-125">サテライトの場所を追加します。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="bc2c6-126">該当する場所用のユーザー アカウントを構成します。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="bc2c6-127">複数地域の状態と可用性</span><span class="sxs-lookup"><span data-stu-id="bc2c6-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="bc2c6-128">OneDrive の複数地域は、現在次の地域と国で提供されています。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="bc2c6-129">アジア太平洋</span><span class="sxs-lookup"><span data-stu-id="bc2c6-129">Asia-Pacific</span></span>

- <span data-ttu-id="bc2c6-130">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="bc2c6-130">Australia</span></span>

- <span data-ttu-id="bc2c6-131">カナダ</span><span class="sxs-lookup"><span data-stu-id="bc2c6-131">Canada</span></span>

- <span data-ttu-id="bc2c6-132">欧州連合 (EMEA)</span><span class="sxs-lookup"><span data-stu-id="bc2c6-132">European Union (EMEA)</span></span>

- <span data-ttu-id="bc2c6-133">フランス</span><span class="sxs-lookup"><span data-stu-id="bc2c6-133">France</span></span>

- <span data-ttu-id="bc2c6-134">インド</span><span class="sxs-lookup"><span data-stu-id="bc2c6-134">India</span></span>

- <span data-ttu-id="bc2c6-135">日本</span><span class="sxs-lookup"><span data-stu-id="bc2c6-135">Japan</span></span>

- <span data-ttu-id="bc2c6-136">英国</span><span class="sxs-lookup"><span data-stu-id="bc2c6-136">United Kingdom</span></span>

- <span data-ttu-id="bc2c6-137">米国 (北アメリカ)</span><span class="sxs-lookup"><span data-stu-id="bc2c6-137">United States (North America)</span></span>

- <span data-ttu-id="bc2c6-138">韓国</span><span class="sxs-lookup"><span data-stu-id="bc2c6-138">Korea</span></span>

## <a name="getting-started"></a><span data-ttu-id="bc2c6-139">はじめに</span><span class="sxs-lookup"><span data-stu-id="bc2c6-139">Getting started</span></span>

<span data-ttu-id="bc2c6-p104">OneDrive for Business 複数地域を開始するには、まず [OneDrive for Business 複数地域の環境を計画](plan-for-multi-geo.md)します。次に、[複数地域の環境の管理について](administering-a-multi-geo-environment.md)と、[ユーザーが複数地域の環境を体験する方法](multi-geo-user-experience.md)について説明します。OneDrive for Business 複数地域を設定する準備ができたら、[複数地域のテナントを構成](multi-geo-tenant-configuration.md)し、[既存の OneDrive サイトを新しい場所に移動](move-onedrive-between-geo-locations.md)して、[検索を設定](configure-search-for-multi-geo.md)します。</span><span class="sxs-lookup"><span data-stu-id="bc2c6-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
