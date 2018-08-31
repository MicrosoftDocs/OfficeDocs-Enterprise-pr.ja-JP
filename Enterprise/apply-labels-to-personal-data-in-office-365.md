---
title: Office 365 の個人データにラベルを適用する
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
search.appverid:
- MET150
description: Office のラベルを GDPR 保護計画の一部として使用する方法について説明します。
ms.openlocfilehash: c0058a023b807b81df42274d5e8b9408e37d505d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914932"
---
# <a name="apply-labels-to-personal-data-in-office-365"></a><span data-ttu-id="3ced0-103">Office 365 の個人データにラベルを適用する</span><span class="sxs-lookup"><span data-stu-id="3ced0-103">Apply labels to personal data in Office 365</span></span>

 <span data-ttu-id="3ced0-p101">GDPR 保護計画の一部として Office ラベルを使用している場合は、このトピックを使用してください。現在、ラベルは、Office 365 セキュリティ/コンプライアンス センターと Azure Information Protection で作成できます。近い将来、これらのテクノロジによりラベル付けとその分類のエクスペリエンスが統一され、より多くのことを達成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p101">Use this topic if you are using Office labels as part of your GDPR protection plan. Today labels can be created in the Office 365 Security & Compliance Center and in Azure Information Protection. Over time these technologies will converge into a unified labeling and classification experience and you will be able to achieve even more.</span></span>

<span data-ttu-id="3ced0-p102">Office 365 で個人用データを保護するためにラベルを使用している場合は、Office ラベルを使用することをお勧めします。アドバンスト データ ガバナンスを使用すると、機密情報の種類やその他の基準に基づいてラベルを自動的に適用できます。データ損失防止機能を備えた Office ラベルを使用して、保護を適用することができます。また、電子情報開示とコンテンツ検索でラベルを使用することもできます。そして間もなく、Cloud App Security でラベルと機密情報の種類の両方を使用して、他の SaaS アプリにある個人データを監視できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p102">If you are using labels for protection of personal data in Office 365, Microsoft recommends you start with Office labels. You can use Advanced Data Governance to automatically apply labels based on sensitive information types or other criteria. You can use Office labels with data loss prevention to apply protection. You can also use labels with eDiscovery and Content Search. You’ll soon be able to use both labels and sensitive information types with Cloud App Security to monitor personal data that resides in other SaaS apps.</span></span>

<span data-ttu-id="3ced0-p103">Azure Information Protection のラベルは現在、オンプレミスのファイル、その他のクラウド サービスのファイル、プロバイダーにラベルを適用する場合に推奨されています。また、営業秘密ファイルなどのデータ保護用の Azure Rights Management (Azure RMS) 暗号化を必要とする Office 365 のファイルにも推奨されます。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p103">Azure Information Protection labels are currently recommended for applying labels to files on premises and in other cloud services and providers. These are also recommended for files in Office 365 that require Azure Rights Management (Azure RMS) encryption for data protection, such as trade secret files.</span></span>

<span data-ttu-id="3ced0-p104">現時点では、Azure Information Protection を使用して Azure RMS 暗号化を適用することは、GDPR の対象となるデータを含む Office 365 のファイルにはお勧めできません。現在、Office 365 サービスでは RMS で暗号化されたファイルへの読み取りはできないため、その種のファイル内の機密データを検出できません。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p104">At this time, using Azure Information Protection to apply Azure RMS encryption is not recommended for files in Office 365 with data that is subject to the GDPR. Office 365 services currently cannot read into RMS-encrypted files. Therefore, the service can’t find sensitive data in these files.</span></span>

<span data-ttu-id="3ced0-p105">Azure Information Protection のラベルは Exchange Online のメールに適用することができ、これらのラベルは Office 365 のデータ損失防止で使用します。ラベル付けとその分類を統一するエンジンが近日公開される予定で、電子メールとファイルに同じラベルを使用できるようになります。また、自動ラベル付けや送信中の電子メールの保護も可能になります。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p105">Azure Information Protection labels can be applied to mail in Exchange Online and these labels work with Office 365 data loss prevention. Coming soon with the unified classification and labeling engine you will be able to use the same labels for email and files, including automatically labeling and protecting email in transit.</span></span>

