---
title: Office 365 PowerShell を使用してユーザー アカウントを作成する
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
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Office 365 PowerShell を使用して Office 365 でユーザー アカウントを作成する方法について学習します。
ms.openlocfilehash: e5fed572d0b835a42071e77b4aeaf8714f2178bd
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
ms.locfileid: "17553260"
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell を使用してユーザー アカウントを作成する

**概要:** Office 365 PowerShell を使用して Office 365 でユーザー アカウントを作成する方法について学習します。
  
Office 365 PowerShell を使用すると、特に複数のユーザー アカウントを効率的に作成できます。Office 365 PowerShell でユーザー アカウントを作成する場合、特定のプロパティは常に必須です。他のプロパティはアカウントを作成する際に必須ではありませんが、別の面で重要となります。次の表で、これらのプロパティを説明します。
  
****

|**プロパティ名**|**必須**|**説明**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |はい  <br/> |これは、Office 365 サービスで使用される表示名です。たとえば、Caleb Sills。  <br/> |
|**UserPrincipalName** <br/> |はい  <br/> |これは、Office 365 サービスにサインインするために使用されるアカウント名です。たとえば、CalebS@contoso.onmicrosoft.com。  <br/> |
|**FirstName** <br/> |いいえ  <br/> ||
|**LastName** <br/> |いいえ  <br/> ||
|**LicenseAssignment** <br/> |いいえ  <br/> |これはライセンシング プラン (ライセンス プラン、Office 365 プラン、SKU とも呼ばれる) で、ここから使用可能なライセンスがユーザー アカウントに割り当てられます。ライセンスによって、アカウントに利用できる Office 365 サービスが定義されます。アカウントを作成するときにユーザーにライセンスを割り当てる必要はありませんが、アカウントは Office 365 サービスにアクセスするためのライセンスを必要とします。ユーザー アカウントにライセンスを割り当てる期間は作成後 30 日です。<br/> **Get-MsolAccountSku** コマンドレットを使用して、ライセンシング プラン (**AccountSkuId**) と、組織で利用可能なライセンスを表示します。詳細については、「[Office 365 PowerShell でライセンスとサービスを確認する](view-licenses-and-services-with-office-365-powershell.md)」をご覧ください。<br/> |
|**Password** <br/> |いいえ  <br/> | パスワードを指定しない場合、ランダムなパスワードがユーザー アカウントに割り当てられ、パスワードはコマンドの結果に表示されます。パスワードを指定する場合、次の複雑さの条件を満たしている必要があります。 <br/>  8 から 16 文字の ASCII テキスト文字。 <br/>  次のうちの 3 つの種類の文字: 小文字、大文字、数字、記号。 <br/> |
|**UsageLocation** <br/> |いいえ  <br/> |これは、有効な ISO 3166-1 alpha-2 の国別コードです。たとえば、米国は US、フランスは FR です。いくつかの Office 365 サービスは特定の国では使用できないため、この値を提供することが重要です。アカウントにこの値を設定しない限り、ユーザー アカウントにライセンスを割り当てることはできません。詳細については、「[ライセンスによる使用制限について](https://go.microsoft.com/fwlink/p/?LinkId=691730)」を参照してください。<br/> |
   
## <a name="before-you-begin"></a>はじめに

このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>Office 365 PowerShell を使用して個別のユーザー アカウントを作成します

個別のアカウントを作成するには、次の構文を使用します。
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

この例では、米国の Caleb Sills という名前のユーザーにアカウントを作成し、 `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスを割り当てます。
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>Office 365 PowerShell を使用して複数のユーザー アカウントを作成する

1. 必要なユーザー アカウント情報を含むコンマ区切り (CSV) ファイルを作成します。例:
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>CSV ファイルの最初の行の列名と順序は任意ですが、ファイルの残りの部分のデータが列名の順序と一致するかどうかを確認し、Office 365 PowerShell コマンドのパラメーター値に列名を使用します。
    
2. 次の構文を使用してください。
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

この例は、C:\My Documents\NewAccounts.csv という名前のファイルからユーザー アカウントを作成し、C:\My Documents\NewAccountResults.csv という名前のファイルに結果を記録します。
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. 出力ファイルで結果を確認します。パスワードを指定しなかったため、生成されたランダムなパスワードが出力ファイルに表示されます。
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a>個別のユーザー アカウントを作成するには Azure Active Directory V2 PowerShell モジュールを使用します

Azure Active Directory V2 PowerShell モジュールから **New-AzureADUser** コマンドレットを使用するには、まず自分のサブスクリプションに接続する必要があります。手順については、「[Azure Active Directory V2 PowerShell モジュールを使用した接続](https://go.microsoft.com/fwlink/?linkid=842218)」を参照してください。
  
接続したら、以下の構文を使用して個別のアカウントを作成します。
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

この例では、米国の Caleb Sills というユーザーのアカウントを作成します。
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a>関連項目

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell でユーザー アカウントをブロックする](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Export-Csv](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

