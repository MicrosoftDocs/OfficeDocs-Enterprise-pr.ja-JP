---
title: "機密情報の種類をカスタマイズまたは新規作成する"
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom:
- Strat_O365_Enterprise
- GDPR
ms.assetid: 
description: "GDPR のための Office 365 の機密情報の種類を変更または新規作成する方法について説明します。"
ms.openlocfilehash: 58bfce19d75a66fe36d3e61ec0b05bcca6913b85
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="customize-or-create-a-new-sensitive-information-type"></a>機密情報の種類をカスタマイズまたは新規作成する

この記事では、GDPR のための Office 365 の機密情報の種類を変更または新規作成する方法を説明する 3 つの例を示します。

-   既存の機密情報の種類を変更する — EU のデビット カード番号

-   新しい機密情報の種類を作成する — 電子メール アドレス

-   XML ファイルの例で、新しい機密情報の種類を作成する — Contoso 顧客番号

以下も参照してください。

-   [カスタムの機密情報の種類を作成する](https://support.office.com/ja-JP/article/Create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30)

-   [組み込みの機密情報の種類をカスタマイズする](https://support.office.com/ja-JP/article/Customize-a-built-in-sensitive-information-type-2164ce3d-4d64-4283-b6b1-b81fbe835e8e)

## <a name="modify-a-sensitive-information-type-to-improve-accuracy"></a>機密情報の種類を変更して精度を向上させる

機密情報の種類を使った個人データの検索にコンテンツ検索を使うと、予想した結果が返されない場合、またはクエリにより返される誤検知が多すぎる場合は、ご利用の環境でのパフォーマンス向上のために、機密情報の種類を変更することをご検討ください。

機密情報の種類を作成またはカスタマイズする場合のベスト プラクティスは、既存の機密情報の種類に基づいて新しい種類を作成することです。たとえば、"EU のデビット カード番号" の機密情報の種類のパラメーターを調整する場合、そのルールのコピーに "EU のデビットカード拡張版" という名前を付けて元のルールと区別できます。

新しい機密情報の種類で、精度を向上させるために変えたい値をそのまま変更します。完了したら、新しい機密情報の種類をアップロードし、新しい DLP ルールを作成 (または既存のルールを変更) すると、追加したばかりの新しい機密情報の種類を使用できるようになります。機密情報の種類の精度を変更するには、何度も試行錯誤をすることが必要になる場合があるため、元の種類のコピーをとっておくと、あとで必要に応じて戻すことができます。

機密情報の種類をカスタマイズする方法

1.  Office 365 で、組み込みの機密情報の種類である既存の Microsoft Rule Package をエクスポートします。

2.  この XML ファイルの名前を変更して、好みの XML エディターで開きます。

3.  機密情報の種類を特定し、それ以外の種類をすべて削除します。

4.  PowerShell を使用して、変更する機密情報の種類のために新しい GUID を 2 つ生成します。

5.  機密情報の種類が一意になるように、ID とその他の基本的な要素を変更します (これには 2 つの GUID を新たに生成した GUID に置き換えることが含まれます)。

6.  精度を向上させるために、合致要件を調整します。

    1.  近接度の変更 — 文字パターンの近接度を変更して、精密情報の種類の近くにあるキーワードを見つけるべき範囲を拡大または縮小します。

    2.  このルールに一致するものが見つかった場合に通知できるように、検索対象に関してより詳細な補強証拠を提供するため、\<Keywords\> 要素のいずれか 1 つにキーワードを追加します。または、誤検知を引き起こしているキーワードを削除します。

    3.  信頼度の変更 — 一致するものが見つかった場合の通知や報告をする前に、機密情報の種類において、定義に指定された条件と一致する必要のある信頼度を変更します。

7.  新しい機密情報の種類をアップロードします。

8.  機密情報を識別するため、コンテンツを再クロールします。「[サイトのクロールとインデックス再作成を手動で要求する](https://support.office.com/ja-JP/article/Manually-request-crawling-and-re-indexing-of-a-site-a-library-or-a-list-9AFA977D-39DE-4321-B4CA-8C7C7E6D264E)」を参照してください。

## <a name="example-modify-the-eu-debit-card-number-sensitive-information-type"></a>例: "EU のデビット カード番号" の機密情報の種類の変更

任意のシステムにおける DLP ルールの精度を向上するには、サンプル データ セットに対するテストが必要です。また、変更とテストを繰り返して微調整する必要があるかもしれません。この例では、"EU のデビット カード番号" の機密情報の種類を変更して、精度を向上する方法を示します。

例の中で EU のデビット カード番号を検索するときの番号の定義は、複雑なパターンを使っており、チェックサムの検証の対象に指定されている 16 桁の数字として厳密に定義されます。この機密情報の種類の文字列の定義により、このパターンを変更することはできません。ただし、以下の調整を行うことで、Office 365 DLP が Office 365 でこの機密情報の種類を見つける精度を向上させることができます。

### <a name="proximity-modification"></a>近接度の変更

\<Entity\> 要素の patternProximity 値を 300 から 150 文字に変更して範囲を縮小します。つまり、このルールで一致を通知するには、補強証拠またはキーワードが機密情報の種類により近くなければいけない、ということになります。

\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\>

### <a name="keyword-modifications"></a>キーワードの変更

一部のキーワードは誤検知を引き起こす可能性があります。そのため、キーワードの削除が必要かもしれません。この例でのキーワードは以下のとおりです。

\<Keyword id="Keyword\_card\_terms\_dict"\>

\<Group\>

\<Term\>corporate card\</Term\>

\<Term\>organization card\</Term\>

\<Term\>acct nbr\</Term\>

\<Term\>acct num\</Term\>

\<Term\>acct no\</Term\>

…

\</Group\>

\</Keyword\>

### <a name="confidence-modifications"></a>信頼度の変更

定義からキーワードを削除する場合、通常、この値を下げることにより、この機密情報の種類を見つけたことに対する信頼度を調整する必要があります。EU のデビット カード番号の種類の既定レベルは、85 です。

\<Entity id="48da7072-821e-4804-9fab-72ffb48f6f78" patternsProximity="150" recommendedConfidence="85"\>

\<Pattern confidenceLevel="85"\>

…

\</Pattern\>

\</Entity\>

## <a name="create-a-new-custom-sensitive-information-type"></a>新しいカスタムの機密情報の種類を作成する

新しいカスタムの機密情報の種類を作成するには、まずコンテンツ検索を使って、以下を行います。

-   KQL クエリを最適化する

-   最も有効なキーワードを確認する

これらの結果を使って新しい機密情報の種類を作成します。それから新しい機密情報の種類を、ご利用の環境で最適化します。

注: EU 諸国では、間もなく個人データの新しい機密情報の種類が多数ご利用いただけるようになります。新しい機密情報の種類を作成する必要がある場合は、まずご利用の環境に合ったデータを対象にしてください。

### <a name="step-1--use-kql-queries-and-key-words-to-find-additional-data-in-your-environment"></a>手順 1 — KQL クエリとキーワードを使用して、環境内の追加のデータを検索する

場合により、GDPR の対象となる個人データを検索するために追加のクエリを作成する必要があります。コンテンツ検索では、キーワード クエリ言語 (KQL) を使ってデータを検索します。ほとんどの機密データは、機密情報の種類を使わずに KQL だけで正確に検出することができません。そのため、コンテンツ検索を使って KQL 文字列のテストと最適化を行ってから、これらの文字列を使って新しい機密情報の種類を作成して調整することにより、精度を向上させることを目標にします。

KQL を使ったクエリの生成と最適化を行うために使うリソース:

-   [キーワード クエリ言語 (KQL) 構文のリファレンス (DMC)](https://docs.microsoft.com/ja-JP/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

-   [Office 365 セキュリティ/コンプライアンス センターでコンテンツ検索を実行する](https://support.office.com/ja-JP/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) 

コンテンツ検索では、KQL クエリと機密情報の種類を開発するのに役立つ他のリソースとしてキーワードを使用できます。キーワードのリストを使用する理由は、各キーワードに一致する項目の数を示す統計を得ることができるからです。これにより、最も効果的 (および不適切) なキーワードをすばやく識別することができます。検索統計の詳細については、「[コンテンツ検索結果のキーワード統計の表示](https://support.office.com/ja-JP/article/View-keyword-statistics-for-Content-Search-results-9701a024-c52e-43f0-b545-9a53478aec04)」を参照してください。

各行のキーワードは、作成された検索クエリの OR 演算子によって結合されます。1 つの行でキーワード フレーズ (かっこで囲まれている) を使用することもできます。

詳細については、「[コンテンツ検索のキーワード クエリと検索条件](https://support.office.com/ja-JP/article/Keyword-queries-and-search-conditions-for-Content-Search-c4639c2e-7223-4302-8e0d-b6e10f1c3be3)」を参照してください。

### <a name="exampleusing-content-search-to-identify-email-addresses"></a>例—コンテンツ検索を使って電子メール アドレスを識別する

電子メール アドレスは、データ主体に関連する機密情報と見なされます。これは、コンテンツ検索がどのように役立つかを示す簡単な例です。

KQL とキーワードを組み合わせて使用することはできません。これらのツールは、別々に使用することで、クエリを洗練し、機密情報の種類で役立つキーワードを判断することができます。

### <a name="kql-query"></a>KQL クエリ

(^|\\b)([a-zA-Z0-9\_\\-\\.]+)@([a-zA-Z0-9\_\\-\\.]+)\\.([a-zA-Z]{2,5})($|\\b)

注:

-   近接検索には、NEAR と ONEAR を使うことができます。

-   残念ながら、KQL は Regex クラスのクエリをサポートしていません (例: IdRef="Regex\_email\_address")

### <a name="keywords"></a>キーワード

各キーワードを別々の行に入力します。キーワードの例を以下に示します。

-   電子メール アドレス

-   メール

-   連絡先

-   送信者

-   受信者

-   Cc

-   Bcc

この例では、キーワードは必要ではなく、キーワードが誤検知の結果を多数生み出すことにお気付きになるかもしれません。

### <a name="step-2--create-a-new-custom-sensitive-information-type"></a>手順 2 — 新しいカスタムの機密情報の種類を作成する

KQL クエリとキーワードを使って機密情報を識別したら、これらを使って新しいカスタムの機密情報の種類を作成します。多くの場合、必要なレベルの精度を実現するには、機密情報の種類を洗練する必要があります。その後、DLP ポリシーとその他のツールおよび他の KQL クエリ内で、これらのカスタムの機密情報の種類をコンテンツ検索と一緒に使うことができます。

ベスト プラクティスは、既存の種類に基づいて新しい機密情報の種類を作成することです。この記事で前述したのと同じ手順を使います。

### <a name="example--create-a-new-sensitive-information-for-email-addresses"></a>例 — 電子メール アドレスの新しい機密情報の種類を作成する 

電子メール アドレスがシンプルなので、引き続きこれを例として使います。以下の表は、新しい電子メールの機密情報の種類に対して推奨される変更の詳細を示しています。

<table>
<thead>
<tr class="header">
<th align="left"><strong>手順</strong></th>
<th align="left"><strong>変更</strong></th>
<th align="left"><strong>XML 構文の例</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">IdRef プロパティの設定
<p>&lt;Entity&gt; 要素内で、&lt;IdMatch&gt; 要素の idRef プロパティが一意の値と同じになるように変更します。この値は電子メール アドレスを見つけるための正規表現を定義する要素をポイントします。</p></td>
<td align="left">IdRef=&quot;Regex_email_address&quot;</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left"><p>近接度属性</p>
<p>まず &lt;Entity&gt; 要素の patternProximity 値を 300 にします。</p></td>
<td align="left">patternsProximity=&quot;300&quot;</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left"><p>信頼度</p>
<p>recommendedConfidence プロパティを、正確に一致するものを見つけるための信頼度を表していると感じる値に設定します。多くの場合、正確な結果を得るためには、典型的なデータ セットを使ってテストする必要があります。初期設定では、この値を 75 に設定します。</p></td>
<td align="left"><p>recommendedConfidence=&quot;75&quot;&gt;</p>
<p>これら最初の 3 つの要素を結合した結果の XML は次のようになります。</p>
<p>&lt;Entity id=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot; patternsProximity=&quot;300&quot; recommendedConfidence=&quot;75&quot;&gt;</p>
<p>&lt;Pattern confidenceLevel=&quot;75&quot;&gt;</p>
<p>&lt;IdMatch idRef=&quot;Regex_email_address&quot; /&gt;</p>
<p>&lt;Any minMatches=&quot;1&quot;&gt;</p>
<p>&lt;Match idRef=&quot;Keyword_email_terms&quot; /&gt;</p>
<p>&lt;/Any&gt;</p>
<p>&lt;/Pattern&gt;</p>
<p>&lt;/Entity&gt;</p></td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left"><p>Regex 要素</p>
<p>新しい &lt;Regex&gt; 要素を、電子メール アドレスの識別に使う正規表現を定義する &lt;Entity&gt; 要素のすぐ下に追加します。</p></td>
<td align="left">&lt;Regex id=&quot;Regex_email_address&quot;&gt;(^|\b)([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.]+)\.([a-zA-Z]{2,5})($|\b)&lt;/Regex&gt;</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left"><p>キーワード</p>
<p>新しい &lt;Keyword&gt; 要素を、キーワードに関連する電子メール アドレスのリストを定義する &lt;Regex&gt; 要素の下に追加します。&lt;Keyword&gt; 要素の ID 値が、&lt;Entity&gt;&lt;Pattern&gt; 要素の &lt;Match idRef&gt; 値と一致していることをご確認ください。必要に応じて、キーワードをさらに追加することができます。</p>
<p>キーワードは、電子メールの機密情報の種類に必ずしも含める必要はありません。ここでは、例として示しています。</p></td>
<td align="left"><p>&lt;Keyword id=&quot;Keyword_email_terms&quot;&gt;</p>
<p>&lt;Group&gt;</p>
<p>&lt;Term&gt;email&lt;/Term&gt;</p>
<p>&lt;Term&gt;email address&lt;/Term&gt;</p>
<p>&lt;Term&gt;contact&lt;/Term&gt;</p>
<p>&lt;/Group&gt;</p>
<p>&lt;/Keyword&gt;</p></td>
</tr>
<tr class="even">
<td align="left">6</td>
<td align="left"><p>LocalizedStrings 要素</p>
<p>&lt;LocalizedStrings&gt;&lt;Resource&gt; 要素に、自分の機密情報の種類を識別する一意の名前があることをご確認ください。</p></td>
<td align="left"><p>&lt;LocalizedStrings&gt;</p>
<p>&lt;Resource idRef=&quot;42e6348e-27f0-4774-9604-d470cb3e219a&quot;&gt;</p>
<p>&lt;Name default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Email Address&lt;/Name&gt;</p>
<p>&lt;Description default=&quot;true&quot; langcode=&quot;en-us&quot;&gt;Detects email addresses.&lt;/Description&gt;</p>
<p>&lt;/Resource&gt;</p>
<p>&lt;/LocalizedStrings&gt;</p></td>
</tr>
</tbody>
</table>

## <a name="create-a-new-sensitive-information-type-with-example-powershell-and-xml-file--contoso-customer-number"></a>例の PowerShell と XML ファイルで、新しい機密情報の種類を作成する — Contoso 顧客番号

Contoso は、Contoso 顧客番号 (CCN) を使って、顧客データベースから各顧客を識別します。CCN には以下の分類があります。

-   記録が作られた年を表す 2 桁の数字。Contoso は 2002 年に設立されたので、使用可能な一番小さい値は 02 です。

-   記録を作成したパートナー代理店を表す 3 桁の数字。代理店の値として使用可能なのは、000 から 999 の範囲です。

-   基幹業務を表す英字。使用可能な値は、a から z で、大文字と小文字は区別されません。

-   4 桁のシリアル番号。シリアル番号の値として使用可能なのは、0000 から 9999 の範囲です。

CCN の例:

> 15080P9562
>
> 14040O1119
>
> 15020J8317
>
> 14050E2330
>
> 16050E2166
>
> 17040O1118

Contoso は、内部対応、外部対応、ドキュメントなどで、常に CCN を使って顧客を参照しています。カスタムの機密情報の種類を作成して、Office 365 での CCN の使用を検出します。これにより、この形式の個人データの使用に対して、保護を適用することができます。

### <a name="create-a-new-sensitive-information-type-for-contoso-customer-number"></a>Contoso 顧客番号に対して新しい機密情報の種類を作成する

<table>
<thead>
<tr class="header">
<th align="left"><strong>手順</strong></th>
<th align="left"><strong>処理</strong></th>
<th align="left"><strong>結果</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">1</td>
<td align="left">Contoso は PowerShell とコンテンツ検索を使用して、CCN の一連の例に一致するドキュメントを検索します。</td>
<td align="left">

<p>#Office 365 セキュリティ/コンプライアンス センターに接続する</p>
<p>$adminUser = &quot;alland@contoso.com&quot;</p>
<p>Connect-IPPSSession -UserPrincipalName $adminUser</p>
<p>#サンプル データの検索を作成して開始する</p>
<p>$searchName = &quot;Sample Customer Information Search&quot;</p>
<p>$searchQuery = &quot;15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118&quot;</p>
<p>New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery</p>
<p>Start-ComplianceSearch -Identity $searchName</p>
</td>
</tr>
<tr class="even">
<td align="left">2</td>
<td align="left">Contoso は結果を分析します。CCN が使われるたびに、EU 形式の日付が使われ、次のキーワードのうちのいずれか 1 つも近接度 300 文字の中で使われます。</td>
<td align="left">customer number、customer no、customer #、customer#、Contoso customer</td>
</tr>
<tr class="odd">
<td align="left">3</td>
<td align="left">Contoso は、CNN を識別するため、次の正規表現 (RegEx) パターンを開発しました。</td>
<td align="left">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</td>
</tr>
<tr class="even">
<td align="left">4</td>
<td align="left">Contoso は、さまざまな子会社で使われる形式の EU の日付を識別するため、次の正規表現 (RegEx) パターンを開発しました。</td>
<td align="left">
````xml
(0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)?|‌ feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|‌ apr(ile|il)?|abr(il)?|avril|may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|‌ oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)?|nov(ember|iembre|embre|embro)?|dec(ember)?|‌ dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}
````
</td>
</tr>
<tr class="odd">
<td align="left">5</td>
<td align="left">Contoso は、PowerShell を使用して、3 つの一意の GUID を生成します。</td>
<td align="left"><p>#RulePack ID、Publisher ID、Entity ID の一意の GUID を生成する</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p>
<p>[guid]::NewGuid().Guid</p></td>
</tr>
<tr class="even">
<td align="left">6</td>
<td align="left">Contoso は、機密項目の種類のルールに対して、次のパラメーターを定義しています。</td>
<td align="left"><p>名前: Contoso 顧客番号 (CCN)</p>
<p>説明: 追加のキーワードと EU 形式の日付を検索する Contoso 顧客番号 (CCN)</p></td>
</tr>
<tr class="odd">
<td align="left">7</td>
<td align="left">Contoso は、Contoso 顧客番号 (CCN) を検出するための新しい機密情報の種類の XML ファイルを作成し、これをローカル ファイル システムに C:\Scripts\ContosoCCN.xml として UTF-8 エンコードで保存します。</td>
<td align="left">この表の下の XML ファイルを参照してください。</td>
</tr>
<tr class="even">
<td align="left">8</td>
<td align="left">Contoso は、次の PowerShell でカスタムの機密情報の種類を作成します。</td>
<td align="left"><p>#Office 365 セキュリティ/コンプライアンス センターに接続する</p>
<p>$adminUser = &quot;alland@contoso.com&quot;</p>
<p>Connect-IPPSSession -UserPrincipalName $adminUser</p>
<p>#新しい機密情報の種類を作成する</p>
<p>New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path &quot;C:\Scripts\ContosoCCN.xml&quot; -Encoding Byte -ReadCount 0)</p></td>
</tr>
</tbody>
</table>

### <a name="example-xml-file-for-the-new-sensitive-information-type-step-7"></a>新しい機密情報の種類のための XML ファイルの例 (手順 7)
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
