---
title: Office 365 サービスの正常性をチェックする方法
ms.author: robmazz
author: robmazz
manager: laurawi
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
ms.openlocfilehash: 7e04e1309c990ccced67663576285f7276603ccc
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651191"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="bacd3-103">Office 365 サービスの正常性をチェックする方法</span><span class="sxs-lookup"><span data-stu-id="bacd3-103">How to check Office 365 service health</span></span>

<span data-ttu-id="bacd3-p101">Office 365**サービスの状態**のページの管理センターでは、Office 365、Yammer、Microsoft Dynamics CRM では、Microsoft Intune クラウド サービスの稼働状況を表示できます。クラウド サービスの問題が発生した場合、は、サポートに連絡するか、問題解決の時間を費やす前に進行中の解像度での既知の問題があるかどうかを判断するのにはサービスの稼働状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="bacd3-106">サービス ポータルにサインインできない場合は、テナントにログインできない場合の既知の問題をチェックする[サービスの状態] ページ](https://status.office365.com)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="bacd3-107">サービス正常性の確認方法</span><span class="sxs-lookup"><span data-stu-id="bacd3-107">How to check service health</span></span>

1. <span data-ttu-id="bacd3-108">[https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) に移動し、管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="bacd3-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="bacd3-p102">全体管理者またはサービス管理者の役割を割り当てられているユーザーは、サービス正常性を表示できます。Exchange、SharePoint、および Skype for Business の管理者がサービス正常性を表示できるようにする場合も、ユーザーにはサービス管理者の役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="bacd3-p103">**状態**に移動を開くにはサービスの稼働状態、管理センターで、 > **サービスの稼働状態**、**ホームのダッシュ ボード**上の**サービスの稼働状態のカード**をクリックします。ダッシュ ボードのカードでは、アクティブなサービスの問題と詳細なサービスの稼働状態のページへのリンクがあるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p103">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="bacd3-114">それぞれのクラウド サービスの正常性状態は表形式で表示され、考えられる状態を示すアイコンが付いています。</span><span class="sxs-lookup"><span data-stu-id="bacd3-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="bacd3-115">モバイル デバイスで [Office 365 Admin アプリ](https://go.microsoft.com/fwlink/p/?linkid=627216)を使って、サービス正常性を表示することもできます。これはプッシュ通知により、常に最新情報を入手する優れた手段です。</span><span class="sxs-lookup"><span data-stu-id="bacd3-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="bacd3-116">投稿されたサービス正常性の詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="bacd3-116">View details of posted service health</span></span>

<span data-ttu-id="bacd3-p104">既定のビューですべてのサービスと、現在の正常性状態が表示されます。インシデントが発生している現在のサービスは、ビューをフィルターするには、左側の灰色のバーから**インシデント**を選択します。**アドバイザリ**を選択すると、転記、アドバイザリを現在されているサービスのみが表示されます。**サービスのすべて**のビューからは、表示されているサービスの状態をクリックすると勧告またはインシデントの概要ビューが開きます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="bacd3-122">勧告またはインシデントの概要では、以下の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-122">The advisory or incident summary provides the following information:</span></span> 
  
![スクリーン ショット サービス アドバイザリ内のフィールドのラベル付け](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="bacd3-124">問題の ID と要約。</span><span class="sxs-lookup"><span data-stu-id="bacd3-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="bacd3-p105">現在の状態。考えられる状態のそれぞれの説明については、この記事の状態の定義を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="bacd3-127">この問題がユーザーにどのように影響するかについての説明。</span><span class="sxs-lookup"><span data-stu-id="bacd3-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="bacd3-p106">問題の開始時刻と、サービス正常性メッセージの最後の更新時刻。問題の期間中は、解決策の適用状況を知らせるメッセージが頻繁に投稿されます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="bacd3-130">[ **詳細の表示**] リンクを選択すると、解決策の取り組み中に投稿されるすべてのメッセージの履歴を含む、問題の詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="bacd3-131">サービス正常性の詳細を翻訳する</span><span class="sxs-lookup"><span data-stu-id="bacd3-131">Translate service health details</span></span>

<span data-ttu-id="bacd3-p107">サービス正常性の説明はリアルタイムで投稿されるため、各国語に自動的には翻訳されず、サービス イベントの詳細は英語のみとなります。説明を翻訳するには、次の手順に従います</span><span class="sxs-lookup"><span data-stu-id="bacd3-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="bacd3-134">1.[翻訳ツール](https://www.bing.com/translator/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="bacd3-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="bacd3-p108">[ **サービス正常性**] ページで、インシデントまたは勧告を選択します。[ **詳細の表示**] で、問題に関するテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="bacd3-137">翻訳ツールで、テキストを貼り付けて、[ **翻訳**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="bacd3-138">定義</span><span class="sxs-lookup"><span data-stu-id="bacd3-138">Definitions</span></span>

<span data-ttu-id="bacd3-p109">ほとんどの場合、サービスは正常として表示され、それ以上の情報は示されません。サービスに問題がある場合、問題は勧告またはインシデントとして認識され、現在の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="bacd3-p110">計画済みメンテナンス イベントはサービス正常性には表示されません。常に **メッセージ センター**を確認することで、計画済みメンテナンス イベントを追跡できます。フィルタリングして [変更の計画] として分類されたメッセージに絞り込み、変更が発生する時期、その影響、およびそのための準備方法を確認します。詳細については、「[Office 365 のメッセージ センター](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="bacd3-145">インシデントおよび勧告</span><span class="sxs-lookup"><span data-stu-id="bacd3-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="bacd3-p111">サービスが勧告と示された場合、一部のユーザーに影響する問題が認識されています。ただし、サービスは引き続き使用可能です。勧告では、多くの場合、回避策があり、問題は一時的なものである可能性があるか、または範囲およびユーザーへの影響は限られます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="bacd3-p112">サービスがアクティブ インシデントと示された場合、重大な問題であり、サービスまたはサービスの主な機能は使用できません。たとえば、ユーザーはメールの送受信やサインインができない可能性があります。インシデントはユーザーに顕著な影響を与えます。進行中にインシデントが発生した場合は、サービス正常性ダッシュボードで調査、軽減への取り組み、解決策の確認に関する更新プログラムを提供します。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="bacd3-154">状態の定義</span><span class="sxs-lookup"><span data-stu-id="bacd3-154">Status definitions</span></span>

|<span data-ttu-id="bacd3-155">**状態**</span><span class="sxs-lookup"><span data-stu-id="bacd3-155">**Status**</span></span>|<span data-ttu-id="bacd3-156">**定義**</span><span class="sxs-lookup"><span data-stu-id="bacd3-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="bacd3-157">**調査中**</span><span class="sxs-lookup"><span data-stu-id="bacd3-157">**Investigating**</span></span> | <span data-ttu-id="bacd3-158">潜在的な問題は認識されており、現状と影響範囲に関する詳細情報を収集中です。</span><span class="sxs-lookup"><span data-stu-id="bacd3-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="bacd3-159">**サービスの低下**</span><span class="sxs-lookup"><span data-stu-id="bacd3-159">**Service degradation**</span></span> | <span data-ttu-id="bacd3-p113">サービスまたは機能の使用に影響する可能性のある問題があることが確認されています。サービスの実行に通常より長い時間がかかる場合、一時的に中断している場合、機能が動作していない場合などにこの状態が示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="bacd3-162">**サービス中断**</span><span class="sxs-lookup"><span data-stu-id="bacd3-162">**Service interruption**</span></span> | <span data-ttu-id="bacd3-p114">問題がサービスへのアクセスを妨げると判断された場合にこの状態が示されます。この場合、問題は重要なものであり、常に再現できます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="bacd3-165">**サービスの復元中**</span><span class="sxs-lookup"><span data-stu-id="bacd3-165">**Restoring service**</span></span> | <span data-ttu-id="bacd3-166">問題の原因は特定されており、対応策はわかっています。また、サービスを正常な状態に戻している段階です。</span><span class="sxs-lookup"><span data-stu-id="bacd3-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="bacd3-167">**拡張復旧**</span><span class="sxs-lookup"><span data-stu-id="bacd3-167">**Extended recovery**</span></span> | <span data-ttu-id="bacd3-p115">この状態は、ほとんどのユーザーに対するサービスを復元するための対応策が進行中ですが、影響を受けるすべてのシステムに適用されるまでは時間がかかることを示します。また、永続的な修正プログラムが適用されるのを待機する間に、一時的な修正プログラムで影響を減らした場合、この状態が表示されることもあります。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="bacd3-170">**調査中断**</span><span class="sxs-lookup"><span data-stu-id="bacd3-170">**Investigation suspended**</span></span> | <span data-ttu-id="bacd3-p116">潜在的な問題の詳細な調査で、さらに調査できるようにお客様からの追加情報を要求する場合は、この状態が示されます。お客様にアクションを求める場合は、必要なデータまたはログをお知らせします。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="bacd3-173">**サービスが復元されました**</span><span class="sxs-lookup"><span data-stu-id="bacd3-173">**Service restored**</span></span> | <span data-ttu-id="bacd3-p117">対応策によって根本的な問題が解決され、サービスが正常な状態に復元されたことが確認されています。原因を確認するには、問題の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="bacd3-176">**インシデント後のレポートを公開**</span><span class="sxs-lookup"><span data-stu-id="bacd3-176">**Post-incident report published**</span></span> | <span data-ttu-id="bacd3-177">ルートの原因に関する情報と同様の問題が発生しないことを確認するのには次の手順を含む特定の問題についての投稿のインシデント レポートを公開しましたしました。</span><span class="sxs-lookup"><span data-stu-id="bacd3-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="bacd3-178">[履歴]</span><span class="sxs-lookup"><span data-stu-id="bacd3-178">History</span></span>

<span data-ttu-id="bacd3-p118">サービス正常性では現在の正常性の状態を確認し、過去 30 日間のサービスの勧告とインシデントの履歴を表示することができます。すべてのサービスの過去の正常性を表示するには、[ **サービス正常性**] ページで [ **履歴の表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="bacd3-182">選択した期間に投稿されたすべての正常性メッセージのリストは、以下のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="bacd3-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="bacd3-p119">過去 7 日間または過去 30 日間の稼働状態の履歴を表示できます。特定の問題に関する詳細情報を表示するのには任意の行を選択します。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="bacd3-186">アップタイムへの取り組みの詳細については、 [Office 365 からの透過的な操作](https://go.microsoft.com/fwlink/?linkid=848695)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bacd3-186">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="bacd3-187">フィードバックを送信する</span><span class="sxs-lookup"><span data-stu-id="bacd3-187">Leave feedback</span></span>

<span data-ttu-id="bacd3-p120">弊社の目標は、進行中の問題について、タイムリーで正確かつ役立つ情報を確実に提供することです。弊社の活動を評価する場合は、星の評価を選択してください。1 つから 5 つの星で評価した後、詳細についてフィードバックできます。お客様からのフィードバックを基に、サービス正常性システムを微調整いたします。</span><span class="sxs-lookup"><span data-stu-id="bacd3-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="bacd3-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="bacd3-193">See also</span></span>

[<span data-ttu-id="bacd3-194">Office 365 管理センターのアクティビティ レポート</span><span class="sxs-lookup"><span data-stu-id="bacd3-194">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

