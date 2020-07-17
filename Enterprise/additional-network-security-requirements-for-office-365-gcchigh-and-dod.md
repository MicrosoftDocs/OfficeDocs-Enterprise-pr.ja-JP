---
title: Office 365 GCC High および DoD の追加のネットワークセキュリティ要件
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: '概要: Office 365 GCC High および DoD には、追加のネットワークセキュリティ要件があります。'
hideEdit: true
ms.openlocfilehash: a79204809787391065ac833d9a3872af4cdc1528
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "44371633"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a><span data-ttu-id="a7b47-103">Office 365 GCC High および DOD の追加のネットワークセキュリティ要件</span><span class="sxs-lookup"><span data-stu-id="a7b47-103">Additional network security requirements for Office 365 GCC High and DOD</span></span>

<span data-ttu-id="a7b47-104">*この記事は、Office 365 GCC High、Office 365 DOD、Microsoft 365 GCC 高、および Microsoft 365 DOD に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="a7b47-104">*This article applies to Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High, and Microsoft 365 DOD.*</span></span>

<span data-ttu-id="a7b47-105">Office 365 GCC High および DOD は、米国政府機関とそのサプライヤーおよび請負業者のニーズを満たすために、セキュリティで保護されたクラウド環境です。</span><span class="sxs-lookup"><span data-stu-id="a7b47-105">Office 365 GCC High and DOD are secure cloud environments to meet the needs of the United States Government and its suppliers and contractors.</span></span>  <span data-ttu-id="a7b47-106">これらのクラウド環境には、サービスがアクセスを許可されている外部エンドポイントに対する、追加のネットワーク制限があります。</span><span class="sxs-lookup"><span data-stu-id="a7b47-106">These cloud environments have additional network restrictions on which external endpoints the services are permitted to access.</span></span>

<span data-ttu-id="a7b47-107">フェデレーション id またはハイブリッド共存を計画しているお客様は、既存のオンプレミス展開への受信または送信アクセスを許可するために Microsoft を必要とする場合があります。</span><span class="sxs-lookup"><span data-stu-id="a7b47-107">GCC High and DOD customers planning to use federated identities or hybrid co-existence may require Microsoft to permit inbound and/or outbound access to your existing on-premises deployments.</span></span>  <span data-ttu-id="a7b47-108">これらのアクティビティの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a7b47-108">Examples of these activities include:</span></span>

* <span data-ttu-id="a7b47-109">フェデレーション id の使用 (Active Directory フェデレーションサービスまたは同様にサポートされている STS)</span><span class="sxs-lookup"><span data-stu-id="a7b47-109">Use of federated identities (with Active Directory Federation Services or similar supported STS)</span></span>
* <span data-ttu-id="a7b47-110">オンプレミスの Exchange サーバーまたは Skype for Business 展開とのハイブリッド共存</span><span class="sxs-lookup"><span data-stu-id="a7b47-110">Hybrid coexistence with an on-premises Exchange Server or Skype for Business deployment</span></span>
* <span data-ttu-id="a7b47-111">オンプレミスのシステムからの既存のユーザーコンテンツの移行</span><span class="sxs-lookup"><span data-stu-id="a7b47-111">Migration of existing user content from an on-premises system</span></span>

<span data-ttu-id="a7b47-112">サービスがオンプレミスエンドポイントと通信できるようにするには、ネットワークの変更に備えて Office 365 エンジニアリングに電子メールを送信する**必要があり**ます。</span><span class="sxs-lookup"><span data-stu-id="a7b47-112">To permit the service to communicate with your on-premises endpoints, you **must** send an email to Office 365 engineering for network changes.</span></span>

> [!WARNING]
> <span data-ttu-id="a7b47-113">すべての要求には**3 週間**の SLA があり、必要なセキュリティとコンプライアンスの制御と展開パイプラインがあるため、優先することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7b47-113">All requests have a **three-week** SLA and cannot be expedited due to the required security and compliance controls and deployment pipelines.</span></span>  <span data-ttu-id="a7b47-114">これには、サービスに移行した後の初期のネットワーク要求だけでなく、すべての変更が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a7b47-114">This includes initial onboarding network requests as well as any changes after you have migrated to the service.</span></span>  <span data-ttu-id="a7b47-115">ネットワークチームがこのタイムラインを認識して、計画サイクルに含めるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a7b47-115">Please ensure that your network teams are aware of this timeline and include it in their planning cycles.</span></span>

<span data-ttu-id="a7b47-116">次の情報を使用して、 [Office 365 Government ネットワークホワイトリスト](mailto:o365gwlt@microsoft.com)にメールを送信してください。</span><span class="sxs-lookup"><span data-stu-id="a7b47-116">Please send an email to [Office 365 Government Network Whitelist](mailto:o365gwlt@microsoft.com) with the following information:</span></span>

