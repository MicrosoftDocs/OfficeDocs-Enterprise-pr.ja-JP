---
title: Office 365 PowerShell でユーザー アカウントを表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: '概要: Office 365 PowerShell を使用して、さまざまな方法でユーザーアカウントを表示、一覧表示、または表示できます。'
ms.openlocfilehash: 0711bf945b863cb89d45a377f61a139b298ca6d7
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748405"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="16085-103">Office 365 PowerShell でユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="16085-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="16085-104">Microsoft 365 管理センターを使用して Office 365 テナントのアカウントを表示することはできますが、Office 365 PowerShell を使用して、管理センターではできないいくつかの操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="16085-104">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="16085-105">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="16085-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="16085-106">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="16085-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="16085-107">すべてのアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="16085-107">View all accounts</span></span>

<span data-ttu-id="16085-108">ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="16085-108">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="16085-109">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="16085-109">You should see information similar to this:</span></span>
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="16085-110">特定のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="16085-110">View a specific account</span></span>

<span data-ttu-id="16085-111">特定のユーザーアカウントを表示するには、ユーザーアカウントのサインインアカウント名 (UPN) を入力し、"<" と ">" 文字を削除して、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="16085-111">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="16085-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-112">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="16085-113">特定のアカウントの追加のプロパティ値を表示する</span><span class="sxs-lookup"><span data-stu-id="16085-113">View additional property values for a specific account</span></span>

