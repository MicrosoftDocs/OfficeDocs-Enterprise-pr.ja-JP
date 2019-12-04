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
ms.openlocfilehash: e57507688fe1efd21bb629b4fad297129eff55d6
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813927"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="4e5de-103">IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="4e5de-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="4e5de-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="4e5de-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="4e5de-105">IdFix によって管理されるルールには2つのセットがあります。マルチテナントと専用/ITAR。</span><span class="sxs-lookup"><span data-stu-id="4e5de-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="4e5de-106">現時点では、2つのルールセットは同じオブジェクト、属性、および属性値を検索から除外します。</span><span class="sxs-lookup"><span data-stu-id="4e5de-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="4e5de-107">これは今後のリリースで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4e5de-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="4e5de-108">IdFix によって使用されるマルチテナントと専用エラーの除外</span><span class="sxs-lookup"><span data-stu-id="4e5de-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="4e5de-109">このセクションでは、IdFix によってディレクトリの検索から除外されるオブジェクト、属性、および値の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="4e5de-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="4e5de-110">アスタリスク (\*) は、他の文字に置き換えることができるワイルドカードです。</span><span class="sxs-lookup"><span data-stu-id="4e5de-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="4e5de-111">IdFix 検索で除外されるオブジェクト、属性、および値</span><span class="sxs-lookup"><span data-stu-id="4e5de-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="4e5de-112">**除外**</span><span class="sxs-lookup"><span data-stu-id="4e5de-112">**Exclusion**</span></span>|<span data-ttu-id="4e5de-113">**例**</span><span class="sxs-lookup"><span data-stu-id="4e5de-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4e5de-114">管理者が\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-114">Admini\*</span></span> |<span data-ttu-id="4e5de-115">管理者</span><span class="sxs-lookup"><span data-stu-id="4e5de-115">Administrator</span></span> |
|<span data-ttu-id="4e5de-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-116">CAS_{\*</span></span>  |<span data-ttu-id="4e5de-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="4e5de-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="4e5de-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="4e5de-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="4e5de-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="4e5de-120">Federatedemail.\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-120">FederatedEmail\*</span></span> |<span data-ttu-id="4e5de-121">Federatedemail..</span><span class="sxs-lookup"><span data-stu-id="4e5de-121">FederatedEmail.</span></span> <span data-ttu-id="4e5de-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="4e5de-122">*GUID*</span></span> |
|<span data-ttu-id="4e5de-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-123">Guest\*</span></span> ||
|<span data-ttu-id="4e5de-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-124">HTTPConnector\*</span></span>  |<span data-ttu-id="4e5de-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="4e5de-125">HTTPConnector</span></span> |
|<span data-ttu-id="4e5de-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-126">krbtgt\*</span></span> |<span data-ttu-id="4e5de-127">ms DS-KrbTgt-リンク</span><span class="sxs-lookup"><span data-stu-id="4e5de-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="4e5de-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-128">iusr_\*</span></span> |<span data-ttu-id="4e5de-129">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="4e5de-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="4e5de-130">iwam\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-130">iwam\*</span></span>  |<span data-ttu-id="4e5de-131">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="4e5de-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="4e5de-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-132">msol\*</span></span> |<span data-ttu-id="4e5de-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="4e5de-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="4e5de-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-134">support_\*</span></span> ||
|<span data-ttu-id="4e5de-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-135">SystemMailbox\*</span></span> |<span data-ttu-id="4e5de-136">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="4e5de-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="4e5de-137">Wwioadadmini\*</span><span class="sxs-lookup"><span data-stu-id="4e5de-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="4e5de-138">distinguishedName には "\0ACNF:" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e5de-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="4e5de-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="4e5de-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="4e5de-140">オブジェクトに IsCriticalSystemObject 属性が含まれている</span><span class="sxs-lookup"><span data-stu-id="4e5de-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="4e5de-141">「 [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e5de-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="4e5de-142">IdFix によってチェックされたマルチテナントおよび専用のオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="4e5de-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="4e5de-143">IdFix によってエラーがチェックされる属性については、 [idfix ツールを使用して Office 365 と同期する](prepare-directory-attributes-for-synch-with-idfix.md)ように、「ディレクトリの属性を準備する」の「ディレクトリオブジェクトと属性の準備」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e5de-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

