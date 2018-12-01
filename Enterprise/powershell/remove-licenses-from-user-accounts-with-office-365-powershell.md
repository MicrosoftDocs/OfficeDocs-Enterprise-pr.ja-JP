---
title: Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
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
ms.openlocfilehash: a993737f4bd1186a7fb5beb7fa0f6a2ae6782618
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123304"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d20cb-103">Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="d20cb-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d20cb-104">**概要:** Office 365 PowerShell を使用して、ユーザーに割り当てられている Office 365 ライセンスを削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d20cb-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="d20cb-105">Before you begin</span></span>

- <span data-ttu-id="d20cb-p101">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d20cb-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="d20cb-108">組織の計画 (**AccountSkuID** ) のライセンス情報を表示するには、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d20cb-108">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="d20cb-109">Office 365 PowerShell でライセンスとサービスを確認する</span><span class="sxs-lookup"><span data-stu-id="d20cb-109">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="d20cb-110">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="d20cb-110">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
- <span data-ttu-id="d20cb-111">_-All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="d20cb-111">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="d20cb-112">ユーザー アカウントからライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-112">Removing licenses from user accounts</span></span>

<span data-ttu-id="d20cb-113">既存のユーザー アカウントからライセンスを削除するには、次の構文を使用します:</span><span class="sxs-lookup"><span data-stu-id="d20cb-113">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="d20cb-114">次の例では、ユーザー アカウント BelindaN@litwareinc.com から  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-114">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="d20cb-115">ライセンス付与済みの既存のユーザーのグループからライセンスを削除するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-115">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="d20cb-116">**既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-116">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="d20cb-117">この例では、米国内の販売部門のユーザーのすべてのアカウントから  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-117">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="d20cb-118">**特定のアカウントの一覧を使用する** これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-118">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="d20cb-119">次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成し、保存します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-119">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="d20cb-120">次の構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d20cb-120">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
  ```

<span data-ttu-id="d20cb-121">この例では、テキスト ファイル C:\My Documents\Accounts.txt で定義されているユーザー アカウントから `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  ```

<span data-ttu-id="d20cb-122">既存のすべてのユーザー アカウントからライセンスを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-122">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="d20cb-123">次の例では、ライセンスを付与された既存の全ユーザー アカウントから  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="d20cb-123">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="d20cb-p102">別の方法として、ユーザー アカウントを削除してライセンスを解放することもできます。詳細については、「[Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d20cb-p102">Another way to free up a license is by deleting the user account. For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d20cb-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="d20cb-126">See also</span></span>

<span data-ttu-id="d20cb-127">Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d20cb-127">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="d20cb-128">Office 365 PowerShell を使用してユーザー アカウントを作成する</span><span class="sxs-lookup"><span data-stu-id="d20cb-128">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d20cb-129">Office 365 PowerShell を使用したユーザー アカウントの削除と復元</span><span class="sxs-lookup"><span data-stu-id="d20cb-129">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d20cb-130">Office 365 PowerShell でユーザー アカウントをブロックする</span><span class="sxs-lookup"><span data-stu-id="d20cb-130">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d20cb-131">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="d20cb-131">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="d20cb-132">これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d20cb-132">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="d20cb-133">Get-Content</span><span class="sxs-lookup"><span data-stu-id="d20cb-133">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="d20cb-134">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="d20cb-134">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="d20cb-135">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="d20cb-135">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="d20cb-136">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="d20cb-136">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="d20cb-137">Where-Object</span><span class="sxs-lookup"><span data-stu-id="d20cb-137">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
## <a name="new-to-office-365"></a><span data-ttu-id="d20cb-138">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="d20cb-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

