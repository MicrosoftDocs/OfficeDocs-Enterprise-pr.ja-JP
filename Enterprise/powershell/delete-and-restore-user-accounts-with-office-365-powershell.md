---
title: PowerShell を使用して Microsoft 365 ユーザーアカウントを削除する
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
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Microsoft 365 の PowerShell を使用してユーザーアカウントを削除する方法について説明します。
ms.openlocfilehash: 62d9dee2e6b0d2054116e5e5f005b5928112186d
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230713"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>PowerShell を使用して Microsoft 365 ユーザーアカウントを削除する

Microsoft 365 の PowerShell を使用して、ユーザーアカウントを削除することができます。
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 用 Azure Active Directory PowerShell モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。

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

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。

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

[PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell を使用して Microsoft 365 を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 の PowerShell の概要](getting-started-with-office-365-powershell.md)
