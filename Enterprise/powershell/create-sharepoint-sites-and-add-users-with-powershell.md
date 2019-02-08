---
title: Office 365 PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '概要: Office 365 PowerShell を使用して SharePoint Online の新しいサイトを作成し、それらのサイトにユーザーおよびグループを追加します。'
ms.openlocfilehash: 61b9338469ed8d01abc76edbf14ed448c3ca00d3
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897170"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a>Office 365 PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する

 **の概要:** Office 365 の PowerShell を使用して、新しい SharePoint Online サイトを作成し、それらのサイトにユーザーおよびグループを追加します。

Office 365 の PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加すると、迅速かつ繰り返しタスクを実行できます Office 356 管理センターでよりもはるかに高速です。Office 356 管理センターで実行することができないタスクも実行できます。 

## <a name="before-you-begin"></a>始める前に

このトピックの手順では、SharePoint Online に接続する必要があります。手順については、 [SharePoint のオンライン PowerShell への接続](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)を参照してください。

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a>手順 1: Office 365 PowerShell を使って新しいサイト コレクションを作成する

Office 365 の PowerShell とサンプル コードが用意されているとメモ帳を使用して作成した .csv ファイルを使用して複数のサイトを作成します。この手順では、独自のサイトやテナント固有の情報をかっこで囲んで表示されているプレース ホルダー情報を交換することです。このプロセスでは、1 つのファイルを作成し、そのファイルを使用する 1 つの Office 365 の PowerShell コマンドを実行することができます。これは、繰り返しとポータブルの両方を実行する操作し、SharePoint のオンライン管理シェルに長いコマンドを入力することによってもたらされる、すべてのエラーの場合、多くが不要します。このプロシージャに 2 つの部分があります。まず .csv ファイルを作成し、その内容を使用してサイトを作成する、Office 365 PowerShell を使用して .csv ファイルを参照します。

Office 365 PowerShell コマンドレットは、その .csv ファイルをインポートし、ファイルの最初の行を列見出しとして読み取る、中かっこ内のループにパイプします。次に、Office 365 PowerShell コマンドレットは、残りのレコードを反復処理し、レコードごとに新規のサイト コレクションを作成し、列見出しに従ってサイト コレクションのプロパティを割り当てます。

### <a name="create-a-csv-file"></a>.csv ファイルの作成

1. メモ帳を開き、次のテキスト ブロックを貼り付けます。<br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/>プライマリ サイト コレクション管理者の役割を付与する*テナント*が、テナントの名前、*所有者*は、先のテナントのユーザーのユーザー名。<br/>(することができます押して Ctrl + H 置換を高速に一括してメモ帳を使用する場合)。<br/>

2. デスクトップ上のファイルを**SiteCollections.csv**として保存します。<br/>

> [!TIP]
> これまたはその他の .csv ファイルまたは Windows PowerShell スクリプト ファイルを使用する前に不要なまたは印刷されない文字がないかどうかを確認することをお勧めします。Word と、リボンの [ファイルを開く、編集記号を表示するのには [段落] アイコンをクリックします。不要な記号はないはずです。などはないはず、ファイルの末尾に最後の 1 つ以上の段落記号です。

### <a name="run-the-windows-powershell-command"></a>Windows PowerShell コマンドの実行

1. Windows PowerShell プロンプトで、次のコマンドレットを入力するか、コピーして貼り付け、Enter キーを押します。<br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/>場所*MyAlias*は、ユーザーのエイリアスと同じです。<br/>

2. WindowsPowerShell プロンプトが再度表示されるまで待機します。これには 1 - 2 分かかる場合があります。<br/>

3. Windows PowerShell プロンプトで、次のコマンドレットを入力するか、コピーして貼り付け、Enter キーを押します。<br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. 一覧に新しいサイト コレクションに注意してください。次のサイト コレクションを参照する必要があります: **contosotest**、 **TeamSite01**、 **Blog01**、および**Project01**

これで完了です。作成した .csv ファイルと 1 つの WindowsPowerShell コマンドレットを使用して、複数のサイト コレクションを作成しました。これで、ユーザーを作成してこれらのサイトに割り当てる準備ができました。

## <a name="step-2-add-users-and-groups"></a>手順 2:ユーザーおよびグループの追加

ここでは、ユーザーを作成し、サイト コレクションのグループに追加します。次に、.csv ファイルを使用して、新しいグループとユーザーを一括アップロードします。

次の手順では、サイト コレクションの contosotest、TeamSite01、Blog01、Project01 が正常に作成されていることが前提になっています。

### <a name="create-csv-and-ps1-files"></a>.csv ファイルおよび .ps1 ファイルの作成

1. メモ帳を開き、次のテキスト ブロックを貼り付けます。<br/>
```
Site,Group,PermissionLevels
https://tenant.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://tenant.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://tenant.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```
<br/>*テナント*に等しい、テナント名を指定します。<br/>

2. **GroupsAndPermissions.csv**として、ファイルをデスクトップに保存します。<br/>

3. メモ帳の新しいインスタンスを開き、次のテキストのブロックを貼り付けます。<br/>

```
Group,LoginName,Site
Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/contosotest
XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
```
<br/>*テナント*に等しい、テナント名、*ユーザー名*が既存のユーザーのユーザー名と同じです。<br/>

4. として**ユーザー.csv**ファイルをデスクトップに保存します。<br/>

5. メモ帳の新しいインスタンスを開き、次のテキストのブロックを貼り付けます。<br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/>MyAlias に等しい現在ログオンしているユーザーのユーザー名を指定します。<br/>

6. **UsersAndGroups.ps1**として、ファイルをデスクトップに保存します。これは、単純な Windows PowerShell スクリプトです。

これで、UsersAndGroup.ps1 スクリプトを実行して複数のサイト コレクションにユーザーとグループを追加する準備ができました。

### <a name="run-usersandgroupsps1-script"></a>UsersAndGroups.ps1 スクリプトの実行

1. SharePoint Online 管理シェルに戻ります。<br/>
2. Windows PowerShell プロンプトで、次の行を入力するか、コピーして貼り付け、Enter キーを押します。<br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. 確認プロンプトで、 **Y**をキーを押します。<br/>

4. Windows PowerShell プロンプトで、次のコマンドを入力するか、コピーして貼り付け、Enter キーを押します。<br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/>*MyAlias*に等しい自分のユーザー名を指定します。<br/>

5. プロンプトが戻るまで待機してから、次に進みます。最初に、作成したとおりにグループが表示されます。次に、ユーザーを追加するたびに、グループの一覧が繰り返し表示されます。

## <a name="see-also"></a>関連項目

[SharePoint Online PowerShell に接続する](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Office 365 の PowerShell SharePoint Online のサイト グループを管理します。](manage-sharepoint-site-groups-with-powershell.md)

[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

