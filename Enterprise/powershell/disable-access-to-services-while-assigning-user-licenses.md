---
title: "ユーザー ライセンスを割り当てる間、サービスへのアクセスを無効にする"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "Office 365 PowerShell を使い、ユーザー アカウントへのライセンスの割り当てと、特定のサービス プランの無効化を同時に行う方法を説明します。"
ms.openlocfilehash: 96ce12f811ee147a92da6b6928c2f6e3391c9b1f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>ユーザー ライセンスを割り当てる間、サービスへのアクセスを無効にする

**概要:** Office 365 PowerShell を使い、ユーザー アカウントへのライセンスの割り当てと、特定のサービス プランの無効化を同時に行う方法を説明します。
  
Office 365 サブスクリプションには、個々のサービスのサービス プランが付属します。Office 365 管理者は、ユーザーにライセンスを割り当てるときに特定のプランを無効にしなければならないことが少なくありません。この資料の手順を使用すると、PowerShell を使用して、1 ユーザー アカウントの、または複数のユーザー アカウントの特定のサービス プランを無効にした状態で、Office 365 ライセンスを割り当てることができます。
  
> [!NOTE]
> この資料は、Microsoft サポート エスカレーション エンジニアの Siddhartha Parmar の説明に基づいています。 
  
## <a name="before-you-begin"></a>はじめに

このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a>サブスクリプションとサービス プランに関する情報を収集する

現在のサブスクリプションを確認するため、次のコマンドを実行します。
  
```
Get-MsolAccountSku
```

`Get-MsolAccountSku` コマンドの出力に関して次に説明します。
  
- **AccountSkuId** は、組織のサブスクリプションです。形式は、\<OrganizationName>:\<Subscription> となります。\<OrganizationName> は、Office 365 に登録時に入力した値で、組織の一意の値です。\<Subscription> 値は、特定のサブスクリプションを表します。たとえば、litwareinc:ENTERPRISEPACK の場合、組織名は litwareinc で、サブスクリプション名が ENTERPRISEPACK (Office 365 Enterprise E3) です。
    
- **ActiveUnits** は、サブスクリプションで購入したライセンス数です。
    
- **WarningUnits** は、まだ更新しておらず、30 日の猶予期間を過ぎると有効期限切れになる、サブスクリプション内のライセンス数です。
    
- **ConsumedUnits** は、このサブスクリプションでユーザーに割り当てたライセンスの数です。
    
ライセンスを割り当てるユーザーが含まれる Office 365 サブスクリプションの AccountSkuId をメモに取ります。また、割り当てる十分な数のライセンスがあることも確認します ( **ActiveUnits** から **ConsumedUnits** を減算します)。
  
次に、以下のコマンドを実行して、使用しているすべてのサブスクリプションで利用できる Office 365 サービス プランの詳細を確認します。
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

このコマンドの出力に基づいて、ユーザーにライセンスを割り当てるときに無効にするサービス プランを判別します。
  
サービス プランの一覧の一部と、対応する Office 365 サービスを以下に示します。
  
|**サービス プラン**|**説明**|
|:-----|:-----|
|SWAY  <br/> |Sway  <br/> |
|INTUNE_O365  <br/> |Office 365 のモバイル デバイス管理  <br/> |
|YAMMER_ENTERPRISE  <br/> |Yammer  <br/> |
|RMS_S_ENTERPRISE  <br/> |Azure Rights Management (RMS)  <br/> |
|OFFICESUBSCRIPTION  <br/> |Office Professional Plus  <br/> |
|MCOSTANDARD  <br/> |Skype for Business Online  <br/> |
|SHAREPOINTWAC  <br/> |Office Online  <br/> |
|SHAREPOINTENTERPRISE  <br/> |SharePoint Online  <br/> |
|EXCHANGE_S_ENTERPRISE  <br/> |Exchange Online プラン 2  <br/> |
   
この時点で、AccountSkuId と無効にするサービス プランが決まったため、1 ユーザーまたは複数ユーザーにライセンスを割り当てることができます。
  
## <a name="for-a-single-user"></a>単一ユーザーの場合

単一ユーザーの場合、そのユーザー アカウントのユーザー プリンシパル名、AccountSkuId、無効にするサービス プランの一覧を入力し、説明テキスト、\< 記号、> 記号を削除します。次に、完成したコマンドを PowerShell コマンド プロンプトで実行します。
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

コマンド ブロックの例を以下に示します。アカウント名は belindan@contoso.com で、ライセンスは contoso:ENTERPRISEPACK であり、RMS_S_ENTERPRISE、SWAY、INTUNE_O365、YAMMER_ENTERPRISE の各サービス プランを無効にします。
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a>複数ユーザーの場合

この管理タスクを複数ユーザーに実行するには、UserPrincipalName フィールドと UsageLocation フィールドが含まれるコンマ区切り値 (CSV) テキスト ファイルを作成します。次に例を示します。
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

その後、入力および出力の各 CSV ファイルの場所、アカウント SKU ID、無効にするサービス プランの一覧を入力し、完成したコマンドを PowerShell コマンド プロンプトで実行します。
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

この PowerShell コマンド ブロックは以下の処理を行います。
  
- 各ユーザーのユーザー プリンシパル名を表示します。
    
- 各ユーザーにカスタマイズされたライセンスを割り当てます。
    
- 処理されたすべてのユーザーが含まれる CSV ファイルを作成し、そのライセンス状態を示します。
    
## <a name="see-also"></a>関連項目

#### 

[Office 365 PowerShell を使ったサービスへのアクセスを無効にする](disable-access-to-services-with-office-365-powershell.md)
  
[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)
  
[Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)

