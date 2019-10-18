---
title: 別の地域の場所に SharePoint サイトを移動する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: SharePoint サイトを別のジオ位置情報に移動する方法について説明します。
ms.openlocfilehash: f1837942a72881578930f94ad8c4b57dbdb0c649
ms.sourcegitcommit: 59c250b5f62e72fb51fd0b80d2be636ee8078f6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "35422376"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a><span data-ttu-id="89d21-103">別の地域の場所に SharePoint サイトを移動する</span><span class="sxs-lookup"><span data-stu-id="89d21-103">Move a SharePoint site to a different geo location (Preview)</span></span>

<span data-ttu-id="89d21-104">SharePoint サイトの地域移動を使って、SharePoint サイトを複数の地域環境内にある別の地域の場所へ移動させることができます。</span><span class="sxs-lookup"><span data-stu-id="89d21-104">With SharePoint site geo move, you can move SharePoint sites to other geo locations within your multi-geo environment.</span></span>

<span data-ttu-id="89d21-105">次のサイトの種類は地域のジオ位置情報間を移動することができます。</span><span class="sxs-lookup"><span data-stu-id="89d21-105">The following types of site can be moved between geo locations:</span></span>

- <span data-ttu-id="89d21-106">Office 365 グループに接続されたサイト</span><span class="sxs-lookup"><span data-stu-id="89d21-106">Office 365 Group-connected sites</span></span>
- <span data-ttu-id="89d21-107">Office 365 グループと関連付けの無いモダン サイト</span><span class="sxs-lookup"><span data-stu-id="89d21-107">Modern sites without an Office 365 Group association</span></span>
- <span data-ttu-id="89d21-108">従来の SharePoint サイト</span><span class="sxs-lookup"><span data-stu-id="89d21-108">Classic SharePoint sites</span></span>
- <span data-ttu-id="89d21-109">コミュニケーション サイト</span><span class="sxs-lookup"><span data-stu-id="89d21-109">Communication sites</span></span>

<span data-ttu-id="89d21-110">ジオ位置情報間でサイトを移動するには、全体管理者または SharePoint 管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="89d21-110">You must be a Global Administrator or SharePoint Administrator to move a site between geo locations.</span></span>

<span data-ttu-id="89d21-111">サイトの内容によりますが、約4～6時間のSharePoint サイトの地域移動中は、読み取り専用ウィンドウになります。</span><span class="sxs-lookup"><span data-stu-id="89d21-111">There is a read-only window during the SharePoint site geo move of approximately 4-6 hours, depending on site contents.</span></span>
 
## <a name="best-practices"></a><span data-ttu-id="89d21-112">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="89d21-112">Best practices</span></span>

- <span data-ttu-id="89d21-113">その手順に慣れるために、テスト サイトで SharePoint サイトを移動してみてください。</span><span class="sxs-lookup"><span data-stu-id="89d21-113">Try a SharePoint site move on a test site to get familiar with the procedure.</span></span> 
- <span data-ttu-id="89d21-114">スケジュールまたは移動を実行する前に、サイトを移動できるかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="89d21-114">Validate whether the site can be moved prior to scheduling or performing the move.</span></span> 
- <span data-ttu-id="89d21-115">可能であれば、地域間の移動スケジュールはユーザーへの影響を減らすために営業時間外に移動します。</span><span class="sxs-lookup"><span data-stu-id="89d21-115">When possible schedule cross-geo sites moves for outside business hours to reduce user impact.</span></span>
- <span data-ttu-id="89d21-116">サイトの移動前に影響を受けるユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="89d21-116">Communicate with impacted users prior to the sites move.</span></span> 

## <a name="communicating-to-your-users"></a><span data-ttu-id="89d21-117">ユーザーへの連絡</span><span class="sxs-lookup"><span data-stu-id="89d21-117">Communicating to your users</span></span>

