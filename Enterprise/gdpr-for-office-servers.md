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
ms.openlocfilehash: bfacb297c77041cf905d2eef6645da3b7459962c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915482"
---
# <a name="gdpr-for-office-on-premises-servers"></a><span data-ttu-id="f3ff6-103">オンプレミス サーバー上の Office の GDPR</span><span class="sxs-lookup"><span data-stu-id="f3ff6-103">GDPR for Office on-premises Servers</span></span>

<span data-ttu-id="f3ff6-p101">一般データ保護規則 (GDPR) により、組織が個人データを保護し、データ主体要求に適切に応答するための要件が導入されます。このシリーズの記事では、オンプレミスのワークロードのために推奨されるアプローチを示します。</span><span class="sxs-lookup"><span data-stu-id="f3ff6-p101">The General Data Protection Regulation (GDPR) introduces requirements for organizations to protect personal data and respond appropriately to data subject requests. This series of articles provides recommended approaches for on-premises workloads:</span></span>

-   [<span data-ttu-id="f3ff6-106">SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="f3ff6-106">SharePoint Server</span></span>](gdpr-for-sharepoint-server.md)

-   [<span data-ttu-id="f3ff6-107">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="f3ff6-107">Exchange Server</span></span>](gdpr-for-exchange-server.md)

-   [<span data-ttu-id="f3ff6-108">Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="f3ff6-108">Skype for Business Server</span></span>](gdpr-for-skype-for-business-server.md)

-   [<span data-ttu-id="f3ff6-109">Project Server</span><span class="sxs-lookup"><span data-stu-id="f3ff6-109">Project Server</span></span>](gdpr-for-project-server.md)

-   [<span data-ttu-id="f3ff6-110">Office Web Apps Server および Office Online Server</span><span class="sxs-lookup"><span data-stu-id="f3ff6-110">Office Web Apps Server and Office Online Server</span></span>](gdpr-for-office-online-server.md)

-   [<span data-ttu-id="f3ff6-111">オンプレミス ファイル共有</span><span class="sxs-lookup"><span data-stu-id="f3ff6-111">On-premises file shares</span></span>](gdpr-for-on-premises-file-shares.md)

