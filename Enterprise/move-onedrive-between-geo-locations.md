---
title: OneDrive サイトを別の地理的な場所に移動します。
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: OneDrive サイトを別の地理的な場所に移動する方法について説明します。
ms.openlocfilehash: 7ce9106fa7d8d144f0f8935713b4df926a73fb6b
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="d11e2-103">OneDrive サイトを別の地理的な場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="d11e2-p101">OneDrive で地域を移動する別の地域の場所にユーザーの OneDrive を移動することができます。OneDrive 地域の移動は、SharePoint Online の管理者、または Office 365 のグローバル管理者によって実行されます。地域を移動する OneDrive を開始する前に必ずが OneDrive の移動中はユーザーに通知し、移動中にすべてのファイルを閉じることをお勧めします。(ユーザーが持っている場合、開いている文書を使用して Office クライアントの移動中に、時に移動完了のドキュメントを新しい場所に保存する必要があります)。必要な場合は、将来の移動をスケジュールできます。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="d11e2-p102">OneDrive サービスは、コンテンツを保存するのには、Azure のブロブ ストレージを使用します。インストール先の地域にはコピー先のユーザーに利用される OneDrive の 40 日間でユーザーの OneDrive に関連付けられているストレージの blob をソースから移動されます。先 OneDrive は、使用するとすぐに、ユーザーの OneDrive へのアクセスが復元されます。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="d11e2-p103">OneDrive 地域移動の期間 (約 2-6 時間) 中のユーザーの OneDrive は、読み取り専用に設定されます。ユーザーは、OneDrive の同期クライアントまたは SharePoint Online では、その OneDrive サイトを使用して、ファイルにアクセスできます。OneDrive 地域の移動が完了したら、ユーザーは自動的に接続先の地域で、OneDrive に Office 365 アプリケーション起動プログラムの OneDrive に移動するとき。新しい場所からの同期は、同期クライアントによって自動的に開始します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="d11e2-115">この資料の手順では、 [Microsoft SharePoint のオンライン PowerShell モジュール](https://www.microsoft.com/en-us/download/details.aspx?id=35588)が必要です。</span><span class="sxs-lookup"><span data-stu-id="d11e2-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="d11e2-116">OneDrive サイトに移動</span><span class="sxs-lookup"><span data-stu-id="d11e2-116">Moving a OneDrive site</span></span>

<span data-ttu-id="d11e2-p104">OneDrive を実行するには、地域に移動、テナント管理者が適切な地域の場所にユーザーの優先データの場所 (PDL) をまず設定する必要があります。PDL を設定すると、少なくとも 24 時間 PDL OneDrive 地域の移動を開始する前に地域の場所の間で同期するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="d11e2-119">措置を使用してコマンドレットを移動するときは、次の構文を使用してユーザーの現在の OneDrive geo 位置で SPO サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="d11e2-120">例: ユーザー 'Matt@contosoenergy.onmicrosoft.com' の OneDrive を移動するには、センターへの接続 EUR SharePoint 管理者 EUR geo の場所では、ユーザーの OneDrive とします。</span><span class="sxs-lookup"><span data-stu-id="d11e2-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="d11e2-121">環境の検証</span><span class="sxs-lookup"><span data-stu-id="d11e2-121">Validating the environment</span></span>

<span data-ttu-id="d11e2-122">開始する前に、OneDrive 地域に移動、環境を検証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d11e2-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="d11e2-123">地域のすべての場所に互換性があることを確認するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="d11e2-p105">法的保持義務があるが、OneDrive 場合、またはサブサイトが含まれている場合を移動することはできません。されて - パラメーターを使用して開始 SPOUserAndContentMove コマンドレットを使用するには場合は、OneDrive は移動することを検証します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="d11e2-p106">OneDrive は、移動するか、法的保持義務または移動を妨げるサブサイトがある場合に失敗する準備ができている場合は、成功した場合に戻ります。OneDrive を移動する準備ができましたが、確認した後、移動を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="d11e2-128">OneDrive 地域の移動を開始します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="d11e2-129">移動を開始するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="d11e2-130">これらのパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-130">Using these parameters:</span></span>

-   <span data-ttu-id="d11e2-131">_UserPrincipalName_ – が OneDrive を移動中は、ユーザーの UPN。</span><span class="sxs-lookup"><span data-stu-id="d11e2-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="d11e2-p107">_DestinationDataLocation_ : 地理的な場所、OneDrive を移動する必要があります。ユーザーの希望するデータの場所と同じ場合があります。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="d11e2-134">実行することをお勧め`Get-SPOGeoMoveStateCompatibility`と`ValidationOnly`OneDrive を開始する前に地域に移動します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="d11e2-135">たとえば、[EUR からオーストラリアの matt@contosoenergy.onmicrosoft.com の OneDrive を移動するに次のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="d11e2-136">後の地域の移動をスケジュールするのには次のパラメーターのいずれかの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d11e2-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="d11e2-p108">_PreferredMoveBeginDate_ – 移動は、この指定された時点で開始します。時刻を世界協定時刻 (UTC) で指定してください。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="d11e2-p109">_PreferredMoveEndDate_ – 移動は、最善努力原則に基づいて、指定された時刻によって完了します。時刻を世界協定時刻 (UTC) で指定してください。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="d11e2-141">OneDrive 地域の移動をキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="d11e2-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="d11e2-142">指定された移動中のユーザーの OneDrive では、地域の移動を停止することができます。 またはコマンドレットを使用して、完了するとします。</span><span class="sxs-lookup"><span data-stu-id="d11e2-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="d11e2-143">_UserPrincipalName_には、OneDrive の移動を停止するユーザーの UPN を指定します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="d11e2-144">現在の状態を決定します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-144">Determining current status</span></span>

<span data-ttu-id="d11e2-145">Geo Get SPOUserAndContentMoveState コマンドレットを使用して接続している地域の内外での移動、OneDrive の状況を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="d11e2-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="d11e2-146">移動ステータスは、次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-146">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="d11e2-147"><strong>状態</strong></span><span class="sxs-lookup"><span data-stu-id="d11e2-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="d11e2-148"><strong>説明</strong></span><span class="sxs-lookup"><span data-stu-id="d11e2-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="d11e2-149">未開始</span><span class="sxs-lookup"><span data-stu-id="d11e2-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="d11e2-150">移動が開始されていません。</span><span class="sxs-lookup"><span data-stu-id="d11e2-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d11e2-151">InProgress (<em></em>n/4)</span><span class="sxs-lookup"><span data-stu-id="d11e2-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="d11e2-152">状態は、次のいずれかで進行中の移動は、: 検証 (1/4)、(2/4) をバックアップするには、(3/4) の復元のクリーンアップ (4/4)。</span><span class="sxs-lookup"><span data-stu-id="d11e2-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="d11e2-153">[成功]</span><span class="sxs-lookup"><span data-stu-id="d11e2-153">Success</span></span></td>
<td align="left"><span data-ttu-id="d11e2-154">移動が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="d11e2-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="d11e2-155">Failed</span><span class="sxs-lookup"><span data-stu-id="d11e2-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="d11e2-156">移動に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="d11e2-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="d11e2-157">特定のユーザーの移動のステータスを確認するには、UserPrincipalName パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="d11e2-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="d11e2-158">またはに接続している地域の場所から、移動のすべての状態を検索、次の値の 1 つに MoveState パラメーターを使用します。: 未開始、InProgress、成功、失敗、すべてです。</span><span class="sxs-lookup"><span data-stu-id="d11e2-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="d11e2-159">追加することも、`-Verbose`の移動の状態の説明についてはより詳細なパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="d11e2-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="d11e2-160">ユーザー エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="d11e2-160">User Experience</span></span>

<span data-ttu-id="d11e2-p110">OneDrive のユーザーは、OneDrive が別の地域の場所に移動した場合の中断を最小限を確認する必要があります。別に、簡単な読み取り専用状態の移行中に、既存のリンクとアクセス許可は、移動が完了したら、正常に動作する続行されます。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="d11e2-163">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="d11e2-163">OneDrive for Business</span></span>

<span data-ttu-id="d11e2-p111">移動の実行中に、ユーザーの OneDrive は、読み取り専用に設定されます。移動が完了すると、Office 365 アプリケーション起動プログラムまたは web ブラウザーで、OneDrive に移動するとき別の地域の場所で、OneDrive にユーザーが送られます。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="d11e2-166">OneDrive コンテンツへのアクセス許可</span><span class="sxs-lookup"><span data-stu-id="d11e2-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="d11e2-167">OneDrive コンテンツへのアクセス許可を持つユーザーは引き続き、完了後、移動中に、コンテンツへのアクセスがあります。</span><span class="sxs-lookup"><span data-stu-id="d11e2-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="d11e2-168">OneDrive 同期クライアント</span><span class="sxs-lookup"><span data-stu-id="d11e2-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="d11e2-p112">OneDrive 同期クライアントは自動的に検出して、OneDrive の地域の移動が完了したら、新しい OneDrive の場所に同期をシームレスに転送します。ユーザーは、もう一度サインインまたはその他のアクションを実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="d11e2-171">OneDrive 地域の移動の実行中に、ユーザーはファイルを更新する場合、同期クライアントは、通知にファイルのアップロードが保留されている移動が進行中です。</span><span class="sxs-lookup"><span data-stu-id="d11e2-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="d11e2-172">リンクの共有</span><span class="sxs-lookup"><span data-stu-id="d11e2-172">Sharing links</span></span> 

<span data-ttu-id="d11e2-173">OneDrive 地域に移動の完了、移動されたファイルの既存の共有リンクは自動的に新しい地域の場所にリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="d11e2-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="d11e2-174">OneNote 体験</span><span class="sxs-lookup"><span data-stu-id="d11e2-174">OneNote Experience</span></span> 

<span data-ttu-id="d11e2-p113">OneNote の win32 クライアントと UWP (ユニバーサル) のアプリケーションが自動的に検出して、OneDrive 地域の移動が完了したら、新しい OneDrive の場所にノートブックをシームレスに同期します。ユーザーは、もう一度サインインまたはその他のアクションを実行する必要はありません。ユーザーにのみ表示されているインジケーターは、OneDrive の地域の移動中にノートブックの同期は失敗します。この経験は、以下のクライアント バージョンの OneNote で利用できます。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="d11e2-179">OneNote の win32-バージョン 16.0.8326.2096 (および後で)</span><span class="sxs-lookup"><span data-stu-id="d11e2-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="d11e2-180">OneNote UWP-バージョン 16.0.8431.1006 (および後で)</span><span class="sxs-lookup"><span data-stu-id="d11e2-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="d11e2-181">OneNote Mobile アプリケーション – バージョン 16.0.8431.1011 (および後で)</span><span class="sxs-lookup"><span data-stu-id="d11e2-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="d11e2-182">チームのアプリケーション</span><span class="sxs-lookup"><span data-stu-id="d11e2-182">Teams app</span></span>

<span data-ttu-id="d11e2-p114">OneDrive 地域に移動の完了、ユーザーがチームのアプリケーションに OneDrive ファイルをさらに、地域の移動前に、OneDrive からのチームのチャット経由で共有されているファイルが移動が完了した後に動作し続けます。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="d11e2-185">ビジネス モバイル アプリ (iOS) に OneDrive</span><span class="sxs-lookup"><span data-stu-id="d11e2-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="d11e2-186">OneDrive 地域に移動の完了、ユーザーをサインアウトしてもう一度サインイン iOS モバイル アプリケーションの新しい OneDrive の場所に同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d11e2-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="d11e2-187">グループとサイトの後に既存</span><span class="sxs-lookup"><span data-stu-id="d11e2-187">Existing followed groups and sites</span></span>

<span data-ttu-id="d11e2-p115">表示済みのサイトとグループは、その地域の場所に関係なくビジネスのユーザーの OneDrive で表示されます。サイトと地域の別の場所でホストされているグループは、別のタブで開かれます。</span><span class="sxs-lookup"><span data-stu-id="d11e2-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
