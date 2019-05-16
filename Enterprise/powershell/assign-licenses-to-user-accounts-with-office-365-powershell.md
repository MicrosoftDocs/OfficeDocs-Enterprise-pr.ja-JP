---
title: Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
audience: Admin
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
search.appverid:
- MET150
description: Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。
ms.openlocfilehash: 91fe9f3a14663ebb9adb61700de3004edd236e0c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069283"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる

**概要:** Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。
  
ユーザーがライセンスプランからライセンスを割り当てられるまで、どの Office 365 サービスも使用できません。 Office 365 PowerShell を使用して、ライセンスのないアカウントにライセンスをすばやく割り当てることができます。 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph モジュールの Azure Active Directory PowerShell を使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

次に、ユーザープリンシパル名 (UPN) とも呼ばれるライセンスを追加するアカウントのサインイン名を取得します。

最後に、ユーザーのサインイン名とライセンスプラン名を指定し、これらのコマンドを実行します。

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

**Get-msolaccountsku**コマンドを実行して、使用可能なライセンスプランと、組織内の各プランの使用可能なライセンスの数を表示します。 各プランで利用可能なライセンスの数は、 **ActiveUnits** - **WarningUnits** - **ConsumedUnits** です。 ライセンスプラン、ライセンス、およびサービスの詳細については、「 [Office 365 PowerShell でライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。
    
組織内のライセンスのないアカウントを検索するには、次のコマンドを実行します。

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
ライセンスは、有効な ISO 3166-1 国コードに設定**** されているユーザーアカウントにのみ割り当てることができます。 たとえば、米国は US、フランスは FR です。 一部の Office 365 サービスは特定の国では使用できません。 詳細については、「[ライセンス制限につい](https://go.microsoft.com/fwlink/p/?LinkId=691730)て」を参照してください。
    
利用**場所**の値を持たないアカウントを検索するには、次のコマンドを実行します。

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

アカウントに対し**** て、使い方の値を設定するには、次のコマンドを実行します。

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

次に例を示します。

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
**-All** パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。

### <a name="assigning-licenses-to-user-accounts"></a>ユーザーアカウントへのライセンスの割り当て
    
ユーザーにライセンスを割り当てるには、Office 365 PowerShell で次のコマンドを使用します。
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

この例では、ライセンスを**litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスプランからライセンスのないユーザー **belindan@litwareinc.com**に割り当てます。
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

ライセンスをライセンスのない複数のユーザーに割り当てるには、このコマンドを実行します。
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>複数のライセンスを同じライセンス プランのユーザーに割り当てることはできません。 十分な数の利用可能なライセンスをお持ちでない場合は、使用可能なライセンスがなくなるまで、ライセンスは **Get-MsolUser** コマンドレットによって返される順序でユーザーに割り当てられます。
>

この例では、ライセンスを**litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスプランからすべてのライセンスのないユーザーに割り当てます。
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

この例では、米国内の販売部門のライセンスのないユーザーに同じライセンスを割り当てます。
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
