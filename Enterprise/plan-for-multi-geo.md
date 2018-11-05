---
title: OneDrive for Business 複数地域の計画
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: OneDrive for Business 複数地域、複数地域のしくみ、およびデータ ストレージに使用できる地域の場所について説明します。
ms.openlocfilehash: d40f84ea3636b4eca2711a48bd9d70c73a242cfd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849863"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="7514f-103">OneDrive for Business 複数地域の計画</span><span class="sxs-lookup"><span data-stu-id="7514f-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="7514f-104">このガイドは、データ所在地の要件を満たすように、SharePoint Online テナントを企業の所在地に応じて追加の地域に展開するための準備を整える多国籍企業 (MNC) の管理者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="7514f-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="7514f-p101">OneDrive Multi-Geo 構成では、Office 365 テナントが 1 つの中央の場所と 1 つ以上のサテライト地域の場所で構成されます。これは、複数の地域の場所に展開する単一のテナントです。OneDrive Multi-Geoでは、地域の場所を含むテナント情報が Azure Active Directory (AAD) でマスター管理されます。</span><span class="sxs-lookup"><span data-stu-id="7514f-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="7514f-108">この構成の基本的な概念についての理解を助けるために、複数地域に関するいくつかの主要な用語を示します。</span><span class="sxs-lookup"><span data-stu-id="7514f-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="7514f-109">**テナント**: Office 365 における組織の表現。通常、1 つ以上のドメインが関連付けられています (例: http://contoso.sharepoint.com)。</span><span class="sxs-lookup"><span data-stu-id="7514f-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="7514f-110">**地理的位置** – Office 365 テナントのデータをホストできる地理的な場所。</span><span class="sxs-lookup"><span data-stu-id="7514f-110">**Geo locations** – The geographic locations available to host data in an Office 365 tenant.</span></span>

