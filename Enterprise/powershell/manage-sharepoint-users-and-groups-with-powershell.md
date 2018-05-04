---
title: Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する
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
description: '使用して Office 365 PowerShell を概要: SharePoint Online のユーザー、グループ、およびサイトを管理します。'
ms.openlocfilehash: 8ed40d2c736853145e21f0f9852bdb18c7842075
ms.sourcegitcommit: 74cdb2534bce376abc9cf4fef85ff039c46ee790
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-users-and-groups-with-office-365-powershell"></a><span data-ttu-id="5a2da-103">Office 365 PowerShell を使用して SharePoint Online のユーザーとグループを管理する</span><span class="sxs-lookup"><span data-stu-id="5a2da-103">Manage SharePoint Online users and groups with Office 365 PowerShell</span></span>

 <span data-ttu-id="5a2da-104">**の概要:** Office 365 の PowerShell を使用すると、SharePoint Online のユーザー、グループ、およびサイトを管理できます。</span><span class="sxs-lookup"><span data-stu-id="5a2da-104">**Summary:** Use Office 365 PowerShell to manage SharePoint Online users, groups, and sites.</span></span>

<span data-ttu-id="5a2da-105">SharePoint Online ユーザー アカウントまたはグループの大規模なリストで動作し、それを管理する簡単な方法を希望する場合は、Office 365 の PowerShell を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5a2da-105">If you are a SharePoint Online who works with large lists of user accounts or groups and wants an easier way to manage them, you can use Office 365 PowerShell.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="5a2da-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="5a2da-106">Before you begin</span></span>

