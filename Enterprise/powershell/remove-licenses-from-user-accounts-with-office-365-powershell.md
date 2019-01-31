---
title: Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/29/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Office 365 PowerShell を使用して、ユーザーに割り当てられている Office 365 ライセンスを削除する方法について説明します。
ms.openlocfilehash: 5b5f4550a5fade7f95669ad455aebd5d5f7fbf34
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651221"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="ea9ac-103">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="ea9ac-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="ea9ac-104">**概要:** Office 365 PowerShell を使用して、ユーザーに割り当てられている Office 365 ライセンスを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ea9ac-105">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="ea9ac-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ea9ac-106">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="ea9ac-107">次に、ライセンスの一覧は、このコマンドを使用して、テナントの予定です。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-107">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="ea9ac-108">次に、ライセンスとも呼ばれるユーザー プリンシパル名 (UPN) を削除するアカウントのサインイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="ea9ac-109">最後に、ユーザーのサインインとライセンスのプラン名を指定、「_lt _」と"_gt"の文字を削除し、これらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ea9ac-110">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="ea9ac-110">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ea9ac-111">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-111">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

   
<span data-ttu-id="ea9ac-112">組織の計画 (**AccountSkuID** ) のライセンス情報を表示するには、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-112">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="ea9ac-113">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="ea9ac-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="ea9ac-114">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="ea9ac-114">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="ea9ac-115">_-All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-115">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="ea9ac-116">ユーザー アカウントからライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-116">Removing licenses from user accounts</span></span>

<span data-ttu-id="ea9ac-117">既存のユーザー アカウントからライセンスを削除するには、次の構文を使用します:</span><span class="sxs-lookup"><span data-stu-id="ea9ac-117">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="ea9ac-118">この例で削除、 `litwareinc:ENTERPRISEPACK` BelindaN@litwareinc.com のユーザー アカウントからの (Office 365 エンタープライズ E3) のライセンスです。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-118">This example removes the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="ea9ac-119">ライセンス付与済みの既存のユーザーのグループからライセンスを削除するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-119">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="ea9ac-120">**既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-120">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="ea9ac-121">この例では、米国内の販売部門のユーザーのすべてのアカウントから  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="ea9ac-122">**特定のアカウントの一覧を使用する** これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-122">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="ea9ac-123">次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成し、保存します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-123">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="ea9ac-124">次の構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-124">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="ea9ac-125">この例では、テキスト ファイル C:\My Documents\Accounts.txt で定義されているユーザー アカウントから `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-125">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="ea9ac-126">既存のすべてのユーザー アカウントからライセンスを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-126">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="ea9ac-127">次の例では、ライセンスを付与された既存の全ユーザー アカウントから  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-127">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="ea9ac-p101">別の方法として、ユーザー アカウントを削除してライセンスを解放することもできます。詳細については、「[Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-p101">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ea9ac-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea9ac-130">See also</span></span>

[<span data-ttu-id="ea9ac-131">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="ea9ac-131">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ea9ac-132">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="ea9ac-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ea9ac-133">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="ea9ac-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a><span data-ttu-id="ea9ac-134">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="ea9ac-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

