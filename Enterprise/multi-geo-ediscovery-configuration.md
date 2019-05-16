---
title: Office 365 Multi-Geo 電子情報開示を構成する
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Office 365 Multi-Geoで電子情報開示を構成する方法を表示する。
ms.openlocfilehash: f9d8fe8b65f5772005bf7d6a7ea3735277077d3b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069963"
---
# <a name="office-365-multi-geo-ediscovery-configuration"></a>Office 365 Multi-Geo 電子情報開示の構成


既定では、複数地域テナントの電子情報開示マネージャーまたは管理者は、テナントの中央の場所でのみ電子情報開示を実施できます。サテライトの場所で電子情報開示を実施できるようにするために、"Region" という新しいコンプライアンス セキュリティ フィルター パラメーターが PowerShell で使用できます。

Office 365 全体管理者は、別のユーザーが電子情報開示を実行できるように電子情報開示マネージャーのアクセス許可を割り当てる必要があります。また、サテライトの場所として電子情報開示を実施する地域を指定するために該当するコンプライアンス セキュリティ フィルターで "Region" パラメーターを割り当てる必要があります。それ以外の場合は、サテライトの場所で電子情報開示は実施されません。

電子情報開示マネージャーまたは管理者の役割が特定のサテライトの場所に設定されている場合、電子情報開示マネージャーまたは管理者は、そのサテライトの場所にある SharePoint サイトと OneDrive サイトに対してのみ電子情報開示の検索操作を実行できます。電子情報開示マネージャーまたは管理者が、指定のサテライトの場所以外の SharePoint サイトまたは OneDrive サイトを検索しようとしても、結果は返されません。さらに、あるサテライトの場所の電子情報開示マネージャーまたは管理者がエクスポートをトリガーすると、データは、その地域の Azure インスタンスにエクスポートされます。制御された境界を越えたコンテンツのエクスポートが許可されなくなることで、これが組織のコンプライアンスの維持に役立ちます。

> [!NOTE]
> 電子情報開示マネージャーが複数の SharePoint のサテライトの場所全体で検索する必要がない場合は、OneDrive サイトまたは SharePoint サイトがある別のサテライトの場所を指定する電子情報開示マネージャー用の別のユーザー アカウントを作成する必要があります。

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

地域のコンプライアンス セキュリティ フィルターを設定するには:

1.  Windows PowerShell を開きます。

2.  次のように入力します  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    例: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

追加のパラメーターと構文については、「[New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx)」の記事を参照してください。
