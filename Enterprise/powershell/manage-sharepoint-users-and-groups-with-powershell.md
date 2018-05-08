---
title: Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '使用して Office 365 PowerShell を概要: SharePoint Online のユーザー、グループ、およびサイトを管理します。'
ms.openlocfilehash: a04bf1538d6f56b760932b5be89b1953fcaa33d5
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a>Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する

 **の概要:** Office 365 の PowerShell を使用すると、SharePoint Online のユーザー、グループ、およびサイトを管理できます。

SharePoint Online 管理者ユーザー アカウントまたはグループの大規模なリストで動作し、それを管理する簡単な方法を希望する場合は、Office 365 の PowerShell を使用することができます。 

## <a name="before-you-begin"></a>はじめに

このトピックの手順では、SharePoint Online に接続する必要があります。手順については、 [SharePoint のオンライン PowerShell への接続](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)を参照してください。

## <a name="get-a-list-of-sites-groups-and-users"></a>サイト、グループ、ユーザーの一覧を取得する

ユーザーとグループを管理する前に、サイト、グループ、ユーザーの一覧を取得する必要があります。この情報は、この記事の例全体を通して使用できます。

### <a name="get-a-list-of-sites"></a>サイトの一覧を取得する

次のコマンドを使用して、テナント内のサイトの一覧を取得します。

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a>グループの一覧を取得する

次のコマンドを使用して、テナント内のグループの一覧を取得します。

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a>ユーザーの一覧を取得する

次のコマンドを使用して、テナント内のユーザーの一覧を取得します。

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>サイト コレクション管理者グループにユーザーを追加する

**セット SPOUser**コマンドを使用するにはサイト コレクションのサイト コレクションの管理者のリストにユーザーを追加します。これは、構文は次の方法です。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

これらのコマンドを使用するには、置換を置換など、二重引用符内のすべての < および > 文字は、正しい名前を持つ。

この一連のコマンドを追加するなど Opal Castillo (ユーザー名 opalc) サイト コレクションの管理者の一覧 contoso1 テナント内の ContosoTest のサイト コレクションにします。

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

コピーしこれらのコマンドをメモ帳に貼り付けます、$tenant、$site、$user のお客様の環境からの実際の値に変数の値を変更して、これをそれらを実行するのには、SharePoint のオンライン管理シェルのウィンドウに貼り付けます。

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a>他のサイト コレクション管理者グループにユーザーを追加する

このタスクでのサイト コレクションで SharePoint グループにユーザーを追加するのには、**追加 SPOUser**コマンド使用します。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

などの追加がきました (ユーザー名 glenr) contoso1 テナント内の ContosoTest のサイト コレクションの監査グループに。

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>サイト コレクション グループを作成する

**セット SPOSiteGroup**コマンドを使用するには、新しい SharePoint グループを作成し、ContosoTest のサイト コレクションに追加します。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
**セット SPOSiteGroup**コマンドレットを使用してアクセス許可レベルなど、グループのプロパティを後で更新できます。

など contoso1 テナントの contoso 社のテスト サイト コレクションを見て表示のみのアクセス許可と監査人グループを追加します。

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>グループからユーザーを削除する

場合によっては、あるサイトまたはすべてのサイトからユーザーを削除する必要があります。たとえば、従業員がある部署から別の部署に異動した場合や、退職した場合などが該当します。対象の従業員が 1 人のみの場合は UI で簡単に削除できますが、部署全体をあるサイトから別のサイトに移動する場合は容易ではありません。

ただし、SharePoint のオンライン管理シェルと CSV ファイルを使用すると、これは、迅速かつ容易です。このタスクでは、サイト コレクションのセキュリティ グループからユーザーを削除するのには Windows PowerShell を使用します。CSV ファイルを使用し、別のサイトから多数のユーザーを削除します。 

ようにコマンドの構文を参照してください、サイト コレクションのグループから 1 つの Office 365 ユーザーを削除するのに**削除 SPOUser**コマンドを使用しています。構文は次の方法を以下に示します。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
たとえば、contoso1 テナントの contoso 社のテスト サイト コレクションのサイト コレクションの監査人グループから見て村中 Overby を削除します。

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Bobby を現在彼が所属しているすべてのグループから削除するとしたら、以下の方法があります。

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> これは、単なる例です。ユーザーが会社を辞める場合など、すべてのグループからユーザーを削除する必要がある本当にしない限りは、このコマンドを実行する必要があります。

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>ユーザーおよびグループの大規模なリストの管理を自動化する

