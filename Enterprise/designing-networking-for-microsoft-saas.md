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
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872268"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="9084a-103">Microsoft SaaS のためのネットワーク デザイン</span><span class="sxs-lookup"><span data-stu-id="9084a-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="9084a-104">**概要:** Office 365、Microsoft Intune、Dynamics 365 を含む Microsoft の SaaS サービスにアクセスするためにネットワークを最適化する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="9084a-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="9084a-105">マイクロソフトの SaaS サービスのネットワークを最適化するには、内部の構成とマイクロソフトの SaaS サービスをさまざまなカテゴリのトラフィックをルーティングするエッジ デバイスが必要です。</span><span class="sxs-lookup"><span data-stu-id="9084a-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="9084a-106">Microsoft SaaS サービスを利用するためのネットワークの準備の手順</span><span class="sxs-lookup"><span data-stu-id="9084a-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="9084a-107">Microsoft SaaS サービス向けにネットワークを最適化するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9084a-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="9084a-108">[Microsoft クラウド接続の一般的な要素](common-elements-of-microsoft-cloud-connectivity.md)の「**Microsoft クラウド サービスを利用するためのネットワークの準備の手順**」セクションを読んでください。</span><span class="sxs-lookup"><span data-stu-id="9084a-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="9084a-109">各オフィスには、インターネットに接続を追加します。</span><span class="sxs-lookup"><span data-stu-id="9084a-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="9084a-110">すべてのインターネット接続を Isp がローカル IP アドレスで DNS サーバーを使用することを確認します。</span><span class="sxs-lookup"><span data-stu-id="9084a-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="9084a-111">ネットワーク hairpins、クラウド ベースのセキュリティ サービスでは、介在する宛先を確認し、可能であればそれを排除します。</span><span class="sxs-lookup"><span data-stu-id="9084a-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="9084a-112">最適化の処理をバイパスし、カテゴリのマイクロソフトの SaaS のトラフィックを許可する、エッジ ・ デバイスを構成します。</span><span class="sxs-lookup"><span data-stu-id="9084a-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="9084a-113">マイクロソフトの SaaS のサービスへのトラフィックを最適化します。</span><span class="sxs-lookup"><span data-stu-id="9084a-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="9084a-114">マイクロソフトの SaaS のトラフィックの次の 3 つに分類されます。</span><span class="sxs-lookup"><span data-stu-id="9084a-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="9084a-115">最適化</span><span class="sxs-lookup"><span data-stu-id="9084a-115">Optimize</span></span>

  <span data-ttu-id="9084a-116">すべてのマイクロソフトの SaaS サービスとマイクロソフトの SaaS の帯域幅、接続、およびデータの量の 75% 以上を表すへの接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="9084a-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="9084a-117">許可</span><span class="sxs-lookup"><span data-stu-id="9084a-117">Allow</span></span>

  <span data-ttu-id="9084a-118">特定への接続に必要なマイクロソフトの SaaS サービスし機能が、ネットワークのパフォーマンスと最適化のカテゴリとしての待機時間に影響はありません。</span><span class="sxs-lookup"><span data-stu-id="9084a-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="9084a-119">既定値</span><span class="sxs-lookup"><span data-stu-id="9084a-119">Default</span></span>

  <span data-ttu-id="9084a-p101">マイクロソフトの SaaS サービスとすべての最適化を必要としない依存関係を表します。通常のインターネット トラフィックのように既定のカテゴリのトラフィックを扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="9084a-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="9084a-122">**図 1: は、マイクロソフトの SaaS のトラフィックをすべてのオフィスの構成を推奨します。**</span><span class="sxs-lookup"><span data-stu-id="9084a-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![図 1: は、マイクロソフトの SaaS のトラフィックをすべてのオフィスの構成を推奨します。](media/Network-Poster/SaaS1.png)

<span data-ttu-id="9084a-124">図 1 は、ブランチ オフィスで、または地域の中心的なものなど、すべてのオフィスの推奨構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="9084a-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="9084a-125">**既定**のカテゴリと全般的なインターネット トラフィックがプロキシ サーバーやその他のインター ネット ベースのセキュリティ リスクに対する保護を提供するエッジ ・ デバイスのあるオフィスにルーティングします。</span><span class="sxs-lookup"><span data-stu-id="9084a-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="9084a-126">カテゴリのトラフィックを**最適化**し、**許可**は、Microsoft ネットワークのフロント エンド プロキシ サーバーやその他のエッジ デバイスをバイパスして、接続しているユーザーが含まれているオフィスに最も近いエッジに直接転送されます。</span><span class="sxs-lookup"><span data-stu-id="9084a-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="9084a-127">ブランチ オフィスでの広域のソフトウェア定義 (SD wan を経由するネットワーク デバイスがトラフィックを分離できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9084a-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="9084a-128">**既定**のカテゴリと全般的なインターネット トラフィックが WAN のバックボーンを介して中央または地域のオフィスに移動します。</span><span class="sxs-lookup"><span data-stu-id="9084a-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="9084a-129">カテゴリのトラフィックを**最適化**し、**許可**は、ローカルのインターネット接続を提供する ISP に移動します。</span><span class="sxs-lookup"><span data-stu-id="9084a-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="9084a-130">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9084a-130">For more information, see:</span></span>
  
- [<span data-ttu-id="9084a-131">ネットワーク接続性の原則</span><span class="sxs-lookup"><span data-stu-id="9084a-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="9084a-132">Office 365 のネットワークと移行の計画</span><span class="sxs-lookup"><span data-stu-id="9084a-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="9084a-133">次の手順</span><span class="sxs-lookup"><span data-stu-id="9084a-133">Next step</span></span>

[<span data-ttu-id="9084a-134">Microsoft Azure PaaS のためのネットワーク デザイン</span><span class="sxs-lookup"><span data-stu-id="9084a-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="9084a-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="9084a-135">See also</span></span>

[<span data-ttu-id="9084a-136">エンタープライズ アーキテクトのための Microsoft クラウド ネットワーク</span><span class="sxs-lookup"><span data-stu-id="9084a-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="9084a-137">Microsoft クラウド IT アーキテクチャのリソース</span><span class="sxs-lookup"><span data-stu-id="9084a-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

