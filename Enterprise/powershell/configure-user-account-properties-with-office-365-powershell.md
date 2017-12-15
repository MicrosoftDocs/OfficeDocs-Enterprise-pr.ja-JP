---
title: "Office 365 PowerShell でユーザー アカウント プロパティを構成する"
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
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "概要:Office 365 PowerShell を使用して、Office 365 テナント内の個別のまたは複数のユーザー アカウントのプロパティを構成します。"
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Office 365 PowerShell でユーザー アカウント プロパティを構成する

 **の概要:**Office 365 の PowerShell を使用するには、Office 365 テナントに個人または複数のユーザー アカウントのプロパティを構成します。
  
Office 365 管理センターを使用して Office 365 テナントのユーザー アカウントのプロパティを構成することもできますが、Office 365 PowerShell を使用すると、Office 365 管理センターでは行えない操作も実行できます。
  
## <a name="before-you-begin"></a>開始する前に

このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
  
## <a name="change-properties-for-a-specific-user-account"></a>特定のユーザー アカウントのプロパティを変更する

特定のユーザー アカウントのプロパティを構成する場合、[Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) コマンドレットを使用して、設定または変更するプロパティを指定します。次の例のコマンドは、Belinda Newman の使用場所をフランスに変更します。
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

**-UserPrincipalName** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。
  
- -都市"\<市区町村名 >"
    
- -国"\<国の名前 >"
    
- -部門「\<部門名 >"
    
- -表示名"\<完全なユーザー名 >"
    
- -[Fax]\<fax 番号 >"
    
- 姓が"\<ユーザー名 >"
    
- [氏名] の"\<ユーザー名 >"
    
- MobilePhone-「\<携帯電話番号 >"
    
- の Office"\<オフィスの所在地 >"
    
- -電話番号"\<オフィスの電話番号 >"
    
- -郵便番号"\<郵便番号 >"
    
- -PreferredLanguage"\<言語 >"
    
- -状態"\<状態の名前 >"
    
- -番地"\<番地 >"
    
- -タイトル"\<タイトル名 >"
    
- -UsageLocation"\<2 文字の国または地域番号 >"
    
    これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。
    
その他のパラメーターについては、[Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) をご覧ください。
  
すべてのユーザーのユーザー プリンシパル名を表示するには、次のコマンドを実行します。
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- ユーザー プリンシパル名の一覧をアルファベット順に並べ替え ( **Sort オブジェクトの UserPrincipalName** ) し、次のコマンドを送信 ( **|** )。
    
- 各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。
    
- 一度に 1 画面ずつ表示する ( **More** )。
    
このコマンドは、すべてのアカウントが表示されます。表示に基づいて、アカウントのユーザー プリンシパル名を表示する場合は、名前 (姓と名)、 **$username$**変数を以下に入力 (削除、\<と > 文字)、し、次のコマンドを実行します。
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>すべてのユーザー アカウントのプロパティを変更する

すべてのユーザーのプロパティを変更する場合には、 **Get-MsolUser** と **Set-MsolUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>特定のユーザー アカウント セットのプロパティを変更する

特定のユーザー アカウント セットのプロパティを変更する場合には、 **Get-MsolUser** 、 **Where-Object** 、 **Set-MsolUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- 検索のすべてのユーザー アカウント プロパティを持つその部門「会計」に設定する ( **Where-object {$_ です。部門 eq「経理」}** ) し、結果の情報を次のコマンドを送信する ( **|** )。
    
- ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。
    
- 一度に 1 画面ずつ表示する ( **More** )。
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウント プロパティを構成する

Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウントのプロパティを構成するには、[セット AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)コマンドレットを使用しを設定または変更するにはプロパティを指定します。ですが、最初に、サービスに接続する必要があります。この手順では、 [Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)を参照してください。
  
### <a name="change-properties-for-a-specific-user-account"></a>特定のユーザー アカウントのプロパティを変更する

次のコマンドの例では、Belinda Newman の使用場所をフランスに変更します。
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

**-ObjectID** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。
  
- -部門「\<部門名 >"
    
- -表示名"\<完全なユーザー名 >"
    
- -FacsimilieTelephoneNumber"\<fax 番号 >"
    
- GivenName の「\<ユーザー名 >"
    
- -姓の"\<ユーザー名 >"
    
- -モバイル"\<携帯電話番号 >"
    
- -役職」\<ジョブのタイトル >]
    
- -PreferredLanguage"\<言語 >"
    
- -番地"\<番地 >"
    
- -都市"\<市区町村名 >"
    
- -状態"\<状態の名前 >"
    
- -郵便番号"\<郵便番号 >"
    
- -国"\<国の名前 >"
    
- 勤務先の"\<オフィスの電話番号 >"
    
- -UsageLocation"\<2 文字の国または地域番号 >"
    
    これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。
    
その他のパラメーターについては、[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) を参照してください。
  
ユーザー アカウントのユーザー プリンシパル名を表示するには、次のコマンドを実行します。
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- ユーザー プリンシパル名の一覧をアルファベット順に並べ替え ( **Sort オブジェクトの UserPrincipalName** ) し、次のコマンドを送信 ( **|** )。
    
- 各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。
- 一度に 1 画面ずつ表示する ( **More** )。
    
このコマンドは、すべてのアカウントが表示されます。表示に基づいて、アカウントのユーザー プリンシパル名を表示する場合は、名前 (姓と名)、 **$username$**変数を以下に入力 (削除、\<と > 文字)、し、次のコマンドを実行します。
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>すべてのユーザー アカウントのプロパティを変更する

すべてのユーザーのプロパティを変更する場合には、 **Get-AzureADUser** と **Set-AzureADUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- ユーザーの所在地をフランスに設定します ( **Set-AzureADUser -UsageLocation "FR"** )。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>特定のユーザー アカウント セットのプロパティを変更する

ユーザー アカウントの特定のセットのプロパティを変更するには、 **Get AzureADUser**、**場所**、および**セット AzureADUser**コマンドレットの組み合わせを使用できます。次の例では、フランスに会計部署のすべてのユーザーの利用状況の場所を変更します。
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。
    
- すべての部門のプロパティ「会計」に設定されているユーザー アカウントの検索 ( **、{$_ です。部門 eq「経理」}** ) し、結果の情報を次のコマンドを送信する ( **|** )。
    
- ユーザーの所在地をフランスに設定します ( **Set-AzureADUser -UsageLocation "FR"** )。
    
## <a name="see-also"></a>See also

#### 

[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

