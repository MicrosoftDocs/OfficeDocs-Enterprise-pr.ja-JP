---
title: DAP パートナー用に Windows PowerShell を使用して Microsoft 365 テナントを管理する
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
ms.custom: seo-marvel-apr2020
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: この記事では、Microsoft 365 の PowerShell を使用して顧客テナンシーを管理する方法について説明します。
ms.openlocfilehash: b1e0459b906bd0a06758147923dff0dcc0af1b3e
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605943"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Microsoft 365 テナントを管理する

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

Windows PowerShell を使用すると、シンジケーションおよびクラウドソリューションプロバイダー (CSP) パートナーは、Microsoft 365 管理センターでは利用できない顧客のテナント設定を簡単に管理および報告できます。パートナー管理者アカウントが顧客テナンシーに接続するには、(AOBO) の代理人として管理する必要があることに注意してください。
  
委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。 他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。 これらのサブスクリプションは、お客様に対して Microsoft 365 のサブスクリプションをサービス提供にバンドルしています。 Microsoft 365 サブスクリプションを販売する際には、顧客のテナンシーに対して管理およびレポートできるように、顧客テナンシーへの (AOBO) アクセス許可が自動的に付与されます。
## <a name="what-do-you-need-to-know-before-you-begin"></a>始める前に把握しておくべき情報

このトピックの手順では、 [PowerShell を使用して Microsoft 365 に](connect-to-office-365-powershell.md)接続するために接続する必要があります。
  
また、パートナーのテナント管理者の資格情報も必要です。
  
## <a name="what-do-you-want-to-do"></a>必要な作業

### <a name="list-all-tenant-ids"></a>すべてのテナント ID を一覧表示する

> [!NOTE]
> テナントが 500 を超える場合は、コマンドレット構文のスコープを  _-All_ または _-MaxResultsParameter_ に設定します。これは、 **Get-MsolUser** など、出力のサイズが大きいコマンドレットに適用されます。
  
アクセスできるすべての顧客テナント ID を一覧表示するには、次のコマンドを実行します。
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

これにより、 **テナント ID** 順にすべての顧客テナントが一覧表示されます。

>[!Note]
>PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。 これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a>ドメイン名を使用してテナント ID を取得する

ドメイン名によって特定の顧客テナントの **テナント ID** を取得するには、次のコマンドを実行します。 _<domainname.onmicrosoft.com>_ を、目的の顧客テナントの実際のドメイン名に置き換えます。
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>テナントのすべてのドメインを一覧表示する

任意の 1 つの顧客テナントの全ドメインを取得するには、次のコマンドを実行します。_<customer TenantId value>_ を実際の値に置き換えます。
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

追加のドメインを登録した場合、顧客の **テナント ID** と関連付けられたすべてのドメインが返されます。
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>すべてのテナントと登録済みドメインのマッピングを取得する

Microsoft 365 用の以前の PowerShell については、テナント Id またはドメインのいずれかを同時に取得し、それらのすべての間で明確なマッピングを行わない方法を示していました。 このコマンドは、すべての顧客テナント ID とそのドメインの一覧を生成します。
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>テナントの全ユーザーを取得する

これにより、特定のテナントの全ユーザーの **UserPrincipalName**、**DisplayName**、および **isLicensed** の状態が表示されます。_<customer TenantId value>_ を実際の値に置き換えます。
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>ユーザーに関するすべての詳細を取得する

特定のユーザーのすべてのプロパティを表示する場合は、次のコマンドを実行します。_<customer TenantId value>_ と _<user principal name value>_ を実際の値に置き換えます。
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>ユーザーの追加、オプションの設定、およびライセンスの割り当てを行う

Microsoft 365 ユーザーの一括作成、構成、およびライセンスは、Microsoft 365 の PowerShell を使用することによって、特に効率よく実現されます。 この2段階のプロセスでは、最初にコンマ区切り値 (CSV) ファイルに追加するすべてのユーザーのエントリを作成し、次に Microsoft 365 の PowerShell を使用してそのファイルをインポートします。 
  
#### <a name="create-a-csv-file"></a>CSV ファイルを作成する

次の形式を使用して、CSV ファイルを作成します。
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
各部分の意味は次のとおりです。
  
- **UsageLocation**: この値は、ユーザーの 2 文字の ISO の国や地域コードです。国や地域コードは、[ISO オンライン参照プラットフォーム](https://go.microsoft.com/fwlink/p/?LinkId=532703)で調べることができます。たとえば、米国のコードは US、ブラジルのコードは BR です。 
    
- **LicenseAssignment**:この値には、次の形式を使用します。 `syndication-account:<PROVISIONING_ID>`。たとえば、顧客テナントのユーザーに O365_Business_Premium ライセンスを割り当てている場合、 **LicenseAssignment** の値は **syndication-account:O365_Business_Premium** のようになります。PROVISIONING_ID は、シンジケートまたは CSP パートナーとしてアクセスできるシンジケート パートナー ポータルで確認できます。
    
#### <a name="import-the-csv-file-and-create-the-users"></a>CSV ファイルをインポートしてユーザーを作成する

CSV ファイルを作成したら、次のコマンドを実行して、無期限のパスワード付きユーザー アカウントを作成します。このパスワードは、ユーザーが初回サインイン時に変更する必要があり、指定したライセンスを割り当てる必要があります。必ず、正しい CSV ファイル名に置き換えてください。
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>関連項目

#### 

[パートナーのヘルプ](https://go.microsoft.com/fwlink/p/?LinkId=533477)

