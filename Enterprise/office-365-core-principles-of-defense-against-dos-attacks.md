---
title: サービス拒否攻撃に対する Office 365 の防御の中核となる原則
ms.author: robmazz
author: robmazz
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
description: Microsoft は、サービス拒否 (DoS) 攻撃に対する防御において、吸収、検出、軽減の中心となる原則を活用する方法について説明します。
ms.openlocfilehash: abfb0efda679930c22d9ce87709aded9a2880f06
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067623"
---
# <a name="core-principles-of-defense-against-denial-of-service-attacks"></a><span data-ttu-id="aeb04-103">サービス拒否攻撃に対する防御の主要な原則</span><span class="sxs-lookup"><span data-stu-id="aeb04-103">Core Principles of Defense Against Denial-of-Service Attacks</span></span>

<span data-ttu-id="aeb04-104">ネットワークベースの DoS 攻撃に対する防御の3つの主要な原則は、配賦、検出、および軽減です。</span><span class="sxs-lookup"><span data-stu-id="aeb04-104">The three core principles when defending against network-based DoS attacks are Absorption, Detection, and Mitigation.</span></span> <span data-ttu-id="aeb04-105">自動処理は検出の前に発生し、軽減の前に検出が行われます。</span><span class="sxs-lookup"><span data-stu-id="aeb04-105">Absorption happens before detection, and detection happens before mitigation.</span></span> <span data-ttu-id="aeb04-106">配賦は、DoS 攻撃に対して最適な防衛策です。</span><span class="sxs-lookup"><span data-stu-id="aeb04-106">Absorption is the best defense against a DoS attack.</span></span> <span data-ttu-id="aeb04-107">攻撃を検出できない場合は、軽減することはできません。</span><span class="sxs-lookup"><span data-stu-id="aeb04-107">If the attack can't be detected, it can't be mitigated.</span></span> <span data-ttu-id="aeb04-108">しかし、最小の DoS 攻撃を吸収できない場合でも、攻撃を検出するのに十分に長い時間がかかることはありません。</span><span class="sxs-lookup"><span data-stu-id="aeb04-108">But if even the smallest DoS attack can't be absorbed, then services aren't going to survive long enough for the attack to be detected.</span></span>

<span data-ttu-id="aeb04-109">多くの組織では、テクノロジと技術スキルに多大な投資が必要になるため、ほとんどの組織では、過剰なキャパシティを購入して DoS 攻撃を吸収することはできません。</span><span class="sxs-lookup"><span data-stu-id="aeb04-109">It is not economically feasible for most organizations to purchase excess capacity to absorb DoS attacks, as this requires a considerable investment in technology and technical skills.</span></span> <span data-ttu-id="aeb04-110">これにより、Microsoft クラウドサービスを使用する場合のセキュリティ上の利点の1つが強調されています。</span><span class="sxs-lookup"><span data-stu-id="aeb04-110">This highlights one of the security benefits of using Microsoft cloud services.</span></span> <span data-ttu-id="aeb04-111">厳密な Microsoft サービスの規模によって、費用対効果の高い方法でクラウドのお客様に強力なネットワーク保護を提供します。</span><span class="sxs-lookup"><span data-stu-id="aeb04-111">The sheer scale of Microsoft services provides strong network protection to cloud customers in a cost-effective manner.</span></span> <span data-ttu-id="aeb04-112">しかし、大規模な場合でも、吸収、検出、および軽減のバランスを取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeb04-112">But even at a large scale, there must be a balance between absorption, detection, and mitigation.</span></span> <span data-ttu-id="aeb04-113">そのバランスを確認するために、Microsoft は攻撃の増加率を調査して、どの程度 Microsoft が吸収する必要があるかを評価しています。</span><span class="sxs-lookup"><span data-stu-id="aeb04-113">To find that balance, Microsoft studies attack growth rates to estimate how much Microsoft needs to absorb.</span></span>

<span data-ttu-id="aeb04-114">検出は、cat とマウスのゲームです。</span><span class="sxs-lookup"><span data-stu-id="aeb04-114">Detection is a cat-and-mouse game.</span></span> <span data-ttu-id="aeb04-115">ユーザーが攻撃を仕掛ける新しい方法を常に探して、システムを敗北させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeb04-115">You must constantly look for new ways people are attack and try to defeat your systems.</span></span> <span data-ttu-id="aeb04-116">検出-> の緩和-> > の緩和などは、無期限に継続する永続的な状態です。</span><span class="sxs-lookup"><span data-stu-id="aeb04-116">Detect -> Mitigate -> Detect -> Mitigate, etc., is a perpetual, persistent state that continues indefinitely.</span></span>

