---
title: Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: office 365 PowerShell を使用して、ユーザーに割り当てられている office 365 サービスを確認する方法について説明します。
ms.openlocfilehash: 113107df75880a21210991d5b301245d75c5c739
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "30052971"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a><span data-ttu-id="54222-103">Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する</span><span class="sxs-lookup"><span data-stu-id="54222-103">View account license and service details with Office 365 PowerShell</span></span>

<span data-ttu-id="54222-104">**概要:** office 365 PowerShell を使用して、ユーザーに割り当てられている office 365 サービスを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="54222-104">**Summary:** Explains how to use Office 365 PowerShell to determine the Office 365 services that have been assigned to users.</span></span>
  
<span data-ttu-id="54222-p101">office 365 のライセンスプラン (sku または Office 365 プランとも呼ばれます) からのライセンスでは、これらのプランに対して定義されている Office 365 サービスへのアクセス権がユーザーに付与されます。ただし、ユーザーには、現在割り当てられているライセンスで利用可能なすべてのサービスへのアクセス権がない可能性があります。Office 365 PowerShell を使用して、ユーザーアカウントのサービスの状態を表示できます。</span><span class="sxs-lookup"><span data-stu-id="54222-p101">In Office 365, licenses from licensing plans (also called SKUs or Office 365 plans) give users access to the Office 365 services that are defined for those plans. However, a user might not have access to all the services that are available in a license that's currently assigned to them. You can use Office 365 PowerShell to view the status of services on user accounts.</span></span> 

<span data-ttu-id="54222-108">ライセンスプラン、ライセンス、およびサービスの詳細については、「 [Office 365 PowerShell でライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54222-108">For more information about licensing plans, license, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="54222-109">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="54222-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="54222-110">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="54222-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="54222-111">次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="54222-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="54222-112">各ライセンスプランで利用可能なサービスを一覧表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="54222-112">Use these commands to list the services that are available in each licensing plan.</span></span>

```
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
````

<span data-ttu-id="54222-113">ユーザーアカウントに割り当てられているライセンスの一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="54222-113">Use these commands to list the licenses that are assigned to a user account.</span></span>

````
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
````

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="54222-114">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="54222-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="54222-115">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="54222-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="54222-116">次に、このコマンドを実行して、組織で使用可能なライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="54222-116">Next, run this command to list the licensing plans that are available in your organization.</span></span> 

```
Get-MsolAccountSku
```

<span data-ttu-id="54222-117">次に、このコマンドを実行して、各ライセンスプランで使用可能なサービスと、それらが表示される順序 (インデックス番号) を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="54222-117">Next, run this command to list the services that are available in each licensing plan, and the order in which they are listed (the index number).</span></span>

````
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
````
  
<span data-ttu-id="54222-118">このコマンドを使用して、ユーザーに割り当てられているライセンスと、ユーザーが表示される順序 (インデックス番号) を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="54222-118">Use this command to list the licenses that are assigned to a user, and the order in which they are listed (the index number).</span></span>

````
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
````

>[!Note]
><span data-ttu-id="54222-119">_All_ パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="54222-119">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
>
   

### <a name="to-view-services-for-a-user-account"></a><span data-ttu-id="54222-120">ユーザーアカウントのサービスを表示するには</span><span class="sxs-lookup"><span data-stu-id="54222-120">To view services for a user account</span></span>

<span data-ttu-id="54222-121">ユーザーがアクセスできるすべての Office 365 サービスを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="54222-121">To view all the Office 365 services that a user has access to, use the following syntax:</span></span>
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

<span data-ttu-id="54222-p102">この例では、ユーザー BelindaN@litwareinc.com がアクセスできるサービスを表示します。これにより、自分のアカウントに割り当てられているすべてのライセンスに関連付けられているサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54222-p102">This example shows the services to which the user BelindaN@litwareinc.com has access. This shows the services that are associated with all licenses that are assigned to her account.</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

<span data-ttu-id="54222-124">次の例では、ユーザー BelindaN@litwareinc.com が、アカウントに割り当てられている最初のライセンス (インデックス番号 0) からアクセスできるサービスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54222-124">This example shows the services that user BelindaN@litwareinc.com has access to from the first license that's assigned to her account (the index number is 0).</span></span>
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

<span data-ttu-id="54222-125">*複数のライセンス*が割り当てられているユーザーのすべてのサービスを表示するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="54222-125">To view all the services for a user who has been assigned *multiple licenses*, use the following syntax:</span></span>

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="new-to-office-365"></a><span data-ttu-id="54222-126">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="54222-126">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="54222-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="54222-127">See also</span></span>

[<span data-ttu-id="54222-128">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="54222-128">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="54222-129">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="54222-129">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="54222-130">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="54222-130">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
