---
title: Office 365 PowerShell でユーザー アカウントを表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
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
ms.openlocfilehash: 5b8243947caa4cf21012bb54187e46c31aa0b931
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072439"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="ffa73-103">Office 365 PowerShell でユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="ffa73-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="ffa73-104">Microsoft 365 管理センターを使用して Office 365 テナントのアカウントを表示することはできますが、Office 365 PowerShell を使用して、管理センターではできないいくつかの操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-104">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ffa73-105">Graph モジュールの Azure Active Directory PowerShell を使用する</span><span class="sxs-lookup"><span data-stu-id="ffa73-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ffa73-106">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="ffa73-107">すべてのアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="ffa73-107">View all accounts</span></span>

<span data-ttu-id="ffa73-108">ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-108">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="ffa73-109">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-109">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="ffa73-110">特定のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="ffa73-110">View a specific account</span></span>

<span data-ttu-id="ffa73-111">特定のユーザーアカウントを表示するには、ユーザーアカウントのサインインアカウント名 (UPN) を入力し、"<" と ">" 文字を削除して、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-111">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="ffa73-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-112">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="ffa73-113">特定のアカウントの追加のプロパティ値を表示する</span><span class="sxs-lookup"><span data-stu-id="ffa73-113">View additional property values for a specific account</span></span>

<span data-ttu-id="ffa73-114">既定では、 **set-azureaduser**コマンドレットでは、アカウントの ObjectID、DisplayName、および UserPrincipalName のプロパティのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="ffa73-115">表示するプロパティの一覧についてより選択的に選択するには、 **Select**コマンドレットと**set-azureaduser**コマンドレットを組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-115">To be more selective about the list of properties to display, you can use the **Select** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="ffa73-116">2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-116">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="ffa73-117">次に、すべてのユーザーアカウントの DisplayName、Department、および使用場所を表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-117">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

<span data-ttu-id="ffa73-118">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ffa73-119">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ffa73-120">ユーザーアカウント名、部署、および使用場所のみを表示します ( **DisplayName、department、および使用場所を選択し**ます)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-120">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="ffa73-121">ユーザーアカウントのすべてのプロパティを表示するには、 **Select**コマンドレットとワイルドカード文字 (\*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-121">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="ffa73-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-122">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="ffa73-123">別の例として、次のコマンドを使用して、特定のユーザーアカウントの有効な状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="ffa73-124">共通プロパティに基づいて一部のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="ffa73-124">View some accounts based on a common property</span></span>

