---
title: IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: 除外され、IdFix ツールでサポートされている属性の一覧を表示します。
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541662"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="6a8c3-103">IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="6a8c3-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="6a8c3-p101">IdFix が保持するルール セットは、マルチテナントと 専用の/ITAR の 2 種類です。現時点で、2 つのルール セットは同じオブジェクト、属性、および属性値を検索対象から除外します。この点は、将来のリリースで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6a8c3-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="6a8c3-107">IdFix によるマルチテナントおよび 専用の のエラー除外</span><span class="sxs-lookup"><span data-stu-id="6a8c3-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="6a8c3-p102">このセクションには、オブジェクト、属性、および IdFix は、ディレクトリの検索から除外する値が一覧表示されます。アスタリスク (\*) の代わりに他の文字をワイルドカードです。</span><span class="sxs-lookup"><span data-stu-id="6a8c3-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="6a8c3-110">IdFix 検索で除外されるオブジェクト、属性、および値</span><span class="sxs-lookup"><span data-stu-id="6a8c3-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="6a8c3-111">**除外**</span><span class="sxs-lookup"><span data-stu-id="6a8c3-111">**Exclusion**</span></span>|<span data-ttu-id="6a8c3-112">**使用例**</span><span class="sxs-lookup"><span data-stu-id="6a8c3-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="6a8c3-113">Admini\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-113">Admini\*</span></span> |<span data-ttu-id="6a8c3-114">管理者</span><span class="sxs-lookup"><span data-stu-id="6a8c3-114">Administrator</span></span> |
|<span data-ttu-id="6a8c3-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-115">CAS_{\*</span></span>  |<span data-ttu-id="6a8c3-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="6a8c3-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="6a8c3-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="6a8c3-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="6a8c3-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="6a8c3-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-119">FederatedEmail\*</span></span> |<span data-ttu-id="6a8c3-p103">FederatedEmail。*GUID*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="6a8c3-122">ゲスト\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-122">Guest\*</span></span> ||
|<span data-ttu-id="6a8c3-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-123">HTTPConnector\*</span></span>  |<span data-ttu-id="6a8c3-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="6a8c3-124">HTTPConnector</span></span> |
|<span data-ttu-id="6a8c3-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-125">krbtgt\*</span></span> |<span data-ttu-id="6a8c3-126">ms DS KrbTgt リンク</span><span class="sxs-lookup"><span data-stu-id="6a8c3-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="6a8c3-127">iusr _\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-127">iusr_\*</span></span> |<span data-ttu-id="6a8c3-128">iusr _*コンピューター名*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="6a8c3-129">iwam\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-129">iwam\*</span></span>  |<span data-ttu-id="6a8c3-130">Iwam _*コンピューター名*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="6a8c3-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-131">msol\*</span></span> |<span data-ttu-id="6a8c3-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="6a8c3-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="6a8c3-133">support_\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-133">support_\*</span></span> ||
|<span data-ttu-id="6a8c3-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-134">SystemMailbox\*</span></span> |<span data-ttu-id="6a8c3-135">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="6a8c3-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="6a8c3-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="6a8c3-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="6a8c3-137">識別名が含まれています"\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="6a8c3-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="6a8c3-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="6a8c3-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="6a8c3-139">オブジェクトには IsCriticalSystemObject 属性が含まれる</span><span class="sxs-lookup"><span data-stu-id="6a8c3-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="6a8c3-140">[IsCriticalSystemObject の属性](https://go.microsoft.com/fwlink/p/?LinkId=401169)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a8c3-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="6a8c3-141">IdFix によって検査されるマルチテナントおよび 専用の のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="6a8c3-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="6a8c3-142">IdFix でエラーをチェックされている属性は、「ディレクトリ オブジェクトと属性の準備」で[IdFix ツールを使用して Office 365 と同期の準備ディレクトリの属性](prepare-directory-attributes-for-synch-with-idfix.md)で説明します。</span><span class="sxs-lookup"><span data-stu-id="6a8c3-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

