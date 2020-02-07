---
title: Office 365 の Office 365 エンジニアリングの内部ログ
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
f1.keywords:
- NOCSH
description: Office 365 エンジニアリングチームの内部ログのしくみについて説明します。
ms.openlocfilehash: 4303b0a927413c791b6b8718fd905f8918c497e1
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844458"
---
# <a name="internal-logging-for-office-365-engineering"></a><span data-ttu-id="bdfa3-103">Office 365 のエンジニアリングのための内部データログ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-103">Internal Logging for Office 365 Engineering</span></span>

<span data-ttu-id="bdfa3-104">お客様が利用できるイベントとログデータに加えて、Office 365 のエンジニアが利用できる内部ログデータ収集システムもあります。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-104">In addition to the events and log data available for customers, there is also an internal log data collection system that is available to Office 365 engineers.</span></span> <span data-ttu-id="bdfa3-105">Office 365 サーバーから、Cosmos と呼ばれる内部の大規模なデータコンピューティングサービスに、さまざまな種類のログデータがアップロードされています。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-105">Many different types of log data are uploaded from Office 365 servers to an internal, big data computing service called Cosmos.</span></span> <span data-ttu-id="bdfa3-106">各サービスチームは、それぞれのサーバーからの監査ログを Cosmos データベースにアップロードして、集約と分析を行います。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-106">Each service team uploads audit logs from their respective servers into the Cosmos database for aggregation and analysis.</span></span> <span data-ttu-id="bdfa3-107">このデータ転送は、「Office データローダー (ODL)」と呼ばれる独自の自動化ツールを使用して、明示的に承認されたポートとプロトコルに基づいて、FIPS 140-2 で検証された TLS 接続を介して行われます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-107">This data transfer occurs over a FIPS 140-2-validated TLS connection on specifically approved ports and protocols using a proprietary automation tool called the Office Data Loader (ODL).</span></span> <span data-ttu-id="bdfa3-108">Office 365 で監査レコードを収集して処理するために使用されるツールでは、元の監査レコードのコンテンツまたは時間の順序を永続的に変更したり、取り消したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-108">The tools used in Office 365 to collect and process audit records do not allow permanent or irreversible changes to the original audit record content or time ordering.</span></span>

<span data-ttu-id="bdfa3-109">サービスチームは、Cosmos を一元的なリポジトリとして使用して、アプリケーションの使用状況の分析、システムおよび運用上のパフォーマンスの測定、問題やセキュリティの問題を示す異常なパターンの調査を行います。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-109">Service teams use Cosmos as a centralized repository to conduct an analysis of application usage, to measure system and operational performance, and to look for abnormalities and patterns that may indicate problems or security issues.</span></span> <span data-ttu-id="bdfa3-110">各サービスチームは、分析の対象に応じてログのベースラインを Cosmos にアップロードします。これには、多くの場合、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-110">Each service team uploads a baseline of logs into Cosmos, depending on what they are looking to analyze, that often include:</span></span>

- <span data-ttu-id="bdfa3-111">イベントログ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-111">Event logs</span></span>
- <span data-ttu-id="bdfa3-112">AppLocker ログ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-112">AppLocker logs</span></span>
- <span data-ttu-id="bdfa3-113">パフォーマンス データ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-113">Performance data</span></span>
- <span data-ttu-id="bdfa3-114">System Center データ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-114">System Center data</span></span>
- <span data-ttu-id="bdfa3-115">通話詳細レコード</span><span class="sxs-lookup"><span data-stu-id="bdfa3-115">Call detail records</span></span>
- <span data-ttu-id="bdfa3-116">Qoe (Quality of experience) データ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-116">Quality of experience data</span></span>
- <span data-ttu-id="bdfa3-117">IIS Web サーバーのログ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-117">IIS Web Server logs</span></span>
- <span data-ttu-id="bdfa3-118">SQL Server ログ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-118">SQL Server logs</span></span>
- <span data-ttu-id="bdfa3-119">Syslog データ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-119">Syslog data</span></span>
- <span data-ttu-id="bdfa3-120">セキュリティ監査ログ</span><span class="sxs-lookup"><span data-stu-id="bdfa3-120">Security audit logs</span></span>

