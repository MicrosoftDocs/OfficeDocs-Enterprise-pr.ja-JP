---
title: "Office 365 PowerShell でユーザー アカウントをブロックする"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- DecEntMigration
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: "Office 365 の PowerShell を使用してブロックし、Office 365 アカウントへのアクセスをブロック解除する方法について説明します。"
ms.openlocfilehash: f22656426e7aa3adf764a3f90adea84cf57a5e89
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell でユーザー アカウントをブロックする

**の概要:** Office 365 の PowerShell を使用してブロックし、Office 365 アカウントへのアクセスをブロック解除する方法について説明します。
  
Office 365 アカウントへのアクセスをブロックできなくなりますアカウントを使用してサインインして、サービスと Office 365 の組織内のデータにアクセスします。アカウントへのアクセスを禁止すると、サインインを試みると、ユーザーは次のエラー メッセージを受け取ります。
  
![ブロックされた Office 365 アカウント。](images/o365_powershell_account_blocked.png)
  
Office 365 の PowerShell を使用するには個別にアクセスし、複数のユーザー アカウントをブロックします。
  
## <a name="before-you-begin"></a>開始する前に

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- ユーザー アカウントをブロックするとは限りすべてのユーザーのデバイスとクライアントを有効にするために 24 時間かかる場合があります。
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Office 365 PowerShell を使用して、個々のユーザー アカウントへのアクセスをブロックする

個々のユーザー アカウントへのアクセスをブロックするには、次の構文を使用します。
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

この例では、ユーザー アカウント fabricec@litwareinc.com へのアクセスをブロックします。
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

ユーザー アカウントのブロックを解除するには、次のコマンドを実行します。
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

いつでも、次のコマンドでユーザー アカウントのブロック状態をチェックできます。
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>Office 365 の PowerShell を使用して複数のユーザー アカウントへのアクセスをブロックするには

最初に、次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
次のコマンドでは、テキスト ファイルの例とは、C:\My Documents\Accounts.txt です。これをテキスト ファイルのパスとファイル名で置き換えます。
    
テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $true
  ```
テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUser -UserPrincipalName $_.UserPrincipalName -BlockCredential $false
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>Azure Active Directory V2 PowerShell モジュールを使用して、ユーザー アカウントへのアクセスをブロックします。

Azure Active Directory V2 PowerShell モジュールから **New-AzureADUser** コマンドレットを使用するには、まず自分のサブスクリプションに接続する必要があります。手順については、「[Azure Active Directory V2 PowerShell モジュールを使用した接続](https://go.microsoft.com/fwlink/?linkid=842218)」を参照してください。
  
接続したら、以下の構文を使用して、個別のユーザー アカウントをブロックします。
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> Set-AzureAD コマンドレットの -ObjectID パラメーターは、アカウント名 (ユーザー プリンシパル名とも呼ばれる) か、アカウントのオブジェクト ID のいずれかを受け付けます。 
  
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
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

この例では、氏の窓台をという名前のユーザーのユーザー アカウント UPN を使用します。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

ユーザーの名前に基づいてアカウントをブロックするには、以下のコマンドを使用します。
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

いつでも、次のコマンドでユーザー アカウントのブロック状態をチェックできます。
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

複数のユーザー アカウントへのアクセスをブロックするには、次のように各行に 1 つのアカウント名を含むテキスト ファイルを作成します。
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

次のコマンドでは、テキスト ファイルの例とは、C:\My Documents\Accounts.txt です。これをテキスト ファイルのパスとファイル名で置き換えます。
    
テキスト ファイルに記載されているアカウントへのアクセスをブロックするには、次のコマンドを実行します。
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $true
```

テキスト ファイルに記載されているアカウントへのアクセスのブロックを解除するには、次のコマンドを実行します。
    
```
Get-Content "C:\My Documents\Accounts.txt" | Set-AzureADUSer -ObjectID $_.ObjectID -AccountEnabled $false
```

## <a name="see-also"></a>関連項目
<a name="SeeAlso"> </a>

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [Office 365 PowerShell を使用してユーザー アカウントを作成する](create-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [セット MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [新しい-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

