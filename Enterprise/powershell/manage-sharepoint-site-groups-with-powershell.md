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
# <a name="manage-sharepoint-online-site-groups-with-office-365-powershell"></a><span data-ttu-id="eb0f7-103">Office 365 PowerShell を使用して SharePoint Online サイト グループを管理する</span><span class="sxs-lookup"><span data-stu-id="eb0f7-103">Manage SharePoint Online site groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="eb0f7-104">**の概要:** SharePoint Online サイト グループを管理するのにには、Office 365 の PowerShell を使用します。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online site groups.</span></span>
  
<span data-ttu-id="eb0f7-105">Office 365 の管理ページを使用できますが、SharePoint Online サイト グループを管理するために Office 365 の PowerShell を使用することができますも。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-105">Although you can use the Office 365 admin center, you can also use Office 365 PowerShell to manage your SharePoint Online site groups.</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="eb0f7-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="eb0f7-106">Before you begin</span></span>

<span data-ttu-id="eb0f7-p101">この資料の手順では、SharePoint Online に接続する必要があります。手順については、 [SharePoint のオンライン PowerShell への接続](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-p101">The procedures in this article require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

## <a name="view-sharepoint-online-with-office-365-powershell"></a><span data-ttu-id="eb0f7-109">SharePoint を Office 365 の PowerShell でオンラインに表示</span><span class="sxs-lookup"><span data-stu-id="eb0f7-109">View SharePoint Online with Office 365 PowerShell</span></span>

<span data-ttu-id="eb0f7-p102">SharePoint Online 管理センターでは、サイト グループを管理するためのいくつかの簡単に使用できる方法があります。たとえば、グループ、および https に対して、グループのメンバーを参照する\://litwareinc.sharepoint.com/sites/finance のサイトです。ために何が必要です。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-p102">The SharePoint Online admin center has some easy-to-use methods for managing site groups. For example, suppose you want to look at the groups, and the group members, for the https\://litwareinc.sharepoint.com/sites/finance site. Here’s what you have to do to:</span></span>

1. <span data-ttu-id="eb0f7-113">Office 365 管理センターで、[**リソース**] をクリックします > **のサイト**サイトの URL をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-113">From the Office 365 admin center, click **Resources** > **Sites**, and then click the URL of the site.</span></span>
2. <span data-ttu-id="eb0f7-114">サイト コレクション] ダイアログ ボックスで**、このサイト**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-114">In the site collection dialog box, click **Go to this site**.</span></span>
3. <span data-ttu-id="eb0f7-115">[サイト] ページで (ページの右上隅にあります)**の設定**] アイコンをクリックし、[**サイトの設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-115">On the site page, click the **Settings** icon (located in the upper right-hand corner of the page) and then click **Site settings**:</span></span></br>
<span data-ttu-id="eb0f7-116">![SharePoint Online サイトの設定](images/spo-site-settings.png)</span><span class="sxs-lookup"><span data-stu-id="eb0f7-116">![SharePoint Online site settings](images/spo-site-settings.png)</span></span></br>
4. <span data-ttu-id="eb0f7-117">[サイトの設定] ページで、[**ユーザーと権限****のサイトのアクセス許可**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-117">On the Site Settings page, click **Sites permissions** under **Users and Permissions**.</span></span>

<span data-ttu-id="eb0f7-118">参照する次のサイトでも、このプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-118">And then repeat the process for the next site you want to look at.</span></span>

<span data-ttu-id="eb0f7-119">Office 365 PowerShell でグループの一覧を取得するには、次のコマンド セットを使用します。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-119">To get a list of the groups with Office 365 PowerShell, you would use the following command set:</span></span>

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

<span data-ttu-id="eb0f7-120">SharePoint のオンライン管理シェルのコマンド プロンプトで設定このコマンドを実行する 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-120">There are two ways to run this command set in the SharePoint Online Management Shell command prompt:</span></span>

- <span data-ttu-id="eb0f7-p103">コマンドをメモ帳 (または別のテキスト エディターにコピー、 **$siteURL**変数の値を変更、コマンドを選択、および SharePoint のオンライン管理シェルのコマンド プロンプトに貼り付けること。PowerShell で停止するには、ときに、**>>** プロンプトします。**Foreach**コマンドを実行するには、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-p103">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, select the commands, and then paste them into the SharePoint Online Management Shell command prompt. When you do, PowerShell will stop at a **>>** prompt. Press Enter to execute the **foreach** command.</span></span></br>
- <span data-ttu-id="eb0f7-p104">メモ帳 (または別のテキスト エディター) にコマンドをコピー、 **$siteURL**変数の値を変更、名前と適切なフォルダーに .ps1 拡張子を持つテキスト ファイルを保存します。次に、そのパスとファイル名を指定することによって SharePoint のオンライン管理シェルのコマンド プロンプトからスクリプトを実行します。コマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-p104">Copy the commands into Notepad (or another text editor), modify the value of the **$siteURL** variable, and then save this text file with a name and the .ps1 extension in a suitable folder. Next, run the script from the SharePoint Online Management Shell command prompt by specifying its path and file name. Here is an example command:</span></span>

```
C:\Scripts\SiteGroupsAndUsers.ps1
```

<span data-ttu-id="eb0f7-127">どちらの場合も、次のように表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-127">In both cases, you should see something similar to this:</span></span>

![SharePoint Online サイト グループ](images/SPO-site-groups.png)

<span data-ttu-id="eb0f7-p105">サイトの https 用に作成されたすべてのグループは、\:/すべてのユーザーだけでなく、litwareinc.sharepoint.com/sites/finance、それらのグループに割り当てられているとします。グループ名は、そのメンバーからの別のグループ名を支援するのには黄色では。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-p105">These are all the groups that have been created for the site https\://litwareinc.sharepoint.com/sites/finance, as well as all the users assigned to those groups. The group names are in yellow to help you separate group names from their members.</span></span>

<span data-ttu-id="eb0f7-131">別の例として、グループ、およびすべての SharePoint Online サイトのすべてのグループのメンバーシップを一覧表示するコマンドのセットです。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-131">As another example, here is a command set that lists the groups, and all the group memberships, for all of your SharePoint Online sites.</span></span>

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
    
## <a name="see-also"></a><span data-ttu-id="eb0f7-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb0f7-132">See also</span></span>

[<span data-ttu-id="eb0f7-133">SharePoint のオンライン PowerShell への接続します。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-133">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="eb0f7-134">SharePoint Online サイトを作成し、Office 365 の PowerShell でユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="eb0f7-134">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="eb0f7-135">Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する</span><span class="sxs-lookup"><span data-stu-id="eb0f7-135">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>](manage-sharepoint-users-and-groups-with-powershell.md)

[<span data-ttu-id="eb0f7-136">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="eb0f7-136">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="eb0f7-137">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="eb0f7-137">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

