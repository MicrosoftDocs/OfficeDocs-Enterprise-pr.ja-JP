---
title: Office 365 向け Azure ExpressRoute
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Office 365 で Azure の ExpressRoute を使用する方法と、Office 365 で使用するための Azure ExpressRoute を展開する場合に求められるネットワークの実装プロジェクトを計画する方法について説明します。
ms.openlocfilehash: 5a82576b541e27c70bca490ff8dfe887ee879c83
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541550"
---
# <a name="azure-expressroute-for-office-365"></a><span data-ttu-id="1010c-103">Office 365 向け Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="1010c-103">Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="1010c-p101">Office 365 で Azure の ExpressRoute を使用する方法と、Office 365 で使用するための Azure ExpressRoute を展開する場合に求められるネットワークの実装プロジェクトを計画する方法について説明します。Azure で実行されているインフラストラクチャおよびプラットフォームのサービスは、ネットワーク アーキテクチャとパフォーマンスの考慮事項に対応することでメリットは多くの場合。Azure の ExpressRoute は、このような場合にお勧めします。としてサービスの提供、インターネット経由で安全かつ確実にアクセスするのには、Office 365、Dynamics 365 をビルドされているようなソフトウェアです。したがって、のみをお勧め ExpressRoute 特定のシナリオでこれらのアプリケーションです。インターネットのパフォーマンスとセキュリティを使用して Office 365 の[Office 365 へのネットワーク接続](network-connectivity.md)の資料に、Azure ExpressRoute を検討する可能性がありますを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="1010c-p101">Learn how Azure ExpressRoute is used with Office 365 and how to plan the network implementation project that will be required if you are deploying Azure ExpressRoute for use with Office 365. Infrastructure and platform services running in Azure will often benefit by addressing network architecture and performance considerations. We recommend ExpressRoute for Azure in these cases. Software as a Service offerings like Office 365 and Dynamics 365 have been built to be accessed securely and reliably via the Internet. Accordingly, we only recommend ExpressRoute for these applications in specific scenarios. You can read about Internet performance and security and when you might consider Azure ExpressRoute for Office 365 in the article [Network connectivity to Office 365](network-connectivity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1010c-p102">2017 年 7 月 31日の開始からは、Azure の管理コンソールまたは PowerShell を使用して直接 Microsoft Peering を有効にできます。Microsoft Peering を有効にすると、特定の BGP ルートのアドバタイズを受信するルート フィルターを作成できます。Office 365 のフィルターを作成するための承認を必要があり、いつでも Dynamics 365 お客様との契約 (旧 CRM Online) のアプリケーション フィルターを作成できます。Office 365 のルートのフィルターを作成するための承認を取得するプロセスについては、マイクロソフト アカウント チームに説明します。[エラー メッセージ](https://support.microsoft.com/kb/3181709)を取得するは、承認されていないサブスクリプションの Office 365 のルート フィルターを作成しようとしています。</span><span class="sxs-lookup"><span data-stu-id="1010c-p102">Starting July 31st, 2017, you can enable Microsoft Peering directly from the Azure Administrative console or using PowerShell. After enabling Microsoft Peering, you can create route filters to receive specific BGP route advertisements. You'll need authorization to create filters for Office 365 and can create Dynamics 365 Customer Engagement applications (formerly known as CRM Online) filters at any time. Talk to your Microsoft Account team about the process to obtain authorization to create Office 365 route filters. Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709)</span></span>

<span data-ttu-id="1010c-p103">選択した Office 365 のネットワーク トラフィックを Office 365 に今すぐネットワークに直接接続を追加できます。Azure の ExpressRoute は、予測可能なパフォーマンスは、直接接続を提供していますが、Microsoft ネットワーク コンポーネントの稼働時間 SLA 99.95% が付属しています。Azure ExpressRoute 経由でサポートされていないサービスのインターネットに接続を要求することもあります。</span><span class="sxs-lookup"><span data-stu-id="1010c-p103">You can now add a direct network connection to Office 365 for selected Office 365 network traffic. Azure ExpressRoute offers a direct connection, predictable performance, and comes with an uptime SLA of 99.95% for the Microsoft networking components. You'll still require an internet connection for services that aren't supported over Azure ExpressRoute.</span></span>

