---
title: Office 365 PowerShell を使用して SharePoint Online サイト グループを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '使用 Office 365 PowerShell を概要: SharePoint Online サイト グループを管理します。'
ms.openlocfilehash: 68be9ce3ef26cb46df6d43716c6719ffd9c172e2
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Office 365 PowerShell を使用して SharePoint Online サイト グループを管理する

 **の概要:** SharePoint Online サイト グループを管理するのにには、Office 365 の PowerShell を使用します。
  
Office 365 の管理ページを使用できますが、SharePoint Online サイト グループを管理するために Office 365 の PowerShell を使用することができますも。

## <a name="before-you-begin"></a>はじめに

この資料の手順では、SharePoint Online に接続する必要があります。手順については、 [SharePoint のオンライン PowerShell への接続](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)を参照してください。

## <a name="view-sharepoint-online-with-office-365-powershell"></a>SharePoint を Office 365 の PowerShell でオンラインに表示

SharePoint Online 管理センターでは、サイト グループを管理するためのいくつかの簡単に使用できる方法があります。たとえばのグループ、およびグループのメンバーを参照する、https://litwareinc.sharepoint.com/sites/financeサイトです。ために何が必要です。

1. Office 365 管理センターで、[**リソース**] をクリックします > **のサイト**サイトの URL をクリックします。
2. サイト コレクション] ダイアログ ボックスで**、このサイト**をクリックします。
3. [サイト] ページで (ページの右上隅にあります)**の設定**] アイコンをクリックし、[**サイトの設定**] をクリックします。</br>
![SharePoint Online サイトの設定](images/spo-site-settings.png)</br>
4. [サイトの設定] ページで、[**ユーザーと権限****のサイトのアクセス許可**をクリックします。

参照する次のサイトでも、このプロセスを繰り返します。

Office 365 PowerShell でグループの一覧を取得するには、次のコマンド セットを使用します。

```
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

SharePoint のオンライン管理シェルのコマンド プロンプトで設定このコマンドを実行する 2 つの方法があります。
- コマンドをメモ帳 (または別のテキスト エディターにコピー、 **$siteURL**変数の値を変更、コマンドを選択、および SharePoint のオンライン管理シェルのコマンド プロンプトに貼り付けること。PowerShell で停止するには、ときに、>> プロンプトします。実行するのには Enter キーを押して、コマンドごとにします。</br>
- メモ帳 (または別のテキスト エディター) にコマンドをコピー、 **$siteURL**変数の値を変更、名前と適切なフォルダーに .ps1 拡張子を持つテキスト ファイルを保存します。次に、そのパスとファイル名を指定することによって SharePoint のオンライン管理シェルのコマンド プロンプトからスクリプトを実行します。例を以下に示します。</br>
```
C:\Scripts\SiteGroupsAndUsers.ps1
```</br>

In both cases, you should see something similar to this:

![SharePoint Online site groups](images/SPO-site-groups.png)

These are all the groups that have been created for the site https://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.

As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.

```
$x = get SPOSite foreach ($x に $y) {書き込みホスト $y.Url の前景色「黄色」$z = Get SPOSiteGroup-サイト $y.Url foreach ($ の $z) {$b = Get SPOSiteGroup-$y.Url のサイトのグループの $a.Title 書き込みホスト $b.Title の前景色「シアン」$b |ホストの選択オブジェクトの ExpandProperty ユーザー書き込み}}
```
    
## See also

[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[Create SharePoint Online sites and add users with Office 365 PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Manage SharePoint Online users and groups with Office 365 PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Manage Office 365 with Office 365 PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Getting started with Office 365 PowerShell](getting-started-with-office-365-powershell.md)

