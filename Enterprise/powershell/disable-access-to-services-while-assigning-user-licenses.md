---
title: "ユーザー ライセンスを割り当てる間、サービスへのアクセスを無効にする"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "Office 365 PowerShell を使い、ユーザー アカウントへのライセンスの割り当てと、特定のサービス プランの無効化を同時に行う方法を説明します。"
ms.openlocfilehash: 907314e13b353e5d5ddbcd8fe467db568473d0b3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="528ed-103">ユーザー ライセンスを割り当てる間、サービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="528ed-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="528ed-104">**概要:** Office 365 PowerShell を使い、ユーザー アカウントへのライセンスの割り当てと、特定のサービス プランの無効化を同時に行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="528ed-104">Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="528ed-p101">Office 365 サブスクリプションには、個々のサービスのサービス プランが付属します。Office 365 管理者は、ユーザーにライセンスを割り当てるときに特定のプランを無効にしなければならないことが少なくありません。この資料の手順を使用すると、PowerShell を使用して、1 ユーザー アカウントの、または複数のユーザー アカウントの特定のサービス プランを無効にした状態で、Office 365 ライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="528ed-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="528ed-108">この資料は、Microsoft サポート エスカレーション エンジニアの Siddhartha Parmar の説明に基づいています。</span><span class="sxs-lookup"><span data-stu-id="528ed-108">This article is based on the work of Siddhartha Parmar, a Microsoft Support Escalation Engineer.</span></span> 
  
## <a name="before-you-begin"></a><span data-ttu-id="528ed-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="528ed-109">Before you begin</span></span>

<span data-ttu-id="528ed-p102">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="528ed-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="528ed-112">サブスクリプションとサービス プランに関する情報を収集する</span><span class="sxs-lookup"><span data-stu-id="528ed-112">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="528ed-113">現在のサブスクリプションを確認するため、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="528ed-113">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="528ed-114">`Get-MsolAccountSku` コマンドの出力に関して次に説明します。</span><span class="sxs-lookup"><span data-stu-id="528ed-114">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="528ed-p103">**AccountSkuId** は、組織のサブスクリプションです。形式は、\<OrganizationName>:\<Subscription> となります。\<OrganizationName> は、Office 365 に登録時に入力した値で、組織の一意の値です。\<Subscription> 値は、特定のサブスクリプションを表します。たとえば、litwareinc:ENTERPRISEPACK の場合、組織名は litwareinc で、サブスクリプション名が ENTERPRISEPACK (Office 365 Enterprise E3) です。</span><span class="sxs-lookup"><span data-stu-id="528ed-p103">AccountSkuId is a subscription for your organization in <OrganizationName>:<Subscription> format. The <OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The <Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="528ed-119">**ActiveUnits** は、サブスクリプションで購入したライセンス数です。</span><span class="sxs-lookup"><span data-stu-id="528ed-119">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="528ed-120">**WarningUnits** は、まだ更新しておらず、30 日の猶予期間を過ぎると有効期限切れになる、サブスクリプション内のライセンス数です。</span><span class="sxs-lookup"><span data-stu-id="528ed-120">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="528ed-121">**ConsumedUnits** は、このサブスクリプションでユーザーに割り当てたライセンスの数です。</span><span class="sxs-lookup"><span data-stu-id="528ed-121">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="528ed-p104">ライセンスを割り当てるユーザーが含まれる Office 365 サブスクリプションの AccountSkuId をメモに取ります。また、割り当てる十分な数のライセンスがあることも確認します ( **ActiveUnits** から **ConsumedUnits** を減算します)。</span><span class="sxs-lookup"><span data-stu-id="528ed-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="528ed-124">次に、以下のコマンドを実行して、使用しているすべてのサブスクリプションで利用できる Office 365 サービス プランの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="528ed-124">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="528ed-125">このコマンドの出力に基づいて、ユーザーにライセンスを割り当てるときに無効にするサービス プランを判別します。</span><span class="sxs-lookup"><span data-stu-id="528ed-125">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="528ed-126">サービス プランの一覧の一部と、対応する Office 365 サービスを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="528ed-126">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="528ed-127">**サービス プラン**</span><span class="sxs-lookup"><span data-stu-id="528ed-127">**Service plan**</span></span>|<span data-ttu-id="528ed-128">**説明**</span><span class="sxs-lookup"><span data-stu-id="528ed-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="528ed-129">SWAY</span><span class="sxs-lookup"><span data-stu-id="528ed-129">SWAY</span></span>  <br/> |<span data-ttu-id="528ed-130">Sway</span><span class="sxs-lookup"><span data-stu-id="528ed-130">Sway</span></span>  <br/> |
|<span data-ttu-id="528ed-131">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="528ed-131">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="528ed-132">Office 365 のモバイル デバイス管理</span><span class="sxs-lookup"><span data-stu-id="528ed-132">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="528ed-133">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="528ed-133">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="528ed-134">Yammer</span><span class="sxs-lookup"><span data-stu-id="528ed-134">Yammer</span></span>  <br/> |
|<span data-ttu-id="528ed-135">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="528ed-135">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="528ed-136">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="528ed-136">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="528ed-137">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="528ed-137">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="528ed-138">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="528ed-138">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="528ed-139">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="528ed-139">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="528ed-140">Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="528ed-140">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="528ed-141">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="528ed-141">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="528ed-142">Office Online</span><span class="sxs-lookup"><span data-stu-id="528ed-142">Office Online</span></span>  <br/> |
|<span data-ttu-id="528ed-143">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="528ed-143">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="528ed-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="528ed-144">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="528ed-145">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="528ed-145">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="528ed-146">Exchange Online プラン 2</span><span class="sxs-lookup"><span data-stu-id="528ed-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="528ed-147">この時点で、AccountSkuId と無効にするサービス プランが決まったため、1 ユーザーまたは複数ユーザーにライセンスを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="528ed-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="528ed-148">単一ユーザーの場合</span><span class="sxs-lookup"><span data-stu-id="528ed-148">For a single user</span></span>

