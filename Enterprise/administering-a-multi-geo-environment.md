---
title: 複数地域環境の管理
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 複数地域環境での SharePoint サービスおよび OneDrive サービスの管理について説明します。
ms.openlocfilehash: 12da695b44c5102c985a8d64960b1d20e092c8cd
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2018
ms.locfileid: "21550060"
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="57180-103">複数地域環境の管理</span><span class="sxs-lookup"><span data-stu-id="57180-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="57180-104">ここでは、複数地域環境で OneDrive および SharePoint のサービスが動作するしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="57180-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="57180-105">OneDrive 管理者のエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="57180-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="57180-p101">[OneDrive 管理センター](https://admin.onedrive.com)の左側のナビゲーションには、**[地域の場所]** タブがあります。このタブには、地域の場所の地図があり、地域の場所を確認および管理できます。</span><span class="sxs-lookup"><span data-stu-id="57180-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="57180-108">分類</span><span class="sxs-lookup"><span data-stu-id="57180-108">Taxonomy</span></span>

<span data-ttu-id="57180-p102">企業の中央の場所でホストされるマスターと共に、複数の地域の場所にわたるエンタープライズ管理メタデータに対する統一された[分類](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)がサポートされています。中央の場所からグローバルな分類を管理し、サテライト地域の場所の分類には地域に固有の用語のみを追加することをお勧めします。グローバルな分類の用語は、サテライト地域の場所に同期されます。</span><span class="sxs-lookup"><span data-stu-id="57180-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="57180-112">共有</span><span class="sxs-lookup"><span data-stu-id="57180-112">Sharing</span></span>

<span data-ttu-id="57180-p103">管理者は、共有ポリシーを場所ごとに設定および管理できます。各地域の場所の OneDrive サイトは、対応する地域の共有設定のみを優先します (たとえば、中央の場所とサテライトの場所のどちらか一方に[外部共有](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)を許可することができます)。共有の設定では、地域の場所間での共有の制限を構成できない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="57180-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo-locations.</span></span>