<span data-ttu-id="89d21-118">ジオ位置情報間で SharePoint サイトを移動する場合は、想定される動作をサイトのユーザー (一般的にサイトの編集権限がある全てのユーザー) に通知することが重要です。</span><span class="sxs-lookup"><span data-stu-id="89d21-118">When moving SharePoint sites between geo locations, it's important to communicate to the sites' users (generally anyone with the ability to edit the site) what to expect.</span></span> <span data-ttu-id="89d21-119">これにより、ユーザーの混乱やヘルプデスクへの問い合わせを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="89d21-119">This can help reduce user confusion and calls to your help desk.</span></span> <span data-ttu-id="89d21-120">移動する前に、次の情報をサイトのユーザーへメールで連絡してください。</span><span class="sxs-lookup"><span data-stu-id="89d21-120">Email your sites' users before the move and let them know the following information:</span></span>

- <span data-ttu-id="89d21-121">移動開始予定時刻と予定所要時間</span><span class="sxs-lookup"><span data-stu-id="89d21-121">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="89d21-122">サイトの移動先となるジオ位置情報と、新しい位置情報にアクセスするための URL</span><span class="sxs-lookup"><span data-stu-id="89d21-122">What geo location their site is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="89d21-123">移動中はファイルを閉じ、編集を加えないこと。</span><span class="sxs-lookup"><span data-stu-id="89d21-123">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="89d21-124">移動してもファイルのアクセス許可と共有設定は変更されないこと。</span><span class="sxs-lookup"><span data-stu-id="89d21-124">File permissions and sharing will not change because of the move.</span></span>
- <span data-ttu-id="89d21-125">複数の地域環境でのユーザー エクスペリエンスから予想されること</span><span class="sxs-lookup"><span data-stu-id="89d21-125">What to expect from the user experience in a multi-geo environment</span></span>

<span data-ttu-id="89d21-126">移動が正常に終了した時点で、作業を再開できることを伝える電子メールをユーザーに送信してください。</span><span class="sxs-lookup"><span data-stu-id="89d21-126">Be sure to send your sites' users an email when the move has successfully completed informing them that they can resume working on their sites.</span></span>

## <a name="scheduling-sharepoint-site-moves"></a><span data-ttu-id="89d21-127">SharePoint サイトのスケジュール設定に移動します</span><span class="sxs-lookup"><span data-stu-id="89d21-127">Scheduling SharePoint site moves</span></span>

<span data-ttu-id="89d21-128">SharePoint サイトの移動を事前にスケジュールすることができます (この記事の後半でご説明します)。</span><span class="sxs-lookup"><span data-stu-id="89d21-128">You can schedule SharePoint site moves in advance (described later in this article).</span></span> <span data-ttu-id="89d21-129">次のように移動をスケジュールします:</span><span class="sxs-lookup"><span data-stu-id="89d21-129">You can schedule moves as follows:</span></span>

- <span data-ttu-id="89d21-130">一度に最大 4,000 件の移動をスケジュールすることができます。</span><span class="sxs-lookup"><span data-stu-id="89d21-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="89d21-131">移動開始後はスケジュールを追加でき、常時最大 4,000 件の保留中の移動をキューに置いておけます。</span><span class="sxs-lookup"><span data-stu-id="89d21-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
 
<span data-ttu-id="89d21-132">SharePoint サイトの地域移動を後でスケジュール設定するには、移動開始時に次のいずれかのパラメーターを含みます:</span><span class="sxs-lookup"><span data-stu-id="89d21-132">To schedule a SharePoint site geo move for a later time, include one of the following parameters when you start the move:</span></span>
- <span data-ttu-id="89d21-133">`PreferredMoveBeginDate` -移動は、この指定時刻に開始されると見込まれます。</span><span class="sxs-lookup"><span data-stu-id="89d21-133">`PreferredMoveBeginDate` – The move will likely begin at this specified time.</span></span>
- <span data-ttu-id="89d21-134">`PreferredMoveEndDate` -移動は、ベストエフォート方式でこの指定時刻に完了すると見込まれます。</span><span class="sxs-lookup"><span data-stu-id="89d21-134">`PreferredMoveEndDate` – The move will likely be completed by this specified time, on a best effort basis.</span></span> 

<span data-ttu-id="89d21-135">両方のパラメーターの時間を協定世界時 (UTC) で指定してください。</span><span class="sxs-lookup"><span data-stu-id="89d21-135">Time must be specified in Coordinated Universal Time (UTC) for both parameters.</span></span>

