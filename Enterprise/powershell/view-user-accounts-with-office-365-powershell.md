---
title: Office 365 PowerShell でユーザー アカウントを表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
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
description: '概要: Office 365 PowerShell を使用して、さまざまな方法でユーザーアカウントを表示、一覧表示、または表示できます。'
ms.openlocfilehash: 2858efef6220beed76894414ea99ed922353afc3
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037921"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell でユーザー アカウントを表示する

**概要:** Office 365 PowerShell を使用して、さまざまな方法でユーザーアカウントを表示します。
  
office 365 管理センターを使用して office 365 テナントのアカウントを表示することはできますが、office 365 PowerShell を使用して、office 365 管理センターでは実行できないいくつかの操作を実行することもできます。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph モジュールの Azure Active Directory PowerShell を使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
  
### <a name="view-all-accounts"></a>すべてのアカウントを表示する

ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。
  
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

### <a name="view-a-specific-account"></a>特定のアカウントを表示する

特定のユーザーアカウントを表示するには、ユーザーアカウントのサインインアカウント名 (UPN) を入力し、"<" および ">" 文字を削除して、次のコマンドを実行します。
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

次に例を示します。
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>特定のアカウントの追加のプロパティ値を表示する

既定では、 **set-azureaduser**コマンドレットでは、アカウントの ObjectID、DisplayName、および UserPrincipalName のプロパティのみが表示されます。

表示するプロパティの一覧についてより詳細な情報を得るには、 **set-azureaduser**コマンドレットと組み合わせて、**オブジェクト**のコマンドレットを使用できます。 2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。 次に、すべてのユーザーアカウントの DisplayName、Department、および使用場所を表示するコマンドの例を示します。
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。
    
- ユーザーアカウント名、部署、使用場所のみを表示する (**選択-オブジェクト DisplayName、部署、使用場所**)。
  
ユーザーアカウントのすべてのプロパティを表示するには、**オブジェクトの選択**コマンドレットとワイルドカード文字 (*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。 次に例を示します。
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

別の例として、次のコマンドを使用して、特定のユーザーアカウントの有効な状態を確認できます。
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>共通プロパティに基づいて一部のアカウントを表示する

表示するアカウントのリストをより詳細に選択できるようにするには、 **set-azureaduser**コマンドレットと組み合わせて、**オブジェクト**のコマンドレットを使用します。 2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。 次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

次のコマンドは、Azure Active Directory PowerShell を Graph に対して次のように指示します。
  
- ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。
    
- 使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます\_(Where オブジェクト {$.の場合は、-eq $Null}** ) を指定します。 中かっこの内側では、コマンドは、Office 365 PowerShell に対して、"アクセス先" ユーザーアカウントプロパティ ( ** $ \_) のアカウントセットのみを検索するように指示します。** は、無効な場所) を指定しません ( **-eq $Null** )。
    
使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。 ユーザーアカウントのすべてのプロパティを表示するには、**オブジェクトの選択**コマンドレットとワイルドカード文字 (*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。 次に例を示します。
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。 これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  これらの例に**** 示されている where-object コマンドレットの構文は、 **where オブジェクト {\_$ にあります。** [ユーザーアカウントのプロパティ名][比較演算子]金額****> [comparison operator] は **-eq** (等しい)、 **-ne** for not equals、 **-lt** (より小さい、- **gT** (より大きい)、または他の場合) です。  [value] は通常、unspecified> の文字列 (一連の文字、数字、およびその他の文字)、数値、または **$Null**を示します。詳細については、「 [Where オブジェクト](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1)」を参照してください。
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

### <a name="view-all-accounts"></a>すべてのアカウントを表示する

ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。
  
```
Get-MsolUser
```

次のような情報が表示されます。
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-MsolUser** コマンドレットには、表示するユーザー アカウントのセットをフィルターにかけるための一連のパラメーターもあります。 たとえば、ライセンスのないユーザー (Office 365 に追加されていても、まだライセンスを持っていないユーザー) の一覧については、次のコマンドを実行します。
  
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

表示されるユーザーアカウントのセットをフィルター処理するための追加パラメーターの詳細については、「 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))」を参照してください。
  

