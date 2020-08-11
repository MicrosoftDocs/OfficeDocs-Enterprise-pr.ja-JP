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
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>別の地域の場所に OneDrive サイトを移動する 

OneDrive 地域移動を使用すると、ユーザーの OneDrive を別の地域の場所に移動することができます。OneDrive 地域移動は、SharePoint Online 管理者または Microsoft 365 グローバル管理者によって実行されます。OneDrive の地域移動を開始する前に、OneDrive が移動されていることをユーザーに通知して、移動中にすべてのファイルを閉じることをお勧めします。(移動時に Office クライアントを使用してドキュメントが開かれている場合は、移動の完了時にドキュメントを新しい場所に保存する必要があります)。必要に応じて、移行を将来の時間にスケジュールすることができます。

OneDrive サービスは、Azure Blob ストレージを使用してコンテンツを格納します。ユーザーの OneDrive に関連付けられている記憶域 blob は、ユーザーが使用可能な宛先の OneDrive から40日以内に、移行元から移行先の地域の場所に移動されます。ユーザーの OneDrive へのアクセスは、移行先の OneDrive が使用可能になるとすぐに復元されます。

OneDrive 地域の移動の期間中 (約 2 ～ 6 時間)、ユーザーの OneDrive は読み取り専用に設定されます。ユーザーは今まで通り OneDrive 同期クライアントまたは SharePoint Online の OneDrive サイトからファイルにアクセスできます。OneDrive 地域の移動の完了後に、ユーザーが Microsoft 365 アプリ起動ツールで OneDrive に移動すると、移動先の地域の場所にある OneDrive に自動的に接続されます。同期クライアントは、新しい場所からの同期を自動的に開始します。

