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
ms.openlocfilehash: 41ca26249bd494d5603a425689e47f9fe6809f1a
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975205"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-office-365-powershell"></a><span data-ttu-id="f0b93-103">Office 365 PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="f0b93-103">Create SharePoint Online sites and add users with Office 365 PowerShell</span></span>

 <span data-ttu-id="f0b93-104">**の概要:** Office 365 の PowerShell を使用して、新しい SharePoint Online サイトを作成し、それらのサイトにユーザーおよびグループを追加します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-104">**Summary:** Use Office 365 PowerShell to create new SharePoint Online sites, and then add users and groups to those sites.</span></span>

<span data-ttu-id="f0b93-p101">Office 365 の PowerShell を使用して SharePoint Online サイトを作成し、ユーザーを追加すると、迅速かつ繰り返しタスクを実行できます Office 356 管理センターでよりもはるかに高速です。Office 356 管理センターで実行することができないタスクも実行できます。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p101">When you use Office 365 PowerShell to create SharePoint Online sites and add users, you can quickly and repeatedly perform tasks much faster than you can in the Office 356 admin center. You can also perform tasks that are not possible to perform in the Office 356 admin center.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="f0b93-107">はじめに</span><span class="sxs-lookup"><span data-stu-id="f0b93-107">Before you begin</span></span>

