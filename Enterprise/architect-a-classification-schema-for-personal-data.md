---
title: 個人データの分類スキーマを設計する
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 2/7/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- Strat_O365_Enterprise
- Ent_O365
- GDPR
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: ''
search.appverid:
- MET150
description: 組織が GDPR 計画の一環としてラベルを実装するかどうかを決定します。
ms.openlocfilehash: 9b58138742d598e66e9eca2bf3ed3b71d1411015
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915532"
---
# <a name="architect-a-classification-schema-for-personal-data"></a>個人データの分類スキーマを設計する

このシリーズの前の記事では、GDPR の対象となる個人データの識別に機密情報の種類を使用することに焦点を置いていました。機密情報の種類は分類の 1 形式であり、これが、必要な分類すべてである場合もあります。ただし、多数の組織ではラベルを使用した幅広いデータ ガバナンス戦略を取り入れています。このトピックを使用して、GDPR 計画の一環としてラベルを実装するかどうかを決定してください。実装する場合、このトピックは多少のガイダンスと例を提供します。

注: 組織の分類スキーマを定義してポリシー、ラベル、条件を構成するには、慎重な計画と準備が必要です。これは IT 部門が主導するプロセスではないことに注意してください。法務およびコンプライアンス チームと共同で、組織のデータのための適切な分類およびラベル作成スキーマの開発にあたってください。

## <a name="decide-if-you-are-using-labels-in-addition-to-sensitive-data-types"></a>機密データの種類の他にラベルを使用するかどうかを決定する

Office 365 では、個人情報に分類の 2 つの方法のいずれかを使用することができます。これらはどちらも GDPR 保護に使用できます。機密情報の種類だけを分類に使用すると決定した場合は、このトピックの残りの部分はスキップすることができます。

次のいずれかのオプションを選んでください

### <a name="option-1-use-only-office-365-sensitive-information-types"></a>オプション 1: Office 365 の機密情報の種類だけを使用する

-   機密情報の種類は GDPR やその他の規制の対象となる個人データの識別と保護に適しています。

-   これらは、組織でまだラベルを使用する広範なデータ ガバナンス計画がない場合、またはその実装が準備段階の場合に簡単に使用できます。

-   これらは DLP ルールにも適しています (Office のラベルも同様)。

-   将来的には、これらは Cloud App Security とも連携するため、他の SaaS アプリでも機密データを検出することができます。

### <a name="option-2-use-sensitive-information-types--office-labels"></a>オプション 2: 機密情報の種類と Office のラベルを使用する

-   GDPR の対象となる個人データにラベルを自動的に適用するには、機密情報の種類が必要になるため、これは前提条件です。

-   Office のラベルを使用すると、GDPR の対象となる個人データを、組織の広範なデータ ガバナンス計画に含めることができます。

-   その後、Office ラベルは Azure Information Protection ラベルと併せて、統一された分類とラベル付けエンジンにまとめられます。

## <a name="develop-a-label-schema-that-includes-personal-data"></a>個人データを含むラベル スキーマを開発する

技術的な機能を使用してラベルと保護を適用するには、最初に組織全体で分類スキーマを定義します。組織内にすでに分類スキーマが存在することがあり、これを使用すると個人データの追加が容易になります。このトピックでは、サンプルの分類スキーマを紹介します。必要であれば、これを開始点として使用することができます。

### <a name="getting-started"></a>はじめに

まず、実装するラベルの数と名前を決定します。これは、どのテクノロジを使用するか、どのようにラベルを適用するかといった点を意識せずに決定してください。このスキーマは、オンプレミスやその他のクラウド サービスに存在するデータを含め、組織全体で汎用的に適用します。

### <a name="recommendations"></a>推奨事項 

ポリシー、ラベル、条件を設計および実装するには、次の推奨事項に従う必要があります。

-   既存の分類スキーマを使用する (ある場合): 多数の組織ではすでに何らかの形でデータ分類を使用しています。既存のラベル スキーマを慎重に評価し、可能であればそのまま使用します。エンド ユーザーが使い慣れているものに類似したラベルを使用すると、導入が円滑に進みます。

-   既定のポリシーとラベルから開始する: すべてのソリューションでは、ポリシーとラベルが事前定義されています。組織の法務および業務要件に照らしてこれらを慎重に評価し、新しいものを作成するのではなく、これを使用することを検討します。

-   小規模で開始する: 作成できるラベルの数に実質的な制限はありません。ただし、ラベルとサブ ラベルの数が多くなると、導入にマイナスの影響を及ぼします。選択肢が多すぎることは、選択肢が何もないことを意味します。

-   シナリオとユース ケースを使用する: 組織内の一般的なユース ケースを特定し、GDPR から派生したシナリオを使用して、作成されたラベルと分類の構成が実際に機能するかどうかを確認します。

-   すべてのシナリオまたはユース ケースに新しいラベルが必要かどうか、すでにあるものは使用できないかなど、新しいラベルに対するすべてに要求に対して質問します。ラベルの数を最小限に抑えると、導入を促進できます。

-   一部の部門では特定のラベルを必要とする特殊なニーズがあり、主要部門にはサブ ラベルを使用します。これらのラベルを既存のラベルに対するサブ ラベルとして定義し、全体ではなく、ユーザー グループに割り当てる範囲限定ポリシーを使用することを検討します。

-   範囲限定ポリシーの使用を検討します。ポリシーの対象をユーザーのサブセットに限定すると、「ラベルのオーバーロード」を防止できます。範囲限定ポリシーによって、ロールまたは部門固有の (サブ) ラベルの割り当てを特定部門に勤務する従業員に限定することができます。

