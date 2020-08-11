---
title: 別の地域の場所に OneDrive サイトを移動する
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Normal
description: サイト移動のスケジュール方法や、ユーザーへの期待の伝達方法など、OneDrive サイトを別の地域の場所に移動する方法についての情報を紹介します。
ms.openlocfilehash: f893102c7460498a56487dc382c58636caea31a8
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606853"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="3711e-103">別の地域の場所に OneDrive サイトを移動する</span><span class="sxs-lookup"><span data-stu-id="3711e-103">Move a OneDrive site to a different geo location</span></span> 

<span data-ttu-id="3711e-p101">OneDrive 地域移動を使用すると、ユーザーの OneDrive を別の地域の場所に移動することができます。OneDrive 地域移動は、SharePoint Online 管理者または Microsoft 365 グローバル管理者によって実行されます。OneDrive の地域移動を開始する前に、OneDrive が移動されていることをユーザーに通知して、移動中にすべてのファイルを閉じることをお勧めします。(移動時に Office クライアントを使用してドキュメントが開かれている場合は、移動の完了時にドキュメントを新しい場所に保存する必要があります)。必要に応じて、移行を将来の時間にスケジュールすることができます。</span><span class="sxs-lookup"><span data-stu-id="3711e-p101">With OneDrive geo move, you can move a user's OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Microsoft 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="3711e-p102">OneDrive サービスは、Azure Blob ストレージを使用してコンテンツを格納します。ユーザーの OneDrive に関連付けられている記憶域 blob は、ユーザーが使用可能な宛先の OneDrive から40日以内に、移行元から移行先の地域の場所に移動されます。ユーザーの OneDrive へのアクセスは、移行先の OneDrive が使用可能になるとすぐに復元されます。</span><span class="sxs-lookup"><span data-stu-id="3711e-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user's OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user's OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="3711e-p103">OneDrive 地域の移動の期間中 (約 2 ～ 6 時間)、ユーザーの OneDrive は読み取り専用に設定されます。ユーザーは今まで通り OneDrive 同期クライアントまたは SharePoint Online の OneDrive サイトからファイルにアクセスできます。OneDrive 地域の移動の完了後に、ユーザーが Microsoft 365 アプリ起動ツールで OneDrive に移動すると、移動先の地域の場所にある OneDrive に自動的に接続されます。同期クライアントは、新しい場所からの同期を自動的に開始します。</span><span class="sxs-lookup"><span data-stu-id="3711e-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Microsoft 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="3711e-115">この記事の手順には、[Microsoft Office SharePoint Online の PowerShell モジュール](https://www.microsoft.com/download/details.aspx?id=35588)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="3711e-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/download/details.aspx?id=35588).</span></span>

## <a name="communicating-to-your-users"></a><span data-ttu-id="3711e-116">ユーザーへの連絡</span><span class="sxs-lookup"><span data-stu-id="3711e-116">Communicating to your users</span></span>

<span data-ttu-id="3711e-p104">OneDrive サイトの地理的場所を移動する際には、想定される動作についてユーザーに通知することが重要です。これは、ユーザーが混乱してヘルプ デスクに問い合わせる可能性を減らすのに役立ちます。移動の前に、次の情報について電子メールでユーザーに連絡してください。</span><span class="sxs-lookup"><span data-stu-id="3711e-p104">When moving OneDrive sites between geo locations, it's important to communicate to your users what to expect. This can help reduce user confusion and calls to your help desk. Email your users before the move and let them know the following information:</span></span>

- <span data-ttu-id="3711e-120">移動開始予定時刻と予定所要時間</span><span class="sxs-lookup"><span data-stu-id="3711e-120">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="3711e-121">ユーザーの OneDrive の移動先となる地理的場所、および新しい場所にアクセスするための URL</span><span class="sxs-lookup"><span data-stu-id="3711e-121">What geo location their OneDrive is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="3711e-122">移動中はファイルを閉じた状態にし、編集を加えてはならないこと。</span><span class="sxs-lookup"><span data-stu-id="3711e-122">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="3711e-123">移動してもファイルの許可と共有は変更されないこと。</span><span class="sxs-lookup"><span data-stu-id="3711e-123">File permissions and sharing will not change as a result of the move.</span></span>
- <span data-ttu-id="3711e-124">[複数地理環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)として期待されること</span><span class="sxs-lookup"><span data-stu-id="3711e-124">What to expect from the [user experience in a multi-geo environment](multi-geo-user-experience.md)</span></span>

