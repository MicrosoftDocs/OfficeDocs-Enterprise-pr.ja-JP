---
title: Microsoft 365 の監視および監査アクセス制御
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
description: '概要: Microsoft 365 で利用可能なさまざまな監視および監査アクセス制御の概要について説明します。'
ms.openlocfilehash: aba1a9966cf50735ba3348fe126d7b4c9233b4b2
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774872"
---
# <a name="monitoring-and-auditing-access-controls-in-microsoft-365"></a><span data-ttu-id="88e9e-103">Microsoft 365 でのアクセス制御の監視と監査</span><span class="sxs-lookup"><span data-stu-id="88e9e-103">Monitoring and Auditing Access Controls in Microsoft 365</span></span>

<span data-ttu-id="88e9e-104">Microsoft では、Microsoft 365 内で発生するすべての委任、特権、および操作の広範な監視と監査を行います。</span><span class="sxs-lookup"><span data-stu-id="88e9e-104">Microsoft performs extensive monitoring and auditing of all delegation, privileges, and operations that occur within Microsoft 365.</span></span> <span data-ttu-id="88e9e-105">Microsoft 365 のアクセス制御は、最小限の特権の原則に基づいて構築された自動化されたプロセスであり、データアクセス制御と監査を組み込んでいます。</span><span class="sxs-lookup"><span data-stu-id="88e9e-105">Microsoft 365 access control is an automated process built on the principle of least privilege and incorporating data access controls and audits:</span></span>

- <span data-ttu-id="88e9e-106">許可されたすべてのアクセスは、一意のユーザーに追跡できます。</span><span class="sxs-lookup"><span data-stu-id="88e9e-106">All permitted access is traceable to a unique user.</span></span> <span data-ttu-id="88e9e-107">管理者はお客様のコンテンツを取り扱う責任があります。</span><span class="sxs-lookup"><span data-stu-id="88e9e-107">Administrators are accountable for their handling of customer content.</span></span>
- <span data-ttu-id="88e9e-108">アクセス制御の要求、承認、および管理操作ログは、セキュリティおよび悪意のあるイベントを分析するためにキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="88e9e-108">Access control requests, approvals, and administrative operations logs are captured for analysis of security and malicious events.</span></span>
- <span data-ttu-id="88e9e-109">アクセスレベルは、セキュリティグループのメンバーシップに基づいてほぼリアルタイムで確認されており、ビジネスの正当な妥当性を持つユーザーのみがシステムにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="88e9e-109">Access levels are reviewed in near real-time based on security group membership to ensure that only users who have authorized business justifications and meet the eligibility requirements have access to the systems.</span></span>
- <span data-ttu-id="88e9e-110">Microsoft 365、そのアクセス制御、および Azure Active Directory と物理データセンターを含むサポートサービスは、 [ISO/IEC 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001)、 [iso/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018)、 [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC)、 [fedramp](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)、その他の[標準](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)に準拠するために、独立したサードパーティによって定期的に監査されます。</span><span class="sxs-lookup"><span data-stu-id="88e9e-110">Microsoft 365, its access controls, and supporting services, including Azure Active Directory and physical datacenters, are regularly audited by independent third-parties for compliance with [ISO/IEC 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [ISO/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP), and other [standards](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).</span></span>
- <span data-ttu-id="88e9e-111">Microsoft 365 のエンジニアは、毎年セキュリティトレーニングを実施し、昇格したアクセスのベストプロシージャを確認し、Microsoft のセキュリティおよびプライバシーポリシーに同意して、サービスに対する権限を維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88e9e-111">Microsoft 365 engineers must take yearly security training, review elevated access best procedures, and acknowledge Microsoft's security and privacy policies to maintain entitlements to the service.</span></span>

<span data-ttu-id="88e9e-112">短時間に複数の失敗したログインなど、疑わしい動作が検出されたときに自動アラートがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="88e9e-112">Automated alerts trigger when suspicious activity is detected, such as multiple failed logins within a short period.</span></span> <span data-ttu-id="88e9e-113">Microsoft 365 セキュリティ対応チームは、機械学習と大規模データ分析を使用して、アクティビティのレビューと分析、不規則なアクセスパターンの検索、および異常で不法なアクティビティへの予防的な対応を行います。</span><span class="sxs-lookup"><span data-stu-id="88e9e-113">The Microsoft 365 Security Response team uses machine learning and big data analysis to review and analyze activity, look for irregular access patterns, and proactively respond to anomalous and illicit activities.</span></span> <span data-ttu-id="88e9e-114">また、Microsoft は、一連の侵入テスト担当者を採用しており、定期的に赤色のチームと青のチームの練習を行い、サービスのセキュリティとアクセス制御の問題を見つけます。</span><span class="sxs-lookup"><span data-stu-id="88e9e-114">Microsoft also employs a dedicated team of penetration testers and engages in periodic Red Team and Blue Team exercises to find security and access control issues in the service.</span></span> <span data-ttu-id="88e9e-115">お客様は、Microsoft 365 によって提供される監査レポートと管理アクティビティ API を使用して、アクセス制御システムの有効性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="88e9e-115">Customers can verify the effectiveness of access control systems by using audit reports and the management activity API provided by Microsoft 365.</span></span>

<span data-ttu-id="88e9e-116">詳細については、「 [office 365 Management ACTIVITY API reference](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference) and [Auditing And reporting in Microsoft 365](office-365-auditing-and-reporting-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88e9e-116">For more information, see [Office 365 Management Activity API reference](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference) and [Auditing and reporting in Microsoft 365](office-365-auditing-and-reporting-overview.md).</span></span>
