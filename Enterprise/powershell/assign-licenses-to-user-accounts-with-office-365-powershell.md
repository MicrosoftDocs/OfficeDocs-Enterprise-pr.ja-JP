---
title: Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123294"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる

**概要:** Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。
  
ユーザーは自分のアカウントにライセンスが供与されるまで Office 365 サービスを一切使用できないため、Office 365 のユーザー アカウントへのライセンス供与は重要です。Office 365 PowerShell を使用することにより、効率的にライセンスをライセンスのないアカウント、特に複数のアカウントに割り当てることができます。 

## <a name="before-you-begin"></a>はじめに
<a name="RTT"> </a>

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- **Get-MsolAccountSku** コマンドレットを使用して、利用可能なライセンス プランと組織で利用可能なライセンスのプランごとの数を表示します。各プランで利用可能なライセンスの数は、**ActiveUnits** - **WarningUnits** - **ConsumedUnits** です。ライセンス プラン、ライセンス、サービスの詳細については、「[Office 365 PowerShell でライセンスとサービスを確認する](view-licenses-and-services-with-office-365-powershell.md)」を参照してください。
    
- 組織内のライセンスのないアカウントを検索するには、コマンド  `Get-MsolUser -All -UnlicensedUsersOnly` を実行します。
    
- ライセンスは、**UsageLocation** プロパティが有効な ISO 3166-1 alpha-2 の国別コードに設定されているユーザー アカウントにのみ割り当てることができます。たとえば、米国は US、フランスは FR です。一部の Office 365 サービスは特定の国では使用できません。詳細については、「[ライセンスによる使用制限について](https://go.microsoft.com/fwlink/p/?LinkId=691730)」を参照してください。
    
    **UsageLocation** 値のないアカウントを検索するには、コマンド `Get-MsolUser -All | where {$_.UsageLocation -eq $null}` を実行します。アカウントに **UsageLocation** 値を設定するには、構文 `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>` を使用します。例: `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。
    
- `-All` パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。

## <a name="assigning-licenses-to-user-accounts"></a>ユーザー アカウントにライセンスを割り当てる
    
ユーザーにライセンスを割り当てるには、Office 365 PowerShell で次の構文を使用します。
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

この例では、ライセンスを `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスのないユーザー `belindan@litwareinc.com` に割り当てます。
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

ライセンスのない多数のユーザーにライセンスを割り当てるには、次の構文を使用します。
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **メモ**
  
- 複数のライセンスを同じライセンス プランのユーザーに割り当てることはできません。
    
- 十分な数の利用可能なライセンスをお持ちでない場合は、使用可能なライセンスがなくなるまで、ライセンスは **Get-MsolUser** コマンドレットによって返される順序でユーザーに割り当てられます。
    
この例では、ライセンスを `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスのないユーザーすべてに割り当てます。
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

この例では、これらの同じライセンスを米国内にある営業部のライセンスのないユーザーに割り当てます。
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>関連項目
<a name="SeeAlso"> </a>

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [ユーザー アカウントを作成します。](create-user-accounts-with-office-365-powershell.md)
    
- [削除し、ユーザー アカウントを復元します。](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [ブロックのユーザー アカウント](block-user-accounts-with-office-365-powershell.md)
    
- [ユーザー アカウントからライセンスを削除します。](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

