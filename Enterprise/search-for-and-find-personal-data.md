---
title: "個人データの検索"
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
description: "Office 365 の個人データを検索する方法について説明します。"
ms.openlocfilehash: f19aed534fe2bb4154edc31f0d1b0c82afcc1f04
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="search-for-and-find-personal-data"></a>個人データの検索

個人データは GDPR のもとで、欧州連合 (EU) 内で特定される個人、または特定可能な個人に関連するあらゆるデータとして、非常に広範に定義されています。

記事 4: 定義

> ‘個人データ’ とは特定される個人、または特定可能な個人 (‘データ主体’) に関連するあらゆる情報であり、特定可能な個人とは、その個人の名前、ID 番号、位置データ、オンライン ID、または物理的、生理学的、遺伝子上、心理的、経済的、文化的、社会的な識別情報に固有の 1 つ以上の因子を参照することによって直接または間接的に特定される人物です。

この記事では、SharePoint Online および OneDrive for Business (すべての Office 365 グループおよび Microsoft Teams のサイトを含む) に保管されている個人データを検索する方法について説明します。

GDPR の対象となる個人データの検索には、Office 365 での機密情報の種類を使用する必要があります。これによって自動化プロセスが健康保険番号やクレジット カード番号などの特定情報の種類を認識する方法が定義されます。現時点では、機密情報の種類は Exchange メールボックスに保管中のデータの検索には使用できません。ただし機密情報の種類は、データ損失防止ポリシーとともに、移動中の電子メールに含まれる個人データの検索には使用できます。

そのため、現在は Exchange Online メールボックスに保管中の個人データはコンテンツ検索には使用できませんが、GDPR のためにまとめた機密情報の種類を使用して、個人情報が電子メールで送信されるときに検索し、保護することができます。

## <a name="use-content-search-to-find-personal-data"></a>コンテンツ検索を使用して個人データを検索する

Microsoft では、Office 365 の個人データ検索に 3 段階のアプローチをお勧めします。このトピックの残りの部分では、これらの各段階について説明します。

<table>
<thead>
<tr class="header">
<th align="left"><strong>手順</strong></th>
<th align="left"><strong>説明</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>1. 機密情報の種類の検索</p></td>
<td align="left"><p>機密情報の種類を使用して個人データの検索を開始します。各機密情報の種類に対してコンテンツ検索クエリを作成します。クエリを実行し、結果を分析します。</p>
必要に応じてクエリにパラメーターを追加し、誤検知を減らします。 <li>カウント範囲</li>
    <li>信頼範囲</li>
    <li>より複雑なクエリのためのその他のプロパティや演算子</li>
<p>必要であれば、機密情報の種類を変更して組織の精度を向上させます。</p>
<p><li>XML で信頼度を直接調整します。</li></p>
<p><li>キーワードを追加します。</li></p>
<p><li>キーワードの近接性要件を調整します。</li></p></td>
</tr>
<tr class="even">
<td align="left"><p>2. キーワード クエリ言語 (KQL) を使用して環境内で追加の個人データを検索する</p></td>
<td align="left"><p>機密情報の種類に含まれていないデータを検索するには、KQL クエリ言語を使用してカスタム クエリを開発します。</p>
<p>これらの検索の結果をテストし、期待どおりの結果が得られるまで、KQL クエリ文字列を調整します。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>3. KQL クエリを使用して新しいカスタムの機密情報の種類を作成する</p></td>
<td align="left">KQL クエリを最適化して対象のデータを検索した後、これらのクエリを使用して新しいカスタムの機密情報の種類を作成します。次に、これらカスタムの機密情報の種類を、DLP ポリシーやその他のツール、およびその他の KQL クエリ内でのコンテンツ検索に使用します。</td>
</tr>
</tbody>
</table>

近日公開: セキュリティ/コンプライアンス センターの新しいユーザー インターフェイスで、機密情報の種類を作成および変更できるようになります。一致した結果を動的に参照し、機密情報の種類をニーズに合わせて調整することができます。

## <a name="search-for-sensitive-information-types-using-content-search"></a>コンテンツ検索を使用した機密情報の種類の検索

Office 365 に含まれている機密情報の種類を使用して個人データの検索を開始します。これらはセキュリティ/コンプライアンス センターの [分類] の下にリストされています。

このトピックには、欧州連合の市民に適用される現在の機密情報の種類がリストされています。これらを開始点として、セキュリティ/コンプライアンス センターで GDPR 準拠を支える新しい追加事項がないか頻繁にチェックしてください。