<span data-ttu-id="f0b93-p102">このトピックの手順では、SharePoint Online に接続する必要があります。手順については、 [SharePoint のオンライン PowerShell への接続](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p102">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="step-1-create-new-site-collections-using-office-365-powershell"></a><span data-ttu-id="f0b93-110">手順 1: Office 365 PowerShell を使って新しいサイト コレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="f0b93-110">Step 1: Create new site collections using Office 365 PowerShell</span></span>

<span data-ttu-id="f0b93-p103">Office 365 PowerShell と、提供されているサンプル コードとメモ帳を使用して作成した .csv ファイルを使用して複数のサイトを作成します。この手順では、角かっこ内に表示されているプレースホルダー情報を自分のサイトやテナント固有の情報に置き換えます。このプロセスでは、1 つのファイルを作成し、そのファイルを使用する 1 つの Office 365 PowerShell コマンドを実行することができます。これにより、実行されるアクションは反復可能かつポータブルになり、長いコマンドを SharePoint Online Management Shell に入力した場合に発生する可能性がある多くのエラー (すべてではないものの) がなくなります。この手順は 2 つの部分で構成されます。最初に .csv ファイルを作成し、次に Office 365 PowerShell を使用してその .csv ファイルを参照します。ファイルの内容を使用してサイトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p103">Create multiple sites using Office 365 PowerShell and a .csv file that you create using the example code provided and Notepad. For this procedure, you’ll be replacing the placeholder information shown in brackets with your own site- and tenant-specific information. This process allows you to create a single file and run a single Office 365 PowerShell command that uses that file. This makes the actions taken both repeatable and portable and eliminates many, if not all, errors that can come from typing long commands into the SharePoint Online Management Shell. There are two parts to this procedure. First you’ll create a .csv file, and then you’ll reference that .csv file using Office 365 PowerShell, which will use its contents to create the sites.</span></span>

<span data-ttu-id="f0b93-p104">Office 365 PowerShell コマンドレットは、その .csv ファイルをインポートし、ファイルの最初の行を列見出しとして読み取る、中かっこ内のループにパイプします。次に、Office 365 PowerShell コマンドレットは、残りのレコードを反復処理し、レコードごとに新規のサイト コレクションを作成し、列見出しに従ってサイト コレクションのプロパティを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p104">The Office 365 PowerShell cmdlet imports the .csv file and pipes it to a loop inside the curly brackets that reads the first line of the file as column headers. The Office 365 PowerShell cmdlet then iterates through the remaining records, creates a new site collection for each record, and assigns properties of the site collection according to the column headers.</span></span>

### <a name="create-a-csv-file"></a><span data-ttu-id="f0b93-119">.csv ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="f0b93-119">Create a .csv file</span></span>

1. <span data-ttu-id="f0b93-120">メモ帳を開き、次のテキスト ブロックを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f0b93-120">Open Notepad, and paste the following text block into it:</span></span><br/>

```
Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
```
<br/><span data-ttu-id="f0b93-121">プライマリ サイト コレクション管理者の役割を付与する*テナント*が、テナントの名前、*所有者*は、先のテナントのユーザーのユーザー名。</span><span class="sxs-lookup"><span data-stu-id="f0b93-121">Where *tenant* is the name of your tenant, and *owner* is the user name of the user on your tenant to whom you want to grant the role of primary site collection administrator.</span></span><br/><span data-ttu-id="f0b93-122">(することができます押して Ctrl + H 置換を高速に一括してメモ帳を使用する場合)。</span><span class="sxs-lookup"><span data-stu-id="f0b93-122">(You can press Ctrl+H when you use Notepad to bulk replace faster.)</span></span><br/>

2. <span data-ttu-id="f0b93-123">デスクトップ上のファイルを**SiteCollections.csv**として保存します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-123">Save the file on your desktop as **SiteCollections.csv**.</span></span><br/>

> [!TIP]
> <span data-ttu-id="f0b93-p105">これまたはその他の .csv ファイルまたは Windows PowerShell スクリプト ファイルを使用する前に不要なまたは印刷されない文字がないかどうかを確認することをお勧めします。Word と、リボンの [ファイルを開く、編集記号を表示するのには [段落] アイコンをクリックします。不要な記号はないはずです。などはないはず、ファイルの末尾に最後の 1 つ以上の段落記号です。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p105">Before you use this or any other .csv or Windows PowerShell script file, it is good practice to make sure that there are no extraneous or nonprinting characters. Open the file in Word, and in the ribbon, click the paragraph icon to show nonprinting characters. There should be no extraneous nonprinting characters. For example, there should be no paragraph marks beyond the final one at the end of the file.</span></span>

### <a name="run-the-windows-powershell-command"></a><span data-ttu-id="f0b93-128">Windows PowerShell コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="f0b93-128">Run the Windows PowerShell command</span></span>

1. <span data-ttu-id="f0b93-129">Windows PowerShell プロンプトで、次のコマンドレットを入力するか、コピーして貼り付け、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-129">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>
```
Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
```
<br/><span data-ttu-id="f0b93-130">場所*MyAlias*は、ユーザーのエイリアスと同じです。</span><span class="sxs-lookup"><span data-stu-id="f0b93-130">Where *MyAlias* equals your user alias.</span></span><br/>

2. <span data-ttu-id="f0b93-p106">WindowsPowerShell プロンプトが再度表示されるまで待機します。これには 1 - 2 分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p106">Wait for the Windows PowerShell prompt to reappear. It might take a minute or two.</span></span><br/>

3. <span data-ttu-id="f0b93-133">Windows PowerShell プロンプトで、次のコマンドレットを入力するか、コピーして貼り付け、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-133">At the Windows PowerShell prompt, type or copy and paste the following cmdlet, and press Enter:</span></span><br/>

```
Get-SPOSite -Detailed | Format-Table -AutoSize
```
<br/>

4. <span data-ttu-id="f0b93-p107">一覧に新しいサイト コレクションに注意してください。次のサイト コレクションを参照する必要があります: **contosotest**、 **TeamSite01**、 **Blog01**、および**Project01**</span><span class="sxs-lookup"><span data-stu-id="f0b93-p107">Note the new site collections in the list. You should see the following site collections: **contosotest**, **TeamSite01**, **Blog01**, and **Project01**</span></span>

<span data-ttu-id="f0b93-p108">これで完了です。作成した .csv ファイルと 1 つの WindowsPowerShell コマンドレットを使用して、複数のサイト コレクションを作成しました。これで、ユーザーを作成してこれらのサイトに割り当てる準備ができました。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p108">That’s it. You’ve created multiple site collections using the .csv file you created and a single Windows PowerShell cmdlet. You’re now ready to create and assign users to these sites.</span></span>

## <a name="step-2-add-users-and-groups"></a><span data-ttu-id="f0b93-139">手順 2:ユーザーおよびグループの追加</span><span class="sxs-lookup"><span data-stu-id="f0b93-139">Step 2: Add users and groups</span></span>

<span data-ttu-id="f0b93-p109">ここでは、ユーザーを作成し、サイト コレクションのグループに追加します。次に、.csv ファイルを使用して、新しいグループとユーザーを一括アップロードします。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p109">Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.</span></span>

<span data-ttu-id="f0b93-142">次の手順では、サイト コレクションの contosotest、TeamSite01、Blog01、Project01 が正常に作成されていることが前提になっています。</span><span class="sxs-lookup"><span data-stu-id="f0b93-142">The following procedures assume that you successfully created the site collections contosotest, TeamSite01, Blog01, and Project01.</span></span>

### <a name="create-csv-and-ps1-files"></a><span data-ttu-id="f0b93-143">.csv ファイルおよび .ps1 ファイルの作成</span><span class="sxs-lookup"><span data-stu-id="f0b93-143">Create .csv and .ps1 files</span></span>

1. <span data-ttu-id="f0b93-144">メモ帳を開き、次のテキスト ブロックを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f0b93-144">Open Notepad, and paste the following text block into it:</span></span><br/>
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
<br/><span data-ttu-id="f0b93-145">*テナント*に等しい、テナント名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-145">Where *tenant* equals your tenant name.</span></span><br/>

2. <span data-ttu-id="f0b93-146">**GroupsAndPermissions.csv**として、ファイルをデスクトップに保存します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-146">Save the file to your desktop as **GroupsAndPermissions.csv**.</span></span><br/>

3. <span data-ttu-id="f0b93-147">メモ帳の新しいインスタンスを開き、次のテキストのブロックを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f0b93-147">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

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
<br/><span data-ttu-id="f0b93-148">*テナント*に等しい、テナント名、*ユーザー名*が既存のユーザーのユーザー名と同じです。</span><span class="sxs-lookup"><span data-stu-id="f0b93-148">Where *tenant* equals your tenant name, and *username* equals the user name of an existing user.</span></span><br/>

4. <span data-ttu-id="f0b93-149">として**ユーザー.csv**ファイルをデスクトップに保存します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-149">Save the file to your desktop as **Users.csv**.</span></span><br/>

5. <span data-ttu-id="f0b93-150">メモ帳の新しいインスタンスを開き、次のテキストのブロックを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f0b93-150">Open a new instance of Notepad, and paste the following text block into it:</span></span><br/>

```
Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```
<br/><span data-ttu-id="f0b93-151">MyAlias に等しい現在ログオンしているユーザーのユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-151">Where MyAlias equals the user name of the user that is currently logged on.</span></span><br/>

6. <span data-ttu-id="f0b93-p110">**UsersAndGroups.ps1**として、ファイルをデスクトップに保存します。これは、単純な Windows PowerShell スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p110">Save the file to your desktop as **UsersAndGroups.ps1**. This is a simple Windows PowerShell script.</span></span>

<span data-ttu-id="f0b93-154">これで、UsersAndGroup.ps1 スクリプトを実行して複数のサイト コレクションにユーザーとグループを追加する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="f0b93-154">You’re now ready to run the UsersAndGroup.ps1 script to add users and groups to multiple site collections.</span></span>

### <a name="run-usersandgroupsps1-script"></a><span data-ttu-id="f0b93-155">UsersAndGroups.ps1 スクリプトの実行</span><span class="sxs-lookup"><span data-stu-id="f0b93-155">Run UsersAndGroups.ps1 script</span></span>

1. <span data-ttu-id="f0b93-156">SharePoint Online 管理シェルに戻ります。</span><span class="sxs-lookup"><span data-stu-id="f0b93-156">Return to the SharePoint Online Management Shell.</span></span><br/>
2. <span data-ttu-id="f0b93-157">Windows PowerShell プロンプトで、次の行を入力するか、コピーして貼り付け、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-157">At the Windows PowerShell prompt, type or copy and paste the following line, and press Enter:</span></span><br/>
```
Set-ExecutionPolicy Bypass
```
<br/>

3. <span data-ttu-id="f0b93-158">確認プロンプトで、 **Y**をキーを押します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-158">At the confirmation prompt, press **Y**.</span></span><br/>

4. <span data-ttu-id="f0b93-159">Windows PowerShell プロンプトで、次のコマンドを入力するか、コピーして貼り付け、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-159">At the Windows PowerShell prompt, type or copy and paste the following, and press Enter:</span></span><br/>

```
c:\users\MyAlias\desktop\UsersAndGroups.ps1
```
<br/><span data-ttu-id="f0b93-160">*MyAlias*に等しい自分のユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-160">Where *MyAlias* equals your user name.</span></span><br/>

5. <span data-ttu-id="f0b93-p111">プロンプトが戻るまで待機してから、次に進みます。最初に、作成したとおりにグループが表示されます。次に、ユーザーを追加するたびに、グループの一覧が繰り返し表示されます。</span><span class="sxs-lookup"><span data-stu-id="f0b93-p111">Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0b93-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0b93-164">See also</span></span>

[<span data-ttu-id="f0b93-165">SharePoint Online PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="f0b93-165">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="f0b93-166">Office 365 の PowerShell SharePoint Online のサイト グループを管理します。</span><span class="sxs-lookup"><span data-stu-id="f0b93-166">Manage SharePoint Online site groups Office 365 PowerShell</span></span>](manage-sharepoint-site-groups-with-powershell.md)

[<span data-ttu-id="f0b93-167">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="f0b93-167">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="f0b93-168">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="f0b93-168">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

