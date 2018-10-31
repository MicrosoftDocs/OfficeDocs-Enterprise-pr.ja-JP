---
title: 地域管理者を追加または削除する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 追加または複数の地域のビジネス OneDrive の地域の管理者を削除する方法について説明します。
ms.openlocfilehash: 4e8c8bec148d5a4e7e55ffa2b08a49cd2ea6aa0a
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849813"
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="46735-103">追加または Busniess 複数の地域の OneDrive の地域の管理者を削除します。</span><span class="sxs-lookup"><span data-stu-id="46735-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="46735-p101">テナント内にある場所を地域ごとに個別の管理者を構成することができます。これらの管理者は、SharePoint Online および OneDrive の設定に、geo の場所に固有のアクセスがあります。</span><span class="sxs-lookup"><span data-stu-id="46735-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="46735-p102">用語ストア - などの一部のサービスは中央の場所から管理し、サテライトの場所にレプリケートします。中央の場所の地域の管理では、サテライト オフィスの地域の管理者でないが、これらへのアクセスがあります。</span><span class="sxs-lookup"><span data-stu-id="46735-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="46735-108">グローバル管理者および SharePoint Online の管理者は、中央の場所とすべてのサテライト オフィスでの設定にアクセスするのには続行します。</span><span class="sxs-lookup"><span data-stu-id="46735-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="46735-109">地域の管理者を構成します。</span><span class="sxs-lookup"><span data-stu-id="46735-109">Configuring geo administrators</span></span>

<span data-ttu-id="46735-110">地域の管理者を構成するには、SharePoint のオンライン PowerShell モジュールが必要です。</span><span class="sxs-lookup"><span data-stu-id="46735-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="46735-111">地域管理者の追加先となる地域の場所の管理センターへの接続に[接続する SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)を使用してください。(たとえば、接続 SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="46735-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="46735-112">場所の既存の地域の管理者を表示するのには次のように実行します。`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="46735-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="46735-113">地域の管理者としてユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="46735-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="46735-114">地域の管理者としてユーザーを追加するのには次のように実行します。`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="46735-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="46735-115">場所の地域の管理者として、ユーザーを削除するのには次のように実行します。`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="46735-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="46735-116">地域の管理者として、グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="46735-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="46735-117">地域管理者としてセキュリティ グループまたはメールが有効なセキュリティ グループを追加することができます。(配布グループと Office 365 のグループはサポートされません。)</span><span class="sxs-lookup"><span data-stu-id="46735-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="46735-118">地域管理者グループを追加するのには次のように実行します。`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="46735-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="46735-119">地域管理者グループを削除するには、次のように実行します。`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="46735-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="46735-p103">すべてのセキュリティ グループに、グループのエイリアスがあることに注意してください。エイリアス、グループの一覧を取得する[Get MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup)を実行していないセキュリティ グループを追加する場合、セキュリティ グループのオブジェクト Id を検索し、実行します。</span><span class="sxs-lookup"><span data-stu-id="46735-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="46735-122">オブジェクト Id を使用してグループを削除するのには次のように実行します。`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="46735-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a><span data-ttu-id="46735-123">特定の地理的な場所の管理センターへのアクセス</span><span class="sxs-lookup"><span data-stu-id="46735-123">Accessing the admin center for a specific geo-location</span></span>

<span data-ttu-id="46735-124">地域の OneDrive の設定を管理するには、管理者は次の URL 形式を使用して直接 OneDrive 管理センターにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="46735-124">To administer OneDrive settings for their geo location, admins must access the OneDrive admin center directly using the following URL format:</span></span>

<span data-ttu-id="46735-125">https://admin.onedrive.com/?geo=<*地域*></span><span class="sxs-lookup"><span data-stu-id="46735-125">https://admin.onedrive.com/?geo=<*geo*></span></span>

<span data-ttu-id="46735-126">たとえば、カナダの OneDrive の管理の中心にある: https://admin.onedrive.com/?geo=CAN。</span><span class="sxs-lookup"><span data-stu-id="46735-126">For example, the OneDrive admin center for Canada is located at: https://admin.onedrive.com/?geo=CAN.</span></span>

## <a name="see-also"></a><span data-ttu-id="46735-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="46735-127">See Also</span></span>

[<span data-ttu-id="46735-128">追加 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="46735-128">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="46735-129">Get SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="46735-129">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="46735-130">削除 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="46735-130">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="46735-131">セキュリティ グループのエイリアス (MailNickName) を設定します。</span><span class="sxs-lookup"><span data-stu-id="46735-131">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)