---
title: 個人データの検索
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
description: Office 365 の個人データを検索する方法について説明します。
ms.openlocfilehash: 8f1a293377570233e4d3ef01da9c56345768828c
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914912"
---
# <a name="search-for-and-find-personal-data"></a><span data-ttu-id="f57d3-103">個人データの検索</span><span class="sxs-lookup"><span data-stu-id="f57d3-103">Search for and find personal data</span></span>

<span data-ttu-id="f57d3-104">個人データは GDPR のもとで、欧州連合 (EU) 内で特定される個人、または特定可能な個人に関連するあらゆるデータとして、非常に広範に定義されています。</span><span class="sxs-lookup"><span data-stu-id="f57d3-104">Personal data is defined very broadly under the GDPR as any data that relates to an identified or identifiable natural person that is a resident of the European Union (EU).</span></span>

<span data-ttu-id="f57d3-105">記事 4: 定義</span><span class="sxs-lookup"><span data-stu-id="f57d3-105">Article 4 – Definitions</span></span>

> <span data-ttu-id="f57d3-106">‘個人データ’ とは特定される個人、または特定可能な個人 (‘データ主体’) に関連するあらゆる情報であり、特定可能な個人とは、その個人の名前、ID 番号、位置データ、オンライン ID、または物理的、生理学的、遺伝子上、心理的、経済的、文化的、社会的な識別情報に固有の 1 つ以上の因子を参照することによって直接または間接的に特定される人物です。</span><span class="sxs-lookup"><span data-stu-id="f57d3-106">‘personal data’ means any information relating to an identified or identifiable natural person (‘data subject’); an identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural or social identity of that natural person;</span></span>

<span data-ttu-id="f57d3-107">この記事では、SharePoint Online および OneDrive for Business (すべての Office 365 グループおよび Microsoft Teams のサイトを含む) に保管されている個人データを検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-107">This article demonstrates how to find personal data stored in SharePoint Online and OneDrive for Business (which includes the sites for all Office 365 groups and Microsoft Teams).</span></span>

<span data-ttu-id="f57d3-p101">GDPR の対象となる個人データの検索には、Office 365 での機密情報の種類を使用する必要があります。これによって自動化プロセスが健康保険番号やクレジット カード番号などの特定情報の種類を認識する方法が定義されます。現時点では、機密情報の種類は Exchange メールボックスに保管中のデータの検索には使用できません。ただし機密情報の種類は、データ損失防止ポリシーとともに、移動中の電子メールに含まれる個人データの検索には使用できます。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p101">Finding personal data subject to GDPR relies on using sensitive information types in Office 365. These define how the automated process recognizes specific information types such as health service numbers and credit card numbers. At this time these cannot be used to find data in Exchange mailboxes at rest. However, sensitive information types can be used with data loss prevention policies to find personal data in mail while in transit.</span></span>

<span data-ttu-id="f57d3-112">そのため、現在は Exchange Online メールボックスに保管中の個人データはコンテンツ検索には使用できませんが、GDPR のためにまとめた機密情報の種類を使用して、個人情報が電子メールで送信されるときに検索し、保護することができます。</span><span class="sxs-lookup"><span data-stu-id="f57d3-112">So, while you can’t currently use Content Search to find personal data at rest in Exchange Online mailboxes, you can use the sensitive information types you curate for GDPR to find and protect personal information as it is sent through email.</span></span>

## <a name="use-content-search-to-find-personal-data"></a><span data-ttu-id="f57d3-113">コンテンツ検索を使用して個人データを検索する</span><span class="sxs-lookup"><span data-stu-id="f57d3-113">Use Content Search to find personal data</span></span>

