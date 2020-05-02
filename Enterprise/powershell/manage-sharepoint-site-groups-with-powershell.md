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
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="67e46-103">Office 365 PowerShell を使用して SharePoint Online サイト グループを管理する</span><span class="sxs-lookup"><span data-stu-id="67e46-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="67e46-104">Microsoft 365 管理センターを使用することもできますが、Office 365 PowerShell を使用して SharePoint Online サイトグループを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="67e46-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="67e46-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="67e46-105">Before you begin</span></span>

<span data-ttu-id="67e46-106">この記事の手順では、SharePoint Online に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67e46-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="67e46-107">手順については、「[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67e46-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="67e46-108">Office 365 PowerShell を使用して SharePoint Online を表示する</span><span class="sxs-lookup"><span data-stu-id="67e46-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="67e46-109">SharePoint Online 管理センターには、サイトグループを管理するための使いやすい方法がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="67e46-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="67e46-110">たとえば、 `https://litwareinc.sharepoint.com/sites/finance`サイトのグループとグループメンバーを表示する場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="67e46-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="67e46-111">必要な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="67e46-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="67e46-112">SharePoint 管理センターで、[**アクティブなサイト**] をクリックし、サイトの URL をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67e46-112">From the SharePoint admin center, click **Active sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="67e46-113">サイトページで、[**設定**] アイコン (ページの右上隅にある) をクリックし、[**サイトの権限**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67e46-113">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page), and then click **Site permissions**.</span></span>

<span data-ttu-id="67e46-114">参照する次のサイトでも、このプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="67e46-114">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="67e46-115">Office 365 PowerShell を使用してグループの一覧を取得するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="67e46-115">To get a list of the groups with Office 365 PowerShell, you can use the following commands:</span></span>

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

<span data-ttu-id="67e46-116">このコマンドセットを SharePoint Online 管理シェルコマンドプロンプトで実行するには、次の2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="67e46-116">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="67e46-117">コマンドをメモ帳 (または別のテキストエディター) にコピーし、 **$siteURL**変数の値を変更し、コマンドを選択して、それらを SharePoint Online Management Shell コマンドプロンプトに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="67e46-117">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="67e46-118">実行すると、 **>>** プロンプトで PowerShell が停止します。</span><span class="sxs-lookup"><span data-stu-id="67e46-118">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="67e46-119">Enter キーを押して`foreach`コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="67e46-119">Press Enter to execute the `foreach` command.</span></span><br/>
- <span data-ttu-id="67e46-120">コマンドをメモ帳 (または別のテキスト エディター) にコピーし、**$siteURL** 変数の値を変更してから、このテキスト ファイルを .ps1 という拡張子の付いた名前で適切なフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="67e46-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="67e46-121">次に、そのパスとファイル名を指定して、SharePoint Online 管理シェルコマンドプロンプトからスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="67e46-121">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="67e46-122">コマンド例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="67e46-122">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="67e46-123">どちらの場合も、次のように表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="67e46-123">In both cases, you should see something similar to this:</span></span>

![SharePoint Online サイトグループ](media/SPO-site-groups.png)

<span data-ttu-id="67e46-125">これらは、サイト`https://litwareinc.sharepoint.com/sites/finance`に対して作成されたすべてのグループ、およびそれらのグループに割り当てられているすべてのユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="67e46-125">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="67e46-126">グループ名とメンバーの見分けがつくように、グループ名は黄色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="67e46-126">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="67e46-127">もう1つの例として、すべての SharePoint Online サイトのグループとすべてのグループメンバーシップを一覧表示するコマンドセットを示します。</span><span class="sxs-lookup"><span data-stu-id="67e46-127">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="67e46-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="67e46-128">See also</span></span>

[<span data-ttu-id="67e46-129">SharePoint Online PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="67e46-129">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="67e46-130">Office 365 PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="67e46-130">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="67e46-131">Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する</span><span class="sxs-lookup"><span data-stu-id="67e46-131">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="67e46-132">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="67e46-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="67e46-133">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="67e46-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

