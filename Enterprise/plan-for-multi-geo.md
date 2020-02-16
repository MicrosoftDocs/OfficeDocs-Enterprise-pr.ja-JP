---
title: Office 365 Multi-Geo のプラン
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Office 365 Multi-Geo 複数地域、複数地域のしくみ、およびデータ ストレージに使用できる地域の場所について説明します。
ms.openlocfilehash: f3bc2b43181bb4479c0f3b9c65ed4bcd5b1f9b38
ms.sourcegitcommit: 265cc03b600e9015a44c60c3f8bb9075b1c20888
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "41974229"
---
# <a name="plan-for-office-365-multi-geo"></a><span data-ttu-id="89190-103">Office 365 Multi-Geo のプラン</span><span class="sxs-lookup"><span data-stu-id="89190-103">Plan for Office 365 Multi-Geo</span></span>

<span data-ttu-id="89190-104">このガイドは、データ所在地の要件を満たすように、Office 365 Multi-Geo テナントを企業の所在地に応じて追加の地域に展開するための準備を整える多国籍企業 (MNC) の管理者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="89190-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their Office 365 tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="89190-105">複数地域構成では、Office 365 テナントは中央の場所と、1 つ以上のサテライトの地理的な場所から構成されます。</span><span class="sxs-lookup"><span data-stu-id="89190-105">In a multi-geo configuration, your Office 365 tenant consists of a central location and one or more satellite locations.</span></span> <span data-ttu-id="89190-106">これは、複数の地域にまたがる単一のテナントです。</span><span class="sxs-lookup"><span data-stu-id="89190-106">This is a single tenant that spans across multiple geo locations.</span></span> <span data-ttu-id="89190-107">地理的な場所を含むテナント情報は、Azure Active Directory (AAD) 内で管理されます。</span><span class="sxs-lookup"><span data-stu-id="89190-107">Your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span>

<span data-ttu-id="89190-108">この構成の基本的な概念についての理解を助けるために、複数地域に関するいくつかの主要な用語を示します。</span><span class="sxs-lookup"><span data-stu-id="89190-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="89190-109">**テナント** - Office 365 における組織の表現。通常、1 つ以上のドメインが関連付けられています (例: https://contoso.sharepoint.com))。</span><span class="sxs-lookup"><span data-stu-id="89190-109">**Tenant** – An organization's representation in Office 365 which typically has one or more domains associated with it (for example, https://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="89190-110">**地理的位置** – Office 365 テナントのデータをホストできる地理的な場所。</span><span class="sxs-lookup"><span data-stu-id="89190-110">**Geo locations** – The geographic locations available to host data in an Office 365 tenant.</span></span>

-   <span data-ttu-id="89190-111">**サテライトの場所** – Office 365 テナントのデータをホストするように構成した地理的な場所。</span><span class="sxs-lookup"><span data-stu-id="89190-111">**Satellite locations** – The additional geo locations that you have configured to host data in your Office 365 tenant.</span></span> <span data-ttu-id="89190-112">複数地域テナントは、複数の地域の場所 (たとえば、北米とヨーロッパ) に展開します。</span><span class="sxs-lookup"><span data-stu-id="89190-112">Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="89190-113">**優先するデータの場所 (PDL)** – 個別のユーザーの Exchange および OneDrive データが保存される地域の場所。</span><span class="sxs-lookup"><span data-stu-id="89190-113">**Preferred Data Location (PDL)** – The geo location where an individual user's Exchange and OneDrive data is stored.</span></span> <span data-ttu-id="89190-114">この場所は、テナントに対して構成されている地理的位置のいずれかに管理者が設定できます。</span><span class="sxs-lookup"><span data-stu-id="89190-114">This can be set by the administrator to any of the geo locations that have been configured for the tenant.</span></span> <span data-ttu-id="89190-115">既に OneDrive サイトを所有しているユーザーの PDL を変更しても、そのユーザーの OneDrive データは新しい地域の場所に自動的には移動されない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="89190-115">Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically.</span></span> <span data-ttu-id="89190-116">詳細については、「[別の地域の場所に OneDrive ライブラリを移動する](move-onedrive-between-geo-locations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89190-116">See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span> <span data-ttu-id="89190-117">Exchange メールボックスがある場合、メールボックスは自動的に新しい優先するデータの場所に移動されます。</span><span class="sxs-lookup"><span data-stu-id="89190-117">If they have an Exchange mailbox, the mailbox is moved to the new preferred data location automatically.</span></span>

