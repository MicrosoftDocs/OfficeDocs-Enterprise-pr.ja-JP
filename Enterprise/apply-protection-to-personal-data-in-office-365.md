---
title: "Office 365 の個人データに保護を適用する"
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
- GDPR
- Strat_O365_Enterprise
ms.assetid: 
description: "DLP ポリシーを使用して、Office 365 の個人データを保護する方法について説明します。"
ms.openlocfilehash: e3ecb020a569cbf2cdcf50b4aead5cedf962b4d9
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="apply-protection-to-personal-data-in-office-365"></a><span data-ttu-id="f5f17-103">Office 365 の個人データに保護を適用する</span><span class="sxs-lookup"><span data-stu-id="f5f17-103">Apply protection to personal data in Office 365</span></span>

<span data-ttu-id="f5f17-p101">Office 365 の個人情報の保護にはデータ損失防止機能の使用が含まれます。Office 365 セキュリティ/コンプライアンス センターでデータ損失防止 (DLP) ポリシーを使用することにより、Office 365 全体で機密情報を識別、監視、および自動的に保護することができます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p101">Protection of personal information in Office 365 includes using data loss prevention capabilities. With data loss prevention (DLP) policies in the Office 365 Security & Compliance Center, you can identify, monitor, and automatically protect sensitive information across Office 365.</span></span>

<span data-ttu-id="f5f17-p102">このトピックでは、DLP を使用して、個人データを保護する方法について説明します。さらに、SharePoint ライブラリでのアクセス許可の設定やデバイス アクセス ポリシーの使用など、GDPR 準拠を実現するために使用できその他の保護機能もリストします。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p102">This topic describes how to use DLP to protect personal data. This topic also lists other protection capabilities that can be used to achieve GDPR compliance, including setting permissions in SharePoint libraries and using device access policies.</span></span>

## <a name="apply-protection-using-data-loss-prevention-in-office-365"></a><span data-ttu-id="f5f17-108">Office 365 のデータ損失防止を使用して保護を適用する</span><span class="sxs-lookup"><span data-stu-id="f5f17-108">Apply protection using data loss prevention in Office 365</span></span>

<span data-ttu-id="f5f17-109">DLP では、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-109">With a DLP policy, you can:</span></span>

-   <span data-ttu-id="f5f17-110">複数の場所にわたって機密情報を識別します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-110">	Identify sensitive information across many locations, such as SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="f5f17-111">機密情報を誤って共有することを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-111">Prevent the accidental sharing of sensitive information.</span></span>

-   <span data-ttu-id="f5f17-112">ユーザーがワークフローを中断せずに、コンプライアンスを準拠しつづける方法を学ぶよう支援します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-112">Help users learn how to stay compliant without interrupting their workflow.</span></span>

-   <span data-ttu-id="f5f17-113">組織の DLP ポリシーと一致するコンテンツを示す DLP レポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-113">View DLP reports showing content that matches your organization’s DLP policies.</span></span>

