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
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>OneDrive サイトを別の地理的な場所に移動します。 

OneDrive で地域を移動する別の地域の場所にユーザーの OneDrive を移動することができます。OneDrive 地域の移動は、SharePoint Online の管理者、または Office 365 のグローバル管理者によって実行されます。地域を移動する OneDrive を開始する前に必ずが OneDrive の移動中はユーザーに通知し、移動中にすべてのファイルを閉じることをお勧めします。(ユーザーが持っている場合、開いている文書を使用して Office クライアントの移動中に、時に移動完了のドキュメントを新しい場所に保存する必要があります)。必要な場合は、将来の移動をスケジュールできます。

OneDrive サービスは、コンテンツを保存するのには、Azure のブロブ ストレージを使用します。インストール先の地域にはコピー先のユーザーに利用される OneDrive の 40 日間でユーザーの OneDrive に関連付けられているストレージの blob をソースから移動されます。先 OneDrive は、使用するとすぐに、ユーザーの OneDrive へのアクセスが復元されます。

OneDrive 地域移動の期間 (約 2-6 時間) 中のユーザーの OneDrive は、読み取り専用に設定されます。ユーザーは、OneDrive の同期クライアントまたは SharePoint Online では、その OneDrive サイトを使用して、ファイルにアクセスできます。OneDrive 地域の移動が完了したら、ユーザーは自動的に接続先の地域で、OneDrive に Office 365 アプリケーション起動プログラムの OneDrive に移動するとき。新しい場所からの同期は、同期クライアントによって自動的に開始します。

