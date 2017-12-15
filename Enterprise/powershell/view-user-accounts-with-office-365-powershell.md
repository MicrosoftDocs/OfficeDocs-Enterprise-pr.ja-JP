---
title: "Office 365 PowerShell でユーザー アカウントを表示する"
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
- LIL_Placement
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "概要: 表示、リスト、または Office 365 の PowerShell でのさまざまな方法でユーザー アカウントを表示します。"
ms.openlocfilehash: b27f9045d26d4dabd3ada70766491f722d822a91
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell でユーザー アカウントを表示する

 **の概要:**ボックスの一覧を表示、または Office 365 の PowerShell でのさまざまな方法でユーザー アカウントを表示します。
  
Office 365 の管理センターを使用するには、Office 365 テナントのアカウントを表示するのも Office 365 の PowerShell を使用して Office 365 の管理センターができないことがいくつかの操作を行います。
  
## <a name="before-you-begin"></a>開始する前に

このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
  
## <a name="display-office-365-user-account-information"></a>Office 365 ユーザー アカウント情報を表示する

ユーザー アカウントの完全な一覧を表示するには、Office 365 の PowerShell コマンド プロンプトまたは PowerShell 統合スクリプト環境 (ISE) でこのコマンドを実行します。
  
```
Get-MsolUser
```

次のような情報が表示されます。
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get MsolUser**コマンドレットでは、表示されるユーザー アカウントのセットをフィルター処理するパラメーターのセットもあります。など、ライセンスのないユーザー (ユーザーが、Office 365 に追加されたこと、サービスのいずれかを使用するのにはライセンスされていないはまだ) の一覧の場合は、このコマンドを実行します。
  
```
Get-MsolUser -UnlicensedUsersOnly
```

次のような情報が表示されます。
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

表示をフィルター処理する追加のパラメーターの詳細について表示するには、ユーザー アカウントの設定では、 [Get MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx)を参照してください。
  