-   わかりやすいラベル名を使用します。ラベル名には専門用語、規格、略語は推奨されません。エンド ユーザーにわかりやすい名前を付けて導入を促進するようにします。PII、PCI、HIPAA、LBI、MBI、HBI のようなラベルではなく、「ビジネス以外」、「公開」、「一般」、「社外秘」、「非常に機密性の高い社外秘」などの名前を検討してください。

### <a name="example-classification-schema"></a>分類スキーマの例

<table>
<thead>
<tr class="header">
<th align="left"><strong>ラベル名</strong></th>
<th align="left"><strong>説明</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">個人</td>
<td align="left">ビジネス以外のデータ (個人使用のみ)。</td>
</tr>
<tr class="even">
<td align="left">公開</td>
<td align="left">公開使用向けに明確に準備、承認されているビジネス データ。</td>
</tr>
<tr class="odd">
<td align="left">顧客データ</td>
<td align="left">個人を特定できる情報を含むビジネス データ。例としては、クレジット カード番号、銀行口座番号、社会保障番号などがあります。</td>
</tr>
<tr class="even">
<td align="left">人事データ</td>
<td align="left">従業員番号や給与データなど、Contoso 社の社員の人事管理データ。</td>
</tr>
<tr class="odd">
<td align="left">社外秘</td>
<td align="left">権限のないユーザーと共有すると、ビジネスに損害を与える可能性のある機密性の高いビジネス データ。例としては、契約書、セキュリティ レポート、予測サマリー、販売取引データなどがあります。</td>
</tr>
<tr class="even">
<td align="left">非常に機密性の高い社外秘</td>
<td align="left">権限のないユーザーと共有すると、ビジネスに損害を与える可能性のある非常に機密性の高いビジネス データ。例としては、従業員情報と顧客情報、パスワード、ソース コード、発表前の財務レポートなどがあります。</td>
</tr>
</tbody>
</table>

## <a name="define-a-taxonomy-and-search-criteria-for-each-label"></a>各ラベルの分類と検索条件を定義する

組織の分類スキーマを開発したら、次にこのデータを検索するための分類と検索条件を開発します。個人データの場合、この作業はすでに機密情報の種類の識別と、環境に応じた機密情報の種類のカスタマイズや新規作成によって完了しています。

次の表には、組織用のスキーマ、分類、および検索条件の例を示します。ラベルは機密性の低いものから高いものの順に並べられ、複数のラベル条件と一致するデータが適切なラベルに割り当てられるようにしています。

注: 構成の例は例示のためのものであり、展開のガイダンスや参照情報として意図されたものではありません。

ここで重要な点は、GDPR 準拠のための個人データの分類に費やす作業が、組織全体の目的と一致している必要があるということです。

### <a name="example-schema-taxonomy-and-search-criteria"></a>スキーマ、分類、および検索条件の例

<table>
<thead>
<tr class="header">
<th align="left"><strong>ラベル</strong></th>
<th align="left"><strong>分類</strong></th>
<th align="left"><strong>メソッド</strong></th>
<th align="left"><strong>検索構文</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">個人</td>
<td align="left">エンド ユーザーによって手動で「個人」とラベルが付けられたドキュメント。</td>
<td align="left">手動</td>
<td align="left">エンド ユーザーによって手動で「個人」とラベルが付けられたドキュメント。</td>
</tr>
<tr class="even">
<td align="left">公開</td>
<td align="left">「Approved for Public Release ##/####」という大文字/小文字を区別しない語句を含み、# が任意の数字を示すドキュメント。</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Approved for Public Release*</p>
<p>RegEx — (?i)(\bApproved for Public Release \d{2}\/\d{4}\b)</p></td>
</tr>
<tr class="odd">
<td align="left">顧客データ</td>
<td align="left">EU 市民データのための機密情報の種類。</td>
<td align="left">機密情報の種類</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">人事 — 従業員データ</td>
<td align="left">CONTOSO-9##### という形式で大文字/小文字を区別する従業員 ID を含み、# が任意の数字を示すドキュメント。</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — CONTOSO-9*</p>
<p>RegEx — (\bCONTOSO-9\d{5}\b)</p></td>
</tr>
<tr class="odd">
<td align="left">人事 — 給与データ</td>
<td align="left">キーワード (大文字/小文字を区別しない)「Contoso 」と、キーワード (大文字/小文字を区別しない)「Salary」または「Compensation」を含むドキュメント</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Contoso AND (Salary OR Compensation)</p>
<p>RegEx — (\bCONTOSO-9\d{5}\b)</p></td>
</tr>
<tr class="even">
<td align="left">Confidential</td>
<td align="left">語句 (大文字/小文字を区別しない)「Contoso Confidential」を含むドキュメント。</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Contoso Confidential</p>
<p>RegEx — (?i)(\bContoso Confidential\b)</p></td>
</tr>
<tr class="odd">
<td align="left">非常に機密性の高い社外秘</td>
<td align="left">語句 (大文字/小文字を区別する)「Contoso Secret」または「Secret-C####」を含み、# が任意の数字を示すドキュメント。</td>
<td align="left"><p>KQL</p>
<p>RegEx</p></td>
<td align="left"><p>KQL — Contoso Secret OR Secret-C*</p>
<p>RegEx — (?i)(\bContoso Secret\b)|(\bSecret-C\d{4}\b)</p></td>
</tr>
</tbody>
</table>
