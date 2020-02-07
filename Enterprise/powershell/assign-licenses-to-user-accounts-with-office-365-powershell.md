---
title: Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Office 365 PowerShell を使用して、ライセンスのないユーザーに Office 365 ライセンスを割り当てる方法について説明します。
ms.openlocfilehash: 9fbf81db3b942dab90ef214169f197a8fea3f7ed
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841684"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="547f5-103">Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="547f5-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="547f5-104">ユーザーがライセンスプランからライセンスを割り当てられるまで、どの Office 365 サービスも使用できません。</span><span class="sxs-lookup"><span data-stu-id="547f5-104">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="547f5-105">Office 365 PowerShell を使用して、ライセンスのないアカウントにライセンスをすばやく割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="547f5-105">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="547f5-106">ユーザーアカウントには、場所を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="547f5-106">User accounts must be assigned a location.</span></span> <span data-ttu-id="547f5-107">これを行うには、Microsoft 365 管理センターまたは PowerShell からユーザーアカウントのプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="547f5-107">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="547f5-108">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="547f5-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="547f5-109">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="547f5-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="547f5-110">次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="547f5-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="547f5-111">次に、ユーザープリンシパル名 (UPN) とも呼ばれるライセンスを追加するアカウントのサインイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="547f5-111">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="547f5-112">次に、ユーザーアカウントに使用場所が割り当てられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="547f5-112">Next, ensure that the user account has a usage location assigned.</span></span>

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="547f5-113">割り当てられている場所がない場合は、次のコマンドを使用して割り当てを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="547f5-113">If there is no usage location assigned, you can assign one with these commands:</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="547f5-114">最後に、ユーザーのサインイン名とライセンスプラン名を指定し、これらのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="547f5-114">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="547f5-115">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="547f5-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="547f5-116">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="547f5-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="547f5-117">`Get-MsolAccountSku`コマンドを実行して、使用可能なライセンスプランと、組織内の各プランの使用可能なライセンスの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="547f5-117">Run the `Get-MsolAccountSku` command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="547f5-118">各プランで利用可能なライセンスの数は、 **ActiveUnits** - **WarningUnits** - **ConsumedUnits** です。</span><span class="sxs-lookup"><span data-stu-id="547f5-118">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="547f5-119">ライセンスプラン、ライセンス、およびサービスの詳細については、「 [Office 365 PowerShell でライセンスとサービスを表示](view-licenses-and-services-with-office-365-powershell.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="547f5-119">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

>[!Note]
><span data-ttu-id="547f5-120">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="547f5-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="547f5-121">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="547f5-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="547f5-122">組織内のライセンスのないアカウントを検索するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="547f5-122">To find the unlicensed accounts in your organization, run this command.</span></span>

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="547f5-123">ライセンスは、有効な ISO 3166-1 国コードに設定**されて**いるユーザーアカウントにのみ割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="547f5-123">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="547f5-124">たとえば、米国は US、フランスは FR です。</span><span class="sxs-lookup"><span data-stu-id="547f5-124">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="547f5-125">一部の Office 365 サービスは特定の国では使用できません。</span><span class="sxs-lookup"><span data-stu-id="547f5-125">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="547f5-126">詳細については、「[ライセンス制限につい](https://go.microsoft.com/fwlink/p/?LinkId=691730)て」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="547f5-126">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="547f5-127">利用**場所**の値を持たないアカウントを検索するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="547f5-127">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="547f5-128">アカウントに対し**て、使い方の値を**設定するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="547f5-128">To set the **UsageLocation** value on an account, run this command.</span></span>

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="547f5-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="547f5-129">For example:</span></span>

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="547f5-130">**-All** パラメーターなしで **Get-MsolUser** コマンドレットを使用する場合、最初の 500 個のアカウントだけが返されます。</span><span class="sxs-lookup"><span data-stu-id="547f5-130">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="547f5-131">ユーザーアカウントへのライセンスの割り当て</span><span class="sxs-lookup"><span data-stu-id="547f5-131">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="547f5-132">ユーザーにライセンスを割り当てるには、Office 365 PowerShell で次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="547f5-132">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="547f5-133">この例では、ライセンスを**litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスプランから、ライセンスのないユーザー**ベル\@の litwareinc.com**に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="547f5-133">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="547f5-134">ライセンスのないすべてのユーザーにライセンスを割り当てるには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="547f5-134">To assign a license to all unlicensed users, run this command.</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="547f5-135">複数のライセンスを同じライセンス プランのユーザーに割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="547f5-135">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="547f5-136">十分な数の利用可能なライセンスをお持ちでない場合は、使用可能なライセンスがなくなるまで、ライセンスは **Get-MsolUser** コマンドレットによって返される順序でユーザーに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="547f5-136">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="547f5-137">この例では、ライセンスを**litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) ライセンスプランからすべてのライセンスのないユーザーに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="547f5-137">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="547f5-138">この例では、米国内の販売部門のライセンスのないユーザーに同じライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="547f5-138">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="547f5-139">Azure Active Directory PowerShell for Graph モジュールを使用して、ユーザーを別のサブスクリプション (ライセンスプラン) に移動する</span><span class="sxs-lookup"><span data-stu-id="547f5-139">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="547f5-140">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="547f5-140">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="547f5-141">次に、ユーザープリンシパル名 (UPN) とも呼ばれる、サブスクリプションを切り替えたいユーザーアカウントのサインイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="547f5-141">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="547f5-142">次に、このコマンドを使用して、テナントのサブスクリプション (ライセンスプラン) を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="547f5-142">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="547f5-143">次に、ユーザーアカウントがこれらのコマンドで現在持っているサブスクリプションを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="547f5-143">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="547f5-144">ユーザーが現在持っているサブスクリプション (FROM サブスクリプション) と、そのユーザーの移動先のサブスクリプション (TO サブスクリプション) を特定します。</span><span class="sxs-lookup"><span data-stu-id="547f5-144">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="547f5-145">最後に、サブスクリプション名 (SKU パーツ番号) を指定し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="547f5-145">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

<span data-ttu-id="547f5-146">次のコマンドを使用して、ユーザーアカウントのサブスクリプションの変更を確認できます。</span><span class="sxs-lookup"><span data-stu-id="547f5-146">You can verify the change in subscription for the user account with these commands.</span></span>

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a><span data-ttu-id="547f5-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="547f5-147">See also</span></span>

[<span data-ttu-id="547f5-148">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="547f5-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="547f5-149">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="547f5-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="547f5-150">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="547f5-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
