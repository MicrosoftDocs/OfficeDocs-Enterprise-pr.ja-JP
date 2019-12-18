---
title: Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Office 365 PowerShell を使用して、ユーザーに割り当てられている Office 365 ライセンスを削除する方法について説明します。
ms.openlocfilehash: f88a8d32616e615ada081af6e7229da57ce3f668
ms.sourcegitcommit: 9dfaeff7a1625a7325bb94f3eb322fc161ce066b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2019
ms.locfileid: "40261540"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph モジュールの Azure Active Directory PowerShell を使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

次に、ユーザープリンシパル名 (UPN) とも呼ばれるライセンスを削除するアカウントのサインイン名を取得します。

最後に、ユーザーのサインインとライセンスプラン名を指定し、"<" と ">" の文字を削除して、次のコマンドを実行します。

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。
   
組織のライセンスプラン (**AccountSkuID** ) 情報を表示するには、以下のトピックを参照してください。
    
  - [Office 365 PowerShell でライセンスとサービスを確認する](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する](view-account-license-and-service-details-with-office-365-powershell.md)
    
_-All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。
    
### <a name="removing-licenses-from-user-accounts"></a>ユーザーアカウントからライセンスを削除する

既存のユーザー アカウントからライセンスを削除するには、次の構文を使用します:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

この例では、ユーザーアカウント BelindaN@litwareinc.com から**litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスを削除します。
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>コマンドレットを使用`Set-MsolUserLicense`して、*取り消さ*れたライセンスからユーザーを割り当て解除することはできません。 この操作は、Microsoft 365 管理センターのユーザーアカウントごとに個別に行う必要があります。
>

ライセンス付与済みの既存のユーザーのグループからライセンスを削除するには、次のいずれかの方法を使用します。
  
- **既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

この例では、米国内の販売部門のユーザーのすべてのアカウントから**litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスを削除します。
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **特定のアカウントの一覧を使用する** これを行うには、次の手順を実行します。
    
1. 次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成し、保存します。
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. 次の構文を使用してください。
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

この例では、テキストファイル C:\My Documents\accounts.txt で定義されているユーザーアカウントから**litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスを削除します。
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

既存のすべてのユーザー アカウントからライセンスを削除するには、次の構文を使用します。
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

この例では、既存のライセンスされたすべてのユーザーアカウントから**litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスを削除します。
  
```powershell
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

別の方法として、ユーザー アカウントを削除してライセンスを解放することもできます。詳細については、「[Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)」を参照してください。
  
## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

