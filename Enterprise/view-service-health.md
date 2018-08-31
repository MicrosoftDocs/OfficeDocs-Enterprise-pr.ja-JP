---
title: Office 365 サービスの稼働状態を確認する方法
ms.author: kfollis
author: kfollis
manager: scotv
ms.date: 6/15/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: アクティブなサービス中断がないかどうかをサポートに連絡する前に、Office 365 サービスの状態を表示します。
ms.openlocfilehash: d01fe8e269ace922ab92cca779d6f8fea8b6802e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541575"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="a8a74-103">Office 365 サービスの稼働状態を確認する方法</span><span class="sxs-lookup"><span data-stu-id="a8a74-103">How to check Office 365 service health</span></span>

<span data-ttu-id="a8a74-p101">Office 365 の Office 365、Yammer、Microsoft Dynamics CRM では、Microsoft Intune クラウド サービスの稼働状況を表示することができます * * の稼働状態のサービスを提供する * * 管理センターのページです。クラウド サービスの問題が発生した場合、は、サポートに連絡するか、問題解決の時間を費やす前に進行中の解像度での既知の問題があるかどうかを判断するのにはサービスの稼働状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 ** Service health ** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="a8a74-106">サービスの稼働状態を確認する方法</span><span class="sxs-lookup"><span data-stu-id="a8a74-106">How to check service health</span></span>

1. <span data-ttu-id="a8a74-107">[https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage)と管理者用のアカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="a8a74-107">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="a8a74-p102">グローバル管理者またはサービス管理者の役割に割り当てられているユーザーは、サービスの稼働状態を表示できます。サービスの稼働状態を表示するのには、Exchange、SharePoint、およびビジネス管理者の Skype は、割り当てる必要がも、サービス管理者の役割です。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> 
  
