---
title: Office 365 PowerShell でユーザー アカウント プロパティを構成する
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
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 概要:Office 365 PowerShell を使用して、Office 365 テナント内の個別のまたは複数のユーザー アカウントのプロパティを構成します。
ms.openlocfilehash: 211210dad54cb0af772af7dc611bc2c0fdf6035a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841604"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="56a64-103">Office 365 PowerShell でユーザー アカウント プロパティを構成する</span><span class="sxs-lookup"><span data-stu-id="56a64-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="56a64-104">Microsoft 365 管理センターを使用して Office 365 テナントのユーザーアカウントのプロパティを構成することもできますが、Office 365 PowerShell を使用して、管理センターではできないいくつかの操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="56a64-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="56a64-105">Graph 用 Azure Active Directory PowerShell モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="56a64-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="56a64-106">Graph モジュールの Azure Active Directory PowerShell を使用してユーザーアカウントのプロパティを構成するには、 [set-azureaduser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0)コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="56a64-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="56a64-107">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)。</span><span class="sxs-lookup"><span data-stu-id="56a64-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="56a64-108">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="56a64-108">Change properties for a specific user account</span></span>

<span data-ttu-id="56a64-109">**-ObjectID** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="56a64-109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="56a64-110">最も一般的なパラメーターの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="56a64-110">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="56a64-111">-Department "\<部署名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="56a64-112">-DisplayName "\<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="56a64-113">-FacsimilieTelephoneNumber "\<fax 番号>"</span><span class="sxs-lookup"><span data-stu-id="56a64-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="56a64-114">-GivenName "\<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="56a64-115">-Surname "\<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="56a64-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="56a64-116">-Mobile "\<携帯電話番号>"</span><span class="sxs-lookup"><span data-stu-id="56a64-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="56a64-117">-JobTitle "\<役職>"</span><span class="sxs-lookup"><span data-stu-id="56a64-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="56a64-118">-PreferredLanguage "\<言語>"</span><span class="sxs-lookup"><span data-stu-id="56a64-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="56a64-119">-StreetAddress "\<番地>"</span><span class="sxs-lookup"><span data-stu-id="56a64-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="56a64-120">-City "\<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="56a64-121">-State "\<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="56a64-122">-PostalCode "\<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="56a64-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="56a64-123">-Country "\<国名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="56a64-124">-TelephoneNumber "\<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="56a64-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="56a64-125">-UsageLocation "\<2 文字の国/地域コード>"</span><span class="sxs-lookup"><span data-stu-id="56a64-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="56a64-126">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="56a64-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="56a64-127">その他のパラメーターについては、[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56a64-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="56a64-128">ユーザー アカウントのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="56a64-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="56a64-129">このコマンドにより、Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="56a64-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="56a64-130">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-131">ユーザープリンシパル名のリストをアルファベット順に並べ替え ( **UserPrincipalName を並べ替え**)、次のコマンドに**|** 送信します ()。</span><span class="sxs-lookup"><span data-stu-id="56a64-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-132">各アカウントのユーザープリンシパル名プロパティのみを表示します ( **UserPrincipalName を選択**します)。</span><span class="sxs-lookup"><span data-stu-id="56a64-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="56a64-133">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="56a64-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="56a64-p102">このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="56a64-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="56a64-136">この例では、Caleb が Ls の表示名を持つユーザーアカウントのユーザープリンシパル名を表示します。</span><span class="sxs-lookup"><span data-stu-id="56a64-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="56a64-p103">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="56a64-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="56a64-139">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="56a64-139">Change properties for all user accounts</span></span>

<span data-ttu-id="56a64-p104">すべてのユーザーのプロパティを変更する場合には、 **Get-AzureADUser** と **Set-AzureADUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="56a64-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="56a64-142">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="56a64-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="56a64-143">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-144">ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="56a64-145">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="56a64-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="56a64-p105">特定のユーザー アカウント セットのプロパティを変更する場合には、**Get-AzureADUser**、**Where**、**Set-AzureADUser** コマンドレットの組み合わせを使用することができます。次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="56a64-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="56a64-148">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="56a64-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="56a64-149">ユーザー アカウントのすべての情報を取得 (**Get-AzureADUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-150">Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-151">ユーザーの所在地をフランスに設定します (**Set-AzureADUser -UsageLocation "FR"**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="56a64-152">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用する</span><span class="sxs-lookup"><span data-stu-id="56a64-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="56a64-153">Windows PowerShell 用 Microsoft Azure Active Directory モジュールを使用して、ユーザーアカウントのプロパティを構成するには、 **get-msoluser**コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="56a64-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="56a64-154">まず、[Office 365 テナントに接続します](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="56a64-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="56a64-155">PowerShell Core は、Windows PowerShell 用 Microsoft Azure Active Directory モジュールと、名前に **Msol** が含まれるコマンドレットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="56a64-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="56a64-156">これらのコマンドレットを引き続き使用するには、Windows PowerShell から実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56a64-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="56a64-157">特定のユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="56a64-157">Change properties for a specific user account</span></span>

<span data-ttu-id="56a64-158">特定のユーザー アカウントのプロパティを構成する場合、[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) コマンドレットを使用して、設定または変更するプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="56a64-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="56a64-p107">**-UserPrincipalName** パラメーターでアカウントを識別し、その他のパラメーターで特定のプロパティを設定または変更します。最も一般的なパラメーターの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="56a64-p107">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="56a64-161">-City "\<市区町村名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="56a64-162">-Country "\<国名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="56a64-163">-Department "\<部署名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="56a64-164">-DisplayName "\<完全なユーザー名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="56a64-165">-Fax "\<fax 番号>"</span><span class="sxs-lookup"><span data-stu-id="56a64-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="56a64-166">-FirstName "\<ユーザーの名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="56a64-167">-LastName "\<ユーザーの姓>"</span><span class="sxs-lookup"><span data-stu-id="56a64-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="56a64-168">-MobilePhone "\<携帯電話番号>"</span><span class="sxs-lookup"><span data-stu-id="56a64-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="56a64-169">-Office "\<事業所の場所>"</span><span class="sxs-lookup"><span data-stu-id="56a64-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="56a64-170">-PhoneNumber "\<勤務先電話番号>"</span><span class="sxs-lookup"><span data-stu-id="56a64-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="56a64-171">-PostalCode "\<郵便番号>"</span><span class="sxs-lookup"><span data-stu-id="56a64-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="56a64-172">-PreferredLanguage "\<言語>"</span><span class="sxs-lookup"><span data-stu-id="56a64-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="56a64-173">-State "\<都道府県名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="56a64-174">-StreetAddress "\<番地>"</span><span class="sxs-lookup"><span data-stu-id="56a64-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="56a64-175">-Title "\<役職名>"</span><span class="sxs-lookup"><span data-stu-id="56a64-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="56a64-176">-UsageLocation "\<2 文字の国/地域コード>"</span><span class="sxs-lookup"><span data-stu-id="56a64-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="56a64-177">これは、ISO 3166-1 alpha-2 (A2) の 2 文字の国/地域コードです。</span><span class="sxs-lookup"><span data-stu-id="56a64-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="56a64-178">その他のパラメーターについては、[Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="56a64-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="56a64-179">すべてのユーザーのユーザー プリンシパル名を表示するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="56a64-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="56a64-180">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="56a64-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="56a64-181">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-182">ユーザープリンシパル名のリストをアルファベット順に並べ替え ( **UserPrincipalName を並べ替え**)、次のコマンドに**|** 送信します ()。</span><span class="sxs-lookup"><span data-stu-id="56a64-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-183">各アカウントのユーザープリンシパル名プロパティのみを表示します ( **UserPrincipalName を選択**します)。</span><span class="sxs-lookup"><span data-stu-id="56a64-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="56a64-184">一度に 1 画面ずつ表示する ( **More** )。</span><span class="sxs-lookup"><span data-stu-id="56a64-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="56a64-p108">このコマンドにより、使用しているアカウントすべてが表示されます。表示名 (姓と名) を指定してアカウントのユーザー プリンシパル名を表示するには、**$userName** 変数を次のように入力し (\< 記号と > 記号は削除します)、以下のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="56a64-p108">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="56a64-187">次の例では、Caleb Sills という名前のユーザーのユーザー プリンシパル名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56a64-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="56a64-p109">**$upn** 変数を使用すると、表示名に基づいて個々のアカウントに変更を加えることができます。次の例では Belinda Newman の使用場所をフランスに設定しますが、ユーザー プリンシパル名ではなく表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="56a64-p109">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="56a64-190">すべてのユーザー アカウントのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="56a64-190">Change properties for all user accounts</span></span>

<span data-ttu-id="56a64-p110">すべてのユーザーのプロパティを変更する場合には、 **Get-MsolUser** と **Set-MsolUser** コマンドレットを組み合わせて使用できます。次の例は、すべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="56a64-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="56a64-193">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="56a64-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="56a64-194">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-195">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="56a64-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="56a64-196">特定のユーザー アカウント セットのプロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="56a64-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="56a64-197">特定のユーザーアカウントセットのプロパティを変更するには、 **get-msoluser**、 **Where**、および**get-msoluser**コマンドレットの組み合わせを使用できます。</span><span class="sxs-lookup"><span data-stu-id="56a64-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="56a64-198">次の例は、会計部門のすべてのユーザーについて、使用場所をフランスに変更します。</span><span class="sxs-lookup"><span data-stu-id="56a64-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="56a64-199">このコマンドによって Office 365 PowerShell に対して次の処理が命令されます。</span><span class="sxs-lookup"><span data-stu-id="56a64-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="56a64-200">ユーザー アカウントのすべての情報を取得 (**Get-MsolUser**) して、次のコマンドにそれを送信する (**|**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-201">Department プロパティが "Accounting" に設定されているすべてのユーザー アカウントを検索し (**Where {$_.Department -eq "Accounting"}**)、結果の情報を次のコマンドに送ります (**|**)。</span><span class="sxs-lookup"><span data-stu-id="56a64-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="56a64-202">ユーザーの所在地をフランスに設定します ( **Set-MsolUser -UsageLocation "FR"** )。</span><span class="sxs-lookup"><span data-stu-id="56a64-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="56a64-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="56a64-203">See also</span></span>

[<span data-ttu-id="56a64-204">Office 365 PowerShell を使用してユーザーアカウント、ライセンス、グループを管理する</span><span class="sxs-lookup"><span data-stu-id="56a64-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="56a64-205">Office 365 PowerShell による Office 365 の管理</span><span class="sxs-lookup"><span data-stu-id="56a64-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="56a64-206">Office 365 PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="56a64-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
