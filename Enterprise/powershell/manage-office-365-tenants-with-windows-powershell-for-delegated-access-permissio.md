---
title: 委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Microsoft 365 テナントを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: '概要: Microsoft 365 用の Windows PowerShell を使用して顧客テナンシーを管理します。'
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998233"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Microsoft 365 テナントを管理する

Windows PowerShell を使用すると、シンジケーションおよびクラウドソリューションプロバイダー (CSP) パートナーは、Microsoft 365 管理センターでは利用できない顧客のテナント設定を簡単に管理および報告できます。 パートナー管理者アカウントが顧客テナンシーに接続するためには、「代理で管理」(AOBO) のアクセス許可が必要であることに注意してください。
  
委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。 他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。 これらのサブスクリプションは、お客様に対して Microsoft 365 のサブスクリプションをサービス提供にバンドルしています。 Microsoft 365 サブスクリプションを販売する際には、顧客のテナンシーに対して管理およびレポートできるように、顧客テナンシーへの (AOBO) アクセス許可が自動的に付与されます。
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).
  
また、パートナーのテナント管理者の資格情報も必要です。
  
## <a name="what-do-you-want-to-do"></a>必要な作業

### <a name="list-all-tenant-ids"></a>すべてのテナント ID を一覧表示する

> [!NOTE]
> If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.
  
アクセスできるすべての顧客テナント ID を一覧表示するには、次のコマンドを実行します。
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

これにより、 **テナント ID** 順にすべての顧客テナントが一覧表示されます。

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>ドメイン名を使用してテナント ID を取得する

To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>テナントのすべてのドメインを一覧表示する

To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

追加のドメインを登録した場合、顧客の **テナント ID** と関連付けられたすべてのドメインが返されます。
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>すべてのテナントと登録済みドメインのマッピングを取得する

The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>テナントの全ユーザーを取得する

This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>ユーザーに関するすべての詳細を取得する

If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>ユーザーの追加、オプションの設定、およびライセンスの割り当てを行う

Microsoft 365 ユーザーの一括作成、構成、およびライセンスは、Office 365 用の Windows PowerShell を使用することによって、特に効率的に実現されます。 この 2 段階のプロセスでは、まず追加するすべてのユーザーのエントリをコンマ区切り値 (CSV) ファイルに作成してから、Office 365 の Windows PowerShell を使用してそのファイルをインポートします。 
  
#### <a name="create-a-csv-file"></a>CSV ファイルを作成する

次の形式を使用して、CSV ファイルを作成します。
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
各部分の意味は次のとおりです。
  
- **UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR. 
    
- **LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.
    
#### <a name="import-the-csv-file-and-create-the-users"></a>CSV ファイルをインポートしてユーザーを作成する

After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>関連項目

#### 

[パートナーのヘルプ](https://go.microsoft.com/fwlink/p/?LinkId=533477)

