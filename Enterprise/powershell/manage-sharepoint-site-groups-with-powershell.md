---
title: Office 365 PowerShell を使用して SharePoint Online サイト グループを管理する
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
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '概要: Office 365 PowerShell を使用して SharePoint Online サイトグループを管理します。'
ms.openlocfilehash: 3a1b999470746cbe02ec52fe888ea26b59cd423b
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004200"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a>Office 365 PowerShell を使用して SharePoint Online サイト グループを管理する

Microsoft 365 管理センターを使用することもできますが、Office 365 PowerShell を使用して SharePoint Online サイトグループを管理することもできます。

## <a name="before-you-begin"></a>はじめに

この記事の手順では、SharePoint Online に接続する必要があります。 手順については、「[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。

## <a name="view-sharepoint-online-with-office-365-powershell"></a>Office 365 PowerShell を使用して SharePoint Online を表示する

SharePoint Online 管理センターには、サイトグループを管理するための使いやすい方法がいくつかあります。 たとえば、 `https://litwareinc.sharepoint.com/sites/finance`サイトのグループとグループメンバーを表示する場合を考えます。 必要な操作は次のとおりです。

1. SharePoint 管理センターで、[**アクティブなサイト**] をクリックし、サイトの URL をクリックします。
2. サイトページで、[**設定**] アイコン (ページの右上隅にある) をクリックし、[**サイトの権限**] をクリックします。

参照する次のサイトでも、このプロセスを繰り返します。

Office 365 PowerShell を使用してグループの一覧を取得するには、次のコマンドを使用します。

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

- コマンドをメモ帳 (または別のテキストエディター) にコピーし、 **$siteURL**変数の値を変更し、コマンドを選択して、それらを SharePoint Online Management Shell コマンドプロンプトに貼り付けます。 実行すると、 **>>** プロンプトで PowerShell が停止します。 Enter キーを押して`foreach`コマンドを実行します。<br/>
- コマンドをメモ帳 (または別のテキスト エディター) にコピーし、**$siteURL** 変数の値を変更してから、このテキスト ファイルを .ps1 という拡張子の付いた名前で適切なフォルダーに保存します。 次に、そのパスとファイル名を指定して、SharePoint Online 管理シェルコマンドプロンプトからスクリプトを実行します。 コマンド例を次に示します。

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

どちらの場合も、次のように表示されるはずです。

![SharePoint Online サイトグループ](media/SPO-site-groups.png)

これらは、サイト`https://litwareinc.sharepoint.com/sites/finance`に対して作成されたすべてのグループ、およびそれらのグループに割り当てられているすべてのユーザーを対象としています。 グループ名とメンバーの見分けがつくように、グループ名は黄色で表示されます。

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

[Office 365 PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する](create-sharepoint-sites-and-add-users-with-powershell.md)

[Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する](manage-sharepoint-users-and-groups-with-powershell.md)

[Office 365 PowerShell による Office 365 の管理](manage-office-365-with-office-365-powershell.md)
  
[Office 365 PowerShell の概要](getting-started-with-office-365-powershell.md)

