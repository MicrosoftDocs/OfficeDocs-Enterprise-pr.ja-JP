---
title: ユーザーライセンスの割り当て中に Microsoft 365 サービスへのアクセスを無効にする
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Microsoft 365 で PowerShell を使用して、ユーザーアカウントにライセンスを割り当て、特定のサービスプランを無効にする方法について説明します。
ms.openlocfilehash: 31199fa2fa61ec5da671da5def2bf648a07e7dd4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230693"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a><span data-ttu-id="5ea61-103">ユーザーライセンスの割り当て中に Microsoft 365 サービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="5ea61-103">Disable access to Microsoft 365 services while assigning user licenses</span></span>

<span data-ttu-id="5ea61-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="5ea61-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="5ea61-105">Microsoft 365 サブスクリプションには、個々のサービスのサービスプランが付属しています。</span><span class="sxs-lookup"><span data-stu-id="5ea61-105">Microsoft 365 subscriptions come with service plans for individual services.</span></span> <span data-ttu-id="5ea61-106">Microsoft 365 管理者は、ユーザーにライセンスを割り当てるときに、特定のプランを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ea61-106">Microsoft 365 administrators often need to disable certain plans when assigning licenses to users.</span></span> <span data-ttu-id="5ea61-107">この記事の手順に従って、個々のユーザーアカウントまたは複数のユーザーアカウントに対して PowerShell を使用して特定のサービスプランを無効にしながら、Microsoft 365 ライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="5ea61-107">With the instructions in this article, you can assign a Microsoft 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5ea61-108">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="5ea61-108">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5ea61-109">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-109">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="5ea61-110">次に、このコマンドを使用して、テナントのライセンスプランを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-110">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="5ea61-111">次に、ユーザープリンシパル名 (UPN) とも呼ばれるライセンスを追加するアカウントのサインイン名を取得します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-111">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="5ea61-112">次に、有効にするサービスの一覧をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="5ea61-112">Next, compile a list of services to enable.</span></span> <span data-ttu-id="5ea61-113">ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ea61-113">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>

