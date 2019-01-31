---
title: Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる
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
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。
ms.openlocfilehash: ab9b66065e20d0c2d6cfb673dac24ee2ab79e831
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651183"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8f7a4-103">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="8f7a4-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8f7a4-104">**概要:** Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-104">**Summary:**  Explains how to use Office 365 PowerShell assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="8f7a4-p101">ユーザーは、自分のアカウントは、ライセンスが割り当てられてライセンス プランからまで、すべての Office 365 サービスを使用できません。簡単にライセンスのないアカウントにライセンスを割り当てるには、Office 365 の PowerShell を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-p101">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan. You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8f7a4-107">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="8f7a4-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8f7a4-108">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="8f7a4-109">次に、ライセンスの一覧は、このコマンドを使用して、テナントの予定です。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-109">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="8f7a4-110">次に、ライセンスとも呼ばれるユーザー プリンシパル名 (UPN) を追加するアカウントのサインイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="8f7a4-111">最後に、ユーザーのサインイン名とライセンス プランの名前を指定し、これらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-111">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8f7a4-112">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="8f7a4-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8f7a4-113">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="8f7a4-p102">それぞれの計画、組織内で使用可能なライセンス プランと利用可能なライセンスの数を表示するのには、 **Get MsolAccountSku**コマンドを実行します。各プランで利用可能なライセンスの数は、 **ActiveUnits** - **WarningUnits** - **ConsumedUnits**。計画、ライセンス、およびサービスのライセンスの詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-p102">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization. The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="8f7a4-117">組織のライセンスのないアカウントを検索するには、このコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-117">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```
    
<span data-ttu-id="8f7a4-p103">**UsageLocation**プロパティが有効な ISO 3166-1 アルファ 2 国コードに設定されているユーザー アカウントにライセンスを割り当てることだけできます。たとえば、アメリカ合衆国およびフランスの FR のことです。いくつかの Office 365 サービスは、特定の国では使用できません。詳細については、[ライセンスによる使用制限の詳細](https://go.microsoft.com/fwlink/p/?LinkId=691730)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-p103">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code. For example, US for the United States, and FR for France. Some Office 365 services aren't available in certain countries. For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="8f7a4-122">**UsageLocation**の値を持たないアカウントを検索するには、このコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-122">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="8f7a4-123">アカウントの**UsageLocation**値を設定するには、このコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-123">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="8f7a4-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-124">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="8f7a4-125">**-All** パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-125">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="8f7a4-126">ユーザー アカウントにライセンスを割り当てる</span><span class="sxs-lookup"><span data-stu-id="8f7a4-126">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="8f7a4-127">ライセンスをユーザーに割り当てるには、Office 365 の PowerShell で次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-127">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="8f7a4-128">次の使用例は、 **litwareinc:ENTERPRISEPACK** (Office 365 エンタープライズ E3) ライセンスのライセンスのないユーザーの**belindan@litwareinc.com**するための計画からライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-128">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="8f7a4-129">ライセンスをライセンスのない多くのユーザーに割り当てるには、このコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-129">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | ForEach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```
  
>[!Note]
><span data-ttu-id="8f7a4-p104">同じライセンス プランから、ユーザーに複数のライセンスを割り当てることはできません。十分な利用可能なライセンスをお持ちでない場合は、取り出されると、 **Get MsolUser**コマンドレットで利用可能なライセンスが不足するまでの順序でユーザーにライセンスが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-p104">You can't assign multiple licenses to a user from the same licensing plan. If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="8f7a4-132">次の使用例は、 **litwareinc:ENTERPRISEPACK** (Office 365 エンタープライズ E3) のライセンスについてのすべてのライセンスのないユーザーにライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-132">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="8f7a4-133">この例では、米国内の販売部門でのライセンスのないユーザーに、同じライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-133">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | ForEach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="8f7a4-134">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="8f7a4-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="8f7a4-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f7a4-135">See also</span></span>

[<span data-ttu-id="8f7a4-136">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="8f7a4-136">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8f7a4-137">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="8f7a4-137">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8f7a4-138">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="8f7a4-138">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
