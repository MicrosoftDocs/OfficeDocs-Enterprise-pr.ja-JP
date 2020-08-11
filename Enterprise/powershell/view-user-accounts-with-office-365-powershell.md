---
title: PowerShell を使用して Microsoft 365 ユーザーアカウントを表示する
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: PowerShell を使用して、Microsoft 365 ユーザーアカウントをさまざまな方法で表示、一覧表示、または表示する方法について説明します。
ms.openlocfilehash: 56da6bfc7b467b6a85a4bd8c84abd4c2ae05913f
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605298"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>PowerShell を使用して Microsoft 365 ユーザーアカウントを表示する

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

Microsoft 365 管理センターを使用して Microsoft 365 テナントのアカウントを表示することはできますが、microsoft 365 の PowerShell を使用して、管理センターではできないことを実行することもできます。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 用 Azure Active Directory PowerShell モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。
  
### <a name="view-all-accounts"></a>すべてのアカウントを表示する

ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。
  
```powershell
Get-AzureADUser
```

次のような情報が表示されます。
  
```powershell
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

特定のユーザーアカウントを表示するには、ユーザーアカウントのサインインアカウント名 (UPN) を入力し、"<" と ">" 文字を削除して、次のコマンドを実行します。
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

次に例を示します：
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>特定のアカウントの追加のプロパティ値を表示する

既定では、 **set-azureaduser**コマンドレットでは、アカウントの ObjectID、DisplayName、および UserPrincipalName のプロパティのみが表示されます。

表示するプロパティの一覧についてより選択的に選択するには、 **Select**コマンドレットと**set-azureaduser**コマンドレットを組み合わせて使用します。 2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。 次に、すべてのユーザーアカウントの DisplayName、Department、および使用場所を表示するコマンドの例を示します。
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

次のコマンドは、PowerShell に次のように指示します。
  
- ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。
    
- ユーザーアカウント名、部署、および使用場所のみを表示します ( **DisplayName、department、および使用場所を選択し**ます)。
  
ユーザーアカウントのすべてのプロパティを表示するには、 **Select**コマンドレットとワイルドカード文字 (*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。 次に例を示します：
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

別の例として、次のコマンドを使用して、特定のユーザーアカウントの有効な状態を確認できます。
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>共通プロパティに基づいて一部のアカウントを表示する

表示するアカウントの一覧をより詳細に選択できるようにするには、 **set-azureaduser**コマンドレットと組み合わせて**Where**コマンドレットを使用します。 2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。 次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

次のコマンドは、Azure Active Directory PowerShell を Graph に対して次のように指示します。
  
- ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。
    
- 使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます (Where {$ \_ .の場合は、-eq $Null}** ) を指定します。 中かっこ内では、コマンドによって、アクセス先ユーザーアカウントプロパティ (という) のアカウントセットのみが検索され** $ \_ ます。** は、無効な場所) を指定しません ( **-eq $Null** )。
    
使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。 ユーザーアカウントのすべてのプロパティを表示するには、 **Select**コマンドレットとワイルドカード文字 (*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。 次に例を示します：
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。 これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  これらの例に示されて**いる where**コマンドレットの構文は、 **{$ \_ .** [ユーザーアカウントのプロパティ名][比較演算子]金額 **}**. > [比較演算子] は、equals、 **-ne** for not equals、 **-lt** (より小さい、-gt (より大きい)、- **gt** (より大きい)、およびその他の場合に- **eq**を指定します。  [value] は、通常、文字列 (一連の文字、数字、およびその他の文字)、数値、または **$Null**指定されていない> の場合は、「詳細情報」を[参照して](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1)ください。
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。

### <a name="view-all-accounts"></a>すべてのアカウントを表示する

ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。
  
```powershell
Get-MsolUser
```

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

次のような情報が表示されます。
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

**Get-MsolUser** コマンドレットには、表示するユーザー アカウントのセットをフィルターにかけるための一連のパラメーターもあります。 たとえば、ライセンスのないユーザー (Microsoft 365 に追加されていても、サービスのいずれかを使用するライセンスを持っていないユーザー) の一覧については、次のコマンドを実行します。
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

次のような情報が表示されます。
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

表示されるユーザーアカウントのセットをフィルター処理するための追加パラメーターの詳細については、「 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))」を参照してください。
  
### <a name="view-a-specific-account"></a>特定のアカウントを表示する

特定のユーザーアカウントを表示するには、ユーザーアカウントのユーザーアカウントのサインイン名 (UPN) を記入し、"<" と ">" 文字を削除して、次のコマンドを実行します。
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>共通プロパティに基づいて一部のアカウントを表示する

表示するアカウントの一覧をより詳細に選択できるようにするには、 **get-msoluser**コマンドレットと組み合わせて**Where**コマンドレットを使用します。 2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、1つのコマンドの結果を受け取って次のコマンドに送信するように PowerShell に指示します。 次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

次のコマンドは、PowerShell に次のように指示します。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- 使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます (Where {$ \_ .の場合は、-eq $Null}** ) を指定します。 中かっこ内では、コマンドによって、アクセス先ユーザーアカウントプロパティ (という) のアカウントセットのみが検索され** $ \_ ます。** は、無効な場所) を指定しません ( **-eq $Null** )。
    
次のような情報が表示されます。
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。 ユーザーアカウントのすべてのプロパティを表示するには、 **Select**コマンドレットとワイルドカード文字 (*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。 次に例を示します：
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。 これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  これらの例に示されて**いる where**コマンドレットの構文は、 **{$ \_ .** [ユーザーアカウントのプロパティ名][比較演算子]金額 **}**.  [comparison operator] は **-eq** (等しい)、 **-ne** for not equals、 **-lt** (より小さい)、- **gt** (より大きい)、または他のものです。  [value] は通常、文字列 (一連の文字、数字、その他の文字)、数値、または **$Null**指定なしの場合に使用します。 詳細[につい](https://technet.microsoft.com/library/hh849715.aspx)ては、「」を参照してください。
  
ユーザーアカウントのブロックされた状態を確認するには、次のコマンドを使用します。
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>アカウントの追加のプロパティ値を表示する

**Get-msoluser**コマンドレットでは、既定でユーザーアカウントの3つのプロパティを表示します。
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
ユーザーが作業する部署や、ユーザーが Microsoft 365 サービスを使用する国/地域など、追加のプロパティが必要な場合は、 **Select**コマンドレットと組み合わせて**get-msoluser**を実行して、ユーザーアカウントのプロパティの一覧を指定できます。 次に例を示します：
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

次のコマンドは、PowerShell に次のように指示します。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- ユーザーアカウント名、部署、および使用場所のみを表示します ( **DisplayName、department、および使用場所を選択し**ます)。
    
次のような情報が表示されます。
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

**Select**コマンドレットを使用すると、コマンドに表示するプロパティを選択して選択できます。 ユーザーアカウントのすべてのプロパティを表示するには、ワイルドカード文字 (*) を使用して、特定のユーザーアカウントに対してすべてのプロパティを表示します。 次に例を示します：
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

表示するアカウントのリストをより詳細に選択できるようにするには、 **Where**コマンドレットを使用することもできます。 次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

次のコマンドは、PowerShell に次のように指示します。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- 使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます (Where {$ \_ .[実行場所-eq $Null}** )] を指定して、結果の情報を次のコマンドに送信し **|** ます ()。 中かっこで囲まれている場合、コマンドは、ユーザーアカウントプロパティ (という) があるアカウントのセットのみを検索するように PowerShell に指示し** $ \_ ます。** は、無効な場所) を指定しません ( **-eq $Null** )。
    
- ユーザーアカウント名、部署、および使用場所のみを表示します ( **DisplayName、department、および使用場所を選択し**ます)。
    
次のような情報が表示されます。
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

ディレクトリ同期を使用して Microsoft 365 ユーザーを作成および管理している場合は、Microsoft 365 ユーザーが射影したローカルアカウントを表示できます。 次の例では、Azure AD Connect が ObjectGUID の既定のソースアンカーを使用するように構成されていると仮定しています (ソースアンカーの構成の詳細については、「 [AZURE Ad connect: デザインの概念](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)」を参照して[ください)。](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)また、PowerShell の Active Directory ドメインサービスモジュールがインストールされていると仮定します

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>関連項目

[Microsoft 365 ユーザー アカウント、ライセンス、PowerShell を使用したグループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell で Microsoft 365を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 用 PowerShell の使用を開始する](getting-started-with-office-365-powershell.md)

