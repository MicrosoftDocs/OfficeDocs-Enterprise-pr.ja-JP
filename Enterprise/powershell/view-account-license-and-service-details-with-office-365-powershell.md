---
title: Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/27/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Office 365 の PowerShell を使用してユーザーに割り当てられている Office 365 のサービスを確認する方法について説明します。
ms.openlocfilehash: 78608c3a52151c115eaf80b5315bb71b61e62356
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223109"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する

**の概要:** Office 365 の PowerShell を使用してユーザーに割り当てられている Office 365 のサービスを確認する方法について説明します。
  
、Office 365 では、計画のライセンスからライセンス (も呼び出された Sku または Office 365 プラン) ユーザーにそれらの計画に定義されている Office 365 サービスへのアクセスを提供します。ただし、[ユーザーはそれらに現在割り当てられているライセンスで使用可能なすべてのサービスへのアクセスをいない可能性があります。ユーザー アカウントのサービスの状態を表示するのには、Office 365 の PowerShell を使用できます。 

## <a name="before-you-begin"></a>はじめに

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- コマンドを使用して、`Get-MsolAccountSku`と`(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus`、次の情報を検索します。
    
  - 組織で使用可能なライセンス プラン。
    
  - 各ライセンス プランで使用可能なサービス、およびサービスがリストされる順序 (インデックス番号)。
    
     計画、ライセンス、およびサービスのライセンスの詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。
    
- コマンドを使用して`Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses`(インデックス番号) を一覧には、ユーザー、および順に割り当てられているライセンスが見つかりません。
    
- _All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。
    

## <a name="to-view-services-for-a-user-account"></a>ユーザー アカウントのサービスを表示するには

ユーザーへのアクセス権を持っているすべての Office 365 サービスを表示するには、次の構文を使用します。
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

この例では、BelindaN@litwareinc.com のユーザーのアクセスを持っているサービスを使用します。自分のアカウントに割り当てられているすべてのライセンスに関連付けられているサービスが表示されます。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

次の例では、ユーザー BelindaN@litwareinc.com が、アカウントに割り当てられている最初のライセンス (インデックス番号 0) からアクセスできるサービスが表示されます。
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

特定のサービスが有効、または無効なすべてのライセンス ユーザーを調べるには、次の構文を使用します。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

以下の例では、次の情報を使用します。
  
- Office 365 サービスに関心をへのアクセスを提供するライセンスは、(インデックス番号は 0 になります) すべてのユーザーに割り当てられている最初のライセンスです。
    
- 関心を Office 365 サービスは、オンライン ビジネスおよび Exchange Online の Skype です。ライセンス プランに関連付けられているライセンス、ビジネス オンラインの Skype は、6 番目の項目に記載されているサービス (インデックス番号が 5)、9 のサービスを Exchange Online には、(インデックス番号は、8) に表示されています。
    
この例が有効になっている Skype のオンライン ビジネスおよび Exchange Online ライセンスを付与されたすべてのユーザーを返します。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

この例では、すべてのライセンスを受けたユーザーは有効になっている Skype のビジネス オンラインまたは Exchange Online を返します。
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

*複数のライセンス*が割り当てられているユーザーのためのすべてのサービスを表示するには、次の構文を使用します。

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="see-also"></a>関連項目

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [Office 365 PowerShell を使用してユーザー アカウントを作成する](create-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell でユーザー アカウントをブロックする](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Convertto-html コマンドレット](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]