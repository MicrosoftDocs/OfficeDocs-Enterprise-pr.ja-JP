---
title: Office 365 PowerShell を使用して SharePoint Online サイト グループを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/01/2018
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '概要: Office 365 PowerShell を使用して SharePoint Online サイトグループを管理します。'
ms.openlocfilehash: 7eb8a472cb021fb2b78468a9100282b72c1b88cb
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748537"
---
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="8c185-103">Office 365 PowerShell を使用して SharePoint Online サイト グループを管理する</span><span class="sxs-lookup"><span data-stu-id="8c185-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

<span data-ttu-id="8c185-104">Microsoft 365 管理センターを使用することもできますが、Office 365 PowerShell を使用して SharePoint Online サイトグループを管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="8c185-104">Although you can use the Microsoft 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="8c185-105">始める前に</span><span class="sxs-lookup"><span data-stu-id="8c185-105">Before you begin</span></span>

<span data-ttu-id="8c185-106">この記事の手順では、SharePoint Online に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c185-106">The procedures in this article require you to connect to SharePoint Online.</span></span> <span data-ttu-id="8c185-107">手順については、「[Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c185-107">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="8c185-108">Office 365 PowerShell を使用して SharePoint Online を表示する</span><span class="sxs-lookup"><span data-stu-id="8c185-108">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="8c185-109">SharePoint Online 管理センターには、サイトグループを管理するための使いやすい方法がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="8c185-109">The SharePoint Online admin center has some easy-to-use methods for managing site groups.</span></span> <span data-ttu-id="8c185-110">たとえば、 `https://litwareinc.sharepoint.com/sites/finance`サイトのグループとグループメンバーを表示する場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="8c185-110">For example, suppose you want to look at the groups, and the group members, for the `https://litwareinc.sharepoint.com/sites/finance` site.</span></span> <span data-ttu-id="8c185-111">必要な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8c185-111">Here’s what you have to do to:</span></span>

1. <span data-ttu-id="8c185-112">Microsoft 365 管理センターで、[**リソース** > **サイト**] をクリックし、サイトの URL をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c185-112">From the Microsoft 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="8c185-113">[サイト コレクション] ダイアログ ボックスで **[このサイトに移動]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c185-113">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="8c185-114">サイト ページで、**[設定]** アイコン (ページの右上隅にある) をクリックしてから、**[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c185-114">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span><br/>
<span data-ttu-id="8c185-115">![SharePoint Online サイトの設定](media/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="8c185-115">![SharePoint Online site settings](media/spo-site-settings.png)</span></span><br/>
4. <span data-ttu-id="8c185-116">[サイトの設定] ページの **[ユーザーと権限]** の下にある、**[サイトの権限]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8c185-116">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="8c185-117">参照する次のサイトでも、このプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8c185-117">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="8c185-118">Office 365 PowerShell でグループの一覧を取得するには、次のコマンド セットを使用します。</span><span class="sxs-lookup"><span data-stu-id="8c185-118">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="8c185-119">このコマンドセットを SharePoint Online 管理シェルコマンドプロンプトで実行するには、次の2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="8c185-119">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="8c185-120">コマンドをメモ帳 (または別のテキストエディター) にコピーし、 **$siteURL**変数の値を変更し、コマンドを選択して、それらを SharePoint Online Management Shell コマンドプロンプトに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8c185-120">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt.</span></span> <span data-ttu-id="8c185-121">実行すると、 **>>** プロンプトで PowerShell が停止します。</span><span class="sxs-lookup"><span data-stu-id="8c185-121">When you do, PowerShell will stop at a **>>** prompt.</span></span> <span data-ttu-id="8c185-122">Enter キーを押して、**foreach** コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c185-122">Press Enter to execute the **foreach** command.</span></span><br/>
- <span data-ttu-id="8c185-123">コマンドをメモ帳 (または別のテキスト エディター) にコピーし、**$siteURL** 変数の値を変更してから、このテキスト ファイルを .ps1 という拡張子の付いた名前で適切なフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="8c185-123">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder.</span></span> <span data-ttu-id="8c185-124">次に、そのパスとファイル名を指定して、SharePoint Online 管理シェルコマンドプロンプトからスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="8c185-124">Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name.</span></span> <span data-ttu-id="8c185-125">コマンド例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8c185-125">Here is an example command:</span></span>

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="8c185-126">どちらの場合も、次のように表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="8c185-126">In both cases, you should see something similar to this:</span></span>

![SharePoint Online サイトグループ](media/SPO-site-groups.png)

<span data-ttu-id="8c185-128">これらは、サイト`https://litwareinc.sharepoint.com/sites/finance`に対して作成されたすべてのグループ、およびそれらのグループに割り当てられているすべてのユーザーを対象としています。</span><span class="sxs-lookup"><span data-stu-id="8c185-128">These are all the groups that have been created for the site `https://litwareinc.sharepoint.com/sites/finance`, and all the users assigned to those groups.</span></span> <span data-ttu-id="8c185-129">グループ名とメンバーの見分けがつくように、グループ名は黄色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c185-129">The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="8c185-130">もう1つの例として、すべての SharePoint Online サイトのグループとすべてのグループメンバーシップを一覧表示するコマンドセットを示します。</span><span class="sxs-lookup"><span data-stu-id="8c185-130">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="8c185-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c185-131">See also</span></span>

[<span data-ttu-id="8c185-132">SharePoint Online PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="8c185-132">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="8c185-133">Office 365 PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="8c185-133">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="8c185-134">Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する</span><span class="sxs-lookup"><span data-stu-id="8c185-134">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="8c185-135">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="8c185-135">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8c185-136">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="8c185-136">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

