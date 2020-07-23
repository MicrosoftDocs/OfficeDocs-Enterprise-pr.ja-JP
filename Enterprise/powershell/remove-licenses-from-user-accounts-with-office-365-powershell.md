---
title: PowerShell を使用してユーザーアカウントから Microsoft 365 ライセンスを削除する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: PowerShell を使用して、ユーザーに割り当てられていた Microsoft 365 ライセンスを削除する方法について説明します。
ms.openlocfilehash: 5f46cfeb075d83504e3562e60e3dfd70a53dd136
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230393"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a><span data-ttu-id="4b549-103">PowerShell を使用してユーザーアカウントから Microsoft 365 ライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="4b549-103">Remove Microsoft 365 licenses from user accounts with PowerShell</span></span>

<span data-ttu-id="4b549-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="4b549-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="4b549-105">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="4b549-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="4b549-106">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="4b549-106">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="4b549-107">次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="4b549-107">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="4b549-108">次に、ユーザープリンシパル名 (UPN) とも呼ばれるライセンスを削除するアカウントのサインイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="4b549-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="4b549-109">最後に、ユーザーのサインインとライセンスプラン名を指定し、"<" と ">" の文字を削除して、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4b549-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

<span data-ttu-id="4b549-110">特定のユーザーアカウントのすべてのライセンスを削除するには、ユーザーのサインイン名を指定し、"<" と ">" の文字を削除して、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4b549-110">To remove all of the licenses for a specific user account, specify the user sign-in name, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
if($userList -is [array]) {
for ($i=0; $i -lt $userList.Count; $i++) {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList[$i].SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList[$i].SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}
} else {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList.SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList.SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="4b549-111">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="4b549-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="4b549-112">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="4b549-112">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="4b549-113">組織のライセンス プラン (**AccountSkuID**) 情報を表示する方法については、以下のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b549-113">To view the licensing plan (**AccountSkuID**) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="4b549-114">PowerShell を使用してライセンスとサービスを表示する</span><span class="sxs-lookup"><span data-stu-id="4b549-114">View licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="4b549-115">PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="4b549-115">View account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="4b549-116">_-All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="4b549-116">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="4b549-117">ユーザーアカウントからライセンスを削除する</span><span class="sxs-lookup"><span data-stu-id="4b549-117">Removing licenses from user accounts</span></span>

<span data-ttu-id="4b549-118">既存のユーザー アカウントからライセンスを削除するには、次の構文を使用します:</span><span class="sxs-lookup"><span data-stu-id="4b549-118">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="4b549-119">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="4b549-119">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="4b549-120">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b549-120">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="4b549-121">この例では、ユーザーアカウント BelindaN@litwareinc.com から**litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="4b549-121">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="4b549-122">コマンドレットを使用して、 `Set-MsolUserLicense` *取り消さ*れたライセンスからユーザーを割り当て解除することはできません。</span><span class="sxs-lookup"><span data-stu-id="4b549-122">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="4b549-123">この操作は、Microsoft 365 管理センターのユーザーアカウントごとに個別に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b549-123">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="4b549-124">既存のライセンスを持つユーザーのグループからすべてのライセンスを削除するには、次のいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b549-124">To remove all licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="4b549-125">**既存のアカウント属性に基づいてアカウントをフィルターする** これを行うには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b549-125">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="4b549-126">この例では、米国内の販売部門のすべてのユーザーアカウントからすべてのライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="4b549-126">This example removes all licenses from all user accounts in the Sales department in the United States.</span></span>
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- <span data-ttu-id="4b549-127">**特定のライセンスに対して特定のアカウントの一覧を使用**するこれを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4b549-127">**Use a list of specific accounts for a specific license** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="4b549-128">次のように各行に 1 つのアカウントが含まれるテキスト ファイルを作成し、保存します。</span><span class="sxs-lookup"><span data-stu-id="4b549-128">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="4b549-129">次の構文を使用してください。</span><span class="sxs-lookup"><span data-stu-id="4b549-129">Use the following syntax:</span></span>
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
<span data-ttu-id="4b549-130">この例では、テキストファイル C:\My Documents\Accounts.txt で定義されているユーザーアカウントから、 **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスを削除します。</span><span class="sxs-lookup"><span data-stu-id="4b549-130">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

<span data-ttu-id="4b549-131">すべての既存のユーザーアカウントからすべてのライセンスを削除するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="4b549-131">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="4b549-132">別の方法として、ユーザー アカウントを削除してライセンスを解放することもできます。</span><span class="sxs-lookup"><span data-stu-id="4b549-132">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="4b549-133">詳細については、「 [PowerShell を使用してユーザーアカウントを削除および復元](delete-and-restore-user-accounts-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b549-133">For more information, see [Delete and restore user accounts with PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4b549-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b549-134">See also</span></span>

[<span data-ttu-id="4b549-135">PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="4b549-135">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="4b549-136">PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="4b549-136">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4b549-137">Microsoft 365 の PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="4b549-137">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

