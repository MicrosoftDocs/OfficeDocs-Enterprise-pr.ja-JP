---
title: Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: '使用して Office 365 PowerShell を概要: SharePoint Online のユーザー、グループ、およびサイトを管理します。'
ms.openlocfilehash: a04bf1538d6f56b760932b5be89b1953fcaa33d5
ms.sourcegitcommit: 5c5489db5d1000296945c9774198bd911bee4f14
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="3b650-103">Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する</span><span class="sxs-lookup"><span data-stu-id="3b650-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="3b650-104">**の概要:** Office 365 の PowerShell を使用すると、SharePoint Online のユーザー、グループ、およびサイトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="3b650-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="3b650-105">SharePoint Online 管理者ユーザー アカウントまたはグループの大規模なリストで動作し、それを管理する簡単な方法を希望する場合は、Office 365 の PowerShell を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3b650-105">If you are a SharePoint Online administrator who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="3b650-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="3b650-106">Before you begin</span></span>

<span data-ttu-id="3b650-p101">このトピックの手順では、SharePoint Online に接続する必要があります。手順については、 [SharePoint のオンライン PowerShell への接続](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b650-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="3b650-109">サイト、グループ、ユーザーの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="3b650-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="3b650-p102">ユーザーとグループを管理する前に、サイト、グループ、ユーザーの一覧を取得する必要があります。この情報は、この記事の例全体を通して使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b650-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="3b650-112">サイトの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="3b650-112">Get a list of sites</span></span>

<span data-ttu-id="3b650-113">次のコマンドを使用して、テナント内のサイトの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="3b650-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="3b650-114">グループの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="3b650-114">Get a list of groups</span></span>

<span data-ttu-id="3b650-115">次のコマンドを使用して、テナント内のグループの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="3b650-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="3b650-116">ユーザーの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="3b650-116">Get a list of users</span></span>

<span data-ttu-id="3b650-117">次のコマンドを使用して、テナント内のユーザーの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="3b650-117">Get a list of the users in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="3b650-118">サイト コレクション管理者グループにユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="3b650-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="3b650-p103">**セット SPOUser**コマンドを使用するにはサイト コレクションのサイト コレクションの管理者のリストにユーザーを追加します。これは、構文は次の方法です。</span><span class="sxs-lookup"><span data-stu-id="3b650-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="3b650-121">これらのコマンドを使用するには、置換を置換など、二重引用符内のすべての < および > 文字は、正しい名前を持つ。</span><span class="sxs-lookup"><span data-stu-id="3b650-121">To use these commands, replace replace everything within the quotes, including the < and > characters, with the correct names.</span></span>

<span data-ttu-id="3b650-122">この一連のコマンドを追加するなど Opal Castillo (ユーザー名 opalc) サイト コレクションの管理者の一覧 contoso1 テナント内の ContosoTest のサイト コレクションにします。</span><span class="sxs-lookup"><span data-stu-id="3b650-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="3b650-123">コピーしこれらのコマンドをメモ帳に貼り付けます、$tenant、$site、$user のお客様の環境からの実際の値に変数の値を変更して、これをそれらを実行するのには、SharePoint のオンライン管理シェルのウィンドウに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="3b650-123">You can copy and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window to run them.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="3b650-124">他のサイト コレクション管理者グループにユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="3b650-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="3b650-125">このタスクでのサイト コレクションで SharePoint グループにユーザーを追加するのには、**追加 SPOUser**コマンド使用します。</span><span class="sxs-lookup"><span data-stu-id="3b650-125">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="3b650-126">などの追加がきました (ユーザー名 glenr) contoso1 テナント内の ContosoTest のサイト コレクションの監査グループに。</span><span class="sxs-lookup"><span data-stu-id="3b650-126">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="3b650-127">サイト コレクション グループを作成する</span><span class="sxs-lookup"><span data-stu-id="3b650-127">Create a site collection group</span></span>

<span data-ttu-id="3b650-128">**セット SPOSiteGroup**コマンドを使用するには、新しい SharePoint グループを作成し、ContosoTest のサイト コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="3b650-128">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection.</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```
<span data-ttu-id="3b650-129">**セット SPOSiteGroup**コマンドレットを使用してアクセス許可レベルなど、グループのプロパティを後で更新できます。</span><span class="sxs-lookup"><span data-stu-id="3b650-129">Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="3b650-130">など contoso1 テナントの contoso 社のテスト サイト コレクションを見て表示のみのアクセス許可と監査人グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="3b650-130">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="3b650-131">グループからユーザーを削除する</span><span class="sxs-lookup"><span data-stu-id="3b650-131">Remove users from a group</span></span>

<span data-ttu-id="3b650-p104">場合によっては、あるサイトまたはすべてのサイトからユーザーを削除する必要があります。たとえば、従業員がある部署から別の部署に異動した場合や、退職した場合などが該当します。対象の従業員が 1 人のみの場合は UI で簡単に削除できますが、部署全体をあるサイトから別のサイトに移動する場合は容易ではありません。</span><span class="sxs-lookup"><span data-stu-id="3b650-p104">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="3b650-p105">ただし、SharePoint のオンライン管理シェルと CSV ファイルを使用すると、これは、迅速かつ容易です。このタスクでは、サイト コレクションのセキュリティ グループからユーザーを削除するのには Windows PowerShell を使用します。CSV ファイルを使用し、別のサイトから多数のユーザーを削除します。</span><span class="sxs-lookup"><span data-stu-id="3b650-p105">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="3b650-p106">ようにコマンドの構文を参照してください、サイト コレクションのグループから 1 つの Office 365 ユーザーを削除するのに**削除 SPOUser**コマンドを使用しています。構文は次の方法を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3b650-p106">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```
<span data-ttu-id="3b650-140">たとえば、contoso1 テナントの contoso 社のテスト サイト コレクションのサイト コレクションの監査人グループから見て村中 Overby を削除します。</span><span class="sxs-lookup"><span data-stu-id="3b650-140">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="3b650-p107">Bobby を現在彼が所属しているすべてのグループから削除するとしたら、以下の方法があります。</span><span class="sxs-lookup"><span data-stu-id="3b650-p107">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="3b650-p108">これは、単なる例です。ユーザーが会社を辞める場合など、すべてのグループからユーザーを削除する必要がある本当にしない限りは、このコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b650-p108">This is just an example. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="3b650-145">ユーザーおよびグループの大規模なリストの管理を自動化する</span><span class="sxs-lookup"><span data-stu-id="3b650-145">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="3b650-p109">多数のアカウントを SharePoint サイトに追加し、アクセス許可を与える、Office 365 管理者センター、個々 の PowerShell コマンド、または PowerShell を使用することができますが、CSV ファイルです。これらのオプションでは、CSV ファイルがこのタスクを自動化する最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="3b650-p109">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="3b650-p110">基本的なプロセスでは、Windows PowerShell スクリプトが必要なパラメーターに対応する見出し (列) を CSV ファイルを作成します。Excel でこのようなリストを簡単に作成し、CSV ファイルとしてエクスポートできます。次に、Windows PowerShell スクリプトを使用して、グループとサイト グループにユーザーを追加することを CSV ファイル内のレコード (行) を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="3b650-p110">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="3b650-p111">例として、サイト コレクション、グループ、アクセス許可を定義する CSV ファイルを作成します。次に、グループにユーザーを取り込むための CSV ファイルを作成します。最後に、グループを作成してユーザーを取り込む単純な Windows PowerShell スクリプトを作成して実行します。</span><span class="sxs-lookup"><span data-stu-id="3b650-p111">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="3b650-154">最初の CSV ファイルは、1 つ以上のグループを 1 つ以上のサイト コレクションに追加します。このファイルの構造は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3b650-154">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="3b650-155">ヘッダー:</span><span class="sxs-lookup"><span data-stu-id="3b650-155">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="3b650-156">項目:</span><span class="sxs-lookup"><span data-stu-id="3b650-156">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,group,level
```

<span data-ttu-id="3b650-157">以下は、サンプル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="3b650-157">Here is an example file:</span></span>

```
Site,Group,PermissionLevels
https://contoso1.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso1.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso1.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso1.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso1.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso1.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

<span data-ttu-id="3b650-158">2 番目の CSV ファイルは、1 つ以上のユーザーを 1 つ以上のグループに追加します。このファイルの構造は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3b650-158">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="3b650-159">ヘッダー:</span><span class="sxs-lookup"><span data-stu-id="3b650-159">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="3b650-160">項目:</span><span class="sxs-lookup"><span data-stu-id="3b650-160">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="3b650-161">以下は、サンプル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="3b650-161">Here is an example file:</span></span>

```
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso1.onmicrosoft.com,https://contoso1.sharepoint.com/sites/Project01
```

<span data-ttu-id="3b650-p112">次の手順では、2 つの CSV ファイルをドライブに保存する必要があります。両方の CSV ファイルを使用するコマンドの例を挙げますとグループ メンバーシップをアクセス許可を追加するとします。</span><span class="sxs-lookup"><span data-stu-id="3b650-p112">For the next step, you must have the two CSV files saved to your drive. Here are example commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="3b650-p113">スクリプトでは、CSV ファイルの内容をインポートし、**新規 SPOSiteGroup**および**追加 SPOUser**コマンドのパラメーターを設定するのには、列の値を使用します。例では、私たちはこのフォルダーに保存 theO365Admin、C ドライブには任意の場所に保存することができます。</span><span class="sxs-lookup"><span data-stu-id="3b650-p113">The script imports the CSV file contents and uses the values in the columns to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to theO365Admin folder on drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="3b650-p114">ここで、同じ CSV ファイルを使用して別のサイト内のいくつかのグループのユーザーを削除します。コマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3b650-p114">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is an example command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="3b650-168">ユーザー レポートを生成する</span><span class="sxs-lookup"><span data-stu-id="3b650-168">Generate user reports</span></span>

<span data-ttu-id="3b650-p115">いくつかのサイトに関する単純なレポートを取得して、該当するサイトのユーザーと各ユーザーのアクセス許可レベルやその他のプロパティを表示しなければならない場合があります。以下に、構文の一例を示します。</span><span class="sxs-lookup"><span data-stu-id="3b650-p115">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "<tenant name, such as litwareinc for litwareinc.onmicrosoft.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="3b650-p116">これら 3 つのサイトのデータを取得され、ローカル ドライブ上のテキスト ファイルに書き込みます。なおパラメーター – 追加は、既存のファイルに新しいコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="3b650-p116">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="3b650-173">たとえば、Contoso1 テナントの ContosoTest サイト、TeamSite01 サイト、および Project01 サイトでレポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="3b650-173">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="3b650-p117">**$Site**変数のみを変更しなければならなかったことに注意してください。**$Tenant**変数は、コマンドのすべての 3 つの実行を使用してその値を保持します。</span><span class="sxs-lookup"><span data-stu-id="3b650-p117">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="3b650-p118">一方、この操作をすべてのサイトに対して行うとしたら、どうなるでしょうか。以下のコードを使用すれば、すべての Web サイトを入力することなく、このコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b650-p118">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="3b650-p119">このレポートは非常に簡単で、および特定のレポートまたは詳細な情報を含むレポートを作成するコードを追加することができます。ことができるよう環境を SharePoint Online でユーザーを管理するために SharePoint のオンライン管理シェルを使用する方法のことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3b650-p119">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="3b650-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b650-180">See also</span></span>

[<span data-ttu-id="3b650-181">SharePoint のオンライン PowerShell への接続します。</span><span class="sxs-lookup"><span data-stu-id="3b650-181">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="3b650-182">Office 365 PowerShell を使用して SharePoint Online を管理する</span><span class="sxs-lookup"><span data-stu-id="3b650-182">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="3b650-183">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="3b650-183">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3b650-184">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="3b650-184">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