<span data-ttu-id="3711e-125">移動が正常に終了した時点で、ユーザーに対し、OneDrive での作業を再開できることを伝える電子メールを送信するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="3711e-125">Be sure to send your users an email when the move has successfully completed informing them that they can resume working in OneDrive.</span></span>

## <a name="scheduling-onedrive-site-moves"></a><span data-ttu-id="3711e-126">OneDrive サイトの移動のスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="3711e-126">Scheduling OneDrive site moves</span></span>

<span data-ttu-id="3711e-p105">OneDrive サイトの移動を事前にスケジュールすることができます (この記事の後半でご説明いたします)。少数のユーザーの移動から始め、ワークフローと連絡手順を確認することをお勧めします。プロセスが満足できるものであった場合、次のように移動をスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="3711e-p105">You can schedule OneDrive site moves in advance (described later in this article). We recommend that you start with a small number of users to validate your workflows and communication strategies. Once you are comfortable with the process, you can schedule moves as follows:</span></span>

- <span data-ttu-id="3711e-130">一度に最大 4,000 件の移動をスケジュールすることができます。</span><span class="sxs-lookup"><span data-stu-id="3711e-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="3711e-131">移動開始後はスケジュールを追加でき、常時最大 4,000 件の保留中の移動をキューに置いておけます。</span><span class="sxs-lookup"><span data-stu-id="3711e-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
- <span data-ttu-id="3711e-132">移動できる OneDrive の最大サイズは 1 テラバイト (1 TB) です。</span><span class="sxs-lookup"><span data-stu-id="3711e-132">The maximum size of a OneDrive that can be moved is 1 terabyte (1 TB).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="3711e-133">OneDrive サイトの移動</span><span class="sxs-lookup"><span data-stu-id="3711e-133">Moving a OneDrive site</span></span>

<span data-ttu-id="3711e-p106">OneDrive の地域移動を実行するには、テナント管理者は、まずユーザーの優先データの場所 (PDL) を適切な地域の場所に設定する必要があります。PDL が設定されたら、OneDrive 地域移動を開始する前に、各 geo の場所間で PDL の更新が同期されるまで、少なくとも24時間待機します。</span><span class="sxs-lookup"><span data-stu-id="3711e-p106">To perform a OneDrive geo move, the tenant administrator must first set the user's Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="3711e-136">Geo move コマンドレットを使用する場合は、次の構文を使用して、ユーザーの現在の OneDrive 地域の場所にある SPO サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="3711e-136">When using the geo move cmdlets, connect to SPO Service at the user's current OneDrive geo location, using the following syntax:</span></span>

`Connect-SPOService -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="3711e-137">例: ユーザー ' Matt@contosoenergy.onmicrosoft.com ' の OneDrive を移動するには、ユーザーの OneDrive が EUR 地域の場所にあるので、[EUR] SharePoint 管理センターに接続します。</span><span class="sxs-lookup"><span data-stu-id="3711e-137">For example: To move OneDrive of user 'Matt@contosoenergy.onmicrosoft.com', connect to EUR SharePoint Admin center as the user's OneDrive is in EUR geo location:</span></span>

`Connect-SPOSservice -url https://contosoenergyeur-admin.sharepoint.com`

