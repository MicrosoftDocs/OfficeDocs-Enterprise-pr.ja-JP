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
ms.openlocfilehash: 881e67b7eb2d8bb5e04f83e28569aa54341d16b9
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Office 365 PowerShell を使用して SharePoint Online サイト グループを管理する

 **の概要:** SharePoint Online サイト グループを管理するのにには、Office 365 の PowerShell を使用します。
  
Office 365 の管理ページを使用できますが、SharePoint Online サイト グループを管理するために Office 365 の PowerShell を使用することができますも。

## <a name="before-you-begin"></a>はじめに

この資料の手順では、SharePoint Online に接続する必要があります。手順については、 [SharePoint のオンライン PowerShell への接続](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)を参照してください。

## <a name="view-sharepoint-online-with-office-365-powershell"></a>SharePoint を Office 365 の PowerShell でオンラインに表示

SharePoint Online 管理センターでは、サイト グループを管理するためのいくつかの簡単に使用できる方法があります。たとえば、グループ、および https に対して、グループのメンバーを参照する\://litwareinc.sharepoint.com/sites/finance のサイトです。ために何が必要です。

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

- コマンドをメモ帳 (または別のテキスト エディターにコピー、 **$siteURL**変数の値を変更、コマンドを選択、および SharePoint のオンライン管理シェルのコマンド プロンプトに貼り付けること。PowerShell で停止するには、ときに、**>>** プロンプトします。**Foreach**コマンドを実行するには、enter キーを押します。</br>
- メモ帳 (または別のテキスト エディター) にコマンドをコピー、 **$siteURL**変数の値を変更、名前と適切なフォルダーに .ps1 拡張子を持つテキスト ファイルを保存します。次に、そのパスとファイル名を指定することによって SharePoint のオンライン管理シェルのコマンド プロンプトからスクリプトを実行します。コマンドの例を以下に示します。

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

どちらの場合も、次のように表示されるはずです。

![SharePoint Online サイト グループ](images/SPO-site-groups.png)

サイトの https 用に作成されたすべてのグループは、\:/すべてのユーザーだけでなく、litwareinc.sharepoint.com/sites/finance、それらのグループに割り当てられているとします。グループ名は、そのメンバーからの別のグループ名を支援するのには黄色では。

別の例として、グループ、およびすべての SharePoint Online サイトのすべてのグループのメンバーシップを一覧表示するコマンドのセットです。

```
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title 
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```
    
## <a name="see-also"></a>関連項目

[SharePoint のオンライン PowerShell への接続します。](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[SharePoint Online サイトを作成し、Office 365 の PowerShell でユーザーを追加します。](create-sharepoint-sites-and-add-users-with-powershell.md)

[Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する](manage-sharepoint-users-and-groups-with-powershell.md)

[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

