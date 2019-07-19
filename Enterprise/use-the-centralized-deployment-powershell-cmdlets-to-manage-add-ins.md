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
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 一元展開 PowerShell コマンドレットを使用すると、Office 365 組織の Office アドインを展開して管理するのに役立ちます。
ms.openlocfilehash: c63a48d212bba4eda25fb6b8843f6321892dc54b
ms.sourcegitcommit: d53033c2d2d41d52047e3e2644d77373d4a5dd9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "35791252"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="5f127-103">一元展開 PowerShell コマンドレットを使用してアドインを管理する</span><span class="sxs-lookup"><span data-stu-id="5f127-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="5f127-104">Microsoft 365 グローバルまたは Exchange 管理者は、一元展開機能を使用して Office アドインをユーザーに展開できます (「[管理センターで Office アドインを展開](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)する」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5f127-104">As a Microsoft 365 global, or Exchange admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="5f127-105">Microsoft 365 管理センター経由で Office アドインを展開することに加えて、Microsoft PowerShell を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f127-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="5f127-106">[Windows PowerShell 用 O365 中央アドイン展開モジュール](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="5f127-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="5f127-107">モジュールをダウンロードした後、通常の Windows PowerShell ウィンドウを開き、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="5f127-108">管理者の資格情報を使用して接続する</span><span class="sxs-lookup"><span data-stu-id="5f127-108">Connect using your admin credentials</span></span>

<span data-ttu-id="5f127-109">一元展開のコマンドレットを使用する前に、サインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f127-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="5f127-110">PowerShell を起動します。</span><span class="sxs-lookup"><span data-stu-id="5f127-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="5f127-111">会社の管理者の資格情報を使用して PowerShell に接続します。</span><span class="sxs-lookup"><span data-stu-id="5f127-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="5f127-112">次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="5f127-113">[**資格情報の入力**] ページで、Office 365 グローバル管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="5f127-113">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="5f127-114">または、コマンドレットに直接資格情報を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="5f127-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="5f127-115">会社の管理者の資格情報を PSCredential オブジェクトとして指定して、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="5f127-116">PowerShell の使用の詳細については、「 [Connect To Office 365 powershell](https://go.microsoft.com/fwlink/p/?linkid=848585)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f127-116">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="5f127-117">アドインマニフェストをアップロードする</span><span class="sxs-lookup"><span data-stu-id="5f127-117">Upload an add-in manifest</span></span>

<span data-ttu-id="5f127-118">**新しい組織のアドイン**コマンドレットを実行して、アドインのマニフェストをパスからアップロードします。これは、ファイルの場所または URL のいずれかにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5f127-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="5f127-119">次の例は、 _Manifestpath_パラメーターの値のファイルの場所を示しています。</span><span class="sxs-lookup"><span data-stu-id="5f127-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="5f127-120">次の例に示すように、**新しい組織のアドイン**コマンドレットを実行して、アドインをアップロードして、ユーザーまたはグループに直接割り当てることもできます。この場合、 _Members_パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="5f127-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="5f127-121">メンバーの電子メールアドレスはコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="5f127-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="5f127-122">Office ストアからアドインをアップロードする</span><span class="sxs-lookup"><span data-stu-id="5f127-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="5f127-123">**新しい-組織の addin**コマンドレットを実行して、Office ストアからマニフェストをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="5f127-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="5f127-124">次の例では、**新しい-組織の addin**コマンドレットは、米国の場所とコンテンツ市場のためにアドインの assetid を指定しています。</span><span class="sxs-lookup"><span data-stu-id="5f127-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="5f127-125">_Assetid_パラメーターの値を確認するには、アドインの Office ストア web ページの URL からコピーします。</span><span class="sxs-lookup"><span data-stu-id="5f127-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="5f127-126">AssetIds は常に "WA" で始まり、その後に数字が続きます。</span><span class="sxs-lookup"><span data-stu-id="5f127-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="5f127-127">たとえば、前の例では、WA104099688 の AssetId 値のソースは、アドイン[https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)の Office ストアの web ページの URL です。</span><span class="sxs-lookup"><span data-stu-id="5f127-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="5f127-128">_Locale_パラメーターと_contentmarket_パラメーターの値は一致しており、アドインをインストールしようとしている国/地域を示しています。</span><span class="sxs-lookup"><span data-stu-id="5f127-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="5f127-129">この形式は en-us (fr-fr) です。</span><span class="sxs-lookup"><span data-stu-id="5f127-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="5f127-130">など。</span><span class="sxs-lookup"><span data-stu-id="5f127-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="5f127-131">Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="5f127-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="5f127-132">アドインの詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="5f127-132">Get details of an add-in</span></span>

<span data-ttu-id="5f127-133">次に示すように、 **Get-help addin**コマンドレットを実行して、テナントにアップロードされたすべてのアドインの詳細を取得し、アドインの製品 ID を含めます。</span><span class="sxs-lookup"><span data-stu-id="5f127-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="5f127-134">_ProductId_パラメーターの値を指定して**取得**し、詳細を取得するアドインを指定するには、このコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="5f127-135">すべてのアドインおよび割り当てられたユーザーとグループの詳細を取得するには、次の例\*\*\*\* に示すように、コマンドレットの出力を Format コマンドレットにパイプ処理します。</span><span class="sxs-lookup"><span data-stu-id="5f127-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="5f127-136">アドインをオンまたはオフにする</span><span class="sxs-lookup"><span data-stu-id="5f127-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="5f127-137">ユーザーおよびグループに割り当てられているグループがアクセスできなくなるようにアドインを無効にするには\*\*\*\* 、次の例に示すように、 _ProductId_パラメーターと_Enabled_パラメーターを`$false`に設定して、このコマンドレットを実行します。.</span><span class="sxs-lookup"><span data-stu-id="5f127-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="5f127-138">アドインを再び有効にするには、_有効な_パラメーターをに`$true`設定して、同じコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="5f127-139">アドインに対してユーザーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="5f127-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="5f127-140">ユーザーおよびグループを特定のアドインに追加するには、 _ProductId_、 _Add_、および_Members_の各パラメーターを指定して、**リソースの設定**コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="5f127-141">メンバーの電子メールアドレスはコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="5f127-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="5f127-142">ユーザーおよびグループを削除するには、 _remove_パラメーターを使用して同じコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="5f127-143">テナントのすべてのユーザーにアドインを割り当てるには、の値をに`$true`設定して、Assign _toeveryone_パラメーターを使用して同じコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="5f127-144">すべてのユーザーにアドインを割り当てずに、以前に割り当てられたユーザーおよびグループに戻すには、同じコマンドレットを実行し、その値をに`$false`設定して、Assign _toeveryone_パラメーターをオフにします。</span><span class="sxs-lookup"><span data-stu-id="5f127-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="5f127-145">アドインを更新する</span><span class="sxs-lookup"><span data-stu-id="5f127-145">Update an add-in</span></span>

<span data-ttu-id="5f127-146">マニフェストからアドインを更新するには、次の例に示すように、 _ProductId_、 _manifestpath_、および_Locale_パラメーターを使用して、次のように**設定**して、このコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="5f127-147">Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="5f127-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="5f127-148">アドインを削除する</span><span class="sxs-lookup"><span data-stu-id="5f127-148">Delete an add-in</span></span>

<span data-ttu-id="5f127-149">アドインを削除するには、次の例に示されているように、 _ProductId_パラメーターを指定して、[**削除**] コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a><span data-ttu-id="5f127-150">組織の Microsoft Store アドインをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="5f127-150">Customize Microsoft Store add-ins for your organization</span></span>

<span data-ttu-id="5f127-151">組織に展開する前に、アドインをカスタマイズする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f127-151">You must customize the add-in before you deploy it to your organization.</span></span> <span data-ttu-id="5f127-152">バージョン1.1 より前のアドインは、この機能ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="5f127-152">Add-ins older than version 1.1 are not supported by this feature.</span></span> 

<span data-ttu-id="5f127-153">また、次の制限に注意してください。</span><span class="sxs-lookup"><span data-stu-id="5f127-153">Note also the following restrictions:</span></span>
- <span data-ttu-id="5f127-154">すべての Url は、絶対 (http または https を含む) であり、有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f127-154">All URLs must be absolute (include http or https) and valid.</span></span>
- <span data-ttu-id="5f127-155">*DisplayName*は125文字以下にする必要があります</span><span class="sxs-lookup"><span data-stu-id="5f127-155">*DisplayName* must not exceed 125 characters</span></span> 
- <span data-ttu-id="5f127-156">*DisplayName*、 *Resources* 、および*AppDomains*には、次の文字を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="5f127-156">*DisplayName*, *Resources* and *AppDomains* must not include the following characters:</span></span> 
 
    - \<
    -  \>
    -  <span data-ttu-id="5f127-157">;</span><span class="sxs-lookup"><span data-stu-id="5f127-157"></span></span>
    -  =   

<span data-ttu-id="5f127-158">展開されているアドインをカスタマイズする場合は、管理センターでアンインストールする必要があり、展開されている各コンピューターから削除する手順については、「[ローカルキャッシュからアドインを削除](#remove-an-add-in-from-local-cache)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f127-158">If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.</span></span>

<span data-ttu-id="5f127-159">アドインをカスタマイズするには、パラメーターとして*ProductId*を指定して**Set –組織**の上書きコマンドレットを実行し、その後に、上書きするタグと新しい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="5f127-159">To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value.</span></span> <span data-ttu-id="5f127-160">*ProductId*を取得する方法については、この記事の「[アドインの詳細を取得](#get-details-of-an-add-in)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f127-160">To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article.</span></span> <span data-ttu-id="5f127-161">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5f127-161">For example:</span></span>

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
<span data-ttu-id="5f127-162">アドインの複数のタグをカスタマイズするには、これらのタグを commandline に追加します。</span><span class="sxs-lookup"><span data-stu-id="5f127-162">To customize multiple tags for an add-in, add those tags to the commandline:</span></span>

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> <span data-ttu-id="5f127-163">1つのコマンドとして、1つのアドインに複数のカスタマイズされたタグを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f127-163">You must apply multiple customized tags to one add-in as one command.</span></span> <span data-ttu-id="5f127-164">タグを1つずつカスタマイズした場合は、最後のカスタマイズのみが適用されます。</span><span class="sxs-lookup"><span data-stu-id="5f127-164">If you customize tags one by one, only the last customization will be applied.</span></span> <span data-ttu-id="5f127-165">また、誤ってタグをカスタマイズした場合は、すべてのカスタマイズを削除して最初からやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f127-165">Additionally, if you customize a tag by mistake, you must remove all customizations and start over.</span></span>

### <a name="tags-you-can-customize"></a><span data-ttu-id="5f127-166">カスタマイズできるタグ</span><span class="sxs-lookup"><span data-stu-id="5f127-166">Tags you can customize</span></span>

| <span data-ttu-id="5f127-167">Tag</span><span class="sxs-lookup"><span data-stu-id="5f127-167">Tag</span></span>                  | <span data-ttu-id="5f127-168">説明</span><span class="sxs-lookup"><span data-stu-id="5f127-168">Description</span></span>          |
| :------------------- | :------------------- |
| <span data-ttu-id="5f127-169">\<IconURL></span><span class="sxs-lookup"><span data-stu-id="5f127-169">\<IconURL></span></span>   </br>| <span data-ttu-id="5f127-170">アドインのアイコンとして使用されるイメージの URL (管理センター内)。</span><span class="sxs-lookup"><span data-stu-id="5f127-170">The URL of the image used as the add-in’s icon (in admin center).</span></span> </br> |
| <span data-ttu-id="5f127-171">\<DisplayName></span><span class="sxs-lookup"><span data-stu-id="5f127-171">\<DisplayName></span></span>| <span data-ttu-id="5f127-172">アドインのタイトル (管理センター)。</span><span class="sxs-lookup"><span data-stu-id="5f127-172">The title of the add-in  (in admin center).</span></span>|
| <span data-ttu-id="5f127-173">\<Hosts></span><span class="sxs-lookup"><span data-stu-id="5f127-173">\<Hosts></span></span>| <span data-ttu-id="5f127-174">アドインをサポートするアプリの一覧。</span><span class="sxs-lookup"><span data-stu-id="5f127-174">List of apps that will support the add-in.</span></span>|
| <span data-ttu-id="5f127-175">\<SourceLocation></span><span class="sxs-lookup"><span data-stu-id="5f127-175">\<SourceLocation></span></span> | <span data-ttu-id="5f127-176">アドインが接続する元の URL。</span><span class="sxs-lookup"><span data-stu-id="5f127-176">The source URL that the add-in will connect to.</span></span>| 
| <span data-ttu-id="5f127-177">\<AppDomains></span><span class="sxs-lookup"><span data-stu-id="5f127-177">\<AppDomains></span></span> | <span data-ttu-id="5f127-178">アドインが接続できるドメインの一覧。</span><span class="sxs-lookup"><span data-stu-id="5f127-178">A list of domains that the add-in can connect with.</span></span> | 
| <span data-ttu-id="5f127-179">\<SupportURL></span><span class="sxs-lookup"><span data-stu-id="5f127-179">\<SupportURL></span></span>| <span data-ttu-id="5f127-180">ユーザーがヘルプとサポートにアクセスするために使用できる URL。</span><span class="sxs-lookup"><span data-stu-id="5f127-180">The URL users can use to access help and support.</span></span> | 
| <span data-ttu-id="5f127-181">\<リソース></span><span class="sxs-lookup"><span data-stu-id="5f127-181">\<Resources></span></span>  | <span data-ttu-id="5f127-182">このタグには、タイトル、ツールヒント、さまざまなサイズのアイコンなど、いくつかの要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f127-182">This tag contains a number of elements including titles, tooltips, and icons of different sizes.</span></span>| 
|
### <a name="customize-resources-tag"></a><span data-ttu-id="5f127-183">リソースのカスタマイズタグ</span><span class="sxs-lookup"><span data-stu-id="5f127-183">Customize Resources tag</span></span>

<span data-ttu-id="5f127-184">マニフェストの<Resources>タグ内の要素は、動的にカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="5f127-184">Any element in the <Resources> tag of the manifest can be customized dynamically.</span></span> <span data-ttu-id="5f127-185">最初に、マニフェストをチェックして、新しい値を割り当てる要素の id を見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f127-185">You first need to check the manifest to find the element id to which you want to assign a new value.</span></span> <span data-ttu-id="5f127-186">タグ<Resources>は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5f127-186">The <Resources> tag looks like this:</span></span>

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
<span data-ttu-id="5f127-187">この例では、イメージの要素 id は "img16icon" で、それに関連付けられている値<i></i>は "http://サイトです。<i> </i>com/img. "</span><span class="sxs-lookup"><span data-stu-id="5f127-187">In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”</span></span>

<span data-ttu-id="5f127-188">カスタマイズする要素を特定したら、Powershell で次のコマンドを使用して、要素に新しい値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5f127-188">Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:</span></span>

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

<span data-ttu-id="5f127-189">必要に応じて、コマンドを使用して複数の要素をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="5f127-189">You can customize as many elements with the command as you need to.</span></span>

### <a name="remove-customization-from-an-add-in"></a><span data-ttu-id="5f127-190">アドインからカスタマイズを削除する</span><span class="sxs-lookup"><span data-stu-id="5f127-190">Remove customization from an add-in</span></span>

<span data-ttu-id="5f127-191">現在、カスタマイズを削除するために使用できるオプションは、一度にすべてを削除することです。</span><span class="sxs-lookup"><span data-stu-id="5f127-191">The only option currently available for deleting customizations is to delete all of them at once:</span></span>

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a><span data-ttu-id="5f127-192">アドインのカスタマイズを表示する</span><span class="sxs-lookup"><span data-stu-id="5f127-192">View add-in customizations</span></span>

<span data-ttu-id="5f127-193">適用されているカスタマイズの一覧を表示するには、" **Get-help Addinoverrides/上書き**" コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="5f127-193">To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet.</span></span> <span data-ttu-id="5f127-194">**取得**した引数が*ProductId*なしで実行される場合は、オーバーライドが適用されたすべてのアドインのリストが返されます。</span><span class="sxs-lookup"><span data-stu-id="5f127-194">If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.</span></span>  

```powershell
Get-OrganizationAddInOverrides 
```
<span data-ttu-id="5f127-195">ProductId が指定されている場合、そのアドインに適用されたオーバーライドの一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="5f127-195">If ProductId is specified, then a list of overrides applied to that add-in is returned.</span></span> 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a><span data-ttu-id="5f127-196">ローカルキャッシュからアドインを削除する</span><span class="sxs-lookup"><span data-stu-id="5f127-196">Remove an add-in from local cache</span></span>

<span data-ttu-id="5f127-197">アドインが展開されている場合は、カスタマイズできるようにするために、各コンピューターのキャッシュから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f127-197">If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized.</span></span> <span data-ttu-id="5f127-198">アドインをキャッシュから再作成するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="5f127-198">To remive an add-in from cache:</span></span>

1. <span data-ttu-id="5f127-199">C:\ の "Users" フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="5f127-199">Navigate to the “Users” folder in C:\</span></span> 
1. <span data-ttu-id="5f127-200">ユーザーフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="5f127-200">Go to your user folder</span></span>
1. <span data-ttu-id="5f127-201">AppData\Local\Microsoft\Office に移動し、Office のバージョンに関連付けられているフォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="5f127-201">Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office</span></span>
1. <span data-ttu-id="5f127-202">*Wef*フォルダーで、[*マニフェスト*] フォルダーを削除します。</span><span class="sxs-lookup"><span data-stu-id="5f127-202">In the *Wef* folder delete the *Manifests* folder.</span></span>

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="5f127-203">各コマンドレットの詳細なヘルプを取得する</span><span class="sxs-lookup"><span data-stu-id="5f127-203">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="5f127-204">各コマンドレットの詳細については、「get-help」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f127-204">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="5f127-205">たとえば、次のコマンドレットは、このコマンドレットに関する詳細な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5f127-205">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


