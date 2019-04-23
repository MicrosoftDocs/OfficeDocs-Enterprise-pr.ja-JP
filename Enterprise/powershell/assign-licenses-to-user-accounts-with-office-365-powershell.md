---
title: Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。
ms.openlocfilehash: ac2cdb8c303cacc5c9664b877ba86a5b196432b1
ms.sourcegitcommit: 51f9e89e4b9d54f92ef5c70468bda96e664b8a6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "31957648"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8aab8-103">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="8aab8-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8aab8-104">**概要:** Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="8aab8-105">ユーザーがライセンスプランからライセンスを割り当てられるまで、どの Office 365 サービスも使用できません。</span><span class="sxs-lookup"><span data-stu-id="8aab8-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="8aab8-106">Office 365 PowerShell を使用して、ライセンスのないアカウントにライセンスをすばやく割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="8aab8-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8aab8-107">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="8aab8-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8aab8-108">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="8aab8-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="8aab8-109">次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="8aab8-110">次に、ユーザープリンシパル名 (UPN) とも呼ばれるライセンスを追加するアカウントのサインイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="8aab8-111">最後に、ユーザーのサインイン名とライセンスプラン名を指定し、これらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8aab8-112">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="8aab8-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8aab8-113">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="8aab8-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="8aab8-114">**get-msolaccountsku**コマンドを実行して、使用可能なライセンスプランと、組織内の各プランの使用可能なライセンスの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-114">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="8aab8-115">各プランで利用可能なライセンスの数は、 **ActiveUnits** - **WarningUnits** - **ConsumedUnits** です。</span><span class="sxs-lookup"><span data-stu-id="8aab8-115">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="8aab8-116">ライセンスプラン、ライセンス、およびサービスの詳細については、「 [Office 365 PowerShell でライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aab8-116">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="8aab8-117">組織内のライセンスのないアカウントを検索するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="8aab8-118">ライセンスは、有効な ISO 3166-1 国コードに設定\*\*\*\* されているユーザーアカウントにのみ割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="8aab8-118">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="8aab8-119">たとえば、米国は US、フランスは FR です。</span><span class="sxs-lookup"><span data-stu-id="8aab8-119">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="8aab8-120">一部の Office 365 サービスは特定の国では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8aab8-120">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="8aab8-121">詳細については、「[ライセンス制限につい](https://go.microsoft.com/fwlink/p/?LinkId=691730)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aab8-121">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="8aab8-122">利用**場所**の値を持たないアカウントを検索するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="8aab8-123">アカウントに対し\*\*\*\* て、使い方の値を設定するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="8aab8-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="8aab8-125">**-All** パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="8aab8-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="8aab8-126">ユーザーアカウントへのライセンスの割り当て</span><span class="sxs-lookup"><span data-stu-id="8aab8-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="8aab8-127">ユーザーにライセンスを割り当てるには、Office 365 PowerShell で次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="8aab8-128">この例では、ライセンスを**litwareinc: enterprisepack** (Office 365 Enterprise E3) ライセンスプランからライセンスのないユーザー **belindan@litwareinc.com**に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8aab8-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="8aab8-129">ライセンスをライセンスのない複数のユーザーに割り当てるには、このコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="8aab8-130">複数のライセンスを同じライセンス プランのユーザーに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="8aab8-130">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="8aab8-131">十分な数の利用可能なライセンスをお持ちでない場合は、使用可能なライセンスがなくなるまで、ライセンスは **Get-MsolUser** コマンドレットによって返される順序でユーザーに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8aab8-131">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="8aab8-132">この例では、ライセンスを**litwareinc: enterprisepack** (Office 365 Enterprise E3) ライセンスプランからすべてのライセンスのないユーザーに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8aab8-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="8aab8-133">この例では、米国内の販売部門のライセンスのないユーザーに同じライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8aab8-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="8aab8-134">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="8aab8-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="8aab8-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="8aab8-135">See also</span></span>

[<span data-ttu-id="8aab8-136">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="8aab8-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8aab8-137">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="8aab8-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8aab8-138">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="8aab8-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
