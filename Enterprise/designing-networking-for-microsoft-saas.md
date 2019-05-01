---
title: Microsoft SaaS のためのネットワーク デザイン
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: '概要: Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487300"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="1347c-103">Microsoft SaaS のためのネットワーク デザイン</span><span class="sxs-lookup"><span data-stu-id="1347c-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="1347c-104">**概要:** Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="1347c-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="1347c-105">Microsoft SaaS サービスに対してネットワークを最適化するには、あらゆるカテゴリのトラフィックを Microsoft SaaS サービスを別のカテゴリのトラフィックをルーティングするために内部デバイスとエッジ デバイスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1347c-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="1347c-106">Microsoft SaaS サービスを利用するためのネットワークの準備の手順</span><span class="sxs-lookup"><span data-stu-id="1347c-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="1347c-107">Microsoft SaaS サービス向けにネットワークを最適化するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1347c-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="1347c-108">[Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。</span><span class="sxs-lookup"><span data-stu-id="1347c-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="1347c-109">各オフィスにインターネット接続を追加します。</span><span class="sxs-lookup"><span data-stu-id="1347c-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="1347c-110">すべてのインターネット接続の isp が、ローカル IP アドレスを持つ DNS サーバーを使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1347c-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="1347c-111">ネットワークヘアピン、クラウドベースのセキュリティサービスなどの中間にある宛先を調べ、可能であれば削除します。</span><span class="sxs-lookup"><span data-stu-id="1347c-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="1347c-112">Microsoft SaaS トラフィックの最適化と許可のカテゴリの処理をバイパスするようにエッジデバイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="1347c-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="1347c-113">Microsoft の SaaS サービスへのトラフィックを最適化する</span><span class="sxs-lookup"><span data-stu-id="1347c-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="1347c-114">Microsoft SaaS トラフィックには、次の3つのカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="1347c-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="1347c-115">最適化</span><span class="sxs-lookup"><span data-stu-id="1347c-115">Optimize</span></span>

  <span data-ttu-id="1347c-116">すべての microsoft saas サービスに接続するために必要です。また、microsoft saas の帯域幅、接続、およびデータ量の 75% を表しています。</span><span class="sxs-lookup"><span data-stu-id="1347c-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="1347c-117">許可</span><span class="sxs-lookup"><span data-stu-id="1347c-117">Allow</span></span>

  <span data-ttu-id="1347c-118">特定の Microsoft SaaS サービスおよび機能への接続に必須ですが、ネットワークパフォーマンスや待機時間は、最適化カテゴリの場合と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="1347c-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="1347c-119">既定</span><span class="sxs-lookup"><span data-stu-id="1347c-119">Default</span></span>

  <span data-ttu-id="1347c-120">Microsoft SaaS サービスと、最適化を必要としない依存関係を表します。</span><span class="sxs-lookup"><span data-stu-id="1347c-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="1347c-121">既定のカテゴリトラフィックを通常のインターネットトラフィックと同じように扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="1347c-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="1347c-122">**図 1: すべてのオフィスの Microsoft SaaS トラフィックに推奨される構成**</span><span class="sxs-lookup"><span data-stu-id="1347c-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![図 1: すべてのオフィスの Microsoft SaaS トラフィックに推奨される構成](media/Network-Poster/SaaS1.png)

<span data-ttu-id="1347c-124">図1は、ブランチオフィス、地域または中央1つを含むすべてのオフィスに推奨される構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="1347c-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="1347c-125">**既定**のカテゴリと一般的なインターネットトラフィックは、プロキシサーバーやその他のエッジデバイスを使用してインターネットベースのセキュリティリスクに対する保護を提供するオフィスにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="1347c-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="1347c-126">[**最適化**と**許可**] カテゴリトラフィックは、接続しているユーザーが含まれている office に最も近い Microsoft ネットワークフロントエンドの端に直接転送されます。プロキシサーバーやその他のエッジデバイスは使用しません。</span><span class="sxs-lookup"><span data-stu-id="1347c-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="1347c-127">ブランチオフィスのソフトウェア定義ワイドエリアネットワーク (SD) デバイスは、トラフィックを分離して、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="1347c-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="1347c-128">**既定**のカテゴリと一般的なインターネットトラフィックは、WAN バックボーン上の中央または地域のオフィスに送られます。</span><span class="sxs-lookup"><span data-stu-id="1347c-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="1347c-129">カテゴリトラフィックの**最適化**と**許可**は、ローカルインターネット接続を提供する ISP に送られます。</span><span class="sxs-lookup"><span data-stu-id="1347c-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="1347c-130">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1347c-130">For more information, see:</span></span>
  
- [<span data-ttu-id="1347c-131">ネットワーク接続の原則</span><span class="sxs-lookup"><span data-stu-id="1347c-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="1347c-132">Office 365 のネットワークと移行の計画</span><span class="sxs-lookup"><span data-stu-id="1347c-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="1347c-133">次の手順</span><span class="sxs-lookup"><span data-stu-id="1347c-133">Next step</span></span>

[<span data-ttu-id="1347c-134">Microsoft Azure PaaS のためのネットワーク デザイン</span><span class="sxs-lookup"><span data-stu-id="1347c-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="1347c-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="1347c-135">See also</span></span>

[<span data-ttu-id="1347c-136">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="1347c-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="1347c-137">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="1347c-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

