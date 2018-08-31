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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>一元的な展開の PowerShell コマンドレットを使用して、アドインを管理するには

一元的な展開を使用してユーザーに Office のアドインを配置する、Office 365 の管理者として機能の ( [Office 365 の管理センターでの Office 365 のアドインの展開の管理](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)を参照してください)。Office 365 の管理センターを使用して Office のアドインを配置するには、Microsoft の PowerShell を使用することもできます。[ダウンロード](https://go.microsoft.com/fwlink/p/?linkid=850850)Microsoft ダウンロード センターから一元的な展開の PowerShell コマンドレットをします。 
  
## <a name="what-do-you-want-to-do"></a>必要な作業

[管理者の資格情報を使用して接続します。](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[アドイン マニフェストをアップロードします。](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[Office ストアからのアップロードします。](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[アドインの詳細情報を取得します。](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[オンまたはアドインを無効にします。](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[追加または削除ユーザーの追加](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[アドインを更新します。](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[アドインを削除します。](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[各コマンドレットの詳細なヘルプを表示します。](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>管理者の資格情報を使用して接続します。
<a name="BKMK_Connect"> </a>

一元的な展開のコマンドレットを使用できますが、サインインする必要があります。
  
1. PowerShell を開始します。
    
2. PowerShell に接続するには、会社の管理者の資格情報を使用します。次のコマンドレットを実行します。
    
  ```
  Connect-OrganizationAddInService
  ```

3. **資格情報の入力**」ページで、Office 365 グローバル管理者の資格情報を入力します。代わりに、コマンドレットに直接資格情報を入力できます。 
    
    PSCredential オブジェクトとして管理者の資格情報、会社を指定する次のコマンドレットを実行します。
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> PowerShell を使用の詳細については、 [Office 365 の PowerShell への接続](https://go.microsoft.com/fwlink/p/?linkid=848585)を参照してください。 
  
## <a name="upload-an-add-in-manifest"></a>アドイン マニフェストをアップロードします。
<a name="BKMK_UploadManifest"> </a>

コマンドレットを実行、新規の OrganizationAdd ので、パスは、ファイルの場所または URL のいずれかから、追加のマニフェストをアップロードします。_ManifestPath_パラメーターの値を作成するファイルの場所の例を次に示します。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

アドインをアップロードし、そのユーザーまたはグループに、_メンバー_のパラメーターを使用すると、次の例のように新規の OrganizationAdd-にコマンドレットを実行することもできます。メンバーの電子メール アドレスをコンマで区切ります。 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Office ストアからのアップロードします。
<a name="BKMK_UploadAddin"> </a>

Office ストアから、マニフェストをアップロードするのには新規 OrganizationAddIn コマンドレットを実行します。
  
次の例では、新規 OrganizationAddIn コマンドレットは、アメリカ合衆国の位置とコンテンツ市場のアドインの AssetId を指定します。
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

_AssetId_パラメーターの値を調べるには、"WA"に続けて番号を使用してアドインの AssetIds の web ページが常に開始 Office ストアの URL からコピーすることができます。たとえば、前の例では、WA104099688 の AssetId 値のソースは、アドインを Office ストアの web ページの URL: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)。
  
_ロケール_パラメーターを使用し、 _ContentMarket_パラメーターの値は、同じからアドインをインストールしようとしている国/地域を示します。形式は、EN-US、fr FR. などです。 
  
> [!NOTE]
> Office ストアからアップロードされたアドインは、Office ストアで使用される最新の更新プログラムの数日間で自動的に更新されます。 
  
## <a name="get-details-of-an-add-in"></a>アドインの詳細情報を取得します。
<a name="BKMK_GetDetails"> </a>

次のように、Get OrganizationAddIn コマンドレットを実行、テナントにアップロードするすべてのアドインの詳細情報を取得するのには含まれているアドインの製品 id。
  
```
Get-OrganizationAddIn
```

するアドインを指定の詳細を取得する _[商品コード]_ パラメーターの値を取得 OrganizationAddIn コマンドレットを実行します。 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

すべてのアドインと、割り当てられたユーザーとグループの完全な詳細情報を取得するには、次の例に示すように Format-list コマンドレットでは、Get OrganizationAddIn コマンドレットの出力をパイプします。
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>オンまたはアドインを無効にします。
<a name="BKMK_TurnOnOff"> </a>

無効にするアドインをユーザーとそれに割り当てられているグループは、アクセスするため、 _[商品コード]_ パラメーターと設定_Enabled_パラメーター セット OrganizationAddIn コマンドレットを実行`$false`次の例のように、です。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

アドインを追加するには、 _Enabled_パラメーターを設定と同じコマンドレットを実行します。 `$true`。
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>追加または削除ユーザーの追加
<a name="BKMK_AddRemove"> </a>

特定のアドインにユーザーおよびグループを追加するには、 _[商品コード]_、_追加_、および_メンバー_のパラメーターを使用してセット OrganizationAddInAssignments コマンドレットを実行します。メンバーの電子メール アドレスをコンマで区切ります。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

ユーザーおよびグループを削除するには、_削除する_パラメーターを使用して同じコマンドレットを実行します。 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

テナントのすべてのユーザーを追加で割り当てるには、 _AssignToEveryone_パラメーターを使用して値設定して同じコマンドレットを実行`$true`。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

ないアドインをすべてのユーザーを割り当てるし、以前に割り当てられたユーザーとグループを元に戻す、同じコマンドレットを実行し、オフに_AssignToEveryone_パラメーターその値を設定する`$false`。
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>アドインを更新します。
<a name="BKMK_UpdateAddin"> </a>

マニフェストからアドインを更新するには、次の例に示すように、_商品コード_、 _ManifestPath_、および_ロケール_パラメーターをセット OrganizationAddIn コマンドレットを実行します。 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Office ストアからアップロードされたアドインは、Office ストアで使用される最新の更新プログラムの数日間で自動的に更新されます。 
  
## <a name="delete-an-add-in"></a>アドインを削除します。
<a name="BKMK_Delete"> </a>

アドインを削除するには、次の例のように、 _[商品コード]_ パラメーターで削除 OrganizationAddIn コマンドレットを実行します。 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>各コマンドレットの詳細なヘルプを表示します。
<a name="BKMK_GetHelp"> </a>

Get-help コマンドレットを使用して、各コマンドレットの詳細なヘルプを表示できます。たとえば、次のコマンドレットは、削除 OrganizationAddIn コマンドレットの詳細についてを提供します。
  
```
Get-help Remove-OrganizationAddIn -Full
```


