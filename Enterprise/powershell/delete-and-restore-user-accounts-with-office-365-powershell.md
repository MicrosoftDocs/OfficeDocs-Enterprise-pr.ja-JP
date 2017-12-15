---
title: "Office 365 PowerShell を使用したユーザー アカウントの削除と復元"
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
- DecEntMigration
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Office 365 の PowerShell を使用して削除し、Office 365 ユーザー アカウントを復元する方法について説明します。"
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell を使用したユーザー アカウントの削除と復元

**の概要:** Office 365 の PowerShell を使用して削除し、Office 365 ユーザー アカウントを復元する方法について説明します。
  
Office 365 PowerShell を使用してユーザー アカウントを削除する場合、アカウントは完全には削除されません。削除されたユーザー アカウントは 30 日以内であれば復元できます。
  
## <a name="before-you-begin"></a>開始する前に

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- 使用せず、 **Get MsolUser**コマンドレットを使用するかどうかは、_のすべて_パラメーターでは、最初の 500 個のアカウントのみが返されます。
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Office 365 PowerShell を使用して、個々のユーザー アカウントへのアクセスをブロックする
<a name="ShortVersion"> </a>

ユーザー アカウントを削除するには、次の構文を使用します。
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

この例では、ユーザー アカウント BelindaN@litwareinc.com を削除します。
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

削除されたユーザー アカウントを 30 日間の猶予期間内に復元するには、次の構文を使用します。
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

この例では、削除されたユーザー アカウント BelindaN@litwareinc.com を復元します。
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **メモ:**
  
- 復元できる削除されたユーザーの一覧を表示するには、次のコマンドを実行します。
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- ユーザー アカウントの元のユーザー プリンシパル名を別のアカウントで使用している場合は、ユーザー アカウントを復元する際に、 _UserPrincipalName_ の代わりに _NewUserPrincipalName_ パラメーターを使用して別のユーザー プリンシパル名を指定します。
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>Azure Active Directory V2 PowerShell モジュールを使用したユーザー アカウントの削除
<a name="ShortVersion"> </a>

Azure Active Directory V2 PowerShell モジュールから**削除 AzureADUser**コマンドレットを使用するには、まずお客様のサブスクリプションに接続する必要があります。この手順では、 [Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)を参照してください。
  
接続したら、以下の構文を使用してユーザー アカウントを個別に削除します。
  
```
Remove-AzureADUser -ObjectID <Account>
```

この例では、ユーザー アカウント fabricec@litwareinc.com を削除します。
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **Remove-AzureAD** コマンドレットの **-ObjectID** パラメーターは、別名ユーザー プリンシパル名であるアカウント名か、アカウントのオブジェクト ID のいずれかを受け付けます。
  
ユーザーの名前に基づいてアカウント名を表示するには、以下のコマンドを使用します。
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

この例では、Caleb Sills という名前のユーザーのアカウント名を表示します。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

ユーザーの名前に基づいてアカウントを削除するには、以下のコマンドを使用します。
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>関連項目
<a name="SeeAlso"> </a>

Office 365 の PowerShell でユーザーを管理する方法は次のトピックを参照してください。
  
- [Office 365 PowerShell を使用してユーザー アカウントを作成する](create-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell でユーザー アカウントをブロックする](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