2. <span data-ttu-id="a8a74-p103">**状態**に移動を開くにはサービスの稼働状態、管理センターで、 \> **サービスの稼働状態**、またはダッシュ ボードのホームページ上のカードのサービスの稼働状態] をクリックします。ダッシュ ボードのカードでは、アクティブなサービスの問題と詳細なサービスの稼働状態のページへのリンクがあるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p103">To open service health, in the admin center, go to **Health** \> **Service health**, or click the Service health card on the Home dashboard. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![サービスの稼働状態のダッシュ ボードのカード](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="a8a74-113">各クラウド サービスの稼働状態は、可能な状態を示すアイコンが表形式で表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8a74-113">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="a8a74-114">Push 通知による最新情報を入手するのにことは、サービスの稼働状態を表示するのには、モバイル デバイスに[Office 365 の管理者用のアプリケーション](https://go.microsoft.com/fwlink/p/?linkid=627216)を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8a74-114">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="a8a74-115">転記済のサービスの稼働状態の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-115">View details of posted service health</span></span>

<span data-ttu-id="a8a74-p104">既定のビューですべてのサービスと、現在の正常性状態が表示されます。インシデントが発生している現在のサービスは、ビューをフィルターするには、左側の灰色のバーから**インシデント**を選択します。**アドバイザリ**を選択すると、転記、アドバイザリを現在されているサービスのみが表示されます。**サービスのすべて**のビューからは、表示されているサービスの状態をクリックすると勧告またはインシデントの概要ビューが開きます。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![サービスの稼働状態の現在の問題点の表示](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="a8a74-121">アドバイザリやインシデントの概要は、次の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-121">The advisory or incident summary provides the following information:</span></span> 
  
![スクリーン ショット サービス アドバイザリ内のフィールドのラベル付け](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="a8a74-123">問題識別子および概要ステートメントの問題です。</span><span class="sxs-lookup"><span data-stu-id="a8a74-123">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="a8a74-p105">現在の状態です。各潜在的な状態の詳細については、この資料でのステータスの定義を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="a8a74-126">この問題がユーザーに与える影響についての説明です。</span><span class="sxs-lookup"><span data-stu-id="a8a74-126">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="a8a74-p106">問題が開始された時刻と前回のサービス稼働状態のメッセージが更新されました。問題の期間全体では、ソリューションを適用するのには、進行状況を把握することが頻繁にメッセージを転記します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="a8a74-129">ソリューションで作業している間に転記されたすべてのメッセージの履歴を含む、問題に関する詳細を表示する**詳細を表示する**リンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-129">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="a8a74-130">翻訳サービスの稼働状態の詳細情報</span><span class="sxs-lookup"><span data-stu-id="a8a74-130">Translate service health details</span></span>

<span data-ttu-id="a8a74-p107">サービス稼働状態の説明は、リアルタイムに転記され、言語に自動的に翻訳されていない、サービス イベントの詳細は、英語でのみためです。説明を翻訳するには、以下の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="a8a74-133">[翻訳者](https://www.bing.com/translator/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-133">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="a8a74-p108">**サービスの稼働状態**] ページでは、インシデントまたはアドバイザリを選択します。[**詳細を表示する**には、問題についてのテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="a8a74-136">トランスレーターでは、テキストを貼り付け、**翻訳**を選択します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-136">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="a8a74-137">定義</span><span class="sxs-lookup"><span data-stu-id="a8a74-137">Definitions</span></span>

<span data-ttu-id="a8a74-p109">タイム サービスのほとんどは、さらに情報がないと正常な状態で表示されます。サービスに問題がない、問題はアドバイザリや問題のいずれかとして識別され、現在の状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="a8a74-p110">イベントはサービスの稼働状態で表示されているメンテナンスを計画します。**メッセージ センター**を最新に保つことにより、計画的な保守イベントを追跡できます。変更が発生すると、その効果、およびそれを準備する方法を確認する変更の計画として分類されたメッセージにフィルターを適用します。詳細については、 [Office 365 のメッセージ センター](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="a8a74-144">インシデントおよびアドバイザリ</span><span class="sxs-lookup"><span data-stu-id="a8a74-144">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![アドバイザリの情報アイコン](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="a8a74-p111">サービスに示すようにセキュリティ アドバイザリがある場合、一部のユーザーに影響を与えることがある問題に注意してくださいがサービスが利用できます。アドバイザリ、問題を回避するには多くの場合で、問題が断続的に発生する可能性がありますまたはスコープおよびユーザーへの影響は限られています。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![インシデントの感嘆符のアイコン](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="a8a74-p112">サービスに表示されているアクティブなサポート案件がある場合は、重大な問題であるし、サービスまたはサービスの主要な機能が利用できません。ユーザーが電子メールの送受信を行うことができませんなど、サインインできませんでした問題がユーザーに影響します。進行中の問題がある場合は、調査、作業の軽減、およびサービス正常性ダッシュ ボードでの解像度の確認に関する更新プログラムを提供します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="a8a74-153">ステータスの定義</span><span class="sxs-lookup"><span data-stu-id="a8a74-153">Status definitions</span></span>

<span data-ttu-id="a8a74-154">| |</span><span class="sxs-lookup"><span data-stu-id="a8a74-154"></span></span>
|<span data-ttu-id="a8a74-155">**状態**</span><span class="sxs-lookup"><span data-stu-id="a8a74-155">**Status**</span></span>|<span data-ttu-id="a8a74-156">**定義**</span><span class="sxs-lookup"><span data-stu-id="a8a74-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a8a74-157">調査</span><span class="sxs-lookup"><span data-stu-id="a8a74-157">Investigating</span></span>  <br/> |<span data-ttu-id="a8a74-158">潜在的な問題を認識しているし、何が起こっていると影響の範囲の詳細については収集しています。</span><span class="sxs-lookup"><span data-stu-id="a8a74-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span>  <br/> |
|<span data-ttu-id="a8a74-159">サービスの低下</span><span class="sxs-lookup"><span data-stu-id="a8a74-159">Service degradation</span></span>  <br/> |<span data-ttu-id="a8a74-p113">サービスまたは機能の使用に影響を与える可能性のある問題があることを確認したことです。サービスが通常より遅い実行している場合は、この状態を確認することがありますが、断続的な中断、または機能が機能していないなどの場合です。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span>  <br/> |
|<span data-ttu-id="a8a74-162">サービスの中断</span><span class="sxs-lookup"><span data-stu-id="a8a74-162">Service interruption</span></span>  <br/> |<span data-ttu-id="a8a74-p114">問題がサービスにアクセスするユーザーの機能を影響することが判断した場合、このステータスが表示されます。この例では、問題は重要でし、一貫して再現することができます。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span>  <br/> |
|<span data-ttu-id="a8a74-165">サービスを復元します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-165">Restoring service</span></span>  <br/> |<span data-ttu-id="a8a74-166">確認された問題の原因ですが、どのような是正措置を実行して、正常な状態に戻す、サービスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="a8a74-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span>  <br/> |
|<span data-ttu-id="a8a74-167">回復</span><span class="sxs-lookup"><span data-stu-id="a8a74-167">Extended recovery</span></span>  <br/> |<span data-ttu-id="a8a74-p115">この状態では、是正措置がほとんどのユーザーにサービスを復元中ですが、影響を受けるすべてのシステムに到達するまでに時間がかかることを示します。この状態は一時的な永続的な修正を適用するを待つために、影響を減らすために修正を作成した場合も表示があります。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span>  <br/> |
|<span data-ttu-id="a8a74-170">調査の中断</span><span class="sxs-lookup"><span data-stu-id="a8a74-170">Investigation suspended</span></span>  <br/> |<span data-ttu-id="a8a74-p116">潜在的な問題の詳細な調査は、お客様からの追加情報についてさらに調査できるようにするための要求の場合、このステータスが表示されます。操作する必要がある場合お知らせどのようなデータまたはログが必要です。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span>  <br/> |
|<span data-ttu-id="a8a74-173">サービスが復元されました</span><span class="sxs-lookup"><span data-stu-id="a8a74-173">Service restored</span></span>  <br/> |<span data-ttu-id="a8a74-p117">根本的な問題およびサービスが正常な状態に復元された是正措置が解決することを確認しました。失敗の原因を調べるには、問題の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span>  <br/> |
   
## <a name="history"></a><span data-ttu-id="a8a74-176">[履歴]</span><span class="sxs-lookup"><span data-stu-id="a8a74-176">History</span></span>

<span data-ttu-id="a8a74-p118">サービスの稼働状態では、現在のヘルス ステータスを確認し、過去 30 日以内に任意のサービスの勧告やインシデントの履歴を表示することができます。過去のすべてのサービスの稼働状態を表示するには、ページで**サービスの状態****の履歴を表示する**を選択します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![健康履歴へのリンクを表示します。](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="a8a74-180">次のように、選択された期間に転記されたすべてのサービス稼働状態のメッセージの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8a74-180">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![サービス稼働状態の履歴を表示します](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="a8a74-p119">過去 7 日間または過去 30 日間の稼働状態の履歴を表示できます。特定の問題に関する詳細情報を表示するのには任意の行を選択します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="a8a74-184">アップタイムへの取り組みの詳細については、 [Office 365 からの透過的な操作](https://go.microsoft.com/fwlink/?linkid=848695)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8a74-184">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="a8a74-185">フィードバックを送信します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-185">Leave feedback</span></span>

<span data-ttu-id="a8a74-p120">私たちの目標を提供する継続的な問題に関する情報が適切なタイミング、正確、かつ便利であることを確認します。お知らせをどのように行っている、星の評価を選択します。お客様によって提供されたスコアが 1 から 5 つ星に後、は、任意の特定の詳細情報のフィードバックを与えます。当社のサービス稼働状態のシステムを微調整するのには、フィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8a74-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![サービスの稼働状態に関する問題のフィードバック フォーム](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="a8a74-191">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8a74-191">See also</span></span>

[<span data-ttu-id="a8a74-192">Office 365 の管理センターでの活動レポート</span><span class="sxs-lookup"><span data-stu-id="a8a74-192">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

