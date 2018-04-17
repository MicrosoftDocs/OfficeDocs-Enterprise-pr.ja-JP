---
title: 機密情報の種類をカスタマイズまたは新規作成する
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
ms.custom: ''
ms.assetid: ''
description: GDPR のための Office 365 の機密情報の種類を変更または新規作成する方法について説明します。
ms.openlocfilehash: 17158dc3de7672e57ff84bc1dab24e844a15f43b
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="customize-or-create-a-new-sensitive-information-type"></a><span data-ttu-id="cbee4-103">機密情報の種類をカスタマイズまたは新規作成する</span><span class="sxs-lookup"><span data-stu-id="cbee4-103">Customize or create a new sensitive information type</span></span>

<span data-ttu-id="cbee4-104">この記事では、GDPR のための Office 365 の機密情報の種類を変更または新規作成する方法を説明する 3 つの例を示します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-104">This article provides three examples to demonstrate how to modify or create new Office 365 sensitive information types for GDPR.</span></span>

-   <span data-ttu-id="cbee4-105">既存の機密情報の種類を変更する — EU のデビット カード番号</span><span class="sxs-lookup"><span data-stu-id="cbee4-105">Modify an existing sensitive information type — EU Debit Card Number</span></span>

-   <span data-ttu-id="cbee4-106">新しい機密情報の種類を作成する — 電子メール アドレス</span><span class="sxs-lookup"><span data-stu-id="cbee4-106">Create a new sensitive information type — email address</span></span>

-   <span data-ttu-id="cbee4-107">XML ファイルの例で、新しい機密情報の種類を作成する — Contoso 顧客番号</span><span class="sxs-lookup"><span data-stu-id="cbee4-107">Create a new sensitive information type with example XML file — Contoso customer number</span></span>

<span data-ttu-id="cbee4-108">以下も参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbee4-108">Also see:</span></span>

