---
title: "Office 365 PowerShell でユーザー アカウント プロパティを構成する"
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
- Ent_Office_Other
- PowerShell
- apr17entnews
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: "概要:Office 365 PowerShell を使用して、Office 365 テナント内の個別のまたは複数のユーザー アカウントのプロパティを構成します。"
ms.openlocfilehash: d9e817530f3b1554cb757720f01afec5ed3b63ef
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="65f48-103">Office 365 PowerShell でユーザー アカウント プロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="65f48-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="65f48-104">**概要:** Office 365 PowerShell を使用して、Office 365 テナント内の個別のまたは複数のユーザー アカウントのプロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="65f48-104">Summary: Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="65f48-105">Office 365 管理センターを使用して Office 365 テナントのユーザー アカウントのプロパティを構成することもできますが、Office 365 PowerShell を使用すると、Office 365 管理センターでは行えない操作も実行できます。</span><span class="sxs-lookup"><span data-stu-id="65f48-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="65f48-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="65f48-106">Before you begin</span></span>

<span data-ttu-id="65f48-p101">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f48-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="65f48-109">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="65f48-109">Change properties for a specific user account</span></span>

<span data-ttu-id="65f48-p102">特定のユーザー アカウントのプロパティを構成する場合、[Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)) コマンドレットを使用して、設定または変更するプロパティを指定します。次の例のコマンドは、Belinda Newman の使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p102">To configure properties for a specific user account, you use the [Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="65f48-p103">**-UserPrincipalName** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="65f48-114">-City "\<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-114">-City "<city name>"</span></span>
    
- <span data-ttu-id="65f48-115">-Country "\<国名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-115">-Country "<country name>"</span></span>
    
- <span data-ttu-id="65f48-116">-Department "\<部署名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-116">-Department "<department name>"</span></span>
    
- <span data-ttu-id="65f48-117">-DisplayName "\<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-117">-DisplayName "<full user name>"</span></span>
    
- <span data-ttu-id="65f48-118">-Fax "\<fax 番号>"</span><span class="sxs-lookup"><span data-stu-id="65f48-118">-Fax "<fax number>"</span></span>
    
- <span data-ttu-id="65f48-119">-FirstName "\<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-119">-FirstName "<user first name>"</span></span>
    
- <span data-ttu-id="65f48-120">-LastName "\<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="65f48-120">-LastName "<user last name>"</span></span>
    
- <span data-ttu-id="65f48-121">-MobilePhone "\<携帯電話番号>"</span><span class="sxs-lookup"><span data-stu-id="65f48-121">-MobilePhone "<mobile phone number>"</span></span>
    
- <span data-ttu-id="65f48-122">-Office "\<事業所の場所>"</span><span class="sxs-lookup"><span data-stu-id="65f48-122">-Office "<office location>"</span></span>
    
- <span data-ttu-id="65f48-123">-PhoneNumber "\<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="65f48-123">-PhoneNumber "<office phone number>"</span></span>
    
- <span data-ttu-id="65f48-124">-PostalCode "\<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="65f48-124">-PostalCode "<postal code>"</span></span>
    
- <span data-ttu-id="65f48-125">-PreferredLanguage "\<言語>"</span><span class="sxs-lookup"><span data-stu-id="65f48-125">-PreferredLanguage "<language>"</span></span>
    
- <span data-ttu-id="65f48-126">-State "\<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-126">-State "<state name>"</span></span>
    
- <span data-ttu-id="65f48-127">-StreetAddress "\<番地>"</span><span class="sxs-lookup"><span data-stu-id="65f48-127">-StreetAddress "<street address>"</span></span>
    
- <span data-ttu-id="65f48-128">-Title "\<役職名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-128">-Title "<title name>"</span></span>
    
- <span data-ttu-id="65f48-129">-UsageLocation "\<2 文字の国/地域コード>"</span><span class="sxs-lookup"><span data-stu-id="65f48-129">-UsageLocation "<2-character country or region code>"</span></span>
    
    <span data-ttu-id="65f48-130">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="65f48-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="65f48-131">その他のパラメーターについては、[Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="65f48-131">See [Set-MsolUser]((https://msdn.microsoft.com/library/azure/dn194136.aspx)) for additional parameters.</span></span>
  
