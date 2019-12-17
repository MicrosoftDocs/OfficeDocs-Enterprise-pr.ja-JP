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
ms.openlocfilehash: cbf19005ac78599a280ff1dd1b007242731e39db
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072189"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="6150d-103">ユーザー ライセンスを割り当てる間、サービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="6150d-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="6150d-p101">Office 365 サブスクリプションには、個々のサービスのサービス プランが付属します。Office 365 管理者は、ユーザーにライセンスを割り当てるときに特定のプランを無効にしなければならないことが少なくありません。この資料の手順を使用すると、PowerShell を使用して、1 ユーザー アカウントの、または複数のユーザー アカウントの特定のサービス プランを無効にした状態で、Office 365 ライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="6150d-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="6150d-107">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="6150d-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="6150d-108">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="6150d-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="6150d-109">次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="6150d-109">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="6150d-110">次に、ユーザープリンシパル名 (UPN) とも呼ばれるライセンスを追加するアカウントのサインイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="6150d-110">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="6150d-111">次に、有効にするサービスの一覧をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="6150d-111">Next, compile a list of services to enable.</span></span> <span data-ttu-id="6150d-112">ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6150d-112">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="6150d-113">次のコマンドブロックの場合は、ユーザーアカウントのユーザープリンシパル名、SKU パーツ番号、およびサービスプランのリストを入力して、説明テキストと\<文字 > を有効にし、削除します。</span><span class="sxs-lookup"><span data-stu-id="6150d-113">For the command block below, fill in the user principal name of the user account, the SKU part number, and the list of service plans to enable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="6150d-114">次に、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="6150d-114">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="6150d-115">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="6150d-115">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="6150d-116">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="6150d-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="6150d-117">次に、このコマンドを実行して現在のサブスクリプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="6150d-117">Next, run this command to see your current subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="6150d-118">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6150d-118">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="6150d-119">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6150d-119">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="6150d-120">`Get-MsolAccountSku` コマンドの出力に関して次に説明します。</span><span class="sxs-lookup"><span data-stu-id="6150d-120">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="6150d-p105">**AccountSkuId** は、組織のサブスクリプションです。形式は、\<OrganizationName>:\<Subscription> となります。\<OrganizationName> は、Office 365 に登録時に入力した値で、組織の一意の値です。\<Subscription> 値は、特定のサブスクリプションを表します。たとえば、litwareinc:ENTERPRISEPACK の場合、組織名は litwareinc で、サブスクリプション名が ENTERPRISEPACK (Office 365 Enterprise E3) です。</span><span class="sxs-lookup"><span data-stu-id="6150d-p105">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="6150d-125">**ActiveUnits** は、サブスクリプションで購入したライセンス数です。</span><span class="sxs-lookup"><span data-stu-id="6150d-125">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="6150d-126">**WarningUnits** は、まだ更新しておらず、30 日の猶予期間を過ぎると有効期限切れになる、サブスクリプション内のライセンス数です。</span><span class="sxs-lookup"><span data-stu-id="6150d-126">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="6150d-127">**ConsumedUnits** は、このサブスクリプションでユーザーに割り当てたライセンスの数です。</span><span class="sxs-lookup"><span data-stu-id="6150d-127">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="6150d-p106">ライセンスを割り当てるユーザーが含まれる Office 365 サブスクリプションの AccountSkuId をメモに取ります。また、割り当てる十分な数のライセンスがあることも確認します ( **ActiveUnits** から **ConsumedUnits** を減算します)。</span><span class="sxs-lookup"><span data-stu-id="6150d-p106">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="6150d-130">次に、以下のコマンドを実行して、使用しているすべてのサブスクリプションで利用できる Office 365 サービス プランの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="6150d-130">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="6150d-131">このコマンドの出力に基づいて、ユーザーにライセンスを割り当てるときに無効にするサービス プランを判別します。</span><span class="sxs-lookup"><span data-stu-id="6150d-131">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="6150d-132">サービス プランの一覧の一部と、対応する Office 365 サービスを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6150d-132">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="6150d-133">次の表は、Office 365 のサービス プランと最も一般的なサービスのフレンドリ名を示します。</span><span class="sxs-lookup"><span data-stu-id="6150d-133">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="6150d-134">実際のサービス プランの一覧とは、異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6150d-134">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="6150d-135">**サービス プラン**</span><span class="sxs-lookup"><span data-stu-id="6150d-135">**Service plan**</span></span>|<span data-ttu-id="6150d-136">**説明**</span><span class="sxs-lookup"><span data-stu-id="6150d-136">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="6150d-137">Sway</span><span class="sxs-lookup"><span data-stu-id="6150d-137">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="6150d-138">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6150d-138">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="6150d-139">Yammer</span><span class="sxs-lookup"><span data-stu-id="6150d-139">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="6150d-140">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="6150d-140">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="6150d-141">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="6150d-141">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="6150d-142">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="6150d-142">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="6150d-143">事業所</span><span class="sxs-lookup"><span data-stu-id="6150d-143">Office</span></span>   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="6150d-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6150d-144">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="6150d-145">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="6150d-145">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="6150d-146">ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6150d-146">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="6150d-147">この時点で、AccountSkuId と無効にするサービス プランが決まったため、1 ユーザーまたは複数ユーザーにライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="6150d-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="6150d-148">単一ユーザーの場合</span><span class="sxs-lookup"><span data-stu-id="6150d-148">For a single user</span></span>

<span data-ttu-id="6150d-p108">単一ユーザーの場合、そのユーザー アカウントのユーザー プリンシパル名、AccountSkuId、無効にするサービス プランの一覧を入力し、説明テキスト、\< 記号、> 記号を削除します。次に、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="6150d-p108">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
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

<span data-ttu-id="6150d-151">コマンド ブロックの例を以下に示します。アカウント名は belindan@contoso.com で、ライセンスは contoso:ENTERPRISEPACK であり、RMS_S_ENTERPRISE、SWAY、INTUNE_O365、YAMMER_ENTERPRISE の各サービス プランを無効にします。</span><span class="sxs-lookup"><span data-stu-id="6150d-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```powershell
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

### <a name="for-multiple-users"></a><span data-ttu-id="6150d-152">複数ユーザーの場合</span><span class="sxs-lookup"><span data-stu-id="6150d-152">For multiple users</span></span>

<span data-ttu-id="6150d-p109">この管理タスクを複数ユーザーに実行するには、UserPrincipalName フィールドと UsageLocation フィールドが含まれるコンマ区切り値 (CSV) テキスト ファイルを作成します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6150d-p109">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="6150d-155">その後、入力および出力の各 CSV ファイルの場所、アカウント SKU ID、無効にするサービス プランの一覧を入力し、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="6150d-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
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

<span data-ttu-id="6150d-156">この PowerShell コマンド ブロックは以下の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="6150d-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="6150d-157">各ユーザーのユーザー プリンシパル名を表示します。</span><span class="sxs-lookup"><span data-stu-id="6150d-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="6150d-158">各ユーザーにカスタマイズされたライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6150d-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="6150d-159">処理されたすべてのユーザーが含まれる CSV ファイルを作成し、そのライセンス状態を示します。</span><span class="sxs-lookup"><span data-stu-id="6150d-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="6150d-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="6150d-160">See also</span></span>

[<span data-ttu-id="6150d-161">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="6150d-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="6150d-162">Office 365 PowerShell を使った Sway へのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="6150d-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="6150d-163">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="6150d-163">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="6150d-164">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="6150d-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

