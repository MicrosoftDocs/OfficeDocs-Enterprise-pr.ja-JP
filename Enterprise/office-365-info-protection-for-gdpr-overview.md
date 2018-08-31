---
title: GDPR のための Office 365 の情報保護の概要
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- GDPR
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: ''
description: GDPR のための Office 365 の情報保護の概要を確認します。個人データを検出、分類、保護、監視する方法について説明します。
ms.openlocfilehash: 472fa9592c87b2ccd0f684aa06b5a996e33f34c2
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914882"
---
# <a name="overview-of-office-365-information-protection-for-gdpr"></a><span data-ttu-id="09bd1-104">GDPR のための Office 365 の情報保護の概要</span><span class="sxs-lookup"><span data-stu-id="09bd1-104">Overview of Office 365 Information Protection for GDPR</span></span>

<span data-ttu-id="09bd1-p102">このソリューションでは、Office 365 サービスに保存されている機密データを保護する方法を示します。これには個人データの検出、分類、保護、監視に規定された推奨事項が含まれています。このソリューションでは、例として一般データ保護規制 (GDPR) を使用しますが、その他の多くの規制遵守のためにも同じ手順を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p102">This solution demonstrates how to protect sensitive data that is stored in Office 365 services. It includes prescriptive recommendations for discovering, classifying, protecting, and monitoring personal data. This solution uses General Data Protection Regulation (GDPR) as an example, but you can apply the same process to achieve compliance with many other regulations.</span></span>

<span data-ttu-id="09bd1-p103">GDPR は個人データの収集、保存、処理、共有を規制します。個人データは GDPR のもとで、欧州連合 (EU) 内で特定される個人、または特定可能な個人に関連するあらゆるデータとして、非常に広範に定義されています。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p103">GDPR regulates the collection, storage, processing, and sharing of personal data. Personal data is defined very broadly under the GDPR as any data that relates to an identified or identifiable natural person that is a resident of the European Union (EU).</span></span>

<span data-ttu-id="09bd1-110">記事 4: 定義</span><span class="sxs-lookup"><span data-stu-id="09bd1-110">Article 4 – Definitions</span></span>

> <span data-ttu-id="09bd1-111">‘個人データ’ とは特定される個人、または特定可能な個人 (‘データ主体’) に関連するあらゆる情報であり、特定可能な個人とは、その個人の名前、ID 番号、位置データ、オンライン ID、または物理的、生理学的、遺伝子上、心理的、経済的、文化的、社会的な識別情報に固有の 1 つ以上の因子を参照することによって直接または間接的に特定される人物です。</span><span class="sxs-lookup"><span data-stu-id="09bd1-111">‘personal data’ means any information relating to an identified or identifiable natural person (‘data subject’); an identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural or social identity of that natural person;</span></span>

<span data-ttu-id="09bd1-p104">このソリューションは組織が GDPR の対象となる Office 365 での個人データを検出し、保護するためのものです。これは GDPR のコンプライアンス構成証明としては提供されません。組織は独自に GDPR コンプライアンスを確認する責任を負うため、法務チームまたはコンプライアンス チームに問い合わせるか、コンプライアンスに特化したサード パーティに指導とアドバイスを求めることを推奨します。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p104">This solution is intended to help organizations discover and protect personal data in Office 365 that might be subject to the GDPR. It is not offered as a GDPR compliance attestation. Organizations are responsible for ensuring their own GDPR compliance and are advised to consult their legal and compliance teams or to seek guidance and advice from third parties that specialize in compliance.</span></span>

