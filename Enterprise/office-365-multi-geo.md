---
title: Office 365 Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Office 365 Multi-Geo を使用して、複数の地域に Office 365 のプレゼンスを展開します。
ms.openlocfilehash: e216f61806ea5d648519ac7217acf7dbaddd1419
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934044"
---
# <a name="office-365-multi-geo"></a><span data-ttu-id="424b6-103">Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="424b6-103">Video: Introducing Office 365 Multi-Geo</span></span>

<span data-ttu-id="424b6-104">Office 365 Multi-Geo を使用すれば、組織はその組織の Office 365 のプレゼンスを、その既存のテナント内の複数の地域または国に対して展開することができます。</span><span class="sxs-lookup"><span data-stu-id="424b6-104">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="424b6-105">お客様の Microsoft アカウント チームと連絡を取って、Office 365 Multi-Geo を入手するためにお客様の多国籍の企業をサインアップしてください。</span><span class="sxs-lookup"><span data-stu-id="424b6-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="424b6-106">Office 365 Multi-Geo を使用すれば、データの常駐に関連する要件を満たすと同時に、モダンな生産性向上エクスペリエンスのグローバル展開を従業員が利用できるようにするために、選択した地理的な場所に保存 (休眠) データをプロビジョニングして蓄えることができます。</span><span class="sxs-lookup"><span data-stu-id="424b6-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="424b6-107">ビデオ: Office 365 Multi-Geo の紹介</span><span class="sxs-lookup"><span data-stu-id="424b6-107">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="424b6-108">Multi-Geo 環境では、Office 365 テナントは中央の場所 (Office 365 サブスクリプションが最初にプロビジョニングされた場所) と 1 つ以上のサテライトの場所で構成されています。</span><span class="sxs-lookup"><span data-stu-id="424b6-108">In a Multi-Geo environment, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="424b6-109">複数地域テナント内では、地理的な場所、グループ、およびユーザー情報に関する情報が、Azure Active Directory (AAD) 内でマスター管理されます。</span><span class="sxs-lookup"><span data-stu-id="424b6-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD).</span></span> <span data-ttu-id="424b6-110">テナント情報が集中的にマスター管理され、個々の地理的な場所に同期されるので、その企業のすべてのユーザーが関わる共有とエクスペリエンスにグローバルな情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="424b6-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![SharePoint 管理センター メニューの複数地域マップのスクリーンショット](media/multi-geo-world-map.png)

<span data-ttu-id="424b6-112">Office 365 Multi-Geo は、パフォーマンスの最適化を主要目的とした設計ではなく、データの常駐に関する要件を満たすように設計されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="424b6-112">Note that Office 365 Multi-Geo is not designed for performance optimization cases, it is designed to meet data residency requirements. For information about performance optimization for Office 365, see Network planning and performance tuning for Office 365 or contact your support group.</span></span> <span data-ttu-id="424b6-113">Office 365 のパフォーマンスを最適化する方法については、「[Office 365 のネットワーク計画とパフォーマンス チューニング](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)」を参照するか、サポート グループにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="424b6-113">Note that Office 365 Multi-Geo is not designed for performance optimization cases, it is designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="424b6-114">用語</span><span class="sxs-lookup"><span data-stu-id="424b6-114">Terminology</span></span>

<span data-ttu-id="424b6-115">Office 365 Multi-Geo の説明に使用される重要な用語を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="424b6-115">Here are the key terms used in describing Office 365 Multi-Geo:</span></span>

