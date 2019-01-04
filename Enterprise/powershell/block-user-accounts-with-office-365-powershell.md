---
title: Office 365 PowerShell でユーザー アカウントをブロックする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Office 365 の PowerShell を使用してブロックし、Office 365 アカウントへのアクセスをブロック解除する方法について説明します。
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546478"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell でユーザー アカウントをブロックする

**の概要:** Office 365 の PowerShell を使用してブロックし、Office 365 アカウントへのアクセスをブロック解除する方法について説明します。
  
Office 365 アカウントへのアクセスをブロックできなくなりますアカウントを使用してサインインして、サービスと Office 365 の組織内のデータにアクセスします。Office 365 の PowerShell を使用するには個別にアクセスし、複数のユーザー アカウントをブロックします。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory の PowerShell を使用して、グラフのモジュールの

最初は[、Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
 
### <a name="block-access-to-individual-user-accounts"></a>個々 のユーザー アカウントへのアクセスをブロック

個々 のユーザー アカウントをブロックするのにには、次の構文を使用します。
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> セット AzureAD コマンドレットでのオブジェクト Id パラメーターは、どちらかのアカウントでサインイン名、ユーザー プリンシパル名、またはアカウントのオブジェクト ID とも呼ばれますを受け入れます。 
  
この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

このユーザー アカウントのブロックを解除するには、以下のコマンドを実行します。
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

UPN は、ユーザーの表示名に基づくユーザー アカウントを表示するには、次のコマンドを使用します。
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

この例では、氏の窓台をという名前のユーザーのユーザー アカウント UPN を使用します。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

ユーザーの表示名を基に、アカウントをブロックするには、次のコマンドを使用します。
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

いつでも、次のコマンドでユーザー アカウントのブロック状態をチェックできます。
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>複数のユーザー アカウントへのアクセスをブロック

複数のユーザー アカウントへのアクセスをブロックするには、1 アカウントでサインイン名次のように各行に含まれているテキスト ファイルを作成します。
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

次のコマンドでは、テキスト ファイルの例とは、C:\My Documents\Accounts.txt です。これをテキスト ファイルのパスとファイル名で置き換えます。
  
テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>モジュールを使用して、Microsoft Azure Active Directory Windows PowerShell の

最初は[、Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。

    
### <a name="block-access-to-individual-user-accounts"></a>個々 のユーザー アカウントへのアクセスをブロック

個々のユーザー アカウントへのアクセスをブロックするには、次の構文を使用します。
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

ユーザー アカウントのブロックを解除するには、次のコマンドを実行します。
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

いつでも、次のコマンドでユーザー アカウントのブロック状態をチェックできます。
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>複数のユーザー アカウントへのアクセスをブロック

最初に、次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
次のコマンドでは、テキスト ファイルの例とは、C:\My Documents\Accounts.txt です。これをテキスト ファイルのパスとファイル名で置き換えます。
    
テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