<span data-ttu-id="f57d3-p102">Microsoft では、Office 365 の個人データ検索に 3 段階のアプローチをお勧めします。このトピックの残りの部分では、これらの各段階について説明します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p102">Microsoft recommends a three-stage approach to finding personal data in Office 365. The rest of this topic provides guidance for each of these stages.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f57d3-116"><strong>手順</strong></span><span class="sxs-lookup"><span data-stu-id="f57d3-116"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="f57d3-117"><strong>説明</strong></span><span class="sxs-lookup"><span data-stu-id="f57d3-117"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="f57d3-118">1. 機密情報の種類の検索</span><span class="sxs-lookup"><span data-stu-id="f57d3-118">1. Search for sensitive information types</span></span></p></td>
<td align="left"><p><span data-ttu-id="f57d3-p103">機密情報の種類を使用して個人データの検索を開始します。各機密情報の種類に対してコンテンツ検索クエリを作成します。クエリを実行し、結果を分析します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p103">Start by using sensitive information types to find personal data. Create a Content Search query for each sensitive information type. Run the query and analyze the results.</span></span></p>
<span data-ttu-id="f57d3-122">必要に応じてクエリにパラメーターを追加し、誤検知を減らします。</span><span class="sxs-lookup"><span data-stu-id="f57d3-122">If needed, add parameters to the query to reduce false positives:</span></span> <li><span data-ttu-id="f57d3-123">カウント範囲</span><span class="sxs-lookup"><span data-stu-id="f57d3-123">Count range</span></span></li>
    <li><span data-ttu-id="f57d3-124">信頼範囲</span><span class="sxs-lookup"><span data-stu-id="f57d3-124">Confidence range</span></span></li>
    <li><span data-ttu-id="f57d3-125">より複雑なクエリのためのその他のプロパティや演算子</span><span class="sxs-lookup"><span data-stu-id="f57d3-125">Other properties or operators for more complex queries</span></span></li>
<p><span data-ttu-id="f57d3-126">必要であれば、機密情報の種類を変更して組織の精度を向上させます。</span><span class="sxs-lookup"><span data-stu-id="f57d3-126">If necessary, modify a sensitive information type to improve accuracy for your organization:</span></span></p>
<p><li><span data-ttu-id="f57d3-127">XML で信頼度を直接調整します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-127">Adjust the confidence level directly in the XML.</span></span></li></p>
<p><li><span data-ttu-id="f57d3-128">キーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-128">Add key words.</span></span></li></p>
<p><li><span data-ttu-id="f57d3-129">キーワードの近接性要件を調整します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-129">Adjust the proximity requirements for keywords.</span></span></li></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="f57d3-130">2. キーワード クエリ言語 (KQL) を使用して環境内で追加の個人データを検索する</span><span class="sxs-lookup"><span data-stu-id="f57d3-130">2. Use Keyword Query Language (KQL) to find additional personal data in your environment</span></span></p></td>
<td align="left"><p><span data-ttu-id="f57d3-131">機密情報の種類に含まれていないデータを検索するには、KQL クエリ言語を使用してカスタム クエリを開発します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-131">To find data not included in sensitive information types, use the KQL query language to develop custom queries.</span></span></p>
<p><span data-ttu-id="f57d3-132">これらの検索の結果をテストし、期待どおりの結果が得られるまで、KQL クエリ文字列を調整します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-132">Test the results of these searches and adjust the KQL query string until you achieve the expected result.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="f57d3-133">3. KQL クエリを使用して新しいカスタムの機密情報の種類を作成する</span><span class="sxs-lookup"><span data-stu-id="f57d3-133">3. Create new custom sensitive information types using the KQL queries</span></span></p></td>
<td align="left"><span data-ttu-id="f57d3-p104">KQL クエリを最適化して対象のデータを検索した後、これらのクエリを使用して新しいカスタムの機密情報の種類を作成します。次に、これらカスタムの機密情報の種類を、DLP ポリシーやその他のツール、およびその他の KQL クエリ内でのコンテンツ検索に使用します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p104">After optimizing KQL queries to find target data, create new custom sensitive information types using these queries. You can then use these custom sensitive information types with Content Search, in DLP policies and other tools, and within other KQL queries.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f57d3-p105">近日公開: セキュリティ/コンプライアンス センターの新しいユーザー インターフェイスで、機密情報の種類を作成および変更できるようになります。一致した結果を動的に参照し、機密情報の種類をニーズに合わせて調整することができます。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p105">Coming soon — You'll be able to create and modify sensitive information types in a new user interface in the Security and Compliance Center. You can dynamically see matching results and tune sensitive information types to meet your needs.</span></span>