多数のアカウントを SharePoint サイトに追加し、アクセス許可を与える、Office 365 管理者センター、個々 の PowerShell コマンド、または PowerShell を使用することができますが、CSV ファイルです。これらのオプションでは、CSV ファイルがこのタスクを自動化する最も簡単な方法です。

基本的なプロセスでは、Windows PowerShell スクリプトが必要なパラメーターに対応する見出し (列) を CSV ファイルを作成します。Excel でこのようなリストを簡単に作成し、CSV ファイルとしてエクスポートできます。次に、Windows PowerShell スクリプトを使用して、グループとサイト グループにユーザーを追加することを CSV ファイル内のレコード (行) を反復処理します。 

例として、サイト コレクション、グループ、アクセス許可を定義する CSV ファイルを作成します。次に、グループにユーザーを取り込むための CSV ファイルを作成します。最後に、グループを作成してユーザーを取り込む単純な Windows PowerShell スクリプトを作成して実行します。

最初の CSV ファイルは、1 つ以上のグループを 1 つ以上のサイト コレクションに追加します。このファイルの構造は以下のとおりです。

### <a name="header"></a>ヘッダー:

```
Site,Group,PermissionLevels
```

### <a name="item"></a>項目:

```
https://tenant.sharepoint.com/sites/site,group,level
```

以下は、サンプル ファイルです。

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

2 番目の CSV ファイルは、1 つ以上のユーザーを 1 つ以上のグループに追加します。このファイルの構造は以下のとおりです。

### <a name="header"></a>ヘッダー:

```
Group,LoginName,Site
```

### <a name="item"></a>項目:

```
group,login,https://tenant.sharepoint.com/sites/site
```

以下は、サンプル ファイルです。

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

次の手順では、2 つの CSV ファイルをドライブに保存する必要があります。両方の CSV ファイルを使用するコマンドの例を挙げますとグループ メンバーシップをアクセス許可を追加するとします。

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

スクリプトでは、CSV ファイルの内容をインポートし、**新規 SPOSiteGroup**および**追加 SPOUser**コマンドのパラメーターを設定するのには、列の値を使用します。例では、私たちはこのフォルダーに保存 theO365Admin、C ドライブには任意の場所に保存することができます。

ここで、同じ CSV ファイルを使用して別のサイト内のいくつかのグループのユーザーを削除します。コマンドの例を以下に示します。

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>ユーザー レポートを生成する

いくつかのサイトに関する単純なレポートを取得して、該当するサイトのユーザーと各ユーザーのアクセス許可レベルやその他のプロパティを表示しなければならない場合があります。以下に、構文の一例を示します。

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

これら 3 つのサイトのデータを取得され、ローカル ドライブ上のテキスト ファイルに書き込みます。なおパラメーター – 追加は、既存のファイルに新しいコンテンツを追加します。

たとえば、Contoso1 テナントの ContosoTest サイト、TeamSite01 サイト、および Project01 サイトでレポートを実行します。

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

**$Site**変数のみを変更しなければならなかったことに注意してください。**$Tenant**変数は、コマンドのすべての 3 つの実行を使用してその値を保持します。

一方、この操作をすべてのサイトに対して行うとしたら、どうなるでしょうか。以下のコードを使用すれば、すべての Web サイトを入力することなく、このコマンドを使用できます。

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

このレポートは非常に簡単で、および特定のレポートまたは詳細な情報を含むレポートを作成するコードを追加することができます。ことができるよう環境を SharePoint Online でユーザーを管理するために SharePoint のオンライン管理シェルを使用する方法のことをお勧めします。
   
## <a name="see-also"></a>関連項目

[SharePoint のオンライン PowerShell への接続します。](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Office 365 PowerShell を使用して SharePoint Online を管理する](create-sharepoint-sites-and-add-users-with-powershell.md)

[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

