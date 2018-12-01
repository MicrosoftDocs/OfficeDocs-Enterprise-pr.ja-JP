---
title: Office 365 PowerShell でユーザー アカウントを表示する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: '概要: 表示、リスト、または Office 365 の PowerShell でのさまざまな方法でユーザー アカウントを表示します。'
ms.openlocfilehash: f2743197456cc56f654e99e682108230420384c9
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123254"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="6c8e5-103">Office 365 PowerShell でユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="6c8e5-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="6c8e5-104">**の概要:** Office 365 の PowerShell でのさまざまな方法でユーザー アカウントを表示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="6c8e5-105">Office 365 の管理センターを使用するには、Office 365 テナントのアカウントを表示するのも Office 365 の PowerShell を使用して Office 365 の管理センターができないことがいくつかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="6c8e5-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="6c8e5-106">Before you begin</span></span>

<span data-ttu-id="6c8e5-p101">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information-with-azure-active-directory-powershell-for-graph"></a><span data-ttu-id="6c8e5-109">グラフのアクティブなディレクトリの PowerShell を Azure で Office 365 のユーザー アカウント情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-109">Display Office 365 user account information with Azure Active Directory PowerShell for Graph</span></span> 

<span data-ttu-id="6c8e5-110">次のセクションでは、ユーザー アカウント情報を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-110">The following sections describe how to display user account information.</span></span>

### <a name="all-accounts"></a><span data-ttu-id="6c8e5-111">すべてのアカウント</span><span class="sxs-lookup"><span data-stu-id="6c8e5-111">All accounts</span></span>

<span data-ttu-id="6c8e5-112">ユーザー アカウントの完全な一覧を表示するには、このコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-112">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="6c8e5-113">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-113">You should see information similar to this:</span></span>
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="a-specific-account"></a><span data-ttu-id="6c8e5-114">特定のアカウント</span><span class="sxs-lookup"><span data-stu-id="6c8e5-114">A specific account</span></span>

