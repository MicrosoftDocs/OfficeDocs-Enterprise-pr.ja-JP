---
title: "Office 365 PowerShell でロールをユーザー アカウントに割り当てる"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: "概要:Office 365 PowerShell と Add-MsolRoleMember コマンドレットを使用して、ユーザー アカウントにロールを割り当てます。"
ms.openlocfilehash: 673a71fb2f85515276e94767ed3f9dd40655dfea
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="b17a4-103">Office 365 PowerShell でロールをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="b17a4-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="b17a4-104">**概要:** Office 365 PowerShell と **Add-MsolRoleMember** コマンドレットを使用して、ユーザー アカウントにロールを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b17a4-104">Summary: Use Office 365 PowerShell and the Add-MsolRoleMember cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="b17a4-105">ユーザー アカウントの表示名とロール名を識別すれば、Office 365 PowerShell を使用してロールをユーザー アカウントに迅速かつ簡単に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="b17a4-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's Display Name and the role's Name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="b17a4-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="b17a4-106">Before you begin</span></span>

<span data-ttu-id="b17a4-p101">このトピックの手順では、全体管理者アカウントを使用して Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b17a4-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="b17a4-109">単一ロールの変更の場合</span><span class="sxs-lookup"><span data-stu-id="b17a4-109">For a single role change</span></span>

<span data-ttu-id="b17a4-110">以下を判別します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-110">Determine the following:</span></span>
  
- <span data-ttu-id="b17a4-111">構成するユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="b17a4-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="b17a4-p102">ユーザー アカウントを指定するには、その表示名を判別する必要があります。アカウントの完全な一覧を取得するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-p102">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="b17a4-p103">このコマンドにより、ユーザー アカウントの表示名の一覧が、表示名順に並び替えられて、一度に 1 画面ずつ示されます。 **Where** コマンドレットを使用すると、一覧をフィルター処理して、出力するセットを小さくできます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="b17a4-117">このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="b17a4-118">割り当てるロール。</span><span class="sxs-lookup"><span data-stu-id="b17a4-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="b17a4-119">ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="b17a4-120">アカウントの表示名とロールの名前を判別した後、次のコマンドを使用してアカウントにロールを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b17a4-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="b17a4-p104">コマンドをコピーし、メモ帳に貼り付けます。**$dispName** 変数と **$roleName** 変数に関しては、説明テキスト部分を値に置き換えて、\< 記号と > 記号を削除します。引用符はそのまま残します。変更後の行をコピーし、[Windows PowerShell 用 Windows Azure Active Directory モジュール] ウィンドウに貼り付けて実行します。または、Windows PowerShell 統合スクリプト環境 (ISE) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b17a4-p104">Copy the commands and paste them into Notepad. For the $dispName and $roleName variables, replace the description text with their values, remove the < and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="b17a4-125">コマンド セットの完成例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="b17a4-126">複数ロールの変更の場合</span><span class="sxs-lookup"><span data-stu-id="b17a4-126">For multiple role changes</span></span>

<span data-ttu-id="b17a4-127">以下を判別します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-127">Determine the following:</span></span>
  
- <span data-ttu-id="b17a4-128">構成するユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="b17a4-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="b17a4-p105">ユーザー アカウントを指定するには、その表示名を判別する必要があります。アカウントの一覧を取得するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="b17a4-p106">このコマンドにより、すべてのユーザー アカウントの表示名の一覧が、表示名順に並び替えられて、一度に 1 画面ずつ示されます。**Where** コマンドレットを使用すると、一覧をフィルター処理して、出力するセットを小さくできます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-p106">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="b17a4-134">このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="b17a4-135">各ユーザー アカウントに割り当てるロール。</span><span class="sxs-lookup"><span data-stu-id="b17a4-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="b17a4-136">ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="b17a4-p107">次に、DisplayName フィールドと RoleName フィールドが含まれるコンマ区切り値 (CSV) テキスト ファイルを作成します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="b17a4-139">その後、PowerShell コマンド プロンプトで CSV ファイルの場所を入力し、完成したコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="b17a4-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="b17a4-140">See also</span></span>

#### 

[<span data-ttu-id="b17a4-141">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="b17a4-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="b17a4-142">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="b17a4-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="b17a4-143">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="b17a4-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
#### 

<span data-ttu-id="b17a4-144">[Add-MsolRoleMember]((https://msdn.microsoft.com/library/dn194120.aspx))</span><span class="sxs-lookup"><span data-stu-id="b17a4-144">[Add-MsolRoleMember]((https://msdn.microsoft.com/library/dn194120.aspx))</span></span>

