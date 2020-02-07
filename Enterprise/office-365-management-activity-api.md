---
title: Office 365 管理アクティビティ API
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
- M365-analytics
f1.keywords:
- NOCSH
description: Office 365 Management Activity API についての簡単な概要。
ms.openlocfilehash: 97f582aa19a523a8b94a17b13efd6a518b067036
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41842624"
---
# <a name="office-365-management-activity-api"></a><span data-ttu-id="ab532-103">Office 365 管理アクティビティ API</span><span class="sxs-lookup"><span data-stu-id="ab532-103">Office 365 Management Activity API</span></span>

<span data-ttu-id="ab532-104">Microsoft では、Office 365 テナントに関する集計されたトランザクション情報を取得するために使用できるレポートサービスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="ab532-104">Microsoft provides reporting services you can use to obtain aggregated transactional information about your Office 365 tenant.</span></span> <span data-ttu-id="ab532-105">[Office 365 Management ACTIVITY API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview)は、業界標準の RESTful 設計および OAuth v2 を使用して認証を行います。</span><span class="sxs-lookup"><span data-stu-id="ab532-105">The [Office 365 Management Activity API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) uses an industry-standard RESTful design and OAuth v2 for authentication.</span></span> <span data-ttu-id="ab532-106">これにより、データの取得や、視覚エフェクトのツールやアプリケーションへの取り込むを簡単に実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ab532-106">This makes it easy to start experimenting with retrieving data and ingesting it into visualization tools and applications.</span></span> <span data-ttu-id="ab532-107">API は、Office 365 のユーザー、管理者、操作、およびセキュリティアクティビティに関する情報をデータフィードに提供します。</span><span class="sxs-lookup"><span data-stu-id="ab532-107">The API provides a data feed with information about user, administrator, operations, and security activity in Office 365.</span></span> <span data-ttu-id="ab532-108">このデータは、規制目的のため、またはオンプレミスのインフラストラクチャまたは他のソースから調達されたログデータと組み合わせて保持できます。</span><span class="sxs-lookup"><span data-stu-id="ab532-108">The data can be kept for regulatory purposes, or combined with log data procured from an on-premises infrastructure or other sources.</span></span> <span data-ttu-id="ab532-109">これにより、企業全体にわたる運用、セキュリティ、およびコンプライアンスの監視ソリューションを構築できます。</span><span class="sxs-lookup"><span data-stu-id="ab532-109">This helps build a monitoring solution for operations, security, and compliance across the enterprise.</span></span>

<span data-ttu-id="ab532-110">Office 365 管理アクティビティ API は、Office 365 と Azure Active Directory のアクティビティ ログからの、ユーザー、管理者、システム、およびポリシー アクションとポリシー イベントについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ab532-110">The Office 365 Management Activity API provides information about various user, admin, system, and policy actions and events from Office 365 and Azure Active Directory activity logs.</span></span> <span data-ttu-id="ab532-111">この API は、すべてのサービスに共通の10個を超えるフィールドを持つ一貫性のある監査スキーマを提供します。</span><span class="sxs-lookup"><span data-stu-id="ab532-111">The API provides a consistent audit schema with over 10 fields common across all the services.</span></span> <span data-ttu-id="ab532-112">この API を使用すると、組織はイベント間の簡単な接続を確立し、新しい方法でデータを理由にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ab532-112">The API allows organizations to make easy connections between events, and enables new ways to reason over the data.</span></span>

<span data-ttu-id="ab532-113">多数の独立系ソフトウェアベンダー (Isv) が Microsoft と提携しており、API に基づくソリューションを構築しています。</span><span class="sxs-lookup"><span data-stu-id="ab532-113">Dozens of Independent Software Vendors (ISVs) partnered with Microsoft and have built solutions based on the API.</span></span> <span data-ttu-id="ab532-114">一部のソリューションでは、Office 365 データと、複数のクラウドプロバイダーおよびオンプレミスシステムからのソースデータのみに焦点を合わせて、運用、セキュリティ、コンプライアンスに関連するアクティビティの統合されたビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="ab532-114">Some solutions focus solely on Office 365 data and others source data from multiple cloud providers and on-premises systems to create a unified view of operations, security, and compliance-related activity.</span></span> 

<span data-ttu-id="ab532-115">詳細については、「 [Office 365 Management ACTIVITY API リファレンス](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab532-115">For more information, see the [Office 365 Management Activity API reference](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference).</span></span>
