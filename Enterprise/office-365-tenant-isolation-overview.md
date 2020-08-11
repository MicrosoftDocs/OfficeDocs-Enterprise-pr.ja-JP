---
title: Microsoft 365 でのテナントの分離
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
description: この記事には、microsoft 365 などのクラウドサービスでのテナントの分離の適用方法の概要が記載されています。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 531b5023af49c776cccfef06dee5bff4b303beff
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606543"
---
# <a name="tenant-isolation-in-microsoft-365"></a><span data-ttu-id="aeafe-103">Microsoft 365 でのテナントの分離</span><span class="sxs-lookup"><span data-stu-id="aeafe-103">Tenant Isolation in Microsoft 365</span></span>

<span data-ttu-id="aeafe-104">クラウドコンピューティングの主な利点の1つは、同時に多数のお客様に共通する共有インフラストラクチャの概念で、スケールの経済につながることです。</span><span class="sxs-lookup"><span data-stu-id="aeafe-104">One of the primary benefits of cloud computing is concept of a shared, common infrastructure across numerous customers simultaneously, leading to economies of scale.</span></span> <span data-ttu-id="aeafe-105">この概念を*マルチテナント*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="aeafe-105">This concept is called *multi-tenancy*.</span></span> <span data-ttu-id="aeafe-106">Microsoft は、クラウド サービスのマルチテナント アーキテクチャによって、エンタープライズレベルのセキュリティ、機密性、プライバシー、完全性、可用性の基準をサポートするため、継続的に取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="aeafe-106">Microsoft works continuously to ensure that the multi-tenant architectures of our cloud services support enterprise-level security, confidentiality, privacy, integrity, and availability standards.</span></span>