## <a name="planning-azure-expressroute-for-office-365"></a><span data-ttu-id="1010c-118">Office 365 を Azure の ExpressRoute を計画します。</span><span class="sxs-lookup"><span data-stu-id="1010c-118">Planning Azure ExpressRoute for Office 365</span></span>

<span data-ttu-id="1010c-p104">インターネット接続のほか、Office 365 のネットワーク トラフィックのサブセットを予測可能性と、99.95% の稼働時間 SLA の Microsoft ネットワーク コンポーネントへの直接接続経由でルーティングすることができます。Azure ExpressRoute に、この専用のネットワーク接続にする Office 365 とその他のマイクロソフトのクラウド サービスに提供します。</span><span class="sxs-lookup"><span data-stu-id="1010c-p104">In addition to internet connectivity, you may choose to route a subset of their Office 365 network traffic over a direct connection that offers predictability and a 99.95% uptime SLA for the Microsoft networking components. Azure ExpressRoute provides you with this dedicated network connection to Office 365 and other Microsoft cloud services.</span></span>

<span data-ttu-id="1010c-p105">既存 MPLS WAN は、次の 3 つの方法の 1 つのネットワーク アーキテクチャに ExpressRoute を追加できます。クラウドがサポートされている exchange コロケーション プロバイダー、イーサネット ポイント ツー ポイント接続のプロバイダー、または MPLS 接続プロバイダーを使用します。どのような[プロバイダーは、お住まいの地域で利用可能な](https://azure.microsoft.com/documentation/articles/expressroute-locations/)を参照してください。ExpressRoute の直接の接続はで説明されているアプリケーションへの接続を有効にする[どのような Office 365 サービスに含まれているですか?](azure-expressroute.md#BKMK_WhatDoIGet)の下。他のすべてのアプリケーションとサービスのネットワーク トラフィックは、インターネット上をスキャンするように続けます。</span><span class="sxs-lookup"><span data-stu-id="1010c-p105">Regardless of whether you have an existing MPLS WAN, ExpressRoute can be added to your network architecture in one of three ways; through a supported cloud exchange co-location provider, an Ethernet point-to-point connection provider, or through an MPLS connection provider. See what [providers are available in your region](https://azure.microsoft.com/documentation/articles/expressroute-locations/). The direct ExpressRoute connection will enable connectivity to the applications outlined in [What Office 365 services are included?](azure-expressroute.md#BKMK_WhatDoIGet) below. Network traffic for all other applications and services will continue to traverse the internet.</span></span>

<span data-ttu-id="1010c-p106">一般的な Office 365 ユーザーが Office 365、Windows の更新プログラム、および TechNet など、Microsoft のすべてのアプリケーションへのアクセスをインターネット経由でマイクロソフトのデータ センターに接続するには次のような高レベルのネットワーク図を検討してください。お客様は、オンプレミスのネットワークから、または個別のインターネット接続から、接続するかどうかに関係なくネットワーク パスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1010c-p106">Consider the following high level network diagram which shows a typical Office 365 customer connecting to Microsoft's datacenters over the internet for access to all Microsoft applications such as Office 365, Windows Update, and TechNet. Customers use a similar network path regardless of whether they're connecting from an on-premises network or from an independent internet connection.</span></span>

![Office 365 のネットワーク接続](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

<span data-ttu-id="1010c-p107">次に、更新された図は、インターネットと ExpressRoute の両方を使用して、Office 365 に接続するのには Office 365 ユーザーを示しています。パブリック DNS、コンテンツ配信ネットワークのノードなどのいくつかの接続は、パブリック インターネット接続をまだ必要とすることを確認します。またお客様のユーザーが接続されている建物は、インターネット経由で接続している、ExpressRoute で配置されていないを確認します。</span><span class="sxs-lookup"><span data-stu-id="1010c-p107">Now look at the updated diagram which depicts an Office 365 customer who uses both the internet and ExpressRoute to connect to Office 365. Notice that some connections such as Public DNS and Content Delivery Network nodes still require the public internet connection. Also notice the customer's users who are not located in their ExpressRoute connected building are connecting over the Internet.</span></span>

![ExpressRoute と office 365 の接続](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

<span data-ttu-id="1010c-p108">詳細についてはしますか。については[Office 365 の Azure ExpressRoute でネットワーク トラフィックを管理](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)する方法について学習し、 [Office 365 の Azure ExpressRoute を構成](https://azure.microsoft.com/documentation/articles/expressroute-faqs/)する方法です。概念をより詳細に説明するためにチャネル 9 の 10 の一部の[Office 365 のトレーニングの Azure ExpressRoute](https://channel9.msdn.com/series/aer)シリーズ記録しました。</span><span class="sxs-lookup"><span data-stu-id="1010c-p108">Still want more information? Learn how to [manage your network traffic with Azure ExpressRoute for Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) and learn how to [configure Azure ExpressRoute for Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). We've also recorded a 10 part [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) series on Channel 9 to help explain the concepts more thoroughly.</span></span>

<span data-ttu-id="1010c-135">([Office 365 の azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="1010c-135">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="what-office-365-services-are-included"></a><span data-ttu-id="1010c-136">Office 365 サービスは、含まれているでしょうか。</span><span class="sxs-lookup"><span data-stu-id="1010c-136">What Office 365 services are included?</span></span>
<span data-ttu-id="1010c-137"><a name="BKMK_WhatDoIGet"> </a></span><span class="sxs-lookup"><span data-stu-id="1010c-137"></span></span>

<span data-ttu-id="1010c-p109">次の表は、ExpressRoute 経由でサポートされている Office 365 のサービスを一覧します。これらのアプリケーションには、どのネットワーク要求は、インターネット接続を必要とするかを理解するのには[Office 365 の端点の資料](https://aka.ms/o365endpoints)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1010c-p109">The following table lists the Office 365 services that are supported over ExpressRoute. Please review the [Office 365 endpoints article](https://aka.ms/o365endpoints) to understand which network requests for these applications require internet connectivity.</span></span>

|<span data-ttu-id="1010c-140">**含まれているアプリケーション**</span><span class="sxs-lookup"><span data-stu-id="1010c-140">**Applications included**</span></span>|
|:-----|
|<span data-ttu-id="1010c-141">Exchange オンライン<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1010c-141">Exchange Online<sup>1</sup></span></span> <br/> <span data-ttu-id="1010c-142">Exchange のオンライン保護<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1010c-142">Exchange Online Protection<sup>1</sup></span></span> <br/> <span data-ttu-id="1010c-143"><sup>1</sup>をを説明します。</span><span class="sxs-lookup"><span data-stu-id="1010c-143">Delve<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="1010c-144">Skype ビジネス オンライン<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1010c-144">Skype for Business Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="1010c-145">SharePoint のオンライン<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1010c-145">SharePoint Online<sup>1</sup></span></span> <br/> <span data-ttu-id="1010c-146">ビジネス<sup>1</sup>の OneDrive</span><span class="sxs-lookup"><span data-stu-id="1010c-146">OneDrive for Business<sup>1</sup></span></span> <br/> <span data-ttu-id="1010c-147">プロジェクト オンライン<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1010c-147">Project Online<sup>1</sup></span></span> <br/> |
|<span data-ttu-id="1010c-148">ポータルと共有<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1010c-148">Portal and shared<sup>1</sup></span></span> <br/> <span data-ttu-id="1010c-149">Azure Active Directory の<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1010c-149">Azure Active Directory<sup>1</sup></span></span> <br/> <span data-ttu-id="1010c-150">AAD<sup>1</sup>をを接続します。</span><span class="sxs-lookup"><span data-stu-id="1010c-150">AAD Connect<sup>1</sup></span></span> <br/> <span data-ttu-id="1010c-151">Office オンライン<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="1010c-151">Office Online<sup>1</sup></span></span> <br/> |

<span data-ttu-id="1010c-152"><sup>1</sup>それぞれのアプリケーションは、ExpressRoute 経由ではサポートされていないインターネット接続の要件がある、詳細については[Office 365 の端点の資料](https://aka.ms/o365endpoints)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1010c-152"><sup>1</sup>Each of these applications have internet connectivity requirements not supported over ExpressRoute, see the [Office 365 endpoints article](https://aka.ms/o365endpoints) for more information.</span></span>

<span data-ttu-id="1010c-153">Office 365 の ExpressRoute に含まれていないサービスは、Office 365 用リソースのクライアントのダウンロード、設置の Id プロバイダーのサインイン、および中国の (21 の Vianet 運用している)、Office 365 のサービスです。</span><span class="sxs-lookup"><span data-stu-id="1010c-153">The services that aren't included with ExpressRoute for Office 365 are Office 365 ProPlus client downloads, On-premises Identity Provider Sign-In, and Office 365 (operated by 21 Vianet) service in China.</span></span>

<span data-ttu-id="1010c-154">([Office 365 の azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="1010c-154">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="implementing-expressroute-for-office-365"></a><span data-ttu-id="1010c-155">Office 365 向け ExpressRoute での実装</span><span class="sxs-lookup"><span data-stu-id="1010c-155">Implementing ExpressRoute for Office 365</span></span>

<span data-ttu-id="1010c-p110">ExpressRoute を実装するネットワークおよびアプリケーションの所有者の関与を必要とし、新しい[ネットワーク ルーティングのアーキテクチャ](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)セキュリティがありますが、帯域幅の要件を決定することを計画するように注意してください、実装、高可用性を実現する必要があります。などなど。ExpressRoute を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1010c-p110">Implementing ExpressRoute requires the involvement of network and application owners and requires careful planning to determine the new [network routing architecture](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), bandwidth requirements, where security will be implemented, high availability, and so on. To implement ExpressRoute, you'll need to:</span></span>

1. <span data-ttu-id="1010c-p111">ExpressRoute は、Office 365 の接続の計画で満たす必要性を完全に理解するには。インターネットや ExpressRoute に使用するどのようなアプリケーションを理解する、セキュリティ、および高可用性が必要なインターネットと ExpressRoute の両方を使用して、Office 365 用のコンテキストではトラフィックのネットワークの容量の計画を綿密に。</span><span class="sxs-lookup"><span data-stu-id="1010c-p111">Fully understand the need ExpressRoute satisfies in your Office 365 connectivity planning. Understand what applications will use the internet or ExpressRoute and fully plan your network capacity, security, and high availability needs in the context of using both the internet and ExpressRoute for Office 365 traffic.</span></span>

2. <span data-ttu-id="1010c-160">出口とインターネットとのトラフィックの ExpressRoute<sup>1</sup>の両方のピアリングの場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="1010c-160">Determine the egress and peering locations for both internet and ExpressRoute traffic<sup>1</sup>.</span></span>

3. <span data-ttu-id="1010c-161">インターネットと ExpressRoute の接続に必要な容量を決定します。</span><span class="sxs-lookup"><span data-stu-id="1010c-161">Determine the capacity required on the internet and ExpressRoute connections.</span></span>

4. <span data-ttu-id="1010c-162">セキュリティおよびその他の標準的な境界コントロール<sup>1</sup>を実装するために計画があります。</span><span class="sxs-lookup"><span data-stu-id="1010c-162">Have a plan in place for implementing security and other standard perimeter controls<sup>1</sup>.</span></span>

5. <span data-ttu-id="1010c-163">ExpressRoute を購読するのには有効な Microsoft Azure アカウントがあります。</span><span class="sxs-lookup"><span data-stu-id="1010c-163">Have a valid Microsoft Azure account to subscribe to ExpressRoute.</span></span>

6. <span data-ttu-id="1010c-p112">接続モデルとの[プロバイダーの承認](https://azure.microsoft.com/documentation/articles/expressroute-locations/)を選択します。注意してください、お客様は、複数の接続モデルを選択できます、または、パートナーのパートナーとする必要はありません、既存のネットワーク プロバイダーの場合と同じにします。</span><span class="sxs-lookup"><span data-stu-id="1010c-p112">Select a connectivity model and an [approved provider](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Keep in mind, customers can select multiple connectivity models or partners and the partner doesn't need to be the same as your existing network provider.</span></span>

7. <span data-ttu-id="1010c-166">ExpressRoute へのトラフィックを送信する前に配置を検証します。</span><span class="sxs-lookup"><span data-stu-id="1010c-166">Validate deployment prior to directing traffic to ExpressRoute.</span></span>

8. <span data-ttu-id="1010c-167">必要に応じて、 [QoS を実装](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d)および地域の拡張を評価します。</span><span class="sxs-lookup"><span data-stu-id="1010c-167">Optionally [implement QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) and evaluate regional expansion.</span></span>

<span data-ttu-id="1010c-p113"><sup>1</sup>パフォーマンスに関する重要な考慮事項です。意思決定ここでは、重要なビジネス用の Skype などのアプリケーションは、遅延を大幅に可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1010c-p113"><sup>1</sup>Important performance considerations. Decisions here can dramatically impact latency which is a critical for applications such as Skype for Business.</span></span>

<span data-ttu-id="1010c-170">その他の参照には、 [ExpressRoute のマニュアル](https://azure.microsoft.com/documentation/articles/expressroute-introduction/)だけでなくさまざまな[ルーティング ガイド](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408)を使用します。</span><span class="sxs-lookup"><span data-stu-id="1010c-170">For additional references, use our [routing guide](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) in addition to the [ExpressRoute documentation](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).</span></span>

<span data-ttu-id="1010c-p114">Office 365 の ExpressRoute を購入するには、1 つまたは複数[のプロバイダーを承認](https://azure.microsoft.com/documentation/articles/expressroute-locations/)に必要な数とサイズの回路、ExpressRoute のプレミアム サブスクリプションの準備を使用する必要があります。Office 365 を購入するライセンスを追加することはありません。</span><span class="sxs-lookup"><span data-stu-id="1010c-p114">To purchase ExpressRoute for Office 365, you'll need to work with one or more [approved providers](https://azure.microsoft.com/documentation/articles/expressroute-locations/) to provision the desired number and size circuits with an ExpressRoute Premium subscription. There are no additional licenses to purchase from Office 365.</span></span>

<span data-ttu-id="1010c-173">戻るを使用することができます短いリンクを以下に示します。[https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span><span class="sxs-lookup"><span data-stu-id="1010c-173">Here's a short link you can use to come back: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)</span></span>

<span data-ttu-id="1010c-174">[Office 365 の ExpressRoute](https://aka.ms/ert)にサインアップできるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="1010c-174">Ready to sign-up for [ExpressRoute for Office 365](https://aka.ms/ert)?</span></span>

<span data-ttu-id="1010c-175">([Office 365 の azure ExpressRoute](azure-expressroute.md#BKMK_HOME))</span><span class="sxs-lookup"><span data-stu-id="1010c-175">([Azure ExpressRoute for Office 365](azure-expressroute.md#BKMK_HOME))</span></span>

## <a name="related-topics"></a><span data-ttu-id="1010c-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="1010c-176">Related Topics</span></span>
<span data-ttu-id="1010c-177"><a name="BKMK_End"> </a></span><span class="sxs-lookup"><span data-stu-id="1010c-177"></span></span>

[<span data-ttu-id="1010c-178">Office 365 へのネットワーク接続</span><span class="sxs-lookup"><span data-stu-id="1010c-178">Network connectivity to Office 365</span></span>](network-connectivity.md)

[<span data-ttu-id="1010c-179">Office 365 向け ExpressRoute の管理</span><span class="sxs-lookup"><span data-stu-id="1010c-179">Managing ExpressRoute for Office 365 connectivity</span></span>](managing-expressroute-for-connectivity.md)

[<span data-ttu-id="1010c-180">Office 365 向け ExpressRoute でのルーティング</span><span class="sxs-lookup"><span data-stu-id="1010c-180">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)

[<span data-ttu-id="1010c-181">Office 365 向け ExpressRoute でのネットワーク計画</span><span class="sxs-lookup"><span data-stu-id="1010c-181">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)

[<span data-ttu-id="1010c-182">Office 365 向け ExpressRoute での実装</span><span class="sxs-lookup"><span data-stu-id="1010c-182">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)

[<span data-ttu-id="1010c-183">ExpressRoute に BGP のコミュニティを使用して Office 365 シナリオ (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="1010c-183">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)

[<span data-ttu-id="1010c-184">メディアの品質とオンライン ビジネスの Skype でのネットワーク接続のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="1010c-184">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[<span data-ttu-id="1010c-185">ベースラインとパフォーマンス履歴を使用した、Office 365 のパフォーマンスのチューニング</span><span class="sxs-lookup"><span data-stu-id="1010c-185">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)

[<span data-ttu-id="1010c-186">Office 365 のパフォーマンスに関するトラブルシューティングの計画</span><span class="sxs-lookup"><span data-stu-id="1010c-186">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)

[<span data-ttu-id="1010c-187">Office 365 の URL と IP アドレス範囲</span><span class="sxs-lookup"><span data-stu-id="1010c-187">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[<span data-ttu-id="1010c-188">Office 365 のネットワークとパフォーマンスの調整</span><span class="sxs-lookup"><span data-stu-id="1010c-188">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
