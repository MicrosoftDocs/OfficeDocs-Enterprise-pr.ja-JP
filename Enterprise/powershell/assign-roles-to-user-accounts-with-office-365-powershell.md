---
title: Office 365 PowerShell でロールをユーザー アカウントに割り当てる
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: '概要: Office 365 PowerShell を使用して、ロールをユーザー アカウントに割り当てます。'
ms.openlocfilehash: 3b57862d78d8699da033ed016338a449650e7140
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841674"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e6f9d-103">Office 365 PowerShell でロールをユーザー アカウントに割り当てる</span><span class="sxs-lookup"><span data-stu-id="e6f9d-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="e6f9d-104">Office 365 PowerShell を使用すると、ロールをユーザー アカウントに迅速かつ簡単に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e6f9d-105">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="e6f9d-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e6f9d-106">最初に、全体管理者アカウントを使用して [Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="e6f9d-p101">次に、ロールに追加するユーザー アカウントのサインイン名を判別します (例: fredsm@contoso.com)。サインイン名はユーザー プリンシパル名 (UPN) とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="e6f9d-109">次に、ロールの名前を決めます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-109">Next, determine the name of the role.</span></span> <span data-ttu-id="e6f9d-110">[Azure Active Directoryでこの管理者ロールのアクセス許可の一覧](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)を使用します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="e6f9d-111">この記事のメモに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="e6f9d-112">Azure AD PowerShellでは一部のロール名が異なります。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="e6f9d-113">たとえば、Microsoft 365管理センターの "SharePoint Administrator"ロールは、Azure AD PowerShellでは "SharePoint Service Administrator"という異なった名前がついています。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="e6f9d-114">次に、サインイン名とロール名を入力し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="e6f9d-115">以下は、SharePoint サービス管理者の役割を belindan@contoso.com アカウントに割り当てる、完成したコマンドセットの例です。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-115">Here is an example of a completed command set that assigns the SharePoint Service Administrator role to the belindan@contoso.com account:</span></span>
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="e6f9d-116">特定のロールのユーザー名の一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-116">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e6f9d-117">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="e6f9d-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e6f9d-118">最初に、全体管理者アカウントを使用して [Office 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="e6f9d-119">単一ロールの変更の場合</span><span class="sxs-lookup"><span data-stu-id="e6f9d-119">For a single role change</span></span>

<span data-ttu-id="e6f9d-120">特定のユーザーアカウントの最も一般的な方法は、その表示名または電子メール名 (サインイン名またはユーザープリンシパル名 (UPN)) を使用することです。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="e6f9d-121">ユーザーアカウントの表示名</span><span class="sxs-lookup"><span data-stu-id="e6f9d-121">Display names of user accounts</span></span>

<span data-ttu-id="e6f9d-122">ユーザーアカウントの表示名の処理に使用する場合は、次の点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="e6f9d-123">構成するユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="e6f9d-p104">ユーザー アカウントを指定するには、その表示名を判別する必要があります。アカウントの完全な一覧を取得するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-p104">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="e6f9d-p105">このコマンドにより、ユーザー アカウントの表示名の一覧が、表示名順に並び替えられて、一度に 1 画面ずつ示されます。 **Where** コマンドレットを使用すると、一覧をフィルター処理して、出力するセットを小さくできます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-p105">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="e6f9d-129">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-129">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e6f9d-130">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-130">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="e6f9d-131">このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-131">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="e6f9d-132">割り当てるロール。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-132">The role you want to assign.</span></span>
    
    <span data-ttu-id="e6f9d-133">ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-133">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="e6f9d-134">アカウントの表示名とロールの名前を判別した後、次のコマンドを使用してアカウントにロールを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-134">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="e6f9d-p107">コマンドをコピーし、メモ帳に貼り付けます。**$dispName** 変数と **$roleName** 変数に関しては、説明テキスト部分を値に置き換えて、\< 記号と > 記号を削除します。引用符はそのまま残します。変更後の行をコピーし、[Windows PowerShell 用 Windows Azure Active Directory モジュール] ウィンドウに貼り付けて実行します。または、Windows PowerShell 統合スクリプト環境 (ISE) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-p107">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="e6f9d-139">コマンド セットの完成例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-139">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="e6f9d-140">ユーザーアカウントのサインイン名</span><span class="sxs-lookup"><span data-stu-id="e6f9d-140">Sign-in names of user accounts</span></span>

<span data-ttu-id="e6f9d-141">ユーザーアカウントのサインイン名または Upn を使用する場合は、次の点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-141">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="e6f9d-142">ユーザーアカウントの UPN。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-142">The user account's UPN.</span></span>
    
    <span data-ttu-id="e6f9d-143">UPN がまだわからない場合は、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-143">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="e6f9d-144">このコマンドは、UPN で並べ替えて、一度に1画面ずつ、ユーザーアカウントの UPN を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-144">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="e6f9d-145">**Where** コマンドレットを使用すると、一覧をフィルター処理して、出力するセットを小さくできます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-145">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="e6f9d-146">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-146">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="e6f9d-147">このコマンドは、表示名が「John」で始まるユーザー アカウントのみを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-147">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="e6f9d-148">割り当てるロール。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-148">The role you want to assign.</span></span>
    
    <span data-ttu-id="e6f9d-149">ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-149">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="e6f9d-150">アカウントの UPN と役割の名前を取得したら、次のコマンドを使用してアカウントに役割を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-150">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="e6f9d-151">コマンドをコピーしてメモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-151">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="e6f9d-152">**$UpnName**変数と **$roleName**変数については、説明テキストをその値に置き換え\< 、および > 文字を削除して、引用符を残します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-152">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="e6f9d-153">変更された行をコピーして、windows PowerShell 用 Windows Azure Active Directory モジュールウィンドウに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-153">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="e6f9d-154">または、Windows PowerShell ISE を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-154">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="e6f9d-155">コマンド セットの完成例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-155">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="e6f9d-156">複数の役割の変更</span><span class="sxs-lookup"><span data-stu-id="e6f9d-156">Multiple role changes</span></span>

<span data-ttu-id="e6f9d-157">複数の役割の変更については、次のことを決定します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-157">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="e6f9d-158">構成するユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-158">Which user accounts that you want to configure.</span></span> <span data-ttu-id="e6f9d-159">前のセクションの方法を使用して、表示名または Upn のセットを収集できます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-159">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="e6f9d-160">各ユーザー アカウントに割り当てるロール。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-160">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="e6f9d-161">ユーザー アカウントに割り当てることができるロールの一覧を表示するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-161">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="e6f9d-162">次に、[表示名] または [UPN] および [役割名] フィールドを含むコンマ区切り値 (CSV) テキストファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-162">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="e6f9d-163">これは、Microsoft Excel で簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-163">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="e6f9d-164">表示名の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-164">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="e6f9d-165">その後、PowerShell コマンド プロンプトで CSV ファイルの場所を入力し、完成したコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="e6f9d-166">次に、Upn の例を示します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-166">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="e6f9d-167">その後、PowerShell コマンド プロンプトで CSV ファイルの場所を入力し、完成したコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="e6f9d-167">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="e6f9d-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6f9d-168">See also</span></span>

- [<span data-ttu-id="e6f9d-169">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="e6f9d-169">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="e6f9d-170">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="e6f9d-170">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="e6f9d-171">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="e6f9d-171">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