<span data-ttu-id="f3ff6-112">GDPR について、また Microsoft による支援方法の詳細については、[Microsoft セキュリティ センター](https://www.microsoft.com/ja-JP/TrustCenter/Privacy/gdpr/default.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3ff6-112">For more information about the GDPR and how Microsoft can help you, see the [Microsoft Trust Center](https://www.microsoft.com/ja-JP/TrustCenter/Privacy/gdpr/default.aspx).</span></span>

<span data-ttu-id="f3ff6-p102">オンプレミス データで何らかの作業を実行する前に、法律およびコンプライアンスのチームに問い合わせて、ガイダンス情報を入手し、個人データを処理する際の既存の分類スキーマやアプローチについて確認してください。Microsoft では、[http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>) の Microsoft GDPR Data Discovery Toolkit で、分類スキーマの開発と拡張の推奨事項を提供しています。このツールキットでは、オンプレミス データをクラウドに移行するためのアプローチも記述されています。クラウドでは、必要に応じて、より洗練されたデータ ガバナンス機能を使用できます。このセクションの記事では、意図的にオンプレミスのままにするデータに関する推奨事項が示されています。</span><span class="sxs-lookup"><span data-stu-id="f3ff6-p102">Before doing any work with on-premises data, consult with your legal and compliance teams to seek guidance and to learn about existing classification schemas and approaches to working with personal data. Microsoft provides recommendations for developing and extending classifications schemas in the Microsoft GDPR Data Discovery Toolkit at [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>). This toolkit also describes approaches for moving on-premises data to the cloud where you can use more sophisticated data governance capabilities, if this is desired. The articles in this section provide recommendations for data that is intended to remain on premises.</span></span>

<span data-ttu-id="f3ff6-p103">次の図に、これらのワークロードそれぞれで、個人データを検出、分類、保護、監視するために使用する推奨機能のリストを示します。詳細については、このセクションの記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3ff6-p103">The following illustration lists recommended capabilities to use across each of these workloads to discover, classify, protect, and monitor personal data. See the articles in this section for more information.</span></span>

![](media/gdpr-for-office-servers-image1.png)

## <a name="illustration-description"></a><span data-ttu-id="f3ff6-119">図の説明</span><span class="sxs-lookup"><span data-stu-id="f3ff6-119">Illustration description</span></span>

<span data-ttu-id="f3ff6-120">見やすいように、次の表では図の例と同じ例を記載しています。</span><span class="sxs-lookup"><span data-stu-id="f3ff6-120">For accessibility, the following table provides the same examples in the illustration.</span></span>

|             |<span data-ttu-id="f3ff6-121">Windows Server ファイル共有</span><span class="sxs-lookup"><span data-stu-id="f3ff6-121">Windows Server file shares</span></span>|<span data-ttu-id="f3ff6-122">SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="f3ff6-122">SharePoint Server</span></span>|<span data-ttu-id="f3ff6-123">Exchange Server</span><span class="sxs-lookup"><span data-stu-id="f3ff6-123">Exchange Server</span></span>|<span data-ttu-id="f3ff6-124">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="f3ff6-124">Skype for Business</span></span>|<span data-ttu-id="f3ff6-125">Project Server</span><span class="sxs-lookup"><span data-stu-id="f3ff6-125">Project Server</span></span>|
|:------------|:-------------------------|:----------------|:--------------|:-----------------|:-------------|
|<span data-ttu-id="f3ff6-126">検出</span><span class="sxs-lookup"><span data-stu-id="f3ff6-126">Discover</span></span>|<span data-ttu-id="f3ff6-127">Azure Information Protection スキャナー\*</span><span class="sxs-lookup"><span data-stu-id="f3ff6-127">Azure Information Protection scanner\*</span></span>|<span data-ttu-id="f3ff6-128">検索センターまたは電子情報開示 (データ分類後); Azure Information Protection スキャナー\*</span><span class="sxs-lookup"><span data-stu-id="f3ff6-128">Search Center or eDiscovery (after data is classified); Azure Information Protection scanner\*</span></span>|<span data-ttu-id="f3ff6-129">Exchange 電子情報開示ポータル</span><span class="sxs-lookup"><span data-stu-id="f3ff6-129">Exchange eDiscovery Portal</span></span>|<span data-ttu-id="f3ff6-130">Exchange 電子情報開示ポータル</span><span class="sxs-lookup"><span data-stu-id="f3ff6-130">Exchange eDiscovery portal</span></span>|<span data-ttu-id="f3ff6-131">検出およびエクスポートのための SQL スクリプト</span><span class="sxs-lookup"><span data-stu-id="f3ff6-131">SQL scripts for discovery and exporting</span></span>|
|<span data-ttu-id="f3ff6-132">分類</span><span class="sxs-lookup"><span data-stu-id="f3ff6-132">Classify</span></span>|<span data-ttu-id="f3ff6-133">Azure Information Protection スキャナー\*; Office 365 機密情報タイプ</span><span class="sxs-lookup"><span data-stu-id="f3ff6-133">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="f3ff6-134">Azure Information Protection スキャナー\*; Office 365 機密情報タイプ</span><span class="sxs-lookup"><span data-stu-id="f3ff6-134">Azure Information Protection scanner\*; Office 365 sensitive information types</span></span>|<span data-ttu-id="f3ff6-135">Exchange 保持タグおよびアイテム保持ポリシー</span><span class="sxs-lookup"><span data-stu-id="f3ff6-135">Exchange retention tags and retention policies</span></span>|<span data-ttu-id="f3ff6-136">Exchange 保持タグおよびアイテム保持ポリシー</span><span class="sxs-lookup"><span data-stu-id="f3ff6-136">Exchange retention tags and retention policies</span></span>||
|<span data-ttu-id="f3ff6-137">保護</span><span class="sxs-lookup"><span data-stu-id="f3ff6-137">Protect</span></span>||<span data-ttu-id="f3ff6-138">Exchange Server データ損失防止規則; アクセス許可、ライブラリの IRM 保護</span><span class="sxs-lookup"><span data-stu-id="f3ff6-138">Exchange Server data loss prevention rules; Permissions, IRM-protection for libraries</span></span>|<span data-ttu-id="f3ff6-139">Exchange Server データ損失防止規則; IRM と Exchange Server の統合</span><span class="sxs-lookup"><span data-stu-id="f3ff6-139">Exchange Server data loss prevention rules; IRM integration with Exchange Server</span></span>|||
|<span data-ttu-id="f3ff6-140">監視</span><span class="sxs-lookup"><span data-stu-id="f3ff6-140">Monitor</span></span>|<span data-ttu-id="f3ff6-141">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="f3ff6-141">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="f3ff6-142">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="f3ff6-142">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="f3ff6-143">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="f3ff6-143">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="f3ff6-144">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="f3ff6-144">Integrate logs with SIEM tools</span></span>|<span data-ttu-id="f3ff6-145">SIEM ツールとのログ統合</span><span class="sxs-lookup"><span data-stu-id="f3ff6-145">Integrate logs with SIEM tools</span></span>|

<span data-ttu-id="f3ff6-p104">\* 保護機能によってファイルが暗号化されることに注意してください。結果として、SharePoint Server では、保護されたファイルの機密情報の種類を検索できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f3ff6-p104">\*Note that protection encrypts the file. Consequently, SharePoint Server can’t find the sensitive information types in protected files.</span></span>
