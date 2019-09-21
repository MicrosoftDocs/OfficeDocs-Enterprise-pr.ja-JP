---
title: Office 365 での分離コントロール
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
description: '概要: Office 365 内の分離コントロールについて説明します。'
ms.openlocfilehash: 87317d753198b50ce360640c94f042adf27ed06e
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067592"
---
# <a name="office-365-isolation-controls"></a><span data-ttu-id="d7cd1-103">Office 365 での分離コントロール</span><span class="sxs-lookup"><span data-stu-id="d7cd1-103">Office 365 Isolation Controls</span></span> 

<span data-ttu-id="d7cd1-104">Microsoft は、Office 365 のマルチテナントアーキテクチャが、エンタープライズレベルのセキュリティ、機密性、プライバシー、整合性、ローカル、国際、および可用性の[標準](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)をサポートしていることを継続的に実現しています。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-104">Microsoft continuously works to ensure that the multi-tenant architecture of Office 365 supports enterprise-level security, confidentiality, privacy, integrity, local, international, and availability [standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).</span></span> <span data-ttu-id="d7cd1-105">Microsoft によって提供されるサービスの規模と範囲によって、Office 365 を多大な人的介入で管理することが困難で、経済的ではありません。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-105">The scale and the scope of services provided by Microsoft make it difficult and non-economical to manage Office 365 with significant human interaction.</span></span> <span data-ttu-id="d7cd1-106">Office 365 サービスは、グローバルに分散された複数のデータセンターを通じて提供され、それぞれ、ユーザーの介入を必要とする操作やお客様のコンテンツへのアクセスを必要とする操作の数が多くなります。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-106">Office 365 services are provided through multiple globally distributed data centers, each highly automated with few operations requiring a human touch or any access to customer content.</span></span> <span data-ttu-id="d7cd1-107">マイクロソフトのスタッフは、自動化ツールおよび高度なセキュリティで保護されたリモートアクセスを使用して、これらのサービスとデータセンターをサポートします。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-107">Our staff supports these services and data centers using automated tools and highly secure remote access.</span></span> <span data-ttu-id="d7cd1-108">大規模サービスが Office 365 でどのように動作するかに関する詳細については、「 [office 365 FOR IT 担当者向けの背景](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-108">For some of the details about how large-scale services are operated in Office 365, see [a behind the scenes look at Office 365 for IT Pros](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202).</span></span>

<span data-ttu-id="d7cd1-109">Office 365 は、重要なビジネス機能を提供し、Office 365 環境全体に貢献する複数のサービスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-109">Office 365 is composed of multiple services that provide important business functionality and contribute to the entire Office 365 experience.</span></span> <span data-ttu-id="d7cd1-110">これらのサービスはそれぞれ独立しており、互いに統合されるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-110">Each of these services is self-contained and designed to integrate with one another.</span></span>

<span data-ttu-id="d7cd1-111">Office 365 は、次の原則に従って設計されています。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-111">Office 365 is designed with the following principles:</span></span>

 - <span data-ttu-id="d7cd1-112">**[サービス指向アーキテクチャ](https://msdn.microsoft.com/library/aa480021.aspx):** 適切に定義されたビジネス機能を提供する、相互運用可能なサービスという形でソフトウェアを設計し、開発します。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-112">**[Service-Oriented Architecture](https://msdn.microsoft.com/library/aa480021.aspx):** designing and developing software in the form of interoperable services providing well-defined business functionality.</span></span>
 - <span data-ttu-id="d7cd1-113">**[運用セキュリティ保証](http://www.microsoft.com/download/details.aspx?id=40872):** Microsoft の[セキュリティ開発ライフサイクル](https://www.microsoft.com/sdl/default.aspx)を含む、microsoft に固有のさまざまな機能によって得られた知識を組み込むフレームワーク。 [microsoft のセキュリティ応答センター](https://technet.microsoft.com/library/dn440717.aspx)、および cybersecurity の脅威の状況を深く認識します。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-113">**[Operational Security Assurance](http://www.microsoft.com/download/details.aspx?id=40872):** a framework that incorporates the knowledge gained through various capabilities that are unique to Microsoft, including the Microsoft [Security Development Lifecycle](https://www.microsoft.com/sdl/default.aspx), the [Microsoft Security Response Center](https://technet.microsoft.com/library/dn440717.aspx), and deep awareness of the cybersecurity threat landscape.</span></span>

<span data-ttu-id="d7cd1-114">Office 365 サービス間で相互運用されていますが、相互に依存しない独立したサービスとして展開および運用できるように設計および実装されています。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-114">Office 365 services inter-operate with each other, but are designed and implemented so they can be deployed and operated as autonomous services, independent of each other.</span></span> <span data-ttu-id="d7cd1-115">Microsoft segregates の職務および Office 365 の責任範囲によって、組織の資産の改ざんまたは誤用の可能性を低減します。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-115">Microsoft segregates duties and areas of responsibility for Office 365 to reduce opportunities for unauthorized or unintentional modification or misuse of the organization's assets.</span></span> <span data-ttu-id="d7cd1-116">Office 365 teams は、役割ベースの総合的なアクセス制御メカニズムの一部として役割を定義しています。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-116">Office 365 teams have defined roles as part of a comprehensive role-based access control mechanism.</span></span>

## <a name="customer-content-isolation"></a><span data-ttu-id="d7cd1-117">顧客コンテンツの分離</span><span class="sxs-lookup"><span data-stu-id="d7cd1-117">Customer content isolation</span></span>

<span data-ttu-id="d7cd1-118">テナント内のすべてのお客様のコンテンツは、他のテナントから分離されています。また、Office 365 の管理で使用されている運用およびシステムデータから分離されています。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-118">All customer content in a tenant is isolated from other tenants and from operations and systems data used in the management of Office 365.</span></span> <span data-ttu-id="d7cd1-119">Office 365 には複数の形式の保護が実装されており、Office 365 サービスまたはアプリケーションの侵害のリスクを最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-119">Multiple forms of protection are implemented throughout Office 365 to minimize the risk of compromise of any Office 365 service or application.</span></span> <span data-ttu-id="d7cd1-120">複数の形式の保護では、テナントまたは Office 365 システム自体の情報に対する権限のないアクセスも防止できます。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-120">Multiple forms of protection also prevent unauthorized access to the information of tenants or the Office 365 system itself.</span></span>

<span data-ttu-id="d7cd1-121">Microsoft が Office 365 内のテナントデータの論理的分離を実装する方法については、「 [office 365 のテナント分離](office-365-tenant-isolation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7cd1-121">For information about how Microsoft implements logical isolation of tenant data within Office 365, see [Tenant Isolation in Office 365](office-365-tenant-isolation-overview.md).</span></span>