## <a name="moving-the-site"></a><span data-ttu-id="89d21-136">サイトの移動</span><span class="sxs-lookup"><span data-stu-id="89d21-136">Moving the site</span></span>

<span data-ttu-id="89d21-137">SharePoint サイトの地域移動は　サイトがあるジオ位置情報でSharePoint の管理 URLから接続し、実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89d21-137">SharePoint site geo move requires that you connect and perform the move from the SharePoint Admin URL in the geo location where the site is.</span></span>

<span data-ttu-id="89d21-138">例えば、サイト URLが https://contosohealthcare.sharepoint.com/sites/Turbinesの場合、 SharePoint の管理 URL https://contosohealthcare-admin.sharepoint.com:に接続します。</span><span class="sxs-lookup"><span data-stu-id="89d21-138">For example, if the site URL is https://contosohealthcare.sharepoint.com/sites/Turbines, connect to the SharePoint Admin URL at https://contosohealthcare-admin.sharepoint.com:</span></span>

`connect-sposervice -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a><span data-ttu-id="89d21-139">環境の検証</span><span class="sxs-lookup"><span data-stu-id="89d21-139">Validating the environment</span></span>

<span data-ttu-id="89d21-140">サイトの移動をスケジュールする前に、サイトが移動できるか検証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89d21-140">We recommend that before scheduling any site move, you perform a validation to ensure that the site can be moved.</span></span>

<span data-ttu-id="89d21-141">サイトの移動はサポートしていません:</span><span class="sxs-lookup"><span data-stu-id="89d21-141">We do not support moving sites with:</span></span>
-   <span data-ttu-id="89d21-142">Business Connectivity Services</span><span class="sxs-lookup"><span data-stu-id="89d21-142">Business Connectivity Services</span></span>
-   <span data-ttu-id="89d21-143">InfoPath フォーム</span><span class="sxs-lookup"><span data-stu-id="89d21-143">InfoPath forms</span></span> 

<span data-ttu-id="89d21-144">すべてのジオ位置情報に互換性があることを確認するために、 `Get-SPOGeoMoveCrossCompatibilityStatus`を実行します。</span><span class="sxs-lookup"><span data-stu-id="89d21-144">To ensure all geo locations are compatible, run `Get-SPOGeoMoveCrossCompatibilityStatus`.</span></span> <span data-ttu-id="89d21-145">すべてのジオ位置情報と、その環境が移動先のジオ位置情報と互換性があるかどうかを表示します。</span><span class="sxs-lookup"><span data-stu-id="89d21-145">This will display all your geo locations and whether the environment is compatible with the destination geo location.</span></span>

<span data-ttu-id="89d21-146">サイトでの検証のみのチェックを実行するには、`-ValidationOnly` パラメーターで`Start-SPOSiteContentMove`を使い、サイトが移動できるか検証します。</span><span class="sxs-lookup"><span data-stu-id="89d21-146">To perform a validation-only check on your site, use `Start-SPOSiteContentMove` with the `-ValidationOnly` parameter to validate if the site is able to be moved.</span></span> <span data-ttu-id="89d21-147">例:</span><span class="sxs-lookup"><span data-stu-id="89d21-147">For example:</span></span>

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

<span data-ttu-id="89d21-148">サイトが移動準備完了の場合、*正常に完了*　と返ってきます。ブロックされている状態がある場合は、*失敗*と返ってきます。</span><span class="sxs-lookup"><span data-stu-id="89d21-148">This will return *Success* if the site is ready to be moved or *Fail* if any of blocked conditions are present.</span></span>

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a><span data-ttu-id="89d21-149">Office 365 グループに関連のないサイトへSharePoint サイトの地域移動を開始する</span><span class="sxs-lookup"><span data-stu-id="89d21-149">Start a SharePoint site geo move for a site with no associated Office 365 Group</span></span>

<span data-ttu-id="89d21-150">既定値では、サイトの最初のURL は移動先のジオ位置情報の URL に変更されます。</span><span class="sxs-lookup"><span data-stu-id="89d21-150">By default, initial URL for the site will change to the URL of the destination geo location.</span></span> <span data-ttu-id="89d21-151">例:</span><span class="sxs-lookup"><span data-stu-id="89d21-151">For example:</span></span>

<span data-ttu-id="89d21-152">https://Contoso.sharepoint.com/sites/projectx から https://ContosoEUR.sharepoint.com/sites/projectx</span><span class="sxs-lookup"><span data-stu-id="89d21-152">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projectx</span></span>

<span data-ttu-id="89d21-153">Office 365 グループとの関連がないサイトは、`-DestinationUrl` パラメーターを使ってサイト名を変更できます。</span><span class="sxs-lookup"><span data-stu-id="89d21-153">For sites with no Office 365 Group association, you can also rename the site by using the `-DestinationUrl` parameter.</span></span> <span data-ttu-id="89d21-154">例:</span><span class="sxs-lookup"><span data-stu-id="89d21-154">For example:</span></span>

<span data-ttu-id="89d21-155">https://Contoso.sharepoint.com/sites/projectx から https://ContosoEUR.sharepoint.com/sites/projecty</span><span class="sxs-lookup"><span data-stu-id="89d21-155">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projecty</span></span>

<span data-ttu-id="89d21-156">サイトの移動を開始するには、次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="89d21-156">To start the site move, run:</span></span>

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Start-SPOSiteContentMove コマンドレットを示す PowerShell ウィンドウのスクリーン ショット](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a><span data-ttu-id="89d21-158">Office 365 グループ接続のサイトへ SharePoint サイトの地域移動を開始する</span><span class="sxs-lookup"><span data-stu-id="89d21-158">Start a SharePoint site geo move for an Office 365 Group-connected site</span></span>

<span data-ttu-id="89d21-159">Office 365 グループ接続のサイトへ移動するには、全体管理者は、優先されるデータの場所 (PDL) を Office 365 グループの属性に最初に変更しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="89d21-159">To move an Office 365 Group-connected site, the global administrator must first change the Preferred Data Location (PDL) attribute for the Office 365 Group.</span></span>

<span data-ttu-id="89d21-160">Office 365 グループの PDL をセットする:</span><span class="sxs-lookup"><span data-stu-id="89d21-160">To set the PDL for an Office 365 Group:</span></span>

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
<span data-ttu-id="89d21-161">PDL を更新したら、サイトの移動を開始できます。</span><span class="sxs-lookup"><span data-stu-id="89d21-161">Once you have updated the PDL, you can start the site move:</span></span> 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a><span data-ttu-id="89d21-162">SharePoint サイトジオへの移動をキャンセルする</span><span class="sxs-lookup"><span data-stu-id="89d21-162">Cancel a SharePoint site geo move</span></span>

<span data-ttu-id="89d21-163">その移動が実行されていない、または`Stop-SPOSiteContentMove`コマンドレットを使って完了した場合、SharePoint サイトの地域移動を停止できます。</span><span class="sxs-lookup"><span data-stu-id="89d21-163">You can stop a SharePoint site geo move, provided the move is not in progress or completed by using the `Stop-SPOSiteContentMove` cmdlet.</span></span>

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a><span data-ttu-id="89d21-164">SharePoint サイトの地域移動の状況を確認する</span><span class="sxs-lookup"><span data-stu-id="89d21-164">Determining the status of a SharePoint site geo move</span></span>

<span data-ttu-id="89d21-165">次のコマンドレットを使用して接続している地域外でのサイトの移動状況を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="89d21-165">You can determine the status of a site move in our out of the geo that you are connected to by using the following cmdlets:</span></span>

- <span data-ttu-id="89d21-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (グループ接続以外のサイト)</span><span class="sxs-lookup"><span data-stu-id="89d21-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (non-Group-connected sites)</span></span>
- <span data-ttu-id="89d21-167">Get-SPOUnifiedGroupMoveState (グループ接続のサイト)</span><span class="sxs-lookup"><span data-stu-id="89d21-167">Get-SPOUnifiedGroupMoveState (Group-connected sites)</span></span>

<span data-ttu-id="89d21-168">`-SourceSiteUrl` パラメーターを使用して、移動状況を確認したいサイトを指定します。</span><span class="sxs-lookup"><span data-stu-id="89d21-168">Use the `-SourceSiteUrl` parameter to specify the site for which you want to see move status.</span></span>

<span data-ttu-id="89d21-169">移動状況については、次に示す表で説明します。</span><span class="sxs-lookup"><span data-stu-id="89d21-169">The move statuses are described in the following table.</span></span>

|<span data-ttu-id="89d21-170">状態</span><span class="sxs-lookup"><span data-stu-id="89d21-170">Status</span></span>|<span data-ttu-id="89d21-171">説明</span><span class="sxs-lookup"><span data-stu-id="89d21-171">Description</span></span>|
|:-----|:----------|
|<span data-ttu-id="89d21-172">トリガーの準備</span><span class="sxs-lookup"><span data-stu-id="89d21-172">Ready to Trigger</span></span>|<span data-ttu-id="89d21-173">移動は開始されていません。</span><span class="sxs-lookup"><span data-stu-id="89d21-173">The move has not started.</span></span>|
|<span data-ttu-id="89d21-174">スケジュール済み</span><span class="sxs-lookup"><span data-stu-id="89d21-174">Scheduled</span></span>|<span data-ttu-id="89d21-175">移動がキューにあり、まだ開始されていません。</span><span class="sxs-lookup"><span data-stu-id="89d21-175">The move is in queue but has not yet started.</span></span>|
|<span data-ttu-id="89d21-176">InProgress (n/4)</span><span class="sxs-lookup"><span data-stu-id="89d21-176">InProgress (n/4)</span></span>|<span data-ttu-id="89d21-177">移動は、検証 (1/4)、バックアップ (2/4)、復元 (3/4)、クリーンアップ (4/4) のいずれかの状態で進行中です。</span><span class="sxs-lookup"><span data-stu-id="89d21-177">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span>|
|<span data-ttu-id="89d21-178">Success</span><span class="sxs-lookup"><span data-stu-id="89d21-178">Success</span></span>|<span data-ttu-id="89d21-179">移動は正常に完了しています。</span><span class="sxs-lookup"><span data-stu-id="89d21-179">The move has completed successfully.</span></span>|
|<span data-ttu-id="89d21-180">Failed</span><span class="sxs-lookup"><span data-stu-id="89d21-180">Failed</span></span>|<span data-ttu-id="89d21-181">移動は失敗しました。</span><span class="sxs-lookup"><span data-stu-id="89d21-181">The move failed.</span></span>|

<span data-ttu-id="89d21-182">移動に関する追加情報を確認する `-Verbose` オプションを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="89d21-182">You can also apply the `-Verbose` option to see additional information about the move.</span></span>

## <a name="user-experience"></a><span data-ttu-id="89d21-183">ユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="89d21-183">User experience</span></span>

<span data-ttu-id="89d21-184">サイトが別のジオ位置情報へ移動した場合は、サイトユーザーに最小限の中断があることを通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89d21-184">Site users should notice minimal disruption when their site is moved to a different geo location.</span></span> <span data-ttu-id="89d21-185">移動中は簡単な読み取り専用状態になることに加えて、既存のリンクとアクセス許可は移動の完了後に引き続き想定通りに操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="89d21-185">Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="site"></a><span data-ttu-id="89d21-186">サイト</span><span class="sxs-lookup"><span data-stu-id="89d21-186">Site</span></span>

<span data-ttu-id="89d21-187">移動の実行中は、サイトは読み取り専用に設定されます。</span><span class="sxs-lookup"><span data-stu-id="89d21-187">While the move is in progress the site is set to read-only.</span></span> <span data-ttu-id="89d21-188">移動の完了後に、ブックマークまたは他のリンクをクリックすると、新しいジオ位置情報の新しいサイトがユーザーに指定されます。</span><span class="sxs-lookup"><span data-stu-id="89d21-188">Once the move is completed, the user is directed to the new site in the new geo location when they click on bookmarks or other links to the site.</span></span>

### <a name="permissions"></a><span data-ttu-id="89d21-189">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="89d21-189">Permissions</span></span>

<span data-ttu-id="89d21-190">サイトへのアクセス許可を持つユーザーは、移動中および移動完了後のサイトに引き続きアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="89d21-190">Users with permissions to site will continue to have access to the site during the move and after it's complete.</span></span>

### <a name="sync-client"></a><span data-ttu-id="89d21-191">同期クライアント</span><span class="sxs-lookup"><span data-stu-id="89d21-191">Sync Client</span></span>

<span data-ttu-id="89d21-192">サイトの移動が完了後に、同期クライアントは自動的に新しいサイトの場所を検出し、シームレスに同期を転送します。</span><span class="sxs-lookup"><span data-stu-id="89d21-192">The sync client will automatically detect and seamlessly transfer syncing to the new site location once the site move is complete.</span></span> <span data-ttu-id="89d21-193">ユーザーはもう一度サインインまたはその他のアクションをする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="89d21-193">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="89d21-194">(バージョン 17.3.6943.0625 またはそれ以降の同期クライアントが必要です)</span><span class="sxs-lookup"><span data-stu-id="89d21-194">(Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="89d21-195">移動の進行中にユーザーがファイルを更新すると、移動の実行中はファイルのアップロードが保留されることを同期クライアントが通知します。</span><span class="sxs-lookup"><span data-stu-id="89d21-195">If a user updates a file while the move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="89d21-196">共有リンク</span><span class="sxs-lookup"><span data-stu-id="89d21-196">Sharing links</span></span>

<span data-ttu-id="89d21-197">SharePoint サイトの地域移動の完了時に、移動されたファイルの既存の共有リンクは、新しいジオ位置情報に自動的にリダイレクトされるようになります。</span><span class="sxs-lookup"><span data-stu-id="89d21-197">When the SharePoint site geo move completes, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="most-recently-used-files-in-office-mru"></a><span data-ttu-id="89d21-198">最近使用された Office のファイル (MRU)</span><span class="sxs-lookup"><span data-stu-id="89d21-198">Most Recently Used files in Office (MRU)</span></span>

<span data-ttu-id="89d21-199">MRU サービスは、移動が完了するとサイトとコンテンツの URL が更新されます。</span><span class="sxs-lookup"><span data-stu-id="89d21-199">The MRU service is updated with the site url and its content URLs once the move completes.</span></span> <span data-ttu-id="89d21-200">Word、Excel、PowerPoint に適用されます。</span><span class="sxs-lookup"><span data-stu-id="89d21-200">This applies to Word, Excel, and PowerPoint.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="89d21-201">OneNote エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="89d21-201">OneNote experience</span></span>

<span data-ttu-id="89d21-202">OneNote win32 クライアントと UWP (ユニバーサル) アプリは、サイトの移動完了後に新しいサイトの場所を自動的に検出し、シームレスにノートブックを同期します。</span><span class="sxs-lookup"><span data-stu-id="89d21-202">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new site location once site move is complete.</span></span> <span data-ttu-id="89d21-203">ユーザーはもう一度サインインまたはその他のアクションをする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="89d21-203">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="89d21-204">サイトの移動が進行中にノートブックの同期が失敗する時だけ、ユーザーにインジケーターで表示されます。</span><span class="sxs-lookup"><span data-stu-id="89d21-204">The only visible indicator to the user is notebook sync would fail when site move is in progress.</span></span> <span data-ttu-id="89d21-205">このエクスペリエンスは、次の OneNote クライアント バージョンで使用できます:</span><span class="sxs-lookup"><span data-stu-id="89d21-205">This experience is available on the following OneNote client versions:</span></span>

- <span data-ttu-id="89d21-206">OneNote win32: バージョン 16.0.8326.2096 (以降)</span><span class="sxs-lookup"><span data-stu-id="89d21-206">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>
- <span data-ttu-id="89d21-207">OneNote UWP: バージョン 16.0.8431.1006 (以降)</span><span class="sxs-lookup"><span data-stu-id="89d21-207">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>
- <span data-ttu-id="89d21-208">OneNote モバイル アプリ: バージョン 16.0.8431.1011 (以降)</span><span class="sxs-lookup"><span data-stu-id="89d21-208">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-applicable-to-office-365-group-connected-sites"></a><span data-ttu-id="89d21-209">チーム (Office 365 グループ接続のサイトに適用)</span><span class="sxs-lookup"><span data-stu-id="89d21-209">Teams (applicable to Office 365 Group connected sites)</span></span>

<span data-ttu-id="89d21-210">SharePoint サイトの地域の移動が完了すると、ユーザーはチーム アプリにある Office 365 グループ サイトのファイルにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="89d21-210">When the SharePoint site geo move completes, users will have access to their Office 365 Group site files on the Teams app.</span></span> <span data-ttu-id="89d21-211">さらに、地域移動前にサイトからチーム チャット経由で共有したファイルは、移動が完了後に引き続き操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="89d21-211">Additionally, files shared via Teams chat from their site prior to geo move will continue to work after move is complete.</span></span>

### <a name="sharepoint-mobile-app-iosandroid"></a><span data-ttu-id="89d21-212">iOS/Android 用 SharePoint モバイル アプリ</span><span class="sxs-lookup"><span data-stu-id="89d21-212">SharePoint Mobile App (iOS/Android)</span></span>

<span data-ttu-id="89d21-213">SharePoint モバイル アプリは、地域間で互換性があり、サイトの新しいジオ位置情報を検出することができます。</span><span class="sxs-lookup"><span data-stu-id="89d21-213">The SharePoint Mobile App is cross geo compatible and able to detect the site's new geo location.</span></span>

### <a name="sharepoint-workflows"></a><span data-ttu-id="89d21-214">SharePoint ワークフロー</span><span class="sxs-lookup"><span data-stu-id="89d21-214">SharePoint workflows</span></span>

<span data-ttu-id="89d21-215">SharePoint 2013 ワークフローは、サイトの移動後に再発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89d21-215">SharePoint 2013 workflows need to be republished after the site move.</span></span> <span data-ttu-id="89d21-216">SharePoint 2010 ワークフローは、正常に動作し続ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="89d21-216">SharePoint 2010 workflows should continue to function normally.</span></span>

### <a name="apps"></a><span data-ttu-id="89d21-217">アプリ</span><span class="sxs-lookup"><span data-stu-id="89d21-217">Apps</span></span>

<span data-ttu-id="89d21-218">アプリを使用してサイトを移動すると、移動先のジオ位置情報に接続できない場合があるので、サイトの新しいジオ位置情報でアプリを再インスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89d21-218">If you are moving a site with apps, you must re-instantiate the app in the site's new geo location as the app and its connections may not be available in the destination geo location.</span></span>

### <a name="flow"></a><span data-ttu-id="89d21-219">フロー</span><span class="sxs-lookup"><span data-stu-id="89d21-219">Flow</span></span>

<span data-ttu-id="89d21-220">ほとんどの場合、フローは SharePoint サイトの地域移動後に引き続き操作することができるようになります。</span><span class="sxs-lookup"><span data-stu-id="89d21-220">In most cases Flows will continue to work after a SharePoint site geo move.</span></span> <span data-ttu-id="89d21-221">移動が完了したらテストすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89d21-221">We recommend that you test them once the move has completed.</span></span>

### <a name="powerapps"></a><span data-ttu-id="89d21-222">PowerApps</span><span class="sxs-lookup"><span data-stu-id="89d21-222">PowerApps</span></span>

<span data-ttu-id="89d21-223">PowerAppsは、移動先の位置情報で再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89d21-223">PowerApps need to be recreated in the destination location.</span></span>

### <a name="data-movement-between-geo-locations"></a><span data-ttu-id="89d21-224">ジオ位置情報間のデータ移動</span><span class="sxs-lookup"><span data-stu-id="89d21-224">Data movement between geo locations</span></span>

<span data-ttu-id="89d21-225">SharePoint にサイトとそのファイルに関連付けられているメタデータが保存されている場合は、コンテンツの Azure Blob ストレージを使用します。</span><span class="sxs-lookup"><span data-stu-id="89d21-225">SharePoint uses Azure Blob storage for its content, while the metadata associated with sites and its files is stored within SharePoint.</span></span> <span data-ttu-id="89d21-226">その元のジオ位置情報から移動先のジオ位置情報へ移動後、サービスも関連付けられている Blob ストレージへ移動します。</span><span class="sxs-lookup"><span data-stu-id="89d21-226">After the site is moved from its source geo location to its destination geo location, the service will also move its associated Blob Storage.</span></span> <span data-ttu-id="89d21-227">BLOB ストレージは約40日で移動を完了します。</span><span class="sxs-lookup"><span data-stu-id="89d21-227">Blob Storage moves complete in approximately 40 days.</span></span> 
