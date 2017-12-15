---
title: "Office 365 PowerShell でユーザー アカウントを表示する"
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
- LIL_Placement
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: "概要: 表示、リスト、または Office 365 の PowerShell でのさまざまな方法でユーザー アカウントを表示します。"
ms.openlocfilehash: b27f9045d26d4dabd3ada70766491f722d822a91
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="a6ec4-103">Office 365 PowerShell でユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="a6ec4-103">View user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="a6ec4-104">**の概要:**ボックスの一覧を表示、または Office 365 の PowerShell でのさまざまな方法でユーザー アカウントを表示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-104">**Summary:** View, list, or display your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="a6ec4-105">Office 365 の管理センターを使用するには、Office 365 テナントのアカウントを表示するのも Office 365 の PowerShell を使用して Office 365 の管理センターができないことがいくつかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="a6ec4-106">開始する前に</span><span class="sxs-lookup"><span data-stu-id="a6ec4-106">Before you begin</span></span>

<span data-ttu-id="a6ec4-p101">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information"></a><span data-ttu-id="a6ec4-109">Office 365 ユーザー アカウント情報を表示する</span><span class="sxs-lookup"><span data-stu-id="a6ec4-109">Display Office 365 user account information</span></span>

<span data-ttu-id="a6ec4-110">ユーザー アカウントの完全な一覧を表示するには、Office 365 の PowerShell コマンド プロンプトまたは PowerShell 統合スクリプト環境 (ISE) でこのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-110">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="a6ec4-111">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-111">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="a6ec4-p102">**Get MsolUser**コマンドレットでは、表示されるユーザー アカウントのセットをフィルター処理するパラメーターのセットもあります。など、ライセンスのないユーザー (ユーザーが、Office 365 に追加されたこと、サービスのいずれかを使用するのにはライセンスされていないはまだ) の一覧の場合は、このコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p102">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="a6ec4-114">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-114">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="a6ec4-115">表示をフィルター処理する追加のパラメーターの詳細について表示するには、ユーザー アカウントの設定では、 [Get MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-115">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span></span>
  
<span data-ttu-id="a6ec4-p103">詳細表示するにはアカウントの一覧のオプションを選択することができます**Where-object**コマンドレットと組み合わせて使用**Get MsolUser**コマンドレットです。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、Office 365 の PowerShell コマンドを 1 つの結果を取得し、次のコマンドを送信することを指示します。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="a6ec4-119">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a6ec4-120">すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-120">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a6ec4-p104">指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** )。コマンドが UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell を指示する中かっこ、( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="a6ec4-123">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-123">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="a6ec4-p105">**UsageLocation**プロパティは、ユーザー アカウントに関連付けられている多くのプロパティの 1 つだけです。すべてのユーザー アカウントのプロパティを表示するには、 **Select-object**コマンドレット、ワイルドカード文字 (*) を特定のユーザー アカウントのすべてを表示するのに使用します。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="a6ec4-p106">たとえば、このボックスの一覧から**市区町村**はユーザー アカウントのプロパティの名前です。つまり、ロンドンに住んでいるユーザーのユーザー アカウントのすべてを一覧表示するのには次のコマンドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="a6ec4-p107">これらの例に示すように**Where-object**コマンドレットの構文は、 **、オブジェクト {$\_です**。[ユーザー アカウントのプロパティ名][比較演算子][値]**}**. > [比較演算子] が等号の**eq**の等しくないため、 **ne**より大きいは、 **-gt**と他の人の**強い**> [値] は、文字列 (文字、数字、およびその他の文字のシーケンス) では通常、数値、またはの**$Null**を指定しない > 詳細については[、オブジェクト](https://technet.microsoft.com/en-us/library/hh849715.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="a6ec4-131">ブロックされた次のコマンドでユーザー アカウントの状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-131">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="a6ec4-132">表示するユーザー アカウントのプロパティを選択する</span><span class="sxs-lookup"><span data-stu-id="a6ec4-132">Select the user account properties to display</span></span>

<span data-ttu-id="a6ec4-133">既定で[Get MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx)コマンドレットでは、ユーザー アカウントの 3 つのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-133">The [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="a6ec4-134">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="a6ec4-134">UserPrincipalName</span></span>
    
- <span data-ttu-id="a6ec4-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a6ec4-135">DisplayName</span></span>
    
- <span data-ttu-id="a6ec4-136">isLicensed</span><span class="sxs-lookup"><span data-stu-id="a6ec4-136">isLicensed</span></span>
    
<span data-ttu-id="a6ec4-p108">ユーザー アカウントの一覧を指定するのに**Select-object**コマンドレットと組み合わせて**取得 MsolUser**を実行するには部門のユーザーの動作と、ユーザーが Office 365 のサービスを使用する国/地域などの追加のプロパティを作成する必要がある場合プロパティです。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p108">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="a6ec4-139">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-139">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a6ec4-140">すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-140">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a6ec4-141">のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-141">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="a6ec4-142">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-142">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

<span data-ttu-id="a6ec4-p109">**Select-object**コマンドレットを使用すると、目的のプロパティを表示するコマンドを選択できます。すべてのユーザー アカウントのプロパティを参照してくださいするのにには、特定のユーザー アカウントのすべてを表示するのにはワイルドカード文字 (*) を使用します。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p109">The **Select-Object** cmdlet allows you to pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="a6ec4-p110">詳細に表示するにはアカウントの一覧のオプションを選択しても使用できます**Where-object**コマンドレット。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p110">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="a6ec4-148">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a6ec4-149">すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-149">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a6ec4-p111">指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** ) し、結果の情報を次のコマンドを送信する ( **|** )。かっこの中には、コマンドは UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell ように指示する ( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="a6ec4-152">のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-152">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="a6ec4-153">次のような情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-153">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a><span data-ttu-id="a6ec4-154">Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウントを表示する</span><span class="sxs-lookup"><span data-stu-id="a6ec4-154">Use the Azure Active Directory V2 PowerShell module to display user accounts</span></span>

<span data-ttu-id="a6ec4-p112">Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウントのプロパティを表示するには、 [Get AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0)コマンドレットを使用します。ですが、最初に、サービスに接続する必要があります。この手順では、[Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p112">To display properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="display-office-365-user-account-information"></a><span data-ttu-id="a6ec4-158">Office 365 ユーザー アカウント情報を表示する</span><span class="sxs-lookup"><span data-stu-id="a6ec4-158">Display Office 365 user account information</span></span>

<span data-ttu-id="a6ec4-159">ユーザー アカウントの完全な一覧を表示するには、Office 365 の PowerShell コマンド プロンプトまたは PowerShell 統合スクリプト環境 (ISE) でこのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-159">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="a6ec4-160">既定で**Get AzureADUser**コマンドレットでは、ユーザー アカウントの 3 つのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-160">The **Get-AzureADUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="a6ec4-161">オブジェクト Id</span><span class="sxs-lookup"><span data-stu-id="a6ec4-161">ObjectID</span></span>
    
- <span data-ttu-id="a6ec4-162">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a6ec4-162">DisplayName</span></span>
    
- <span data-ttu-id="a6ec4-163">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="a6ec4-163">UserPrincipalName</span></span>
    
<span data-ttu-id="a6ec4-p113">詳細表示するにはアカウントの一覧のオプションを選択することができます**Where-object**コマンドレットと組み合わせて使用**Get AzureADUser**コマンドレットです。「パイプ」文字を使用する 2 つのコマンドレットを結合するには、"|"、Office 365 の PowerShell コマンドを 1 つの結果を取得し、次のコマンドを送信することを指示します。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p113">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="a6ec4-167">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-167">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a6ec4-168">すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-168">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a6ec4-p114">指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** )。コマンドが UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell を指示する中かっこ、( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p114">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="a6ec4-p115">**UsageLocation**プロパティは、ユーザー アカウントに関連付けられている多くのプロパティの 1 つだけです。すべてのユーザー アカウントのプロパティを表示するには、 **Select-object**コマンドレット、ワイルドカード文字 (*) を 1 つのページ (**詳細**) の時に、特定のユーザー アカウントのそれらのすべてを表示するのに使用します。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p115">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account, one page at a time ( **More** ). Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

<span data-ttu-id="a6ec4-p116">などの**都市**は、ユーザー アカウントのプロパティの名前です。つまり、ロンドンに住んでいるユーザーのユーザー アカウントのすべてを一覧表示するのには次のコマンドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p116">For example, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="a6ec4-p117">これらの例に示すように**Where-object**コマンドレットの構文は、 **、オブジェクト {$\_です**。[ユーザー アカウントのプロパティ名][比較演算子][値]**}**. > [比較演算子] が等号の**eq**の等しくないため、 **ne**より大きいは、 **-gt**と他の人の**強い**> [値] は、文字列 (文字、数字、およびその他の文字のシーケンス) では通常、数値、またはの**$Null**を指定しない > 詳細については[、オブジェクト](https://technet.microsoft.com/en-us/library/hh849715.aspx)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p117">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
### <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="a6ec4-178">表示するユーザー アカウントのプロパティを選択する</span><span class="sxs-lookup"><span data-stu-id="a6ec4-178">Select the user account properties to display</span></span>

<span data-ttu-id="a6ec4-p118">既定で**Get AzureADUser**コマンドレットでは、ユーザー アカウントのオブジェクト Id、表示名、および UserPrincipalName プロパティを表示します。ユーザーのリストを指定する**Select-object**コマンドレットと組み合わせて**取得 AzureADUser**を実行するには部門のユーザーの動作と、ユーザーが Office 365 のサービスを使用する国/地域などの追加のプロパティを作成する必要がある場合アカウントのプロパティです。例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p118">The **Get-AzureADUser** cmdlet by default displays the ObjectID, DisplayName, and UserPrincipalName properties of user accounts. If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-AzureADUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="a6ec4-182">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-182">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a6ec4-183">すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-183">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a6ec4-184">のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-184">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="a6ec4-p119">詳細に表示するにはアカウントの一覧のオプションを選択しても使用できます**Where-object**コマンドレット。指定されていない使用法は、場所を持っているユーザーのアカウントのみを表示するコマンドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p119">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="a6ec4-187">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a6ec4-188">すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-188">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a6ec4-p120">指定されていない使用法は、場所を持っているユーザーのアカウントのすべてを検索 ( **、オブジェクト {$\_。$Null を eq - UsageLocation}** ) し、結果の情報を次のコマンドを送信する ( **|** )。かっこの中には、コマンドは UsageLocation ユーザー アカウントのプロパティでアカウントの設定だけを検索する Office 365 の PowerShell ように指示する ( ** $ \_。UsageLocation** ) は指定されたものであるか ( **eq $Null** ) ではありません。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p120">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="a6ec4-191">のみユーザー アカウント名、部署、および使用法の場所 (**選択オブジェクトの表示名、部門、UsageLocation** ) を表示します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
## <a name="new-to-office-365"></a><span data-ttu-id="a6ec4-192">Office 365 を初めて使用する場合</span><span class="sxs-lookup"><span data-stu-id="a6ec4-192">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="a6ec4-p121">![LinkedIn Learning の小さいアイコン](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 を初めて使用する場合は、**         LinkedIn Learning が提供する [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5) のための無料のビデオ コースをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-p121">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="a6ec4-195">See also</span><span class="sxs-lookup"><span data-stu-id="a6ec4-195">See also</span></span>

#### 

[<span data-ttu-id="a6ec4-196">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="a6ec4-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a6ec4-197">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="a6ec4-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a6ec4-198">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="a6ec4-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

