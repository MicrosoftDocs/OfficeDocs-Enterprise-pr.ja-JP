---
title: PowerShell を使用して SharePoint Online サイト グループを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
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
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: この記事では、Microsoft 365 の PowerShell を使用して SharePoint Online サイトグループを管理する手順を検索します。
ms.openlocfilehash: 5df2b57db4ac57aaf7905346d090ccde2d96a11c
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605903"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>PowerShell を使用して SharePoint Online サイト グループを管理する

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

Microsoft 365 管理センターを使用することもできますが、Microsoft 365 の PowerShell を使用して SharePoint Online サイトグループを管理することもできます。

## <a name="before-you-begin"></a>はじめに

この記事の手順では、SharePoint Online に接続する必要があります。 手順については、「[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>Microsoft 365 の PowerShell を使用して SharePoint Online を表示する

SharePoint Online 管理センターには、サイトグループを管理するための使いやすい方法がいくつかあります。 たとえば、サイトのグループとグループメンバーを表示する場合を考え `https://litwareinc.sharepoint.com/sites/finance` ます。 必要な操作は次のとおりです。

1. SharePoint 管理センターで、[**アクティブなサイト**] をクリックし、サイトの URL をクリックします。
2. サイトページで、[**設定**] アイコン (ページの右上隅にある) をクリックし、[**サイトの権限**] をクリックします。

参照する次のサイトでも、このプロセスを繰り返します。

Microsoft 365 の PowerShell を使用してグループの一覧を取得するには、次のコマンドを使用します。

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

このコマンドセットを SharePoint Online 管理シェルコマンドプロンプトで実行するには、次の2つの方法があります。

- コマンドをメモ帳 (または別のテキストエディター) にコピーし、 **$siteURL**変数の値を変更し、コマンドを選択して、それらを SharePoint Online Management Shell コマンドプロンプトに貼り付けます。 実行すると、プロンプトで PowerShell が停止 **>>** します。 Enter キーを押して `foreach` コマンドを実行します。<br/>
- コマンドをメモ帳 (または別のテキスト エディター) にコピーし、**$siteURL** 変数の値を変更してから、このテキスト ファイルを .ps1 という拡張子の付いた名前で適切なフォルダーに保存します。 次に、そのパスとファイル名を指定して、SharePoint Online 管理シェルコマンドプロンプトからスクリプトを実行します。 コマンド例を次に示します。

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

どちらの場合も、次のように表示されるはずです。

![SharePoint Online サイトグループ](media/SPO-site-groups.png)

これらは、サイトに対して作成されたすべてのグループ、 `https://litwareinc.sharepoint.com/sites/finance` およびそれらのグループに割り当てられているすべてのユーザーを対象としています。 グループ名とメンバーの見分けがつくように、グループ名は黄色で表示されます。

もう1つの例として、すべての SharePoint Online サイトのグループとすべてのグループメンバーシップを一覧表示するコマンドセットを示します。

```powershell
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

[SharePoint Online PowerShell に接続する](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する](create-sharepoint-sites-and-add-users-with-powershell.md)

[PowerShell を使用して SharePoint Online のユーザーとグループを管理する](manage-sharepoint-users-and-groups-with-powershell.md)

[PowerShell で Microsoft 365を管理する](manage-office-365-with-office-365-powershell.md)
  
[Microsoft 365 用 PowerShell の使用を開始する](getting-started-with-office-365-powershell.md)

