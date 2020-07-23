---
title: PowerShell を使用して Microsoft 365 アカウントのライセンスとサービスの詳細を表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: PowerShell を使用して、ユーザーに割り当てられている Microsoft 365 サービスを確認する方法について説明します。
ms.openlocfilehash: 73af2fd40df8b36507250edcef48359e9d555a7f
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230243"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>PowerShell を使用して Microsoft 365 アカウントのライセンスとサービスの詳細を表示する

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 では、ライセンスプラン (Sku または Microsoft 365 プランとも呼ばれます) からのライセンスで、これらのプランに対して定義されている Microsoft 365 サービスへのアクセス権をユーザーに付与します。 しかし、ユーザーは、現在割り当てられているライセンスで使用可能なすべてのサービスにアクセスできるとは限りません。 Microsoft 365 の PowerShell を使用して、ユーザーアカウントのサービスの状態を表示できます。 

ライセンスプラン、ライセンス、およびサービスの詳細については、「 [PowerShell を使用してライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 用 Azure Active Directory PowerShell モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
  
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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。

次に、このコマンドを実行して、組織で使用可能なライセンスプランを一覧表示します。 

```powershell
Get-MsolAccountSku
```
>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

次に、このコマンドを実行して、各ライセンスプランで使用可能なサービスと、それらが表示される順序 (インデックス番号) を一覧表示します。

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
このコマンドを使用して、ユーザーに割り当てられているライセンスと、ユーザーが表示される順序 (インデックス番号) を一覧表示します。

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>ユーザーアカウントのサービスを表示するには

ユーザーがアクセスできるすべての Microsoft 365 サービスを表示するには、次の構文を使用します。
  
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
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
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

[PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell を使用して Microsoft 365 を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 の PowerShell の概要](getting-started-with-office-365-powershell.md)
