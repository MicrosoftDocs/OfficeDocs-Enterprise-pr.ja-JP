---
title: 特定 PDL で Office 365 グループを作成する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: 複数地域環境で指定された優先データの場所を使用して、Office 365 グループを作成する方法について説明します。
ms.openlocfilehash: a46a34d9fd5be9b3acda5ee3859f4eed08797b7c
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "30934045"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>特定 PDL で Office 365 グループを作成する

複数地域環境のユーザーが Office 365 グループを作成すると、グループ優先データの場所は自動的にそのユーザーの場所に設定されます。 特定 PDL でグループを作成する必要がある場合は、Exchange Online New-unifiedgroup Microsoft PowerShell コマンドレットを使用して作成できます。 これを実行すると、グループ メールボックスとグループに関連付けられている SharePoint サイトは両方とも、指定 PDL でプロビジョニングされます。

これを実行するのは、全体管理者、SharePoint Online 管理者、Exchange Online 管理者のいずれかである必要があります。

指定した PDL を使用して Office 365 グループを作成するのには、Exchange Online PowerShell に接続して、パラメーター *-MailBoxRegion* を地域の場所コードとともに渡します。

次に例を示します。 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![構文を使用した New-UnifiedGroup PowerShell コマンドレットのスクリーンショット](media/multi-geo-new-group-with-pdl-powershell.png)

SharePoint グループのサイト プロビジョニングがオンデマンドであることに注意してください。 サイトは、グループの所有者またはメンバーが初めてアクセスを試みたときにプロビジョニングされます。

## <a name="geo-location-codes"></a>地域の場所コード

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>関連項目

[Exchange Online PowerShell への接続](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)