-   [<span data-ttu-id="cbee4-109">カスタムの機密情報の種類を作成する</span><span class="sxs-lookup"><span data-stu-id="cbee4-109">Create a custom sensitive information type</span></span>](https://support.office.com/ja-JP/article/Create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30)

-   [<span data-ttu-id="cbee4-110">組み込みの機密情報の種類をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="cbee4-110">Customize a built-in sensitive information type </span></span>](https://support.office.com/ja-JP/article/Customize-a-built-in-sensitive-information-type-2164ce3d-4d64-4283-b6b1-b81fbe835e8e)

## <a name="modify-a-sensitive-information-type-to-improve-accuracy"></a><span data-ttu-id="cbee4-111">機密情報の種類を変更して精度を向上させる</span><span class="sxs-lookup"><span data-stu-id="cbee4-111">Modify a sensitive information type to improve accuracy</span></span>

<span data-ttu-id="cbee4-112">機密情報の種類を使った個人データの検索にコンテンツ検索を使うと、予想した結果が返されない場合、またはクエリにより返される誤検知が多すぎる場合は、ご利用の環境でのパフォーマンス向上のために、機密情報の種類を変更することをご検討ください。</span><span class="sxs-lookup"><span data-stu-id="cbee4-112">If you’re using Content Search to search for personal data using sensitive information types and you’re not returning the expected results, or the query returns too many false positives, consider modifying the sensitive information type to work better with your environment.</span></span>

<span data-ttu-id="cbee4-p101">機密情報の種類を作成またはカスタマイズする場合のベスト プラクティスは、既存の機密情報の種類に基づいて新しい種類を作成することです。たとえば、"EU のデビット カード番号" の機密情報の種類のパラメーターを調整する場合、そのルールのコピーに "EU のデビットカード拡張版" という名前を付けて元のルールと区別できます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p101">The best practice when creating or customizing a sensitive information type is to create a new sensitive information type based on an existing one, giving it a unique name and identifiers. For example, if you wish to adjust the parameters of the “EU Debit Card Number” sensitive information type, you could name your copy of that rule “EU Debit Card Enhanced” to distinguish it from the original.</span></span>

<span data-ttu-id="cbee4-p102">新しい機密情報の種類で、精度を向上させるために変えたい値をそのまま変更します。完了したら、新しい機密情報の種類をアップロードし、新しい DLP ルールを作成 (または既存のルールを変更) すると、追加したばかりの新しい機密情報の種類を使用できるようになります。機密情報の種類の精度を変更するには、何度も試行錯誤をすることが必要になる場合があるため、元の種類のコピーをとっておくと、あとで必要に応じて戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p102">In your new sensitive information type, simply modify the values you wish to change to improve its accuracy. Once complete, upload your new sensitive information type and create a new DLP rule (or modify an existing one) to use the new sensitive information type you just added. Modifying the accuracy of sensitive information types might require some trial and error, so maintaining a copy of the original type allows you to fall back to it if required in the future.</span></span>

<span data-ttu-id="cbee4-118">機密情報の種類をカスタマイズする方法</span><span class="sxs-lookup"><span data-stu-id="cbee4-118">To customize a sensitive information type:</span></span>

1.  <span data-ttu-id="cbee4-119">Office 365 で、組み込みの機密情報の種類である既存の Microsoft Rule Package をエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="cbee4-119">Export the existing Microsoft Rule Package of built in sensitive information types in Office 365.</span></span>

2.  <span data-ttu-id="cbee4-120">この XML ファイルの名前を変更して、好みの XML エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-120">Rename this XML file and open it in your favorite XML editor.</span></span>

3.  <span data-ttu-id="cbee4-121">機密情報の種類を特定し、それ以外の種類をすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-121">Isolate the sensitive information type and remove all others.</span></span>

4.  <span data-ttu-id="cbee4-122">PowerShell を使用して、変更する機密情報の種類のために新しい GUID を 2 つ生成します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-122">Use PowerShell to generate two new GUIDs for the sensitive information type you are modifying.</span></span>

5.  <span data-ttu-id="cbee4-123">機密情報の種類が一意になるように、ID とその他の基本的な要素を変更します (これには 2 つの GUID を新たに生成した GUID に置き換えることが含まれます)。</span><span class="sxs-lookup"><span data-stu-id="cbee4-123">Modify the ID and other basic elements so the sensitive information type is unique (this includes replacing two GUIDs with the new ones you generated).</span></span>

6.  <span data-ttu-id="cbee4-124">精度を向上させるために、合致要件を調整します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-124">Tune the match requirements to improve accuracy.</span></span>

    1.  <span data-ttu-id="cbee4-125">近接度の変更 — 文字パターンの近接度を変更して、精密情報の種類の近くにあるキーワードを見つけるべき範囲を拡大または縮小します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-125">Proximity modifications — Modify the character pattern proximity to expand or shrink the window in which keywords must be found around the sensitive information type.</span></span>

    2.  <span data-ttu-id="cbee4-p103">このルールに一致するものが見つかった場合に通知できるように、検索対象に関してより詳細な補強証拠を提供するため、\<Keywords\> 要素のいずれか 1 つにキーワードを追加します。または、誤検知を引き起こしているキーワードを削除します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p103">Keyword modifications — Add keywords to one of the \<Keywords\> element in order to provide our sensitive information type more specific corroborative evidence to search for in order to signal a match on this rule. Or remove keywords that are causing false positives.</span></span>

    3.  <span data-ttu-id="cbee4-128">信頼度の変更 — 一致するものが見つかった場合の通知や報告をする前に、機密情報の種類において、定義に指定された条件と一致する必要のある信頼度を変更します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-128">Confidence modifications — Modify the confidence with which the sensitive information type must match the criteria specified in its definition before a match is signaled and reported.</span></span>

7.  <span data-ttu-id="cbee4-129">新しい機密情報の種類をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="cbee4-129">Upload the new sensitive information type.</span></span>

8.  <span data-ttu-id="cbee4-p104">機密情報を識別するため、コンテンツを再クロールします。「[サイトのクロールとインデックス再作成を手動で要求する](https://support.office.com/ja-JP/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p104">Recrawl your content to identify the sensitive information. See [Manually request crawling and re-indexing of a site](https://support.office.com/ja-JP/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E).</span></span>

## <a name="example-modify-the-eu-debit-card-number-sensitive-information-type"></a><span data-ttu-id="cbee4-132">例: "EU のデビット カード番号" の機密情報の種類の変更</span><span class="sxs-lookup"><span data-stu-id="cbee4-132">Example: modify the ‘EU Debit Card Number’ sensitive information type</span></span>

<span data-ttu-id="cbee4-p105">任意のシステムにおける DLP ルールの精度を向上するには、サンプル データ セットに対するテストが必要です。また、変更とテストを繰り返して微調整する必要があるかもしれません。この例では、"EU のデビット カード番号" の機密情報の種類を変更して、精度を向上する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p105">Improving the accuracy of DLP rules in any system requires testing against a sample data set, and may require fine tuning through repetitive modifications and tests. This example demonstrates modifications to the ‘EU Debit Card Number’ sensitive information type to improve its accuracy.</span></span>

<span data-ttu-id="cbee4-p106">例の中で EU のデビット カード番号を検索するときの番号の定義は、複雑なパターンを使っており、チェックサムの検証の対象に指定されている 16 桁の数字として厳密に定義されます。この機密情報の種類の文字列の定義により、このパターンを変更することはできません。ただし、以下の調整を行うことで、Office 365 DLP が Office 365 でこの機密情報の種類を見つける精度を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p106">When searching for an EU Debit Card Number in our example, the definition of that number is strictly defined as 16 digits using a complex pattern, and being subject to the validation of a checksum. We cannot alter this pattern due to the string definition of this sensitive information type. However, we can make the following adjustments to improve the accuracy of how Office 365 DLP finds this sensitive information type within Office 365.</span></span>

### <a name="proximity-modification"></a><span data-ttu-id="cbee4-138">近接度の変更</span><span class="sxs-lookup"><span data-stu-id="cbee4-138">Proximity modification</span></span>

<span data-ttu-id="cbee4-p107">\<Entity\> 要素の patternProximity 値を 300 から 150 文字に変更して範囲を縮小します。つまり、このルールで一致を通知するには、補強証拠またはキーワードが機密情報の種類により近くなければいけない、ということになります。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p107">We'll shrink the window by modifying the patternProximity value in our \<Entity\> element from 300 to 150 characters. This means that our corroborative evidence, or our keywords, must be closer to our sensitive information type in order to signal a match on this rule.</span></span>

<span data-ttu-id="cbee4-141">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span><span class="sxs-lookup"><span data-stu-id="cbee4-141">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span></span>

### <a name="keyword-modifications"></a><span data-ttu-id="cbee4-142">キーワードの変更</span><span class="sxs-lookup"><span data-stu-id="cbee4-142">Keyword modifications</span></span>

<span data-ttu-id="cbee4-p108">一部のキーワードは誤検知を引き起こす可能性があります。そのため、キーワードの削除が必要かもしれません。この例でのキーワードは以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p108">Some keywords might cause false positives to occur. As a result you might want to remove keywords. Here are the keywords for this example::</span></span>

<span data-ttu-id="cbee4-146">\<Keyword id="Keyword\_card\_terms\_dict"\></span><span class="sxs-lookup"><span data-stu-id="cbee4-146">\<Keyword id="Keyword\_card\_terms\_dict"\></span></span>

<span data-ttu-id="cbee4-147">\<Group\></span><span class="sxs-lookup"><span data-stu-id="cbee4-147">\<Group\></span></span>

<span data-ttu-id="cbee4-148">\<Term\>corporate card\</Term\></span><span class="sxs-lookup"><span data-stu-id="cbee4-148">\<Term\>corporate card\</Term\></span></span>

<span data-ttu-id="cbee4-149">\<Term\>organization card\</Term\></span><span class="sxs-lookup"><span data-stu-id="cbee4-149">\<Term\>organization card\</Term\></span></span>

<span data-ttu-id="cbee4-150">\<Term\>acct nbr\</Term\></span><span class="sxs-lookup"><span data-stu-id="cbee4-150">\<Term\>acct nbr\</Term\></span></span>

<span data-ttu-id="cbee4-151">\<Term\>acct num\</Term\></span><span class="sxs-lookup"><span data-stu-id="cbee4-151">\<Term\>acct num\</Term\></span></span>

<span data-ttu-id="cbee4-152">\<Term\>acct no\</Term\></span><span class="sxs-lookup"><span data-stu-id="cbee4-152">\<Term\>acct no\</Term\></span></span>

<span data-ttu-id="cbee4-153">…</span><span class="sxs-lookup"><span data-stu-id="cbee4-153">…</span></span>

<span data-ttu-id="cbee4-154">\</Group\></span><span class="sxs-lookup"><span data-stu-id="cbee4-154">\</Group\></span></span>

<span data-ttu-id="cbee4-155">\</Keyword\></span><span class="sxs-lookup"><span data-stu-id="cbee4-155">\</Keyword\></span></span>

### <a name="confidence-modifications"></a><span data-ttu-id="cbee4-156">信頼度の変更</span><span class="sxs-lookup"><span data-stu-id="cbee4-156">Confidence modifications</span></span>

<span data-ttu-id="cbee4-p109">定義からキーワードを削除する場合、通常、この値を下げることにより、この機密情報の種類を見つけたことに対する信頼度を調整する必要があります。EU のデビット カード番号の種類の既定レベルは、85 です。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p109">If you remove keywords from the definition, you would typically want to adjust how confident you are that this sensitive information type was found by lowering this value. The default level for EU Debit Card Number type is 85.</span></span>

<span data-ttu-id="cbee4-159">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span><span class="sxs-lookup"><span data-stu-id="cbee4-159">\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\></span></span>

<span data-ttu-id="cbee4-160">\<Pattern confidenceLevel="85"\></span><span class="sxs-lookup"><span data-stu-id="cbee4-160">\<Pattern confidenceLevel="85"\></span></span>

<span data-ttu-id="cbee4-161">…</span><span class="sxs-lookup"><span data-stu-id="cbee4-161">…</span></span>

<span data-ttu-id="cbee4-162">\</Pattern\></span><span class="sxs-lookup"><span data-stu-id="cbee4-162">\</Pattern\></span></span>

<span data-ttu-id="cbee4-163">\</Entity\></span><span class="sxs-lookup"><span data-stu-id="cbee4-163">\</Entity\></span></span>

## <a name="create-a-new-custom-sensitive-information-type"></a><span data-ttu-id="cbee4-164">新しいカスタムの機密情報の種類を作成する</span><span class="sxs-lookup"><span data-stu-id="cbee4-164">Create a new custom sensitive information type</span></span>

<span data-ttu-id="cbee4-165">新しいカスタムの機密情報の種類を作成するには、まずコンテンツ検索を使って、以下を行います。</span><span class="sxs-lookup"><span data-stu-id="cbee4-165">To create a new custom sensitive information type, start by using Content Search to:</span></span>

-   <span data-ttu-id="cbee4-166">KQL クエリを最適化する</span><span class="sxs-lookup"><span data-stu-id="cbee4-166">Optimize a KQL query</span></span>

-   <span data-ttu-id="cbee4-167">最も有効なキーワードを確認する</span><span class="sxs-lookup"><span data-stu-id="cbee4-167">See which keywords are most useful</span></span>

<span data-ttu-id="cbee4-p110">これらの結果を使って新しい機密情報の種類を作成します。それから新しい機密情報の種類を、ご利用の環境で最適化します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p110">Use these results to create a new sensitive information type. Then optimize the new sensitive information type for your environment.</span></span>

<span data-ttu-id="cbee4-p111">注: EU 諸国では、間もなく個人データの新しい機密情報の種類が多数ご利用いただけるようになります。新しい機密情報の種類を作成する必要がある場合は、まずご利用の環境に合ったデータを対象にしてください。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p111">Note: Many new sensitive information types are coming soon for personal data in EU countries. If you need to create new sensitive information types, begin by targeting data that is custom to your environment.</span></span>

### <a name="step-1--use-kql-queries-and-key-words-to-find-additional-data-in-your-environment"></a><span data-ttu-id="cbee4-172">手順 1 — KQL クエリとキーワードを使用して、環境内の追加のデータを検索する</span><span class="sxs-lookup"><span data-stu-id="cbee4-172">Step 1 — Use KQL queries and key words to find additional data in your environment</span></span>

<span data-ttu-id="cbee4-p112">場合により、GDPR の対象となる個人データを検索するために追加のクエリを作成する必要があります。コンテンツ検索では、キーワード クエリ言語 (KQL) を使ってデータを検索します。ほとんどの機密データは、機密情報の種類を使わずに KQL だけで正確に検出することができません。そのため、コンテンツ検索を使って KQL 文字列のテストと最適化を行ってから、これらの文字列を使って新しい機密情報の種類を作成して調整することにより、精度を向上させることを目標にします。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p112">You might need to create additional queries to find personal data that is subject to GDPR. Content Search uses Keyword Query Language (KQL) to find data. Most sensitive data can’t be accurately detected using just KQL without sensitive information types. So the goal is to test and optimize KQL strings using Content Search and then use these to create and tune new sensitive information types where you can achieve even greater accuracy.</span></span>

<span data-ttu-id="cbee4-177">KQL を使ったクエリの生成と最適化を行うために使うリソース:</span><span class="sxs-lookup"><span data-stu-id="cbee4-177">Use these resources to formulate and optimize queries using KQL:</span></span>

-   [<span data-ttu-id="cbee4-178">キーワード クエリ言語 (KQL) 構文のリファレンス (DMC)</span><span class="sxs-lookup"><span data-stu-id="cbee4-178">Keyword Query Language (KQL) syntax reference (DMC)</span></span>](https://docs.microsoft.com/ja-JP/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

-   [<span data-ttu-id="cbee4-179">Office 365 セキュリティ/コンプライアンス センターでコンテンツ検索を実行する</span><span class="sxs-lookup"><span data-stu-id="cbee4-179">Run a Content Search in the Office 365 Security & Compliance Center</span></span>](https://support.office.com/ja-JP/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) 

<span data-ttu-id="cbee4-p113">コンテンツ検索では、KQL クエリと機密情報の種類を開発するのに役立つ他のリソースとしてキーワードを使用できます。キーワードのリストを使用する理由は、各キーワードに一致する項目の数を示す統計を得ることができるからです。これにより、最も効果的 (および不適切) なキーワードをすばやく識別することができます。検索統計の詳細については、「[コンテンツ検索結果のキーワード統計の表示](https://support.office.com/ja-JP/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p113">Content Search provides another resource to help you develop KQL queries and sensitive information types — keywords. Why use the keyword list? You can get statistics that show how many items match each keyword. This can help you quickly identify which keywords are the most (and least) effective. For more information about search statistics, see [View keyword statistics for Content Search results](https://support.office.com/ja-JP/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04).</span></span>

<span data-ttu-id="cbee4-p114">各行のキーワードは、作成された検索クエリの OR 演算子によって結合されます。1 つの行でキーワード フレーズ (かっこで囲まれている) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p114">Keywords on each row are connected by the OR operator in the search query that's created. You can also use a keyword phrase (surrounded by parentheses) in a row.</span></span>

<span data-ttu-id="cbee4-187">詳細については、「[コンテンツ検索のキーワード クエリと検索条件](https://support.office.com/ja-JP/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbee4-187">For more information, see [Keyword queries and search conditions for Content Search](https://support.office.com/ja-JP/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3).</span></span>

### <a name="exampleusing-content-search-to-identify-email-addresses"></a><span data-ttu-id="cbee4-188">例—コンテンツ検索を使って電子メール アドレスを識別する</span><span class="sxs-lookup"><span data-stu-id="cbee4-188">Example—Using Content Search to identify email addresses</span></span>

<span data-ttu-id="cbee4-p115">電子メール アドレスは、データ主体に関連する機密情報と見なされます。これは、コンテンツ検索がどのように役立つかを示す簡単な例です。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p115">Email addresses are considered sensitive information related to data subjects. This is a simple example to demonstrate how Content Search can help.</span></span>

<span data-ttu-id="cbee4-p116">KQL とキーワードを組み合わせて使用することはできません。これらのツールは、別々に使用することで、クエリを洗練し、機密情報の種類で役立つキーワードを判断することができます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p116">KQL and keywords can’t be used together. Use these tools separately to hone your query and determine keywords that might be useful in sensitive information types.</span></span>

### <a name="kql-query"></a><span data-ttu-id="cbee4-193">KQL クエリ</span><span class="sxs-lookup"><span data-stu-id="cbee4-193">KQL query</span></span>

<span data-ttu-id="cbee4-194">(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)</span><span class="sxs-lookup"><span data-stu-id="cbee4-194">(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)</span></span>

<span data-ttu-id="cbee4-195">注:</span><span class="sxs-lookup"><span data-stu-id="cbee4-195">Notes:</span></span>

-   <span data-ttu-id="cbee4-196">近接検索には、NEAR と ONEAR を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-196">You can use NEAR and ONEAR for proximity searches.</span></span>

-   <span data-ttu-id="cbee4-197">残念ながら、KQL は Regex クラスのクエリをサポートしていません (例: IdRef="Regex\_email\_address")</span><span class="sxs-lookup"><span data-stu-id="cbee4-197">Unfortunately, KQL doesn’t support queries with the Regex Class (ex: IdRef="Regex\_email\_address")</span></span>

### <a name="keywords"></a><span data-ttu-id="cbee4-198">キーワード</span><span class="sxs-lookup"><span data-stu-id="cbee4-198">Keywords</span></span>

<span data-ttu-id="cbee4-p117">各キーワードを別々の行に入力します。キーワードの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p117">Enter each keyword on a separate line. Example keywords:</span></span>

-   <span data-ttu-id="cbee4-201">電子メール アドレス</span><span class="sxs-lookup"><span data-stu-id="cbee4-201">email address</span></span>

-   <span data-ttu-id="cbee4-202">メール</span><span class="sxs-lookup"><span data-stu-id="cbee4-202">mail</span></span>

-   <span data-ttu-id="cbee4-203">連絡先</span><span class="sxs-lookup"><span data-stu-id="cbee4-203">contact</span></span>

-   <span data-ttu-id="cbee4-204">送信者</span><span class="sxs-lookup"><span data-stu-id="cbee4-204">sender</span></span>

-   <span data-ttu-id="cbee4-205">受信者</span><span class="sxs-lookup"><span data-stu-id="cbee4-205">recipient</span></span>

-   <span data-ttu-id="cbee4-206">Cc</span><span class="sxs-lookup"><span data-stu-id="cbee4-206">cc</span></span>

-   <span data-ttu-id="cbee4-207">Bcc</span><span class="sxs-lookup"><span data-stu-id="cbee4-207">bcc</span></span>

<span data-ttu-id="cbee4-208">この例では、キーワードは必要ではなく、キーワードが誤検知の結果を多数生み出すことにお気付きになるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="cbee4-208">In this example, you might learn the keywords are not necessary and produce a lot of false positive results.</span></span>

### <a name="step-2--create-a-new-custom-sensitive-information-type"></a><span data-ttu-id="cbee4-209">手順 2 — 新しいカスタムの機密情報の種類を作成する</span><span class="sxs-lookup"><span data-stu-id="cbee4-209">Step 2 — Create a new custom sensitive information type</span></span>

<span data-ttu-id="cbee4-p118">KQL クエリとキーワードを使って機密情報を識別したら、これらを使って新しいカスタムの機密情報の種類を作成します。多くの場合、必要なレベルの精度を実現するには、機密情報の種類を洗練する必要があります。その後、DLP ポリシーとその他のツールおよび他の KQL クエリ内で、これらのカスタムの機密情報の種類をコンテンツ検索と一緒に使うことができます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p118">After using KQL queries and keywords to identify sensitive information, use these to create new custom sensitive information types. In many cases, you’ll require the sophistication of sensitive information types to achieve the right level of accuracy. You can then use these custom sensitive information types with Content Search, in DLP policies and other tools, and within other KQL queries.</span></span>

<span data-ttu-id="cbee4-p119">ベスト プラクティスは、既存の種類に基づいて新しい機密情報の種類を作成することです。この記事で前述したのと同じ手順を使います。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p119">The best practice is to create a new sensitive information type based on an existing one. Use the same process described earlier in this article.</span></span>

### <a name="example--create-a-new-sensitive-information-for-email-addresses"></a><span data-ttu-id="cbee4-215">例 — 電子メール アドレスの新しい機密情報の種類を作成する</span><span class="sxs-lookup"><span data-stu-id="cbee4-215">Example — Create a new sensitive information for email addresses</span></span> 

<span data-ttu-id="cbee4-p120">電子メール アドレスがシンプルなので、引き続きこれを例として使います。以下の表は、新しい電子メールの機密情報の種類に対して推奨される変更の詳細を示しています。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p120">We’ll continue with the email address as an example because it’s simple. The following table details the modifications recommended for a new email sensitive information type.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="cbee4-218"><strong>手順</strong></span><span class="sxs-lookup"><span data-stu-id="cbee4-218"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="cbee4-219"><strong>変更</strong></span><span class="sxs-lookup"><span data-stu-id="cbee4-219"><strong>Modification </strong></span></span></th>
<th align="left"><span data-ttu-id="cbee4-220"><strong>XML 構文の例</strong></span><span class="sxs-lookup"><span data-stu-id="cbee4-220"><strong>Example XML syntax</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="cbee4-221">1</span><span class="sxs-lookup"><span data-stu-id="cbee4-221">1</span></span></td>
<td align="left"><span data-ttu-id="cbee4-222">IdRef プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="cbee4-222">Set the IdRef property</span></span>
<p><span data-ttu-id="cbee4-p121">&lt;Entity&gt; 要素内で、&lt;IdMatch&gt; 要素の idRef プロパティが一意の値と同じになるように変更します。この値は電子メール アドレスを見つけるための正規表現を定義する要素をポイントします。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p121">Within the &lt;Entity&gt; element, modify the &lt;IdMatch&gt; element so that its idRef property is = to a unique value. This value will point to an element that defines our regular expression to find email addresses.</span></span></p></td>
<td align="left"><span data-ttu-id="cbee4-225">IdRef=&quot;Regex_email_address&quot;</span><span class="sxs-lookup"><span data-stu-id="cbee4-225">IdRef=&quot;Regex_email_address&quot;</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cbee4-226">2</span><span class="sxs-lookup"><span data-stu-id="cbee4-226">2</span></span></td>
<td align="left"><p><span data-ttu-id="cbee4-227">近接度属性</span><span class="sxs-lookup"><span data-stu-id="cbee4-227">Proximity attribute</span></span></p>
<p><span data-ttu-id="cbee4-228">まず &lt;Entity&gt; 要素の patternProximity 値を 300 にします。</span><span class="sxs-lookup"><span data-stu-id="cbee4-228">We'll start with a patternProximity value in our &lt;Entity&gt; element of 300.</span></span></p></td>
<td align="left"><span data-ttu-id="cbee4-229">patternsProximity=&quot;300&quot;</span><span class="sxs-lookup"><span data-stu-id="cbee4-229">patternsProximity=&quot;300&quot;</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cbee4-230">3</span><span class="sxs-lookup"><span data-stu-id="cbee4-230">3</span></span></td>
<td align="left"><p><span data-ttu-id="cbee4-231">信頼度</span><span class="sxs-lookup"><span data-stu-id="cbee4-231">Confidence level</span></span></p>
<p><span data-ttu-id="cbee4-p122">recommendedConfidence プロパティを、正確に一致するものを見つけるための信頼度を表していると感じる値に設定します。多くの場合、正確な結果を得るためには、典型的なデータ セットを使ってテストする必要があります。初期設定では、この値を 75 に設定します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p122">Set the recommendedConfidence property to a value you feel will represent the confidence of finding an accurate match. This will likely require testing with a representative data set to get an accurate result. As an initial setting, set this value to 75.</span></span></p></td>
<td align="left"><p><span data-ttu-id="cbee4-235">recommendedConfidence=&quot;75&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-235">recommendedConfidence=&quot;75&quot;&gt;</span></span></p>
<p><span data-ttu-id="cbee4-236">これら最初の 3 つの要素を結合した結果の XML は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="cbee4-236">The resulting XML for these first three elements combined looks like this:</span></span></p>
<p><span data-ttu-id="cbee4-237">&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-237">&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</span></span></p>
<p><span data-ttu-id="cbee4-238">&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-238">&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</span></span></p>
<p><span data-ttu-id="cbee4-239">&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-239">&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</span></span></p>
<p><span data-ttu-id="cbee4-240">&lt;Any minMatches=&quot;1&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-240">&lt;Any minMatches=&quot;1&quot;&gt;</span></span></p>
<p><span data-ttu-id="cbee4-241">&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-241">&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</span></span></p>
<p><span data-ttu-id="cbee4-242">&lt;/Any&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-242">&lt;/Any&gt;</span></span></p>
<p><span data-ttu-id="cbee4-243">&lt;/Pattern&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-243">&lt;/Pattern&gt;</span></span></p>
<p><span data-ttu-id="cbee4-244">&lt;/Entity&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-244">&lt;/Entity&gt;</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cbee4-245">4</span><span class="sxs-lookup"><span data-stu-id="cbee4-245">4</span></span></td>
<td align="left"><p><span data-ttu-id="cbee4-246">Regex 要素</span><span class="sxs-lookup"><span data-stu-id="cbee4-246">Regex element</span></span></p>
<p><span data-ttu-id="cbee4-247">新しい &lt;Regex&gt; 要素を、電子メール アドレスの識別に使う正規表現を定義する &lt;Entity&gt; 要素のすぐ下に追加します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-247">Add a new &lt;Regex&gt; element immediately be below the &lt;Entity&gt; elements that defines the regular expression used to identify email addresses.</span></span></p></td>
<td align="left"><span data-ttu-id="cbee4-248">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-248">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cbee4-249">5</span><span class="sxs-lookup"><span data-stu-id="cbee4-249">5</span></span></td>
<td align="left"><p><span data-ttu-id="cbee4-250">キーワード</span><span class="sxs-lookup"><span data-stu-id="cbee4-250">Keywords</span></span></p>
<p><span data-ttu-id="cbee4-p123">新しい &lt;Keyword&gt; 要素を、キーワードに関連する電子メール アドレスのリストを定義する &lt;Regex&gt; 要素の下に追加します。&lt;Keyword&gt; 要素の ID 値が、&lt;Entity&gt;&lt;Pattern&gt; 要素の &lt;Match idRef&gt; 値と一致していることをご確認ください。必要に応じて、キーワードをさらに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p123">Add a new &lt;Keyword&gt; element below the &lt;Regex&gt; element that defines list of email address related keywords. Ensure that the id value for the &lt;Keyword&gt; element matches the &lt;Match idRef&gt; value in the &lt;Entity&gt;&lt;Pattern&gt; element. You may continue to add your own keywords if needed.</span></span></p>
<p><span data-ttu-id="cbee4-p124">キーワードは、電子メールの機密情報の種類に必ずしも含める必要はありません。ここでは、例として示しています。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p124">Keywords are likely not necessary to include in an email sensitive information type. These are provided as an example.</span></span></p></td>
<td align="left"><p><span data-ttu-id="cbee4-256">&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-256">&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</span></span></p>
<p><span data-ttu-id="cbee4-257">&lt;Group&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-257">&lt;Group&gt;</span></span></p>
<p><span data-ttu-id="cbee4-258">&lt;Term&gt;email&lt;/Term&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-258">&lt;Term&gt;email&lt;/Term&gt;</span></span></p>
<p><span data-ttu-id="cbee4-259">&lt;Term&gt;email address&lt;/Term&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-259">&lt;Term&gt;email address&lt;/Term&gt;</span></span></p>
<p><span data-ttu-id="cbee4-260">&lt;Term&gt;contact&lt;/Term&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-260">&lt;Term&gt;contact&lt;/Term&gt;</span></span></p>
<p><span data-ttu-id="cbee4-261">&lt;/Group&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-261">&lt;/Group&gt;</span></span></p>
<p><span data-ttu-id="cbee4-262">&lt;/Keyword&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-262">&lt;/Keyword&gt;</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cbee4-263">6</span><span class="sxs-lookup"><span data-stu-id="cbee4-263">6</span></span></td>
<td align="left"><p><span data-ttu-id="cbee4-264">LocalizedStrings 要素</span><span class="sxs-lookup"><span data-stu-id="cbee4-264">LocalizedStrings element</span></span></p>
<p><span data-ttu-id="cbee4-265">&lt;LocalizedStrings&gt;&lt;Resource&gt; 要素に、自分の機密情報の種類を識別する一意の名前があることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cbee4-265">In the &lt;LocalizedStrings&gt;&lt;Resource&gt; element ensure that you have a unique name that identifies your sensitive information type.</span></span></p></td>
<td align="left"><p><span data-ttu-id="cbee4-266">&lt;LocalizedStrings&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-266">&lt;LocalizedStrings&gt;</span></span></p>
<p><span data-ttu-id="cbee4-267">&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-267">&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</span></span></p>
<p><span data-ttu-id="cbee4-268">&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-268">&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</span></span></p>
<p><span data-ttu-id="cbee4-269">&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-269">&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</span></span></p>
<p><span data-ttu-id="cbee4-270">&lt;/Resource&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-270">&lt;/Resource&gt;</span></span></p>
<p><span data-ttu-id="cbee4-271">&lt;/LocalizedStrings&gt;</span><span class="sxs-lookup"><span data-stu-id="cbee4-271">&lt;/LocalizedStrings&gt;</span></span></p></td>
</tr>
</tbody>
</table>

## <a name="create-a-new-sensitive-information-type-with-example-powershell-and-xml-file--contoso-customer-number"></a><span data-ttu-id="cbee4-272">例の PowerShell と XML ファイルで、新しい機密情報の種類を作成する — Contoso 顧客番号</span><span class="sxs-lookup"><span data-stu-id="cbee4-272">Create a new sensitive information type with example PowerShell and XML file — Contoso customer number</span></span>

<span data-ttu-id="cbee4-p125">Contoso は、Contoso 顧客番号 (CCN) を使って、顧客データベースから各顧客を識別します。CCN には以下の分類があります。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p125">Contoso uses a Contoso Customer Number (CCN) to identify each customer in their customer database. A CCN consists of the following taxonomy:</span></span>

-   <span data-ttu-id="cbee4-p126">記録が作られた年を表す 2 桁の数字。Contoso は 2002 年に設立されたので、使用可能な一番小さい値は 02 です。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p126">Two digits to represent the year that the record was created. Contoso was founded in 2002; therefore, the earliest possible value would be 02.</span></span>

-   <span data-ttu-id="cbee4-p127">記録を作成したパートナー代理店を表す 3 桁の数字。代理店の値として使用可能なのは、000 から 999 の範囲です。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p127">Three digits to represent the partner agency that created the record. Possible agency values range from 000 to 999.</span></span>

-   <span data-ttu-id="cbee4-p128">基幹業務を表す英字。使用可能な値は、a から z で、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p128">An alpha character to represent the line of business. Possible values are a-z and should be case insensitive.</span></span>

-   <span data-ttu-id="cbee4-p129">4 桁のシリアル番号。シリアル番号の値として使用可能なのは、0000 から 9999 の範囲です。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p129">A four-digit serial number. Possible serial number values range from 0000 to 9999.</span></span>

<span data-ttu-id="cbee4-283">CCN の例:</span><span class="sxs-lookup"><span data-stu-id="cbee4-283">Example CCNs:</span></span>

> <span data-ttu-id="cbee4-284">15080P9562</span><span class="sxs-lookup"><span data-stu-id="cbee4-284">15080P9562</span></span>
>
> <span data-ttu-id="cbee4-285">14040O1119</span><span class="sxs-lookup"><span data-stu-id="cbee4-285">14040O1119</span></span>
>
> <span data-ttu-id="cbee4-286">15020J8317</span><span class="sxs-lookup"><span data-stu-id="cbee4-286">15020J8317</span></span>
>
> <span data-ttu-id="cbee4-287">14050E2330</span><span class="sxs-lookup"><span data-stu-id="cbee4-287">14050E2330</span></span>
>
> <span data-ttu-id="cbee4-288">16050E2166</span><span class="sxs-lookup"><span data-stu-id="cbee4-288">16050E2166</span></span>
>
> <span data-ttu-id="cbee4-289">17040O1118</span><span class="sxs-lookup"><span data-stu-id="cbee4-289">17040O1118</span></span>

<span data-ttu-id="cbee4-290">Contoso は、内部対応、外部対応、ドキュメントなどで、常に CCN を使って顧客を参照しています。カスタムの機密情報の種類を作成して、Office 365 での CCN の使用を検出します。これにより、この形式の個人データの使用に対して、保護を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-290">Contoso always refers to customers by using a CCN in internal correspondence, external correspondence, documents, etc. They would like to create a custom sensitive information type to detect the use of CCN in Office 365 so that they may apply protection to the use of this form of personal data.</span></span>

### <a name="create-a-new-sensitive-information-type-for-contoso-customer-number"></a><span data-ttu-id="cbee4-291">Contoso 顧客番号に対して新しい機密情報の種類を作成する</span><span class="sxs-lookup"><span data-stu-id="cbee4-291">Create a new sensitive information type for Contoso customer number</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="cbee4-292"><strong>手順</strong></span><span class="sxs-lookup"><span data-stu-id="cbee4-292"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="cbee4-293"><strong>処理</strong></span><span class="sxs-lookup"><span data-stu-id="cbee4-293"><strong>Action </strong></span></span></th>
<th align="left"><span data-ttu-id="cbee4-294"><strong>結果</strong></span><span class="sxs-lookup"><span data-stu-id="cbee4-294"><strong>Result</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="cbee4-295">1</span><span class="sxs-lookup"><span data-stu-id="cbee4-295">1</span></span></td>
<td align="left"><span data-ttu-id="cbee4-296">Contoso は PowerShell とコンテンツ検索を使用して、CCN の一連の例に一致するドキュメントを検索します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-296">Contoso uses PowerShell and Content Search to find documents that match an example set of CCNs.</span></span></td>
<td align="left">

<p><span data-ttu-id="cbee4-297">#Office 365 セキュリティ/コンプライアンス センターに接続する</span><span class="sxs-lookup"><span data-stu-id="cbee4-297">#Connect to Office 365 Security &amp; Compliance Center</span></span></p>
<p><span data-ttu-id="cbee4-298">$adminUser = &quot;alland@contoso.com&quot;</span><span class="sxs-lookup"><span data-stu-id="cbee4-298">$adminUser = &quot;alland@contoso.com&quot;</span></span></p>
<p><span data-ttu-id="cbee4-299">Connect-IPPSSession -UserPrincipalName $adminUser</span><span class="sxs-lookup"><span data-stu-id="cbee4-299">Connect-IPPSSession -UserPrincipalName $adminUser</span></span></p>
<p><span data-ttu-id="cbee4-300">#サンプル データの検索を作成して開始する</span><span class="sxs-lookup"><span data-stu-id="cbee4-300">#Create &amp; start search for sample data</span></span></p>
<p><span data-ttu-id="cbee4-301">$searchName = &quot;Sample Customer Information Search&quot;</span><span class="sxs-lookup"><span data-stu-id="cbee4-301">$searchName = &quot;Sample Customer Information Search&quot;</span></span></p>
<p><span data-ttu-id="cbee4-302">$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</span><span class="sxs-lookup"><span data-stu-id="cbee4-302">$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</span></span></p>
<p><span data-ttu-id="cbee4-303">New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</span><span class="sxs-lookup"><span data-stu-id="cbee4-303">New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</span></span></p>
<p><span data-ttu-id="cbee4-304">Start-ComplianceSearch -Identity $searchName</span><span class="sxs-lookup"><span data-stu-id="cbee4-304">Start-ComplianceSearch -Identity $searchName</span></span></p>
</td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cbee4-305">2</span><span class="sxs-lookup"><span data-stu-id="cbee4-305">2</span></span></td>
<td align="left"><span data-ttu-id="cbee4-p130">Contoso は結果を分析します。CCN が使われるたびに、EU 形式の日付が使われ、次のキーワードのうちのいずれか 1 つも近接度 300 文字の中で使われます。</span><span class="sxs-lookup"><span data-stu-id="cbee4-p130">Contoso analyzes the results. Every time the CCN was used, an EU formatted date was used and one of these keywords were also used within a proximity of 300 characters.</span></span></td>
<td align="left"><span data-ttu-id="cbee4-308">customer number、customer no、customer #、customer#、Contoso customer</span><span class="sxs-lookup"><span data-stu-id="cbee4-308">customer number, customer no, customer #, customer#, Contoso customer</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cbee4-309">3</span><span class="sxs-lookup"><span data-stu-id="cbee4-309">3</span></span></td>
<td align="left"><span data-ttu-id="cbee4-310">Contoso は、CNN を識別するため、次の正規表現 (RegEx) パターンを開発しました。</span><span class="sxs-lookup"><span data-stu-id="cbee4-310">Contoso developed the following Regular Expression (RegEx) pattern to identify their CCN.</span></span></td>
<td align="left"><span data-ttu-id="cbee4-311">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</span><span class="sxs-lookup"><span data-stu-id="cbee4-311">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cbee4-312">4</span><span class="sxs-lookup"><span data-stu-id="cbee4-312">4</span></span></td>
<td align="left"><span data-ttu-id="cbee4-313">Contoso は、さまざまな子会社で使われる形式の EU の日付を識別するため、次の正規表現 (RegEx) パターンを開発しました。</span><span class="sxs-lookup"><span data-stu-id="cbee4-313">Contoso developed the following Regular Expression (RegEx) pattern to identify EU dates in the formats used by their various subsidiaries.</span></span></td>
<td align="left">
````xml
(0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?|‌ feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|‌ apr(ile|il)?|abr(il)?|avril|may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|‌ oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?|nov(ember|iembre|embre|embro)?|dec(ember)?|‌ dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}
````
</td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cbee4-314">5</span><span class="sxs-lookup"><span data-stu-id="cbee4-314">5</span></span></td>
<td align="left"><span data-ttu-id="cbee4-315">Contoso は、PowerShell を使用して、3 つの一意の GUID を生成します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-315">Contoso uses PowerShell to generate three unique GUIDs.</span></span></td>
<td align="left"><p><span data-ttu-id="cbee4-316">#RulePack ID、Publisher ID、Entity ID の一意の GUID を生成する</span><span class="sxs-lookup"><span data-stu-id="cbee4-316">#Generate a unique GUID for RulePack Id, Publisher Id, and Entity Id</span></span></p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cbee4-317">6</span><span class="sxs-lookup"><span data-stu-id="cbee4-317">6</span></span></td>
<td align="left"><span data-ttu-id="cbee4-318">Contoso は、機密項目の種類のルールに対して、次のパラメーターを定義しています。</span><span class="sxs-lookup"><span data-stu-id="cbee4-318">Contoso defines the following parameters for their sensitive item type rule.</span></span></td>
<td align="left"><p><span data-ttu-id="cbee4-319">名前: Contoso 顧客番号 (CCN)</span><span class="sxs-lookup"><span data-stu-id="cbee4-319">Name: Contoso Customer Number (CCN)</span></span></p>
<p><span data-ttu-id="cbee4-320">説明: 追加のキーワードと EU 形式の日付を検索する Contoso 顧客番号 (CCN)</span><span class="sxs-lookup"><span data-stu-id="cbee4-320">Description: Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="cbee4-321">7</span><span class="sxs-lookup"><span data-stu-id="cbee4-321">7</span></span></td>
<td align="left"><span data-ttu-id="cbee4-322">Contoso は、Contoso 顧客番号 (CCN) を検出するための新しい機密情報の種類の XML ファイルを作成し、これをローカル ファイル システムに C:\Scripts\ContosoCCN.xml として UTF-8 エンコードで保存します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-322">Contoso creates an XML file for a new sensitive information type to detect a Contoso Customer Number (CCN) and saves this to a local file system as C:\Scripts\ContosoCCN.xml in with UTF-8 encoding.</span></span></td>
<td align="left"><span data-ttu-id="cbee4-323">この表の下の XML ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbee4-323">See the XML file below this table.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="cbee4-324">8</span><span class="sxs-lookup"><span data-stu-id="cbee4-324">8</span></span></td>
<td align="left"><span data-ttu-id="cbee4-325">Contoso は、次の PowerShell でカスタムの機密情報の種類を作成します。</span><span class="sxs-lookup"><span data-stu-id="cbee4-325">Contoso creates the custom sensitive information type with the following PowerShell.</span></span></td>
<td align="left"><p><span data-ttu-id="cbee4-326">#Office 365 セキュリティ/コンプライアンス センターに接続する</span><span class="sxs-lookup"><span data-stu-id="cbee4-326">#Connect to Office 365 Security &amp; Compliance Center</span></span></p>
<p><span data-ttu-id="cbee4-327">$adminUser = &quot;alland@contoso.com&quot;</span><span class="sxs-lookup"><span data-stu-id="cbee4-327">$adminUser = &quot;alland@contoso.com&quot;</span></span></p>
<p><span data-ttu-id="cbee4-328">Connect-IPPSSession -UserPrincipalName $adminUser</span><span class="sxs-lookup"><span data-stu-id="cbee4-328">Connect-IPPSSession -UserPrincipalName $adminUser</span></span></p>
<p><span data-ttu-id="cbee4-329">#新しい機密情報の種類を作成する</span><span class="sxs-lookup"><span data-stu-id="cbee4-329">#Create new Sensitive Information Type</span></span></p>
<p><span data-ttu-id="cbee4-330">New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</span><span class="sxs-lookup"><span data-stu-id="cbee4-330">New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</span></span></p></td>
</tr>
</tbody>
</table>

### <a name="example-xml-file-for-the-new-sensitive-information-type-step-7"></a><span data-ttu-id="cbee4-331">新しい機密情報の種類のための XML ファイルの例 (手順 7)</span><span class="sxs-lookup"><span data-stu-id="cbee4-331">Example XML file for the new sensitive information type (step 7)</span></span>
```xml
\<?xml version="1.0" encoding="utf-8"?\>

\<RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce"\>

\<RulePack id="130ae63b-a91e-4a12-9e02-a90e36a83d7f"\>

\<Version major="1" minor="0" build="0" revision="0" /\>

\<Publisher id="47148982-defd-42a1-890a-7b9472099f1f" /\>

\<Details defaultLangCode="en"\>

\<LocalizedDetails langcode="en"\>

\<PublisherName\>Contoso Ltd.\</PublisherName\>

\<Name\>Contoso Rule Package\</Name\>

\<Description\>Defines Contoso's custom set of classification rules\</Description\>

\</LocalizedDetails\>

\</Details\>

\</RulePack\>

\<Rules\>

\<!-- Contoso Customer Number (CCN) --\>

\<Entity id="a91f9a2e-6cfc-4622-8c5d-954875aa5b2b" patternsProximity="300" recommendedConfidence="85"\>

\<Pattern confidenceLevel="85"\>

\<IdMatch idRef="Regex\_contoso\_ccn" /\>

\<Match idRef="Keyword\_contoso\_ccn" /\>

\<Match idRef="Regex\_eu\_date" /\>

\</Pattern\>

\</Entity\>

\<Regex id="Regex\_contoso\_ccn"\>[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}\</Regex\>

\<Keyword id="Keyword\_contoso\_ccn"\>

\<Group matchStyle="word"\>

\<Term caseSensitive="false"\>customer number\</Term\>

\<Term caseSensitive="false"\>customer no\</Term\>

\<Term caseSensitive="false"\>customer \#\</Term\>

\<Term caseSensitive="false"\>customer\#\</Term\>

\<Term caseSensitive="false"\>Contoso customer\</Term\>

\</Group\>

\</Keyword\>

\<Regex id="Regex\_eu\_date"\> (0?[1-9]|[12][0-9]|3[0-1])[\\/-](0?[1-9]|1[0-2]|j\\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?‌ |feb(ruary|ruari|rero|braio|ruar|br)?|f\\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\\x00e4rz|maart‌|apr(ile|il)?|abr(il)?|avril‌ |may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?‌ |nov(ember|iembre|embre|embro)?|dec(ember)?|dic(iembre|embre)?|dez(ember|embro)?|d\\x00e9c(embre)?)[ \\/-](19|20)?[0-9]{2}\</Regex\>

\<LocalizedStrings\>

\<Resource idRef="a91f9a2e-6cfc-4622-8c5d-954875aa5b2b"\>

\<Name default="true" langcode="en-us"\>Contoso Customer Number (CCN)\</Name\>

\<Description default="true" langcode="en-us"\>Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date\</Description\>

\</Resource\>

\</LocalizedStrings\>

\</Rules\>

\</RulePackage\>
```
