---
title: PowerShell を使用して Microsoft 365 ユーザーアカウントに役割を割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: '概要: Microsoft 365 の PowerShell を使用して、ユーザーアカウントに役割を割り当てます。'
ms.openlocfilehash: 2be491692c23b1f528612cc5c56e041553f80c48
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230873"
---
# <a name="assign-roles-to-microsoft-365-user-accounts-with-powershell"></a>PowerShell を使用して Microsoft 365 ユーザーアカウントに役割を割り当てる

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 の PowerShell を使用して、ユーザーアカウントに役割をすばやく簡単に割り当てることができます。

>[!Note]
>Microsoft 365 管理センターを使用してユーザーアカウントに役割を割り当てるには、[次の手順](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles)を参照してください。
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 用 Azure Active Directory PowerShell モジュールを使用する

最初に、全体管理者アカウントを使用して[Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
  
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

最初に、全体管理者アカウントを使用して[Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。
  
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

コマンドをコピーしてメモ帳に貼り付けます。 **$DispName**変数と **$roleName**変数については、説明テキストをその値に置き換え、 \< and > 文字を削除して、引用符のままにします。 変更された行をコピーして、windows PowerShell 用 Windows Azure Active Directory モジュールウィンドウに貼り付けます。 または、Windows PowerShell 統合スクリプト環境 (ISE) を使用することもできます。
  
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

コマンドをコピーしてメモ帳に貼り付けます。 **$UpnName**変数と **$roleName**変数については、説明テキストをその値に置き換え、 \< and > 文字を削除して、引用符のままにします。 変更された行をコピーして、windows PowerShell 用 Windows Azure Active Directory モジュールウィンドウに貼り付けます。 または、Windows PowerShell ISE を使用することもできます。
  
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

- [PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [PowerShell を使用して Microsoft 365 を管理する](manage-office-365-with-office-365-powershell.md)
- [Microsoft 365 の PowerShell の概要](getting-started-with-office-365-powershell.md)
