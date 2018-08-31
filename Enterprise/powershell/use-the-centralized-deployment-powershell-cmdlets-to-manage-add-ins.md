---
title: 一元的な展開の PowerShell コマンドレットを使用して、アドインを管理するには
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 展開し、Office 365 の組織での Office のアドインを管理するための一元的な展開の PowerShell コマンドレットを使用します。
ms.openlocfilehash: f15bd1048d9240a125a1ae8245c773d83c6c935d
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "22541539"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="3786e-103">一元的な展開の PowerShell コマンドレットを使用して、アドインを管理するには</span><span class="sxs-lookup"><span data-stu-id="3786e-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="3786e-p101">一元的な展開を使用してユーザーに Office のアドインを配置する、Office 365 の管理者として機能の ( [Office 365 の管理センターでの Office 365 のアドインの展開の管理](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)を参照してください)。Office 365 の管理センターを使用して Office のアドインを配置するには、Microsoft の PowerShell を使用することもできます。[ダウンロード](https://go.microsoft.com/fwlink/p/?linkid=850850)Microsoft ダウンロード センターから一元的な展開の PowerShell コマンドレットをします。</span><span class="sxs-lookup"><span data-stu-id="3786e-p101">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the Office 365 admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). In addition to deploying Office add-ins via the Office 365 admin center, you can also use Microsoft PowerShell. [Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="3786e-107">必要な作業</span><span class="sxs-lookup"><span data-stu-id="3786e-107">What do you want to do?</span></span>

