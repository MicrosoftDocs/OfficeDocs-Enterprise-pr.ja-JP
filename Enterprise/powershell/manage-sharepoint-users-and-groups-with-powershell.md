---
title: Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '概要: Office 365 PowerShell を使用して、SharePoint Online のユーザー、グループ、およびサイトを管理します。'
ms.openlocfilehash: 54a493cc7635562733241fb371ecdb59477ac717
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841324"
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="79416-103">Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する</span><span class="sxs-lookup"><span data-stu-id="79416-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

<span data-ttu-id="79416-104">ユーザーアカウントまたはグループの大規模なリストを処理する SharePoint Online 管理者は、Office 365 PowerShell を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="79416-104">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

<span data-ttu-id="79416-105">開始する前に、このトピックの手順で SharePoint Online に接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79416-105">Before you begin, the procedures in this topic require you to connect to SharePoint Online.</span></span> <span data-ttu-id="79416-106">手順については、「 [SharePoint Online PowerShell への接続](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79416-106">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="79416-107">サイト、グループ、ユーザーの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="79416-107">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="79416-p102">ユーザーとグループを管理する前に、サイト、グループ、ユーザーの一覧を取得する必要があります。この情報は、この記事の例全体を通して使用できます。</span><span class="sxs-lookup"><span data-stu-id="79416-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

<span data-ttu-id="79416-110">次のコマンドを使用して、テナント内のサイトの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="79416-110">Get a list of the sites in your tenant with this command:</span></span>

```powershell
Get-SPOSite
```

<span data-ttu-id="79416-111">次のコマンドを使用して、テナント内のグループの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="79416-111">Get a list of the groups in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

<span data-ttu-id="79416-112">次のコマンドを使用して、テナント内のユーザーの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="79416-112">Get a list of the users in your tenant with this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="79416-113">サイト コレクション管理者グループにユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="79416-113">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="79416-114">`Set-SPOUser`コマンドレットを使用して、サイトコレクションのサイトコレクション管理者のリストにユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="79416-114">You use the `Set-SPOUser` cmdlet to add a user to the list of Site Collection Administrators on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="79416-115">これらのコマンドを使用するには、を置き換えます。置換するには、< と > の文字を含めて、引用符内のすべてを正しい名前で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="79416-115">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="79416-116">たとえば、次のコマンドを使用すると、Opal Castillo (user name opalc) が contoso テナント内の ContosoTest サイトコレクションのサイトコレクション管理者の一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="79416-116">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="79416-117">これらのコマンドをメモ帳にコピーして貼り付けることができます。 $tenant、$site、および $user の変数値を環境から実際の値に変更し、それを SharePoint Online 管理シェルウィンドウに貼り付けて実行します。</span><span class="sxs-lookup"><span data-stu-id="79416-117">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-groups"></a><span data-ttu-id="79416-118">他のサイトコレクショングループにユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="79416-118">Add a user to other site collection groups</span></span>

<span data-ttu-id="79416-119">この作業では、 `Add-SPOUser`コマンドレットを使用して、サイトコレクションの SharePoint グループにユーザーを追加します。</span><span class="sxs-lookup"><span data-stu-id="79416-119">In this task, we'll use the `Add-SPOUser` cmdlet to add a user to a SharePoint group on a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="79416-120">たとえば、「Glen Rife (ユーザー名 glenr)」を「contoso テナント内の ContosoTest サイトコレクションの監査者グループに追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="79416-120">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="79416-121">サイト コレクション グループを作成する</span><span class="sxs-lookup"><span data-stu-id="79416-121">Create a site collection group</span></span>

<span data-ttu-id="79416-122">この`New-SPOSiteGroup`コマンドレットを使用して、新しい SharePoint グループを作成し、それをサイトコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="79416-122">You use the `New-SPOSiteGroup` cmdlet to create a new SharePoint group and add it to a site collection.</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="79416-123">アクセス許可レベルなどのグループのプロパティは、後で`Set-SPOSiteGroup`コマンドレットを使用して更新できます。</span><span class="sxs-lookup"><span data-stu-id="79416-123">Group properties, such as permission levels, can be updated later by using the `Set-SPOSiteGroup` cmdlet.</span></span>

<span data-ttu-id="79416-124">たとえば、contoso テナント内の contosotest サイトコレクションに対する表示のみのアクセス許可を持つ監査グループを追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="79416-124">For example, let’s add the Auditors group with View Only permissions to the contosotest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="79416-125">グループからユーザーを削除する</span><span class="sxs-lookup"><span data-stu-id="79416-125">Remove users from a group</span></span>