<span data-ttu-id="ffa73-125">表示するアカウントの一覧をより詳細に選択できるようにするには、 **set-azureaduser**コマンドレットと組み合わせて**Where**コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-125">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="ffa73-126">2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-126">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="ffa73-127">次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-127">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="ffa73-128">次のコマンドは、Azure Active Directory PowerShell を Graph に対して次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="ffa73-129">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ffa73-130">使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます (Where {$\_.の場合は、-eq $Null}** ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-130">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="ffa73-131">中かっこの内側では、コマンドは、Office 365 PowerShell に対して、"アクセス先" ユーザーアカウントプロパティ ( \*\* $ \_) のアカウントセットのみを検索するように指示します。\*\* は、無効な場所) を指定しません ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="ffa73-131">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="ffa73-132">使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="ffa73-132">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="ffa73-133">ユーザーアカウントのすべてのプロパティを表示するには、 **Select**コマンドレットとワイルドカード文字 (\*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-133">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="ffa73-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-134">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="ffa73-135">たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="ffa73-135">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="ffa73-136">これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-136">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="ffa73-137">これらの例に示されて**いる where**コマンドレットの構文は、 **{$\_.**</span><span class="sxs-lookup"><span data-stu-id="ffa73-137">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="ffa73-138">[ユーザーアカウントのプロパティ名][比較演算子]金額 **}**. > [比較演算子] は、equals、 **-ne** for not equals、 **-lt** (より小さい、-gt (より大きい)、- **gt** (より大きい)、およびその他の場合に- **eq**を指定します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-138">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="ffa73-139">[value] は、通常、文字列 (一連の文字、数字、およびその他の文字)、数値、または **$Null**指定されていない> の場合は、「詳細情報」を[参照して](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1)ください。</span><span class="sxs-lookup"><span data-stu-id="ffa73-139">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ffa73-140">Windows PowerShell の Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="ffa73-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ffa73-141">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="ffa73-142">すべてのアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="ffa73-142">View all accounts</span></span>

<span data-ttu-id="ffa73-143">ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-143">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

>[!Note]
><span data-ttu-id="ffa73-144">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="ffa73-144">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="ffa73-145">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffa73-145">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="ffa73-146">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-146">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="ffa73-147">**Get-MsolUser** コマンドレットには、表示するユーザー アカウントのセットをフィルターにかけるための一連のパラメーターもあります。</span><span class="sxs-lookup"><span data-stu-id="ffa73-147">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="ffa73-148">たとえば、ライセンスのないユーザー (Office 365 に追加されていても、まだライセンスを持っていないユーザー) の一覧については、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-148">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="ffa73-149">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-149">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="ffa73-150">表示されるユーザーアカウントのセットをフィルター処理するための追加パラメーターの詳細については、「 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffa73-150">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  
### <a name="view-a-specific-account"></a><span data-ttu-id="ffa73-151">特定のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="ffa73-151">View a specific account</span></span>

<span data-ttu-id="ffa73-152">特定のユーザーアカウントを表示するには、ユーザーアカウントのユーザーアカウントのサインイン名 (UPN) を記入し、"<" と ">" 文字を削除して、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-152">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="ffa73-153">共通プロパティに基づいて一部のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="ffa73-153">View some accounts based on a common property</span></span>

<span data-ttu-id="ffa73-154">表示するアカウントの一覧をより詳細に選択できるようにするには、 **get-msoluser**コマンドレットと組み合わせて**Where**コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-154">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="ffa73-155">2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Office 365 PowerShell に対して1つのコマンドの結果を取得し、次のコマンドに送信するように指示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-155">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="ffa73-156">次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-156">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="ffa73-157">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-157">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ffa73-158">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-158">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ffa73-159">使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます (Where {$\_.の場合は、-eq $Null}** ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-159">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="ffa73-160">中かっこの内側では、コマンドは、Office 365 PowerShell に対して、"アクセス先" ユーザーアカウントプロパティ ( \*\* $ \_) のアカウントセットのみを検索するように指示します。\*\* は、無効な場所) を指定しません ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="ffa73-160">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="ffa73-161">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-161">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="ffa73-162">使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="ffa73-162">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="ffa73-163">ユーザーアカウントのすべてのプロパティを表示するには、 **Select**コマンドレットとワイルドカード文字 (\*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-163">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="ffa73-164">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-164">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="ffa73-165">たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="ffa73-165">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="ffa73-166">これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-166">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="ffa73-167">これらの例に示されて**いる where**コマンドレットの構文は、 **{$\_.**</span><span class="sxs-lookup"><span data-stu-id="ffa73-167">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="ffa73-168">[ユーザーアカウントのプロパティ名][比較演算子]金額 **}**.</span><span class="sxs-lookup"><span data-stu-id="ffa73-168">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="ffa73-169">[comparison operator] は **-eq** (等しい)、 **-ne** for not equals、 **-lt** (より小さい)、- **gt** (より大きい)、または他のものです。</span><span class="sxs-lookup"><span data-stu-id="ffa73-169">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="ffa73-170">[value] は通常、文字列 (一連の文字、数字、その他の文字)、数値、または **$Null**指定なしの場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-170">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="ffa73-171">詳細[につい](https://technet.microsoft.com/library/hh849715.aspx)ては、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffa73-171">See [Where](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="ffa73-172">ユーザーアカウントのブロックされた状態を確認するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-172">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="ffa73-173">アカウントの追加のプロパティ値を表示する</span><span class="sxs-lookup"><span data-stu-id="ffa73-173">View additional property values for accounts</span></span>

<span data-ttu-id="ffa73-174">**Get-msoluser**コマンドレットでは、既定でユーザーアカウントの3つのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-174">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="ffa73-175">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="ffa73-175">UserPrincipalName</span></span>
    
- <span data-ttu-id="ffa73-176">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ffa73-176">DisplayName</span></span>
    
- <span data-ttu-id="ffa73-177">isLicensed</span><span class="sxs-lookup"><span data-stu-id="ffa73-177">isLicensed</span></span>
    
<span data-ttu-id="ffa73-178">ユーザーが作業する部署や、ユーザーが Office 365 サービスを使用する国/地域など、追加のプロパティが必要な場合は、 **Select**コマンドレットと組み合わせて**get-msoluser**を実行して、ユーザーアカウントのプロパティの一覧を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-178">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="ffa73-179">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-179">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="ffa73-180">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ffa73-181">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ffa73-182">ユーザーアカウント名、部署、および使用場所のみを表示します ( **DisplayName、department、および使用場所を選択し**ます)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-182">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="ffa73-183">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-183">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="ffa73-184">**Select**コマンドレットを使用すると、コマンドに表示するプロパティを選択して選択できます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-184">The **Select** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="ffa73-185">ユーザーアカウントのすべてのプロパティを表示するには、ワイルドカード文字 (\*) を使用して、特定のユーザーアカウントに対してすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-185">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="ffa73-186">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-186">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="ffa73-187">表示するアカウントのリストをより詳細に選択できるようにするには、 **Where**コマンドレットを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-187">To be more selective about the list of accounts to display, you can also use the **Where** cmdlet.</span></span> <span data-ttu-id="ffa73-188">次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="ffa73-188">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="ffa73-189">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-189">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="ffa73-190">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-190">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="ffa73-191">使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます (Where {$\_.[実行場所-eq $Null}** )] を指定して、結果の情報**|** を次のコマンドに送信します ()。</span><span class="sxs-lookup"><span data-stu-id="ffa73-191">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="ffa73-192">中かっこ内では、コマンドは、Office 365 PowerShell に対して、"アクセス先" ユーザーアカウントプロパティ ( \*\* $ \_) のアカウントセットのみを検索するように指示します。\*\* は、無効な場所) を指定しません ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="ffa73-192">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="ffa73-193">ユーザーアカウント名、部署、および使用場所のみを表示します ( **DisplayName、department、および使用場所を選択し**ます)。</span><span class="sxs-lookup"><span data-stu-id="ffa73-193">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="ffa73-194">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-194">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="ffa73-195">ディレクトリ同期を使用して Office 365 ユーザーを作成および管理している場合は、Office 365 ユーザーがどのローカルアカウントから射影されているかを表示できます。</span><span class="sxs-lookup"><span data-stu-id="ffa73-195">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="ffa73-196">次の例では、Azure AD Connect が ObjectGUID の既定のソースアンカーを使用するように構成されていると仮定しています (ソースアンカーの構成の詳細については、「 [AZURE Ad connect: デザインの概念](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)」を参照して[ください)。](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)また、PowerShell の Active Directory ドメインサービスモジュールがインストールされていると仮定します</span><span class="sxs-lookup"><span data-stu-id="ffa73-196">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory Domain Services module for PowerShell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a><span data-ttu-id="ffa73-197">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffa73-197">See also</span></span>

[<span data-ttu-id="ffa73-198">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="ffa73-198">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ffa73-199">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="ffa73-199">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ffa73-200">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="ffa73-200">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