<span data-ttu-id="09bd1-115">[GDPR 評価](https://assessment.microsoft.com/gdpr-compliance)は迅速なオンライン自己評価ツールであり、組織はコストをかけずに、それ自体の GDPR への遵守状況の全体的なレベルを確認することができます (<http://aka.ms/gdprassessment>)。</span><span class="sxs-lookup"><span data-stu-id="09bd1-115">[GDPR Assessment](https://assessment.microsoft.com/gdpr-compliance) is a quick, online self-evaluation tool available at no cost to help your organization review its overall level of readiness to comply with the GDPR (<http://aka.ms/gdprassessment>).</span></span>

## <a name="assess-and-manage-your-compliance-risk"></a><span data-ttu-id="09bd1-116">コンプライアンスのリスクを評価および管理する</span><span class="sxs-lookup"><span data-stu-id="09bd1-116">Assess and manage your compliance risk</span></span>

<span data-ttu-id="09bd1-p105">GDPR 遵守に向けた最初の手順は、GDPR が組織に適用されるかどうか、また適用される場合はその範囲を評価することです。この分析には、組織で保持するデータとその場所を理解することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p105">The first step towards GDPR compliance is to assess whether the GDPR applies to your organization, and, if so, to what extent. This analysis includes understanding the data your organization processes and where it resides.</span></span>

### <a name="step-1--use-compliance-manager-to-view-the-regulation-requirements-and-track-your-progress"></a><span data-ttu-id="09bd1-119">手順 1: コンプライアンス マネージャーを使用して規制要件を確認し、進捗状況を追跡します。</span><span class="sxs-lookup"><span data-stu-id="09bd1-119">Step 1 — Use Compliance Manager to view the regulation requirements and track your progress</span></span>

<span data-ttu-id="09bd1-120">コンプライアンス マネージャーには監査制御を追跡、実装、管理するためのツールが用意されており、組織は GDPR をはじめとするさまざまな基準に対してコンプライアンスを達成することができます。</span><span class="sxs-lookup"><span data-stu-id="09bd1-120">Compliance Manager provides tools to track, implement, and manage the auditing controls to help your organization reach compliance against various standards, including GDPR.</span></span>

![コンプライアンス マネージャーを使用して要件を表示して進捗状況を追跡する](Media/Overview-image1.png)

<span data-ttu-id="09bd1-122">詳細については、「[Service Trust Portal でコンプライアンス マネージャーを使用する](https://support.office.com/ja-JP/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09bd1-122">For more information, see [Use Compliance Manager in the Service Trust Portal](https://support.office.com/ja-JP/article/Use-Compliance-Manager-in-the-Service-Trust-Portal-Preview-5756d342-5af9-4496-82e8-4dd50fa39942).</span></span> 

### <a name="step-2--use-content-search-and-sensitive-information-types-to-find-personal-data"></a><span data-ttu-id="09bd1-123">手順 2: コンテンツ検索と機密情報の種類を使用して個人データを検索する</span><span class="sxs-lookup"><span data-stu-id="09bd1-123">Step 2 — Use Content Search and sensitive information types to find personal data</span></span> 

<span data-ttu-id="09bd1-p106">環境内で GDPR の対象となる個人データを検出します。コンテンツ検索と機密情報の種類を組み合わせて次のようにします。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p106">Discover personal data in your environment that is subject to the GDPR. Use Content Search together with sensitive information types to:</span></span>

-   <span data-ttu-id="09bd1-126">個人データの保存場所について、検索とレポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="09bd1-126">Find and report on where personal data resides.</span></span>

-   <span data-ttu-id="09bd1-127">機密データの種類とその他のクエリを最適化して、環境内のすべての個人データを検索します。</span><span class="sxs-lookup"><span data-stu-id="09bd1-127">Optimize sensitive data types and other queries to find all personal data in your environment.</span></span>

![コンテンツ検索と機密情報の種類を使用して個人データを検索する](Media/Overview-image2.png)

<span data-ttu-id="09bd1-p107">機密情報の種類は、自動化されたプロセスで、健康保険番号やクレジット カード番号など、特定の情報の種類をどのように認識するかを定義するものです。この記事では、開始点として使用できるセットが含まれています。EU 加盟国の個人データについては、他にも機密情報の種類が追加される予定です。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p107">Sensitive information types define how the automated process recognizes specific information types such as health service numbers and credit card numbers. This article includes a set you can use as a starting point. Many more sensitive information types are coming soon for personal data in EU countries.</span></span>

<span data-ttu-id="09bd1-132">詳細については、「[個人データの検索および検出](search-for-and-find-personal-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09bd1-132">For more information, see [Search for and find personal data](search-for-and-find-personal-data.md).</span></span> 

## <a name="classify-protect-and-monitor-personal-data-in-office-365-and-other-saas-apps"></a><span data-ttu-id="09bd1-133">Office 365 およびその他の SaaS アプリの個人データを分類、保護、監視します。</span><span class="sxs-lookup"><span data-stu-id="09bd1-133">Classify, protect, and monitor personal data in Office 365 and other SaaS apps</span></span>

<span data-ttu-id="09bd1-134">Office 365 での情報保護に使用される一部の機能は、その他の SaaS アプリケーションの機密データ保護にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="09bd1-134">Some of the capabilities used for information protection in Office 365 can also be used to protect sensitive data in other SaaS applications.</span></span>

![個人データを分類、保護、監視する](Media/Overview-image3.png)

<span data-ttu-id="09bd1-136">この図はこのセクションの後半 (手順 3-5) で説明します。</span><span class="sxs-lookup"><span data-stu-id="09bd1-136">This illustration is described by the rest this section (steps 3-5).</span></span>

### <a name="step-3--decide-if-you-want-to-use-labels-in-addition-to-sensitive-information-types"></a><span data-ttu-id="09bd1-137">手順 3: 機密データの種類の他にラベルを使用するかどうかを決定する</span><span class="sxs-lookup"><span data-stu-id="09bd1-137">Step 3 — Decide if you want to use labels in addition to sensitive information types</span></span>

<span data-ttu-id="09bd1-p108">機密データの種類とは、分類の 1 形式です。「[個人データの分類スキーマを設計する](architect-a-classification-schema-for-personal-data.md)」を参照して、ラベルの導入を許可するかどうかを決定します。ラベルを適用するには、「[Office 365 の個人データにラベルを適用する](apply-labels-to-personal-data-in-office-365.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p108">Sensitive information types are a form of classification. See [Architect a classification schema for personal data](architect-a-classification-schema-for-personal-data.md), to decide if you also want to implement labels. To apply labels, see [Apply labels to personal data in Office 365](apply-labels-to-personal-data-in-office-365.md).</span></span>

<span data-ttu-id="09bd1-p109">この図では、機密情報の種類とラベルは Office 365 全体で機能します。今後はこれらを Cloud App Security で使用して、Box や Salesforce など他の SaaS アプリにある機密データを検索できるようになります。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p109">In the illustration, sensitive information types and labels work across Office 365. Coming soon, you can use these with Cloud App Security to find sensitive data in other SaaS apps, such as Box and Salesforce.</span></span>

### <a name="step-4--protect-personal-data-in-office-365"></a><span data-ttu-id="09bd1-143">手順 4: Office 365 の個人データを保護する</span><span class="sxs-lookup"><span data-stu-id="09bd1-143">Step 4 — Protect personal data in Office 365</span></span> 

<span data-ttu-id="09bd1-p110">個人データの保護は Office 365 のデータ損失防止から始まります。個人データへのアクセスを保護するには、電子メールのための Office 365 Message Encryption など、他にもいくつかの推奨機能があります。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p110">Protection for personal data starts with Office 365 data loss prevention. There are several other capabilities recommended for protecting access to personal data, including Office 365 Message Encryption for email.</span></span>

<span data-ttu-id="09bd1-146">これらの保護のターゲットは、特定のデータ セットに設定できます。</span><span class="sxs-lookup"><span data-stu-id="09bd1-146">These protections can be targeted to specific data sets:</span></span>

-   <span data-ttu-id="09bd1-147">サイトおよびライブラリ レベルのアクセス許可</span><span class="sxs-lookup"><span data-stu-id="09bd1-147">Site and library-level permissions</span></span>

-   <span data-ttu-id="09bd1-148">サイト レベルの外部共有ポリシー</span><span class="sxs-lookup"><span data-stu-id="09bd1-148">Site-level external sharing policies</span></span>

-   <span data-ttu-id="09bd1-149">サイトレベルのデバイス アクセス ポリシー</span><span class="sxs-lookup"><span data-stu-id="09bd1-149">Site-level device access policies</span></span>

<span data-ttu-id="09bd1-150">Office 365 およびその他のクラウド サービスへのアクセス保護には、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="09bd1-150">Protection for access to Office 365 and other cloud services include:</span></span>

-   <span data-ttu-id="09bd1-151">Enterprise Mobility + Security (EMS) の ID およびデバイスのアクセス保護</span><span class="sxs-lookup"><span data-stu-id="09bd1-151">Identity and device access protection in Enterprise Mobility + Security (EMS)</span></span>

-   <span data-ttu-id="09bd1-152">特権アクセスの管理</span><span class="sxs-lookup"><span data-stu-id="09bd1-152">Privileged access management</span></span>

-   <span data-ttu-id="09bd1-153">Windows 10 のセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="09bd1-153">Windows 10 security capabilities</span></span>

<span data-ttu-id="09bd1-154">保護を適用する方法の詳細については、「[Office 365 の個人データに保護を適用する](apply-protection-to-personal-data-in-office-365.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09bd1-154">For more information about applying proteciton, see [Apply protection to personal data in Office 365](apply-protection-to-personal-data-in-office-365.md).</span></span>

### <a name="step-5--monitor-for-leaks-of-personal-data"></a><span data-ttu-id="09bd1-155">手順 5: 個人情報の漏えいを監視する</span><span class="sxs-lookup"><span data-stu-id="09bd1-155">Step 5 — Monitor for leaks of personal data</span></span>

<span data-ttu-id="09bd1-p111">Office 365 データ損失防止レポートでは、機密データ監視について最高レベルの詳細を提供します。自動アラートを設定し、Office 365 監査ログを使用して侵害を調査することができます。Cloud App Security は機密データの検索と監視の機能を他の SaaS プロバイダーまで拡張します。これらのツールの詳細は、「[個人データ侵害を監視する](monitor-for-leaks-of-personal-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09bd1-p111">Office 365 data loss prevention reports provide the greatest level of detail for monitoring sensitive data. You can setup automated alerts and investigate breaches by using the Office 365 audit log. Cloud App Security extends the ability to find and monitor sensitive data to other SaaS providers. For more information on these tools, see [Monitor for breaches of personal data](monitor-for-leaks-of-personal-data.md).</span></span>
