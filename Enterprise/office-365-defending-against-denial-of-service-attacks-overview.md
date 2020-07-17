---
title: Microsoft 365 でのサービス拒否攻撃に対する防御
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: サービス拒否 (DoS) 攻撃の概要。
ms.openlocfilehash: 2cbe5eb86402fd7b7888f39440a58935604c90eb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998421"
---
# <a name="defend-against-denial-of-service-attacks-in-microsoft-365"></a><span data-ttu-id="719cd-103">Microsoft 365 でのサービス拒否攻撃に対する防御</span><span class="sxs-lookup"><span data-stu-id="719cd-103">Defend Against Denial-of-Service Attacks in Microsoft 365</span></span>

## <a name="introduction"></a><span data-ttu-id="719cd-104">概要</span><span class="sxs-lookup"><span data-stu-id="719cd-104">Introduction</span></span>

<span data-ttu-id="719cd-105">Microsoft は、100を超えるデータセンターのグローバルクラウドインフラストラクチャでホストされている200を超えるクラウドサービスのための信頼できるインフラストラクチャを提供しています。</span><span class="sxs-lookup"><span data-stu-id="719cd-105">Microsoft delivers a trustworthy infrastructure for more than 200 cloud services hosted in a global cloud infrastructure of more than 100 datacenters.</span></span> <span data-ttu-id="719cd-106">これには次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="719cd-106">These include:</span></span>

- <span data-ttu-id="719cd-107">Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="719cd-107">Microsoft Azure</span></span>
- <span data-ttu-id="719cd-108">Microsoft Bing</span><span class="sxs-lookup"><span data-stu-id="719cd-108">Microsoft Bing</span></span>
- <span data-ttu-id="719cd-109">Microsoft Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="719cd-109">Microsoft Dynamics 365</span></span>
- <span data-ttu-id="719cd-110">Microsoft 365 および Office 365</span><span class="sxs-lookup"><span data-stu-id="719cd-110">Microsoft 365 and Office 365</span></span>
- <span data-ttu-id="719cd-111">Microsoft OneDrive</span><span class="sxs-lookup"><span data-stu-id="719cd-111">Microsoft OneDrive</span></span>
- <span data-ttu-id="719cd-112">Skype</span><span class="sxs-lookup"><span data-stu-id="719cd-112">Skype</span></span>
- <span data-ttu-id="719cd-113">Xbox Live</span><span class="sxs-lookup"><span data-stu-id="719cd-113">Xbox Live</span></span>

<span data-ttu-id="719cd-114">大規模なインターネットプレゼンスがあり、クラウドサービスを提供する多くの主要なインターネットプロパティを持つグローバル組織の場合、Microsoft はハッカーやその他の悪意のある個人にとって大きな共通の標的となります。</span><span class="sxs-lookup"><span data-stu-id="719cd-114">As a global organization with a significant Internet presence and many prominent Internet properties that provide cloud services, Microsoft is a large, common target for hackers and other malicious individuals.</span></span> <span data-ttu-id="719cd-115">クライアントと Microsoft クラウドとの間のネットワーク通信層は、悪意のある攻撃の最大目標の1つです。</span><span class="sxs-lookup"><span data-stu-id="719cd-115">The network communication layer between clients and the Microsoft Cloud is one of the biggest targets of malicious attacks.</span></span> <span data-ttu-id="719cd-116">実際、Microsoft は何らかの形式のネットワークベースの cyberattack で継続的かつ永続的に実行されています。</span><span class="sxs-lookup"><span data-stu-id="719cd-116">In fact, Microsoft is continuously and persistently under some form of network-based cyberattack.</span></span> <span data-ttu-id="719cd-117">これを使用すると、Microsoft は多層防御セキュリティ原則を使用して、クラウドサービスとネットワークを保護します。</span><span class="sxs-lookup"><span data-stu-id="719cd-117">In line with this, Microsoft uses defense-in-depth security principles to protect its cloud services and networks.</span></span> <span data-ttu-id="719cd-118">このような攻撃から防御する信頼性の高い永続的なリスク軽減システムがない場合は、Microsoft のクラウドサービスがオフラインになり、お客様が利用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="719cd-118">Without reliable and persistent mitigation systems that defend against these attacks, Microsoft's cloud services would be offline and unavailable to customers.</span></span>

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a><span data-ttu-id="719cd-119">サービス拒否攻撃の定義と現象</span><span class="sxs-lookup"><span data-stu-id="719cd-119">Definition and Symptoms of Denial-of-Service Attacks</span></span>

