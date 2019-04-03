---
title: 複数地域環境における SharePoint ストレージ クォータ
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 複数地域環境における SharePoint ストレージ クォータについて説明します。
ms.openlocfilehash: 9c43f21a844507c4de7971d70a110665ddc094ba
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934038"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a><span data-ttu-id="49890-103">複数地域環境における SharePoint ストレージ クォータ</span><span class="sxs-lookup"><span data-stu-id="49890-103">SharePoint storage quotas in multi-geo environments</span></span>

<span data-ttu-id="49890-104">既定では、複数地域環境のすべての地域の場所では、使用できるテナントのストレージ クォータを共有します。</span><span class="sxs-lookup"><span data-stu-id="49890-104">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>

<span data-ttu-id="49890-105">SharePoint 地域ストレージ クォータ設定では、地域の場所ごとにストレージ クォータを管理することができます。</span><span class="sxs-lookup"><span data-stu-id="49890-105">With the SharePoint geo storage quota setting, you can manage the storage quota for each geo location.</span></span> <span data-ttu-id="49890-106">地域の場所のストレージ クォータを割り当てると、それがその地域の場所に使用可能な最大ストレージ容量になり、使用可能なテナント ストレージ クォータから差し引かれます。</span><span class="sxs-lookup"><span data-stu-id="49890-106">When you allocate a storage quota for a geo location, it becomes the maximum amount of storage available for that geo location, and is deducted from the available tenant storage quota.</span></span> <span data-ttu-id="49890-107">残りの利用可能なテナント ストレージ クォータは、特定のストレージ クォータが割り当てられていない構成済みの地域の場所間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="49890-107">The remaining available tenant storage quota is then shared across the configured geo locations for which a specific storage quota has not been allocated.</span></span>

<span data-ttu-id="49890-108">地域の場所に対する SharePoint ストレージ クォータは、SharePoint Online 管理者が中央の場所に接続することによって割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="49890-108">The SharePoint storage quota for any geo location can be allocated by the SharePoint Online administrator by connecting to the central location.</span></span> <span data-ttu-id="49890-109">サテライトの場所の地域管理者は、ストレージ クォータを表示できますが、割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="49890-109">Geo administrators for satellite locations can view the storage quota but cannot allocate it.</span></span>

## <a name="configure-a-storage-quota-for-a-geo-location"></a><span data-ttu-id="49890-110">地域の場所のストレージ クォータを構成する</span><span class="sxs-lookup"><span data-stu-id="49890-110">Configure a storage quota for a geo location</span></span>

<span data-ttu-id="49890-111">地域の場所にストレージ クォータを割り当てるには、[Microsoft Office SharePoint Online モジュール](https://www.microsoft.com/en-us/download/details.aspx?id=35588 )を使用して、中央の場所に接続します。</span><span class="sxs-lookup"><span data-stu-id="49890-111">Use the [Microsoft SharePoint Online Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588 ) and connect to the central location to allocate the storage quota for a geo location.</span></span> 

<span data-ttu-id="49890-112">場所にストレージ クォータを割り当てるには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="49890-112">To allocate Storage Quota for a location, run cmdlet:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

<span data-ttu-id="49890-113">現在の地域の場所に対するストレージ クォータを表示するには、次を実行します。</span><span class="sxs-lookup"><span data-stu-id="49890-113">To view Storage Quota for the current geo location, run:</span></span>

`Get-SPOGeoStorageQuota`

![Get-SPOGeoStorageQuota コマンドレットを表示している PowerShell ウィンドウのスクリーンショット](media/multi-geo-storage-quota.png)

<span data-ttu-id="49890-115">すべての地域の場所に対するストレージ クォータを表示するには、次を実行します。</span><span class="sxs-lookup"><span data-stu-id="49890-115">To view Storage Quota for all geo locations, run:</span></span>

`Get-SPOGeoStorageQuota -AllLocations`

<span data-ttu-id="49890-116">地域の場所の割り当てられたストレージ クォータを削除するには、`StorageQuota value = 0` を設定します。</span><span class="sxs-lookup"><span data-stu-id="49890-116">To remove the allocated storage quota for a geo location, set `StorageQuota value = 0`:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