* <span data-ttu-id="a7b47-117">**To**: [Office 365 Government ネットワークホワイトリスト](mailto:o365gwlt@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="a7b47-117">**To**: [Office 365 Government Network Whitelist](mailto:o365gwlt@microsoft.com)</span></span>
* <span data-ttu-id="a7b47-118">**From**: テナント管理者-送信メールはテナント内の全体管理者の連絡先と一致**する必要があります**</span><span class="sxs-lookup"><span data-stu-id="a7b47-118">**From**: A tenant administrator - the send email **must** match a Global Administrator contact in your tenant</span></span>
* <span data-ttu-id="a7b47-119">**電子メールの件名**: OFFICE 365 GCC High Network Request-contoso.onmicrosoft.us (これをテナント名に置き換えます)</span><span class="sxs-lookup"><span data-stu-id="a7b47-119">**Email subject**: Office 365 GCC High Network Request - contoso.onmicrosoft.us (replace this with your tenant name)</span></span>

<span data-ttu-id="a7b47-120">メッセージの本文には、次のデータを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7b47-120">The body of your message should include the following data:</span></span>

* <span data-ttu-id="a7b47-121">Microsoft Online Services テナント名 (contoso.onmicrosoft.com、fabrikam.onmicrosoft.us)</span><span class="sxs-lookup"><span data-stu-id="a7b47-121">Your Microsoft Online Services tenant name (i.e. contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)</span></span>
* <span data-ttu-id="a7b47-122">ネットワークの変更に関連した、または無効なサブネットのフォローアップのために Microsoft が通信する電子メール配布リスト</span><span class="sxs-lookup"><span data-stu-id="a7b47-122">An email distribution list that Microsoft will communicate with for on-going communications related to network changes and/or follow up for invalid subnets</span></span>
* <span data-ttu-id="a7b47-123">オンプレミスの展開で Microsoft Teams ハイブリッド共存を使用することを計画しているかどうかを示します</span><span class="sxs-lookup"><span data-stu-id="a7b47-123">Indicate whether you plan to use Microsoft Teams hybrid co-existence with your on-premises deployments</span></span>
* <span data-ttu-id="a7b47-124">(たとえば、sts.contoso.com) 外部からアクセス可能な URL (たとえば、10.1.1.0/28) のフェデレーション id システム (たとえば、) および IP アドレス範囲</span><span class="sxs-lookup"><span data-stu-id="a7b47-124">Federated identity system externally accessible URL (e.g. sts.contoso.com) and IP address range in CIDR notation (e.g. 10.1.1.0/28)</span></span>
* <span data-ttu-id="a7b47-125">CIDR 表記でのオンプレミスの PKI 証明書失効リストの URL と IP アドレス範囲</span><span class="sxs-lookup"><span data-stu-id="a7b47-125">On-Premises PKI Certificate Revocation List URL and IP address range in CIDR notation</span></span>
* <span data-ttu-id="a7b47-126">CIDR 表記での Exchange Server オンプレミス展開の外部アクセス可能な URL と IP アドレス範囲</span><span class="sxs-lookup"><span data-stu-id="a7b47-126">Externally accessible URL and IP address range for Exchange Server on-premises deployment in CIDR notation</span></span>
* <span data-ttu-id="a7b47-127">CIDR 表記での、Skype for Business のオンプレミス展開の外部アクセス可能な URL と IP アドレス範囲</span><span class="sxs-lookup"><span data-stu-id="a7b47-127">Externally accessible URL and IP address range for Skype for Business on-premises deployment in CIDR notation</span></span>

<span data-ttu-id="a7b47-128">セキュリティおよびコンプライアンス上の理由から、要求に関する以下の制限事項に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a7b47-128">For security and compliance reasons, please keep in mind the following restrictions on your request:</span></span>

* <span data-ttu-id="a7b47-129">テナントごとに4つのサブネット制限があります。</span><span class="sxs-lookup"><span data-stu-id="a7b47-129">There is a four subnet limitation per tenant</span></span>
* <span data-ttu-id="a7b47-130">サブネットは CIDR 表記 (例: 10.1.1.0/28) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7b47-130">Subnets must be in CIDR Notation (e.g. 10.1.1.0/28)</span></span>
* <span data-ttu-id="a7b47-131">サブネット範囲を/24 より大きくすることはできません</span><span class="sxs-lookup"><span data-stu-id="a7b47-131">Subnet ranges cannot be larger than /24</span></span>
* <span data-ttu-id="a7b47-132">商用のクラウドサービス (市販の Office 365、Google G-Suite、Amazon Web サービスなど) へのアクセスを許可する要求に対応する**ことはできません**。</span><span class="sxs-lookup"><span data-stu-id="a7b47-132">We **cannot** accommodate requests to allow access to commercial cloud services (commercial Office 365, Google G-Suite, Amazon Web Services, etc.)</span></span>

<span data-ttu-id="a7b47-133">要求が Microsoft によって受信され、承認されると、実装に3週間の SLA が発生し、優先度を設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a7b47-133">Once your request has been received and approved by Microsoft, there is a three-week SLA for implementation and cannot be expedited.</span></span>  <span data-ttu-id="a7b47-134">要求を受信した後、最初の受信確認が送信されます。完了した後、最終的な受信確認を受信します。</span><span class="sxs-lookup"><span data-stu-id="a7b47-134">You will receive an initial acknowledgment when we’ve received your request and a final acknowledgement once it has been completed.</span></span>
