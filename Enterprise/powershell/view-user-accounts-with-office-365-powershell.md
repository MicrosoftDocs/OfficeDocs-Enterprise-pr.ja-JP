---
title: Office 365 PowerShell でユーザー アカウントを表示する
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: '概要: 表示、リスト、または Office 365 の PowerShell でのさまざまな方法でユーザー アカウントを表示します。'
ms.openlocfilehash: dc33b64207341576968867fbeea6f211034eeca6
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546528"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell でユーザー アカウントを表示する

**の概要:** Office 365 の PowerShell でのさまざまな方法でユーザー アカウントを表示します。
  
Office 365 の管理センターを使用するには、Office 365 テナントのアカウントを表示するのも Office 365 の PowerShell を使用して Office 365 の管理センターができないことがいくつかの操作を行います。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory の PowerShell を使用して、グラフのモジュールの

最初は[、Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
  
### <a name="view-all-accounts"></a>すべてのアカウントを表示します。

ユーザー アカウントの完全な一覧を表示するには、このコマンドを実行します。
  
```
Get-AzureADUser
```

次のような情報が表示されます。
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>特定のアカウントを表示します。

特定のユーザー アカウントを表示するには、ユーザー アカウントのユーザー プリンシパル名 (UPN) を入力、削除、"<"と">"文字、および次のコマンドを実行します。
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="view-additional-property-values-for-a-specific-account"></a>特定のアカウントの追加のプロパティの値を表示します

既定では、 **Get AzureADUser**コマンドレットには、アカウントのオブジェクト Id、表示名、および UserPrincipalName プロパティのみが表示されます。

詳細に表示するにはプロパティの一覧のオプションを選択できるコマンドレットを使用する**選択オブジェクト** **Get AzureADUser**コマンドレットと組み合わせて。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、1 つのコマンドの結果を取得し、次のコマンドを送信するのにはグラフのアクティブなディレクトリの PowerShell を Azure に伝えます。すべてのユーザー アカウントの表示名、部署、および UsageLocation を表示するコマンドの例を以下に示します。
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。
    
- のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。
  
すべてのユーザー アカウントのプロパティを表示するには、 **Select-object**コマンドレット、ワイルドカード文字 (*) を特定のユーザー アカウントのすべてを表示するのに使用します。例を以下に示します。
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

別の例としては、次のコマンドを使用して特定のユーザー アカウントの有効な状態をチェックできます。
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>一般的なプロパティに基づいていくつかのアカウントを表示します。

詳細表示するにはアカウントの一覧のオプションを選択することができます**Where-object**コマンドレットと組み合わせて使用**Get AzureADUser**コマンドレットです。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、1 つのコマンドの結果を取得し、次のコマンドを送信するのにはグラフのアクティブなディレクトリの PowerShell を Azure に伝えます。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

このコマンドは、グラフのアクティブなディレクトリの PowerShell を Azure を指示します。
  
- ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。
    
- 指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** )。コマンドが UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell を指示する中かっこ、( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。
    
**UsageLocation**プロパティは、ユーザー アカウントに関連付けられている多くのプロパティの 1 つだけです。すべてのユーザー アカウントのプロパティを表示するには、 **Select-object**コマンドレット、ワイルドカード文字 (*) を特定のユーザー アカウントのすべてを表示するのに使用します。例を以下に示します。
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

たとえば、この一覧で、**City** がユーザー アカウント プロパティの名前であるとします。つまり、以下のコマンドを使用すると、ロンドン在住のユーザーのユーザー アカウントすべての一覧を表示できます。
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  これらの例に示すように**Where-object**コマンドレットの構文は、 **、オブジェクト {$\_です**。[ユーザー アカウントのプロパティ名][比較演算子][値]**}**. > [比較演算子] が等号の**eq**の等しくないため、 **ne**より大きいは、 **-gt**と他の人の**強い**。 [値] は、通常の文字列 (文字、数字、およびその他の文字のシーケンス)、数値、または **$Null**未指定の > 詳細については[、オブジェクト](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1)を参照してください。
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>モジュールを使用して、Microsoft Azure Active Directory Windows PowerShell の

最初は[、Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。

### <a name="view-all-accounts"></a>すべてのアカウントを表示します。

ユーザー アカウントの完全な一覧を表示するには、このコマンドを実行します。
  
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

表示をフィルター処理する追加のパラメーターの詳細について表示するには、ユーザー アカウントの設定では、 [Get MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))を参照してください。
  

### <a name="view-a-specific-account"></a>特定のアカウントを表示します。

特定のユーザー アカウントを表示するには、ユーザー アカウントのユーザー プリンシパル名 (UPN) を入力、削除、"<"と">"文字、および次のコマンドを実行します。
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>一般的なプロパティに基づいていくつかのアカウントを表示します。

詳細表示するにはアカウントの一覧のオプションを選択することができます**Where-object**コマンドレットと組み合わせて使用**Get MsolUser**コマンドレットです。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、Office 365 の PowerShell コマンドを 1 つの結果を取得し、次のコマンドを送信することを指示します。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
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

たとえば、この一覧で、**City** がユーザー アカウント プロパティの名前であるとします。つまり、以下のコマンドを使用すると、ロンドン在住のユーザーのユーザー アカウントすべての一覧を表示できます。
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  これらの例に示すように**Where-object**コマンドレットの構文は、 **、オブジェクト {$\_です**。[ユーザー アカウントのプロパティ名][比較演算子][値]**}**. [比較演算子] は、equals の**eq**が、等しくないため、 **ne**より大きいは、 **-gt**と他の人の**強い**です。 [値] は、通常 (文字、数字、およびその他の文字のシーケンス)、文字列、数値、または **$Null**指定されていないのです。詳細については[、オブジェクト](https://technet.microsoft.com/en-us/library/hh849715.aspx)を参照してください。
  
ブロックされた次のコマンドでユーザー アカウントの状態を確認できます。
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>アカウントの追加のプロパティの値を表示します

既定で**Get MsolUser**コマンドレットでは、ユーザー アカウントの 3 つのプロパティが表示されます。
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
ユーザー アカウントの一覧を指定するのに**Select-object**コマンドレットと組み合わせて**取得 MsolUser**を実行するには部門のユーザーの動作と、ユーザーが Office 365 のサービスを使用する国/地域などの追加のプロパティを作成する必要がある場合プロパティです。例を以下に示します。
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
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
Scott Wallace           Operations
```

**Select-object**コマンドレットでは、目的のプロパティを表示するコマンドを選択することができます。すべてのユーザー アカウントのプロパティを参照してくださいするのにには、特定のユーザー アカウントのすべてを表示するのにはワイルドカード文字 (*) を使用します。例を以下に示します。
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

アカウントの一覧をより選択的に表示する場合には、**Where-object** コマンドレットも使用できます。次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- 指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** ) し、結果の情報を次のコマンドを送信する ( **|** )。かっこの中には、コマンドは UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell ように指示する ( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。
    
- のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。
    
次のような情報が表示されます。
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

作成し、Office 365 のユーザーを管理するにディレクトリ同期を使用する場合、Office 365 ユーザーがから投影されたローカル アカウントを表示します。次は、ObjectGUID の既定のソース アンカーを使用するのには、Azure AD 接続が構成されていると仮定しています (ソース アンカーの設定に関する詳細を参照してください[Azure AD 接続: 概念のデザイン](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) powershell の Active Directory のモジュールを持っているを前提としていますされてインストールされている (を参照してください[RSAT ツール](https://www.microsoft.com/en-gb/download/details.aspx?id=45520))。

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

