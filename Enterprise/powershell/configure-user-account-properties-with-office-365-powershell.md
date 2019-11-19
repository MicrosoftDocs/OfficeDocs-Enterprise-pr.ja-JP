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
ms.openlocfilehash: 94596326c9d52b4010f6e9baf67fe3c7a12399be
ms.sourcegitcommit: 21901808f112dd1d8d01617c4be37911efc379f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "38706994"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="cc4a7-103">Office 365 PowerShell でユーザー アカウント プロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="cc4a7-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="cc4a7-104">**概要:** Office 365 PowerShell を使用して、Office 365 テナント内の個別のまたは複数のユーザー アカウントのプロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="cc4a7-105">Microsoft 365 管理センターを使用して Office 365 テナントのユーザーアカウントのプロパティを構成することもできますが、Office 365 PowerShell を使用して、管理センターではできないいくつかの操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="cc4a7-106">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="cc4a7-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="cc4a7-107">Graph モジュールの Azure Active Directory PowerShell を使用してユーザーアカウントのプロパティを構成するには、 [set-azureaduser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="cc4a7-108">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="cc4a7-109">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="cc4a7-109">Change properties for a specific user account</span></span>

<span data-ttu-id="cc4a7-110">**-ObjectID** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="cc4a7-111">最も一般的なパラメーターの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="cc4a7-112">-Department "\<部署名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="cc4a7-113">-DisplayName "\<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="cc4a7-114">-FacsimilieTelephoneNumber "\<fax 番号>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="cc4a7-115">-GivenName "\<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="cc4a7-116">-Surname "\<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="cc4a7-117">-Mobile "\<携帯電話番号>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="cc4a7-118">-JobTitle "\<役職>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="cc4a7-119">-PreferredLanguage "\<言語>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="cc4a7-120">-StreetAddress "\<番地>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="cc4a7-121">-City "\<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="cc4a7-122">-State "\<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="cc4a7-123">-PostalCode "\<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="cc4a7-124">-Country "\<国名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="cc4a7-125">-TelephoneNumber "\<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="cc4a7-126">-UsageLocation "\<2 文字の国/地域コード>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="cc4a7-127">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="cc4a7-128">その他のパラメーターについては、[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="cc4a7-129">ユーザー アカウントのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="cc4a7-130">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cc4a7-131">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-132">ユーザー プリンシパル名のリストをアルファベット順に並び替えて (**Sort-Object UserPrincipalName**)、次のコマンドに送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-133">各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="cc4a7-134">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="cc4a7-p102">このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="cc4a7-137">この例では、Caleb が Ls の表示名を持つユーザーアカウントのユーザープリンシパル名を表示します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="cc4a7-p103">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="cc4a7-140">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="cc4a7-140">Change properties for all user accounts</span></span>

<span data-ttu-id="cc4a7-p104">すべてのユーザーのプロパティを変更する場合には、 **Get-AzureADUser** と **Set-AzureADUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="cc4a7-143">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cc4a7-144">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-145">ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="cc4a7-146">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="cc4a7-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="cc4a7-p105">特定のユーザー アカウント セットのプロパティを変更する場合には、**Get-AzureADUser**、**Where**、**Set-AzureADUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="cc4a7-149">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cc4a7-150">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-151">Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-152">ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="cc4a7-153">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="cc4a7-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="cc4a7-154">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用して、ユーザーアカウントのプロパティを構成するには、Get-msoluser コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="cc4a7-155">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="cc4a7-156">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="cc4a7-156">Change properties for a specific user account</span></span>

<span data-ttu-id="cc4a7-157">特定のユーザー アカウントのプロパティを構成する場合、[Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="cc4a7-p106">**-UserPrincipalName** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="cc4a7-160">-City "\<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="cc4a7-161">-Country "\<国名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="cc4a7-162">-Department "\<部署名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="cc4a7-163">-DisplayName "\<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="cc4a7-164">-Fax "\<fax 番号>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="cc4a7-165">-FirstName "\<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="cc4a7-166">-LastName "\<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="cc4a7-167">-MobilePhone "\<携帯電話番号>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="cc4a7-168">-Office "\<事業所の場所>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="cc4a7-169">-PhoneNumber "\<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="cc4a7-170">-PostalCode "\<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="cc4a7-171">-PreferredLanguage "\<言語>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="cc4a7-172">-State "\<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="cc4a7-173">-StreetAddress "\<番地>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="cc4a7-174">-Title "\<役職名>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="cc4a7-175">-UsageLocation "\<2 文字の国/地域コード>"</span><span class="sxs-lookup"><span data-stu-id="cc4a7-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="cc4a7-176">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="cc4a7-177">その他のパラメーターについては、[Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

<span data-ttu-id="cc4a7-178">すべてのユーザーのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="cc4a7-179">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cc4a7-180">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-181">ユーザー プリンシパル名のリストをアルファベット順に並び替えて (**Sort-Object UserPrincipalName**)、次のコマンドに送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-182">各アカウントのユーザー プリンシパル名プロパティのみを表示する ( **Select-Object UserPrincipalName** )。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="cc4a7-183">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="cc4a7-p107">このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="cc4a7-186">次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="cc4a7-p108">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="cc4a7-189">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="cc4a7-189">Change properties for all user accounts</span></span>

<span data-ttu-id="cc4a7-p109">すべてのユーザーのプロパティを変更する場合には、 **Get-MsolUser** と **Set-MsolUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="cc4a7-192">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cc4a7-193">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-194">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="cc4a7-195">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="cc4a7-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="cc4a7-p110">特定のユーザー アカウント セットのプロパティを変更する場合には、 **Get-MsolUser** 、 **Where-Object** 、 **Set-MsolUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="cc4a7-198">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="cc4a7-199">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-200">Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where-Object {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="cc4a7-201">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="cc4a7-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc4a7-202">See also</span></span>

[<span data-ttu-id="cc4a7-203">Office 365 PowerShell を使ってユーザー アカウントとライセンスを管理します。</span><span class="sxs-lookup"><span data-stu-id="cc4a7-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="cc4a7-204">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="cc4a7-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="cc4a7-205">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="cc4a7-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
