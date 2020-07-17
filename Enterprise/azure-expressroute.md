---
title: Office 365 向け Azure ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Office 365 で Azure ExpressRoute を使用する方法と、Office 365 で使用するために Azure ExpressRoute を展開する場合に必要となるネットワーク実装プロジェクトを計画する方法について説明します。
ms.openlocfilehash: 80b42fc43f395d9dd94384d456d40eb536541746
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997951"
---
# <a name="azure-expressroute-for-office-365"></a><span data-ttu-id="67a3f-103">Office 365 向け Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="67a3f-103">Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="67a3f-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="67a3f-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="67a3f-105">Office 365 で Azure ExpressRoute を使用する方法と、Office 365 で使用するために Azure ExpressRoute を展開する場合に必要となるネットワーク実装プロジェクトを計画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-105">Learn how Azure ExpressRoute is used with Office 365 and how to plan the network implementation project that will be required if you are deploying Azure ExpressRoute for use with Office 365.</span></span> <span data-ttu-id="67a3f-106">多くの場合、Azure で実行されるインフラストラクチャおよびプラットフォームサービスは、ネットワークアーキテクチャとパフォーマンスに関する考慮事項に対処することでメリットを得られます。</span><span class="sxs-lookup"><span data-stu-id="67a3f-106">Infrastructure and platform services running in Azure will often benefit by addressing network architecture and performance considerations.</span></span> <span data-ttu-id="67a3f-107">このような場合は、Azure に ExpressRoute をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="67a3f-107">We recommend ExpressRoute for Azure in these cases.</span></span> <span data-ttu-id="67a3f-108">Office 365 や Dynamics 365 などのサービスとしてのソフトウェアは、インターネットを介して安全かつ確実にアクセスできるように構築されています。</span><span class="sxs-lookup"><span data-stu-id="67a3f-108">Software as a Service offerings like Office 365 and Dynamics 365 have been built to be accessed securely and reliably via the Internet.</span></span> <span data-ttu-id="67a3f-109">「 [Office 365 のネットワーク接続の評価](assessing-network-connectivity.md)」の記事では、インターネットのパフォーマンスとセキュリティについて説明し、「office 365 用の Azure ExpressRoute」を検討することができます。</span><span class="sxs-lookup"><span data-stu-id="67a3f-109">You can read about Internet performance and security and when you might consider Azure ExpressRoute for Office 365 in the article [Assessing Office 365 network connectivity](assessing-network-connectivity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="67a3f-110">Office 365 の ExpressRoute を使用するには、Microsoft の承認が必要です。</span><span class="sxs-lookup"><span data-stu-id="67a3f-110">Microsoft authorization is required to use ExpressRoute for Office 365.</span></span> <span data-ttu-id="67a3f-111">お客様の規制要件で直接的な接続が義務付けられている場合、Microsoft はお客様のすべての要求をレビューし、Office 365 の使用状況を承認します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-111">Microsoft reviews every customer request and authorizes ExpressRoute for Office 365 usage when a customer's regulatory requirement mandates direct connectivity.</span></span> <span data-ttu-id="67a3f-112">このような要件がある場合は、テキストの抜粋と web リンクを入力してください。これは、Microsoft レビューを開始するために、 [Office 365 の ExpressRoute の要求フォーム](https://aka.ms/O365ERReview)に直接接続する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-112">If you have such requirements, please provide the text excerpt and web link to the regulation which you interpret to mean that direct connectivity is required in the [ExpressRoute for Office 365 Request Form](https://aka.ms/O365ERReview) to begin a Microsoft review.</span></span> <span data-ttu-id="67a3f-113">承認されていないサブスクリプション Office 365 のルートフィルターを作成しようとすると、[エラーメッセージ](https://support.microsoft.com/kb/3181709)が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67a3f-113">Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>

<span data-ttu-id="67a3f-114">これで、選択した Office 365 のネットワークトラフィックに対して、Office 365 への直接ネットワーク接続を追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="67a3f-114">You can now add a direct network connection to Office 365 for selected Office 365 network traffic.</span></span> <span data-ttu-id="67a3f-115">Azure ExpressRoute は直接接続で予測可能なパフォーマンスを提供し、Microsoft ネットワークコンポーネントの稼働時間の SLA を99.95% にします。</span><span class="sxs-lookup"><span data-stu-id="67a3f-115">Azure ExpressRoute offers a direct connection, predictable performance, and comes with an uptime SLA of 99.95% for the Microsoft networking components.</span></span> <span data-ttu-id="67a3f-116">Azure ExpressRoute でサポートされていないサービスに対しては、インターネット接続が依然として必要になります。</span><span class="sxs-lookup"><span data-stu-id="67a3f-116">You'll still require an internet connection for services that aren't supported over Azure ExpressRoute.</span></span>