<span data-ttu-id="719cd-120">ネットワークサービスを攻撃する方法の1つは、サービスホストに対して多数の要求を作成して、ネットワークとサーバーが正規ユーザーからのサービスを拒否できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="719cd-120">One way to attack network services is to create many requests against service hosts to overwhelm the network and servers to deny service to legitimate users.</span></span> <span data-ttu-id="719cd-121">これは、サービス拒否 (DoS) 攻撃と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="719cd-121">This is referred to as a denial-of-service (DoS) attack.</span></span> <span data-ttu-id="719cd-122">複数のアクター、エンドポイント、またはベクトルによって攻撃が実行されると、その攻撃は分散型サービス拒否 (DDoS) 攻撃と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="719cd-122">When the attack is performed by multiple actors, endpoints, and/or vectors, it is referred to as a distributed denial-of-service (DDoS) attack.</span></span> <span data-ttu-id="719cd-123">手段、motives、およびターゲットは異なりますが、DoS および DDoS 攻撃は、インターネットサイトまたはサービスが、一時的または無限に機能しないようにするための取り組みとなります。</span><span class="sxs-lookup"><span data-stu-id="719cd-123">Although the means, motives, and targets vary, DoS and DDoS attacks generally consist of efforts to prevent an Internet site or service from functioning correctly or at all, either temporarily or indefinitely.</span></span>

<span data-ttu-id="719cd-124">[米国のコンピュータエマージェンシーレディネスチーム](https://www.us-cert.gov/)(米国-CERT) は、次のものを含む DoS 攻撃の兆候を定義します。</span><span class="sxs-lookup"><span data-stu-id="719cd-124">The [United States Computer Emergency Readiness Team](https://www.us-cert.gov/) (US-CERT) defines symptoms of DoS attacks to include:</span></span>

- <span data-ttu-id="719cd-125">ネットワークのパフォーマンスが異常に遅くなる (ファイルを開くとき、またはインターネットサイトにアクセスするとき)</span><span class="sxs-lookup"><span data-stu-id="719cd-125">Unusually slow network performance (when opening files or accessing Internet sites)</span></span>
- <span data-ttu-id="719cd-126">Web サイトの利用不可</span><span class="sxs-lookup"><span data-stu-id="719cd-126">Unavailability of a Web site</span></span>
- <span data-ttu-id="719cd-127">Web サイトへのアクセス不可</span><span class="sxs-lookup"><span data-stu-id="719cd-127">Inability to access a Web site</span></span>
- <span data-ttu-id="719cd-128">受信したスパムが飛躍的に増加する</span><span class="sxs-lookup"><span data-stu-id="719cd-128">Dramatic increase in received spam</span></span>
- <span data-ttu-id="719cd-129">ワイヤレスまたは有線のインターネット接続の切断</span><span class="sxs-lookup"><span data-stu-id="719cd-129">Disconnection of a wireless or wired Internet connection</span></span>
- <span data-ttu-id="719cd-130">Web またはインターネットサービスへのアクセスが長期間失われる</span><span class="sxs-lookup"><span data-stu-id="719cd-130">Long-term loss of access to the Web or any Internet services</span></span>

## <a name="related-topics"></a><span data-ttu-id="719cd-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="719cd-131">Related Topics</span></span>

- [<span data-ttu-id="719cd-132">サービス拒否攻撃に対する防御の主要な原則</span><span class="sxs-lookup"><span data-stu-id="719cd-132">Core Principles of Defense Against Denial-of-Service Attacks</span></span>](office-365-core-principles-of-defense-against-dos-attacks.md)
- [<span data-ttu-id="719cd-133">Microsoft のサービス拒否防御戦略</span><span class="sxs-lookup"><span data-stu-id="719cd-133">Microsoft's Denial-of-Service Defense Strategy</span></span>](office-365-microsoft-dos-defense-strategy.md)
- [<span data-ttu-id="719cd-134">サービス拒否攻撃に対する Microsoft クラウドサービスの防御</span><span class="sxs-lookup"><span data-stu-id="719cd-134">Defending Microsoft Cloud Services Against Denial-of-Service Attacks</span></span>](office-365-defending-cloud-services-against-dos-attacks.md)
