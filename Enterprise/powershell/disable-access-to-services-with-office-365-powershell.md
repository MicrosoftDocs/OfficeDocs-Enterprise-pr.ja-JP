---
title: Office 365 PowerShell を使ったサービスへのアクセスを無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/04/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Office 365 PowerShell を使用して、ユーザーの Office 365 サービスへのアクセスを無効にします。
ms.openlocfilehash: 83967e0b44099fb651edaa7f7cba9e811f9fdf81
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072199"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Office 365 PowerShell を使ったサービスへのアクセスを無効にする

Office 365 アカウントにライセンスプランのライセンスが割り当てられている場合、そのライセンスから Office 365 サービスがユーザーに対して利用可能になります。 ただし、ユーザーがアクセスできる Office 365 サービスを制御することができます。 たとえば、ライセンスで SharePoint Online サービスへのアクセスが許可されている場合でも、アクセスを無効にすることができます。 PowerShell を使用して、次のような特定のライセンスプランで任意の数のサービスへのアクセスを無効にすることができます。

- 個々のアカウント。
- アカウントのグループ。
- 組織内のすべてのアカウント。

>[!Note]
>Office 365 サービスの依存関係によって、他のサービスに依存している場合に、指定されたサービスが無効になることがあります。
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する

まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。

次に、このコマンドを使用して、使用可能なライセンスプラン (AccountSkuIds とも呼ばれます) を表示します。

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>

詳細については、「 [Office 365 PowerShell でライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。
    
このトピックの手順の前と後の結果を確認するには、「 [Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示](view-account-license-and-service-details-with-office-365-powershell.md)する」を参照してください。
    
このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。 具体的には、このスクリプトを使用すると、Sway などの Office 365 組織のサービスを表示したり、無効にしたりできます。 詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>特定のライセンスプランの特定のユーザーに対して特定の Office 365 サービスを無効にする
  
特定のライセンスプランのユーザーに対して特定の Office 365 サービスのセットを無効にするには、次の手順を実行します。
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a>手順 1: 次の構文を使用して、ライセンスプランで不要なサービスを特定します。
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

次の例では、という名前`litwareinc:ENTERPRISEPACK`のライセンスプラン (Office 365 Enterprise E3) で Office および SharePoint Online サービスを無効にする**licenseoptions**オブジェクトを作成します。
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>手順 2: 1 人以上のユーザーの手順1の**Licenseoptions**オブジェクトを使用します。
    
サービスが無効になっている新しいアカウントを作成するには、次の構文を使用します。
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

次の例では、ライセンスを割り当て、手順1で説明されているサービスを無効にする Allie Bellew の新しいアカウントを作成します。
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Office 365 PowerShell でユーザーアカウントを作成する方法の詳細については、「 [office 365 powershell を使用してユーザーアカウントを作成](create-user-accounts-with-office-365-powershell.md)する」を参照してください。
    
ライセンスを付与された既存のユーザー用のサービスを無効にするには、次の構文を使用します。
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

この例では、ユーザー BelindaN@litwareinc.com に対してサービスを無効にします。
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

既存のライセンスを持つすべてのユーザーについて、手順1で説明されているサービスを無効にするには、 **get-msolaccountsku**コマンドレット ( **LITWAREINC: enterprisepack**など) の表示から Office 365 プランの名前を指定し、次のコマンドを実行します。
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 _All_パラメーターを使用せずに**get-msoluser**コマンドレットを使用すると、最初の500ユーザーアカウントのみが返されます。

既存のユーザーのグループに対してサービスを無効にするには、次のいずれかの方法を使用して、ユーザーを特定します。
    
**方法1既存のアカウント属性に基づいてアカウントをフィルター処理する** 

この設定を行うには、次の構文を使用します。
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

次の例では、米国内の販売部門のユーザーのサービスを無効にします。
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**方法 2: 特定のアカウントの一覧を使用する** 

これを行うには、次の手順を実行します。
    
1. 次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  この例では、テキストファイルは「C\\: My\\Documents のアカウント .txt」です。
    
2. 次のコマンドを実行します。
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

複数のライセンスプランのサービスへのアクセスを無効にする場合は、ライセンスプランごとに上記の手順を繰り返し、以下のことを確認してください。

- ユーザーアカウントにはライセンスプランが割り当てられています。
- 無効化するサービスは、ライセンスプランで利用できます。

ユーザーがライセンスプランに割り当てている間、ユーザーに対して Office 365 サービスを無効にするには、「[ユーザーのライセンスの割り当て中にサービスへのアクセスを無効](disable-access-to-services-while-assigning-user-licenses.md)にする」を参照してください。


## <a name="see-also"></a>関連項目
<a name="SeeAlso"> </a>

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell でユーザー アカウントをブロックする](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザー アカウントを作成する](create-user-accounts-with-office-365-powershell.md)
    
