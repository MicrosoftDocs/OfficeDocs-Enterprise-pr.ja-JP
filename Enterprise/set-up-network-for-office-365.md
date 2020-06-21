---
title: Microsoft 365 用にネットワークをセットアップする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: '概要: Microsoft 365 のネットワークについて理解するには、次の記事を参照してください。'
ms.openlocfilehash: 4c414d8cbf597af9165e991a71e5d6a6a330e33a
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735661"
---
# <a name="set-up-your-network-for-microsoft-365"></a><span data-ttu-id="1c4c8-103">Microsoft 365 用にネットワークをセットアップする</span><span class="sxs-lookup"><span data-stu-id="1c4c8-103">Set up your network for Microsoft 365</span></span>

<span data-ttu-id="1c4c8-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="1c4c8-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="1c4c8-105">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access.</span><span class="sxs-lookup"><span data-stu-id="1c4c8-105">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access.</span></span> <span data-ttu-id="1c4c8-106">Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span><span class="sxs-lookup"><span data-stu-id="1c4c8-106">Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span></span> 

<span data-ttu-id="1c4c8-107">以下の記事を活用して主な違いを理解し、エッジ デバイス、クライアント コンピューター、オンプレミス ネットワークを変更して、オンプレミス ユーザーの最高のパフォーマンスを引き出します。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-107">Use these articles to understand the key differences and to modify your edge devices, client computers, and on-premises network to get the best performance for your on-premises users.</span></span>

## <a name="how-microsoft-365-networking-works"></a><span data-ttu-id="1c4c8-108">Microsoft 365 ネットワークのしくみ</span><span class="sxs-lookup"><span data-stu-id="1c4c8-108">How Microsoft 365 networking works</span></span>

<span data-ttu-id="1c4c8-109">Microsoft 365 の接続の概要については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-109">See these articles for an overview of connectivity for Microsoft 365:</span></span>

- [<span data-ttu-id="1c4c8-110">Microsoft 365 ネットワーク接続の概要</span><span class="sxs-lookup"><span data-stu-id="1c4c8-110">Microsoft 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="1c4c8-111">Microsoft 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="1c4c8-111">Microsoft 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="1c4c8-112">Microsoft 365 ネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="1c4c8-112">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="1c4c8-113">パフォーマンスの向上に関するアドバイスについては、「 [Microsoft 365 のネットワーク計画とパフォーマンスチューニング](network-planning-and-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-113">For advice on enhancing performance, see [Network planning and performance tuning for Microsoft 365](network-planning-and-performance.md).</span></span>

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="1c4c8-114">ネットワーク機器ベンダーとしての Microsoft 365 ネットワークのサポート</span><span class="sxs-lookup"><span data-stu-id="1c4c8-114">Support Microsoft 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="1c4c8-115">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span><span class="sxs-lookup"><span data-stu-id="1c4c8-115">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md).</span></span> <span data-ttu-id="1c4c8-116">Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span><span class="sxs-lookup"><span data-stu-id="1c4c8-116">Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="1c4c8-117">Office 365 エンドポイント</span><span class="sxs-lookup"><span data-stu-id="1c4c8-117">Office 365 endpoints</span></span>

<span data-ttu-id="1c4c8-118">エンドポイントとは、インターネット上の Office 365 トラフィックの宛先 IP アドレス、DNS ドメイン名、URL のセットのことです。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="1c4c8-119">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network.</span><span class="sxs-lookup"><span data-stu-id="1c4c8-119">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network.</span></span> <span data-ttu-id="1c4c8-120">These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span><span class="sxs-lookup"><span data-stu-id="1c4c8-120">These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="1c4c8-121">詳細については、「[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="1c4c8-122">There are currently five different Office 365 clouds.</span><span class="sxs-lookup"><span data-stu-id="1c4c8-122">There are currently five different Office 365 clouds.</span></span> <span data-ttu-id="1c4c8-123">This table takes you to the list of endpoints for each one.</span><span class="sxs-lookup"><span data-stu-id="1c4c8-123">This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="1c4c8-124">世界中のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="1c4c8-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="1c4c8-125">米国政府機関向けコミュニティ クラウド (GCC) を含む、世界中の Office 365 サブスクリプションのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="1c4c8-126">米国政府の DoD エンドポイント</span><span class="sxs-lookup"><span data-stu-id="1c4c8-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="1c4c8-127">米国国防総省 (DoD) のサブスクリプションのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="1c4c8-128">米国政府の GCC High エンドポイント</span><span class="sxs-lookup"><span data-stu-id="1c4c8-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="1c4c8-129">米国政府機関向けコミュニティ クラウド High (GCC High) サブスクリプションのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="1c4c8-130">21Vianet エンドポイントが運用している Office 365</span><span class="sxs-lookup"><span data-stu-id="1c4c8-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="1c4c8-131">中国での Office 365 のニーズを満たすために設計された、21Vianet が運用する Office 365 のエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="1c4c8-132">Office 365 Germany エンドポイント</span><span class="sxs-lookup"><span data-stu-id="1c4c8-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="1c4c8-133">ヨーロッパにある、規制が最も厳しいドイツ、欧州連合 (EU)、および欧州自由貿易連合 (EFTA) のお客様向けの特別なクラウドのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="1c4c8-134">Office 365 クラウドのエンドポイントの最新の一覧を自動的に取得するには、「[Office 365 IP アドレスと URL の Web サービス](office-365-ip-web-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="1c4c8-135">その他のエンドポイントについては次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="1c4c8-136">Web サービスに含まれていないその他のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="1c4c8-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="1c4c8-137">Office 2016 for Mac でのネットワーク要求</span><span class="sxs-lookup"><span data-stu-id="1c4c8-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a><span data-ttu-id="1c4c8-138">Microsoft 365 ネットワークに関するその他のトピック</span><span class="sxs-lookup"><span data-stu-id="1c4c8-138">Additional topics for Microsoft 365 networking</span></span>

<span data-ttu-id="1c4c8-139">Microsoft 365 ネットワークの専門的なトピックについては、以下の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-139">See these articles for specialized topics in Microsoft 365 networking:</span></span>

- [<span data-ttu-id="1c4c8-140">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="1c4c8-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="1c4c8-141">Office 365 サービスでの IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="1c4c8-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="1c4c8-142">Office 365 の NAT サポート</span><span class="sxs-lookup"><span data-stu-id="1c4c8-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a><span data-ttu-id="1c4c8-143">Microsoft 365 向け ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="1c4c8-143">ExpressRoute for Microsoft 365</span></span>

<span data-ttu-id="1c4c8-144">Office 365 トラフィック向け ExpressRoute の使用についての詳細は、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c4c8-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="1c4c8-145">Office 365 向け Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="1c4c8-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="1c4c8-146">Office 365 向け ExpressRoute の実装</span><span class="sxs-lookup"><span data-stu-id="1c4c8-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="1c4c8-147">Office 365 向け ExpressRoute でのネットワーク計画</span><span class="sxs-lookup"><span data-stu-id="1c4c8-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="1c4c8-148">Office 365 向け ExpressRoute でのルーティング</span><span class="sxs-lookup"><span data-stu-id="1c4c8-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
