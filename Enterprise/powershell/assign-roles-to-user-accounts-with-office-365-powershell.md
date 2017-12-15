---
title: "Office 365 PowerShell でロールをユーザー アカウントに割り当てる"
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "概要:Office 365 PowerShell と Add-MsolRoleMember コマンドレットを使用して、ユーザー アカウントにロールを割り当てます。"
ms.openlocfilehash: 673a71fb2f85515276e94767ed3f9dd40655dfea
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell でロールをユーザー アカウントに割り当てる

 **の概要:**ユーザー アカウントにロールを割り当てるには、Office 365 の PowerShell および**追加 MsolRoleMember**コマンドレットを使用します。
  
できます迅速かつ容易にロールを割り当てるユーザー アカウントの表示名およびロール名を識別することによって Office 365 の PowerShell を使用してユーザー アカウントにします。
  
## <a name="before-you-begin"></a>はじめに

このトピックの手順では、全体管理者アカウントを使用して Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
  
## <a name="for-a-single-role-change"></a>単一ロールの変更の場合

以下を判別します。
  
- 構成するユーザー アカウント。
    
    ユーザー アカウントを指定するには、その表示名を決定します。アカウントを完全なリストを取得するには、このコマンドを使用します。
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    このコマンドにより、ユーザー アカウントの表示名の一覧が、表示名順に並び替えられて、一度に 1 画面ずつ示されます。 **Where** コマンドレットを使用すると、一覧をフィルター処理して、出力するセットを小さくできます。次に例を示します。
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。
    
- 割り当てるロール。
    
    ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

アカウントの表示名とロールの名前を判別した後、次のコマンドを使用してアカウントにロールを割り当てます。
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

コマンドをコピーし、メモ帳に貼り付けます。**$DispName**と**$roleName**の変数の説明のテキストのそれらの値を削除、\<と > 文字、および引用符のままにします。変更後の行をコピーし、それらを実行するのには、Windows Azure Active Directory モジュールを Windows PowerShell のウィンドウに貼り付けます。また、Windows PowerShell 統合スクリプト環境 (ISE) を使用することができます。
  
コマンド セットの完成例を以下に示します。
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a>複数ロールの変更の場合

以下を判別します。
  
- 構成するユーザー アカウント。
    
    ユーザー アカウントを指定するには、その表示名を判別する必要があります。アカウントの一覧を取得するには、次のコマンドを使用します。
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    このコマンドは、一度に 1 つの画面の表示名順に並べ替え、すべてのユーザー アカウントの表示名を一覧表示します。**ある**コマンドレットを使用してサイズを小さく設定するリストをフィルター処理できます。例を以下に示します。
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。
    
- 各ユーザー アカウントに割り当てるロール。
    
    ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

次に、DisplayName フィールドと RoleName フィールドが含まれるコンマ区切り値 (CSV) テキスト ファイルを作成します。次に例を示します。
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

その後、PowerShell コマンド プロンプトで CSV ファイルの場所を入力し、完成したコマンドを実行します。
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>See also

#### 

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
#### 

[Add-MsolRoleMember](https://msdn.microsoft.com/library/dn194120.aspx)

