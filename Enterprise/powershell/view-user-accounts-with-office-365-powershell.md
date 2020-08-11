---
title: PowerShell を使用して Microsoft 365 ユーザーアカウントを表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: PowerShell を使用して、Microsoft 365 ユーザーアカウントをさまざまな方法で表示、一覧表示、または表示する方法について説明します。
ms.openlocfilehash: 56da6bfc7b467b6a85a4bd8c84abd4c2ae05913f
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605298"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="c508b-103">PowerShell を使用して Microsoft 365 ユーザーアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="c508b-103">View Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="c508b-104">*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="c508b-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="c508b-105">Microsoft 365 管理センターを使用して Microsoft 365 テナントのアカウントを表示することはできますが、microsoft 365 の PowerShell を使用して、管理センターではできないことを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="c508b-105">Although you can use the Microsoft 365 admin center to view the accounts for your Microsoft 365 tenant, you can also use PowerShell for Microsoft 365 and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c508b-106">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="c508b-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c508b-107">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)します。</span><span class="sxs-lookup"><span data-stu-id="c508b-107">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="c508b-108">すべてのアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="c508b-108">View all accounts</span></span>

<span data-ttu-id="c508b-109">ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c508b-109">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="c508b-110">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c508b-110">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="c508b-111">特定のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="c508b-111">View a specific account</span></span>

<span data-ttu-id="c508b-112">特定のユーザーアカウントを表示するには、ユーザーアカウントのサインインアカウント名 (UPN) を入力し、"<" と ">" 文字を削除して、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c508b-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="c508b-113">次に例を示します：</span><span class="sxs-lookup"><span data-stu-id="c508b-113">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="c508b-114">特定のアカウントの追加のプロパティ値を表示する</span><span class="sxs-lookup"><span data-stu-id="c508b-114">View additional property values for a specific account</span></span>

<span data-ttu-id="c508b-115">既定では、 **set-azureaduser**コマンドレットでは、アカウントの ObjectID、DisplayName、および UserPrincipalName のプロパティのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c508b-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="c508b-116">表示するプロパティの一覧についてより選択的に選択するには、 **Select**コマンドレットと**set-azureaduser**コマンドレットを組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="c508b-116">To be more selective about the list of properties to display, you can use the **Select** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="c508b-117">2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="c508b-118">次に、すべてのユーザーアカウントの DisplayName、Department、および使用場所を表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

<span data-ttu-id="c508b-119">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-119">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="c508b-120">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="c508b-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c508b-121">ユーザーアカウント名、部署、および使用場所のみを表示します ( **DisplayName、department、および使用場所を選択し**ます)。</span><span class="sxs-lookup"><span data-stu-id="c508b-121">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="c508b-122">ユーザーアカウントのすべてのプロパティを表示するには、 **Select**コマンドレットとワイルドカード文字 (\*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-122">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="c508b-123">次に例を示します：</span><span class="sxs-lookup"><span data-stu-id="c508b-123">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="c508b-124">別の例として、次のコマンドを使用して、特定のユーザーアカウントの有効な状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c508b-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="c508b-125">共通プロパティに基づいて一部のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="c508b-125">View some accounts based on a common property</span></span>