![Office 365 のラベルと Azure Information Protection のラベル](Media/Apply-labels-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="3ced0-120">この図について:</span><span class="sxs-lookup"><span data-stu-id="3ced0-120">In the illustration:</span></span>

-   <span data-ttu-id="3ced0-121">SharePoint Online および OneDrive for Business では、個人データや厳しく規制された営業秘密ファイルに Office 365 のラベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="3ced0-121">Use Office 365 labels for personal data and for highly regulated & trade secret files in SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="3ced0-122">厳しく規制された営業秘密ファイル、Exchange Online 電子メール、他の SaaS サービスのファイル、オンプレミスのデータセンターのファイル、他のクラウド プロバイダーのファイルには、Azure Information Protection (AIP) のラベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="3ced0-122">Use Azure Information Protection (AIP) labels for highly regulated & trade secret files, Exchange Online email, files in other SaaS services, files in on-premises datacenters, and files in other cloud providers.</span></span>

-   <span data-ttu-id="3ced0-123">近日公開: 両方のラベルに関して、ラベル付けとその分類のエクスペリエンスが統一されます。</span><span class="sxs-lookup"><span data-stu-id="3ced0-123">Coming soon: both types of labels will converge into a unified classification and labeling experience.</span></span>

## <a name="use-office-labels-and-sensitive-information-types-across-microsoft-365-for-information-protection"></a><span data-ttu-id="3ced0-124">情報を保護するために Microsoft 365 全体で Office のラベルと機密情報の種類を使用する</span><span class="sxs-lookup"><span data-stu-id="3ced0-124">Use Office labels and sensitive information types across Microsoft 365 for information protection</span></span>

<span data-ttu-id="3ced0-125">次の図は、ラベル ポリシー、データ損失防止ポリシー、Cloud App Security ポリシーで Office のラベルと機密情報の種類を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3ced0-125">The following illustration shows how Office labels and sensitive information types can be used in label policies, data loss prevention policies, and with Cloud App Security policies.</span></span>

![Office のラベルと機密情報の種類](Media/Apply-labels-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="3ced0-127">次の表では、図での例と同じものを見やすいように記載しています。</span><span class="sxs-lookup"><span data-stu-id="3ced0-127">For accessibility, the following table provides the same examples in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3ced0-128"><strong>分類の要素</strong></span><span class="sxs-lookup"><span data-stu-id="3ced0-128"><strong>Classification elements</strong></span></span></th>
<th align="left"><span data-ttu-id="3ced0-129"><strong>ラベル ポリシー — 2 つの例</strong></span><span class="sxs-lookup"><span data-stu-id="3ced0-129"><strong>Label policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="3ced0-130"><strong>データ損失防止ポリシー — 2 つの例</strong></span><span class="sxs-lookup"><span data-stu-id="3ced0-130"><strong>Data loss prevention policies — 2 examples</strong></span></span></th>
<th align="left"><span data-ttu-id="3ced0-131"><strong>すべての SaaS アプリの Cloud App Security ポリシー — 1 つの例</strong></span><span class="sxs-lookup"><span data-stu-id="3ced0-131"><strong>Cloud App Security policies for all SaaS apps — 1 example</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3ced0-p106">Office のラベル。例: 個人、公開、顧客データ、人事データ、社外秘、非常に機密性の高い社外秘</span><span class="sxs-lookup"><span data-stu-id="3ced0-p106">Office labels. Examples: Personal, Public, Customer data, HR data, Confidential, Highly confidential</span></span></td>
<td align="left"><p><span data-ttu-id="3ced0-p107">このラベルを自動で . . .</span><span class="sxs-lookup"><span data-stu-id="3ced0-p107">Auto apply this label . . .</span></span></p>
<p><span data-ttu-id="3ced0-137">顧客データ</span><span class="sxs-lookup"><span data-stu-id="3ced0-137">Customer data</span></span></p>
<p><span data-ttu-id="3ced0-p108">. . . これらの機密情報の種類に一致する文書に適用します . . .</span><span class="sxs-lookup"><span data-stu-id="3ced0-p108">. . . to documents that match these sensitive information types . . .</span></span></p>
<p><span data-ttu-id="3ced0-144">&lt;機密情報の種類の例の一覧&gt;</span><span class="sxs-lookup"><span data-stu-id="3ced0-144">&lt;list of example sensitive information types&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="3ced0-p109">この保護を . . .</span><span class="sxs-lookup"><span data-stu-id="3ced0-p109">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="3ced0-148">&lt;保護の定義&gt;</span><span class="sxs-lookup"><span data-stu-id="3ced0-148">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="3ced0-p110">. . . このラベルを持つドキュメントに適用します . . .</span><span class="sxs-lookup"><span data-stu-id="3ced0-p110">. . . to documents with this label . . .</span></span></p>
<p><span data-ttu-id="3ced0-155">顧客データ</span><span class="sxs-lookup"><span data-stu-id="3ced0-155">Customer data</span></span></p></td>
<td align="left"><p><span data-ttu-id="3ced0-p111">承認された SaaS アプリのこれらの属性を持つファイルが . . .</span><span class="sxs-lookup"><span data-stu-id="3ced0-p111">Alert when files with these attributes . . .</span></span></p>
<p><span data-ttu-id="3ced0-159">&lt;定義済みの PII 属性 -または- ユーザー設定の式&gt;</span><span class="sxs-lookup"><span data-stu-id="3ced0-159">&lt;predefined PII attribute -or- custom expression&gt;</span></span></p>
<p><span data-ttu-id="3ced0-p112">. . . 組織外で共有された際に警告します</span><span class="sxs-lookup"><span data-stu-id="3ced0-p112">. . . in any sanctioned SaaS app are shared outside the organization</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3ced0-p113">機密情報の種類。例: ベルギーの国民番号、クレジット カード番号、クロアチアの身分証明書番号、フィンランドの国民 ID</span><span class="sxs-lookup"><span data-stu-id="3ced0-p113">Sensitive information types. Examples: Belgium National Number, Credit Card Number, Croatia Identity Cart Number, Finland National ID</span></span></td>
<td align="left"><p><span data-ttu-id="3ced0-p114">これらのラベルを発行して、ユーザーが . . .</span><span class="sxs-lookup"><span data-stu-id="3ced0-p114">Publish these labels for users to manually apply . . .</span></span></p>
<p><span data-ttu-id="3ced0-169">&lt;ラベルの選択&gt;</span><span class="sxs-lookup"><span data-stu-id="3ced0-169">&lt;select labels&gt;</span></span></p>
<p><span data-ttu-id="3ced0-p115">. . . これらの場所に手動で適用するようにします . . .</span><span class="sxs-lookup"><span data-stu-id="3ced0-p115">. . . to these locations . . .</span></span></p>
<p><span data-ttu-id="3ced0-176">&lt;すべての場所、あるいは特定の場所を選択&gt;</span><span class="sxs-lookup"><span data-stu-id="3ced0-176">&lt;all locations or choose specific locations&gt;</span></span></p></td>
<td align="left"><p><span data-ttu-id="3ced0-p116">この保護を . . .</span><span class="sxs-lookup"><span data-stu-id="3ced0-p116">Apply this protection . . .</span></span></p>
<p><span data-ttu-id="3ced0-180">&lt;保護の定義&gt;</span><span class="sxs-lookup"><span data-stu-id="3ced0-180">&lt;define protection&gt;</span></span></p>
<p><span data-ttu-id="3ced0-p117">. . . これらの機密情報の種類に一致する文書に適用します&gt;</span><span class="sxs-lookup"><span data-stu-id="3ced0-p117">. . . to documents that match these sensitive information types&gt;</span></span></p></td>
<td align="left"><span data-ttu-id="3ced0-185">注: 近日公開される、Cloud App Security への属性には、Office 365 の機密情報の種類があり、Office 365 と Azure Information Protection の統一ラベルも含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ced0-185">Note: Attributes coming soon to Cloud App Security include Office 365 sensitive information types and Unified labels across Office 365 and Azure Information Protection.</span></span></td>
</tr>
</tbody>
</table>

## <a name="prioritize-auto-apply-label-policies"></a><span data-ttu-id="3ced0-186">自動適用ラベル ポリシーの優先順位付け</span><span class="sxs-lookup"><span data-stu-id="3ced0-186">Prioritize auto-apply label policies</span></span>

<span data-ttu-id="3ced0-p118">GDPR の対象となる個人データについては、環境に合わせて設定した機密情報の種類を使用してラベルを自動適用することをお勧めします。自動適用ラベル ポリシーは、意図した動作が確実に行われるように、適切に設計され、テストされていることが重要です。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p118">For personal data that is subject to GDPR, Microsoft recommends auto-applying labels by using the sensitive information types you curated for your environment. It is important that auto-apply label policies are well designed and tested to ensure the intended behavior occurs.</span></span>

<span data-ttu-id="3ced0-p119">自動適用ポリシーが作成される順序と、ユーザーもこれらのラベルを適用するかどうかによって結果が異なってきます。したがって、ポリシーの作成とラベルの適用を慎重に計画する必要があります。重要なポイントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p119">The order that auto-apply policies are created and whether users are also applying these labels affect the result. So, it is important to carefully plan the roll-out. Here’s what you need to know.</span></span>

### <a name="one-label-at-a-time"></a><span data-ttu-id="3ced0-191">一度に 1 つのラベルを適用する</span><span class="sxs-lookup"><span data-stu-id="3ced0-191">One label at a time</span></span>

<span data-ttu-id="3ced0-192">ドキュメントに割り当てることができるラベルの数は 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="3ced0-192">You can only assign one label to a document.</span></span>

### <a name="older-auto-apply-policies-win"></a><span data-ttu-id="3ced0-193">優先されるのは古いポリシー</span><span class="sxs-lookup"><span data-stu-id="3ced0-193">Older auto-apply policies win</span></span>

<span data-ttu-id="3ced0-p120">自動適用ラベルを割り当てるルールが複数あり、コンテンツが複数のルールの条件を満たす場合は、最も古いルールのラベルが割り当てられます。このため、ラベル ポリシーを構成する前に注意深く計画することが重要です。組織がラベル ポリシーの優先順位を変更する必要がある場合は、ラベル ポリシーを削除して再度作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p120">If there are multiple rules that assign an auto-apply label and content meets the conditions of multiple rules, the label for the oldest rule is assigned. For this reason, it is important to plan the label policies carefully before configuring them. If an organization requires a change to the priority of the label policies, they will need to delete and recreate them.</span></span>

### <a name="manual-user-applied-labels-trump-auto-applied-labels"></a><span data-ttu-id="3ced0-197">自動適用ラベルよりもユーザーが手動で適用したラベルが優先される</span><span class="sxs-lookup"><span data-stu-id="3ced0-197">Manual user-applied labels trump auto-applied labels</span></span>

<span data-ttu-id="3ced0-p121">ユーザーが手動で適用したラベルは、自動適用ラベルよりも優先されます。自動適用ポリシーでは、ユーザーがすでに適用しているラベルを置き換えることはできませんが、ユーザーは、自動適用されたラベルを置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p121">Manual user applied labels trump auto-applied labels. Auto-apply policies cannot replace a label that is already applied by a user. Users can replace labels that are auto-applied.</span></span>

### <a name="auto-assigned-labels-can-be-updated"></a><span data-ttu-id="3ced0-201">自動的に割り当てられたラベルは更新可能</span><span class="sxs-lookup"><span data-stu-id="3ced0-201">Auto-assigned labels can be updated</span></span>

<span data-ttu-id="3ced0-202">自動的に割り当てられたラベルは、新しいラベル ポリシーにより、または既存のポリシーを更新することによって最新の状態にすることができます。</span><span class="sxs-lookup"><span data-stu-id="3ced0-202">Auto-assigned labels can be updated by either newer label policies or by updates to existing policies.</span></span>

<span data-ttu-id="3ced0-203">ラベルを実装する際に重要な点:</span><span class="sxs-lookup"><span data-stu-id="3ced0-203">Be sure your plan for implementing labels includes:</span></span>

-   <span data-ttu-id="3ced0-204">自動適用ポリシーが作成される順序の優先順位付けを行います。</span><span class="sxs-lookup"><span data-stu-id="3ced0-204">Prioritizing the order that auto-apply policies are created.</span></span>

-   <span data-ttu-id="3ced0-p122">ユーザーが手動でラベルを適用する前に、ラベルが自動適用されるまで十分な時間の余裕があります。条件に一致するすべてのコンテンツにラベルが適用されるまでに最大 7 日間かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p122">Allowing enough time for labels to be automatically applied before rolling these out for users to manually apply. It can take up to seven days for the labels to be applied to all content that matches the conditions.</span></span>

### <a name="example-priority-for-creating-the-auto-apply-policies"></a><span data-ttu-id="3ced0-207">自動適用ポリシー作成の優先順位の例</span><span class="sxs-lookup"><span data-stu-id="3ced0-207">Example priority for creating the auto-apply policies</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3ced0-208"><strong>ラベル</strong></span><span class="sxs-lookup"><span data-stu-id="3ced0-208"><strong>Labels</strong></span></span></th>
<th align="left"><span data-ttu-id="3ced0-209"><strong>自動適用ポリシーの作成順序の優先順位</strong></span><span class="sxs-lookup"><span data-stu-id="3ced0-209"><strong>Priority order to create auto-apply policies</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3ced0-210">人事 — 従業員データ</span><span class="sxs-lookup"><span data-stu-id="3ced0-210">Human Resources — Employee Data</span></span></td>
<td align="left"><span data-ttu-id="3ced0-211">1</span><span class="sxs-lookup"><span data-stu-id="3ced0-211">1</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3ced0-212">顧客データ</span><span class="sxs-lookup"><span data-stu-id="3ced0-212">Customer Data</span></span></td>
<td align="left"><span data-ttu-id="3ced0-213">2</span><span class="sxs-lookup"><span data-stu-id="3ced0-213">2</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3ced0-214">非常に機密性の高い社外秘</span><span class="sxs-lookup"><span data-stu-id="3ced0-214">Highly Confidential</span></span></td>
<td align="left"><span data-ttu-id="3ced0-215">3</span><span class="sxs-lookup"><span data-stu-id="3ced0-215">3</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3ced0-216">人事 — 給与データ</span><span class="sxs-lookup"><span data-stu-id="3ced0-216">Human Resources — Salary Data</span></span></td>
<td align="left"><span data-ttu-id="3ced0-217">4</span><span class="sxs-lookup"><span data-stu-id="3ced0-217">4</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3ced0-218">社外秘</span><span class="sxs-lookup"><span data-stu-id="3ced0-218">Confidential</span></span></td>
<td align="left"><span data-ttu-id="3ced0-219">5</span><span class="sxs-lookup"><span data-stu-id="3ced0-219">5</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3ced0-220">公開</span><span class="sxs-lookup"><span data-stu-id="3ced0-220">Public</span></span></td>
<td align="left"><span data-ttu-id="3ced0-221">6</span><span class="sxs-lookup"><span data-stu-id="3ced0-221">6</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3ced0-222">個人</span><span class="sxs-lookup"><span data-stu-id="3ced0-222">Personal</span></span></td>
<td align="left"><span data-ttu-id="3ced0-223">自動適用ポリシーなし</span><span class="sxs-lookup"><span data-stu-id="3ced0-223">No auto-apply policy</span></span></td>
</tr>
</tbody>
</table>

## <a name="create-labels-and-auto-apply-label-policies"></a><span data-ttu-id="3ced0-224">ラベルおよび自動適用ラベル ポリシーの作成</span><span class="sxs-lookup"><span data-stu-id="3ced0-224">Create labels and auto-apply label policies</span></span>

<span data-ttu-id="3ced0-225">セキュリティ/コンプライアンス センターで、ラベルおよびポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ced0-225">Create labels and policies in the Security & Compliance Center.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3ced0-226"><strong>手順</strong></span><span class="sxs-lookup"><span data-stu-id="3ced0-226"><strong>Step</strong></span></span></th>
<th align="left"><span data-ttu-id="3ced0-227"><strong>説明</strong></span><span class="sxs-lookup"><span data-stu-id="3ced0-227"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="3ced0-228">コンプライアンス チームのメンバーにアクセス許可を与えます。</span><span class="sxs-lookup"><span data-stu-id="3ced0-228">Give permissions to members of your compliance team.</span></span></p></td>
<td align="left"><p><span data-ttu-id="3ced0-p123">ラベルを作成するコンプライアンス チームのメンバーには、セキュリティ &amp; コンプライアンス センターを使用するためのアクセス許可が必要です。[セキュリティ/コンプライアンス センターのアクセス許可] に移動し、コンプライアンス管理者グループのメンバーを変更します。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p123">Members of your compliance team who will create labels need permissions to use the Security &amp; Compliance Center. Go to Permissions in Security and Compliance Center and modify the members of the Compliance Administrator group.</span></span></p>
<p><span data-ttu-id="3ced0-231">「<a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">ユーザーに Office 365 セキュリティ センター &amp; コンプライアンス センターへのアクセスを許可する</a>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ced0-231">See <a href="https://support.office.com/en-ie/article/Give-users-access-to-the-Office-365-Security-Compliance-Center-2cfce2c8-20c5-47f9-afc4-24b059c1bd76">Give users access to the Office 365 Security &amp; Compliance Center</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="3ced0-232">Office のラベルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ced0-232">Create Office labels.</span></span></p></td>
<td align="left"><span data-ttu-id="3ced0-233">セキュリティ/コンプライアンス センターの [分類] に移動し、[ラベル] を選択して、使用している環境のラベルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ced0-233">Go to Classifications in Security and Compliance Center, choose Labels, and create the labels for your environment.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="3ced0-234">ラベルの自動適用ポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ced0-234">Create auto-apply policies for labels.</span></span></p></td>
<td align="left"><span data-ttu-id="3ced0-p124">セキュリティ/コンプライアンスセンターの [分類] に移動し、[ラベル ポリシー] を選択し、自動適用ラベルのポリシーを作成します。これらのポリシーは、優先順位に従って作成してください。</span><span class="sxs-lookup"><span data-stu-id="3ced0-p124">Go to Classification in Security and Compliance Center, choose Label policies, and create the policies for auto-applying labels. Be sure to create these policies in the prioritized order.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="3ced0-237">次の図は、顧客データ ラベル用の自動適用ラベルを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3ced0-237">The following illustration shows how to create an auto-apply label for the Customer data label.</span></span>

![顧客データのラベルの作成と適用](Media/Apply-labels-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="3ced0-239">この図について:</span><span class="sxs-lookup"><span data-stu-id="3ced0-239">In the illustration:</span></span>

-   <span data-ttu-id="3ced0-240">“顧客データ” ラベルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3ced0-240">The “Customer data” label is created.</span></span>

-   <span data-ttu-id="3ced0-241">GDPR の必要な機密情報の種類 (ベルギーの国民番号、クレジット カード番号、クロアチアの身分証明書番号、フィンランドの国民 ID) が記載されています。</span><span class="sxs-lookup"><span data-stu-id="3ced0-241">The desired sensitive information types for GDPR are listed: Belgium National Number, Credit Card Number, Croatia Identity Card Number, Finland National ID.</span></span>

-   <span data-ttu-id="3ced0-242">自動適用ポリシーを作成すると、ポリシーに追加する機密情報の種類のいずれかを含むファイルに、“顧客データ” ラベルが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3ced0-242">Create an auto-apply policy assigns the label “Customer data” to any file that includes one of the sensitive information types that you add to the policy.</span></span>
