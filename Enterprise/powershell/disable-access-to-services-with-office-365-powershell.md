---
title: Office 365 PowerShell を使ったサービスへのアクセスを無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/11/2018
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
description: Office 365 の PowerShell を使用して、組織内のユーザーの Office 365 サービスへのアクセスを無効にする方法について説明します。
ms.openlocfilehash: 66f6c04c1488f14d5752974a5475e7ef11279406
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897420"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Office 365 PowerShell を使ったサービスへのアクセスを無効にする

**の概要:** Office 365 の PowerShell を使用して、組織内のユーザーの Office 365 サービスへのアクセスを無効にする方法について説明します。
  
Office 365 アカウントは、ライセンス計画からライセンスが割り当てられているが、ときに Office 365 のサービスが割り当てられているユーザー ライセンスからです。ただし、ユーザーがアクセスできる Office 365 サービスを制御できます。などのライセンスでは、SharePoint のオンライン サービスへのアクセス、にもかかわらずへのアクセス権を無効にできます。任意の数の特定のライセンス計画のためのサービスへのアクセスを無効にするのには、Office 365 の PowerShell を使用できます。

- 個々のアカウント。
    
- アカウントのグループ。
    
- 組織内のすべてのアカウント。
    
## <a name="before-you-begin"></a>始める前に
<a name="RTT"> </a>

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- **Get MsolAccountSku**コマンドレットを使用するには使用可能なライセンスの計画、およびそれらのプランで利用可能な Office 365 サービスを表示します。詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。
    
- 参照してくださいするのには、前に、このトピックで説明する手順の実行結果の後は、 [Office 365 の PowerShell でアカウントのライセンスおよびサービスの詳細を表示](view-account-license-and-service-details-with-office-365-powershell.md)を参照してください。
    
- PowerShell スクリプトが利用可能なこのトピックで説明する手順を自動化します。具体的には、スクリプトでは、表示し、影響を与えるを含む、Office 365 の組織でサービスを無効にすることができます。詳細については、 [Office 365 の PowerShell で影響を与えるへのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)を参照してください。
    
- **Get MsolUser**コマンドレットを使用するには、_すべて_のパラメーターを使用せず、最初の 500 のユーザー アカウントのみが返されます。
    
## <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>特定のライセンスについての特定のユーザーに対して特定の Office 365 サービスを無効にします。
  
特定のライセンスについてのユーザーの Office 365 サービスの特定のセットを無効にするには、次の手順に従います。
  
1. ライセンスについての次の構文を使用して、不要なサービスを識別します。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  ライセンス プランという名前で、Office オンライン サービスと SharePoint のオンライン サービスを無効にする**LicenseOptions**オブジェクトを作成する例を次`litwareinc:ENTERPRISEPACK`(Office 365 エンタープライズ E3)。
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. 手順 1 の **LicenseOptions** オブジェクトを、1 人以上のユーザーに使用します。
    
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

ライセンス プランが複数のサービスへのアクセスを無効にする場合は、ライセンス プランごとに確認する上記の手順を繰り返します。

- ユーザー アカウントには、ライセンスのプランが割り当てられています。
- ライセンス プランを無効にするサービスを利用できます。

ライセンスが必要にそれらを割り当てるときにユーザーの Office 365 サービスを無効にするには、[ユーザー ライセンスを割り当てる際にサービスへのアクセスを無効にする](disable-access-to-services-while-assigning-user-licenses.md)を参照してください。


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
    
  

