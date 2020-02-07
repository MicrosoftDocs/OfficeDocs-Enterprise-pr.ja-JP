---
title: Office 365 PowerShell でユーザー アカウント プロパティを構成する
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 概要:Office 365 PowerShell を使用して、Office 365 テナント内の個別のまたは複数のユーザー アカウントのプロパティを構成します。
ms.openlocfilehash: 211210dad54cb0af772af7dc611bc2c0fdf6035a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841604"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Office 365 PowerShell でユーザー アカウント プロパティを構成する

Microsoft 365 管理センターを使用して Office 365 テナントのユーザーアカウントのプロパティを構成することもできますが、Office 365 PowerShell を使用して、管理センターではできないいくつかの操作を実行することもできます。
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph 用 Azure Active Directory PowerShell モジュールを使用する

Graph モジュールの Azure Active Directory PowerShell を使用してユーザーアカウントのプロパティを構成するには、 [set-azureaduser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)コマンドレットを使用して、設定または変更するプロパティを指定します。 

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。
   
### <a name="change-properties-for-a-specific-user-account"></a>特定のユーザー アカウントのプロパティを変更する

**-ObjectID** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。 最も一般的なパラメーターの一覧を次に示します。
  
- -Department "\<部署名>"
    
- -DisplayName "\<完全なユーザー名>"
    
- -FacsimilieTelephoneNumber "\<fax 番号>"
    
- -GivenName "\<ユーザーの名>"
    
- -Surname "\<ユーザーの姓>"
    
- -Mobile "\<携帯電話番号>"
    
- -JobTitle "\<役職>"
    
- -PreferredLanguage "\<言語>"
    
- -StreetAddress "\<番地>"
    
- -City "\<市区町村名>"
    
- -State "\<都道府県名>"
    
- -PostalCode "\<郵便番号>"
    
- -Country "\<国名>"
    
- -TelephoneNumber "\<勤務先電話番号>"
    
- -UsageLocation "\<2 文字の国/地域コード>"
    
    これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。
    
その他のパラメーターについては、[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) を参照してください。


ユーザー アカウントのユーザー プリンシパル名を表示するには、次のコマンドを実行します。
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。
    
- ユーザープリンシパル名のリストをアルファベット順に並べ替え ( **UserPrincipalName を並べ替え**)、次のコマンドに**|** 送信します ()。
    
- 各アカウントのユーザープリンシパル名プロパティのみを表示します ( **UserPrincipalName を選択**します)。

- 一度に 1 画面ずつ表示する ( **More** )。
    
このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

この例では、Caleb が Ls の表示名を持つユーザーアカウントのユーザープリンシパル名を表示します。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>すべてのユーザー アカウントのプロパティを変更する

すべてのユーザーのプロパティを変更する場合には、 **Get-AzureADUser** と **Set-AzureADUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。
    
- ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>特定のユーザー アカウント セットのプロパティを変更する

特定のユーザー アカウント セットのプロパティを変更する場合には、**Get-AzureADUser**、**Where**、**Set-AzureADUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。
    
- Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。
    
- ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する

Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用して、ユーザーアカウントのプロパティを構成するには、 **get-msoluser**コマンドレットを使用して、設定または変更するプロパティを指定します。 

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。
  
>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

### <a name="change-properties-for-a-specific-user-account"></a>特定のユーザー アカウントのプロパティを変更する

特定のユーザー アカウントのプロパティを構成する場合、[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) コマンドレットを使用して、設定または変更するプロパティを指定します。 

**-UserPrincipalName** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。
  
- -City "\<市区町村名>"
    
- -Country "\<国名>"
    
- -Department "\<部署名>"
    
- -DisplayName "\<完全なユーザー名>"
    
- -Fax "\<fax 番号>"
    
- -FirstName "\<ユーザーの名>"
    
- -LastName "\<ユーザーの姓>"
    
- -MobilePhone "\<携帯電話番号>"
    
- -Office "\<事業所の場所>"
    
- -PhoneNumber "\<勤務先電話番号>"
    
- -PostalCode "\<郵便番号>"
    
- -PreferredLanguage "\<言語>"
    
- -State "\<都道府県名>"
    
- -StreetAddress "\<番地>"
    
- -Title "\<役職名>"
    
- -UsageLocation "\<2 文字の国/地域コード>"
    
    これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。
    
その他のパラメーターについては、[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) をご覧ください。

すべてのユーザーのユーザー プリンシパル名を表示するには、次のコマンドを実行します。
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- ユーザープリンシパル名のリストをアルファベット順に並べ替え ( **UserPrincipalName を並べ替え**)、次のコマンドに**|** 送信します ()。
    
- 各アカウントのユーザープリンシパル名プロパティのみを表示します ( **UserPrincipalName を選択**します)。
    
- 一度に 1 画面ずつ表示する ( **More** )。
    
このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>すべてのユーザー アカウントのプロパティを変更する

すべてのユーザーのプロパティを変更する場合には、 **Get-MsolUser** と **Set-MsolUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>特定のユーザー アカウント セットのプロパティを変更する

特定のユーザーアカウントセットのプロパティを変更するには、 **get-msoluser**、 **Where**、および**get-msoluser**コマンドレットの組み合わせを使用できます。 次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。
  
- ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。
    
- Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。
    
- ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。
    

## <a name="see-also"></a>関連項目

[Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)
