---
title: ユーザー ライセンスを割り当てる間、サービスへのアクセスを無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/27/2019
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Office 365 PowerShell を使い、ユーザー アカウントへのライセンスの割り当てと、特定のサービス プランの無効化を同時に行う方法を説明します。
ms.openlocfilehash: ac356e5cc70ef36ad2e45b84f0dcd9d2252c79a4
ms.sourcegitcommit: 6b4fca7ccdbb7aeadc705d82f1007ac285f27357
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "37282922"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="80012-103">ユーザー ライセンスを割り当てる間、サービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="80012-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="80012-104">**概要:** Office 365 PowerShell を使い、ユーザー アカウントへのライセンスの割り当てと、特定のサービス プランの無効化を同時に行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="80012-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="80012-p101">Office 365 サブスクリプションには、個々のサービスのサービス プランが付属します。Office 365 管理者は、ユーザーにライセンスを割り当てるときに特定のプランを無効にしなければならないことが少なくありません。この資料の手順を使用すると、PowerShell を使用して、1 ユーザー アカウントの、または複数のユーザー アカウントの特定のサービス プランを無効にした状態で、Office 365 ライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="80012-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="80012-108">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="80012-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="80012-109">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="80012-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="80012-110">次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="80012-110">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="80012-111">次に、ユーザープリンシパル名 (UPN) とも呼ばれるライセンスを追加するアカウントのサインイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="80012-111">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="80012-112">次に、有効にするサービスの一覧をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="80012-112">Next, compile a list of services to enable.</span></span> <span data-ttu-id="80012-113">ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80012-113">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="80012-114">次のコマンドブロックの場合は、ユーザーアカウントのユーザープリンシパル名、SKU パーツ番号、およびサービスプランのリストを入力して、説明テキストと\<文字 > を有効にし、削除します。</span><span class="sxs-lookup"><span data-stu-id="80012-114">For the command block below, fill in the user principal name of the user account, the SKU part number, and the list of service plans to enable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="80012-115">次に、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="80012-115">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="80012-116">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="80012-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="80012-117">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="80012-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="80012-118">次に、このコマンドを実行して現在のサブスクリプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="80012-118">Next, run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="80012-119">`Get-MsolAccountSku` コマンドの出力に関して次に説明します。</span><span class="sxs-lookup"><span data-stu-id="80012-119">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="80012-p104">**AccountSkuId** は、組織のサブスクリプションです。形式は、\<OrganizationName>:\<Subscription> となります。\<OrganizationName> は、Office 365 に登録時に入力した値で、組織の一意の値です。\<Subscription> 値は、特定のサブスクリプションを表します。たとえば、litwareinc:ENTERPRISEPACK の場合、組織名は litwareinc で、サブスクリプション名が ENTERPRISEPACK (Office 365 Enterprise E3) です。</span><span class="sxs-lookup"><span data-stu-id="80012-p104">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="80012-124">**ActiveUnits** は、サブスクリプションで購入したライセンス数です。</span><span class="sxs-lookup"><span data-stu-id="80012-124">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="80012-125">**WarningUnits** は、まだ更新しておらず、30 日の猶予期間を過ぎると有効期限切れになる、サブスクリプション内のライセンス数です。</span><span class="sxs-lookup"><span data-stu-id="80012-125">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="80012-126">**ConsumedUnits** は、このサブスクリプションでユーザーに割り当てたライセンスの数です。</span><span class="sxs-lookup"><span data-stu-id="80012-126">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="80012-p105">ライセンスを割り当てるユーザーが含まれる Office 365 サブスクリプションの AccountSkuId をメモに取ります。また、割り当てる十分な数のライセンスがあることも確認します ( **ActiveUnits** から **ConsumedUnits** を減算します)。</span><span class="sxs-lookup"><span data-stu-id="80012-p105">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="80012-129">次に、以下のコマンドを実行して、使用しているすべてのサブスクリプションで利用できる Office 365 サービス プランの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="80012-129">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="80012-130">このコマンドの出力に基づいて、ユーザーにライセンスを割り当てるときに無効にするサービス プランを判別します。</span><span class="sxs-lookup"><span data-stu-id="80012-130">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="80012-131">サービス プランの一覧の一部と、対応する Office 365 サービスを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="80012-131">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="80012-132">次の表は、Office 365 のサービス プランと最も一般的なサービスのフレンドリ名を示します。</span><span class="sxs-lookup"><span data-stu-id="80012-132">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="80012-133">実際のサービス プランの一覧とは、異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="80012-133">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="80012-134">**サービス プラン**</span><span class="sxs-lookup"><span data-stu-id="80012-134">**Service plan**</span></span>|<span data-ttu-id="80012-135">**説明**</span><span class="sxs-lookup"><span data-stu-id="80012-135">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="80012-136">Sway</span><span class="sxs-lookup"><span data-stu-id="80012-136">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="80012-137">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="80012-137">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="80012-138">Yammer</span><span class="sxs-lookup"><span data-stu-id="80012-138">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="80012-139">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="80012-139">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="80012-140">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="80012-140">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="80012-141">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="80012-141">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="80012-142">Office</span><span class="sxs-lookup"><span data-stu-id="80012-142">Office</span></span>   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="80012-143">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="80012-143">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="80012-144">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="80012-144">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="80012-145">ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80012-145">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="80012-146">この時点で、AccountSkuId と無効にするサービス プランが決まったため、1 ユーザーまたは複数ユーザーにライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="80012-146">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="80012-147">単一ユーザーの場合</span><span class="sxs-lookup"><span data-stu-id="80012-147">For a single user</span></span>

<span data-ttu-id="80012-p107">単一ユーザーの場合、そのユーザー アカウントのユーザー プリンシパル名、AccountSkuId、無効にするサービス プランの一覧を入力し、説明テキスト、\< 記号、> 記号を削除します。次に、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="80012-p107">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="80012-150">コマンド ブロックの例を以下に示します。アカウント名は belindan@contoso.com で、ライセンスは contoso:ENTERPRISEPACK であり、RMS_S_ENTERPRISE、SWAY、INTUNE_O365、YAMMER_ENTERPRISE の各サービス プランを無効にします。</span><span class="sxs-lookup"><span data-stu-id="80012-150">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

### <a name="for-multiple-users"></a><span data-ttu-id="80012-151">複数ユーザーの場合</span><span class="sxs-lookup"><span data-stu-id="80012-151">For multiple users</span></span>

<span data-ttu-id="80012-p108">この管理タスクを複数ユーザーに実行するには、UserPrincipalName フィールドと UsageLocation フィールドが含まれるコンマ区切り値 (CSV) テキスト ファイルを作成します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="80012-p108">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="80012-154">その後、入力および出力の各 CSV ファイルの場所、アカウント SKU ID、無効にするサービス プランの一覧を入力し、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="80012-154">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="80012-155">この PowerShell コマンド ブロックは以下の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="80012-155">This PowerShell command block:</span></span>
  
- <span data-ttu-id="80012-156">各ユーザーのユーザー プリンシパル名を表示します。</span><span class="sxs-lookup"><span data-stu-id="80012-156">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="80012-157">各ユーザーにカスタマイズされたライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="80012-157">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="80012-158">処理されたすべてのユーザーが含まれる CSV ファイルを作成し、そのライセンス状態を示します。</span><span class="sxs-lookup"><span data-stu-id="80012-158">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="80012-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="80012-159">See also</span></span>

[<span data-ttu-id="80012-160">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="80012-160">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="80012-161">Office 365 PowerShell を使った Sway へのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="80012-161">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="80012-162">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="80012-162">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="80012-163">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="80012-163">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