<span data-ttu-id="aeafe-107">[信頼できるコンピューティング](https://www.microsoft.com/trust-center)および[セキュリティ開発ライフサイクル](https://www.microsoft.com/securityengineering/sdl/)から得られる重要な投資と経験に基づいて、Microsoft cloud services は、すべてのテナントが他のすべてのテナントに悪影響を与える可能性があることを前提として設計されており、1つのテナントのアクションが別のテナントのセキュリティまたはサービスに影響を与えたり、別のテナントのコンテンツ</span><span class="sxs-lookup"><span data-stu-id="aeafe-107">Based upon the significant investments and experience gathered from [Trustworthy Computing](https://www.microsoft.com/trust-center) and the [Security Development Lifecycle](https://www.microsoft.com/securityengineering/sdl/), Microsoft cloud services were designed with the assumption that all tenants are potentially hostile to all other tenants, and we have implemented security measures to prevent the actions of one tenant from affecting the security or service of another tenant, or accessing the content of another tenant.</span></span>

<span data-ttu-id="aeafe-108">マルチテナント環境でテナントの分離を維持するための主な目標は次の2つです。</span><span class="sxs-lookup"><span data-stu-id="aeafe-108">The two primary goals of maintaining tenant isolation in a multi-tenant environment are:</span></span>

1.    <span data-ttu-id="aeafe-109">テナント間での顧客コンテンツの漏洩、または不正アクセスを防止する。そして</span><span class="sxs-lookup"><span data-stu-id="aeafe-109">Preventing leakage of, or unauthorized access to, customer content across tenants; and</span></span>
2.    <span data-ttu-id="aeafe-110">あるテナントのアクションが別のテナントのサービスに悪影響を及ぼすことを防ぐ</span><span class="sxs-lookup"><span data-stu-id="aeafe-110">Preventing the actions of one tenant from adversely affecting the service for another tenant</span></span>

<span data-ttu-id="aeafe-111">Microsoft 365 には複数の形式の保護が実装されており、お客様が Microsoft 365 のサービスまたはアプリケーションを侵害したり、他のテナントまたは Microsoft 365 システム自体の情報に無許可でアクセスしたりすることを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="aeafe-111">Multiple forms of protection have been implemented throughout Microsoft 365 to prevent customers from compromising Microsoft 365 services or applications or gaining unauthorized access to the information of other tenants or the Microsoft 365 system itself, including:</span></span>

- <span data-ttu-id="aeafe-112">Microsoft 365 サービス用の各テナント内の顧客コンテンツの論理的分離は、Azure Active Directory の承認と役割ベースのアクセス制御によって実現されます。</span><span class="sxs-lookup"><span data-stu-id="aeafe-112">Logical isolation of customer content within each tenant for Microsoft 365 services is achieved through Azure Active Directory authorization and role-based access control.</span></span>
- <span data-ttu-id="aeafe-113">SharePoint Online は、データ分離メカニズムをストレージレベルで提供します。</span><span class="sxs-lookup"><span data-stu-id="aeafe-113">SharePoint Online provides data isolation mechanisms at the storage level.</span></span>
- <span data-ttu-id="aeafe-114">Microsoft は、厳密な物理的なセキュリティ、背景審査、および複数層の暗号化戦略を使用して、顧客のコンテンツの機密性と整合性を保護しています。</span><span class="sxs-lookup"><span data-stu-id="aeafe-114">Microsoft uses rigorous physical security, background screening, and a multi-layered encryption strategy to protect the confidentiality and integrity of customer content.</span></span> <span data-ttu-id="aeafe-115">すべての Microsoft 365 データセンターには、バイオメトリクスアクセスコントロールがあり、ほとんどの場合、物理的なアクセスを得るために palm 印刷が要求されています。</span><span class="sxs-lookup"><span data-stu-id="aeafe-115">All Microsoft 365 datacenters have biometric access controls, with most requiring palm prints to gain physical access.</span></span> <span data-ttu-id="aeafe-116">また、米国のすべての Microsoft の従業員は、雇用プロセスの一環として、標準のバックグラウンドチェックを正常に完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeafe-116">In addition, all U.S.-based Microsoft employees are required to successfully complete a standard background check as part of the hiring process.</span></span> <span data-ttu-id="aeafe-117">Microsoft 365 での管理アクセスに使用されるコントロールの詳細については、「 [microsoft 365 管理アクセス制御](office-365-administrative-access-controls-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeafe-117">For more information on the controls used for administrative access in Microsoft 365, see [Microsoft 365 Administrative Access Controls](office-365-administrative-access-controls-overview.md).</span></span>
- <span data-ttu-id="aeafe-118">Microsoft 365 は、BitLocker、ファイル暗号化、トランスポート層セキュリティ (TLS)、およびインターネットプロトコルセキュリティ (IPsec) を含む、お客様のコンテンツを保存し、送信中で暗号化するサービス側のテクノロジを使用しています。</span><span class="sxs-lookup"><span data-stu-id="aeafe-118">Microsoft 365 uses service-side technologies that encrypt customer content at rest and in transit, including BitLocker, per-file encryption, Transport Layer Security (TLS) and Internet Protocol Security (IPsec).</span></span> <span data-ttu-id="aeafe-119">Microsoft 365 での暗号化の詳細については、「 [microsoft 365 のデータ暗号化テクノロジ](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aeafe-119">For specific details about encryption in Microsoft 365, see [Data Encryption Technologies in Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview).</span></span>

<span data-ttu-id="aeafe-120">これらの保護によって、物理的な分離だけで提供される脅威の保護と軽減対策を提供する、堅牢な論理的分離コントロールが提供されます。</span><span class="sxs-lookup"><span data-stu-id="aeafe-120">Together, the above-listed protections provide robust logical isolation controls that provide threat protection and mitigation equivalent to that provided by physical isolation alone.</span></span>

## <a name="related-links"></a><span data-ttu-id="aeafe-121">関連リンク</span><span class="sxs-lookup"><span data-stu-id="aeafe-121">Related Links</span></span>

- [<span data-ttu-id="aeafe-122">Azure Active Directory での分離とアクセス制御</span><span class="sxs-lookup"><span data-stu-id="aeafe-122">Isolation and Access Control in Azure Active Directory</span></span>](office-365-isolation-in-azure-active-directory.md)
- [<span data-ttu-id="aeafe-123">Office Graph と Delve でのテナントの分離</span><span class="sxs-lookup"><span data-stu-id="aeafe-123">Tenant Isolation in the Office Graph and Delve</span></span>](office-365-isolation-in-graph-and-delve.md)
- [<span data-ttu-id="aeafe-124">Microsoft 365 の検索でのテナントの分離</span><span class="sxs-lookup"><span data-stu-id="aeafe-124">Tenant Isolation in Microsoft 365 Search</span></span>](office-365-isolation-in-office-365-search.md)
- [<span data-ttu-id="aeafe-125">Office 365 でのテナントの分離のビデオ</span><span class="sxs-lookup"><span data-stu-id="aeafe-125">Tenant Isolation in Office 365 Video</span></span>](office-365-isolation-in-office-365-video.md)
- [<span data-ttu-id="aeafe-126">リソースの制限</span><span class="sxs-lookup"><span data-stu-id="aeafe-126">Resource Limits</span></span>](office-365-resource-limits.md)
- [<span data-ttu-id="aeafe-127">テナント境界の監視とテスト</span><span class="sxs-lookup"><span data-stu-id="aeafe-127">Monitoring and Testing Tenant Boundaries</span></span>](office-365-monitoring-and-testing.md)
- [<span data-ttu-id="aeafe-128">Microsoft 365 での分離とアクセス制御</span><span class="sxs-lookup"><span data-stu-id="aeafe-128">Isolation and Access Control in Microsoft 365</span></span>](office-365-isolation-in-office-365.md)