<span data-ttu-id="6c8e5-115">特定のユーザー アカウントを表示するには、ユーザー アカウントのユーザー プリンシパル名 (UPN) を入力、削除、"<"と">"文字、および次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-115">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account>
```

### <a name="additional-property-values-for-a-specific-account"></a><span data-ttu-id="6c8e5-116">特定のアカウントの追加のプロパティの値</span><span class="sxs-lookup"><span data-stu-id="6c8e5-116">Additional property values for a specific account</span></span>

<span data-ttu-id="6c8e5-117">既定では、 **Get AzureADUser**コマンドレットには、アカウントのオブジェクト Id、表示名、および UserPrincipalName プロパティのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-117">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="6c8e5-p102">詳細に表示するにはプロパティの一覧のオプションを選択できるコマンドレットを使用する**選択オブジェクト** **Get AzureADUser**コマンドレットと組み合わせて。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、1 つのコマンドの結果を取得し、次のコマンドを送信するのにはグラフのアクティブなディレクトリの PowerShell を Azure に伝えます。すべてのユーザー アカウントの表示名、部署、および UsageLocation を表示するコマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p102">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="6c8e5-121">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-121">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c8e5-122">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-122">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c8e5-123">のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-123">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="6c8e5-p103">すべてのユーザー アカウントのプロパティを表示するには、 **Select-object**コマンドレット、ワイルドカード文字 (\*) を特定のユーザー アカウントのすべてを表示するのに使用します。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p103">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="6c8e5-126">別の例としては、次のコマンドを使用して特定のユーザー アカウントの有効な状態をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-126">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <UPN of user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="some-accounts-based-on-a-common-property"></a><span data-ttu-id="6c8e5-127">一般的なプロパティに基づいていくつかのアカウント</span><span class="sxs-lookup"><span data-stu-id="6c8e5-127">Some accounts based on a common property</span></span>

<span data-ttu-id="6c8e5-p104">詳細表示するにはアカウントの一覧のオプションを選択することができます**Where-object**コマンドレットと組み合わせて使用**Get AzureADUser**コマンドレットです。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、1 つのコマンドの結果を取得し、次のコマンドを送信するのにはグラフのアクティブなディレクトリの PowerShell を Azure に伝えます。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p104">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="6c8e5-131">このコマンドは、グラフのアクティブなディレクトリの PowerShell を Azure を指示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-131">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="6c8e5-132">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-132">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c8e5-p105">指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** )。コマンドが UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell を指示する中かっこ、( \*\* $ \_。UsageLocation\*\* ) は指定されたものであるか ( **eq $Null** ) ではありません。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p105">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="6c8e5-p106">**UsageLocation**プロパティは、ユーザー アカウントに関連付けられている多くのプロパティの 1 つだけです。すべてのユーザー アカウントのプロパティを表示するには、 **Select-object**コマンドレット、ワイルドカード文字 (\*) を特定のユーザー アカウントのすべてを表示するのに使用します。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p106">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="6c8e5-p107">たとえば、この一覧で、**City** がユーザー アカウント プロパティの名前であるとします。つまり、以下のコマンドを使用すると、ロンドン在住のユーザーのユーザー アカウントすべての一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p107">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="6c8e5-p108">これらの例に示すように**Where-object**コマンドレットの構文は、 **、オブジェクト {$\_です**。[ユーザー アカウントのプロパティ名][比較演算子][値]**}**. > [比較演算子] が等号の**eq**の等しくないため、 **ne**より大きいは、 **-gt**と他の人の**強い**。 [値] は、通常の文字列 (文字、数字、およびその他の文字のシーケンス)、数値、または **$Null**未指定の > 詳細については[、オブジェクト](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p108">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="display-office-365-user-account-information-with-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="6c8e5-143">Microsoft Azure Active Directory モジュールを Windows PowerShell での Office 365 ユーザー アカウントの情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-143">Display Office 365 user account information with Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="6c8e5-144">次のセクションでは、ユーザー アカウント情報を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-144">The following sections describe how to display user account information.</span></span>

### <a name="all-accounts"></a><span data-ttu-id="6c8e5-145">すべてのアカウント</span><span class="sxs-lookup"><span data-stu-id="6c8e5-145">All accounts</span></span>

<span data-ttu-id="6c8e5-146">ユーザー アカウントの完全な一覧を表示するには、このコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-146">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="6c8e5-147">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-147">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="6c8e5-p109">**Get MsolUser**コマンドレットでは、表示されるユーザー アカウントのセットをフィルター処理するパラメーターのセットもあります。など、ライセンスのないユーザー (ユーザーが、Office 365 に追加されたこと、サービスのいずれかを使用するのにはライセンスされていないはまだ) の一覧の場合は、このコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p109">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="6c8e5-150">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-150">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="6c8e5-151">表示をフィルター処理する追加のパラメーターの詳細について表示するには、ユーザー アカウントの設定では、 [Get MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100))を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-151">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="a-specific-account"></a><span data-ttu-id="6c8e5-152">特定のアカウント</span><span class="sxs-lookup"><span data-stu-id="6c8e5-152">A specific account</span></span>

<span data-ttu-id="6c8e5-153">特定のユーザー アカウントを表示するには、ユーザー アカウントのユーザー プリンシパル名 (UPN) を入力、削除、"<"と">"文字、および次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-153">To display a specific user account, fill in the user principal name (UPN) of the user account, remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <UPN of user account>
```

### <a name="some-accounts-based-on-a-common-property"></a><span data-ttu-id="6c8e5-154">一般的なプロパティに基づいていくつかのアカウント</span><span class="sxs-lookup"><span data-stu-id="6c8e5-154">Some accounts based on a common property</span></span>