## <a name="planning-azure-expressroute-for-office-365"></a><span data-ttu-id="67a3f-117">Office 用 Azure ExpressRoute の計画365</span><span class="sxs-lookup"><span data-stu-id="67a3f-117">Planning Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="67a3f-118">インターネット接続に加えて、Office 365 ネットワークトラフィックのサブセットを、予測可能で、Microsoft ネットワークコンポーネントに対して99.95% の稼働時間の SLA を提供する直接接続でルーティングするように選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="67a3f-118">In addition to internet connectivity, you may choose to route a subset of their Office 365 network traffic over a direct connection that offers predictability and a 99.95% uptime SLA for the Microsoft networking components.</span></span> <span data-ttu-id="67a3f-119">Azure ExpressRoute には、Office 365 およびその他の Microsoft クラウドサービスへの専用ネットワーク接続が用意されています。</span><span class="sxs-lookup"><span data-stu-id="67a3f-119">Azure ExpressRoute provides you with this dedicated network connection to Office 365 and other Microsoft cloud services.</span></span>

<span data-ttu-id="67a3f-120">既存の MPLS WAN を使用しているかどうかに関係なく、ExpressRoute は3つの方法のいずれかでネットワークアーキテクチャに追加できます。サポートされているクラウド exchange コロケーションプロバイダー、イーサネットポイントツーポイント接続プロバイダー、または MPLS 接続プロバイダを介して。</span><span class="sxs-lookup"><span data-stu-id="67a3f-120">Regardless of whether you have an existing MPLS WAN, ExpressRoute can be added to your network architecture in one of three ways; through a supported cloud exchange co-location provider, an Ethernet point-to-point connection provider, or through an MPLS connection provider.</span></span> <span data-ttu-id="67a3f-121">[お客様の地域で利用可能なプロバイダーを](https://azure.microsoft.com/documentation/articles/expressroute-locations/)参照してください。</span><span class="sxs-lookup"><span data-stu-id="67a3f-121">See what [providers are available in your region](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="67a3f-122">Direct ExpressRoute 接続を使用すると、 [Office 365 サービスに含まれて](azure-expressroute.md#BKMK_WhatDoIGet)いるアプリケーションへの接続を有効にすることができます。次の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67a3f-122">The direct ExpressRoute connection will enable connectivity to the applications outlined in [What Office 365 services are included?](azure-expressroute.md#BKMK_WhatDoIGet) below.</span></span> <span data-ttu-id="67a3f-123">他のすべてのアプリケーションおよびサービスのネットワークトラフィックは、引き続きインターネットをスキャンします。</span><span class="sxs-lookup"><span data-stu-id="67a3f-123">Network traffic for all other applications and services will continue to traverse the internet.</span></span>

<span data-ttu-id="67a3f-124">Office 365、Windows Update、TechNet などのすべての Microsoft アプリケーションにアクセスするためにインターネット経由で Microsoft のデータセンターに接続する一般的な Office 365 ユーザーの場合は、次のような高レベルのネットワーク図を検討してください。</span><span class="sxs-lookup"><span data-stu-id="67a3f-124">Consider the following high level network diagram which shows a typical Office 365 customer connecting to Microsoft's datacenters over the internet for access to all Microsoft applications such as Office 365, Windows Update, and TechNet.</span></span> <span data-ttu-id="67a3f-125">お客様は、オンプレミスのネットワークから接続しているか、独立したインターネット接続から接続しているかに関係なく、同じネットワークパスを使用します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-125">Customers use a similar network path regardless of whether they're connecting from an on-premises network or from an independent internet connection.</span></span>

![Office 365 のネットワーク接続](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

<span data-ttu-id="67a3f-127">次に、インターネットと ExpressRoute の両方を使用して Office 365 に接続する Office 365 お客様を示す、更新された図を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="67a3f-127">Now look at the updated diagram which depicts an Office 365 customer who uses both the internet and ExpressRoute to connect to Office 365.</span></span> <span data-ttu-id="67a3f-128">パブリック DNS およびコンテンツ配信ネットワークノードなどの一部の接続では、依然としてパブリックインターネット接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="67a3f-128">Notice that some connections such as Public DNS and Content Delivery Network nodes still require the public internet connection.</span></span> <span data-ttu-id="67a3f-129">また、お客様の ExpressRoute の接続構築に配置されていないユーザーは、インターネットを介して接続していることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="67a3f-129">Also notice the customer's users who are not located in their ExpressRoute connected building are connecting over the Internet.</span></span>

![ExpressRoute を使用した Office 365 接続](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

<span data-ttu-id="67a3f-131">さらに情報が必要な場合</span><span class="sxs-lookup"><span data-stu-id="67a3f-131">Still want more information?</span></span> <span data-ttu-id="67a3f-132">[Azure expressroute For office 365 を使用してネットワークトラフィックを管理](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)する方法と、 [office 365 用に azure expressroute を構成](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-132">Learn how to [manage your network traffic with Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) and learn how to [configure Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).</span></span> <span data-ttu-id="67a3f-133">また、より詳細な概念を説明するため、Channel 9 の「 [Office 365 の Azure ExpressRoute のための10の](https://channel9.msdn.com/series/aer)パーツを記録しました。</span><span class="sxs-lookup"><span data-stu-id="67a3f-133">We've also recorded a 10 part [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to help explain the concepts more thoroughly.</span></span>

## <a name="what-office-365-services-are-included"></a><span data-ttu-id="67a3f-134">どの Office 365 サービスが含まれていますか?</span><span class="sxs-lookup"><span data-stu-id="67a3f-134">What Office 365 services are included?</span></span>
<span data-ttu-id="67a3f-135"><a name="BKMK_WhatDoIGet"> </a></span><span class="sxs-lookup"><span data-stu-id="67a3f-135"><a name="BKMK_WhatDoIGet"> </a></span></span>

<span data-ttu-id="67a3f-136">次の表に、ExpressRoute でサポートされている Office 365 サービスの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-136">The following table lists the Office 365 services that are supported over ExpressRoute.</span></span> <span data-ttu-id="67a3f-137">[Office 365 エンドポイントの記事](https://aka.ms/o365endpoints)を参照して、これらのアプリケーションのネットワーク要求がインターネット接続を必要とするかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="67a3f-137">Please review the [Office 365 endpoints article](https://aka.ms/o365endpoints) to understand which network requests for these applications require internet connectivity.</span></span>

|<span data-ttu-id="67a3f-138">**含まれるアプリケーション**</span><span class="sxs-lookup"><span data-stu-id="67a3f-138">**Applications included**</span></span>|
|:-----|
|<span data-ttu-id="67a3f-139">Exchange Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-139">Exchange Online<sup>1</sup></span></span> <br/> <span data-ttu-id="67a3f-140">Exchange Online Protection<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-140">Exchange Online Protection<sup>1</sup></span></span> <br/> <span data-ttu-id="67a3f-141">Delve<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-141">Delve<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="67a3f-142">Skype for Business Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-142">Skype for Business Online<sup>1</sup></span></span> <br/> <span data-ttu-id="67a3f-143">Microsoft Teams <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-143">Microsoft Teams <sup>1</sup></span></span> <br/> |
|<span data-ttu-id="67a3f-144">SharePoint Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-144">SharePoint Online<sup>1</sup></span></span> <br/> <span data-ttu-id="67a3f-145">OneDrive for Business<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-145">OneDrive for Business<sup>1</sup></span></span> <br/> <span data-ttu-id="67a3f-146">Project Online<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-146">Project Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="67a3f-147">ポータルと共有<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-147">Portal and shared<sup>1</sup></span></span> <br/> <span data-ttu-id="67a3f-148">Azure Active Directory<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-148">Azure Active Directory<sup>1</sup></span></span> <br/> <span data-ttu-id="67a3f-149">AAD Connect<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-149">AAD Connect<sup>1</sup></span></span> <br/> <span data-ttu-id="67a3f-150">Office<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="67a3f-150">Office<sup>1</sup></span></span> <br/> |

<span data-ttu-id="67a3f-151"><sup>1</sup>これらの各アプリケーションには、ExpressRoute でサポートされていないインターネット接続要件があります。詳細については、「 [Office 365 endpoints](https://aka.ms/o365endpoints) 」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67a3f-151"><sup>1</sup>Each of these applications have internet connectivity requirements not supported over ExpressRoute, see the [Office 365 endpoints article](https://aka.ms/o365endpoints) for more information.</span></span>

<span data-ttu-id="67a3f-152">Office 365 用の ExpressRoute に含まれていないサービスは、エンタープライズクライアントのダウンロード用の Microsoft 365 アプリ、オンプレミスの Id プロバイダーのサインイン、および中国での Office 365 (21 Vianet) サービスを対象としています。</span><span class="sxs-lookup"><span data-stu-id="67a3f-152">The services that aren't included with ExpressRoute for Office 365 are Microsoft 365 Apps for enterprise client downloads, On-premises Identity Provider Sign-In, and Office 365 (operated by 21 Vianet) service in China.</span></span>

## <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="67a3f-153">Office 365 向け ExpressRoute の実装</span><span class="sxs-lookup"><span data-stu-id="67a3f-153">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="67a3f-154">ExpressRoute を実装するには、ネットワークとアプリケーションの所有者の関与が必要であり、新しい[ネットワークルーティングアーキテクチャ](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)、帯域幅の要件、セキュリティを実装する場所、高可用性などを決定するための慎重な計画が必要です。</span><span class="sxs-lookup"><span data-stu-id="67a3f-154">Implementing ExpressRoute requires the involvement of network and application owners and requires careful planning to determine the new [network routing architecture](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandwidth requirements, where security will be implemented, high availability, and so on.</span></span> <span data-ttu-id="67a3f-155">ExpressRoute を実装するには、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="67a3f-155">To implement ExpressRoute, you'll need to:</span></span>

1. <span data-ttu-id="67a3f-156">Office 365 の接続計画で ExpressRoute が満たす必要があることを完全に理解します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-156">Fully understand the need ExpressRoute satisfies in your Office 365 connectivity planning.</span></span> <span data-ttu-id="67a3f-157">インターネットまたは ExpressRoute を使用するアプリケーションについて理解し、Office 365 トラフィック用のインターネットと ExpressRoute の両方を使用して、ネットワークの容量、セキュリティ、高可用性の要件を十分に計画します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-157">Understand what applications will use the internet or ExpressRoute and fully plan your network capacity, security, and high availability needs in the context of using both the internet and ExpressRoute for Office 365 traffic.</span></span>

2. <span data-ttu-id="67a3f-158">インターネットと ExpressRoute の両方のトラフィックについて、出口およびピアリングの場所を<sup>決定します</sup>。</span><span class="sxs-lookup"><span data-stu-id="67a3f-158">Determine the egress and peering locations for both internet and ExpressRoute traffic<sup>1</sup>.</span></span>

3. <span data-ttu-id="67a3f-159">インターネットおよび ExpressRoute の接続に必要な容量を決定します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-159">Determine the capacity required on the internet and ExpressRoute connections.</span></span>

4. <span data-ttu-id="67a3f-160">セキュリティおよびその他の標準的な境界のコントロール<sup>1</sup>を実装するための計画を立ててください。</span><span class="sxs-lookup"><span data-stu-id="67a3f-160">Have a plan in place for implementing security and other standard perimeter controls<sup>1</sup>.</span></span>

5. <span data-ttu-id="67a3f-161">ExpressRoute にサブスクライブするには、有効な Microsoft Azure アカウントが必要です。</span><span class="sxs-lookup"><span data-stu-id="67a3f-161">Have a valid Microsoft Azure account to subscribe to ExpressRoute.</span></span>

6. <span data-ttu-id="67a3f-162">接続モデルと[承認済みプロバイダー](https://azure.microsoft.com/documentation/articles/expressroute-locations/)を選択します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-162">Select a connectivity model and an [approved provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/).</span></span> <span data-ttu-id="67a3f-163">お客様は複数の接続モデルまたはパートナーを選択できるため、パートナーは既存のネットワークプロバイダーと同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="67a3f-163">Keep in mind, customers can select multiple connectivity models or partners and the partner doesn't need to be the same as your existing network provider.</span></span>

7. <span data-ttu-id="67a3f-164">ExpressRoute にトラフィックを誘導する前に展開を検証します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-164">Validate deployment prior to directing traffic to ExpressRoute.</span></span>

8. <span data-ttu-id="67a3f-165">必要に応じて[QoS を実装](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)し、地域の拡張を評価します。</span><span class="sxs-lookup"><span data-stu-id="67a3f-165">Optionally [implement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) and evaluate regional expansion.</span></span>

<span data-ttu-id="67a3f-166"><sup>1</sup>パフォーマンスに関する重要な考慮事項。</span><span class="sxs-lookup"><span data-stu-id="67a3f-166"><sup>1</sup>Important performance considerations.</span></span> <span data-ttu-id="67a3f-167">ここでの決定は、Skype for Business などのアプリケーションにとって重要な待機時間に大きな影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="67a3f-167">Decisions here can dramatically impact latency which is a critical for applications such as Skype for Business.</span></span>

<span data-ttu-id="67a3f-168">その他の参照については、 [ExpressRoute のドキュメント](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)に加えて、[ルーティングガイド](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)を使用してください。</span><span class="sxs-lookup"><span data-stu-id="67a3f-168">For additional references, use our [routing guide](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) in addition to the [ExpressRoute documentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).</span></span>

<span data-ttu-id="67a3f-169">Office 365 の ExpressRoute を購入するには、1つまたは複数の[承認](https://azure.microsoft.com/documentation/articles/expressroute-locations/)されたプロバイダーと連携して、必要な数とサイズの回路を ExpressRoute Premium サブスクリプションでプロビジョニングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="67a3f-169">To purchase ExpressRoute for Office 365, you'll need to work with one or more [approved providers](https://azure.microsoft.com/documentation/articles/expressroute-locations/) to provision the desired number and size circuits with an ExpressRoute Premium subscription.</span></span> <span data-ttu-id="67a3f-170">Office 365 から購入する追加のライセンスはありません。</span><span class="sxs-lookup"><span data-stu-id="67a3f-170">There are no additional licenses to purchase from Office 365.</span></span>

<span data-ttu-id="67a3f-171">ここに戻る場合は、次の短いリンクをご利用ください: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="67a3f-171">Here's a short link you can use to come back: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span></span>

<span data-ttu-id="67a3f-172">[Office 365 の ExpressRoute](https://aka.ms/ert)にサインアップする準備ができましたか?</span><span class="sxs-lookup"><span data-stu-id="67a3f-172">Ready to sign-up for [ExpressRoute for Office 365](https://aka.ms/ert)?</span></span>

## <a name="related-topics"></a><span data-ttu-id="67a3f-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="67a3f-173">Related Topics</span></span>

[<span data-ttu-id="67a3f-174">Office 365 のネットワーク接続の評価</span><span class="sxs-lookup"><span data-stu-id="67a3f-174">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

[<span data-ttu-id="67a3f-175">Office 365 向け ExpressRoute の管理</span><span class="sxs-lookup"><span data-stu-id="67a3f-175">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)

[<span data-ttu-id="67a3f-176">Office 365 向け ExpressRoute でのルーティング</span><span class="sxs-lookup"><span data-stu-id="67a3f-176">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)

[<span data-ttu-id="67a3f-177">Office 365 向け ExpressRoute でのネットワーク計画</span><span class="sxs-lookup"><span data-stu-id="67a3f-177">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)

[<span data-ttu-id="67a3f-178">Office 365 向け ExpressRoute の実装</span><span class="sxs-lookup"><span data-stu-id="67a3f-178">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)

[<span data-ttu-id="67a3f-179">Office 365 シナリオ用の ExpressRoute での BGP コミュニティの使用 (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="67a3f-179">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)

[<span data-ttu-id="67a3f-180">Skype for Business Online でのメディア品質とネットワーク接続のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="67a3f-180">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[<span data-ttu-id="67a3f-181">ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="67a3f-181">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="67a3f-182">Office 365 のパフォーマンスに関するトラブルシューティングの計画</span><span class="sxs-lookup"><span data-stu-id="67a3f-182">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="67a3f-183">Office 365 の URL および IP アドレスの範囲</span><span class="sxs-lookup"><span data-stu-id="67a3f-183">Office 365 URLs and IP address ranges</span></span>](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[<span data-ttu-id="67a3f-184">Office 365 のネットワークとパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="67a3f-184">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

## <a name="see-also"></a><span data-ttu-id="67a3f-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="67a3f-185">See also</span></span>

[<span data-ttu-id="67a3f-186">Microsoft 365 Enterprise の概要</span><span class="sxs-lookup"><span data-stu-id="67a3f-186">Microsoft 365 Enterprise overview</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