<span data-ttu-id="c508b-126">表示するアカウントの一覧をより詳細に選択できるようにするには、 **set-azureaduser**コマンドレットと組み合わせて**Where**コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="c508b-126">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="c508b-127">2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、Azure Active Directory PowerShell が1つのコマンドの結果を取得して次のコマンドに送信するように指示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="c508b-128">次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="c508b-129">次のコマンドは、Azure Active Directory PowerShell を Graph に対して次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="c508b-130">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="c508b-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c508b-131">使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます (Where {$ \_ .の場合は、-eq $Null}** ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c508b-131">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="c508b-132">中かっこ内では、コマンドによって、アクセス先ユーザーアカウントプロパティ (という) のアカウントセットのみが検索され\*\* $ \_ ます。\*\* は、無効な場所) を指定しません ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="c508b-132">Inside the braces, the command instructs PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="c508b-133">使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="c508b-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="c508b-134">ユーザーアカウントのすべてのプロパティを表示するには、 **Select**コマンドレットとワイルドカード文字 (\*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-134">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="c508b-135">次に例を示します：</span><span class="sxs-lookup"><span data-stu-id="c508b-135">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="c508b-136">たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="c508b-136">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="c508b-137">これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c508b-137">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="c508b-138">これらの例に示されて**いる where**コマンドレットの構文は、 **{$ \_ .**</span><span class="sxs-lookup"><span data-stu-id="c508b-138">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="c508b-139">[ユーザーアカウントのプロパティ名][比較演算子]金額 **}**. > [比較演算子] は、equals、 **-ne** for not equals、 **-lt** (より小さい、-gt (より大きい)、- **gt** (より大きい)、およびその他の場合に- **eq**を指定します。</span><span class="sxs-lookup"><span data-stu-id="c508b-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="c508b-140">[value] は、通常、文字列 (一連の文字、数字、およびその他の文字)、数値、または **$Null**指定されていない> の場合は、「詳細情報」を[参照して](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1)ください。</span><span class="sxs-lookup"><span data-stu-id="c508b-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c508b-141">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="c508b-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c508b-142">最初に、 [Microsoft 365 テナントに接続](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)します。</span><span class="sxs-lookup"><span data-stu-id="c508b-142">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="c508b-143">すべてのアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="c508b-143">View all accounts</span></span>

<span data-ttu-id="c508b-144">ユーザーアカウントの完全な一覧を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c508b-144">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

>[!Note]
><span data-ttu-id="c508b-145">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c508b-145">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="c508b-146">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c508b-146">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="c508b-147">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c508b-147">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="c508b-148">**Get-MsolUser** コマンドレットには、表示するユーザー アカウントのセットをフィルターにかけるための一連のパラメーターもあります。</span><span class="sxs-lookup"><span data-stu-id="c508b-148">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="c508b-149">たとえば、ライセンスのないユーザー (Microsoft 365 に追加されていても、サービスのいずれかを使用するライセンスを持っていないユーザー) の一覧については、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c508b-149">For example, for the list of unlicensed users (users who've been added to Microsoft 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="c508b-150">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c508b-150">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="c508b-151">表示されるユーザーアカウントのセットをフィルター処理するための追加パラメーターの詳細については、「 [get-msoluser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c508b-151">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  
### <a name="view-a-specific-account"></a><span data-ttu-id="c508b-152">特定のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="c508b-152">View a specific account</span></span>

<span data-ttu-id="c508b-153">特定のユーザーアカウントを表示するには、ユーザーアカウントのユーザーアカウントのサインイン名 (UPN) を記入し、"<" と ">" 文字を削除して、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c508b-153">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="c508b-154">共通プロパティに基づいて一部のアカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="c508b-154">View some accounts based on a common property</span></span>

<span data-ttu-id="c508b-155">表示するアカウントの一覧をより詳細に選択できるようにするには、 **get-msoluser**コマンドレットと組み合わせて**Where**コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="c508b-155">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="c508b-156">2つのコマンドレットを組み合わせるには、"pipe" 文字 "|" を使用します。これは、1つのコマンドの結果を受け取って次のコマンドに送信するように PowerShell に指示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-156">To combine the two cmdlets, we use the "pipe" character "|", which tells PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="c508b-157">次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-157">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="c508b-158">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-158">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="c508b-159">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="c508b-159">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c508b-160">使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます (Where {$ \_ .の場合は、-eq $Null}** ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c508b-160">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="c508b-161">中かっこ内では、コマンドによって、アクセス先ユーザーアカウントプロパティ (という) のアカウントセットのみが検索され\*\* $ \_ ます。\*\* は、無効な場所) を指定しません ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="c508b-161">Inside the braces, the command instructs PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="c508b-162">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c508b-162">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="c508b-163">使用**場所**プロパティは、ユーザーアカウントに関連付けられている多くのプロパティのうちの1つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="c508b-163">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="c508b-164">ユーザーアカウントのすべてのプロパティを表示するには、 **Select**コマンドレットとワイルドカード文字 (\*) を使用して、特定のユーザーアカウントについてすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-164">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="c508b-165">次に例を示します：</span><span class="sxs-lookup"><span data-stu-id="c508b-165">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="c508b-166">たとえば、このリストから、 **City**はユーザーアカウントプロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="c508b-166">For example, from this list, **City** is the name of a user account property.</span></span> <span data-ttu-id="c508b-167">これは、次のコマンドを使用して、London に住むユーザーのすべてのユーザーアカウントを一覧表示できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c508b-167">This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="c508b-168">これらの例に示されて**いる where**コマンドレットの構文は、 **{$ \_ .**</span><span class="sxs-lookup"><span data-stu-id="c508b-168">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="c508b-169">[ユーザーアカウントのプロパティ名][比較演算子]金額 **}**.</span><span class="sxs-lookup"><span data-stu-id="c508b-169">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="c508b-170">[comparison operator] は **-eq** (等しい)、 **-ne** for not equals、 **-lt** (より小さい)、- **gt** (より大きい)、または他のものです。</span><span class="sxs-lookup"><span data-stu-id="c508b-170">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="c508b-171">[value] は通常、文字列 (一連の文字、数字、その他の文字)、数値、または **$Null**指定なしの場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c508b-171">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="c508b-172">詳細[につい](https://technet.microsoft.com/library/hh849715.aspx)ては、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c508b-172">See [Where](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="c508b-173">ユーザーアカウントのブロックされた状態を確認するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c508b-173">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="c508b-174">アカウントの追加のプロパティ値を表示する</span><span class="sxs-lookup"><span data-stu-id="c508b-174">View additional property values for accounts</span></span>

<span data-ttu-id="c508b-175">**Get-msoluser**コマンドレットでは、既定でユーザーアカウントの3つのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-175">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="c508b-176">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="c508b-176">UserPrincipalName</span></span>
    
- <span data-ttu-id="c508b-177">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c508b-177">DisplayName</span></span>
    
- <span data-ttu-id="c508b-178">isLicensed</span><span class="sxs-lookup"><span data-stu-id="c508b-178">isLicensed</span></span>
    
<span data-ttu-id="c508b-179">ユーザーが作業する部署や、ユーザーが Microsoft 365 サービスを使用する国/地域など、追加のプロパティが必要な場合は、 **Select**コマンドレットと組み合わせて**get-msoluser**を実行して、ユーザーアカウントのプロパティの一覧を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c508b-179">If you need additional properties, such as the department the user works for and the country/region where the user uses Microsoft 365 services, you can run **Get-MsolUser** in combination with the **Select** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="c508b-180">次に例を示します：</span><span class="sxs-lookup"><span data-stu-id="c508b-180">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="c508b-181">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-181">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="c508b-182">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="c508b-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c508b-183">ユーザーアカウント名、部署、および使用場所のみを表示します ( **DisplayName、department、および使用場所を選択し**ます)。</span><span class="sxs-lookup"><span data-stu-id="c508b-183">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="c508b-184">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c508b-184">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="c508b-185">**Select**コマンドレットを使用すると、コマンドに表示するプロパティを選択して選択できます。</span><span class="sxs-lookup"><span data-stu-id="c508b-185">The **Select** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="c508b-186">ユーザーアカウントのすべてのプロパティを表示するには、ワイルドカード文字 (\*) を使用して、特定のユーザーアカウントに対してすべてのプロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-186">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="c508b-187">次に例を示します：</span><span class="sxs-lookup"><span data-stu-id="c508b-187">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="c508b-188">表示するアカウントのリストをより詳細に選択できるようにするには、 **Where**コマンドレットを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c508b-188">To be more selective about the list of accounts to display, you can also use the **Where** cmdlet.</span></span> <span data-ttu-id="c508b-189">次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-189">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="c508b-190">次のコマンドは、PowerShell に次のように指示します。</span><span class="sxs-lookup"><span data-stu-id="c508b-190">This command instructs PowerShell to:</span></span>
  
- <span data-ttu-id="c508b-191">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="c508b-191">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="c508b-192">使用できない場所が指定されているすべてのユーザーアカウントを検索し**ます (Where {$ \_ .[実行場所-eq $Null}** )] を指定して、結果の情報を次のコマンドに送信し **|** ます ()。</span><span class="sxs-lookup"><span data-stu-id="c508b-192">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="c508b-193">中かっこで囲まれている場合、コマンドは、ユーザーアカウントプロパティ (という) があるアカウントのセットのみを検索するように PowerShell に指示し\*\* $ \_ ます。\*\* は、無効な場所) を指定しません ( **-eq $Null** )。</span><span class="sxs-lookup"><span data-stu-id="c508b-193">Inside the braces, the command is instructing PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="c508b-194">ユーザーアカウント名、部署、および使用場所のみを表示します ( **DisplayName、department、および使用場所を選択し**ます)。</span><span class="sxs-lookup"><span data-stu-id="c508b-194">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="c508b-195">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c508b-195">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="c508b-196">ディレクトリ同期を使用して Microsoft 365 ユーザーを作成および管理している場合は、Microsoft 365 ユーザーが射影したローカルアカウントを表示できます。</span><span class="sxs-lookup"><span data-stu-id="c508b-196">If you are using directory synchronization to create and manage your Microsoft 365 users, you can display which local account a Microsoft 365 user has been projected from.</span></span> <span data-ttu-id="c508b-197">次の例では、Azure AD Connect が ObjectGUID の既定のソースアンカーを使用するように構成されていると仮定しています (ソースアンカーの構成の詳細については、「 [AZURE Ad connect: デザインの概念](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)」を参照して[ください)。](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)また、PowerShell の Active Directory ドメインサービスモジュールがインストールされていると仮定します</span><span class="sxs-lookup"><span data-stu-id="c508b-197">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory Domain Services module for PowerShell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a><span data-ttu-id="c508b-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="c508b-198">See also</span></span>

[<span data-ttu-id="c508b-199">Microsoft 365 ユーザー アカウント、ライセンス、PowerShell を使用したグループを管理する</span><span class="sxs-lookup"><span data-stu-id="c508b-199">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c508b-200">PowerShell で Microsoft 365を管理する</span><span class="sxs-lookup"><span data-stu-id="c508b-200">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c508b-201">Microsoft 365 用 PowerShell の使用を開始する</span><span class="sxs-lookup"><span data-stu-id="c508b-201">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