## <a name="defending-against-dos-attacks"></a><span data-ttu-id="aeb04-117">DoS 攻撃からの防御</span><span class="sxs-lookup"><span data-stu-id="aeb04-117">Defending Against DoS Attacks</span></span>

<span data-ttu-id="aeb04-118">DoS 攻撃に対して適切に防御するには、早期の検出が不可欠です。</span><span class="sxs-lookup"><span data-stu-id="aeb04-118">To successfully defend against a DoS attack, early detection is essential.</span></span> <span data-ttu-id="aeb04-119">システムが過負荷になる前に攻撃を検出することによって、defenders は応答計画を実行できます。</span><span class="sxs-lookup"><span data-stu-id="aeb04-119">By detecting an attack before the system is overwhelmed, defenders can execute a response plan.</span></span>

<span data-ttu-id="aeb04-120">次の式を使用すると、DoS 攻撃の影響に近い時間を見積もることができます。</span><span class="sxs-lookup"><span data-stu-id="aeb04-120">The following formula helps approximate the time to impact of a DoS attack:</span></span>

   <span data-ttu-id="aeb04-121">**最大容量 (バイト/秒)/増加率 (バイト/秒) = 影響時間 (バイト/秒)**</span><span class="sxs-lookup"><span data-stu-id="aeb04-121">**Maximum Capacity (in bytes/sec) / Growth Rate (in bytes/sec) = Time to Impact (in bytes/sec)**</span></span>

<span data-ttu-id="aeb04-122">影響が発生した後に検出時間が経過すると、DoS 攻撃が成功する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="aeb04-122">If the time-to-detection occurs after time-to-impact, it is likely the DoS attack will be successful.</span></span> <span data-ttu-id="aeb04-123">問題が発生するまでの時間が非常に大きくなった場合、攻撃対象のサービスは、軽減戦略が使用されていれば、オンライン状態のままにしてアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="aeb04-123">If the time-to-detection occurs before time-to-impact, the attacked services should remain online and accessible if mitigation strategies are used.</span></span> <span data-ttu-id="aeb04-124">そのため、DoS 攻撃に対して防御するには、次の2つのことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="aeb04-124">Thus, there are only two things that can be done to defend against DoS attacks:</span></span>

- <span data-ttu-id="aeb04-125">最大処理能力の上限を上げるために、処理能力を向上させます (これにより、攻撃を検出するための時間が長くなります)。や</span><span class="sxs-lookup"><span data-stu-id="aeb04-125">Increase capacity to raise the ceiling of maximum capacity (which in turn provides more time to detect an attack); or</span></span>
- <span data-ttu-id="aeb04-126">検出時間を短縮します。</span><span class="sxs-lookup"><span data-stu-id="aeb04-126">Decrease the time to detect.</span></span>

<span data-ttu-id="aeb04-127">キャパシティの増加は、直接の会計に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="aeb04-127">Increasing capacity has a direct fiscal impact.</span></span> <span data-ttu-id="aeb04-128">Microsoft は、少なくとも基本的な吸収処理能力を開発して、ある程度の DoS 攻撃に備えられるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="aeb04-128">Microsoft recommends that customers develop at least basic absorption capacity to ensure that they can survive some level of DoS attack.</span></span> <span data-ttu-id="aeb04-129">実際の吸収処理能力は顧客によって異なりますが、顧客ごとに、公開、リスク、および財務支出に対して独自のしきい値があります。</span><span class="sxs-lookup"><span data-stu-id="aeb04-129">The actual absorption capacity varies from customer to customer, as each customer has their own thresholds for exposure, risk, and financial outlay.</span></span> <span data-ttu-id="aeb04-130">経済的な理由から、検出時間を短縮する方法に関する研究および時間への投資は、通常、最も費用対効果の高い防御です。</span><span class="sxs-lookup"><span data-stu-id="aeb04-130">For economic reasons, investments in research and time for ways to decrease time-to-detection are usually the most cost-effective defense.</span></span>