## <a name="search-for-sensitive-information-types-using-content-search"></a><span data-ttu-id="f57d3-138">コンテンツ検索を使用した機密情報の種類の検索</span><span class="sxs-lookup"><span data-stu-id="f57d3-138">Search for sensitive information types using Content Search</span></span>

<span data-ttu-id="f57d3-p106">Office 365 に含まれている機密情報の種類を使用して個人データの検索を開始します。これらはセキュリティ/コンプライアンス センターの [分類] の下にリストされています。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p106">Begin searching for personal data by using the sensitive information types that are included with Office 365. These are listed in the Security and Compliance Center under Classification.</span></span>

<span data-ttu-id="f57d3-p107">このトピックには、欧州連合の市民に適用される現在の機密情報の種類がリストされています。これらを開始点として、セキュリティ/コンプライアンス センターで GDPR 準拠を支える新しい追加事項がないか頻繁にチェックしてください。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p107">This topic includes a list of current sensitive information types that apply to citizens in the European Union. Use these as a starting point. Check Security and Compliance Center frequently for new additions that can help with GDPR compliance.</span></span>

<span data-ttu-id="f57d3-144">また次の記事も参照してください: [機密情報の種類と、それぞれの検索対象の一覧](https://support.office.com/ja-JP/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b)</span><span class="sxs-lookup"><span data-stu-id="f57d3-144">Also see this article: [List of sensitive information types and what each one looks for](https://support.office.com/ja-JP/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b).</span></span>

<span data-ttu-id="f57d3-p108">機密情報の種類は、自動化されたプロセスが銀行口座番号、健康保険番号、クレジット カード番号などの特定の情報の種類を認識できる方法を定義します。機密情報の種類は条件とも呼ばれます。機密情報の種類はパターンで定義され、正規表現または関数で識別できます。機密情報の種類はさらに、キーワードやチェックサムなどの確証的な証拠を使用して識別することもできます。また、評価プロセスでは信頼度や近接度も使用されます。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p108">Sensitive information types define how the automated process recognizes specific information types such as bank account numbers, health service numbers, and credit card numbers. Sensitive information types are also referred to as conditions. A sensitive information type is defined by a pattern that can be identified by a regular expression or a function. In addition, corroborative evidence such as keywords and checksums can be used to identify a sensitive information type. Confidence level and proximity are also used in the evaluation process.</span></span>

<span data-ttu-id="f57d3-150">現時点では、メールボックス内に保管中のデータ検索には機密情報の種類を使用できません。</span><span class="sxs-lookup"><span data-stu-id="f57d3-150">At this time sensitive information types cannot be used to find data at rest in mailboxes.</span></span>

### <a name="using-content-search-with-sensitive-information-types"></a><span data-ttu-id="f57d3-151">機密情報の種類によるコンテンツ検索の使用</span><span class="sxs-lookup"><span data-stu-id="f57d3-151">Using Content Search with sensitive information types</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f57d3-152"><strong>手順</strong></span><span class="sxs-lookup"><span data-stu-id="f57d3-152"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="f57d3-153"><strong>詳細情報</strong></span><span class="sxs-lookup"><span data-stu-id="f57d3-153"><strong>More information</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd"><td align="left"><p><span data-ttu-id="f57d3-154">セキュリティ/コンプライアンス センターでコンテンツ検索に進む</span><span class="sxs-lookup"><span data-stu-id="f57d3-154">Go to Content Search in the Security and Compliance Center</span></span></p></td>
<td align="left"><p><span data-ttu-id="f57d3-155">セキュリティ/コンプライアンス センターの左側のウィンドウで、**[検索と調査]** &gt; **[コンテンツ検索]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="f57d3-155">In the left pane of the Security &amp; Compliance Center, click **Search &amp; investigation** &gt; **Content search**.</span></span></p>
<p><span data-ttu-id="f57d3-156">「<a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">Office 365 のセキュリティ/コンプライアンス センターでコンテンツ検索を実行する</a>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f57d3-156">See <a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">Run a Content Search in the Office 365 Security &amp; Compliance Center</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="f57d3-157">それぞれの機密情報の種類に新しい検索項目を作成する</span><span class="sxs-lookup"><span data-stu-id="f57d3-157">Create a new search item for each sensitive information type</span></span></p></td>
<td align="left"><p><span data-ttu-id="f57d3-158">次の構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="f57d3-158">Use the following syntax:</span></span></p>
<blockquote>
<p><span data-ttu-id="f57d3-159">SensitiveType:”&lt;type&gt;”</span><span class="sxs-lookup"><span data-stu-id="f57d3-159">SensitiveType:”&lt;type&gt;”</span></span></p>
</blockquote>
<p><span data-ttu-id="f57d3-160">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-160">For example:</span></span></p>
<blockquote>
<p><span data-ttu-id="f57d3-161">SensitiveType:&quot;France Passport Number&quot;</span><span class="sxs-lookup"><span data-stu-id="f57d3-161">SensitiveType:&quot;France Passport Number&quot;</span></span></p>
</blockquote>
<p><span data-ttu-id="f57d3-p109">SharePoint (OneDrive for Business を含む) に、検索の範囲を指定します。構文が完全に一致し、余分なスペースや入力ミスがないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p109">Scope the search to SharePoint (includes OneDrive for Business). Make sure the syntax is exact and there are no extra spaces or typos.</span></span></p>
<p><span data-ttu-id="f57d3-164">「<a href="https://support.office.com/ja-JP/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">サイトに保存された機密データを検索するクエリの形成</a>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f57d3-164">See <a href="https://support.office.com/ja-JP/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">Form a query to find sensitive data stored on sites</a>.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="f57d3-165">各検索の結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-165">Review the results for each search</span></span></p></td>
<td align="left"><p><span data-ttu-id="f57d3-166">次のような種類の問題を確認して、クエリの精度が正確かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="f57d3-166">Look for these types of issues to determine if the query accuracy is on target:</span></span></p>
<p><li><span data-ttu-id="f57d3-167">誤検知が多い</span><span class="sxs-lookup"><span data-stu-id="f57d3-167">Many false positives</span></span></li></p>
<p><li><span data-ttu-id="f57d3-168">データの既知のインスタンスがない</span><span class="sxs-lookup"><span data-stu-id="f57d3-168">Missing known instances of data</span></span></li></p>
<p><span data-ttu-id="f57d3-169">「<a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">Office 365 セキュリティ/コンプライアンス センターの検索結果をエクスポートする</a>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f57d3-169">See <a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">Export Content Search results from the Office 365 Security &amp; Compliance Center</a>.</span></span></p>
<p><span data-ttu-id="f57d3-170">注: Mozilla Firefox または Chrome を使用している場合、最初に Internet Explorer または Edge を使用してレポートをダウンロードし、必要なアドオンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f57d3-170">Note: if you’re using Mozilla Firefox or Chrome, you might need to first download reports using Internet Explorer or Edge in order to install the required add-in.</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="sensitive-information-types-for-eu-citizen-data"></a><span data-ttu-id="f57d3-171">EU 市民データのための機密情報の種類</span><span class="sxs-lookup"><span data-stu-id="f57d3-171">Sensitive information types for EU citizen data</span></span>

<span data-ttu-id="f57d3-p110">次のような機密情報の種類から開始します。EU 加盟国の個人データについては、その他にも多数の機密情報の種類が近日公開されます。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p110">Start with these sensitive information types. Many more sensitive information types are coming soon for personal data in EU countries.</span></span>

> <span data-ttu-id="f57d3-174">ベルギーの国民番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-174">Belgium National Number</span></span>
>
> <span data-ttu-id="f57d3-175">クレジット カード番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-175">Credit Card Number</span></span>
>
> <span data-ttu-id="f57d3-176">クロアチアの身分証明書番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-176">Croatia Identity Card Number</span></span>
>
> <span data-ttu-id="f57d3-177">クロアチアの個人識別 (OIB) 番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-177">Croatia Personal Identification (OIB) Number</span></span>
>
> <span data-ttu-id="f57d3-178">チェコの国民身分証明書番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-178">Czech National Identity Card Number</span></span>
>
> <span data-ttu-id="f57d3-179">デンマークの個人識別番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-179">Denmark Personal Identification Number</span></span>
>
> <span data-ttu-id="f57d3-180">欧州連合のデビット カード番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-180">EU Debit Card Number</span></span>
>
> <span data-ttu-id="f57d3-181">フィンランドの国民 ID</span><span class="sxs-lookup"><span data-stu-id="f57d3-181">Finland National ID</span></span>
>
> <span data-ttu-id="f57d3-182">フィンランドのパスポート番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-182">Finland Passport Number</span></span>
>
> <span data-ttu-id="f57d3-183">フランスの運転免許証番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-183">France Driver's License Number</span></span>
>
> <span data-ttu-id="f57d3-184">フランスの国民識別カード (CNI)</span><span class="sxs-lookup"><span data-stu-id="f57d3-184">France National ID Card (CNI)</span></span>
>
> <span data-ttu-id="f57d3-185">フランスのパスポート番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-185">France Passport Number</span></span>
>
> <span data-ttu-id="f57d3-186">フランスの社会保障番号 (INSEE)</span><span class="sxs-lookup"><span data-stu-id="f57d3-186">France Social Security Number (INSEE)</span></span>
>
> <span data-ttu-id="f57d3-187">ドイツの運転免許証番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-187">German Driver’s License Number</span></span>
>
> <span data-ttu-id="f57d3-188">ドイツの身分証明書番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-188">Germany Identity Card Number</span></span>
>
> <span data-ttu-id="f57d3-189">ドイツのパスポート番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-189">German Passport Number</span></span>
>
> <span data-ttu-id="f57d3-190">ギリシャの国民識別カード</span><span class="sxs-lookup"><span data-stu-id="f57d3-190">Greece National ID Card</span></span>
>
> <span data-ttu-id="f57d3-191">国際銀行口座番号 (IBAN)</span><span class="sxs-lookup"><span data-stu-id="f57d3-191">International Banking Account Number (IBAN)</span></span>
>
> <span data-ttu-id="f57d3-192">IP アドレス</span><span class="sxs-lookup"><span data-stu-id="f57d3-192">IP Address</span></span>
>
> <span data-ttu-id="f57d3-193">アイルランドの個人公共サービス (PPS) 番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-193">Ireland Personal Public Service (PPS) Number</span></span>
>
> <span data-ttu-id="f57d3-194">イタリアの運転免許証番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-194">Italy’s Driver’s License Number</span></span>
>
> <span data-ttu-id="f57d3-195">オランダの市民サービス (BSN) 番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-195">Netherlands Citizen’s Service (BSN) Number</span></span>
>
> <span data-ttu-id="f57d3-196">ノルウェーの識別番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-196">Norway Identity Number</span></span>
>
> <span data-ttu-id="f57d3-197">ポーランドの ID カード</span><span class="sxs-lookup"><span data-stu-id="f57d3-197">Poland Identity Card</span></span>
>
> <span data-ttu-id="f57d3-198">ポーランドの国民 ID (PESEL)</span><span class="sxs-lookup"><span data-stu-id="f57d3-198">Poland National ID (PESEL)</span></span>
>
> <span data-ttu-id="f57d3-199">ポーランドのパスポート</span><span class="sxs-lookup"><span data-stu-id="f57d3-199">Poland Passport</span></span>
>
> <span data-ttu-id="f57d3-200">ポルトガルの市民カード番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-200">Portugal Citizen Card Number</span></span>
>
> <span data-ttu-id="f57d3-201">スペインの社会保障番号 (SSN)</span><span class="sxs-lookup"><span data-stu-id="f57d3-201">Spain Social Security Number (SSN)</span></span>
>
> <span data-ttu-id="f57d3-202">スウェーデンの国民 ID</span><span class="sxs-lookup"><span data-stu-id="f57d3-202">Sweden National ID</span></span>
>
> <span data-ttu-id="f57d3-203">スウェーデンのパスポート番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-203">Sweden Passport Number</span></span>
>
> <span data-ttu-id="f57d3-p111">英国の運転免許証番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-p111">U.K. Driver’s License Number</span></span>
>
> <span data-ttu-id="f57d3-p112">英国の選挙登録番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-p112">U.K. Electoral Roll Number</span></span>
>
> <span data-ttu-id="f57d3-p113">英国の国民健康保険番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-p113">U.K. National Health Service Number</span></span>
>
> <span data-ttu-id="f57d3-p114">英国の国民保険番号 (NINO)</span><span class="sxs-lookup"><span data-stu-id="f57d3-p114">U.K. National Insurance Number (NINO)</span></span>
>
> <span data-ttu-id="f57d3-p115">米国/英国のパスポート番号</span><span class="sxs-lookup"><span data-stu-id="f57d3-p115">U.S./U.K. Passport Number</span></span>

## <a name="add-parameters-to-a-sensitive-information-type-query-to-hone-the-results"></a><span data-ttu-id="f57d3-214">機密情報の種類クエリにパラメーターを追加して、結果の精度を上げます。</span><span class="sxs-lookup"><span data-stu-id="f57d3-214">Add parameters to a sensitive information type query to hone the results</span></span>

<span data-ttu-id="f57d3-215">次のパラメーターを機密情報の種類クエリに追加できます。</span><span class="sxs-lookup"><span data-stu-id="f57d3-215">You can add these parameters to a sensitive information type query:</span></span>

-   <span data-ttu-id="f57d3-216">カウント範囲: 定義した数の機密情報がドキュメント内に出現した場合にそのドキュメントをクエリ結果に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f57d3-216">Count range — define the number of occurrences of sensitive information a document needs to contain before it’s included in the query results.</span></span>

-   <span data-ttu-id="f57d3-217">信頼範囲: 85 (85%) など、検出された機密情報の種類が満たすべき信頼レベルです。</span><span class="sxs-lookup"><span data-stu-id="f57d3-217">Confidence range — the level of confidence that the detected sensitive type is actually a match, such as 85 (85%).</span></span>

<span data-ttu-id="f57d3-218">構文:</span><span class="sxs-lookup"><span data-stu-id="f57d3-218">Syntax:</span></span>

-   <span data-ttu-id="f57d3-219">SensitiveType:”\<種類\>|\<カウント範囲\>|\<信頼範囲\>”</span><span class="sxs-lookup"><span data-stu-id="f57d3-219">SensitiveType:”\<type\>|\<count range\>|\<confidence range\>”</span></span>

<span data-ttu-id="f57d3-220">例:</span><span class="sxs-lookup"><span data-stu-id="f57d3-220">Examples:</span></span>

-   <span data-ttu-id="f57d3-221">SensitiveType:“Credit Card Number|5” (5 つのクレジット カード番号を持つドキュメントのみを返します)</span><span class="sxs-lookup"><span data-stu-id="f57d3-221">SensitiveType:“Credit Card Number|5” (return only documents that contain exactly five credit card numbers)</span></span>

-   <span data-ttu-id="f57d3-p116">SensitiveType:“Credit Card Number|\*|85..” (信頼範囲が 85% 以上)</span><span class="sxs-lookup"><span data-stu-id="f57d3-p116">SensitiveType:“Credit Card Number|\*|85..” (confidence range is 85 percent or higher)</span></span>

<span data-ttu-id="f57d3-224">注: "SensitiveType" は大文字と小文字を区別しますが、クエリの残りの部分では区別しません。</span><span class="sxs-lookup"><span data-stu-id="f57d3-224">Note: “SensitiveType” is case sensitive, but the rest of the query is not.</span></span>

<span data-ttu-id="f57d3-p117">プロパティと演算子を使用してクエリを調整する方法を示すこともできます。詳細とその他の例については、「[サイトに保存された機密データを検索するクエリの形成](https://support.office.com/ja-JP/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f57d3-p117">You can also use properties, and operators to illustrate how you can refine your queries. For more information and examples, see [Form a query to find sensitive data stored on sites](https://support.office.com/ja-JP/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836).</span></span>
