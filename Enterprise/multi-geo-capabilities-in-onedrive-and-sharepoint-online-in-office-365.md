---
title: OneDrive および SharePoint Online の複数地域機能
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
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948588"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="2d5fc-103">OneDrive および SharePoint Online の複数地域機能</span><span class="sxs-lookup"><span data-stu-id="2d5fc-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="2d5fc-104">OneDrive および SharePoint Online の複数地域機能を使用すると、SharePoint チーム サイトや Office 365 グループ メールボックスなどの共有リソースを保存する国または地域をコントロールすることができます。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of the country or region where shared resources like SharePoint team sites and Office 365 Group mailboxes are stored at rest.</span></span>

<span data-ttu-id="2d5fc-105">ユーザー、グループ メールボックス、SharePoint サイトごとに、関連データが格納される地域の場所を示す PDL (Preferred Data Location、優先されるデータの場所) があります。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="2d5fc-106">ユーザーの個人データ (Exchange メールボックスと OneDrive) を、本人が作成した Office 365 グループまたは SharePoint サイトと共に指定された地域の場所に格納して、データ所在地の要件を満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-106">Users' personal data (Exchange mailbox and OneDrive) along with any Office 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="2d5fc-107">[地域の場所ごとに異なる管理者を指定する](add-a-sharepoint-geo-admin.md)ことができます。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="2d5fc-108">ユーザーが Office アプリケーション、OneDrive、Search などの Office 365 サービスを使用するとき、シームレスなエクスペリエンスが可能になります。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-108">Users get a seamless experience when using Office 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="2d5fc-109">詳細については、「[複数地域環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="2d5fc-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="2d5fc-110">OneDrive</span></span>

<span data-ttu-id="2d5fc-111">各ユーザーの OneDrive は、ユーザーの PDL に従ってサテライトの場所でプロビジョニングされるか、または[管理者が移動させる](move-onedrive-between-geo-locations.md)ことができます。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="2d5fc-112">個人用ファイルはその地域の場所に保存されますが、他の地域の場所にいるユーザーと共有することも可能です。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sites-and-groups"></a><span data-ttu-id="2d5fc-113">サイトとグループ</span><span class="sxs-lookup"><span data-stu-id="2d5fc-113">Calendar, Mail, Sites, Users and Groups</span></span>

<span data-ttu-id="2d5fc-114">ユーザーが SharePoint グループに接続されたサイトを作成する場合、サイトおよび関連付けられているグループ メールボックスが作成される地域の場所を決定するのに、PDL が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-114">When a user creates a SharePoint group-connected site, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="2d5fc-115">(ユーザーの PDL 値が設定されていない場合、またはサテライトの場所として構成されていない地域の場所に設定されている場合、サイトとメールボックスは中央の場所に作成されます)。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-115">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="2d5fc-116">Exchange、OneDrive、SharePoint 以外の Office 365 サービスは複数地域機能に対応していません。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-116">Office 365 services other than Exchange, OneDrive, and SharePoint are not Multi-Geo.</span></span> <span data-ttu-id="2d5fc-117">ただし、これらのサービスによって作成された Office 365 グループには作成者の PDL がスタンプされ、Exchange グループ メールボックスと SharePoint O365 グループ サイトは対応する地域でプロビジョニングされます。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-117">However, Office 365 Groups that are created by these services will be stamped with the PDL of the creator and their Exchange Group mailbox and SharePoint O365 Group Site provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="2d5fc-118">複数地域環境の管理</span><span class="sxs-lookup"><span data-stu-id="2d5fc-118">Managing the multi-geo environment</span></span>

<span data-ttu-id="2d5fc-119">複数地域環境の設定と管理は、SharePoint 管理センターで行います。</span><span class="sxs-lookup"><span data-stu-id="2d5fc-119">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![SharePoint 管理センターの [地域の場所] ページのスクリーン ショット](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="2d5fc-121">(SharePoint サイトや OneDrive サイトを移動するなど、一部の操作では Microsoft PowerShell が必要です。)</span><span class="sxs-lookup"><span data-stu-id="2d5fc-121">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="2d5fc-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d5fc-122">See also</span></span>

[<span data-ttu-id="2d5fc-123">Aka.ms/GetMultiGeo </span><span class="sxs-lookup"><span data-stu-id="2d5fc-123">Aka.ms/GetMultiGeo </span></span>](https://Aka.ms/GetMultiGeo)

[<span data-ttu-id="2d5fc-124">複数地域環境の管理</span><span class="sxs-lookup"><span data-stu-id="2d5fc-124">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="2d5fc-125">複数地域環境における SharePoint ストレージ クォータ</span><span class="sxs-lookup"><span data-stu-id="2d5fc-125">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="2d5fc-126">複数地域環境での Exchange Online メールボックスの管理</span><span class="sxs-lookup"><span data-stu-id="2d5fc-126">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
