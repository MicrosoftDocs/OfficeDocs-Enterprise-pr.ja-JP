---
title: 追加または地域の管理者を削除します。
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 追加または複数の地域のビジネス OneDrive の地域の管理者を削除する方法について説明します。
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="5e947-103">追加または Busniess 複数の地域の OneDrive の地域の管理者を削除します。</span><span class="sxs-lookup"><span data-stu-id="5e947-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="5e947-p101">テナント内にある場所を地域ごとに個別の管理者を構成することができます。これらの管理者は、SharePoint Online および OneDrive の設定には、地理的な場所に固有のアクセスがあります。</span><span class="sxs-lookup"><span data-stu-id="5e947-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="5e947-p102">用語ストア - などの一部のサービスは中央の場所から管理し、サテライトの場所にレプリケートします。中央の場所の地域の管理では、サテライト オフィスの地域の管理者でないが、これらへのアクセスがあります。</span><span class="sxs-lookup"><span data-stu-id="5e947-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="5e947-108">グローバル管理者および SharePoint Online の管理者は、地域のすべての場所の設定へのアクセスを有効にして続行します。</span><span class="sxs-lookup"><span data-stu-id="5e947-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="5e947-109">地域の管理者を構成します。</span><span class="sxs-lookup"><span data-stu-id="5e947-109">Configuring geo administrators</span></span>

<span data-ttu-id="5e947-110">地域の管理者を構成するには、SharePoint のオンライン PowerShell モジュールが必要です。</span><span class="sxs-lookup"><span data-stu-id="5e947-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="5e947-111">地域管理者の追加先となる地域の場所の管理センターへの接続に[接続する SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)を使用してください。(たとえば、接続 SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="5e947-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="5e947-112">地域の管理者としてユーザーを追加するのには次のように実行します。`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="5e947-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="5e947-113">場所の既存の地域の管理者を表示するのには次のように実行します。`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="5e947-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="5e947-114">場所の地域の管理者として、ユーザーを削除するのには次のように実行します。`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="5e947-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="5e947-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e947-115">See Also</span></span>

[<span data-ttu-id="5e947-116">追加 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="5e947-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="5e947-117">Get SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="5e947-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="5e947-118">削除 SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="5e947-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)