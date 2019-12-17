---
title: Office 365 PowerShell でロールをユーザー アカウントに割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: '概要: Office 365 PowerShell を使用して、ロールをユーザー アカウントに割り当てます。'
ms.openlocfilehash: 999b44f56e2652c0d6d2d746a3ed204be9d1f69c
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072529"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell でロールをユーザー アカウントに割り当てる

Office 365 PowerShell を使用すると、ロールをユーザー アカウントに迅速かつ簡単に割り当てることができます。

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 用 Azure Active Directory PowerShell モジュールを使用する

最初に、全体管理者アカウントを使用して [Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
  
次に、ロールに追加するユーザー アカウントのサインイン名を判別します (例: fredsm@contoso.com)。サインイン名はユーザー プリンシパル名 (UPN) とも呼ばれます。

次に、ロールの名前を決めます。 [Azure Active Directoryでこの管理者ロールのアクセス許可の一覧](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)を使用します。

>[!Note]
>この記事のメモに注意してください。 Azure AD PowerShellでは一部のロール名が異なります。 たとえば、Microsoft 365管理センターの "SharePoint Administrator"ロールは、Azure AD PowerShellでは "SharePoint Service Administrator"という異なった名前がついています。
>

次に、サインイン名とロール名を入力し、次のコマンドを実行します。
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

以下は、SharePoint サービス管理者の役割を belindan@contoso.com アカウントに割り当てる、完成したコマンドセットの例です。
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

特定のロールのユーザー名の一覧を表示するには、次のコマンドを使用します。

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する

最初に、全体管理者アカウントを使用して [Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。
  
### <a name="for-a-single-role-change"></a>単一ロールの変更の場合

特定のユーザーアカウントの最も一般的な方法は、その表示名または電子メール名 (サインイン名またはユーザープリンシパル名 (UPN)) を使用することです。

#### <a name="display-names-of-user-accounts"></a>ユーザーアカウントの表示名

ユーザーアカウントの表示名の処理に使用する場合は、次の点を確認してください。
  
- 構成するユーザー アカウント。
    
    ユーザー アカウントを指定するには、その表示名を判別する必要があります。アカウントの完全な一覧を取得するには、次のコマンドを使用します。
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    このコマンドにより、ユーザー アカウントの表示名の一覧が、表示名順に並び替えられて、一度に 1 画面ずつ示されます。 **Where** コマンドレットを使用すると、一覧をフィルター処理して、出力するセットを小さくできます。次に例を示します。

   >[!Note]
   >PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。
    
- 割り当てるロール。
    
    ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

アカウントの表示名とロールの名前を判別した後、次のコマンドを使用してアカウントにロールを割り当てます。
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

コマンドをコピーし、メモ帳に貼り付けます。**$dispName** 変数と **$roleName** 変数に関しては、説明テキスト部分を値に置き換えて、\< 記号と > 記号を削除します。引用符はそのまま残します。変更後の行をコピーし、[Windows PowerShell 用 Windows Azure Active Directory モジュール] ウィンドウに貼り付けて実行します。または、Windows PowerShell 統合スクリプト環境 (ISE) を使用することができます。
  
コマンド セットの完成例を以下に示します。
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>ユーザーアカウントのサインイン名

ユーザーアカウントのサインイン名または Upn を使用する場合は、次の点を確認してください。
  
- ユーザーアカウントの UPN。
    
    UPN がまだわからない場合は、次のコマンドを使用します。
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    このコマンドは、UPN で並べ替えて、一度に1画面ずつ、ユーザーアカウントの UPN を一覧表示します。 **Where** コマンドレットを使用すると、一覧をフィルター処理して、出力するセットを小さくできます。 次に例を示します。
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。
    
- 割り当てるロール。
    
    ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

アカウントの UPN と役割の名前を取得したら、次のコマンドを使用してアカウントに役割を割り当てます。
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

コマンドをコピーしてメモ帳に貼り付けます。 **$UpnName**変数と **$roleName**変数については、説明テキストをその値に置き換え\< 、および > 文字を削除して、引用符を残します。 変更された行をコピーして、windows PowerShell 用 Windows Azure Active Directory モジュールウィンドウに貼り付けます。 または、Windows PowerShell ISE を使用することもできます。
  
コマンド セットの完成例を以下に示します。
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>複数の役割の変更

複数の役割の変更については、次のことを決定します。
  
- 構成するユーザー アカウント。 前のセクションの方法を使用して、表示名または Upn のセットを収集できます。
    
- 各ユーザー アカウントに割り当てるロール。
    
    ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

次に、[表示名] または [UPN] および [役割名] フィールドを含むコンマ区切り値 (CSV) テキストファイルを作成します。 これは、Microsoft Excel で簡単に実行できます。

表示名の例を次に示します。
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

その後、PowerShell コマンド プロンプトで CSV ファイルの場所を入力し、完成したコマンドを実行します。
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

次に、Upn の例を示します。
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

その後、PowerShell コマンド プロンプトで CSV ファイルの場所を入力し、完成したコマンドを実行します。
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>関連項目

- [Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
- [Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