- <span data-ttu-id="424b6-116">**中央の場所**のテナントが最初にプロビジョニングされた地域の場所です。</span><span class="sxs-lookup"><span data-stu-id="424b6-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="424b6-117">**地域管理者** - 指定された 1 つ以上のサテライトの場所を管理できる管理者。</span><span class="sxs-lookup"><span data-stu-id="424b6-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="424b6-118">**地域コード** - 特定の地域の場所を表す 3 文字のコード。</span><span class="sxs-lookup"><span data-stu-id="424b6-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="424b6-119">**地域の場所** - Exchange メールボックス、OneDrive サイト、SharePoint サイトなど、データをホストする複数地域テナントで使用できる地理的な場所。</span><span class="sxs-lookup"><span data-stu-id="424b6-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="424b6-120">**優先されるデータの場所 (PDL)** - 管理者が設定したユーザー プロパティであり、ユーザーの Exchange メールボックスと OneDrive がプロビジョニングされる地域の場所を示します。</span><span class="sxs-lookup"><span data-stu-id="424b6-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="424b6-121">PDL では、ユーザーによって作成された SharePoint サイトのプロビジョニング場所も決定されます。</span><span class="sxs-lookup"><span data-stu-id="424b6-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="424b6-122">**サテライトの場所** - 地理機能に対応している Office 365 ワークロード (SharePoint、OneDrive、および Exchange) が複数地域テナントで有効になっている地域の場所。</span><span class="sxs-lookup"><span data-stu-id="424b6-122">**Satellite location** – The geo locations where the geo-aware Office 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="424b6-123">**テナント** - Office 365 における組織の表現。通常、1 つ以上のドメインが関連付けられています (例: contoso.com)。</span><span class="sxs-lookup"><span data-stu-id="424b6-123">Tenant – An organization's representation in the Office 365 cloud which typically has one or more domains associated with it (for example, .</span></span>

## <a name="office-365-multi-geo-availability"></a><span data-ttu-id="424b6-124">Office 365 Multi-Geo の利用可能地域</span><span class="sxs-lookup"><span data-stu-id="424b6-124">Office 365 Multi-Geo availability</span></span>

<span data-ttu-id="424b6-125">現在、Office 365 Multi-Geo は次の地域と国で提供されています。</span><span class="sxs-lookup"><span data-stu-id="424b6-125">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="424b6-126">はじめに</span><span class="sxs-lookup"><span data-stu-id="424b6-126">Getting started</span></span>

<span data-ttu-id="424b6-127">以下の手順に従って複数地域を開始しましょう。</span><span class="sxs-lookup"><span data-stu-id="424b6-127">Follow these steps to get started:</span></span>

1. <span data-ttu-id="424b6-p105">アカウント チームと協力して、_Office 365 複数地域機能_サービス プランを追加します。チームから、必要な数のライセンスを追加するように説明があります。</span><span class="sxs-lookup"><span data-stu-id="424b6-p105">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>

   <span data-ttu-id="424b6-130">Office 365 Multi-Geo の使用を開始するには、事前に Microsoft が複数地域サポート用に Exchange Online テナントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="424b6-130">Before you can start using Office 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="424b6-131">この 1 回限りの構成プロセスは、*Office 365 の複数地域機能*サービス プランを注文し、ライセンスがテナントに表示された後に開始されます。</span><span class="sxs-lookup"><span data-stu-id="424b6-131">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Office 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="424b6-132">Multi-Geo ライセンスが適用されると、[Office 365 メッセージ センター](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093)に通知が送信され、その後、Office 365 Multi-Geo 機能の設定と使用を開始できます。</span><span class="sxs-lookup"><span data-stu-id="424b6-132">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Office 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="424b6-133">「[OneDrive for Business 複数地域の計画](plan-for-multi-geo.md)」を参照します。</span><span class="sxs-lookup"><span data-stu-id="424b6-133">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="424b6-134">[複数地域環境の管理](administering-a-multi-geo-environment.md)および[環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)について確認します。</span><span class="sxs-lookup"><span data-stu-id="424b6-134">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="424b6-135">Office 365 Multi-Geo のセットアップ準備ができたら、[複数地域用のテナントを構成します](multi-geo-tenant-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="424b6-135">When you are ready to set up Office 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="424b6-136">[検索を設定します](configure-search-for-multi-geo.md)。</span><span class="sxs-lookup"><span data-stu-id="424b6-136">[](configure-search-for-multi-geo.md)Set up people search</span></span>

## <a name="see-also"></a><span data-ttu-id="424b6-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="424b6-137">See also</span></span>

[<span data-ttu-id="424b6-138">Aka.ms/GoMultiGeo </span><span class="sxs-lookup"><span data-stu-id="424b6-138">Aka.ms/GoMultiGeo </span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="424b6-139">OneDrive および SharePoint Online の複数地域機能</span><span class="sxs-lookup"><span data-stu-id="424b6-139">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365.md)

[<span data-ttu-id="424b6-140">Exchange Online の複数地域機能</span><span class="sxs-lookup"><span data-stu-id="424b6-140">NoteFor information on Multi-Geo Capabilities, see Multi-Geo Capabilities in Exchange Online.</span></span>](multi-geo-capabilities-in-exchange-online.md)
