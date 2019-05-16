---
title: サテライト地域で SharePoint Multi-Geo の有効化
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: サテライト地域で SharePoint Multi-Geo を有効にします。
ms.openlocfilehash: d1f18c22410ec98e6c27cf3d10cdaf05a5095036
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070763"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a><span data-ttu-id="a1eda-103">サテライト地域で SharePoint Multi-Geo の有効化</span><span class="sxs-lookup"><span data-stu-id="a1eda-103">Enabling SharePoint Multi-Geo in your satellite geo location</span></span>

<span data-ttu-id="a1eda-104">この記事は、2019 年 3 月 27日に SharePoint Multi-Geo の機能が一般的に利用できるようになる**前に**、Multi-Geo のサテライト地域を作成した Global または SharePoint の管理者、およびサテライト地域で SharePoint Multi-Geo を有効にしていないユーザー向けのものです。</span><span class="sxs-lookup"><span data-stu-id="a1eda-104">This article is for Global or SharePoint administrators who have created a Multi-Geo satellite location **before** SharePoint Multi-Geo capabilities became generally available on March 27, 2019, and who have not enabled SharePoint Multi-Geo in their satellite geo location(s).</span></span> 

>[!Note]
><span data-ttu-id="a1eda-105">**3 月 27日以降**に新しい地域を追加した場合、OneDrive と SharePoint Multi-Geo でその新しい地域がすでに有効になっていれば、以下の手順を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a1eda-105">If you have added a new geo location **after March 27th**, you do not need to perform these instructions, as your new geo location will already be enabled for OneDrive and SharePoint Multi-Geo.</span></span>

<span data-ttu-id="a1eda-106">以下の手順により、ユーザーのサテライト地域で SharePoint を有効にできるため、Multi-Geo サテライト ユーザーは O365 で、OneDrive と SharePoint Multi-Geo 両方の機能を利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a1eda-106">These instructions will allow you to enable SharePoint in your satellite location, so your Multi-Geo satellite users can take advantage of both OneDrive and SharePoint Multi-Geo capabilities in O365.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="a1eda-107">これは有効化の方法の 1 つであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a1eda-107">Please note that this is a one way enablement.</span></span> <span data-ttu-id="a1eda-108">SPO モードを設定したら、サポートによるエスカレーションなしでテナントを OneDrive の Multi-Geo モードに戻すことだけはできません。</span><span class="sxs-lookup"><span data-stu-id="a1eda-108">Once you set SPO mode, you will not be able to revert your tenant to OneDrive only Multi-Geo mode without an escalation with support.</span></span> 

## <a name="to-set-a-geo-location-into-spo-mode"></a><span data-ttu-id="a1eda-109">SPO モードに地域を設定するには</span><span class="sxs-lookup"><span data-stu-id="a1eda-109">To set a geo location into SPO Mode</span></span>

<span data-ttu-id="a1eda-110">SPO モードに地域を設定するには、SPO モードで設定する地域に接続します。</span><span class="sxs-lookup"><span data-stu-id="a1eda-110">To set a geo location into SPO mode, connect to the geo location you want to set in SPO Mode:</span></span>

1.  <span data-ttu-id="a1eda-111">SharePoint Online 管理シェルを開く</span><span class="sxs-lookup"><span data-stu-id="a1eda-111">Open your SharePoint Online Management Shell</span></span> 
2.  <span data-ttu-id="a1eda-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span><span class="sxs-lookup"><span data-stu-id="a1eda-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span></span>
3.  <span data-ttu-id="a1eda-113">Set-SPOMultiGeoExperience</span><span class="sxs-lookup"><span data-stu-id="a1eda-113">Set-SPOMultiGeoExperience</span></span></br></br>
<span data-ttu-id="a1eda-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="a1eda-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span></span>
4.  <span data-ttu-id="a1eda-115">この操作は通常 1 時間程度かかり、その間、サービス内でさまざまな発行バックを実行し、テナントに再度スタンプを付けます。</span><span class="sxs-lookup"><span data-stu-id="a1eda-115">This operation usually takes about an hour while we perform various publish backs in the service and re-stamp your tenant.</span></span> <span data-ttu-id="a1eda-116">少なくとも 1 時間後に Get-SPOMultiGeoExperience を実行してください。</span><span class="sxs-lookup"><span data-stu-id="a1eda-116">After at least 1 hour, please perform a Get-SPOMultiGeoExperience.</span></span>  <span data-ttu-id="a1eda-117">実行すると、SPO モードにこの地域があるかどうかが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a1eda-117">This will show you whether this geo location is in SPO mode.</span></span></br></br>
<span data-ttu-id="a1eda-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="a1eda-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span></span>

 
 
 
>[!Note]
><span data-ttu-id="a1eda-119">サービスの特定のキャッシュは 24 時間ごとに更新するため、最大で 24 時間、ODB モードのままであるかのように、サテライト地域が断続的に動作する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a1eda-119">Certain caches in the service update every 24 hours, so it is possible that for a period of up to 24 hours, your satellite geo may intermittently behave as if it was still in ODB mode.</span></span> <span data-ttu-id="a1eda-120">この動作により技術的な問題が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="a1eda-120">This does not cause any technical issues.</span></span> 
 
<span data-ttu-id="a1eda-121">SharePoint Multi-Geo に関する詳細については [aka.ms/sharepointmultigeo](https://docs.microsoft.com/ja-JP/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1eda-121">For additional information regarding SharePoint Multi-Geo, please refer to [aka.ms/sharepointmultigeo](https://docs.microsoft.com/en-us/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span></span>


