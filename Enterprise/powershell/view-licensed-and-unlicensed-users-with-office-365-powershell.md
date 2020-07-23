---
title: PowerShell を使用してライセンスを付与された Microsoft 365 ユーザーを表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/21/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: PowerShell を使用してライセンスを付与された Microsoft 365 ユーザーアカウントを表示する方法について説明します。
ms.openlocfilehash: 02b1f76bab0e64e4e7e72f5e5556f5047d956d11
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230253"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>PowerShell を使用してライセンスを付与された Microsoft 365 ユーザーを表示する

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 組織のユーザーアカウントには、組織で使用可能なライセンスプランから割り当てられている利用可能なライセンスの一部、またはすべてがある場合があります。 Microsoft 365 の PowerShell を使用して、組織内のライセンスを取得したユーザーとライセンスのないユーザーをすばやく見つけることができます。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 用 Azure Active Directory PowerShell モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
 
ライセンスプラン (ライセンスのないユーザー) が割り当てられていない組織内のすべてのユーザーアカウントの一覧を表示するには、次のコマンドを実行します。
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

ライセンスプラン (ライセンスユーザー) のいずれかが割り当てられている組織内のすべてのユーザーアカウントの一覧を表示するには、次のコマンドを実行します。
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>サブスクリプション内のすべてのユーザーを一覧表示するには、コマンドを使用し `Get-AzureAdUser -All $true` ます。
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。

組織内のすべてのユーザーアカウントとライセンスの状態の一覧を表示するには、PowerShell で次のコマンドを実行します。
  
```powershell
Get-MsolUser -All
```

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

組織内でライセンスのないすべてのユーザー アカウントの一覧を表示するには、次のコマンドを実行します。
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

組織内でライセンスのあるすべてのユーザー アカウントの一覧を表示するには、次のコマンドを実行します。
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>関連項目

[PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell を使用して Microsoft 365 を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 の PowerShell の概要](getting-started-with-office-365-powershell.md)
