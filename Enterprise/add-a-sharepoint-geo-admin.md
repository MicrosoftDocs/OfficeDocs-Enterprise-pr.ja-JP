---
title: 地域管理者を追加または削除する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: Office 365 Multi-Geo で地域管理者を追加または削除する方法について説明します。
ms.openlocfilehash: 54850252d133e3e26b02cabe3ead0900287e832c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490913"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a>Office 365 Multi-Geo で地域管理者を追加または削除する

テナント内にある地域の場所ごとに個別の管理者を構成することができます。 これらの管理者は、各自の地域の場所に固有の SharePoint Online と OneDrive の設定にアクセスすることができます。

用語ストアなどの一部のサービスは、中央の場所から管理され、サテライトの場所にレプリケートされます。 中央の場所の地域管理者は、これらのサービスにアクセスできますが、サテライトの場所の地理管理者はアクセスできません。

グローバル管理者と SharePoint Online 管理者は、中央の場所とすべてのサテライトの場所の設定に引き続きアクセスできます。

## <a name="configuring-geo-administrators"></a>地域管理者の構成

地域管理者の構成には、SharePoint Online PowerShell モジュールが必要です。

[Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) を使用して、地域管理者を追加する地域の場所の管理センターに接続します。(例: Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)

場所の既存の地域管理者を表示するには、`Get-SPOGeoAdministrator` を実行します。

### <a name="adding-a-user-as-a-geo-admin"></a>地域管理者としてのユーザーの追加

地域管理者としてのユーザーを追加するには、`Add-SPOGeoAdministrator -UserPrincipalName <UPN>` を実行します。

場所の地域管理者としてのユーザーを削除するには、`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>` を実行します。

### <a name="adding-a-group-as-a-geo-admin"></a>地域管理者としてのグループの追加

地域管理者として、セキュリティ グループまたはメールが有効なセキュリティ グループを追加できます。(配布グループと Office 365 グループはサポートされていません。)

地域管理者としてグループを追加するには、`Add-SPOGeoAdministrator -GroupAlias <alias>` を実行します。

地域管理者としてのグループを削除するには、`Remove-SPOGeoAdministrator -GroupAlias <alias>` を実行します。

一部のセキュリティ グループにはグループ エイリアスがないことに注意してください。 エイリアスがないセキュリティ グループを追加する場合は、[Get-MsolGroup](https://docs.microsoft.com/ja-JP/powershell/module/msonline/get-msolgroup) を実行して、グループの一覧を取得し、セキュリティ グループの ObjectID を検索して、次を実行します。

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

ObjectID を使用してグループを削除するには、`Remove-SPOGeoAdministrator -ObjectID <ObjectID>` を実行します。

## <a name="see-also"></a>関連項目

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[セキュリティ グループのエイリアス (MailNickName) を設定する](https://docs.microsoft.com/ja-JP/powershell/module/azuread/set-azureadgroup)