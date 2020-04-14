---
title: Office 365 PowerShell を使用してユーザーアカウントを削除する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Office 365 PowerShell を使用して Office 365 ユーザーアカウントを削除する方法について説明します。
ms.openlocfilehash: ea803d82bb54e5430ceb9a59e8c04a0f72b200fc
ms.sourcegitcommit: 069f56455252d6f4001ec0ecee792b83b585e692
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "43237808"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell を使用してユーザーアカウントを削除する

Office 365 PowerShell を使用して、ユーザーアカウントを削除できます。
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph モジュールの Azure Active Directory PowerShell を使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。

接続したら、以下の構文を使用してユーザー アカウントを個別に削除します。
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

この例では、ユーザー アカウント fabricec@litwareinc.com を削除します。
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> **Set-azureaduser**コマンドレットの **-ObjectID**パラメーターは、アカウントのサインイン名 (ユーザープリンシパル名とも呼ばれる)、またはアカウントのオブジェクト ID のいずれかを受け入れます。
  
ユーザーの名前に基づいてアカウント名を表示するには、以下のコマンドを使用します。
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

この例では、Caleb Sills という名前のユーザーのアカウント名を表示します。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

ユーザーの表示名に基づいてアカウントを削除するには、次のコマンドを使用します。
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する

Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用してユーザーアカウントを削除しても、そのアカウントは完全に削除されません。 削除されたユーザー アカウントは 30 日以内であれば復元できます。

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

ユーザー アカウントを削除するには、次の構文を使用します。
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

この例では、ユーザー アカウント BelindaN@litwareinc.com を削除します。
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

削除されたユーザー アカウントを 30 日間の猶予期間内に復元するには、次の構文を使用します。
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

この例では、削除されたユーザー アカウント BelindaN@litwareinc.com を復元します。
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **メモ:**
  
- 復元できる削除されたユーザーの一覧を表示するには、次のコマンドを実行します。
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- ユーザーアカウントの元のユーザープリンシパル名が別のアカウントで使用されている場合、ユーザーアカウントを復元するときに別のユーザープリンシパル名を指定するには、 _UserPrincipalName_の代わりに_newuserprincipalname_パラメーターを使用します。


## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
