---
title: "Office 365 PowerShell を使ったサービスへのアクセスを無効にする"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Office 365 の PowerShell を使用して、組織内のユーザーの Office 365 サービスへのアクセスを無効にする方法について説明します。"
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Office 365 PowerShell を使ったサービスへのアクセスを無効にする

**の概要:**Office 365 の PowerShell を使用して、組織内のユーザーの Office 365 サービスへのアクセスを無効にする方法について説明します。
  
Office 365 アカウントは、ライセンス計画からライセンスが割り当てられているが、ときに Office 365 のサービスが割り当てられているユーザー ライセンスからです。ただし、ユーザーがアクセスできる Office 365 サービスを制御できます。などの場合でも、ライセンスは、SharePoint Online へのアクセスを許可へのアクセス権を無効にすることができます。実際には、任意の数のためのサービスへのアクセスを無効にするのには、Office 365 の PowerShell を使用できます。

- 個々のアカウント。
    
- アカウントのグループ。
    
- 組織内のすべてのアカウント。
    
## <a name="before-you-begin"></a>はじめに
<a name="RTT"> </a>

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- **Get MsolAccountSku**コマンドレットを使用するには使用可能なライセンスの計画、およびそれらのプランで利用可能な Office 365 サービスを表示します。詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。
    
- 参照してくださいするのには、前に、このトピックで説明する手順の実行結果の後は、 [Office 365 の PowerShell でアカウントのライセンスおよびサービスの詳細を表示](view-account-license-and-service-details-with-office-365-powershell.md)を参照してください。
    
- このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。具体的に言うと、このスクリプトにより、Office 365 組織のサービス (Sway を含む) を表示し、無効化できます。詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。
    
- **Get MsolUser**コマンドレットを使用するには、_すべて_のパラメーターを使用せず、最初の 500 のユーザー アカウントのみが返されます。
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a>1 つのライセンスについての特定のユーザーに対して特定の Office 365 サービス
  
1 つのライセンスについてのユーザーの Office 365 サービスの特定のセットを無効にするには、次の手順に従います。
  
1. ライセンスについての次の構文を使用して、不要なサービスを識別します。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    ライセンス プランという名前で、Office オンライン サービスと SharePoint のオンライン サービスを無効にする**LicenseOptions**オブジェクトを作成する例を次`litwareinc:ENTERPRISEPACK`(Office 365 エンタープライズ E3)。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 1 つまたは複数のユーザーには、手順 1 から**LicenseOptions**オブジェクトを使用します。
    
  - サービスが無効になっている新しいアカウントを作成するには、次の構文を使用します。
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    Allie Bellew、ライセンスが割り当てられ、手順 1 で説明されているサービスを無効にするため、新しいアカウントを作成する例を次にします。
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    Office 365 の PowerShell でのユーザー アカウントの作成の詳細については、 [Office 365 の PowerShell でのユーザー アカウントの作成](create-user-accounts-with-office-365-powershell.md)を参照してください。
    
  - ライセンスを付与された既存のユーザー用のサービスを無効にするには、次の構文を使用します。
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    この例では、ユーザー BelindaN@litwareinc.com に対してサービスを無効にします。
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - すべての既存のライセンスを受けたユーザーの手順 1 で説明されているサービスを無効にするには、 **Get MsolAccountSku**コマンドレット ( **litwareinc:ENTERPRISEPACK**) などの表示から、Office 365 のプランの名前を指定し、次のコマンドを実行します。
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - 既存のユーザーのグループに対してサービスを無効にするには、次のいずれかの方法を使用して、ユーザーを特定します。
    
  - **既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    次の使用例は、米国内の販売部門のユーザー用のサービスを無効にします。
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **特定のアカウントの一覧を使用する** これを行うには、次の手順を実行します。
    
1. 次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成します。
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    この例で、テキスト ファイルは、c:\\マイ ドキュメント\\Accounts.txt。
    
2. 次のコマンドを実行します。
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

ライセンスが必要にそれらを割り当てるときにユーザーの Office 365 サービスを無効にするには、[ユーザー ライセンスを割り当てる際にサービスへのアクセスを無効にする](disable-access-to-services-while-assigning-user-licenses.md)を参照してください。
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a>ライセンス プランのすべてのユーザーに対して特定の Office 365 サービス
  
使用可能なライセンスのすべての計画では、ユーザーの Office 365 サービスを無効にする、次の手順に従います。
  
1. このスクリプトをコピーして、メモ帳に貼り付けます。
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. 環境に合わせて次の値をカスタマイズします。
    
  -  _<UndesirableService>_この例では、Office オンラインおよび SharePoint Online を使用します。
    
  -  _<Account>_この例では、belindan@litwareinc.com を使用します。
    
    カスタマイズされたスクリプトは、次のようになります。
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. としてスクリプトを保存する`RemoveO365Services.ps1`を簡単に検索することができる場所にします。この例でファイルを保存しましたが`C:\\O365 Scripts`。
    
4. Office 365 の PowerShell のスクリプトを実行するには、次のコマンドを使用します。
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> これらの手順のいずれかの効果を逆にする (つまり、無効になっているサービスを再度有効にする) プロシージャを実行できません、ですが、値を使用して、 `$null` _DisabledPlans_パラメーターの。
  
[ページのトップへ](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a>1 つのライセンスのすべてのユーザーのすべての Office 365 サービスの計画します。
 
特定のライセンスについてのすべてのユーザーのすべての Office 365 サービスを無効にするには、$acctSKU ( **litwareinc:ENTERPRISEPACK**) などのライセンスの計画の名前を指定し、PowerShell コマンド ウィンドウでこれらのコマンドを実行します。

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>関連項目
<a name="SeeAlso"> </a>

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell でユーザー アカウントをブロックする](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザー アカウントを作成する](create-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [新しい-MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-msoluser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

