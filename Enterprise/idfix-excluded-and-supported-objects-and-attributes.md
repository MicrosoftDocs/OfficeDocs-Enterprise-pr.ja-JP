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
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: idfix ツールで除外およびサポートされている属性を一覧表示します。
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085086"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="b5138-103">IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性</span><span class="sxs-lookup"><span data-stu-id="b5138-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="b5138-p101">IdFix が保持するルール セットは、マルチテナントと 専用の/ITAR の 2 種類です。現時点で、2 つのルール セットは同じオブジェクト、属性、および属性値を検索対象から除外します。この点は、将来のリリースで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b5138-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="b5138-107">IdFix によるマルチテナントおよび 専用の のエラー除外</span><span class="sxs-lookup"><span data-stu-id="b5138-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="b5138-p102">このセクションでは、idfix によってディレクトリの検索から除外されるオブジェクト、属性、および値の一覧を示します。アスタリスク (\*) は、他の文字に置き換えることができるワイルドカードです。</span><span class="sxs-lookup"><span data-stu-id="b5138-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="b5138-110">IdFix 検索で除外されるオブジェクト、属性、および値</span><span class="sxs-lookup"><span data-stu-id="b5138-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="b5138-111">**除外**</span><span class="sxs-lookup"><span data-stu-id="b5138-111">**Exclusion**</span></span>|<span data-ttu-id="b5138-112">**例**</span><span class="sxs-lookup"><span data-stu-id="b5138-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b5138-113">管理者が\*</span><span class="sxs-lookup"><span data-stu-id="b5138-113">Admini\*</span></span> |<span data-ttu-id="b5138-114">管理者</span><span class="sxs-lookup"><span data-stu-id="b5138-114">Administrator</span></span> |
|<span data-ttu-id="b5138-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="b5138-115">CAS_{\*</span></span>  |<span data-ttu-id="b5138-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="b5138-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="b5138-117">discoverysearchmailbox\*</span><span class="sxs-lookup"><span data-stu-id="b5138-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="b5138-118">discoverysearchmailbox</span><span class="sxs-lookup"><span data-stu-id="b5138-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="b5138-119">federatedemail.\*</span><span class="sxs-lookup"><span data-stu-id="b5138-119">FederatedEmail\*</span></span> |<span data-ttu-id="b5138-p103">federatedemail..*GUID*</span><span class="sxs-lookup"><span data-stu-id="b5138-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="b5138-122">ゲスト\*</span><span class="sxs-lookup"><span data-stu-id="b5138-122">Guest\*</span></span> ||
|<span data-ttu-id="b5138-123">httpconnector\*</span><span class="sxs-lookup"><span data-stu-id="b5138-123">HTTPConnector\*</span></span>  |<span data-ttu-id="b5138-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="b5138-124">HTTPConnector</span></span> |
|<span data-ttu-id="b5138-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="b5138-125">krbtgt\*</span></span> |<span data-ttu-id="b5138-126">ms DS-KrbTgt-リンク</span><span class="sxs-lookup"><span data-stu-id="b5138-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="b5138-127">iusr\*</span><span class="sxs-lookup"><span data-stu-id="b5138-127">iusr_\*</span></span> |<span data-ttu-id="b5138-128">iusr_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="b5138-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="b5138-129">iwam\*</span><span class="sxs-lookup"><span data-stu-id="b5138-129">iwam\*</span></span>  |<span data-ttu-id="b5138-130">IWAM_ *machinename*</span><span class="sxs-lookup"><span data-stu-id="b5138-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="b5138-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="b5138-131">msol\*</span></span> |<span data-ttu-id="b5138-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="b5138-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="b5138-133">・\*</span><span class="sxs-lookup"><span data-stu-id="b5138-133">support_\*</span></span> ||
|<span data-ttu-id="b5138-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="b5138-134">SystemMailbox\*</span></span> |<span data-ttu-id="b5138-135">Systemmailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="b5138-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="b5138-136">wwioadadmini\*</span><span class="sxs-lookup"><span data-stu-id="b5138-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="b5138-137">distinguishedName には "\0ACNF:" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b5138-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="b5138-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="b5138-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="b5138-139">オブジェクトには IsCriticalSystemObject 属性が含まれる</span><span class="sxs-lookup"><span data-stu-id="b5138-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="b5138-140">「 [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5138-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="b5138-141">IdFix によって検査されるマルチテナントおよび 専用の のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="b5138-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="b5138-142">idfix によってエラーがチェックされる属性については、 [idfix ツールを使用して Office 365 と同期する](prepare-directory-attributes-for-synch-with-idfix.md)ように、「ディレクトリの属性を準備する」の「ディレクトリオブジェクトと属性の準備」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5138-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

