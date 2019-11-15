---
title: 別の地域の場所に SharePoint サイトを移動する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: SharePoint サイトを別のジオ位置情報に移動する方法について説明します。
ms.openlocfilehash: 77f5adee161739d8896004988b8a4d6ba0151ef1
ms.sourcegitcommit: 6d3420e41a52820729dd417511286bf98d3713ea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2019
ms.locfileid: "38626147"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>別の地域の場所に SharePoint サイトを移動する

SharePoint サイトの地域移動を使って、SharePoint サイトを複数の地域環境内にある別の地域の場所へ移動させることができます。

次のサイトの種類は地域のジオ位置情報間を移動することができます。

- Office 365 グループに接続されたサイト
- Office 365 グループと関連付けの無いモダン サイト
- 従来の SharePoint サイト
- コミュニケーション サイト

ジオ位置情報間でサイトを移動するには、全体管理者または SharePoint 管理者である必要があります。

サイトの内容によりますが、約4～6時間のSharePoint サイトの地域移動中は、読み取り専用ウィンドウになります。
 
## <a name="best-practices"></a>ベスト プラクティス

- その手順に慣れるために、テスト サイトで SharePoint サイトを移動してみてください。 
- スケジュールまたは移動を実行する前に、サイトを移動できるかどうかを検証します。 
- 可能であれば、地域間の移動スケジュールはユーザーへの影響を減らすために営業時間外に移動します。
- サイトの移動前に影響を受けるユーザーに通知します。 

## <a name="communicating-to-your-users"></a>ユーザーへの連絡

ジオ位置情報間で SharePoint サイトを移動する場合は、想定される動作をサイトのユーザー (一般的にサイトの編集権限がある全てのユーザー) に通知することが重要です。 これにより、ユーザーの混乱やヘルプデスクへの問い合わせを減らすことができます。 移動する前に、次の情報をサイトのユーザーへメールで連絡してください。

- 移動開始予定時刻と予定所要時間
- サイトの移動先となるジオ位置情報と、新しい位置情報にアクセスするための URL
- 移動中はファイルを閉じ、編集を加えないこと。
- 移動してもファイルのアクセス許可と共有設定は変更されないこと。
- 複数の地域環境でのユーザー エクスペリエンスから予想されること

移動が正常に終了した時点で、作業を再開できることを伝える電子メールをユーザーに送信してください。

## <a name="scheduling-sharepoint-site-moves"></a>SharePoint サイトのスケジュール設定に移動します

SharePoint サイトの移動を事前にスケジュールすることができます (この記事の後半でご説明します)。 次のように移動をスケジュールします:

- 一度に最大 4,000 件の移動をスケジュールすることができます。
- 移動開始後はスケジュールを追加でき、常時最大 4,000 件の保留中の移動をキューに置いておけます。
 
SharePoint サイトの地域移動を後でスケジュール設定するには、移動開始時に次のいずれかのパラメーターを含みます:
- `PreferredMoveBeginDate` -移動は、この指定時刻に開始されると見込まれます。
- `PreferredMoveEndDate` -移動は、ベストエフォート方式でこの指定時刻に完了すると見込まれます。 

両方のパラメーターの時間を協定世界時 (UTC) で指定してください。

## <a name="moving-the-site"></a>サイトの移動

SharePoint サイトの地域移動は　サイトがあるジオ位置情報でSharePoint の管理 URLから接続し、実行する必要があります。

例えば、サイト URLが https://contosohealthcare.sharepoint.com/sites/Turbinesの場合、 SharePoint の管理 URL https://contosohealthcare-admin.sharepoint.com:に接続します。

