---
title: IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: IdFix ツールで除外およびサポートされている属性を一覧表示します。
ms.openlocfilehash: bf88fea3592860a89d69717177593b6553318ee4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067273"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="f6bd5-103">IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="f6bd5-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="f6bd5-104">IdFix によって管理されるルールには2つのセットがあります。マルチテナントと専用/ITAR。</span><span class="sxs-lookup"><span data-stu-id="f6bd5-104">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="f6bd5-105">現時点では、2つのルールセットは同じオブジェクト、属性、および属性値を検索から除外します。</span><span class="sxs-lookup"><span data-stu-id="f6bd5-105">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="f6bd5-106">これは今後のリリースで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6bd5-106">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="f6bd5-107">IdFix によって使用されるマルチテナントと専用エラーの除外</span><span class="sxs-lookup"><span data-stu-id="f6bd5-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="f6bd5-108">このセクションでは、IdFix によってディレクトリの検索から除外されるオブジェクト、属性、および値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="f6bd5-108">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="f6bd5-109">アスタリスク (\*) は、他の文字に置き換えることができるワイルドカードです。</span><span class="sxs-lookup"><span data-stu-id="f6bd5-109">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="f6bd5-110">IdFix 検索で除外されるオブジェクト、属性、および値</span><span class="sxs-lookup"><span data-stu-id="f6bd5-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="f6bd5-111">**除外**</span><span class="sxs-lookup"><span data-stu-id="f6bd5-111">**Exclusion**</span></span>|<span data-ttu-id="f6bd5-112">**例**</span><span class="sxs-lookup"><span data-stu-id="f6bd5-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="f6bd5-113">管理者が\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-113">Admini\*</span></span> |<span data-ttu-id="f6bd5-114">管理者</span><span class="sxs-lookup"><span data-stu-id="f6bd5-114">Administrator</span></span> |
|<span data-ttu-id="f6bd5-115">CAS_{\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-115">CAS_{\*</span></span>  |<span data-ttu-id="f6bd5-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="f6bd5-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="f6bd5-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="f6bd5-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="f6bd5-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="f6bd5-119">Federatedemail.\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-119">FederatedEmail\*</span></span> |<span data-ttu-id="f6bd5-120">Federatedemail..</span><span class="sxs-lookup"><span data-stu-id="f6bd5-120">FederatedEmail.</span></span> <span data-ttu-id="f6bd5-121">*GUID*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-121">*GUID*</span></span> |
|<span data-ttu-id="f6bd5-122">Guest\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-122">Guest\*</span></span> ||
|<span data-ttu-id="f6bd5-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-123">HTTPConnector\*</span></span>  |<span data-ttu-id="f6bd5-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="f6bd5-124">HTTPConnector</span></span> |
|<span data-ttu-id="f6bd5-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-125">krbtgt\*</span></span> |<span data-ttu-id="f6bd5-126">ms DS-KrbTgt-リンク</span><span class="sxs-lookup"><span data-stu-id="f6bd5-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="f6bd5-127">iusr\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-127">iusr_\*</span></span> |<span data-ttu-id="f6bd5-128">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="f6bd5-129">iwam\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-129">iwam\*</span></span>  |<span data-ttu-id="f6bd5-130">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="f6bd5-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-131">msol\*</span></span> |<span data-ttu-id="f6bd5-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="f6bd5-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="f6bd5-133">・\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-133">support_\*</span></span> ||
|<span data-ttu-id="f6bd5-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-134">SystemMailbox\*</span></span> |<span data-ttu-id="f6bd5-135">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="f6bd5-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="f6bd5-136">Wwioadadmini\*</span><span class="sxs-lookup"><span data-stu-id="f6bd5-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="f6bd5-137">distinguishedName には "\0ACNF:" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f6bd5-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="f6bd5-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="f6bd5-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="f6bd5-139">オブジェクトに IsCriticalSystemObject 属性が含まれている</span><span class="sxs-lookup"><span data-stu-id="f6bd5-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="f6bd5-140">「 [Attribute IsCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6bd5-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="f6bd5-141">IdFix によってチェックされたマルチテナントおよび専用のオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="f6bd5-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="f6bd5-142">IdFix によってエラーがチェックされる属性については、 [idfix ツールを使用して Office 365 と同期する](prepare-directory-attributes-for-synch-with-idfix.md)ように、「ディレクトリの属性を準備する」の「ディレクトリオブジェクトと属性の準備」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6bd5-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

