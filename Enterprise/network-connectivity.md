---
title: Office 365 へのネットワーク接続
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/2/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 は、世界中のお客様は、インターネット接続を使用してサービスへの接続を有効にするよう設計されています。サービスの拡大に伴って、セキュリティ、パフォーマンス、および Office 365 の信頼性が向上しましたベース サービスへの接続を確立するためにインターネットを使用しているお客様に。
ms.openlocfilehash: b72b0a4584542e4c8673c7cf009c66aa97c6b81c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541756"
---
# <a name="network-connectivity-to-office-365"></a><span data-ttu-id="e2df6-104">Office 365 へのネットワーク接続</span><span class="sxs-lookup"><span data-stu-id="e2df6-104">Network connectivity to Office 365</span></span>

<span data-ttu-id="e2df6-p102">Office 365 は、世界中のお客様は、インターネット接続を使用してサービスへの接続を有効にするよう設計されています。サービスの拡大に伴って、セキュリティ、パフォーマンス、および Office 365 の信頼性が向上しましたベース サービスへの接続を確立するためにインターネットを使用しているお客様に。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p102">Office 365 is designed to enable customers all over the world to connect to the service using an internet connection. As the service evolves, the security, performance, and reliability of Office 365 are improved based on customers using the internet to establish a connection to the service.</span></span>
  
<span data-ttu-id="e2df6-p103">Office 365 を使用する予定のユーザーは、展開プロジェクトの一部として、既存の予測とインターネットの接続性のニーズを評価する必要があります。エンタープライズ クラスの導入インターネット接続の信頼性が高く、適切なサイズの使用 Office 365 の機能およびシナリオの重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p103">Customers planning to use Office 365 should assess their existing and forecasted internet connectivity needs as a part of the deployment project. For enterprise class deployments reliable and appropriately sized internet connectivity is a critical part of consuming Office 365 features and scenarios.</span></span>
  
<span data-ttu-id="e2df6-p104">多くのさまざまな人々 や組織によっては、サイズと初期設定では、ネットワークの評価を実行できます。評価のネットワーク範囲にしているので、展開プロセスによって異なります。ネットワークを評価するためにかかるを把握するために、ネットワークの評価ガイド」に使用できるオプションを理解するために開発しました。この評価が可能かどうかの手順とリソースを正常に Office 365 を採用することを有効にする配置プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p104">Network evaluations can be performed by many different people and organizations depending on your size and preferences. The network scope of the assessment can also vary depending on where you're at in your deployment process. To help you get a better understanding of what it takes to perform a network assessment, we've produced a network assessment guide to help you understand the options available to you. This assessment will determine what steps and resources need to be added to the deployment project to enable you to successfully adopt Office 365.</span></span>
  
