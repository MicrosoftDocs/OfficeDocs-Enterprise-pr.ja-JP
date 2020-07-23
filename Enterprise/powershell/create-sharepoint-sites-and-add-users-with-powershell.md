---
title: PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '概要: PowerShell を使用して新しい SharePoint Online サイトを作成し、それらのサイトにユーザーとグループを追加します。'
ms.openlocfilehash: 2791b4de9388e3ff828a665aeeef5ada19627107
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230803"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する

*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*

Microsoft 365 に対して PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する場合、Microsoft 365 管理センターでの作業よりも迅速かつ繰り返し実行することができます。 また、Microsoft 365 管理センターでは実行できないタスクを実行することもできます。 

## <a name="before-you-begin"></a>はじめに

このトピックの手順では、SharePoint Online に接続する必要があります。 手順については、「 [SharePoint Online PowerShell への接続](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。

## <a name="step-1-create-new-site-collections-using-powershell"></a>手順 1: PowerShell を使用して新しいサイトコレクションを作成する

PowerShell を使用して複数のサイトを作成し、指定されたコード例およびメモ帳を使用して作成した .csv ファイルを作成します。 この手順では、角かっこに示されているプレースホルダー情報を、独自のサイトとテナント固有の情報に置き換えます。 このプロセスを使用すると、1つのファイルを作成し、そのファイルを使用する1つの PowerShell コマンドを実行することができます。 これにより、アクションが繰り返し可能で持ち運び可能になるため、SharePoint Online 管理シェルに長いコマンドを入力することによって発生する可能性のある多くのエラーが発生しなくなります。 この手順には2つの部分があります。 最初に .csv ファイルを作成してから、PowerShell を使用してその .csv ファイルを参照します。これにより、コンテンツを使用してサイトが作成されます。

PowerShell コマンドレットは .csv ファイルをインポートして、ファイルの最初の行を列の見出しとして読み取る波かっこ内のループにパイプ処理します。 PowerShell コマンドレットは、残りのレコードを反復処理し、各レコードに対して新しいサイトコレクションを作成し、列ヘッダーに従ってサイトコレクションのプロパティを割り当てます。

### <a name="create-a-csv-file"></a>.csv ファイルの作成

1. メモ帳を開き、次のテキスト ブロックを貼り付けます。<br/>

```powershell
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>ここで、 *tenant*はテナントの名前で、 *owner*は、サイトコレクションの管理者の役割を付与するテナントのユーザー名です。<br/>メモ帳を使用して一括置換をすばやく実行するには、Ctrl + H キーを押します。<br/>

2. ファイルを**SiteCollections.csv**としてデスクトップに保存します。<br/>

> [!TIP]
> このまたはその他の .csv または Windows PowerShell スクリプトファイルを使用する前に、余分または印刷されない文字がないことを確認することをお勧めします。 Word でファイルを開き、リボンで [段落] アイコンをクリックすると、印刷されない文字が表示されます。 印刷されない余分の文字がないようにしてください。 たとえば、ファイルの末尾の最後の文字の後ろに段落記号があってはなりません。

### <a name="run-the-windows-powershell-command"></a>Windows PowerShell コマンドの実行

1. Windows PowerShell プロンプトで、次のコマンドを入力するか、コピーして貼り付け、Enter キーを押します。<br/>
```powershell
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>*Myalias*はユーザーエイリアスと同じです。<br/>

2. WindowsPowerShell プロンプトが再度表示されるまで待機します。これには 1 - 2 分かかる場合があります。<br/>

3. Windows PowerShell プロンプトで、次のコマンドレットを入力するか、コピーして貼り付け、Enter キーを押します。<br/>

```powershell
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. リストに新しいサイトコレクションが表示されることを確認します。 この例の CSV ファイルを使用すると、次のサイトコレクションが表示されます: **TeamSite01**、 **Blog01**、 **Project01**、および**Community01**

これで完了です。 作成した .csv ファイルと1つの Windows PowerShell コマンドを使用して複数のサイトコレクションを作成しました。 これで、ユーザーを作成してこれらのサイトに割り当てる準備ができました。

## <a name="step-2-add-users-and-groups"></a>手順 2:ユーザーおよびグループの追加

ここでは、ユーザーを作成し、サイト コレクションのグループに追加します。次に、.csv ファイルを使用して、新しいグループとユーザーを一括アップロードします。

次の手順では、TeamSite01、Blog01、Project01、Community01 というサイトの例を引き続き使用します。

### <a name="create-csv-and-ps1-files"></a>.csv ファイルおよび .ps1 ファイルの作成

1. メモ帳を開き、次のテキスト ブロックを貼り付けます。<br/>

```powershell
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>*テナント*はテナント名と同じです。<br/>

2. ファイルを**GroupsAndPermissions.csv**としてデスクトップに保存します。<br/>

3. メモ帳の新しいインスタンスを開き、次のテキストのブロックを貼り付けます。<br/>

```powershell
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>*テナント*はテナント名と同じで、 *username*は既存のユーザーのユーザー名と同じです。<br/>

4. ファイルを**Users.csv**としてデスクトップに保存します。<br/>

5. メモ帳の新しいインスタンスを開き、次のテキストのブロックを貼り付けます。<br/>

```powershell
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>MyAlias は、現在ログオンしているユーザーのユーザー名と同じです。<br/>

6. ファイルを**UsersAndGroups.ps1**としてデスクトップに保存します。 これは、単純な Windows PowerShell スクリプトです。

これで、UsersAndGroup.ps1 スクリプトを実行して複数のサイト コレクションにユーザーとグループを追加する準備ができました。

### <a name="run-usersandgroupsps1-script"></a>UsersAndGroups.ps1 スクリプトの実行

1. SharePoint Online 管理シェルに戻ります。<br/>
2. Windows PowerShell プロンプトで、次の行を入力するか、コピーして貼り付け、Enter キーを押します。<br/>
```powershell
Set-ExecutionPolicy Bypass
```
<br/>

3. 確認のプロンプトで、 **Y**キーを押します。<br/>

4. Windows PowerShell プロンプトで、次のコマンドを入力するか、コピーして貼り付け、Enter キーを押します。<br/>

```powershell
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>*Myalias*は、ユーザー名と同じです。<br/>

5. プロンプトが戻るまで待機してから、次に進みます。最初に、作成したとおりにグループが表示されます。次に、ユーザーを追加するたびに、グループの一覧が繰り返し表示されます。

## <a name="see-also"></a>関連項目

[SharePoint Online PowerShell に接続する](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[PowerShell を使用して SharePoint Online サイト グループを管理する](manage-sharepoint-site-groups-with-powershell.md)

[PowerShell を使用して Microsoft 365 を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 の PowerShell の概要](getting-started-with-office-365-powershell.md)