<span data-ttu-id="5ea61-114">次のコマンドブロックの場合は、ユーザーアカウントのユーザープリンシパル名、SKU パーツ番号、およびサービスプランのリストを入力して、説明テキストと文字を有効にし、削除し \< and > ます。</span><span class="sxs-lookup"><span data-stu-id="5ea61-114">For the command block below, fill in the user principal name of the user account, the SKU part number, and the list of service plans to enable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="5ea61-115">次に、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-115">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5ea61-116">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="5ea61-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5ea61-117">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-117">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="5ea61-118">次に、このコマンドを実行して現在のサブスクリプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-118">Next, run this command to see your current subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku
```

>[!Note]
><span data-ttu-id="5ea61-119">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5ea61-119">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="5ea61-120">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ea61-120">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="5ea61-121">`Get-MsolAccountSku` コマンドの出力に関して次に説明します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-121">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="5ea61-122">**AccountSkuId**は、組織のサブスクリプションの \<OrganizationName> \<Subscription> 形式です。</span><span class="sxs-lookup"><span data-stu-id="5ea61-122">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format.</span></span> <span data-ttu-id="5ea61-123">\<OrganizationName>は、Microsoft 365 に登録したときに指定した値で、組織に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="5ea61-123">The \<OrganizationName> is the value that you provided when you enrolled in Microsoft 365, and is unique for your organization.</span></span> <span data-ttu-id="5ea61-124">この \<Subscription> 値は、特定のサブスクリプションのためのものです。</span><span class="sxs-lookup"><span data-stu-id="5ea61-124">The \<Subscription> value is for a specific subscription.</span></span> <span data-ttu-id="5ea61-125">たとえば、litwareinc: ENTERPRISEPACK の場合、組織名は litwareinc で、サブスクリプション名は ENTERPRISEPACK (Office 365 Enterprise E3) になります。</span><span class="sxs-lookup"><span data-stu-id="5ea61-125">For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="5ea61-126">**ActiveUnits** は、サブスクリプションで購入したライセンス数です。</span><span class="sxs-lookup"><span data-stu-id="5ea61-126">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="5ea61-127">**WarningUnits** は、まだ更新しておらず、30 日の猶予期間を過ぎると有効期限切れになる、サブスクリプション内のライセンス数です。</span><span class="sxs-lookup"><span data-stu-id="5ea61-127">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="5ea61-128">**ConsumedUnits** は、このサブスクリプションでユーザーに割り当てたライセンスの数です。</span><span class="sxs-lookup"><span data-stu-id="5ea61-128">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="5ea61-129">ライセンスを付与するユーザーを含む Microsoft 365 サブスクリプションの AccountSkuId に注意してください。</span><span class="sxs-lookup"><span data-stu-id="5ea61-129">Note the AccountSkuId for your Microsoft 365 subscription that contains the users you want to license.</span></span> <span data-ttu-id="5ea61-130">また、割り当てに十分なライセンスがあることを確認してください ( **Activeunits**から**ConsumedUnits**を差し引く)。</span><span class="sxs-lookup"><span data-stu-id="5ea61-130">Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="5ea61-131">次に、次のコマンドを実行して、すべてのサブスクリプションで利用可能な Microsoft 365 サービスプランの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-131">Next, run this command to see the details about the Microsoft 365 service plans that are available in all your subscriptions:</span></span>
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="5ea61-132">このコマンドの出力に基づいて、ユーザーにライセンスを割り当てるときに無効にするサービス プランを判別します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-132">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="5ea61-133">ここでは、サービスプランと、それに対応する Microsoft 365 サービスの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-133">Here is a partial list of service plans and their corresponding Microsoft 365 services.</span></span>

<span data-ttu-id="5ea61-134">次の表に、最も一般的なサービスの Microsoft 365 サービスプランとそのフレンドリ名を示します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-134">The following table shows the Microsoft 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="5ea61-135">実際のサービス プランの一覧とは、異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5ea61-135">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="5ea61-136">**サービス プラン**</span><span class="sxs-lookup"><span data-stu-id="5ea61-136">**Service plan**</span></span>|<span data-ttu-id="5ea61-137">**説明**</span><span class="sxs-lookup"><span data-stu-id="5ea61-137">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="5ea61-138">Sway</span><span class="sxs-lookup"><span data-stu-id="5ea61-138">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="5ea61-139">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5ea61-139">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="5ea61-140">Yammer</span><span class="sxs-lookup"><span data-stu-id="5ea61-140">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="5ea61-141">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="5ea61-141">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="5ea61-142">Microsoft 365 enterprise 用アプリ *(旧称 Office 365 ProPlus)*</span><span class="sxs-lookup"><span data-stu-id="5ea61-142">Microsoft 365 Apps for enterprise *(previously named Office 365 ProPlus)*</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="5ea61-143">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="5ea61-143">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="5ea61-144">Office</span><span class="sxs-lookup"><span data-stu-id="5ea61-144">Office</span></span>   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="5ea61-145">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5ea61-145">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="5ea61-146">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="5ea61-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="5ea61-147">ライセンスプランの完全な一覧 (製品名とも呼ばれます)、含まれるサービスプラン、およびそれに対応するフレンドリ名については、「[ライセンスの製品名とサービスプラン識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ea61-147">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="5ea61-148">この時点で、AccountSkuId と無効にするサービス プランが決まったため、1 ユーザーまたは複数ユーザーにライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="5ea61-148">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="5ea61-149">単一ユーザーの場合</span><span class="sxs-lookup"><span data-stu-id="5ea61-149">For a single user</span></span>

<span data-ttu-id="5ea61-150">単一のユーザーの場合は、ユーザーアカウントのユーザープリンシパル名、AccountSkuId、およびサービスプランのリストを入力して、説明テキストと文字を無効にし、削除し \< and > ます。</span><span class="sxs-lookup"><span data-stu-id="5ea61-150">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="5ea61-151">次に、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-151">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

<span data-ttu-id="5ea61-152">コマンド ブロックの例を以下に示します。アカウント名は belindan@contoso.com で、ライセンスは contoso:ENTERPRISEPACK であり、RMS_S_ENTERPRISE、SWAY、INTUNE_O365、YAMMER_ENTERPRISE の各サービス プランを無効にします。</span><span class="sxs-lookup"><span data-stu-id="5ea61-152">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a><span data-ttu-id="5ea61-153">複数ユーザーの場合</span><span class="sxs-lookup"><span data-stu-id="5ea61-153">For multiple users</span></span>

<span data-ttu-id="5ea61-p109">この管理タスクを複数ユーザーに実行するには、UserPrincipalName フィールドと UsageLocation フィールドが含まれるコンマ区切り値 (CSV) テキスト ファイルを作成します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-p109">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="5ea61-156">その後、入力および出力の各 CSV ファイルの場所、アカウント SKU ID、無効にするサービス プランの一覧を入力し、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-156">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="5ea61-157">この PowerShell コマンド ブロックは以下の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="5ea61-157">This PowerShell command block:</span></span>
  
- <span data-ttu-id="5ea61-158">各ユーザーのユーザー プリンシパル名を表示します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-158">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="5ea61-159">各ユーザーにカスタマイズされたライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5ea61-159">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="5ea61-160">処理されたすべてのユーザーが含まれる CSV ファイルを作成し、そのライセンス状態を示します。</span><span class="sxs-lookup"><span data-stu-id="5ea61-160">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="5ea61-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ea61-161">See also</span></span>

[<span data-ttu-id="5ea61-162">PowerShell を使用して Microsoft 365 サービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="5ea61-162">Disable access to Microsoft 365 services with PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="5ea61-163">PowerShell を使用して Sway へのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="5ea61-163">Disable access to Sway with PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="5ea61-164">PowerShell を使用して Microsoft 365 のユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="5ea61-164">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5ea61-165">PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="5ea61-165">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
