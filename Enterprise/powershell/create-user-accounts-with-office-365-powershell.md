---
title: PowerShell を使用して Microsoft 365 ユーザーアカウントを作成する
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Microsoft 365 の PowerShell を使用してユーザーアカウントを作成する方法について説明します。
ms.openlocfilehash: 4057f4e1b29e8177bee32306c49f25f607ac5a0f
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230793"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>PowerShell を使用して Microsoft 365 ユーザーアカウントを作成する

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 の PowerShell を使用すると、ユーザーアカウント、特に複数のユーザーアカウントを効率的に作成できます。 PowerShell でユーザーアカウントを作成する場合、特定のアカウントのプロパティが常に必要です。 他のプロパティはアカウントを作成する際に必須ではありませんが、別の面で重要となります。 次の表では、これらのプロパティについて説明します。
  
|**プロパティ名**|**必須**|**説明**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |はい  <br/> |これは、Microsoft 365 サービスで使用される表示名です。 たとえば、Caleb Sills。  <br/> |
|**UserPrincipalName** <br/> |はい  <br/> |これは、Microsoft 365 サービスへのサインインに使用されるアカウント名です。 たとえば、CalebS@contoso.onmicrosoft.com。  <br/> |
|**FirstName** <br/> |いいえ  <br/> ||
|**LastName** <br/> |いいえ  <br/> ||
|**LicenseAssignment** <br/> |いいえ  <br/> |これは、使用可能なライセンスがユーザーアカウントに割り当てられているライセンスプラン (ライセンスプランまたは SKU とも呼ばれます) です。 ライセンスでは、アカウントで利用可能な Microsoft 365 サービスが定義されています。 アカウントの作成時にライセンスをユーザーに割り当てる必要はありませんが、そのアカウントには Microsoft 365 サービスにアクセスするためのライセンスが必要です。 ユーザー アカウントにライセンスを割り当てる期間は作成後 30 日です。 |
|**Password** <br/> |いいえ  <br/> | パスワードを指定しない場合、ランダムなパスワードがユーザー アカウントに割り当てられ、パスワードはコマンドの結果に表示されます。パスワードを指定する場合、小文字、大文字、数字、記号のうちの 3 つの種類の文字を使った 8 から 16 文字の ASCII テキスト文字にする必要があります。 <br/> |
|**UsageLocation** <br/> |いいえ  <br/> |これは有効な ISO 3166-1 alpha 国コードです。 たとえば、米国は US、フランスは FR です。 一部の Microsoft 365 サービスは特定の国では利用できないため、この値を指定することは重要です。そのため、アカウントにこの値が設定されていない限り、ユーザーアカウントにライセンスを割り当てることはできません。 詳細については、「[ライセンス制限につい](https://go.microsoft.com/fwlink/p/?LinkId=691730)て」を参照してください。  <br/> |
   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph モジュールの Azure Active Directory PowerShell を使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。

接続したら、以下の構文を使用して個別のアカウントを作成します。
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

この例では、米国の Caleb Sills というユーザーのアカウントを作成します。
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する

最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。

### <a name="create-an-individual-user-account"></a>個別のユーザー アカウントの作成

個別のアカウントを作成するには、次の構文を使用します。
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

使用可能なライセンスのプラン名を一覧表示するには、次のコマンドを使用します。

````powershell
Get-MsolAccountSku
````

この例では、米国の Caleb Sills という名前のユーザーにアカウントを作成し、 `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンス プランからライセンスを割り当てます。
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>複数のユーザー アカウントを作成する

1. 必要なユーザー アカウント情報を含むコンマ区切り (CSV) ファイルを作成します。例:
    
  ```powershell
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
  ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
  LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
  ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>CSV ファイルの最初の行の列名とその順序は任意ですが、ファイルの残りの部分のデータが列名の順序と一致していることを確認し、Microsoft 365 コマンドの PowerShell のパラメーター値として列名を使用します。
    
2. 次の構文を使用してください。
    
  ```powershell
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

この例は、C:\My Documents\NewAccounts.csv という名前のファイルからユーザー アカウントを作成し、C:\My Documents\NewAccountResults.csv という名前のファイルに結果を記録します。
    
  ```powershell
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. 出力ファイルで結果を確認します。 パスワードを指定していないため、Microsoft 365 によって生成されたランダムなパスワードが出力ファイルに表示されます。
    
## <a name="see-also"></a>関連項目

[PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[PowerShell を使用して Microsoft 365 を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 の PowerShell の概要](getting-started-with-office-365-powershell.md)