<span data-ttu-id="5a2da-p101">このトピックの手順では、SharePoint Online に接続する必要があります。手順については、 [SharePoint のオンライン PowerShell への接続](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p101">The procedures in this topic require you to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)</span></span>

## <a name="get-a-list-of-sites-groups-and-users"></a><span data-ttu-id="5a2da-109">サイト、グループ、ユーザーの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="5a2da-109">Get a list of sites, groups, and users</span></span>

<span data-ttu-id="5a2da-p102">ユーザーとグループを管理する前に、サイト、グループ、ユーザーの一覧を取得する必要があります。この情報は、この記事の例全体を通して使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p102">Before we start to manage users and groups, you need to get lists of your sites, groups, and users. You can then use this information to work through the example in this article.</span></span>

### <a name="get-a-list-of-sites"></a><span data-ttu-id="5a2da-112">サイトの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="5a2da-112">Get a list of sites</span></span>

<span data-ttu-id="5a2da-113">次のコマンドを使用して、テナント内のサイトの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-113">Get a list of the sites in your tenant with this command:</span></span>

```
Get-SPOSite
```

### <a name="get-a-list-of-groups"></a><span data-ttu-id="5a2da-114">グループの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="5a2da-114">Get a list of groups</span></span>

<span data-ttu-id="5a2da-115">次のコマンドを使用して、テナント内のグループの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-115">Get a list of the groups in your tenant with this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup -Site $_.Url} |Format-Table
```

### <a name="get-a-list-of-users"></a><span data-ttu-id="5a2da-116">ユーザーの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="5a2da-116">Get a list of users</span></span>

<span data-ttu-id="5a2da-117">次のコマンドを使用して、テナント内のユーザーの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-117">Get a list of the users in your tenant with this command:</span></span>

```Get-SPOSite | ForEach-Object {Get-SPOUser -Site $_.Url}```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a><span data-ttu-id="5a2da-118">サイト コレクション管理者グループにユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="5a2da-118">Add a user to the Site Collection Administrators group</span></span>

<span data-ttu-id="5a2da-p103">**セット SPOUser**コマンドを使用するにはサイト コレクションのサイト コレクションの管理者のリストにユーザーを追加します。これは、構文は次の方法です。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p103">You use the **Set-SPOUser** command to add a user to the list of Site Collection Administrators on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--# This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example "opalc"-->
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
 ```

<span data-ttu-id="5a2da-121">この例は、値を格納する変数を使用し、スクリプトのメモには (たとえば"<!--This is the Tenant Name…-->") これらの値である必要がありますを理解するため。</span><span class="sxs-lookup"><span data-stu-id="5a2da-121">This example uses variables to store values and has notes in the script (for example "<!--This is the Tenant Name…-->") to help you understand what those values should be.</span></span>

<span data-ttu-id="5a2da-122">この一連のコマンドを追加するなど Opal Castillo (ユーザー名 opalc) サイト コレクションの管理者の一覧 contoso1 テナント内の ContosoTest のサイト コレクションにします。</span><span class="sxs-lookup"><span data-stu-id="5a2da-122">For example, this set of commands adds Opal Castillo (user name opalc) the list of Site Collection Administrators on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.onmicrosoft.com -IsSiteCollectionAdmin $true
```

<span data-ttu-id="5a2da-123">これらのコマンドは実際に切り取ってメモ帳に貼り付け、$tenant、$site、および $user の変数の値をそれぞれの環境の実際の値に変更して、SharePoint Online Management Shell ウィンドウに貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="5a2da-123">You can actually cut and paste these commands into Notepad, change the variable values for $tenant, $site, and $user to actual values from your environment, and then paste this into your SharePoint Online Management Shell window.</span></span>

## <a name="add-a-user-to-other-site-collection-administrators-groups"></a><span data-ttu-id="5a2da-124">他のサイト コレクション管理者グループにユーザーを追加する</span><span class="sxs-lookup"><span data-stu-id="5a2da-124">Add a user to other Site Collection Administrators groups</span></span>

<span data-ttu-id="5a2da-p104">このタスクでのサイト コレクションで SharePoint グループにユーザーを追加するのには、**追加 SPOUser**コマンド使用します。これは、構文は次の方法です。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p104">In this task, we'll use the **Add-SPOUser** command to add a user to a SharePoint group on a site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks. Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks. Example: "contosotest"-->
$user = "loginname"
<!--This is the users login name. Value must be enclosed in double quotation marks. Example: "opalc"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks. Example: "Auditors"-->
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site

```

<span data-ttu-id="5a2da-127">などの追加がきました (ユーザー名 glenr) contoso1 テナント内の ContosoTest のサイト コレクションの監査グループに。</span><span class="sxs-lookup"><span data-stu-id="5a2da-127">For example, let’s add Glen Rife (user name glenr) to the Auditors group on the ContosoTest site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a><span data-ttu-id="5a2da-128">サイト コレクション グループを作成する</span><span class="sxs-lookup"><span data-stu-id="5a2da-128">Create a site collection group</span></span>

<span data-ttu-id="5a2da-p105">**セット SPOSiteGroup**コマンドを使用するには、新しい SharePoint グループを作成し、ContosoTest のサイト コレクションに追加します。これは、構文は次の方法です。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p105">You use the **Set-SPOSiteGroup** command to create a new SharePoint group and add it to the ContosoTest site collection. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$level = "permission level"
<!--This is the level of permissions to assign to the group. Value must be enclosed in double quotation marks, Example: "View Only"-->
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

> [!IMPORTANT]
> <span data-ttu-id="5a2da-p106">引用符で囲まれたスペースを含む任意の文字列を囲む必要があります。**セット SPOSiteGroup**コマンドレットを使用してアクセス許可レベルなど、グループのプロパティを後で更新できます。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p106">You must enclose any string with spaces in quotation marks. Group properties, such as permission levels, can be updated later by using the **Set-SPOSiteGroup** cmdlet.</span></span>

<span data-ttu-id="5a2da-133">など contoso1 テナントの contoso 社のテスト サイト コレクションを見て表示のみのアクセス許可と監査人グループを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-133">For example, let’s add the Auditors group with View Only permissions to the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "Contoso Test"
$level = "View Only"
$group = "Auditors"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a><span data-ttu-id="5a2da-134">グループからユーザーを削除する</span><span class="sxs-lookup"><span data-stu-id="5a2da-134">Remove users from a group</span></span>

<span data-ttu-id="5a2da-p107">場合によっては、あるサイトまたはすべてのサイトからユーザーを削除する必要があります。たとえば、従業員がある部署から別の部署に異動した場合や、退職した場合などが該当します。対象の従業員が 1 人のみの場合は UI で簡単に削除できますが、部署全体をあるサイトから別のサイトに移動する場合は容易ではありません。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p107">Sometimes you have to remove a user from a site or even all sites. Perhaps the employee moves from one division to another or leaves the company. You can do this for one employee easily in the UI, but this is not easily done when you have to move a complete division from one site to another.</span></span>

<span data-ttu-id="5a2da-p108">ただし、SharePoint のオンライン管理シェルと CSV ファイルを使用すると、これは、迅速かつ容易です。このタスクでは、サイト コレクションのセキュリティ グループからユーザーを削除するのには Windows PowerShell を使用します。CSV ファイルを使用し、別のサイトから多数のユーザーを削除します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p108">However by using the SharePoint Online Management Shell and CSV files, this is fast and easy. In this task, you'll use Windows PowerShell to remove a user from a site collection security group. Then you'll use a CSV file and remove lots of users from different sites.</span></span> 

<span data-ttu-id="5a2da-p109">ようにコマンドの構文を参照してください、サイト コレクションのグループから 1 つの Office 365 ユーザーを削除するのに**削除 SPOUser**コマンドを使用しています。構文は次の方法を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p109">We'll be using the **Remove-SPOUser** command to remove a single Office 365 user from a site collection group just so we can see the command syntax. Here is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotation marks, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotation marks, Example: "contosotest"-->
$group = "group"
<!--This is the SharePoint security Group name. Value must be enclosed in double quotation marks, Example: "Auditors"-->
$user = "loginname"
<!--This is the user’s login name. Value must be enclosed in double quotation marks, Example: "opalc"-->
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site
```

<span data-ttu-id="5a2da-143">たとえば、contoso1 テナントの contoso 社のテスト サイト コレクションのサイト コレクションの監査人グループから見て村中 Overby を削除します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-143">For example, let’s remove Bobby Overby from the site collection Auditors group in the Contoso Test site collection in the contoso1 tenancy:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

<span data-ttu-id="5a2da-p110">Bobby を現在彼が所属しているすべてのグループから削除するとしたら、以下の方法があります。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p110">Suppose we wanted to remove Bobby from all the groups he is currently in. Here is how we would do that:</span></span>

```
$tenant = "contoso1"
$user = "bobbyo"
Get-SPOSite | ForEach-Object {Get-SPOSiteGroup –Site $_.Url} | ForEach-Object {Remove-SPOUser -LoginName $user@$tenant.onmicrosoft.com -Site &_.Url}
```

> [!WARNING]
> <span data-ttu-id="5a2da-p111">これは、方法を示すためだけのものです。たとえば、ユーザーが退職した場合など、ユーザーをすべてのグループから実際に削除しなければならないのでない限り、このコマンドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p111">This is just to show how to do this. You should not run this command unless you really have to remove a user from every group, for example if the user leaves the company.</span></span>

## <a name="automate-management-of-large-lists-of-users-and-groups"></a><span data-ttu-id="5a2da-148">ユーザーおよびグループの大規模なリストの管理を自動化する</span><span class="sxs-lookup"><span data-stu-id="5a2da-148">Automate management of large lists of users and groups</span></span>

<span data-ttu-id="5a2da-p112">多数のアカウントを SharePoint サイトに追加し、アクセス許可を与える、Office 365 管理者センター、個々 の PowerShell コマンド、または PowerShell を使用することができますが、CSV ファイルです。これらのオプションでは、CSV ファイルがこのタスクを自動化する最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p112">To add a large number of accounts to SharePoint sites and give them permissions, you can use the Office 365 admin center, individual PowerShell commands, or PowerShell an a CSV file. Of these choices, the CSV file is the fastest way to automate this task.</span></span>

<span data-ttu-id="5a2da-p113">基本的なプロセスでは、Windows PowerShell スクリプトが必要なパラメーターに対応する見出し (列) を CSV ファイルを作成します。Excel でこのようなリストを簡単に作成し、CSV ファイルとしてエクスポートできます。次に、Windows PowerShell スクリプトを使用して、グループとサイト グループにユーザーを追加することを CSV ファイル内のレコード (行) を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p113">The basic process is to create a CSV file that has headers (columns) that correspond to the parameters that the Windows PowerShell script needs. You can easily create such a list in Excel and then export it as a CSV file. Then, you use a Windows PowerShell script to iterate through records (rows) in the CSV file, adding the users to groups and the groups to sites.</span></span> 

<span data-ttu-id="5a2da-p114">例として、サイト コレクション、グループ、アクセス許可を定義する CSV ファイルを作成します。次に、グループにユーザーを取り込むための CSV ファイルを作成します。最後に、グループを作成してユーザーを取り込む単純な Windows PowerShell スクリプトを作成して実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p114">For example, let’s create a CSV file to define a group of site collections, groups, and permissions. Next, we will create a CSV file to populate the groups with users. Finally, we will create and run a simple Windows PowerShell script that creates and populates the groups.</span></span>

<span data-ttu-id="5a2da-157">最初の CSV ファイルは、1 つ以上のグループを 1 つ以上のサイト コレクションに追加します。このファイルの構造は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5a2da-157">The first CSV file will add one or more groups to one or more site collections and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="5a2da-158">ヘッダー:</span><span class="sxs-lookup"><span data-stu-id="5a2da-158">Header:</span></span>

```
Site,Group,PermissionLevels
```

### <a name="item"></a><span data-ttu-id="5a2da-159">項目:</span><span class="sxs-lookup"><span data-stu-id="5a2da-159">Item:</span></span>

```
https://tenant.sharepoint.com/sites/site,site collection,group,level
```

<span data-ttu-id="5a2da-160">以下は、サンプル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="5a2da-160">Here is an example file:</span></span>

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

<span data-ttu-id="5a2da-161">2 番目の CSV ファイルは、1 つ以上のユーザーを 1 つ以上のグループに追加します。このファイルの構造は以下のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5a2da-161">The second CSV file will add one or more users to one or more groups and will have this structure:</span></span>

### <a name="header"></a><span data-ttu-id="5a2da-162">ヘッダー:</span><span class="sxs-lookup"><span data-stu-id="5a2da-162">Header:</span></span>

```
Group,LoginName,Site
```

### <a name="item"></a><span data-ttu-id="5a2da-163">項目:</span><span class="sxs-lookup"><span data-stu-id="5a2da-163">Item:</span></span>

```
group,login,https://tenant.sharepoint.com/sites/site
```

<span data-ttu-id="5a2da-164">以下は、サンプル ファイルです。</span><span class="sxs-lookup"><span data-stu-id="5a2da-164">Here is an example file:</span></span>

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

<span data-ttu-id="5a2da-p115">次の手順では、2 つの CSV ファイルをドライブに保存する必要があります。次のコマンドは両方の CSV ファイルを使用し、アクセス許可とグループ メンバーシップを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p115">For the next step, you must have the two CSV files saved to your drive. Here are the commands that use both CSV files and to add permissions and group membership:</span></span>

```
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

<span data-ttu-id="5a2da-p116">スクリプトでは、CSV ファイルの内容をインポートし、(太字) で列の値を使用して、**新規 SPOSiteGroup**および**追加 SPOUser**コマンドのパラメーターを設定します。例では、C ドライブにこれを保存していますが、任意の場所に保存することができます。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p116">The script imports the CSV file contents and uses the values in the columns (in bold) to populate the parameters of the **New-SPOSiteGroup** and **Add-SPOUser** commands. In our example, we are saving this to the drive C, but you can save it wherever you want.</span></span>

<span data-ttu-id="5a2da-p117">ここでは、同じ CSV ファイルを使用して、異なる複数のサイトの複数のグループから、ユーザーをまとめて削除します。コマンドを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p117">Now, let’s remove a bunch of people for several groups in different sites using the same CSV file. Here is the command:</span></span>

```
Import-Csv C:\O365Admin\Users.csv | ForEach-Object {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a><span data-ttu-id="5a2da-171">ユーザー レポートを生成する</span><span class="sxs-lookup"><span data-stu-id="5a2da-171">Generate user reports</span></span>

<span data-ttu-id="5a2da-p118">いくつかのサイトに関する単純なレポートを取得して、該当するサイトのユーザーと各ユーザーのアクセス許可レベルやその他のプロパティを表示しなければならない場合があります。以下に、構文の一例を示します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p118">You might want to get a simple report for a few sites and display the users for those sites, their permission level, and other properties. This is how the syntax looks:</span></span>

```
$tenant = "tenant"
<!--This is the Tenant Name. Value must be enclosed in double quotes, Example: "Contoso01"-->
$site = "site"
<!--This is the Site name. Value must be enclosed in double quotes, Example: "contosotest"-->
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="5a2da-p119">これら 3 つのサイトのデータを取得され、ローカル ドライブ上のテキスト ファイルに書き込みます。なおパラメーター – 追加は、既存のファイルに新しいコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p119">This will grab the data for these three sites and write them to a text file on your local drive. Note that the parameter –Append will add new content to an existing file.</span></span>

<span data-ttu-id="5a2da-176">たとえば、Contoso1 テナントの ContosoTest サイト、TeamSite01 サイト、および Project01 サイトでレポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-176">For example, let's run a report on the ContosoTest, TeamSite01, and Project01 sites for the Contoso1 tenant:</span></span>

```
$tenant = "contoso1"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="5a2da-p120">**$Site**変数のみを変更しなければならなかったことに注意してください。**$Tenant**変数は、コマンドのすべての 3 つの実行を使用してその値を保持します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p120">Note that we had to change only the **$site** variable. The **$tenant** variable keeps its value through all three runs of the command.</span></span>

<span data-ttu-id="5a2da-p121">一方、この操作をすべてのサイトに対して行うとしたら、どうなるでしょうか。以下のコードを使用すれば、すべての Web サイトを入力することなく、このコマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p121">However, what if you wanted to do this for every site? You can do this without having to type all those websites by using this command:</span></span>

```
Get-SPOSite | ForEach-Object {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

<span data-ttu-id="5a2da-p122">このレポートは非常に簡単で、および特定のレポートまたは詳細な情報を含むレポートを作成するコードを追加することができます。ことができるよう環境を SharePoint Online でユーザーを管理するために SharePoint のオンライン管理シェルを使用する方法のことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5a2da-p122">This report is fairly simple, and you can add more code to create more specific reports or reports that include more detailed information. But this should give you an idea of how to use the SharePoint Online Management Shell to manage users in the SharePoint Online environment.</span></span>
   
## <a name="see-also"></a><span data-ttu-id="5a2da-183">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a2da-183">See also</span></span>

[<span data-ttu-id="5a2da-184">SharePoint のオンライン PowerShell への接続します。</span><span class="sxs-lookup"><span data-stu-id="5a2da-184">Connect to SharePoint Online PowerShell</span></span>](https://docs.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)

[<span data-ttu-id="5a2da-185">Office 365 PowerShell を使用して SharePoint Online を管理する</span><span class="sxs-lookup"><span data-stu-id="5a2da-185">Manage SharePoint Online with Office 365 PowerShell</span></span>](create-sharepoint-sites-and-add-users-with-powershell.md)

[<span data-ttu-id="5a2da-186">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="5a2da-186">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5a2da-187">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="5a2da-187">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

