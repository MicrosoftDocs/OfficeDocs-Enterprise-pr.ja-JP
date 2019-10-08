---
title: Office 365 PowerShell でユーザー アカウント プロパティを構成する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 概要:Office 365 PowerShell を使用して、Office 365 テナント内の個別のまたは複数のユーザー アカウントのプロパティを構成します。
ms.openlocfilehash: 3d81a7e5860b086fd411e8e6fcaab44568e890d5
ms.sourcegitcommit: 4d29b00a57c22225f2cdd592064ee8b6e575fceb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "37411516"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="a8eeb-103">Office 365 PowerShell でユーザー アカウント プロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="a8eeb-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="a8eeb-104">**概要:** Office 365 PowerShell を使用して、Office 365 テナント内の個別のまたは複数のユーザー アカウントのプロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="a8eeb-105">Microsoft 365 管理センターを使用して Office 365 テナントのユーザーアカウントのプロパティを構成することもできますが、Office 365 PowerShell を使用して、管理センターではできないいくつかの操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a8eeb-106">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="a8eeb-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="a8eeb-107">Graph モジュールの Azure Active Directory PowerShell を使用してユーザーアカウントのプロパティを構成するには、 [set-azureaduser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="a8eeb-108">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="a8eeb-109">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="a8eeb-109">Change properties for a specific user account</span></span>

<span data-ttu-id="a8eeb-110">**-ObjectID** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="a8eeb-111">最も一般的なパラメーターの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="a8eeb-112">-Department "\<部署名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="a8eeb-113">-DisplayName "\<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="a8eeb-114">-FacsimilieTelephoneNumber "\<fax 番号>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="a8eeb-115">-GivenName "\<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="a8eeb-116">-Surname "\<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="a8eeb-117">-Mobile "\<携帯電話番号>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="a8eeb-118">-JobTitle "\<役職>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="a8eeb-119">-PreferredLanguage "\<言語>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="a8eeb-120">-StreetAddress "\<番地>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="a8eeb-121">-City "\<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="a8eeb-122">-State "\<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="a8eeb-123">-PostalCode "\<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="a8eeb-124">-Country "\<国名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="a8eeb-125">-TelephoneNumber "\<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="a8eeb-126">-UsageLocation "\<2 文字の国/地域コード>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="a8eeb-127">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="a8eeb-128">その他のパラメーターについては、[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>

>[!Note]
> <span data-ttu-id="a8eeb-129">**メール**のプロパティは、 **-othermails**パラメーターを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-129">You set the **Mail** property with the **-OtherMails** parameter.</span></span>
>
 
<span data-ttu-id="a8eeb-130">ユーザー アカウントのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-130">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="a8eeb-131">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-131">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a8eeb-132">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-132">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-133">ユーザー プリンシパル名のリストをアルファベット順に並び替えて (**Sort-Object UserPrincipalName**)、次のコマンドに送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-133">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-134">各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-134">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="a8eeb-135">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-135">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="a8eeb-p102">このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a8eeb-138">この例では、Caleb が Ls の表示名を持つユーザーアカウントのユーザープリンシパル名を表示します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-138">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a8eeb-p103">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="a8eeb-141">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="a8eeb-141">Change properties for all user accounts</span></span>

<span data-ttu-id="a8eeb-p104">すべてのユーザーのプロパティを変更する場合には、 **Get-AzureADUser** と **Set-AzureADUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="a8eeb-144">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-144">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a8eeb-145">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-145">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-146">ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-146">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="a8eeb-147">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="a8eeb-147">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="a8eeb-p105">特定のユーザー アカウント セットのプロパティを変更する場合には、**Get-AzureADUser**、**Where**、**Set-AzureADUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="a8eeb-150">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-150">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a8eeb-151">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-151">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-152">Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-152">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-153">ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-153">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a8eeb-154">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="a8eeb-154">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a8eeb-155">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用して、ユーザーアカウントのプロパティを構成するには、Get-msoluser コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-155">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="a8eeb-156">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-156">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="a8eeb-157">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="a8eeb-157">Change properties for a specific user account</span></span>

<span data-ttu-id="a8eeb-158">特定のユーザー アカウントのプロパティを構成する場合、[Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="a8eeb-p106">**-UserPrincipalName** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="a8eeb-161">-City "\<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="a8eeb-162">-Country "\<国名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="a8eeb-163">-Department "\<部署名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="a8eeb-164">-DisplayName "\<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="a8eeb-165">-Fax "\<fax 番号>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="a8eeb-166">-FirstName "\<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="a8eeb-167">-LastName "\<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="a8eeb-168">-MobilePhone "\<携帯電話番号>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="a8eeb-169">-Office "\<事業所の場所>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="a8eeb-170">-PhoneNumber "\<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="a8eeb-171">-PostalCode "\<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="a8eeb-172">-PreferredLanguage "\<言語>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="a8eeb-173">-State "\<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="a8eeb-174">-StreetAddress "\<番地>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="a8eeb-175">-Title "\<役職名>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="a8eeb-176">-UsageLocation "\<2 文字の国/地域コード>"</span><span class="sxs-lookup"><span data-stu-id="a8eeb-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="a8eeb-177">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="a8eeb-178">その他のパラメーターについては、[Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-178">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

>[!Note]
> <span data-ttu-id="a8eeb-179">**-Alternateemailaddresses**パラメーターを使用して、 **Mail**プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-179">You set the **Mail** property with the **-AlternateEmailAddresses** parameter.</span></span>
>
 
<span data-ttu-id="a8eeb-180">すべてのユーザーのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="a8eeb-181">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a8eeb-182">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-183">ユーザー プリンシパル名のリストをアルファベット順に並び替えて (**Sort-Object UserPrincipalName**)、次のコマンドに送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-183">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-184">各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-184">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="a8eeb-185">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-185">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="a8eeb-p107">このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a8eeb-188">次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="a8eeb-p108">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="a8eeb-191">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="a8eeb-191">Change properties for all user accounts</span></span>

<span data-ttu-id="a8eeb-p109">すべてのユーザーのプロパティを変更する場合には、 **Get-MsolUser** と **Set-MsolUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="a8eeb-194">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-194">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a8eeb-195">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-195">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-196">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-196">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="a8eeb-197">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="a8eeb-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="a8eeb-p110">特定のユーザー アカウント セットのプロパティを変更する場合には、 **Get-MsolUser** 、 **Where-Object** 、 **Set-MsolUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="a8eeb-200">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-200">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="a8eeb-201">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-201">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-202">Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where-Object {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-202">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="a8eeb-203">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-203">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="a8eeb-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8eeb-204">See also</span></span>

[<span data-ttu-id="a8eeb-205">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="a8eeb-205">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="a8eeb-206">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="a8eeb-206">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="a8eeb-207">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="a8eeb-207">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