<span data-ttu-id="79416-p103">場合によっては、あるサイトまたはすべてのサイトからユーザーを削除する必要があります。たとえば、従業員がある部署から別の部署に異動した場合や、退職した場合などが該当します。対象の従業員が 1 人のみの場合は UI で簡単に削除できますが、部署全体をあるサイトから別のサイトに移動する場合は容易ではありません。</span><span class="sxs-lookup"><span data-stu-id="79416-p103">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="79416-129">ただし、SharePoint Online 管理シェルと CSV ファイルを使用することで、これは迅速かつ簡単になります。</span><span class="sxs-lookup"><span data-stu-id="79416-129">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy.</span></span> <span data-ttu-id="79416-130">このタスクでは、まず、Windows PowerShell を使用して、サイト コレクションのセキュリティ グループから 1 人のユーザーを削除します。</span><span class="sxs-lookup"><span data-stu-id="79416-130">In this task, you'll use Windows PowerShell to remove a user from a site collection security group.</span></span> <span data-ttu-id="79416-131">次に、CSV ファイルを使用して、複数の異なるサイトから多数のユーザーを削除します。</span><span class="sxs-lookup"><span data-stu-id="79416-131">Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="79416-132">コマンド構文を確認できるように、' Remove-SPOUser ' コマンドレットを使用して、1つの Office 365 ユーザーをサイトコレクショングループから削除します。</span><span class="sxs-lookup"><span data-stu-id="79416-132">We'll be using the 'Remove-SPOUser' cmdlet to remove a single Office 365 user from a site collection group just so we can see the command syntax.</span></span> <span data-ttu-id="79416-133">以下に、構文の一例を示します。</span><span class="sxs-lookup"><span data-stu-id="79416-133">Here is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="79416-134">たとえば、contoso テナントの contosotest サイトコレクションのサイトコレクション監査グループから、[村中 Overby を削除しましょう。</span><span class="sxs-lookup"><span data-stu-id="79416-134">For example, let’s remove Bobby Overby from the site collection Auditors group in the contosotest site collection in the contoso tenancy:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="79416-135">ユーザーが現在所属しているすべてのグループから、村中を削除するとします。</span><span class="sxs-lookup"><span data-stu-id="79416-135">Suppose we wanted to remove Bobby from all the groups he is currently in.</span></span> <span data-ttu-id="79416-136">これを行う方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="79416-136">Here is how we would do that:</span></span>

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="79416-137">これは1つの例にすぎません。</span><span class="sxs-lookup"><span data-stu-id="79416-137">This is just an example.</span></span> <span data-ttu-id="79416-138">たとえば、ユーザーが退職した場合など、ユーザーをすべてのグループから実際に削除しなければならないのでない限り、このコマンドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="79416-138">You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="79416-139">ユーザーおよびグループの大規模なリストの管理を自動化する</span><span class="sxs-lookup"><span data-stu-id="79416-139">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="79416-140">多数のアカウントを SharePoint サイトに追加してアクセス許可を付与するには、Microsoft 365 管理センター、個々の PowerShell コマンド、または PowerShell を CSV ファイルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="79416-140">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Microsoft 365 admin center, individual PowerShell commands, or PowerShell an a CSV file.</span></span> <span data-ttu-id="79416-141">これらの選択肢の中では、CSV ファイルがこのタスクを自動化する最も簡単な方法になります。</span><span class="sxs-lookup"><span data-stu-id="79416-141">Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="79416-142">基本的なプロセスは、CSV を作成し、ヘッダー (列) を Windows PowerShell スクリプトに必要なパラメーターに対応させることです。</span><span class="sxs-lookup"><span data-stu-id="79416-142">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs.</span></span> <span data-ttu-id="79416-143">このようなリストは、Excel で簡単に作成して、それを CSV ファイルとしてエクスポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="79416-143">You can easily create such a list in Excel and then export it as a CSV file.</span></span> <span data-ttu-id="79416-144">次に、Windows PowerShell スクリプトを使用して、CSV ファイルのレコード (行) を反復処理し、ユーザーをグループに、グループをサイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="79416-144">Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="79416-p110">例として、サイト コレクション、グループ、アクセス許可を定義する CSV ファイルを作成します。次に、グループにユーザーを取り込むための CSV ファイルを作成します。最後に、グループを作成してユーザーを取り込む単純な Windows PowerShell スクリプトを作成して実行します。</span><span class="sxs-lookup"><span data-stu-id="79416-p110">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="79416-148">最初の CSV ファイルは、1 つ以上のグループを 1 つ以上のサイト コレクションに追加します。このファイルの構造は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="79416-148">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

<span data-ttu-id="79416-149">見出し</span><span class="sxs-lookup"><span data-stu-id="79416-149">Header:</span></span>

```powershell
Site,Group,PermissionLevels
```

<span data-ttu-id="79416-150">部分</span><span class="sxs-lookup"><span data-stu-id="79416-150">Item:</span></span>

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="79416-151">以下は、サンプル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="79416-151">Here is an example file:</span></span>

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

<span data-ttu-id="79416-152">2 番目の CSV ファイルは、1 つ以上のユーザーを 1 つ以上のグループに追加します。このファイルの構造は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="79416-152">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

<span data-ttu-id="79416-153">見出し</span><span class="sxs-lookup"><span data-stu-id="79416-153">Header:</span></span>

```powershell
Group,LoginName,Site
```

<span data-ttu-id="79416-154">部分</span><span class="sxs-lookup"><span data-stu-id="79416-154">Item:</span></span>

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="79416-155">以下は、サンプル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="79416-155">Here is an example file:</span></span>

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

<span data-ttu-id="79416-156">次の手順では、2 つの CSV ファイルをドライブに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79416-156">For the next step, you must have the two CSV files saved to your drive.</span></span> <span data-ttu-id="79416-157">次に、両方の CSV ファイルを使用してアクセス許可とグループメンバーシップを追加するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="79416-157">Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="79416-158">このスクリプトは、CSV ファイルの内容をインポートし、列の値を使用して、 **remove-spositegroup**および**Add-spouser**コマンドのパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="79416-158">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands.</span></span> <span data-ttu-id="79416-159">この例では、ドライブ C の theO365Admin フォルダーに保存していますが、任意の場所に保存できます。</span><span class="sxs-lookup"><span data-stu-id="79416-159">In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="79416-160">ここでは、同じ CSV ファイルを使用して、異なる複数のサイトの複数のグループから、ユーザーをまとめて削除します。</span><span class="sxs-lookup"><span data-stu-id="79416-160">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file.</span></span> <span data-ttu-id="79416-161">コマンド例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="79416-161">Here is an example command:</span></span>

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="79416-162">ユーザー レポートを生成する</span><span class="sxs-lookup"><span data-stu-id="79416-162">Generate user reports</span></span>

<span data-ttu-id="79416-p114">いくつかのサイトに関する単純なレポートを取得して、該当するサイトのユーザーと各ユーザーのアクセス許可レベルやその他のプロパティを表示しなければならない場合があります。以下に、構文の一例を示します。</span><span class="sxs-lookup"><span data-stu-id="79416-p114">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="79416-165">上記のコードは、3 つのサイトのデータを取得して、ローカル ドライブ上のテキスト ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="79416-165">This will grab the data for these three sites and write them to a text file on your local drive.</span></span> <span data-ttu-id="79416-166">パラメーター –Append は、既存のファイルに新しいコンテンツを追加することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="79416-166">Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="79416-167">たとえば、Contoso1 テナントの ContosoTest サイト、TeamSite01 サイト、および Project01 サイトでレポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="79416-167">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="79416-168">**$Site**変数のみを変更する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="79416-168">Note that we had to change only the **$site** variable.</span></span> <span data-ttu-id="79416-169">**$Tenant**変数の値は、コマンドの3つの実行によって保持されます。</span><span class="sxs-lookup"><span data-stu-id="79416-169">The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="79416-p117">一方、この操作をすべてのサイトに対して行うとしたら、どうなるでしょうか。以下のコードを使用すれば、すべての Web サイトを入力することなく、このコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="79416-p117">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="79416-172">このレポートはかなり単純ですが、コードを追加すれば、より具体的なレポートや、その他の詳細情報が含まれるレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="79416-172">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information.</span></span> <span data-ttu-id="79416-173">しかし、sharepoint online 管理シェルを使用して SharePoint Online 環境のユーザーを管理する方法についての理解が得られます。</span><span class="sxs-lookup"><span data-stu-id="79416-173">But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="79416-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="79416-174">See also</span></span>

[<span data-ttu-id="79416-175">SharePoint Online PowerShell に接続する</span><span class="sxs-lookup"><span data-stu-id="79416-175">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="79416-176">Office 365 PowerShell を使用して SharePoint Online を管理する</span><span class="sxs-lookup"><span data-stu-id="79416-176">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="79416-177">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="79416-177">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="79416-178">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="79416-178">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

