---
title: 複数地域の環境を管理します。
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: マルチ geo 環境で SharePoint と OneDrive のサービスの管理について説明します。
ms.openlocfilehash: f49cf35503ee6495b5982dc7d72f9b1936f564c6
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="f4988-103">複数地域の環境を管理します。</span><span class="sxs-lookup"><span data-stu-id="f4988-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="f4988-104">OneDrive と SharePoint のサービスが複数地域環境で作業する方法を見てです。</span><span class="sxs-lookup"><span data-stu-id="f4988-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="f4988-105">OneDrive 管理者の経験</span><span class="sxs-lookup"><span data-stu-id="f4988-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="f4988-p101">[OneDrive 管理センター](https://admin.onedrive.com)では、左側のナビゲーション機能 geo の場所にマップを表示し、地域、サイトの管理の**Geo の場所**] タブがあります。地域、テナントの場所を追加、削除するには、このページを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4988-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="f4988-108">分類</span><span class="sxs-lookup"><span data-stu-id="f4988-108">Taxonomy</span></span>

<span data-ttu-id="f4988-p102">サポート統一された[分類](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC)管理エンタープライズ メタデータの地域拠点には、会社の中央の場所でホストされているマスターとします。中央の場所から、グローバルの分類を管理し、サテライト地域場所の分類にのみの場所に固有の用語を追加することをお勧めします。グローバル分類の用語は、サテライトの地域の場所に同期されます。</span><span class="sxs-lookup"><span data-stu-id="f4988-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="f4988-112">共有</span><span class="sxs-lookup"><span data-stu-id="f4988-112">Sharing</span></span>

<span data-ttu-id="f4988-p103">管理者が設定し、それぞれの場所の共有ポリシーを管理できます。各地域拠点の OneDrive サイトには、のみ、対応する地域特定共有の設定を優先します。たとえば、ことができます[外部共有](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)用ではなく、サテライトの場所またはその逆の場合ですが、中央の場所です。OneDrive の複数の地域、テナント間でこれらが同期するいないと、各地域の拠点で、共有の設定を管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4988-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa. For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant.</span></span>