<span data-ttu-id="528ed-p105">単一ユーザーの場合、そのユーザー アカウントのユーザー プリンシパル名、AccountSkuId、無効にするサービス プランの一覧を入力し、説明テキスト、\< 記号、> 記号を削除します。次に、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="528ed-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the < and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="528ed-151">コマンド ブロックの例を以下に示します。アカウント名は belindan@contoso.com で、ライセンスは contoso:ENTERPRISEPACK であり、RMS_S_ENTERPRISE、SWAY、INTUNE_O365、YAMMER_ENTERPRISE の各サービス プランを無効にします。</span><span class="sxs-lookup"><span data-stu-id="528ed-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
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

## <a name="for-multiple-users"></a><span data-ttu-id="528ed-152">複数ユーザーの場合</span><span class="sxs-lookup"><span data-stu-id="528ed-152">For multiple users</span></span>

<span data-ttu-id="528ed-p106">この管理タスクを複数ユーザーに実行するには、UserPrincipalName フィールドと UsageLocation フィールドが含まれるコンマ区切り値 (CSV) テキスト ファイルを作成します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="528ed-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="528ed-155">その後、入力および出力の各 CSV ファイルの場所、アカウント SKU ID、無効にするサービス プランの一覧を入力し、完成したコマンドを PowerShell コマンド プロンプトで実行します。</span><span class="sxs-lookup"><span data-stu-id="528ed-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="528ed-156">この PowerShell コマンド ブロックは以下の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="528ed-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="528ed-157">各ユーザーのユーザー プリンシパル名を表示します。</span><span class="sxs-lookup"><span data-stu-id="528ed-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="528ed-158">各ユーザーにカスタマイズされたライセンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="528ed-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="528ed-159">処理されたすべてのユーザーが含まれる CSV ファイルを作成し、そのライセンス状態を示します。</span><span class="sxs-lookup"><span data-stu-id="528ed-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="528ed-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="528ed-160">See also</span></span>

#### 

[<span data-ttu-id="528ed-161">Office 365 PowerShell を使ったサービスへのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="528ed-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="528ed-162">Office 365 PowerShell を使った Sway へのアクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="528ed-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="528ed-163">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="528ed-163">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="528ed-164">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="528ed-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

