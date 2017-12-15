---
title: "Office 365 PowerShell を使ったサービスへのアクセスを無効にする"
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Office 365 の PowerShell を使用して追加または、組織内のユーザーの Office 365 サービスへのアクセスを削除する方法について説明します。"
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Office 365 PowerShell を使ったサービスへのアクセスを無効にする

**の概要:**Office 365 の PowerShell を使用して追加または、組織内のユーザーの Office 365 サービスへのアクセスを削除する方法について説明します。
  
Office 365 アカウントは、ライセンス計画からライセンスが割り当てられているが、ときに Office 365 のサービスが割り当てられているユーザー ライセンスからです。ただし、ユーザーがアクセスできる Office 365 サービスを制御できます。などの場合でも、ライセンスは、SharePoint Online へのアクセスを許可へのアクセス権を無効にすることができます。実際には、任意の数のためのサービスへのアクセスを無効にするのには、Office 365 の PowerShell を使用できます。
- 個々のアカウント。
    
- アカウントのグループ。
    
- 組織内のすべてのアカウント。
    
 **内容:**[短いバージョン (手順説明なし)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[長いバージョン (詳細な説明と指示)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[参照してください。](disable-access-to-services-with-office-365-powershell.md#SeeAlso)
## <a name="before-you-begin"></a>開始する前に
<a name="RTT"> </a>

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- **Get MsolAccountSku**コマンドレットを使用するには使用可能なライセンスの計画、およびそれらのプランで利用可能な Office 365 サービスを表示します。詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。
    
- 参照してくださいするのには、前に、このトピックで説明する手順の実行結果の後は、 [Office 365 の PowerShell でアカウントのライセンスおよびサービスの詳細を表示](view-account-license-and-service-details-with-office-365-powershell.md)を参照してください。
    
- このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。具体的に言うと、このスクリプトにより、Office 365 組織のサービス (Sway を含む) を表示し、無効化できます。詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。
    
- _All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。
    
## <a name="the-short-version-instructions-without-explanations"></a>簡略版 (説明なしの手順)
<a name="ShortVersion"> </a>

このセクションでは、余分な説明を省いて簡潔に手順を示します。ご質問がある場合、または詳細情報が必要な場合には、このトピックの残りの部分をご覧ください。
  
1 つのライセンスについてのユーザーの Office 365 サービスを無効にするには、次の手順に従います。
  
1. ライセンスについての次の構文を使用して、不要なサービスを識別します。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    次の使用例という名前のライセンス プランで、Office オンライン サービスと SharePoint のオンライン サービスを無効にする**LicenseOptions**オブジェクトを作成する`litwareinc:ENTERPRISEPACK`(Office 365 エンタープライズ E3)。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 1 つまたは複数のユーザーには、手順 1 から**LicenseOptions**オブジェクトを使用します。
    
  - サービスが無効になっている新しいアカウントを作成するには、次の構文を使用します。
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    この例では、Allie Bellew の新しいアカウントを作成して、手順 1 で説明されているライセンスの割り当てとサービスの無効化を行います。
    
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

  - すべての既存のライセンスを受けたユーザーの手順 1 で説明されているサービスを無効にするには、 **Get MsolAccountSku**コマンドレット ( **litwareinc:ENTERPRISEPACK** ) などの表示から、Office 365 のプランの名前を指定し、次のコマンドを実行します。
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - 既存のユーザーのグループに対してサービスを無効にするには、次のいずれかの方法を使用して、ユーザーを特定します。
    
  - **既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    この例では、米国内の販売部門のユーザーに対してサービスを無効にします。
    
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
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

ライセンスが必要にそれらを割り当てるときにユーザーの Office 365 サービスを無効にするには、[ユーザー ライセンスを割り当てる際にサービスへのアクセスを無効にする](disable-access-to-services-while-assigning-user-licenses.md)を参照してください。
  
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

3. としてスクリプトを保存する`RemoveO365Services.ps1`を簡単に検索することができる場所にします。この例でファイルを保存しましたが「 `C:\\O365 Scripts`」です。
    
4. Office 365 の PowerShell のスクリプトを実行するには、次のコマンドを使用します。
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> これらの手順のいずれかの効果を逆にする (つまり、無効になっているサービスを再度有効にする) プロシージャを実行できません、ですが、値を使用して、 `$null` _DisabledPlans_パラメーターの。
  
[ページのトップへ](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a>詳細版 (詳細な説明付きの手順)
<a name="LongVersion"> </a>

既定では、Office 365 の PowerShell を使用してライセンスを発行するときにすべてのサービスを有効にします。良いことは多くの場合: を割り当てることができます迅速かつ簡単にライセンス ユーザーに方法に沿って、各サービスを有効にするかを指定せずに、ことを意味します。
  
ただし、されても、ユーザーの利用可能なサービスを制限する場合は trueなどの一部のユーザーが Office Professional Plus、ビジネス オンライン、および Exchange Online では、Skype へのアクセス権を持つかもしれませんが、同じユーザーが SharePoint Online または Office Online へのアクセスを持つべきではありません。その方法でアカウントを制限することができますか。結局のところ、以下の操作を実行できます。このしくみについて説明するために、みましょう次の 2 つの方法この問題に対処するため。
  
1. 自動的にすべてのサービスを有効にする Office 365 のライセンスをユーザーに割り当てます。
    
2. 1 組のユーザーの指定されたサービスを無効にする Office 365 の PowerShell コマンドを実行します。
    
既にきました手順 1: ユーザー (Belinda ようにしてください。) が彼女をすべての Office 365 サービスへのアクセスを提供する Office 365 のライセンスを持ちます。彼女 SharePoint Online へのアクセス権がないように、Belinda のアカウントを変更する、( `SHAREPOINTENTERPRISE`) または Office Online に ( `SHAREPOINTWAC`)。ですが、方法は、利用すべきですか。
  
ここではどのようにします。まず始めに、無効にするサービスを含む**LicenseOption**オブジェクトを作成する**新規 MsolLicenseOptions**コマンドレットを使用するつもりです。Belinda の場合は、無効にする`SHAREPOINTENTERPRISE`と`SHAREPOINTWAC`ので、このコマンドを使用します。
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

しくみを参照してください。ライセンス計画を指定する ( `litwareinc:ENTERPRISEPACK`) の各サービスを無効にすると、コンマを使用してこれらのサービスを分離することを指定するとします。
  
> [!NOTE]
> 新しい**LicenseOption**オブジェクトを変数に格納することを確認します。使用して上記の例では、 `$x`、有効な Windows PowerShell の変数名を使用することができます。 
  
この時点で 2 つのサービスへの Belinda のアクセスを無効にするのに次のコマンドを使用できます。
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

特別なここでは、いずれか:**セット MsolUserLicense**コマンドレットを呼び出すし、 _LicenseOptions_パラメーターと変数が含まれますが私たちだけ ( `$x`) を無効にする計画が含まれています。何が表示されるようになりましたかどうかは時間をかけて Belinda のライセンス情報をコマンドを実行して、:`(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`でしょうか。ここに表示されます。
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

なかなか良いと思いませんか。もちろんにすれば同じことを複数のユーザーに必要な場合です。たとえば、これらのコマンドは、すべてのライセンスを受けたユーザーの同じ 2 つのサービスを無効にします。**Get MsolAccountSku**コマンドレット ( **litwareinc:ENTERPRISEPACK** ) などの表示から、Office 365 のプランの名前を指定し、それらを実行します。
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

Belinda がまだ有効な Office 365 ライセンスのことに留意してください。あっただけですので、彼女は、以下のサービスへのアクセス。2 つのサービスを無効にし、前に Belinda がニュースフィード、OneDrive、および SharePoint へのアクセス オンライン サイト。
  
![SharePoint アクセス権を持つユーザー。](images/o365_powershell_with_sharepoint.png)
  
今、彼女はこれらのオプションを利用できません。
  
![SharePoint アクセス権を持たないユーザー。](images/o365_powershell_without_sharepoint.png)
  
これで望みどおりになりました。
  
場合変更後に、: これらのサービスを再度有効にすることは可能でしょうか。当然です。ユーザーのすべてのサービスを再度有効にするには、次の**LicenseOption**オブジェクトを作成するのにこのコマンドを使用しました。
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

そのコマンドは何をしますか。先頭に、Windows PowerShell の定数を`$null`"nothing"の意味(または、「null 値」を意味に少しそれ以上の技術的な言語で)ご存知、サービスを無効にすることを示すためにある**新規 MsolLicenseOptions**コマンドレットを使用する場合。この例では、たくはありませんを無効にするサービスのいずれかです。_DisabledPlans_パラメーターの値は指定してコマンドを次のようなコマンドを使用するいると判断して潜在顧客を可能性があります。
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

ただし、次のように使うことはできません。代わりに、エラー メッセージが生成されます。
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
幸いなことに、パラメーター値を設定`$null`が機能します。
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

つまり、**セット MsolUserLicense**コマンドレットを実行するとということですね**セット MsolUserLicense**されないようにするため Belinda がすべて無効になっているサービス。
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

また、論理的には、無効になるサービスがないということは、すべてのサービスが有効になるということを意味します。
  
このスクリプトの動作方法を理解したら、みましょうを表示するライセンスを発行し、指定されたサービスと同じコマンドを使用してすべてを無効にする方法です。サウンドの非常に印象的ですが、正直に言うと、本当に何もすること: するだけで_AddLicenses_と_LicenseOptions_のパラメーターの両方を同じコマンドに含めます。つまり、最初にオブジェクトを作成する、 **LicenseOption** 。
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

前述のように、使用する_AddLicenses_および_LicenseOptions_パラメーターの両方のようにします。
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

コマンドが発行していること Belinda ようにしてください。 新しいライセンスがライセンスを Skype でのオンライン ビジネス ( `SHAREPOINTWAC`) とは、SharePoint Online ( `SHAREPOINTENTERPRISE`) どちらも使用できません。
  
[ページのトップへ](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合
<a name="LongVersion"> </a>

||
|:-----|
|![LinkedIn Learning の小さいアイコン](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 を初めて使用する場合は、**         LinkedIn Learning が提供する **Office 365 admins and IT pros** のための無料のビデオ コースをご覧ください。 |
   
## <a name="see-also"></a>See also
<a name="SeeAlso"> </a>

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell でユーザー アカウントをブロックする](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザー アカウントを作成する](create-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [新しい-MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [新しい-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [セット MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach オブジェクト](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[ページのトップへ](disable-access-to-services-with-office-365-powershell.md#RTT)
  