<span data-ttu-id="f4988-p104">共有のアクセス、 [OneDrive 管理センターの共有の設定](https://admin.onedrive.com/?v=SharingSettings)] ページを管理します。既定で外部の共有は各サテライト サイト内の全員が有効になります。</span><span class="sxs-lookup"><span data-stu-id="f4988-p104">To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="f4988-119">ユーザー プロファイル アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f4988-119">User Profile Application</span></span>

<span data-ttu-id="f4988-p105">各地域拠点では、[ユーザー プロファイル アプリケーション](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723)を使用です。各ユーザーのプロファイル情報は、geo の場所とその地域の場所の管理者に使用可能なホストされています。</span><span class="sxs-lookup"><span data-stu-id="f4988-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="f4988-122">カスタム プロファイルのプロパティがある場合同じプロファイル スキーマを使用して、地理的に分散し、地域のすべての場所のいずれか、カスタム プロファイル プロパティを設定することを推奨し、または必要な場所です。</span><span class="sxs-lookup"><span data-stu-id="f4988-122">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="f4988-123">BCS では、セキュリティで保護されたストアは、アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f4988-123">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="f4988-124">BCS、セキュリティで保護されたストアおよびアプリケーションは、別の地域のインスタンスを持つ、したがって SharePoint Online の管理者が管理し、必要な場所に存在する各地理インスタンスからこれらのサービスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4988-124">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="f4988-125">セキュリティおよびコンプライアンス管理センター</span><span class="sxs-lookup"><span data-stu-id="f4988-125">Security and Compliance Admin Center</span></span>

<span data-ttu-id="f4988-126">複数地域のテナントの 1 つの中心的なコンプライアンス センターがある: [Office 365 のセキュリティとコンプライアンスの中心](https://protection.office.com/?rfr=AdminCenter\#/homepage)です。</span><span class="sxs-lookup"><span data-stu-id="f4988-126">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="f4988-127">情報 (IP) の保護データの損失防止 (DLP) のポリシー</span><span class="sxs-lookup"><span data-stu-id="f4988-127">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="f4988-p106">ポリシーを設定できます、IP DLP OneDrive ビジネスのためのセキュリティとコンプライアンス ・ センターの全体のテナントまたは該当するユーザーに必要なポリシーのスコープの設定です。たとえば:、サテライトの場所に OneDrive のユーザーのポリシーを選択するには、特定の OneDrive にポリシーを適用し、ユーザー名を入力する場合に選択の OneDrive の url です。DLP ポリシーを作成する一般的な方法については、[データ損失防止ポリシーの概要](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4988-p106">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="f4988-131">DLP ポリシーは、各地域の場所に適用性に基づいて自動的に同期されます。</span><span class="sxs-lookup"><span data-stu-id="f4988-131">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="f4988-132">地域の場所にすべてのユーザー情報の保護とデータ損失の防止ポリシーを実装することは、UI で使用可能なオプションではありませんが、代わりに、ポリシーの適用可能な OneDrive のアカウントを選択してか OneDrive のすべてのアカウントをグローバルにポリシーを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4988-132">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="f4988-133">電子情報開示</span><span class="sxs-lookup"><span data-stu-id="f4988-133">eDiscovery</span></span> 

<span data-ttu-id="f4988-p107">既定では、マネージャーまたは多地域のテナントの管理者、電子的証拠開示は、テナントの中央の場所にのみ電子的証拠開示を行うことが可能になります。サテライト オフィスの電子的証拠開示を実施する機能をサポートするために「領域」と呼ばれる新しいコンプライアンス セキュリティ フィルター パラメーターは、PowerShell を使用して利用可能です。</span><span class="sxs-lookup"><span data-stu-id="f4988-p107">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="f4988-136">Office 365 のグローバル管理者は、電子的証拠開示を実行し、サテライトとして電子的証拠開示を実施するための領域を指定するのには、適用可能なコンプライアンス セキュリティ フィルターで「地域」パラメーターを指定するようにするのには、電子的証拠開示マネージャーのアクセス許可を割り当てる必要があります。場所、それ以外の場合サテライトの場所に電子的証拠開示が実行されるなし。</span><span class="sxs-lookup"><span data-stu-id="f4988-136">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="f4988-p108">特定の地域の場所を電子的証拠開示マネージャー ロールまたは管理者ロールを設定すると、マネージャーまたは管理者、電子的証拠開示のみできるようになります、SharePoint サイトとその地理的な場所にある OneDrive サイトに対して電子的証拠開示検索の操作を実行します。電子的証拠開示マネージャーまたは管理者は、指定した領域の外側の SharePoint または OneDrive サイトの検索を試みると、結果は返されません。また、電子的証拠開示マネージャーまたは管理者の領域には、エクスポートがトリガーされた場合は、その地域の Azure のインスタンスにデータがエクスポートされます。これにより、組織を対象となるコントロールの境界線の間でコンテンツを許可しないことによって、コンプライアンスを維持します。</span><span class="sxs-lookup"><span data-stu-id="f4988-p108">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="f4988-141">電子的証拠開示マネージャーが複数の SharePoint の領域全体を検索するために必要な場合は、別のユーザー アカウントは、電子的証拠開示マネージャー、OneDrive または SharePoint サイトが配置されている別の領域を指定するために作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4988-141">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f4988-142"><strong>複数地域は、地域の場所をサポートします。</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-142"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="f4988-143"><strong>SharePoint にエクスポートされたデータの電子的証拠開示は、この Azure Blob データの場所になります.</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-143"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f4988-144"><strong>名</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-144"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="f4988-145">米国のデータ ・ センター</span><span class="sxs-lookup"><span data-stu-id="f4988-145">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f4988-146"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-146"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="f4988-147">ヨーロッパのデータ ・ センター</span><span class="sxs-lookup"><span data-stu-id="f4988-147">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f4988-148"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-148"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="f4988-149">東の南または東アジアのデータ ・ センター</span><span class="sxs-lookup"><span data-stu-id="f4988-149">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f4988-150"><strong>できます。</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-150"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="f4988-151">米国のデータ ・ センター</span><span class="sxs-lookup"><span data-stu-id="f4988-151">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f4988-152"><strong>オーストラリア</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-152"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="f4988-153">東の南または東アジアのデータ ・ センター</span><span class="sxs-lookup"><span data-stu-id="f4988-153">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f4988-154"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-154"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="f4988-155">テナントの既定のデータの場所</span><span class="sxs-lookup"><span data-stu-id="f4988-155">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f4988-156"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-156"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="f4988-157">ヨーロッパのデータ ・ センター</span><span class="sxs-lookup"><span data-stu-id="f4988-157">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f4988-158"><strong>日本語版</strong></span><span class="sxs-lookup"><span data-stu-id="f4988-158"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="f4988-159">東の南または東アジアのデータ ・ センター</span><span class="sxs-lookup"><span data-stu-id="f4988-159">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f4988-160">地域のコンプライアンス ・ セキュリティ ・ フィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="f4988-160">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="f4988-161">開いている Windows PowerShell の</span><span class="sxs-lookup"><span data-stu-id="f4988-161">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="f4988-162">「</span><span class="sxs-lookup"><span data-stu-id="f4988-162">Enter</span></span>  
    <span data-ttu-id="f4988-163">$s = Microsoft.Exchange を新規 PSSession ConfigurationName ConnectionUri - <https://ps.compliance.protection.outlook.com/powershell-liveid> -$cred に資格情報の AllowRedirection では基本認証-SessionOption (新規 PSSessionOption SkipCACheck-サーバー-SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="f4988-163">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="f4988-164">$を = $s のインポート-PSSession AllowClobber</span><span class="sxs-lookup"><span data-stu-id="f4988-164">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="f4988-165">**新しい-ComplianceSecurityFilter****-アクション**すべて**のフィルター名**EnterTheNameYouWantToAssign **-地域**EnterTheRegionParameter **-ユーザー** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="f4988-165">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="f4988-166">例を示します**ComplianceSecurityFilter で新しい-アクション**すべて**のフィルター名**NAMEDISCOVERYMANAGERS **-地域**名**・ ユーザー** adwood@contosodemosx.onmicrosoft.com。</span><span class="sxs-lookup"><span data-stu-id="f4988-166">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="f4988-167">[新規 ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)この資料は、追加のパラメーターと構文を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4988-167">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="f4988-168">監査ログ検索</span><span class="sxs-lookup"><span data-stu-id="f4988-168">Audit log search</span></span>

<span data-ttu-id="f4988-p109">統一された[監査ログ](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c)のすべての地域の場所に、Office 365 の監査ログの検索ページから利用可能です。地域全体からのすべての監査ログ エントリを表示できます、やなどの名と EUR 地域ユーザーの活動は、組織の 1 つのビューに表示し、特定のユーザーの活動を確認する既存のフィルターを適用できます。</span><span class="sxs-lookup"><span data-stu-id="f4988-p109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