<span data-ttu-id="89190-118">複数地域の有効化に必要になる主な 4 つの手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="89190-118">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="89190-119">アカウント チームと協力して、_Office 365 の複数地域機能_サービス プランを追加します。</span><span class="sxs-lookup"><span data-stu-id="89190-119">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="89190-120">サテライトの場所を選択して、その場所をテナントに追加します。</span><span class="sxs-lookup"><span data-stu-id="89190-120">Choose your desired satellite location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="89190-121">ユーザーの優先するデータの場所を適切なサテライトの場所に設定します。</span><span class="sxs-lookup"><span data-stu-id="89190-121">Set your users' preferred data location to the desired satellite location.</span></span> <span data-ttu-id="89190-122">ユーザーに新しい OneDrive サイトまたは Exchange メールボックスがプロビジョニングされると、そのサイトがユーザーの PDL にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="89190-122">When a new OneDrive site or Exchange mailbox is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="89190-123">ユーザーの既存の OneDrive サイトを中央の場所から、そのユーザーの優先するデータの場所に移行します (必要な場合)。</span><span class="sxs-lookup"><span data-stu-id="89190-123">Migrate your users' existing OneDrive sites from the central location to their preferred data location as needed.</span></span> <span data-ttu-id="89190-124">(ユーザーの PDL を設定すると、Exchange メールボックスは自動的に移行されます。)</span><span class="sxs-lookup"><span data-stu-id="89190-124">(Exchange mailboxes are migrated automatically when you set a user's PDL.)</span></span>

<span data-ttu-id="89190-125">それぞれの手順の詳細については、「[Office 365 Multi-Geo の構成](multi-geo-tenant-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89190-125">See [Configure Office 365 Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89190-126">Office 365 Multi-Geo は、パフォーマンスの最適化を目的とした設計ではなく、データの常駐に関する要件を満たすように設計されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="89190-126">Note that Office 365 Multi-Geo is not designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="89190-127">Office 365 のパフォーマンスを最適化する方法については、「[Office 365 のネットワーク計画とパフォーマンス チューニング](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)」を参照するか、サポート グループにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="89190-127">For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="89190-128">次に示す場所は、OneDrive、SharePoint サイト、Exchange のメールボックスをホストできるサテライトの場所として構成できます。</span><span class="sxs-lookup"><span data-stu-id="89190-128">You can configure any of the following locations to be satellite locations where you can host OneDrive and SharePoint sites, and Exchange mailboxes.</span></span> <span data-ttu-id="89190-129">Multi-Geo の計画の際には、Office 365 テナントに追加する場所のリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="89190-129">As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant.</span></span> <span data-ttu-id="89190-130">1 つまたは 2 つのサテライトの場所から初めて、必要に応じて段階的に別の地域の場所に拡張することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89190-130">We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

<span data-ttu-id="89190-p108">複数地域を構成するときは、Office 365 への移行と同時にオンプレミスのインフラストラクチャを統合する機会だと考えてください。たとえば、シンガポールとマレーシアにオンプレミス ファームがある場合、データ所在地の要件で許可されているときには、それらのファームを APC サテライトの場所に統合できます。</span><span class="sxs-lookup"><span data-stu-id="89190-p108">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="89190-133">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="89190-133">Best practices</span></span>

<span data-ttu-id="89190-134">いくつかの初期テストのために Office 365 のテスト用ユーザーを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89190-134">We recommend that you create a test user in Office 365 to do some initial testing.</span></span> <span data-ttu-id="89190-135">Office 365 Multi-Geo に実稼働ユーザーをオンボードする前に、このテスト用ユーザーでいくつかのテストと検証の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="89190-135">We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into Office 365 Multi-Geo.</span></span>

<span data-ttu-id="89190-136">テスト用ユーザーでのテストが完了したら、新しい地域の場所で最初に OneDrive および Exchange を使用するパイロット グループを IT 部門 (など) から選択します。</span><span class="sxs-lookup"><span data-stu-id="89190-136">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive and Exchange in a new geo location.</span></span> <span data-ttu-id="89190-137">この最初のグループには、OneDrive をまだ所有していないユーザーを選択します。</span><span class="sxs-lookup"><span data-stu-id="89190-137">For this first group, select users who do not yet have a OneDrive.</span></span> <span data-ttu-id="89190-138">この初期グループのユーザーは 5 人未満にして、バッチ ロールアウトのアプローチに従って段階的に増員していきます。</span><span class="sxs-lookup"><span data-stu-id="89190-138">We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="89190-p111">各ユーザーには*優先するデータの場所* (PDL) を設定しておく必要があります。これにより、それぞれのユーザーの OneDrive をプロビジョニングする地域の場所を Office 365 が判断できるようになります。ユーザーの優先するデータの場所は、選択したサテライトの場所のいずれか、または中央の場所と一致する必要があります。PDL フィールドは必須ではありませんが、すべてのユーザーの PDL を設定することをお勧めします。PDL のないユーザーのワークロードは中央の場所にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="89190-p111">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user's preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location.</span></span>

<span data-ttu-id="89190-p112">ユーザーのリストを作成して、ユーザー プリンシパル名 (UPN) と適切な優先するデータの場所の地域コードを含めます。テスト用ユーザーと初期パイロット グループを含めて開始します。このリストは、構成の手順で必要になります。</span><span class="sxs-lookup"><span data-stu-id="89190-p112">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You'll need this list for the configuration procedures.</span></span>

<span data-ttu-id="89190-146">ユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期される場合、同期されるユーザーの優先されるデータの場所を Active Directory 属性にして、Azure Active Directory Connect を使用して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89190-146">If your users are synchronized from an on-premises Active Directory system to Azure Active Directory, you must set the preferred data location as an Active Directory attribute and synchronize it by using Azure Active Directory Connect.</span></span> <span data-ttu-id="89190-147">同期されるユーザーの優先されるデータの場所は、Azure AD PowerShell を使用して直接構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="89190-147">You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell.</span></span> <span data-ttu-id="89190-148">AD で PDL を設定して同期する手順については、「[Azure Active Directory Connect 同期: Office 365 リソースの優先されるデータの場所を構成する](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89190-148">The steps to set up PDL in Active Directory and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="89190-p114">複数地域テナントの管理は、複数地域ではないテナントの管理と異なることがあり、SharePoint および OneDrive の設定と機能の多くが複数地域に対応しています。構成を進める前に、「[複数地域環境の管理](administering-a-multi-geo-environment.md)」を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89190-p114">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="89190-151">複数地域環境でのエンド ユーザーのエクスペリエンスの詳細については、「[複数地域環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89190-151">Read [User experience in a mult-geo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="89190-152">Office 365 Multi-Geo 複数地域の構成を開始する場合は、「[Office 365 Multi-Geoの構成](multi-geo-tenant-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89190-152">To get started configuring Office 365 Multi-Geo, see [Configure Office 365 Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="89190-153">構成の完了後は、ユーザーが優先するデータの場所から作業するために必要になる、[ユーザーの OneDrive ライブラリの移行](move-onedrive-between-geo-locations.md)を必ず実行してください。</span><span class="sxs-lookup"><span data-stu-id="89190-153">Once you've completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
