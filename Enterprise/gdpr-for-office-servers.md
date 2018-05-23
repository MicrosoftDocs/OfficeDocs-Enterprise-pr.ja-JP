---
title: Office Server の GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: オンプレミス サーバー上の Office で GDPR の要件に対応する方法について説明します。
ms.openlocfilehash: dc1150361db6a28f011e4890a2770f4a6b607a91
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-office-on-premises-servers"></a><span data-ttu-id="e1c7c-103">オンプレミス サーバー上の Office の GDPR</span><span class="sxs-lookup"><span data-stu-id="e1c7c-103">GDPR for Office on-premises Servers</span></span>

<span data-ttu-id="e1c7c-p101">一般データ保護規則 (GDPR) により、組織が個人データを保護し、データ主体要求に適切に応答するための要件が導入されます。このシリーズの記事では、オンプレミスのワークロードのために推奨されるアプローチを示します。</span><span class="sxs-lookup"><span data-stu-id="e1c7c-p101">The General Data Protection Regulation (GDPR) introduces requirements for organizations to protect personal data and respond appropriately to data subject requests. This series of articles provides recommended approaches for on-premises workloads:</span></span>

-   [<span data-ttu-id="e1c7c-106">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="e1c7c-106">Exchange Server</span></span>](gdpr-for-exchange-server.md)

-   [<span data-ttu-id="e1c7c-107">Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="e1c7c-107">Skype for Business Server</span></span>](gdpr-for-skype-for-business-server.md)

-   [<span data-ttu-id="e1c7c-108">Project Server</span><span class="sxs-lookup"><span data-stu-id="e1c7c-108">Project Server</span></span>](gdpr-for-project-server.md)

-   [<span data-ttu-id="e1c7c-109">Office Web Apps Server および Office Online Server</span><span class="sxs-lookup"><span data-stu-id="e1c7c-109">Office Web Apps Server and Office Online Server</span></span>](gdpr-for-office-online-server.md)

-   [<span data-ttu-id="e1c7c-110">オンプレミス ファイル共有</span><span class="sxs-lookup"><span data-stu-id="e1c7c-110">On-premises file shares</span></span>](gdpr-for-on-premises-file-shares.md)