<span data-ttu-id="f5f17-114">詳しくは、「[データ損失防止ポリシーの概要](https://support.office.com/ja-JP/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5f17-114">For more information, see [Overview of data loss prevention policies](https://support.office.com/ja-JP/article/Overview-of-data-loss-prevention-policies-1966b2a7-d1e2-4d92-ab61-42efbb137f5e).</span></span>

![データ損失防止ポリシーを作成するためのオプション](Media/Apply-protection-to-personal-data-in-Office-365-image1.png)

<span data-ttu-id="f5f17-116">この図は、DLP ポリシーを作成するためのオプションを示しています。</span><span class="sxs-lookup"><span data-stu-id="f5f17-116">This illustration shows the options for creating a DLP policy:</span></span>

-   <span data-ttu-id="f5f17-p103">適用する保護を選択します。保護には以下を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p103">Choose the protection to apply. Protection can include:</span></span>

    -   <span data-ttu-id="f5f17-119">ユーザーのポリシー ヒント</span><span class="sxs-lookup"><span data-stu-id="f5f17-119">Policy tips for users</span></span>

    -   <span data-ttu-id="f5f17-120">管理者のメール レポート</span><span class="sxs-lookup"><span data-stu-id="f5f17-120">Email report for admins</span></span>

    -   <span data-ttu-id="f5f17-121">外部、内部、またはその両方で共有できないようにする</span><span class="sxs-lookup"><span data-stu-id="f5f17-121">Prevent sharing externally, internally, or both</span></span>

-   <span data-ttu-id="f5f17-p104">保護を適用する条件を選択します。この種類のコンテンツを含むドキュメントに保護を適用します。機密情報の種類やラベルを使用するポリシーを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p104">Choose the criteria for applying the protection. Apply the protection to documents with this type of content: you can configure the policy to use sensitive information types and/or labels.</span></span>

### <a name="using-dlp-for-gdpr-compliance"></a><span data-ttu-id="f5f17-124">GDPR 準拠のための DLP の使用</span><span class="sxs-lookup"><span data-stu-id="f5f17-124">Using DLP for GDPR compliance</span></span>

<span data-ttu-id="f5f17-p105">Office 365 DLP の主な用途の 1 つは、Office 365 環境内の EU データ サブジェクトに関連する個人データを特定することです。Office 365 DLP は、SharePoint Online と OneDrive for Business で個人情報が保存されている場所や、ユーザーが個人情報を含むメールを送信した旨をコンプライアンス チームに通知することができます。さらに、EU 居住者に関連する個人情報を処理する場合、従業員にポリシー ヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p105">One of the primary uses of Office 365 DLP is to identify personal data related to EU data subjects in your Office 365 environment. Office 365 DLP can notify your compliance teams of where personal information is stored in SharePoint Online and OneDrive for Business, or when users send email containing personal information. DLP can also provide policy tips to your employees when working with personal information related to EU residents.</span></span>

<span data-ttu-id="f5f17-p106">Office 365 DLP を使用した情報の保護レベルの 1 つは、環境内の EU 居住者のデータの保存場所や、従業員にその処理を許可する方法について教育し、意識を高めることです。多くの場合、この種類の情報へのアクセスを持つ従業員は日常の作業を実行するためにこのアクセスを必要としています。GDPR に準拠する DLP ポリシーの適用では、アクセスを制限する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p106">Educating and raising awareness to where EU resident data is stored in your environment and how your employees are permitted to handle it represents one level of information protection using Office 365 DLP. Often, employees who already have access to this type of information require this access to perform their day to day work. Enforcing DLP policies to help comply with GDPR may not require restricting access.</span></span>

<span data-ttu-id="f5f17-p107">ただし、GDPR の準拠には通常、法的事項と情報セキュリティの両方の観点から見た、組織に関するリスク ベースの評価、個人情報の種類と保存場所の識別、その情報を保存および処理する法的な理由があるかどうかの判断が含まれます。この評価に基づいて、組織を保護し、GDPR に準拠するためのポリシーを実装する場合、EU のデータ サブジェクトの個人情報が含まれているドキュメントへの従業員のアクセスを削除しなければならない場合があります。さらに保護が必要な場合には、追加の DLP 保護を構成できます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p107">However, complying with GDPR typically involves a risk based assessment of the organization from both a legal and information security perspective, identification of what type and where personal information is stored, as well as if there is a legal justification to store and process that information. Based on this assessment, implementing policies to protect the organization and comply with GDPR might require removing access for employees to documents that contain personal information for EU data subjects. In cases where further protection is required, additional DLP protection can be configured.</span></span>

<span data-ttu-id="f5f17-p108">次の表は、DLP を使用して保護を強化する 3 つの構成を表示しています。最初の構成である認識は出発点であり、GDPR の保護の最小レベルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p108">The following table lists three configurations of increasing protection using DLP. The first configuration, awareness, can be used as a starting point and minimum level of protection for GDPR.</span></span>

### <a name="example-protection-levels-that-can-be-configured-with-dlp-policies-and-used-for-gdpr-compliance"></a><span data-ttu-id="f5f17-136">DLP ポリシーを使用して構成し、GDPR 準拠に使用できる保護レベルの例</span><span class="sxs-lookup"><span data-stu-id="f5f17-136">Example protection levels that can be configured with DLP policies and used for GDPR compliance</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f5f17-137"><strong>保護レベル</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-137"><strong>Protection level</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-138"><strong>EU のデータ サブジェクトに関連する個人情報が含まれるドキュメントの DLP 構成</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-138"><strong>DLP configuration for documents with personal information related to EU data subjects</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-139"><strong>メリットとリスク</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-139"><strong>Benefits and risks</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-140">認識</span><span class="sxs-lookup"><span data-stu-id="f5f17-140">Awareness</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-141">このデータが SharePoint Online と OneDrive for Business のドキュメントで検出されたときに、コンプライアンス チームにメール通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-141">Send email notifications to compliance teams when this data is found in documents in SharePoint Online and OneDrive for Business.</span></span></p>
<p><span data-ttu-id="f5f17-142">SharePoint と OneDrive for Business で従業員がこのデータを含むドキュメントにアクセスするときに、ポリシー ヒントをカスタマイズして表示します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-142">Customize and display Policy Tips to employees in SharePoint and OneDrive for Business when accessing documents containing this data.</span></span></p>
<p><span data-ttu-id="f5f17-143">このデータが共有されているときは、それを検出して報告します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-143">Detect and report when this data is being shared.</span></span></p></td>
<td align="left"><p><span data-ttu-id="f5f17-144">このデータの保存場所に関するコンプライアンス チームおよび従業員の意識を向上させます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-144">Raise awareness with compliance teams as well as employees regarding where this data is stored.</span></span></p>
<p><span data-ttu-id="f5f17-145">このデータを含むドキュメントを処理するための企業ポリシーについて従業員に教育します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-145">Educate employees on corporate policy for handling documents containing this data.</span></span></p>
<p><span data-ttu-id="f5f17-146">従業員がこのデータを内部または外部で共有できなくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="f5f17-146">Does not prevent employees from sharing this data internally or externally.</span></span></p>
<p><span data-ttu-id="f5f17-147">共有データの DLP レポートを確認し、保護を強化する必要があるかどうか決定できます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-147">You can review DLP reports for shared data and decide if you need to increase the protection.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-148">外部共有を禁止する</span><span class="sxs-lookup"><span data-stu-id="f5f17-148">Prevent external sharing</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-149">外部ユーザーとそのコンテンツを共有している場合、SharePoint Online と OneDrive for Business でこのデータを含むドキュメントへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-149">Restrict access to documents that contain this data in SharePoint Online and OneDrive for Business when that content is shared with external users.</span></span></p>
<p><span data-ttu-id="f5f17-150">このデータを含むドキュメントが含まれるメールを外部の受信者に送信できないようにします。</span><span class="sxs-lookup"><span data-stu-id="f5f17-150">Prevent sending emails with documents that contain this data to external recipients.</span></span></p>
<p><span data-ttu-id="f5f17-151">このデータが共有されているときは、それを検出して報告します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-151">Detect and report when this data is being shared.</span></span></p></td>
<td align="left"><p><span data-ttu-id="f5f17-152">このデータの外部共有を禁止しますが、従業員はこのデータを内部的に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-152">Prevents external sharing of this data while allowing for employees to work with this data internally.</span></span></p>
<p><span data-ttu-id="f5f17-153">内部共有データの DLP レポートを確認し、この保護を強化する必要があるかどうか決定できます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-153">You can review DLP reports for internally shared data and decide if you need to increase this protection.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-154">内部共有および外部共有を禁止する</span><span class="sxs-lookup"><span data-stu-id="f5f17-154">Prevent internal and external sharing</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-155">内部または外部でそのコンテンツを共有している場合、SharePoint Online と OneDrive for Business でこのデータを含むドキュメントへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-155">Restrict access to documents that contain this data in SharePoint Online and OneDrive for Business when that content is shared internally or externally.</span></span></p>
<p><span data-ttu-id="f5f17-156">このデータを含むメールを内部と外部両方の受信者に送信できないようにします。</span><span class="sxs-lookup"><span data-stu-id="f5f17-156">Prevent sending emails which contain this data to both internal and external recipients.</span></span></p></td>
<td align="left"><p><span data-ttu-id="f5f17-157">このデータの内部共有および外部共有を禁止します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-157">Prevents internal and external sharing of this data.</span></span></p>
<p><span data-ttu-id="f5f17-158">従業員は、このデータの処理を必要とするタスクを完了できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5f17-158">Employees might not be able to complete tasks that require working with this data.</span></span></p>
<p><span data-ttu-id="f5f17-159">内部または外部の共有データの DLP レポートを確認し、エンドユーザーのトレーニングを強化する必要があるかどうか決定できます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-159">You can review DLP reports for internally or externally shared data and decide if end user training is needed.</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f5f17-p109">注: 保護のレベルが上がるにつれて、情報にアクセスするユーザーの能力が場合によって低下する可能性があり、日常業務の生産性や能力に影響を及ぼす可能性があります。従業員に影響を与えるポリシーを実装することで保護レベルを上げることには、エンドユーザーのトレーニングを実施し、より安全な環境で生産性を維持するための新しいセキュリティ ポリシーと手順についてユーザーに教育することが関係しています。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p109">Note: As the levels of protection increase, the ability of users to access information will decrease in some cases, and could potentially impact their productivity or ability to complete day to day tasks. Increasing protection levels by implementing policies that impact employees is typically accompanied by end user training, educating users on new security policies and procedures to help them continue to be productive in a more secure environment.</span></span>

### <a name="example-dlp-policy-for-gdpr--awareness"></a><span data-ttu-id="f5f17-162">GDPR 用の DLP ポリシーの例 - 認識</span><span class="sxs-lookup"><span data-stu-id="f5f17-162">Example DLP policy for GDPR — Awareness</span></span> 

<span data-ttu-id="f5f17-163">名前: GDPR の対象となる個人データの認識。</span><span class="sxs-lookup"><span data-stu-id="f5f17-163">Name: Awareness for personal data that is subject to GDPR.</span></span>

<span data-ttu-id="f5f17-164">説明: 従業員にポリシーのヒントを表示し、このデータが SharePoint Online と OneDrive for Business のドキュメントで検出されたときはコンプライアンス チームに通知し、このデータが組織外で共有されている場合にはそれを検出して報告します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-164">Description: Display policy tips to employees, notify compliance teams when this data is found in documents in SharePoint Online and OneDrive for Business, detect and report when this data is being shared outside your organization.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f5f17-165"><strong>コントロール</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-165"><strong>control</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-166"><strong>設定</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-166"><strong>Settings</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-167">保護する情報を選択する</span><span class="sxs-lookup"><span data-stu-id="f5f17-167">Choose what to protect</span></span></td>
<td align="left"><span data-ttu-id="f5f17-168">カスタム ポリシー テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-168">Select a Custom policy template.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-169">場所</span><span class="sxs-lookup"><span data-stu-id="f5f17-169">Locations</span></span></td>
<td align="left"><span data-ttu-id="f5f17-170">Office 365 のすべての場所</span><span class="sxs-lookup"><span data-stu-id="f5f17-170">All locations in Office 365</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-171">含まれているコンテンツを検索する</span><span class="sxs-lookup"><span data-stu-id="f5f17-171">Find content that contains</span></span></td>
<td align="left"><span data-ttu-id="f5f17-172">[編集] をクリックし、環境に合わせて設定したすべての機密情報の種類を追加します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-172">Click ‘Edit’ and add all the sensitive information types you curated for your environment.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-173">このコンテンツが共有されている場合に検出する</span><span class="sxs-lookup"><span data-stu-id="f5f17-173">Detect when this content is shared</span></span></td>
<td align="left"><span data-ttu-id="f5f17-174">このボックスをチェックし、[自分の所属組織外のユーザー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-174">Check this box and select ‘with people outside my organization.’</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-175">コンテンツがポリシーの設定に一致する場合にユーザーに通知する</span><span class="sxs-lookup"><span data-stu-id="f5f17-175">Notify users when content matches the policy settings</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-176">このボックスをチェックします ([ユーザーにポリシー ヒントを表示して電子メール通知を送信する])。</span><span class="sxs-lookup"><span data-stu-id="f5f17-176">Check this box (“Show policy tips to users and send them an email notification.”)</span></span></p>
<p><span data-ttu-id="f5f17-p110">[ヒントとメールをカスタマイズする] をクリックし、環境に合わせてこれらを更新します。この記事の既定の通知 [<a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">メール通知を送信し、DLP ポリシーのポリシー ヒントを表示する</a>] を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p110">Click ‘Customize the tip and email’ and update these for your environment. See the default notifications in this article: <a href="https://support.office.com/en-us/article/Send-email-notifications-and-show-policy-tips-for-DLP-policies-87496bc5-9601-4473-8021-cb05c71369c1?ui=en-US&amp;rs=en-US&amp;ad=US">Send email notifications and show policy tips for DLP policies</a>.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-179">特定の量の機密情報が同時に共有されている場合に検出します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-179">Detect when a specific amount of sensitive info is being shared at one time</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-180">[共有コンテンツが含まれている場合に検出: 機密性タイプが同じ情報の最小インスタンス数] - これを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-180">‘Detect when content that’s being shared contains: At least ____ instances of the same sensitive info type’ — Set this to 1.</span></span></p>
<p><span data-ttu-id="f5f17-p111">[インシデント レポートを電子メールで送信] - このボックスをチェックします。[レポートに含める内容とそれを受け取るユーザーを選択] をクリックします。コンプライアンス チームを必ず追加してください。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p111">‘Send incident reports in email’ — check this box. Click ‘Choose what to include in the report and who receives it.’ Be sure to add your compliance team.</span></span></p>
<p><span data-ttu-id="f5f17-184">[コンテンツにアクセスしてポリシーを上書きするユーザーを制限する] - ユーザーが機密情報にアクセスするのを妨げることなくその情報に関する通知を受信するには、このチェック ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="f5f17-184">‘Restrict who can access the content and override the policy’ — clear this checkbox to receive notifications about sensitive information without preventing users from access that information.</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f5f17-185">すべての場所には次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-185">All locations includes:</span></span>

-   <span data-ttu-id="f5f17-186">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f5f17-186">SharePoint Online</span></span>

-   <span data-ttu-id="f5f17-187">OneDrive for Business アカウント</span><span class="sxs-lookup"><span data-stu-id="f5f17-187">OneDrive for Business Hybrid</span></span>

-   <span data-ttu-id="f5f17-188">Exchange メールボックス</span><span class="sxs-lookup"><span data-stu-id="f5f17-188">Exchange mailboxes: 5,000</span></span>

<span data-ttu-id="f5f17-189">コンテンツ検索では、電子メールで機密情報の種類をテストできないため、各ポリシーの機密情報タイプのサブセットと Exchange の個別ポリシーを作成し、これらのポリシーのロールアウトを監視することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f5f17-189">Because Content Search doesn’t currently let you test sensitive information types with email,consider creating separate policies for Exchange with a subset of sensitive information types in each policy and monitoring the rollout of these policies.</span></span>

## <a name="additional-protection-you-can-apply-to-protect-personal-data-in-office-365"></a><span data-ttu-id="f5f17-190">Office 365 の個人データの保護に適用できる追加の保護</span><span class="sxs-lookup"><span data-stu-id="f5f17-190">Additional protection you can apply to protect personal data in Office 365</span></span>

<span data-ttu-id="f5f17-p112">機密情報の種類、ラベル、およびデータ損失保護ポリシーでは、特定のデータを含むドキュメントを特定し、保護を適用できます。ただし、これらの保護は、データへのアクセス用に設定されている適切なアクセス許可、侵害されていないアカウントを持つユーザー、および正常なデバイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p112">Sensitive information types, labels, and data loss protection policies help you identify documents containing specific data and apply protection. However, these protections depend on appropriate permissions being set for access to data, users with accounts that are not compromised, and devices that are healthy.</span></span>

<span data-ttu-id="f5f17-193">次の図では、個人データへのアクセスを保護するために適用できる追加の保護について説明しています。</span><span class="sxs-lookup"><span data-stu-id="f5f17-193">The following illustration details additional protection you can apply to protect access to personal data.</span></span>

![個人データへのアクセスを保護するための追加の保護](Media/Apply-protection-to-personal-data-in-Office-365-image2.png)

<span data-ttu-id="f5f17-195">次の表では、図での情報と同じものを見やすいように記載しています。</span><span class="sxs-lookup"><span data-stu-id="f5f17-195">For accessibility, the following table provides the same information in the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f5f17-196"><strong>保護の範囲</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-196"><strong>Scope of protection</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-197"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-197"><strong>Capabilities</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-198">ドキュメントと電子メール レベルの保護 (転送中のメールを含みますが、現在メールボックスに保存されているメールは含まない)</span><span class="sxs-lookup"><span data-stu-id="f5f17-198">Document and email-level protection (includes mail in transit, but not currently mailboxes at rest)</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-199">機密情報の種類</span><span class="sxs-lookup"><span data-stu-id="f5f17-199">Sensitive information types</span></span></p>
<p><span data-ttu-id="f5f17-200">Office のラベル</span><span class="sxs-lookup"><span data-stu-id="f5f17-200">Office 365 labels</span></span></p>
<p><span data-ttu-id="f5f17-201">データ損失防止ポリシー</span><span class="sxs-lookup"><span data-stu-id="f5f17-201">Data loss prevention policies and attachment transport rules</span></span></p>
<p><span data-ttu-id="f5f17-202">電子メール用の Office 365 Message Encryption</span><span class="sxs-lookup"><span data-stu-id="f5f17-202">Preparing for Office 365 Message Encryption</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-203">サイトとライブラリ レベルの保護 (SharePoint Online と OneDrive for Business サイトを含む)</span><span class="sxs-lookup"><span data-stu-id="f5f17-203">Site and library-level protection (includes SharePoint Online and OneDrive for Business sites)</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-204">SharePoint と OneDrive for Business のサイトとライブラリに関するアクセス許可</span><span class="sxs-lookup"><span data-stu-id="f5f17-204">Permissions for SharePoint Online and OneDrive for Business sites and libraries</span></span></p>
<p><span data-ttu-id="f5f17-205">SharePoint Online と OneDrive for Business に関する外部共有ポリシー (サイトレベル)</span><span class="sxs-lookup"><span data-stu-id="f5f17-205">External sharing policies for SharePoint Online and OneDrive for Business (site-level)</span></span></p>
<p><span data-ttu-id="f5f17-206">サイトレベルのデバイス アクセス ポリシー</span><span class="sxs-lookup"><span data-stu-id="f5f17-206">Site-level device access controls</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-207">サービスのアクセス保護 (Office 365 のすべてのサービスへのアクセスを含む)</span><span class="sxs-lookup"><span data-stu-id="f5f17-207">Service access protection (includes access to all services in Office 365)</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-208">Enterprise Mobility + Security (EMS) スイートの ID およびデバイスのアクセス保護</span><span class="sxs-lookup"><span data-stu-id="f5f17-208">Identity and device access protection in Enterprise Mobility + Security (EMS) suite</span></span></p>
<p><span data-ttu-id="f5f17-209">特権アクセスの管理</span><span class="sxs-lookup"><span data-stu-id="f5f17-209">Privileged access management</span></span></p>
<p><span data-ttu-id="f5f17-210">Windows 10 のセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="f5f17-210">Windows 10 security capabilities</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f5f17-211">この記事の残りの部分では、これらの各カテゴリの保護の詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-211">The rest of this article provides more information on each of these categories of protection.</span></span>

### <a name="capabilities-that-are-ok-to-use-with-gdpr"></a><span data-ttu-id="f5f17-212">GDPR で使用できる機能</span><span class="sxs-lookup"><span data-stu-id="f5f17-212">Capabilities that are OK to use with GDPR</span></span>

<span data-ttu-id="f5f17-p113">GDPR 準拠用に構成された環境では、次の機能を使用できます。これらの機能には、GDPR 準拠に必ずしも必要ではありませんが、GDPR 準拠に関連するデータの検出、保護、監視、レポートの機能に悪影響を及ぼすことなく使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p113">You can use the following capabilities in an environment configured for GDPR compliance. These capabilities are not necessary for GDPR compliance, but they can be used without adversely affecting your ability to discover, protect, monitor, and report on data related to GDPR compliance.</span></span>

<span data-ttu-id="f5f17-p114">顧客キー - Office 365 内に保存されているデータを暗号化するために使用される暗号化キーを顧客に提供し、制御できるようにします。独自の暗号化キーを管理する規制上の必要がある顧客にのみ推奨されます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p114">Customer Key — Allows customers to provide and retain control over the encryption keys that are used to encrypt data at rest within Office 365. Recommended only for customers with a regulatory need to manage their own encryption keys.</span></span>

<span data-ttu-id="f5f17-p115">カスタマー ロックボックス - カスタマー ロックボックスを使用すると、必要に応じて、Microsoft のサポート エンジニアが自分のデータにアクセスして、ケースごとに技術的な問題を解決する方法を制御できます。サポート エンジニアにデータへのアクセス権を付与するかどうかを制御できます。要求ごとに有効期限が指定されます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p115">Customer Lockbox — Customer lockbox allows you to control how a Microsoft support engineer accesses your data, if needed, to fix a technical issue on a case by case basis. You can control whether to give the support engineer access to your data or not. An expiration time is provided with each request.</span></span>

## <a name="site-and-library-level-protection"></a><span data-ttu-id="f5f17-220">サイトおよびライブラリ レベルの保護</span><span class="sxs-lookup"><span data-stu-id="f5f17-220">Site and library-level protection</span></span>

### <a name="permissions-for-sharepoint-and-onedrive-for-business-libraries"></a><span data-ttu-id="f5f17-221">SharePoint と OneDrive for Business のライブラリに関するアクセス許可</span><span class="sxs-lookup"><span data-stu-id="f5f17-221">Permissions for SharePoint and OneDrive for Business libraries</span></span>

<span data-ttu-id="f5f17-p116">SharePoint のアクセス許可を使用して、サイトまたはそのコンテンツへのユーザーのアクセスを制限します。個々のユーザーまたは Azure Active Directory グループを既定の SharePoint グループに追加します。または、細かくコントロールするためにカスタム グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p116">Use permissions in SharePoint to provide or restrict user access to the site or its contents. Add individual users or Azure Active Directory groups to the default SharePoint groups. Or, create a custom group for finer-grain control.</span></span>

![フル コントロールから表示のみまでのアクセス許可レベル](Media/Apply-protection-to-personal-data-in-Office-365-image3.png)

<span data-ttu-id="f5f17-p117">この図は、フル コントロールから表示のみまでのアクセス許可レベルを示しています。次の表には、同じ情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p117">The illustration plots permission levels from Full control to View Only. The following table includes the same information.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f5f17-228"><strong>フル コントロール</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-228"><strong>Full control</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-229"><strong>デザイン</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-229"><strong>Design</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-230"><strong>編集</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-230"><strong>Edit</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-231"><strong>投稿</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-231"><strong>Contribute</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-232"><strong>読み取り</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-232"><strong>Read</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-233"><strong>表示のみ</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-233"><strong>View Only</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="f5f17-234">投稿 + 承認してカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="f5f17-234">Contribute + approve and customize</span></span></td>
<td align="left"><span data-ttu-id="f5f17-235">投稿 + リストを追加、編集、削除する (リスト アイテムだけでない)</span><span class="sxs-lookup"><span data-stu-id="f5f17-235">Contribute + add, edit and delete lists (not just list items)</span></span></td>
<td align="left"><span data-ttu-id="f5f17-236">リスト アイテムおよびドキュメントを表示、追加、更新、削除する</span><span class="sxs-lookup"><span data-stu-id="f5f17-236">Contribute - Can view, add, update, and delete list items and documents.</span></span></td>
<td align="left"><span data-ttu-id="f5f17-237">表示およびダウンロードする</span><span class="sxs-lookup"><span data-stu-id="f5f17-237">View pages, list items and download documents.</span></span></td>
<td align="left"><span data-ttu-id="f5f17-238">表示するが、ダウンロードしない</span><span class="sxs-lookup"><span data-stu-id="f5f17-238">View, no download</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f5f17-239">詳しくは、以下の資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5f17-239">More Information</span></span>

-   [<span data-ttu-id="f5f17-240">SharePoint でのアクセス許可レベルについて</span><span class="sxs-lookup"><span data-stu-id="f5f17-240">Understanding permission levels in SharePoint</span></span>](https://support.office.com/ja-JP/article/Understanding-permission-levels-in-SharePoint-87ecbb0e-6550-491a-8826-c075e4859848)

-   [<span data-ttu-id="f5f17-241">SharePoint グループについて</span><span class="sxs-lookup"><span data-stu-id="f5f17-241">Understanding SharePoint groups</span></span>](https://support.office.com/ja-JP/article/Understanding-SharePoint-groups-94d9b261-161e-4ace-829e-eca1c8cd2eb8)

### <a name="external-sharing-policies-for-sharepoint-and-onedrive-for-business-libraries"></a><span data-ttu-id="f5f17-242">SharePoint と OneDrive for Business ライブラリに関する外部共有ポリシー</span><span class="sxs-lookup"><span data-stu-id="f5f17-242">External sharing policies for SharePoint and OneDrive for Business libraries</span></span>

<span data-ttu-id="f5f17-p118">多くの組織では、コラボレーションをサポートする外部共有が許可されています。テナント全体の設定を構成する方法について説明します。さらに、個人データが含まれているサイトの外部共有設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p118">Many organizations allow external sharing to support collaboration. Find out how your tenant-wide settings are configured. Then review the external sharing settings for sites that contain personal data.</span></span>

<span data-ttu-id="f5f17-246">外部ユーザーとは、SharePoint Online または Microsoft Office 365 サブスクリプションのライセンスはありませんが、SharePoint Online サイトやドキュメントにアクセスするように招待された組織外のユーザーです。</span><span class="sxs-lookup"><span data-stu-id="f5f17-246">An external user is someone outside of your organization who is invited to access your SharePoint Online sites and documents but does not have a license for your SharePoint Online or Microsoft Office 365 subscription.</span></span>

<span data-ttu-id="f5f17-247">外部共有ポリシーは、SharePoint Online と OneDrive for Business の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-247">External sharing policies apply to both SharePoint Online and OneDrive for Business.</span></span>

-   <span data-ttu-id="f5f17-248">共有ポリシーを構成するには、SharePoint Online 管理者でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="f5f17-248">You must be a SharePoint Online admin to configure sharing policies.</span></span>

-   <span data-ttu-id="f5f17-249">サイトの所有者であるか、外部ユーザーとサイトまたはドキュメントを共有するフル コントロール アクセス許可を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5f17-249">You must be a Site Owner or have full control permissions to share a site or document with external users.</span></span>

<span data-ttu-id="f5f17-250">次の表は、構成できるコントロールの要約を示しています。</span><span class="sxs-lookup"><span data-stu-id="f5f17-250">The following table summarizes the different settings that you can configure for form regions.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f5f17-251"><strong>コントロールのカテゴリ</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-251"><strong>Control category</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-252"><strong>オプション</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-252"><strong>Options</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-253">共有の種類</span><span class="sxs-lookup"><span data-stu-id="f5f17-253">Type of sharing</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-254">組織外の共有を許可しない (個別のサイト コレクションに対して設定できます)</span><span class="sxs-lookup"><span data-stu-id="f5f17-254">Don’t allow sharing outside your organization (can be set for individual site collections)</span></span></p>
<p><span data-ttu-id="f5f17-255">認証された外部ユーザーにのみ共有を許可する (新規ユーザーを許可するか、または既存のユーザーに制限する。個別のサイト コレクションに対して設定できます)\*</span><span class="sxs-lookup"><span data-stu-id="f5f17-255">Allow sharing to authenticated external users only (allow new or limit to existing, can be set for individual site collections)\*</span></span></p>
<p><span data-ttu-id="f5f17-256">匿名アクセス リンクを持つ外部ユーザーに共有を許可する (個別のサイト コレクションに対して設定できます)</span><span class="sxs-lookup"><span data-stu-id="f5f17-256">Allow sharing to external users with an anonymous access link (can be set for individual site collections)</span></span></p>
<p><span data-ttu-id="f5f17-257">ドメインを使用して外部共有を制限する (許可および拒否の一覧)</span><span class="sxs-lookup"><span data-stu-id="f5f17-257">Limit external sharing using domains (allow and deny list)</span></span></p>
<p><span data-ttu-id="f5f17-258">既定のリンクの種類 (匿名、会社で共有可能、または制限) を選択します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-258">Choose the default link type (anonymous, company shareable, or restricted)</span></span></p>
</td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-259">外部ユーザーが実行できる操作</span><span class="sxs-lookup"><span data-stu-id="f5f17-259">What external users can do</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-260">外部ユーザーが自分の所有していないファイル、フォルダー、サイトを共有できないようにする</span><span class="sxs-lookup"><span data-stu-id="f5f17-260">Prevent external users from sharing files, folders, sites they don’t own</span></span></p>
<p><span data-ttu-id="f5f17-261">外部ユーザーに、招待の送信元と同じアカウントで招待の共有を承諾するように要求する</span><span class="sxs-lookup"><span data-stu-id="f5f17-261">Require external users to accept sharing invitations with the same account the invitation was sent to</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-262">通知</span><span class="sxs-lookup"><span data-stu-id="f5f17-262">Notifications</span></span></td>
<td align="left"><p><span data-ttu-id="f5f17-p119">現在、OneDrive for Business でのみ使用できます。次の場合に所有者に通知します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p119">Currently only available in OneDrive for Business. Notify owners when:</span></span></p>
- <p><span data-ttu-id="f5f17-265">ユーザーが追加の外部ユーザーを共有ファイルに招待する</span><span class="sxs-lookup"><span data-stu-id="f5f17-265">Users invite additional external users to shared files</span></span></p>
- <p><span data-ttu-id="f5f17-266">外部ユーザーがファイルへのアクセスの招待を承諾する</span><span class="sxs-lookup"><span data-stu-id="f5f17-266">External users accept invitations to access files</span></span></p>
- <p><span data-ttu-id="f5f17-267">匿名アクセス リンクが作成または変更される</span><span class="sxs-lookup"><span data-stu-id="f5f17-267">An anonymous access link is created or changed</span></span></p></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f5f17-268">詳しくは、以下の資料を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5f17-268">More Information</span></span>

-   [<span data-ttu-id="f5f17-269">SharePoint Online 環境の外部共有を管理する</span><span class="sxs-lookup"><span data-stu-id="f5f17-269">Manage external sharing for your SharePoint Online environment</span></span>](https://support.office.com/en-us/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&rs=en-US&ad=US)

-   [<span data-ttu-id="f5f17-270">組織外部のユーザーとのサイトまたはドキュメントの共有</span><span class="sxs-lookup"><span data-stu-id="f5f17-270">Share sites or documents with people outside your organization</span></span>](https://support.office.com/ja-JP/article/Share-sites-or-documents-with-people-outside-your-organization-80e49744-e30f-44db-8d51-16661b1d4232)

### <a name="site-level-device-access-policies"></a><span data-ttu-id="f5f17-271">サイトレベルのデバイス アクセス ポリシー</span><span class="sxs-lookup"><span data-stu-id="f5f17-271">Site-level device access controls</span></span>

<span data-ttu-id="f5f17-p120">SharePoint Online と OneDrive for Business を使用して、サイト レベルでデバイス アクセス ポリシーを構成できます。これにより、機密データを含むサイトに対して追加の保護を構成できます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p120">SharePoint Online and OneDrive for Business let you configure device access policies at the site level. This lets you configure more protection for sites with sensitive data.</span></span>

<span data-ttu-id="f5f17-274">サイト レベルのデバイス アクセス ポリシーを構成する場合は、必ずテナント レベルのポリシーと Azure Active Directory、Intune、Intune App Management で構成されているアクセス ポリシーと一緒に調整してください。</span><span class="sxs-lookup"><span data-stu-id="f5f17-274">If you configure site-level device access policies, be sure to coordinate these with tenant-level policies and also with access policies that are configured in Azure Active Directory, Intune, and Intune App Management.</span></span>

<span data-ttu-id="f5f17-p121">SharePoint と OneDrive for Business のデバイス アクセス ポリシーには、実装するシナリオによっては Azure Active Directory と Microsoft Intune でのサポート ポリシーが必要です。次の表は、デバイス アクセス ポリシーを使用して実行できる目標の要約を示し、サポート ポリシーが必要な製品を示します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p121">Device access policies for SharePoint and OneDrive for Business require supporting policies in Azure Active Directory and Microsoft Intune depending on the scenario you are implementing. The following table summarizes objectives you can achieve with device access policies and indicates which products require supporting policies.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"></th>
<th align="left"><span data-ttu-id="f5f17-277">特定の IP アドレスの場所からのアクセスのみを許可する</span><span class="sxs-lookup"><span data-stu-id="f5f17-277">Only allow access from specific IP address locations</span></span></th>
<th align="left"><span data-ttu-id="f5f17-278">ドメインに参加していないデバイスにユーザーがファイルをダウンロードできないようにする</span><span class="sxs-lookup"><span data-stu-id="f5f17-278">Prevent users from downloading files to non-domain joined devices</span></span></th>
<th align="left"><span data-ttu-id="f5f17-279">ドメインに参加していないデバイスでのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="f5f17-279">Block access on non-domain joined devices</span></span></th>
<th align="left"><span data-ttu-id="f5f17-280">ユーザーが非準拠デバイスにファイルをダウンロードできないようにする</span><span class="sxs-lookup"><span data-stu-id="f5f17-280">Prevent users from downloading files to non-compliant devices</span></span></th>
<th align="left"><span data-ttu-id="f5f17-281">非準拠デバイスでのアクセスをブロックする</span><span class="sxs-lookup"><span data-stu-id="f5f17-281">Block access on non-compliant devices</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-282">SharePoint 管理センター</span><span class="sxs-lookup"><span data-stu-id="f5f17-282">SharePoint admin center</span></span></td>
<td align="left"><span data-ttu-id="f5f17-283">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-283">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-284">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-284">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-285">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-285">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-286">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-286">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-287">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-287">Yes</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-288">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="f5f17-288">Azure Active Directory</span></span></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="f5f17-289">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-289">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-290">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-290">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-291">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-291">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-292">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-292">Yes</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-293">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="f5f17-293">Microsoft Intune</span></span></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><span data-ttu-id="f5f17-294">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-294">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-295">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-295">Yes</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f5f17-296">詳細: [SharePoint Online 管理センター: 非管理対象デバイスからのアクセスをコントロールします](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US)。</span><span class="sxs-lookup"><span data-stu-id="f5f17-296">More information: [SharePoint Online admin center: Control access from unmanaged devices](https://support.office.com/en-us/article/Control-access-from-unmanaged-devices-5ae550c4-bd20-4257-847b-5c20fb053622?ui=en-US&rs=en-US&ad=US).</span></span>

## <a name="service-access-protection-for-identities-and-devices"></a><span data-ttu-id="f5f17-297">ID とデバイスのサービス アクセスの保護</span><span class="sxs-lookup"><span data-stu-id="f5f17-297">Service access protection for identities and devices</span></span>

<span data-ttu-id="f5f17-p122">サービスにアクセスする ID とデバイスの保護を構成することをお勧めします。Office 365 サービスへのアクセスを保護する作業は、他の SaaS サービス、PaaS サービス、さらには他のクラウド プロバイダーのアプリへのアクセスを保護するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p122">Microsoft recommends you configure protection for identities and devices that access the service. The work you put into protecting access to Office 365 services can also be used to protect access to other SaaS services, PaaS services, and even apps in other cloud providers.</span></span>

<span data-ttu-id="f5f17-300">ID とデバイスのアクセス保護は、ID が侵害されず、デバイスが安全で、デバイス上でアクセスされる組織データが分離され保護されるようにする保護のベースラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-300">Access protection for identities and devices provides a baseline of protection to ensure that identities are not compromised, devices are safe, and organization data that is accessed on devices is isolated and protected.</span></span>

<span data-ttu-id="f5f17-301">開始時の推奨事項と構成のガイダンスについては、「[選挙運動、非営利組織、およびその他のアジャイル組織のための Microsoft Security ガイダンス](https://docs.microsoft.com/ja-JP/microsoft-365-enterprise/microsoft-security-guidance)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5f17-301">For starting point recommendations and configuration guidance, see [Microsoft security guidance for political campaigns, nonprofits, and other agile organizations](https://docs.microsoft.com/ja-JP/microsoft-365-enterprise/microsoft-security-guidance).</span></span>

<span data-ttu-id="f5f17-302">AD FS を使用するハイブリッド ID 環境については、「[推奨されるセキュリティ ポリシーと構成](https://docs.microsoft.com/ja-JP/microsoft-365-enterprise/microsoft-security-guidance)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5f17-302">For hybrid identity environments with AD FS, see [Recommended security policies and configurations](https://docs.microsoft.com/ja-JP/microsoft-365-enterprise/microsoft-security-guidance).</span></span>

<span data-ttu-id="f5f17-p123">次の図は、クラウド サービス (SaaS、PaaS)、アカウントの種類 (テナント ドメイン アカウントと B2B アカウント)、およびサービス アクセス機能の関連について説明しています。どの機能を B2B アカウントで使用できるかを銘記することが重要です。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p123">The following illustration describes how cloud services (SaaS, PaaS), account types (tenant domain accounts vs. B2B accounts) and service access capabilities relate. It’s important to note which capabilities can be used with B2B accounts.</span></span>

![クラウド サービス、アカウントの種類、およびアクセス機能](Media/Apply-protection-to-personal-data-in-Office-365-image4.png)

<span data-ttu-id="f5f17-306">アクセシビリティのため、このセクションの残りの部分でこの図について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-306">For accessibility, the rest of this section describes this illustration.</span></span>

### <a name="cloud-services"></a><span data-ttu-id="f5f17-307">クラウド サービス</span><span class="sxs-lookup"><span data-stu-id="f5f17-307">Cloud services</span></span>

<span data-ttu-id="f5f17-p124">Azure Active Directory は、Amazon Web サービスなどの Microsoft 以外のプロバイダーを含む、任意のクラウド サービスへの ID アクセスを提供します。この図は、Office 365、「その他の SaaS アプリ」、および「PaaS アプリ」を示しています。Azure Active Directory からこれらの各サービスを指す矢印は、Azure Active Directory がこれらすべてのアプリの種類への認証に使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p124">Azure Active Directory provides identity access to any cloud service, including non-Microsoft providers such as Amazon Web Services. The illustration shows Office 365, “Other SaaS app,” and “PaaS app.” Arrows point from Azure Active Directory to each of these services, showing that Azure Active Directory can be used for authentication to all of these app types.</span></span>

### <a name="types-of-accounts"></a><span data-ttu-id="f5f17-311">アカウントの種類</span><span class="sxs-lookup"><span data-stu-id="f5f17-311">Types of accounts</span></span>

<span data-ttu-id="f5f17-p125">テナント ドメイン アカウントは、テナントに追加して、直接管理するためのアカウントです。B2B アカウントは、共同作業に招待する組織外のユーザーのアカウントです。これには、他の Office 365 のアカウント、他の組織のアカウント、またはコンシューマー アカウント (Gmail など) があります。この図は、Azure Active Directory 内での両方のアカウントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p125">Tenant domain accounts are account you add to your tenant and manage directly. B2B accounts are accounts for users outside your organization you invite to collaborate with. These can be other Office 365 accounts, other organization accounts, or consumer accounts (such as Gmail). The illustration shows both account types within Azure Active Directory.</span></span>

### <a name="capabilities"></a><span data-ttu-id="f5f17-316">機能</span><span class="sxs-lookup"><span data-stu-id="f5f17-316">Capabilities</span></span>

<span data-ttu-id="f5f17-p126">次の表にある機能は、ID およびデバイスを保護します。この表は、図にあるように B2B アカウントでも使用できる機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="f5f17-p126">The capabilities in the following table protect identities and devices. The table indicates which capabilities can also be used with B2B accounts, similar to the illustration.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f5f17-319"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-319"><strong>Capability</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-320"><strong>テナント ドメイン アカウントを処理する</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-320"><strong>Works with tenant domain accounts</strong></span></span></th>
<th align="left"><span data-ttu-id="f5f17-321"><strong>Azure B2B アカウントを処理する (追加ライセンスを使用しない)</strong></span><span class="sxs-lookup"><span data-stu-id="f5f17-321"><strong>Works with Azure B2B accounts (without additional licensing)</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-322">多要素認証および条件付きアクセス</span><span class="sxs-lookup"><span data-stu-id="f5f17-322">Multi-factor authentication and conditional access</span></span></td>
<td align="left"><span data-ttu-id="f5f17-323">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-323">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-324">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-324">Yes</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-325">Azure AD Identity Protection</span><span class="sxs-lookup"><span data-stu-id="f5f17-325">Azure AD Identity Protection</span></span></td>
<td align="left"><span data-ttu-id="f5f17-326">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-326">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-327">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-327">Yes</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-328">Azure AD Privileged Identity Management</span><span class="sxs-lookup"><span data-stu-id="f5f17-328">Azure AD Privileged Identity Management</span></span></td>
<td align="left"><span data-ttu-id="f5f17-329">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-329">Yes</span></span></td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-330">モバイル アプリケーション管理 (MAM)</span><span class="sxs-lookup"><span data-stu-id="f5f17-330">Mobile Application Management (MAM)</span></span></td>
<td align="left"><span data-ttu-id="f5f17-331">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-331">Yes</span></span></td>
<td align="left"></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f5f17-332">デバイスの登録と管理</span><span class="sxs-lookup"><span data-stu-id="f5f17-332">Device enrollment and management</span></span></td>
<td align="left"><span data-ttu-id="f5f17-333">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-333">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-334">1 つの組織のみがデバイスを管理できる</span><span class="sxs-lookup"><span data-stu-id="f5f17-334">Only one organization can manage a device</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f5f17-335">Windows 10 のセキュリティ機能 (デバイスの準拠に基づく条件付きアクセスにはデバイスの管理が必要です)</span><span class="sxs-lookup"><span data-stu-id="f5f17-335">Windows 10 security capabilities (conditional access based on device compliance requires device management)</span></span></td>
<td align="left"><span data-ttu-id="f5f17-336">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-336">Yes</span></span></td>
<td align="left"><span data-ttu-id="f5f17-337">はい</span><span class="sxs-lookup"><span data-stu-id="f5f17-337">Yes</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f5f17-338">B2B アカウントにライセンスを追加すると、必要に応じてこれらのユーザーに追加の機能を提供して、ご使用の環境内で個人データへのアクセスを保護できます。</span><span class="sxs-lookup"><span data-stu-id="f5f17-338">You can add licenses to B2B accounts to give these users additional capabilities, if needed, to protect access to personal data in your environment.</span></span>