![Connect-SPOService コマンドレットを示す PowerShell ウィンドウのスクリーン ショット](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="3711e-139">環境の検証</span><span class="sxs-lookup"><span data-stu-id="3711e-139">Validating the environment</span></span>

<span data-ttu-id="3711e-140">OneDrive 地域移動の開始前に、目的の環境を検証するようにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3711e-140">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="3711e-141">すべての地域の場所に互換性があることを確認するために、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3711e-141">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCrossCompatibilityStatus`

<span data-ttu-id="3711e-142">地域の場所のリストが表示され、その場所間でコンテンツを移動できるかどうかが「互換性あり」として示されます。</span><span class="sxs-lookup"><span data-stu-id="3711e-142">You will see a list of your geo locations and whether content can be moved between will be denoted as "Compatible".</span></span> <span data-ttu-id="3711e-143">コマンドが「互換性なし」を返した場合は、後日、状態の検証をあとでもう一度お試しください。</span><span class="sxs-lookup"><span data-stu-id="3711e-143">If the command returns "Incompatible" please retry validating the status at a later date.</span></span>

<span data-ttu-id="3711e-144">たとえば、サブサイトが含まれている場合、OneDrive は移動できません。</span><span class="sxs-lookup"><span data-stu-id="3711e-144">If a OneDrive contains a subsite, for example, it cannot be moved.</span></span> <span data-ttu-id="3711e-145">OneDrive が移動可能かどうかを検証するには、-ValidationOnly パラメーターを指定した Start-SPOUserAndContentMove コマンドレットを使用してください。</span><span class="sxs-lookup"><span data-stu-id="3711e-145">You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="3711e-p109">OneDrive の移動が可能な状態になっている場合は Success が返されます。移動を妨げる訴訟ホールドまたはサブサイトがある場合は Fail が返されます。OneDrive が移動できる状態になっていることを確認したら、移動を開始します。</span><span class="sxs-lookup"><span data-stu-id="3711e-p109">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="3711e-148">OneDrive 地域移動の開始</span><span class="sxs-lookup"><span data-stu-id="3711e-148">Start a OneDrive geo move</span></span>

<span data-ttu-id="3711e-149">移動を開始するには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3711e-149">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="3711e-150">次に示すパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="3711e-150">Using these parameters:</span></span>

-   <span data-ttu-id="3711e-151">_UserPrincipalName_: 移動する OneDrive を所有するユーザーの UPN です。</span><span class="sxs-lookup"><span data-stu-id="3711e-151">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="3711e-p110">_DestinationDataLocation_ –地域-OneDrive を移動する必要がある場所。これは、ユーザーの優先されるデータの場所と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="3711e-p110">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user's preferred data location.</span></span>

<span data-ttu-id="3711e-154">たとえば、matt@contosoenergy.onmicrosoft.com の OneDrive を EUR から AUS に移動するには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3711e-154">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![Start-SPOUserAndContentMove コマンドレットを示す PowerShell ウィンドウのスクリーン ショット](media/move-onedrive-between-geo-locations-image2.png)

<span data-ttu-id="3711e-156">将来の地域移動をスケジュールするには、次に示すパラメーターのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="3711e-156">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="3711e-p111">_PreferredMoveBeginDate_: 移動は、この指定時刻に開始されると見込まれます。時刻は、協定世界時 (UTC) で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3711e-p111">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="3711e-p112">_PreferredMoveEndDate_: 移動は、最善努力の原則で、この指定時刻に完了すると見込まれます。時刻は、協定世界時 (UTC) で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3711e-p112">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="3711e-161">OneDrive 地域移動のキャンセル</span><span class="sxs-lookup"><span data-stu-id="3711e-161">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="3711e-162">コマンドレットを使用して移動が進行中または完了していない場合は、ユーザーの OneDrive の地域の移動を停止することができます。</span><span class="sxs-lookup"><span data-stu-id="3711e-162">You can stop the geo move of a user's OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="3711e-163">_UserPrincipalName_ は、移動を停止する OneDrive の所有ユーザーの UPN です。</span><span class="sxs-lookup"><span data-stu-id="3711e-163">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="3711e-164">現在の状態の確認</span><span class="sxs-lookup"><span data-stu-id="3711e-164">Determining current status</span></span>

<span data-ttu-id="3711e-165">Get-SPOUserAndContentMoveState コマンドレットを使用して、接続している geo の OneDrive 地域移動の状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="3711e-165">You can check the status of a OneDrive geo move in or out of the geo that you're connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="3711e-166">移動の状態については、次に示す表で説明します。</span><span class="sxs-lookup"><span data-stu-id="3711e-166">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="3711e-167"><strong>状態</strong></span><span class="sxs-lookup"><span data-stu-id="3711e-167"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="3711e-168"><strong>説明</strong></span><span class="sxs-lookup"><span data-stu-id="3711e-168"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="3711e-169">NotStarted</span><span class="sxs-lookup"><span data-stu-id="3711e-169">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="3711e-170">移動は開始されていません。</span><span class="sxs-lookup"><span data-stu-id="3711e-170">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3711e-171">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="3711e-171">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="3711e-172">移動は、検証 (1/4)、バックアップ (2/4)、復元 (3/4)、クリーンアップ (4/4) のいずれかの状態で進行中です。</span><span class="sxs-lookup"><span data-stu-id="3711e-172">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="3711e-173">Success</span><span class="sxs-lookup"><span data-stu-id="3711e-173">Success</span></span></td>
<td align="left"><span data-ttu-id="3711e-174">移動は正常に完了しています。</span><span class="sxs-lookup"><span data-stu-id="3711e-174">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="3711e-175">Failed</span><span class="sxs-lookup"><span data-stu-id="3711e-175">Failed</span></span></td>
<td align="left"><span data-ttu-id="3711e-176">移動は失敗しました。</span><span class="sxs-lookup"><span data-stu-id="3711e-176">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="3711e-177">特定のユーザーの移動の状態を検索するには、UserPrincipalName パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="3711e-177">To find the status of a specific user's move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="3711e-178">接続している地理的位置にあるすべての移動の状態を検索するには、MoveState パラメーターを次のいずれかの値で指定します。 NotStarted、InProgress、Success、Failed、All。</span><span class="sxs-lookup"><span data-stu-id="3711e-178">To find the status of all of the moves in or out of the geo location that you're connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="3711e-179">また、より詳細な移動状態の説明が示されるように、`-Verbose` パラメーターを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="3711e-179">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="3711e-180">ユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="3711e-180">User Experience</span></span>

<span data-ttu-id="3711e-p113">ユーザーの OneDrive を別の地域の場所に移動する場合は、OneDrive のユーザーに最小限の説明についての通知が必要です。移動中は読み取り専用の状態になることの説明に加えて、既存のリンクとアクセス許可は移動の完了後に引き続き期待どおりに動作することも説明します。</span><span class="sxs-lookup"><span data-stu-id="3711e-p113">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="3711e-183">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="3711e-183">OneDrive for Business</span></span>

<span data-ttu-id="3711e-p114">移動が進行中に、ユーザーの OneDrive は読み取り専用に設定されます。移動が完了すると、ユーザーは OneDrive (Microsoft 365 アプリ起動ツールまたは web ブラウザー) に移動すると、新しい地理的位置にある OneDrive にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="3711e-p114">While the move is in progress the user's OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Microsoft 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="3711e-186">OneDrive コンテンツに対するアクセス許可</span><span class="sxs-lookup"><span data-stu-id="3711e-186">Permissions on OneDrive content</span></span>

<span data-ttu-id="3711e-187">OneDrive コンテンツへのアクセス許可を持つユーザーは、移動中および完了後にコンテンツへのアクセスを続けられます。</span><span class="sxs-lookup"><span data-stu-id="3711e-187">Users with permissions to OneDrive content will continue to have access to the content during the move and after it's complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="3711e-188">OneDrive 同期クライアント</span><span class="sxs-lookup"><span data-stu-id="3711e-188">OneDrive Sync Client</span></span> 

<span data-ttu-id="3711e-p115">OneDrive 同期クライアントは、OneDrive 地域移動の完了後に、自動的に新しい OneDrive の場所を検出し、シームレスに同期を転換します。ユーザーは、再度サインインするなどの操作を一切実行する必要がありません。(同期クライアントのバージョン 17.3.6943.0625 以降が必要。)</span><span class="sxs-lookup"><span data-stu-id="3711e-p115">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.  (Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="3711e-192">OneDrive 地域移動の進行中にユーザーがファイルを更新すると、同期クライアントにより、移動が進行している間はファイルの更新が保留されることが通知されます。</span><span class="sxs-lookup"><span data-stu-id="3711e-192">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="3711e-193">共有リンク</span><span class="sxs-lookup"><span data-stu-id="3711e-193">Sharing links</span></span> 

<span data-ttu-id="3711e-194">OneDrive 地域移動の完了時に、移動されたファイルの既存の共有リンクは、新しい地域の場所に自動的にリダイレクトされるようになります。</span><span class="sxs-lookup"><span data-stu-id="3711e-194">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="3711e-195">OneNote エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="3711e-195">OneNote Experience</span></span> 

<span data-ttu-id="3711e-p116">OneNote win32 クライアントと UWP (ユニバーサル) アプリは、OneDrive 地域移動の完了後に、自動的に新しい OneDrive の場所を検出してシームレスにノートブックを同期します。ユーザーは、再度サインインするなどの操作を一切実行する必要がありません。ユーザーが認識できることは、OneDrive 地域移動が進行中のときにノートブックの同期が失敗することのみです。このエクスペリエンスは、次に示す OneNote クライアントのバージョンで利用できます。</span><span class="sxs-lookup"><span data-stu-id="3711e-p116">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="3711e-200">OneNote win32: バージョン 16.0.8326.2096 (以降)</span><span class="sxs-lookup"><span data-stu-id="3711e-200">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="3711e-201">OneNote UWP: バージョン 16.0.8431.1006 (以降)</span><span class="sxs-lookup"><span data-stu-id="3711e-201">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="3711e-202">OneNote モバイル アプリ: バージョン 16.0.8431.1011 (以降)</span><span class="sxs-lookup"><span data-stu-id="3711e-202">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="3711e-203">Teams アプリ</span><span class="sxs-lookup"><span data-stu-id="3711e-203">Teams app</span></span>

<span data-ttu-id="3711e-p117">OneDrive 地域移動の完了時に、ユーザーは Teams アプリで OneDrive ファイルにアクセスできます。さらに、地域移動の前に OneDrive から Teams チャットで共有したファイルは、移動の完了後も引き続き操作できます。</span><span class="sxs-lookup"><span data-stu-id="3711e-p117">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="3711e-206">OneDrive for Business モバイル アプリ (iOS)</span><span class="sxs-lookup"><span data-stu-id="3711e-206">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="3711e-207">OneDrive 地域移動の完了時に、ユーザーは、新しい OneDrive の場所に同期するために、iOS モバイル アプリでサインアウトしてから再度サインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3711e-207">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="3711e-208">既存のフォロー対象グループおよびサイト</span><span class="sxs-lookup"><span data-stu-id="3711e-208">Existing followed groups and sites</span></span>

<span data-ttu-id="3711e-p118">フォロー対象のサイトとグループは、地域の場所に関係なく、ユーザーの OneDrive に表示されます。別の地域の場所にホストされているサイトとグループは、別のタブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3711e-p118">Followed sites and groups will show up in the user's OneDrive regardless of their geo location. Sites and groups hosted in another geo location will open in a separate tab.</span></span>

### <a name="delve-geo-url-updates"></a><span data-ttu-id="3711e-211">Delve 地域 URL の更新</span><span class="sxs-lookup"><span data-stu-id="3711e-211">Delve Geo URL updates</span></span>

<span data-ttu-id="3711e-212">ユーザーは、OneDrive が新しい geo に移動された後にのみ、PDL に対応する Delve geo に送信されます。</span><span class="sxs-lookup"><span data-stu-id="3711e-212">Users will be sent to the Delve geo corresponding to their PDL only after their OneDrive has been moved to the new geo.</span></span>