<span data-ttu-id="e1c7c-111">GDPR について、また Microsoft による支援方法の詳細については、[Microsoft セキュリティ センター](https://www.microsoft.com/ja-JP/TrustCenter/Privacy/gdpr/default.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1c7c-111">For more information about the GDPR and how Microsoft can help you, see the [Microsoft Trust Center](https://www.microsoft.com/ja-JP/TrustCenter/Privacy/gdpr/default.aspx).</span></span>

<span data-ttu-id="e1c7c-p102">オンプレミス データで何らかの作業を実行する前に、法律およびコンプライアンスのチームに問い合わせて、ガイダンス情報を入手し、個人データを処理する際の既存の分類スキーマやアプローチについて確認してください。Microsoft では、[http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>) の Microsoft GDPR Data Discovery Toolkit で、分類スキーマの開発と拡張の推奨事項を提供しています。このツールキットでは、オンプレミス データをクラウドに移行するためのアプローチも記述されています。クラウドでは、必要に応じて、より洗練されたデータ ガバナンス機能を使用できます。このセクションの記事では、意図的にオンプレミスのままにするデータに関する推奨事項が示されています。</span><span class="sxs-lookup"><span data-stu-id="e1c7c-p102">Before doing any work with on-premises data, consult with your legal and compliance teams to seek guidance and to learn about existing classification schemas and approaches to working with personal data. Microsoft provides recommendations for developing and extending classifications schemas in the Microsoft GDPR Data Discovery Toolkit at [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>). This toolkit also describes approaches for moving on-premises data to the cloud where you can use more sophisticated data governance capabilities, if this is desired. The articles in this section provide recommendations for data that is intended to remain on premises.</span></span>

<span data-ttu-id="e1c7c-p103">次の図に、これらのワークロードそれぞれで、個人データを検出、分類、保護、監視するために使用する推奨機能のリストを示します。詳細については、このセクションの記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1c7c-p103">The following illustration lists recommended capabilities to use across each of these workloads to discover, classify, protect, and monitor personal data. See the articles in this section for more information.</span></span>

![](media/gdpr-for-office-servers_image1.png)

## <a name="illustration-description"></a><span data-ttu-id="e1c7c-118">図の説明</span><span class="sxs-lookup"><span data-stu-id="e1c7c-118">Illustration description</span></span>

<span data-ttu-id="e1c7c-119">見やすいように、次の表では図の例と同じ例を記載しています。</span><span class="sxs-lookup"><span data-stu-id="e1c7c-119">For accessibility, the following table provides the same examples in the illustration.</span></span>

|             |<span data-ttu-id="e1c7c-120">Windows Server ファイル共有</span><span class="sxs-lookup"><span data-stu-id="e1c7c-120">Windows Server file shares</span></span>|<span data-ttu-id="e1c7c-121">SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="e1c7c-121">SharePoint Server</span></span>|<span data-ttu-id="e1c7c-122">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="e1c7c-122">Exchange Server</span></span>|<span data-ttu-id="e1c7c-123">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="e1c7c-123">Skype for Business</span></span>|<span data-ttu-id="e1c7c-124">Project Server</span><span class="sxs-lookup"><span data-stu-id="e1c7c-124">Project Server</span></span>|
|:------------|:-------------------------|:----------------|:--------------|:-----------------|:-------------|
|<span data-ttu-id="e1c7c-125">検出</span><span class="sxs-lookup"><span data-stu-id="e1c7c-125">discover
</span></span>|<span data-ttu-id="e1c7c-126">Azure Information Protection スキャナー\*</span><span class="sxs-lookup"><span data-stu-id="e1c7c-126">Azure Information Protection</span></span>|<span data-ttu-id="e1c7c-127">検索センターまたは電子情報開示 (データ分類後); Azure Information Protection スキャナー\*</span><span class="sxs-lookup"><span data-stu-id="e1c7c-127">Search Center or eDiscovery (after data is classified); Azure Information Protection scanner\*</span></span>|<span data-ttu-id="e1c7c-128">Exchange 電子情報開示ポータル</span><span class="sxs-lookup"><span data-stu-id="e1c7c-128">Exchange eDiscovery Portal</span></span>|<span data-ttu-id="e1c7c-129">Exchange 電子情報開示ポータル</span><span class="sxs-lookup"><span data-stu-id="e1c7c-129">Exchange eDiscovery portal</span></span>|<span data-ttu-id="e1c7c-130">検出およびエクスポートのための SQL スクリプト</span><span class="sxs-lookup"><span data-stu-id="e1c7c-130">SQL scripts for discovery and exporting</span></span>|
|<span data-ttu-id="e1c7c-131">分類</span><span class="sxs-lookup"><span data-stu-id="e1c7c-131">Classify</span></span>|<span data-ttu-id="e1c7c-132">Azure Information Protection スキャナー\*; Office 365 機密情報タイプ</span><span class="sxs-lookup"><span data-stu-id="e1c7c-132">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="e1c7c-133">Azure Information Protection スキャナー\*; Office 365 機密情報タイプ</span><span class="sxs-lookup"><span data-stu-id="e1c7c-133">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="e1c7c-134">Exchange 保持タグおよびアイテム保持ポリシー</span><span class="sxs-lookup"><span data-stu-id="e1c7c-134">Exchange retention tags and retention policies</span></span>|<span data-ttu-id="e1c7c-135">Exchange 保持タグおよびアイテム保持ポリシー</span><span class="sxs-lookup"><span data-stu-id="e1c7c-135">Exchange retention tags and retention policies</span></span>||
|<span data-ttu-id="e1c7c-136">保護</span><span class="sxs-lookup"><span data-stu-id="e1c7c-136">protect</span></span>||<span data-ttu-id="e1c7c-137">Exchange Server データ損失防止規則; アクセス許可、ライブラリの IRM 保護</span><span class="sxs-lookup"><span data-stu-id="e1c7c-137">Exchange Server data loss prevention rules; Permissions, IRM-protection for libraries</span></span>|<span data-ttu-id="e1c7c-138">Exchange Server データ損失防止規則; IRM と Exchange Server の統合</span><span class="sxs-lookup"><span data-stu-id="e1c7c-138">Exchange Server data loss prevention rules; IRM integration with Exchange Server</span></span>|||
|<span data-ttu-id="e1c7c-139">監視</span><span class="sxs-lookup"><span data-stu-id="e1c7c-139">Monitor</span></span>|<span data-ttu-id="e1c7c-140">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="e1c7c-140">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="e1c7c-141">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="e1c7c-141">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="e1c7c-142">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="e1c7c-142">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="e1c7c-143">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="e1c7c-143">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="e1c7c-144">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="e1c7c-144">Integrate logs with SIEM tools</span></span>|

<span data-ttu-id="e1c7c-p104">\*GDPR では、保護を含まないラベルを適用します。保護では、ファイルが暗号化されます。その結果、SharePoint Server では、それらのファイル内の機密情報タイプを検出できません。</span><span class="sxs-lookup"><span data-stu-id="e1c7c-p104">\*For GDPR, apply labels that do not include protection. Protection encrypts the file. Consequently, SharePoint Server can't find the sensitive information types in these files.</span></span>
