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
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: 一元展開 PowerShell コマンドレットを使用すると、Office 365 組織の Office アドインを展開して管理するのに役立ちます。
ms.openlocfilehash: 586b66ac3632a5d86a63014a50f3c605b1c005e7
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844158"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>一元展開 PowerShell コマンドレットを使用してアドインを管理する

Office 365 管理者は、一元展開機能を使用して Office アドインをユーザーに展開できます (「[管理センターで office 365 アドインの展開を管理](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)する」を参照してください)。 管理センターで Office アドインを展開するだけでなく、Microsoft PowerShell を使用することもできます。 Microsoft ダウンロードセンターから一元展開の PowerShell コマンドレットを[ダウンロード](https://go.microsoft.com/fwlink/p/?linkid=850850)します。 
  
## <a name="what-do-you-want-to-do"></a>目的に合ったトピックをクリックしてください

[管理者の資格情報を使用して接続する](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[アドインマニフェストをアップロードする](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[Office ストアからアドインをアップロードする](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[アドインの詳細を取得する](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[アドインをオンまたはオフにする](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[アドインに対してユーザーを追加または削除する](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[アドインを更新する](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[アドインを削除する](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[各コマンドレットの詳細なヘルプを取得する](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>管理者の資格情報を使用して接続する
<a name="BKMK_Connect"> </a>

一元展開のコマンドレットを使用する前に、サインインする必要があります。
  
1. PowerShell を起動します。
    
2. 会社の管理者の資格情報を使用して PowerShell に接続します。 次のコマンドレットを実行します。
    
  ```
  Connect-OrganizationAddInService
  ```

3. [**資格情報の入力**] ページで、Office 365 グローバル管理者の資格情報を入力します。 または、コマンドレットに直接資格情報を入力することもできます。 
    
    会社の管理者の資格情報を PSCredential オブジェクトとして指定して、次のコマンドレットを実行します。
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> PowerShell の使用の詳細については、「 [Connect To Office 365 powershell](https://go.microsoft.com/fwlink/p/?linkid=848585)」を参照してください。 
  
## <a name="upload-an-add-in-manifest"></a>アドインマニフェストをアップロードする
<a name="BKMK_UploadManifest"> </a>

新しい組織のアドインコマンドレットを実行して、アドインのマニフェストをパスからアップロードします。これは、ファイルの場所または URL のいずれかにすることができます。 次の例は、 _Manifestpath_パラメーターの値のファイルの場所を示しています。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

次の例に示すように、新しい組織のアドインコマンドレットを実行して、アドインをアップロードして、ユーザーまたはグループに直接割り当てることもできます。この場合、 _Members_パラメーターを使用します。 メンバーの電子メールアドレスはコンマで区切ります。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Office ストアからアドインをアップロードする
<a name="BKMK_UploadAddin"> </a>

新しい-組織の Addin コマンドレットを実行して、Office ストアからマニフェストをアップロードします。
  
次の例では、新しい-組織の Addin コマンドレットは、米国の場所とコンテンツ市場のためにアドインの AssetId を指定しています。
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

_Assetid_パラメーターの値を確認するには、アドインの Office ストア web ページの URL からコピーします。 AssetIds は常に "WA" で始まり、その後に数字が続きます。 たとえば、前の例では、WA104099688 の AssetId 値のソースは、アドイン[https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)の Office ストアの web ページの URL です。
  
_Locale_パラメーターと_contentmarket_パラメーターの値は一致しており、アドインをインストールしようとしている国/地域を示しています。 この形式は en-us (fr-fr) です。 など。 
  
> [!NOTE]
> Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。 
  
## <a name="get-details-of-an-add-in"></a>アドインの詳細を取得する
<a name="BKMK_GetDetails"> </a>

次に示すように、Get-help Addin コマンドレットを実行して、テナントにアップロードされたすべてのアドインの詳細を取得し、アドインの製品 ID を含めます。
  
```
Get-OrganizationAddIn
```

_ProductId_パラメーターの値を指定して取得し、詳細を取得するアドインを指定するには、このコマンドレットを実行します。 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

すべてのアドインおよび割り当てられたユーザーとグループの詳細を取得するには、次の例に示すように、コマンドレットの出力を Format コマンドレットにパイプ処理します。
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>アドインをオンまたはオフにする
<a name="BKMK_TurnOnOff"> </a>

ユーザーおよびグループに割り当てられているグループがアクセスできなくなるようにアドインを無効にするには、次の例に示すように、 _ProductId_パラメーターと_Enabled_パラメーターを`$false`に設定して、このコマンドレットを実行します。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

アドインを再び有効にするには、_有効な_パラメーターをに`$true`設定して、同じコマンドレットを実行します。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>アドインに対してユーザーを追加または削除する
<a name="BKMK_AddRemove"> </a>

ユーザーおよびグループを特定のアドインに追加するには、 _ProductId_、 _Add_、および_Members_の各パラメーターを指定して、リソースの設定コマンドレットを実行します。 メンバーの電子メールアドレスはコンマで区切ります。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

ユーザーおよびグループを削除するには、 _remove_パラメーターを使用して同じコマンドレットを実行します。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

テナントのすべてのユーザーにアドインを割り当てるには、の値をに`$true`設定して、Assign _toeveryone_パラメーターを使用して同じコマンドレットを実行します。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

すべてのユーザーにアドインを割り当てずに、以前に割り当てられたユーザーおよびグループに戻すには、同じコマンドレットを実行し、その値をに`$false`設定して、Assign _toeveryone_パラメーターをオフにします。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>アドインを更新する
<a name="BKMK_UpdateAddin"> </a>

マニフェストからアドインを更新するには、次の例に示すように、 _ProductId_、 _manifestpath_、および_Locale_パラメーターを使用して、次のように設定して、このコマンドレットを実行します。 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Office ストアからアップロードされたアドインは、Office ストアで入手可能な最新の更新プログラムから数日以内に自動的に更新されます。 
  
## <a name="delete-an-add-in"></a>アドインを削除する
<a name="BKMK_Delete"> </a>

アドインを削除するには、次の例に示されているように、 _ProductId_パラメーターを指定して、[削除] コマンドレットを実行します。 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>各コマンドレットの詳細なヘルプを取得する
<a name="BKMK_GetHelp"> </a>

各コマンドレットの詳細については、「get-help」を参照してください。 たとえば、次のコマンドレットは、このコマンドレットに関する詳細な情報を提供します。
  
```
Get-help Remove-OrganizationAddIn -Full
```


