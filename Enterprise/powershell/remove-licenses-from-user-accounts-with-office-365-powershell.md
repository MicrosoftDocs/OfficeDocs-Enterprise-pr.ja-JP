---
title: "Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する"
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
- DecEntMigration
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: "ユーザーに以前割り当てられた Office 365 のライセンスを削除するのには Office 365 の PowerShell を使用する方法について説明します。"
ms.openlocfilehash: 90cae603a7a7cda0b7318571d3eb045f750fd58d
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する

**の概要:**ユーザーに以前割り当てられた Office 365 のライセンスを削除するのには Office 365 の PowerShell を使用する方法について説明します。
  
## <a name="before-you-begin"></a>開始する前に

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- 組織のライセンス プラン ( **AccountSkuID** ) 情報を表示する方法については、以下のトピックをご覧ください。
    
  - [Office 365 PowerShell でライセンスとサービスを確認する](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する](view-account-license-and-service-details-with-office-365-powershell.md)
    
- 使用せず、 **Get MsolUser**コマンドレットを使用するかどうかは、_のすべて_パラメーターでは、最初の 500 個のアカウントのみが返されます。
    
## <a name="the-short-version-instructions-without-explanations"></a>簡略版 (説明なしの手順)
<a name="ShortVersion"> </a>

このセクションでは、余分な説明を省いて簡潔に手順を示します。ご質問がある場合、または詳細情報が必要な場合には、このトピックの残りの部分をご覧ください。
  
既存のユーザー アカウントからライセンスを削除するには、次の構文を使用します:
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

次の例では、ユーザー アカウント BelindaN@litwareinc.com から  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

ライセンス付与済みの既存のユーザーのグループからライセンスを削除するには、次のいずれかの方法を使用します。
  
- **既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

この例では、米国内の販売部門のユーザーのすべてのアカウントから  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- **特定のアカウントの一覧を使用する** これを行うには、次の手順を実行します。
    
1. 次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成し、保存します。
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. 次の構文を使用してください。
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

この例で削除、 `litwareinc:ENTERPRISEPACK` C:\My Documents\Accounts.txt のテキスト ファイルで定義されているユーザー アカウントからの (Office 365 エンタープライズ E3) のライセンスです。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

既存のすべてのユーザー アカウントからライセンスを削除するには、次の構文を使用します。
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

次の例では、ライセンスを付与された既存の全ユーザー アカウントから  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>詳細版 (詳細な説明付きの手順)
<a name="LongVersion"> </a>

永遠に続くものなどありません。これは Office 365 のライセンスにも該当します。遅かれ早かれユーザー アカウントからライセンスを削除しなければならないときがきます。休暇をとる、ライセンスが必要でなくなるなど、ユーザー ライセンスを削除する理由は無数にあります。
  
詳しい説明に入る前に、気を付けなければならない重要なポイントは、ライセンスを削除するには、やはりライセンスを削除しなければならないという点です。つまり、ライセンスのすべてのサービスを無効にしても、それはライセンスの削除とはなりません。たとえば、Office 365 のライセンスをすべて使用してしまい、利用できるライセンスが 1 つもないとします。「[Office 365 PowerShell を使ったサービスへのアクセスを無効にする](disable-access-to-services-with-office-365-powershell.md)」の手順に従って、たとえば Belinda Newman のアカウントのすべてのサービスを無効にすることにします。このコマンドを実行した後、利用できるライセンスの数はいくつになりますか?そうです。ゼロです。このトピックの手順では、Belinda のライセンスのすべてのサービスを *無効*  にしますが、ライセンス自体を無効にする (つまり、削除する) わけではありません。ライセンスは有効のままで、Belinda Newman に割り当てられたままです。Belinda は、このライセンスを使用して Office 365 のサービスにアクセスできなくなるにすぎません。
  
これは重要なポイントです。ユーザーからライセンスを削除する場合は、実際にライセンスを *削除*  する必要があります。サービスをすべて無効にすると、ユーザーは Office 365 にログオンできなくなりますが、ライセンスが解放されるわけではありません。ユーザーに現在割り当てられているライセンスを削除する場合は、次のようなコマンドを実行する必要があります。このコマンドでは、 _RemoveLicenses_ パラメーターを使用して、以前に Belinda に割り当てたライセンスを実際に削除します。
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

このコマンドを実行すると、Belinda Newman に Office 365 を使用するライセンスが付与された状態ではなくなります。
  
> [!NOTE]
> わかるように、削除するライセンスの名前を指定する必要があります_RemoveLicenses_パラメーターを使用するとします。よいかわからない場合、次のようにコマンドを実行するだけのユーザーにライセンスを割り当てるにはどのライセンス プランが使用されていました。`Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Format-List DisplayName,Licenses`
  
ライセンスが本当に削除されていることを確認するには、Get-MsolUser を使用して対象のユーザー アカウントを確認します。
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

Belinda の**isLicensed**プロパティ設定するプランではすべての場合、 `False`。
  
```
UserPrincipalName            DisplayName         isLicensed
-----------------            -----------         ----------
BelindaN@litwareinc.com      Newman, Belinda     False
```

別の方法として、ユーザー アカウントを削除してライセンスを解放することもできます。詳細については、「[Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)」を参照してください。
  
## <a name="see-also"></a>関連項目

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [Office 365 PowerShell を使用してユーザー アカウントを作成する](create-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell でユーザー アカウントをブロックする](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

||
|:-----|
|![LinkedIn Learning の小さいアイコン](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 を初めて使用する場合は、**         LinkedIn Learning が提供する [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5) のための無料のビデオ コースをご覧ください。 |
   