この資料の手順では、 [Microsoft SharePoint のオンライン PowerShell モジュール](https://www.microsoft.com/en-us/download/details.aspx?id=35588)が必要です。

## <a name="moving-a-onedrive-site"></a>OneDrive サイトに移動

OneDrive を実行するには、地域に移動、テナント管理者が適切な地域の場所にユーザーの優先データの場所 (PDL) をまず設定する必要があります。PDL を設定すると、少なくとも 24 時間 PDL OneDrive 地域の移動を開始する前に地域の場所の間で同期するまで待機します。

措置を使用してコマンドレットを移動するときは、次の構文を使用してユーザーの現在の OneDrive geo 位置で SPO サービスに接続します。

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

例: ユーザー 'Matt@contosoenergy.onmicrosoft.com' の OneDrive を移動するには、センターへの接続 EUR SharePoint 管理者 EUR geo の場所では、ユーザーの OneDrive とします。

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>環境の検証

開始する前に、OneDrive 地域に移動、環境を検証することをお勧めします。

地域のすべての場所に互換性があることを確認するには、次のコマンドを実行します。

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

法的保持義務があるが、OneDrive 場合、またはサブサイトが含まれている場合を移動することはできません。されて - パラメーターを使用して開始 SPOUserAndContentMove コマンドレットを使用するには場合は、OneDrive は移動することを検証します。

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

OneDrive は、移動するか、法的保持義務または移動を妨げるサブサイトがある場合に失敗する準備ができている場合は、成功した場合に戻ります。OneDrive を移動する準備ができましたが、確認した後、移動を開始することができます。

## <a name="start-a-onedrive-geo-move"></a>OneDrive 地域の移動を開始します。

移動を開始するには、次のコマンドを実行します。  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

これらのパラメーターを使用します。

-   _UserPrincipalName_ – が OneDrive を移動中は、ユーザーの UPN。

-   _DestinationDataLocation_ : 地理的な場所、OneDrive を移動する必要があります。ユーザーの希望するデータの場所と同じ場合があります。

> [!NOTE]
> 実行することをお勧め`Get-SPOGeoMoveStateCompatibility`と`ValidationOnly`OneDrive を開始する前に地域に移動します。

たとえば、[EUR からオーストラリアの matt@contosoenergy.onmicrosoft.com の OneDrive を移動するに次のいずれかを実行します。

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

後の地域の移動をスケジュールするのには次のパラメーターのいずれかの手順に従います。

-   _PreferredMoveBeginDate_ – 移動は、この指定された時点で開始します。時刻を世界協定時刻 (UTC) で指定してください。

-   _PreferredMoveEndDate_ – 移動は、最善努力原則に基づいて、指定された時刻によって完了します。時刻を世界協定時刻 (UTC) で指定してください。 

## <a name="cancel-a-onedrive-geo-move"></a>OneDrive 地域の移動をキャンセルします。 

指定された移動中のユーザーの OneDrive では、地域の移動を停止することができます。 またはコマンドレットを使用して、完了するとします。

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

_UserPrincipalName_には、OneDrive の移動を停止するユーザーの UPN を指定します。

## <a name="determining-current-status"></a>現在の状態を決定します。

Geo Get SPOUserAndContentMoveState コマンドレットを使用して接続している地域の内外での移動、OneDrive の状況を確認することができます。

移動ステータスは、次の表で説明します。

<table>
<thead>
<tr class="header">
<th align="left"><strong>状態</strong></th>
<th align="left"><strong>説明</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">未開始</td>
<td align="left">移動が開始されていません。</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em></em>n/4)</td>
<td align="left">状態は、次のいずれかで進行中の移動は、: 検証 (1/4)、(2/4) をバックアップするには、(3/4) の復元のクリーンアップ (4/4)。</td>
</tr>
<tr class="odd">
<td align="left">[成功]</td>
<td align="left">移動が正常に完了しました。</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">移動に失敗しました。</td>
</tr>
</tbody>
</table>

特定のユーザーの移動のステータスを確認するには、UserPrincipalName パラメーターを使用します。

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

またはに接続している地域の場所から、移動のすべての状態を検索、次の値の 1 つに MoveState パラメーターを使用します。: 未開始、InProgress、成功、失敗、すべてです。

`Get-SPOUserAndContentMoveState -MoveState <value>`

追加することも、`-Verbose`の移動の状態の説明についてはより詳細なパラメーターです。

## <a name="user-experience"></a>ユーザー エクスペリエンス

OneDrive のユーザーは、OneDrive が別の地域の場所に移動した場合の中断を最小限を確認する必要があります。別に、簡単な読み取り専用状態の移行中に、既存のリンクとアクセス許可は、移動が完了したら、正常に動作する続行されます。

### <a name="onedrive-for-business"></a>OneDrive for Business

移動の実行中に、ユーザーの OneDrive は、読み取り専用に設定されます。移動が完了すると、Office 365 アプリケーション起動プログラムまたは web ブラウザーで、OneDrive に移動するとき別の地域の場所で、OneDrive にユーザーが送られます。

### <a name="permissions-on-onedrive-content"></a>OneDrive コンテンツへのアクセス許可

OneDrive コンテンツへのアクセス許可を持つユーザーは引き続き、完了後、移動中に、コンテンツへのアクセスがあります。

### <a name="onedrive-sync-client"></a>OneDrive 同期クライアント 

OneDrive 同期クライアントは自動的に検出して、OneDrive の地域の移動が完了したら、新しい OneDrive の場所に同期をシームレスに転送します。ユーザーは、もう一度サインインまたはその他のアクションを実行する必要はありません。

OneDrive 地域の移動の実行中に、ユーザーはファイルを更新する場合、同期クライアントは、通知にファイルのアップロードが保留されている移動が進行中です。

### <a name="sharing-links"></a>リンクの共有 

OneDrive 地域に移動の完了、移動されたファイルの既存の共有リンクは自動的に新しい地域の場所にリダイレクトします。

### <a name="onenote-experience"></a>OneNote 体験 

OneNote の win32 クライアントと UWP (ユニバーサル) のアプリケーションが自動的に検出して、OneDrive 地域の移動が完了したら、新しい OneDrive の場所にノートブックをシームレスに同期します。ユーザーは、もう一度サインインまたはその他のアクションを実行する必要はありません。ユーザーにのみ表示されているインジケーターは、OneDrive の地域の移動中にノートブックの同期は失敗します。この経験は、以下のクライアント バージョンの OneNote で利用できます。

-   OneNote の win32-バージョン 16.0.8326.2096 (および後で)

-   OneNote UWP-バージョン 16.0.8431.1006 (および後で)

-   OneNote Mobile アプリケーション – バージョン 16.0.8431.1011 (および後で)

### <a name="teams-app"></a>チームのアプリケーション

OneDrive 地域に移動の完了、ユーザーがチームのアプリケーションに OneDrive ファイルをさらに、地域の移動前に、OneDrive からのチームのチャット経由で共有されているファイルが移動が完了した後に動作し続けます。

### <a name="onedrive-for-business-mobile-app-ios"></a>ビジネス モバイル アプリ (iOS) に OneDrive 

OneDrive 地域に移動の完了、ユーザーをサインアウトしてもう一度サインイン iOS モバイル アプリケーションの新しい OneDrive の場所に同期する必要があります。

### <a name="existing-followed-groups-and-sites"></a>グループとサイトの後に既存

表示済みのサイトとグループは、その地域の場所に関係なくビジネスのユーザーの OneDrive で表示されます。サイトと地域の別の場所でホストされているグループは、別のタブで開かれます。