<span data-ttu-id="65f48-132">すべてのユーザーのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="65f48-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="65f48-133">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="65f48-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="65f48-134">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-135">ユーザー プリンシパル名のリストをアルファベット順に並び替えて (**Sort-Object UserPrincipalName**)、次のコマンドに送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-136">各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="65f48-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="65f48-137">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="65f48-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="65f48-p104">このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the $userName variable below (removing the < and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="65f48-140">次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="65f48-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="65f48-p105">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="65f48-143">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="65f48-143">Change properties for all user accounts</span></span>

<span data-ttu-id="65f48-p106">すべてのユーザーのプロパティを変更する場合には、 **Get-MsolUser** と **Set-MsolUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="65f48-146">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="65f48-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="65f48-147">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-148">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="65f48-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="65f48-149">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="65f48-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="65f48-p107">特定のユーザー アカウント セットのプロパティを変更する場合には、 **Get-MsolUser** 、 **Where-Object** 、 **Set-MsolUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="65f48-152">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="65f48-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="65f48-153">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-154">Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where-Object {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-155">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="65f48-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="65f48-156">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="65f48-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="65f48-157">Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウント プロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="65f48-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="65f48-p108">Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウントのプロパティを構成する場合には、[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) コマンドレットを使用して、設定または変更するプロパティを指定します。しかし、まずサブスクリプションに接続する必要があります。手順については、「[Azure Active Directory V2 PowerShell モジュールを使用した接続](https://go.microsoft.com/fwlink/?linkid=842218)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f48-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="65f48-161">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="65f48-161">Change properties for a specific user account</span></span>

<span data-ttu-id="65f48-162">次のコマンドの例では、Belinda Newman の使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="65f48-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="65f48-p109">**-ObjectID** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="65f48-165">-Department "\<部署名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-165">-Department "<department name>"</span></span>
    
- <span data-ttu-id="65f48-166">-DisplayName "\<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-166">-DisplayName "<full user name>"</span></span>
    
- <span data-ttu-id="65f48-167">-FacsimilieTelephoneNumber "\<fax 番号>"</span><span class="sxs-lookup"><span data-stu-id="65f48-167">-FacsimilieTelephoneNumber "<fax number>"</span></span>
    
- <span data-ttu-id="65f48-168">-GivenName "\<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-168">-GivenName "<user first name>"</span></span>
    
- <span data-ttu-id="65f48-169">-Surname "\<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="65f48-169">-Surname "<user last name>"</span></span>
    
- <span data-ttu-id="65f48-170">-Mobile "\<携帯電話番号>"</span><span class="sxs-lookup"><span data-stu-id="65f48-170">-Mobile "<mobile phone number>"</span></span>
    
- <span data-ttu-id="65f48-171">-JobTitle "\<役職>"</span><span class="sxs-lookup"><span data-stu-id="65f48-171">-JobTitle "<job title>"</span></span>
    
- <span data-ttu-id="65f48-172">-PreferredLanguage "\<言語>"</span><span class="sxs-lookup"><span data-stu-id="65f48-172">-PreferredLanguage "<language>"</span></span>
    
- <span data-ttu-id="65f48-173">-StreetAddress "\<番地>"</span><span class="sxs-lookup"><span data-stu-id="65f48-173">-StreetAddress "<street address>"</span></span>
    
- <span data-ttu-id="65f48-174">-City "\<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-174">-City "<city name>"</span></span>
    
- <span data-ttu-id="65f48-175">-State "\<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-175">-State "<state name>"</span></span>
    
- <span data-ttu-id="65f48-176">-PostalCode "\<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="65f48-176">-PostalCode "<postal code>"</span></span>
    
- <span data-ttu-id="65f48-177">-Country "\<国名>"</span><span class="sxs-lookup"><span data-stu-id="65f48-177">-Country "<country name>"</span></span>
    
- <span data-ttu-id="65f48-178">-TelephoneNumber "\<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="65f48-178">-TelephoneNumber "<office phone number>"</span></span>
    
- <span data-ttu-id="65f48-179">-UsageLocation "\<2 文字の国/地域コード>"</span><span class="sxs-lookup"><span data-stu-id="65f48-179">-UsageLocation "<2-character country or region code>"</span></span>
    
    <span data-ttu-id="65f48-180">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="65f48-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="65f48-181">その他のパラメーターについては、[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65f48-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="65f48-182">ユーザー アカウントのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="65f48-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="65f48-183">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="65f48-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="65f48-184">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-185">ユーザー プリンシパル名のリストをアルファベット順に並び替えて (**Sort-Object UserPrincipalName**)、次のコマンドに送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-186">各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="65f48-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="65f48-187">一度に 1 画面ずつ表示する (**More**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="65f48-p110">このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the $userName variable below (removing the < and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="65f48-190">次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="65f48-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="65f48-p111">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="65f48-193">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="65f48-193">Change properties for all user accounts</span></span>

<span data-ttu-id="65f48-p112">すべてのユーザーのプロパティを変更する場合には、 **Get-AzureADUser** と **Set-AzureADUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="65f48-196">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="65f48-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="65f48-197">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-198">ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="65f48-199">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="65f48-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="65f48-p113">特定のユーザー アカウント セットのプロパティを変更する場合には、**Get-AzureADUser**、**Where**、**Set-AzureADUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="65f48-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where-Object**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="65f48-202">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="65f48-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="65f48-203">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-204">Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( ** |**).</span></span>
    
- <span data-ttu-id="65f48-205">ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="65f48-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="65f48-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="65f48-206">See also</span></span>

#### 

[<span data-ttu-id="65f48-207">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="65f48-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="65f48-208">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="65f48-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="65f48-209">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="65f48-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

