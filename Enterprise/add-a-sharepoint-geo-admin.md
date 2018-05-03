---
title: 追加または地域の管理者を削除します。
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 追加または複数の地域のビジネス OneDrive の地域の管理者を削除する方法について説明します。
ms.openlocfilehash: b88467cf2f33ec3a3a8bf6c2d6927e69e9f7af65
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>追加または Busniess 複数の地域の OneDrive の地域の管理者を削除します。

テナント内にある場所を地域ごとに個別の管理者を構成することができます。これらの管理者は、SharePoint Online および OneDrive の設定には、地理的な場所に固有のアクセスがあります。

用語ストア - などの一部のサービスは中央の場所から管理し、サテライトの場所にレプリケートします。中央の場所の地域の管理では、サテライト オフィスの地域の管理者でないが、これらへのアクセスがあります。

グローバル管理者および SharePoint Online の管理者は、地域のすべての場所の設定へのアクセスを有効にして続行します。

## <a name="configuring-geo-administrators"></a>地域の管理者を構成します。

地域の管理者を構成するには、SharePoint のオンライン PowerShell モジュールが必要です。

地域管理者の追加先となる地域の場所の管理センターへの接続に[接続する SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)を使用してください。(たとえば、接続 SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

場所の既存の地域の管理者を表示するのには次のように実行します。`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>地域の管理者としてユーザーを追加します。

地域の管理者としてユーザーを追加するのには次のように実行します。`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

場所の地域の管理者として、ユーザーを削除するのには次のように実行します。`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>地域の管理者として、グループを追加します。

地域管理者としてセキュリティ グループまたはメールが有効なセキュリティ グループを追加することができます。(配布グループと Office 365 のグループはサポートされません。)

地域管理者としてグループを追加するのには次のように実行します。`Add-SPOGeoAdministrator -GroupAlias <alias>`

地域の管理者として、グループを削除するのには次のように実行します。`Remove-SPOGeoAdministrator -GroupAlias <alias>`

すべてのセキュリティ グループに、グループのエイリアスがあることに注意してください。エイリアス、グループの一覧を取得する[Get MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup)を実行していないセキュリティ グループを追加する場合、セキュリティ グループのオブジェクト Id を検索し、実行します。

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

オブジェクト Id を使用してグループを削除するのには次のように実行します。`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

### <a name="accessing-the-admin-center-for-a-specific-geo-location"></a>特定の地理的な場所の管理センターへのアクセス

地理的な場所の OneDrive の設定を管理するには、管理者は次の URL 形式を使用して直接 OneDrive 管理センターにアクセスする必要があります。

https://admin.onedrive.com/?geo=<*地域*>

たとえば、カナダの OneDrive の管理の中心にある: https://admin.onedrive.com/?geo=CAN。

## <a name="see-also"></a>関連項目

[追加 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[削除 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[セキュリティ グループのエイリアス (MailNickName) を設定します。](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)