`Connect-SPOService -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a>環境の検証

サイトの移動をスケジュールする前に、サイトが移動できるか検証することをお勧めします。

サイトの移動はサポートしていません:
-   Business Connectivity Services
-   InfoPath フォーム 

すべてのジオ位置情報に互換性があることを確認するために、 `Get-SPOGeoMoveCrossCompatibilityStatus`を実行します。 すべてのジオ位置情報と、その環境が移動先のジオ位置情報と互換性があるかどうかを表示します。

サイトでの検証のみのチェックを実行するには、`-ValidationOnly` パラメーターで`Start-SPOSiteContentMove`を使い、サイトが移動できるか検証します。 例:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

サイトが移動準備完了の場合、*正常に完了*　と返ってきます。ブロックされている状態がある場合は、*失敗*と返ってきます。

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a>Office 365 グループに関連のないサイトへSharePoint サイトの地域移動を開始する

既定値では、サイトの最初のURL は移動先のジオ位置情報の URL に変更されます。 例:

https://Contoso.sharepoint.com/sites/projectx から https://ContosoEUR.sharepoint.com/sites/projectx

Office 365 グループとの関連がないサイトは、`-DestinationUrl` パラメーターを使ってサイト名を変更できます。 例:

https://Contoso.sharepoint.com/sites/projectx から https://ContosoEUR.sharepoint.com/sites/projecty

サイトの移動を開始するには、次のコマンドを実行します:

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Start-SPOSiteContentMove コマンドレットを示す PowerShell ウィンドウのスクリーン ショット](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a>Office 365 グループ接続のサイトへ SharePoint サイトの地域移動を開始する

Office 365 グループ接続のサイトへ移動するには、全体管理者は、優先されるデータの場所 (PDL) を Office 365 グループの属性に最初に変更しなければなりません。

Office 365 グループの PDL をセットする:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
PDL を更新したら、サイトの移動を開始できます。 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>SharePoint サイトジオへの移動をキャンセルする

その移動が実行されていない、または`Stop-SPOSiteContentMove`コマンドレットを使って完了した場合、SharePoint サイトの地域移動を停止できます。

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>SharePoint サイトの地域移動の状況を確認する

次のコマンドレットを使用して接続している地域外でのサイトの移動状況を確認することができます。

- [Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (グループ接続以外のサイト)
- Get-SPOUnifiedGroupMoveState (グループ接続のサイト)

`-SourceSiteUrl` パラメーターを使用して、移動状況を確認したいサイトを指定します。

移動状況については、次に示す表で説明します。

|状態|説明|
|:-----|:----------|
|トリガーの準備|移動は開始されていません。|
|スケジュール済み|移動がキューにあり、まだ開始されていません。|
|InProgress (n/4)|移動は、検証 (1/4)、バックアップ (2/4)、復元 (3/4)、クリーンアップ (4/4) のいずれかの状態で進行中です。|
|Success|移動は正常に完了しています。|
|Failed|移動は失敗しました。|

移動に関する追加情報を確認する `-Verbose` オプションを適用することもできます。

## <a name="user-experience"></a>ユーザー エクスペリエンス

サイトが別のジオ位置情報へ移動した場合は、サイトユーザーに最小限の中断があることを通知する必要があります。 移動中は簡単な読み取り専用状態になることに加えて、既存のリンクとアクセス許可は移動の完了後に引き続き想定通りに操作できるようになります。

### <a name="site"></a>サイト

移動の実行中は、サイトは読み取り専用に設定されます。 移動の完了後に、ブックマークまたは他のリンクをクリックすると、新しいジオ位置情報の新しいサイトがユーザーに指定されます。

### <a name="permissions"></a>アクセス許可

サイトへのアクセス許可を持つユーザーは、移動中および移動完了後のサイトに引き続きアクセスすることができます。

### <a name="sync-client"></a>同期クライアント

サイトの移動が完了後に、同期クライアントは自動的に新しいサイトの場所を検出し、シームレスに同期を転送します。 ユーザーはもう一度サインインまたはその他のアクションをする必要はありません。 (バージョン 17.3.6943.0625 またはそれ以降の同期クライアントが必要です)

移動の進行中にユーザーがファイルを更新すると、移動の実行中はファイルのアップロードが保留されることを同期クライアントが通知します。

### <a name="sharing-links"></a>共有リンク

SharePoint サイトの地域移動の完了時に、移動されたファイルの既存の共有リンクは、新しいジオ位置情報に自動的にリダイレクトされるようになります。

### <a name="most-recently-used-files-in-office-mru"></a>最近使用された Office のファイル (MRU)

MRU サービスは、移動が完了するとサイトとコンテンツの URL が更新されます。 Word、Excel、PowerPoint に適用されます。

### <a name="onenote-experience"></a>OneNote エクスペリエンス

OneNote win32 クライアントと UWP (ユニバーサル) アプリは、サイトの移動完了後に新しいサイトの場所を自動的に検出し、シームレスにノートブックを同期します。 ユーザーはもう一度サインインまたはその他のアクションをする必要はありません。 サイトの移動が進行中にノートブックの同期が失敗する時だけ、ユーザーにインジケーターで表示されます。 このエクスペリエンスは、次の OneNote クライアント バージョンで使用できます:

- OneNote win32: バージョン 16.0.8326.2096 (以降)
- OneNote UWP: バージョン 16.0.8431.1006 (以降)
- OneNote モバイル アプリ: バージョン 16.0.8431.1011 (以降)

### <a name="teams-applicable-to-office-365-group-connected-sites"></a>チーム (Office 365 グループ接続のサイトに適用)

SharePoint サイトの地域の移動が完了すると、ユーザーはチーム アプリにある Office 365 グループ サイトのファイルにアクセスできるようになります。 さらに、地域移動前にサイトからチーム チャット経由で共有したファイルは、移動が完了後に引き続き操作できるようになります。

### <a name="sharepoint-mobile-app-iosandroid"></a>iOS/Android 用 SharePoint モバイル アプリ

SharePoint モバイル アプリは、地域間で互換性があり、サイトの新しいジオ位置情報を検出することができます。

### <a name="sharepoint-workflows"></a>SharePoint ワークフロー

SharePoint 2013 ワークフローは、サイトの移動後に再発行する必要があります。 SharePoint 2010 ワークフローは、正常に動作し続ける必要があります。

### <a name="apps"></a>アプリ

アプリを使用してサイトを移動すると、移動先のジオ位置情報に接続できない場合があるので、サイトの新しいジオ位置情報でアプリを再インスタンス化する必要があります。

### <a name="flow"></a>フロー

ほとんどの場合、フローは SharePoint サイトの地域移動後に引き続き操作することができるようになります。 移動が完了したらテストすることをお勧めします。

### <a name="powerapps"></a>PowerApps

PowerAppsは、移動先の位置情報で再作成する必要があります。

### <a name="data-movement-between-geo-locations"></a>ジオ位置情報間のデータ移動

SharePoint にサイトとそのファイルに関連付けられているメタデータが保存されている場合は、コンテンツの Azure Blob ストレージを使用します。 その元のジオ位置情報から移動先のジオ位置情報へ移動後、サービスも関連付けられている Blob ストレージへ移動します。 BLOB ストレージは約40日で移動を完了します。 
