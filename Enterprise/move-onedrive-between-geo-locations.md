---
title: 別の地域の場所に OneDrive サイトを移動する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 別の地域の場所に OneDrive サイトを移動する方法について説明します。
ms.openlocfilehash: 80768d0838d1d5d072d3e221c4c2b4b1af78dae6
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="6137c-103">別の地域の場所に OneDrive サイトを移動する</span><span class="sxs-lookup"><span data-stu-id="6137c-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="6137c-p101">OneDrive 地域移動により、ユーザーの OneDrive を別の地域に移動できます。OneDrive 地域移動は、SharePoint Online 管理者または Office 365 全体管理者が実行します。OneDrive 地域移動を開始する前に、移動する OneDrive の所有ユーザーに通知して、移動中はすべてのファイルを閉じておくように勧告してください (移動中に、ユーザーが Office クライアントを使用してドキュメントを開いている場合は、移動の完了時にドキュメントを新しい場所に保存する必要があります)。移動は、将来に実行するように必要に応じてスケジュールできます。</span><span class="sxs-lookup"><span data-stu-id="6137c-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="6137c-p102">OneDrive サービスでは、コンテンツの保存に Azure Blob Storage が使用されます。ユーザーの OneDrive に関連付けられた Storage Blob は、ユーザーが移動先の OneDrive を利用できるようになってから 40 日以内に移動元から移動先の地域の場所に移動されます。ユーザーの OneDrive へのアクセスは、移動先の OneDrive が利用できるようになった直後に復元されます。</span><span class="sxs-lookup"><span data-stu-id="6137c-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="6137c-p103">OneDrive 地域移動の期間中 (約 2 ～ 6 時間)、ユーザーの OneDrive は読み取り専用に設定されます。その間、ユーザーは OneDrive 同期クライアントまたは SharePoint Online の OneDrive サイトからファイルにアクセスできます。OneDrive 地域移動の完了後に、ユーザーが Office 365 アプリ起動ツールで OneDrive に移動すると、移動先の地域の場所にある OneDrive に自動的に接続されます。同期クライアントは、新しい場所からの同期を自動的に開始します。</span><span class="sxs-lookup"><span data-stu-id="6137c-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="6137c-115">この記事の手順には、[Microsoft Office SharePoint Online の PowerShell モジュール](https://www.microsoft.com/en-us/download/details.aspx?id=35588)が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6137c-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="communicating-to-your-users"></a><span data-ttu-id="6137c-116">ユーザーへの連絡</span><span class="sxs-lookup"><span data-stu-id="6137c-116">Communicating to your users</span></span>

<span data-ttu-id="6137c-p104">OneDrive サイトの地理的場所を移動する際には、想定される動作についてユーザーに通知することが重要です。これは、ユーザーが混乱してヘルプ デスクに問い合わせる可能性を減らすのに役立ちます。移動の前に、次の情報について電子メールでユーザーに連絡してください:</span><span class="sxs-lookup"><span data-stu-id="6137c-p104">When moving OneDrive sites between geo-locations, it's important to communicate to your users what to expect. This can help reduce user confusion and calls to your help desk. Email your users before the move and let them know the following information:</span></span>

- <span data-ttu-id="6137c-120">移動開始予定時刻と予定所要時間</span><span class="sxs-lookup"><span data-stu-id="6137c-120">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="6137c-121">ユーザーの OneDrive の移動先となる地理的場所、および新しい場所にアクセスするための URL</span><span class="sxs-lookup"><span data-stu-id="6137c-121">What geo location their OneDrive is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="6137c-122">移動中はファイルを閉じた状態にし、編集を加えてはならないこと。</span><span class="sxs-lookup"><span data-stu-id="6137c-122">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="6137c-123">移動してもファイルの許可と共有は変更されないこと。</span><span class="sxs-lookup"><span data-stu-id="6137c-123">File permissions and sharing will not change as a result of the move.</span></span>
- <span data-ttu-id="6137c-124">[複数地理環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)として期待されること</span><span class="sxs-lookup"><span data-stu-id="6137c-124">What to expect from the [user experience in a multi-geo environment](multi-geo-user-experience.md)</span></span>

<span data-ttu-id="6137c-125">移動が正常に終了した時点で、ユーザーに対し、OneDrive での作業を再開できることを伝える電子メールを送信するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="6137c-125">Be sure to send your users an email when the move has successfully completed informing them that they can resume working in OneDrive.</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="6137c-126">OneDrive サイトの移動</span><span class="sxs-lookup"><span data-stu-id="6137c-126">Moving a OneDrive site</span></span>

<span data-ttu-id="6137c-p105">OneDrive 地域移動を実行するには、まず、管理者がユーザーの優先されるデータの場所 (PDL) を適切な地域の場所に設定しておく必要があります。PDL の設定後、PDL の更新内容が地域の場所全体に同期されるまで少なくとも 24 時間待機してから、OneDrive 地域移動を開始します。</span><span class="sxs-lookup"><span data-stu-id="6137c-p105">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="6137c-129">地域移動のコマンドレットを使用するときには、ユーザーの現在の OneDrive 地域の場所で、次の構文を使用して SPO サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="6137c-129">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="6137c-130">たとえば、ユーザー 'Matt@contosoenergy.onmicrosoft.com' の OneDrive を移動する場合は、このユーザーの OneDrive が EUR 地域の場所にあるため、次のようにして EUR の SharePoint 管理センターに接続します。</span><span class="sxs-lookup"><span data-stu-id="6137c-130">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="6137c-131">環境の検証</span><span class="sxs-lookup"><span data-stu-id="6137c-131">Validating the environment</span></span>

<span data-ttu-id="6137c-132">OneDrive 地域移動の開始前に、目的の環境を検証するようにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6137c-132">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="6137c-133">すべての地域の場所に互換性があることを確認するために、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="6137c-133">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="6137c-p106">訴訟ホールドの状態になっている場合やサブサイトが含まれている場合、OneDrive は移動できません。OneDrive が移動可能かどうかを検証するには、-ValidationOnly パラメーターを指定した Start-SPOUserAndContentMove コマンドレットを使用してください。</span><span class="sxs-lookup"><span data-stu-id="6137c-p106">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="6137c-p107">OneDrive の移動が可能な状態になっている場合は Success が返されます。移動を妨げる訴訟ホールドまたはサブサイトがある場合は Fail が返されます。OneDrive が移動できる状態になっていることを確認したら、移動を開始します。</span><span class="sxs-lookup"><span data-stu-id="6137c-p107">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="6137c-138">OneDrive 地域移動の開始</span><span class="sxs-lookup"><span data-stu-id="6137c-138">Start a OneDrive geo move</span></span>

<span data-ttu-id="6137c-139">移動を開始するには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="6137c-139">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="6137c-140">次に示すパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="6137c-140">Using these parameters:</span></span>

-   <span data-ttu-id="6137c-141">_UserPrincipalName_: 移動する OneDrive を所有するユーザーの UPN です。</span><span class="sxs-lookup"><span data-stu-id="6137c-141">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="6137c-p108">_DestinationDataLocation_: OneDrive の移動先にする必要がある地域の場所です。これは、ユーザーの優先されるデータの場所と同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6137c-p108">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="6137c-144">OneDrive 地域移動を開始する前に、`ValidationOnly` を指定した `Get-SPOGeoMoveStateCompatibility` を実行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6137c-144">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="6137c-145">たとえば、matt@contosoenergy.onmicrosoft.com の OneDrive を EUR から AUS に移動するには、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="6137c-145">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="6137c-146">将来の地域移動をスケジュールするには、次に示すパラメーターのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="6137c-146">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="6137c-p109">_PreferredMoveBeginDate_: 移動は、この指定時刻に開始されると見込まれます。時刻は、協定世界時 (UTC) で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6137c-p109">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="6137c-p110">_PreferredMoveEndDate_: 移動は、最善努力の原則で、この指定時刻に完了すると見込まれます。時刻は、協定世界時 (UTC) で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6137c-p110">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="6137c-151">OneDrive 地域移動のキャンセル</span><span class="sxs-lookup"><span data-stu-id="6137c-151">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="6137c-152">ユーザーの OneDrive の地域移動は、その移動が進行中または完了済みでない場合、次のコマンドレットを使用して停止できます。</span><span class="sxs-lookup"><span data-stu-id="6137c-152">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="6137c-153">_UserPrincipalName_ は、移動を停止する OneDrive の所有ユーザーの UPN です。</span><span class="sxs-lookup"><span data-stu-id="6137c-153">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="6137c-154">現在の状態の確認</span><span class="sxs-lookup"><span data-stu-id="6137c-154">Determining current status</span></span>

<span data-ttu-id="6137c-155">OneDrive 地域移動の状態は、Get-SPOUserAndContentMoveState コマンドレットを使用することで、現在接続している地域の内外で確認できます。</span><span class="sxs-lookup"><span data-stu-id="6137c-155">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="6137c-156">移動の状態については、次に示す表で説明します。</span><span class="sxs-lookup"><span data-stu-id="6137c-156">The fields in alerts are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="6137c-157"><strong>状態</strong></span><span class="sxs-lookup"><span data-stu-id="6137c-157"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="6137c-158"><strong>説明</strong></span><span class="sxs-lookup"><span data-stu-id="6137c-158"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="6137c-159">NotStarted</span><span class="sxs-lookup"><span data-stu-id="6137c-159">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="6137c-160">移動は開始されていません。</span><span class="sxs-lookup"><span data-stu-id="6137c-160">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="6137c-161">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="6137c-161">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="6137c-162">移動は、検証 (1/4)、バックアップ (2/4)、復元 (3/4)、クリーンアップ (4/4) のいずれかの状態で進行中です。</span><span class="sxs-lookup"><span data-stu-id="6137c-162">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="6137c-163">Success</span><span class="sxs-lookup"><span data-stu-id="6137c-163">Success</span></span></td>
<td align="left"><span data-ttu-id="6137c-164">移動は正常に完了しています。</span><span class="sxs-lookup"><span data-stu-id="6137c-164">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="6137c-165">Failed</span><span class="sxs-lookup"><span data-stu-id="6137c-165">Failed</span></span></td>
<td align="left"><span data-ttu-id="6137c-166">移動は失敗しました。</span><span class="sxs-lookup"><span data-stu-id="6137c-166">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="6137c-167">特定のユーザーの移動の状態を調べるには、UserPrincipalName パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="6137c-167">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="6137c-168">現在接続している地域の場所の内外で、すべての移動の状態を調べるには、MoveState パラメーターに NotStarted、InProgress、Success、Failed、All のいずれかの値を使用します。</span><span class="sxs-lookup"><span data-stu-id="6137c-168">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="6137c-169">また、より詳細な移動状態の説明が示されるように、`-Verbose` パラメーターを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="6137c-169">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="6137c-170">ユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="6137c-170">User Experience</span></span>

<span data-ttu-id="6137c-p111">ユーザーの OneDrive を別の地域の場所に移動する場合は、OneDrive のユーザーに最小限の説明についての通知が必要です。移動中は読み取り専用の状態になることの説明に加えて、既存のリンクとアクセス許可は移動の完了後に引き続き期待どおりに動作することも説明します。</span><span class="sxs-lookup"><span data-stu-id="6137c-p111">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="6137c-173">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="6137c-173">OneDrive for Business</span></span>

<span data-ttu-id="6137c-p112">移動が進行中のときには、ユーザーの OneDrive が読み取り専用に設定されます。移動の完了後に、ユーザーが Office 365 アプリ起動ツールまたは Web ブラウザーで OneDrive に移動すると、ユーザーは新しい地域の場所の OneDrive に転送されます。</span><span class="sxs-lookup"><span data-stu-id="6137c-p112">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="6137c-176">OneDrive コンテンツに対するアクセス許可</span><span class="sxs-lookup"><span data-stu-id="6137c-176">Permissions on OneDrive content</span></span>

<span data-ttu-id="6137c-177">OneDrive コンテンツへのアクセス許可を持つユーザーは、移動中および移動完了後のコンテンツに引き続きアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6137c-177">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="6137c-178">OneDrive 同期クライアント</span><span class="sxs-lookup"><span data-stu-id="6137c-178">OneDrive Sync Client</span></span> 

<span data-ttu-id="6137c-p113">OneDrive 同期クライアントは、OneDrive 地域移動の完了後に、自動的に新しい OneDrive の場所を検出し、シームレスに同期を転換します。ユーザーは、再度サインインするなどの操作を一切実行する必要がありません。(同期クライアントのバージョン 17.3.6943.0625 以降が必要。)</span><span class="sxs-lookup"><span data-stu-id="6137c-p113">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.  (Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="6137c-182">OneDrive 地域移動の進行中にユーザーがファイルを更新すると、同期クライアントにより、移動が進行している間はファイルの更新が保留されることが通知されます。</span><span class="sxs-lookup"><span data-stu-id="6137c-182">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="6137c-183">共有リンク</span><span class="sxs-lookup"><span data-stu-id="6137c-183">Sharing links</span></span> 

<span data-ttu-id="6137c-184">OneDrive 地域移動の完了時に、移動されたファイルの既存の共有リンクは、新しい地域の場所に自動的にリダイレクトされるようになります。</span><span class="sxs-lookup"><span data-stu-id="6137c-184">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="6137c-185">OneNote エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="6137c-185">OneNote Experience</span></span> 

<span data-ttu-id="6137c-p114">OneNote win32 クライアントと UWP (ユニバーサル) アプリは、OneDrive 地域移動の完了後に、自動的に新しい OneDrive の場所を検出してシームレスにノートブックを同期します。ユーザーは、再度サインインするなどの操作を一切実行する必要がありません。ユーザーが認識できることは、OneDrive 地域移動が進行中のときにノートブックの同期が失敗することのみです。このエクスペリエンスは、次に示す OneNote クライアントのバージョンで利用できます。</span><span class="sxs-lookup"><span data-stu-id="6137c-p114">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="6137c-190">OneNote win32: バージョン 16.0.8326.2096 (以降)</span><span class="sxs-lookup"><span data-stu-id="6137c-190">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="6137c-191">OneNote UWP: バージョン 16.0.8431.1006 (以降)</span><span class="sxs-lookup"><span data-stu-id="6137c-191">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="6137c-192">OneNote モバイル アプリ: バージョン 16.0.8431.1011 (以降)</span><span class="sxs-lookup"><span data-stu-id="6137c-192">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="6137c-193">Teams アプリ</span><span class="sxs-lookup"><span data-stu-id="6137c-193">Teams app</span></span>

<span data-ttu-id="6137c-p115">OneDrive 地域移動の完了時に、ユーザーは Teams アプリで OneDrive ファイルにアクセスできます。さらに、地域移動の前に OneDrive から Teams チャットで共有したファイルは、移動の完了後も引き続き操作できます。</span><span class="sxs-lookup"><span data-stu-id="6137c-p115">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="6137c-196">OneDrive for Business モバイル アプリ (iOS)</span><span class="sxs-lookup"><span data-stu-id="6137c-196">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="6137c-197">OneDrive 地域移動の完了時に、ユーザーは、新しい OneDrive の場所に同期するために、iOS モバイル アプリでサインアウトしてから再度サインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6137c-197">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="6137c-198">既存のフォロー対象グループおよびサイト</span><span class="sxs-lookup"><span data-stu-id="6137c-198">Existing followed groups and sites</span></span>

<span data-ttu-id="6137c-p116">フォロー対象サイトおよびグループは、地域の場所に関係なく、ユーザーの OneDrive for Business に表示されます。別の地域の場所でホストされているサイトとグループは、個別のタブで開かれます。</span><span class="sxs-lookup"><span data-stu-id="6137c-p116">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