<span data-ttu-id="6c8e5-p110">詳細表示するにはアカウントの一覧のオプションを選択することができます**Where-object**コマンドレットと組み合わせて使用**Get MsolUser**コマンドレットです。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、Office 365 の PowerShell コマンドを 1 つの結果を取得し、次のコマンドを送信することを指示します。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p110">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="6c8e5-158">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-158">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c8e5-159">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-159">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c8e5-p111">指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** )。コマンドが UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell を指示する中かっこ、( \*\* $ \_。UsageLocation\*\* ) は指定されたものであるか ( **eq $Null** ) ではありません。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="6c8e5-162">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-162">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="6c8e5-p112">**UsageLocation**プロパティは、ユーザー アカウントに関連付けられている多くのプロパティの 1 つだけです。すべてのユーザー アカウントのプロパティを表示するには、 **Select-object**コマンドレット、ワイルドカード文字 (\*) を特定のユーザー アカウントのすべてを表示するのに使用します。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p112">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="6c8e5-p113">たとえば、この一覧で、**City** がユーザー アカウント プロパティの名前であるとします。つまり、以下のコマンドを使用すると、ロンドン在住のユーザーのユーザー アカウントすべての一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p113">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="6c8e5-p114">これらの例に示すように**Where-object**コマンドレットの構文は、 **、オブジェクト {$\_です**。[ユーザー アカウントのプロパティ名][比較演算子][値]**}**. [比較演算子] は、equals の**eq**が、等しくないため、 **ne**より大きいは、 **-gt**と他の人の**強い**です。 [値] は、通常 (文字、数字、およびその他の文字のシーケンス)、文字列、数値、または **$Null**指定されていないのです。詳細については[、オブジェクト](https://technet.microsoft.com/en-us/library/hh849715.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p114">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="6c8e5-173">ブロックされた次のコマンドでユーザー アカウントの状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-173">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="additional-property-values-for-accounts"></a><span data-ttu-id="6c8e5-174">アカウントの追加のプロパティ値</span><span class="sxs-lookup"><span data-stu-id="6c8e5-174">Additional property values for accounts</span></span>

<span data-ttu-id="6c8e5-175">既定で**Get MsolUser**コマンドレットでは、ユーザー アカウントの 3 つのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-175">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="6c8e5-176">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="6c8e5-176">UserPrincipalName</span></span>
    
- <span data-ttu-id="6c8e5-177">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6c8e5-177">DisplayName</span></span>
    
- <span data-ttu-id="6c8e5-178">isLicensed</span><span class="sxs-lookup"><span data-stu-id="6c8e5-178">isLicensed</span></span>
    
<span data-ttu-id="6c8e5-p115">ユーザー アカウントの一覧を指定するのに**Select-object**コマンドレットと組み合わせて**取得 MsolUser**を実行するには部門のユーザーの動作と、ユーザーが Office 365 のサービスを使用する国/地域などの追加のプロパティを作成する必要がある場合プロパティです。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p115">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="6c8e5-181">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c8e5-182">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c8e5-183">のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-183">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="6c8e5-184">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-184">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="6c8e5-p116">**Select-object**コマンドレットでは、目的のプロパティを表示するコマンドを選択することができます。すべてのユーザー アカウントのプロパティを参照してくださいするのにには、特定のユーザー アカウントのすべてを表示するのにはワイルドカード文字 (\*) を使用します。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p116">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="6c8e5-p117">アカウントの一覧をより選択的に表示する場合には、**Where-object** コマンドレットも使用できます。次に、使用場所が指定されていないユーザー アカウントのみを表示するコマンドの例を示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p117">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="6c8e5-190">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-190">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="6c8e5-191">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-191">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="6c8e5-p118">指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** ) し、結果の情報を次のコマンドを送信する ( **|** )。かっこの中には、コマンドは UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell ように指示する ( \*\* $ \_。UsageLocation\*\* ) は指定されたものであるか ( **eq $Null** ) ではありません。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p118">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="6c8e5-194">のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-194">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="6c8e5-195">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-195">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="6c8e5-p119">作成し、Office 365 のユーザーを管理するにディレクトリ同期を使用する場合、Office 365 ユーザーがから投影されたローカル アカウントを表示します。次は、ObjectGUID の既定のソース アンカーを使用するのには、Azure AD 接続が構成されていると仮定しています (ソース アンカーの設定に関する詳細を参照してください[Azure AD 接続: 概念のデザイン](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) powershell の Active Directory のモジュールを持っているを前提としていますされてインストールされている (を参照してください[RSAT ツール](https://www.microsoft.com/en-gb/download/details.aspx?id=45520))。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-p119">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="new-to-office-365"></a><span data-ttu-id="6c8e5-198">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="6c8e5-198">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
  
## <a name="see-also"></a><span data-ttu-id="6c8e5-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c8e5-199">See also</span></span>

[<span data-ttu-id="6c8e5-200">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="6c8e5-200">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="6c8e5-201">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="6c8e5-201">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="6c8e5-202">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="6c8e5-202">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

