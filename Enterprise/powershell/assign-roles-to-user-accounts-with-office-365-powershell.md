---
title: Office 365 PowerShell でロールをユーザー アカウントに割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: '概要: Office 365 PowerShell を使用して、ロールをユーザー アカウントに割り当てます。'
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690438"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d0590-103">Office 365 PowerShell でロールをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="d0590-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d0590-104">Office 365 PowerShell を使用すると、ロールをユーザー アカウントに迅速かつ簡単に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="d0590-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d0590-105">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="d0590-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d0590-106">最初に、全体管理者アカウントを使用して [Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="d0590-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="d0590-p101">次に、ロールに追加するユーザー アカウントのサインイン名を判別します (例: fredsm@contoso.com)。サインイン名はユーザー プリンシパル名 (UPN) とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d0590-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="d0590-p102">その後、ロールの名前を判別します。以下のコマンドを使用して、PowerShell で割り当てることができるロールの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="d0590-p102">Next, determine the name of the role. Use this command to list the roles that you can assign with PowerShell.</span></span>

````
Get-AzureADDirectoryRole
````

<span data-ttu-id="d0590-111">次に、サインイン名とロール名を入力し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d0590-111">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="d0590-112">完成したコマンド セットの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d0590-112">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="d0590-113">特定のロールのユーザー名の一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0590-113">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d0590-114">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="d0590-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d0590-115">最初に、全体管理者アカウントを使用して [Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="d0590-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="d0590-116">単一ロールの変更の場合</span><span class="sxs-lookup"><span data-stu-id="d0590-116">For a single role change</span></span>

<span data-ttu-id="d0590-117">以下を判別します。</span><span class="sxs-lookup"><span data-stu-id="d0590-117">Determine the following:</span></span>
  
- <span data-ttu-id="d0590-118">構成するユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="d0590-118">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="d0590-p103">ユーザー アカウントを指定するには、その表示名を判別する必要があります。アカウントの完全な一覧を取得するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0590-p103">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d0590-p104">このコマンドにより、ユーザー アカウントの表示名の一覧が、表示名順に並び替えられて、一度に 1 画面ずつ示されます。 **Where** コマンドレットを使用すると、一覧をフィルター処理して、出力するセットを小さくできます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d0590-p104">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d0590-124">このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d0590-124">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="d0590-125">割り当てるロール。</span><span class="sxs-lookup"><span data-stu-id="d0590-125">The role you want to assign.</span></span>
    
    <span data-ttu-id="d0590-126">ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0590-126">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="d0590-127">アカウントの表示名とロールの名前を判別した後、次のコマンドを使用してアカウントにロールを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d0590-127">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="d0590-p105">コマンドをコピーし、メモ帳に貼り付けます。**$dispName** 変数と **$roleName** 変数に関しては、説明テキスト部分を値に置き換えて、\< 記号と > 記号を削除します。引用符はそのまま残します。変更後の行をコピーし、[Windows PowerShell 用 Windows Azure Active Directory モジュール] ウィンドウに貼り付けて実行します。または、Windows PowerShell 統合スクリプト環境 (ISE) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d0590-p105">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="d0590-132">コマンド セットの完成例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d0590-132">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="d0590-133">複数ロールの変更の場合</span><span class="sxs-lookup"><span data-stu-id="d0590-133">For multiple role changes</span></span>

<span data-ttu-id="d0590-134">以下を判別します。</span><span class="sxs-lookup"><span data-stu-id="d0590-134">Determine the following:</span></span>
  
- <span data-ttu-id="d0590-135">構成するユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="d0590-135">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="d0590-p106">ユーザー アカウントを指定するには、その表示名を判別する必要があります。アカウントの一覧を取得するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0590-p106">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d0590-p107">このコマンドにより、すべてのユーザー アカウントの表示名の一覧が、表示名順に並び替えられて、一度に 1 画面ずつ示されます。**Where** コマンドレットを使用すると、一覧をフィルター処理して、出力するセットを小さくできます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d0590-p107">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d0590-141">このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="d0590-141">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="d0590-142">各ユーザー アカウントに割り当てるロール。</span><span class="sxs-lookup"><span data-stu-id="d0590-142">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="d0590-143">ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0590-143">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="d0590-p108">次に、DisplayName フィールドとロール名フィールドが含まれるコンマ区切り値 (CSV) テキスト ファイルを作成します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d0590-p108">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="d0590-146">その後、PowerShell コマンド プロンプトで CSV ファイルの場所を入力し、完成したコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d0590-146">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="d0590-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0590-147">See also</span></span>

- [<span data-ttu-id="d0590-148">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="d0590-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="d0590-149">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="d0590-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="d0590-150">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="d0590-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