詳細表示するにはアカウントの一覧のオプションを選択することができます**Where-object**コマンドレットと組み合わせて使用**Get MsolUser**コマンドレットです。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、Office 365 の PowerShell コマンドを 1 つの結果を取得し、次のコマンドを送信することを指示します。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- 指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** )。コマンドが UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell を指示する中かっこ、( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。
    
次のような情報が表示されます。
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

**UsageLocation**プロパティは、ユーザー アカウントに関連付けられている多くのプロパティの 1 つだけです。すべてのユーザー アカウントのプロパティを表示するには、 **Select-object**コマンドレット、ワイルドカード文字 (*) を特定のユーザー アカウントのすべてを表示するのに使用します。例を以下に示します。
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

たとえば、このボックスの一覧から**市区町村**はユーザー アカウントのプロパティの名前です。つまり、ロンドンに住んでいるユーザーのユーザー アカウントのすべてを一覧表示するのには次のコマンドを使用することができます。
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  これらの例に示すように**Where-object**コマンドレットの構文は、 **、オブジェクト {$\_です**。[ユーザー アカウントのプロパティ名][比較演算子][値]**}**. > [比較演算子] が等号の**eq**の等しくないため、 **ne**より大きいは、 **-gt**と他の人の**強い**> [値] は、文字列 (文字、数字、およびその他の文字のシーケンス) では通常、数値、またはの**$Null**を指定しない > 詳細については[、オブジェクト](https://technet.microsoft.com/en-us/library/hh849715.aspx)を参照してください。
  
ブロックされた次のコマンドでユーザー アカウントの状態を確認できます。
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>表示するユーザー アカウントのプロパティを選択する

既定で[Get MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx)コマンドレットでは、ユーザー アカウントの 3 つのプロパティが表示されます。
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
ユーザー アカウントの一覧を指定するのに**Select-object**コマンドレットと組み合わせて**取得 MsolUser**を実行するには部門のユーザーの動作と、ユーザーが Office 365 のサービスを使用する国/地域などの追加のプロパティを作成する必要がある場合プロパティです。例を以下に示します。
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。
    
次のような情報が表示されます。
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

**Select-object**コマンドレットを使用すると、目的のプロパティを表示するコマンドを選択できます。すべてのユーザー アカウントのプロパティを参照してくださいするのにには、特定のユーザー アカウントのすべてを表示するのにはワイルドカード文字 (*) を使用します。例を以下に示します。
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

詳細に表示するにはアカウントの一覧のオプションを選択しても使用できます**Where-object**コマンドレット。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- 指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** ) し、結果の情報を次のコマンドを送信する ( **|** )。かっこの中には、コマンドは UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell ように指示する ( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。
    
- のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。
    
次のような情報が表示されます。
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウントを表示する

Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウントのプロパティを表示するには、 [Get AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0)コマンドレットを使用します。ですが、最初に、サービスに接続する必要があります。この手順では、[Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)を参照してください。
  
### <a name="display-office-365-user-account-information"></a>Office 365 ユーザー アカウント情報を表示する

ユーザー アカウントの完全な一覧を表示するには、Office 365 の PowerShell コマンド プロンプトまたは PowerShell 統合スクリプト環境 (ISE) でこのコマンドを実行します。
  
```
Get-AzureADUser
```

既定で**Get AzureADUser**コマンドレットでは、ユーザー アカウントの 3 つのプロパティが表示されます。
  
- オブジェクト Id
    
- DisplayName
    
- UserPrincipalName
    
詳細表示するにはアカウントの一覧のオプションを選択することができます**Where-object**コマンドレットと組み合わせて使用**Get AzureADUser**コマンドレットです。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、Office 365 の PowerShell コマンドを 1 つの結果を取得し、次のコマンドを送信することを指示します。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- 指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** )。コマンドが UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell を指示する中かっこ、( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。
    
**UsageLocation**プロパティは、ユーザー アカウントに関連付けられている多くのプロパティの 1 つだけです。すべてのユーザー アカウントのプロパティを表示するには、 **Select-object**コマンドレット、ワイルドカード文字 (*) を 1 つのページ (**詳細**) の時に、特定のユーザー アカウントのそれらのすべてを表示するのに使用します。例を以下に示します。
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

などの**都市**は、ユーザー アカウントのプロパティの名前です。つまり、ロンドンに住んでいるユーザーのユーザー アカウントのすべてを一覧表示するのには次のコマンドを使用することができます。
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  これらの例に示すように**Where-object**コマンドレットの構文は、 **、オブジェクト {$\_です**。[ユーザー アカウントのプロパティ名][比較演算子][値]**}**. > [比較演算子] が等号の**eq**の等しくないため、 **ne**より大きいは、 **-gt**と他の人の**強い**> [値] は、文字列 (文字、数字、およびその他の文字のシーケンス) では通常、数値、またはの**$Null**を指定しない > 詳細については[、オブジェクト](https://technet.microsoft.com/en-us/library/hh849715.aspx)を参照してください。
  
### <a name="select-the-user-account-properties-to-display"></a>表示するユーザー アカウントのプロパティを選択する

既定で**Get AzureADUser**コマンドレットでは、ユーザー アカウントのオブジェクト Id、表示名、および UserPrincipalName プロパティを表示します。ユーザーのリストを指定する**Select-object**コマンドレットと組み合わせて**取得 AzureADUser**を実行するには部門のユーザーの動作と、ユーザーが Office 365 のサービスを使用する国/地域などの追加のプロパティを作成する必要がある場合アカウントのプロパティです。例を以下に示します。
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。
    
詳細に表示するにはアカウントの一覧のオプションを選択しても使用できます**Where-object**コマンドレット。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- 指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** ) し、結果の情報を次のコマンドを送信する ( **|** )。かっこの中には、コマンドは UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell ように指示する ( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。
    
- のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。
    
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

||
|:-----|
|![LinkedIn Learning の小さいアイコン](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 を初めて使用する場合は、**         LinkedIn Learning が提供する [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5) のための無料のビデオ コースをご覧ください。 |
   
## <a name="see-also"></a>See also

#### 

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

