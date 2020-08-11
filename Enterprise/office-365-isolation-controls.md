---
title: Microsoft 365 分離コントロール
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
description: Microsoft 365 で分離コントロールが動作する方法について説明します。これにより、必要に応じてサービス間での相互運用を行うことができます。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: da49d19371c0b7f704bf7cb1c4c83205b9cc9cb0
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605619"
---
# <a name="microsoft-365-isolation-controls"></a><span data-ttu-id="49c5a-103">Microsoft 365 分離コントロール</span><span class="sxs-lookup"><span data-stu-id="49c5a-103">Microsoft 365 isolation controls</span></span> 

<span data-ttu-id="49c5a-104">Microsoft 365 のマルチテナントアーキテクチャが、エンタープライズレベルのセキュリティ、機密性、プライバシー、整合性、ローカル、国際、および可用性の[標準](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)をサポートしていることを確認するために、継続的に作業を行います。</span><span class="sxs-lookup"><span data-stu-id="49c5a-104">Microsoft continuously works to ensure that the multi-tenant architecture of Microsoft 365 supports enterprise-level security, confidentiality, privacy, integrity, local, international, and availability [standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).</span></span> <span data-ttu-id="49c5a-105">Microsoft によって提供されるサービスの規模と範囲によって、Microsoft 365 を多大な人的介入で管理することは困難で、経済的ではありません。</span><span class="sxs-lookup"><span data-stu-id="49c5a-105">The scale and the scope of services provided by Microsoft make it difficult and non-economical to manage Microsoft 365 with significant human interaction.</span></span> <span data-ttu-id="49c5a-106">Microsoft 365 サービスは、グローバルに分散された複数のデータセンターを介して提供され、それぞれ、ユーザーの介入を必要とする操作やお客様のコンテンツへのアクセスを必要とする運用の数が多くなります。</span><span class="sxs-lookup"><span data-stu-id="49c5a-106">Microsoft 365 services are provided through multiple globally distributed data centers, each highly automated with few operations requiring a human touch or any access to customer content.</span></span> <span data-ttu-id="49c5a-107">マイクロソフトのスタッフは、自動化ツールおよび高度なセキュリティで保護されたリモートアクセスを使用して、これらのサービスとデータセンターをサポートします。</span><span class="sxs-lookup"><span data-stu-id="49c5a-107">Our staff supports these services and data centers using automated tools and highly secure remote access.</span></span> 

<span data-ttu-id="49c5a-108">Microsoft 365 は、重要なビジネス機能を提供し、Microsoft の365環境全体に貢献する複数のサービスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="49c5a-108">Microsoft 365 is composed of multiple services that provide important business functionality and contribute to the entire Microsoft 365 experience.</span></span> <span data-ttu-id="49c5a-109">これらのサービスはそれぞれ独立しており、互いに統合されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="49c5a-109">Each of these services is self-contained and designed to integrate with one another.</span></span>

<span data-ttu-id="49c5a-110">Microsoft 365 は、次の原則を使用して設計されています。</span><span class="sxs-lookup"><span data-stu-id="49c5a-110">Microsoft 365 is designed with the following principles:</span></span>

 - <span data-ttu-id="49c5a-111">**[サービス指向アーキテクチャ](https://docs.microsoft.com/previous-versions/aa480021(v=msdn.10)):** 適切に定義されたビジネス機能を提供する、相互運用可能なサービスという形でソフトウェアを設計し、開発します。</span><span class="sxs-lookup"><span data-stu-id="49c5a-111">**[Service-Oriented Architecture](https://docs.microsoft.com/previous-versions/aa480021(v=msdn.10)):** designing and developing software in the form of interoperable services providing well-defined business functionality.</span></span>
 - <span data-ttu-id="49c5a-112">**運用時の[セキュリティ保証](https://www.microsoft.com/download/details.aspx?id=40872):** Microsoft の[セキュリティ開発ライフサイクル](https://www.microsoft.com/sdl/default.aspx)、 [microsoft セキュリティレスポンスセンター](https://technet.microsoft.com/library/dn440717.aspx)、cybersecurity の脅威に対する深い認識など、microsoft に固有のさまざまな機能によって得られた知識を組み込むフレームワーク。</span><span class="sxs-lookup"><span data-stu-id="49c5a-112">**[Operational Security Assurance](https://www.microsoft.com/download/details.aspx?id=40872):** a framework that incorporates the knowledge gained through various capabilities that are unique to Microsoft, including the Microsoft [Security Development Lifecycle](https://www.microsoft.com/sdl/default.aspx), the [Microsoft Security Response Center](https://technet.microsoft.com/library/dn440717.aspx), and deep awareness of the cybersecurity threat landscape.</span></span>

<span data-ttu-id="49c5a-113">Microsoft 365 サービスは相互に連携していますが、相互に依存しない独立したサービスとして展開および運用できるように設計および実装されています。</span><span class="sxs-lookup"><span data-stu-id="49c5a-113">Microsoft 365 services inter-operate with each other, but are designed and implemented so they can be deployed and operated as autonomous services, independent of each other.</span></span> <span data-ttu-id="49c5a-114">Microsoft segregates の職務および Microsoft 365 の責任範囲。組織の資産の改ざんまたは誤用の可能性を低減します。</span><span class="sxs-lookup"><span data-stu-id="49c5a-114">Microsoft segregates duties and areas of responsibility for Microsoft 365 to reduce opportunities for unauthorized or unintentional modification or misuse of the organization's assets.</span></span> <span data-ttu-id="49c5a-115">Microsoft 365 teams では、役割ベースの総合的なアクセス制御メカニズムの一部として役割が定義されています。</span><span class="sxs-lookup"><span data-stu-id="49c5a-115">Microsoft 365 teams have defined roles as part of a comprehensive role-based access control mechanism.</span></span>

## <a name="customer-content-isolation"></a><span data-ttu-id="49c5a-116">顧客コンテンツの分離</span><span class="sxs-lookup"><span data-stu-id="49c5a-116">Customer content isolation</span></span>

<span data-ttu-id="49c5a-117">テナント内のすべてのお客様のコンテンツは、他のテナントから分離されています。また、Microsoft 365 の管理で使用されている運用およびシステムデータからは分離されています</span><span class="sxs-lookup"><span data-stu-id="49c5a-117">All customer content in a tenant is isolated from other tenants and from operations and systems data used in the management of Microsoft 365.</span></span> <span data-ttu-id="49c5a-118">Microsoft 365 には複数の保護形態が実装されており、Microsoft 365 のサービスやアプリケーションが侵害される危険を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="49c5a-118">Multiple forms of protection are implemented throughout Microsoft 365 to minimize the risk of compromise of any Microsoft 365 service or application.</span></span> <span data-ttu-id="49c5a-119">複数の形式の保護では、テナントまたは Microsoft 365 システム自体の情報に対する権限のないアクセスも防止できます。</span><span class="sxs-lookup"><span data-stu-id="49c5a-119">Multiple forms of protection also prevent unauthorized access to the information of tenants or the Microsoft 365 system itself.</span></span>

<span data-ttu-id="49c5a-120">Microsoft 365 内のテナントデータの論理的分離を実装する方法については、「 [microsoft 365 のテナント分離](office-365-tenant-isolation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49c5a-120">For information about how Microsoft implements logical isolation of tenant data within Microsoft 365, see [Tenant Isolation in Microsoft 365](office-365-tenant-isolation-overview.md).</span></span>
