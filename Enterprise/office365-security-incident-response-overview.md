---
title: Office 365 のセキュリティ事故の対応
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/27/2018
ms.audience: ITPro
ms.topic: overview
ms.collection:
- o365_security_incident_response
- Strat_O365_IP
ms.service: o365-solutions
localization_priority: Normal
ms.custom: ''
ms.assetid: ''
description: このソリューションは、Office 365 とそれに応答する方法で攻撃する、最も一般的なサイバー ・ セキュリティのようになります
ms.openlocfilehash: b9800070bde662603c731e2b8d64609b4f821cce
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="office-365-security-incident-response"></a><span data-ttu-id="70068-103">Office 365 のセキュリティ事故の対応</span><span class="sxs-lookup"><span data-stu-id="70068-103">Office 365 Security Incident Response</span></span>

 <span data-ttu-id="70068-104">**の概要:** このソリューションでは、Office 365 の最も一般的なサイバー セキュリティ攻撃の状況説明マークとは、特定の攻撃を確実に確認する方法、それに応答する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="70068-104">**Summary:** This solution tells you what the indicators are for the most common cyber-security attacks in Office 365, how to positively confirm any given attack, and how to respond to it.</span></span>
  
## <a name="overview"></a><span data-ttu-id="70068-105">概要</span><span class="sxs-lookup"><span data-stu-id="70068-105">Overview</span></span>
<span data-ttu-id="70068-p101">すべてのサイバー攻撃を阻止できます。攻撃者は防御的な戦略の新しい脆弱性を常に模索してか、古いものを悪用しています。セキュリティ インシデントの期間が短くなります攻撃を使用すると、それにより迅速な対応を認識する方法を知ることです。</span><span class="sxs-lookup"><span data-stu-id="70068-p101">Not all cyber attacks can be thwarted. Attackers are constantly looking for new weaknesses in your defensive strategy or they are exploiting old ones. Knowing how to recognize an attack allows you to respond to it faster, which shortens the duration of the security incident.</span></span>

<span data-ttu-id="70068-p102">この一連の資料は、Office 365 に表示される特定の種類の攻撃を理解するのに役立つし、応答するための手順を使用します。簡単に入力のポイントを理解することがあります。</span><span class="sxs-lookup"><span data-stu-id="70068-p102">This series of article helps you understand what a particular type of attack might look like in Office 365 and gives you steps you can take to respond. They are quick entry points to understanding:</span></span>
 
- <span data-ttu-id="70068-111">どのような攻撃とそのしくみ。</span><span class="sxs-lookup"><span data-stu-id="70068-111">What the attack is and how it works.</span></span>
- <span data-ttu-id="70068-112">内容には、署名には、インジケーターを探して妥協 (IOC)、およびそれらを検索する方法と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="70068-112">What signs, called indicators of compromise (IOC), to look for and how to look for them.</span></span>
- <span data-ttu-id="70068-113">攻撃を確実に確認する方法です。</span><span class="sxs-lookup"><span data-stu-id="70068-113">How to positively confirm the attack.</span></span>
- <span data-ttu-id="70068-114">攻撃が省略され、向上するための手順は、将来的に組織を保護します。</span><span class="sxs-lookup"><span data-stu-id="70068-114">Steps to take to cut off the attack and better protect your organization in the future.</span></span>
- <span data-ttu-id="70068-115">各に関する詳細な情報へのリンクの種類を攻撃します。</span><span class="sxs-lookup"><span data-stu-id="70068-115">Links to in-depth information on each attack type.</span></span>

<span data-ttu-id="70068-116">チェックして毎月のように他の資料は、時間の経過と共に追加されます。</span><span class="sxs-lookup"><span data-stu-id="70068-116">Check back here monthly as more articles will be added over time.</span></span>

## <a name="detect-and-remediate-articles"></a><span data-ttu-id="70068-117">検出し、記事の修正</span><span class="sxs-lookup"><span data-stu-id="70068-117">Detect and Remediate Articles</span></span>
- [<span data-ttu-id="70068-118">検出し、Office 365 で不正な同意の補助金の修正</span><span class="sxs-lookup"><span data-stu-id="70068-118">Detect and Remediate Illicit Consent Grants in Office 365</span></span>](detect-and-remediate-illicit-consent-grants.md)
- [<span data-ttu-id="70068-119">検出し、Outlook の仕訳ルールと Office 365 でユーザー設定フォームのインジェクション攻撃を修正</span><span class="sxs-lookup"><span data-stu-id="70068-119">Detect and Remediate Outlook Rules and Custom Forms Injections Attacks in Office 365</span></span>](detect-and-remediate-outlook-rules-forms-attack.md)
 
## <a name="secure-office-365-like-a-cybersecurity-pro"></a><span data-ttu-id="70068-120">Pro の cybersecurity のように Office 365 をセキュリティで保護します。</span><span class="sxs-lookup"><span data-stu-id="70068-120">Secure Office 365 like a cybersecurity pro</span></span>
<span data-ttu-id="70068-p103">Office 365 サブスクリプションのデータとユーザーを保護するために使用できるセキュリティ機能の強力なセットが付属します。 使用、 [Office 365 のセキュリティ ロードマップ: 最初の 30 日、90 日間での内外の優先順位のトップ](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352)マイクロソフトが推奨する、Office 365 テナントのセキュリティに関するベスト プラクティスを実装します。</span><span class="sxs-lookup"><span data-stu-id="70068-p103">Your Office 365 subscription comes with a powerful set of security capabilities that you can use to protect your data and your users.  Use the [Office 365 security roadmap: Top priorities for the first 30 days, 90 days, and beyond](https://support.office.com/en-us/article/Office-365-security-roadmap-Top-priorities-for-the-first-30-days-90-days-and-beyond-28c86a1c-e4dd-4aad-a2a6-c768a21cb352) to implement Microsoft recommended best practices for securing your Office 365 tenant.</span></span>
- <span data-ttu-id="70068-p104">最初の 30 日以内に実行するタスクです。 即座に影響があり、影響の少ないのはこれらのユーザーにします。</span><span class="sxs-lookup"><span data-stu-id="70068-p104">Tasks to accomplish in the first 30 days.  These have immediate affect and are low-impact to your users.</span></span>
- <span data-ttu-id="70068-p105">90 日以内に実行するタスクです。計画し実装しますが、セキュリティ体制を大幅に向上させるのには少し時間がかかるこれら</span><span class="sxs-lookup"><span data-stu-id="70068-p105">Tasks to accomplish in 90 days. These take a bit more time to plan and implement but greatly improve your security posture</span></span>
- <span data-ttu-id="70068-p106">90 日が経過します。これらの拡張機能は、最初の 90 日間の作業でビルドします。</span><span class="sxs-lookup"><span data-stu-id="70068-p106">Beyond 90 days. These enhancements build in your first 90 days work.</span></span>






