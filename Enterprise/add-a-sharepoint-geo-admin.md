---
title: 追加または地域の管理者を削除します。
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: 追加または複数の地域のビジネス OneDrive の地域の管理者を削除する方法について説明します。
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>追加または Busniess 複数の地域の OneDrive の地域の管理者を削除します。

テナント内にある場所を地域ごとに個別の管理者を構成することができます。これらの管理者は、SharePoint Online および OneDrive の設定には、地理的な場所に固有のアクセスがあります。

用語ストア - などの一部のサービスは中央の場所から管理し、サテライトの場所にレプリケートします。中央の場所の地域の管理では、サテライト オフィスの地域の管理者でないが、これらへのアクセスがあります。

グローバル管理者および SharePoint Online の管理者は、地域のすべての場所の設定へのアクセスを有効にして続行します。

## <a name="configuring-geo-administrators"></a>地域の管理者を構成します。

地域の管理者を構成するには、SharePoint のオンライン PowerShell モジュールが必要です。

地域管理者の追加先となる地域の場所の管理センターへの接続に[接続する SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService)を使用してください。(たとえば、接続 SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

地域の管理者としてユーザーを追加するのには次のように実行します。`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

場所の既存の地域の管理者を表示するのには次のように実行します。`Get-SPOGeoAdministrators`

場所の地域の管理者として、ユーザーを削除するのには次のように実行します。`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## <a name="see-also"></a>関連項目

[追加 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[削除 SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)