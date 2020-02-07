---
title: Office 365 のネットワークをセットアップする
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
description: '概要: Office 365 のネットワークを理解するには、このページに記載されている記事を参照してください。'
ms.openlocfilehash: c1976a6b1ae5bff0b5f6f909ee9ab8495f371653
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844028"
---
# <a name="set-up-your-network-for-office-365"></a><span data-ttu-id="fab77-103">Office 365 のネットワークをセットアップする</span><span class="sxs-lookup"><span data-stu-id="fab77-103">Set up your network for Office 365</span></span>

<span data-ttu-id="fab77-104">*この記事は、Office 365 Enterprise および Microsoft 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="fab77-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="fab77-p101">Office 365 のオンボーディングで重要な部分は、必ず、ネットワークとインターネット接続が最適化されたアクセスとなるように設定することです。グローバルに分散されたサービスとしてのソフトウェア (SaaS) のクラウドにアクセスするためにオンプレミス ネットワークを構成することは、オンプレミスのデータセンターおよび中央インターネット接続のトラフィック用に最適化された従来のネットワークを構成する場合とは異なります。</span><span class="sxs-lookup"><span data-stu-id="fab77-p101">An important part of your Office 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span></span> 

<span data-ttu-id="fab77-107">以下の記事を活用して主な違いを理解し、エッジ デバイス、クライアント コンピューター、オンプレミス ネットワークを変更して、オンプレミス ユーザーの最高のパフォーマンスを引き出します。</span><span class="sxs-lookup"><span data-stu-id="fab77-107">Use these articles to understand the key differences and to modify your edge devices, client computers, and on-premises network to get the best performance for your on-premises users.</span></span>

## <a name="how-office-365-networking-works"></a><span data-ttu-id="fab77-108">Office 365 ネットワークのしくみ</span><span class="sxs-lookup"><span data-stu-id="fab77-108">How Office 365 networking works</span></span>

<span data-ttu-id="fab77-109">Office 365 の接続の概要については、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fab77-109">See these articles for an overview of connectivity for Office 365:</span></span>

- [<span data-ttu-id="fab77-110">Office 365 ネットワーク接続の概要</span><span class="sxs-lookup"><span data-stu-id="fab77-110">Office 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="fab77-111">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="fab77-111">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="fab77-112">Office 365 ネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="fab77-112">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="fab77-113">パフォーマンスの向上に関するアドバイスについては、「[Office 365 のネットワーク計画とパフォーマンス チューニング](network-planning-and-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fab77-113">For advice on enhancing performance, see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="fab77-114">ネットワーク機器業者として Office 365 ネットワークをサポートする</span><span class="sxs-lookup"><span data-stu-id="fab77-114">Support Office 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="fab77-p102">ネットワーク機器業者のお客様は、[Office 365 ネットワーク パートナー プログラム](office-365-networking-partner-program.md)にぜひご参加ください。ご参加いただくと、Office 365 のネットワーク接続の基本原則をお客様の会社の製品とソリューションに組み込んでいただけます。</span><span class="sxs-lookup"><span data-stu-id="fab77-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="fab77-117">Office 365 エンドポイント</span><span class="sxs-lookup"><span data-stu-id="fab77-117">Office 365 endpoints</span></span>

<span data-ttu-id="fab77-118">エンドポイントとは、インターネット上の Office 365 トラフィックの宛先 IP アドレス、DNS ドメイン名、URL のセットのことです。</span><span class="sxs-lookup"><span data-stu-id="fab77-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="fab77-p103">Office 365 のクラウドベース サービスのパフォーマンスを最適化するには、クライアント ブラウザーと境界ネットワーク内のデバイスを使用し、一部のエンドポイントに対して特別な処理を行う必要があります。これらのデバイスには、ファイアウォール、SSL 中断/検査とパケット検査デバイス、およびデータ損失防止システムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="fab77-p103">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="fab77-121">詳細については、「[Office 365 エンドポイントの管理](managing-office-365-endpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fab77-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="fab77-p104">現在、5 つの異なる Office 365 クラウドがあります。この表からそれぞれのクラウドのエンドポイント一覧へ移動できます。</span><span class="sxs-lookup"><span data-stu-id="fab77-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="fab77-124">世界中のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="fab77-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="fab77-125">米国政府機関向けコミュニティ クラウド (GCC) を含む、世界中の Office 365 サブスクリプションのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="fab77-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="fab77-126">米国政府の DoD エンドポイント</span><span class="sxs-lookup"><span data-stu-id="fab77-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="fab77-127">米国国防総省 (DoD) のサブスクリプションのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="fab77-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="fab77-128">米国政府の GCC High エンドポイント</span><span class="sxs-lookup"><span data-stu-id="fab77-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="fab77-129">米国政府機関向けコミュニティ クラウド High (GCC High) サブスクリプションのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="fab77-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="fab77-130">21Vianet エンドポイントが運用している Office 365</span><span class="sxs-lookup"><span data-stu-id="fab77-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="fab77-131">中国での Office 365 のニーズを満たすために設計された、21Vianet が運用する Office 365 のエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="fab77-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="fab77-132">Office 365 Germany エンドポイント</span><span class="sxs-lookup"><span data-stu-id="fab77-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="fab77-133">ヨーロッパにある、規制が最も厳しいドイツ、欧州連合 (EU)、および欧州自由貿易連合 (EFTA) のお客様向けの特別なクラウドのエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="fab77-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="fab77-134">Office 365 クラウドのエンドポイントの最新の一覧を自動的に取得するには、「[Office 365 IP アドレスと URL の Web サービス](office-365-ip-web-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fab77-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="fab77-135">その他のエンドポイントについては次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fab77-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="fab77-136">Web サービスに含まれていないその他のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="fab77-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="fab77-137">Office 2016 for Mac でのネットワーク要求</span><span class="sxs-lookup"><span data-stu-id="fab77-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a><span data-ttu-id="fab77-138">Office 365 ネットワークに関するその他のトピック</span><span class="sxs-lookup"><span data-stu-id="fab77-138">Additional topics for Office 365 networking</span></span>

<span data-ttu-id="fab77-139">Office 365 ネットワークの専門的なトピックについては、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fab77-139">See these articles for specialized topics in Office 365 networking:</span></span>

- [<span data-ttu-id="fab77-140">コンテンツ配信ネットワーク</span><span class="sxs-lookup"><span data-stu-id="fab77-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="fab77-141">Office 365 サービスでの IPv6 サポート</span><span class="sxs-lookup"><span data-stu-id="fab77-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="fab77-142">Office 365 の NAT サポート</span><span class="sxs-lookup"><span data-stu-id="fab77-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a><span data-ttu-id="fab77-143">Office 365 向け ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="fab77-143">ExpressRoute for Office 365</span></span>

<span data-ttu-id="fab77-144">Office 365 トラフィック向け ExpressRoute の使用についての詳細は、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fab77-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="fab77-145">Office 365 向け Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="fab77-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="fab77-146">Office 365 向け ExpressRoute の実装</span><span class="sxs-lookup"><span data-stu-id="fab77-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="fab77-147">Office 365 向け ExpressRoute でのネットワーク計画</span><span class="sxs-lookup"><span data-stu-id="fab77-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="fab77-148">Office 365 向け ExpressRoute でのルーティング</span><span class="sxs-lookup"><span data-stu-id="fab77-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
