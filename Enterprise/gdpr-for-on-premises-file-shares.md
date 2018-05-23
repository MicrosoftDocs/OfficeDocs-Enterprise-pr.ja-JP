---
title: オンプレミス ファイル共有の GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: オンプレミスの Windows Server ファイル共有で GDPR の要件に対応する方法について説明します。
ms.openlocfilehash: d9d17f134d77ee03e11208744ba9a2e56d506b1f
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-on-premises-windows-server-file-shares"></a><span data-ttu-id="7acf7-103">オンプレミスの Windows Server ファイル共有の GDPR</span><span class="sxs-lookup"><span data-stu-id="7acf7-103">GDPR for on-premises Windows Server file shares</span></span>

<span data-ttu-id="7acf7-104">ファイル共有のための推奨される基本的なアプローチは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7acf7-104">The basic recommended approach for file shares is:</span></span>

-   <span data-ttu-id="7acf7-105">Azure Information Protection を使用して、機密データにラベルを付けます。</span><span class="sxs-lookup"><span data-stu-id="7acf7-105">Use Azure Information Protection to label sensitive data.</span></span>

-   <span data-ttu-id="7acf7-106">Azure Information Protection スキャナーを使用して、データを検索します。</span><span class="sxs-lookup"><span data-stu-id="7acf7-106">Use Azure Information Protection scanner to find data.</span></span>

<span data-ttu-id="7acf7-107">ファイル共有のための推奨されるアプローチには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7acf7-107">The recommended approach for files shares includes these steps:</span></span>

1.  <span data-ttu-id="7acf7-108">**Azure Information Protection スキャナーをインストールし、構成します。**</span><span class="sxs-lookup"><span data-stu-id="7acf7-108">**Install and configure Azure Information Protection scanner.**</span></span>

    -   <span data-ttu-id="7acf7-109">使用する機密データの種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="7acf7-109">Decide which sensitive data types to use.</span></span>

    -   <span data-ttu-id="7acf7-110">使用するローカル フォルダーとネットワーク共有を指定します。</span><span class="sxs-lookup"><span data-stu-id="7acf7-110">Specify local folders and network shares to use.</span></span>

2.  <span data-ttu-id="7acf7-111">**検出サイクルを完了します。**</span><span class="sxs-lookup"><span data-stu-id="7acf7-111">**Complete a discovery cycle.**</span></span>

    -   <span data-ttu-id="7acf7-112">検出モードでスキャナーを実行し、検出結果を検証します。</span><span class="sxs-lookup"><span data-stu-id="7acf7-112">Run the scanner in discovery mode and validate the findings.</span></span>

    -   <span data-ttu-id="7acf7-113">必要に応じて、条件と機密情報の種類を最適化します。</span><span class="sxs-lookup"><span data-stu-id="7acf7-113">If needed, optimize the conditions and sensitive information types.</span></span>

    -   <span data-ttu-id="7acf7-114">自動的に適用されるラベルの予期される影響を評価します。</span><span class="sxs-lookup"><span data-stu-id="7acf7-114">Assess the expected impact of automatically applying labels.</span></span>

3.  <span data-ttu-id="7acf7-115">**Azure Information Protection スキャナーを実行して、対象となるドキュメントにラベルを適用します**。</span><span class="sxs-lookup"><span data-stu-id="7acf7-115">**Run the Azure Information Protection scanner to apply labels to qualifying documents**.</span></span>

4.  <span data-ttu-id="7acf7-116">**保護のために、**</span><span class="sxs-lookup"><span data-stu-id="7acf7-116">**For protection:**</span></span>

    -   <span data-ttu-id="7acf7-117">目的としたラベルのドキュメントを保護するための Exchange データ損失防止ルールを構成します。</span><span class="sxs-lookup"><span data-stu-id="7acf7-117">Configure Exchange data loss prevention rules to protect documents with the desired label.</span></span>

    -   <span data-ttu-id="7acf7-118">アクセス許可を使用して、ファイルにアクセスできるユーザーを制限するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="7acf7-118">Be sure to use permissions to limit who can access files.</span></span>

5.  <span data-ttu-id="7acf7-119">**監視のため、Windows Server のログを SIEM ツールに統合します。**</span><span class="sxs-lookup"><span data-stu-id="7acf7-119">**For monitoring, integrate Windows Server logs with a SIEM tool.**</span></span>

    -   <span data-ttu-id="7acf7-p101">データ主体要求の個人データを検索するため、Azure Information Protection スキャナーを使用します。また、ファイル共有をクロールするよう、SharePoint Server 検索を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="7acf7-p101">To find personal data for data subject requests, use Azure Information Protection scanner. You can also configure SharePoint Server search to crawl file shares.</span></span>

<span data-ttu-id="7acf7-122">Azure Information Protection スキャナーを使用して個人データを検索したりラベル付けしたりすることに関する詳細については、[http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>) にある Microsoft GDPR Data Discovery Toolkit を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7acf7-122">For more information on using Azure Information Protection scanner to find and label personal data, see the Microsoft GDPR Data Discovery Toolkit at [http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>).</span></span>

<span data-ttu-id="7acf7-p102">さまざまな条件でスキャナーを構成すること、また Office 365 データ損失防止 (DLP) のさまざまな機密情報タイプを使用することに関する情報については、「[Azure Information Protection 用の自動および推奨分類の条件を構成する方法](https://docs.microsoft.com/ja-JP/information-protection/deploy-use/configure-policy-classification)」を参照してください。新しいタイプの Office 365 機密情報はスキャナーですぐに利用できるようになるわけではなく、カスタム機密情報タイプはスキャナーで使用できないことに注意ください。</span><span class="sxs-lookup"><span data-stu-id="7acf7-p102">For information on configuring the scanner for conditions and using the Office 365 data loss prevention (DLP) sensitive information types, see [How to configure conditions for automatic and recommended classification for Azure Information Protection](https://docs.microsoft.com/ja-JP/information-protection/deploy-use/configure-policy-classification). Note that new Office 365 sensitive information types will not be immediately available to use with the scanner and custom sensitive information types cannot be used with the scanner.</span></span>