<span data-ttu-id="bdfa3-121">データを Cosmos にアップロードする前に、ODL アプリケーションはスクラブサービスを使用して、テナント情報やエンドユーザー識別情報などの顧客データを含むフィールドを難読化し、それらのフィールドをハッシュ値で置換します。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-121">Prior to uploading data into Cosmos, the ODL application uses a scrubbing service to obfuscate any fields that contain customer data, such as tenant information and end-user identifiable information, and replace those fields with a hash value.</span></span> <span data-ttu-id="bdfa3-122">匿名化とハッシュ化されたログが書き直され、Cosmos にアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-122">The anonymized and hashed logs are rewritten and then uploaded into Cosmos.</span></span> <span data-ttu-id="bdfa3-123">サービスチームは、Cosmos 内のデータに対してスコープ指定クエリを実行して、関連付け、警告、およびレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-123">Service teams run scoped queries against their data in Cosmos for correlation, alerting, and reporting.</span></span> <span data-ttu-id="bdfa3-124">Cosmos での監査ログデータの保持期間は、サービスチームによって決定されます。ほとんどの監査ログデータは、セキュリティインシデント調査のサポートおよび規制保持要件への対応のために、90日間またはそれ以上保持されます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-124">The period of audit log data retention in Cosmos is determined by the service teams; most audit log data is retained for 90 days or longer to support security incident investigations and to meet regulatory retention requirements.</span></span>

<span data-ttu-id="bdfa3-125">Cosmos に格納されている Office 365 データへのアクセスは、権限のある人物に制限されます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-125">Access to Office 365 data stored in Cosmos is restricted to authorized personnel.</span></span> <span data-ttu-id="bdfa3-126">Microsoft は、監査機能の管理を、監査機能を担当するサービスチームメンバーの制限されたサブセットに制限します。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-126">Microsoft restricts the management of audit functionality to the limited subset of service team members that are responsible for audit functionality.</span></span> <span data-ttu-id="bdfa3-127">これらのチームメンバーは、Cosmos のデータを変更または削除することはできません。また、Cosmos のログメカニズムに加えられたすべての変更は記録および監査されます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-127">These team members do not have the ability to modify or delete data from Cosmos, and all changes to logging mechanisms for Cosmos are recorded and audited.</span></span>

<span data-ttu-id="bdfa3-128">各サービスチームは、特定のアプリケーションが特定の分析を実行することを承認することによって、分析用のログデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-128">Each service team accesses its log data for analysis by authorizing certain applications to conduct specific analysis.</span></span> <span data-ttu-id="bdfa3-129">たとえば、Office 365 セキュリティチームは、独自のイベントログパーサーを使用して Cosmos のデータを使用して、Office 365 運用環境で疑わしい可能性のあるアクティビティに関する操作可能なレポートを関連付け、警告、および生成します。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-129">For example, the Office 365 Security team uses data from Cosmos through a proprietary event log parser to correlate, alert, and generate actionable reports on possible suspicious activity in the Office 365 production environment.</span></span> <span data-ttu-id="bdfa3-130">このデータからのレポートは、脆弱性を修正し、サービスの全体的なパフォーマンスを向上させるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-130">The reports from this data are used to correct vulnerabilities, and to improve the overall performance of the service.</span></span> <span data-ttu-id="bdfa3-131">特定の警告またはレポートでさらに調査が必要な場合、サービス担当者は、そのデータを Office 365 サービスにインポートし直すように要求できます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-131">If a specific alert or report requires further investigation, service personnel can request that data be imported back into the Office 365 service.</span></span> <span data-ttu-id="bdfa3-132">Cosmos からインポートされる特定のログは暗号化されており、サービス担当者は復号化キーにアクセスできないため、対象のログは、スコープが設定された結果を承認済みのサービス担当者に返す復号化サービスを介してプログラムによって渡されます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-132">Since the specific log being imported from Cosmos is in encrypted and service personnel do not have access to decryption keys, the target log is programmatically passed through a decryption service that returns scoped results to the authorized service personnel.</span></span> <span data-ttu-id="bdfa3-133">この課題から見つかった脆弱性は、Microsoft の標準セキュリティインシデント管理チャネルを使用して報告およびエスカレートされます。</span><span class="sxs-lookup"><span data-stu-id="bdfa3-133">Any vulnerabilities found from this exercise are reported and escalated using Microsoft's standard security incident management channels.</span></span>
