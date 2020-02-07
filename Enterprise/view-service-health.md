---
title: Office 365 サービスの正常性をチェックする方法
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: サポートを呼び出す前に Office 365 サービスの正常性の状態を表示して、アクティブなサービスが中断していないかどうかを確認します。
ms.openlocfilehash: 2d5b12e4443395d5a9a16fd6934ca68a99601416
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843968"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="56740-103">Office 365 サービスの正常性をチェックする方法</span><span class="sxs-lookup"><span data-stu-id="56740-103">How to check Office 365 service health</span></span>

<span data-ttu-id="56740-104">[![管理センターについて知らせるラベルが変更されていますので、詳細については、aka.ms/aboutM365preview を参照してください。](media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)</span><span class="sxs-lookup"><span data-stu-id="56740-104">[![Label to let you know the admin center is changing and you can find more details at aka.ms/aboutM365preview.](media/O365-Admin-AdminCenterChanging.png)](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview?view=o365-worldwide)</span></span>

<span data-ttu-id="56740-105">[管理センター](https://go.microsoft.com/fwlink/p/?linkid=2024339)の Office 365 **Service health**ページで、Web、YAMMER、Microsoft Dynamics CRM、microsoft Intune cloud services の office など、microsoft サービスの正常性を確認できます。</span><span class="sxs-lookup"><span data-stu-id="56740-105">You can view the health of your Microsoft services, including Office on the web, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services, on the Office 365 **Service health** page in the [admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339).</span></span> <span data-ttu-id="56740-106">クラウド サービスの問題が発生している場合は、サポートに連絡するかトラブルシューティングに時間を費やす前に、サービス正常性を確認することで、解決に向けて取り組み中の既知の問題であるかどうかを判別できます。</span><span class="sxs-lookup"><span data-stu-id="56740-106">If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span>

<span data-ttu-id="56740-107">サービスポータルにサインインできない場合は、[[サービスの状態] ページ](https://status.office365.com)を使用して既知の問題があるかどうかを確認し、テナントへのログインを妨げることができます。</span><span class="sxs-lookup"><span data-stu-id="56740-107">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="56740-108">サービス正常性の確認方法</span><span class="sxs-lookup"><span data-stu-id="56740-108">How to check service health</span></span>

1. <span data-ttu-id="56740-109">の管理センター [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339)に移動し、管理者アカウントでサインインします。</span><span class="sxs-lookup"><span data-stu-id="56740-109">Go to the admin center at [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339), and sign in with an admin account.</span></span>

    > [!NOTE]
    > <span data-ttu-id="56740-110">全体管理者またはサービス管理者の役割を割り当てられているユーザーは、サービス正常性を表示できます。</span><span class="sxs-lookup"><span data-stu-id="56740-110">People who are assigned the global admin or service administrator role can view service health.</span></span> <span data-ttu-id="56740-111">Exchange、SharePoint、および Skype for Business の管理者がサービス正常性を表示できるようにする場合も、ユーザーにはサービス管理者の役割が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="56740-111">To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> <span data-ttu-id="56740-112">サービス正常性を表示できる役割の詳細については、「[管理者の役割につい](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56740-112">For more information about roles that can view service health, see [About admin roles](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles?view=o365-worldwide#roles-available-in-the-microsoft-365-admin-center).</span></span>
  
2. <span data-ttu-id="56740-113">新しい管理センターを使用していない場合は、ホームページで、右上隅にある [**新しい管理センターの**切り替えを試みる] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56740-113">If you are not using the new admin center, on the Home page, select the **Try the new admin center** toggle in the upper-right corner.</span></span>

3. <span data-ttu-id="56740-114">サービス正常性を表示するには、管理センターで、**ヘルス** > **サービスの状態**に移動するか、または**ホームダッシュボード**の**サービス正常性**カードを選択します。</span><span class="sxs-lookup"><span data-stu-id="56740-114">To view service health, in the admin center, go to **Health** > **Service health**, or select the **Service health** card on the **Home dashboard**.</span></span> <span data-ttu-id="56740-115">ダッシュボードカードは、アクティブなサービスの問題があるかどうかを示し、[詳細な**サービス正常性**] ページにリンクします。</span><span class="sxs-lookup"><span data-stu-id="56740-115">The dashboard card indicates whether there is an active service issue and links to the detailed **Service health** page.</span></span>
  
4. <span data-ttu-id="56740-116">[**サービス正常性**] ページでは、各クラウドサービスの正常性状態が表形式で示されています。</span><span class="sxs-lookup"><span data-stu-id="56740-116">On the **Service health** page, the health state of each cloud service is shown in a table format.</span></span>

   ![View of current issues in service health](media/service-health-all-services.png)

<span data-ttu-id="56740-118">[**すべてのサービス**] タブ (既定のビュー) には、すべてのサービスとその現在の正常性の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56740-118">The **All services** tab (the default view) shows all services and their current health state.</span></span> <span data-ttu-id="56740-119">アイコンと [**状態**] 列は各サービスの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="56740-119">An icon and the **Status** column indicate the state of each service.</span></span> <span data-ttu-id="56740-120">現在インシデントが発生しているサービスにビューをフィルター処理するには、ページの上部にある [**インシデント**] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="56740-120">To filter your view to services currently experiencing an incident, select the **Incidents** tab at the top of the page.</span></span> <span data-ttu-id="56740-121">[**アドバイザリ**] タブを選択すると、現在アドバイザリが投稿されているサービスのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56740-121">Selecting the **Advisories** tab will show only services that currently have an advisory posted.</span></span> <span data-ttu-id="56740-122">[**履歴**] タブには、解決されたインシデントとアドバイザリの履歴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56740-122">The **History** tab shows the history of incidents and advisories that have been resolved.</span></span>

<span data-ttu-id="56740-123">Office 365 サービスで問題が発生し、[**サービス正常性**] ページに表示されていない場合は、[**問題を報告**する] を選択して、短縮形を完了します。</span><span class="sxs-lookup"><span data-stu-id="56740-123">If you're experiencing an issue with an Office 365 service and you don’t see it listed on the **Service health** page, tell us about it by selecting **Report an issue**, and completing the short form.</span></span> <span data-ttu-id="56740-124">この記事では、他の組織からの関連データとレポートを調べて、その問題がどの程度広くなっているかを確認し、サービスによって発生したものであるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="56740-124">We’ll look at related data and reports from other organizations to see how widespread the issue is, and if it originated with our service.</span></span> <span data-ttu-id="56740-125">その場合は、**サービスの正常性**ページに新しいインシデントまたはアドバイザリとして追加し、その解決方法を追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="56740-125">If it did, we’ll add it as a new incident or advisory on the **Service health** page, where you can track its resolution.</span></span> <span data-ttu-id="56740-126">約30分以内に一覧に表示されない場合は、サポートに連絡して問題を解決することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="56740-126">If you don’t see it appear on the list within about 30 minutes, consider contacting support to resolve the issue.</span></span>

> [!TIP]
> <span data-ttu-id="56740-127">モバイル デバイスで [Office 365 Admin アプリ](https://go.microsoft.com/fwlink/p/?linkid=627216)を使って、サービス正常性を表示することもできます。これはプッシュ通知により、常に最新情報を入手する優れた手段です。</span><span class="sxs-lookup"><span data-stu-id="56740-127">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="56740-128">投稿されたサービス正常性の詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="56740-128">View details of posted service health</span></span>

<span data-ttu-id="56740-129">[**すべてのサービス**] ビューで、[サービスの状態] を選択すると、アドバイザリまたはインシデントの概要ビューが開きます。</span><span class="sxs-lookup"><span data-stu-id="56740-129">On the **All services** view, selecting the service status will open a summary view of advisories or incidents.</span></span>
  
![サービス勧告を示すスクリーンショット](media/service-health-advisory.png)

<span data-ttu-id="56740-131">勧告またはインシデントの概要では、以下の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="56740-131">The advisory or incident summary provides the following information:</span></span>

- <span data-ttu-id="56740-132">**タイトル**-問題の概要。</span><span class="sxs-lookup"><span data-stu-id="56740-132">**Title** - A summary of the problem.</span></span>
- <span data-ttu-id="56740-133">**Service** -影響を受けるサービスの名前。</span><span class="sxs-lookup"><span data-stu-id="56740-133">**Service** - The name of the affected service.</span></span>
- <span data-ttu-id="56740-134">**ID** -問題の数値 id。</span><span class="sxs-lookup"><span data-stu-id="56740-134">**ID** - A numeric identifier for the problem.</span></span>
- <span data-ttu-id="56740-135">**状態**-この問題がサービスに及ぼす影響。</span><span class="sxs-lookup"><span data-stu-id="56740-135">**Status** - How this problem affects the service.</span></span>
- <span data-ttu-id="56740-136">**開始時刻**-懸案事項が開始された時刻。</span><span class="sxs-lookup"><span data-stu-id="56740-136">**Start time** - The time when the issue started.</span></span>
- <span data-ttu-id="56740-137">**最終更新**日時-サービス正常性メッセージが最後に更新された日時。</span><span class="sxs-lookup"><span data-stu-id="56740-137">**Last updated** - The last time that the service health message was updated.</span></span> <span data-ttu-id="56740-138">ソリューションを適用している間の進行状況を知らせるために、頻繁にメッセージを投稿します。</span><span class="sxs-lookup"><span data-stu-id="56740-138">We post frequent messages to let you know the progress that we're making in applying a solution.</span></span>

<span data-ttu-id="56740-139">[問題のタイトル] を選択して、問題に関する詳細情報を示す [問題の詳細] ページを表示します。これには、ソリューションで作業している間に投稿されたすべてのメッセージの[履歴](#history)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="56740-139">Select the issue title to see the issue detail page, which shows more information about the issue, including the [history](#history) of all messages posted while we work on a solution.</span></span>

![問題の詳細を示すスクリーンショット](media/service-health-advisory-detail.png)

### <a name="translate-service-health-details"></a><span data-ttu-id="56740-141">サービス正常性の詳細を翻訳する</span><span class="sxs-lookup"><span data-stu-id="56740-141">Translate service health details</span></span>

<span data-ttu-id="56740-p107">サービス正常性の説明はリアルタイムで投稿されるため、各国語に自動的には翻訳されず、サービス イベントの詳細は英語のみとなります。説明を翻訳するには、次の手順に従います</span><span class="sxs-lookup"><span data-stu-id="56740-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="56740-144">1.[翻訳ツール](https://www.bing.com/translator/)に移動します。</span><span class="sxs-lookup"><span data-stu-id="56740-144">Go to [Translator](https://www.bing.com/translator/).</span></span>

2. <span data-ttu-id="56740-p108">[ **サービス正常性**] ページで、インシデントまたは勧告を選択します。[ **詳細の表示**] で、問題に関するテキストをコピーします。</span><span class="sxs-lookup"><span data-stu-id="56740-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>

3. <span data-ttu-id="56740-147">翻訳ツールで、テキストを貼り付けて、[ **翻訳**] を選びます。</span><span class="sxs-lookup"><span data-stu-id="56740-147">In Translator, paste the text and choose **Translate**.</span></span>

### <a name="definitions"></a><span data-ttu-id="56740-148">定義</span><span class="sxs-lookup"><span data-stu-id="56740-148">Definitions</span></span>

<span data-ttu-id="56740-149">ほとんどの場合、サービスは正常として表示され、それ以上の情報はありません。</span><span class="sxs-lookup"><span data-stu-id="56740-149">Most of the time, services will appear as healthy with no further information.</span></span> <span data-ttu-id="56740-150">サービスに問題がある場合、問題は勧告またはインシデントとして認識され、現在の状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56740-150">When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="56740-p110">計画済みメンテナンス イベントはサービス正常性には表示されません。常に **メッセージ センター**を確認することで、計画済みメンテナンス イベントを追跡できます。フィルタリングして [変更の計画] として分類されたメッセージに絞り込み、変更が発生する時期、その影響、およびそのための準備方法を確認します。詳細については、「[Office 365 のメッセージ センター](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56740-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span>
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="56740-155">インシデントおよび勧告</span><span class="sxs-lookup"><span data-stu-id="56740-155">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="56740-p111">サービスが勧告と示された場合、一部のユーザーに影響する問題が認識されています。ただし、サービスは引き続き使用可能です。勧告では、多くの場合、回避策があり、問題は一時的なものである可能性があるか、または範囲およびユーザーへの影響は限られます。</span><span class="sxs-lookup"><span data-stu-id="56740-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="56740-p112">サービスがアクティブ インシデントと示された場合、重大な問題であり、サービスまたはサービスの主な機能は使用できません。たとえば、ユーザーはメールの送受信やサインインができない可能性があります。インシデントはユーザーに顕著な影響を与えます。進行中にインシデントが発生した場合は、サービス正常性ダッシュボードで調査、軽減への取り組み、解決策の確認に関する更新プログラムを提供します。</span><span class="sxs-lookup"><span data-stu-id="56740-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |

### <a name="status-definitions"></a><span data-ttu-id="56740-164">状態の定義</span><span class="sxs-lookup"><span data-stu-id="56740-164">Status definitions</span></span>

|<span data-ttu-id="56740-165">**状態**</span><span class="sxs-lookup"><span data-stu-id="56740-165">**Status**</span></span>|<span data-ttu-id="56740-166">**定義**</span><span class="sxs-lookup"><span data-stu-id="56740-166">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="56740-167">**Investigating**</span><span class="sxs-lookup"><span data-stu-id="56740-167">**Investigating**</span></span> | <span data-ttu-id="56740-168">潜在的な問題は認識されており、現状と影響範囲に関する詳細情報を収集中です。</span><span class="sxs-lookup"><span data-stu-id="56740-168">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="56740-169">**サービスの低下**</span><span class="sxs-lookup"><span data-stu-id="56740-169">**Service degradation**</span></span> | <span data-ttu-id="56740-p113">サービスまたは機能の使用に影響する可能性のある問題があることが確認されています。サービスの実行に通常より長い時間がかかる場合、一時的に中断している場合、機能が動作していない場合などにこの状態が示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="56740-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="56740-172">**サービス中断**</span><span class="sxs-lookup"><span data-stu-id="56740-172">**Service interruption**</span></span> | <span data-ttu-id="56740-p114">問題がサービスへのアクセスを妨げると判断された場合にこの状態が示されます。この場合、問題は重要なものであり、常に再現できます。</span><span class="sxs-lookup"><span data-stu-id="56740-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="56740-175">**サービスの復元中**</span><span class="sxs-lookup"><span data-stu-id="56740-175">**Restoring service**</span></span> | <span data-ttu-id="56740-176">問題の原因は特定されており、対応策はわかっています。また、サービスを正常な状態に戻している段階です。</span><span class="sxs-lookup"><span data-stu-id="56740-176">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="56740-177">**拡張復旧**</span><span class="sxs-lookup"><span data-stu-id="56740-177">**Extended recovery**</span></span> | <span data-ttu-id="56740-p115">この状態は、ほとんどのユーザーに対するサービスを復元するための対応策が進行中ですが、影響を受けるすべてのシステムに適用されるまでは時間がかかることを示します。また、永続的な修正プログラムが適用されるのを待機する間に、一時的な修正プログラムで影響を減らした場合、この状態が表示されることもあります。</span><span class="sxs-lookup"><span data-stu-id="56740-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="56740-180">**調査中断**</span><span class="sxs-lookup"><span data-stu-id="56740-180">**Investigation suspended**</span></span> | <span data-ttu-id="56740-p116">潜在的な問題の詳細な調査で、さらに調査できるようにお客様からの追加情報を要求する場合は、この状態が示されます。お客様にアクションを求める場合は、必要なデータまたはログをお知らせします。</span><span class="sxs-lookup"><span data-stu-id="56740-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="56740-183">**サービスが復元されました**</span><span class="sxs-lookup"><span data-stu-id="56740-183">**Service restored**</span></span> | <span data-ttu-id="56740-p117">対応策によって根本的な問題が解決され、サービスが正常な状態に復元されたことが確認されています。原因を確認するには、問題の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="56740-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="56740-186">**誤検知**</span><span class="sxs-lookup"><span data-stu-id="56740-186">**False positive**</span></span> | <span data-ttu-id="56740-187">詳細な調査を行った後、サービスが正常であり、設計どおりに動作していることを確認しました。</span><span class="sxs-lookup"><span data-stu-id="56740-187">After a detailed investigation, we’ve confirmed the service is healthy and operating as designed.</span></span> <span data-ttu-id="56740-188">サービスへの影響がなかったか、またはサービスの外部からインシデントが発生した可能性があります。</span><span class="sxs-lookup"><span data-stu-id="56740-188">No impact to the service was observed or the cause of the incident originated outside of the service.</span></span> |
|<span data-ttu-id="56740-189">**公開後のインシデントレポート**</span><span class="sxs-lookup"><span data-stu-id="56740-189">**Post-incident report published**</span></span> | <span data-ttu-id="56740-190">問題が発生した場合に問題が発生しないように、根本原因の情報や次の手順を含む特定の問題について、インシデント報告後のレポートを公開しています。</span><span class="sxs-lookup"><span data-stu-id="56740-190">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |

### <a name="history"></a><span data-ttu-id="56740-191">履歴</span><span class="sxs-lookup"><span data-stu-id="56740-191">History</span></span>

<span data-ttu-id="56740-192">サービス正常性により、現在の正常性の状態を確認し、過去30日間にテナントに影響を受けたサービスアドバイザリとインシデントの履歴を確認できます。</span><span class="sxs-lookup"><span data-stu-id="56740-192">Service health lets you look at current health status and view the history of any service advisories and incidents that have affected your tenant in the past 30 days.</span></span> <span data-ttu-id="56740-193">すべてのサービスの過去の状態を表示するには、[問題の詳細] ページの [**履歴の表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56740-193">To view the past health of all services, select **View history** on the issue detail page.</span></span>
  
![Show link to health history](media/service-health-view-history.png)
  
<span data-ttu-id="56740-195">選択した期間に投稿されたすべての正常性メッセージのリストは、以下のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="56740-195">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/service-health-history.png)
  
<span data-ttu-id="56740-197">任意の行を展開して、問題の詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="56740-197">Expand any row to view more details about the issue.</span></span>
  
<span data-ttu-id="56740-198">稼働時間に対するコミットメントの詳細については、「 [Office 365 からの透過的な操作](https://go.microsoft.com/fwlink/?linkid=848695)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56740-198">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="56740-199">フィードバックを送信する</span><span class="sxs-lookup"><span data-stu-id="56740-199">Leave feedback</span></span>

<span data-ttu-id="56740-p120">弊社の目標は、進行中の問題について、タイムリーで正確かつ役立つ情報を確実に提供することです。弊社の活動を評価する場合は、星の評価を選択してください。1 つから 5 つの星で評価した後、詳細についてフィードバックできます。お客様からのフィードバックを基に、サービス正常性システムを微調整いたします。</span><span class="sxs-lookup"><span data-stu-id="56740-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="56740-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="56740-204">See also</span></span>

[<span data-ttu-id="56740-205">Microsoft 365 管理センターのアクティビティレポート</span><span class="sxs-lookup"><span data-stu-id="56740-205">Activity Reports in the Microsoft 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)