また次の記事も参照してください: [機密情報の種類と、それぞれの検索対象の一覧](https://support.office.com/ja-JP/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b)

機密情報の種類は、自動化されたプロセスが銀行口座番号、健康保険番号、クレジット カード番号などの特定の情報の種類を認識できる方法を定義します。機密情報の種類は条件とも呼ばれます。機密情報の種類はパターンで定義され、正規表現または関数で識別できます。機密情報の種類はさらに、キーワードやチェックサムなどの確証的な証拠を使用して識別することもできます。また、評価プロセスでは信頼度や近接度も使用されます。

現時点では、メールボックス内に保管中のデータ検索には機密情報の種類を使用できません。

### <a name="using-content-search-with-sensitive-information-types"></a>機密情報の種類によるコンテンツ検索の使用

<table>
<thead>
<tr class="header">
<th align="left"><strong>手順</strong></th>
<th align="left"><strong>詳細情報</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd"><td align="left"><p>セキュリティ/コンプライアンス センターでコンテンツ検索に進む</p></td>
<td align="left"><p>セキュリティ/コンプライアンス センターの左側のウィンドウで、**[検索と調査]** &gt; **[コンテンツ検索]** の順にクリックします。</p>
<p>「<a href="https://support.office.com/en-us/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a">Office 365 のセキュリティ/コンプライアンス センターでコンテンツ検索を実行する</a>」を参照してください。</p></td>
</tr>
<tr class="even">
<td align="left"><p>それぞれの機密情報の種類に新しい検索項目を作成する</p></td>
<td align="left"><p>次の構文を使用してください。</p>
<blockquote>
<p>SensitiveType:”&lt;type&gt;”</p>
</blockquote>
<p>次に例を示します。</p>
<blockquote>
<p>SensitiveType:&quot;France Passport Number&quot;</p>
</blockquote>
<p>SharePoint (OneDrive for Business を含む) に、検索の範囲を指定します。構文が完全に一致し、余分なスペースや入力ミスがないことを確認してください。</p>
<p>「<a href="https://support.office.com/ja-JP/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836">サイトに保存された機密データを検索するクエリの形成</a>」を参照してください。</p></td>
</tr>
<tr class="odd">
<td align="left"><p>各検索の結果を確認します。</p></td>
<td align="left"><p>次のような種類の問題を確認して、クエリの精度が正確かどうかを判断します。</p>
<p><li>誤検知が多い</li></p>
<p><li>データの既知のインスタンスがない</li></p>
<p>「<a href="https://support.office.com/en-us/article/Export-Content-Search-results-from-the-Office-365-Security-Compliance-Center-ed48d448-3714-4c42-85f5-10f75f6a4278">Office 365 セキュリティ/コンプライアンス センターの検索結果をエクスポートする</a>」を参照してください。</p>
<p>注: Mozilla Firefox または Chrome を使用している場合、最初に Internet Explorer または Edge を使用してレポートをダウンロードし、必要なアドオンをインストールする必要があります。</p></td>
</tr>
</tbody>
</table>

## <a name="sensitive-information-types-for-eu-citizen-data"></a>EU 市民データのための機密情報の種類

次のような機密情報の種類から開始します。EU 加盟国の個人データについては、その他にも多数の機密情報の種類が近日公開されます。

> ベルギーの国民番号
>
> クレジット カード番号
>
> クロアチアの身分証明書番号
>
> クロアチアの個人識別 (OIB) 番号
>
> チェコの国民身分証明書番号
>
> デンマークの個人識別番号
>
> 欧州連合のデビット カード番号
>
> フィンランドの国民 ID
>
> フィンランドのパスポート番号
>
> フランスの運転免許証番号
>
> フランスの国民識別カード (CNI)
>
> フランスのパスポート番号
>
> フランスの社会保障番号 (INSEE)
>
> ドイツの運転免許証番号
>
> ドイツの身分証明書番号
>
> ドイツのパスポート番号
>
> ギリシャの国民識別カード
>
> 国際銀行口座番号 (IBAN)
>
> IP アドレス
>
> アイルランドの個人公共サービス (PPS) 番号
>
> イタリアの運転免許証番号
>
> オランダの市民サービス (BSN) 番号
>
> ノルウェーの識別番号
>
> ポーランドの ID カード
>
> ポーランドの国民 ID (PESEL)
>
> ポーランドのパスポート
>
> ポルトガルの市民カード番号
>
> スペインの社会保障番号 (SSN)
>
> スウェーデンの国民 ID
>
> スウェーデンのパスポート番号
>
> 英国の運転免許証番号
>
> 英国の選挙登録番号
>
> 英国の国民健康保険番号
>
> 英国の国民保険番号 (NINO)
>
> 米国/英国のパスポート番号

## <a name="add-parameters-to-a-sensitive-information-type-query-to-hone-the-results"></a>機密情報の種類クエリにパラメーターを追加して、結果の精度を上げます。

次のパラメーターを機密情報の種類クエリに追加できます。

-   カウント範囲: 定義した数の機密情報がドキュメント内に出現した場合にそのドキュメントをクエリ結果に含めることができます。

-   信頼範囲: 85 (85%) など、検出された機密情報の種類が満たすべき信頼レベルです。

構文:

-   SensitiveType:”\<種類\>|\<カウント範囲\>|\<信頼範囲\>”

例:

-   SensitiveType:“Credit Card Number|5” (5 つのクレジット カード番号を持つドキュメントのみを返します)

-   SensitiveType:“Credit Card Number|\*|85..” (信頼範囲が 85% 以上)

注: "SensitiveType" は大文字と小文字を区別しますが、クエリの残りの部分では区別しません。

プロパティと演算子を使用してクエリを調整する方法を示すこともできます。詳細とその他の例については、「[サイトに保存された機密データを検索するクエリの形成](https://support.office.com/ja-JP/article/Form-a-query-to-find-sensitive-data-stored-on-sites-3019fbc5-7f15-4972-8d0e-dc182dc7f836)」を参照してください。
