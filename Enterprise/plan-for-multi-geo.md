---
title: ビジネスの複数の地域の OneDrive の計画
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: ビジネスの複数の地域、複数地域のしくみ、およびどのような地域の場所は、データ ストレージに使用できるは、OneDrive について説明します。
ms.openlocfilehash: d7d6cfbbff4cf0ec2516f2506946c2832d96b3f2
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="597f7-103">ビジネスの複数の地域の OneDrive の計画</span><span class="sxs-lookup"><span data-stu-id="597f7-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="597f7-104">このガイドは、SharePoint Online のテナント データの常駐サービスの要件を満たすために会社の存在に基づいてその他の地域に展開する準備をしている多国籍企業 (MNCs) の管理者向けです。</span><span class="sxs-lookup"><span data-stu-id="597f7-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="597f7-p101">OneDrive の複数の地域の設定を Office 365 テナントの中央の場所 (既定の場所とも呼ばれます) と 1 つまたは複数のサテライト地域の場所で構成されます。これは、複数の地域の拠点にまたがる単一のテナントです。OneDrive 複数の地域では、テナントについては、地域を含むには、Azure Active Directory (AAD) ではマスターです。</span><span class="sxs-lookup"><span data-stu-id="597f7-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="597f7-108">構成の基本的な概念を理解するのに役立ついくつかのキーの複数地域用語を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="597f7-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="597f7-109">**テナント**– 通常、それに関連付けられている 1 つまたは複数のドメインには、Office 365 の雲の中の組織の形式 (たとえば、 http://contoso.sharepoint.com)。</span><span class="sxs-lookup"><span data-stu-id="597f7-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="597f7-p102">**Geo の場所**テナントのデータをホストしている地理的な場所です。テナントの複数地域にまたがる複数の地域の場所、北アメリカやヨーロッパなどの。</span><span class="sxs-lookup"><span data-stu-id="597f7-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="597f7-112">**許可されるデータの場所 (ADL)** – geo の場所を OneDrive と SharePoint のデータをホストする、テナントが構成されています。</span><span class="sxs-lookup"><span data-stu-id="597f7-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="597f7-p103">**優先データの場所 (PDL)** – 個々 のユーザーの OneDrive のデータが保存されている地域の場所です。テナントに対して構成されている許可されるデータの場所のいずれかを管理者が設定できます。OneDrive サイトを既に持っているユーザーは PDL を変更する場合、OneDrive のデータは地域の別の場所に自動的に移動されませんに注意してください。詳細については、[別の地理的な場所に OneDrive ライブラリを移動](move-onedrive-between-geo-locations.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="597f7-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="597f7-117">複数地域を有効にするには、4 つの主要手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="597f7-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="597f7-118">_Office 365 の機能を複数の地域_のサービス プランを追加するのには、アカウント ・ チームと協力します。</span><span class="sxs-lookup"><span data-stu-id="597f7-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="597f7-119">目的の地域の場所の衛星し、テナントに追加を選択します。</span><span class="sxs-lookup"><span data-stu-id="597f7-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="597f7-p104">必要なサテライト地域の場所に、ユーザーの希望するデータの場所を設定します。ユーザーの新しい OneDrive サイトを準備すると、ときに、PDL にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="597f7-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="597f7-122">ホームの場所から、ユーザーの既存の OneDrive サイトを必要に応じて、希望するデータの場所に移行します。</span><span class="sxs-lookup"><span data-stu-id="597f7-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="597f7-123">これらの各手順の詳細については[OneDrive を構成する複数の地域のビジネス](multi-geo-tenant-configuration.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="597f7-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="597f7-p105">Office 365 の複数の地域の機能は、パフォーマンスの最適化の場合に設計されていないデータの常駐サービスの要件を満たすよう設計されていますが、注意してください。Office 365 のパフォーマンスを最適化する方法については、[ネットワークの計画と Office 365 のパフォーマンスの調整](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)を参照するか、サポート グループに問い合わせてください。</span><span class="sxs-lookup"><span data-stu-id="597f7-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="597f7-p106">OneDrive ファイルをホストしているサテライト地域の場所にするのには、次の場所のいずれかを設定できます。複数地域のことを計画する際、Office 365 テナントに追加する場所の一覧を確認します。お勧め 1 つまたは 2 つのサテライト オフィスで始まると、複数の地域の場所に徐々 に拡張が必要な場合です。</span><span class="sxs-lookup"><span data-stu-id="597f7-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="597f7-129"><strong>場所</strong></span><span class="sxs-lookup"><span data-stu-id="597f7-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="597f7-130"><strong>コード</strong></span><span class="sxs-lookup"><span data-stu-id="597f7-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="597f7-131">アジア太平洋</span><span class="sxs-lookup"><span data-stu-id="597f7-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="597f7-132">APC</span><span class="sxs-lookup"><span data-stu-id="597f7-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="597f7-133">ヨーロッパ東中央//アフリカ</span><span class="sxs-lookup"><span data-stu-id="597f7-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="597f7-134">EUR</span><span class="sxs-lookup"><span data-stu-id="597f7-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="597f7-135">北アメリカ</span><span class="sxs-lookup"><span data-stu-id="597f7-135">North America</span></span></td>
<td align="left"><span data-ttu-id="597f7-136">名</span><span class="sxs-lookup"><span data-stu-id="597f7-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="597f7-137">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="597f7-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="597f7-138">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="597f7-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="597f7-139">カナダ</span><span class="sxs-lookup"><span data-stu-id="597f7-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="597f7-140">できます。</span><span class="sxs-lookup"><span data-stu-id="597f7-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="597f7-141">日本</span><span class="sxs-lookup"><span data-stu-id="597f7-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="597f7-142">日本語版</span><span class="sxs-lookup"><span data-stu-id="597f7-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="597f7-143">韓国</span><span class="sxs-lookup"><span data-stu-id="597f7-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="597f7-144">KOR</span><span class="sxs-lookup"><span data-stu-id="597f7-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="597f7-145">英国</span><span class="sxs-lookup"><span data-stu-id="597f7-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="597f7-146">GBR</span><span class="sxs-lookup"><span data-stu-id="597f7-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="597f7-147">今後提供予定の地理的な場所:</span><span class="sxs-lookup"><span data-stu-id="597f7-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="597f7-148">フランス</span><span class="sxs-lookup"><span data-stu-id="597f7-148">France</span></span>
- <span data-ttu-id="597f7-149">インド</span><span class="sxs-lookup"><span data-stu-id="597f7-149">India</span></span>

<span data-ttu-id="597f7-p107">複数地域を構成する場合は、Office 365 に移行するときに、オンプレミス インフラストラクチャを統合する機会を活用して検討してください。など、シンガポールとマレーシアでの設置のファームがあれば、しを統合できますに APC のサテライトの場所に常駐要件のデータを許可するよう指定しました。</span><span class="sxs-lookup"><span data-stu-id="597f7-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="597f7-152">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="597f7-152">Best practices</span></span>

<span data-ttu-id="597f7-p108">初期テストを実行するのには Office 365 では、テスト ユーザーを作成することをお勧めします。みましょういくつかのテストと検証の手順をこのユーザーに OneDrive の複数の地域の機能をオンボードの運用環境のユーザーに続行する前にします。</span><span class="sxs-lookup"><span data-stu-id="597f7-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="597f7-p109">テスト ユーザーでテストが完了したら、おそらく最初に新規の地理的な場所で OneDrive を使用する: IT 部門から、パイロット グループを選択します。この最初のグループ、OneDrive を所有していないユーザーを選択します。この最初のグループ内の 5 つまでの人をお勧めしてバッチ処理の展開方法を段階的に展開します。</span><span class="sxs-lookup"><span data-stu-id="597f7-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="597f7-p110">各ユーザーには、*希望するデータの場所*(PDL)、OneDrive を提供する地域の場所に Office 365 を判断できますように設定が必要です。ユーザーの希望するデータの場所を選択したサテライトの場所や、中央の場所のいずれかに一致しなければなりません。PDL のフィールドは必須ではありませんが、PDL は、すべてのユーザーに対して設定することをお勧めします。PDL のないユーザーの作業負荷は複数地域のロジックに基づいて、中央の場所で準備します。</span><span class="sxs-lookup"><span data-stu-id="597f7-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="597f7-p111">ユーザーのリストを作成し、ユーザー プリンシパル名 (UPN) および適切な優先データの場所の場所のコードが含まれます。まず、テスト ユーザーと、初期のパイロットのグループが含まれます。構成手順については、このリストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="597f7-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="597f7-p112">Azure Active Directory (AAD) に、ユーザーがオンプレミスの Active Directory (AD) システムから同期する場合は、Azure Active Directory の接続を使用して同期されたユーザーの希望するデータの場所を設定する必要があります。直接 Azure AD PowerShell を使用して同期のユーザーの希望するデータの場所を構成することはできません。AD の PDL の設定し、同期する手順は、「 [Azure Active Directory 接続の同期: Office 365 リソースの優先データのパスを構成する](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)です。</span><span class="sxs-lookup"><span data-stu-id="597f7-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="597f7-p113">複数地域のテナントの管理とは異なる多くの SharePoint と OneDrive の設定として、複数地域ではないテナントとサービスは、複数の地域に注意してください。確認すること[、複数地域の環境を管理する](administering-a-multi-geo-environment.md)構成を続行する前にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="597f7-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="597f7-170">複数地域の環境で、ユーザーのエクスペリエンスの詳細について[multgeo 環境で発生するユーザー](multi-geo-user-experience.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="597f7-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="597f7-171">OneDrive を構成する複数の地域のビジネスを始めるには、 [OneDrive を構成する複数の地域のビジネス](multi-geo-tenant-configuration.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="597f7-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="597f7-172">構成が完了したらに注意して[、ユーザーの OneDrive ライブラリを移行](move-onedrive-between-geo-locations.md)するのには、希望するデータの場所からユーザーを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="597f7-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
