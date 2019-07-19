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
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>一元展開 PowerShell コマンドレットを使用してアドインを管理する

Microsoft 365 グローバルまたは Exchange 管理者は、一元展開機能を使用して Office アドインをユーザーに展開できます (「[管理センターで Office アドインを展開](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)する」を参照してください)。 Microsoft 365 管理センター経由で Office アドインを展開することに加えて、Microsoft PowerShell を使用することもできます。 [Windows PowerShell 用 O365 中央アドイン展開モジュール](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment)をインストールします。 

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

_Assetid_パラメーターの値を確認するには、アドインの Office ストア web ページの URL からコピーします。 AssetIds は常に "WA" で始まり、その後に数字が続きます。 たとえば、前の例では、WA104099688 の AssetId 値のソースは、アドイン[https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688)の Office ストアの web ページの URL です。
  
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

すべてのアドインおよび割り当てられたユーザーとグループの詳細を取得するには、次の例**** に示すように、コマンドレットの出力を Format コマンドレットにパイプ処理します。
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>アドインをオンまたはオフにする

ユーザーおよびグループに割り当てられているグループがアクセスできなくなるようにアドインを無効にするには**** 、次の例に示すように、 _ProductId_パラメーターと_Enabled_パラメーターを`$false`に設定して、このコマンドレットを実行します。.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

アドインを再び有効にするには、_有効な_パラメーターをに`$true`設定して、同じコマンドレットを実行します。
  
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

テナントのすべてのユーザーにアドインを割り当てるには、の値をに`$true`設定して、Assign _toeveryone_パラメーターを使用して同じコマンドレットを実行します。
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

すべてのユーザーにアドインを割り当てずに、以前に割り当てられたユーザーおよびグループに戻すには、同じコマンドレットを実行し、その値をに`$false`設定して、Assign _toeveryone_パラメーターをオフにします。
  
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

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a>組織の Microsoft Store アドインをカスタマイズする

組織に展開する前に、アドインをカスタマイズする必要があります。 バージョン1.1 より前のアドインは、この機能ではサポートされていません。 

また、次の制限に注意してください。
- すべての Url は、絶対 (http または https を含む) であり、有効である必要があります。
- *DisplayName*は125文字以下にする必要があります 
- *DisplayName*、 *Resources* 、および*AppDomains*には、次の文字を含めることはできません。 
 
    - \<
    -  \>
    -  ;
    -  =   

展開されているアドインをカスタマイズする場合は、管理センターでアンインストールする必要があり、展開されている各コンピューターから削除する手順については、「[ローカルキャッシュからアドインを削除](#remove-an-add-in-from-local-cache)する」を参照してください。

アドインをカスタマイズするには、パラメーターとして*ProductId*を指定して**Set –組織**の上書きコマンドレットを実行し、その後に、上書きするタグと新しい値を指定します。 *ProductId*を取得する方法については、この記事の「[アドインの詳細を取得](#get-details-of-an-add-in)する」を参照してください。 次に例を示します。

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
アドインの複数のタグをカスタマイズするには、これらのタグを commandline に追加します。

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> 1つのコマンドとして、1つのアドインに複数のカスタマイズされたタグを適用する必要があります。 タグを1つずつカスタマイズした場合は、最後のカスタマイズのみが適用されます。 また、誤ってタグをカスタマイズした場合は、すべてのカスタマイズを削除して最初からやり直す必要があります。

### <a name="tags-you-can-customize"></a>カスタマイズできるタグ

| Tag                  | 説明          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| アドインのアイコンとして使用されるイメージの URL (管理センター内)。 </br> |
| \<DisplayName>| アドインのタイトル (管理センター)。|
| \<Hosts>| アドインをサポートするアプリの一覧。|
| \<SourceLocation> | アドインが接続する元の URL。| 
| \<AppDomains> | アドインが接続できるドメインの一覧。 | 
| \<SupportURL>| ユーザーがヘルプとサポートにアクセスするために使用できる URL。 | 
| \<リソース>  | このタグには、タイトル、ツールヒント、さまざまなサイズのアイコンなど、いくつかの要素が含まれています。| 
|
### <a name="customize-resources-tag"></a>リソースのカスタマイズタグ

マニフェストの<Resources>タグ内の要素は、動的にカスタマイズできます。 最初に、マニフェストをチェックして、新しい値を割り当てる要素の id を見つける必要があります。 タグ<Resources>は次のようになります。

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
この例では、イメージの要素 id は "img16icon" で、それに関連付けられている値<i></i>は "http://サイトです。<i> </i>com/img. "

カスタマイズする要素を特定したら、Powershell で次のコマンドを使用して、要素に新しい値を割り当てます。

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

必要に応じて、コマンドを使用して複数の要素をカスタマイズできます。

### <a name="remove-customization-from-an-add-in"></a>アドインからカスタマイズを削除する

現在、カスタマイズを削除するために使用できるオプションは、一度にすべてを削除することです。

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a>アドインのカスタマイズを表示する

適用されているカスタマイズの一覧を表示するには、" **Get-help Addinoverrides/上書き**" コマンドレットを実行します。 **取得**した引数が*ProductId*なしで実行される場合は、オーバーライドが適用されたすべてのアドインのリストが返されます。  

```powershell
Get-OrganizationAddInOverrides 
```
ProductId が指定されている場合、そのアドインに適用されたオーバーライドの一覧が返されます。 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a>ローカルキャッシュからアドインを削除する

アドインが展開されている場合は、カスタマイズできるようにするために、各コンピューターのキャッシュから削除する必要があります。 アドインをキャッシュから再作成するには、次のようにします。

1. C:\ の "Users" フォルダーに移動します。 
1. ユーザーフォルダーに移動します。
1. AppData\Local\Microsoft\Office に移動し、Office のバージョンに関連付けられているフォルダーを選択します。
1. *Wef*フォルダーで、[*マニフェスト*] フォルダーを削除します。

## <a name="get-detailed-help-for-each-cmdlet"></a>各コマンドレットの詳細なヘルプを取得する

各コマンドレットの詳細については、「get-help」を参照してください。 たとえば、次のコマンドレットは、このコマンドレットに関する詳細な情報を提供します。
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