[<span data-ttu-id="3786e-108">管理者の資格情報を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="3786e-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="3786e-109">アドイン マニフェストをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="3786e-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="3786e-110">Office ストアからのアップロードします。</span><span class="sxs-lookup"><span data-stu-id="3786e-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="3786e-111">アドインの詳細情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="3786e-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="3786e-112">オンまたはアドインを無効にします。</span><span class="sxs-lookup"><span data-stu-id="3786e-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="3786e-113">追加または削除ユーザーの追加</span><span class="sxs-lookup"><span data-stu-id="3786e-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="3786e-114">アドインを更新します。</span><span class="sxs-lookup"><span data-stu-id="3786e-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="3786e-115">アドインを削除します。</span><span class="sxs-lookup"><span data-stu-id="3786e-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="3786e-116">各コマンドレットの詳細なヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="3786e-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="3786e-117">管理者の資格情報を使用して接続します。</span><span class="sxs-lookup"><span data-stu-id="3786e-117">Connect using your admin credentials</span></span>
<span data-ttu-id="3786e-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="3786e-118"></span></span>

<span data-ttu-id="3786e-119">一元的な展開のコマンドレットを使用できますが、サインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3786e-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="3786e-120">PowerShell を開始します。</span><span class="sxs-lookup"><span data-stu-id="3786e-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="3786e-p102">PowerShell に接続するには、会社の管理者の資格情報を使用します。次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3786e-p102">Connect to PowerShell by using your company admin credentials. Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="3786e-p103">**資格情報の入力**」ページで、Office 365 グローバル管理者の資格情報を入力します。代わりに、コマンドレットに直接資格情報を入力できます。</span><span class="sxs-lookup"><span data-stu-id="3786e-p103">In the **Enter Credentials** page, enter your Office 365 global admin credentials. Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="3786e-125">PSCredential オブジェクトとして管理者の資格情報、会社を指定する次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3786e-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="3786e-126">PowerShell を使用の詳細については、 [Office 365 の PowerShell への接続](https://go.microsoft.com/fwlink/p/?linkid=848585)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3786e-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="3786e-127">アドイン マニフェストをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="3786e-127">Upload an add-in manifest</span></span>
<span data-ttu-id="3786e-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="3786e-128"></span></span>

<span data-ttu-id="3786e-p104">コマンドレットを実行、新規の OrganizationAdd ので、パスは、ファイルの場所または URL のいずれかから、追加のマニフェストをアップロードします。_ManifestPath_パラメーターの値を作成するファイルの場所の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3786e-p104">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL. The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="3786e-p105">アドインをアップロードし、そのユーザーまたはグループに、_メンバー_のパラメーターを使用すると、次の例のように新規の OrganizationAdd-にコマンドレットを実行することもできます。メンバーの電子メール アドレスをコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="3786e-p105">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example. Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="3786e-133">Office ストアからのアップロードします。</span><span class="sxs-lookup"><span data-stu-id="3786e-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="3786e-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="3786e-134"></span></span>

<span data-ttu-id="3786e-135">Office ストアから、マニフェストをアップロードするのには新規 OrganizationAddIn コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3786e-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="3786e-136">次の例では、新規 OrganizationAddIn コマンドレットは、アメリカ合衆国の位置とコンテンツ市場のアドインの AssetId を指定します。</span><span class="sxs-lookup"><span data-stu-id="3786e-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="3786e-p106">_AssetId_パラメーターの値を調べるには、"WA"に続けて番号を使用してアドインの AssetIds の web ページが常に開始 Office ストアの URL からコピーすることができます。たとえば、前の例では、WA104099688 の AssetId 値のソースは、アドインを Office ストアの web ページの URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。</span><span class="sxs-lookup"><span data-stu-id="3786e-p106">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in. AssetIds always begin with "WA" followed by a number. For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="3786e-p107">_ロケール_パラメーターを使用し、 _ContentMarket_パラメーターの値は、同じからアドインをインストールしようとしている国/地域を示します。形式は、EN-US、fr FR. などです。</span><span class="sxs-lookup"><span data-stu-id="3786e-p107">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from. The format is en-US, fr-FR. and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="3786e-143">Office ストアからアップロードされたアドインは、Office ストアで使用される最新の更新プログラムの数日間で自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3786e-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="3786e-144">アドインの詳細情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="3786e-144">Get details of an add-in</span></span>
<span data-ttu-id="3786e-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="3786e-145"></span></span>

<span data-ttu-id="3786e-146">次のように、Get OrganizationAddIn コマンドレットを実行、テナントにアップロードするすべてのアドインの詳細情報を取得するのには含まれているアドインの製品 id。</span><span class="sxs-lookup"><span data-stu-id="3786e-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="3786e-147">するアドインを指定の詳細を取得する _[商品コード]_ パラメーターの値を取得 OrganizationAddIn コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3786e-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="3786e-148">すべてのアドインと、割り当てられたユーザーとグループの完全な詳細情報を取得するには、次の例に示すように Format-list コマンドレットでは、Get OrganizationAddIn コマンドレットの出力をパイプします。</span><span class="sxs-lookup"><span data-stu-id="3786e-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="3786e-149">オンまたはアドインを無効にします。</span><span class="sxs-lookup"><span data-stu-id="3786e-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="3786e-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="3786e-150"></span></span>

<span data-ttu-id="3786e-151">無効にするアドインをユーザーとそれに割り当てられているグループは、アクセスするため、 _[商品コード]_ パラメーターと設定_Enabled_パラメーター セット OrganizationAddIn コマンドレットを実行`$false`次の例のように、です。</span><span class="sxs-lookup"><span data-stu-id="3786e-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="3786e-152">アドインを追加するには、 _Enabled_パラメーターを設定と同じコマンドレットを実行します。 `$true`。</span><span class="sxs-lookup"><span data-stu-id="3786e-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="3786e-153">追加または削除ユーザーの追加</span><span class="sxs-lookup"><span data-stu-id="3786e-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="3786e-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="3786e-154"></span></span>

<span data-ttu-id="3786e-p108">特定のアドインにユーザーおよびグループを追加するには、 _[商品コード]_、_追加_、および_メンバー_のパラメーターを使用してセット OrganizationAddInAssignments コマンドレットを実行します。メンバーの電子メール アドレスをコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="3786e-p108">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters. Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="3786e-157">ユーザーおよびグループを削除するには、_削除する_パラメーターを使用して同じコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3786e-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="3786e-158">テナントのすべてのユーザーを追加で割り当てるには、 _AssignToEveryone_パラメーターを使用して値設定して同じコマンドレットを実行`$true`。</span><span class="sxs-lookup"><span data-stu-id="3786e-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="3786e-159">ないアドインをすべてのユーザーを割り当てるし、以前に割り当てられたユーザーとグループを元に戻す、同じコマンドレットを実行し、オフに_AssignToEveryone_パラメーターその値を設定する`$false`。</span><span class="sxs-lookup"><span data-stu-id="3786e-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="3786e-160">アドインを更新します。</span><span class="sxs-lookup"><span data-stu-id="3786e-160">Update an add-in</span></span>
<span data-ttu-id="3786e-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="3786e-161"></span></span>

<span data-ttu-id="3786e-162">マニフェストからアドインを更新するには、次の例に示すように、_商品コード_、 _ManifestPath_、および_ロケール_パラメーターをセット OrganizationAddIn コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3786e-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="3786e-163">Office ストアからアップロードされたアドインは、Office ストアで使用される最新の更新プログラムの数日間で自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3786e-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="3786e-164">アドインを削除します。</span><span class="sxs-lookup"><span data-stu-id="3786e-164">Delete an add-in</span></span>
<span data-ttu-id="3786e-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="3786e-165"></span></span>

<span data-ttu-id="3786e-166">アドインを削除するには、次の例のように、 _[商品コード]_ パラメーターで削除 OrganizationAddIn コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="3786e-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="3786e-167">各コマンドレットの詳細なヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="3786e-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="3786e-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="3786e-168"></span></span>

<span data-ttu-id="3786e-p109">Get-help コマンドレットを使用して、各コマンドレットの詳細なヘルプを表示できます。たとえば、次のコマンドレットは、削除 OrganizationAddIn コマンドレットの詳細についてを提供します。</span><span class="sxs-lookup"><span data-stu-id="3786e-p109">You can look at detailed help for each cmdlet by using the Get-help cmdlet. For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


