---
title: "委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Office 365 テナントを管理する"
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: "概要:Office 365 の Windows PowerShell を使用して顧客テナンシーを管理します。"
ms.openlocfilehash: 6001a6b40d2851d13e8fb74da615a2b8137f17ec
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="manage-office-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="69f0b-103">委任アクセス許可 (DAP) パートナー用 Windows PowerShell で Office 365 テナントを管理する</span><span class="sxs-lookup"><span data-stu-id="69f0b-103">Manage Office 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="69f0b-104">**概要:** Office 365 の Windows PowerShell を使用して顧客テナンシーを管理します。</span><span class="sxs-lookup"><span data-stu-id="69f0b-104">Summary: Use Windows PowerShell for Office 365 to manage your customer tenancies.</span></span>
  
<span data-ttu-id="69f0b-p101">Windows PowerShell を使うと、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナー は、Office 365 管理センター で使うことができない顧客テナンシー設定を簡単に管理してレポートすることができます。パートナー管理者アカウントが顧客テナンシーに接続するためには、「代理で管理」(AOBO) のアクセス許可が必要であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p101">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Office 365 admin center. Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="69f0b-p102">委任アクセス許可 (DAP) パートナー とは、シンジケート パートナーとクラウド ソリューション プロバイダー (CSP) パートナーです。他の会社のネットワーク プロバイダーまたは通信プロバイダーであることもよくあります。それらの企業は、顧客に提供するサービスに Office 365 サブスクリプションをバンドルします。 Office 365 サブスクリプションを販売する際に、顧客テナンシー に対する「代理で管理」(AOBO) 権限が自動的に付与されるため、顧客テナンシーを管理し、顧客テナンシーに関するレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="69f0b-111">始める前に把握しておくべき情報</span><span class="sxs-lookup"><span data-stu-id="69f0b-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="69f0b-p103">このトピックの手順では、Office 365 のために Windows PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p103">The procedures in this topic require you to connect to Windows PowerShell for Office 365. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="69f0b-114">また、パートナーのテナント管理者の資格情報も必要です。</span><span class="sxs-lookup"><span data-stu-id="69f0b-114">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="69f0b-115">必要な作業</span><span class="sxs-lookup"><span data-stu-id="69f0b-115">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="69f0b-116">すべてのテナント ID を一覧表示する</span><span class="sxs-lookup"><span data-stu-id="69f0b-116">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="69f0b-p104">テナントが 500 を超える場合は、コマンドレット構文のスコープを  _-All_ または _-MaxResultsParameter_ に設定します。これは、 **Get-MsolUser** など、出力のサイズが大きいコマンドレットに適用されます。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p104">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="69f0b-119">アクセスできるすべての顧客テナント ID を一覧表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="69f0b-119">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object -TenantId
```

<span data-ttu-id="69f0b-120">これにより、 **テナント ID** 順にすべての顧客テナントが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="69f0b-120">This will display a listing of all your customer tenants by **TenantId**.</span></span>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="69f0b-121">ドメイン名を使用してテナント ID を取得する</span><span class="sxs-lookup"><span data-stu-id="69f0b-121">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="69f0b-p105">ドメイン名によって特定の顧客テナントの **テナント ID** を取得するには、次のコマンドを実行します。 _<domainname.onmicrosoft.com>_ を、目的の顧客テナントの実際のドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object -TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="69f0b-124">テナントのすべてのドメインを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="69f0b-124">List all domains for a tenant</span></span>

<span data-ttu-id="69f0b-p106">任意の 1 つの顧客テナントの全ドメインを取得するには、次のコマンドを実行します。_<customer TenantId value>_ を実際の値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p106">To get all domains for any one customer tenant, run this command. Replace  <customer TenantId value> with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="69f0b-127">追加のドメインを登録した場合、顧客の **テナント ID** と関連付けられたすべてのドメインが返されます。</span><span class="sxs-lookup"><span data-stu-id="69f0b-127">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="69f0b-128">すべてのテナントと登録済みドメインのマッピングを取得する</span><span class="sxs-lookup"><span data-stu-id="69f0b-128">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="69f0b-p107">上記のOffice 365 の Windows PowerShell コマンドでは、テナント ID またはドメインの取得方法を示していましたが、両方同時に取得する方法と、これらの間の明確なマッピングは全く示されていませんでした。このコマンドは、すべての顧客テナント ID とそのドメインの一覧を生成します。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p107">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all. This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="69f0b-131">テナントの全ユーザーを取得する</span><span class="sxs-lookup"><span data-stu-id="69f0b-131">Get all users for a tenant</span></span>

<span data-ttu-id="69f0b-p108">これにより、特定のテナントの全ユーザーの **UserPrincipalName**、**DisplayName**、および **isLicensed** の状態が表示されます。_<customer TenantId value>_ を実際の値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p108">This will display the UserPrincipalName, the DisplayName, and the isLicensed status for all users for a particular tenant.   Replace  <customer TenantId value> with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="69f0b-134">ユーザーに関するすべての詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="69f0b-134">Get all details about a user</span></span>

<span data-ttu-id="69f0b-p109">特定のユーザーのすべてのプロパティを表示する場合は、次のコマンドを実行します。_<customer TenantId value>_ と _<user principal name value>_ を実際の値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p109">If you want to see all the properties of a particular user, run this command.  Replace  <customer TenantId value> and <user principal name value> with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="69f0b-137">ユーザーの追加、オプションの設定、およびライセンスの割り当てを行う</span><span class="sxs-lookup"><span data-stu-id="69f0b-137">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="69f0b-p110">Office 365 ユーザーの一括作成、構成、およびライセンス付与は、Office 365 の Windows PowerShell を使用すると特に効率的です。この 2 段階のプロセスでは、まず追加するすべてのユーザーのエントリをコンマ区切り値 (CSV) ファイルに作成してから、Office 365 の Windows PowerShell を使用してそのファイルをインポートします。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p110">The bulk creation, configuration, and licensing of Office 365 users is particularly efficient by using Windows PowerShell for Office 365. In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="69f0b-140">CSV ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="69f0b-140">Create a CSV file</span></span>

<span data-ttu-id="69f0b-141">次の形式を使用して、CSV ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="69f0b-141">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="69f0b-142">各部分の意味は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="69f0b-142">where:</span></span>
  
- <span data-ttu-id="69f0b-p111">**UsageLocation**: この値は、ユーザーの 2 文字の ISO の国や地域コードです。国や地域コードは、[ISO オンライン参照プラットフォーム](https://go.microsoft.com/fwlink/p/?LinkId=532703)で調べることができます。たとえば、米国のコードは US、ブラジルのコードは BR です。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="69f0b-p112">**LicenseAssignment**:この値には、次の形式を使用します。 `syndication-account:<PROVISIONING_ID>`。たとえば、顧客テナントのユーザーに O365_Business_Premium ライセンスを割り当てている場合、 **LicenseAssignment** の値は **syndication-account:O365_Business_Premium** のようになります。PROVISIONING_ID は、シンジケートまたは CSP パートナーとしてアクセスできるシンジケート パートナー ポータルで確認できます。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="69f0b-149">CSV ファイルをインポートしてユーザーを作成する</span><span class="sxs-lookup"><span data-stu-id="69f0b-149">Import the CSV file and create the users</span></span>

<span data-ttu-id="69f0b-p113">CSV ファイルを作成したら、次のコマンドを実行して、無期限のパスワード付きユーザー アカウントを作成します。このパスワードは、ユーザーが初回サインイン時に変更する必要があり、指定したライセンスを割り当てる必要があります。必ず、正しい CSV ファイル名に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="69f0b-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="69f0b-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="69f0b-152">See also</span></span>

#### 

[<span data-ttu-id="69f0b-153">パートナーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="69f0b-153">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