<span data-ttu-id="57180-p104">OneDrive 複数地域では、共有の設定がテナント全体には同期されないため、地域の場所ごとに管理する必要があります。共有を管理するには、[OneDrive 管理センターの共有設定](https://admin.onedrive.com/?v=SharingSettings)ページに移動します。既定では、各サテライトの場所の全員に外部共有が有効化されています。</span><span class="sxs-lookup"><span data-stu-id="57180-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="57180-119">ユーザー プロファイル アプリケーション</span><span class="sxs-lookup"><span data-stu-id="57180-119">User Profile Application</span></span>

<span data-ttu-id="57180-p105">各地域の場所ごとに、[ユーザー プロファイル アプリケーション](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)があります。それぞれのユーザーのプロファイル情報は、それらのユーザーの地域の場所でホストされ、その場所の管理者が利用できます。</span><span class="sxs-lookup"><span data-stu-id="57180-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="57180-p106">カスタムのプロファイル プロパティがある場合は、すべての地域で同じプロファイル スキーマを使用して、すべての地域の場所または必要な場所のどちらかにカスタムのプロファイル プロパティを設定します。ユーザー プロファイル データをプログラムによって設定する方法のガイダンスについては、「[SharePoint Online 用カスタム ユーザー プロファイル プロパティの一括更新用 API の概要](https://docs.microsoft.com/ja-JP/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57180-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/ja-JP/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="57180-124">BCS、Secure Store、Apps</span><span class="sxs-lookup"><span data-stu-id="57180-124">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="57180-125">BCS、Secure Store、および Apps のすべてに、個別の地域インスタンスがあります。そのため、SharePoint Online 管理者は、これらのサービスが存在する各地域インスタンスから、そのサービスを管理および構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57180-125">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="57180-126">セキュリティ/コンプライアンス管理センター</span><span class="sxs-lookup"><span data-stu-id="57180-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="57180-127">複数地域テナントには、[Office 365 セキュリティ/コンプライアンス センター](https://protection.office.com/?rfr=AdminCenter\#/homepage)という 1 つの中心的なコンプライアンス センターがあります。</span><span class="sxs-lookup"><span data-stu-id="57180-127">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="57180-128">Information Protection (IP) データ損失防止 (DLP) ポリシー</span><span class="sxs-lookup"><span data-stu-id="57180-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="57180-p107">セキュリティ/コンプライアンス センターでは、ポリシーの適用範囲をテナント全体または該当するユーザーに設定することで、OneDrive for Business の IP DLP ポリシーを設定できます。たとえば、サテライトの場所の OneDrive ユーザーのポリシーを選択する場合、特定の OneDrive に適用するポリシーを選択して、ユーザーの OneDrive の URL を入力します。DLP ポリシーの作成に関する一般的なガイダンスについては、「[データ損失防止ポリシーの概要](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57180-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="57180-132">DLP ポリシーは、そのポリシーの適用性に基づいて各地域の場所に自動的に同期されます。</span><span class="sxs-lookup"><span data-stu-id="57180-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="57180-133">地域の場所のすべてのユーザーに対する Information Protection ポリシーとデータ損失防止ポリシーの実装は、UI で使用可能なオプションではありません。その代わりに、ポリシーの適用が可能な OneDrive アカウントを選択するか、すべての OneDrive アカウントにグローバルにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57180-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="57180-134">電子情報開示</span><span class="sxs-lookup"><span data-stu-id="57180-134">eDiscovery</span></span> 

<span data-ttu-id="57180-p108">既定では、複数地域テナントの電子情報開示マネージャーまたは管理者は、テナントの中央の場所でのみ電子情報開示を実施できます。サテライトの場所で電子情報開示を実施できるようにするために、"Region" という新しいコンプライアンス セキュリティ フィルター パラメーターが PowerShell で使用できます。</span><span class="sxs-lookup"><span data-stu-id="57180-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="57180-137">Office 365 全体管理者は、別のユーザーが電子情報開示を実行できるように電子情報開示マネージャーのアクセス許可を割り当てる必要があります。また、サテライトの場所として電子情報開示を実施する地域を指定するために該当するコンプライアンス セキュリティ フィルターで "Region" パラメーターを割り当てる必要があります。それ以外の場合は、サテライトの場所で電子情報開示は実施されません。</span><span class="sxs-lookup"><span data-stu-id="57180-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="57180-p109">電子情報開示マネージャーまたは管理者の役割が特定の地域の場所に設定されている場合、電子情報開示マネージャーまたは管理者は、その地域の場所にある SharePoint サイトと OneDrive サイトに対してのみ電子情報開示の検索操作を実行できます。電子情報開示マネージャーまたは管理者が、指定の地域外の SharePoint サイトまたは OneDrive サイトを検索しようとしても結果は返されません。さらに、ある地域の電子情報開示マネージャーまたは管理者がエクスポートをトリガーすると、データは、その地域の Azure インスタンスにエクスポートされます。制御された境界を越えたコンテンツのエクスポートが許可されなくなることで、これが組織のコンプライアンスの維持に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="57180-p109">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="57180-142">電子情報開示マネージャーが複数の SharePoint 地域全体で検索する必要がない場合は、OneDrive サイトまたは SharePoint サイトがある別の地域を指定する電子情報開示マネージャー用の別のユーザー アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57180-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="57180-143"><strong>複数地域でサポートされる地域の場所</strong></span><span class="sxs-lookup"><span data-stu-id="57180-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="57180-144"><strong>SharePoint でエクスポートされた電子情報開示データが存在する Azure Blob データの場所</strong></span><span class="sxs-lookup"><span data-stu-id="57180-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="57180-145"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="57180-145"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="57180-146">東南アジアまたは東アジアのデータ センター</span><span class="sxs-lookup"><span data-stu-id="57180-146">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="57180-147"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="57180-147"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="57180-148">東南アジアまたは東アジアのデータ センター</span><span class="sxs-lookup"><span data-stu-id="57180-148">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="57180-149"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="57180-149"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="57180-150">米国のデータセンター</span><span class="sxs-lookup"><span data-stu-id="57180-150">US datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="57180-151"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="57180-151"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="57180-152">ヨーロッパのデータセンター</span><span class="sxs-lookup"><span data-stu-id="57180-152">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="57180-153"><strong>FRA</strong></span><span class="sxs-lookup"><span data-stu-id="57180-153"><strong>FRA</strong></span></span></td>
<td align="left"><span data-ttu-id="57180-154">ヨーロッパのデータセンター</span><span class="sxs-lookup"><span data-stu-id="57180-154">Europe datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="57180-155"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="57180-155"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="57180-156">ヨーロッパのデータセンター</span><span class="sxs-lookup"><span data-stu-id="57180-156">Europe datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="57180-157"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="57180-157"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="57180-158">東南アジアまたは東アジアのデータ センター</span><span class="sxs-lookup"><span data-stu-id="57180-158">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="57180-159"><strong>JPN </strong></span><span class="sxs-lookup"><span data-stu-id="57180-159"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="57180-160">東南アジアまたは東アジアのデータ センター</span><span class="sxs-lookup"><span data-stu-id="57180-160">Southeast or East Asia datacenters</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="57180-161"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="57180-161"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="57180-162">米国のデータセンター</span><span class="sxs-lookup"><span data-stu-id="57180-162">US datacenters</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="57180-163">地域のコンプライアンス セキュリティ フィルターを設定するには:</span><span class="sxs-lookup"><span data-stu-id="57180-163">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="57180-164">Windows PowerShell を開きます。</span><span class="sxs-lookup"><span data-stu-id="57180-164">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="57180-165">次のように入力します</span><span class="sxs-lookup"><span data-stu-id="57180-165">Enter</span></span>  
    <span data-ttu-id="57180-166">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="57180-166">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="57180-167">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="57180-167">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="57180-168">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="57180-168">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="57180-169">例: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="57180-169">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="57180-170">追加のパラメーターと構文については、「[New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57180-170">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="57180-171">監査ログ検索</span><span class="sxs-lookup"><span data-stu-id="57180-171">Audit log search</span></span>

<span data-ttu-id="57180-p110">すべての地域の場所に対して統一された[監査ログ](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)は、Office 365 の監査ログの検索ページから利用できます。すべての地域からの監査ログのエントリを参照できます。たとえば、NAM 地域と EUR 地域のユーザーのアクティビティが、1 つの組織ビューに表示され、既存のフィルターを適用することで特定のユーザーのアクティビティを確認できます。</span><span class="sxs-lookup"><span data-stu-id="57180-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