<span data-ttu-id="16085-114">既定では、 **set-azureaduser**コマンドレットでは、アカウントの ObjectID、DisplayName、および UserPrincipalName のプロパティのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="16085-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="16085-115">表示するプロパティの一覧についてより詳細な情報を得るには、 **set-azureaduser**コマンドレットと組み合わせて、**オブジェクト**のコマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="16085-115">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="16085-116">2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。</span><span class="sxs-lookup"><span data-stu-id="16085-116">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="16085-117">次に、すべてのユーザーアカウントの DisplayName、Department、および使用場所を表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-117">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="16085-118">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="16085-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="16085-119">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="16085-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="16085-120">ユーザーアカウント名、部署、使用場所のみを表示する (**選択-オブジェクト DisplayName、部署、使用場所**)。</span><span class="sxs-lookup"><span data-stu-id="16085-120">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="16085-121">ユーザーアカウントのすべてのプロパティを表示するには、**オブジェクトの選択**コマンドレットとワイルドカード文字 (\*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="16085-121">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="16085-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-122">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="16085-123">別の例として、次のコマンドを使用して、特定のユーザーアカウントの有効な状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="16085-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="16085-124">共通プロパティに基づいて一部のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="16085-124">View some accounts based on a common property</span></span>

<span data-ttu-id="16085-125">表示するアカウントのリストをより詳細に選択できるようにするには、 **set-azureaduser**コマンドレットと組み合わせて、**オブジェクト**のコマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="16085-125">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="16085-126">2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。</span><span class="sxs-lookup"><span data-stu-id="16085-126">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="16085-127">次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-127">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="16085-128">次のコマンドは、Azure Active Directory PowerShell を Graph に対して次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="16085-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="16085-129">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="16085-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="16085-130">使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます\_(Where オブジェクト {$.の場合は、-eq $Null}** ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="16085-130">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="16085-131">中かっこの内側では、コマンドは、Office 365 PowerShell に対して、"アクセス先" ユーザーアカウントプロパティ ( \*\* $ \_) のアカウントセットのみを検索するように指示します。\*\* は、無効な場所) を指定しません ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="16085-131">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="16085-132">使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="16085-132">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="16085-133">ユーザーアカウントのすべてのプロパティを表示するには、**オブジェクトの選択**コマンドレットとワイルドカード文字 (\*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="16085-133">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="16085-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-134">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="16085-135">たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="16085-135">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="16085-136">これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="16085-136">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="16085-137">これらの例に示され**ている where-object コマンドレット**の構文は、 **where オブジェクト {\_$ にあります。**</span><span class="sxs-lookup"><span data-stu-id="16085-137">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="16085-138">[ユーザーアカウントのプロパティ名][比較演算子]金額 **}**. > [比較演算子] は、equals、 **-ne** for not equals、 **-lt** (より小さい、-gt (より大きい)、- **gt** (より大きい)、およびその他の場合に- **eq**を指定します。</span><span class="sxs-lookup"><span data-stu-id="16085-138">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="16085-139">[value] は通常、指定されていない文字列 (一連の文字、数字、およびその他の文字)、数値、または **$Null**を指定しない> の場合は、 [Where オブジェクト](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1)を参照してください。詳細については、ここを参照してください。</span><span class="sxs-lookup"><span data-stu-id="16085-139">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="16085-140">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="16085-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="16085-141">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="16085-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="16085-142">すべてのアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="16085-142">View all accounts</span></span>

<span data-ttu-id="16085-143">ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="16085-143">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

<span data-ttu-id="16085-144">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="16085-144">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="16085-145">**Get-MsolUser** コマンドレットには、表示するユーザー アカウントのセットをフィルターにかけるための一連のパラメーターもあります。</span><span class="sxs-lookup"><span data-stu-id="16085-145">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="16085-146">たとえば、ライセンスのないユーザー (Office 365 に追加されていても、まだライセンスを持っていないユーザー) の一覧については、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="16085-146">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="16085-147">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="16085-147">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="16085-148">表示されるユーザーアカウントのセットをフィルター処理するための追加パラメーターの詳細については、「 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16085-148">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="16085-149">特定のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="16085-149">View a specific account</span></span>

<span data-ttu-id="16085-150">特定のユーザーアカウントを表示するには、ユーザーアカウントのユーザーアカウントのサインイン名 (UPN) を記入し、"<" と ">" 文字を削除して、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="16085-150">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="16085-151">共通プロパティに基づいて一部のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="16085-151">View some accounts based on a common property</span></span>

<span data-ttu-id="16085-152">表示するアカウントのリストをより詳細に選択できるようにするには、 **get-msoluser**コマンドレットと組み合わせて、**オブジェクト**のコマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="16085-152">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="16085-153">2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Office 365 PowerShell に対して1つのコマンドの結果を取得し、次のコマンドに送信するように指示します。</span><span class="sxs-lookup"><span data-stu-id="16085-153">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="16085-154">次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-154">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="16085-155">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="16085-155">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="16085-156">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="16085-156">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="16085-157">使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます\_(Where オブジェクト {$.の場合は、-eq $Null}** ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="16085-157">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="16085-158">中かっこの内側では、コマンドは、Office 365 PowerShell に対して、"アクセス先" ユーザーアカウントプロパティ ( \*\* $ \_) のアカウントセットのみを検索するように指示します。\*\* は、無効な場所) を指定しません ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="16085-158">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="16085-159">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="16085-159">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="16085-160">使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="16085-160">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="16085-161">ユーザーアカウントのすべてのプロパティを表示するには、**オブジェクトの選択**コマンドレットとワイルドカード文字 (\*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="16085-161">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="16085-162">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-162">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="16085-163">たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="16085-163">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="16085-164">これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="16085-164">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="16085-165">これらの例に示され**ている where-object コマンドレット**の構文は、 **where オブジェクト {\_$ にあります。**</span><span class="sxs-lookup"><span data-stu-id="16085-165">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="16085-166">[ユーザーアカウントのプロパティ名][比較演算子]金額 **}**.</span><span class="sxs-lookup"><span data-stu-id="16085-166">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="16085-167">[comparison operator] は **-eq** (等しい)、 **-ne** for not equals、 **-lt** (より小さい)、- **gt** (より大きい)、または他のものです。</span><span class="sxs-lookup"><span data-stu-id="16085-167">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="16085-168">[value] は通常、文字列 (一連の文字、数字、その他の文字)、数値、または **$Null**指定なしの場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="16085-168">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="16085-169">詳細については[、「Where オブジェクト](https://technet.microsoft.com/library/hh849715.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16085-169">See [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="16085-170">ユーザーアカウントのブロックされた状態を確認するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="16085-170">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="16085-171">アカウントの追加のプロパティ値を表示する</span><span class="sxs-lookup"><span data-stu-id="16085-171">View additional property values for accounts</span></span>

<span data-ttu-id="16085-172">**Get-msoluser**コマンドレットでは、既定でユーザーアカウントの3つのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="16085-172">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="16085-173">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="16085-173">UserPrincipalName</span></span>
    
- <span data-ttu-id="16085-174">DisplayName</span><span class="sxs-lookup"><span data-stu-id="16085-174">DisplayName</span></span>
    
- <span data-ttu-id="16085-175">isLicensed</span><span class="sxs-lookup"><span data-stu-id="16085-175">isLicensed</span></span>
    
<span data-ttu-id="16085-176">ユーザーが作業する部署や、ユーザーが Office 365 サービスを使用する国/地域など、追加のプロパティが必要な場合**は、get-msoluser コマンドレット**と組み合わせて\*\*\*\* を実行して、ユーザーアカウントのプロパティの一覧を指定できます。</span><span class="sxs-lookup"><span data-stu-id="16085-176">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="16085-177">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-177">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="16085-178">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="16085-178">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="16085-179">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="16085-179">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="16085-180">ユーザーアカウント名、部署、使用場所のみを表示する (**選択-オブジェクト DisplayName、部署、使用場所**)。</span><span class="sxs-lookup"><span data-stu-id="16085-180">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="16085-181">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="16085-181">You should see information similar to this:</span></span>
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="16085-182">**オブジェクトの選択**コマンドレットを使用すると、コマンドに表示するプロパティを選択して選択できます。</span><span class="sxs-lookup"><span data-stu-id="16085-182">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="16085-183">ユーザーアカウントのすべてのプロパティを表示するには、ワイルドカード文字 (\*) を使用して、特定のユーザーアカウントに対してすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="16085-183">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="16085-184">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-184">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="16085-185">表示するアカウントのリストをより詳細に選択できるようにするに**は、where-object コマンドレット**を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="16085-185">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet.</span></span> <span data-ttu-id="16085-186">次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="16085-186">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="16085-187">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="16085-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="16085-188">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="16085-188">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="16085-189">使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます\_(Where オブジェクト {$.[実行場所-eq $Null}** )] を指定して、結果の情報**|** を次のコマンドに送信します ()。</span><span class="sxs-lookup"><span data-stu-id="16085-189">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="16085-190">中かっこ内では、コマンドは、Office 365 PowerShell に対して、"アクセス先" ユーザーアカウントプロパティ ( \*\* $ \_) のアカウントセットのみを検索するように指示します。\*\* は、無効な場所) を指定しません ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="16085-190">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="16085-191">ユーザーアカウント名、部署、使用場所のみを表示する (**選択-オブジェクト DisplayName、部署、使用場所**)。</span><span class="sxs-lookup"><span data-stu-id="16085-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="16085-192">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="16085-192">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="16085-193">ディレクトリ同期を使用して Office 365 ユーザーを作成および管理している場合は、Office 365 ユーザーがどのローカルアカウントから射影されているかを表示できます。</span><span class="sxs-lookup"><span data-stu-id="16085-193">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="16085-194">次の例では、Azure AD Connect が ObjectGUID の既定のソースアンカーを使用するように構成されていると仮定しています (ソースアンカーの構成の詳細については、「 [AZURE Ad connect: デザインの概念](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)」を参照して[ください)。](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)また、powershell の Active Directory モジュールがインストールされていることを前提とします</span><span class="sxs-lookup"><span data-stu-id="16085-194">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="16085-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="16085-195">See also</span></span>

[<span data-ttu-id="16085-196">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="16085-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="16085-197">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="16085-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="16085-198">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="16085-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

