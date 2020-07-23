---
title: PowerShell を使用して Microsoft 365 アカウントのライセンスとサービスの詳細を表示する
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
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: PowerShell を使用して、ユーザーに割り当てられている Microsoft 365 サービスを確認する方法について説明します。
ms.openlocfilehash: 73af2fd40df8b36507250edcef48359e9d555a7f
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230243"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a><span data-ttu-id="9231a-103">PowerShell を使用して Microsoft 365 アカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="9231a-103">View Microsoft 365 account license and service details with PowerShell</span></span>

<span data-ttu-id="9231a-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="9231a-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="9231a-105">Microsoft 365 では、ライセンスプラン (Sku または Microsoft 365 プランとも呼ばれます) からのライセンスで、これらのプランに対して定義されている Microsoft 365 サービスへのアクセス権をユーザーに付与します。</span><span class="sxs-lookup"><span data-stu-id="9231a-105">In Microsoft 365, licenses from licensing plans (also called SKUs or Microsoft 365 plans) give users access to the Microsoft 365 services that are defined for those plans.</span></span> <span data-ttu-id="9231a-106">しかし、ユーザーは、現在割り当てられているライセンスで使用可能なすべてのサービスにアクセスできるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="9231a-106">However, a user might not have access to all the services that are available in a license that's currently assigned to them.</span></span> <span data-ttu-id="9231a-107">Microsoft 365 の PowerShell を使用して、ユーザーアカウントのサービスの状態を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9231a-107">You can use PowerShell for Microsoft 365 to view the status of services on user accounts.</span></span> 

<span data-ttu-id="9231a-108">ライセンスプラン、ライセンス、およびサービスの詳細については、「 [PowerShell を使用してライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9231a-108">For more information about licensing plans, license, and services, see [View licenses and services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="9231a-109">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="9231a-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="9231a-110">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="9231a-110">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="9231a-111">次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9231a-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="9231a-112">各ライセンスプランで利用可能なサービスを一覧表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9231a-112">Use these commands to list the services that are available in each licensing plan.</span></span>

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

<span data-ttu-id="9231a-113">ユーザーアカウントに割り当てられているライセンスの一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9231a-113">Use these commands to list the licenses that are assigned to a user account.</span></span>

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="9231a-114">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="9231a-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="9231a-115">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="9231a-115">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="9231a-116">次に、このコマンドを実行して、組織で使用可能なライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9231a-116">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```powershell
Get-MsolAccountSku
```
>[!Note]
><span data-ttu-id="9231a-117">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9231a-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="9231a-118">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9231a-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="9231a-119">次に、このコマンドを実行して、各ライセンスプランで使用可能なサービスと、それらが表示される順序 (インデックス番号) を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9231a-119">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
<span data-ttu-id="9231a-120">このコマンドを使用して、ユーザーに割り当てられているライセンスと、ユーザーが表示される順序 (インデックス番号) を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9231a-120">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="9231a-121">ユーザーアカウントのサービスを表示するには</span><span class="sxs-lookup"><span data-stu-id="9231a-121">To view services for a user account</span></span>

<span data-ttu-id="9231a-122">ユーザーがアクセスできるすべての Microsoft 365 サービスを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9231a-122">To view all the Microsoft 365 services that a user has access to, use the following syntax:</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="9231a-123">この例では、ユーザー BelindaN@litwareinc.com がアクセスできるサービスを表示します。</span><span class="sxs-lookup"><span data-stu-id="9231a-123">This example shows the services to which the user BelindaN@litwareinc.com has access.</span></span> <span data-ttu-id="9231a-124">これにより、このユーザーのアカウントに割り当てられているすべてのライセンスに関連付けられているサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9231a-124">This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="9231a-125">次の例では、ユーザー BelindaN@litwareinc.com が、アカウントに割り当てられている最初のライセンス (インデックス番号 0) からアクセスできるサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9231a-125">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="9231a-126">*複数のライセンス*が割り当てられているユーザーのすべてのサービスを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="9231a-126">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a><span data-ttu-id="9231a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="9231a-127">See also</span></span>

[<span data-ttu-id="9231a-128">PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="9231a-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="9231a-129">PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="9231a-129">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9231a-130">Microsoft 365 の PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="9231a-130">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
