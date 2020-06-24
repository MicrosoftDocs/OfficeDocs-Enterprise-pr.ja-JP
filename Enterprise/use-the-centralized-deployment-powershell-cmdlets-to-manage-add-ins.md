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
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
f1.keywords:
- NOCSH
description: 一元展開 PowerShell コマンドレットを使用すると、Office 365 組織の Office アドインを展開して管理するのに役立ちます。
ms.openlocfilehash: 52445b2f2ff6d9fdf3f5997e1c76adbd1808e56f
ms.sourcegitcommit: 12a22fa9224ab2a29330ee0aabecff28d577d7e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "44861124"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>一元展開 PowerShell コマンドレットを使用してアドインを管理する

Microsoft 365 グローバル管理者は、一元展開機能を使用して Office アドインをユーザーに展開できます (「[管理センターで Office アドインを展開](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)する」を参照してください)。 Microsoft 365 管理センター経由で Office アドインを展開することに加えて、Microsoft PowerShell を使用することもできます。 [Windows PowerShell 用 O365 中央アドイン展開モジュール](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)をインストールします。 

モジュールをダウンロードした後、通常の Windows PowerShell ウィンドウを開き、次のコマンドレットを実行します。

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>管理者の資格情報を使用して接続する

一元展開のコマンドレットを使用する前に、サインインする必要があります。
  
1. PowerShell を起動します。
    
2. 会社の管理者の資格情報を使用して PowerShell に接続します。 次のコマンドレットを実行します。
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. [**資格情報の入力**] ページで、Office 365 グローバル管理者の資格情報を入力します。 または、コマンドレットに直接資格情報を入力することもできます。 
    
    会社の管理者の資格情報を PSCredential オブジェクトとして指定して、次のコマンドレットを実行します。
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> PowerShell の使用の詳細については、「 [Connect To Office 365 powershell](https://go.microsoft.com/fwlink/p/?linkid=848585)」を参照してください。 
  
## <a name="upload-an-add-in-manifest"></a>アドインマニフェストをアップロードする

**新しい組織のアドイン**コマンドレットを実行して、アドインのマニフェストをパスからアップロードします。これは、ファイルの場所または URL のいずれかにすることができます。 次の例は、 _Manifestpath_パラメーターの値のファイルの場所を示しています。 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

次の例に示すように、**新しい組織のアドイン**コマンドレットを実行して、アドインをアップロードして、ユーザーまたはグループに直接割り当てることもできます。この場合、 _Members_パラメーターを使用します。 メンバーの電子メールアドレスはコンマで区切ります。 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Office ストアからアドインをアップロードする

**新しい-組織の addin**コマンドレットを実行して、Office ストアからマニフェストをアップロードします。
  
次の例では、**新しい-組織の addin**コマンドレットは、米国の場所とコンテンツ市場のためにアドインの assetid を指定しています。
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

_Assetid_パラメーターの値を確認するには、アドインの Office ストア web ページの URL からコピーします。 AssetIds は常に "WA" で始まり、その後に数字が続きます。 たとえば、前の例では、WA104099688 の AssetId 値のソースは、アドインの Office ストアの web ページの URL [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688) です。
  
_Locale_パラメーターと_contentmarket_パラメーターの値は一致しており、アドインをインストールしようとしている国/地域を示しています。 この形式は en-us (fr-fr) です。 など。 
  
> [!NOTE]
> Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。 
  
## <a name="get-details-of-an-add-in"></a>アドインの詳細を取得する

次に示すように、 **Get-help addin**コマンドレットを実行して、テナントにアップロードされたすべてのアドインの詳細を取得し、アドインの製品 ID を含めます。
  
```powershell
Get-OrganizationAddIn
```

_ProductId_パラメーターの値を指定して**取得**し、詳細を取得するアドインを指定するには、このコマンドレットを実行します。 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

すべてのアドインおよび割り当てられたユーザーとグループの詳細を取得するには、次の例に示すように、コマンドレットの出力を Format**コマンドレットに**パイプ処理します。
  
```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a>アドインをオンまたはオフにする

ユーザーおよびグループに割り当てられているグループがアクセスできなくなるようにアドインを無効にするには、次の例に示すように、 _ProductId_パラメーターと_Enabled_パラメーターをに設定して、このコマンドレットを**実行し** `$false` ます。
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

アドインを再び有効にするには、_有効な_パラメーターをに設定して、同じコマンドレットを実行し `$true` ます。
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>アドインに対してユーザーを追加または削除する

ユーザーおよびグループを特定のアドインに追加するには、 _ProductId_、 _Add_、および_Members_の各パラメーターを指定して、**リソースの設定**コマンドレットを実行します。 メンバーの電子メールアドレスはコンマで区切ります。 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

ユーザーおよびグループを削除するには、 _remove_パラメーターを使用して同じコマンドレットを実行します。 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

テナントのすべてのユーザーにアドインを割り当てるには、の値をに設定して、assign _Toeveryone_パラメーターを使用して同じコマンドレットを実行し `$true` ます。
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

すべてのユーザーにアドインを割り当てずに、以前に割り当てられたユーザーおよびグループに戻すには、同じコマンドレットを実行し、その値をに設定して、assign _Toeveryone_パラメーターをオフにし `$false` ます。
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>アドインを更新する

マニフェストからアドインを更新するには、次の例に示すように、 _ProductId_、 _manifestpath_、および_Locale_パラメーターを使用して、次のように**設定**して、このコマンドレットを実行します。 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。 
  
## <a name="delete-an-add-in"></a>アドインを削除する

アドインを削除するには、次の例に示されているように、 _ProductId_パラメーターを指定して、[**削除**] コマンドレットを実行します。 
  
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

## <a name="get-detailed-help-for-each-cmdlet"></a>各コマンドレットの詳細なヘルプを取得する

各コマンドレットの詳細については、「get-help」を参照してください。 たとえば、次のコマンドレットは、このコマンドレットに関する詳細な情報を提供します。
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


