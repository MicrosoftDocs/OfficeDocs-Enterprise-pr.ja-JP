---
title: Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
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
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651183"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる

**概要:** Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。
  
ユーザーは、自分のアカウントは、ライセンスが割り当てられてライセンス プランからまで、すべての Office 365 サービスを使用できません。簡単にライセンスのないアカウントにライセンスを割り当てるには、Office 365 の PowerShell を使用できます。 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph モジュールの Azure Active Directory PowerShell を使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  

次に、ライセンスの一覧は、このコマンドを使用して、テナントの予定です。

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

次に、ライセンスとも呼ばれるユーザー プリンシパル名 (UPN) を追加するアカウントのサインイン名を取得します。

最後に、ユーザーのサインイン名とライセンス プランの名前を指定し、これらのコマンドを実行します。

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

それぞれの計画、組織内で使用可能なライセンス プランと利用可能なライセンスの数を表示するのには、 **Get MsolAccountSku**コマンドを実行します。各プランで利用可能なライセンスの数は、 **ActiveUnits** - **WarningUnits** - **ConsumedUnits**。計画、ライセンス、およびサービスのライセンスの詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。
    
組織のライセンスのないアカウントを検索するには、このコマンドを実行します。

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
**UsageLocation**プロパティが有効な ISO 3166-1 アルファ 2 国コードに設定されているユーザー アカウントにライセンスを割り当てることだけできます。たとえば、アメリカ合衆国およびフランスの FR のことです。いくつかの Office 365 サービスは、特定の国では使用できません。詳細については、[ライセンスによる使用制限の詳細](https://go.microsoft.com/fwlink/p/?LinkId=691730)を参照してください。
    
**UsageLocation**の値を持たないアカウントを検索するには、このコマンドを実行します。

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

アカウントの**UsageLocation**値を設定するには、このコマンドを実行します。

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

次に例を示します。

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
**-All** パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。

### <a name="assigning-licenses-to-user-accounts"></a>ユーザー アカウントにライセンスを割り当てる
    
ライセンスをユーザーに割り当てるには、Office 365 の PowerShell で次のコマンドを使用します。
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

次の使用例は、 **litwareinc:ENTERPRISEPACK** (Office 365 エンタープライズ E3) ライセンスのライセンスのないユーザーの**belindan@litwareinc.com**するための計画からライセンスを割り当てます。
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

ライセンスをライセンスのない多くのユーザーに割り当てるには、このコマンドを実行します。
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
>同じライセンス プランから、ユーザーに複数のライセンスを割り当てることはできません。十分な利用可能なライセンスをお持ちでない場合は、取り出されると、 **Get MsolUser**コマンドレットで利用可能なライセンスが不足するまでの順序でユーザーにライセンスが割り当てられます。
>

次の使用例は、 **litwareinc:ENTERPRISEPACK** (Office 365 エンタープライズ E3) のライセンスについてのすべてのライセンスのないユーザーにライセンスを割り当てます。
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

この例では、米国内の販売部門でのライセンスのないユーザーに、同じライセンスを割り当てます。
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