-   <span data-ttu-id="7514f-p102">**サテライトの場所** – Office 365 テナントのデータをホストするように構成した地理的な場所。複数地域テナントは、複数の地域の場所 (たとえば、北米とヨーロッパ) に展開します。</span><span class="sxs-lookup"><span data-stu-id="7514f-p102">**Satellite locations** – The geo locations that you have configured to host data in your Office 365 tenant. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="7514f-p103">**優先されるデータの場所 (PDL)**: 個別のユーザーの OneDrive データが保存される地域の場所。この場所は、テナントに対して構成されている許可されているデータの場所のいずれかに管理者が設定できます。既に OneDrive サイトを所有しているユーザーの PDL を変更しても、そのユーザーの OneDrive データは新しい地域の場所に自動的には移動されない点に注意してください。詳細については、「[OneDrive ライブラリを別の地域の場所に移動する](move-onedrive-between-geo-locations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7514f-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="7514f-117">複数地域の有効化に必要になる主な 4 つの手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7514f-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="7514f-118">アカウント チームと協力して、_Office 365 の複数地域機能_サービス プランを追加します。</span><span class="sxs-lookup"><span data-stu-id="7514f-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="7514f-119">サテライトの場所を選択して、その場所をテナントに追加します。</span><span class="sxs-lookup"><span data-stu-id="7514f-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="7514f-p104">ユーザーの優先されるデータの場所を適切なサテライトの場所に設定します。ユーザーに新しい OneDrive サイトがプロビジョニングされると、そのサイトがユーザーの PDL にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="7514f-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="7514f-122">ユーザーの既存の OneDrive サイトを中央の場所から、そのユーザーの優先されるデータの場所に移行します (必要な場合)。</span><span class="sxs-lookup"><span data-stu-id="7514f-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="7514f-123">それぞれの手順の詳細については、「[OneDrive for Business 複数地域の構成](multi-geo-tenant-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7514f-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7514f-p105">Office 365 Multi-Geo は、パフォーマンス最適化のケースに向けて設計されたものではなく、データ所在地の要件を満たすために設計されている点に注意してください。Office 365 のパフォーマンス最適化に関する詳細については、「[Office 365 のネットワーク計画とパフォーマンスのチューニング](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848)」を参照するか、サポート グループにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="7514f-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="7514f-p106">次に示す場所は、OneDrive のファイルをホストできるサテライトの場所として構成できます。Multi-Geo の計画の際には、Office 365 テナントに追加する場所のリストを作成します。1 つまたは 2 つのサテライトの場所から初めて、必要に応じて段階的に別の地域の場所に拡張することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7514f-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="7514f-129"><strong>場所</strong></span><span class="sxs-lookup"><span data-stu-id="7514f-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="7514f-130"><strong>コード</strong></span><span class="sxs-lookup"><span data-stu-id="7514f-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="7514f-131">アジア太平洋</span><span class="sxs-lookup"><span data-stu-id="7514f-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="7514f-132">APC</span><span class="sxs-lookup"><span data-stu-id="7514f-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7514f-133">オーストラリア</span><span class="sxs-lookup"><span data-stu-id="7514f-133">Australia</span></span></td>
<td align="left"><span data-ttu-id="7514f-134">AUS</span><span class="sxs-lookup"><span data-stu-id="7514f-134">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7514f-135">カナダ</span><span class="sxs-lookup"><span data-stu-id="7514f-135">Canada</span></span></td>
<td align="left"><span data-ttu-id="7514f-136">CAN</span><span class="sxs-lookup"><span data-stu-id="7514f-136">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7514f-137">ヨーロッパ/中東/アフリカ</span><span class="sxs-lookup"><span data-stu-id="7514f-137">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="7514f-138">EUR</span><span class="sxs-lookup"><span data-stu-id="7514f-138">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7514f-139">フランス</span><span class="sxs-lookup"><span data-stu-id="7514f-139">France</span></span></td>
<td align="left"><span data-ttu-id="7514f-140">FRA</span><span class="sxs-lookup"><span data-stu-id="7514f-140">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7514f-141">日本</span><span class="sxs-lookup"><span data-stu-id="7514f-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="7514f-142">JPN</span><span class="sxs-lookup"><span data-stu-id="7514f-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="7514f-143">韓国</span><span class="sxs-lookup"><span data-stu-id="7514f-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="7514f-144">KOR</span><span class="sxs-lookup"><span data-stu-id="7514f-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7514f-145">北アメリカ</span><span class="sxs-lookup"><span data-stu-id="7514f-145">North America</span></span></td>
<td align="left"><span data-ttu-id="7514f-146">NAM</span><span class="sxs-lookup"><span data-stu-id="7514f-146">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="7514f-147">イギリス</span><span class="sxs-lookup"><span data-stu-id="7514f-147">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="7514f-148">GBR</span><span class="sxs-lookup"><span data-stu-id="7514f-148">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="7514f-149">今後提供予定の地域の場所:</span><span class="sxs-lookup"><span data-stu-id="7514f-149">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="7514f-150">インド</span><span class="sxs-lookup"><span data-stu-id="7514f-150">India</span></span>

<span data-ttu-id="7514f-p107">複数地域を構成するときは、Office 365 への移行と同時にオンプレミスのインフラストラクチャを統合する機会だと考えてください。たとえば、シンガポールとマレーシアにオンプレミス ファームがある場合、データ所在地の要件で許可されているときには、それらのファームを APC サテライトの場所に統合できます。</span><span class="sxs-lookup"><span data-stu-id="7514f-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="7514f-153">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="7514f-153">Best practices</span></span>

<span data-ttu-id="7514f-p108">いくつかの初期テストのために Office 365 のテスト用ユーザーを作成することをお勧めします。OneDrive Multi-Geo に実稼働ユーザーをオンボードする前に、このテスト用ユーザーでいくつかのテストと検証の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7514f-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="7514f-p109">テスト用ユーザーでのテストが完了したら、新しい地域の場所で最初に OneDrive を使用するパイロット グループを IT 部門 (など) から選択します。この最初のグループには、OneDrive をまだ所有していないユーザーを選択します。この初期グループのユーザーは 5 人未満にして、バッチ ロールアウトのアプローチに従って段階的に増員していきます。</span><span class="sxs-lookup"><span data-stu-id="7514f-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="7514f-p110">各ユーザーには*優先されるデータの場所* (PDL) を設定しておく必要があります。これにより、それぞれのユーザーの OneDrive をプロビジョニングする地域の場所を Office 365 が判断できるようになります。ユーザーの優先されるデータの場所は、選択したサテライトの場所のいずれか、または中央の場所と一致する必要があります。PDL フィールドは必須ではありませんが、すべてのユーザーの PDL を設定することをお勧めします。PDL のないユーザーのワークロードは中央の場所にプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="7514f-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="7514f-p111">ユーザーのリストを作成して、ユーザー プリンシパル名と適切な優先されるデータの場所の地域コードを含めます。テスト用ユーザーと初期パイロット グループを含めて開始します。このリストは、構成の手順で必要になります。</span><span class="sxs-lookup"><span data-stu-id="7514f-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="7514f-p112">ユーザーがオンプレミスの Active Directory システムから Azure Active Directory に同期される場合、同期されるユーザーの優先されるデータの場所は、Azure Active Directory Connect を使用して設定する必要があります。同期されるユーザーの優先されるデータの場所は、Azure AD PowerShell を使用して直接構成することはできません。AD で PDL を設定して同期する手順については、「[Azure Active Directory Connect 同期: Office 365 リソースの優先されるデータの場所を構成する](https://docs.microsoft.com/ja-JP/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7514f-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/ja-JP/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="7514f-p113">複数地域テナントの管理は、複数地域ではないテナントの管理と異なることがあり、SharePoint および OneDrive の設定と機能の多くが複数地域に対応しています。構成を進める前に、「[複数地域環境の管理](administering-a-multi-geo-environment.md)」を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7514f-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="7514f-171">複数地域環境でのエンド ユーザーのエクスペリエンスの詳細については、「[複数地域環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7514f-171">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="7514f-172">OneDrive for Business 複数地域の構成を開始する場合は、「[OneDrive for Business 複数地域の構成](multi-geo-tenant-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7514f-172">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="7514f-173">構成の完了後は、ユーザーが優先されるデータの場所から作業するために必要になる、[ユーザーの OneDrive ライブラリの移行](move-onedrive-between-geo-locations.md)を必ず実行してください。</span><span class="sxs-lookup"><span data-stu-id="7514f-173">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
