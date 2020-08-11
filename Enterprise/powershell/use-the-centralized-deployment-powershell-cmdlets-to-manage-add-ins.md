---
title: 一元展開 PowerShell コマンドレットを使用してアドインを管理する
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2020
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
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
ms.custom:
- seo-marvel-apr2020
description: 一元展開 PowerShell コマンドレットを使用すると、Microsoft 365 組織の Office アドインを展開および管理するのに役立ちます。
ms.openlocfilehash: 849e27dc3bda5dc9e6b4f45bc100e896eae3e281
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605349"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="ac4e0-103">一元展開 PowerShell コマンドレットを使用してアドインを管理する</span><span class="sxs-lookup"><span data-stu-id="ac4e0-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="ac4e0-104">Microsoft 365 グローバル管理者は、一元展開機能を使用して Office アドインをユーザーに展開できます (「[管理センターで Office アドインを展開](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins)する」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-104">As a Microsoft 365 global admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://docs.microsoft.com/microsoft-365/admin/manage/manage-deployment-of-add-ins)).</span></span> <span data-ttu-id="ac4e0-105">Microsoft 365 管理センター経由で Office アドインを展開することに加えて、Microsoft PowerShell を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="ac4e0-106">[Windows PowerShell 用 O365 中央アドイン展開モジュール](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="ac4e0-107">モジュールをダウンロードした後、通常の Windows PowerShell ウィンドウを開き、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="ac4e0-108">管理者の資格情報を使用して接続する</span><span class="sxs-lookup"><span data-stu-id="ac4e0-108">Connect using your admin credentials</span></span>

<span data-ttu-id="ac4e0-109">一元展開のコマンドレットを使用する前に、サインインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="ac4e0-110">PowerShell を起動します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="ac4e0-111">会社の管理者の資格情報を使用して PowerShell に接続します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="ac4e0-112">次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="ac4e0-113">[**資格情報の入力**] ページで、Microsoft 365 グローバル管理者の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-113">In the **Enter Credentials** page, enter your Microsoft 365 global admin credentials.</span></span> <span data-ttu-id="ac4e0-114">または、コマンドレットに直接資格情報を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="ac4e0-115">会社の管理者の資格情報を PSCredential オブジェクトとして指定して、次のコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="ac4e0-116">PowerShell の使用の詳細については、「 [Connect To Microsoft 365 With powershell](https://go.microsoft.com/fwlink/p/?linkid=848585)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-116">For more information about using PowerShell, see [Connect to Microsoft 365 with PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="ac4e0-117">アドインマニフェストをアップロードする</span><span class="sxs-lookup"><span data-stu-id="ac4e0-117">Upload an add-in manifest</span></span>

<span data-ttu-id="ac4e0-118">**新しい組織のアドイン**コマンドレットを実行して、アドインのマニフェストをパスからアップロードします。これは、ファイルの場所または URL のいずれかにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="ac4e0-119">次の例は、 _Manifestpath_パラメーターの値のファイルの場所を示しています。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="ac4e0-120">次の例に示すように、**新しい組織のアドイン**コマンドレットを実行して、アドインをアップロードして、ユーザーまたはグループに直接割り当てることもできます。この場合、 _Members_パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="ac4e0-121">メンバーの電子メールアドレスはコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="ac4e0-122">Office ストアからアドインをアップロードする</span><span class="sxs-lookup"><span data-stu-id="ac4e0-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="ac4e0-123">**新しい-組織の addin**コマンドレットを実行して、Office ストアからマニフェストをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="ac4e0-124">次の例では、**新しい-組織の addin**コマンドレットは、米国の場所とコンテンツ市場のためにアドインの assetid を指定しています。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="ac4e0-125">_Assetid_パラメーターの値を確認するには、アドインの Office ストア web ページの URL からコピーします。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="ac4e0-126">AssetIds は常に "WA" で始まり、その後に数字が続きます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="ac4e0-127">たとえば、前の例では、WA104099688 の AssetId 値のソースは、アドインの Office ストアの web ページの URL [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688) です。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="ac4e0-128">_Locale_パラメーターと_contentmarket_パラメーターの値は一致しており、アドインをインストールしようとしている国/地域を示しています。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="ac4e0-129">この形式は en-us (fr-fr) です。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="ac4e0-130">など。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="ac4e0-131">Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="ac4e0-132">アドインの詳細を取得する</span><span class="sxs-lookup"><span data-stu-id="ac4e0-132">Get details of an add-in</span></span>

<span data-ttu-id="ac4e0-133">次に示すように、 **Get-help addin**コマンドレットを実行して、テナントにアップロードされたすべてのアドインの詳細を取得し、アドインの製品 ID を含めます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="ac4e0-134">_ProductId_パラメーターの値を指定して**取得**し、詳細を取得するアドインを指定するには、このコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="ac4e0-135">すべてのアドインおよび割り当てられたユーザーとグループの詳細を取得するには、次の例に示すように、コマンドレットの出力を Format**コマンドレットに**パイプ処理します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="ac4e0-136">アドインをオンまたはオフにする</span><span class="sxs-lookup"><span data-stu-id="ac4e0-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="ac4e0-137">ユーザーおよびグループに割り当てられているグループがアクセスできなくなるようにアドインを無効にするには、次の例に示すように、 _ProductId_パラメーターと_Enabled_パラメーターをに設定して、このコマンドレットを**実行し** `$false` ます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="ac4e0-138">アドインを再び有効にするには、_有効な_パラメーターをに設定して、同じコマンドレットを実行し `$true` ます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="ac4e0-139">アドインに対してユーザーを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="ac4e0-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="ac4e0-140">ユーザーおよびグループを特定のアドインに追加するには、 _ProductId_、 _Add_、および_Members_の各パラメーターを指定して、**リソースの設定**コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="ac4e0-141">メンバーの電子メールアドレスはコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="ac4e0-142">ユーザーおよびグループを削除するには、 _remove_パラメーターを使用して同じコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="ac4e0-143">テナントのすべてのユーザーにアドインを割り当てるには、の値をに設定して、assign _Toeveryone_パラメーターを使用して同じコマンドレットを実行し `$true` ます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="ac4e0-144">すべてのユーザーにアドインを割り当てずに、以前に割り当てられたユーザーおよびグループに戻すには、同じコマンドレットを実行し、その値をに設定して、assign _Toeveryone_パラメーターをオフにし `$false` ます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="ac4e0-145">アドインを更新する</span><span class="sxs-lookup"><span data-stu-id="ac4e0-145">Update an add-in</span></span>

<span data-ttu-id="ac4e0-146">マニフェストからアドインを更新するには、次の例に示すように、 _ProductId_、 _manifestpath_、および_Locale_パラメーターを使用して、次のように**設定**して、このコマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="ac4e0-147">Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="ac4e0-148">アドインを削除する</span><span class="sxs-lookup"><span data-stu-id="ac4e0-148">Delete an add-in</span></span>

<span data-ttu-id="ac4e0-149">アドインを削除するには、次の例に示されているように、 _ProductId_パラメーターを指定して、[**削除**] コマンドレットを実行します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<!--
## Customize Microsoft Store add-ins for your organization

You must customize the add-in before you deploy it to your organization. Add-ins older than version 1.1 are not supported by this feature. 

We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.

Note also the following restrictions:
- All URLs must be absolute (include http or https) and valid.
- *DisplayName* must not exceed 125 characters 
- *DisplayName*, *Resources* and *AppDomains* must not include the following characters: 
 
    - \<
    -  \>
    -  ;
    -  =   

If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.

To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
To customize multiple tags for an add-in, add those tags to the commandline:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> You must apply multiple customized tags to one add-in as one command. If you customize tags one by one, only the last customization will be applied. Additionally, if you customize a tag by mistake, you must remove all customizations and start over.

### Tags you can customize

| Tag                  | Description          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| The URL of the image used as the add-in’s icon (in admin center). </br> |
| \<DisplayName>| The title of the add-in  (in admin center).|
| \<Hosts>| List of apps that will support the add-in.|
| \<SourceLocation> | The source URL that the add-in will connect to.| 
| \<AppDomains> | A list of domains that the add-in can connect with. | 
| \<SupportURL>| The URL users can use to access help and support. | 
| \<Resources>  | This tag contains a number of elements including titles, tooltips, and icons of different sizes.| 
|
### Customize Resources tag

Any element in the <Resources> tag of the manifest can be customized dynamically. You first need to check the manifest to find the element id to which you want to assign a new value. The <Resources> tag looks like this:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

You can customize as many elements with the command as you need to.

### Remove customization from an add-in

The only option currently available for deleting customizations is to delete all of them at once:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### View add-in customizations

To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet. If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.  

```powershell
Get-OrganizationAddInOverrides 
```
If ProductId is specified, then a list of overrides applied to that add-in is returned. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### Remove an add-in from local cache

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remive an add-in from cache:

1. Navigate to the “Users” folder in C:\ 
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="ac4e0-150">各コマンドレットの詳細なヘルプを取得する</span><span class="sxs-lookup"><span data-stu-id="ac4e0-150">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="ac4e0-151">各コマンドレットの詳細については、「get-help」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-151">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="ac4e0-152">たとえば、次のコマンドレットは、このコマンドレットに関する詳細な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ac4e0-152">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