この記事の手順には、[Microsoft Office SharePoint Online の PowerShell モジュール](https://www.microsoft.com/download/details.aspx?id=35588)が必要になります。

## <a name="communicating-to-your-users"></a>ユーザーへの連絡

OneDrive サイトの地理的場所を移動する際には、想定される動作についてユーザーに通知することが重要です。これは、ユーザーが混乱してヘルプ デスクに問い合わせる可能性を減らすのに役立ちます。移動の前に、次の情報について電子メールでユーザーに連絡してください。

- 移動開始予定時刻と予定所要時間
- ユーザーの OneDrive の移動先となる地理的場所、および新しい場所にアクセスするための URL
- 移動中はファイルを閉じた状態にし、編集を加えてはならないこと。
- 移動してもファイルの許可と共有は変更されないこと。
- [複数地理環境でのユーザー エクスペリエンス](multi-geo-user-experience.md)として期待されること

移動が正常に終了した時点で、ユーザーに対し、OneDrive での作業を再開できることを伝える電子メールを送信するようにしてください。

## <a name="scheduling-onedrive-site-moves"></a>OneDrive サイトの移動のスケジュール設定

OneDrive サイトの移動を事前にスケジュールすることができます (この記事の後半でご説明いたします)。少数のユーザーの移動から始め、ワークフローと連絡手順を確認することをお勧めします。プロセスが満足できるものであった場合、次のように移動をスケジュールします。

- 一度に最大 4,000 件の移動をスケジュールすることができます。
- 移動開始後はスケジュールを追加でき、常時最大 4,000 件の保留中の移動をキューに置いておけます。
- 移動できる OneDrive の最大サイズは 1 テラバイト (1 TB) です。

## <a name="moving-a-onedrive-site"></a>OneDrive サイトの移動

OneDrive の地域移動を実行するには、テナント管理者は、まずユーザーの優先データの場所 (PDL) を適切な地域の場所に設定する必要があります。PDL が設定されたら、OneDrive 地域移動を開始する前に、各 geo の場所間で PDL の更新が同期されるまで、少なくとも24時間待機します。

Geo move コマンドレットを使用する場合は、次の構文を使用して、ユーザーの現在の OneDrive 地域の場所にある SPO サービスに接続します。

`Connect-SPOService -url https://<tenantName>-admin.sharepoint.com`

例: ユーザー ' Matt@contosoenergy.onmicrosoft.com ' の OneDrive を移動するには、ユーザーの OneDrive が EUR 地域の場所にあるので、[EUR] SharePoint 管理センターに接続します。

`Connect-SPOSservice -url https://contosoenergyeur-admin.sharepoint.com`

![Connect-SPOService コマンドレットを示す PowerShell ウィンドウのスクリーン ショット](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>環境の検証

OneDrive 地域移動の開始前に、目的の環境を検証するようにお勧めします。

すべての地域の場所に互換性があることを確認するために、次のコマンドレットを実行します。

`Get-SPOGeoMoveCrossCompatibilityStatus`

地域の場所のリストが表示され、その場所間でコンテンツを移動できるかどうかが「互換性あり」として示されます。 コマンドが「互換性なし」を返した場合は、後日、状態の検証をあとでもう一度お試しください。

たとえば、サブサイトが含まれている場合、OneDrive は移動できません。 OneDrive が移動可能かどうかを検証するには、-ValidationOnly パラメーターを指定した Start-SPOUserAndContentMove コマンドレットを使用してください。

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

OneDrive の移動が可能な状態になっている場合は Success が返されます。移動を妨げる訴訟ホールドまたはサブサイトがある場合は Fail が返されます。OneDrive が移動できる状態になっていることを確認したら、移動を開始します。

## <a name="start-a-onedrive-geo-move"></a>OneDrive 地域移動の開始

移動を開始するには、次のコマンドレットを実行します。  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

次に示すパラメーターを使用します。

-   _UserPrincipalName_: 移動する OneDrive を所有するユーザーの UPN です。

-   _DestinationDataLocation_ –地域-OneDrive を移動する必要がある場所。これは、ユーザーの優先されるデータの場所と同じである必要があります。

たとえば、matt@contosoenergy.onmicrosoft.com の OneDrive を EUR から AUS に移動するには、次のコマンドレットを実行します。

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![Start-SPOUserAndContentMove コマンドレットを示す PowerShell ウィンドウのスクリーン ショット](media/move-onedrive-between-geo-locations-image2.png)

将来の地域移動をスケジュールするには、次に示すパラメーターのいずれかを使用します。

-   _PreferredMoveBeginDate_: 移動は、この指定時刻に開始されると見込まれます。時刻は、協定世界時 (UTC) で指定する必要があります。

-   _PreferredMoveEndDate_: 移動は、最善努力の原則で、この指定時刻に完了すると見込まれます。時刻は、協定世界時 (UTC) で指定する必要があります。 

## <a name="cancel-a-onedrive-geo-move"></a>OneDrive 地域移動のキャンセル 

コマンドレットを使用して移動が進行中または完了していない場合は、ユーザーの OneDrive の地域の移動を停止することができます。

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

_UserPrincipalName_ は、移動を停止する OneDrive の所有ユーザーの UPN です。

## <a name="determining-current-status"></a>現在の状態の確認

Get-SPOUserAndContentMoveState コマンドレットを使用して、接続している geo の OneDrive 地域移動の状態を確認できます。

移動の状態については、次に示す表で説明します。

<table>
<thead>
<tr class="header">
<th align="left"><strong>状態</strong></th>
<th align="left"><strong>説明</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NotStarted</td>
<td align="left">移動は開始されていません。</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">移動は、検証 (1/4)、バックアップ (2/4)、復元 (3/4)、クリーンアップ (4/4) のいずれかの状態で進行中です。</td>
</tr>
<tr class="odd">
<td align="left">Success</td>
<td align="left">移動は正常に完了しています。</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">移動は失敗しました。</td>
</tr>
</tbody>
</table>

特定のユーザーの移動の状態を検索するには、UserPrincipalName パラメーターを使用します。

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

接続している地理的位置にあるすべての移動の状態を検索するには、MoveState パラメーターを次のいずれかの値で指定します。 NotStarted、InProgress、Success、Failed、All。

`Get-SPOUserAndContentMoveState -MoveState <value>`

また、より詳細な移動状態の説明が示されるように、`-Verbose` パラメーターを追加することもできます。

## <a name="user-experience"></a>ユーザー エクスペリエンス

ユーザーの OneDrive を別の地域の場所に移動する場合は、OneDrive のユーザーに最小限の説明についての通知が必要です。移動中は読み取り専用の状態になることの説明に加えて、既存のリンクとアクセス許可は移動の完了後に引き続き期待どおりに動作することも説明します。

### <a name="onedrive-for-business"></a>OneDrive for Business

移動が進行中に、ユーザーの OneDrive は読み取り専用に設定されます。移動が完了すると、ユーザーは OneDrive (Microsoft 365 アプリ起動ツールまたは web ブラウザー) に移動すると、新しい地理的位置にある OneDrive にリダイレクトされます。

### <a name="permissions-on-onedrive-content"></a>OneDrive コンテンツに対するアクセス許可

OneDrive コンテンツへのアクセス許可を持つユーザーは、移動中および完了後にコンテンツへのアクセスを続けられます。

### <a name="onedrive-sync-client"></a>OneDrive 同期クライアント 

OneDrive 同期クライアントは、OneDrive 地域移動の完了後に、自動的に新しい OneDrive の場所を検出し、シームレスに同期を転換します。ユーザーは、再度サインインするなどの操作を一切実行する必要がありません。(同期クライアントのバージョン 17.3.6943.0625 以降が必要。)

OneDrive 地域移動の進行中にユーザーがファイルを更新すると、同期クライアントにより、移動が進行している間はファイルの更新が保留されることが通知されます。

### <a name="sharing-links"></a>共有リンク 

OneDrive 地域移動の完了時に、移動されたファイルの既存の共有リンクは、新しい地域の場所に自動的にリダイレクトされるようになります。

### <a name="onenote-experience"></a>OneNote エクスペリエンス 

OneNote win32 クライアントと UWP (ユニバーサル) アプリは、OneDrive 地域移動の完了後に、自動的に新しい OneDrive の場所を検出してシームレスにノートブックを同期します。ユーザーは、再度サインインするなどの操作を一切実行する必要がありません。ユーザーが認識できることは、OneDrive 地域移動が進行中のときにノートブックの同期が失敗することのみです。このエクスペリエンスは、次に示す OneNote クライアントのバージョンで利用できます。

-   OneNote win32: バージョン 16.0.8326.2096 (以降)

-   OneNote UWP: バージョン 16.0.8431.1006 (以降)

-   OneNote モバイル アプリ: バージョン 16.0.8431.1011 (以降)

### <a name="teams-app"></a>Teams アプリ

OneDrive 地域移動の完了時に、ユーザーは Teams アプリで OneDrive ファイルにアクセスできます。さらに、地域移動の前に OneDrive から Teams チャットで共有したファイルは、移動の完了後も引き続き操作できます。

### <a name="onedrive-for-business-mobile-app-ios"></a>OneDrive for Business モバイル アプリ (iOS) 

OneDrive 地域移動の完了時に、ユーザーは、新しい OneDrive の場所に同期するために、iOS モバイル アプリでサインアウトしてから再度サインインする必要があります。

### <a name="existing-followed-groups-and-sites"></a>既存のフォロー対象グループおよびサイト

フォロー対象のサイトとグループは、地域の場所に関係なく、ユーザーの OneDrive に表示されます。別の地域の場所にホストされているサイトとグループは、別のタブに表示されます。

### <a name="delve-geo-url-updates"></a>Delve 地域 URL の更新

ユーザーは、OneDrive が新しい geo に移動された後にのみ、PDL に対応する Delve geo に送信されます。
