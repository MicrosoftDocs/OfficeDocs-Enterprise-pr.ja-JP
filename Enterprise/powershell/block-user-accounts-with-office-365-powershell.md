---
title: Office 365 PowerShell でユーザー アカウントをブロックする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Office 365 PowerShell を使用して Office 365 アカウントへのアクセスをブロックおよびブロック解除する方法について説明します。
ms.openlocfilehash: 3cc063fac2fa7795ba924b7b937efc9afe6594a1
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "38706984"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell でユーザー アカウントをブロックする

**概要:** Office 365 PowerShell を使用して Office 365 アカウントへのアクセスをブロックおよびブロック解除する方法について説明します。
  
Office 365 アカウントへのアクセスをブロックすると、ユーザーがアカウントを使用して Office 365 組織のサービスとデータにサインインしてアクセスするのを防ぐことができます。 Office 365 PowerShell を使用して、個別および複数のユーザーアカウントへのアクセスをブロックすることができます。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph モジュールの Azure Active Directory PowerShell を使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
 
### <a name="block-access-to-individual-user-accounts"></a>個別のユーザーアカウントへのアクセスをブロックする

個々のユーザーアカウントをブロックするには、次の構文を使用します。
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> AzureAD コマンドレットの-ObjectID パラメーターは、アカウントのサインイン名 (ユーザープリンシパル名とも呼ばれる)、またはアカウントのオブジェクト ID のいずれかを受け入れます。 
  
この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

このユーザー アカウントのブロックを解除するには、以下のコマンドを実行します。
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

ユーザーの表示名に基づいてユーザーアカウント UPN を表示するには、次のコマンドを使用します。
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

この例では、Caleb/Ls という名前のユーザーのユーザーアカウント UPN を表示します。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

ユーザーの表示名に基づいてアカウントをブロックするには、次のコマンドを使用します。
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

次のコマンドを使用して、ユーザーアカウントのブロックされた状態をいつでも確認できます。
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>複数のユーザーアカウントへのアクセスをブロックする

複数のユーザーアカウントへのアクセスをブロックするには、次のように各行に1つのアカウントサインイン名を含むテキストファイルを作成します。
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

次のコマンドでは、サンプルテキストファイルは C:\My Documents\accounts.txt です。 これをテキストファイルのパスとファイル名に置き換えます。
  
テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

    
### <a name="block-access-to-individual-user-accounts"></a>個別のユーザーアカウントへのアクセスをブロックする

個々のユーザー アカウントへのアクセスをブロックするには、次の構文を使用します。
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

ユーザー アカウントのブロックを解除するには、次のコマンドを実行します。
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

次のコマンドを使用して、ユーザーアカウントのブロックされた状態をいつでも確認できます。
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>複数のユーザーアカウントへのアクセスをブロックする

最初に、次のような各行に1つのアカウントを含むテキストファイルを作成します。
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
次のコマンドでは、サンプルテキストファイルは C:\My Documents\accounts.txt です。 これをテキストファイルのパスとファイル名に置き換えます。
    
テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
