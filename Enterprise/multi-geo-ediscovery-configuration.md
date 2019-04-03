---
title: Office 365 Multi-Geo 電子情報開示を構成する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Office 365 Multi-Geoで電子情報開示を構成する方法を表示する。
ms.openlocfilehash: 11d226605ba1f194393405edd5bb535da6ad7343
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934043"
---
# <a name="office-365-multi-geo-ediscovery-configuration"></a><span data-ttu-id="e522d-103">Office 365 Multi-Geo 電子情報開示の構成</span><span class="sxs-lookup"><span data-stu-id="e522d-103">Office 365 Multi-Geo eDiscovery configuration</span></span>


<span data-ttu-id="e522d-p101">既定では、複数地域テナントの電子情報開示マネージャーまたは管理者は、テナントの中央の場所でのみ電子情報開示を実施できます。サテライトの場所で電子情報開示を実施できるようにするために、"Region" という新しいコンプライアンス セキュリティ フィルター パラメーターが PowerShell で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e522d-p101">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="e522d-106">Office 365 全体管理者は、別のユーザーが電子情報開示を実行できるように電子情報開示マネージャーのアクセス許可を割り当てる必要があります。また、サテライトの場所として電子情報開示を実施する地域を指定するために該当するコンプライアンス セキュリティ フィルターで "Region" パラメーターを割り当てる必要があります。それ以外の場合は、サテライトの場所で電子情報開示は実施されません。</span><span class="sxs-lookup"><span data-stu-id="e522d-106">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="e522d-p102">電子情報開示マネージャーまたは管理者の役割が特定のサテライトの場所に設定されている場合、電子情報開示マネージャーまたは管理者は、そのサテライトの場所にある SharePoint サイトと OneDrive サイトに対してのみ電子情報開示の検索操作を実行できます。電子情報開示マネージャーまたは管理者が、指定のサテライトの場所以外の SharePoint サイトまたは OneDrive サイトを検索しようとしても、結果は返されません。さらに、あるサテライトの場所の電子情報開示マネージャーまたは管理者がエクスポートをトリガーすると、データは、その地域の Azure インスタンスにエクスポートされます。制御された境界を越えたコンテンツのエクスポートが許可されなくなることで、これが組織のコンプライアンスの維持に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e522d-p102">When the eDiscovery Manager or Administrator role is set for a particular satellite location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that satellite location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified satellite location, no results will be returned. Also, when the eDiscovery Manager or Administrator for a satellite location triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="e522d-111">電子情報開示マネージャーが複数の SharePoint のサテライトの場所全体で検索する必要がない場合は、OneDrive サイトまたは SharePoint サイトがある別のサテライトの場所を指定する電子情報開示マネージャー用の別のユーザー アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e522d-111">If it's necessary for an eDiscovery Manager to search across multiple SharePoint satellite locations, another user account will need to be created for the eDiscovery Manager which specifies the alternate satellite location where the OneDrive or SharePoint sites are located.</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

<span data-ttu-id="e522d-112">地域のコンプライアンス セキュリティ フィルターを設定するには:</span><span class="sxs-lookup"><span data-stu-id="e522d-112">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="e522d-113">Windows PowerShell を開きます。</span><span class="sxs-lookup"><span data-stu-id="e522d-113">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="e522d-114">次のように入力します</span><span class="sxs-lookup"><span data-stu-id="e522d-114">Enter</span></span>  
    <span data-ttu-id="e522d-115">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="e522d-115">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="e522d-116">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="e522d-116">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="e522d-117">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="e522d-117">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="e522d-118">例: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="e522d-118">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="e522d-119">追加のパラメーターと構文については、「[New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e522d-119">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>
