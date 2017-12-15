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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="0ae50-103">Office 365 PowerShell でユーザー アカウント プロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="0ae50-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="0ae50-104">**の概要:**Office 365 の PowerShell を使用するには、Office 365 テナントに個人または複数のユーザー アカウントのプロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="0ae50-105">Office 365 管理センターを使用して Office 365 テナントのユーザー アカウントのプロパティを構成することもできますが、Office 365 PowerShell を使用すると、Office 365 管理センターでは行えない操作も実行できます。</span><span class="sxs-lookup"><span data-stu-id="0ae50-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="0ae50-106">開始する前に</span><span class="sxs-lookup"><span data-stu-id="0ae50-106">Before you begin</span></span>

<span data-ttu-id="0ae50-p101">このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="0ae50-109">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="0ae50-109">Change properties for a specific user account</span></span>

<span data-ttu-id="0ae50-p102">特定のユーザー アカウントのプロパティを構成する場合、[Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) コマンドレットを使用して、設定または変更するプロパティを指定します。次の例のコマンドは、Belinda Newman の使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="0ae50-p103">**-UserPrincipalName** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="0ae50-114">-都市"\<市区町村名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="0ae50-115">-国"\<国の名前 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="0ae50-116">-部門「\<部門名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="0ae50-117">-表示名"\<完全なユーザー名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="0ae50-118">-[Fax]\<fax 番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="0ae50-119">姓が"\<ユーザー名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="0ae50-120">[氏名] の"\<ユーザー名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="0ae50-121">MobilePhone-「\<携帯電話番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="0ae50-122">の Office"\<オフィスの所在地 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="0ae50-123">-電話番号"\<オフィスの電話番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="0ae50-124">-郵便番号"\<郵便番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="0ae50-125">-PreferredLanguage"\<言語 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="0ae50-126">-状態"\<状態の名前 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="0ae50-127">-番地"\<番地 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="0ae50-128">-タイトル"\<タイトル名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="0ae50-129">-UsageLocation"\<2 文字の国または地域番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="0ae50-130">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="0ae50-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="0ae50-131">その他のパラメーターについては、[Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0ae50-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="0ae50-132">すべてのユーザーのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="0ae50-133">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="0ae50-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0ae50-134">すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-135">ユーザー プリンシパル名の一覧をアルファベット順に並べ替え ( **Sort オブジェクトの UserPrincipalName** ) し、次のコマンドを送信 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-136">各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="0ae50-137">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="0ae50-p104">このコマンドは、すべてのアカウントが表示されます。表示に基づいて、アカウントのユーザー プリンシパル名を表示する場合は、名前 (姓と名)、 **$username$**変数を以下に入力 (削除、\<と > 文字)、し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="0ae50-140">次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ae50-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="0ae50-p105">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="0ae50-143">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="0ae50-143">Change properties for all user accounts</span></span>

<span data-ttu-id="0ae50-p106">すべてのユーザーのプロパティを変更する場合には、 **Get-MsolUser** と **Set-MsolUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="0ae50-146">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="0ae50-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0ae50-147">すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-148">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="0ae50-149">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="0ae50-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="0ae50-p107">特定のユーザー アカウント セットのプロパティを変更する場合には、 **Get-MsolUser** 、 **Where-Object** 、 **Set-MsolUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="0ae50-152">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="0ae50-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0ae50-153">すべてのユーザー アカウント ( **Get MsolUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-154">検索のすべてのユーザー アカウント プロパティを持つその部門「会計」に設定する ( **Where-object {$_ です。部門 eq「経理」}** ) し、結果の情報を次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-155">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="0ae50-156">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="0ae50-157">Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウント プロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="0ae50-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="0ae50-p108">Azure Active Directory V2 PowerShell モジュールを使用してユーザー アカウントのプロパティを構成するには、[セット AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)コマンドレットを使用しを設定または変更するにはプロパティを指定します。ですが、最初に、サービスに接続する必要があります。この手順では、 [Azure Active Directory V2 PowerShell モジュールを使用して接続](https://go.microsoft.com/fwlink/?linkid=842218)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="0ae50-161">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="0ae50-161">Change properties for a specific user account</span></span>

<span data-ttu-id="0ae50-162">次のコマンドの例では、Belinda Newman の使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="0ae50-p109">**-ObjectID** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="0ae50-165">-部門「\<部門名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="0ae50-166">-表示名"\<完全なユーザー名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="0ae50-167">-FacsimilieTelephoneNumber"\<fax 番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="0ae50-168">GivenName の「\<ユーザー名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="0ae50-169">-姓の"\<ユーザー名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="0ae50-170">-モバイル"\<携帯電話番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="0ae50-171">-役職」\<ジョブのタイトル >]</span><span class="sxs-lookup"><span data-stu-id="0ae50-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="0ae50-172">-PreferredLanguage"\<言語 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="0ae50-173">-番地"\<番地 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="0ae50-174">-都市"\<市区町村名 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="0ae50-175">-状態"\<状態の名前 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="0ae50-176">-郵便番号"\<郵便番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="0ae50-177">-国"\<国の名前 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="0ae50-178">勤務先の"\<オフィスの電話番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="0ae50-179">-UsageLocation"\<2 文字の国または地域番号 >"</span><span class="sxs-lookup"><span data-stu-id="0ae50-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="0ae50-180">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="0ae50-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="0ae50-181">その他のパラメーターについては、[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ae50-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="0ae50-182">ユーザー アカウントのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="0ae50-183">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="0ae50-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0ae50-184">すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-185">ユーザー プリンシパル名の一覧をアルファベット順に並べ替え ( **Sort オブジェクトの UserPrincipalName** ) し、次のコマンドを送信 ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-186">各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="0ae50-187">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="0ae50-p110">このコマンドは、すべてのアカウントが表示されます。表示に基づいて、アカウントのユーザー プリンシパル名を表示する場合は、名前 (姓と名)、 **$username$**変数を以下に入力 (削除、\<と > 文字)、し、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="0ae50-190">次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ae50-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="0ae50-p111">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="0ae50-193">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="0ae50-193">Change properties for all user accounts</span></span>

<span data-ttu-id="0ae50-p112">すべてのユーザーのプロパティを変更する場合には、 **Get-AzureADUser** と **Set-AzureADUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="0ae50-196">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="0ae50-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0ae50-197">すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-198">ユーザーの所在地をフランスに設定します ( **Set-AzureADUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="0ae50-199">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="0ae50-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="0ae50-p113">ユーザー アカウントの特定のセットのプロパティを変更するには、 **Get AzureADUser**、**場所**、および**セット AzureADUser**コマンドレットの組み合わせを使用できます。次の例では、フランスに会計部署のすべてのユーザーの利用状況の場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="0ae50-202">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="0ae50-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="0ae50-203">すべてのユーザー アカウント ( **Get AzureADUser** ) の情報を取得し、次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-204">すべての部門のプロパティ「会計」に設定されているユーザー アカウントの検索 ( **、{$_ です。部門 eq「経理」}** ) し、結果の情報を次のコマンドを送信する ( **|** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="0ae50-205">ユーザーの所在地をフランスに設定します ( **Set-AzureADUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="0ae50-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="0ae50-206">See also</span><span class="sxs-lookup"><span data-stu-id="0ae50-206">See also</span></span>

#### 

[<span data-ttu-id="0ae50-207">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="0ae50-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="0ae50-208">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="0ae50-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="0ae50-209">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="0ae50-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