### <a name="view-a-specific-account"></a>特定のアカウントを表示する

特定のユーザーアカウントを表示するには、ユーザーアカウントのユーザーアカウントのサインイン名 (UPN) を記入し、"<" および ">" 文字を削除して、次のコマンドを実行します。
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>共通プロパティに基づいて一部のアカウントを表示する

表示するアカウントのリストをより詳細に選択できるようにするには、 **get-msoluser**コマンドレットと組み合わせて、**オブジェクト**のコマンドレットを使用します。 2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Office 365 PowerShell に対して1つのコマンドの結果を取得し、次のコマンドに送信するように指示します。 次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- 使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます\_(Where オブジェクト {$.の場合は、-eq $Null}** ) を指定します。 中かっこの内側では、コマンドは、Office 365 PowerShell に対して、"アクセス先" ユーザーアカウントプロパティ ( ** $ \_) のアカウントセットのみを検索するように指示します。** は、無効な場所) を指定しません ( **-eq $Null** )。
    
次のような情報が表示されます。
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。 ユーザーアカウントのすべてのプロパティを表示するには、**オブジェクトの選択**コマンドレットとワイルドカード文字 (*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。 次に例を示します。
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。 これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  これらの例に**** 示されている where-object コマンドレットの構文は、 **where オブジェクト {\_$ にあります。** [ユーザーアカウントのプロパティ名][比較演算子]金額 **}**.  [comparison operator] は **-eq** (等しい)、 **-ne** for not equals、 **-lt** (より小さい)、- **gt** (より大きい)、または他のものです。  [value] は通常、文字列 (一連の文字、数字、その他の文字)、数値、または **$Null**指定なしの場合に使用します。 詳細については[、「Where オブジェクト](https://technet.microsoft.com/en-us/library/hh849715.aspx)」を参照してください。
  
ユーザーアカウントのブロックされた状態を確認するには、次のコマンドを使用します。
  
```
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>アカウントの追加のプロパティ値を表示する

**get-msoluser**コマンドレットでは、既定でユーザーアカウントの3つのプロパティを表示します。
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
ユーザーが作業する部署や、ユーザーが Office 365 サービスを使用する国/地域など、追加のプロパティが必要な場合は、get-msoluser コマンドレットと組み合わせて**** を**** 実行して、ユーザーアカウントの一覧を指定することができます。プロパティ. 次に例を示します。
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- ユーザーアカウント名、部署、使用場所のみを表示する (**選択-オブジェクト DisplayName、部署、使用場所**)。
    
次のような情報が表示されます。
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

**オブジェクトの選択**コマンドレットを使用すると、コマンドに表示するプロパティを選択して選択できます。 ユーザーアカウントのすべてのプロパティを表示するには、ワイルドカード文字 (*) を使用して、特定のユーザーアカウントに対してすべてのプロパティを表示します。 次に例を示します。
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

表示するアカウントのリストをより詳細に選択できるようにするには、 **** where-object コマンドレットを使用することもできます。 次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- 使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます\_(Where オブジェクト {$.[実行場所-eq $Null}** )] を指定して、結果の情報**|** を次のコマンドに送信します ()。 中かっこ内では、コマンドは、Office 365 PowerShell に対して、"アクセス先" ユーザーアカウントプロパティ ( ** $ \_) のアカウントセットのみを検索するように指示します。** は、無効な場所) を指定しません ( **-eq $Null** )。
    
- ユーザーアカウント名、部署、使用場所のみを表示する (**選択-オブジェクト DisplayName、部署、使用場所**)。
    
次のような情報が表示されます。
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

ディレクトリ同期を使用して office 365 ユーザーを作成および管理している場合は、office 365 ユーザーがどのローカルアカウントから射影されているかを表示できます。 次の例では、azure ad connect が ObjectGUID の既定のソースアンカーを使用するように構成されていると仮定しています (ソースアンカーの構成の詳細については、「 [azure ad connect: デザインの概念](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)」を参照してください)。また、powershell の Active Directory モジュールがインストールされている場合 (「 [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)」を参照):

```
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

