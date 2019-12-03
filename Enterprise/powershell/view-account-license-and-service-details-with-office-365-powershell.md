---
title: Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Office 365 PowerShell を使用して、ユーザーに割り当てられている Office 365 サービスを確認する方法について説明します。
ms.openlocfilehash: f73acb5a107aa6ef970046a371b7a722a6abc8d9
ms.sourcegitcommit: 460c722d63e7e604ef0a57ec18fa7900fa6a4157
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2019
ms.locfileid: "39655869"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する

Office 365 のライセンスプラン (Sku または Office 365 プランとも呼ばれます) からのライセンスでは、これらのプランに対して定義されている Office 365 サービスへのアクセス権がユーザーに付与されます。 しかし、ユーザーは、現在割り当てられているライセンスで使用可能なすべてのサービスにアクセスできるとは限りません。 Office 365 PowerShell を使用して、ユーザーアカウントのサービスの状態を表示できます。 

ライセンスプラン、ライセンス、およびサービスの詳細については、「 [Office 365 PowerShell でライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph モジュールの Azure Active Directory PowerShell を使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

各ライセンスプランで利用可能なサービスを一覧表示するには、次のコマンドを使用します。

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

ユーザーアカウントに割り当てられているライセンスの一覧を表示するには、次のコマンドを使用します。

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

次に、このコマンドを実行して、組織で使用可能なライセンスプランを一覧表示します。 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

次に、このコマンドを実行して、各ライセンスプランで使用可能なサービスと、それらが表示される順序 (インデックス番号) を一覧表示します。

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
```
  
このコマンドを使用して、ユーザーに割り当てられているライセンスと、ユーザーが表示される順序 (インデックス番号) を一覧表示します。

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

>[!Note]
>**All** パラメーターなしで _Get-MsolUser_ コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。
>
   

### <a name="to-view-services-for-a-user-account"></a>ユーザーアカウントのサービスを表示するには

ユーザーがアクセスできるすべての Office 365 サービスを表示するには、次の構文を使用します。
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

この例では、ユーザー BelindaN@litwareinc.com がアクセスできるサービスを表示します。 これにより、このユーザーのアカウントに割り当てられているすべてのライセンスに関連付けられているサービスが表示されます。
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

次の例では、ユーザー BelindaN@litwareinc.com が、アカウントに割り当てられている最初のライセンス (インデックス番号 0) からアクセスできるサービスが表示されます。
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

*複数のライセンス*が割り当てられているユーザーのすべてのサービスを表示するには、次の構文を使用します。

```powershell
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

  
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
