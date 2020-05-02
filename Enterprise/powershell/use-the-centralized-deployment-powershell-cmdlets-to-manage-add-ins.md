---
title: 一元展開 PowerShell コマンドレットを使用してアドインを管理する
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
- MET150
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 一元展開 PowerShell コマンドレットを使用すると、Office 365 組織の Office アドインを展開して管理するのに役立ちます。
ms.openlocfilehash: 3e3ca622f4c7a84d1fb267880ebf13cc56ad9373
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004500"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="75cc2-103">一元展開 PowerShell コマンドレットを使用してアドインを管理する</span><span class="sxs-lookup"><span data-stu-id="75cc2-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="75cc2-104">Office 365 管理者は、一元展開機能を使用して Office アドインをユーザーに展開できます (「[管理センターで office 365 アドインの展開を管理](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)する」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="75cc2-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="75cc2-105">管理センターで Office アドインを展開するだけでなく、Microsoft PowerShell を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="75cc2-105">In addition to deploying Office add-ins via the admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="75cc2-106">Microsoft ダウンロードセンターから一元展開の PowerShell コマンドレットを[ダウンロード](https://go.microsoft.com/fwlink/p/?linkid=850850)します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="75cc2-107">目的に合ったトピックをクリックしてください</span><span class="sxs-lookup"><span data-stu-id="75cc2-107">What do you want to do?</span></span>

[<span data-ttu-id="75cc2-108">管理者の資格情報を使用して接続する</span><span class="sxs-lookup"><span data-stu-id="75cc2-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="75cc2-109">アドインマニフェストをアップロードする</span><span class="sxs-lookup"><span data-stu-id="75cc2-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="75cc2-110">Office ストアからアドインをアップロードする</span><span class="sxs-lookup"><span data-stu-id="75cc2-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="75cc2-111">アドインの詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="75cc2-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="75cc2-112">アドインをオンまたはオフにする</span><span class="sxs-lookup"><span data-stu-id="75cc2-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="75cc2-113">アドインに対してユーザーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="75cc2-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="75cc2-114">アドインを更新する</span><span class="sxs-lookup"><span data-stu-id="75cc2-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="75cc2-115">アドインを削除する</span><span class="sxs-lookup"><span data-stu-id="75cc2-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="75cc2-116">各コマンドレットの詳細なヘルプを取得する</span><span class="sxs-lookup"><span data-stu-id="75cc2-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="75cc2-117">管理者の資格情報を使用して接続する</span><span class="sxs-lookup"><span data-stu-id="75cc2-117">Connect using your admin credentials</span></span>
<span data-ttu-id="75cc2-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="75cc2-118"><a name="BKMK_Connect"> </a></span></span>

<span data-ttu-id="75cc2-119">一元展開のコマンドレットを使用する前に、サインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="75cc2-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="75cc2-120">PowerShell を起動します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="75cc2-121">会社の管理者の資格情報を使用して PowerShell に接続します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="75cc2-122">次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="75cc2-123">[**資格情報の入力**] ページで、Office 365 グローバル管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="75cc2-124">または、コマンドレットに直接資格情報を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="75cc2-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="75cc2-125">会社の管理者の資格情報を PSCredential オブジェクトとして指定して、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="75cc2-126">PowerShell の使用の詳細については、「 [Connect To Office 365 powershell](https://go.microsoft.com/fwlink/p/?linkid=848585)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75cc2-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="75cc2-127">アドインマニフェストをアップロードする</span><span class="sxs-lookup"><span data-stu-id="75cc2-127">Upload an add-in manifest</span></span>
<span data-ttu-id="75cc2-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="75cc2-128"><a name="BKMK_UploadManifest"> </a></span></span>

<span data-ttu-id="75cc2-129">新しい組織のアドインコマンドレットを実行して、アドインのマニフェストをパスからアップロードします。これは、ファイルの場所または URL のいずれかにすることができます。</span><span class="sxs-lookup"><span data-stu-id="75cc2-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="75cc2-130">次の例は、 _Manifestpath_パラメーターの値のファイルの場所を示しています。</span><span class="sxs-lookup"><span data-stu-id="75cc2-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="75cc2-131">次の例に示すように、新しい組織のアドインコマンドレットを実行して、アドインをアップロードして、ユーザーまたはグループに直接割り当てることもできます。この場合、 _Members_パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="75cc2-132">メンバーの電子メールアドレスはコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="75cc2-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="75cc2-133">Office ストアからアドインをアップロードする</span><span class="sxs-lookup"><span data-stu-id="75cc2-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="75cc2-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="75cc2-134"><a name="BKMK_UploadAddin"> </a></span></span>

<span data-ttu-id="75cc2-135">新しい-組織の Addin コマンドレットを実行して、Office ストアからマニフェストをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="75cc2-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="75cc2-136">次の例では、新しい-組織の Addin コマンドレットは、米国の場所とコンテンツ市場のためにアドインの AssetId を指定しています。</span><span class="sxs-lookup"><span data-stu-id="75cc2-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="75cc2-137">_Assetid_パラメーターの値を確認するには、アドインの Office ストア web ページの URL からコピーします。</span><span class="sxs-lookup"><span data-stu-id="75cc2-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="75cc2-138">AssetIds は常に "WA" で始まり、その後に数字が続きます。</span><span class="sxs-lookup"><span data-stu-id="75cc2-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="75cc2-139">たとえば、前の例では、WA104099688 の AssetId 値のソースは、アドイン[https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)の Office ストアの web ページの URL です。</span><span class="sxs-lookup"><span data-stu-id="75cc2-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="75cc2-140">_Locale_パラメーターと_contentmarket_パラメーターの値は一致しており、アドインをインストールしようとしている国/地域を示しています。</span><span class="sxs-lookup"><span data-stu-id="75cc2-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="75cc2-141">この形式は en-us (fr-fr) です。</span><span class="sxs-lookup"><span data-stu-id="75cc2-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="75cc2-142">など。</span><span class="sxs-lookup"><span data-stu-id="75cc2-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="75cc2-143">Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="75cc2-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="75cc2-144">アドインの詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="75cc2-144">Get details of an add-in</span></span>
<span data-ttu-id="75cc2-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="75cc2-145"><a name="BKMK_GetDetails"> </a></span></span>

<span data-ttu-id="75cc2-146">次に示すように、Get-help Addin コマンドレットを実行して、テナントにアップロードされたすべてのアドインの詳細を取得し、アドインの製品 ID を含めます。</span><span class="sxs-lookup"><span data-stu-id="75cc2-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="75cc2-147">_ProductId_パラメーターの値を指定して取得し、詳細を取得するアドインを指定するには、このコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="75cc2-148">すべてのアドインおよび割り当てられたユーザーとグループの詳細を取得するには、次の例に示すように、コマンドレットの出力を Format コマンドレットにパイプ処理します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="75cc2-149">アドインをオンまたはオフにする</span><span class="sxs-lookup"><span data-stu-id="75cc2-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="75cc2-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="75cc2-150"><a name="BKMK_TurnOnOff"> </a></span></span>

<span data-ttu-id="75cc2-151">ユーザーおよびグループに割り当てられているグループがアクセスできなくなるようにアドインを無効にするには、次の例に示すように、 _ProductId_パラメーターと_Enabled_パラメーターを`$false`に設定して、このコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="75cc2-152">アドインを再び有効にするには、_有効な_パラメーターをに`$true`設定して、同じコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="75cc2-153">アドインに対してユーザーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="75cc2-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="75cc2-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="75cc2-154"><a name="BKMK_AddRemove"> </a></span></span>

<span data-ttu-id="75cc2-155">ユーザーおよびグループを特定のアドインに追加するには、 _ProductId_、 _Add_、および_Members_の各パラメーターを指定して、リソースの設定コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="75cc2-156">メンバーの電子メールアドレスはコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="75cc2-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="75cc2-157">ユーザーおよびグループを削除するには、 _remove_パラメーターを使用して同じコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="75cc2-158">テナントのすべてのユーザーにアドインを割り当てるには、の値をに`$true`設定して、Assign _toeveryone_パラメーターを使用して同じコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="75cc2-159">すべてのユーザーにアドインを割り当てずに、以前に割り当てられたユーザーおよびグループに戻すには、同じコマンドレットを実行し、その値をに`$false`設定して、Assign _toeveryone_パラメーターをオフにします。</span><span class="sxs-lookup"><span data-stu-id="75cc2-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="75cc2-160">アドインを更新する</span><span class="sxs-lookup"><span data-stu-id="75cc2-160">Update an add-in</span></span>
<span data-ttu-id="75cc2-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="75cc2-161"><a name="BKMK_UpdateAddin"> </a></span></span>

<span data-ttu-id="75cc2-162">マニフェストからアドインを更新するには、次の例に示すように、 _ProductId_、 _manifestpath_、および_Locale_パラメーターを使用して、次のように設定して、このコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="75cc2-163">Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="75cc2-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="75cc2-164">アドインを削除する</span><span class="sxs-lookup"><span data-stu-id="75cc2-164">Delete an add-in</span></span>
<span data-ttu-id="75cc2-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="75cc2-165"><a name="BKMK_Delete"> </a></span></span>

<span data-ttu-id="75cc2-166">アドインを削除するには、次の例に示されているように、 _ProductId_パラメーターを指定して、[削除] コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="75cc2-167">各コマンドレットの詳細なヘルプを取得する</span><span class="sxs-lookup"><span data-stu-id="75cc2-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="75cc2-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="75cc2-168"><a name="BKMK_GetHelp"> </a></span></span>

<span data-ttu-id="75cc2-169">各コマンドレットの詳細については、「get-help」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75cc2-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="75cc2-170">たとえば、次のコマンドレットは、このコマンドレットに関する詳細な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="75cc2-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


