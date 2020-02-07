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
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: IdFix ツールで除外およびサポートされている属性を一覧表示します。
ms.openlocfilehash: 0203f47864dc4222cd2f95a4e67b2f10bec44f71
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840144"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="4925e-103">IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="4925e-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="4925e-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="4925e-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="4925e-105">IdFix によって管理されるルールには2つのセットがあります。マルチテナントと専用/ITAR。</span><span class="sxs-lookup"><span data-stu-id="4925e-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="4925e-106">現時点では、2つのルールセットは同じオブジェクト、属性、および属性値を検索から除外します。</span><span class="sxs-lookup"><span data-stu-id="4925e-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="4925e-107">これは今後のリリースで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4925e-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="4925e-108">IdFix によって使用されるマルチテナントと専用エラーの除外</span><span class="sxs-lookup"><span data-stu-id="4925e-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="4925e-109">このセクションでは、IdFix によってディレクトリの検索から除外されるオブジェクト、属性、および値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="4925e-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="4925e-110">アスタリスク (\*) は、他の文字に置き換えることができるワイルドカードです。</span><span class="sxs-lookup"><span data-stu-id="4925e-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="4925e-111">IdFix 検索で除外されるオブジェクト、属性、および値</span><span class="sxs-lookup"><span data-stu-id="4925e-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="4925e-112">**除外**</span><span class="sxs-lookup"><span data-stu-id="4925e-112">**Exclusion**</span></span>|<span data-ttu-id="4925e-113">**例**</span><span class="sxs-lookup"><span data-stu-id="4925e-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4925e-114">管理者が\*</span><span class="sxs-lookup"><span data-stu-id="4925e-114">Admini\*</span></span> |<span data-ttu-id="4925e-115">管理者</span><span class="sxs-lookup"><span data-stu-id="4925e-115">Administrator</span></span> |
|<span data-ttu-id="4925e-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="4925e-116">CAS_{\*</span></span>  |<span data-ttu-id="4925e-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="4925e-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="4925e-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4925e-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="4925e-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="4925e-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="4925e-120">Federatedemail.\*</span><span class="sxs-lookup"><span data-stu-id="4925e-120">FederatedEmail\*</span></span> |<span data-ttu-id="4925e-121">Federatedemail..</span><span class="sxs-lookup"><span data-stu-id="4925e-121">FederatedEmail.</span></span> <span data-ttu-id="4925e-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="4925e-122">*GUID*</span></span> |
|<span data-ttu-id="4925e-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="4925e-123">Guest\*</span></span> ||
|<span data-ttu-id="4925e-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="4925e-124">HTTPConnector\*</span></span>  |<span data-ttu-id="4925e-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="4925e-125">HTTPConnector</span></span> |
|<span data-ttu-id="4925e-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="4925e-126">krbtgt\*</span></span> |<span data-ttu-id="4925e-127">ms DS-KrbTgt-リンク</span><span class="sxs-lookup"><span data-stu-id="4925e-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="4925e-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="4925e-128">iusr_\*</span></span> |<span data-ttu-id="4925e-129">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="4925e-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="4925e-130">iwam\*</span><span class="sxs-lookup"><span data-stu-id="4925e-130">iwam\*</span></span>  |<span data-ttu-id="4925e-131">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="4925e-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="4925e-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="4925e-132">msol\*</span></span> |<span data-ttu-id="4925e-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="4925e-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="4925e-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="4925e-134">support_\*</span></span> ||
|<span data-ttu-id="4925e-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4925e-135">SystemMailbox\*</span></span> |<span data-ttu-id="4925e-136">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="4925e-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="4925e-137">Wwioadadmini\*</span><span class="sxs-lookup"><span data-stu-id="4925e-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="4925e-138">distinguishedName には "\0ACNF:" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4925e-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="4925e-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="4925e-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="4925e-140">オブジェクトに IsCriticalSystemObject 属性が含まれている</span><span class="sxs-lookup"><span data-stu-id="4925e-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="4925e-141">「 [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4925e-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="4925e-142">IdFix によってチェックされたマルチテナントおよび専用のオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="4925e-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="4925e-143">IdFix によってエラーがチェックされる属性については、 [idfix ツールを使用して Office 365 と同期する](prepare-directory-attributes-for-synch-with-idfix.md)ように、「ディレクトリの属性を準備する」の「ディレクトリオブジェクトと属性の準備」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4925e-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

