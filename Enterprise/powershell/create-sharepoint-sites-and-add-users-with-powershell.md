---
title: Office 365 PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '概要: Office 365 PowerShell を使用して新しい SharePoint Online サイトを作成し、それらのサイトにユーザーとグループを追加します。'
ms.openlocfilehash: c2ed2afd7915fa5fc3aa936b5aa09cf90679ff97
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069103"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="23d85-103">Office 365 PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="23d85-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="23d85-104">**概要:** Office 365 PowerShell を使用して新しい SharePoint Online サイトを作成し、それらのサイトにユーザーとグループを追加します。</span><span class="sxs-lookup"><span data-stu-id="23d85-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="23d85-105">Office 365 PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加すると、Office 356 管理センターでの作業よりも迅速かつ繰り返しタスクを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="23d85-105">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center.</span></span> <span data-ttu-id="23d85-106">また、Office 356 管理センターでは実行できないタスクも実行できます。</span><span class="sxs-lookup"><span data-stu-id="23d85-106">You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="23d85-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="23d85-107">Before you begin</span></span>

<span data-ttu-id="23d85-108">このトピックの手順では、SharePoint Online に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="23d85-108">The procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="23d85-109">手順については、「 [SharePoint Online PowerShell への接続](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23d85-109">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="23d85-110">手順 1: Office 365 PowerShell を使って新しいサイト コレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="23d85-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="23d85-111">Office 365 PowerShell を使用して複数のサイトを作成し、指定されたコード例およびメモ帳を使用して作成した .csv ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="23d85-111">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad.</span></span> <span data-ttu-id="23d85-112">この手順では、角かっこに示されているプレースホルダー情報を、独自のサイトとテナント固有の情報に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="23d85-112">For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information.</span></span> <span data-ttu-id="23d85-113">このプロセスにより、1つのファイルを作成し、そのファイルを使用する1つの Office 365 PowerShell コマンドを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="23d85-113">This process lets you create a single file and run a single Office 365 PowerShell command that uses that file.</span></span> <span data-ttu-id="23d85-114">これにより、アクションが繰り返し可能で持ち運び可能になるため、SharePoint Online 管理シェルに長いコマンドを入力することによって発生する可能性のある多くのエラーが発生しなくなります。</span><span class="sxs-lookup"><span data-stu-id="23d85-114">This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell.</span></span> <span data-ttu-id="23d85-115">この手順には2つの部分があります。</span><span class="sxs-lookup"><span data-stu-id="23d85-115">There are two parts to this procedure.</span></span> <span data-ttu-id="23d85-116">最初に .csv ファイルを作成してから、Office 365 PowerShell を使用してその .csv ファイルを参照します。これにより、そのコンテンツを使用してサイトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="23d85-116">First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="23d85-p104">Office 365 PowerShell コマンドレットは、その .csv ファイルをインポートし、ファイルの最初の行を列見出しとして読み取る、中かっこ内のループにパイプします。次に、Office 365 PowerShell コマンドレットは、残りのレコードを反復処理し、レコードごとに新規のサイト コレクションを作成し、列見出しに従ってサイト コレクションのプロパティを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="23d85-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="23d85-119">.csv ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="23d85-119">Create a .csv file</span></span>

1. <span data-ttu-id="23d85-120">メモ帳を開き、次のテキスト ブロックを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="23d85-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="23d85-121">ここで、 *tenant*はテナントの名前で、 *owner*は、サイトコレクションの管理者の役割を付与するテナントのユーザー名です。</span><span class="sxs-lookup"><span data-stu-id="23d85-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="23d85-122">メモ帳を使用して一括置換をすばやく実行するには、Ctrl + H キーを押します。</span><span class="sxs-lookup"><span data-stu-id="23d85-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="23d85-123">ファイルを**SiteCollections**としてデスクトップに保存します。</span><span class="sxs-lookup"><span data-stu-id="23d85-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="23d85-124">この .csv ファイルやそれ以外の .csv ファイル、または Windows PowerShell スクリプト ファイルを使用する前に、余分の文字または印刷されない文字がないか確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="23d85-124">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters.</span></span> <span data-ttu-id="23d85-125">Word でファイルを開き、リボンで [段落] アイコンをクリックすると、印刷されない文字が表示されます。</span><span class="sxs-lookup"><span data-stu-id="23d85-125">Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters.</span></span> <span data-ttu-id="23d85-126">印刷されない余分の文字がないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="23d85-126">There should be no extraneous nonprinting characters.</span></span> <span data-ttu-id="23d85-127">たとえば、ファイルの末尾の最後の文字の後ろに段落記号があってはなりません。</span><span class="sxs-lookup"><span data-stu-id="23d85-127">For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="23d85-128">Windows PowerShell コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="23d85-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="23d85-129">Windows PowerShell プロンプトで、次のコマンドレットを入力するか、コピーして貼り付け、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="23d85-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="23d85-130">*Myalias*はユーザーエイリアスと同じです。</span><span class="sxs-lookup"><span data-stu-id="23d85-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="23d85-p106">WindowsPowerShell プロンプトが再度表示されるまで待機します。これには 1 - 2 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="23d85-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="23d85-133">Windows PowerShell プロンプトで、次のコマンドレットを入力するか、コピーして貼り付け、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="23d85-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="23d85-134">リストに新しいサイトコレクションが表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="23d85-134">Note the new site collections in the list.</span></span> <span data-ttu-id="23d85-135">次のサイトコレクションが表示されます。 **contosotest**、 **TeamSite01**、 **Blog01**、および**Project01**</span><span class="sxs-lookup"><span data-stu-id="23d85-135">You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="23d85-p108">これで完了です。作成した .csv ファイルと 1 つの WindowsPowerShell コマンドレットを使用して、複数のサイト コレクションを作成しました。これで、ユーザーを作成してこれらのサイトに割り当てる準備ができました。</span><span class="sxs-lookup"><span data-stu-id="23d85-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="23d85-139">手順 2:ユーザーおよびグループの追加</span><span class="sxs-lookup"><span data-stu-id="23d85-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="23d85-p109">ここでは、ユーザーを作成し、サイト コレクションのグループに追加します。次に、.csv ファイルを使用して、新しいグループとユーザーを一括アップロードします。</span><span class="sxs-lookup"><span data-stu-id="23d85-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="23d85-142">次の手順では、サイト コレクションの contosotest、TeamSite01、Blog01、Project01 が正常に作成されていることが前提になっています。</span><span class="sxs-lookup"><span data-stu-id="23d85-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="23d85-143">.csv ファイルおよび .ps1 ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="23d85-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="23d85-144">メモ帳を開き、次のテキスト ブロックを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="23d85-144">Open Notepad, and paste the following text block into it:</span></span><br/>
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
<br/><span data-ttu-id="23d85-145">*テナント*はテナント名と同じです。</span><span class="sxs-lookup"><span data-stu-id="23d85-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="23d85-146">ファイルをグループ名、**アクセス許可 .csv**としてデスクトップに保存します。</span><span class="sxs-lookup"><span data-stu-id="23d85-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="23d85-147">メモ帳の新しいインスタンスを開き、次のテキストのブロックを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="23d85-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="23d85-148">*テナント*はテナント名と同じで、 *username*は既存のユーザーのユーザー名と同じです。</span><span class="sxs-lookup"><span data-stu-id="23d85-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="23d85-149">ファイルを**ユーザー .csv**としてデスクトップに保存します。</span><span class="sxs-lookup"><span data-stu-id="23d85-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="23d85-150">メモ帳の新しいインスタンスを開き、次のテキストのブロックを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="23d85-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="23d85-151">MyAlias は、現在ログオンしているユーザーのユーザー名と同じです。</span><span class="sxs-lookup"><span data-stu-id="23d85-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="23d85-152">ファイルを**usersandgroups.ps1**としてデスクトップに保存します。</span><span class="sxs-lookup"><span data-stu-id="23d85-152">Save the file to your desktop as **UsersAndGroups.ps1**.</span></span> <span data-ttu-id="23d85-153">これは、単純な Windows PowerShell スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="23d85-153">This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="23d85-154">これで、UsersAndGroup.ps1 スクリプトを実行して複数のサイト コレクションにユーザーとグループを追加する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="23d85-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="23d85-155">UsersAndGroups.ps1 スクリプトの実行</span><span class="sxs-lookup"><span data-stu-id="23d85-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="23d85-156">SharePoint Online 管理シェルに戻ります。</span><span class="sxs-lookup"><span data-stu-id="23d85-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="23d85-157">Windows PowerShell プロンプトで、次の行を入力するか、コピーして貼り付け、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="23d85-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="23d85-158">確認のプロンプトで、 **Y**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="23d85-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="23d85-159">Windows PowerShell プロンプトで、次のコマンドを入力するか、コピーして貼り付け、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="23d85-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="23d85-160">*Myalias*は、ユーザー名と同じです。</span><span class="sxs-lookup"><span data-stu-id="23d85-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="23d85-p111">プロンプトが戻るまで待機してから、次に進みます。最初に、作成したとおりにグループが表示されます。次に、ユーザーを追加するたびに、グループの一覧が繰り返し表示されます。</span><span class="sxs-lookup"><span data-stu-id="23d85-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="23d85-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="23d85-164">See also</span></span>

[<span data-ttu-id="23d85-165">SharePoint Online PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="23d85-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="23d85-166">SharePoint Online サイトグループの管理 Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="23d85-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="23d85-167">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="23d85-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="23d85-168">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="23d85-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