<span data-ttu-id="e2df6-p105">これら所定の宿[Skype の運用フレームワーク](https://www.skypeoperationsframework.com/)のような包括的なネットワークの評価と実装の詳細ネットワーク設計上の課題の解決策の候補が提供されます。[マイナーの構成やデザインの変更](https://aka.ms/manageo365endpoints)、既存のネットワークとインターネットの出口のインフラストラクチャに、Office 365 へのネットワーク接続を確保できるほとんどのネットワークの評価が示されます。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p105">A comprehensive network assessment, like those prescribed inn the [Skype Operations Framework](https://www.skypeoperationsframework.com/) will provide possible solutions to networking design challenges along with implementation details. Most network assessments will indicate network connectivity to Office 365 can be accommodated with [minor configuration or design changes](https://aka.ms/manageo365endpoints) to the existing network and internet egress infrastructure.</span></span>

<span data-ttu-id="e2df6-p106">いくつかの評価には、Office 365 へのネットワーク接続のネットワーク コンポーネントの追加投資が必要になりますが表示されます。たとえば、WAN の帯域幅、または Office 365 へのインターネット接続をサポートするためにルーティング インフラストラクチャの最適化に投資します。場合によっては評価では、[ビジネス オンラインのメディアの品質の Skype](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917)などの場合に、規制やパフォーマンスの要件は、影響を受ける Office 365 へのネットワーク接続が表示されます。これらの要件は、インターネット接続インフラストラクチャ、ルーティングの最適化では、専用のダイレクト接続への投資する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p106">Some assessments will indicate network connectivity to Office 365 will require additional investments in networking components. For example, investments in WAN bandwidth or optimized routing infrastructure to support internet connectivity to Office 365. Occasionally an assessment will indicate network connectivity to Office 365 is influenced by regulation or performance requirements for scenarios such as [Skype for Business Online media quality](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). These additional requirements may lead to investments in internet connectivity infrastructure, routing optimization, and specialized direct connectivity.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e2df6-p107">マイクロソフトでは、Azure ExpressRoute の Microsoft Peering ルーティング ドメインを確認する方法を変更します。2017 年 7 月 31日の開始 Azure ExpressRoute のすべての顧客ができます Microsoft Peering Azure の管理コンソールから直接、または PowerShell を使用しています。Microsoft Peering を有効にすると、すべてのお客様は、Dynamics 365 お客様との契約のアプリケーション (CRM Online と呼ばれていました) の BGP ルートのアドバタイズを受信するルート フィルターを作成できます。Office 365 の Azure ExpressRoute を必要とするお客様は、ルート フィルターを作成するには Office 365 の前に、マイクロソフトからレビューを取得しなければなりません。Office 365 の ExpressRoute を有効にするためのレビューを要求する方法の詳細については、マイクロソフト アカウント チームにお問い合わせください。承認されていないサブスクリプションの Office 365 のルート フィルターを作成しようとして[エラー メッセージ](https://support.microsoft.com/kb/3181709)が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p107">Microsoft changed how the Microsoft Peering routing domain is reviewed for Azure ExpressRoute. Starting July 31st, 2017, all Azure ExpressRoute customers can enable Microsoft Peering directly from the Azure Administrative console or via PowerShell. After enabling Microsoft Peering, any customer can create route filters to receive BGP route advertisements for Dynamics 365 Customer Engagement applications (formerly known as CRM Online). Customers needing Azure ExpressRoute for Office 365 must obtain review from Microsoft before they can create route filters for Office 365. Please contact your Microsoft Account team to learn about how to request a review for enabling Office 365 ExpressRoute. Unauthorized subscriptions trying to create route filters for Office 365 will receive an [error message](https://support.microsoft.com/kb/3181709).</span></span>
  
<span data-ttu-id="e2df6-125">Office 365 は、ネットワークの評価を計画する際に考慮すべき重要なポイント。</span><span class="sxs-lookup"><span data-stu-id="e2df6-125">Key points to consider when planning your network assessment for Office 365:</span></span>
  
- <span data-ttu-id="e2df6-p108">Office 365 は、パブリック インターネット経由で実行されるセキュリティで保護された、信頼性の高い、高パフォーマンスのサービスです。サービスのこれらの側面を強化するために投資していきます。すべての Office 365 サービスは、インターネット接続経由で使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p108">Office 365 is a secure, reliable, high performance service that runs over the public internet. We continue to invest to enhance these aspects of the service. All Office 365 services are available via internet connectivity.</span></span>

- <span data-ttu-id="e2df6-p109">コアの Office 365 の可用性、グローバルなどの側面に達したを最適化する継続的に私たちとインターネットのパフォーマンス ベースの接続性。たとえば、多くの Office 365 サービスは、インターネットへのエッジのノードの一連の拡張を活用します。このネットワークのエッジでは、最高レベルの近接性と、インターネット経由で送信される接続のパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p109">We are continually optimizing core aspects of Office 365 such as availability, global reach, and performance for internet based connectivity. For example, many Office 365 services leverage an expanding set of internet facing edge nodes. This edge network offers the best proximity and performance to connections coming over the internet.</span></span>

- <span data-ttu-id="e2df6-p110">Office 365 を使用して、含まれている Skype などのサービス ビジネス オンラインの音声、ビデオ、または会議の機能のいずれかを検討するときお客様がエンド ツー エンドのネットワークの評価を完了や、Skype の運用フレームワークを使用して要件を満たす必要があります。このようなお客様は、ExpressRoute を含む、クラウドの接続の特定の要件を満たすためにいくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p110">When considering using Office 365 for any of the included services such as Skype for Business Online voice, video, or meeting capabilities, customers must complete an end to end network assessment and meet requirements using our Skype Operations Framework. These customers will have several options to meet specific requirements for cloud connectivity, including ExpressRoute.</span></span>

<span data-ttu-id="e2df6-p111">[Microsoft Office 365 のネットワーク パフォーマンスを最適化する](https://msdn.microsoft.com/en-us/library/mt450488.aspx)マイクロソフトの事例を見てください。Office 365 の評価からしていない場合を確認、ネットワークの評価、またはネットワークの設計を発見する場所の課題をしてください Microsoft アカウント ・ チームとともに作業を克服するための支援をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p111">Have a look at Microsoft's case study [Optimizing network performance for Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). If you're evaluating Office 365 and aren't sure where to begin with your network assessment or have found network design challenges that you need assistance to overcome, please work with your Microsoft account team.</span></span>
  
<span data-ttu-id="e2df6-p112">また、Office 365 のトラフィックを安全に管理し、最高のパフォーマンスを取得するための接続の原理を理解するのには[Office 365 のネットワーク接続性の原則](https://aka.ms/o365networkingprinciples)を参照してください。この資料では Office 365 のネットワーク接続を安全に最適化するため、最新のガイダンスを理解できます。</span><span class="sxs-lookup"><span data-stu-id="e2df6-p112">Also, read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span>
  
<span data-ttu-id="e2df6-138">戻るを使用することができます短いリンクを次のとおりです: [ https://aka.ms/o365networkconnectivity。](https://aka.ms/o365networkconnectivity)</span><span class="sxs-lookup"><span data-stu-id="e2df6-138">Here's a short link you can use to come back: [https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e2df6-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2df6-139">See also</span></span>

[<span data-ttu-id="e2df6-140">Office 365 エンドポイントを管理します。</span><span class="sxs-lookup"><span data-stu-id="e2df6-140">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="e2df6-141">Office 365 エンドポイントに関する FAQ</span><span class="sxs-lookup"><span data-stu-id="e2df6-141">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[<span data-ttu-id="e2df6-142">Office 365 のネットワークとパフォーマンスの調整</span><span class="sxs-lookup"><span data-stu-id="e2df6-142">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)
  
[<span data-ttu-id="e2df6-143">Office 365 向け Azure ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="e2df6-143">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
  
[<span data-ttu-id="e2df6-144">Office 365 向け ExpressRoute でのルーティング</span><span class="sxs-lookup"><span data-stu-id="e2df6-144">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
  
[<span data-ttu-id="e2df6-145">Office 365 向け ExpressRoute でのネットワーク計画</span><span class="sxs-lookup"><span data-stu-id="e2df6-145">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
  
[<span data-ttu-id="e2df6-146">ExpressRoute に BGP のコミュニティを使用して Office 365 シナリオ (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="e2df6-146">Using BGP communities in ExpressRoute for Office 365 scenarios (preview)</span></span>](bgp-communities-in-expressroute.md)
  
[<span data-ttu-id="e2df6-147">メディアの品質とオンライン ビジネスの Skype でのネットワーク接続のパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="e2df6-147">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="e2df6-148">Office 365 の URL と IP アドレス範囲</span><span class="sxs-lookup"><span data-stu-id="e2df6-148">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="e2df6-149">Office 365 ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="e2df6-149">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
